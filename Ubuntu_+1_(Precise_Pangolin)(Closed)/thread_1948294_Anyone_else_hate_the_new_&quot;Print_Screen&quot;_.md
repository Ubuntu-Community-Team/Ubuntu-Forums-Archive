---
title: "Anyone else hate the new &quot;Print Screen&quot; changes?"
date: 2012-03-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dcstar on 2012-03-28
[https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/927952](https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/927952)

Just wasted heaps of time trying to do a screen capture to use in another bug report.

---

### Post by meborc on 2012-03-28
it is working fine for me. Just PrintScreen gives me the screeshot with both monitors and Alt+PrintScreen gives me the main monitor. 

had to use scrot to get the screenshot of the screenshot window though :)

---

### Post by dino99 on 2012-03-28
never been happy with this setting :(

some devs may have swallow some dangerous mushroom :(

---

### Post by winh8r on 2012-03-28
> Thanks, that need consideration but that's neither a regression not an important bug, the new behaviour is what new devices out there like phones or tablets do


Sorry, it's our fault for not having smartphones and tablets and underestanding this behaviour. 

 Problem solved then!

---

### Post by dcstar on 2012-03-28
> **winh8r said:**
> Sorry, it's our fault for not having smartphones and tablets and underestanding this behaviour. 

 Problem solved then!

Yeah, no doubt EVERYONE now has a system with working sound so that this change gives them some feedback when they use it.

The worst thing any programmer can do is separate an action done in in one medium (visual) from the feedback which is provided in another medium (sound).

This change breaks this basic rule on the arrogant assumption that all Ubuntu users will have audible sound to let them know that the action of pressing the Print Screen key actually does something. At the very least a message should flash up for a short time to let people know the capture has been done.

I am old enough to remember when doing something so bone-headed would almost get an immediate fail in any software development course.

---

### Post by winh8r on 2012-03-28
Never mind working sound, what happens if you are DEAF !!!!

Hardly meets accessibility criteria.

---

### Post by dcstar on 2012-03-28
> **winh8r said:**
> Never mind working sound, what happens if you are DEAF !!!!

Hardly meets accessibility criteria.

Good point - if this escalates further we can probably put together a lynch mob!

---

### Post by Grenage on 2012-03-28
Good news on this front:

> Mark Shuttleworth (sabdfl) wrote 31 minutes ago: 	#43

This is a regression, clear guidance was given to have the screenshot
dialog show on PrintScreen.

Mark

---

### Post by dcstar on 2012-03-28
> **Grenage said:**
> Good news on this front:

Hurrah, look at what happens when someone whinges REALLY hard!  ):P

---

### Post by winh8r on 2012-03-28
> **dcstar said:**
> Hurrah, look at what happens when someone whinges REALLY hard!  ):P

Now THAT was a result!

\\:D/ =D> \\:D/

---

### Post by cmccauley on 2012-03-28
> **dcstar said:**
> 
This change breaks this basic rule on the arrogant assumption that all Ubuntu users will have audible sound to let them know that the action of pressing the Print Screen key actually does something. At the very least a message should flash up for a short time to let people know the capture has been done.



Dohh, that's why the PrntScn button "works" on my laptop in the office but not at home - the sound on the laptop at home is off. Both are actually working, I just didn't know it. 

We really need that screen-shot dialog back.

Chris

---

### Post by VMC on 2012-03-28
This must have been fixed now. Installed the current ISO and it works.

[gnome-screenshot = 3.3.92-0ubuntu2]

---

### Post by winh8r on 2012-03-29
From the changelog for the screenshot utility::


> * debian/patches/ubuntu_interactive_screenshots.patch:
    - on Unity sessions display a confirmation dialog after taking 
      screenshots with the keybindings, [B][COLOR="Red"]the auto saving behaviour is
      confusing our users[/COLOR][/B] (lp: #927952)

Well , I apologise for saying this here and you can delete this post if you want , but it is **HIS** arrogance that is confusing me.
There is no point in having an accessibility policy and claiming to be for everyone, and deciding that those with hearing impairment dont need to know when they have taken a screenshot or where it has gone.

Anyway, it has been fixed and is now working as it should (tested and confirmed)

****EDIT**** Have taken it up with the gnome developers which I probably should have and would have, had I been able to get into the launchpad page last night and seen the link to the gnome bugzilla. I will be making no further comment on this matter in this thread/forum as the issue is resolved for the end user.

---

### Post by mc4man on 2012-03-29
> **winh8r said:**
> From the changelog for the screenshot utility::




Well , I apologise for saying this here and you can delete this post if you want , but it is **HIS** arrogance that is confusing me.
There is no point in having an accessibility policy and claiming to be for everyone, and deciding that those with hearing impairment dont need to know when they have taken a screenshot or where it has gone.

Anyway, it has been fixed and is now working as it should (tested and confirmed)

[COLOR="Red"]rant over-- thank you[/COLOR]

The launchpad page seems to be "locked" at the moment.

Not sure what you're referring to, anyway this has been fixed for unity* for over 5 weeks now. As far as gnome* sessions it has not & likely won't be unless gnome decides too.

---

### Post by cariboo on 2012-03-29
> **winh8r said:**
> From the changelog for the screenshot utility::




Well , I apologise for saying this here and you can delete this post if you want , but it is **HIS** arrogance that is confusing me.
There is no point in having an accessibility policy and claiming to be for everyone, and deciding that those with hearing impairment dont need to know when they have taken a screenshot or where it has gone.

Anyway, it has been fixed and is now working as it should (tested and confirmed)

[COLOR="Red"]rant over-- thank you[/COLOR]

The launchpad page seems to be "locked" at the moment.

The bug you quoted, has a link to an upstream bug report, that's where your rant should really go, as it's a problem with Gnome, not Unity.

---

### Post by hakermania on 2012-03-30
Hey! For everyone who hates gnome-screenshot because of the flashing and stuff, that's a little trick to make gnome-screenshot let you select the area you want to capture every time you press the PrtSc button:
You MUST be root for this:
```

mkdir /screenshot
mv /usr/bin/gnome-screenshot /screenshot
echo -e '#!bin/bash\n/screenshot/gnome-screenshot -a' > /usr/bin/gnome-screenshot
chmod +x /usr/bin/gnome-screenshot

```Now, every time you push the PrtSc button you will be asked to select area for capturing, which is most of the times handy.

---

### Post by VMC on 2012-03-30
Maybe I'm missing what your trying to do, but doesn't Shift+PrtScr do same thing?

---

### Post by meborc on 2012-03-30
> **VMC said:**
> Maybe I'm missing what your trying to do, but doesn't Shift+PrtScr do same thing?

yes and Ctrl+PrtSc will take a shot of the active monitor instead of all your monitors

---

