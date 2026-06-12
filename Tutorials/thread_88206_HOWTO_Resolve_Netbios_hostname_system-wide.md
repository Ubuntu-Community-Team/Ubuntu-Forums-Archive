---
title: "HOWTO: Resolve Netbios hostname system-wide"
date: 2005-11-09
forum: Tutorials
---

### Post by javiwwweb on 2005-11-09
Let me start with a little background info.  I manage a computer lab with 85 workstations.  I ocassionally use either RDP or VNC to do some maintenance.  I have no problem doing this from windows, but I wanted my lonely Ubuntu workstation to be able to do the same thing.  After about a week of research I am finally able to ping my windows workstations via their Netbios names.  Woohoo!!

All you have to do is:

edit /etc/nsswitch.conf

change the line that says

> hosts:          files dns 

to this:

> hosts:          files wins dns
(order does matter)

finally, you need to install winbind

```
sudo apt-get install winbind
```

that's all that it took for me.

now ping <hostname> works great.  And I can finally use the built-in terminal server client with hostnames instead of IP addresses.


I hope this brief guide can be of help!  Thank you all for always providing such great support in these forums!

---

### Post by smack on 2005-11-09
That's real handy. Thanks a lot! :D

---

### Post by ashrack on 2005-12-08
Tanx man. Works great

---

### Post by prammy on 2005-12-09
awesome tip :-)

---

### Post by ashrack on 2005-12-09
This tip should be added to the guide. At help.ubuntu.com
Anyway to make this happen?

---

### Post by One Quick Question on 2005-12-09
Arg.  I've been so confused about this for a while.   Why isn't that wins bit on there by default?

---

### Post by ashrack on 2005-12-10
[QUOTE=One Quick Question]Arg.  I've been so confused about this for a while.   Why isn't that wins bit on there by default?[/QUOTE]
I am wondering the same thing?

---

### Post by doclivingston on 2005-12-10
[QUOTE=One Quick Question]Arg.  I've been so confused about this for a while.   Why isn't that wins bit on there by default?[/QUOTE]

Probably because winbind isn't installed by default (it's in Universe), the same reason why mdns lookup using Avahi isn't enabled by default.

---

### Post by zeusave on 2005-12-12
Thank you very much, very good post.

---

### Post by ashrack on 2005-12-13
[QUOTE=doclivingston]Probably because winbind isn't installed by default (it's in Universe), the same reason why mdns lookup using Avahi isn't enabled by default.[/QUOTE]
But at least this should be in the guide

---

### Post by tbeehler on 2005-12-28
[QUOTE=javiwwweb]Let me start with a little background info.  I manage a computer lab with 85 workstations.  I ocassionally use either RDP or VNC to do some maintenance.  I have no problem doing this from windows, but I wanted my lonely Ubuntu workstation to be able to do the same thing.  After about a week of research I am finally able to ping my windows workstations via their Netbios names.  Woohoo!!

All you have to do is:

edit /etc/nsswitch.conf

change the line that says



to this:



finally, you need to install winbind

```
sudo apt-get install winbind
```

that's all that it took for me.

now ping <hostname> works great.  And I can finally use the built-in terminal server client with hostnames instead of IP addresses.


I hope this brief guide can be of help!  Thank you all for always providing such great support in these forums![/QUOTE]


You sir are my personal hero.  This problem was driving me NUTS!  Worked perfectly!

Travis

---

### Post by grendelkhan on 2005-12-29
i agree, given that samba sharing is part of the official gnome directory sharing tool now, there's no reason this setup is not the default with ubuntu.

think of how easy it makes networking a new user's ubuntu install with their existing windows network?

Thank you again sir, you are a genius.

---

