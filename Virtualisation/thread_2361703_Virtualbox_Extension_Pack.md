---
title: "Virtualbox Extension Pack"
date: 2017-05-19
forum: Virtualisation
---

### Post by shane_faulkinbury2 on 2017-05-19
I reinstalled my entire system to Ubuntu 16.04 LTS and I installed Virtualbox with```
sudo apt-get install virtualbox
```

I downloaded the extension pack for 5.0 since I couldn't install the latest versions extension pack.   When I tried to install it, it told me I had 5.1.22.  ```
Failed to install the Extension Pack **/home/richard/Downloads/Oracle_VM_VirtualBox_Extension_Pack-5.1.22-115126 (1).vbox-extpack**.VBoxExtPackRegister returned VERR_VERSION_MISMATCH, pReg=0000000000000000 ErrInfo='VirtualBox version mismatch - expected 5.1 got 5.0'.
[TABLE="width: 100%"]
[TR]
[TD]Result Code: [/TD]
[TD]NS_ERROR_FAILURE (0x80004005)[/TD]
[/TR]
[TR]
[TD]Component: [/TD]
[TD]ExtPackManagerWrap[/TD]
[/TR]
[TR]
[TD]Interface: [/TD]
[TD]IExtPackManager {edba9d10-45d8-b440-1712-46ac0c9bc4c5}[/TD]
[/TR]
[/TABLE]


```

How can I fix this?  I really need to get items for my Windows 10 on Virtualbox.  Please help.

---

### Post by CharlesA on 2017-05-19
The extension pack is for use with the version of VirtualBox you get from the website, not the one in the Ubuntu repos.

Are you installing it from that repos listed here? [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by shane_faulkinbury2 on 2017-05-19
I sure did install it from Ubuntu Software Center.  I guess I should install it from here?  [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

That's actually the same .deb I installed from the Ubuntu Software Center.  Where do I get the one you speak of?

---

### Post by howefield on 2017-05-20
Going here [http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/) and clicking on the matching virtualbox version that you have installed should give you the relevant extension pack.

Exactly which version of Virtualbox have you installed, is it 5.0.18 ?

```
vboxmanage --version
```

---

### Post by shane_faulkinbury2 on 2017-05-21
Hmm, I must of purged it.  So I tried to install the package from the link you provided and this is what happens.

I finally got Virtualbox 5.1.225 to partially install.  The reason I say partially is because the install bar has been stuck right before almost complete for about an hour.  I tried to go ahead and fire it up and here are the errors I get including screen shots of me firing it up as root and the error I got.  Please help again!  :confused:

---

### Post by #&amp;thj^% on 2017-05-22
See if this helps:
```
sudo rcvboxdrv setup
```
I think DKMS may be a miss here...anyway let us know if this works.

---

### Post by shane_faulkinbury2 on 2017-05-22
I can't get that command to go.

---

### Post by #&amp;thj^% on 2017-05-22
Bummer :(...Ok lets see if this will poke it then:```
sudo /usr/lib/virtualbox/vboxdrv.sh setup

```

---

### Post by shane_faulkinbury2 on 2017-05-22
Nope, I get the same two error boxes.

---

### Post by #&amp;thj^% on 2017-05-22
I would file a bug>> or check to see if there is one already filed.  Here: [https://www.virtualbox.org/wiki/Bugtracker](https://www.virtualbox.org/wiki/Bugtracker)
In the meantime I'll see if I can recreate your problem.
I'll be back in any case.

---

### Post by #&amp;thj^% on 2017-05-23
Well as I don't seem to be able to reproduce the problem...and this is just a guess on my part.
But it is possible that there are mixed packages in your install with VB
This is the version that I installed:
```
$ vboxmanage --version
5.1.22r115126

```
And no errors with:
```
$ sudo rcvboxdrv setup
vboxdrv.sh: Stopping VirtualBox services.
vboxdrv.sh: Building VirtualBox kernel modules.
vboxdrv.sh: Starting VirtualBox services.

```
So just to be clear...this is the one I installed:
```
virtualbox-5.1/now 5.1.22-115126~Ubuntu~zesty amd64 [installed,local]
  Oracle VM VirtualBox

