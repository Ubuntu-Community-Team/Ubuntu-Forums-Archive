---
title: "AD problem"
date: 2007-07-05
forum: Server Platforms
---

### Post by kdpo on 2007-07-05
Hi I'm new to the forum, hope someone could give share some ideas

I've installed Ubuntu Feisty 7.04 on a PC and have it authenticated successfully to the Windows Active Directory. 
Now AD users can now login to the Ubuntu desktop. I've used Samba + Kerberos + Winbind and some added configuration to PAM to make this happen. 

I configured a user from Windows AD to change the password on first time logon, then I tried to logon using my Ubuntu desktop, when I typed in my password it requires me to change my password, that means AD is working.
 
However it prompts me with this  error:

The change of the authentication token failed. Please contact the system administrator.

That leaves me to not having my password changed.
Could anyone help me on this. Any help would be greatly appreciated. Many Thanks and More Power. ;)

---

### Post by kdpo on 2007-07-08
Hi any help would be greatly appreciated?

---

### Post by The_night on 2007-12-06
I would very much like to know the same thing, I know this is an old thread, but I don't want to make a new one.  :lolflag:

---

### Post by HermanAB on 2007-12-06
Hmm, that is something I haven't encountered - yet...

Have a look at this guide, maybe it helps!
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

With MS ADS, *anything* can go wrong.  It is not a finite state machine, so there is little method in its madness.

Cheers,

Herman

---

