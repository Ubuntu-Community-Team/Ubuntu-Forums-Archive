---
title: "CCSM now works in Gnome Classic"
date: 2011-12-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-12-29
Ta da.

[http://www.youtube.com/watch?v=7L7hyllXgrE](http://www.youtube.com/watch?v=7L7hyllXgrE)

---

### Post by ventrical on 2011-12-29
Thats confirmed on multiple PCs.

---

### Post by MacUntu on 2011-12-29
Didn't it before? :confused:

---

### Post by ventrical on 2011-12-29
> **MacUntu said:**
> Didn't it before? :confused:

Not that I know of . In fact that was a big issue with Oneiric testing. That CCSM did not work with Gnome Classic. It just started with  the 3.2.0-7 kernel. I  have other installs not yet updated to that kernel that will not allow CCSM to work. So defintely this is somthing left under the tree ! :)

---

### Post by MacUntu on 2011-12-29
Oh, that's Unity 2D - not Gnome Classic (gnome-session-fallback). !:*[I]*[/I]-)

---

### Post by ventrical on 2011-12-29
That sure is strange because it will not work with anything prior to 3.2.0-7 in Gnome Classic. I just  got a dead flat screen until now.

---

### Post by ventrical on 2011-12-29
Sorry MacUntu. CCSM is deader that a doornail in Gnome Classic on anything prior to the most recent kernel update.

---

### Post by seeker5528 on 2011-12-29
I'm pretty sure CCSM always worked no matter what your desktop environment was.

Don't know about compiz, but I thought I remembered seeing 'Gnome Classic' and 'Gnome Classic (No FX)' as separate session options a while ago so assumed it was working.

I thought they had it sorted out so Unity used different settings files, so when starting the Unity session you would have Unity enabled in Compiz even if you disabled it while in some other desktop session. Doesn't appear to be the case now.

Later, Seeker

---

### Post by mc4man on 2011-12-29
> **seeker5528 said:**
> I'm pretty sure CCSM always worked no matter what your desktop environment was.

Don't know about compiz, but I thought I remembered seeing 'Gnome Classic' and 'Gnome Classic (No FX)' as separate session options a while ago so assumed it was working.

I thought they had it sorted out so Unity used different settings files, so when starting the Unity session you would have Unity enabled in Compiz even if you disabled it while in some other desktop session. Doesn't appear to be the case now.

Later, Seeker

It has been sorted for awhile in a non-borked/unmodified install. 
The 'ubuntu' session uses the unity profile, the Gnome Classic, (fallback with effects) uses the Default profile. They aren't the same & don't get 'mixed' without some user help.

The only difference seen here from 11.10 to 12.04 is in 11.10, when choosing the "Gnome Classic" login, compiz would Not be loaded at login, it has to be started.
In 12.04 it is started at login.
In both cases you could use compiz in the Classic session if desired, doesn't seem to be a matter of kernel version. (at least in normal practice.

---

### Post by seeker5528 on 2011-12-30
> **mc4man said:**
> It has been sorted for awhile in a non-borked/unmodified install.

I think I deleted all the compiz* directories in .config at some point in the early going, when there were a lot of issues between Compiz and Unity, maybe in not finding a '.config/compiz/' directory when starting a non-Unity session it falls back to '.config/compiz-1/', but that's not the way I expect it to work.

Later, Seeker

---

### Post by ventrical on 2011-12-30
The whole reason I posted this thread was because  CCSM was not working in GNOME Classic on Precise (or Ocelot) for that matter). Thats why I joined Kansasnoobs' Gnome Classic Megathread, because  it was just going on and on that  anything GNOME 2(n) was obsoleted and we had to accept GNOME 3 or take Unity 3D and compiz with CCSM. So for 6 months I have been trying to get compiz CCSM to work on GNOME Classic with Precise alpha (as well as Ocelot) and then along comes 3.2.0-7 and CCSM can now  be conigured in Gnome Classic. So I guess my 11 Precise installs on 8 different PCs are all hybrids then ?

It fact it was stated again and again in the previous Ubuntu version that CCSM would not work in Gnome Classic (and it still will not in Oneiric) but now does with Precise.

So I guess its all relative .. yeah right :)

---

