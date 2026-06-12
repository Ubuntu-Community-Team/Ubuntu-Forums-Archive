---
title: "Better battery life on Mint than Ubuntu"
date: 2014-01-03
forum: Ubuntu, Linux and OS Chat
---

### Post by jan-goebel-g on 2014-01-03
Hi.

First of all, i did mutltiple tests, im using hardware to mesure power usage. I set the panel to max. Im running tlp and putting all improvements in from powertop.
Im using an i3 2350m processor on my thinkpad l420 but for what i could check quickly its the same outcome using live usb distros on friends dell and even on a macbook 2009.

I compared ubuntu 13.10 to mint16(which should be about the same core right?) and i tried 14.04 alpha. From what i rememer it wasnt better at 12.04 so dont recommend me using it.

**IT IS NOT A UNITY PROBLEM.Unity is fine and fast. If it wasnt i wouldnt care about getting the same results on Ubuntu**
DE make no difference at all, i tried all of them and i3 is giving very similar results to unity!!
Thats for the DE part, i CANNOT judge if maybe some of the deamons or notifications is running in the background while switching the De.

Both Ubuntu versions score about the same, one  browser window(firefox and chrome, chromium are more or less the same) and one terminal running top the power usage jumps between 11w and 13w.
Moving windows it goes up to 14to16w (a lot worse on 14.04 but thats alpha..).
Killing processes and stopping services didnt improve the idle load, at least i didnt find the one causing the difference.
Unity is using 650to700mb on ram on bootup but i dont care, iv got 8gb of ram.
I didnt use any of the dash for the basic tests, but its alright once u turn the blur to static (dynamic blur which is coded badly just sucks) its about the same as opening the menus on other DE.

Now here comes mint and after trying everything from manjaro openbox to suse kde i was amazed on power efficiency and most importantly idle/low usage power consumption. Then i got confused.
Lets see the results:
Starting up a browser with google and a terminal with top it ends up with 10,6to11w power usage. No spiking up to 13w even though im using the same indicators and while there is no ubuntu1 running on the ubuntu system im running dropbox on mint.
The big deal is that after a second or two of idle the power usage drops to 10,2w which is amazing and does make a difference in the end if what you do is text editing.
Using dockbarx to compare it vs unity i found that its about the same, hovering the icons both go up to 13w which is nice of both, both wont change idle power usage.


I did some more testing of real world situations and the .8to2w difference stays throughout the whole process.


So is there anybody that looked into the issue? Its really bugging me since i like how i get maximum screen estate from unity without going full screen mode (basicly i dont like to press a key to look at the clock) and that its overall nicely done.

Id appreciate any help on how to find differences, i once did a ps aux and stuff but i couldnt really find a difference or a method to mesure how much power is used up by the processes via powertop.

I think that getting stuff like this to the next release could help ubuntu bigtime, people buying mac for battery efficiency and lenovo for big batterys while windows is ignoring the issue putting very few late efford in power usage but still getting as good results as the latest ubuntu since windows 7.
With mint i get better battery life then with windows and i am, i reapt myself, not speaking about DE because right now im running KDE  at steady 11w having 10tabs open in chrome while i would be near 12w on ubuntu even with xfce or mate DE.
Cant we get near apple, at least for the popular and nice cpu choices like intel? Mint shows that somehow they can be above the other distros consistently even using the ubuntu kde package right now why cant we (im considering myself an ubuntu user, started using it over gentoo a decade ago)get at least the same or maybe even better results creating an argument to use ubuntu and kill off the ubuntu=slow myth?

---

### Post by tgalati4 on 2014-01-03
Use what works with your hardware.

Run *powertop* on each distro and compare the results.

---

### Post by jan-goebel-g on 2014-01-03
I did and i posted the results. I just dont get the difference, both distributions should use mostly the same stuff and id like to know the difference.
Powertop itself shows very similar wakeups and gpu usage, im even getting better results with unity on mint.

---

