---
title: "LXC commands hang"
date: 2013-04-20
forum: Virtualisation
---

### Post by thnewguy on 2013-04-20
I am trying to work with LXC to set up containers for web servers. I'm running into two problems which I suspect are linked. The first is that LXC commands often hang. For example, if I run

sudo lxc-create -n Server -t ubuntu -d
sudo lxc-start -n Server

This creates a container, called Server, which I can connect to. So far, so good. However, if I stop the container and then try to start it again

sudo lxc-stop -n Server
sudo lxc-start -n Server -d

The lxc-start command hangs. The container does not appear to be running and the lxc-start command does not return. I am unable to connect to the container using lxc-console. In fact, any lxc- commands will hang if I run them at this point. I have found if I reboot the machine and run lxc-start again it will usually run the container properly, until I try to stop the container or change its configuration.

I'm running Ubuntu 12.04 (both 32-bit and 64-bit). I have tried using LXC on two different machines, both run into the same problem where containers hang until the machine is rebooted.

I have two questions:
1. How can I work around the containers hanging when I try to stop/restart them?
2. What is the easiest way to set up Bridged networking to a container. I've read several tutorials and all of them are really vague on this point. It seems there are a lot of configuration files which alter how containers handle networking and I'm not sure which one (or which ones) would provide the easiest path to bridged networking.


Edit: I have figured out a few things. The first is that if I don't make any configuration changes to LXC on the host, the hang-up doesn't happen. Or at least it hasn't happened again so far. As long as I do all of my configuration within the container it seems to be okay and the LXC container runs. The second thing is the LXC container was trying to use a IPv6 address. My network is exclusively IPv4. Once I forced LXC to use a IPv4 address I was able to connect.

---

### Post by qzjul on 2013-04-21
Hi; how exactly did you force it to use an IPv4 address? I've managed to give mine an IPv4 address, but can't connect to it via ssh, only via the console, and have no network connectivity.

---

### Post by thnewguy on 2013-04-22
This might not be the most correct way to do it, but I logged into the LXC container using lxc-console. Then I ran
```

ifconfig eth0 down
ifconfig eth0 up 10.0.3.10

```

Once that was done I could connect to 10.0.3.10 using ssh. You can put the above lines in the /etc/rc.local script and they will run automatically whenever the container is run.

Now, if your host is not on the 10.0.3.x network you may need to edit another file. I think the /etc/defaults/lxc file contain the default network settings and specify the address of the host's network/bridge interface. Change the IP range in the /etc/defaults/lxc file to reflect your local network addresses and reboot the host. In my case I would change the network range from 10.0.3.x to 192.168.0.x

I hope that helps. I've been sort of casting around in the dark with this as I can't find any clear documentation on the subject.

---

