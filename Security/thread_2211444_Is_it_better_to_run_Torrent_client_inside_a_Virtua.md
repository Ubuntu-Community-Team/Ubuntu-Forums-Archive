---
title: "Is it better to run Torrent client inside a Virtual Machine ?"
date: 2014-03-16
forum: Security
---

### Post by linuxyogi on 2014-03-16
Hi,I use DSL router to connect to the internet.  All ports of the router are in stealth mode and ICMP is also blocked (I checked that at grc.com).Then there's ufw making all ports stealth on the OS side. Despite the router configured in stealth mode I see ufw blocking incoming connections when I do dmesg | tail which means the router's firewall is not all that effective.The number of attempts increases greatly when I am torrenting. I am bit concerned about this.So I was thinking should I run Transmission inside Virtualbox ?

---

### Post by Lars Noodén on 2014-03-16
VirtualBox will only add another few pieces to possibly break or get in the way.  If you want to contain your bittorrent software probably the best way would be to make an [apparmor profile](https://wiki.ubuntu.com/AppArmor) for it and lock it down that way.    That's what apparmor is good at.  

About 'stealth' mode, there is really no such thing.  Other machines can still scan your machine and find out just as much, if not more, than if in normal operation.  

[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)
[http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)

For *known* malicious traffic, there is always [tarpit](http://www.netfilter.org/projects/patch-o-matic/pom-external.html#pom-external-TARPIT), if you want to go that route.  For everything else, reject is a smoother option.

I'm not sure how much torrents specifically need ICMP but in general not responding to ICMP means that your corner of the net is a little broken.

Again, take a look at apparmor.

---

### Post by linuxyogi on 2014-03-17
@Lars Noodén 

Read your links. On the router I can either enable or disable the firewall. Enabling the firewall makes it to drop the packets. So there's nothing much I can do about it.

Same thing with Ubuntu. I have tested and found that with ufw disabled Ubuntu rejects all packets. Once enabled it drops them.

I will look into tarpit.

I am looking for some good apparmor profiles but I cant find any and if am not wrong profile for a particular app differ from distro to didtro.ATM I am using Xubuntu 12.04 and openSUSE 13.1. Some years back I tried to learn about apparmor like how to create profiles etc. Frankly apparmor is out of my range. If I am able to find profiles I will implement them.

Thanks

---

### Post by Lars Noodén on 2014-03-17
> **linuxyogi said:**
> I am looking for some good apparmor profiles but I cant find any and if am not wrong profile for a particular app differ from distro to didtro.s

Here's what I got for Ubuntu 14.04 beta.  It probably works for 12.04.  Check step 3 below to be sure.

```

#include <tunables/global>

/usr/bin/transmission-gtk {
  #include <abstractions/base>
  #include <abstractions/gnome>
  #include <abstractions/lightdm>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  network inet stream,
  network inet6 stream,

  owner /.Trash-*/ w,

  owner @{HOME}/.Xauthority r,
  owner @{HOME}/.cache/transmission/ w,
  owner @{HOME}/.cache/transmission/** rw,
  owner @{HOME}/.config/dconf/user r,
  owner @{HOME}/.config/gtk-3.0/bookmarks r,
  owner @{HOME}/.config/transmission/ w,
  owner @{HOME}/.config/transmission/** rw,
  owner @{HOME}/.config/user-dirs.dirs r,
  owner @{HOME}/.local/share/Trash/files/* w,
  owner @{HOME}/.local/share/Trash/info/* rw,
  owner @{HOME}/.local/share/applications/ r,
  owner @{HOME}/.local/share/applications/mimeapps.list r,
  owner @{HOME}/.local/share/applications/mimeinfo.cache r,
  owner @{HOME}/.local/share/gvfs-metadata/home r,
  owner @{HOME}/.local/share/gvfs-metadata/home-*.log r,
  owner @{HOME}/.local/share/gvfs-metadata/root r,
  owner @{HOME}/.local/share/gvfs-metadata/root-*.log r,
  owner @{HOME}/.local/share/mime/mime.cache r,
  owner @{HOME}/.local/share/recently-used.xbel rw,
  owner @{HOME}/.local/share/recently-used.xbel.* rw,
  owner @{HOME}/Downloads/** rw,

  @{PROC}/*/fd/ r,
  @{PROC}/*/mountinfo r,
  @{PROC}/[0-9]*/net/dev r,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/wireless r,
  @{PROC}/net/ipv6_route r,
  @{PROC}/net/route r,
  @{PROC}/sys/kernel/random/uuid r,

}

```

It's the first profile I've tried making so it is likely to be imperfect.

Here's how I got it.  

1) Generating an initial profile takes three steps.

1a) start up aa-genprof

