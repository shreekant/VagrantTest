Vagrant.configure("2") do |config|
  (1..1).each do |i|
	config.vm.define "lb-node-#{i}" do |node|
	  node.vm.box = "puppetlabs/ubuntu-14.04-64-nocm"
      node.vm.provision :shell, path: "test_port.sh"
      node.vm.network :forwarded_port, host: 5555, guest: 80
      node.vm.provision :puppet do |puppet|
        puppet.manifests_path = 'puppet/manifests'
        puppet.module_path = 'puppet/modules'
        puppet.manifest_file = 'init.pp'
	  end
    end
  end
  (1..2).each do |i|
	config.vm.define "lb-node-#{i}" do |node|
	  node.vm.box = "puppetlabs/ubuntu-14.04-64-nocm"
      node.vm.provision :shell, path: "test_port.sh"
      node.vm.network :forwarded_port, host: 6666, guest: 80
      node.vm.provision :puppet do |puppet|
        puppet.manifests_path = 'puppet/manifests'
        puppet.module_path = 'puppet/modules'
        puppet.manifest_file = 'init.pp'
	  end
    end
  end
end