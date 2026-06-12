---
title: "SSH Server: External IP Troubleshooting"
date: 2007-05-15
forum: Server Platforms
---

### Post by odelay on 2007-05-15
Hey all,

The last week I've been trying my hand at setting up an Ubuntu Server out of an old PowerMac I had lying around.  The original idea was just a local file server (Samba), but I quickly became interested in setting up a SSH server that I could access from both my LAN and external computers not on my network.  I ran the Feisty Server install with only DNS Server (not LAMP) checked.  I haven't had to enter any information related to this DNS server...and frankly, I don't really even know what one is.

_My Current Setup/Situation:_

* Feisty Server Install (DNS only); Hostname: "homeserver"
* Router = Netgear WGR 614 @ 192.168.0.1 ; External IP: ##.###.#.##
* In order to setup a static IP, I used my router's "Address Reservation" feature to assign a single IP to a single MAC address.  This does infact give each computer a "static" IP, but I don't know if it's identical to manually assigning static IP's on each computer.
* I edited my "/etc/hosts" to the following:
> 192.168.0.13    homeserver.cfl.rr.com   homeserver
* I have port 22/TCP forwarded to 192.168.0.13 on my router
* I have Default DMZ Server set to 192.168.0.13 on my router
* I have Dynamic DNS disabled on my router
* I have my router set as a "DHCP server"
* SSH working fine within LAN (local IP -> local IP)
* I CANNOT use "ssh username@ExternalIPAddress" from a LAN computer
* I currently don't have access an external IP (stuck at home for the summer)
* I'm trying to setup the server in one city but I'll be living in another nearby city

[U]My Aspirations:
[/U]
* Be able to add files to server via ssh (from external location)
* Eventually be able to access those files, read-only, from any computer via FTP
* Use VNC through SSH (externally)

_Confusion:_

* How do I check my external IP in Ubuntu?  I have a widget in OSX that tells me.
* Since I'm assuming my external IP changes each time my router is reset, and I'm not willing to pay for a static external IP...is there any way to fix this.  I'm utterly confused by what places like zoneedit.com or dynDNS.org do.
* Will I be able to specify an external hostname for SSH?  That is, instead of having to type "ssh username@ExternalIP I could type something like "ssh [email]username@homeserver.cfl.rr.com[/email]" from any computer to login to my computer.
* Will my current static IP setup (see above) cause problems?
* I have no clue what the DMZ Server option on the router really does (?!?)
* What is bind9 and do I need to install it?


My main focus in this post, however, is just dealing with SSH & an external IP.  I'm sort of in a Catch 22 though.  While I will mostly be using SSH from an external computer, I need to be able to test that it works now (from a LAN computer) before I leave.  This is a largely educational experience for me, so it really helps to be right by the server while messing around.

I know this post is loaded, so thanks for any feedback.  I've spent dozens of hours reading different posts...but I just keep getting inundated more and more terms/concepts that may or may not apply to my situation.  Thanks for your patience and help!

---

### Post by craigp84 on 2007-05-15
Hi Odelay,

> I CANNOT use "ssh server@ExternalIPAddress" from a LAN computer

Just to double check you're using the right command, it should look something like:

```
ssh craig@12.34.56.78
or
ssh 12.34.56.78   (if your username is the same on both boxes)
```

If you're getting no joy with that, you turn on verbose output by adding "-vvv" to the SSH command. This also works for launching the sshd process as well if you need it.

> In order to setup a static IP, I used my router's "Address Reservation" 
This is probably what you'd do in a larger network anyway. This is fine, even though the IP is dished out via DHCP, you have a proper static IP.

> I currently don't have access an external IP

If you are trying "ssh <external interface on the router>" from within the network, it probably wont work - the router wont be configured to forward packets from the internal interface with destination on the external interface (although it will happily route through the external to go to say google.co.uk).

You'd really need to test from outwith your network.

> Be able to add files to server via ssh

Easy, loads of solutions for this. scp and sftp are your friends, there are clients build into GNOME, KDE etc and are some available for download for windoze.

> Eventually be able to access those files, read-only, from any computer via FTP

Dead easy,

> Use VNC through SSH (externally)

No sweat.

> How do I check my external IP in Ubuntu

Well, you don't have one on Ubuntu by the sounds of it, you only have one on your router. Ubuntu can only tell you about what it physically knows of. But no worries, you can do it the same way the dashboard widget does - ask an external service: "hey, what IP do i appear to be coming from?".

Visit grc.com - do the shields up test. Not only will it tell you your external IP, it'll also show you whether your SSH is accessible from outside your router / firewall.

