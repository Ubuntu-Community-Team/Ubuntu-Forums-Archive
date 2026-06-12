---
title: "Network interfaces, hosts file, etc..."
date: 2010-08-08
forum: Server Platforms
---

### Post by CoolBreeze47 on 2010-08-08
Hi

I'm using Ubuntu 10.04. I've had no problems at all following the instructions provided for setting up the "perfect server" with ISPConfig 3 over at howtoforge. I just have a few questions though...

In "/etc/network/interfaces" I see the following in the example provided...

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

Where exactly do I locate each of these IP's so I can change the ones in the example above to the correct ones and do I need to include all of them?.

Also, in the "/etc/hosts" example is the following...

> 127.0.0.1       localhost.localdomain   localhost
192.168.0.100   server1.example.com     server1

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

I have a business account with a dedicated IP address. Should I use that instead of the "192.168.0.100"?.

Another things is, I have two different domains on my local Ubuntu 10.04 server and even after the DNS resolved successfully, each time I would try to bring up a PHP page it would tell me the file was not found (static pages worked fine).

Finally, I am not using the server edition of Ubuntu 10.04 (I'm using the desktop edition as a server) and so my hostname is "jaybird-desktop" and yet in ISPConfig it's shown as "jaybird.domain.com". Should I do a quick "sudo hostname newname" and change the computer's hostname to match the hostname shown by ISPConfig (in other words, get rid of the "-desktop" part)?.

Ok, one last one (sorry, still new to this). The tutorial says to use "192.168.0.100" in order to view your site locally and yet I've tried adding (or replacing) this in both the interfaces and/or hosts file, rebooting, etc and still no cigar. How exactly are sites viewed locally?.

I've used Linux for a lot of years but up until now, all of my hosting has been done with various WAMPS on a Windows machine so this is a little different for me :).

Thanks again for you any help!.

- CB

---

### Post by Ryan Dwyer on 2010-08-08
You said you're using the desktop edition. The desktop edition uses Network Manager for networking, whereas the server version uses /etc/network/interfaces. Looks like the desktop version is also adding the domain to your hostname.

Either use the server version like the tutorial instructs or don't follow that tutorial at all.

---

### Post by CoolBreeze47 on 2010-08-08
@Ryan Dwyer

And how am I supposed to copy/paste all of the numerous commands listed on the site if all I have to work with is a shell?. No Desktop...no browser...not even X. If someone could recommend a browser I could use in the shell, I'd gladly install (and prefer) the server because the server has a low latency kernel and other things that are nice to have when running a server.

-CB

---

### Post by Ryan Dwyer on 2010-08-09
Install SSH on the server (sudo apt-get install openssh-server) then use a client machine to connect to it and paste your commands into the SSH terminal.

---

### Post by spynappels on 2010-08-09
You may also find it helpful to read up a bit on what different bits of the tutorial are talking about. This way, rather than slavishly following a tutorial using copy and paste, you will understand what each command does and why you are using it. This way you can tailor your server to your own needs, rather than setting up a server the way someone else wants it to be. Tutorials are very useful if they are understood and can be adapted to your own needs. 

Perhaps if you can explain what you are setting up the server to so, we can offer more specific help. There is no one answer to your original questions as the answer will depend on your network setup etc.

---

### Post by 1serveyou on 2010-08-09
> **spynappels said:**
> You may also find it helpful to read up a bit on what different bits of the tutorial are talking about. This way, rather than slavishly following a tutorial using copy and paste, you will understand what each command does and why you are using it. This way you can tailor your server to your own needs, rather than setting up a server the way someone else wants it to be. Tutorials are very useful if they are understood and can be adapted to your own needs. 

Perhaps if you can explain what you are setting up the server to so, we can offer more specific help. There is no one answer to your original questions as the answer will depend on your network setup etc.

I completely agree. I was in the same position a few months back, and I was a deer in headlights at first. Once, I start looking up what the different things meant, it has made it a lot easier.

---

### Post by koenn on 2010-08-09
quick answers:
1- you don't locate those IP adresses. You choose them. Or they follow from how the rest of your network is set up

2- you should probably not use the IP address your ISP assigned to you, but that depends on how your network is set up.

3- the thing about DNS and PHP is very unclear, I have no idea what you're trying to say, but anyway, it's better not to try to solve that untul you got your networking working correcvtly

4- you browse files by typing 'http://' + their address, or the server name,  in the address of a web browsser.



I agree with spynappels. blindly following a tuturial without any understanding of what you're doing is not how you (learn to) manage a server.

---

