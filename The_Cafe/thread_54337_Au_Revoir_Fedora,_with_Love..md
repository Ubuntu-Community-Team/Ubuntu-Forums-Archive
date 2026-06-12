---
title: "Au Revoir Fedora, with Love."
date: 2005-08-04
forum: The Cafe
---

### Post by andrew_t on 2005-08-04
I have just switched to Ubuntu after a friend  said he had downloaded a new linux distro and was going to give it a go. The main point is that it is very stable and has a very good support backing.

So I decided to steal his DVD and make a switch from Fedora.

An easy (although not graphical installation) without a hundred and one questions (some of which usually include do I like sliced bread?) the installation was complete and I was away to go! 

Unliked Redhat Fedora (which I love) it loaded straight away (no urgent update to actually let me login or load the desktop).

BUT THE BEST THING, a few friends have been using Muine (its a media player) and after 3 days off cross dependency issues and constant changes I gave up with Fedora . . . 

apt-get install muine 

. . . and in less than 10 minutes its working - so I would like to propose marriage to Ubuntu for I can now listen to my music with album covers and a really nifty interface.  I must say that so far it has been ever so easy to use and the install feature (which does not use YUM) has taken care of all dependencies on its own and updated everything without even a slight wimper.

I moved to Fedora just over a year ago and while it has been great, much more stable than Windows the latest release had a lot of compatibility issues with my system and SELinux kept closing applications and freezing the desktop interface while trying to do basic tasks (even after trying to disable SELinux) and that has led me to try UBUNTU. So far it gets a major  \\:D/ 

Sorry if this is the wrong section of the website but I couldn't find a welcome section or an opinion section. But I would like to say so far so good and the only disappointing aspect is, I don't think its going to turn down my proposal of marriage  :)

---

### Post by jasmuz on 2005-08-04
Hooray! We have a new convert! 
Welcome to the Ubuntu Lovers Club

---

### Post by charlieg on 2005-08-04
Intriguingly, Muine segfaults on me. :(

---

### Post by andrew_t on 2005-08-04
I just new it had to be to good to be true :(

I imported all my albums into muine, click play and it crashes :cry: 

Ok off to debug :

** Message: don't know how to handle application/x-id3

(muine:19903): libmuine-CRITICAL **: player_stop: assertion `IS_PLAYER (player)' failed

(muine:19903): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(muine:19903): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed


Well at least it loaded muine :) Hooorah! 

If worse comes to worse I can plug my head phones in and * pretend * to be 
listening to music  :-P

Yes it looks like a problem with mono and not Muine, which figures  :) 

All fixed . .  . well erm nearly I can play all songs except MP3 :)

Update

Just in case anybody has this problem in the future. I installed the latest version of Muine from the website from source file but it still displayed an error message when trying to play MP3's or crashed when I clicked the play button (Segmentation error). In my case it was missing the Gstreamer-0.8-plugins & Gstreamer-Mad (Synaptic installed from the Universe). Once I had installed these plugins and set sound to ASLA it plays all files and doesn't crash with the above error message. 

Ubuntu appears to be so much quicker than fedora as well. So far very impressed

---

