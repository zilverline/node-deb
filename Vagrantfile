# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|

  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.auto_detect = true
    config.cache.scope = :box
  end

  # because of GuestAdditions problems
  config.vbguest.auto_update = false

  config.vm.provision 'nodejs', type: 'shell', path: './test/nodejs-install.sh'

  config.vm.define :upstart do |box|
    box.vm.host_name = 'upstart'
    box.vm.box = 'ubuntu/trusty64'
    box.vm.network :private_network, ip: '192.168.200.2'
    box.vm.provision 'bootstrap', type: 'shell', path: './test/upstart-project/upstart-bootstrap.sh'
  end

  config.vm.define :systemd do |box|
    box.vm.host_name = 'systemd'
    box.vm.box = 'debian/jessie64'
    box.vm.network :private_network, ip: '192.168.200.3'
    box.vm.provision 'bootstrap', type: 'shell', path: './test/systemd-project/systemd-bootstrap.sh'
  end

end
