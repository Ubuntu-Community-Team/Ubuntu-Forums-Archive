---
title: "Vivid Vervet 15.04 Innit: cannot read descriptor: broken pipe"
date: 2014-11-02
forum: Ubuntu Development Version
---

### Post by Hazzabin on 2014-11-02
I've been getting this at boot-up, tho it does boot eventually

I have no idea how to possibly fix this.....it happens with Gnome and but mostly with Unity boots

regards

---

### Post by Cavsfan on 2014-11-03
> **Hazzabin said:**
> I've been getting this at boot-up, tho it does boot eventually

I have no idea how to possibly fix this.....it happens with Gnome and but mostly with Unity boots

regards

I get this every time I boot into Vivid I have Vivid Mate - just changed the utopic to vivid in the sources and did a dist-upgrade. Mate is gnome only.

I haven't seen anything that is affected by this error myself nor do I know what "pipe" is broken.

---

### Post by Hazzabin on 2014-11-03
Thanks for that info Cavsfan, Mate is one distro I've not got. OK I'll give your idea a try as I should of mentioned even tho 15.04 Unity I have most
have Gnome-flashback

---

### Post by Cavsfan on 2014-11-03
> **Hazzabin said:**
> Thanks for that info Cavsfan, Mate is one distro I've not got. OK I'll give your idea a try as I should of mentioned even tho 15.04 Unity I have most
have Gnome-flashback

You're welcome. I don't think it matters what session. From what you posted you get this in unity and flashback I get it in Mate.
And I don't see it causing any harm but who am I to know. :p

---

### Post by Hazzabin on 2014-11-03
> **Cavsfan said:**
> You're welcome. I don't think it matters what session. From what you posted you get this in unity and flashback I get it in Mate.
And I don't see it causing any harm but who am I to know. :p

I'm sure you know a hell of a lot more than I do :)  I just downloaded and hard installed Mate tho is version 14.10, very impressive, I'll get use to this for a bit then attempt to push it
through to 15.04 errr ummm just for fun :P

---

### Post by Cavsfan on 2014-11-04
> **Hazzabin said:**
> I'm sure you know a hell of a lot more than I do :)  I just downloaded and hard installed Mate tho is version 14.10, very impressive, I'll get use to this for a bit then attempt to push it
through to 15.04 errr ummm just for fun :P

I really like Mate - it's kind of a throwback to when there was no Unity. 
BTW I didn't see that error when I booted into Vivid Mate just now.

I had the hardest time getting the sources changed over from utopic to vivid but I think I finally got that accomplished yesterday.

I had to comment out extras as they do not have vivid set up yet (totally normal at this stage in the game).
I think I commented out a few others that were utopic in **/etc/apt/**. Trying not to add Utopic sources in the mix.

---

### Post by Elfy on 2014-11-04
[lpbug]1364630[/lpbug]

---

### Post by Cavsfan on 2014-11-04
I also updated my wiki for a custom grub screen adding Mate yesterday if you're interested. It's a little bit different from the other versions.

Here's what my current grub screen looks like:

[[IMG]http://en.zimagez.com/miniature/20141103120413.jpg[/IMG]]("http://en.zimagez.com/zimage/20141103120413.php") [[IMG]http://en.zimagez.com/miniature/20141103120425.jpg[/IMG]]("http://en.zimagez.com/zimage/20141103120425.php")

The first is with flash and better quality but I cut the left side of the screen off, the other one is without flash but doesn't look quite as good as it actually does.
BTW Lebron going back to Cleveland just re-validated my forum name. :p

---

### Post by Cavsfan on 2014-11-04
> **Elfy said:**
> [lpbug]1364630[/lpbug]

Thanks Elfy! I added my name to that bug. I didn't see it today but that doesn't mean a whole lot.

---

### Post by Hazzabin on 2014-11-04
Thanks Elfy for that info.

Cavsfan.....that 'Grub' very impressive.......I tried it a few of times following your wiki and botched it, my patience ran out :)
with 18 partitions found it rough going :P 

After playing with Mate 14.10 I pushed ahead into 15.04, took the source setup from a Vivid install and copied across and did a few commented outs
This is coming from the Mate install and yeah I'm happy with it even got compiz with rotating cube etc etc

Thanks again for your help

---

### Post by Cavsfan on 2014-11-04
> **Hazzabin said:**
> Thanks Elfy for that info.

Cavsfan.....that 'Grub' very impressive.......I tried it a few of times following your wiki and botched it, my patience ran out :)
with 18 partitions found it rough going :P 

After playing with Mate 14.10 I pushed ahead into 15.04, took the source setup from a Vivid install and copied across and did a few commented outs
This is coming from the Mate install and yeah I'm happy with it even got compiz with rotating cube etc etc

Thanks again for your help

Good deal! I understand that the grub wiki appears a little frustrating but the more you get to know it the smaller and less complicated it gets.
I use it because the default grub does not work once I install a new version. I'll select one but it won't boot into it then I press Cntl+Alt+F1 to login tty and it shows I'm in another version than I had selected.
I had to customize it just to be able to boot into any of the others besides the top one (the one that was just installed).

I'm glad to see on that bug that Utopic is also mentioned because I just booted into it and seen the broken pipe error.

So we are saying it affects both Vivid and Utopic - good. Not really knowledgeable enough to know what the error does but I'm sure it does something bad. 

Yeah I love compiz, the cube and of course VinDSL's conky. :p

[[IMG]http://en.zimagez.com/miniature/screenshotff92249660dc21a6288f65eb7d295fd8.png[/IMG]]("http://en.zimagez.com/zimage/screenshotff92249660dc21a6288f65eb7d295fd8.php")

---

### Post by Hazzabin on 2014-11-05
Oh yeah gotta love our cube, for me I havent' used a conky for yonks

Guess we slightly off topic now :) I actually haven't seen the 'broken pipe' for pass couple of days  :lolflag:

---

### Post by Cavsfan on 2014-11-06
> **Hazzabin said:**
> Oh yeah gotta love our cube, for me I havent' used a conky for yonks

Guess we slightly off topic now :) I actually haven't seen the 'broken pipe' for pass couple of days  :lolflag:

Indeed eye candy is necessary! :guitar:

I have not seen the "broken pipe" message for several days now in Vivid upstart only of course.
But, I did see it again when booting into Utopic just now.

I looked at the bug and it is tagged with just "Utopic" so if any one is seeing this in Vivid, the bug needs to be tagged as affecting Vivid also.

---

