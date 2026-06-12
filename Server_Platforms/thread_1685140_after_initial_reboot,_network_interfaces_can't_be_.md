---
title: "after initial reboot, network interfaces can't be found"
date: 2011-02-10
forum: Server Platforms
---

### Post by rogdawg on 2011-02-10
Last night I created a fresh install of Ubuntu Server 10.10. I was working through a tutorial to set up a development server for home use, and everything worked perfectly. I was able to install OpenSSH, Apache, MySQL, and PHP (and Vim) with no problems. I was also able to use "ifconfig" to determine the network address of the server and I was able to view web pages on the server from another machine on my home network, using a browser. So, everything was "peachy". 

[By the way: The server is connected to the router using a CAT5 cable. This is a WIRED connection]

I shut the Ubuntu server down at the end of the night and, now that I have rebooted this morning, I have apparently lost the network interface. I cannot ping anything from the server. If I run ifconfig, only the "lo" configuration is listed, with the 127.0.0.1 address.

Here are the contents of /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

If I run "sudo ifconfig eth1 up", I get the following error:
eth1: ERROR while getting interface flags: No such device

I believe that eth1 is the correct device, as opposed to eth0. When installing Ubuntu Server, two network devices were listed. When I attempted to autoconfig the network using eth0, the installation/configuration failed. When I designated eth1 as the interface, everything worked, network configuration succeeded, and the installation continued. The interface was working because, as I said, as was able to download packages and install them, and I was able to connect to Apache via a browser on another networked computer. 

Is this a driver problem? How can I determine if it is a driver problem, a bad network interface, or just an incorrect setting somewhere in a configuration file?

Thanks in advance for any advice you can give.

---

### Post by volkswagner on 2011-02-10
To eliminate a hardware issue, boot a live CD and verify the NIC works and can get online.

List the output of (network portion only)

```
lspci
```

You can run lsmod to see what is currently loaded.

```
lsmod
```

You can also check logs for helpful information.


```
less /var/log/messages
```

or

```
dmesg | less
```

---

### Post by rogdawg on 2011-02-10
Thank you for your response!

As I was following your instructions, I rebooted the machine once or twice, and now the eth1 connection is working! I haven't done anything to fix the problem, other than rebooting. (I had rebooted earlier, and that did not fix the problem).

I booted to a live CD, as you suggested, and was able to connect to the internet without any problem. When I rebooted to Ubuntu Server, I was using the commands that you suggested to gather as much information as I could. I decided to try ifconfig once more to take a look at that and voila`, eth1 was listed in the configuration. I went to another machine on my home network, and navigated to the IP address listed for eth1, and I was able to see the web page there. 

This is a little disturbing. I am glad that the thing is working now but I don't know why it wasn't working before, and I don't know what fixed the problem. 

Hmmmmm.

Is it possible that booting to the live cd and connecting to the internet somehow corrected a setting that had been damaged? I am grasping at straws at this point...

I have rebooted the server twice, and the ifconfig seems to remain consistent. It appears to be fixed. (I hope)

---

### Post by volkswagner on 2011-02-10
It could be an early warning of failing hardware.

---

### Post by elico on 2011-02-10
or wrong settings in bios.. such as plug and pluy system or irq settings..
or..
did you ever tried 
sudo ifconfig -a
?
the first card is eth0 and not eth1 so it might be something you defined in the network settings.
do you have only one network interface?

---

### Post by rogdawg on 2011-02-10
Thank you all for your posts.

I believe it may be hardware that is failing.

After functioning properly for a while (see my second post) it went out again. I re-booted several times, with no luck. I booted to Ubuntu Desktop Live CD, and this time I COULD NOT connect to the internet. However, once I shutdown the live CD, and booted once more to Ubuntu Server, the connectivity seems to have returned. 

I can ping web sites, eth1 has an inet address attached to it when I run ifconfig -a, and I am able to download packages using "apt-get install".

So, I will have to keep a close eye on this problem, and I may have to get a new NIC. 

Are there any settings, or configurations I should check to see if something that is software-related may actually be the issue?

Thanks for any suggestions you can give.

---