```
I would try removing  the packages you have installed..and reinstall with the proper packages.
Sorry not more helpfull...but if i can't reproduce I can't find a fix or work-around. :(
NOTE: I did use "gdebi" to install the .deb I downloaded.

---

### Post by shane_faulkinbury2 on 2017-05-24
Thanks a lot 1fallen, this command did the trick!   I'm up and running again.  :D  I must have missed this one the other day.

:cry:  

> [COLOR=#000000][FONT=&quot]sudo /usr/lib/virtualbox/vboxdrv.sh setup[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2017-05-24
Awesome! ;)
Happy VB-ing

---

### Post by shane_faulkinbury2 on 2017-06-02
I had to mark this thread as unsolved after marking it solved because it worked on my old system.  Now I've reinstalled Ubuntu 16.04 and I can't get Virtualbox 5.1.22-115126 to load.  I don't know what the problem could be since my entire system is updated.

---

### Post by #&amp;thj^% on 2017-06-02
Can I ask why you want/need the Precise(12.04) Deb instead of the one for xenial (16.04)

---

### Post by shane_faulkinbury2 on 2017-06-02
Sorry, I downloaded the wrong deb, but have since downloaded the correct one and it does the same thing!

---

### Post by #&amp;thj^% on 2017-06-02
> **shane_faulkinbury2 said:**
> Sorry, I downloaded the wrong deb, but have since downloaded the correct one and it does the same thing!

hehehe ;) Ok all square now

Any errors shown?

---

### Post by shane_faulkinbury2 on 2017-06-02
:(

---

### Post by #&amp;thj^% on 2017-06-02
Welp I guess we start here:
paste back this from the terminal:
```
vboxmanage --version
```
EDIT: shane_faulkinbury2 are you saying it won't install the .deb?
If yes then just install gdebi...then install it with gdebi.
I flat hate software center and package managers, but thats just me.:)
How ever I do use synaptic and gdebi on occations.
I install all Virtual Box debs with gdebi and no problems on my installs.

---

### Post by shane_faulkinbury2 on 2017-06-02
Well low and behold it installed after I did a reboot!  I figured it wasn't working because I tried to install the other version of Virtualbox.  I did a reboot and installed the version posted by howefield and everything is working now.  Now I just have to install Windows 10 and then the extension pack to make sure everything works, but it should just like before the reinstall!  :)

Hmm, how do I load the kernel driver?

Well it appears I have to remove it, but when I do I get this error.  When I fire up Software it says install, but clicking the install button does nothing.

---

### Post by #&amp;thj^% on 2017-06-03
> **shane_faulkinbury2 said:**
> Hmm,_** how do I load the kernel driver**_?

```
sudo rcvboxdrv setup
[sudo] password for me: 
vboxdrv.sh: Stopping VirtualBox services.
vboxdrv.sh: Building VirtualBox kernel modules.
vboxdrv.sh: Starting VirtualBox services.


```
And:
```
vboxmanage --version
5.1.22r115126

```
Again gdebi Rocks...Software-center>>>not so much :P
But you seem stuck in your ways.:)
With the install from [U][B]gdebi :
[/B][/U]```
sudo apt remove --purge virtualbox-5.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  virtualbox-5.1*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 161 MB disk space will be freed.
Do you want to continue? [Y/n] n

