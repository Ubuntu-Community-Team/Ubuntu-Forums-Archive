---
title: "Installing/Testing Mir on Vivid"
date: 2014-10-24
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-10-24
It appears that mir is not installed by default. (I thought the packages would be).

```

xserver-xorg-mir
ubuntu-desktop-mir
unity-system-compositor

```


Here goes..

---

### Post by ventrical on 2014-10-24
After install and hard shutdown/restart I have all the 'mir' reports in terminal.

```

ventrical@ventrical-Satellite-A105:~$ ps aux | grep unity-system-compositor 
root      1318  0.4  1.7 812688 35292 tty7     Ssl+ 12:59   0:02 /usr/sbin/unity-system-compositor --disable-inactivity-policy=true --on-fatal-error-abort --file /run/mir_socket --from-dm-fd 10 --to-dm-fd 13 --vt 7
ventric+  3294  0.0  0.1  13680  2160 pts/6    S+   13:07   0:00 grep --color=auto unity-system-compositor
ventrical@ventrical-Satellite-A105:~$ grep -i xmir /var/log/Xorg.0.log 
[     4.836] (II) LoadModule: "xmir"
[     4.836] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[     4.841] (II) Module xmir: vendor="X.Org Foundation"
ventrical@ventrical-Satellite-A105:~$ ls -l /var/log/lightdm/unity-system-compositor.log 
-rw------- 1 root root 260 Oct 24 12:59 /var/log/lightdm/unity-system-compositor.log
ventrical@ventrical-Satellite-A105:~$ 

```

---

### Post by rrnbtter on 2014-10-24
Greetings,
I have been running xmir in Utopic through most of the cycle and it carried over into the Vivid conversion.

rrnbtter@Toshiba-Satellite-L305:~$ grep -i xmir /var/log/Xorg.0.log 
[    31.372] (II) LoadModule: "xmir"
[    31.373] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[    31.414] (II) Module xmir: vendor="X.Org Foundation"
rrnbtter@Toshiba-Satellite-L305:~$ ls -l /var/log/lightdm/unity-system-compositor.log 
-rw------- 1 root root 326 Oct 24 07:45 /var/log/lightdm/unity-system-compositor.log
I have not had any problems with this even with the various kernels I've tested nor with Systemd.
FYI

---

### Post by ventrical on 2014-10-24
Thanks.

I was talking of a fresh install from .iso.

Regards..

---

### Post by rrnbtter on 2014-10-24
Greetings,

> **ventrical said:**
> Thanks.

I was talking of a fresh install from .iso.

Regards..

I think I getting too old to keep up in these forums.  I didn't even know a Vivid installer was available yet. I presumed a upgrade of Utopic. Sorry for the error.

---

### Post by ventrical on 2014-10-24
> **rrnbtter said:**
> Greetings,



I think I getting too old to keep up in these forums.  I didn't even know a Vivid installer was available yet. I presumed a upgrade of Utopic. Sorry for the error.

:)

No ,no ...  I fresh installed of Utopic (no mir by default) then convert to /vivid, then add mir and run lunity from there. :)

Regards..

---

### Post by rrnbtter on 2014-10-24
Greetings,

> **ventrical said:**
> :)

No ,no ...  I fresh installed of Utopic (no mir by default) then convert to /vivid, then add mir and run lunity from there. :)

Regards..

Actually I was just pulling your leg a bit there ventrical.  I don't know if you are getting all of the updates that I am but I just downloaded a new systemd-shim. Looks like the game is on.  I am eager to see if systemd, mir, and other processes that are hanging around will default on the new ISO. Can't really go with what has been reported in the past with Canonical and with desktop-next running parallel to Vivid anything can happen on a whim.

---

### Post by ventrical on 2014-10-24
> **rrnbtter said:**
> Greetings,



