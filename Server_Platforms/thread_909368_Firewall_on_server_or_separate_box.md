---
title: "Firewall on server or separate box?"
date: 2008-09-03
forum: Server Platforms
---

### Post by kpatz on 2008-09-03
I know, topic title is a bit vague, here's the scoop.

I presently have a box running Hardy which serves the following on my home network:  firewall (iptables), email, DNS, DHCP, NTP, Apache, spam filtering, and probably a few other things I'm forgetting right now.  This is an old Dell Optiplex Pentium III system, which works fine for what it's doing (a bit underpowered for running the GUI and virus scanners for email), but I'm also planning on building a bigger development/file server.

The file server will have a RAID 5 array, probably 1-1.5 TB in size, and I'll put a fast enough CPU in it (dual core something most likely) to make compiling and debugging stuff go faster.  I hope to run virtualbox on this system as well, and maybe decommission my permanent Windows system eventually.

What I'm wondering, in the interest in saving some space and energy, if I should move the firewall box's functionality onto the file server box, or is it better to keep it separate, for security (especially if it's running virtual systems).

I may build a new firewall box as well, and make it a compact fanless system, possibly using a USB stick in place of a hard drive.  That way I don't have as many heat and noise generating machines running 24/7.

So, to sum it up, I could do any/all of the following:

1.  Build file/dev server box, keep firewall as-is.
2.  Build file/dev server box w/2 NICs and have it be the firewall/internet gateway as well.
3.  Build file/dev server box, and build new, compact, fanless, USB-drive-based firewall box (if I do this, I'll move email, spam filter, apache and mysql to the dev server box).
4.  Like #3 but keep the old Dell as firewall box, while moving higher-resource services to the file/dev server box.

Thoughts?

---

### Post by windependence on 2008-09-03
#2 is best, but better yet would be a good hardware firewall. Remember, all they have to do is overload the box with your firewall (DDOS ATTACK) and you go down without even being compromised. A single isolated box can take much more pounding than a box running all kinds of stuff. 

Take a look at pfsense. Small, compact, web interface, built on one of the most secure OSs on the planet.

-Tim

---

### Post by dannyboy1121 on 2008-09-03
Probably one for the security forums. It's your call but my gut feeling would be to keep your internal services (file / email etc) separate from your internet firewall. If the worst happens, at least they are an extra hop away hidden behind another password.

I've just gone through the process of building my own firewall and put smoothwall on it (just started blogging it - check out my blog link in the sig). The whole aim was to run it as a low power system. I've gone for the full hard drive because I wanted to use the squid web cache functionality. Plus .... building stuff is fun (unless you're my wife).

:guitar:

So .. option 3 ;)

---

### Post by kpatz on 2008-09-04
I had another thought, which leans toward keeping the firewall/email box separate.  One of the things I'm developing is a greylister/spam filter.  With separate boxes, I can keep my live email on the firewall box (where it is now) and have test email servers on the other, since I'll want to make sure my filter works on postfix, sendmail, exim, etc.

---

