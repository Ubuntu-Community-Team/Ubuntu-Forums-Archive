---
title: "Ubuntu Software Center - few thoughts"
date: 2009-10-30
forum: The Cafe
---

### Post by zubaran on 2009-10-30
I have installed Ubuntu 9.10 and I must admit that Ubuntu Software Center isn't exactly what I had in mind...
It is a bit clumsy. It hides some info, for example current download speed, package dependencies, what you can see is only progress bar. Moreover it is installing software right away, which sometimes is ok, but when you are chosing multiple packages it annoys with repeating freezing which forces to pointless waiting.  It keeps asking for password to frequently. 
It would be nice to have option to download later, when you are done with selecting software.
For now Add/Remove was better for me.
Does somebody feel the same way or I just miss some functionality?

---

### Post by fancypiper on 2009-10-30
I much prefer synaptic, myself.

---

### Post by Wanas on 2009-10-30
+1 for synaptic 
I do every thing with synaptic I dont use software center nor gnome add/remove

---

### Post by zubaran on 2009-10-30
Of course, but I used Synaptic for "serious work". Add/Remove was to install let's say popular packages. Now in Ubuntu Software Center I can't see the stars;).
I was also amused when I saw "Price" description. I know that it can be useful in some future commercial activities. But looks "scary";).

---

### Post by ninjatiger422 on 2009-10-30
```

sudo software-properties-gtk -e universe
sudo apt-get update
sudo apt-get install gnome-app-install

```

After you run that go to System > Administration and you should see it.

---

### Post by zubaran on 2009-10-30
Works. Thanks for your assistance ninjatiger422!

---

### Post by lovinglinux on 2009-10-30
> **zubaran said:**
> Does somebody feel the same way or I just miss some functionality?

You are not missing anything. It really sucks IMO. Too many clicks to get things done and not even bulk installation allowed.

I also use Synaptic instead of Add/Remove or Software Center, but it seems the last one will replace Synaptic eventually. Not a good move IMO, unless they make some sort of "advanced interface" option that would allow to do bulk installations and check more detailed info about packages.

---

### Post by NoaHall on 2009-10-30
I always use apt-get anyway, not the GUI package managers.

---

### Post by Dharmachakra on 2009-10-30
It will be interesting to see how it evolves over the next few releases. For now, I'll pass.

---

### Post by SunnyRabbiera on 2009-10-30
Well in many ways its a good tool for beginners, but if its going to replace synaptic it needs some serious fleshing out.

---

### Post by Ric_NYC on 2009-10-30
> **zubaran said:**
> I have installed Ubuntu 9.10 and I must admit that Ubuntu Software Center isn't exactly what I had in mind...
It is a bit clumsy. It hides some info, for example current download speed, package dependencies, what you can see is only progress bar. Moreover it is installing software right away, which sometimes is ok, but when you are chosing multiple packages it annoys with repeating freezing which forces to pointless waiting.  It keeps asking for password to frequently. 
It would be nice to have option to download later, when you are done with selecting software.
For now Add/Remove was better for me.
Does somebody feel the same way or I just miss some functionality?

I agree 100%.

---

### Post by ericab on 2009-10-30
software center = bloatware.

---

### Post by misfitpierce on 2009-10-30
Its the first step into the software center... They said it would upgrade over time and releases within next 2 releases which will eventually be the center for upgrades for apps and all and synaptic all in one. I feel it is quite nice and has potential and will get better over time... Give it a bit of time and it should evolve into the full fledged app its meant to be!

---

### Post by Nerd King on 2009-10-30
At first glance it looked ok. Then I tried using it. I decided to install a bunch of FOSS games and see how it handled. Oh dear. Like a dog. The lack of 'tick-lots-of-boxes-then-hit-apply' really bites for starters. It's slow, not very responsive, and really not much fun to use. Synaptic or apt-get when I can remember how to spell the package names!

---

### Post by Stosskraft on 2009-10-31
> **ric_nyc said:**
> i agree 100%.

+1

---

### Post by papangul on 2009-10-31
I think the left side panel and the file menu both can be eliminated. In place of file menu an icon based improvised menu can be included(this menu can be placed at the left, where the side panel is currently). 

Also, we have to click an individual package and then the arrow becomes visible at the right, which has to be clicked again to view the details - this is ridiculous! In place of the arrow a 'view details' sign can be be there. The list of installable items can have an alternating 'stripe' colour.

---

### Post by NoSheds on 2009-11-04
See also thread "9.10 Ubuntu Software Center Stinks!"

in Ubuntu Forums > The Ubuntu Forum Community > Main Support Categories > Installation & Upgrades

[http://ubuntuforums.org/showthread.php?t=1306894](http://ubuntuforums.org/showthread.php?t=1306894)

---

### Post by juancarlospaco on 2009-11-04
Its Version 1, dont expect to overtake Synaptic, 
is for people that NEVER used a PC and want to start using it, 
and dont know whats a dependency, and dont want to know.

Never will be Geek friendly, 
if you know too much use te CLI, Synaptic, etc.

---

### Post by ssam on 2009-11-04
i do like how you can keep browsing and selecting things while it installs in the background. i have not noticed the freezing that some of you report.

its a shame they took out the popularity. there is an overwhelming number of packages, of varying quality, so it needs some way of ranking. maybe have a rating system, or a featured apps page.

i'll still use synaptic because i need to install various commandline apps that don't have entries in software-center or add+remove.

i think it partly clever marketing. it has not added anything new, but all the karmic release articles mentioned it as an easy way to install software. for people who have the idea that installing on linux is hard, those articles might encourage them to have a try with ubuntu.

i look forward to seeing how it improves in lucid.

---