### Post by mc4man on 2011-12-30
> **seeker5528 said:**
> I think I deleted all the compiz* directories in .config ...

Later, Seeker

The file in there that was or is of interest is ~/.config/compiz-1/compizconfig/config.
By default/fresh install it's there but empty on a ubuntu session (unity-3d).

Empty on an ubuntu session would be the same as this - 
 [general_ubuntu]
profile = unity

It is possible to end up with  the Default profile on a ubuntu session, then something like this would be there - 
 [general_ubuntu]
profile = 

For a classic w/ compiz, Default profile,  there would be this section - 
[gnome_session]
profile = 

Though I guess someone could run Classic/compiz under the unity profile, as in - 
[gnome_session]
profile = unity

---

### Post by Bowmore on 2011-12-30
> **ventrical said:**
> The whole reason I posted this thread was because  CCSM was not working in GNOME Classic on Precise (or Ocelot) for that matter).Compiz works great both in Precise and Oneiric. Just tested Oneiric Gnome Classic too yesterday with the cube and other stuff. Just works. The only drawback is some flickering of windows when I rotate to another viewport. Happens to both Precise and Oneiric but might be a driver (nvidia-current) issue, hmm, guess not.

Actually didn't know about all of this a few days ago cause I'm mostly running Unity nowadays :P

---

### Post by mc4man on 2011-12-30
> **Bowmore said:**
>  The only drawback is some flickering of windows when I rotate to another viewport. Happens to both Precise and Oneiric but might be a driver (nvidia-current) issue, hmm, guess not.


The 'flickering' with rotate affects quite a number of users, a fix was mentioned for compiz but has not as yet shown any sign of being implemented

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198)

---

### Post by ventrical on 2011-12-31
> **Bowmore said:**
> Compiz works great both in Precise and Oneiric. Just tested Oneiric Gnome Classic too yesterday with the cube and other stuff. Just works. The only drawback is some flickering of windows when I rotate to another viewport. Happens to both Precise and Oneiric but might be a driver (nvidia-current) issue, hmm, guess not.

Actually didn't know about all of this a few days ago cause I'm mostly running Unity nowadays :P
Thanks  Bowmore. Thats news to me!! I'll update my occasions of Ocelot and see what happens because I tried that in GC 2 days ago and no cube,effects etc..

---

### Post by ventrical on 2011-12-31
> **mc4man said:**
> The 'flickering' with rotate affects quite a number of users, a fix was mentioned for compiz but has not as yet shown any sign of being implemented

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198)

 No flickering here .. CCSM never worked better in Gnome(classic).

---

### Post by ventrical on 2011-12-31
> **Bowmore said:**
> Compiz works great both in Precise and Oneiric. Just tested Oneiric Gnome Classic too yesterday with the cube and other stuff. Just works. The only drawback is some flickering of windows when I rotate to another viewport. Happens to both Precise and Oneiric but might be a driver (nvidia-current) issue, hmm, guess not.

Actually didn't know about all of this a few days ago cause I'm mostly running Unity nowadays :P


There is no way I can get CCSM to work in Oneiric on the Gnome Classic Desktop.  I'll keep at it.

---

### Post by Bowmore on 2011-12-31
> **mc4man said:**
> The 'flickering' with rotate affects quite a number of users, a fix was mentioned for compiz but has not as yet shown any sign of being implemented

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198)Thanks, that's just the one :D

---

### Post by kansasnoob on 2011-12-31
I've always preferred metacity over compiz anyway, just a matter of personal preference, so excuse my dumb question(s) :)

From what I've read some "actual work" is required to get classic to actually run compiz, is this true?

Two examples:

[http://mandriver.users.sourceforge.net/classic-gnome-guide.html](http://mandriver.users.sourceforge.net/classic-gnome-guide.html)

[http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/](http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/)

In the first they say:

> Get Compiz working

Compiz is the world's best window manager. Due to an error in gnome-session package, it doesn't start automatically and Metacity is used. This is already fixed for Precise, but if you want to get this working on Natty, open /usr/share/gnome-session/sessions/gnome-classic.session file as root and change

RequiredProviders=windowmanager;notifications;

line to

RequiredProviders=windowmanager;

Now Compiz should start automatically when you log in. You can easily switch back to Metacity by selecting ‘Gnome Classic (No effects)’ in the greeter. 

In the latter they say:

> Enable Compiz 3D Effects in Gnome Classic

In /usr/share/gnome-session/sessions/gnome-fallback.session change metacity to compiz under the heading DefaultProvider-windowmanager.

Note: You may also want to read the section "Stop the window decorator crashing" in that latter post because it concerns CCSM :)

