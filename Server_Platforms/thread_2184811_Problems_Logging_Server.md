---
title: "Problems Logging Server"
date: 2013-10-30
forum: Server Platforms
---

### Post by unsoc on 2013-10-30
I've had my home server up and running for some time now with no issues. Over the last few months there seems to be an issue logging in with SSH or SFTP when logging in the first attempt don't work, it usually takes two or three times until the server will allow a connection. I have another server that lets me in on the first try. What would be causing this issue? Both servers are Ubuntu Sever 12.04

---

### Post by TheFu on 2013-10-30
What do the log files on both the client and server show?
Have you tried using the IP address directly?
Any recent changes to DNS or /etc/hosts files?
Using key-based authentication or passwords?
Capslock?

Is this on the LAN or over the internet? Is there a router involved?

---

### Post by tgalati4 on 2013-10-31
How much RAM in each?  If the ssh daemon is swapped out of memory, that could cause a delay in authentication resulting in a failed attempt for the first time.  Does one server have more memory than the other?  How many processes are running on each?  Are either running virtual machines?  If so, how many?

---

### Post by unsoc on 2013-10-31
Thanks for the replies. This morning I went to login the server that wasn't given me problems, and now that one is doing the same thing. I have it tracked down to my router, I have DHCP Reservation set for both machines. Last night I added the other server in the router to tell it what IP to use.

Would it be best for the router to hand out IP's using DHCP Reservation or set all this in the config files for the server?

---

### Post by tgalati4 on 2013-10-31
Generally you want manually-assigned IP's for this reason.  The ssh daemon consults a file that has the encrypted passwords associated with the IP of the attempting remote machine.  If your IP's are changing with DHCP, then ssh will have multiple entries with the same password, which creates a problem.  DHCP is used for casual users.  If you are using ssh, you are no longer a casual user.

And since you are no longer a casual user, you have some reading to do:  [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

Also, make sure you have the same /etc/hosts file on each machine with the correct, manual IP's defined.

---

### Post by SeijiSensei on 2013-11-01
If you are using your router as the DNS server, you may be able to add hostname records for the servers whose IPs you set up manually. If so, that is far preferable to maintaining hosts files on any clients.

---

### Post by TheFu on 2013-11-01
> **unsoc said:**
> Would it be best for the router to hand out IP's using DHCP Reservation or set all this in the config files for the server?

In a home environment, where to use DHCP reservations or not is a personal preference, but there are issues. What happens when the router fails? That does happen from time to time.

I use a mix of DHCP reservations and static IP setups. 
* DHCP reservations are only used for portable devices - Android phones, tablets, laptops, netbooks.
* Manually configured static IPs are used for desktops, servers and VMs.  I centrally manage a /etc/hosts file and can redeploy it easily to all -server- systems through Ansible templates. 

There are times when both methods suck and there are times with both methods work perfectly. I see both cases here.

I would strongly suggest that you use static IPs manually configured and push /etc/hosts files out. In this way a network issue with the switch, router, cables doesnt mean that DNS has failed for internal name resolving. That can be very nice when trying to solve issues like you are seeing .... which, BTW, may still be 100% due to your router or cables.

BTW, my /etc/hosts file is about 12,000 lines - mostly blocking ad networks, but also tracking networks and just nasty parts of the internet like cnbc7.com.  The internal DNS server has this same hosts file, so Android devices (not rooted) don't get screwed too much.  You can read about it on lifehacker.com

---

### Post by tgalati4 on 2013-11-01
I follow the advice of TheFu on my home network, a mixture of DHCP and static IP's for fixed computers and laptops that I do development work on.  Maintaining host files is not an issue if you have a NAS or at least one device that has a network file share, then you can grab the updated host file addendum and either cut and paste or simply ssh into the server and cut and paste the host entries to the new machine.

Using ssh from mobile devices can be problematic, but you can set long DHCP lease times, so that your IP addresses don't change that often.

---

### Post by SeijiSensei on 2013-11-02
I run bind9 on a server and manage all my name services that way.  I hate using hosts files.

I don't use host files for adblocking or anything like that either.  I find it's much easier letting AdBlockPlus and Ghostery handle these things at the browser level.  At a client site, though, we push every request through Squid and impose all the blocking there.  It's a lot easier than managing 200+ workstations!

---

### Post by TheFu on 2013-11-02
> **SeijiSensei said:**
> I run bind9 on a server and manage all my name services that way.  I hate using hosts files.

I don't use host files for adblocking or anything like that either.  I find it's much easier letting AdBlockPlus and Ghostery handle these things at the browser level.  At a client site, though, we push every request through Squid and impose all the blocking there.  It's a lot easier than managing 200+ workstations!

Servers need to come up, be on the network, and provide services regardless of DNS or DHCP working, IMHO.

I hate using hosts files too.  At least using ansible (or a simple perl filter+ssh script) makes this much easier ... even trivial.

---

### Post by SeijiSensei on 2013-11-02
> **TheFu said:**
> Servers need to come up, be on the network, and provide services regardless of DNS or DHCP working, IMHO.

Sure they do, though a server without a resolvable name is obviously pretty limited. At home here I have little redundancy, but production networks should.  I used to run dhcpd on the same server that hosts my local DNS and mail, but it's just easier to let the router handle it, especially since I only buy routers that use dd-wrt like this nice [Buffalo]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833162069") I picked up the other day.

I'm also trying to cut down my electric bill.  I'm playing with a Raspberry Pi to see how many services it can take over from my ten-year-old Dell server that does DNS/NFS/Samba/Mail/OpenVPN and some routing.  I'm a bit unimpressed at the video quality of the Pi compared to my machines with NVIDIA or ATI adapters, so I may not use it at the display end.  I can see it as a server with an external drive attached.

---

### Post by unsoc on 2013-12-05
Still haven't got this problem cleared up yet. I'm not sure if it's a setting I'm doing wrong or what. These are the settings I have currently

auto lo
iface lo inet static

address 10.168.1.111
netmask 255.255.255.0
network 10.168.1.1
broadcast 10.168.1.253
dns-nameservers 8.8.8.8 8.8.4.4

I don't have the server open outside the router at all, when I login SSH it's with a password. I did just change the network from 10.168.1.0 to 10.168.1.0 to see if that would help out and seems like it did't.

---

### Post by tgalati4 on 2013-12-06
Try changing *network* to *gateway* and take out the *broadcast* line. Reboot.

---

