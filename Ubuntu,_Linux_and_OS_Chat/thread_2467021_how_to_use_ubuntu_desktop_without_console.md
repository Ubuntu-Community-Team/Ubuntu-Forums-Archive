---
title: "how to use ubuntu desktop without console?"
date: 2021-09-13
forum: Ubuntu, Linux and OS Chat
---

### Post by danielfoo on 2021-09-13
how to use ubuntu desktop without terminal?

In the process of using ubuntu desktop, apart from professional technology, what functions in your daily life make you have to use the terminal? Please reply and record it, I think this is the direction of system improvement.

---

### Post by danielfoo on 2021-09-13
When I plug in the headset, I have to use the command line to turn on the headset interface and disable the speaker.

---

### Post by Frogs Hair on 2021-09-13
Linux,Mac, and Windows all include a terminal/command line as part of the UI and using it is really a matter of choice. It is great resource for gathering information about the underlying system that supports the GUI. The command line is also a great tool for trouble shooting, and quickly resolving problems without digging though the UI to find particular applications. Sample of my terminal history.

    ```
modprobe efivarfs
  201  ls /sys/firmware/efi
  202  sudo mokutil --sb-state&#8203;
  203  mokutil --sb-state
  204  ls /sys/firmware/efi
  205  echo $XDG_SESSION_TYPE
  206  dpkg --get-selections | grep nvidia
  207  lspci | grep VGA
  208  nvidia-settings
  209  ubuntu-drivers devices
  210  df -h
  211  mokutil --sb-state
  212  sudo apt update && sudo apt upgrade
  213  glances
  214  man glances

```

Moved to Ubuntu Linux and OS Chat , not a support request.

---

### Post by TheFu on 2021-09-13
> **danielfoo said:**
> When I plug in the headset, I have to use the command line to turn on the headset interface and disable the speaker.

Appears that pulse audio isn't setup correctly. By default, any newly connected audio device, either a source or a sink, should become active at connection time.  We can override this behavior in the client.conf file or by using the **pavucontrol** GUI program.

IMHO, people avoiding the shell are only using 20% of the power of their systems.
Plus, in these text-based forums, providing steps that can be copied/pasted and still work vastly shortens the question-to-answer time. Having to post 20 images for a solution highlighting which button on each screen to be pressed is a hassle.

Don't fear the shell.

---

### Post by kevdog on 2021-09-13
idk --- 90% of my ubuntu desktop are ubuntu-server installed without a window manager or desktop.  Control is via ssh/tmux.  Maybe I should ask the question -- How to use Ubuntu with a GUI?

---

### Post by TheFu on 2021-09-14
> **kevdog said:**
> Maybe I should ask the question -- How to use Ubuntu with a GUI?

Testify!

On my "desktop" now, there are 14 "windows" in the window list. The non-terminals are:
FF, Thunderbird, KeePassXC, Handbrake, alarm-clock-applet and gnubiff. All the others are terminal windows into this and other systems.  That's on this workspace.  I use 3 workspaces.  1 workspace is empty. The 2nd has a terminal and a different browser.  

My setup doesn't have a menu.  I tend to launch programs from a terminal. This means both CLI and GUI programs can be easily run - no limits, no hidden name, no hidden output, using program options that I've customized.

Rather than point to a menu, look for an group, click, look for the name that someone else decided to call a program, click and get stuck using whatever the defaults are, when I want to run a program, if I use it all the time, there will be some options I want to have that aren't the defaults. For example, to launch thunderbird, here's the script:
```
more ~/bin/thunderbird.sh 
#!/bin/bash
FJ_OPTS="--dns=172.22.22.80 --rlimit-as=3500000000"
TB_OPTS="-no-remote "

# limit RAM VSS to 4G
PID=$(ssh -X  regulus /usr/bin/firejail $FJ_OPTS /usr/bin/thunderbird $TB_OPTS $@ & )
exit;

``` 

This creates a GUI channel to a different system to run thunderbird, inside a firejail sandbox, forces a specific DNS server (ad and "bad guy" blocking), limits the amount of RAM the program can see/grab and runs it.  It prevents a locally run TB from being used when I specifically want to run it on that other system as well.  The defaults just can't touch that flexibility.

Of course, most Ubuntu end-users don't know that this stuff is possible.

I don't use firejail confinement very often, but for high-risk programs, I'm happy to have it available.  My firefox setup is very similar. It is extremely high-risk, IMHO.  But I don't go crazy, so a calculator or video editor don't need any confinement.  I do run the password manager on regulus too, through an ssh GUI connection - no confinement/jail needed. Regulus is a 20.04 system and has a newer version of the password manager than most other systems here. In general, programs that have internet connections get confined inside a firejail.  Programs that don't, don't.

BTW, regulus is a virtual machine.  Nearly the only way I use it is over an ssh connection.

---

### Post by monkeybrain20122 on 2021-09-14
> **danielfoo said:**
> When I plug in the headset, I have to use the command line to turn on the headset interface and disable the speaker.

