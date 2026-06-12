---
title: "[SOLVED] Firefox  can't access web pages on localhost with network cable unplugged"
date: 2008-07-16
forum: Security
---

### Post by KC_Ransom on 2008-07-16
Hello,
I'm new to the Ubuntu world. I am reviving an old Kayak XU desktop with a 450 MHz processor and 8 G SCSI drive (yes, it's old). To put less load on the box, I installed Xubuntu 8.04 since it has a lighter desktop. I plan to use this box to teach myself web development,
I installed LAMPP, and it worked immediately. I was able to browse to [http://localhost/xampp/index.php](http://localhost/xampp/index.php) with no problems. 
I ran a few sessions with no security set for mysql, ftp, etc.
Tonight I am having a problem, in that all of a sudden I can't browse to anything on localhost unless the network cable is plugged in. Firefox tells me it's in Offline mode. I sometimes plugged the LAN cable prior to this to browse out to the web, but with no problems accessing sites under my htdocs directory if it was unplugged.
Could this be a security problem? Did I get hacked? When the network cable was plugged into the box, I heard the hard drive start to grind away so I unplugged it.
Apache, mysql, etc are up and running when this occurs.
Can anyone help me? I'd like to avoid a complete re-install.

thanks,
KC:confused:

---

### Post by p_quarles on 2008-07-16
Doesn't sound like a security issue at all, just sounds like dbus telling Firefox to go into offline mode when you unplug the cable. Try manually setting it back to online. 

The fact that the hard drive grinds when and only when the ethernet cable is plugged in is strange. Can you confirm that this happens every time you plug it in?

---

### Post by KC_Ransom on 2008-07-16
The hard drive only ground away that one time. What is perplexing is that I was able to access localhost just a few days ago with the cable unplugged.
Any idea how to set Firefox to online mode manually? I tried in security.
Thanks.

---

### Post by p_quarles on 2008-07-16
It's the second to last line in the "File" dropdown menu.

---

### Post by KC_Ransom on 2008-07-16
Shame on me...I just found it right before checking the forum again. Sorry, it's getting late. I appreciate the help.
I unchecked the 'Work offline' box and localhost sites come up with the cable unplugged.
KChttp://ubuntuforums.org/images/smilies/icon_mad.gif
:mad:

---