```
I have no idea how to help here.

---

### Post by #&amp;thj^% on 2017-06-03
> **shane_faulkinbury2 said:**
> Well it appears I have to remove it, but when I do I get this error.  When I fire up Software it says install, but clicking the install button does nothing.

Dang I wish you would more clear here!! Screenshots just leaves me at least guessing here>
Okay I guess you are now trying to install>> The ExtPack but it needs to write to the VirtualBox directory. This has typically restricted access  for users (read-only).
    So you need to run VirtualBox as administrator (right-click, Run as Administrator).
    Or just open the terminal and run:
```
sudo virtualbox
```
    Go to the VirtualBox Manager>> preferences<<, Extensions and install the ExtPack.
    Close VirtualBox.
    Run VirtualBox again as your normal user.
Just need more input from you as to what your trying to do.

---

### Post by shane_faulkinbury2 on 2017-06-03
Nope, it does the same thing as administrator.  I tried purge, but that did nothing.  When I run the package again it opens Software and it still says install.  I'm at a lose here!

---

### Post by #&amp;thj^% on 2017-06-03
> **shane_faulkinbury2 said:**
> Nope, it does the same thing as administrator.  I tried purge, but that did nothing.  When I run the package again it opens Software and it still says install.  I'm at a lose here!

What dose the same thing??? :confused: Installing Virtual Box or Installing the ExtPack?
See what I mean :).... please try to be more helpful here.
IE: I'm having problems installing Virtual Box (and version and arch 64/32 bit) blah blah.
Or I,m having Problems installing the the ExtPack in VB.
So where are you at right now?  Is Virtual Box installed?

---

### Post by shane_faulkinbury2 on 2017-06-03
I just put in "not installing on Ubuntu 16.04" and get only 4 results that have nothing to do with my issue.  Should I try something else?

---

### Post by #&amp;thj^% on 2017-06-04
In the terminal, type:

```
sudo apt install gdebi
```

You can right click on the VirtualBox .deb file and select to open it with Gdebi.

If you like Gdeb, you can make it default to have it open all the .deb files in future.

Read this: [https://itsfoss.com/gdebi-default-ubuntu-software-center/](https://itsfoss.com/gdebi-default-ubuntu-software-center/)

---

### Post by shane_faulkinbury2 on 2017-06-04
Thanks a lot 1fallen, gdebi worked perfectly!  I'll get to the extension pack when I get home this evening!

I just have to ask, why aren't you a moderator?  you have great Ubuntu knowledge and have helped me many times!

---

### Post by #&amp;thj^% on 2017-06-04
I'm best right where I'm at.:D
Thanks though, I appreciate the kind  sentiment.;)
Besides I think the staff here is just the best bar none...as is.
Kind Regards

---

### Post by shane_faulkinbury2 on 2017-06-04
Well I got home installed Windows, installed updates, shut it down,, ran the extension pack and everything went fine.  I fired Windows back up, plugged me flash drive in and nothing!  Should I run it again just to make sure everything installed correctly?

---

### Post by #&amp;thj^% on 2017-06-05
> **shane_faulkinbury2 said:**
> Well I got home installed Windows, installed updates, shut it down,, ran the extension pack and everything went fine.  I fired Windows back up, plugged me flash drive in and nothing!  Should I run it again just to make sure everything installed correctly?
Nope you shoiuld not need to install the extentions again, but some other steps are needed.
Open your terminal and run:
```

sudo adduser $USER vboxusers

```
Log out and Log in again.
Now Attach to your PC the USB devices you want to be automatically mounted in the VM (virtual machine).
Open Virtualbox
   1.) Select your VM and go to "Machine" -> "Settings" -> "USB".
   2.) Check "Enable USB Controller"; click on the icon with the USB plug and the plus, and click on the devices you want to be automatically mounted in the VM. Click "Ok".

Click on "Start" toolbar button, and ensure your USB devices are recognized and mounted by the VM. 
Just to be sure...after your VB session is up...At the top of your screen>>>you will see:
**<File>, <Machine>, <View>, <Input>, <Devices>, <Help>.**
Click the Devices...and find your USB.

Note: that Extensions Pack and Guest Additions are not strictly required, **but with Extension Pack you can use USB 2.0. **You have also to enable it under USB settings. Without it all your USB devices are controlled as USB 1.0, so they will work at a lower speed.

---

### Post by shane_faulkinbury2 on 2017-06-05
I added myself as the user, but I'm not sure how to do #!?

---

### Post by #&amp;thj^% on 2017-06-05
See Screenshots.
Open VB then just click to highlight the OS (Windows10) Then look for the Icon that looks like a Gear>>>It is right next to New!
Ill wait till we have that enabled first before going forward. :)

---

### Post by shane_faulkinbury2 on 2017-06-05
Gear/USB then USB 2.0 (EHCI) Controller?

---

### Post by #&amp;thj^% on 2017-06-05
> **shane_faulkinbury2 said:**
> Gear/USB then USB 2.0 (EHCI) Controller?

Yep just like Screenshot #2

---

### Post by shane_faulkinbury2 on 2017-06-05
Then add USB filter?

---

### Post by #&amp;thj^% on 2017-06-05
You don't need to.
Now if it looks like my screenshot>>> 
2 Check Box's Ticked 1st Enable USB Controller>>>
2nd Checked Box>> USB _2_.0 (EHCI) Controller.

---

### Post by shane_faulkinbury2 on 2017-06-05
Click OK and everything's good?

---

### Post by #&amp;thj^% on 2017-06-05
Should be good to go..:)

---

### Post by shane_faulkinbury2 on 2017-06-05
Should the flash drive be formatted to NTFS?

---

### Post by #&amp;thj^% on 2017-06-05
Mine is for Windows, but Fat 32 also works.

---

### Post by shane_faulkinbury2 on 2017-06-05
Right on!  Thanks for all your help!  Hey, can I check mark and add 1.0 too?

---

### Post by #&amp;thj^% on 2017-06-05
Your Welcome ;)
You can only enable **"1"** option at a time. :(
EDIT: But you can switch to 1.0 and  switch back to 2.0 before you load the VM first.
And if you really want you add a filter now...but I use mine differently, meaning i have about USB devices that I use as needed, and I don't set a filter, but pick and choose with the Device menu.
When your happy with this solution, it would be most helpful to others Marking this as "Solved" again.

---

### Post by shane_faulkinbury2 on 2017-06-09
Hey 1fallen can you tell me one last thing before I close this thread.  It looks like I'm going to have to purge Virtualbox and reapply because I've tried three different flash drives and none of them show.  :(

So the question!  Do you have to do something special to take screen shots?  The reason I'm asking is because I specifically want to take screen shots of where I logged in on say Facebook.  I was able to this in the previous version of Virtualbox, but I just can't do it in version 5.1_5.1.22-115126.

---

### Post by shane_faulkinbury2 on 2017-06-11
So I purged Virtualbox and tried to reinstall it after waiting for a half hour for it to load.  I then got the following error when I wanted to check for the version and whether it was installed.  I got ```
sudo /sbin/vboxconfig[sudo] password for bubba: 
sudo: /sbin/vboxconfig: command not found
```  So I searched for sbin and found that vboxconfig wasn't even in it.  What should I do now?[ATTACH=CONFIG]275592[/ATTACH][ATTACH=CONFIG]275593[/ATTACH][ATTACH=CONFIG]275594[/ATTACH]

---

### Post by #&amp;thj^% on 2017-06-15
> **shane_faulkinbury2 said:**
> So I purged Virtualbox and tried to reinstall it after waiting for a half hour for it to load.  I then got the following error when I wanted to check for the version and whether it was installed.  I got ```
sudo /sbin/vboxconfig[sudo] password for bubba: 
sudo: /sbin/vboxconfig: command not found
```  So I searched for sbin and found that vboxconfig wasn't even in it.  What should I do now?[ATTACH=CONFIG]275592[/ATTACH][ATTACH=CONFIG]275593[/ATTACH]

Sorry for the long delay, had to deal with some personal issue's
From your screen shot you were probably to far down to see it, but anyway everything we have covered in this thread should of had you up and running again.
So can you tell me now where you are at.
1. Is VirtualBox installed?
```
VBoxManage --version
5.1.22r115126