Since I've never really been a fan of compiz it'd be cool if someone could lump all of the steps needed to run a classic compiz DE into one post ........... if they're so inclined :D

---

### Post by ventrical on 2011-12-31
> **kansasnoob said:**
> I've always preferred metacity over compiz anyway, just a matter of personal preference, so excuse my dumb question(s) :)

From what I've read some "actual work" is required to get classic to actually run compiz, is this true?

Two examples:

[http://mandriver.users.sourceforge.net/classic-gnome-guide.html](http://mandriver.users.sourceforge.net/classic-gnome-guide.html)

[http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/](http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/)

In the first they say:

 

In the latter they say:



Note: You may also want to read the section "Stop the window decorator crashing" in that latter post because it concerns CCSM :)

Since I've never really been a fan of compiz it'd be cool if someone could lump all of the steps needed to run a classic compiz DE into one post ........... if they're so inclined :D


@kansasnoob,

Thanks a million for this post.  First of all  I have no idea what Metacity is (so I will look into that).
I did however start learning CCSM when I first started Ubuntu  about 2 years ago. As I said previously, when i was beta testing 11.10 , CCSM was more or less blacklisted from being used in GnomeClassic (with effect). In fact I just tired to get it working in two installs on Ocelot and there is no way I can get it going like it is NOW running in Precise Pangolin!!

  What happened is that I was sharing some messages with @effenberg about the funny  bottom bar that showed up on my screen.  ***I didn't even log-in to Gnome Classic** Now, when I logged off and  then clicked to see, it showed I was logged in to Gnome Classic. The only reason I had been using Gnome Classic was to  try to benchmark some of your stuff from Gnome Classic Megathread . 


So .. there is this bottom bar and I'm wondering... 'what the E'll is this??' and then the Unity Launcher pops up and so I think I  am in Unity 3D so I do twirly cube, then log-off and I am not in Unuty 3D desktop, but, I am in Gnome Classic!!!!


  So I was completely befuddled by what had taken place.

  Anyways ... a long story short .. bravo !!!!   now I can have CCSM working with Gnome Classic in Precise if I want to swtich from Unity 3D.   I had made many posts about this in previous threads concerning 11.10 ... so either I missed the transition or I am not writng my expression correctly and  my emphasis  is being lost in translation.

thanks again..

---

### Post by kansasnoob on 2011-12-31
You can easily see what window manager you're using:

```
lance@lance-AMD-desktop:~$ wmctrl -m 
The program 'wmctrl' is currently not installed.  You can install it by typing:
**sudo apt-get install wmctrl**
lance@lance-AMD-desktop:~$ sudo apt-get install wmctrl
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  wmctrl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.7 kB of archives.
After this operation, 90.1 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe wmctrl i386 1.07-6 [21.7 kB]
Fetched 21.7 kB in 1s (17.5 kB/s)       
Selecting previously deselected package wmctrl.
(Reading database ... 191168 files and directories currently installed.)
Unpacking wmctrl (from .../wmctrl_1.07-6_i386.deb) ...
Processing triggers for man-db ...
Setting up wmctrl (1.07-6) ...
lance@lance-AMD-desktop:~$ **[COLOR="Red"]wmctrl -m[/COLOR]**
Name: **Metacity**
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A

```

As a matter of full disclosure I haven't tried that yet in Precise :)

---

### Post by kansasnoob on 2011-12-31
Yep, still works in Precise :)

---

### Post by ventrical on 2011-12-31
ventrical@ventrical-P4M266A-8237:~$ wmctrl -m
Name: Compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
ventrical@ventrical-P4M266A-8237:~$ 

"mode:OFF" ???

On this PC all the bells and whistles are working.

---

### Post by ventrical on 2011-12-31
After installing that program I can barely drag my windows.

It causes the dbus-daemon to run the processors high.

---

### Post by ventrical on 2011-12-31
Reboot solved that!

---

