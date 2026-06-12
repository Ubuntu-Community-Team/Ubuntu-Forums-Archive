---
title: "an overheating problem?"
date: 2009-12-09
forum: The Cafe
---

### Post by ragip on 2009-12-09
well, this is not an ubuntu related problem at all but i need all the help i can get

beside my ubuntu-box, i have a pentium 4 pc running win xp (it's full of crap but i want to play games ;)). it has a ati radeon hd3650 chipset agp video card.

the problem is, during random points of all games that i play - except football manager - the game application quits (unproperly)

i think it may be an overheating problem and will take measures , like another fan for the case, but if you know anything about this or any way to detect the problem please help me, as you may guessed, it is frustrating

---

### Post by mivo on 2009-12-09
Have you monitored the temperature before you started playing and after the games' crash? A good Windows utility for this is [Speccy]("http://www.piriform.com/speccy") (it's fairly new, but works well for me).

---

### Post by gradinaruvasile on 2009-12-09
Remove the crap. :)

Might  be a driver/directx related problem. I saw Ati drivers messed up on XP.
Or, better, just reinstall Windows. Thats the best solution.

---

### Post by ragip on 2009-12-09
> **gradinaruvasile said:**
> Remove the crap. :)

Might  be a driver/directx related problem. I saw Ati drivers messed up on XP.
Or, better, just reinstall Windows. Thats the best solution.

it is a fresh install and i am sure that there is no driver - directx related issue. i ve checked that stuff many times. not installing windows (removing the crap) is the best solution :) but i cannot play COD on ubuntu :(

> **mivo said:**
> Have you monitored the temperature before you started playing and after the games' crash? A good Windows utility for this is [Speccy]("http://www.piriform.com/speccy") (it's fairly new, but works well for me).

i will try the software and try to log tempreatures both for cpu and vga card and later i can write about the results

thanks for suggestions :)

---

### Post by cascade9 on 2009-12-09
Take the side off the case, and get a desktop fan and make it blow into the case. If you the games dont shut down, then its a heat problem. 

Even if that doesnt work, it could still be a heat problem (dried out thermal paste etc). 

I guess its more likely that you've got a driver (motherboard and/or video card) and/or direct x problem.

---

### Post by jwbrase on 2009-12-09
> **ragip said:**
> it is a fresh install and i am sure that there is no driver - directx related issue. i ve checked that stuff many times. not installing windows (removing the crap) is the best solution :) but i cannot play COD on ubuntu :(

"Fresh install" doesn't always mean "drivers all in order". About a year ago my family got a new machine, and it came straight from Dell with ATI drivers that bluescreened with one of my games.

---

### Post by Bartender on 2009-12-09
> **cascade9 said:**
> Take the side off the case, and get a desktop fan and make it blow into the case. If you the games dont shut down, then its a heat problem. 

Even if that doesnt work, it could still be a heat problem (dried out thermal paste etc).

+1  The room fan trick is pretty effective.

I have a Pentium 4 PC, built in about 2006 or so.  It has never been run hard, and the last couple of years it's been in semi-retirement, fired up occasionally for playing with Linux distros.  For some reason I connected the original Windows disk one day.  While poking around idly I opened up Speedfan.  It said the Northbridge was burning up.  I stuck my finger on the passive NB heatsink - the fins were damned hot!

I shut the thing down and popped the little spring clip off.  The heatsink fell off.  The original thermal paste wasn't fluid anymore.  It was like old spackle.  Cleaned it off with some alcohol, applied a dab of Arctic Silver, reassembled, the heatsink went back to the usual warm but not hot.  Speedfan was happy.

You'd think if the heatsink wasn't transferring the heat, that the fins would be cool while the chip underneath was melting down, wouldn't you?  I can't explain that part of it, but the old thermal paste definitely wasn't doing its job.

---

### Post by ragip on 2009-12-09
@cascade9

all games i have start normally in terms of performance and quality
but after a random amount of time applications quit
i think it is not driver related because games can start normally and without errors

do you think a motherboard driver problem can do that?
heating issue - i ll test tonight

---

### Post by ragip on 2009-12-09
> **jwbrase said:**
> "Fresh install" doesn't always mean "drivers all in order". About a year ago my family got a new machine, and it came straight from Dell with ATI drivers that bluescreened with one of my games.

i did mention "fresh install" because re installing windows is suggested
i know that proper drivers and installing windows are connected, yet not the same
;)

---

### Post by x33a on 2009-12-09
From my own experiences, the computer shuts down (more like crashing) in case of overheating. That is when the system reaches the critical temperature, the system shuts down to prevent damage.

closing down of applications/games, seems to point to a different cause.

---

### Post by ragip on 2009-12-09
> **x33a said:**
> From my own experiences, the computer shuts down (more like crashing) in case of overheating. That is when the system reaches the critical temperature, the system shuts down to prevent damage.

closing down of applications/games, seems to point to a different cause.

i first googled and came to that conclusion but maybe only the graphics card is overheating and somehow stops working and computer goes on
can it be like this?

