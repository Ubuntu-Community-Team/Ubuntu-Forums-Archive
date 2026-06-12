---
title: "avahi-daemon is giving me hard time"
date: 2024-08-07
forum: Server Platforms
---

### Post by kaynemo2 on 2024-08-07
Hi all!
I am running an Ubuntu Server 22.04 with a bunch of serices (ftp, nextcloud etc.). Among them is netatalk for MacOs machines on the network and time machine backup storage. As a part of netatalk setup I have avahi-daemon running, so that the machine would announce itself on the network with a hostname. Lately the avahi-daemon (albeit running) keeps throwing out this same error. I've browsed high and low, including ChatGPT and  I can't figure out what the problem is (the service IS running) and there is absolutely nothing in any logs except the same error over and over again. Maybe someone has ran in a problem like mine? I would greatly appreciate some help. Avahi-daemon is at it's latest version. The last thing that was modified - an upgrade to php - it is now php8.3.

This is what the error looks like:

```
sudo systemctl status avahi-daemon
&#9679; avahi-daemon.service - Avahi mDNS/DNS-SD Stack
     Loaded: loaded (/lib/systemd/system/avahi-daemon.service; enabled; vendor preset: enabled)
     Active: active (running) since Wed 2024-08-07 02:00:01 MSK; 11h ago
TriggeredBy: &#9679; avahi-daemon.socket
   Main PID: 30853 (avahi-daemon)
     Status: "avahi-daemon 0.8 starting up."
      Tasks: 2 (limit: 14076)
     Memory: 5.8M
        CPU: 39min 48.262s
     CGroup: /system.slice/avahi-daemon.service
             &#9500;&#9472;30853 "avahi-daemon: running [wookiee.local]"
             &#9492;&#9472;30854 "avahi-daemon: chroot helper"


Aug 07 13:26:48 wookiee avahi-daemon[30853]: avahi_normalize_name() failed.
Aug 07 13:26:48 wookiee avahi-daemon[30853]: avahi_key_new() failed.
Aug 07 13:31:59 wookiee avahi-daemon[30853]: avahi_normalize_name() failed.
Aug 07 13:31:59 wookiee avahi-daemon[30853]: avahi_key_new() failed.
Aug 07 13:31:59 wookiee avahi-daemon[30853]: avahi_normalize_name() failed.
Aug 07 13:31:59 wookiee avahi-daemon[30853]: avahi_key_new() failed.
Aug 07 13:53:54 wookiee avahi-daemon[30853]: avahi_normalize_name() failed.
Aug 07 13:53:54 wookiee avahi-daemon[30853]: avahi_key_new() failed.
Aug 07 13:53:54 wookiee avahi-daemon[30853]: avahi_normalize_name() failed.
Aug 07 13:53:54 wookiee avahi-daemon[30853]: avahi_key_new() failed.

```
Thanks

---

### Post by TheFu on 2024-08-07
Google found this: [https://askubuntu.com/questions/1249437/installing-avahi-daemon-on-ubuntu-server](https://askubuntu.com/questions/1249437/installing-avahi-daemon-on-ubuntu-server)
It says that the avahi config file is likely missing.  So, verify that your avahi config file exists and contains the minimum stuff specific to your machine to work. Any other working avahi client should have the config file you likely want - just change any IPs/hostname inside it, I'd guess.

<rant>
I consider Avahi an abomination and purge it from all my systems.  For the first few years it was out, it would eat all RAM, all CPU, then crash over and over and over.  OTOH, setting up a proper DNS on a LAN isn't that hard. That would be the preferred solution.  Many home routers can do this.  

Of course, you could manually manage /etc/hosts files across all your computers so they know about each other.  That's fine for servers and desktops, but less useful for laptops and doesn't work at all for phones and tablets because Apple and Android are setup only to trust DNS. They say it is for security, but if you run nextcloud on your LAN, you really need DNS for a number of reasons anyway.  

Of course, with DNS and servers, you need to make those systems have static IPs on your LAN.  I hard code those into each system because I've seen what terrible things can happen when DHCP fails. Best to just avoid that problem completely by manually setting static IPs.
</rant>

But I expect you'll want to use avahi, because when it works, it seems easier. Good luck with that.

---

### Post by kaynemo2 on 2024-08-07
Well... unfortunately or fortunately I do have that file and I've gone over it again and again with ChatGPT for good measure - i cannot find what is wrong with it.

---

### Post by TheFu on 2024-08-07
ChatGPT, and many AI tools, provide bad answers.  Best to stick with humans for advice, since all AIs seem to have "hallucinations" and make up answers far too often.

BTW, nobody should be using plain FTP since about 2002. There are better options.

I have a 22.04 system that has an avahi-daemon.conf file and is running avahi (guess I forgot to purge it?).

The non-commented lines are:
```
$ egrep -v '^#' /etc/avahi/avahi-daemon.conf
[server]
use-ipv4=yes
use-ipv6=yes
ratelimit-interval-usec=1000000
ratelimit-burst=1000

[wide-area]
enable-wide-area=yes

[publish]
publish-hinfo=no
publish-workstation=no

[reflector]

[rlimits]
```

And I'm able to ping my print server as hostname.local (also running avahi), so I guess it is working.  Don't know if this is helpful or not.

---

### Post by #&amp;thj^% on 2024-08-07
I also agree with TheFu on "ChatGPT, and many AI tools" seems we always have to fix or undo what it tells other users to use>
Have you looked at the config where it point to:
```
 less /etc/avahi/avahi-daemon.conf|grep disallow-other
#disallow-other-stacks=no

```
If it is truly there then try an edit to:
```
disallow-other-stacks=yes
```

This flag is apparently what now causes avahi to attempt to use SO_REUSEPORT (and turning it to yes disables this new behavior.) The docs indicate this is some mechanism to accomodate nasty setups with more than one mdns handler on them at the same time.

---

### Post by kaynemo2 on 2024-08-07
Hi! Thanks for all your support. 

This line was commented
```
disallow-other-stacks=yes
```

I uncommented it and tried with both values (yes and no)

But to no avail - after sometime the error still appears.

I, then, looked a little closer at the config file and found that a lot of information strings were also commented. I edited the most harmless ones (hostname, allow interfaces) and restarted it with disallow-other-stacks=yes....
Lo and behold - no more errors....
I will be monitoring the daemon for a while, but it seems like that was the fix!

Thank you all!

EDIT: Nope... spoke too soon. After a while (next morning) the error is back.

---

