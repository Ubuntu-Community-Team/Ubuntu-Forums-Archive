---
title: "Laptop Hardrive Killer"
date: 2007-10-28
forum: System76 Support
---

### Post by sonmez on 2007-10-28
Hello,

I just came across the "[Laptop harddrive killer bug"]("http://ubuntudemon.wordpress.com/2007/10/28/laptop-hardrive-killer-bug-how-to-discover-whether-you-are-affected/")
I don't have my daru2 with me. So I can't check whether 
my laptop suffers from this bug. But I wonder if system76 laptops have this problem. 

Thanks

---

### Post by Wiebelhaus on 2007-10-28
FUD , sensationalism or I prefer BS , Haters steady sippin' the haterade , No worries mate it's complete nonsense.


and of course , No , 76 wouldn't be shipping PC's like that.

---

### Post by AusIV4 on 2007-10-28
> **sx66gns said:**
> FUD , sensationalism or I prefer BS , Haters steady sippin' the haterade , No worries mate it's complete nonsense.


and of course , No , 76 wouldn't be shipping PC's like that.

...

This isn't Microsoft trying to push their OS by saying "Linux kills your hard drive." It's a concerned (perhaps misinformed, I don't really know) Linux user pushing for a solution.

In any case, System76 wouldn't knowingly ship PC's like that, but it's a problem that's just been surfacing, so I don't know that they've had a chance to look into it yet.

I definitely think it should be looked into. It may turn out to be nothing, but it shouldn't be dismissed as just being the usual FUD from corporate rivals.

---

### Post by Wiebelhaus on 2007-10-28
> **AusIV4 said:**
> ...

This isn't Microsoft trying to push their OS by saying "Linux kills your hard drive." It's a concerned (perhaps misinformed, I don't really know) Linux user pushing for a solution.

In any case, System76 wouldn't knowingly ship PC's like that, but it's a problem that's just been surfacing, so I don't know that they've had a chance to look into it yet.

I definitely think it should be looked into. It may turn out to be nothing, but it shouldn't be dismissed as just being the usual FUD from corporate rivals.

It has been , there was a huge thread many moons ago about this with the title "UBUNTU KILZZ HARD DREVIS" (I'm joking, but it was almost that ridiculous) and it got allot of attention , I'm absolutely certain people at the top of the Ubuntu hierarchy saw that and it was researched.

---

### Post by tferero on 2007-10-28
I am not a System76 customer; but I am watching another post in this area related to this problem, so I thought I would put my '2 cents' in.

This is a real problem.  Whether it is a software problem causing excessive load cycles, a misreading by the Smartmon software, or a problem with the HD firmware; no-one seems to know.  Some people have suggested it is a bug in Ubuntu, but Ubuntu disables power management by default. 

I for one am getting readings of  ~5 loads per minute, which is far too high.  I haven't had success with other fixes that have worked for other people, so I personally am leaning towards a misreading with the software (or maybe a problem with my drive's firmware).  However, if the drive really is loading/unloading 5 times per minute, it will fail far sooner than it should.

Regardless of what is causing the problem, people do need an answer, even if it turns out to be along the lines of "your firmware doesn't display this information correctly."

Just my thoughts.

---

### Post by leptons on 2007-10-29
you can check your load cycle by typing

sudo smatctl -a /dev/sda
I have a laptop almost identical to darter ultra 2 (basically same laptop but i get the parts myself) running ubuntu and has a sata harddrive. my load cycle is 1522 after like 2 months of useage.. not bad at all.

Basically, I used to have those annoying clicking noises every 10 seconds or so and I did the following (tips gathered all over different places): 

1. when installing ubuntu, I disabled swap (I have 2 GB ram.. well you don't have to do that)
2. I add a line
hdparm -B255 /dev/sda
in /etc/init.d/rc.local file so it runs everytime it boots. it seems that change settings in hdparm config files do not do anything. Running that command explicitly will guarantee to disable hdparm.
3. I did the notime mounting thing (whatever that is, don't ask me) in the /etc/fstab file so that all the tmp files go in ram (I don't know if that's what it really does... I just add it)
4. I erased everything in /etc/acpi/power.sh so that nothing happens when I unplug/plug AC power (i.e. no change of hdparm settings)
5. I edited the /etc/laptop-mode/laptop-mode.conf and disabled anything that might have some relation to harddrive power saving.

Also, I run laptop-mode start regardless of any situation. I've heard that enabling laptop-mode actually reduces those annoying clicking... but what do I know, try it and see if it does you any good.

the harddrive that i have is a WD scorpio 160 GB. I searched the WD website and they have a firmware upgrade that is supposedly to fix those clicking thing. I ran the program but it says my firmware is already up to date so nothing to upgrade... needless to say, that was pretty useless, though your harddrive manufacturer might have some more useful firmware upgrade, it might be worth a try. 

I can't guarantee if anything might work though. I don't know much about linux and my method seems to work well for me... at least last time I check smartctl, the load count is still in control. hope these hints help.

---

### Post by dirkmegabyte on 2007-11-02
I'm not sure I believe the "bug" that has been filed regarding the laptop drive load/unload cycle count. (#59695 in acpi-support listed on launchpad.net)
   To date, it appears to be unfounded and unsupported by anyone of note. I think the following document from Hitachi paints load/unload cycles in a positive light and is worth reading:
[http://www.hitachigst.com/tech/techlib.nsf/techdocs/9076679E3EE4003E86256FAB005825FB/$file/LoadUnload_white_paper_FINAL.pdf]("http://www.hitachigst.com/tech/techlib.nsf/techdocs/9076679E3EE4003E86256FAB005825FB/$file/LoadUnload_white_paper_FINAL.pdf")

My final point is this: if this were truly a problem, wouldn't this be in the best interest of the harddrive manufacturers to either make a change with their hardware operation -or- pressure BIOS vendors to make a change in theirs to prevent this from happening? The answer to this is an unqualified 'yes'. The hardware manufacturers would be replacing people's harddrives still under warranty for failing in such a short time....all for free. Definitely not in their best interest.

I suspect the smartctl command either displays load/unload values incorrectly or the value it reports is being interpreted incorrectly.

---