---

### Post by x33a on 2009-12-09
That might be a possibility.

Well, you should first monitor your temperatures. use speedfan and keep it running in the background. it monitors the temperatures continuously and keeps a history of current, minimum and  maximum temperature for cpu, gpu, hard drives, motherboard, fan speed, and voltages.

if it seems alright, then run memtest86+ for issues with ram. and even search the event log for anything suspicious.

---

### Post by ragip on 2009-12-09
same problem - an another forum

> I had same problem. Set your AGP rate to x4 instead of x8. There is a tab in desktop properties where you can do it.

fiddling with the rate may be the answer

---

### Post by The Real Dave on 2009-12-09
Pentium IVs in my experience won't crash because of heat. It depends on your motherboard, but many have thermal throttling, as the heat goes up, the speed of the CPU goes down, to prevent damage. 

My 3Ghz PIV used run at 50C idle, and 67C under load. I opened it up, and it was clogged with dust, the heatsink in particular. Its quite a good heatsink as stock coolers go, with many thin fins, a large fan, and copper heat pipes. 

An air duster is an invaluable buy. It will clear the heatsink right out, just make sure you have a hoover behind to suck up the blown out dust. Clean the inside of the case with paper towel, and ensure that any heatsink has decent thermal grease, invest in some Artic Silver 5, and some pure alcohol to clean the old grease off. Ensure that all your fans work, and replace any that don't or that rattle, a worn fan will just generate heat. Just make sure you earth your self well when cleaning, especially with the hoover.

In my case, I added an 80mm fan behind the CPU to eject air out, and a 120mm to the grill on the side of the case (using wire, its not designed to go there). That blows cold air down onto the motherboard, CPU, and even to the harddrives. One trouble is that it moves alot of air, in a dusty place, so I clean my computer once a month. 

With that, and a slight change to the PWM values to make the CPU fan run faster, my PIV now sits at 35C under load (its constantly under load thanks to Folding@Home).

Oh, before I forget, seeing as its possible that its your GFX card, have a look at [PCI fans]("http://www.xoxide.com/slotcooler2.html"). You could slot one under your card, and blow air onto it. Try and put as many fans in your case as possible, to eject the hot air, but don't forget to bring it in aswell :) Hope that helps :)

EDIT - If you want to see a picture of my set up, you can find one [here]("http://linuxexpresso.wordpress.com/hardware/"). The computer I'm talking about is the first listed :)

---

### Post by alphaniner on 2009-12-09
Do you have Catalyst Control Center installed?  It will show you the temp of the GPU.

---

### Post by cascade9 on 2009-12-09
> **Bartender said:**
> +1  The room fan trick is pretty effective.

I have a Pentium 4 PC, built in about 2006 or so.  It has never been run hard, and the last couple of years it's been in semi-retirement, fired up occasionally for playing with Linux distros.  For some reason I connected the original Windows disk one day.  While poking around idly I opened up Speedfan.  It said the Northbridge was burning up.  I stuck my finger on the passive NB heatsink - the fins were damned hot!

I shut the thing down and popped the little spring clip off.  The heatsink fell off.  The original thermal paste wasn't fluid anymore.  It was like old spackle.  Cleaned it off with some alcohol, applied a dab of Arctic Silver, reassembled, the heatsink went back to the usual warm but not hot.  Speedfan was happy.

You'd think if the heatsink wasn't transferring the heat, that the fins would be cool while the chip underneath was melting down, wouldn't you?  I can't explain that part of it, but the old thermal paste definitely wasn't doing its job.

I've seen _exactly_ the same thing, more than once. I'm glad I'm not the only one. As far as the 'heatsink not transferring heat' issue, from what I know, thats because of the thermal paste acting like a 'blanket'. The heat still has to go somehwere, so the heatsink still gets hot, but its not transferring the way it should so the chip underneath will be burning up with the heatsink still hot, from radiant heat.   

> **The Real Dave said:**
> Pentium IVs in my experience won't crash because of heat. **It depends on your motherboard**, but many have thermal throttling, as the heat goes up, the speed of the CPU goes down, to prevent damage. 

My 3Ghz PIV used run at 50C idle, and 67C under load. I opened it up, and it was clogged with dust, the heatsink in particular. Its quite a good heatsink as stock coolers go, with many thin fins, a large fan, and copper heat pipes. 


Bolded is the important bit. Some P4 boards are good for this, others can be flaky....at best. 

> **ragip said:**
> @cascade9

all games i have start normally in terms of performance and quality
but after a random amount of time applications quit
i think it is not driver related because games can start normally and without errors

do you think a motherboard driver problem can do that?
heating issue - i ll test tonight

I've seen just that happen. Games start normally, but then crash some time after. In the instances when I've seen it (when it hasnt been caused by hardware problems) I've solved it by getting newer (or more stable) direct x, motherboard drivers and video card drivers.

---

### Post by KIAaze on 2009-12-09
> **The Real Dave said:**
> Pentium IVs in my experience won't crash because of heat. 


