---
title: "Xubuntu 13.10 XMir ISO Available For Testing"
date: 2013-08-05
forum: Ubuntu Development Version
---

### Post by philinux on 2013-08-05
> The Xubuntu team hasn't decided yet if the Xfce Ubuntu flavor will switch to XMir or continue with X.org for 13.10. Before making the decision, this needs to be properly tested so an Xubuntu ISO running on Mir & XMir has been made available for download.

[http://www.webupd8.org/2013/08/xubuntu-1310-xmir-iso-available-for.html](http://www.webupd8.org/2013/08/xubuntu-1310-xmir-iso-available-for.html)

---

### Post by ventrical on 2013-08-05
Thats a monster iso .. but here goes ....

btw .. I have had no luck with xmir and Xubuntu ..

we'll see .

thnx

---

### Post by grahammechanical on 2013-08-05
I will give it a go. I already have an install of Xubuntu running on xmir. It was made from the daily image of 3rd July and I followed the instructions on Ollie Reis blog. I am not too happy with the Xubuntu developers.

I reviewed an IRC chat session they had with Jon Bacon who wanted to know what assistance Canonical could give them in keeping up with these developments and their response was very immature. They demanded that Canonical promise that 13.10 would release with xmir which Jono could not give. He could only repeat that it was the intention to have it in 13.10. The Xubuntu devs then claimed that they had heard it all before and Canonical had broken its promises.

This session did reveal something very interesting. There are fewer Xfce developers than Xubuntu developers. If you are in that situation then you ought not to insult those who are offering to help.


And then there are the Kubuntu devs who say that as mir is not complete they do not want their users to be testers. As if user in Linux have not been testers from the beginning. But they are going to Weyland and I found this on the KDE site.

> The most complex task is to implement Wayland support in KWin, KDE  Plasma's Compositor and Window Manager. Since 4.11 KWin has some initial  Wayland support. It is not yet able to manage Wayland Clients

> 
Starting a new Wayland compositor would mean to stop the work on the X11  window manager, which would be a bad move as we cannot know yet whether  Wayland will succeed and will be supported on all hardware. 

So, Kubuntu users will be testers after all. Oh, I also have Kubuntu running on xmir. And that was on the daily image of the 2nd of July. Well the ISO has downloaded. So, I will burn it and test it tomorrow. I will even install it.

Regards.

---

### Post by ventrical on 2013-08-05
Here is what I have with the live session. More than what I would get from the ppa.
edit:

According to the website , the below says that xmir is running.

It is very spry at first but then the cursor slows down (as I am typing here right now).

---

### Post by slickymaster on 2013-08-05
> **ventrical said:**
> Thats a monster iso .. but here goes ....

btw .. I have had no luck with xmir and Xubuntu ..

we'll see .

thnx

:p Yeah, it's quite big but I think [unit193]("https://launchpad.net/~unit193") has made a fabulous work on it.

I would just like to point one thing which is what [xubuntu-devel team]("https://launchpad.net/~xubuntu-dev") really really need it's real hardware tests. Virtual Machines are not true enough for the objective at this subject, they work for other xubuntu tests, like standard release tests, but in this case what is needed is to know how it behaves in a wide wide wide variety of hardware, the extreme the cases the better.
And if you can manage to find the time to do it, please send your test reports to [EMAIL="xubuntu-devel@lists.ubuntu.com"][COLOR=#222222]xubuntu[/COLOR]-[COLOR=#222222]devel[/COLOR]@lists.ubuntu.com[/EMAIL]

---

### Post by cecilpierce on 2013-08-05
I DL both amd64 that just flickered white and flashed to the back ground image and the i686 that im on now, 
it took over an hour to dd this to a usb drive !

I don't know if mir is runing or not ?

---

### Post by ventrical on 2013-08-05
> **cecilpierce said:**
> I DL both amd64 that just flickered white and flashed to the back ground image and the i686 that im on now, 
it took over an hour to dd this to a usb drive !

I don't know if mir is runing or not ?


According to the web page and what they report , your xmir is running.

---

### Post by ventrical on 2013-08-05
> **slickymaster said:**
> :p Yeah, it's quite big but I think [unit193]("https://launchpad.net/%7Eunit193") has made a fabulous work on it.

I would just like to point one thing which is what [xubuntu-devel team]("https://launchpad.net/%7Exubuntu-dev") really really need it's real hardware tests. Virtual Machines are not true enough for the objective at this subject, they work for other xubuntu tests, like standard release tests, but in this case what is needed is to know how it behaves in a wide wide wide variety of hardware, the extreme the cases the better.
And if you can manage to find the time to do it, please send your test reports to [EMAIL="xubuntu-devel@lists.ubuntu.com"][COLOR=#222222]xubuntu[/COLOR]-[COLOR=#222222]devel[/COLOR]@lists.ubuntu.com[/EMAIL]


No virtual machine here! :)

 I'll try it on some older machines. Mabey there is hope for those older legacy P4s.

regards...

---

### Post by ventrical on 2013-08-05
Got it working on an old p4 with ATi Radeon. 

```

xubuntu@xubuntu:~$ ps ax | grep system-comp
 4133 ?        S      0:00 /bin/sh /usr/sbin/unity-system-compositor.sleep --enable-input=false --from-dm-fd 8 --to-dm-fd 11 --vt 7
 4137 ?        Sl     0:01 /usr/sbin/unity-system-compositor --enable-input=false --from-dm-fd 8 --to-dm-fd 11 --vt 7
 4268 ?        S      0:00 gksudo xfce4-terminal -x less /var/log/lightdm/unity-system-compositor.log
 4303 ?        Ss     0:00 /usr/bin/sudo -H -S -p GNOME_SUDO_PASS -u root -- xfce4-terminal -x less /var/log/lightdm/unity-system-compositor.log
 4306 ?        Sl     0:01 xfce4-terminal -x less /var/log/lightdm/unity-system-compositor.log
 4385 pts/0    Ss+    0:00 less /var/log/lightdm/unity-system-compositor.log
 4762 pts/2    S+     0:00 grep --color=auto system-comp
xubuntu@xubuntu:~$ lsmod|grep radeon
radeon                927911  5 
i2c_algo_bit           13197  1 radeon
ttm                    72297  1 radeon
drm_kms_helper         46867  1 radeon
drm                   235993  7 ttm,drm_kms_helper,radeon
xubuntu@xubuntu:~$ 

```

---

### Post by ventrical on 2013-08-05
> **cecilpierce said:**
> I DL both amd64 that just flickered white and flashed to the back ground image and the i686 that im on now, 
it took over an hour to dd this to a usb drive !

I don't know if mir is runing or not ?

Check your results with here ..

[http://i.imgur.com/1z3IKvd.png](http://i.imgur.com/1z3IKvd.png)

---

### Post by cecilpierce on 2013-08-05
@ventrical

I just installed the amd64 and it boots ok, on it now with nouveau, I don't think nvidia will work yet.

This is all I get in a terminal:
$ ps ax | grep system-comp
14640 pts/0    S+     0:00 grep --color=auto system-comp
and
[Error: Failed to set DRM crtc]  in the log file.

I might try the nvidia again later and see !

---

### Post by ventrical on 2013-08-05
> **cecilpierce said:**
> @ventrical

I just installed the amd64 and it boots ok, on it now with nouveau, I don't think nvidia will work yet.

This is all I get in a terminal:
$ ps ax | grep system-comp
14640 pts/0    S+     0:00 grep --color=auto system-comp
and
[Error: Failed to set DRM crtc]  in the log file.

I might try the nvidia again later and see !

 I used 32bit on a 64bit capable machine.

---

### Post by OrangeCrate on 2013-08-05
Tested on a Lenovo  T400, 64-bit, with the "Mobile Intel 4 Series Express Chipset Family"

xubuntu@xubuntu:~$  ps ax | grep system-comp
 2133 ?        S      0:00 /bin/sh /usr/sbin/unity-system-compositor.sleep --enable-input=false --from-dm-fd 9 --to-dm-fd 13 --vt 7
 2248 ?        Sl     0:10 /usr/sbin/unity-system-compositor --enable-input=false --from-dm-fd 9 --to-dm-fd 13 --vt 7
 3232 pts/0    S+     0:00 grep --color=auto system-comp

Comments:

Some lag when trying to type this post. (Would that be an issue with xmir? I'm not familiar with how this all works.)

An odd rendering of this post showed up pulsing/flickering on shut down (image was on a USB stick).

---

### Post by mikewhatever on 2013-08-05
Seems to have worked well here. The test machine was Intel's GMA500 abomination.

---

### Post by ventrical on 2013-08-05
> **OrangeCrate said:**
> Tested on a Lenovo  T400, 64-bit, with the "Mobile Intel 4 Series Express Chipset Family"

xubuntu@xubuntu:~$  ps ax | grep system-comp
 2133 ?        S      0:00 /bin/sh /usr/sbin/unity-system-compositor.sleep --enable-input=false --from-dm-fd 9 --to-dm-fd 13 --vt 7
 2248 ?        Sl     0:10 /usr/sbin/unity-system-compositor --enable-input=false --from-dm-fd 9 --to-dm-fd 13 --vt 7
 3232 pts/0    S+     0:00 grep --color=auto system-comp

Comments:

Some lag when trying to type this post. (Would that be an issue with xmir? I'm not familiar with how this all works.)

An odd rendering of this post showed up pulsing/flickering on shut down (image was on a USB stick).


  I had two machines do that . nVida and ATi .. but not Intel graphics.

---

### Post by OrangeCrate on 2013-08-05
> **ventrical said:**
> I had two machines do that . nVida and ATi .. but not Itnel graphics.

Just to be sure what was happening, I went ahead and installed to disk. Everything works fine. No typing lag or odd shutdown. I'm OK with the change if it happens.

Edit:

Acting up again, lag when typing is back.

> 
What graphics hardware is supported by XMir?

If your Intel, AMD, or NVIDIA card works without proprietary drivers, it will work with XMir.


[http://fridge.ubuntu.com/2013/06/27/mir-plans-in-13-10/](http://fridge.ubuntu.com/2013/06/27/mir-plans-in-13-10/)

If the folks behind the curtain decide to go with XMir, I guess we'll see in the production release, if that's true...

---

### Post by ventrical on 2013-08-05
> **OrangeCrate said:**
> Just to be sure what was happening, I went ahead and installed to disk. Everything works fine. No typing lag or odd shutdown. I'm OK with the change.

Edit:

Acting up again, lag when typing is back. Guess I'm not OK with it, at least for now.

  I think they will work it out. I noticed that when I was typing in terminal or mousepad that the cursor would delay but if I moved my mouse it would accelerate to normal speed - so - just jiggle mouse when typing :) lol

  It worked great on the Dell Dimension (Intel chipset). I would like to see Ubuntu_Unity give us  one of these.  Using the old ppa method  works sometimes and then don't work after an update etc... patience :)

---

### Post by OrangeCrate on 2013-08-05
^,

I was editing my post as you were typing. Sorry. And yes, I think they'll get it worked out too.

---

### Post by ventrical on 2013-08-05
> **OrangeCrate said:**
> ^,

I was editing my post as you were typing. Sorry. And yes, I think they'll get it worked out too.

I just installed too. I notice that the install to hdd still has the startup script that brings in the terminal after logon. Very kewl indeed :) lol

Typing is very fast - no lag. I am on nouveau. I am going to try and install ubuntu-desktop and see if I can get unity to work normally.

  There is some horizontal tearing of course..

edit:

 I am getting very smooth scrolling in forefox..


No big prob for testing..

---

### Post by ventrical on 2013-08-05
I ran the hypertorus in <screensaver> and I noticed that the colours are more full and defined and that the movement is more fluid and balanced. I am not sure if this is an effect of xmir or just some fixes over the past year or so. Still very fast and fluid.

---

### Post by ventrical on 2013-08-05
It must be xmir bringing all the screensaver xtras to life because they are displaying a 3D effect that I have not noticed before . especially with the 'noof' screesaver... jumps right off the screen..:)

---

### Post by QDR06VV9 on 2013-08-05
> **slickymaster said:**
> :p Yeah, it's quite big but I think [unit193]("https://launchpad.net/~unit193") has made a fabulous work on it.

I would just like to point one thing which is what [xubuntu-devel team]("https://launchpad.net/~xubuntu-dev") really really need it's real hardware tests. Virtual Machines are not true enough for the objective at this subject, they work for other xubuntu tests, like standard release tests, but in this case what is needed is to know how it behaves in a wide wide wide variety of hardware, the extreme the cases the better.
And if you can manage to find the time to do it, please send your test reports to [EMAIL="xubuntu-devel@lists.ubuntu.com"][COLOR=#222222]xubuntu[/COLOR]-[COLOR=#222222]devel[/COLOR]@lists.ubuntu.com[/EMAIL]

Will test on Lenovo B570 Lappy
and on a Acer AMD Quadcore Nviidia Gforce350 video..:rolleyes:

---

### Post by ventrical on 2013-08-06
I have Unity-Desktop working just great on the Xubuntu xmir .iso !! :) I don't know why  ubuntu-desktop flavor never thought of this  Kudos to Xubuntu!

And there is no lag in the Unity dash.  Only thing I notice is that  some of the icons on the Unity Panel are of a different style.

The workplace switcher works also. Also there is an improvmenet with the resizing of the Unity Panel Icons. Now, the slider to resize does not delay (like it has been for the past 3 testing cycles) so Xubuntu is definetly onto something here and we ought to listen. At this stage of the game I am a firm believer that Xubuntu can do for Unity-Desktop +xmir what it can't do for itself.

Thanks ! :)lol

 I hope the Unity team is listening.

```

ventrical@ventrical-xmir-fazoomer:~$ ps ax | grep system-comp
  946 ?        S      0:00 /bin/sh /usr/sbin/unity-system-compositor.sleep --enable-input=false --from-dm-fd 10 --to-dm-fd 13 --vt 7
  953 ?        Sl     0:10 /usr/sbin/unity-system-compositor --enable-input=false --from-dm-fd 10 --to-dm-fd 13 --vt 7
 2311 ?        Sl     0:01 gksudo xfce4-terminal -x less /var/log/lightdm/unity-system-compositor.log
 2361 ?        Ss     0:00 /usr/bin/sudo -H -S -p GNOME_SUDO_PASS -u root -- xfce4-terminal -x less /var/log/lightdm/unity-system-compositor.log
 2435 ?        Sl     0:00 xfce4-terminal -x less /var/log/lightdm/unity-system-compositor.log
 2445 pts/2    Ss+    0:00 less /var/log/lightdm/unity-system-compositor.log
 3015 pts/0    S+     0:00 grep --color=auto system-comp
ventrical@ventrical-xmir-fazoomer:~$ lsmod|grep nouveau
nouveau               882905  6 
mxm_wmi                12893  1 nouveau
wmi                    18590  2 mxm_wmi,nouveau
video                  18937  1 nouveau
ttm                    72297  1 nouveau
drm_kms_helper         46867  1 nouveau
drm                   235993  8 ttm,drm_kms_helper,nouveau
i2c_algo_bit           13197  1 nouveau
ventrical@ventrical-xmir-fazoomer:~$ 


```

---

### Post by grahammechanical on 2013-08-06
Well I have run the live session twice (wait until we see the TRY-INSTALL dialog and press Enter three times and the live session loads with XMIR). Apart from the message in the terminal I ran 4 other commands that test if XMIR is loaded and I get the expected result. This is on a Nvidia GT220 and the session is stable. I am posting from it now. 

For the information of those trying XMIR for the first time, the typing/insertion point lag-jump takes time to manifest. and the shutdown flashing between a shutdown screen and a Linux black screen with text from a video cache is also usual.

One weird thing. When I ran the live session from the TRY-INSTALL dialog I got three internal error messages (nm-applet & 2 for apport-gtk) Which I get on my install of saucy Ubuntu. What is wierd is that I did not get these error messages when I ran the live session from the text mode screen. 

I will now install Xubuntu-xmir.

Regards.

---

### Post by ventrical on 2013-08-06
I got most of the above but it is running just fine here with nouveau. I also installed ubunt-desktop+ccsm and it is running more smoother than usual .

 It is hardly using any resources (even with ccsm full load) and there is only very minimal tearing with wobbly windows. 

Workplace Switcher is not working but that is probably due to having cube+rotate and desktop wall disabled.

In 'top' unity-system-comp is only using .3% of CPU and up to 3.5Mb of RAM .. evry stable and well managed there.

  Of course there is some slight instability with ccsm... but it is working better off the ubuntu-desktop on xubuntu+xmir than if I were to have it run on the ubuntu .iso.  A real feat for xubuntu.

---

### Post by grahammechanical on 2013-08-06
Well the install of Xubuntu-Xmir failed in the sense that it is not running on XMIR. No, I did not tick Install Third Party Software. The system is not using an Nvidia driver. I checked Addtitional Drivers tab. This is the message in the terminal that appears at log in.

> ERROR: /build/buildd/mir-0.0.8+13.10.20130730bzr898saucy0/src/server/graphics/gbm/linux_virtual_terminal.cpp(137): Throw in function virtual void mir::graphics::gbm::LinuxVirtualTerminal::register_switch_handlers(mir::MainLoop&, const std::function<bool()>&, const std::function<bool()>&)
Dynamic exception type: boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<std::runtime_error> >
std::exception::what: Failed to set the current VT mode
[boost::errinfo_errno_*] = 5, "Input/output error"

I also ran the usual commands to test for xmir. It is not there in LoadModule. This is a bit wierd as the live session runs with Xmir.

UPDATE: I ran the Software Updater. It brought in a few MB. I then rebooted and this is the message in the terminal

> dm_connection_start
set_active_session '0'
set_active_session

```
 grep -i LoadModule /var/log/Xorg.0.log
```

gives this
> 
    28.719] (II) LoadModule: "glx"
[    28.762] (II) LoadModule: "xmir"
[    28.792] (II) LoadModule: "nvidia"
[    28.794] (II) UnloadModule: "nvidia"
[    28.794] (II) LoadModule: "nouveau"
[    28.801] (II) LoadModule: "vesa"

So XMIR is now running. Perhaps it takes a second reboot after installation to get Xmir on the job. The user is not supposed to notice any difference between Xserver and Xmir so I don't think it matters too much from a ordinary user's point of view if it is Xserver or Xmir that is active. At least until the middle of 2014 when support for Xserver is dropped. These are the important questions: Is the platform stable? Do the applications load and run as they should? And the answer is Yes. Things could be a bit better, but the answer is Yes.

Regards.

---

### Post by ventrical on 2013-08-06
In this installed xubuntu-xmir  session I have xmir (unity-system-compositor) working just fine.

Download:

```

sudo apt-get install htop

```

and then run it in terminal. You should see 'unity-system-compositor' popping in and out.

[http://www.youtube.com/watch?v=uUSVaoeIFbs&feature=youtu.be](http://www.youtube.com/watch?v=uUSVaoeIFbs&feature=youtu.be)

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)

---

### Post by ventrical on 2013-08-06
Here is the flickerty bug from the Xubuntu+xmir Live session when  going for shutdown.

[http://www.youtube.com/watch?v=J40fDdN3Dp8&feature=youtu.be](http://www.youtube.com/watch?v=J40fDdN3Dp8&feature=youtu.be)

However, this is resolved on full install.

Regards..

---

### Post by ventrical on 2013-08-06
> **grahammechanical said:**
> 


So XMIR is now running. Perhaps it takes a second reboot after installation to get Xmir on the job. The user is not supposed to notice any difference between Xserver and Xmir so I don't think it matters too much from a ordinary user's point of view if it is Xserver or Xmir that is active. At least until the middle of 2014 when support for Xserver is dropped. These are the important questions: Is the platform stable? Do the applications load and run as they should? And the answer is Yes. Things could be a bit better, but the answer is Yes.

Regards.

With 70 or so days to go I think the team has done a great job to deliver xmir to the desktop PC for  release with 13.10. Obviously they have been buring the midnight oil .. as well as us testers also.

Regards..

---

### Post by grahammechanical on 2013-08-06
I have just posted my results on Etherpad and I notice that some are reporting issues that are usual for a development ISO image and are not Xmir related at all. I think that it is important that we distinguish between stuff that we expect to happen during a development cycle and stuff that is particular to a specific code.

Regards.

---

### Post by ventrical on 2013-08-06
I am moving over to my ATi based box and see how the xubuntu+xmir install works there.

---

### Post by slickymaster on 2013-08-06
> **OrangeCrate said:**
> Tested on a Lenovo  T400, 64-bit, with the "Mobile Intel 4 Series Express Chipset Family"

xubuntu@xubuntu:~$  ps ax | grep system-comp
 2133 ?        S      0:00 /bin/sh /usr/sbin/unity-system-compositor.sleep --enable-input=false --from-dm-fd 9 --to-dm-fd 13 --vt 7
 2248 ?        Sl     0:10 /usr/sbin/unity-system-compositor --enable-input=false --from-dm-fd 9 --to-dm-fd 13 --vt 7
 3232 pts/0    S+     0:00 grep --color=auto system-comp

Comments:

Some lag when trying to type this post. (Would that be an issue with xmir? I'm not familiar with how this all works.)

An odd rendering of this post showed up pulsing/flickering on shut down (image was on a USB stick).

Most probably. See this: [Bug #1199450]("https://bugs.launchpad.net/mir/+bug/1199450")

---

### Post by mc4man on 2013-08-06
Overall works fine here though am disappointed that video tearing exists even with compositing turned off
(though that seems to also occur in default Xubuntu
Whether one can properly turn off compositing in a live session without logging out or restarting not sure, guess I'll try an install or go back to live & set up a new user to log out/in to.
(currently no live sessions I've tried allow logging out  for the default live session user, only an added user.

---

### Post by slickymaster on 2013-08-06
> **mc4man said:**
> Overall works fine here though am disappointed that video tearing exists even with compositing turned off
(though that seems to also occur in default Xubuntu...

When running Xubuntu on XMir, I got no video tearing. This had always been my biggest issue with Xfce/Xfwm, the ugly video tearing when scrolling in Chrome, watching videos, moving windows etc... I had always had to resort to using a 3rd party opengl compositor and I'd rather not, I prefer to use the native WM.

In my testing of the ISO on an Intel HD4000 there was absolutely no tearing, and scrolling in Chrome was butter-smooth. I watched a full-screen html5 video and again, no tearing.

---

### Post by ventrical on 2013-08-06
Here is running xmir on older radeon card.

```

ventrical@ventrical-P4M266A-8237:~$  grep -i LoadModule /var/log/Xorg.0.log
[    44.583] (II) LoadModule: "glx"
[    44.758] (II) LoadModule: "xmir"
[    44.831] (II) LoadModule: "fglrx"
[    44.859] (II) UnloadModule: "fglrx"
[    44.859] (II) LoadModule: "ati"
[    44.877] (II) LoadModule: "radeon"
[    44.932] (II) LoadModule: "vesa"
[    44.950] (II) LoadModule: "modesetting"
[    44.960] (II) LoadModule: "fbdev"
[    44.979] (II) LoadModule: "fglrx"
[    44.980] (II) UnloadModule: "fglrx"
[    44.980] (II) LoadModule: "ati"
[    44.980] (II) LoadModule: "vesa"
[    44.980] (II) UnloadModule: "vesa"
[    44.980] (II) LoadModule: "modesetting"
[    44.981] (II) UnloadModule: "modesetting"
[    44.981] (II) LoadModule: "fbdev"
[    44.981] (II) UnloadModule: "fbdev"
[    44.991] (II) UnloadModule: "vesa"
[    44.991] (II) UnloadModule: "modesetting"
[    44.991] (II) UnloadModule: "fbdev"
[    45.010] (II) LoadModule: "dri2"
[    45.010] (II) LoadModule: "exa"
[    45.030] (II) LoadModule: "fb"
[    45.052] (II) LoadModule: "ramdac"
[    45.937] (II) LoadModule: "evdev"
ventrical@ventrical-P4M266A-8237:~$ 

```

---

### Post by ventrical on 2013-08-06
> **slickymaster said:**
> When running Xubuntu on XMir, I got no video tearing. This had always been my biggest issue with Xfce/Xfwm, the ugly video tearing when scrolling in Chrome, watching videos, moving windows etc... I had always had to resort to using a 3rd party opengl compositor and I'd rather not, I prefer to use the native WM.

In my testing of the ISO on an Intel HD4000 there was absolutely no tearing, and scrolling in Chrome was butter-smooth. I watched a full-screen html5 video and again, no tearing.


  I  have  smooth scrolling and hardly no tear in xubuntu. Not much either in Unity with excepetion of wobbly windows.

 Ok.. time to install ubuntu-desktop and ccsm on top of all this once again :)

---

### Post by pqwoerituytrueiwoq on 2013-08-06
Seems to work perfectly on my laptop, thought xbacklight does not work,however my backlightx script does
cairo-dock seems to work
temperatures look good
kazam works
youtube html5 works with good temps
suddenly trying is impossible, seems to be lagging (nrv not lagging, but just displaying 1 keypress behind)
webcam works
flash works on youtube
suddenly able to type in terminal properly again
back to 1 key behind lag
lag seems to be on a per tab basis in my terminal
hedgewars works, looks like a new version to me,unless xmir made a transition feature work
lag is not limited to terminal, started happening in my alt+tab
key lag also effects copy paste via middle click
does flicker at shutdown
[COLOR=#ff0000]EVERY KEYPRESS SHOWS UP IN THE TTY XMIR IS RUNNING ON[/COLOR]: probably for debugging, but it is a security issue
shutdown failed, used REISUB

sound is broken, same in virtualbox without mir

---

### Post by slickymaster on 2013-08-06
> **pqwoerituytrueiwoq said:**
> Seems to work perfectly on my laptop, thought xbacklight does not work,however my backlightx script does
cairo-dock seems to work
temperatures look good
kazam works
youtube html5 works with good temps
suddenly trying is impossible, seems to be lagging (nrv not lagging, but just displaying 1 keypress behind)
webcam works
flash works on youtube
suddenly able to type in terminal properly again
back to 1 key behind lag
lag seems to be on a per tab basis in my terminal
hedgewars works, looks like a new version to me,unless xmir made a transition feature work
lag is not limited to terminal, started happening in my alt+tab
key lag also effects copy paste via middle click
does flicker at shutdown
[COLOR=#ff0000]EVERY KEYPRESS SHOWS UP IN THE TTY XMIR IS RUNNING ON[/COLOR]: probably for debugging, but it is a security issue
shutdown failed, used REISUB

sound is broken, same in virtualbox without mir

The keypress lagging is already filled as a bug: [Bug #1199450]("https://bugs.launchpad.net/mir/+bug/1199450")

---

### Post by OrangeCrate on 2013-08-06
> **slickymaster said:**
> Most probably. See this: [Bug #1199450]("https://bugs.launchpad.net/mir/+bug/1199450")

Good catch, thanks.

After my flurry of activity in this thread yesterday, something came up, and I had to move on. Meant to get back here, and also to research any bugs related to my observations/comments, but, hadn't gotten to it yet. I do now feel confident, that this issue will be fixed prior to Saucy's official release.

---

### Post by pqwoerituytrueiwoq on 2013-08-06
found a cursor bug on my desktop (specs in sig)
in firefox when i view a raw image and move the mouse over it the cursor leaves artifact layer that is visible under the cursor at the max cursor size
screenshots and kazam are unable to capture it
using the stock drivers on a live session

hedgewars seems to work on it
when i played it on my laptop i seem to recall sound despise not having any sound controls
on my desktop i have no sound, cause i can't set it to use HDMI audio

no flickering on shutdown with my desktop, but the shutdown tty has artifacts from the desktop session where cario dock was

---

### Post by mc4man on 2013-08-06
> **slickymaster said:**
> When running Xubuntu on XMir, I got no video tearing. This had always been my biggest issue with Xfce/Xfwm, the ugly video tearing when scrolling in Chrome, watching videos, moving windows etc... I had always had to resort to using a 3rd party opengl compositor and I'd rather not, I prefer to use the native WM.

In my testing of the ISO on an Intel HD4000 there was absolutely no tearing, and scrolling in Chrome was butter-smooth. I watched a full-screen html5 video and again, no tearing.

On nouveau with the xmir-xubuntu have no tearing in scrolling, do on moving windows (could really care less), & definitely on videos, both with some dvd scene clips that are prone & with a small tear test vid.
(the tear test vid was linked here - 
[http://ubuntuforums.org/showthread.php?t=2164393&p=12745821#post12745821](http://ubuntuforums.org/showthread.php?t=2164393&p=12745821#post12745821)

Will give the live session a test on newer laptop with a nvidia 660m so intel 4000 on live session.

---

### Post by pqwoerituytrueiwoq on 2013-08-06
Tried nvidia driver from there site that was released yesterday, it just uses xorg still no mir support from nvidia :(
was tricky getting it to install since i could not open a tty using mir, so i installed it via ssh

---

### Post by cariboo on 2013-08-06
I'm running it here on my netbook,using the i945 graphics chipset, aside from the keyboard lag, (it's really annoying in a terminal) everything seems to be working great. Even 720p youtube videos seem to run a bit better.

---

### Post by inte2 on 2013-08-07
> **grahammechanical said:**
> 

So, Kubuntu users will be testers after all. Oh, I also have Kubuntu running on xmir. And that was on the daily image of the 2nd of July. Well the ISO has downloaded. So, I will burn it and test it tomorrow. I will even install it.

Regards.

Wow, running KDE on Xmir, what an achievement! Xmir is just a compatibility layer for X11-apps running under Mir in a nested XServer. You could do the same with Wayland, of course. But why would anyone do that, it's a rather stupid idea.
What the Kubuntu guys are talking about is real programming and native development. Nokia (RIP) ported most of the Qt-bindings to Wayland for their MeeGo project (which is now beeing finished by Jolla (using Wayland, of course)). Since KDE is based on Qt, the native port is in the works of course, and THAT is what seems to make great progress.
I personally think Mir is crap and I'm happy to hear Kubuntu has chosen Wayland and not Mir AND most of the porting seems to be completed already, according to your quote. Thanks for that great news!

---

### Post by ventrical on 2013-08-07
> **inte2 said:**
> 
I personally think Mir is crap...

But it is actually *doing* somthing for the desktop testers-users of Unity with this new release of Xubuntu+mir. I am noticing some smoother animations already ... although be it they be the screensaver xtras and Unity in general .. it has come a long way since we started testing mir in raring and now saucy.

Regards..

---

### Post by grahammechanical on 2013-08-07
> AND most of the porting seems to be completed already, according to your quote.

No.The page says exactly the opposite. The KDE developers are going to stick with Kwin  (X11 Window Manager/Compositor) and not develop a KDE Wayland compositor because

> 
Wayland support in the KDE Plasma Workspaces is still in a pre-alpha  state. The workspaces have been developed for X11 and much functionality  relies on X11. To be able to make proper use of Wayland these bits have  to be rewritten. 


The most complex task is to implement Wayland support in KWin,  KDE Plasma's Compositor and Window Manager. Since 4.11 KWin has some  initial Wayland support. It is not yet able to manage Wayland Clients  but can use another Wayland compositor as a rendering target instead of  X. This is the beginning of a Wayland session compositor running on top  of a Wayland system compositor.

> 
Writing a new Wayland Compositor would require to rewrite the complete  X11 workspace in one go. This includes not only the Window Manager, but  also parts of Plasma, KDM, Screen Locker and many, many more. This would  take a long development time and the transition would not be smooth,  very likely buggy and with regressions like the 4.0 introduction. We do  not want to break the desktop!

Regards.

---

### Post by mkis62 on 2013-08-07
Posting from live session.
Terminal is a big pain. Installed Terminator, and working better.
glxgears reporting unusual framerate (600-700 fps), but the screensavers reporting still between 15-30 fps.
After installing xubuntu-restricted-extras, music and videos are smooth
on Youtube's full HD videos the processor usage is quite high, and the core temperatures too,  for this computer specs (Samsung R538).
The programs installed running just fine, with some lags on typing (right now, on this reply).

The first impression: very smooth (except writing on it).
-------------
Intel Pentium CPU P6200 (dual core)  @ 2.13GHz, 3GB RAM, on-board graphics
Multiboot: Xubuntu 13.10 (the first choice), MintX 15, Manjaro Ascella (unstable), win7

---

### Post by ventrical on 2013-08-07
> **mc4man said:**
> Overall works fine here though am disappointed that video tearing exists even with compositing turned off
(though that seems to also occur in default Xubuntu
Whether one can properly turn off compositing in a live session without logging out or restarting not sure, guess I'll try an install or go back to live & set up a new user to log out/in to.
(currently no live sessions I've tried allow logging out  for the default live session user, only an added user.

There is absolutely no tear on my Dell Dimension3100  under xubuntu:

```

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

```

 and finally I can get super- smooth scrolling in ff!

This is the 4th machine where I have had success with the xubuntu+xmir iso + installed ubuntu-desktop.Thats nouveau, ati radeon and now Intel drivers that this .iso works on.


Off now to MSi B75MA-P45 sandybridge:)

edit:

There were problems with sandybridge(Sandybridge Desktop x86/MMX/SSE2) at first. The xubuntu screen was distorted and illegible after three re-boots. I then  installed ubuntu-desktop and it is working exceptionally smooth with no tearing. It actually auto-resolved it's own errors. One of those phenoms about Ubuntu.

```

ventrical@ventrical-MS-7798:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
11961 frames in 5.0 seconds = 2390.200 FPS
11160 frames in 5.0 seconds = 2231.456 FPS
11094 frames in 5.0 seconds = 2217.437 FPS
11089 frames in 5.0 seconds = 2217.233 FPS
11114 frames in 5.0 seconds = 2222.327 FPS
11047 frames in 5.0 seconds = 2209.271 FPS
11118 frames in 5.0 seconds = 2222.156 FPS
11044 frames in 5.0 seconds = 2208.742 FPS
11049 frames in 5.0 seconds = 2208.673 FPS
11090 frames in 5.0 seconds = 2216.986 FPS
10954 frames in 5.0 seconds = 2190.377 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 378272 requests (378272 known processed) with 0 events remaining.
ventrical@ventrical-MS-7798:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +103.0°C)
temp2:        +29.8°C  (crit = +103.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +32.0°C  (high = +82.0°C, crit = +102.0°C)
Core 0:         +30.0°C  (high = +82.0°C, crit = +102.0°C)
Core 1:         +31.0°C  (high = +82.0°C, crit = +102.0°C)

ventrical@ventrical-MS-7798:~$ 

```

edit- Temperatures reflect results after 3 uptime hours.

---

### Post by ventrical on 2013-08-07
I installed ccsm as was running some tests and my processors and graphics  actually got cooler.

```

ventrical@ventrical-MS-7798:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +103.0°C)
temp2:        +29.8°C  (crit = +103.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +29.0°C  (high = +82.0°C, crit = +102.0°C)
Core 0:         +27.0°C  (high = +82.0°C, crit = +102.0°C)
Core 1:         +28.0°C  (high = +82.0°C, crit = +102.0°C)

ventrical@ventrical-MS-7798:~$ 

```

---

### Post by slickymaster on 2013-08-08
Just a heads up.
[URL="https://bugs.launchpad.net/mir/+bug/1199450"]
Bug #1199450[/URL] on Mir, that had been annoying some of us testing the ISO is as of now marked with a Fix Committed status.

The fix was committed into [lp:mir]("https://bugs.launchpad.net/+branch/mir") at revision 948, scheduled for release in mir, milestone 0.0.9.

---

### Post by philinux on 2013-08-08
I've been waiting to get to GF's to test the 32 bit version as she has an ancient machine. Let's see how it goes this weekend.

---

### Post by ventrical on 2013-08-09
Updating/Upgrading the xubuntu xmir install will now break.

```

/usr/sbin/unity-system-compositor: error while loading shared libraries: libmirserver.so.1: cannot open shared object file: No such file or directory
/var/log/lightdm/unity-system-compositor.log (END)



```

```

Unpacking replacement xfwm4 ...
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0:i386 ...
No such key 'auto-launch' in schema 'com.ubuntu.update-notifier' as specified in override file '/usr/share/glib-2.0/schemas/20_xubuntu-default-settings.gschema.override'; ignoring override for this key.
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libmirserver1_0.0.8+13.10.20130808.2bzr948saucy0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ventrical@ventrical-xmir:~$ 


```

---

### Post by slickymaster on 2013-08-09
FYI

In a email to [EMAIL="xubuntu-devel@lists.ubuntu.com"]xubuntu-devel@lists.ubuntu.com[/EMAIL], Jono Bacon asked everyone testing Mir to:> ...make it easier for the Mir team to track bugs uncovered in flavor testing (such as with the recent round of XMir testing in the Xubuntu community), I would like to ask that you file bugs with issues you have found and tag the bug with 'flavormirbug'.

The resulting search which brings back all of these bugs (across multiple projects) is at:
[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=&orderby=-importance&field.status%3Alist=NEW&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&assignee_option=any&field.assignee=&field.bug_reporter=&field.bug_commenter=&field.subscriber=&field.tag=flavormirbug&field.tags_combinator=ANY&field.status_upstream-empty-marker=1&field.has_cve.used=&field.omit_dupes.used=&field.omit_dupes=on&field.affects_me.used=&field.has_patch.used=&field.has_branches.used=&field.has_branches=on&field.has_no_branches.used=&field.has_no_branches=on&field.has_blueprints.used=&field.has_blueprints=on&field.has_no_blueprints.used=&field.has_no_blueprints=on&search=Search](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=&orderby=-importance&field.status%3Alist=NEW&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&assignee_option=any&field.assignee=&field.bug_reporter=&field.bug_commenter=&field.subscriber=&field.tag=flavormirbug&field.tags_combinator=ANY&field.status_upstream-empty-marker=1&field.has_cve.used=&field.omit_dupes.used=&field.omit_dupes=on&field.affects_me.used=&field.has_patch.used=&field.has_branches.used=&field.has_branches=on&field.has_no_branches.used=&field.has_no_branches=on&field.has_blueprints.used=&field.has_blueprints=on&field.has_no_blueprints.used=&field.has_no_blueprints=on&search=Search)Also, according to his email the final component for Mir and XMir being in the Saucy archive is landing tomorrow, and he has assurances that many issues reported in the testing should have been fixed.

---

### Post by The Cog on 2013-08-09
Dumb question, probably just showing my ignorance:
I have read that next year, mir intends to drop its support for X. 

If that's true, then what is the future for XFCE/Xubuntu? Won't it cease to work on mir? 

Even if XFCE/Xubuntu continues to work on mir, what about older program binaries that (I presume) are written to run on X? I'm thinking of things like Google Earth, Doom3, UT2004.

---

### Post by grahammechanical on 2013-08-09
I guess it depends on what is meant by "dropping support for X."  I will have to check where I read that but I thought it was Ubuntu/Canonical that was dropping support some time during 2014. I took that to mean that Ubuntu 14.10 will not have the Xserver in the ISO image. Why would the Xserver be needed if we get Nouveau and proprietary drivers working with MIR and giving a user expected performance? 

What support does Ubuntu give to X right now? I see packages being updated. What else would we include as support that is to be dropped and who will it affect? Why will Xfce/Xubuntu cease to work? It works on Xmir now. It will work on MIR. I do not understand why it will cease to work.

I have found this as the roadmap for 2013.
> 
Unity Next & Mir window management are completely integrated with  the rest of the system to support an Ubuntu Phone product. For the  desktop/laptop form-factor, we want to fully replace X in user sessions  and _provide a legacy mode that allows to run legacy X clients against an  on-demand rootless X server. _A cascade of display servers/shells is  implemented, with the session-level instances talking to a global system  compositor instance, providing a flicker-free, tightly integrated and  beautiful UX.

[https://wiki.ubuntu.com/Mir/Spec?action=show&redirect=MirSpec](https://wiki.ubuntu.com/Mir/Spec?action=show&redirect=MirSpec)

And this

> The chosen approach was to develop Mir, our own Display Server which is  engineered driven by the designs and requirements that our larger vision  dictates &#8211; no compromises, no crude hacks, fully testable & tested,  performance in mind, _support for legacy X applications,_ developed by  Ubuntu for Ubuntu.

[http://www.olli-ries.com/mir-unity-qml-unity-apis-unity/](http://www.olli-ries.com/mir-unity-qml-unity-apis-unity/)

I will add more as I re-find stuff.
> 
And we also know that we can deliver a high-performance X stack on Mir,  which means any application that talks X, or any desktop environment  that talks X, will perform just as well with Mir, and have smoother  transitions in and out thanks to the system compositor capabilities that  Mir provides.

On Ubuntu, we&#8217;re committed that every desktop environment perform well  with Mir, either under X or directly. We didn&#8217;t press the &#8216;GO&#8217; button on  Mir until we were satisfied that the whole Ubuntu community, and other  distributions, could easily benefit from the advantages of a leaner,  cleaner graphics stack. We&#8217;re busy optimising performance for X now so  that every app and every desktop environment will work really well in  13.10 under Mir, without having to make any changes. And we&#8217;re taking  patches from people who want Mir to support capabilities they need for  native, super-fast Mir access. Distributions should be able to provide  Mir as an option for their users to experiment with very easily &#8211; the  patch to X is very small (less than 500 lines


[http://www.markshuttleworth.com/archives/1269](http://www.markshuttleworth.com/archives/1269)

Regards.

---

### Post by slickymaster on 2013-08-09
I'm convinced that in the long term X.org will be maintained.
XMir will have to be updated to match each new X.org release regardless. When the time comes that there will be no new X.org releases, then there will be also no new XMir releases either.

---

### Post by The Cog on 2013-08-09
Thanks grahammechanical, that makes sense. I had perhaps misunderstood that the x in xmir was just temporary legacy support, and that in the future it would just be mir without that x compatibility layer. Re-reading the links you gave reinforces the feeling that mir intends to support x applications for some time to come.

---

### Post by Chanath on 2013-08-10
I installed it, but didn't notice any changes of its work. What am I to look for? Xubuntu in my laptop works always smoothly.

---

### Post by The Cog on 2013-08-10
Run this command to check that xmir is active. You shoudl see several processes of unity-system-compositor running:
```
ps -ef | grep unity
```
Assuming it is running, then I think they want to know if everything looks normal, or whether you see any differences. I guess if everyone says it looks fine then they will decide to go with xmir in the next release, but if people report lots of problems they'll stick with good ol' X. The more people who report results, good or bad - both matter, the better basis they have for that decision.

---

### Post by grahammechanical on 2013-08-10
> **Chanath said:**
> I installed it, but didn't notice any changes of its work. What am I to look for? Xubuntu in my laptop works always smoothly.

Have you done a second reboot. I found that the first reboot after installation was running on Xserver but I rebooted and this time it was running on xmir. We are not supposed to notice anything different. That is the point. The aim is to get to a situation where a user installs and has the same user experience as he would have done without xmir and mir being developed.

This is what I see when I run commands to find out if xmir is loaded.

```
grep -i xmir /var/log/Xorg.0.log
```

> [    46.997] (II) LoadModule: "xmir"
[    46.998] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[    47.001] (II) Module xmir: vendor="X.Org Foundation"
[    47.069] (II) NOUVEAU(0): Output XMIR-1 has no monitor section
[    47.069] (II) NOUVEAU(0): Printing probed modes for output XMIR-1
[    47.069] (II) NOUVEAU(0): Modeline "XMIR mode of death"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    47.069] (II) NOUVEAU(0): Output XMIR-1 connected
[    47.069] (II) NOUVEAU(0): Output XMIR-1 using initial mode XMIR mode of death
[    47.069] (**) NOUVEAU(0):  Driver mode "XMIR mode of death": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
[    47.069] (II) NOUVEAU(0): Modeline "XMIR mode of death"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)

```
grep -i LoadModule /var/log/Xorg.0.log
```

>     46.979] (II) LoadModule: "glx"
[    46.997] (II) LoadModule: "xmir"
[    47.053] (II) LoadModule: "nvidia"
[    47.065] (II) UnloadModule: "nvidia"
[    47.065] (II) LoadModule: "nouveau"
[    47.065] (II) LoadModule: "vesa"


That is only a partial list. We need to see LoadModule; "xmir." If we install and tick Install Third Party Software, then we will get a proprietary video driver and xmir will not load. We need to use an open source video driver (Nouveau). Discussions are under way with the owners of proprietary video drivers to make their drivers compatible with MIR. So, we have to wait and see.

The main point is that the user does not experience a worse user experience under MIR.

Regards.

---

