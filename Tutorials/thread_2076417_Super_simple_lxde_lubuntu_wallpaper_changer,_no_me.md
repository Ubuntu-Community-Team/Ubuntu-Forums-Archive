---
title: "Super simple lxde lubuntu wallpaper changer, no memory usage, no crazy scripts"
date: 2012-10-26
forum: Tutorials
---

### Post by ronniew on 2012-10-26
Wallpaper changers on lxde or lubuntu are nice to have but tough to find, particularly if you are trying to stay lightweight. Usually wallpaper changers don't usually work because they aren't compatible with pcmanfm.

So after searching the Internet for quite some time and fiddling around I came up with a super easy, simple way to have a wallpaper changer on lxde / lubuntu without using any memory or complicated scripts or programs.

I tried the wallpaper changer called variety which i found on these forums... however it didn't work for me but also upon launch it was using about 40 megs of ram on my system just to change the wallpaper... not exactly lightweight, and it was always running in the background. 

I've also looked at some scripts and while they do work they are more complicated then they need to be... although i will say that they usually provide some type of timer wallpaper change feature, which this solution does not... however you'll see it really doesn't matter.

Ok here we go.

First lets make a desktop icon.

To create a desktop icon right click on the desktop and create a blank file. Name the file whatever you want just end it with .desktop I usually name the icon randomwallpaper.desktop

Once the file is created right click on it and open it with leafpad.

Copy and paste the following code in it

```
[Desktop Entry]
Version=1.0
Name=Random Wallpaper
Comment=Randomly change LXDE wallpaper.
Exec=bash -c 'pcmanfm -w "$(find ~/Pictures/Wallpapers -type f | shuf -n1)"'
Terminal=false
Type=Application
Categories=Utility;
Icon=wallpaper

```

Once the code is pasted close and save it.

Now I'm going to assume your new icon is on the desktop

We will place this icon in two place... 

One in your autostart folder (which provide a random background on startup)

And the other one will go in your applications folder (which will provide access to it through your accessories menu.)

Open your terminal and enter these commands

cd Desktop
cp randomdesktop.desktop ~/.config/autostart
sudo mv randomdesktop.desktop /usr/share/applications

Open up desktop session settings (preferences menu) and make sure the Random Desktop icon is checked if you want it to change your desktop background on startup. 

**Finally and important**... create a folder named Wallpapers inside your Pictures folder and place your desktop backgrounds in there..

Now whenever your computer starts it changes the background and if you want to change it yourself you can select random wallpaper from the accessories menu and it will switch it instantly.

This is an excellent no memory usage, super easy wallpaper changer solution without involving complicated scripts or heavy programs.

[IMG]http://www.unleashpc.com/wallpaperchanger.png[/IMG]

CAUTION: This has only been test on Lubuntu 12.04

*****
**I will be providing a series of easy solutions and linking to them below**
[URL="http://ubuntuforums.org/showthread.php?t=2076351"]
lxde simple weather[/URL]
[aero snap for lubuntu]("http://ubuntuforums.org/showthread.php?p=12318519")
[expose feature for lubuntu]("http://ubuntuforums.org/showthread.php?p=12318587")

---

