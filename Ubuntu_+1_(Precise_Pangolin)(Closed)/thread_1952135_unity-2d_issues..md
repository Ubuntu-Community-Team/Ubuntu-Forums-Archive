---
title: "unity-2d issues."
date: 2012-04-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by White-Energy on 2012-04-03
Well i've upgraded from 11.10 to 12.04 this night.. but i might seem to have a problem here..
when i do $ sudo apt-get dist-upgrade
I get this

```
adam@Adam-Laptop:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 unity-2d-launcher : Depends: libunity-2d-private0 (= 4.12.0-0ubuntu1.1) but 5.8.0-0ubuntu1 is installed
 unity-2d-places : Depends: libunity-2d-private0 (= 4.12.0-0ubuntu1.1) but 5.8.0-0ubuntu1 is installed
 unity-2d-shell : Breaks: unity-2d-launcher (< 5.4~) but 4.12.0-0ubuntu1.1 is installed
                  Breaks: unity-2d-places (< 5.4~) but 4.12.0-0ubuntu1.1 is installed
E: Unmet dependencies. Try using -f.

```

I try to use the $sudo apt-get -f install
and i get this
```
adam@Adam-Laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  unity-2d-launcher unity-2d-places
The following packages will be upgraded:
  unity-2d-launcher unity-2d-places
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/3,420 B of archives.
After this operation, 874 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: warning: there's no installed package matching unity-2d-launcher:all
dpkg: warning: there's no installed package matching unity-2d-places:all

```

I've tried to remove/reinstall everything but it fails to do so..

One thing is that is annoying right now is the sidebar that is on the left is not hiding i have no idea how to get it to work..

Thank you in advance.

---

### Post by grahammechanical on 2012-04-03
Are you using Ubuntu (Unity 3D) or Ubuntu 2D?

If it is 3D open System Settings and go to Appearance, click on the behaviour tab. You will see a slider that controls the auto-reveal behaviour of the launcher. Click it to ON.

If it is already on then you have a much harder problem to solve.

If you are loading to a working desktop then I would advise that you wait a bit for things to be sorted out. This situation might be corrected in a day or two.

I have two installs of 12.04. On my default beta 2 install an update last night brought in kernel 3.2.0-21.

But the update to my other 12.04 which I have been using since Alpha 1 did not get kernel 3.2.0-21 it was still at kernel 3.2.0-18. So, I upgraded the kernel.

Now when I boot into it the Unity desktop does not load and it tries to get into 2D but fails because there obsolete packages present. And I am left with just the background wallpaper.

So, I am back to using the kernel 3.2.0-18.

Anyway I am guessing that we are in the middle of some updates being made to Unity 2D that are only partially available. I have experienced this kind of thing before.

Can you get a working Desktop? I am not an expert but Unity 2D should be at 5.8 but It looks to me that In the first place it was trying to install unity-2d-launcher and unity-2d-places and it wanted Unity 4.12 to go with it but Unity 5.8 was installed.

You can try running sudo apt-get install -f again or opening the Update Manager and running the update from there. I once got better results do that then using the apt-get install -f command.

You can also check the Settings of Update Manager, the System Sources, are they Precise or is there one that is still Oneiric.

This is all I can think of.

Regards.

---

### Post by White-Energy on 2012-04-04
> **grahammechanical said:**
> Are you using Ubuntu (Unity 3D) or Ubuntu 2D?

If it is 3D open System Settings and go to Appearance, click on the behaviour tab. You will see a slider that controls the auto-reveal behaviour of the launcher. Click it to ON.

If it is already on then you have a much harder problem to solve.

If you are loading to a working desktop then I would advise that you wait a bit for things to be sorted out. This situation might be corrected in a day or two.

I have two installs of 12.04. On my default beta 2 install an update last night brought in kernel 3.2.0-21.

But the update to my other 12.04 which I have been using since Alpha 1 did not get kernel 3.2.0-21 it was still at kernel 3.2.0-18. So, I upgraded the kernel.

Now when I boot into it the Unity desktop does not load and it tries to get into 2D but fails because there obsolete packages present. And I am left with just the background wallpaper.

So, I am back to using the kernel 3.2.0-18.

Anyway I am guessing that we are in the middle of some updates being made to Unity 2D that are only partially available. I have experienced this kind of thing before.

Can you get a working Desktop? I am not an expert but Unity 2D should be at 5.8 but It looks to me that In the first place it was trying to install unity-2d-launcher and unity-2d-places and it wanted Unity 4.12 to go with it but Unity 5.8 was installed.

You can try running sudo apt-get install -f again or opening the Update Manager and running the update from there. I once got better results do that then using the apt-get install -f command.

You can also check the Settings of Update Manager, the System Sources, are they Precise or is there one that is still Oneiric.

This is all I can think of.

Regards.

