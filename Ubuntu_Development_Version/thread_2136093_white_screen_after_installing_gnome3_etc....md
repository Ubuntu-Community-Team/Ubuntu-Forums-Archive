---
title: "white screen after installing gnome3 etc...?"
date: 2013-04-16
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2013-04-16
this is on a dv9000 laptop with nvidia go 6150

I then installed nvidia latest driver in software center.

I get the ubuntu icon list on the side and everything to the right is white.
Gnome3 login, everything is white, goto top left corner and you get some icons, etc...

So what should I do now?

---

### Post by mc4man on 2013-04-16
Try going to dconf-editor > org/gnome/desktop/background & disable show-desktop-icons
(if for some reason already disabled then enable/disable

---

### Post by sdowney717 on 2013-04-16
when enabled, entire screen is white
when disabled, entire screen is black
/
so what is normally used, white or black?

---

### Post by mc4man on 2013-04-16
> **sdowney717 said:**
> when enabled, entire screen is white
when disabled, entire screen is black
/
so what is normally used, white or black?
In a gnome session you should get the actual background with disabled, when enabled you get the Desktop folder (white
In a ubuntu session then white enabled, black disabled.

When you say "installing gnome3" if you mean the gnome3 ppa then did you run sudo apt-get dist-upgrade? 
(i believe most that use that ppa also add the staging ppa

---

### Post by sdowney717 on 2013-04-16
yes, i added a ppa and did dist upgrade etc...
from
[www.webupd8.org](www.webupd8.org)

sudo  add-apt-repository ppa:gnome3-team/gnome3

perhaps it just needs a backround image to show?

---

### Post by sdowney717 on 2013-04-16
well, it can either show desktop icons like newfolder and the entire screen white

or

it can show a background image and no icons at all

my desktop can do both icons and images so what is wrong?

---

### Post by mc4man on 2013-04-16
> **sdowney717 said:**
> well, it can either show desktop icons like newfolder and the entire screen white

or

it can show a background image and no icons at all

my desktop can do both icons and images so what is wrong?
gnome 3.8 no longer has any support for nautilus handling the Desktop, so it's no Desktop or  Desktop & problems



(to note - I believe the staging ppa is not longer getting any new stuff..

---

### Post by sdowney717 on 2013-04-16
so is there a solution, is gnome 3.8 too old. I dont really understand what you posted.

---

### Post by mc4man on 2013-04-16
> **sdowney717 said:**
> so is there a solution, is gnome 3.8 too old. I dont really understand what you posted.
Solution? - 
If you want to use unity then leave 'desktop icons' enabled & don't upgrade with the gnome3 ppa for best experience

If you want to use gnome-shell from the gnome3 ppa then disable 'desktop icons'

---

### Post by cariboo on 2013-04-17
I ran into a similar problem, and found that of the default backgrounds only blinds.jpg worked. Using other backgrounds from my Pictures and Wallpaper directories also work, so I really haven't chased the problem any further.

---

### Post by MattBergholm on 2013-04-22
I am running into the same EXACT issue.

I installed Gnome 3.8 from the following instructions:
[http://www.ubuntukiller.com/2013/03/how-to-installupgrade-gnome-38-in.html](http://www.ubuntukiller.com/2013/03/how-to-installupgrade-gnome-38-in.html)

I used it for a bit and didn't love Gnome so I logged back into Unity. Now when I enable "Show Desktop Icons" I get a white screen with no background image. When I disable it I get a back screen with no background image.

I have uninstalled and reinstalled LightDM. Deleted the config files and forced it to recreate them.
I uninstalled (purge and reinstall) the nVidia-313-updates
I have booted into XFCE and Unity and both have the same issue

I just want my Unity back!!! What the heck do I do now?

Thanks,
Matt

---

### Post by MattBergholm on 2013-04-22
I was able to fix my issue. I re-added the repository, then installed ppa-purge

Then I ran ```
sudo ppa-purge ppa:gnome3-team/gnome3
```

After that I just had to restart, run some updates, restart again, and I was back to normal. Seems I hadn't removed all the gnome3 stuff properly.

---

### Post by defconoii on 2013-04-24
> **MattBergholm said:**
> I was able to fix my issue. I re-added the repository, then installed ppa-purge

Then I ran ```
sudo ppa-purge ppa:gnome3-team/gnome3
```

After that I just had to restart, run some updates, restart again, and I was back to normal. Seems I hadn't removed all the gnome3 stuff properly.

I did exactly this, and it didnt fix the issue for me, any ideas?

---

### Post by MattBergholm on 2013-05-07
Do you have ppa-purge installed?

When you ran that command did it appear to be removing software?

Are you running Unity? I need more information about your system and I can help.

You may need to enable desktop icons again the the dconf-editor or from Unity Tweak Tool. Let me know...

---