### Post by mörgæs on 2012-10-26
Thanks, but please post these guides in 
[https://help.ubuntu.com/community/Lubuntu/Documentation](https://help.ubuntu.com/community/Lubuntu/Documentation)
in order to have everything in one place.

We are trying to move stuff of long-time value to the wiki and use the forum mainly for support questions.

---

### Post by ankspo71 on 2012-10-28
Thanks for the tip. 

Unfortunately I am unable to use it in a stock Lubuntu 12.10 because I am affected by a bug in pcmanfm 1.0.1-0ubuntu1, where pcmanfm refuses to launch after setting the wallpaper by command. The latest git version 1.0.2-alpha1 fixes the bug though, which I was able to temporarily test on a non-persistant liveusb. Bug: [http://sourceforge.net/tracker/?func=detail&aid=3578503&group_id=156956&atid=801864](http://sourceforge.net/tracker/?func=detail&aid=3578503&group_id=156956&atid=801864)

---

### Post by ronniew on 2012-10-28
i reported that bug early on, glad to see its been fixed in the latest build

which you might be able to get from here

[https://launchpad.net/ubuntu/+source/pcmanfm](https://launchpad.net/ubuntu/+source/pcmanfm)

---

### Post by ronniew on 2012-10-28
> **xfctr said:**
> and being heavy on resources, neither of which is true.

I guess I'm old school, anything over 10 megs for a wallpaper changer seems crazy. (in truth anything over 5)

In my mind ram is the single most valuable resource in your computer that you actually have quite a bit of control over. There has never been a time that saving as much ram as possible wasn't a good thing.

---

### Post by xfctr on 2012-10-29
> I guess I'm old school, anything over 10 megs for a wallpaper changer seems crazy. (in truth anything over 5)

Try this utterly simple Python program - on my machine it eats 8.8 mb RAM (reported by System Monitor, roughly one third of what it reports for Variety here).

```
from gi.repository import Gtk
win = Gtk.Window()
win.connect("delete-event", Gtk.main_quit)
win.show_all()
Gtk.main()
```

5-10 years ago 5 MB would have been a reasonable expectation using the modern technologies of that time. Not now. Reason is simple - RAM is cheap, everyone simply prefers using clean easily maintainable high-level code to highly optimized low-level code, so every tier in the application stack consumes more RAM than several years ago (VM, UI toolkit, application code, etc.). Things add up and now an application that displays one empty window consumes 9 mb RAM.

A full-featured wallpaper changer can fit in 5 mb only if coded in low-level C, hand-crafted for a particular type of use-case, with no GUI, or using some very light non-standard UI toolkit. This won't be a general solution that people can install and use in a user-friendly manner.

Another experiment: try running the find/shuf command on a big directory tree (several thousand files) several times in a row. See how much time and HDD activity the first run takes and then how much faster the next runs are. This is because the OS caches the results. You cannot easily measure this memory consumption, but it is there, simply not allotted to a specific process. There is no escaping - you either have to trash the disk heavily every time, or you need to cache something and consume RAM. Speed vs memory usage is pretty much a "law of nature" - there is always need for compromising between them.

---

### Post by ronniew on 2012-10-29
There is no thrashing of the hard drive that goes on, unless you are changing the wallpaper ever 10 seconds like you suggested in a previous post... 

who is changing their wallpaper every 10 seconds with multiple thousands of images?  if they are they don't need a wallpaper changer they need a slideshow program

that being said.... something that run then exits, get the job done and consumes no ram is in my mind a better solution...

thrashing of the hard drive may have been a concern 15 yrs ago, now however i feel it used as an excuse for overly complicated solutions.

---

### Post by xfctr on 2012-10-29
I said it earlier - your approach is elegant, but will only serve some people. From there on, you seem to ignore any possibility that the use-case your solution covers is not the only one possible or that users may want something more than the mere basics, like filtering by image size or automatic downloading of new wallpapers so that they don't look at the same several hundred images till they know them by heart. Also you seem to confuse "simple" and "lightweight" - they are different things that don't necessarily go together, and same goes for "complex", "featureful" and "heavy".

> something that run then exits, get the job done and consumes no ram is in my mind a better solution...
I said it before, a "better solution" is a subjective matter: my exact words were "this very strongly depends on the usage pattern and how you value things" - "things" meaning CPU and memory consumption, features, simplicity of usage, etc, etc. 

Judging by the feedback, Variety is clearly a great solution for a lot of people. It doesn't suit you - I understand this, but please refrain from putting labels on it that don't represent reality.

---

### Post by ronniew on 2012-10-29
listen man, i came here to post my simple solution for anyone who wanted it... i'm sorry i mentioned your program to be honest it would have saved a lot of unecessary typing if I hadn't. 

Soon as I did I'm being slammed for offering a solution outside of your ingenious this program fits all because its perfect attitude. 

I'm sorry if I put a dent in your ego over your creation. Sorry I mentioned it. Trust me I will not being doing so ever again.

To be honest no one really gives a crap about either of our creations. They are going to use what they are going to use. The idea is to offer it and let others decide what they want. 

You don't need to play defender over your ideas or creations. You only need to know why you are doing them.

Maybe you should study the following about your program:

in your reality its great

in my reality its unnecessary..

who knows what other peoples reality might be

you don't get to dictate reality, 

only the individual does.


**** Now please shut up about it

---

### Post by xfctr on 2012-10-30
Man, cool off :-) I'm not slamming you for your solution, just asked you to not put false labels on mine. You are right this time, too much typing about it. See you around.

---

### Post by ankspo71 on 2012-11-08
I just noticed a newer pcmanfm in the raring ringtail repositories, so I installed it to give it a try. It is version  1.1.0-0ubuntu1 and so far it is working good in Lubuntu 12.10 after setting the wallpaper from command line.

[https://launchpad.net/ubuntu/+source/pcmanfm](https://launchpad.net/ubuntu/+source/pcmanfm)
or
[http://packages.ubuntu.com/search?keywords=pcmanfm&searchon=names&suite=raring&section=all](http://packages.ubuntu.com/search?keywords=pcmanfm&searchon=names&suite=raring&section=all)

---

### Post by ronniew on 2012-11-09
sweet , thx for the update, now I can rest assured knowing that when I do upgrades on everyones machines in the future, that their random wallpaper will keep working.... nice

---

### Post by Dencrypt on 2012-12-15
Best solution I've found for this purpose on any system so far. Thanks for this superior idea ):P

---

### Post by ronniew on 2012-12-28
no problem, glad it came in handy.

---

### Post by MalWiggin on 2013-01-20
> **ankspo71 said:**
> Unfortunately I am unable to use it in a stock Lubuntu 12.10 because I am affected by a bug in pcmanfm 1.0.1-0ubuntu1, where pcmanfm refuses to launch after setting the wallpaper by command.

I had the same problem but noticed that pcmanfm would still start from a shortcut to a folder, but wouldn't start from it's base application.  It meant that I could easily start it up with a shortcut to the home folder on the desktop, but the application launch bar shortcut didn't work.  

You can fix that by editing the desktop configuration file for the PCManFM application to direct it to open to a specific file.

To do this, open the terminal and type the following:
cd usr/share/applications
sudo leafpad pcmanfm.desktop

Now scroll down and find the line:
Exec=pcmanfm %U

Here you need to change the "%U" to your preferred default folder.  I use /home/malwiggin so the line reads:
Exec=pcmanfm /home/malwiggin

Save the file, and your File Manager should start as normal now.

---

### Post by seppalta on 2013-01-21
For an automatic  wallpaper *rotator *(slide show) script, rather than just a changer, see 
[http://lxlinux.com/#5](http://lxlinux.com/#5).

---

### Post by MrZorg2012 on 2013-01-24
> **ankspo71 said:**
> Thanks for the tip. 

Unfortunately I am unable to use it in a stock Lubuntu 12.10 because I am affected by a bug in pcmanfm 1.0.1-0ubuntu1, where pcmanfm refuses to launch after setting the wallpaper by command. The latest git version 1.0.2-alpha1 fixes the bug though, which I was able to temporarily test on a non-persistant liveusb. Bug: [http://sourceforge.net/tracker/?func=detail&aid=3578503&group_id=156956&atid=801864](http://sourceforge.net/tracker/?func=detail&aid=3578503&group_id=156956&atid=801864)

Yeah mine too. So I had to remove this, too bad, it was kinda cool. :-)

---

### Post by offgridguy on 2013-01-27
Thanks  for this thread.:D

---

### Post by Jakopc on 2013-02-02
Thanks very much for this nice tutorial! :D
The only thing is that the manual switching via the menu is not always reacting, any clue why?

---

### Post by jonbfl on 2013-04-07
Great little script - I used it on Fedora 16/LXDE - zero probs, thanks very much. It was just exactly what I was looking for! :KS


One note - in the instructions, ronniew says "Name the file whatever you want just end it with .desktop I usually name the icon randomwallpaper.desktop"

for the not too observant or a 'noob' - that could cause an 'ooops' later

> Open your terminal and enter these commands

 cd Desktop
 cp randomdesktop.desktop ~/.config/autostart
 sudo mv randomdesktop.desktop /usr/share/applications 

the example filename is [I]randomwallpaper.desktop

[/I]Thanks again - 
:cool:

---

### Post by momist on 2013-07-11
OK, this is a bit wierd.  I have newly installed Lubuntu 13.04, but with a separate pre-existing /home partition.  When I use this wallpaper changer, all I get is a new PCManFM file window open at my home directory.  The wallpaper doesn't change.  

I've deleted it all and gone throught the process of creating it again with the same results.  I've checked the entries in ~/.config/autostart and in /usr/share/applications and I can't find what I may have done wrong.  Can anyone suggest where I look next?

Thanks.

P.S. it works fine on my laptop which was running 12.04 and continues to work after a dist-upgrade.

---

### Post by momist on 2013-07-12
My bad.  My wallpapers are all symlinks to files within my photos, many gigabytes worth.  It seems this code doesn't work with symlinks.  I've put in a test folder with real images, and it works fine with that.

SOLUTION:
Amend the 'find' function with the parameter -L, as follows:
Exec=bash -c 'pcmanfm -w "$(find -L /data/WallpaperLinks -type f | shuf -n1)"'

This overrides the default action of 'find' to make it follow symbolic links.  See 'man find'.

HTH someone.

---

### Post by iain_m2 on 2014-02-26
Hey thanks man... This was exactly what I wanted for my Lubuntu Asus Eeepc. No resource hog and just works.

---

### Post by 1leenie on 2014-05-15
Need new instructions for Lubuntu 14.04. "Random Wallpaper" does not show on the list of automatically started applications in LXSession configuration in Autostart section.

---

### Post by uvbphxfn on 2014-05-17
Thanks [**[COLOR=#000000]ronniew[/COLOR]**]("http://ubuntuforums.org/member.php?u=37749"), thanks for making this script, it works great on my ArchLinux LXDE. However, I noticed a problem, which you may consider adding to the OP.

Sometimes the script starts too soon, before pcmanfm has started. This results in a error window and the wallpaper not changing.

I have been able to "fix" this problem by adding a polling loop before the pcmanfm call, as in

```
until [ $(pidof pcmanfm) ]; do sleep 0.2; done;
```

On my specific case, I also wanted to be able to specify the wallpaper mode, because I was using this on a volatile /home folder (granted, this is not a typical use case), so I added:

```
--wallpaper-mode=fit
``` before the ending apostrophe.

E.g. my final line looks like this:

```
Exec=bash -c 'until [ $(pidof pcmanfm) ]; do sleep 0.2; done; pcmanfm --set-wallpaper="$(find ~/.wallpapers -type f | shuf -n1)" --wallpaper-mode=fit'
```

PS: <snip ubuntuforums, it's a nightmare to register.

---

### Post by rmcellig on 2015-01-20
How can I run this from a Crontab?

---

### Post by os2 on 2015-01-20
script.sh,

and cronfile in say /etc/cron.d/cronfile as in the following format:

```

mm hh * * * user /home/user/script.sh

```

---

### Post by brunoleaotm on 2015-07-19
Hello, i am new here so, don't shot any bullets at me, ok?

I have tried this solution in my previous installation of lubuntu 14.04, at the same computer (Hp Pavilion dv6500) and it worked greatly, with no problems. I had make this change at the original solution: line 5: Exec=bash -c 'pcmanfm -w "$(find /usr/share/backgrounds -type f | shuf -n1)", nothing great...

Here is the bug: I have formatted my computer, installed the same lubuntu 14.04, updated the SO, but sometimes when i turn on the computer, the following message appears on a box: "The desktop manager is not active" and no wallpaper is shown in the background (black screen). Sometimes it works, sometimes not. If o log off the user and log on again the wallpaper is shown and changed.

Any ideas on how to fix it?

Thank you guys. Any problems with my English, please tell me :D

PS: If i remove the icon from the autostart folder this problem do not happens anymore, but... i wanna the changer >.<

---

### Post by sergio53 on 2016-01-07
Wuhu I finally decided to be part of a forum! Hello World!

Tested code on Kali Linux running LXDE and it works like a charm! Thanks OP!

---

### Post by William_Chamberlai on 2016-01-30
Thanks: works perfectly.
Your command-line script needs to be updated for consistency with your preferred file name though:  
```

cd ~/Desktop
cp randomwallpaper.desktop ~/.config/autostart
sudo mv randomwallpaper.desktop /usr/share/applications

```

---