There is something wrong with your audio set up. You shouldn't need to do that.

---

### Post by mastablasta on 2021-09-15
> **monkeybrain20122 said:**
> There is something wrong with your audio set up. You shouldn't need to do that.

my old motherboard did that. it left the output on speakers. new one turn it off and switches to headset. so drivers are the issue here.

as for the OP. 
in daily life i do not use terminal. but then again i mostly just browse internet or play games (Steam or PoL). On occasion i am doing something in Libre office, pasting together video clips or watching photos.

i use terminal to talk to home server. and to troubleshoot. like during this weekend i used at my kids PC to try to resolve bad steam update. in the end it didn't help at all, and i eventually resolved it via Steam GUI.

---

### Post by zebra2 on 2021-09-15
Don't fool yourself about Windows. It has a vast registry, cmd line and programming built-in.  The millions of end users don't need those things at all.  I agree with you that Ubuntu needs robust point and click problem solving to be mainstream.  What I am using right now with Impish and Gnome 4.2 has greatly improved its "settings" section but doesn't come close to what we had with the Unity Compiz Config. With the point and click compiz config one could brick an OS pretty fast. During that period I actually felt safer at the terminal.  Today, because I only use current development versions life always resorts to the terminal.  An operating system is no different than your car, there is an engine and drive train under that sheet metal. Own one long enough and you may have to get dirty.  Linux has a reputation for being a down and dirty OS. Put your coveralls on and get to it.

---

### Post by monkeybrain20122 on 2021-09-15
> **zebra2 said:**
> Don't fool yourself about Windows. It has a vast registry, cmd line and programming built-in.  The millions of end users don't need those things at all.  I agree with you that Ubuntu needs robust point and click problem solving to be mainstream.  What I am using right now with Impish and Gnome 4.2 has greatly improved its "settings" section but doesn't come close to what we had with the Unity Compiz Config. With the point and click compiz config one could brick an OS pretty fast. During that period I actually felt safer at the terminal.  Today, because I only use current development versions life always resorts to the terminal.  An operating system is no different than your car, there is an engine and drive train under that sheet metal. Own one long enough and you may have to get dirty.  Linux has a reputation for being a down and dirty OS. Put your coveralls on and get to it.

I am still using unity on 20.04 and 21.04. I don't see how you could brick your system with compiz config, worst you just reset compiz, and how do you change compiz settings with the terminal??

---

### Post by zebra2 on 2021-09-15
I did the same thing back then that I did last week when kernel 16 blew up.  I did my super fast reinstall. I always use a dev version and I always keep an updated installer handy.

On the other hand, its been a long time since 11.04 or later when I used a Unity desktop but looking back I guess I could have just clicked the reset link but looking back I admit I didn't know it existed. Must be a Unity 20.04 thing.  I'm on Gnome 40 so just don't know.

---

### Post by sblip on 2021-09-24
Hello, and I am telling you this in the kindest way possible, you CANNOT use ubuntu without the terminal, no matter what, sometime you will just need to open the terminal to either download software or fix something.

---

### Post by TheFu on 2021-09-24
> **sblip said:**
> Hello, and I am telling you this in the kindest way possible, you CANNOT use ubuntu without the terminal, no matter what, sometime you will just need to open the terminal to either download software or fix something.

This is not true.  My mother never opened a terminal in her life and she used Lubuntu for years.

About once a year, she'd ask me to do something for her and because I lived 3 states away, I'd ssh in and do it (7 hrs driving) .  She didn't know what a terminal was and was happy pointing and clicking.  Of course, I advised her on what hardware to buy that "just worked", so she didn't have to hunt down drivers - ever.  Also, I setup weekly patching and back-in-time backups for her that never screwed up.  If something bad happened, she knew exactly how to get an old backup copy of a file or directory.  I pulled backups once a week for her. That was so her most important stuff was off-site and safe from natural disasters.

Lots of users don't ever touch a terminal.

---

### Post by QIII on 2021-09-24
> **sblip said:**
> Hello, and I am telling you this in the kindest way possible, you CANNOT use ubuntu without the terminal, no matter what, sometime you will just need to open the terminal to either download software or fix something.

Nonsense!  FUD.

You "need" to use the terminal about as often as a Windows user does.  There are operations that are done in the cmd window in Windows, but they are usually rather esoteric things or special operations power users might want.

Edit:  The reason that the CLI is so often used here and on many other sites is that it is the *lingua franca* of Linux.  DEs are all different and there are different GUI elements for getting things done.  It does not matter what desktop environment is being used.  The CLI works across the board and other users do not need to know the intricacies of all of them to help.

---

### Post by zebra2 on 2021-10-08
My wife has never used a Linux or Windows terminal.  That doesn't mean one hasn't been used. If the access is performed by another person for the system to function then I think the general idea that the terminal access is necessary is still valid. Some users are task oriented, very good at what they do but if something breaks someone else is going to have to open the terminal.

---

