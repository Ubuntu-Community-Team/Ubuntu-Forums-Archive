---
title: "problem - Running Mir natively"
date: 2015-02-28
forum: Ubuntu Development Version
---

### Post by stef-baly on 2015-02-28
With a daily 15.04, i'm trying to configure and launch mir.
Following the different steps [http://unity.ubuntu.com/mir/using_mir_on_pc.html](http://unity.ubuntu.com/mir/using_mir_on_pc.html)
sudo mir_demo_server OK
sudo chmod a+rw /tmp/mir_socket OK
some-mir-client -m /tmp/mir_socket "some-mir-client command" not found !

Any solution ?

Thank U

Stef

---

### Post by grahammechanical on 2015-02-28
> [COLOR=#000000][FONT=Ubuntu]If you are running Ubuntu 14.04 or later, instead install ubuntu-desktop-mir. These packages will install dependencies you need and will create a file in /etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf.[/FONT][/COLOR]

Please confirm that you have installed ubuntu-desktop-mir. Synaptic Package Manager tells me that it is still in the Vivid repositories. We never know. Things have moved on since that wiki page was written. It seems that xmir will be needed to run applications like Libreoffice on Mir.

Regards.

---

### Post by stef-baly on 2015-02-28
[COLOR=#000000][FONT=Ubuntu]ubuntu-desktop-mir : OK

ps aux | grep unity-system-compositor
root      1268  1.0  0.6 741492 26376 tty7     Ssl+ 17:10   0:02 /usr/sbin/unity-system-compositor --disable-inactivity-policy=true --on-fatal-error-abort --file /run/mir_socket --from-dm-fd 10 --to-dm-fd 13 --vt 7
stef      2720  0.0  0.0   9512  2064 pts/10   S+   17:13   0:00 grep --color=auto unity-system-compositor

grep -i xmir /var/log/Xorg.0.log
[    37.470] (II) LoadModule: "xmir"
[    37.503] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[    37.522] (II) Module xmir: vendor="X.Org Foundation"

ls -l /var/log/lightdm/unity-system-compositor.log
-rw------- 1 root root 1993 févr. 28 17:10 /var/log/lightdm/unity-system-compositor.log

and there's no 10-unity-system-compositor.conf file in /etc/lightdm/lightdm.conf.d/ folder !


[/FONT][/COLOR]

---

### Post by grahammechanical on 2015-02-28
It is a long while since I experimented with xmir. I proved that I could get all the Ubuntu flavours running on xmir except Ubuntu Gnome and that was because Gnome Display Manager (GDM) was hard coded to load on xserver. Whereas, lightDM had been modified to allow a switch to xmir.

Things moved on quickly and I stopped using that wiki page to install xmir. Instead I went from this blog

[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

The PPA is available for Vivid.

[https://launchpad.net/~mir-team/+archive/ubuntu/system-compositor-testing](https://launchpad.net/~mir-team/+archive/ubuntu/system-compositor-testing)

I cannot think of anything else to offer. Sorry.

Regards.

---

### Post by Mateusz Stachowski on 2015-03-01
> **stef-baly said:**
> some-mir-client -m /tmp/mir_socket "some-mir-client command" not found !

Did you install the mir-demos package?

Also do you really tried with "some-mir-client command" or did you replaced it with one of the mir demos. For example with "mir_demo_client_egltriangle".

Also Mir doesn't work at this time on binary drivers. You should only try with opensource graphics drivers.

@[COLOR=#000000]grahammechanical the post that you linked from Oliver Ries blog is very old and it's about running XMir not Mir. Also that PPA is dicontinued and it doesn't have any packages, it is completely irrelevant by now. Especially if you use Vivid which has the latest Mir releases in it's repos.[/COLOR]

---

### Post by Mateusz Stachowski on 2015-03-01
This is how you should do it:

1. Install mir-demos. This package is in univers so you first have to enable it in Software & Updates
2. Switch to VT1 (Ctrl+Alt+F1)
3. sudo mir_proving_server (this will give you window decorations and other things)
4. Switch to VT2 (Ctrl+Alt+F2)
5. sudo chmod a+rw /tmp/mir_socket
6. mir_demo_client_egltriangle -m /tmp/mir_socket, if that didn't work run: sudo mir_demo_client_egltriangle
7. Switch to VT1 to see the egltriangle running

There are many more demos. If you type mir_demo_client_ and then double tap the Tab key (it's completion of commands) you will see all the other clients besides egltriangle.

You can also run different GNOME apps on Mir. First use this command in VT2:

```
export GDK_BACKEND=mir
```

Then run for example gedit just like the way in step 6. above:

gedit -m /tmp/mir_socket or sudo gedit

and see it running on VT1.

With mir_proving_server you can zoom in and out with Super (windows logo) + mouse wheel, move windows by holding Alt + left mose button, resize windows Alt + middle mose button, change orientation with Ctrl+Alt+ keyboard arrows.

You will find all the controls for mir_proving_server AKA Mir Demo Shell in this [file]("http://bazaar.launchpad.net/~mir-team/mir/development-branch/view/head:/doc/demo_shell_controls.md").

[Here]("https://www.youtube.com/watch?v=Qr6TznQMtxo") you can see a video of gedit running on this mir_proving_server.

---

