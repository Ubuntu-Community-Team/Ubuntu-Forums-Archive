---
title: "First upgrade of day - Adobe Flash AWOL"
date: 2012-05-31
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by VinDSL on 2012-05-31
Guess I'll go try a wash, rinse, and restyle.

Anyone else experience this problem, e.g. Flash disappearing:confused:

---

### Post by jerrylamos on 2012-05-31
Me too.  Flash deader than a doorknob.  I always try to have spare partitions - just remember, don't update them too.  Let me try re-insall....

Jerry

---

### Post by jppr on 2012-05-31
I think it is part of gcc 4.7 upgrade and new Firefox is also part of that problem...

[https://launchpad.net/ubuntu/quantal/+source/firefox/13.0~b6+build1-0ubuntu2]("https://launchpad.net/ubuntu/quantal/+source/firefox/13.0%7Eb6+build1-0ubuntu2")

e. youtube works me but nothing else flash not... strange

---

### Post by jerrylamos on 2012-05-31
Follow on from Flash killed with today's quantal updates.  Yes I did re-boot after the updates.

1.  Re-install Firefox.

2.  Re-install Flashplugin-installer.

Video s-l-o-w  a-n-d  j-e-r-k-y-.

3.  Reboot.  Video seems O.K.  I think.

Jerry

---

### Post by zika on 2012-05-31
> **jerrylamos said:**
> Yes I did re-boot after the updates.Why reboot? Isn't X-restart (in worst case) just enough? That practice reminds me of some other OS... ;)

---

### Post by VinDSL on 2012-05-31
> **jerrylamos said:**
> Follow on from Flash killed with today's quantal updates.  Yes I did re-boot after the updates.

1.  Re-install Firefox.

2.  Re-install Flashplugin-installer.

Video s-l-o-w  a-n-d  j-e-r-k-y-.

3.  Reboot.  Video seems O.K.  I think.

Jerry
I took a slightly different path.

I've been looking for an opportunity to test Lightspark in Gnash, thus...

[LIST=1]
[*]I purged Adobe Flash and installed Lightspark & Gnash -- couldn't get them to work either.

[*]Reinstalled Adobe Flash (but not the plugin) and everything is back to normal.
[/LIST]
I'm looking forward to some serious breakage with Alpha 1.  Maybe this was a harbinger.  ;)

---

### Post by jppr on 2012-05-31
Ha-haa, problem solved :popcorn:

[https://lists.ubuntu.com/archives/quantal-changes/2012-May/001876.html](https://lists.ubuntu.com/archives/quantal-changes/2012-May/001876.html)

---

### Post by VinDSL on 2012-05-31
> **jppr said:**
> Ha-haa, problem solved :popcorn:

[https://lists.ubuntu.com/archives/quantal-changes/2012-May/001876.html](https://lists.ubuntu.com/archives/quantal-changes/2012-May/001876.html)
Interesting!

---

### Post by jppr on 2012-05-31
> **VinDSL said:**
> Interesting!

... but works :) just did latest upgrade (firefox and totem) and now 
flash works fine.

---

### Post by jbicha on 2012-05-31
Yes, the Totem Vegas plugin is a "Flash killer".

Actually, it probably works well for some sites. Unfortunately it conflicts with the official Flash player and doesn't work for all sites. [A bit more info]("http://www.hadess.net/2011/12/vegas-baby.html").

---

### Post by VinDSL on 2012-05-31
> **jppr said:**
> ... but works :)
It's funny too...

After a while, you get a *gut feeling* for this sort of stuff, and my gut was telling me; it's a plugin issue.  Why?

First thing I did was look in these forums, to see if anyone else was having a problem with Flash.  Seeing nothing, I started this thread, then did some forensics.

Flash appeared be be installed, but my browsers weren't recognizing the SWF plugin.

In my rush to try Lightspark, that's about as far as I got into investing the problem -- Facebook was calling me -- and I needed to get Flash (any Flash) working. Adobe Flash won the toss...

Kinda sad how much we depend on an orphaned app, eh what?!?!?

---

### Post by jerrylamos on 2012-05-31
> **zika said:**
> Why reboot? Isn't X-restart (in worst case) just enough? That practice reminds me of some other OS... ;)

I haven't kept track.  Is it startx?  Or gdm restart?  Or service lxdm restart?  Or is it lxde? Or stop & start?  So I just used the "no think" method and rebooted.  

Jerry

---

### Post by jerrylamos on 2012-05-31
> **VinDSL said:**
> I'm looking forward to some serious breakage with Alpha 1.  Maybe this was a harbinger.  ;)
External monitor on my notebook "mirrors" the laptop on boot of live USB or of install.

Not really, the notebook is 1366x768 and the external monitor 1280x1024.

What I get is 1024x768.  Select System Settings, Displays and un-check mirror and boom.  Some complicated error.  Absolutely stuck on mirror and 1024x768.  That's a "regression", used to work, and still does on another partition oops don't update that until there's a fix, if ever.

Update:  Able to get going by using the notebook's keyboard disable of laptop display, and then Display seems to default to something usable on the external.  Still can't change anything on settings Display but quantal is up and running.

Apport and ubuntu-bug have been rather poor lately....

Jerry

---

### Post by zika on 2012-06-01
> **jppr said:**
> Ha-haa, problem solved :popcorn:

[https://lists.ubuntu.com/archives/quantal-changes/2012-May/001876.html](https://lists.ubuntu.com/archives/quantal-changes/2012-May/001876.html)Yes, that is noted for some time. Even I've alerted my LOCO about that... [http://forum.ubuntu-rs.org/Thread-64-bit-java-flash-i-script-za-brisanje-prethodnih-install-acija-flash-a?pid=198594#pid198594](http://forum.ubuntu-rs.org/Thread-64-bit-java-flash-i-script-za-brisanje-prethodnih-install-acija-flash-a?pid=198594#pid198594) ...

---

### Post by zika on 2012-06-01
> **jerrylamos said:**
> I haven't kept track.  Is it startx?  Or gdm restart?  Or service lxdm restart?  Or is it lxde? Or stop & start?  So I just used the "no think" method and rebooted.  

Jerry[img]http://www.sherv.net/cm/emo/laughing/smilie.gif[/img]

---

