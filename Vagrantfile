# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"

  # use NFS as it's a lot faster
  config.vm.synced_folder ".", "/vagrant", type: "nfs"

  # cachier - save us some time and bandwidth please..
  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
    config.cache.synced_folder_opts = { type: :nfs, mount_options: ['rw', 'vers=3', 'tcp', 'nolock'] }
  end

  # Create a private network, which allows host-only access to the machine using a specific IP.
  config.vm.network "private_network", ip: "192.168.51.10"
  config.vm.hostname = "drupal8.dev"

  # provisioning of the vm
  config.vm.provision :shell, path: "scripts/vagrant-always.sh", run: "always"
  config.vm.provision :shell, path: "scripts/vagrant-once.sh"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "drupal8"
    vb.memory = 1024
  end

end
