---
title: "Locking no longer works."
date: 2007-10-19
forum: System76 Support
---

### Post by sail on 2007-10-19
I just finished updating to Gutsy on my Gazelle, but I've found that a feature is no longer functioning. Before, when I closed my laptop lid, if I opened it again I would have to enter my password. It was a minor inconvenience, but it's worth if for the extra security. How can I turn this feature back on?

---

### Post by tedrampart on 2007-10-19
edit- okay.. I think I found how to get it back 

run "gconf-editor" .. then under "apps > gnome-power-manager > lock" check the box that says "blank_screen". ..make sure its checked!

hopefully that works..

edit 2 - worked for me.. give it a shot!

-------

I believe they took that out by default for gutsy in general.. but I agree, I want it back!  its one of the reassuring features of linux on a laptop, you close the lid, and its locked..

I can't seem to find where I read that it was a new feature.. so maybe I dreamed it up.. in any case, I can't seem to find any info either on how to get it back..

---

### Post by octathlon on 2007-10-19
What do you have set to happen when you close the lid?  If you use any of the power management functions (Blank screen, suspend, or hibernate), it should lock for you.  But if it doesn't, you can turn locking on by running gconf-editor; under apps>gnome-power-manager, there are checkboxes for lock_on_blank_screen, lock_on_hibernate and lock_on_suspend.

---

### Post by sail on 2007-10-19
Thanks, it worked =)

---

### Post by tedrampart on 2007-10-19
Noice!!

---

### Post by AusIV4 on 2007-10-20
Thanks, I'd been trying to figure that out.

---

### Post by bucik85 on 2007-10-20
Thank you. :)

---

### Post by steveneddy on 2007-10-20
Why not go to 

System --> Preferences --> Power Management

to adjust your settings there?

:popcorn:

---

### Post by tedrampart on 2007-10-20
because its not in there.  setting it to blank screen doesn't help, if the gconf settings for blank screen don't include the lock part.  I checked a number of times, this is the only way I could get it to work.

---

### Post by steveneddy on 2007-10-20
> **tedrampart said:**
> because its not in there.  setting it to blank screen doesn't help, if the gconf settings for blank screen don't include the lock part.  I checked a number of times, this is the only way I could get it to work.

That's odd, because I noticed the same thing when I upgraded to Gutsy and this is how I changed the setting.

Maybe this is a bug and needs to be filed?

---

### Post by tedrampart on 2007-10-20
that is strange.. 

in your power settings, how exactly did you fix this?  was there a check box or something?

I've attached the screens of my power management settings, could you compare them to yours?  maybe some of us have something missing and a bug does need to be filed if thats the case..

if it is a bug, atleast there's a somewhat easy fix..

EDIT - I'm also posting a screenshot of gconf-editor settings for lock.. the arrow points to the box that needs to be checked, it was off after installing gutsy..

---

### Post by steveneddy on 2007-10-20
These are the same screen shots you showed me, but this is what i get when I shoose the option for lid closing.

I notice that your setting for laptop lid closed is blank screen.

I just set mine to suspend and it works very well.

I use this all the time at work every day, maybe 10 - 20 times a day, and just lock the screen with ctrl+alt+L

I you don't have these settings or they don't work for you, there may be a bug.

---

### Post by tedrampart on 2007-10-20
yea, I don't like setting mine to suspend.. I have a 5 hour battery, and when I'm at work, I just like to close the lid when I walk away, so blanking the screen is what I'm used to.  

I'll try to dig up where it was I saw that they took out the locking, I'm pretty sure it was intentional, so I won't file a bug for it.

thanks for the help though! :)

---

### Post by steveneddy on 2007-10-20
Couldn't you just ctrl+alt+L and lock it that way?

---

### Post by tedrampart on 2007-10-20
there is that option too.. but its easier for me (and I suspect others too) to have it lock when you close the lid, instead of hitting ctrl+alt+L before hand..

personal preference I suppose.. some people can't stand having to enter the password, which I guess is why the option is there to change it.  

there's also the applet to lock the screen, as well as the setting in the screensaver to lock when it turns on.

---

### Post by Mirko on 2007-10-21
> **tedrampart said:**
> there is that option too.. but its easier for me (and I suspect others too) to have it lock when you close the lid, instead of hitting ctrl+alt+L before hand..

Security-wise, this seems like kind of an obvious feature we need.

Is this a Gnome issue or an Ubuntu issue?

---

### Post by tedrampart on 2007-10-21
knew I read it somewhere.. found these...

[http://www.mail-archive.com/gutsy-changes@lists.ubuntu.com/msg09841.html](http://www.mail-archive.com/gutsy-changes@lists.ubuntu.com/msg09841.html)
[https://launchpad.net/ubuntu/+source/gnome-power-manager](https://launchpad.net/ubuntu/+source/gnome-power-manager)

---

### Post by Zxaos on 2007-10-21
Might be more useful to set use_screensaver_settings to checked instead - that way you can enable and disable the locking in the screensaver settings box - where you would have managed it before gutsy.

---

### Post by guttersnipe on 2007-12-04
I don't care that it was disabled by default (IMHO, it's better when computers don't automatically turn features on for you), but it was a bit difficult to re-enable.

Thanks for the info, I love the auto-lock on lid close feature :-D

---

