Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/xenial64"
    config.vm.box_check_update = true

    config.vm.define "webserver" do |server|
        server.vm.hostname = "webserver"
        server.vm.network "private_network", ip: "192.168.50.30"
        server.vm.provider "virtualbox" do |v|
            v.name = "webserver"
            v.memory = 768
            v.cpus = 1
            v.linked_clone = true
            v.gui = false
        end
        server.vm.provision "ansible" do |ansible|
            ansible.playbook = "provisioning/webserver.yml"
        end
    end


    config.vm.define "db1" do |server|
        server.vm.hostname = "db1"
        server.vm.network "private_network", ip: "192.168.50.31"
        server.vm.provider "virtualbox" do |v|
            v.name = "db1"
            v.memory = 1024
            v.cpus = 1
            v.linked_clone = true
            v.gui = false
        end
        server.vm.provision "ansible" do |ansible|
            ansible.playbook = "provisioning/mysql-server.yml"
        end
    end
end