> Since I'm assuming my external IP changes each time my router is reset, and I'm not willing to pay for a static external IP...is there any way to fix this. I'm utterly confused by what places like zoneedit.com or dynDNS.org do.

Well, yeah, it's zoneedit or dyndns to solve this problem - they let you associate a domain name with a (frequently) changing IP address.

> Will I be able to specify an external hostname for SSH? That is, instead of having to type "ssh server@ExternalIP I could type something like "ssh [email]server@homeserver.cfl.rr.com[/email]" from any computer to login to my computer.

As above, it'd be ssh [email]user@my.home.domain.com[/email] - but yes, you can.

> Will my current static IP setup (see above) cause problems?

Na, i doubt it. Hundreds of thousands of businesses run with a similar config every day, you'll be fine! :-)

> I have no clue what the DMZ Server option on the router really does

Well it's a special "zone" where you're supposed to put your servers & external facing boxes. This means that there is an extra layer of protection between them and your internal network.

> What is bind9 and do I need to install it?

Its the worlds most popular DNS server software. But, you probably shouldn't install it here. When you need it, you'll clearly know about it. I'd just turn it off for now (sudo /etc/init.d/bind stop; sudo chmod -x /etc/init.d/bind).

Hope this helps,

Craig

---

### Post by dreamie on 2007-05-15
> **odelay said:**
> 
* In order to setup a static IP, I used my router's "Address Reservation" feature to assign a single IP to a single MAC address.  This does infact give each computer a "static" IP, but I don't know if it's identical to manually assigning static IP's on each computer.

- It's not the same thing, but doing what you do is fine. Leave the client's IP-choice to dynamic, and let the router choose what number goes where.

> **odelay said:**
> 
* I CANNOT use "ssh server@ExternalIPAddress" from a LAN computer

Probably a typo: ssh "username"@"hostname" (i.e. ssh odelay@68.202.3.152) or is server a user on the server?

> **odelay said:**
> 
* Be able to add files to server via ssh (from external location)
* Eventually be able to access those files, read-only, from any computer via FTP

- You probably need to add a SFTP server to be able to send and retrieve files. If it's ok with root access for the ftp-user I think there is a built in sftp-server that you only need to activate.
- If your client is windows based try WinSCP (else look for a SSH enabled ftp-client), that should do the trick.

> **odelay said:**
> 
* Use VNC through SSH (externally)

- No problem, you need to enable X11 forwarding in your ssh.conf / sshd_config files
- I'd look at NoMachine NX Server/Client which is a super tool for this! Fast and stable!

> **odelay said:**
> 
* I have Dynamic DNS disabled on my router
* Since I'm assuming my external IP changes each time my router is reset, and I'm not willing to pay for a static external IP...is there any way to fix this.  I'm utterly confused by what places like zoneedit.com or dynDNS.org do.
* Will I be able to specify an external hostname for SSH?  That is, instead of having to type "ssh server@ExternalIP I could type something like "ssh [email]server@homeserver.cfl.rr.com[/email]" from any computer to login to my computer.
* Will my current static IP setup (see above) cause problems?

- If you use dyndns.org you will be able to select a name from their list of available dns-names, which is then assigned to your IP. This means you will use something like: ssh [email]odelay@odelay.dyndns.org[/email]. The problem is that you will have to re-enter the IP into the dyndns.org database every 30 days or so (this applies to the free service), and I don't think you can use the automatic Dynamic DNS update setting in the router if you use the free service of dyndns.org (or zoneedit.com), but I could be wrong here.

Without a dynamic dns solution, you will have trouble connecting to your computer from your location in another city IF the IP changes. I had a similar problem, I solved it by sending a mail from the server including information about it's IP each time it started. Alternatively, it could send this information on a timely basis.

Most of the time the router will get the same IP even if it resets. I have the same configuration here and I don't have to change the dyndns ip more than a few times a year.

Hope this helps!

 / Peter

---

### Post by craigp84 on 2007-05-15
> Leave the client's IP-choice to dynamic, and let the router choose what number goes where.

No no no! Dynamic is no use here, we need static so we know where the forwarded port is to go.

> No problem, you need to enable X11 forwarding in your ssh.conf / sshd_config files

No. You'lll need to forward the VNC port (5901?), *not* X11 - you can build this into your SSH command: ssh -L 5901:127.0.0.1:5901 user@hostname, then vncviewer 127.0.0.1 will show the desktop on hostname.

Other than that, all good.

-c

---

### Post by markthecarp on 2007-05-15
> * I CANNOT use "ssh server@ExternalIPAddress" from a LAN computer

That will probably never work. You'll need to test from an external site.

**Think three times, no five times before posting your external IP to a public forum!!!!!**

