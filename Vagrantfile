# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.define "testlub"
  config.vm.hostname = "testlub"
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.name = "testlub"
  end
  config.vm.network "public_network"
  config.vm.synced_folder "share", "/home/share"
#  config.vm.provision "chef_solo" do |chef|
#    chef.cookbooks_path = "prj/cookbooks"
#    chef.add_recipe "ruby"
#  end
  config.vm.provision "shell", inline: <<-SHELL
    sudo yum install -y git-core zlib zlib-devel gcc-c++ patch readline readline-devel libyaml-devel libffi-devel openssl-devel make bzip2 autoconf automake libtool bison curl sqlite-devel
    curl -sL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-installer | bash -
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
    echo 'eval "$(rbenv init -)"' >> ~/.bashrc
    source ~/.bashrc
    rbenv install 2.5.1
    rbenv global 2.5.1
    gem install bundler
    gem install rails -v 5.2.0
    gem install sqlite3
    rbenv rehash
  SHELL


  # config.vm.box_check_update = false

  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # config.vm.network "private_network", ip: "192.168.33.10"

end