```

sudo aa-genprof /usr/bin/transmission-gtk

```

1b) Then I wiped all configurations for Transmission and started it up and ran it through all the actions I could think of:

```

/usr/bin/transmission-gtk

```


2) Initial refinement of the profile takes several steps.  Repeat until "done"  with globbing and consolidation.  

2a) Edit the rules manually, globbing where possible.  See the manual page for apparmor.d   Add in 'includes' as needed, they can be found in  /etc/apparmor.d/abstractions/ and  /etc/apparmor.d/tunables/

```

sudo nano -w /etc/apparmor.d/usr.bin.transmission-gtk

```  

2b) Set apparmor to test the rules

```

sudo aa-complain /usr/bin/transmission-gtk 

```

2c) Run transmission through its paces again.

```

/usr/bin/transmission-gtk

```

2d) Add any exceptions

```

sudo aa-logprof

```


3) Final refinements.  Repeat until done.

3a) Edit in rule qualifiers like 'owner' and variables like @{HOME} and @{PROC}

3b) Load apparmor in enforcing mode.  Needs to be done each time the profile is changed.

```

sudo aa-enforce  /usr/bin/transmission-gtk

```

3c) Watch the logs for problems and while that is running, put Transmission through its paces.

```

sudo tail -f /var/log/kern.log | grep apparmor

```

---

### Post by bashiergui on 2014-03-18
> **linuxyogi said:**
> Hi,I use DSL router to connect to the internet.  All ports of the router are in stealth mode and ICMP is also blocked (I checked that at grc.com).Then there's ufw making all ports stealth on the OS side. Despite the router configured in stealth mode I see ufw blocking incoming connections when I do dmesg | tail which means the router's firewall is not all that effective.The number of attempts increases greatly when I am torrenting. I am bit concerned about this.So I was thinking should I run Transmission inside Virtualbox ?
I agree that apparmor is a good way to go.

I encourage you to take the time to understand what UFW is blocking. Make sure it's not just your router doing its job and chatting with devices on your network.

When you use torrents, the idea is you can download something from multiple locations. You will also seed other downloads with the copies you have previously torrented. That means you'll see inbound and outbound traffic when you start torrenting. Sounds like you've got your firewall rules blocking some torrenting traffic, so you may want to work out what's really getting blocked. Ideally the firewall will let all the torrenting through.

A firewall is important but not the only step in security. Your instinct to look for additional security is good. However running torrent inside of a VM won't get you there. Apparmor is a good idea although the learning curve is steep. Another excellent defense is to avoid torrenting anything that's a free version of something that usually costs money. They tend to contain malware (aside from being illegal and all that). If you're not running any services that you have port forwarded through the router, then you probably don't need to do much more than that.

---

### Post by ant2ne on 2014-03-18
The advantage of torrenting with a VM is that if something malicious came in with your torrent you could resent the VM to a previous snapshot. Of course you'd have to copy what you torrented off of the VM each time to another location you would store them. And if you copied the bad program then your reason for using the VM would become irrelevant.

---