It's working....
```

mark@smokey:/var/log$ ssh server@XX.XXX.X.XXXThe authenticity of host 'XX.XXX.X.XXX (XX.XXX.X.XXX)' can't be established.
RSA key fingerprint is 55:13:af:c4:fd:6c:00:ba:a1:36:4f:ff:17:5c:90:91.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'XX.XXX.X.XXX' (RSA) to the list of known hosts.
server@XX.XXX.X.XXX's password: 

```

Consider making your sshd listen on a non-standard port, say 2222. This should cut down on the attacks that will come.

I have pretty much the same setup you describe. My static local IP's were set at install time by the installer. Listening on port 22 I get a couple of attacks a day. This is from yesterday...

snip from /var/log/auth.log...
```

May 14 17:06:58 localhost sshd[28295]: Invalid user rdbackup from 65.98.40.84
May 14 17:06:58 localhost sshd[28297]: Invalid user boni from 65.98.40.84
May 14 17:06:59 localhost sshd[28299]: Invalid user backups from 65.98.40.84
May 14 17:06:59 localhost sshd[28301]: Invalid user fiedler from 65.98.40.84
May 14 17:07:00 localhost sshd[28303]: Invalid user domains from 65.98.40.84
May 14 17:07:00 localhost sshd[28306]: Invalid user adminftp from 65.98.40.84
May 14 17:07:01 localhost sshd[28308]: Invalid user cobaye from 65.98.40.84
May 14 17:07:01 localhost sshd[28312]: Invalid user jalil from 65.98.40.84
May 14 17:07:01 localhost sshd[28314]: Invalid user lonase from 65.98.40.84
May 14 17:07:02 localhost sshd[28316]: Invalid user totot from 65.98.40.84
May 14 17:07:02 localhost sshd[28318]: Invalid user userftp from 65.98.40.84
May 14 17:07:03 localhost sshd[28320]: Invalid user mustre from 65.98.40.84
May 14 17:07:03 localhost sshd[28322]: Invalid user cleis from 65.98.40.84
May 14 17:07:04 localhost sshd[28324]: Invalid user costa from 65.98.40.84
May 14 17:07:04 localhost sshd[28326]: Invalid user demo from 65.98.40.84
May 14 17:07:05 localhost sshd[28328]: Invalid user discover from 65.98.40.84

```

I'm switching to a non-standard port.

-mark

P.S. I'd change the user name on the server to something besides "server".

---

### Post by dreamie on 2007-05-15
> **craigp84 said:**
> 
No no no! Dynamic is no use here, we need static so we know where the forwarded port is to go.

Why? He clearly stated that he forced the IPs of the local machines using MAC-address binding. This way the server wil never get any other IP-address than the one specified in the router. If he wants to change this address in the future, there is only one place he needs to change it. Isn't this a better approach?


> **craigp84 said:**
> 
No. You'lll need to forward the VNC port (5901?), *not* X11 - you can build this into your SSH command: ssh -L 5901:127.0.0.1:5901 user@hostname, then vncviewer 127.0.0.1 will show the desktop on hostname.

Yeah, sorry about that... don't know where I got the impression you need X11 forwarding to view external desktops. I'm scratching my head at the moment wondering if I really need it enabled on my server... Anyway, I still think you should consider looking at NoMachine NX Server/Client, very fast and stable!

 / Peter

---

### Post by markthecarp on 2007-05-15
> 
Yeah, sorry about that... don't know where I got the impression you need X11 forwarding to view external desktops. I'm scratching my head at the moment wondering if I really need it enabled on my server... Anyway, I still think you should consider looking at NoMachine NX Server/Client, very fast and stable!


I like having it on. But I typically use it to start a terminal session on the remote system. Example:
```

mark@smokey:~$ ssh -X 192.168.1.102
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
d7:d5:21:90:f4:42:78:01:77:36:08:03:6b:60:8e:e4.
Please contact your system administrator.
Add correct host key in /home/mark/.ssh/known_hosts to get rid of this message.
Offending key in /home/mark/.ssh/known_hosts:5
RSA host key for 192.168.1.102 has changed and you have requested strict checking.
Host key verification failed.

mark@smokey:~$ vim /home/mark/.ssh/known_hosts 

mark@smokey:~$ ssh -X 192.168.1.102
The authenticity of host '192.168.1.102 (192.168.1.102)' can't be established.
RSA key fingerprint is d7:d5:21:90:f4:42:78:01:77:36:08:03:6b:60:8e:e4.
Are you sure you want to continue connecting (yes/no)? yes

Warning: Permanently added '192.168.1.102' (RSA) to the list of known hosts.
mark@192.168.1.102's password: 

Linux spinach 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Fri May 11 18:08:04 2007
mark@spinach:~$ xterm &
[1] 28328
mark@spinach:~$ 

```
Edited by adding blank lines to improve readability.

