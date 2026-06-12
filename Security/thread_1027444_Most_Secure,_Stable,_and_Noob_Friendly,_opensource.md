---
title: "Most Secure, Stable, and Noob Friendly, opensource VPN"
date: 2009-01-01
forum: Security
---

### Post by SSVegito888 on 2009-01-01
What is the most secure, stable, and noob Friendly opensource VPN for wireless and wired networking?


Tutorials for your vpn soloution answer would be apprecciated.


Thanks,
SSVegito888

---

### Post by pdtpatrick on 2009-01-01
[http://openvpn.net/index.php/documentation/howto.html](http://openvpn.net/index.php/documentation/howto.html)

---

### Post by hyper_ch on 2009-01-01
I think most secure and noob friendly exclude one another. Noob friendly, IMHO, is setting only a few settings (if at all) and the most secure will have to be setted to your needs.

---

### Post by The Cog on 2009-01-01
OpenVPN is secure, performs well and utterly reliably in my experience. It also works through NAT. OpenVPN is in the repositories. Use the HOWTO that pdtpatrick linked to to work out a configuuration. It's a bit complex but the HOWTO is very detailed. The server configuration file goes in /etc/openvpn (the boot-up scripts look there).

---

### Post by SSVegito888 on 2009-01-02
I have 4 more questions.

1. I am planning on putting the vpn on my home computer.


I have 2 notebooks that I want to use the vpn.

Basically, I was wondering since the vpn will be on my desktop pc, will I still be able to use my desktop pc to do other stuff such as browse the web, check email, watch movies, and use samba and still be secure (If I use Safe practices)?

--------------------------------------------------------------------------

2. Do I need to know IPTables or can I use a GUI such as gufw or firestarter for my desktop pc (the one with the vpn)?

--------------------------------------------------------------------------


3. To use the vpn with wifi do I need a certain type of router such as a wireless vpn router or can I use a just standard wireless NAT router?

--------------------------------------------------------------------------


4. Is 512 megs of ram enough to run a vpn?








Thanks and sorry for asking so many questions,


SSVegito888

---

### Post by The Cog on 2009-01-02
1:
Yes you should be able to do all the other stuff too. The VPN will consumen very litle resource. However, I don't think that list goes very will with your stated 512 Meg. The VPN isn't the issue, but all the other stuff might be.

2:
You don't need to know iptables. If you want your laptope to route **through** your desktop to other PCs, you will have to enable IP forwarding on your desktop and then will perhaps want a firewall to limit what else they can connect to. 

But if the laptops are just connecting to the desktop then I'm not sure I would even bother with a firewall - what would you permit and what would you block? You would probably want to permit them access to all the desktop's services in which case ou don't need a firewall because you're not blocking anything.

3:
For OpenVPN:
No really special requirerments, except that if you are using a NAT router, you will need to arrange for it to forward the VPN traffic (UDP port 1194 normally) to the desktop. And if you don't have a fixed IP address, you may need to have your router register its address with DynDns or similar so the laptops know which IP address to connect to.

For any other VPN type (Microsoft, Cisco for instance):
You will need a router that can forward multiple IP protocols to your desktop. GRE (IP protocol number 51) is often used, and several different TCP/IP port numbers may also need forwarding. You are unlikely to get both laptops working from the same remote location at the same time because GRE doesn't NAT very nicely.

4:
No problems. But as I said earlier, I'm not sure that 512M is enough for all the other things you mentioned, esp. the movies.

---

### Post by SSVegito888 on 2009-01-03
> **The Cog said:**
> 1:
For any other VPN type (Microsoft, Cisco for instance):
You will need a router that can forward multiple IP protocols to your desktop. GRE (IP protocol number 51) is often used, and several different TCP/IP port numbers may also need forwarding. You are unlikely to get both laptops working from the same remote location at the same time because GRE doesn't NAT very nicely.



What wireless router would you suggest for this.  Also, is there any way to make it so that both laptops can access the desktop simultaneously, is their another protocol I could use to accomplish this?


I can probably spend up to 300 U.S Dollars and I need a STABLE wireless N Router and the notebooks I want to be able to connect simultaneously are running windows vista and Linux.

Also, the windows notebook's wirless NIC uses PRE-N specification. Will this work with the N and N1 specifications?



Thanks,

SSVegito888

---

### Post by The Cog on 2009-01-03
Actually, I notice that my Netgear DG834G router has a "VPN Wizard" that claims to be able to connect to a VPN. It says VPNC type VPNs whatever they are. I've never tried it so can't say how well it works. It might be that two sites both using a Netgear router can be joined using this Netgear VPN feature without doing any PC software configuration or installation at all, but I'm not sure and their documentation is rather skimpy.

The NetGear router cannot forward GRE to an internal VPN end-point though - it can only forward TCP or UDP. So operating a MS or Cisco VPN access server on the inside is not possible. Same goes for my previous ADSL router, and most others, I guess.

I still recommend using OpenVPN, which uses UDP so has no problem going through NAT or being forwarded by cheap ADSL routers.

I have no experience of N wireless hardware - I don't need that kind of speed because my ADSL isn't that fast anyway.

---

### Post by albinootje on 2009-01-03
> **SSVegito888 said:**
> What is the most secure, stable, and noob Friendly opensource VPN for wireless and wired networking?

I found OpenVPN pretty hard to set up in the past :( 
And when I had it running between my desktop and my local file-server I had problems with "static" ip-addresses for the OpenVPN setup.

What looks much easier to do is to set up ssh tunnels, if you're only dealing with two computers, haven't tried that yet though.
Any recommendations ?
===================

By the way, here's a brand new project, perhaps not easy, but looks very flexible and interesting.

[http://exa.czweb.org/?view=cloudvpn](http://exa.czweb.org/?view=cloudvpn)

---

### Post by HermanAB on 2009-01-04
Here is the trick to tunnel Samba over SSH:
[http://aeronetworks.ca/samba-ssh-tunnel-howto.htm](http://aeronetworks.ca/samba-ssh-tunnel-howto.htm)

Cheers,

Herman

---

### Post by SSVegito888 on 2009-01-04
Thanks.



I have 3 more questions about the vpn.



1. If I use my desktop pc (the one with the vpn) will that pc also be secured by the vpn?


2. Also, is the vpn kind of like a barrier around my wired and wirless networks?


3. Will my neighbors be able to see my samba share?



PS: In my Neighborhood, the houses are 30 feet apart (estimation) and the houses are made of wood not brick, so wifi signals go whereever the heck they want.



Thanks Again,

SSVegito888

---

### Post by HermanAB on 2009-01-04
No, no, maybe.  The reason being that you can have multiple network connections to Samba.  The VPN is only one of them.  It is up to you to block other connections.

You need a firewall.  Run firestarter once and configure iptables.  You don't need to keep firestarter running.  Just use it as a wizard to set iptables up.  Thereafter it doesn't matter anymore.

Cheers,

Herman

---

### Post by SSVegito888 on 2009-01-05
I'm a little confused, I know that I will need a firewall, but is the desktop pc going to be behind the vpn.


EXAMPLE: To access the desktop pc remotely, I have to provide authentication to get through the vpn, am I correct.

---

### Post by HermanAB on 2009-01-05
It will be secure if and only if the firewall allows ONLY a VPN connection to the PC.  If the firewall still allows other connections (or no firewall), then someone can still connect to the PC directly over SMB, without using the VPN.

Cheers,

Herman

---

### Post by SSVegito888 on 2009-01-06
Thanks,

Thats good to know.



Also, I may have good news.  Intrepid comes with a GUI to set up openvpn and vpnc connection.

It is the network manager applet in the sys tray.


The only thing is, I can't upgrade to intrepid because I don't have enough system resources.


Is there any way you can tell me how to upgrade network-manager but not to Intrepid.



I'll even take files from debian.


I know you can't let things in, but is there a way to use the ports to run media servers after you get into the vpn.



How do I get the ports to forward on my desktop to forward through the vpn to the outside world securely by still having to auth to the vpn.



Eg. (Direction:OUT) Media Server >>>  VPN >>> Internet


Eg. (Direction:IN) Internet >>> VPN >>> Media Server



Eg. Same with vnc


Eg. same with ssh

---

### Post by albinootje on 2009-01-06
> **SSVegito888 said:**
> 
The only thing is, I can't upgrade to intrepid because I don't have enough system resources.


You're running Hardy now ? 
What do you mean with not "enough system resources" ? 
Is it the lack of free disk space for /var/cache/apt/archives/ ?

---

### Post by SSVegito888 on 2009-01-06
Every time I either upgrade to intrepid or do fresh install of intrepid on my desktop, my desktop pc slows down my system by a lot.


I am running ubuntu hardy heron with all updtaes, Intel x86.


sorry for the confusion.

---

### Post by SSVegito888 on 2009-01-06
I think it is because I only have 512 megs of RAM.

I don't think it is the processor because it is a Pentium 4.



Another problem is is the computer is over 3 yrs. old.  It is also a Dell from Hell.


Here: is the output of /proc/cpuinfo


processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 1
cpu MHz		: 2793.170
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 3
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pebs bts pni monitor ds_cpl cid xtpr
bogomips	: 5591.21
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 1
cpu MHz		: 2793.170
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 3
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pebs bts pni monitor ds_cpl cid xtpr
bogomips	: 5586.03
clflush size	: 64





PS: I know my processor is 64bit.  I just choose to use 32bit OS's because of software compatiblity.

---

### Post by SSVegito888 on 2009-01-06
Sorry, I made a mistake, I was configuring Fedora earlier and forgot that I had to install openvpn support into network manager.  I found the package in the ubuntu repos to do the same in ubuntu and installed it. The GUI is now installed in my ubuntu hardy heron desktop.


But, if you can I would still like to upgrade my network manager.  Remember, I will also take packages from debian.


PS: I'd rather get the packages from ubuntu's repos, but if this is not possible, then I'll take debian packages (Not Full Blown Debian Repos Please; just packages)

---

### Post by SSVegito888 on 2009-01-06
I want to create a network similar to the one depicted at the url below under router setup.


The only thing is, in the diagram, it talks about using ssh.  Since I am going to be using openvpn, do I really need the ssh.



Is the network manager's openvpn integrated GUI powerful enough for what I need it for.


Also, if my new wireless router has a firewall built-in, will this cause problems

Thanks

---