### Post by linuxyogi on 2014-03-18
[COLOR=#DD4814][COLOR=#000000]@[bashiergui]("http://ubuntuforums.org/member.php?u=1879546") / [/COLOR][/COLOR][Lars Noodén]("http://ubuntuforums.org/member.php?u=168643")[COLOR=#000000] : I am having a tough time with apparmor. Problem is Chromium is on Xubuntu but Transmission is installed under openSUSE. I tried copying your(Nooden) profile and putting it in enforce mode but Transmission wont start. The I tried generating a fresh profile, putting it in complain mode, used aa-logprof to allow or deny. I was almost done. My main aim here is to restrict Transmission's rw access to /home/*Downloads. 

During the aa-logprof analysis I denied access to /home/user/ which resulted in deny /home/username/ 

But I allowed access to /home/username/Downloads.

But problem was Transmission failed to access the Downloads folder despite the permission present in the profile.

I was struggling with for hours. Feeling really stressed [/COLOR]:shock:


> [COLOR=#000000]The advantage of torrenting with a VM is that if something malicious came in with your torrent you could resent the VM to a previous snapshot. Of course you'd have to copy what you torrented off of the VM each time to another location you would store them. And if you copied the bad program then your reason for using the VM would become irrelevant.[/COLOR]

I never download any software using torrent other than distros and I get the link (.torrent) for those from the distro's official page. 

[COLOR=#000000]


[/COLOR]

---

### Post by Lars Noodén on 2014-03-18
I've tested the profile on 14.04 beta in all the ways that I can think of and it seems to work.  As it is it restricts access to the Downloads directory in the user's own home directory.  But I can't imagine that it would work on other distros than Ubuntu.  OpenSuse has things in different locations and might not have /etc/apparmor.d/abstractions/ and tunables/ which the profile relies on.  The helper applications might even be different.  I do find apparmor a bit hard to work with.

---

### Post by ant2ne on 2014-03-18
> **linuxyogi said:**
> [COLOR=#DD4814]
I never download any software using torrent other than distros and I get the link (.torrent) for those from the distro's official page. 
Then what is it exactly you are trying to accomplish with the VM?

---

### Post by linuxyogi on 2014-03-19
> **ant2ne said:**
> Then what is it exactly you are trying to accomplish with the VM?

Try downloading something like distro using torrent and while download is in progress check ufw logs or just do dmesg | tail. You will find incoming connections from multiple sources trying to connect to  your ip.

---

### Post by Lars Noodén on 2014-03-19
Yes, that is normal.  Part of torrenting is seeding and when you do that other machines connect to your machine to download pieces of the file.  So seeing connections on the port you are using for torrents is quite normal.  

What version of Ubuntu are you running this on?

---

### Post by linuxyogi on 2014-03-19
> **Lars Noodén said:**
> Yes, that is normal. Part of torrenting is seeding and when you do that other machines connect to your machine to download pieces of the file. So seeing connections on the port you are using for torrents is quite normal. 

The fact is I find both Ubuntu and openSUSE blocking incoming connections **even when I am not torrenting**. I get to know this by reading the firewall logs. 

As you said its normal for the number of incoming connections to increase while torrenting. I see that too.

I am planning to assemble a low spec machine and install PFsense. I guess having a dedicated firewall is logical. 


> **Lars Noodén said:**
>  What version of Ubuntu are you running this on?

I use Transmission under both Xubuntu 12.04 and openSUSE 13.1.

---

### Post by Lars Noodén on 2014-03-19
Ok.  I've tried an apparmor profile on Xubuntu 12.04.04 and the above profile needed some modifications.  Here it is for 12.04.04.  I see no 'DENIED' entries in kern.log when I run it for /usr/bin/transmission-gtk.  YMMV.  

```

#include <tunables/global>

/usr/bin/transmission-gtk {
  #include <abstractions/base>
  #include <abstractions/gnome>
  #include <abstractions/lightdm>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  network inet stream,
  network inet6 stream,

  owner /.Trash-*/ w,

  owner @{HOME}/.Xauthority r,
  owner @{HOME}/.cache/dconf/user rw,
  owner @{HOME}/.cache/transmission/ w,
  owner @{HOME}/.cache/transmission/** rw,
  owner @{HOME}/.config/dconf/user r,
  owner @{HOME}/.config/gtk-3.0/bookmarks r,
  owner @{HOME}/.config/ibus/bus/ rw,
  owner @{HOME}/.config/ibus/bus/** rw,
  owner @{HOME}/.config/transmission/ w,
  owner @{HOME}/.config/transmission/** rw,
  owner @{HOME}/.config/user-dirs.dirs r,
  owner @{HOME}/.local/share/Trash/files/* w,
  owner @{HOME}/.local/share/Trash/info/* rw,
  owner @{HOME}/.local/share/applications/ r,
  owner @{HOME}/.local/share/applications/mimeapps.list r,
  owner @{HOME}/.local/share/applications/mimeinfo.cache r,
  owner @{HOME}/.local/share/gvfs-metadata/home r,
  owner @{HOME}/.local/share/gvfs-metadata/home-*.log r,
  owner @{HOME}/.local/share/gvfs-metadata/root r,
  owner @{HOME}/.local/share/gvfs-metadata/root-*.log r,
  owner @{HOME}/.local/share/mime/mime.cache r,
  owner @{HOME}/.local/share/recently-used.xbel rw,
  owner @{HOME}/.local/share/recently-used.xbel.* rw,
  owner @{HOME}/Downloads/ rw,
  owner @{HOME}/Downloads/** rw,

  /tmp/.X[0-9]*-lock r,

  @{PROC}/*/fd/ r,
  @{PROC}/*/mountinfo r,
  @{PROC}/[0-9]*/net/dev r,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/wireless r,
  @{PROC}/net/ipv6_route r,
  @{PROC}/net/route r,
  @{PROC}/sys/kernel/random/uuid r,

}

```

As far as the incoming connections go, that is part of being on the net.  If you are on the net, you are being scanned.  If you have ports open, they are probed.  pfsense should be pretty good, certainly PF is nice to work with.

---

### Post by linuxyogi on 2014-03-19
@[Lars Noodén]("http://ubuntuforums.org/member.php?u=168643")

The profile works. Thanks a lot. :D

---

### Post by ant2ne on 2014-03-19
Thinking maybe you miss the difference to torrenting and regular downloading..

---