I've been using unity 3d yesterday and today it did not work just a wallpaper nothing else shows.. only unity-2d works now.. weird..
I tried the Update Manager and every possibility to solve this but i keep failing to fix it.. i think the only way to do it is to install the Precise from scratch.. seems like updating from ubuntu version to another is buggy (isnt the first time.. i've experienced bugs when upgrading from 10.04 to 10.10 before..) My only problem right now is.. how will have the access to my Encrypted /data after re installing ubuntu.. anyway to do it ?

---

### Post by grahammechanical on 2012-04-04
I agree with you about the value of a fresh install. It is what I will be inclined to do when I change my 11.10 into 12.04 after 12.04 is officially released.

Can you not boot into an earlier kernel? I suppose not. May I suggest that you boot into rescue mode and use the command line to update.

Here is a link to some commands that you might use:

[https://wiki.ubuntu.com/U+1/tester-wiki]("https://wiki.ubuntu.com/U+1/tester-wiki")

Go down to the section called Sudo Code Quick Grabber.

Regards.

---

### Post by White-Energy on 2012-04-04
in rescue mode, should i just 
```
$sudo apt-get update && sudo apt-get upgrade
```
or
```
$sudo apt-get update && sudo apt-get dist-upgrade
```

i'm afraid of getting badly working updates.. 
:)

---

### Post by cariboo on 2012-04-04
> **White-Energy said:**
> in rescue mode, should i just 
```
$sudo apt-get update && sudo apt-get upgrade
```
or
```
$sudo apt-get update && sudo apt-get dist-upgrade
```

i'm afraid of getting badly working updates.. 
:)

That's why we recommend when running a testing version, that you install it beside a stable release, so that you can repair problems that you run into.

---

### Post by White-Energy on 2012-04-04
Sadly i upgraded directly from 11.10 to 12.04 without thinking about the consequences i'll be facing.. too bad that i updated and lost my stable release.. 
you can never beat stupidity until you face the consequences :(

---

### Post by White-Energy on 2012-04-05
Can this thread be marked as Solved ?
I've re-installed Ubuntu.. and it works perfectly without having my /home partition touched.

---

### Post by ventrical on 2012-04-05
> **White-Energy said:**
> Can this thread be marked as Solved ?
I've re-installed Ubuntu.. and it works perfectly without having my /home partition touched.

I'm just curious if you had CCSM installed .. if you do .. log-in to Unity 2D, open CCSM and tic off Unity Plug-in because there were some updates that wiped out all compiz settings a day or so ago.

---

### Post by ventrical on 2012-04-05
> **grahammechanical said:**
> Are you using Ubuntu (Unity 3D) or Ubuntu 2D?

If it is 3D open System Settings and go to Appearance, click on the behaviour tab. You will see a slider that controls the auto-reveal behaviour of the launcher. Click it to ON.

If it is already on then you have a much harder problem to solve.

If you are loading to a working desktop then I would advise that you wait a bit for things to be sorted out. This situation might be corrected in a day or two.

I have two installs of 12.04. On my default beta 2 install an update last night brought in kernel 3.2.0-21.

But the update to my other 12.04 which I have been using since Alpha 1 did not get kernel 3.2.0-21 it was still at kernel 3.2.0-18. So, I upgraded the kernel.

Now when I boot into it the Unity desktop does not load and it tries to get into 2D but fails because there obsolete packages present. And I am left with just the background wallpaper.

So, I am back to using the kernel 3.2.0-18.

Anyway I am guessing that we are in the middle of some updates being made to Unity 2D that are only partially available. I have experienced this kind of thing before.

Can you get a working Desktop? I am not an expert but Unity 2D should be at 5.8 but It looks to me that In the first place it was trying to install unity-2d-launcher and unity-2d-places and it wanted Unity 4.12 to go with it but Unity 5.8 was installed.

You can try running sudo apt-get install -f again or opening the Update Manager and running the update from there. I once got better results do that then using the apt-get install -f command.

You can also check the Settings of Update Manager, the System Sources, are they Precise or is there one that is still Oneiric.

This is all I can think of.

Regards.

  I have Unity 2D working on one of my Intel machines with the 3.2.0-21 kernel , no problems - however the graphical log-on 'bug of the century' is back !  when I log in to Unity 2D.

---

### Post by ventrical on 2012-04-05
Doh .. here comes  3.2.0-22 down the pipe.!

---

### Post by ventrical on 2012-04-05
All is well here with Unity 2D with new 3.2.0-22 kernel and updates. This being off a development upgrade from October.

---

### Post by ventrical on 2012-04-05
> **White-Energy said:**
> Can this thread be marked as Solved ?
I've re-installed Ubuntu.. and it works perfectly without having my /home partition touched.


My apologies  I didn't see this part.

---

### Post by White-Energy on 2012-04-05
Nope I did not have ccsm installed..
i thought ccsm was just a compiz manager.. 
unity-3d works with compiz..
unity-2d doesn't work with compiz i think.. so that explains why unity-2d works fine while unity-3d is buggy.. anyway i must say **DO NOT UPGRADE FROM 11.10 to 12.04 (b)**

a funny thing happened hours ago.. i had a [yellowish unity panel bug]("http://ubuntuforums.org/showthread.php?p=11820603").. it took me hours to solve.. ueehhhhh bugs *sigh*

---