### Post by tgalati4 on 2014-01-03
I wonder if Mint uses a different kernel configuration to build its kernel.  Perhaps compare the *sysctl* settings for each distro--/etc/sysctl.conf.  I know that IPV4 and not IPV6 is set as default in Mint distros for browsing performance reasons.  Perhaps this fact alone accounts for the power difference.

I misunderstood your testing.  You said you used hardware for testing the power, and I assumed that you used an external power meter, such as a Kill-a-Watt meter for your tests.

Regardless, your testing shows some interesting data for i3 architecture.  Anyone test i5 or i7?

---

### Post by nerdtron on 2014-01-04
> **tgalati4 said:**
> I wonder if Mint uses a different kernel configuration to build its kernel.  Perhaps compare the *sysctl* settings for each distro--/etc/sysctl.conf.  I know that IPV4 and not IPV6 is set as default in Mint distros for browsing performance reasons.  Perhaps this fact alone accounts for the power difference.



My initial impression too. Are mint and ubuntu using the same kernel version?

---

### Post by caymus on 2014-01-04
Is zeitgeist-core running also on mint?
This is a ram eater, but i dont thing ram could eat so much power.
Since you say you have tested both DE on ubuntu i dont thing this is a problem from openGL gpu rendering vs openGL raster rendering by cpu also.

Maybe from the number of active proccess? Since you say 600MB of ram is used at startup?
I use 394 MB of ram for unity at startup, from mini.iso install & zeitgeist disable, & a bunch of unity-lens craps & various things, removed.

Maybe advanced power management for hdd is enable on mint for you?

This is a scratch-head problem ^^.

---

### Post by jan-goebel-g on 2014-01-04
@tgalti: To clarify it, i was using powertop, noticed things, used hardware to be safe so its no calculation issue and then im switching distros every few days lately and iv gotta say, be it kde, xfce, cinnamon, mate all of them run longer on mint.

The main thing mint does is stepping the powerdrain down further when idle, since our laptop is idle or deep c-state most of the time anyway (code editing, forum browsing, chat).

Some facts:
-Flash kills the battery, but it does the same strain on the cpu on all platforms, sometimes i feel that the proprietary chrome works a tiny bit better then the open chrome and firefox.
-WM wont make a difference, i was --replace´ing xfwm4, compiz and gala in my xfce installation and they were all the same at idle and guess what, xfce LOST once windows got moved while compiz actually was at least as good as gala. Gala is awesome though, really smooth and quick...in the end its half a second spikes where power usage goes up 3to6w.
The only real bummer is the dash at default (dynamic blur...durrr) but once put to static and of course disabling online lenses its as good as all of the others, but more STABLE.  
-Archlinux is by no means ever faster then ubuntu nor is it more power efficient. In fact its totally the same as ubuntu...