Actually I was just pulling your leg a bit there ventrical.  I don't know if you are getting all of the updates that I am but I just downloaded a new systemd-shim. Looks like the game is on.  I am eager to see if systemd, mir, and other processes that are hanging around will default on the new ISO. Can't really go with what has been reported in the past with Canonical and with desktop-next running parallel to Vivid anything can happen on a whim.

ehehehe  .. hey .. we're having fun.:) It's going to be interesting for sure.

Regards..

---

### Post by xc3RnbFO8P on 2014-10-28
Do I have Mir that I can use?:
> ringi@ringi-Lenovo-Ideapad-Flex-15:~$ ps ax | grep "unity"
 1374 tty7     Ssl+   0:04 /usr/sbin/unity-system-compositor --disable-inactivity-policy=true --on-fatal-error-abort --file /run/mir_socket --from-dm-fd 9 --to-dm-fd 13 --vt 7
 2219 ?        Ssl    0:00 /usr/lib/unity-settings-daemon/unity-settings-daemon
 2233 ?        Ssl    0:03 /usr/lib/unity/unity-panel-service
 2435 ?        Sl     0:00 /usr/lib/unity-settings-daemon/unity-fallback-mount-helper
 3151 ?        Sl     0:00 /usr/lib/x86_64-linux-gnu/unity-scope-home/unity-scope-home
 3161 ?        Sl     0:00 /usr/bin/unity-scope-loader applications/applications.scope applications/scopes.scope commands.scope
 3163 ?        Sl     0:00 /usr/lib/x86_64-linux-gnu/unity-lens-files/unity-files-daemon
 3625 pts/7    S+     0:00 grep --color=auto unity
ringi@ringi-Lenovo-Ideapad-Flex-15:~$ 

---

### Post by grahammechanical on 2014-10-28
> [COLOR=#000000]Do I have Mir that I can use?:[/COLOR]

I would say that you have Unity. Try

```
ps aux | grep unity-system-compositor
```

Although, I found that Unity System Compositor gets left behind if we install and then remove unity8-desktop-session-mir. I have just checked a Vivid install of daily image (20141027) and unity-system-compositor is not installed by default.

I have just checked  a Vivid Ubuntu Desktop Next install by going into tty2 after logging into the phone UI and unity-system-compositor is installed and running

```
ps aux | grep mir
```

comes up with /run/lightdm-mir. So, we have progressed from Xmir to lightdm-mir. It makes sense. One day we will get mir-mir or will that be mir-eol and purr purr? :)

For your information. 

Regards

---

### Post by xc3RnbFO8P on 2014-10-28
Thanks Graham,
I got this:
> ringi@ringi-Lenovo-Ideapad-Flex-15:~$ ps aux | grep unity-system-compositor
root      1374  0.5  1.0 820508 40456 tty7     Ssl+ 14:35   0:26 /usr/sbin/unity-system-compositor --disable-inactivity-policy=true --on-fatal-error-abort --file /run/mir_socket --from-dm-fd 9 --to-dm-fd 13 --vt 7
ringi     5554  0.0  0.0  11064  2088 pts/7    S+   15:59   0:00 grep --color=auto unity-system-compositor

ringi@ringi-Lenovo-Ideapad-Flex-15:~$ ps aux | grep mir
root      1374  0.5  1.0 820508 40572 tty7     Ssl+ 14:35   0:27 /usr/sbin/unity-system-compositor --disable-inactivity-policy=true --on-fatal-error-abort --file /run/mir_socket --from-dm-fd 9 --to-dm-fd 13 --vt 7
root      1672  1.9  2.2 481504 84164 ?        Sl   14:35   1:40 /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -mir x-0 -mirSocket /run/mir_socket -nolisten tcp



> ringi@ringi-Lenovo-Ideapad-Flex-15:~$ ps aux | grep unity-system-compositorroot      1700  0.8  0.9 820504 37172 tty7     Ssl+ 18:28   0:16 /usr/sbin/unity-system-compositor --disable-inactivity-policy=true --on-fatal-error-abort --file /run/mir_socket --from-dm-fd 10 --to-dm-fd 13 --vt 7
ringi     5209  0.0  0.0  11064  2180 pts/8    S+   19:01   0:00 grep --color=auto unity-system-compositor
ringi     5689  0.0  0.0  11064  2180 pts/8    S+   19:13   0:00 grep --color=auto mir

