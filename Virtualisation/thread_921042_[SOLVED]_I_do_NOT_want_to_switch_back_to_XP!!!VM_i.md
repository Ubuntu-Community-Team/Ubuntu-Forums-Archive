---
title: "[SOLVED] I do NOT want to switch back to XP!!!/VM install problem"
date: 2008-09-15
forum: Virtualisation
---

### Post by novus721 on 2008-09-15
I hate to make even another thread about this, but I am completely lost and I have been trying to fix this for days. Here's the issue:

Every time I try to install vitrualbox, it has an issue with my kernel set. I am running under 2.6.22-14-generic in Hardy, which I thought was a supported set. However, here is one example of my output while trying to install it
```
Installing new version of config file /etc/init.d/vboxdrv ...
 * Starting VirtualBox host networking...                                [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.

``` All the other meathods just give me the same message in different forms.

I have tried:
-installing straight from the [vbox website]("http://www.virtualbox.org/wiki/Linux_Downloads") with the i386.deb for Hardy
-installing virtualbox-ose & virtualbox-ose-modules-generic
-installing virtualbox2.0 and all of that fun stuff
- and the commonly recommended```
sudo apt-get install virtualbox-ose virtualbox-ose-source module-assistant
sudo module-assistant prepare
sudo module-assistant auto-install virtualbox-ose
sudo modprobe vboxdrv

``` but I get cut off at the second line because I constantly get the output ```
Package linux-headers-2.6.22-14-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.22-14-generic has no installation candidate

```

Do I need to update my headers?:confused:

I have TRIED to delete Virtualbox completely, but I don't think I have gotten rid of everything for some reason - I have cleared all the packages in synaptic, physically deleted all of the files in my /usr/bin and used autoremove to try to purge anything else, but I'm not sure if that did the trick

THIS IS DRIVING ME NUTS! ](*,)](*,)](*,)I need a vm running asap or I will be forced to switch back to M$ for 2 months and I never ever ever ever ever *ever* want to do that again. I felt like a whore long enough. :)

---

### Post by sonofusion82 on 2008-09-15
I am not sure if this is the solution, have you enabled your source repository in /etc/apt/sources.list?

deb-src [http://yourMirrorUrl/](http://yourMirrorUrl/) hardy main universe...

---

### Post by novus721 on 2008-09-15
Thanks for your quick reply, but it seems I actually have a bigger problem - I decided to just suck it up and update my kernel etc, but for whatever reason, even though synaptic confirms I have the updated kernels, my grub will only allow me to boot into 7.10 with 2.6.22-14, when I have 8.04 with 2.6.24-(all 16 through 19). Now I am COMPLETELY lost.:)

lsb_release confirms I am running 8.04, but uname -r confirms the .22-14 headers - how this is happening is beyond me

I updated my grub list to include the .24 headers, but none of them fully load and I go to an error screen with each version, 2.6.24-16 through 2.6.24-19.

[looks like I have have to change the venue of this posting unfortunately]("http://ubuntuforums.org/showthread.php?p=5797457#post5797457")...but still any ideas are welcome :D

---

### Post by bpalone on 2008-09-16
I don't know enough to be much help on your version and headers issue.  But, in the manual provided by Sun, in the beginning there is a section about installing in Linux.  In there they mention a recommended package that is available in the Synaptic packages.  I  am talking from memory, but I think it is **_dkms_** and originates from HP.  It helps with the compiling for the modules.  I have installed it on my three machines running Hardy without a hitch.

Hope that this helps.

---

### Post by insane_alien on 2008-09-16
you need to install the kernel headers.

```
sudo aptitude install build-essential
```

That command should sort you out.

---

### Post by novus721 on 2008-09-16
Hmm thanks to the both of you, but I think I did already try the build-essential, but I will give it a shot again. however I will not be able to get to my computer again until tomorrow night, so check back then - thank you guys!

---

