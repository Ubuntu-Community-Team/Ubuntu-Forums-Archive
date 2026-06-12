---
title: "ufw and firewalls in general for simple end user"
date: 2016-09-22
forum: Security
---

### Post by Kris_M on 2016-09-22
I have a dual boot 16.04.1/win7 simple system behind a router connected to comcast.  GRC says I'm fine.  

Most of my time is spent on Ubuntu. I have FF, TBird, and a few old games runing on wine and dosbox. My only worry is from the outside.  I shut off upnp in the router.

If I enable UFW and don't add any configuration to it am I getting more protection with its default, ie could I connect computer straight to comcast modem?

---

### Post by TheFu on 2016-09-22
You should set some default block rules for ufw to be useful.
Yes, you **can** connect your system directly to the modem, but you shouldn't if there is a router available.  Having 2 levels of blocking means when (not if) you make a stupid mistake, at least 1 of those layers of protection will stop it.

If you don't run any services that "listen" no the network, then a firewall isn't strictly needed, but if you look at the firewall logs after a few days of use, even behind the router, you'll see different connection attempts that a router's firewall lets through.  

If you are really new to Linux, perhaps using **gufw** would be easier?

All programs that you've heard about for Linux firewalls are just different interfaces into the netfilter tables controlled by the kernel. It is best to pick 1 tool and stick with that to avoid confusion and prevent conflicts.

My advice is to use both a separate router with firewall enabled AND enable the linux kernel firewall.
If you have a smartphone and let it connect to wifi on the LAN, that is another attack vector against your Linux system (and all others).

---

### Post by Kris_M on 2016-09-22
> **TheFu said:**
> You should set some default block rules for ufw to be useful.
Yes, you **can** connect your system directly to the modem, but you shouldn't if there is a router available.  Having 2 levels of blocking means when (not if) you make a stupid mistake, at least 1 of those layers of protection will stop it.

If you don't run any services that "listen" no the network, then a firewall isn't strictly needed, but if you look at the firewall logs after a few days of use, even behind the router, you'll see different connection attempts that a router's firewall lets through.  

If you are really new to Linux, perhaps using **gufw** would be easier?

All programs that you've heard about for Linux firewalls are just different interfaces into the netfilter tables controlled by the kernel. It is best to pick 1 tool and stick with that to avoid confusion and prevent conflicts.

My advice is to use both a separate router with firewall enabled AND enable the linux kernel firewall.
If you have a smartphone and let it connect to wifi on the LAN, that is another attack vector against your Linux system (and all others).

Huge thanks!
My problem is I wouldn't know which rules to set.
Yes, I'm using gufw. Thanks.
I don't believe I have a service that listens to the network - FF and TBird just talk to it.
So maybe a good beginning would be to turn gufw on and leave Incoming as Deny and Outgoing as Allow, and check the log in a few days? Yes and stay behind the router for the moment.
Thanks again!

edit - yes to when, not if!
How about 2 routers...:mrgreen:

looking at  [URL="https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands"]https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands
     [https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-14-04)
[/URL]

---

### Post by ian-weisser on 2016-09-22
> **Kris_M said:**
> I don't believe I have a service that listens to the network - FF and TBird just talk to it

Finding out what services are listening for network connections is not at all difficult:
```
$ sudo netstat -tulpn | grep LISTEN
tcp        0      0 0.0.0.0:xxxx           0.0.0.0:*               LISTEN      4886/skype      
tcp        0      0 10.0.1.1:xx            0.0.0.0:*               LISTEN      3111/dnsmasq
```

I *want* connections on Skype. Never know when mom might call...
dnsmasq is running, but that's a different subnet, for talking among my VMs. Not on the router's subnet.
In other words, adding firewall rules would not provide any useful additional security from inbound attacks on this particular system.

Outbound-connecting applications can be audited the same way. Simply omit the 'grep LISTEN' filter.

Regularly auditing your port-listening and port-using applications in precisely this way is a good security habit.

---

### Post by Kris_M on 2016-09-22
```
$ sudo netstat -tulpn | grep LISTEN
[sudo] password for kris: 
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1316/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      846/cupsd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      846/cupsd
```

Thanks!
So what should I do?

---

### Post by ian-weisser on 2016-09-22
dnsmasq is included with Network Manager. It's for sharing your network connection on a subnet. Leave it alone.

cupsd is for sharing your printer. Do you want others to see/use your printer? If so, leave it alone. If not, disable printer-sharing in CUPS.