ringi@ringi-Lenovo-Ideapad-Flex-15:~$ grep -i xmir /var/log/Xorg.0.log
[    15.031] (II) LoadModule: "xmir"
[    15.032] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[    15.035] (II) Module xmir: vendor="X.Org Foundation"

ringi@ringi-Lenovo-Ideapad-Flex-15:~$ ls -l /var/log/lightdm/unity-system-compositor.log
-rw------- 1 root root 367 Oct 28 18:59 /var/log/lightdm/unity-system-compositor.log

---

### Post by ventrical on 2014-10-28
> **grahammechanical said:**
> I would say that you have Unity. Try

```
ps aux | grep unity-system-compositor
```

Although, I found that Unity System Compositor gets left behind if we install and then remove unity8-desktop-session-mir. I have just checked a Vivid install of daily image (20141027) and unity-system-compositor is not installed by default.

I have just checked  a Vivid Ubuntu Desktop Next install by going into tty2 after logging into the phone UI and unity-system-compositor is installed and running

```
ps aux | grep mir
```

comes up with /run/lightdm-mir. So, we have progressed from Xmir to lightdm-mir. It makes sense. One day we will get mir-mir or will that be mir-eol and purr purr? :)

For your information. 

Regards


What I am expecting from mir is that we will be able to slip-stream desktop experiences either from the VTs or from a GUI shim (or be able to run two desktops concurrently)!! Now , VTs can be run concurrently , say . two terminals .. one with htop and one with midnight commander. Very cool. Now , imagine with lightdm-mir we can bump , lets say. gnome-session or gnome-shell or mate with Unity3D or ubuntu-next .. and back again without  having to log off - log on. That would be a real feat.  I think it can be done. Perhaps it can already be done. I'm looking.   It would make mir an 'all that a compositor should be'  kind of hallmark for ubuntu.   Ubuntu-next  will then have it's place . but perhaps not on the desktop as much.

Currently VMs  only emulate the appearance that  two DE's or OSes can run concurrently but   they are actually WAITed when switching from one OS to another so it is not a true parallel process. All that resource  gone to waste.

Regards..

---

### Post by grahammechanical on 2014-10-28
I tried on Desktop Next running setsid unity and I got back "failed to execute unity: no such file or directory." We know the Terminal is not installing and there is supposed to be a File Manager but I cannot find it in the App store. Those are the only two apps that are "unconfined". That is they can access data in other apps. All the other apps in the app store are confined. This means that the music app cannot access the contacts list in the contacts app, for example.

I can see you idea working and it might work they way you think - on different VTs. If MIr is running from the first loading of Linux and other DE+Ui are configured to run on Mir. And why should that not be possible? Then Yes. It could happen.

I tried Linux years and years ago. And I remember that it was possible to run one application in one console and another application in another console. It makes me wonder what happens when we select another session from the login screen. Does the session run on tty7 or maybe another tty? Is this switching of VTs already happening?

To my mind there might be another way. In Unity 8 apps run on "surfaces." An alternative desktop could be made to run on a surface running on Unity 8. But what do I know about anything. I am talking out of the top of my head. Ignore me.

Regards.

---

### Post by ventrical on 2014-10-29
@ grahammechanical. I think you nailed it!  I remember and olde DOS program (using MSDOS 5.0) It was shareware (Association of Sharware Professionals) and I was also at the time experimenting with Linus's first boot-disk floppy (which didn't boot ) :).

  The DOS program took advantage of the 80386 DX processors capabilities to multitask (circa 1992) It gave me three real-time terminals (Windows) One , I could have a game running , 2nd I could have the word-processor going and third I could have the DOS command line and I could switch between them by using an Alt+(n) macro with out flushing any buffers .. etc..  so we are on the same line of thinking except I think  except  I cannnot help thinking that 2 kernels can be running at the same time on Mir , concurrently = so there is actually no down time.

