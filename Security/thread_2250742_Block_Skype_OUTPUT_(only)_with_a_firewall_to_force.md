---
title: "Block Skype OUTPUT (only) with a firewall to force proxy"
date: 2014-10-30
forum: Security
---

### Post by Totolanio on 2014-10-30
Hi,

Can someone give me a command for iptables or the procedure for UFW (i understand better iptables though lol weird) to block the outgoing packets from skype.
Skype can be forced to use a proxy by blocking the outgoing connections (in windows you can do some registry modification but I don't know how to do on linux). So I would like to know the exact process because I'm trying for hours and nothing works.


In fact, if I block EVERYTHING from the OUTPUT chain, and I try to connect to skype without tunneling by SSH to my server (which will act as a proxy) it doesn't work, but if I tunnel, then it works. So I would like to block only the skype output and really I don't get it.

Can someone help ?

PS : and if skype use only 80 and 443 ports, how can I force it to use another port and block it ? (for outgoing not incoming)

---

### Post by HermanAB on 2014-10-31
I've done this years ago.  Basically, run Skype with the 'sg' command to make it run with a specific group ID, then make an iptables rule to mark the packets with that group and finally, make a rule to filter the marked packets.

---

### Post by Totolanio on 2014-11-03
I'm not good enough with iptables as of yet :'(
If you have more informations it would be appreciated. Otherwise thank you for the procedure, i'll keep it in mind

---

### Post by HermanAB on 2014-11-04
OK, iptables changed a bit since I last dunnit but here is a possible way to do it.

Make a new group called skypegroup and check the ID is say 555

Launch skype with sg:
sg skype skypegroup

Add this rule to iptables:
iptables -I INPUT -m owner --gid-owner 555 -j DROP

Now skype will be cut off and will only be able to work through a tunnel.

---

### Post by Totolanio on 2014-11-06
I created a group and I put myself in it. When i use sg skypegroup skype it says :
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"

And when I use the iptables rule, it says this :
iptables: Invalid argument. Run `dmesg' for more information.

The "-m owner" should work from what i've seen, but maybe it's the --gid-owner (i tried -g but it doesnt work)
EDIT : i searched it looks like --gid-owner is the right way to go, but it doesn't work :(

But the idea seems great ! I think it's almost done :( I'll focus on this solution if you can't figure it out but if you find the solution in 3 min instead of 3 days for me, i'll be even even even more more grateful (and i already am)

---

### Post by HermanAB on 2014-11-07
It depends on the version of iptables.  Read the man page on your actual target machine.  Depending on the version, you may need to make two rules, one to mark the packets, the other to filter on the marks, instead of the above single rule.

---

### Post by Totolanio on 2014-11-12
If someone knows how to do this, i'll be glad because I checked the manpage and it's really not helping me.

---

