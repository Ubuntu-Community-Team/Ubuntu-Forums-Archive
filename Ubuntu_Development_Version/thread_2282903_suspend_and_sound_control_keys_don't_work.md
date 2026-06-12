---
title: "suspend and sound control keys don't work"
date: 2015-06-17
forum: Ubuntu Development Version
---

### Post by sgage on 2015-06-17
The 'hardware controlling' keys on my keyboard no longer work - the suspend, vol up, vol down, and mute keys simply do nothing.

Also, there is no way to put the system into suspend mode from the power menu item - only restart and shut down. I can't seem to figure out a command line method to suspend my machine - can someone help me out?

TIA...

---

### Post by QDR06VV9 on 2015-06-17
What DE? OK I see **[COLOR=#5E2750][B]UbuntuGnome**[/COLOR][/B]

 Using Mate here and all is Good.
Have you tried?
```
sudo pm-suspend
```
Or more here [http://ubuntuforums.org/showthread.php?t=1978290](http://ubuntuforums.org/showthread.php?t=1978290)
Regards

---

### Post by sgage on 2015-06-17
pm-suspend gets the job done.

Thanks for the reminder...

But it would be nice to have those keys/buttons working...

---

### Post by QDR06VV9 on 2015-06-17
> **sgage said:**
> pm-suspend gets the job done.

Thanks for the reminder...

**But it would be nice to have those keys/buttons working..**.
Agree!
I think this still works.
**Enable Hibernate in System Tray Menu:**
 The indicator-session was updated to use logind instead of upower. Hibernate is disabled by default in both upower and logind.
 To re-enable hibernate, run the commands below one by one to edit the config file:
 ```
sudo -i

cd **/var/lib**/polkit-1/localauthority/50-local.d/

gedit com.ubuntu.enable-hibernate.pkla
```

More Here [http://ubuntuhandbook.org/index.php/2014/04/enable-hibernate-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/04/enable-hibernate-ubuntu-14-04/)
When Trusty was still in development I had to just remap the volume, pause, next, play Etc Etc but It has stuck to current Willey
Cheers

---

### Post by sgage on 2015-06-17
I'm talking here about suspend - I'm not so worried about hibernate. I use hibernate rarely enough that I'm happy to type 'pm-hibernate'. I do use suspend frequently, and it has always worked perfectly up until now. Ditto the sound keys. 

I look at the keyboard settings, and the sound functions are properly mapped to the appropriate key. I can even re-set them - the system recognizes those keypresses as the right keys. They just don't do anything.

Guess I'll go see if anyone has filed a bug report yet. I always have bad luck when I try to search the bug database, but I'll give it a try...

---

### Post by QDR06VV9 on 2015-06-17
OMG Did you ever stop to think, and forget to start again? he he he
I get wrapped up in my own stuff so bad forgive me, This is the link I meant to send in the first place.
As a temp fix.
[http://ubuntuforums.org/showthread.php?t=1978290](http://ubuntuforums.org/showthread.php?t=1978290) Post #4
But Yes A Bug should be filed or add yourself what ever the case maybe.

---

### Post by sgage on 2015-06-17
> **runrickus said:**
> OMG Did you ever stop to think, and forget to start again? he he he
I get wrapped up in my own stuff so bad forgive me, This is the link I meant to send in the first place.
As a temp fix.
[http://ubuntuforums.org/showthread.php?t=1978290](http://ubuntuforums.org/showthread.php?t=1978290) Post #4
But Yes A Bug should be filed or add yourself what ever the case maybe.

I take my line from Curly in the Three Stooges:

"I'm trying to think, but nothing's happening!"

:KS

---

### Post by cariboo on 2015-06-17
I've run into the same problem with the Gnome desktop. My volume keys don't work, and the system will only go into hibernate if I leave the screen open. Strangely enough, when using the Unity desktop, everything works as it should. I run both desktops on my laptop.

---

### Post by sgage on 2015-06-17
> **cariboo said:**
> I've run into the same problem with the Gnome desktop. My volume keys don't work, and the system will only go into hibernate if I leave the screen open. Strangely enough, when using the Unity desktop, everything works as it should. I run both desktops on my laptop.

Yes, it just seems to be a problem with the Gnome Shell key mapping - a bit of plumbing. If I type 'pm-suspend' it works fine, and the the volume control on the task bar works fine, so the underlying stuff is there. I'm sure it will get sorted...

---

### Post by muktupavels on 2015-06-18
If you are not using ppa to get newer GNOME programs then problem is gnome-settings-daemon. It is 3.14.2, but gnome-shell 3.16.2. Both must be 3.16.x...

---

### Post by sgage on 2015-06-18
> **albertsmuktupavels said:**
> If you are not using ppa to get newer GNOME programs then problem is gnome-settings-daemon. It is 3.14.2, but gnome-shell 3.16.2. Both must be 3.16.x...

No, I'm not using the ppa, just out-of-the-box Ubuntu Gnome. I assume you mean 'staging'?

---

### Post by QDR06VV9 on 2015-06-18
Yep Staging
> [h=3]Publishing details[/h]        
[LIST]
[*]
[*]       Published       on 2015-05-21
[/LIST]
      [h=3]Changelog[/h]         gnome-settings-daemon (3.16.2-0ubuntu1~vivid1) vivid; urgency=medium

  * New upstream release
  * d/p/revert-gsettings-removals.patch: Refreshed

 -- Tim Lunn <email address hidden>  Wed, 20 May 2015 10:38:58 +1000
It says Vivid but the same in wily

---

### Post by sgage on 2015-06-18
> **runrickus said:**
> Yep Staging

It says Vivid but the same in wily

Yep, that's all there was to it - I just needed the 3.16 Gnome Control Center. Everything is working fine now. Thanks for the pointers!

---