My recommendation: Do nothing. No useful vulns here.

---

### Post by Kris_M on 2016-09-22
Thanks. I unchecked shared in policies of both my printers and rebooted but cups is still there.  Academically, how would I shut printer-sharing off in cups?

also did this
```
$ sudo netstat -tulpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1295/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      919/cupsd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      919/cupsd       
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           856/avahi-daemon: r
udp        0      0 0.0.0.0:60114           0.0.0.0:*                           856/avahi-daemon: r
udp        0      0 127.0.1.1:53            0.0.0.0:*                           1295/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1285/dhclient   
udp6       0      0 :::5353                 :::*                                856/avahi-daemon: r
udp6       0      0 :::33433                :::*                                856/avahi-daemon: r

```

---

### Post by Kris_M on 2016-09-22
Okay, I'll bite.  Done a bunch of googling. Why do I need avahi-daemon? (simple end user with FF and TBird and some old games on wine and dosbox)

and apparently I can't kill it with 
  	 	 	 	   echo manual | sudo tee /etc/init/avahi-daemon.override

---

### Post by Kris_M on 2016-09-22
Okay, this says it for me: so, yes, I could briefly connect directly to the comcast modem if I had to, but of course I won't. Nice!!!!!!!!! skype installed and worked fine.
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
```
When you turn UFW on, it uses a default set of rules (profile) that  should be fine for the average home user. That's at least the goal of  the Ubuntu developers. In short, all 'incoming' is being denied, with  some exceptions to make things easier for home users. 
```

Still would like to know about the avahi-daemon thing...

---

### Post by cariboo on 2016-09-22
From:

[https://wiki.archlinux.org/index.php/avahi](https://wiki.archlinux.org/index.php/avahi)

> Avahi is a free Zero-configuration networking (zeroconf) implementation, including a system for multicast DNS/DNS-SD service discovery. It allows programs to publish and discover services and hosts running on a local network with no specific configuration. For example you can plug into a network and instantly find printers to print to, files to look at and people to talk to. It is licensed under the GNU Lesser General Public License (LGPL).

You can turn it off to see if it makes any difference using the following command in a terminal:

```
sudo systemctl stop avahi.service
```

to restart avahi:

```
sudo systemctl start avahi.service
```

---

### Post by Kris_M on 2016-09-23
Thanks!

---

### Post by TheFu on 2016-09-23
CUPs listens on the internal socket by default. That's the 127.x.x.x addresses. Outside systems can't get there.

Avahi can be a blessing or a curse, IMHO.  If you have other devices on your network - perhaps a video player, Kodi system, roku, smart-TV, BluRay player that you'd like to see this system, then avahi can make that easier. It advertises the IP address on the LAN for all systems that speak the same zeroconf protocol.  Access by using "hostname.local" .... a system here is named "hadar", so other systems can find it using "hadar.local" ..... except that I manage my network carefully and purge avahi from every system during my initial setup efforts.  This is habit these days because the avahi daemon wasn't always well-behaved.

If you have a laptop, the default ufw rules might not be sufficient.  It allowed the LAN addresses access to the system, which isn't sufficient when at a cafe or hotel. In those places, ALL inbound connections, even from the same subnet need to be blocked.  

Firewalls are just the start of Unix system security.  There are many other techniques - like running a browser and email client inside a separate container that can be helpful for the more paranoid types - or people who don't want to take chances when there is a way to have a little more protection. **firejail** is a tool to make this easy. That's just 1 thing, must be 50 others that are easy to do as well.

Be certain to look at the firewall logs ... a tool like **logwatch** can help with that.

You are asking a bunch of great questions.  Do you realize that your system already has most of the answers on it?  Inside the built-in manpages? Learning to use manpages is something every Linux user should know.

You joked about using 2 routers.  That is actually more common than you'd think.  I have 4 routers at home today, using all 4, to segment different subnets for different purposes.  I'm required to have a comcast-owned device due to having a subnet and multiple static IPs. I don't trust their equipment and treat it like a bridge, not a router.  There is a "guest" subnet, which is very close to the internet and outside my internet-facing "server" subnet. There is the kids/media/games subnet, for devices that are hard to control, but I can't trust.  Then there is the parent's subnet - which I like to believe is actually secure.  Some people would use vlans for this, but I don't consider vlan tagging anything more than a suggestion. It isn't "security" anymore than telling your neighbors not to look inside your windows is security.  It is impossible to know whether a device on a network will actually honor VLAN tags or not. Never trust the specs from any home network device maker. They lie, all the time. they have full of bugs and usually someone has figured out how to break out.  Multiple ways to block undesired network traffic is needed.   I worked with a client who was being attacked (the company had small DoD contracts). We setup port taps on their edge router and watched packets that were supposed to be blocked going right through. Somehow, the attacker had gotten someone inside (probably through a tainted webpage) to open the router port to their attack servers.  In the end, we got a different subnet under a different corporate name and started using that for the client-to-contractor stuff. Has been working for 5 yrs now. We swapped in 4 different firewalls - they all had the same issue. Got to monitor those logs guys.

> Marketing security is much easier than actually providing it. - anonymous

Lots of great advice in this thread.

---

### Post by steeldriver on 2016-09-23
> **TheFu said:**
> 
If you have a laptop, the default ufw rules might not be sufficient.  It allowed the LAN addresses access to the system


Sauce? I've ALWAYS had to add an explicit rule to allow ANY inbound connection

---

### Post by TheFu on 2016-09-23
> **steeldriver said:**
> Sauce? I've ALWAYS had to add an explicit rule to allow ANY inbound connection

I like marinara on chicken myself, but could be swayed to a peppercorn on a steak. 

Thought the OP was using gufw. I'm not behind a system with it now (and can't get to it - too many routers in the way ;)), but thought the "work" profile allowed inbound LAN access.  I've been wrong (multiple times). We all need to double check firewall rules anyway.

