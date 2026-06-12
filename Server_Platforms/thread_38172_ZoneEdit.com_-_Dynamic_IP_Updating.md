---
title: "ZoneEdit.com - Dynamic IP Updating"
date: 2005-05-30
forum: Server Platforms
---

### Post by BKonkle on 2005-05-30
Is there a linux dynamic IP updater that works with the zoneedit.com service?  I use Direct Update for Windows and I love it, but I'd rather move that process to my Ubuntu server so I can use Ubuntu on my desktop computer all the time instead of just occasionally.  Right now, I have to stay in the Windows desktop whenever I leave the computer to make sure it always updates my IP when it changes.

---

### Post by jiyuu0 on 2005-05-30
i'm not this might help... but i'm using dyndns

How to assign Hostname to local machine with dynamic IP using free DynDNS service?
[http://ubuntuguide.org/#assignhostnametodynamicip](http://ubuntuguide.org/#assignhostnametodynamicip)

---

### Post by BKonkle on 2005-05-30
Unfortunately it doesn't really help me, but I really appreciate the try!  From what I understand, ipcheck only works with dyndns.org.

Is there another way to get FREE dynamic DNS hosting, besides using zoneedit?  Dyndns charges for their DNS services. . . I'm hosting tonguesoffire.net and firstsamuel.net right out of my apartment. . .

Maybe I just need to see if I can pay my ISP extra for a static IP. . .

---

### Post by dmccarney on 2005-05-30
I use the Python ipcheck script as a cron-job that runs every half hour and it works great for me. As for Dyndns charging, they only charge for certain more advanced packages. I use dyndns and ipcheck to dynamically redirect xxxxxx.homelinux.com to myself. :) Very handy for when you need to SSH into your home box when its hosted on ADSL.

---

### Post by BKonkle on 2005-05-30
I'm actually wanting a DNS service that will point tonguesoffire.net and firstsamuel.net to my constantly changing IP address.  DynDNS actually charges $24.95 a month for it.  ZoneEdit gives you the first 3 free, and then any more after that are $10.00 a month. . . but I can't find any script to update it.  Anybody else have any other ideas?

---

### Post by jimcooncat on 2005-05-31
The following entry was copied from: [http://zoneedit.com/doc/dynamic.html?](http://zoneedit.com/doc/dynamic.html?) 

This works very slick, and takes minimal resources on your computer.

I've been using the wget method in a cron job, though I'm getting an error when it runs and my IP address hasn't changed. I'm sure redirecting the error output will fix it, I've just been too lazy lately to do the research yet.

> 
[INDENT]From one of our customers: It's very easy to update the dynamic zoneedit entries on UNIX with either of these two command lines (if you have wget or lynx installed):
```

lynx -source -auth=username:password 'http://dynamic.zoneedit.com/auth/dynamic.html?host=www.mydomain.com'
```
```

wget -O - --http-user=username --http-passwd=password 'http://dynamic.zoneedit.com/auth/dynamic.html?host=www.mydomain.com'
```

PPP users should place one of the above commands (or a perl client) in the file /etc/ppp/ip-up or /etc/ppp/ppp.linkup, which are called whenever a ppp connection is made.

Users of dhcpcd may place these commands in the file /etc/dhcpc/dhcpcd-eth0.exe or /etc/dhcpc/dhcpcd-eth1.exe which are executed whenever a new dynamic IP address is acquired. [/INDENT]

---

### Post by BKonkle on 2005-05-31
Oh, this is beautiful!  Thank you so much for finding this!  I was just looking in the wrong place, I should have been looking at zoneedit.com.

Thanks, I'll work on it and if I figure out how to get the error redirecting done I'll let you know!

---

### Post by sciurus on 2005-06-02
I'm a fan of ddclient; it supports dyndns, zoneedit, easydns, and hammernode.

---

### Post by jimcooncat on 2005-06-03
Sciurus's post got me thinking -- my cron job was running every five minutes, and didn't seem as I was being very nice to zoneedit.com to be asking to update when there was no change.

I abandoned it today in favor of ddclient, which I set up to get my external IP address from my router. Now it will only connect to zoneedit when it has an actual update to process.

ddclient was a bit of a bear to configure, but it's well worth it to avoid abusing a great free service.

---

### Post by KRavEN on 2005-06-03
[QUOTE=sciurus]I'm a fan of ddclient; it supports dyndns, zoneedit, easydns, and hammernode.[/QUOTE]


ddclient is probably the easiest solution by far for ubuntu.  When you install the package it runs you through a ncurses gui to configure everything and then sets everything up to start it on boot and poll your ppp interface or to just check for an ip change at a configurable time interval.  It supports all dynamic dns services including zoneedit.  It also supports multiple records per domain and multiple domains if you use zoneedit, just seperate them all by a comma in the config.  

If you ever have to reconfigure just do a dpkg-reconfigure ddclient.

---

### Post by BKonkle on 2005-06-06
You say it uses a GUI for configuration. . . I am running my Ubuntu server computer in purely terminal mode, no X installed at all.  Would I still be able to use ddclient?

(I'm at work right now, so I can't try installing it at the moment. . .)

---

### Post by jimcooncat on 2005-06-06
[QUOTE=BKonkle]You say it uses a GUI for configuration. . . I am running my Ubuntu server computer in purely terminal mode, no X installed at all.  Would I still be able to use ddclient?

(I'm at work right now, so I can't try installing it at the moment. . .)[/QUOTE]

It's not a GUI as you're thinking of, ncurses is a character-mode interface (same as the Ubuntu installer presents). No X required.

---

### Post by Metz on 2005-06-07
I'm trying to configure DDClient....can anyone help ??

I'm running though a linksys wireless router (WAG54G)....so how can I configure DDClient to pick up my external IP address from the router ?

Driving me mad !! :mad:

---

### Post by sciurus on 2005-06-07
[QUOTE=Metz]I'm trying to configure DDClient....can anyone help ??

I'm running though a linksys wireless router (WAG54G)....so how can I configure DDClient to pick up my external IP address from the router ?

Driving me mad !! :mad:[/QUOTE]
 You should be able to configure ddclient to use it, but probably the easiest thing to do is set use=web in /etc/ddclient.conf. This will get your external ip from checkip.dyndns.org. Any errors will be reported in syslog.

---

### Post by Metz on 2005-06-08
[QUOTE=sciurus]You should be able to configure ddclient to use it, but probably the easiest thing to do is set use=web in /etc/ddclient.conf. This will get your external ip from checkip.dyndns.org. Any errors will be reported in syslog.[/QUOTE]

Thanks :) Will try that tonight :)

---