### Post by novus721 on 2008-09-17
ok so:

1) tired the build-essential, but there was nothing new to download or install unfortunately

2) got the dkms package which by its description seems useful, but it had no effect after downloading it and restarting - is there anything else I need to do with the package after getting it through synaptic? 

thanks again for all the help!

---

### Post by UbuWu on 2008-09-17
If you still can only run the old kernel, you can manually download the headers from [http://packages.ubuntu.com/gutsy-updates/linux-headers-2.6.22-14-generic](http://packages.ubuntu.com/gutsy-updates/linux-headers-2.6.22-14-generic) and install them. Then install virtualbox from the website, not from the ubuntu repositories (the version in hardy doesn't have dkms which is needed to build the kernel modules yet).

---

### Post by novus721 on 2008-09-17
Thanks, I could search for the headers I need, but I already have them on my computer. [I just get that BusyBox error]("http://ubuntuforums.org/showthread.php?p=5797457#post5797457") whenever I try to load them from grub. when I do update-grub it finds the headers, it just wont let me load them.

And also, I tried to download straight from the website, which didn't help. 

I just think I need to update my headers, I just don't understand why I can't load into them. 

Thanks!!!

---

### Post by UbuWu on 2008-09-17
Grub boots the kernel, not the headers. The headers are needed to build the kernel modules. Do you have the headers installed for the kernel that does work for you (matching versions)? If you run 2.6.22-14, you should install the headers from the links I pointed you to. Then you should be able to install virtualbox successfully.

---

### Post by y@w on 2008-09-17
You can make sure you get the headers of the kernel you are booting to using:

```
sudo apt-get install linux-headers-`uname -r`
```

(make sure to use the backticks)

---

### Post by novus721 on 2008-09-17
OOOOK - so we're half way there...

So I got the required headers (thanks to you both) but I honestly don't understand why I didn't have them earlier as "uname -r" told me I did. Anyway.

Half-way there!

So I got it to install (I'm pretty sure) but now I can't get it to run...I tried to download it from the website, but the install wouldn't work for some reason. I mean I downloaded the package...it just didn't do anything. Am I missing a step here?

So instead, I used this
```
sudo apt-get install virtualbox-ose virtualbox-ose-source module-assistant
sudo module-assistant prepare
sudo module-assistant auto-install virtualbox-ose
sudo modprobe vboxdrv
``` which I know is an older version but it installed and all of the steps were completed, but it just won't work now and keeps telling me that I have to reinstall it when I try to make it run through terminal. Any ideas?

BIG THANKS!!

---

### Post by novus721 on 2008-09-17
```
Could not find VirtualBox installation. Please reinstall.

```is exactly the error I get. There is an icon for it in my system tray...what's going on?

---

### Post by Shazaam on 2008-09-17
I have found that the correct terminal command to start VirtualBox is case sensitive...
```
VirtualBox
```
Try that and post back.

---

### Post by novus721 on 2008-09-17
ahhh yes the case fixed everything - thanks for the tip!

OK so I am one step away from marking this thread SOLVED and rightfully so

I HAVE VB RUNNING! However, I'm having a problem I've never had and have not seen yet on the forum entirely. 

When I go to install my xp .iso, the setup brings up the blue install screen that asks me to hit "enter" to continue. I let it capture my mouse...and then everything freezes. The icons show that both my keyboard and mouse are captured, but I have no control and am forced to restart X to get things going again - VERY annoying to say the least :)

Also, the host key is RCtrl, but I can slam on it forever and it doesn't do a thing. Any ideas why when my mouse is captured I can't do ANYTHING?! Even hitting enter just trying to get the xp going doesn't do a thing...

Man I am earning this virtualization :)

---

### Post by novus721 on 2008-09-17
ok so now i realize its just that my keyboard isn't being recognized

UPDATE - found out you just need to uncheck complex character support in your Language Support settings - fixed everything! 

THANK YOU EVERYONE!

---