### Post by soosh on 2006-02-03
Thanks so much for this tip!  It should absolutely be in the guide, or added to this wiki:  [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

---

### Post by ace2005 on 2006-02-03
What does Netbios do? dont you get hacked using that? or is that just windows?

---

### Post by ashrack on 2006-02-15
[QUOTE=ace2005]What does Netbios do? dont you get hacked using that? or is that just windows?[/QUOTE]
By using NETBIOS U no longer have to access your remote computers by only IP numbers which is kinda hard to remember but with their computer name

---

### Post by digitalsy on 2006-02-26
doooood! I can go to bed now, this problem was driving my insannnneee! THANKS!

---

### Post by claes on 2006-02-26
[QUOTE=ashrack]By using NETBIOS U no longer have to access your remote computers by only IP numbers which is kinda hard to remember but with their computer name[/QUOTE]

Yes thats correct but you do it by using the microsoft way of doing it with WINS. A much better solution would be that ubuntu would handle dynamic dns.

Claes

---

### Post by ashrack on 2006-02-28
[QUOTE=claes]Yes thats correct but you do it by using the microsoft way of doing it with WINS. A much better solution would be that ubuntu would handle dynamic dns.
[/QUOTE]
Could U be more specific, why would DYN DNS be better?

---

### Post by qferret on 2006-03-13
Though in most cases I agree dynamic DNS is a better solution, what about small LAN's that don't have their own DNS servers? Shouldn't need to hardcode IP's and use host files just because your network is small and not worth the expense of your very own DNS server. NetBIOS is a way to accomplish this without extra hardware....

btw....muchos gracias javiwwweb!!! =D>

---

### Post by mr.p on 2006-03-14
\\:D/ 

Thumbs up on this HOWTO, will be sure to remember this.

---

### Post by claes on 2006-03-27
[QUOTE=qferret]Though in most cases I agree dynamic DNS is a better solution, what about small LAN's that don't have their own DNS servers? Shouldn't need to hardcode IP's and use host files just because your network is small and not worth the expense of your very own DNS server. NetBIOS is a way to accomplish this without extra hardware....

btw....muchos gracias javiwwweb!!! =D>[/QUOTE]

But it's worth the expense of a wins server? Or are you saying that it's ok with silly microsoft broadcasts (smb)?

Claes

---

### Post by FredSambo on 2006-03-27
thanks a lot, this works great!

---

### Post by dungtran0719 on 2006-04-29
yes very good! thanks man!

---

### Post by n8bounds on 2006-05-01
You rock.  plus plus, man

---

### Post by frio on 2006-05-09
Thanks javiwwweb... worked perfectly as described.

---

### Post by [Yatta] on 2006-05-13
[QUOTE=qferret]Though in most cases I agree dynamic DNS is a better solution, what about small LAN's that don't have their own DNS servers? Shouldn't need to hardcode IP's and use host files just because your network is small and not worth the expense of your very own DNS server. NetBIOS is a way to accomplish this without extra hardware....

btw....muchos gracias javiwwweb!!! =D>[/QUOTE]

I have ubuntu working as a DDNS server.. and there is no extra hardware in my mix .  I can ping hostname and IP address effortlessly. The method described above seems to get the job done no problem. :D

---

### Post by ashrack on 2006-05-14
For all of those running DAPPER and getting SEG FAULT of the WINBIND in the REPOS use this WINBIND which fixes that:
[http://www.eleves.ens.fr/home/gama/samba/winbind_3.0.22-1ubuntu1_i386.deb](http://www.eleves.ens.fr/home/gama/samba/winbind_3.0.22-1ubuntu1_i386.deb)

I got it from this bug report:
[https://launchpad.net/bugs/39990](https://launchpad.net/bugs/39990)

---

### Post by frio on 2006-05-26
Check this... I thought everything was working perfectly but now I've come across this.

I am using DHCP assigned by my router (Dlink DI-624). The server is a static DHCP assigned IP. At random, or so it seems, I cannot find the server by hostname. It is always available by it's IP.

Example:
I ping SVR1... I get 192.168.1.101:confused:
At some random time later I ping SVr1, I get 192.168.1.2 (correct IP):-D
At some random time later I ping SVR1, I get 192.168.1.103:mad:

This is not a huge deal since this is on a small home network and I know the server IP address. But it is frustrating.

Along with the DHPC, I have Ubuntu setup as the only wins server, and it's te only linux pc on the network. Also, just for the record, I have changed all the windows pc's to not maintain network browser lists:

HKLM\SYSTEM\CurrentControlSet\Services\Browser\Parameters\MaintainServerList = FALSE

Any ideas?

---

### Post by Boelcke on 2006-06-23
Help! I thought this was the answer, but it isn't repeatable for me.

I have two ubuntu PCs on my network, both running 5.10.  I made these changes to the first PC (updated /etc/nsswitch.conf, installed winbind), and it works great.  I can ping the second PC using its hostname.

I thought my problem was solved until I went to do it to the second machine, and it doesn't work.  I updated the nsswitch.conf file, installed winbind, and nothing changed!  I mean, when I try ping the first machine from the second, I still get
> ping: unknown host: hostname
Any ideas on how to troubleshoot this?

---

### Post by spd106 on 2006-07-05
I've been looking for this kind of solution for ages, thanks.

Any ideas how to get the the arp cache to show hostnames as well?

---

### Post by ketnoe on 2006-07-25
I'm rather new to Linux as my operating system.  

I was wondering, if there was an equivalent to Windows "Terminal Server" in Linux/Ubuntu?  

I was using "Remote Desktop Connection" with my old XP, and have used "Terminal Server" too.  I want to basically be able to login to my UBUNTU Box using my Windows laptop.

Is there a way to do this?

thanks for everyones help in advance!!..lol.. :-D

---

### Post by viveknz76 on 2006-07-25
A very cool tip.

---

### Post by sile on 2006-07-27
> **ketnoe said:**
> I was wondering, if there was an equivalent to Windows "Terminal Server" in Linux/Ubuntu?

Closest thing i've found is using x11vnc.

```
sudo apt-get install x11vnc
```

Unlike the plain vanilla vnc server, x11vnc will actually let you connect to your existing X session so you can see your real, actual desktop along with anything that you had open.  Makes it work the way VNC server for Windows works.

---

### Post by ashrack on 2006-07-28
But unfortunetly all VNC crap is so SLOOOOW! So it useless when used on LAN

---

### Post by mingster on 2006-08-15
Excellent :D i've been puzzling over this one for a while

I can finally dump windows at work for all my webdev stuff as previously i couldnt figure out how to access the network drives reliably

*grins like a buffoon and loads up NVU*

---

### Post by Kurdt on 2006-08-15
YOU are the MAN !!

---

### Post by sefs on 2006-09-13
> **ketnoe said:**
> I'm rather new to Linux as my operating system.  

I was wondering, if there was an equivalent to Windows "Terminal Server" in Linux/Ubuntu?  

I was using "Remote Desktop Connection" with my old XP, and have used "Terminal Server" too.  I want to basically be able to login to my UBUNTU Box using my Windows laptop.

Is there a way to do this?

thanks for everyones help in advance!!..lol.. :-D

Try NX Server and NX Client from [www.nomachine.com](www.nomachine.com).   Its Terminal Server for linux.

Just Install the NX Client, NX Node, and NX Server on Ubuntu.  Then install the NX Client for windows on your windows laptop and you are good to go.

---

### Post by sefs on 2006-09-13
This does not work for me.

I made teh nsswitch addition of wins then installed winbind.  and tried to ping but no cigar.

Any idea what i am missing.  Do i have to enable wins in smb.conf?

Thanks.

---

### Post by ineluki12 on 2006-09-28
It is not working for me either. Did exactly as he said with no results. The winbindd daemon doesn't appear to be starting, but starting it manually doesn't help. Does anyone have a clue on this? This is a big problem for a lot of people on predominantly Windows networks.

---

### Post by 1_UP on 2006-09-28
Great post!!! Fixed my prob, now I can manage all my Win stations from my Ubuntu laptop!!! yay!!!

---

### Post by 1_UP on 2006-09-28
Great post...fixed my prob, now I can manage my Win terminal with my ubuntu laptop w/o stupid IP addys...sweet!

---

### Post by bandoba on 2006-10-13
Great post OP! The only question I have is - when I try to ping any windows machine, the response to ping is very very slow. Any idea why it is that way? I tried putting wins first in nsswitch.conf but no luck.

---

### Post by c4mden on 2006-10-20
I believe this will only work if the machines you're trying to resolve are on the same subnet.  After setting this up, and doing an nmblookup, it just broadcasts out the request.  So only machines on the same subnet will hear the request.

If your network has multiple subnets and a central wins server, I believe something needs to be setup in samba.  I got this working once in Fedora, but I can't get it to work in Ubuntu for the life of me...

---

### Post by dannyboy79 on 2006-10-20
i don't have winbind installed and I can ping all my boxes (winxp, ubuntu, & xubuntu) by ip as well as HOSTNAME. I simply added all my hostnames and ip's into the /etc/hosts file and in my smb.conf the name resolve order = hosts wins bcast. No need to install WINBIND!! I don't have a WINS server either. Nor did I change my nsswitch. whatever. Just thought I'd let people know this isn't true. There is a setting in WINXP, something about netbios over tcp/ip or whatever that I had to tick.

---

### Post by lordgibbness on 2006-11-15
> **bandoba said:**
> Great post OP! The only question I have is - when I try to ping any windows machine, the response to ping is very very slow. Any idea why it is that way? I tried putting wins first in nsswitch.conf but no luck.

I concur - pinging by name takes much longer than by IP. Has anyone found a solution to this?

---

### Post by dannyboy79 on 2006-11-16
it's the same amount of time for me, check this out, and this is even after sshing into my box from work, he he

ping 192.168.0.5
PING 192.168.0.5 (192.168.0.5) 56(84) bytes of data.
64 bytes from 192.168.0.5: icmp_seq=1 ttl=64 time=9.26 ms
64 bytes from 192.168.0.5: icmp_seq=2 ttl=64 time=1.47 ms
64 bytes from 192.168.0.5: icmp_seq=3 ttl=64 time=1.32 ms
64 bytes from 192.168.0.5: icmp_seq=4 ttl=64 time=1.42 ms


 ping XUBUNTU
PING XUBUNTU (192.168.0.5) 56(84) bytes of data.
64 bytes from XUBUNTU (192.168.0.5): icmp_seq=1 ttl=64 time=1.37 ms
64 bytes from XUBUNTU (192.168.0.5): icmp_seq=2 ttl=64 time=1.29 ms
64 bytes from XUBUNTU (192.168.0.5): icmp_seq=3 ttl=64 time=1.35 ms
64 bytes from XUBUNTU (192.168.0.5): icmp_seq=4 ttl=64 time=1.29 ms
64 bytes from XUBUNTU (192.168.0.5): icmp_seq=5 ttl=64 time=1.28 ms


It's actually quicker by name, ha ha. Don't know why that is. Don't forget, I don't even use winbind, so this is unneccessary to install!

---

### Post by lordgibbness on 2006-11-22
I went down the winbindd route as I don't want a static hosts list.

However, this seems to result in very slow name resolution. Does anyone have any ideas?

---

### Post by lordgibbness on 2006-11-25
Bump.

I have been doing some reading and was unable to find any answers. I have a feeling that it is probably a caching setting. It appears that when I ping my windows boxes it is resolving names by looking up all machines on the network until it finds the match. Windows stores a cached list ('Computer Browser' service). Is there any way to make ubuntu do the same? Perhaps with a one hour cache time or something.

---

### Post by Garyu on 2007-01-22
Bump.

Anything like hostname resolving going on for Feisty Fawn? :-k

---

### Post by steve101101 on 2007-02-27
thanks for the guide. it worked great.:KS

---

### Post by dimeotane on 2007-03-09
Any reason this isn't set already at install by default?  It should also be in the guide shouldn't it?

I wish I had read this a lot sooner!

---

### Post by robinlennox on 2007-03-11
This didn't work for me...

Even after a reboot????

Is it only me who is having an issue?

*****ICMP Packets were block on my firestarter firewall!

So it's working now!****

---

### Post by steve101101 on 2007-03-20
this worked great. Thanks

---

### Post by dannyboy79 on 2007-03-23
This is ONLY if Windows XP is your Local Master Browser or Master Browser or maybe even a wins server. I have my Ubuntu box overrid Winbloz strong desire to become 1 of these because I don't always have my winbloz box on. So I use my hosts file for internal name resolution (i think) I also have the nmbd daemon running, which I believe broadcasts my machines name to the other machines. Windows does this broadcasting thing thru Netbios over TCP/IP I think. (some1 please correct me if I am wrong) I don't have a wins server defined and I don't have an internal DNS server. Also, according to recent documentation, winbind is in the Samba package so if you installed samba, winbind should already installed.  You can find out by doing sudo aptitude show winbind. Ayway, according to man winbindd:

[I]The service provided by winbindd is called `winbind' and can be used to
       resolve user and group information from a Windows NT server.  The  ser-
       vice  can  also  provide  authentication services via an associated PAM
       module.

The following simple configuration in the/etc/nsswitch.conf file can be
       used  to  initially resolve hostnames from /etc/hosts and then from the
       WINS server.

       hosts:         files wins[/I]


So what this is saying is that resolving hostnames is done first by the hosts file ([files) and then a wins server (wins). The guide you followed, the config line was files dns wins so that merely means that it would use the hosts file, then a dns server, then a wins server. **So if you have a wins server and want to use winbind than do so but if you don't have a wins server than there is no need for you to add wins to the nsswitch.conf file** (unless some1 can explian to me otherwise). Just add your hostnames and their ip's to your /etc/hosts file. Much easier! This will only work of course if you have all static ips. You can setup static ip's 2 different ways if your router or dhcp server has this setting. (this is so easy, I don't know why people are so scared to set static ip's) I mean maybe if it's a laptop but if it's a desktop, you dont go around attaching it to different routers do you, so there is no reason for dhcp. Either set the ip static thru the actual OS and it's mask and gateway etc etc or you can config your router or dhcp server so it'll always "reserve" that ip based on the interfaces MAC address. I can do this also thru my netgear, I turn on all computers, then log into my router, then I go LAN IP Setup and tell the dhcp to always give that MAC address the same IP. Also, if you make all your machines static by using the OS (you don't need to disable the dhcp server or router) and still want the dhcp server set so that when you introduce a new computer it gets an ip automatically (say some1 with a laptop comes in to visit) make sure you change your dhcp server ip's so that the range no longer includes the ones that you have statically assigned at the machine's.

For example: 
My router's DHCP server hands out ip's from 192.168.5.20 thru 192.168.5.254
and then I can use 192.168.5.2 thru 192.168.5.19 for static ips and there will never be a same ip problem.

---

### Post by starterz on 2007-04-25
> **javiwwweb said:**
> Let me start with a little background info.  I manage a computer lab with 85 workstations.  I ocassionally use either RDP or VNC to do some maintenance.  I have no problem doing this from windows, but I wanted my lonely Ubuntu workstation to be able to do the same thing.  After about a week of research I am finally able to ping my windows workstations via their Netbios names.  Woohoo!!

All you have to do is:

edit /etc/nsswitch.conf

change the line that says



to this:



finally, you need to install winbind

```
sudo apt-get install winbind
```

that's all that it took for me.

now ping <hostname> works great.  And I can finally use the built-in terminal server client with hostnames instead of IP addresses.


I hope this brief guide can be of help!  Thank you all for always providing such great support in these forums!

Thank you LOTS for this guide. It didn't work for me right away, but it pointed me in the right direction. We have a domain controller (Win2003 Server) which is also a WINS server. I had to place it's IP address (10.10.10.9 for example) in smb.conf WINS server, for Samba to work as a WINS client. Now it works perfectly, even with workstations on different LAN subnets.

---

### Post by Lieter on 2007-05-17
Thanks a great lot, I was trying to get this to work for a week now :KS

---

### Post by Russianspi on 2007-10-26
Still works in Gutsy!  Just add WINS to the appropriate line.  The line looks a little different on Gutsy, but not different enough to cause confusion, I think.  Thanks for the tip.  It's been driving me nuts doing IT in a mixed Windows/Linux environment.  This will make my life much easier!

---

### Post by superfunkymonkey on 2007-12-05
This tip did not work at first for me in Gusty. I had to make a minor tweak.

On top of editing nsswitch.conf and installing winbind I had to declare my wins server in /etc/samba/smb.conf and add a couple lines so that it now looks like this:

wins server = 128.222.100.10
name resolve order = host wins lmhosts bcast
wins proxy = yes

Then that worked. :)

---

### Post by tmcmulli on 2008-01-14
> **dannyboy79 said:**
> . Also, according to recent documentation, winbind is in the Samba package so if you installed samba, winbind should already installed.  

I have Samba on both my 7.10 machines and was never able to resolve my windows dynamic host names until I manually installed winbind

Thanks, javiwwweb!!

---

### Post by dannyboy79 on 2008-01-15
> **tmcmulli said:**
> I have Samba on both my 7.10 machines and was never able to resolve my windows dynamic host names until I manually installed winbind

Thanks, javiwwweb!!

I am not sure how you installed samba but aptitude is very clear as to what all comes with samba when you install samba. I to am running gutsy.

uname -a
Linux gutsy 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

sudo aptitude show samba
Package: samba
State: installed
Automatically installed: yes
Version: 3.0.26a-1ubuntu2.3
Priority: optional
Section: net
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 9433k
Depends: samba-common (= 3.0.26a-1ubuntu2.3), logrotate, libacl1 (>= 2.2.11-1), libattr1 (>= 2.4.4-1), libc6 (>= 2.6-1),
         libcomerr2 (>= 1.33-3), libcupsys2 (>= 1.3.0), libgnutls13 (>= 1.6.3-0), libkrb53 (>= 1.6.dfsg.1), libldap2 (>=
         2.1.17-1), libpam0g (>= 0.99.7.1), libpopt0 (>= 1.10), zlib1g (>= 1:1.2.3.3.dfsg-1), debconf (>= 0.5) | debconf-2.0,
         libpam-runtime (>= 0.76-13.1), libpam-modules, lsb-base (>= 3.0-6), procps, update-inetd
Recommends: smbldap-tools
Suggests: openbsd-inetd | inet-superserver
Replaces: samba-common (<= 2.0.5a-2)
Description: a LanManager-like file and printer server for Unix
 The Samba software suite is a collection of programs that implements the SMB/CIFS protocol for unix systems, allowing you to
 serve files and printers to Windows, NT, OS/2 and DOS clients. This protocol is sometimes also referred to as the LanManager or
 NetBIOS protocol.

 This package contains all the components necessary to turn your Debian GNU/Linux box into a powerful file and printer server.

 Currently, the Samba Debian packages consist of the following:

 samba - LanManager-like file and printer server for Unix.
 samba-common - Samba common files used by both the server and the client.
 smbclient - LanManager-like simple client for Unix.
 swat - Samba Web Administration Tool
 samba-doc - Samba documentation.
 samba-doc-pdf - Samba documentation in PDF format.
 smbfs - Mount and umount commands for the smbfs (kernels 2.2.x and above).
 libpam-smbpass - pluggable authentication module for SMB/CIFS password
                  database
 libsmbclient - Shared library that allows applications to talk to SMB/CIFS
                servers
 libsmbclient-dev - libsmbclient shared libraries
[B] winbind - Service to resolve user and group information from Windows NT
           servers[/B]
 It is possible to install a subset of these packages depending on your particular needs. For example, to access other SMB/CIFS
 servers you should only need the smbclient and samba-common packages.

 [http://www.samba.org/](http://www.samba.org/)

---

### Post by tmcmulli on 2008-01-15
Don't know what to tell you.  Before I explicitly installed winbind, I could not resolve hostnames on my windows boxes.  Now I can...

I actually had to remove the winbind package on my SMB server, because it stopped my machines from being able to talk to the shares correctly...

Damnit... sounds like I have some trouble shooting to do...

---

### Post by PryGuy on 2008-02-03
Id worked for me but veeeeeeeery slow... :( > peter@cheetah:~$ ping server
PING server (192.168.0.1) 56(84) bytes of data.
64 bytes from server.local (192.168.0.1): icmp_seq=1 ttl=64 time=0.241 ms
64 bytes from server.local (192.168.0.1): icmp_seq=2 ttl=64 time=0.230 ms
64 bytes from server.local (192.168.0.1): icmp_seq=3 ttl=64 time=0.242 ms
64 bytes from server.local (192.168.0.1): icmp_seq=4 ttl=64 time=0.246 ms
64 bytes from server.local (192.168.0.1): icmp_seq=5 ttl=64 time=0.239 ms
64 bytes from server.local (192.168.0.1): icmp_seq=6 ttl=64 time=0.242 ms
64 bytes from server.local (192.168.0.1): icmp_seq=7 ttl=64 time=0.240 ms
64 bytes from server.local (192.168.0.1): icmp_seq=8 ttl=64 time=0.228 ms
64 bytes from server.local (192.168.0.1): icmp_seq=9 ttl=64 time=0.246 ms

--- server ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 80101ms
rtt min/avg/max/mdev = 0.228/0.239/0.246/0.014 ms


---

### Post by jdindo01 on 2008-03-17
Couple of things:

1.  I had to login as root using sudo -i
2.  It didn't work.  It still says "Sorry, couldn't display all the contents of Windows Network: "

Any ideas?

---

### Post by mooseydoom on 2008-06-08
Thanks!  Now I can see and browse samba shares in nautilus. I had to put wins before dns in my /etc/nsswitch.conf file to get this to work properly.

/etc/nsswitch.conf
```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

```

---

### Post by scot524 on 2008-07-09
I did the same as moosey -- evertyhing is cool except I get two desktop icons for the share I connect to. At least I did not get the annoying dialog about can't display location smb://blahblah

Thanks for the great tips!

Scot

---

### Post by JohnAdriaan on 2008-07-18
> **PryGuy said:**
> It worked for me but veeeeeeeery slow... :(

I read all this thread with interest, since it matched (some of) the problems I'm having.

When you say the ping is slow, it's misleading: each individual ping is very fast (sub-millisecond), but the time period between pings is a lot longer usual. At least now I know why!

If it was a name resolution problem, then only the initial phase of the ping would have been slow, while it resolved the name into the IP address. From then on, it would have done each ping at the typical one-second intervals.

The reason it's taking so long between each ping is because it is attempting to do a reverse IP lookup on each ping reply - and failing. To prevent that, you'd either need a true DNS server that can resolve reverse IP lookups, or you need to tell ping to stop doing it using the -n option (which means 'numerical only').

Hope this helps!

John

---

### Post by HeikoH on 2008-09-06
> **JohnAdriaan said:**
> The reason it's taking so long between each ping is because it is attempting to do a reverse IP lookup on each ping reply - and failing. To prevent that, you'd either need a true DNS server that can resolve reverse IP lookups, or you need to tell ping to stop doing it using the -n option (which means 'numerical only').

Hope this helps!

John

Ah, that solved indeed the long 'in between' ping times in my case. Unfortunately the long ping times are the least of problems in my configuration. I'm using autofs with ldap to mount nfs shares and ldap to do client authentication. This also is slow which causes some problems sometimes.

Perhaps I'll look into a true DNS server setup to solve this. Unless someone knows how to solve this in a different way?

---

### Post by dmizer on 2008-11-06
> **mooseydoom said:**
> Thanks!  Now I can see and browse samba shares in nautilus. I had to put wins before dns in my /etc/nsswitch.conf file to get this to work properly.

/etc/nsswitch.conf
```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

```
I've updated the howto to reflect this change.

> **dannyboy79 said:**
> **So if you have a wins server and want to use winbind than do so but if you don't have a wins server than there is no need for you to add wins to the nsswitch.conf file** (unless some1 can explian to me otherwise).

Two reasons.
[LIST=1]
[*]CIFS does not query /etc/hosts for name resolution, so if you want to use fstab for mounting your Windows shares, you'll need winbind.
[*]Most retail consumer end routers are configured to hand out IP addresses via DHCP. Static network configuration requires more knowledge and understanding of networking than most people have.
[/LIST]

---

### Post by madflyguy on 2009-03-03
> **javiwwweb said:**
> 
finally, you need to install winbind

```
sudo apt-get install winbind
```


TY TY, I remember doing this once but could not remember where this setting was. HOWEVER for me I only needed to put DNS in front of a few others in that list (but still after files), and this works for me. TY again.

---

### Post by lavi17 on 2009-04-06
Thanx... it solved my problem, now i'm able to ping windows machines using their hostnames from ubuntu, but now i have to tackle a different problem pinging ubuntu from windows... well hope i'll find someway to do that... thanx buddy... :)

---

### Post by dmbfan2007 on 2009-04-26
This fix was working just fine for me in Ibex, but I just did the upgrade to Jaunty Jackalope, and it doesn't.  I opened up the config file to make sure the line was still as it should be, and I even reinstalled winbind.

Any suggestions?

-------------

Edit: It helps when you connect to the correct wireless network :-)

---

### Post by ricojonah on 2009-09-01
> **dmbfan2007 said:**
> This fix was working just fine for me in Ibex, but I just did the upgrade to Jaunty Jackalope, and it doesn't.  I opened up the config file to make sure the line was still as it should be, and I even reinstalled winbind.

Any suggestions?

-------------

Edit: It helps when you connect to the correct wireless network :-)

Wow, what are the odds. I just did that myself. Stupid wireless interwebs! >.D

---

### Post by hawthornso23 on 2009-09-02
Using this method permitted me to setup a network printer by name instead of IP address. This allowed me to let the router assign the printer an IP address by DHCP so that I could avoid the need to set up a static IP address for my network printer.

Static IP addresses don't woprk well for me. The router seems to drop them at unpredictable intervals or whenever the power is interrupted. Every time someone bumped a plug I had to reconfigure the network.

Thanks!

---

### Post by acelandow on 2010-01-18
Worked like a charm.  Thanks!

---

### Post by mws604 on 2010-01-19
I have been looking thru the networking forum for hours and this is the FIRST solution the worked consistently.  THANK YOU!!!

---

### Post by jerwilkins on 2010-03-30
Massive help!
Would be nice if this were included by default :)

---

### Post by papibe on 2010-04-03
Great!... works perfectly.

I'd like to get the order right, though. My original line was:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```
Since order matters, What would be the better place for "wins"? Right after "files" or just before "dns"? Right now I'm using wins after files. Anybody knows what "mdns4_minimal" and "mdns4" mean?

Thanks in advance,
Regards.

---

### Post by dmizer on 2010-04-04
> **papibe said:**
> Great!... works perfectly.

I'd like to get the order right, though. My original line was:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```
Since order matters, What would be the better place for "wins"? Right after "files" or just before "dns"? Right now I'm using wins after files. Anybody knows what "mdns4_minimal" and "mdns4" mean?

Thanks in advance,
Regards.

I would put it after [NOTFOUND=return]. There's no need to scan WINS more than once for host names, and it could possibly slow down internet browsing if you put WINS before [NOTFOUND=return].

---

### Post by Pablo Alonso on 2010-04-06
Thank you very much!!!
This is really easy and works fast! not even have to restart networking service, just editing the file nsswitch.conf will suffice!

Congrats!

Regards,
Pablo Alonso

---

### Post by papibe on 2010-04-06
> **dmizer said:**
> I would put it after [NOTFOUND=return]. There's no need to scan WINS more than once for host names, and it could possibly slow down internet browsing if you put WINS before [NOTFOUND=return].

Thanks dmizer! I followed your advice and made the change.
Regards.

---

### Post by Praetor77 on 2011-05-03
Hi!

Thanks for this guide, but I followed your instructions, as well as some other suggestions I found elsewhere such as installing smbnetfs,opening ports 137-139 and 445 on my firewall, adding:    "name resolve order = host wins bcast lmhosts" and "WINS support = yes" to my smb.conf, and others, to absolutely NO avail.

Nothing worked. After HOURS of googling and reading through forums, I found a solution, and I am posting it here in case it can save somebody else from HOURS of work. Perhaps you could add it to your guide?

Adding nf_conntrack_netbios_ns to IPT_MODULES in /etc/default/ufw
solved my problem and I can now properly resolve netbios hostnames.

That is change:

# extra connection tracking modules to load
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc"

to:

# extra connection tracking modules to load
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns"

Thanks! Regards!

---

### Post by MestreLion on 2012-02-11
> **Praetor77 said:**
> Adding nf_conntrack_netbios_ns to IPT_MODULES in /etc/default/ufw
solved my problem and I can now properly resolve netbios hostnames.

ufw is Ubuntu's firewall, which is not enabled by default, by the way. This has nothing to do with netbios name resolution. Disabling firewall would work too, or opening the required ports for NetBios protocol.

If you are behind a router (and who isn't these days?) you don't need a built-in firewall. Unless you don't trust your router and/or ythe other computers inside your own LAN. But, if so, you have way more problems than netbios resolution :P

---

### Post by Champeau on 2012-09-01
I just wanted to confirm what worked for me.  I tried a whole slue of options.  I followed many guides . . . 

After a while I realized my problem was host name resolution.  I could get everywhere with the correct IP address, but never with the host name.  This only applied when I tried to connect to a Windows 7 network from my Ubuntu machine.  To fix this I added all the relevant IP address to /etc/hosts with their corresponding host name.  An example of how to do this was earlier in the thread. 

The other issue I was having was that my two Ubuntu machines were able to see my Windows machines, but not the other way around (except for the Windows 7 virtual machine, but I am not counting that one).  On my Windows machines I used the 'run' command and connected to my Ubuntu machines just fine by IP address.  This was suggested on tomshardware I believe.  In the run box, for example, one would connect by typing '//192.168.1.1' except you would put the IP you really want to connect to.  I decided to quit at this point . . . I could at least connect to all the computers.  Some day I will take another stab at it . . .

---

