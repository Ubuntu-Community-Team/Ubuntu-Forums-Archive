---
title: "Windows equivalent of rdesktop?"
date: 2014-03-24
forum: Virtualisation
---

### Post by bigfamine on 2014-03-24
[COLOR=#333333][FONT=Verdana][FONT=Lucida Grande]Heya, So at work I use virtualbox too boot a linux ISO, then I connect to a VPN, then I launch rdesktop

The linux shortcut looks like this

"rdesktop -Z -f -a 8 <site address dot com>"

What software would I use to to connect to said address with the same properties (ie -Z -f -a [IMG]https://forums.virtualbox.org/images/smilies/icon_cool.gif[/IMG]

How would I connect to that from windows (i want to bypass virtualbox entirely

Thanks![/FONT]
[/FONT][/COLOR]
[BigFamine]("https://forums.virtualbox.org/memberlist.php?mode=viewprofile&u=84476") [COLOR=#000000]Posts:[/COLOR] 1[COLOR=#000000]Joined:[/COLOR] 24. Mar 2014, 15:39
[LIST]
[*]
[/LIST]
[RIGHT][COLOR=#536482][FONT=Verdana][/FONT][/COLOR][/RIGHT]

---

### Post by TheFu on 2014-04-03
So I looked up those options on rdesktop here - -Z and -a are not options in the default version shipped with 13.10, so I can't help there. There are -z and -A (seamless RDP and compression) options. Case matters.

"Remote Desktop" is the windows tool - don't know anymore about that.  I much prefer NX/FreeNX, but don't think it works on Windows. Sorry.

---

