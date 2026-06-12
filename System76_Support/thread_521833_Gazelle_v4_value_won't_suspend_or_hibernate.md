---
title: "Gazelle v4 value won't suspend or hibernate"
date: 2007-08-09
forum: System76 Support
---

### Post by sbergman27 on 2007-08-09
I just got a Gazelle Value v4 in and when I try to suspend, the screen fades, there is a short bit of disk activity, and the leds above the keyboard go off.  But the fan is still running and the power and wireless led's are still on solid on the front.  And then I'm stuck.  Closing and opening the lid does nothing.  Hitting the power button does nothing.  Hitting keys does nothing.  I have to hold the power button down and boot the system to get it back.  I ran the system 76 driver utility to get the latest driver.  Still have the same problem.

Hibernate acts similarly.  Except that instead of a dark screen, I have a flashing cursor at the top left.

My client is planning on buying 8 more of these, but I can't present it without suspend working.

Thanks for any assistance.

-Steve Bergman

---

### Post by Mach1US on 2007-08-09
I have had same problem and this how-to fixed it 100% .
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

### Post by sbergman27 on 2007-08-09
Thanks.  That does help.  It then will suspend.  But when I resume, the power light comes on and the CD reader clicks a time or two.  But nothing else.  Black screen.

I must say that the reason I recommended System76 is that all of this sort of thing was presumably supposed to "just work".

This kind of thing would be acceptable if I had bought a Compaq off the shelf and put Ubuntu on it.  

But I am ***extremely*** disappointed with System76 at this point.  It might be different if I had purchased this machine for myself, and had the time to muck with it.  But I'm supposed to deliver this, in working order, to my client's business site tomorrow.

If suspend doesn't work on the Gazelle, that fact needs to be displayed prominently on the sales site.

---

### Post by thomasaaron on 2007-08-10
Suspend should work on the Gazelle.

1. Have you either re-imaged the machine, or are you using something other than the gnome-desktop?

2. Try running your System 76 driver.

3. Please post the results of: swapon -s

Best,
Tom

---

### Post by sbergman27 on 2007-08-10
We just pulled the machine out of the box.  No reimaging.

I'm logging into the gnome desktop and hitting Fn-F1.

Output of swapon -s:

```

FIlename                                     Type       Size          Used Priority
/dev/mapper/ubuntu-swap_1 partition 1015800 0       -1

```

Also, the large "System 76" vinyl sheet on the top cover of the unit has *very* noticeably peeled up all along the left and right edges.  And less noticeably all along the top and bottom edges.

---

### Post by thomasaaron on 2007-08-13
OK. I'm not sure what's going on with it. I'll image the one I have in the shop and do some testing on it today.

Send me an email (support[at]system76[dot]com) requesting a new sticker, and I'll send you one.

Best,
Tom

---

