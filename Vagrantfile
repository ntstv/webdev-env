# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |vb|
    #vb.gui = true
    vb.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/var/www/", "1"]
    vb.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/var/www/*", "1"]
    vb.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1"]
    vb.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/usr", "1"]
    vb.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/.", "1"]
	vb.memory = 256
	vb.cpus = 1
  end
  config.vm.box = "ubuntu_1404"
  config.vm.network "private_network", ip: "192.168.33.33"
  config.vm.network "forwarded_port", guest: 80, host: 80
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.network "forwarded_port", guest: 8008, host: 8008
  config.vm.network "forwarded_port", guest: 8078, host: 8078
  config.vm.hostname = "scotchbox"
  config.vm.synced_folder "www", "/var/www", :mount_options => ["dmode=777","fmode=666"]
  config.vm.provision "shell", path: "vm.provision.sh"
end
