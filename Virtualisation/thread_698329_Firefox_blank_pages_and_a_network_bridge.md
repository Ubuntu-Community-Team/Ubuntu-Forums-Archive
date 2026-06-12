---
title: "Firefox blank pages and a network bridge"
date: 2008-02-16
forum: Virtualisation
---

### Post by Levander on 2008-02-16
I'm running virtual box on Gutsy so that I can use an XP guest.  I've configured a network bridge so that I can use a static IP on both the Gutsy host and the XP guest.

Sometimes in Firefox on Gutsy, I'll pull up a well-known web site and Firefox will try to download the web page (you see little messages like "transferring...", "waiting..." in the Firefox status bar), but then it will only display a blank page in Firefox.

I'll try to hit Ctrl-F5 a bunch of times and I still just get a blank page.  I'll try again a few hours later and get the web site fine.

When I have this problem in Firefox on Gutsy, I switch to my XP guest and pull down the web site in Firefox on XP.  The site always comes down fine.

I don't know that it's related to the bridge, but I'm thinking it might be, so I asked here in the Virtualization forum where lots of other people are using network bridges.

Anybody know what the problem could be?

---

### Post by Levander on 2008-02-16
Never mind.  This last time I got it, it was because I was trying to pull up amule.org and not [www.amule.org](www.amule.org).  It does seem like I've been getting this fairly frequently, but I'll wait until I can reproduce it here in a true test case before I bump this thread next time.

---

### Post by Levander on 2008-02-17
Well, I just got it again.  I went to [http://mythbuntu.org](http://mythbuntu.org) and clicked on "Mythbuntu 8.04 Alpha 2 available for testing".  Then instead of the browser pulling up the page that text was linked to, it tried to pull up [http://www.mythbuntu.org](http://www.mythbuntu.org)  and just gave me a blank page.  I switched to XP running under KVM and it worked fine.  Switched back to Gutsy and then it worked fine.  It's like pulling it up under XP is clearing out some cache in the way my machine is networked with the bridge that's screwing me up.

And no, if you follow the instructions I've posted, I don't expect you to be able to re-create.  It's intermittent even here.

The problem is I have no idea where to look to fix this.

If someone could give me a hint, I would love it.

---

### Post by karyonix on 2008-02-19
How did you create your network bridge?   Please write your network configuration, /etc/network/interfaces or your script, so someone here may see what is wrong with it.

---

### Post by Zalbor on 2008-02-19
I don't use virtual box, but if it works similarly to what I know: Have you set a *different* static IP for the guest than for the host?

---

### Post by Levander on 2008-02-19
Oh, cool.  I had given up on anyone responding.  I set up my networking according to a HOWTO on virtualbox.org that doesn't appear to be online anymore - at least not for the last couple of days.  It was here, in case the URL looks similar to anyone:

[http://www.virtualbox.org/discussion/1/126](http://www.virtualbox.org/discussion/1/126)

The only changes were in /etc/network/interfaces.  This is the contents of that file now:

```

auto lo
iface lo inet loopback

iface eth0 inet manual
auto eth0
      
auto tap0
iface tap0 inet manual
      tunctl_user levander

auto bridge0
iface bridge0 inet static 
      address 192.168.0.63
      netmask 255.255.255.0
      broadcast 192.168.0.255
      gateway 192.168.0.1
      bridge-ports eth0 tap0 
      bridge-ageing 7200
      bridge-fd 0

```

The XP guest uses the tap0 interface and 192.168.0.64 as its static IP address.  But, I've used XP's services to configure that IP address.

Here's the output of 'ip addr' on the host:

```

1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:1d:7d:a2:77:6b brd ff:ff:ff:ff:ff:ff
    inet6 fe80::21d:7dff:fea2:776b/64 scope link 
       valid_lft forever preferred_lft forever
3: tap0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 500
    link/ether 00:ff:f3:79:f4:54 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::2ff:f3ff:fe79:f454/64 scope link 
       valid_lft forever preferred_lft forever
4: bridge0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc noqueue 
    link/ether 00:1d:7d:a2:77:6b brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.63/24 brd 192.168.0.255 scope global bridge0
    inet6 fe80::21d:7dff:fea2:776b/64 scope link 
       valid_lft forever preferred_lft forever

```

I've noticed mnior network flakiness in one app on XP too.  There's an app I use for work that when I start it up, it downloads some thumbnail images to use as buttons on an initial screen to let you select where to go.  I have to restart the application a couple of times because the first time or two, not all the thumbnails come down.

I'm definitely thinking there's something flaky with my networking.  Be it I configured it wrong or there just some little bug that's got me.

---

