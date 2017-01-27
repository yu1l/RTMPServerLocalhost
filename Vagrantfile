Vagrant.configure(2) do |config|
  # Staging Server
  config.vm.define 'stagingServer' do |staging|
    staging.vm.box = 'ubuntu/trusty64'
    staging.vm.box_check_update = false
    staging.vm.network 'public_network'
    staging.vm.network 'forwarded_port', guest: 80, host: 8080
    staging.vm.synced_folder '../data', '/vagrant_data', disabled: true

    staging.vm.provider 'virtualbox' do |vb|
      vb.gui = false
      vb.memory = '4096'
    end
    staging.vm.provision 'ansible' do |ansible|
      ansible.playbook = 'provisioning/main.yml'
    end
  end

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   sudo apt-get update
  #   sudo apt-get install -y apache2
  # SHELL
end
