---
title: "gnome-shell on wayland, some issues"
date: 2017-04-08
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-04-08
A couple that jump out are,
apps using polkit (pkexec) fail to open, ex.'s are, nautilus-admin, synaptic, system-settings > users, maybe some more..
Error is - 
No protocol specified
Unable to init server: Could not connect: Connection refused

hardware decoding thru vaapi seems a bit inconsistent, for example vlc fails, mpv works from cli but not context menu (nautilus), gnome-mpv fails altogether (falls back to software decoding..

I guess it only works with gdm not lightdm 
(- i.e. Ubuntu-Gnome is good there, users who add gnome-shell on an Ubuntu install likely stay with lightdm. Overall gnome-shell in an Ubuntu install is flawed anyway & not a good 'try it' option..

---

### Post by sevendogs on 2017-04-09
I think there are still some issues with Wayland. I was playing around with the latest Fedora and it uses Gnome/Wayland and although it worked with no errors, the performance was bad: there was a tad bit of lag when you did everything - open apps, click on a item, etc. An online reviewer noted the same behavior. Not my hardware, running on the Watson equivalent of a desktop 8-)

Not sure Wayland is ready for prime-time yet but Fedora is pretty bleeding edge and I guess they felt they could run with it. I am staying with Xorg until they work out the issues.

---

### Post by rogervn on 2017-04-11
I was also testing it on arch and it seems fine, but some weird things happens some times, like my KeePass freezing mouse clicks after some time clearing the passwords from the clipboard.

---

### Post by jbicha on 2017-04-11
> **mc4man said:**
> A couple that jump out are,
apps using polkit (pkexec) fail to open, ex.'s are, nautilus-admin, synaptic, system-settings > users, maybe some more..

Yes, that's basically intentional as I understand it. File bugs with those apps upstream.

> **mc4man said:**
> 
I guess it only works with gdm not lightdm 


Thanks, there is a recent bug filed for that.

---

### Post by ventrical on 2017-04-21
> **mc4man said:**
> A couple that jump out are,
apps using polkit (pkexec) fail to open, ex.'s are, nautilus-admin, synaptic, system-settings > users, maybe some more..
Error is - 
No protocol specified
Unable to init server: Could not connect: Connection refused

hardware decoding thru vaapi seems a bit inconsistent, for example vlc fails, mpv works from cli but not context menu (nautilus), gnome-mpv fails altogether (falls back to software decoding..

I guess it only works with gdm not lightdm 


gnome3 with wayland option will not work with lighdm. I get blackspace. Also with gdm3 installed  it, (gnome with wayland) will lock up.

Regards..

---

### Post by #&amp;thj^% on 2017-04-23
> **ventrical said:**
> gnome3 with wayland option will not work with lighdm. I get blackspace. Also with gdm3 installed  it, (gnome with wayland) will lock up.

Regards..

I have it working:
```
$ echo $DESKTOP_SESSION
gnome-wayland

```

```
apt policy lightdm
lightdm:
  Installed: 1.22.0-0ubuntu2
  Candidate: 1.22.0-0ubuntu2
  Version table:
 *** 1.22.0-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu artful/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by ventrical on 2017-04-23
@1fallen,

maybe after all the updates it might work.
Will check.
edit:
Nope! maybe this info might help.

The installs were originally 17.04 ubuntu-desktop installs. I just  installed gnome-shell on top of them. Would that break wayland?

regards..

---

### Post by ventrical on 2017-04-23
> **1fallen said:**
> I have it working:
```
$ echo $DESKTOP_SESSION
gnome-wayland

```

```
apt policy lightdm
lightdm:
  Installed: 1.22.0-0ubuntu2
  Candidate: 1.22.0-0ubuntu2
  Version table:
 *** 1.22.0-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu artful/main amd64 Packages
        100 /var/lib/dpkg/status

```

Ok.. got it working on an ubuntu-gnome install.

---

### Post by Frogs Hair on 2017-04-24
Wayland is also working on 17.04 after updates.

---

### Post by ventrical on 2017-04-24
> **Frogs Hair said:**
> Wayland is also working on 17.04 after updates.

I notice  little bit of a performance problem on wayland - but gnome-shell and gnome-classic (compiz) are very snappy on older machines.

---

### Post by Frogs Hair on 2017-04-24
Just noticed my password prompts for synaptic , bleachbit, and nautilus as super user don't work in the wayland Gnome Shell session. :confused:

---

### Post by #&amp;thj^% on 2017-04-24
> **Frogs Hair said:**
> Just noticed my password prompts for synaptic , bleachbit, and nautilus as super user don't work in the wayland Gnome Shell session. :confused:

You just beat me for reporting this :D....I can confirm the same behavior here.
Regular Unity && Gnome works as expected.
EDIT: Well I had to reread mc4man's first post here:
> A couple that jump out are,
apps using polkit (pkexec) fail to open, ex.'s are, nautilus-admin, synaptic, system-settings > users, maybe some more..
Error is - 
No protocol specified
Unable to init server: Could not connect: Connection refused

---

### Post by jbicha on 2017-04-24
GNOME on Wayland does not support running apps as root like that. There's already a bug for [Synaptic]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1551951"). Could you file a bug for BleachBit and use the 'wayland' tag? If you can figure out a way to report that to the BleachBit developers, that would be great too.

For Nautilus, you just have to use the gvfs admin backend available in Ubuntu 17.04+. Use the prefix admin:// to browse as root. (So admin:///etc/ to browse your /etc/ directory as root). That will work in any app that uses gvfs, which is many of the usual GNOME apps.

On the first page of this thread, some people mentioned that they couldn't log in to GNOME on Wayland from LightDM. That's [bug 1632772]("https://bugs.launchpad.net/ubuntu-gnome/+bug/1632772").

For a few other wayland bugs, browse the bugs [tagged]("https://bugs.launchpad.net/ubuntu/+bugs?field.tag=wayland") with 'wayland'.

---

### Post by Frogs Hair on 2017-04-24
> **jbicha said:**
> GNOME on Wayland does not support running apps as root like that. There's already a bug for [Synaptic]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1551951"). Could you file a bug for BleachBit and use the 'wayland' tag? If you can figure out a way to report that to the BleachBit developers, that would be great too.

For Nautilus, you just have to use the gvfs admin backend available in Ubuntu 17.04+. Use the prefix admin:// to browse as root. (So admin:///etc/ to browse your /etc/ directory as root). That will work in any app that uses gvfs, which is many of the usual GNOME apps.

On the first page of this thread, some people mentioned that they couldn't log in to GNOME on Wayland from LightDM. That's [bug 1632772]("https://bugs.launchpad.net/ubuntu-gnome/+bug/1632772").

For a few other wayland bugs, browse the bugs [tagged]("https://bugs.launchpad.net/ubuntu/+bugs?field.tag=wayland") with 'wayland'.

Good to know. Thanks

---

### Post by #&amp;thj^% on 2017-04-24
> **jbicha said:**
> GNOME on Wayland does not support running apps as root like that. There's already a bug for [Synaptic]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1551951"). Could you file a bug for BleachBit and use the 'wayland' tag? If you can figure out a way to report that to the BleachBit developers, that would be great too.

_**For Nautilus, you just have to use the gvfs admin backend available in Ubuntu 17.04+. Use the prefix admin:// to browse as root. (So admin:///etc/ to browse your /etc/ directory as root). That will work in any app that uses gvfs, which is many of the usual GNOME apps.**_

On the first page of this thread, some people mentioned that they couldn't log in to GNOME on Wayland from LightDM. That's [bug 1632772]("https://bugs.launchpad.net/ubuntu-gnome/+bug/1632772").

For a few other wayland bugs, browse the bugs [tagged]("https://bugs.launchpad.net/ubuntu/+bugs?field.tag=wayland") with 'wayland'.
Great Thanks jeremy:)
Kind regards

---

### Post by ventrical on 2017-04-24
> **jbicha said:**
> 

On the first page of this thread, some people mentioned that they couldn't log in to GNOME on Wayland from LightDM. That's [bug 1632772]("https://bugs.launchpad.net/ubuntu-gnome/+bug/1632772").



Yep .. thnxs.

Regards..

---

### Post by wildmanne39 on 2017-04-24
I had 17.10 up and running then I installed gnome and it gives me the blank screen.

I read the bug report and it said to create a file, how do you do that when you can not get to the terminal or tty, and it will not boot in recovery mode.

If there is a way please let me know.
Thanks

---

### Post by mc4man on 2017-04-24
> **wildmanne39 said:**
> I had 17.10 up and running then I installed gnome and it gives me the blank screen.

I read the bug report and it said to create a file, how do you do that when you can not get to the terminal or tty, and it will not boot in recovery mode.

If there is a way please let me know.
Thanks
If you have to install gnome then it's not '17.10' by any stretch. Seeing as though there are no 17.10 images I'd suggest starting with 17.04 UbuntuGnome & making it '17.10' by however it is you all are doing.
gnome-shell on an Ubuntu image is flawed from the get-go..

---

### Post by wildmanne39 on 2017-04-24
> **mc4man said:**
> If you have to install gnome then it's not '17.10' by any stretch. Seeing as though there are no 17.10 images I'd suggest starting with 17.04 UbuntuGnome & making it '17.10' by however it is you all are doing.
gnome-shell on an Ubuntu image is flawed from the get-go..

I only installed gnome on ubuntu 17.10 because I thought they wanted us to test it and see how it works, with unity 17.10 was working well.

Can I remove gnome without reinstalling 17.04 then upgrading? 
Thanks

---

### Post by #&amp;thj^% on 2017-04-24
> **wildmanne39 said:**
> I only installed gnome on ubuntu 17.10 because I thought they wanted us to test it and see how it works, with unity 17.10 was working well.

Can I remove gnome without reinstalling 17.04 then upgrading? 
Thanks

Was it Gnome that you installed...or gnome-shell?

---

### Post by wildmanne39 on 2017-04-24
Gnome shell.

---

### Post by mc4man on 2017-04-24
My point is that gnome-shell in an Ubuntu install does not work as well as gnome-shell in an UbuntuGnome install. Seeing as though Ubuntu is dropping what's now an ubuntu session then it seems a waste of time and or effort to 'test' Ubuntu (ubuntu session) anymore, unity or gnome-shell.

As far as wayland - there is nothing about it currently that qualifies it to be the default. Will that change over next 5 months?, I think it's doubtful. Though if Ubuntu is committed to make it the default in 18.04 then they might as well start, the 9 month releases are more points in time then a release anyway.
Ubuntu's predictive history is questionable to say the least..

---

### Post by #&amp;thj^% on 2017-04-24
> **wildmanne39 said:**
> Gnome shell.

All good here removing gnome-shell...if you can get to a tty 1/2/3
```
sudo apt remove --purge gnome-shell
[sudo] password for me: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-geoclue-2.0
  gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0 gir1.2-gweather-3.0
  gir1.2-mutter-0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0 gir1.2-polkit-1.0
  gir1.2-rsvg-2.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-upowerglib-1.0 gjs gnome-backgrounds gnome-contacts
  gnome-shell-common gnome-themes-standard-data gnome-tweak-tool
  libcaribou-common libcaribou0 libchamplain-0.12-0 libfolks-telepathy25
  libgdm1 libgjs0f libmozjs-38-0 libtelepathy-logger3 switcheroo-control
  xserver-xorg-legacy
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  chrome-gnome-shell* gdm3* gnome-shell* gnome-shell-extension-autohidetopbar*
  gnome-shell-extension-caffeine* gnome-shell-extension-dashtodock*
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 13.1 MB disk space will be freed.
(Reading database ... 231321 files and directories currently installed.)
Removing chrome-gnome-shell (8.2.1-1ubuntu1) ...
Removing gdm3 (3.24.1-0ubuntu1) ...
Removing gnome-shell-extension-dashtodock (57-1ubuntu1) ...
Removing gnome-shell-extension-caffeine (0~git20161228-1ubuntu2) ...
Removing gnome-shell-extension-autohidetopbar (20161203-1ubuntu1) ...
Removing gnome-shell (3.24.1-0ubuntu1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu2) ...
Processing triggers for libglib2.0-0:amd64 (2.52.0-1) ...
Processing triggers for bamfdaemon (0.5.3+17.04.20170406-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for man-db (2.7.6.1-2) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu5) ...
Processing triggers for hicolor-icon-theme (0.15-1) ...
(Reading database ... 230922 files and directories currently installed.)
Purging configuration files for gdm3 (3.24.1-0ubuntu1) ...
Removing user `gdm' ...
Warning: group `gdm' has no more members.
Done.
Purging configuration files for chrome-gnome-shell (8.2.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (233-5ubuntu1) ...
Processing triggers for dbus (1.10.10-1ubuntu2) ...


```
Just rebooted twice for safe measure...but i seem to be immune to the troubles others are having here.
I also agree with mc4man....nothing really to see here of quality anyway.
But i did want to check the progress with gnome-wayland anyway:P

---

### Post by wildmanne39 on 2017-04-24
Thanks 1fallen, I knew I could do it that way but I could not get a tty to work, I finally was able to mount the file system read and write then use the root shell to remove the files.

It loads further but still stops before the desktop, I think because lightdm is not the default anymore and wayland is removed, I will google and see what I come up with.

---

### Post by #&amp;thj^% on 2017-04-24
> **wildmanne39 said:**
> Thanks 1fallen, I knew I could do it that way but I could not get a tty to work, I finally was able to mount the file system read and write then use the root shell to remove the files.

It loads further but still stops before the desktop, I think because lightdm is not the default anymore and wayland is removed, I will google and see what I come up with.

Yes I knew you could uninstall it :D....I was trying to take the bullet for you if something else would arise from the removal of "gnome-shell"
is all.
to reconfigure lightdm: [https://askubuntu.com/questions/74196/how-to-restore-lightdm-settings](https://askubuntu.com/questions/74196/how-to-restore-lightdm-settings)

---

### Post by wildmanne39 on 2017-04-24
> **1fallen said:**
> Yes I knew you could uninstall it :D....I was trying to take the bullet for you if something else would arise from the removal of "gnome-shell"
is all.
to reconfigure lightdm: [https://askubuntu.com/questions/74196/how-to-restore-lightdm-settings](https://askubuntu.com/questions/74196/how-to-restore-lightdm-settings)

Thanks 1fallen your help is very much appreciated, I did what was in the ask ubuntu link but it still does not load to the desktop, I will stop working on it tonight and:) start fresh in the morning.

---

### Post by ventrical on 2017-04-25
> **mc4man said:**
> If you have to install gnome then it's not '17.10' by any stretch. Seeing as though there are no 17.10 images I'd suggest starting with 17.04 UbuntuGnome & making it '17.10' by however it is you all are doing.
gnome-shell on an Ubuntu image is flawed from the get-go..

+1

am learning the hard way.

---

### Post by ventrical on 2017-04-25
> **mc4man said:**
> My point is that gnome-shell in an Ubuntu install does not work as well as gnome-shell in an UbuntuGnome install. Seeing as though Ubuntu is dropping what's now an ubuntu session then it seems a waste of time and or effort to 'test' Ubuntu (ubuntu session) anymore, unity or gnome-shell.

..yes .. or why even have an ubuntu-desktop iso for this release?
> 
As far as wayland - there is nothing about it currently that qualifies it to be the default. Will that change over next 5 months?, I think it's doubtful. Though if Ubuntu is committed to make it the default in 18.04 then they might as well start, the 9 month releases are more points in time then a release anyway.
Ubuntu's predictive history is questionable to say the least..

All those hours with mir. Actually , all those hours testing wayland.

---

### Post by wildmanne39 on 2017-04-25
I reinstalled, 17.10 now working again. Do you use the development version of Ubuntu all the time during testing or do you also use your production machines?

Thanks

---

### Post by ventrical on 2017-04-25
> **wildmanne39 said:**
> I reinstalled, 17.10 now working again. Do you use the development version of Ubuntu all the time during testing or do you also use your production machines?

Thanks

I have 8 working boxes (towers and lappys) in my ubuntu-shack that all have multiple installs of ubuntu at one stage of development or other. So far (as beginning with trusty) I have always run development  in grub along side my production machines. If I use  open ppas or 'proposed' I usually isolate the machine as there is potential for damage to grub (as per my experience in the last 24 hours).

For the most part there is a 90% probability of a smooth cycle but we have to remember we are on cutting edge of things :)

Regards..

---

### Post by wildmanne39 on 2017-04-25
> **ventrical said:**
> I have 8 working boxes (towers and lappys) in my ubuntu-shack that all have multiple installs of ubuntu at one stage of development or other. So far (as beginning with trusty) I have always run development  in grub along side my production machines. If I use  open ppas or 'proposed' I usually isolate the machine as there is potential for damage to grub (as per my experience in the last 24 hours).

For the most part there is a 90% probability of a smooth cycle but we have to remember we are on cutting edge of things :)

Regards..Thanks for your reply, I have a lot to learn running a development version, I am running Ubuntu but from what I have read it does not look like it matters if we are testing Xubuntu, Ubuntu Mate or any of the official flavors correct? or is it best to keep it to testing Ubuntu?
Thanks

---

### Post by ventrical on 2017-04-25
> **wildmanne39 said:**
> Thanks for your reply, I have a lot to learn running a development version, I am running Ubuntu but from what I have read it does not look like it matters if we are testing Xubuntu, Ubuntu Mate or any of the official flavors correct? or is it best to keep it to testing Ubuntu?
Thanks

That's a free preference. I usually experiment with all distros.  However. we are encouraged during this cycle and the next to give a little extra time to gnome3 (ubuntu-gnome) as it will officially become the default desktop with unity7 in the universe for 18.04 (if chief cook and bottle washer has his way) :)

 Development testing can become stressful so we have to  try things to have a little fun. I have several hard drives on hand and several form factors to work with so when I try to break an install I can do it while having fun also. In that breakage we may find a bug that the QA tracker smoke tester might not find, especially if the testers are using virtual machines. Experience  has proven  that what works on a virtual machine does not always work on a hard install.  so we core testers here have created an awesome fall-back database for developers. Even if we influence  the fixing of just a few bugs we are still active game changers within the community.

Regards..

---

### Post by wildmanne39 on 2017-04-25
Sounds good, over the weekend I will most likely get the dev version set up on a desktop and off of this laptop, were I can have several hard drives.

What you said reminded me a very long time ago when I was very new to Ubuntu I tested Ubuntu development version and I had three OS's on separate drives, there was an issue with that version and it wiped out everything, some how it could cross over to other partitions, it was not a fun time.
Thanks

---

### Post by ventrical on 2017-04-25
> **wildmanne39 said:**
> Sounds good, over the weekend I will most likely get the dev version set up on a desktop and off of this laptop, were I can have several hard drives.

What you said reminded me a very long time ago when I was very new to Ubuntu I tested Ubuntu development version and I had three OS's on separate drives, there was an issue with that version and it wiped out everything, some how it could cross over to other partitions, it was not a fun time.
Thanks

Yes .I agree  . .not so much fun  to have breakage such as you mentioned .. thats why I bay-swap hdds on different machines. My production machines are unaffected and there are no taskmasters here. We can work at our own pace.... uh yeah .. I see you have been here longer than me :) so for certain you have  lot of experience around here.

regards..

---

### Post by wildmanne39 on 2017-04-25
> **ventrical said:**
> Yes .I agree  . .not so much fun  to have breakage such as you mentioned .. thats why I bay-swap hdds on different machines. My production machines are unaffected and there are no taskmasters here. We can work at our own pace.... uh yeah .. I see you have been here longer than me :) so for certain you have  lot of experience around here.

regards..
Almost everything I have done in the last six years has been with wireless issues, out of practice with everything else, but probably not for long.

I will stop taking this thread off topic, bad wildmanne39.
Thanks

---

### Post by ventrical on 2017-04-25
> **wildmanne39 said:**
> Almost everything I have done in the last six years has been with wireless issues, out of practice with everything else, but probably not for long.

I will stop taking this thread off topic, bad wildmanne39.
Thanks

No wonder my wireless works so good ! :)

me off topic too. shuttin up :)

---

### Post by #&amp;thj^% on 2017-04-25
> **wildmanne39 said:**
> I reinstalled, 17.10 now working again. Do you use the development version of Ubuntu all the time during testing or do you also use your production machines?

Thanks
Glad your up and running again.;)
I'm like ventrical...i have a couple of towers with AMD and Intel for hardware bugs, but I'm down to  one Lenovo lappy with the UEFI Bios...All Intel, no hybrid graphics.(Gives me a rash just thinking about them)LOL
But yes i use the Dev cycle daily to thoroughly test things

---

### Post by wildmanne39 on 2017-04-26
Thanks 1fallen.:)

---

### Post by Frogs Hair on 2017-04-26
> **jbicha said:**
> GNOME on Wayland does not support running apps as root like that. There's already a bug for [Synaptic]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1551951"). Could you file a bug for BleachBit and use the 'wayland' tag? If you can figure out a way to report that to the BleachBit developers, that would be great too.

For Nautilus, you just have to use the gvfs admin backend available in Ubuntu 17.04+. Use the prefix admin:// to browse as root. (So admin:///etc/ to browse your /etc/ directory as root). That will work in any app that uses gvfs, which is many of the usual GNOME apps.

On the first page of this thread, some people mentioned that they couldn't log in to GNOME on Wayland from LightDM. That's [bug 1632772]("https://bugs.launchpad.net/ubuntu-gnome/+bug/1632772").

For a few other wayland bugs, browse the bugs [tagged]("https://bugs.launchpad.net/ubuntu/+bugs?field.tag=wayland") with 'wayland'.

I just noticed gdebi package installer is affected as well , so I'm not sure filing a bug report on an application by application basis is the way to go here. This suggests to me a problem having to do with elevated permissions in general in regard to graphical applications.

---

### Post by #&amp;thj^% on 2017-04-26
> **Frogs Hair said:**
> I just noticed gdebi package installer is affected as well , so I'm not sure filing a bug report on an application by application basis is the way to go here. This suggests to me a problem having to do with elevated permissions in general in regard to graphical applications.

I have no problem with gdebi....but others I'm using this as a work-around temporarily.
```
sudo dbus-launch <your-app-here>
```
mainly using it for opening "nautilus" with admin privileges. And a friendly warning to be careful while using it.:)
Hope this is useful.

---

### Post by jbicha on 2017-04-26
> **Frogs Hair said:**
> I just noticed gdebi package installer is affected as well , so I'm not sure filing a bug report on an application by application basis is the way to go here.

Yes, that's exactly what we're asking you to do. Thanks.

Almost every app works for me in a GNOME on Wayland session, either through native Wayland (most GTK3 apps) or with XWayland. We want to know about the ones that don't work, but it's ultimately up to the developers of those apps to make the necessary changes.

---

### Post by Frogs Hair on 2017-04-26
I tested the following with gksu because it's installed and it didn't work. I only open the file system to install themes/icons anyway. I'll use another session for installation.
```
gksu dbus-launch nautilus

```

---

### Post by Frogs Hair on 2017-04-26
> **jbicha said:**
> yes, that's exactly what we're asking you to do. Thanks.

Almost every app works for me in a gnome on wayland session, either through native wayland (most gtk3 apps) or with xwayland. We want to know about the ones that don't work, but it's ultimately up to the developers of those apps to make the necessary changes.

ok, I started with bleachbit.

---

### Post by #&amp;thj^% on 2017-04-26
> **Frogs Hair said:**
> ok, I started with bleachbit.

If you provide the links to your bug/reports we can add ourselves to the report as effected by also.
Instead of filing numerous reports:)...Hope that makes sense.
Thanks and Best Regards

---

### Post by Frogs Hair on 2017-04-26
I only gave a general description.  


Bleachbit as Root

[https://bugs.launchpad.net/bugs/1686504](https://bugs.launchpad.net/bugs/1686504)

---

### Post by #&amp;thj^% on 2017-04-26
> **Frogs Hair said:**
> I only gave a general description.  


Bleachbit as Root

[https://bugs.launchpad.net/bugs/1686504](https://bugs.launchpad.net/bugs/1686504)
Thats a good start :KSI'll see if I can generate a report to go along with it.
Thanks Frogs Hair
Well then...guess i'll try again later
> [h=1]Oops![/h]                    Sorry, something just went wrong in Launchpad.         
                    We&#8217;ve recorded what happened,           and we&#8217;ll fix it as soon as possible.           Apologies for the inconvenience.         
                    (Error ID:           OOPS-1fd1e47b169f815c0eae310bfb570b38)         



---

### Post by mc4man on 2017-04-26
> **jbicha said:**
> Yes, that's exactly what we're asking you to do. Thanks.

Almost every app works for me in a GNOME on Wayland session, either through native Wayland (most GTK3 apps) or with XWayland. We want to know about the ones that don't work, but it's ultimately up to the developers of those apps to make the necessary changes.
Is Launchpad going to more responsive than Debian, github, Redhat, ect. as these non working apps are well known for some time & bugs/issues have been filed for some time.
ex. synaptic - bug in debian 1 year+, several months on github. gparted - bugs on Redhat, bugzillla,  ect.

For many of these apps the use of a startup script employing xhost  enables their use in a wayland session though likely  ill-advised so won't post.

---

### Post by #&amp;thj^% on 2017-04-26
> **mc4man said:**
> Is Launchpad going to more responsive than Debian, github, Redhat, ect. as these non working apps are well known for some time & bugs/issues have been filed for some time.
ex. synaptic - bug in debian 1 year+, several months on github. gparted - bugs on Redhat, bugzillla,  ect.

For many of these apps the use of a startup script employing xhost  enables their use in a wayland session though likely  ill-advised so won't post.
+1 yep some have been reported many many moons ago :o  I guess we just keep squeaking...till it/they get fixed or removed.;)
If they don't start doing or pushing the fix/patch....this ends up just being a big waste of time....Just Saying.

---

### Post by mc4man on 2017-04-26
> **Frogs Hair said:**
> ok, I started with bleachbit.

Bleachbit uses 'su-to-root' which will look for gksu before opening a terminal to run bleachbit as root. 
It would appear gksu will not work in wayland, you'd get a password prompt window that won't accept input. 
So initial 'bug' for you is gksu in wayland.
(plus it's possible gksu needs ~/.Xauthority which isn't used in UbuntuGnome, don't really know..

If gksu isn't installed then su-to-root will use a terminal & currently that wouldn't work in Wayland but if I allow it then the behavior is bad. It will create & own as root ~/.dbus & possibly some other root owned files in the users $HOME

So the current .desktop for bleachbit as root seems to be unsuitable going forward, (or the menu package),  possibly your 2nd bug..
(- it probably would behave better with a policy or just being run as sudo -H bleachbit ..
screen shows clean output, this is in a wayland session.

---

### Post by #&amp;thj^% on 2017-04-26
Don't know why i did not even give that a thought...works here also "sudo -H"
Thanks Doug :)

---

### Post by Frogs Hair on 2017-04-26
> **mc4man said:**
> Bleachbit uses 'su-to-root' which will look for gksu before opening a terminal to run bleachbit as root. 
It would appear gksu will not work in wayland, you'd get a password prompt window that won't accept input. 
So initial 'bug' for you is gksu in wayland.
(plus it's possible gksu needs ~/.Xauthority which isn't used in UbuntuGnome, don't really know..

If gksu isn't installed then su-to-root will use a terminal & currently that wouldn't work in Wayland but if I allow it then the behavior is bad. It will create & own as root ~/.dbus & possibly some other root owned files in the users $HOME

So the current .desktop for bleachbit as root seems to be unsuitable going forward, (or the menu package),  possibly your 2nd bug..
(- it probably would behave better with a policy or just being run as sudo -H bleachbit ..
screen shows clean output, this is in a wayland session.



Thanks , 

Learning ! :)

```
sudo -H bleachbit
[sudo] password for d-book: 
No protocol specified
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Could not open X display
``` :neutral:

---

### Post by mc4man on 2017-04-26
> **Frogs Hair said:**
> Thanks , 

Learning ! :)

```
sudo -H bleachbit
[sudo] password for d-book: 
No protocol specified
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Could not open X display
``` :neutral:

I was sorta surprised when 1fallen said it worked for him (unless he did the below unmentioned.
So run this command in a terminal, then try again. This command will only last until you reboot, it can be scripted to autorun on login but as I mentioned before don't know it's advisability...
(you'll now be able to also use synaptic, ect.

```
 xhost +si:localuser:root
```

---

### Post by #&amp;thj^% on 2017-04-26
He He He....thought i should respect your wish to not mention it.;)
I also added it to auto-start....just about an hour ago...so i will report any adverse events if/when they occur.
Sorry about that.

---

### Post by Frogs Hair on 2017-04-26
Got it .

---

### Post by #&amp;thj^% on 2017-04-27
> **1fallen said:**
> He He He....thought i should respect your wish to not mention it.;)
I also added it to auto-start....just about an hour ago...so i will report any adverse events if/when they occur.
Sorry about that.

Well about the safest way I found for myself is to just add it to my .bashrc as a alias.
That way seems to work for my usage.

---

### Post by jbicha on 2017-04-27
This section of the Fedora 25 release notes looks helpful in explaining:

[https://fedoraproject.org/wiki/Common_F25_bugs#wayland-root-apps](https://fedoraproject.org/wiki/Common_F25_bugs#wayland-root-apps)

---

### Post by wildmanne39 on 2017-04-27
> **jbicha said:**
> This section of the Fedora 25 release notes looks helpful in explaining:

[https://fedoraproject.org/wiki/Common_F25_bugs#wayland-root-apps](https://fedoraproject.org/wiki/Common_F25_bugs#wayland-root-apps)

That is a very informative read.

---

### Post by #&amp;thj^% on 2017-04-27
I must be reading it wrong then....my ~.bashrc...with alias now shows:
```
rt
localuser:root being added to access control list
```
So far no troubles opening or editing..things that i've needed.

---

### Post by mc4man on 2017-04-27
I would be curious to know 1 tangible thing that Wayland does better than X11 from a user perspective/experience?

---

### Post by #&amp;thj^% on 2017-04-28
Just some good information...and no offense _**or opinion meant on my behalf.**_

The Failings of X: [https://www.phoronix.com/scan.php?page=article&item=x_wayland_situation](https://www.phoronix.com/scan.php?page=article&item=x_wayland_situation)

---

### Post by mc4man on 2017-04-28
> **1fallen said:**
> Just some good information...and no offense or opinion meant on my behalf.

The Failings of X: [https://www.phoronix.com/scan.php?page=article&item=x_wayland_situation](https://www.phoronix.com/scan.php?page=article&item=x_wayland_situation)
I've seen/read bits & pieces of that all before. It's all well & good, true, ect.

It still doesn't change the _fact_ that right now X is still a better user experience. 

So Canonical/Ubuntu would like current Ubuntu users to move to Gnome(gnome-shell) which while it's superior to Unity/compiz in that it's being actively developed, refined, ect.,  is to many (most) Ubuntu users an inferior concept compared to Unity/compiz.
So at the same time as that to present the clearly inferior  Wayland (currently)  as default makes no sense here.

What's the reasoning behind that? Maybe the crystal ball says Wayland will be good enough in 10 months, maybe Canonical just wants to wash their hands of the Desktop as quickly & cleanly as possible. Maybe ... whatever, I can't imagine.

As far as X11 being available as an alternate, well great. Currently X is not good as it could be in Ubuntu, why would anyone think that when it's not the default it'll be treated any better..

---

### Post by #&amp;thj^% on 2017-04-28
> **mc4man said:**
> I've seen/read bits & pieces of that all before. It's all well & good, true, ect.

It still doesn't change the _fact_ that right now X is still a better user experience. 

So Canonical/Ubuntu would like current Ubuntu users to move to Gnome(gnome-shell) which while it's superior to Unity/compiz in that it's being actively developed, refined, ect.,  is to many (most) Ubuntu users an inferior concept compared to Unity/compiz.
So at the same time as that to present the clearly inferior  Wayland (currently)  as default makes no sense here.

What's the reasoning behind that? Maybe the crystal ball says Wayland will be good enough in 10 months, maybe Canonical just wants to wash their hands of the Desktop as quickly & cleanly as possible. Maybe ... whatever, I can't imagine.

As far as X11 being available as an alternate, well great. Currently X is not good as it could be in Ubuntu, why would anyone think that when it's not the default it'll be treated any better..

With all do respect, I'm not here to debate weather wayland is worse or better than x11.
The fact is it is here to stay.
But I also share your frustration, "systemd" when it was adopted by debian and ubuntu made me so [S]mad[/S] or frustrated that I was sure that it would send me away from linux due to it's wide spread adoption. I have warmed now to systemd.(Not in love with it...but learning it).
From what I take away from all of this is... _Gnome feels_ "wayland" is a lot more safer than Xorg.(Xorg/11 is prone to hacks)
User's perspective: is it easy to use or friendly to us....that's a big fat NO. (A new graphical server is a Huge undertaking dose not happen overnight)
I've just learned to embrace change and move forward.:)
I'm sure as it matures further, it will also improve...and _perhaps_ become a little more user friendly.
Respectfully.

---

### Post by VMC on 2017-04-28
One of things X does for me is work,  Wayland doesn't, and I doubt it ever will. I have an integrated graphics chip; low end, but at least it works under X.

The *phoronix* article was interesting though.

---

### Post by P-I H on 2017-04-29
Installed the daily ISO today. Had to do **sudo apt install gnome-shell** to activate Gnome. Made login with Gnome Wayland. Install Synaptic with Software, but this didn't worked. The installation stopped after about 50%. Closed Software logged out and changed login to Gnome. This might however be related to a lock on the administration directory.

---

### Post by ventrical on 2017-04-30
> **VMC said:**
> One of things X does for me is work,  Wayland doesn't, and I doubt it ever will. I have an integrated graphics chip; low end, but at least it works under X.

The *phoronix* article was interesting though.

Yes .. a lot of hardware will be obsoleted but 'wayland' will not be default. AFAIK. I had tested wayland when it first came out. It was had to get it working.

regards..

---

### Post by wildmanne39 on 2017-05-01
I have ubuntu gnome 17.10 running on a desktop that was in a closet for a while, I tried it on my new laptop and the desktop went crazy, it does not like my new amd graphics.

I had to try several different times to install it on the desktop, I tried to let it make the partitions as LVM but it would not install the boot loader, I tried to let it make normal partitions and still would not install the boot loader, so I had to manually create my own partitions and it installed without issue.

I still do not have wifi but it is late so I will deal with that tomorrow and see if the install issues have been reported at the same time.

---

### Post by Frogs Hair on 2017-05-01
Wayland on 17.04 works with integrated intel graphics though doesn't work on 17.10 with a much more powerful nVidia graphics card. I just get booted back to the login screen.

---

### Post by mc4man on 2017-05-01
> **Frogs Hair said:**
> Wayland on 17.04 works with integrated intel graphics though doesn't work on 17.10 with a much more powerful nVidia graphics card. I just get booted back to the login screen.
Here with an Optimus laptop if nvidia drivers are installed then there is no option for gnome - wayland. (- Though it wouldn't work anyway.
Additionally nvidia-settings wouldn't be able to open either, similar to synaptic, ect.
 
There is eglstreams support in Gnome but not as yet in Ubuntu. There's likely a number of things converging there that would need to be worked out, i.e. gdm vs. lightdm, the presence of xserver, whether eglstreams/wayland needs nvidia modesetting, ect.

The last one I don't know if required but atm there seems no way to enable nvidia modeset in Ubuntu. By default it's disabled & even if that is overidden somewhere in the boot process it's always disabled. 
Actually this is the reason Prime Synchronization does not work in Ubuntu with latest xserver. And no one seems to care to try to fix that...

---

### Post by wildmanne39 on 2017-05-01
I still well 24 hours after getting ubuntu gnome working on an older dell desktop. I bought a ethernet cable and plugged it in so I will not have to mess with a usb wifi adapter.

---

### Post by ventrical on 2017-05-02
> **mc4man said:**
> I've seen/read bits & pieces of that all before. It's all well & good, true, ect.

It still doesn't change the _fact_ that right now X is still a better user experience. 

So Canonical/Ubuntu would like current Ubuntu users to move to Gnome(gnome-shell) which while it's superior to Unity/compiz in that it's being actively developed, refined, ect.,  is to many (most) Ubuntu users an inferior concept compared to Unity/compiz.
So at the same time as that to present the clearly inferior  Wayland (currently)  as default makes no sense here.

What's the reasoning behind that? Maybe the crystal ball says Wayland will be good enough in 10 months, maybe Canonical just wants to wash their hands of the Desktop as quickly & cleanly as possible. Maybe ... whatever, I can't imagine.

As far as X11 being available as an alternate, well great. Currently X is not good as it could be in Ubuntu, why would anyone think that when it's not the default it'll be treated any better..



My point of view is that wayland will be scattershot by 18.04. Thats why unity7 of sorts will be in the universe. The real difference is how unity was tested in the wild.  Certainly the unityDesktop team  were diligent in their testing, they depended mostly on volunteers from the U+1 and elsewhere communities. More bugs were fixed and there was a certain enthusiasm while looking forward to testing  it. Gnome3 had a spike  of interest but it seemed, as wayland got introduced, that the *testing* experience became more difficult.  And even now it requires way more default tweaking after setup to try and get a handle on the *new* learning curve involved.  Not only the user-experience is affected , but ,also the user space... a case in point ... pasting screeshots to desktop.  Default unity presents the option (on one-click) to choose desktop (or other)  for pasting to default. Gnome three takes several clicks to adjust gnome-tweaktool to achieve this .. etc.. so the point being is that the end_user has to tailor a new curve to fit in with the preference-ility mechanism of gnome-3.

Because wayland is more or less unpredictable, (past and present), in it's hardware jockey video stack choices , testers in the wild seem to shy  away from it . However, it's only fair to say that unity did it's fair share of obsoleting a lot of legacy hardware and hence why we have Lubuntu and Xubuntu to test.  But, anyone  who is a diligent tester of all the flavors knows that unity7 was (is) the top end_user experience and I know we will miss it when it's gone. Lets not forget now that as unity8 has been dropped from development they also had to drop devrelopment of the 'mir' compositior.  I think that if gnome-shell becomes default (which looks like a definite will happen) gnome developers should re-think wayland but at this stage of the game it looks highly doubtful that will be the case.

regards..

---

### Post by mc4man on 2017-05-02
In regards to using the Desktop to store &  access files, in gnome-shell & X11 that works fine if option is enabled. However with Wayland-gnome there seems to be no concept of the Desktop. To see just right click on  the Desktop...

---

### Post by jbicha on 2017-05-02
@mc4man, You can have desktop icons with GNOME on Wayland. Make sure you've upgraded nautilus to 3.24 (available now in artful).

---

### Post by ventrical on 2017-05-02
> **mc4man said:**
> In regards to using the Desktop to store &  access files, in gnome-shell & X11 that works fine if option is enabled. However with Wayland-gnome there seems to be no concept of the Desktop. To see just right click on  the Desktop...

The latest  version is very slick. I want wayland to succeed. Really...  if they can do some of the things on wayland  what they did with compiz on 10.1o then that would be a real bonus.

---

### Post by mc4man on 2017-05-02
> **jbicha said:**
> @mc4man, You can have desktop icons with GNOME on Wayland. Make sure you've upgraded nautilus to 3.24 (available now in artful).
Yep, didn't notice it's now 'functional', thanks for mentioning.

Is there any current info on the state of eglstreams?

---

### Post by jbicha on 2017-05-02
> **mc4man said:**
> 
Is there any current info on the state of eglstreams?

Basically, the NVIDIA proprietary drivers currently in Ubuntu don't support GNOME on Wayland yet. (If you change the config to enable KMS which is needed for GNOME on Wayland, then GNOME on X will stop working.) [URL="https://launchpad.net/bugs/1672033"]LP: #1672033

[/URL]I don't have NVIDIA hardware myself.

---

### Post by mc4man on 2017-05-02
> **jbicha said:**
> Basically, the NVIDIA proprietary drivers currently in Ubuntu don't support GNOME on Wayland yet. (If you change the config to enable KMS which is needed for GNOME on Wayland, then GNOME on X will stop working.) [URL="https://launchpad.net/bugs/1672033"]LP: #1672033

[/URL]I don't have NVIDIA hardware myself.

Interesting..
So finally seem to be able to enable nvidia_drm.modeset 1 here on 17.10/gnome/gnome-shell which enables PRIME Synchronization in X11.
I.E. - 

> xrandr --verbose
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
.......
PRIME Synchronization: 1 
		supported: 0, 1

That gives some hope to getting this going in 16.04..

---

### Post by wildmanne39 on 2017-05-02
I am using 17.10 all the time now, I am new to gnome but I have not had any issues, except with the bootloader installing, but I worked around that.

---

### Post by BigCityCat on 2017-05-06
> **Frogs Hair said:**
> I just noticed gdebi package installer is affected as well , so I'm not sure filing a bug report on an application by application basis is the way to go here. This suggests to me a problem having to do with elevated permissions in general in regard to graphical applications.

It's my understanding that this is a design decision for security purposes. I think you could file bug reports but I wouldn't expect a resolution. I think the idea is that it is up to the app maintainers to fix the applications to request root access through gnome user privileges so to speak. I don't understand all the language but I have seen this spoken about on the current bug report regarding synaptic. They see it as a insecure design flaw by the application to run it's gui as root when all the application needs to do is request root privileges for the action requested. I don't think Wayland display was designed to display application gui as root. for security purposes. In layman's terms.

---

### Post by Frogs Hair on 2017-05-06
> **BigCityCat said:**
> It's my understanding that this is a design decision for security purposes. I think you could file bug reports but I wouldn't expect a resolution. I think the idea is that it is up to the app maintainers to fix the applications to request root access through gnome user privileges so to speak. I don't understand all the language but I have seen this spoken about on the current bug report regarding synaptic. They see it as a insecure design flaw by the application to run it's gui as root when all the application needs to do is request root privileges for the action requested. I don't think Wayland display was designed to display application gui as root. for security purposes. In layman's terms.

Not sure if you saw this post.

 >  					[IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **Frogs Hair** 					[[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("https://ubuntuforums.org/showthread.php?p=13638207#post13638207") 				

 				I just noticed gdebi package installer is  affected as well , so I'm not sure filing a bug report on an application  by application basis is the way to go here.
 			 		 	 > Yes, that's exactly what we're asking you to do. Thanks.

Almost every app works for me in a GNOME on Wayland session, either  through native Wayland (most GTK3 apps) or with XWayland. We want to  know about the ones that don't work, but it's ultimately up to the  developers of those apps to make the necessary changes. 				 			  			   		 			 				 			 				 			 			 				



---

### Post by mc4man on 2017-05-06
> **BigCityCat said:**
> the current bug report regarding synaptic. They see it as a insecure design flaw by the application to run it's gui as root when all the application needs to do is request root privileges for the action requested. 
So those reports are over a year old. I guess that "all the application needs to do is.." isn't that simple or Mv could not be bothered as of yet (or ever.

At the end of the day users expect installable apps to work, period..

---

### Post by jbicha on 2017-05-06
gdebi and synaptic are both exclusive to Debian-derived distros and only minimally maintained now. Since Debian GNOME still doesn't default to Wayland (probably will for Buster, the release after this year's Stretch) and Ubuntu wasn't that interested in Wayland until just recently, there had not been much pressure to get those working.

Anyway, we're tracking these issues now with the LP tag [wayland]("https://bugs.launchpad.net/ubuntu/+bugs?field.tag=wayland")

---

### Post by VMC on 2017-05-31
> **Frogs Hair said:**
> Just noticed my password prompts for synaptic , bleachbit, and nautilus as super user don't work in the wayland Gnome Shell session. :confused:

Bleachbit, also doesn't work on xwayland. There's a bug report for wayland here:
[https://bugs.launchpad.net/bleachbit/+bug/1686504](https://bugs.launchpad.net/bleachbit/+bug/1686504)

oops: I see just now that this topic has been solved .

---

### Post by mc4man on 2017-06-01
> **VMC said:**
> 

oops: I see just now that this topic has been solved .
Marked solved as I've no intention of using anytime soon

---

### Post by VMC on 2017-06-02
> **Frogs Hair said:**
> I only gave a general description.  


Bleachbit as Root

[https://bugs.launchpad.net/bugs/1686504](https://bugs.launchpad.net/bugs/1686504)

I "Yes, it affects me" on that report.

---