Came across this looking for an answer: [https://help.ubuntu.com/community/DoINeedAFirewall](https://help.ubuntu.com/community/DoINeedAFirewall)

I always add ssh as an inbound rule on all my systems, then install fail2ban to mitigate simple brute-force attacks if someone gets onto that LAN.  Only 2 systems allow external ssh and I watch those log files closely. The routers are setup to block most of the world from ssh access, unless I'm on travel. Got burned once.

---

### Post by steeldriver on 2016-09-23
Ahh OK thanks - I've never used GUFW, I wasn't aware it had additional rulesets beyond the 'allow out / deny in' UFW default

---

### Post by Kris_M on 2016-09-23
Okay! Tons of info here and huge thanks to all!

Yes, gufw allows additional rules but I understand that if you also manually add rules, it can't edit them with gufw - only the ones gufw adds.  I am/was a windows person so attracted to GUIs LOL.

Last night I decided I wasn't probably ever going to have this on a net so CZ'ed it and ran
sudo apt-get remove avahi-daemon

I feel that's sorta like shutting down netbios, which I always do.(and a few others)
Yes, I would suspect/imagine that keeping a net secure would be a constant job. Certainly not for me and my level of knowledge/experience at the moment, and no need for it.

Yes, marinara on chicken and pepercorn on steak, but about that logwatch...  ok did per this linkhttps://www.digitalocean.com/community/tutorials/how-to-install-and-use-logwatch-log-analyzer-and-reporter-on-a-vps```
sudo apt install aptitude sudo aptitude install -y logwatch
sudo gedit /usr/share/logwatch/default.conf/logwatch.conf
 
```
but I didn't know which to choose of (no config, internet site, internet w smarthost, satellite site, local only) so chose no config so tell me if I have to uninstall and reinstall.  I am using my gmail account. So need help here.

Also firejail looks interesting - I assume I could run FF in there if I'm paranoid.  I don't know if I am, but there is the rare time where links lead me to a bad site.  I rely on FF to catch it, and probably shouldn't.  On win I am used to having panda cloud AV running, but here I haven't fired up clamav.  I don't do anything risky like looking for keys, etc, but you never know.

With CZ I am set up to make me total disaster proof (or as much as possible) with both disk and partition image backups. (screwed up on this in 14.04!)  So now I am trying to make sure Ubuntu is as safe as I thought win7 was. So I can go back to sleep and live on Ubuntu forever.

I am lucky that the world of Ubuntu info is HUGE and I can google for anything.  

Okay on manpage - no, I didn't know about it so googled and installed the search engine plugin for FF and tried it with ufw and voila.  Thanks!

So first I need help making sure logwatch is set up right.  Thanks again all!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

edit:
 /etc/pastfix/main.cf now looks like this
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

myhostname = smtp.gmail.com
```

but running
```
logwatch --detail Low --mailto (my email addy) --service http --range today
```
yields nothing...

---

### Post by TheFu on 2016-09-23
Don't use **sudo gedit** .... er ... ever. It can cause bad things on newly installed systems by making config directories/files owned by root. There are multiple ways around those issues
* use sudo vi file <---- gedit doesn't work on remote servers anyway.  vi works on every platform I've eve used, including routers.
* run gedit once without sudo on the system to get all those directories/files created with YOUR useid, first.
* use **sudoedit** - right now, this is my preferred method for many, many, reasons. It is safer.
* use **sudo -H gedit** - this tells sudo to use the proper HOME directory, thus avoiding the config file ownership issues
* use gskudo <--- or whatever it is called. I've **never** used it.

Ok enough about that.
logwatch - I automated the install and config years ago. They are specific to my network and use an email server that I maintain. logwatch required a working MTA to work.  My systems all send email to this email server as and nowhere else.  Unix historically has used smtp as a way to notify admins of issues.  I'd never send anything as sensitive as system logs to gmail - just don't. 

I don't consider Window secure enough to allow on the internet. Too many issues and too many unpublicized issues remain.  AV is a complete boondoggle.  If you run 10 of them, only 85% of known virii are handled. That leaves 15% doing their will. 

ClamAV looks for Windows viruses. Meh. 

Don't know what CZ means.  Only use image backups for Windows. With linux, that is just too much wasted space and very hard to automate in a useful way.
All browsers are broken, IMHO. They've become a mess that cannot be fixed thanks to all the "features" added to help us all be tracked.  Did you know that CAs are notified if a browser sees a strange cert?  Lots and lots of other items have been added over the years that don't help end users.

Be careful googling for answers on Linux.  The vast majority of articles I've seen are either out of date (for older systems) or something a noob wrote because he thought he'd figured something out. Almost always, the 2nd set of articles is very flawed at worst and slightly flawed at best.  For example "sudo gedit" .... unintended repercussions because the person doesn't have sufficient understanding of all the other side-effects.  Linux security is very subtle.

FF manpages are mostly useless.  If you want to see the power of the manpage, look at ssh or bash or vim or openvpn .... Programs creates by/for Windows transferred people tend to have crappy manpages.  If you script, THOSE are the manpages.  Try **man -k perl** to get an idea.

logwatch - needs a working MTA. Until you can use **Mail -s foo [email]you@gmail.com[/email]**, forgetaboutit.  On comcast residential, you'll need to use their email gateway as a relay.  I've never used that. Can't help. Sorry.

---

### Post by Kris_M on 2016-09-23
okay, thanks.
This is way beyond anything I will ever need.
CZ is Clonezilla - I backup the linux partition and the entire disk and have used it many times to restore - saved my butt. I didn't when I was on 14.04 and lost everything.  So I just restored to before any playing with logwatch after failing to get it to create a simple file that i could look at when I want.  Yeah windows is insecure but on the other hand I've never had a virus. - been on win since 3.1 .  I never did pay attention to who was attacking me since I've been behind a router since forever.  okay so clamav is no good etc etc.  I remember when I was on 14.04 I installed sophos and ran that for a bit but it noticeably slowed things down so I got rid of it.  Guess for the moment I'll just run gufw in default mode.  better than nothing. Maybe if I'm bored I'll try sophos again though as you suggest it's doubtful it would actually protect me against anything since i think it's all windows viruses.  I would never use comcast's email for anything.  Someone somewhere suggested that this is all an exercise in futility for folks like me, anyway.

---

### Post by TheFu on 2016-09-23
There is no way to know if any Windows system has or doesn't have a virus. Some are hidden for years.  I suppose the same can be said for any OS.  I assume my android devices have been compromised.  Too many permissions allowed, no way to disable them selectively and too many ad networks who just don't care about security.

Thought sophos was an all-in-1 firewall distro.  Never used it myself.

You missed my point about using "comcast email relay." To send email out, if you are on comcast residential, then the MTA on your machine will need to send all email to a relay server managed by comcast. It will be blocked otherwise - they do this to prevent spamming.  Most email servers block DHCP subnets like comcast residential.  I do. There are probably threads here explaining how to setup postfix to send email to gmail. Think I've seen a few.

I think there is a way to manually run logwatch and look at the output too. Check the manpage.

Futility?  Only if you stop learning and give up.  It takes time to learn a new language. Same for Linux and linux security.

---