>>[COLOR=#000000]My initial impression too. Are mint and ubuntu using the same kernel version?
[/COLOR]I dont know, i hope that we find somebody that already dug into kernel stuff, i wouldnt expect big differences since driver modules come from intel and i doubt that they hacked wifi drivers for a better fit.
It cant be the notification stuff, i didnt use ubuntu one (which is supsect to be worse then dropbox) or those useless lenses.

>>[COLOR=#000000]Maybe advanced power management for hdd is enable on mint for you?[/COLOR]
Im using tlp bat profile (thats 2to3w off, its huge but its the same on all the systems) and im even putting the minor fixes powertop wants on.

>>[COLOR=#000000]This is a ram eater, but i dont thing ram could eat so much power.
[/COLOR]Ram is saving battery rather then burning it, i doubt that theres an issue with ram though since the laptop has 8gb now (had to buy the cheap offer i saw on original additional 4gb:D).

I gotta admit that i dont know how much/less the ssd does to the equation, shouldnt make a difference though its the same core of drivers and apps.

>>[COLOR=#000000]This is a scratch-head problem ^^
[/COLOR]I totally agree, but thats one of the problem we should scratch our heads other then who forks another DE to feature that one mighty applet he needs so he doesnt have to use the more advanced ways:D.
As i said, apple wins by battery use and ease of use, ubuntu beats mac osx (its true^^) at screen estate and to be honest apart of some nice software i didnt feel a difference, both os work well and game badly.
Im imagining the 30+90wh battery configuration one could pot on the t440s combined with even more improved battery life at low loads (macbook air has the same max performance battery life, its 30%better on normal use though!) and thats why im not trying to measure battery usage on benchmarks but usage on near idle which is 95%of our work.

>>[COLOR=#000000]Is zeitgeist-core running also on mint?[/COLOR]
Thats a good one, i didnt even check till now since every distribution i used found my files and programs easily over dash, menu, catfish so i didnt think that it could be different.
Its a shame i wasnt mistaken, look at this:
[[IMG]http://abload.de/thumb/zeitgeistrunningmintpcjij.png[/IMG]]("http://abload.de/image.php?img=zeitgeistrunningmintpcjij.png")
Its my usual brightness, like 60% which works well inside.


...its to bad it wasnt something trivial like zeitgeist:(

To get a start at the digging im gonna link my ps -ef on mint and then maybe somebody can link his ubuntu, maybe caymus could do it and compare to his already tweaked ubuntu!

[http://paste.ubuntu.com/6693011/](http://paste.ubuntu.com/6693011/)

---

### Post by grahammechanical on 2014-01-04
As regards your last appeal, a lot of work is being done on power consumption for the Ubuntu phone/tablet platform and any improvements will find their way into the Ubuntu desktop platform over the next year due to the Convergence strategy.

Is it not hardware that is the main cause of power consumption? Hard drives, CPU, graphic adapter, wireless adapter, ventilation.  All things should be equal for both distributions. Unless the wireless adapter is switched on in one distribution and not the other. It is just something to check.

Regards.

---

### Post by tgalati4 on 2014-01-04
Here's a simple test:  Install *htop* and run it in a terminal window.  Let the machine stay idle for exactly 1 hour.  Sort by Time+ (accumulated cpu time) and save the screen shot or cut and paste the list of processes and time.  Load the next distro and install *htop* and do the same.  There has to be some process that is running (consuming cpu cycles and power) on the non-Mint distros to account for the difference.

---

### Post by richardsdma on 2014-01-05
from what i have red, it seems there is not such a big difference of power consumption. 
i am interested in this field too, but i did a comparison between windows and ubuntu. check this:
[http://ubuntuforums.org/showthread.php?t=2185639](http://ubuntuforums.org/showthread.php?t=2185639)

another issue: maybe when you have measured the power on ubuntu, the vent just started in that moment and that give you the extra power consumption. 
so, compare the consumption doing a standard task (ie. listen a mp3 stream in the same player) for some time and watch if the cooler is on or off and also if the system is not looking for updates or other hidden temporary processes. 
from my experience, on my machine, the cooler takes about 1-2W, depends of a revolution speed.

---

### Post by Bucky Ball on 2014-01-05
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by ssam on 2014-01-05
Powertop will tell you which processes are causing the most wake ups (which stop the CPU going into low power mode). Maybe ubuntu has something running that cause a lot of wake ups.

It will also show you the tunable parameters. maybe mint is setting something into a low power mode that ubuntu has missed.

---

### Post by jan-goebel-g on 2014-01-06
Sorry for the delay, couldnt get some minutes to post earlier.

>>[COLOR=#000000]maybe mint is setting something into a low power mode that ubuntu has missed.
Im setting everything to minimal through powertop/tlp so it shouldnt matter.
Is there a way to set my gpu to power saving and maybe thats what mint does?


>>[/COLOR][COLOR=#000000]from what i have red, it seems there is not such a big difference of power consumption. 
Its noticable on everyday live, cinnamon and xfce both do about as good and both do better then xfce on ubuntu if i remember it right.

>>[/COLOR][COLOR=#000000]another issue: maybe when you have measured the power on ubuntu, the vent just started in that moment and that give you the extra power consumption. 
[/COLOR][COLOR=#000000]I put some time into that and for the last mesures i didnt use powertop because i fear that it could harm the results.

>>[/COLOR][COLOR=#000000]so, compare the consumption doing a standard task (ie. listen a mp3 stream in the same player) for some time and watch if the cooler is on or off and also if the system is not looking for updates or other hidden temporary >>processes. [/COLOR]
[COLOR=#000000]>>from my experience, on my machine, the cooler takes about 1-2W, depends of a revolution speed.
The cooler is not the difference, i measured with both cooler on hardware control which means 750rpm and then i disabled it (like i do when coding so theres no noise and while coding it can run like that for a good while).
I didnt even get the feeling that the fan took that much, its a power efficient latptop for afterall even if its 2years old now:D

>>[/COLOR][COLOR=#000000]As regards your last appeal, a lot of work is being done on power consumption for the Ubuntu phone/tablet platform and any improvements will find their way into the Ubuntu desktop platform over the next year due to the Convergence strategy.
Im seriously waiting for those things to come with buying a new laptop, id really prefer a lenovo with **** vs a shinybook but they run smooth, they run a commandline, they have the best service and they run 40%longer so its hard to beat them.
If we could get 20%better battery life it would still be worse but it could own windows hard and compete with the mac because of the nice big fat batterys u can put onto lenovo laptops.

>>[/COLOR][COLOR=#000000]Is it not hardware that is the main cause of power consumption? Hard drives, CPU, graphic adapter, wireless adapter, ventilation. All things should be equal for both distributions. Unless the wireless adapter is switched on in one >>distribution and not the other. It is just something to check.
Just take a minute and compare the macbook air 13" to the windows surface faple pro,  it has about the same cpu and then compare the battery life.
Its a SHAME that they dont get to do it, id really consider using their spyware over apples spyware but id like to stay with gnu/linux the most even though that means using the horrible gimp over the great photoshop:D

>>[/COLOR][COLOR=#000000]Here's a simple test: Install [/COLOR][I]htop and run it in a terminal window. Let the machine stay idle for exactly 1 hour. Sort by Time+ (accumulated cpu time) and save the screen shot or cut and paste the list of processes and time. Load the next >>distro and install [I]htop and do the same. There has to be some process that is running (consuming cpu cycles and power) on the non-Mint distros to account for the difference.
[/I][/I][COLOR=#000000]Alright im gonna give it a try, im really bad at bash scripts but wouldnt there be a way to time it to exactly 60minutes and maybe even a way to make it refresh google.de every 15seconds?


>>[/COLOR][COLOR=#000000]i am interested in this field too, but i did a comparison between windows and ubuntu. check this
Mint is quiet on the same level as windows, on low load it drops even further if one can believe what i experienced years ago and from what a review i read said. 
Ubuntu is slighty worse, used to be a lot 2years ago so thumbs up for that but there has to be more to, we arent there yet.[/COLOR]

---

### Post by tgalati4 on 2014-01-06
You can get some power savings by turning on "Dynamic Clock" on the graphics chip.  This will throttle the graphics processor speed up and down depending on workload.  This can be done through /etc/X11/xorg.conf or through a module switch.

Yes, you could use a bash script for your testing, but a simple wall-clock test for 60 minutes and then a screen-grab of *htop* should show the differences right away.  And you would only need to do it once for each distro.  Because *htop* keeps accumulated time, exact timing is not really needed, you just want to see the rank-order of processes and see how they compare.  If Ubuntu has one process that Mint does not, then you can focus on the effects of that one process.  My guess is the Ubuntu One sync or Dash phone-home that causes both the CPU and wireless to wake up more often.

---

### Post by jan-goebel-g on 2014-01-06
Alright i didnt know about those nice features of htop, im using top most of the time if i want to quickly know what bugged a 100%process (synapse indicator was the last one, a lot of people may get the same and wonder about battery life in the end:)).
Im gonna put it to a test later, im gonna use live distributions from my thumbdrive to compare it so its fair. 
So the setup would be 13.10 64bit live usb, powertop put all power savings to "good".

Maybe u want to do that on your laptop or even pc too? It could get interesting to see what kills the battery that little but noticable bit more (im at 50wh battery, 10avg would give me 5h, 12w avg would only result in 4,2hourse. 50minutes, thats totally noticable and what i felt its at least 30minutes to one hour of difference. Add another 50minutes with some optimizations and we would really get awesome battery life in between apple and doze instead of a competition vs windows.

Now compare it vs windows that is using, like most of the people will, an antivirus sucking up performance and battery there would be very few reasons to use windows (corporation needs for special office functionality, thats it we couldnt come up with more after tsting the llibre suite and windows vs mac and linux).

---

### Post by tgalati4 on 2014-01-06
I'm on a Linux Mint 14 (based on 12.10) Acer laptop that someone gave me because Vista locked up.  I fixed Vista, but it will take a lot of money for me to boot back into it.  But, I'm satified with Mint's power handling.  I seem to get as good as Windows and that is good enough.

---

### Post by jan-goebel-g on 2014-01-06
Vista is the biggest failure OS ever, microsoft admitted it.
You should not compare windows and linux with those two, try to get windows 7 or even faster and better windows 8.1 which both got a nice boost to performance and therefore power usage.
As for my laptop, i love getting everything working out of the box with windows and linux, out of the box power management with windows is a lot better, tlp solves the problem and gets them on about the same level.
Mint then shows that it could be better.
Also, 12.10 is a lot worse then 13.10 and the Mint 14 is a LOT worse then the outstandingly great Mint 16.

So you should really consider upgrading if u can get the time to do it, u will benefit on windows and linux:)
New OS=faster OS, mostly everytime xcept for vista (win7 beats the hell out of xp and vista isnt even in the competition, same goes for the first 1year of unity and gnome3).

Atm im struggeling to choose a DE, i love cinnamon but i really like the unity screen estate with maximus+appmenu...im loosing focus, sorry just upgrade (use the 13.10 live cd/flashdrive, no need to install it)or try a live version, u wont regret it and then we can really compare:D

---

### Post by tgalati4 on 2014-01-07
I have several laptops and I do need to perform an upgrade cycle, but I am lazy.  I don't use Windows, so I won't be wasting my time with Windows7 or 8 or RT or Surface or Winphone--life is much too short to waste on Windows.  As for DE, I'm a fan of Gnome2 and MATE works fine for what I use it for.

---

### Post by jan-goebel-g on 2014-01-07
Its alright that u like mate but u get worse performance on it then with cinnamon and maybe even unity.
Its the same code that its based on but without the vast improvements they made with cinnamon or unity so u give up features to get the same performance out of it.
Point is, if u upgrade try cinnamon, put on classic mode so u get the look u want (two panels, on 27"and up thats maybe okay cuz you cant look at the whole screen at one time anyway).


Statusupdate: I took the time (while watching tv) to try and install unity and strip all the lenses out. I removed all of them, just leaving the home thing but seriously killing everything that could use the web, ubuntu one included.
Didnt change a thing, the service itself wont make a difference and as long as there is no sync going ubuntu one doesnt use up battery noticably, same goes for dropbox and the lenses (the search itself is the same plus zeitgeist for recent docs which im starting to like anyway).

Then i tried the 3.12 kernel, made it worse or the same i cant tell.
I tried latest mesa via ppa, didnt change a thing.
I tried bootoptions to enable some state of the gpu, cant tell the result but im gonna stick to it unless i notice its making things worse.

In the end i took a screenshot from powertop with less (i think, gotta make another one once its running mint again) wakeups, gpu, cpu-usage and its about 2w which is too much for it being the same core...
If we cant find it im gonna have to start contacting one of the devs since im getting more curious the more i look for a difference in the system and a solution to me getting the lovely unity(i like it:)) with mint performance.
Im gonna start with trying on getting a clean unity install on mint later i guess.

---