In my experience, they definitely do. Or at least the overheating causes an immediate shutdown as somebody said previously in this thread.

My solution was to open the case of my laptop and clean it.
My story: [http://www.linuxquestions.org/questions/linux-hardware-18/stupid-overheating-567540/](http://www.linuxquestions.org/questions/linux-hardware-18/stupid-overheating-567540/)

Overheating related info: [http://www.linuxquestions.org/questions/linux-kernel-70/deactivating-forced-shutdown-because-of-high-temperature-446452/](http://www.linuxquestions.org/questions/linux-kernel-70/deactivating-forced-shutdown-because-of-high-temperature-446452/)

---

### Post by The Real Dave on 2009-12-09
> **KIAaze said:**
> In my experience, they definitely do. Or at least the overheating causes an immediate shutdown as somebody said previously in this thread.

My solution was to open the case of my laptop and clean it.
My story: [http://www.linuxquestions.org/questions/linux-hardware-18/stupid-overheating-567540/](http://www.linuxquestions.org/questions/linux-hardware-18/stupid-overheating-567540/)

Overheating related info: [http://www.linuxquestions.org/questions/linux-kernel-70/deactivating-forced-shutdown-because-of-high-temperature-446452/](http://www.linuxquestions.org/questions/linux-kernel-70/deactivating-forced-shutdown-because-of-high-temperature-446452/)

Thats just my experience, I found out recently that the thermal throttling is dependant on motherboard :) So maybe I've just been lucky

---

### Post by ragip on 2009-12-11
status update :)
i did install a new 120 mm fan to the case over the graphics card
reinstalled the chipset driver of the mainboard
decreased AGP acceleration to 4x from 8x
changed settings to performance side
reinstalled directx
result : nothing has changed, games still quit

tonight i will go home and reinstall windows from a different cd

---

### Post by sdowney717 on 2009-12-11
check the ram, boot the live cd and do memtest.
bad ram causes sudden program crashes.
when bad ram heats up, it gets worse.

windows wont let you do this
linux lets you lock out bad ram using memmap. at bootup memmap tells the kernel to ignore whole areas of ram. 
you still have to find the bad area in ram and pass it using the memmap command at boot.

Say I have 1024 MB and the last 54 MB is bad according to memtest86.
you should also grab more memory on each side of the area to block out. this way you are sure to get it all.
SO, all you have to do is make a comment in the kernel boot line

For grub2 it is tricky. You have to run sudo update-grub to regenerate
/boot/grub/grub.cfg and grub2 uses the settings in /etc/default/grub to generate the new /boot/grub/grub.cfg file.

edit grub do this 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" should be
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash memmap=54M\\\$970M"

this then writes into grub.cfg  memmap=54M\$970 when you run update-grub

thus
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro quiet splash
becomes
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro quiet splash memmap=54M\$970M

for example in my case memmap=54M\$970M tells it to ignore the last 54MB of the ram. You can use M for MB's and K for kilobytes or use an address.

memmap examples, personally think setting the memmap parameters using MB's and not addresses is easier
[http://linux.derkeiler.com/Mailing-L.../msg05303.html](http://linux.derkeiler.com/Mailing-L.../msg05303.html)
[http://ubuntuforums.org/showthread.php?t=860631](http://ubuntuforums.org/showthread.php?t=860631)
grub2 help
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by PaulReaver on 2009-12-11
It could also be a power problem. Did the graphics card come with the pc? or did you add that later?. I had a similar problem after fitting my graphics card. fixed it with a bigger psu
 
I also had an ati card that heat up so much it desoldered the gpu. not easily identified. gave me similar errors to yours.

Cheapest first.
I would start by changing the thermal paste first.
Then undo any overclocking.
if this does'nt work you might need to spend some money :(

---

### Post by cascade9 on 2009-12-15
> **PaulReaver said:**
> It could also be a power problem. Did the graphics card come with the pc? or did you add that later?. I had a similar problem after fitting my graphics card. fixed it with a bigger psu
 
I also had an ati card that heat up so much it desoldered the gpu. not easily identified. gave me similar errors to yours.

Cheapest first.
I would start by changing the thermal paste first.
Then undo any overclocking.
if this does'nt work you might need to spend some money :(

Good ideas. I would add "if you have overclocked it, try underclocking". Thats worked for me, once.

---

### Post by tom66 on 2009-12-15
For Windows, I use Speedfan, which monitors many sensors; and on Linux, I use lm-sensors (try running 'sensors' on your PC.) Speedfan may not pick up some GPU sensors, while lm-sensors seems to be better in that area.

---

### Post by Exodist on 2009-12-15
P4 = HOT. They are very prone to get to hot.

Take side off, blow all the dust out.
If you want to keep using the unit, get new heat paste and possibly a larger heatsink or just more case fans. 

P4s always tend to run hotter the older they get. PC manufacturers always seem to elect to letting the PC get hotter then it should over slightly elevated fan noise.

---

