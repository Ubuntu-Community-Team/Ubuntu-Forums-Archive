---
title: "VirtualBox logs me out of ubuntu"
date: 2010-11-16
forum: Virtualisation
---

### Post by CuTop on 2010-11-16
I upgraded to 10.10.  When I did so my virtualbox developed an odd error that I cannot find through google searches.  

When I run virtualbox it comes up fine.  When I move my mouse to the form or if I start a virtual machine from the command line ubuntu logs me out. 

I am hoping there is a simple solution. 

Thank you for you any advise you can provide.

---

### Post by gamblor01 on 2010-12-03
Are you using dual monitors?  I just ran into this problem with my new computer at work and found your post here via google.  No solution...bummer.  Until now!

Every darn time I moused over the license agreement window, I got logged out of gnome.  I eventually wound up launching VirtualBox from the command line, and got some error like "the composite extension is not available".  When I googled that phrase it took me to this post:

[http://ubuntuforums.org/showthread.php?t=837819](http://ubuntuforums.org/showthread.php?t=837819)



Basically, it appears this problem occurs because Xinerama is enabled.  Edit your xorg.conf file (sudo vi /etc/X11/xorg.conf) and change the option for Xinerama from true to false.  For example, I commented it out of my file and then added a new line to set it to zero (or false) so my file now looks like this:

```

#    Option         "Xinerama" "1"
    Option         "Xinerama" "0"

```
Save the file, logout (which should kill your current X session), and then log back in.  Now you should be able to accept the agreement.  I have personally left Xinerama disabled but perhaps you could re-enable it after getting past the license agreement?  I really don't know.  I still have Twinview enabled and have my desktop spanning across two screens (and I can move windows between the two or spanning across the two) so I haven't really found a need for Xinerama yet.

---

