# All Vagrant configuration is done below.

Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"

  # Disable automatic box update checking.
  config.vm.box_check_update = false

  config.vm.define "cardfile-devel", primary: true do |devel|

    devel.vm.hostname = "cardfile-devel"

    # Create a forwarded port mapping which allows access to a specific port
    # within the machine from a port on the host machine.
    # devel.vm.network :forwarded_port, guest: 80, host: 8080

    # Create a private network, which allows host-only access to the machine
    # using a specific IP.
    # devel.vm.network :private_network, ip: "192.168.33.10"

    # Create a public network, which generally matched to bridged network.
    devel.vm.network :public_network

    # Provider-specific configuration so you can fine-tune various
    # backing providers for Vagrant.
    devel.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "512"
      vb.cpus = 1
    end

  end

  # Enable provisioning with Ansible.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yaml"
    ansible.host_vars = {
      "cardfile-devel" => {"mode" => "devel"},
      # "cardfile-prod" => {"mode" => "prod"},
    }
  end

end
