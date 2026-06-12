---
title: "Any Howto's for an Ubuntu &quot;Back to my Mac&quot;"
date: 2008-05-22
forum: Security
---

### Post by WrathofthePenguin on 2008-05-22
I've done a little searching, but found nothing. I found the "Back to my Mac" story in which a woman used it to recover her laptop to be very interesting. While my laptop doesn't have a built-in webcam, there is data that would help immensely in an attempt to recover my laptop if it were stolen.

Simply sending the IP address assigned would be very helpful (LocatePC will do this, but it's Windows only), but with the nature of Ubuntu/Linux, we could certainly do much more.

Imagine if you received an email detailing the IP address, the results of a traceroute (to google or similar), and other bits of information. If a built-in webcam exists, some pictures. Randomly timed screenshots, etc. I'm sure people could come up with more.

Granted, not every thief is going to connect a laptop to the internet, so it wouldn't be foolproof, but it would certainly help.

---

### Post by vrangforestillinger on 2008-05-22
> **WrathofthePenguin said:**
> I've done a little searching, but found nothing. I found the "Back to my Mac" story in which a woman used it to recover her laptop to be very interesting. While my laptop doesn't have a built-in webcam, there is data that would help immensely in an attempt to recover my laptop if it were stolen.

For dynamic IP, check out [www.no-ip.com]("http://www.no-ip.com") or [www.dyndns.com]("http://www.dyndns.com"). Here you can aquire a domain name (e.g. yourcomputer.no-ip.com) that points to your computers current IP. They work by having a daemon on your computer reporting back the IP. Daemons for both these providers are availible in the repositries.

When you have your dynamic IP daemon working. You can install openssh-server availible in the repos. But first [COLOR="Red"]be shure to have strong passwords for all users as this will open a service on your computer that can be attacked.[/COLOR] I think you can disable ssh-login for some users if you want though, but they are all enabled by default.
```
sudo apt-get install openssh-server
```

Openssh-server will enable you to connect to your computer from anywhere where you have an ssh-client. F.ex. in a linux-terminal with openssh-client
```
ssh username@yourcomputer.no-ip.org
```
will grant you access to your shell with *username*.

From there, having ssh-access to your computer with yourcomputer.no-ip.com, there are many many possibilities. Download personal files with [_scp_]("http://www.google.no/search?hl=no&q=howto%20scp&meta="), delete or even shred sensitive information. And... catching the thieves on cam:
```
ssh -X -C username@yourcomputer.no-ip.org
cheese
```
The -C will compress the transfer, and -X will forward xserver connection so you can run programs on your computer and show the graphical output on the terminal you are sitting.

Cheese is a webcam toy that is included in the latest GNOME (which means it is in _U_buntu Hardy Heron). When you run this having enabled x-forwarding, the output will show up on the terminal you are sitting. The usability is limited by bandwidth. But I've tried to use cheese from 500km away on a 2MBit connection, and I got a nice view of my own flat. :)

Good luck!

---