So now I've two terminals open connected to the same "remote" system. (remote is relative, the hosts are two feet apart). The first login probably failed due to the remote system having been rebooted since my last login. I used vim to comment out line 5. 

-mark

---

### Post by odelay on 2007-05-15
> **markthecarp said:**
> That will probably never work. You'll need to test from an external site.
OK...I think I had read that elsewhere, but I wasn't sure if there was no way around it.  I guess there isn't.
> It's working....
Good to know.  I really appreciate it!
> 
Consider making your sshd listen on a non-standard port, say 2222. This should cut down on the attacks that will come.

I was kind of thinking of doing this.  I know it's more of "security through obscurity", but since a lot of the more common brute force attacks are designed for port 22, I don't really see the harm.  Other than changing ssh to port 2222 and forwarding port 2222 on the router...is there any other settings I'll need to change?  I guess I'll need to open the firewall on my Mac (no firewall on the server), but I think that's it.

> Listening on port 22 I get a couple of attacks a day. This is from yesterday...
When you say "listening", do you just mean checking your /var/log/auth.log file?  Is this the primary way to keep track of people attempting to login?

> P.S. I'd change the user name on the server to something besides "server".
Is there a way to do this without reinstalling?

Wow...this is some *great* feedback from everyone!  I'm still sorting through some of it, but I really appreciate it, guys.

---

### Post by odelay on 2007-05-15
> **dreamie said:**
> - If you use dyndns.org you will be able to select a name from their list of available dns-names, which is then assigned to your IP. This means you will use something like: ssh [email]odelay@odelay.dyndns.org[/email]. The problem is that you will have to re-enter the IP into the dyndns.org database every 30 days or so (this applies to the free service), and I don't think you can use the automatic Dynamic DNS update setting in the router if you use the free service of dyndns.org (or zoneedit.com), but I could be wrong here.

OK...I used DynDNS.org to set up a hostname and my external IP.  So now it would appear I could type "ssh [email]my_username@my_selected_hostname.selfip.org[/email]".  Awesome!

DynDNS.org [linked to these 2 clients]("http://www.dyndns.com/support/clients/") (ddclient & inadyn) as far as making sure the hostname will go to my server, even if the router changes.  Is this all I need then?

OR

Do I want to try out my built-in router function?  In my router I can set up Dynamic DNS using dynDNS.org.  Basically, it says to go sign up for an account, then get a hostname.  In the router, I enter my hostname (servername.selfip.org), my account name (for dyndns.org), and my password.  There is no mention of using paid services or any catches.  I'm going to try this option first to avoid installing additional software.  The only problem, again, is not being able to test things from an extern IP (doh!).

Also of note, I have Fail2Ban installed.  I didn't really do much to set it up, but I think it's working.  Thanks again everyone!

---

### Post by odelay on 2007-05-15
Thanks again **markthecarp** for the PM.

From reading a bit more, it seems that using the DMZ Server option automatically forwards all ports needed to the server.  Since I only really want port 22 forwarded to the server, and I want to still be able to forward other ports to other, non-server computers on the LAN, should I disable the DMZ Server?

On a more general note, I seem to have a basic misunderstanding of the necessity of security on a home server.  Does the number of brute force attacks (or any other attacks) have anything to do with the relative obscurity of my little server?  I mean, I was thinking that no one would bother attacking it since it barely get's used.  Now I'm getting the impression that the majority of attacks are automated, and the targets aren't handpicked by an individual.  If that's the case, what exactly puts my server "on the map"?  Was it opening port 22?  If so, wouldn't opening, say port 59000 for a Bit Torrent make me just as much of a target?  Is it just the inherent capabilities of SSH that makes this difference?  Thanks!

---