```

---

### Post by shane_faulkinbury2 on 2017-06-15
Yep.  Maybe you should just help and tell me how to get rid of the entire thing.  I did a ```
sudo apt-get purge virtualbox
```  but that didn't work.

---

### Post by #&amp;thj^% on 2017-06-15
> **shane_faulkinbury2 said:**
> Yep.  Maybe you should just help and tell me how to get rid of the entire thing.  I did a ```
sudo apt-get purge virtualbox
```  but that didn't work.
What dose this show:
```
apt policy VirtualBox-5.1
```
Perhaps your right to remove it and move on.
```
sudo apt remove --purge --autoremove VirtualBox-5.1

```

---

### Post by shane_faulkinbury2 on 2017-06-15
```
bubba@bubba-110-194:~$ apt policy VirtualBox-5.1
virtualbox-5.1:
  Installed: 5.1.22-115126~Ubuntu~xenial
  Candidate: 5.1.22-115126~Ubuntu~xenial
  Version table:
 *** 5.1.22-115126~Ubuntu~xenial 100
        100 /var/lib/dpkg/status
```

---

### Post by #&amp;thj^% on 2017-06-16
Lets just remove it and move on. It's just not this hard. ;)
```
sudo apt remove --purge --autoremove VirtualBox-5.1
```

---

### Post by shane_faulkinbury2 on 2017-06-16
Does that command not remove the .png's?  Because look at the after command pic.

---

### Post by shane_faulkinbury2 on 2017-06-17
Oh yeah, how do you set up Virtualbox to take screen shots!  Man I sure like the older version because all of this was so much easier!

---

### Post by #&amp;thj^% on 2017-06-17
> **shane_faulkinbury2 said:**
> Oh yeah, how do you set up Virtualbox to take screen shots!  Man I sure like the older version because all of this was so much easier!

Well there are many ways to do Screenshots of virtualbox, but to make  this very easy to follow all you have to do when the VB is up and runing is to use the Host Key (Right ctrl) + E..._**.<right-ctrl+e>**_ and you can save to where you want or need them.
You can also use your Host's system Screenshot device to do the same.
I urge you to take some time to better know VB via this site: ;)
[https://www.virtualbox.org/manual/UserManual.html](https://www.virtualbox.org/manual/UserManual.html)
Regards

---

### Post by shane_faulkinbury2 on 2017-06-17
Thanks 1fallen!  :P

---

