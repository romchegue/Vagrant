# -*- mode: ruby -*-
# vi: set ft=ruby :

# Create a new variable mach_quant - the quantity of vortual machines:
$mach_quant = 3


Vagrant.configure("2") do |config|

    config.vm.provider "virtualbox" do |vb|
        vb.gui=false
        vb.memory=256
        vb.cpus=1
        vb.check_guest_additions=false
    end        
    config.vm.box_check_update=true
    config.vm.box="centos/7"

    (1..$mach_quant).each do |i|
        config.vm.define "node#{i}" do |node|
            node.vm.network "public_network", bridge: "wlp3s0", ip: "172.24.113.#{11+i}"
            node.vm.hostname = "node#{i}"

           # # default router
           # config.vm.provision "shell",
           #     run: "always",
           #     inline: "ip route add default via 172.24.113.1 dev eth2"

           # # delete default gw on eth0
           # config.vm.provision "shell",
           #     run: "always",
           #     inline: "sudo -i; eval $(ip route show default | awk '{ if ($5 ==\"eth0\") print \"ip route del default dev \" $5; }')"

        end
    end

end