Regards..

edit:

 I recall at times it  was called 'split terminal' but this had a WAIT state I believe.

---

### Post by grahammechanical on 2014-10-29
What put this into my mind was you discovering that Desktop Next is running on tty8 and not tty7. And that is true. With Desktop Next I go into tty2 and run update/upgrade and then switch to the OS on tty8. By the way, I have one Desktop Next install running on the devel repositories. Those repositories are now open as far as I can see.

In time we shall need a whole different set of sudo commands. For example, startx won't work on Mir, will it?

Regards.

---

### Post by ventrical on 2014-10-29
> **grahammechanical said:**
> What put this into my mind was you discovering that Desktop Next is running on tty8 and not tty7. And that is true. With Desktop Next I go into tty2 and run update/upgrade and then switch to the OS on tty8. By the way, I have one Desktop Next install running on the devel repositories. Those repositories are now open as far as I can see.

In time we shall need a whole different set of sudo commands. For example, startx won't work on Mir, will it?

Regards.

As far as I recall in the past few days , startx is no longer downloaded by default , at least not on Ubuntu- Next. I'm back at it now ... checking this out.

Edit:

If you are using your Ubuntu Desktop-Next , no, startx  or (xinit)is not installed by default. To install it you have to:

```

sudo apt-get install xinit

```

 I'm willing to bust my install just to see what happens.

 I'll get back.

Regards..

---

### Post by ventrical on 2014-10-29
My system did not bust but, now , after update/upgrade, unity8 is deprecated with no network connection or at least the browser will not work (I do not think it is related to  installing <xinit> but I was able to open the notepad in ubity8 desktop next and mc in tty1 and was able to switch back and forth between tty1 and tty8 with no interruption in editing on unity8 slate not midnight commander.

 So ...this was the case before I installed xinit.

That leads to the question ... what terminal server was midnight commander and htop running on. Xmir or xorg? (Couldn't find the processes/service xorg/xmir/unity-system-compositor running in htop so beats me).




Regards..

---

### Post by grahammechanical on 2014-10-29
I have had some success in my experiments. I have managed to install the original touch core apps that we messed around with months ago. I post my report in the Desktop Next thread

[http://ubuntuforums.org/showthread.php?t=2248940&page=3](http://ubuntuforums.org/showthread.php?t=2248940&page=3)

I wonder what going to tty6 and running lightdm start will do?

Regards.

---

### Post by ventrical on 2014-11-01
Anybody have any idea what this 'pay-service' is.

Ubuntu-Desktop Next

---

### Post by ventrical on 2014-11-01
> **grahammechanical said:**
> I have had some success in my experiments. I have managed to install the original touch core apps that we messed around with months ago. I post my report in the Desktop Next thread

[http://ubuntuforums.org/showthread.php?t=2248940&page=3](http://ubuntuforums.org/showthread.php?t=2248940&page=3)

I wonder what going to tty6 and running lightdm start will do?

Regards.

  I tired running this  (also in a script) and it will either restart the unity-greeter login or just hang and you will need a Ctrl+z in CLI to get out.

Regards..

---

### Post by grahammechanical on 2014-11-01
It is to do with the Software Centre or perhaps the apps store in Ubuntu Desktop Next

[https://launchpad.net/ubuntu/utopic/+source/pay-service](https://launchpad.net/ubuntu/utopic/+source/pay-service)

My idea about Lightdm failed for me. I also tried "setsid unity" and got back "failed to execute unity. No such fiile or directory." I then tried "setsid unity8 " that was a bit better. I got back "could not detect display." and that is the full limit of my knowledge of commands relating to Unity. I tried searching for some other commands. Not success.

Regards

---