### Post by MJN on 2007-05-16
I wouldn't recommend using the DMZ function of your router, particularly as you say it's only SSH that you need forwarding through (and no doubt some other explicit services at a later date). Runnning a DMZ blows a hole right through the inherent firewalling capabilities of your NAT router so unless you *need  *it (which you don't in the situation described) then there's no advantage to using it.

With regards to you being 'singled out' for SSH probing remember your IP is just a number at the end of the day and equally likely to be picked out from the 4-billion or so other addresses for random probing. With so many automated bots hunting around your chances are quite reasonable that you'll get picked on.

The reason they're knocking on SSH's door is because so many people's password are weak and hence dictionary attackes against SSH accounts can be quite effective. One they've got shell access to your machine they can they use it as a platform to launch attacks/spam to others, so it's not necessarily *your* data that they're after.

Incidentally, you mention not being able to access your internal SSH server using the external WAN address - unfortunately this is quite common on some routers however many (e.g. most D-Link's) do support it (often known as 'NAT loopback'). I don't think there's any correlation between quality/price and whether this feature is available, it seems more just one of those things that you either have or you don't.

Mathew

---

### Post by dreamie on 2007-05-16
> **odelay said:**
> 
Do I want to try out my built-in router function?  In my router I can set up Dynamic DNS using dynDNS.org.  Basically, it says to go sign up for an account, then get a hostname.  In the router, I enter my hostname (servername.selfip.org), my account name (for dyndns.org), and my password.  There is no mention of using paid services or any catches.  I'm going to try this option first to avoid installing additional software.  The only problem, again, is not being able to test things from an extern IP (doh!).

You could always insert you dyndns login information, and hit the "show status" button. If it signals all clear you should be alright! 
I am not sure why this doesn't work for me... I have the latest firmware of my Netgear FVL 328 and when I hit "show status" I get a "DNS query errror". The router is also not listed under DynDns's list of tested routers...

> **odelay said:**
> 
Also of note, I have Fail2Ban installed.  I didn't really do much to set it up, but I think it's working.  Thanks again everyone!
You could run the following command to see if there are any banned IP-addresses: 
> "sudo iptables -L"
At the end of the list there should be something called fail2ban chain, under it there could be some banned ips.

You could also run the following command to see how many failed logon attempts has been done (per date):
> zcat /var/log/auth.log* | grep 'Failed password' | grep sshd | awk '{print $1,$2}' | sort | uniq -c
or
> cat /var/log/auth.log | grep 'Failed password' | grep sshd | awk '{print $1,$2}' | sort | uniq -c

Aslo see this site for more info: 
[http://www.the-art-of-web.com/system/fail2ban-log/](http://www.the-art-of-web.com/system/fail2ban-log/)

> **odelay said:**
> 
Does the number of brute force attacks (or any other attacks) have anything to do with the relative obscurity of my little server? I mean, I was thinking that no one would bother attacking it since it barely get's used. Now I'm getting the impression that the majority of attacks are automated, and the targets aren't handpicked by an individual. If that's the case, what exactly puts my server "on the map"? Was it opening port 22? If so, wouldn't opening, say port 59000 for a Bit Torrent make me just as much of a target? Is it just the inherent capabilities of SSH that makes this difference? Thanks!
Your biggest "mistake" was problably to display the ip-number together with the user name of the server on a public forum. I believe most attacks are from bots, not handmade attacks. As you have opened a port, your server responds to a request on that port, this means the bot knows there is something behind this IP-address. If it also knows the username, he has made some great progress. Bots also scan ip-ranges for open ports so you are never really safe ;)

/ P

---

### Post by az on 2007-05-16
> **craigp84 said:**
> No no no! Dynamic is no use here, we need static so we know where the forwarded port is to go.

-c

You need a static IP on the outside (or a dynamic dns host on the outside) and your IP address on the inside should not change (either by a static IP your Ubuntu box uses when it connects to the router or address reservation through DHCP)

Since you don't have a static IP address, use dyndns.  If you connectoto your machine throught your dynamic dns host name, you will not get the warnings about REMOTE HOST IDENTIFICATION HAS CHANGED!,

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by odelay on 2007-05-16
Well since I'm already getting about a dozen attacks a day, I'm thinking of making a few changes:

* Change SSH password.  I have a pretty terrible password right now, and I need to change it.  Does anyone know of an easy way to change this?

* I disabled X11 forwarding.  Hopefully VNC will still work.

* Just to make my log file smaller, I might change the default SSH port.  One big question though...will I have to add a "-p ####" option each time I try to use ssh?  I'd say this inconvenience would be enough to deter me from doing that, but otherwise, I don't see the harm.

* Would it be worthwhile to change the username on my server to something...less obvious.  Would the security benefits outweigh the time it would take to change my username (I don't know how much work's involved)?

Thanks for all the tips!

---

### Post by dreamie on 2007-05-16
> **odelay said:**
> 
* I disabled X11 forwarding.  Hopefully VNC will still work.

This is not necessary. After reading some articles on this subject I found that it is a common misunderstanding that X11 on a server imposes a security threat (to the server). It's actually on the client side you have the security hole. A client connectig to a server which uses X11 to relay applications are vulnarble to the server. But as you are connecting to your own server this shouldn't be any problem. Anyway, if you are not using it there's no need to have it activated...

 / Peter

---

