---
title: "Headless TeamViewer on Ubuntu 19.10"
date: 2019-11-21
forum: Server Platforms
---

### Post by aravindvnair99 on 2019-11-21
Hey folks!


I have been attempting to connect to my home server running Ubuntu 19.10 over TeamViewer from my other devices (Linux computers, Android phones or Windows computers) in vain. I have tried fiddling with Xorg configurations, installing and uninstalling various things.


To summarise:



[LIST]
[*]Unable to connect to the server without a monitor connected. It does connect, but I end up on a black screen.
[*]When I installed 'xserver-xorg-video-dummy' package and tried setting Xorg configurations in 'etc' and 'usr' in their respective paths, I could no longer log in to Ubuntu by entering by username and password via TeamViewer on the Ubuntu login screen until I got rid of it via ssh. Also, when I installed the package, my mouse and keyboard stopped working. Only through TeamViewer, it was accessible. Installing the package also disabled my monitor.
[*]The same issue persists when I am using with the monitor and I disconnect the monitor while TeamViewer is running.
[/LIST]

What I am looking to do:

[LIST]
[*]Have a headless Ubuntu 19.10 server accessible over TeamViewer.
[*]Should be able to use when monitor is also connected.
[*]All hardware should be accessible.
[/LIST]

Any help or suggestion would be welcome, even the ones I have already tried in case I did it wrong. Please suggest. Thanks for reading! :)

EDIT:

I have solved it and put up my answer here: [https://ubuntuforums.org/showthread.php?t=2431781&page=2&p=13932126#post13932126](https://ubuntuforums.org/showthread.php?t=2431781&page=2&p=13932126#post13932126)

---

### Post by howefield on 2019-11-21
Thread moved to the "*Server Platforms*" forum.

---

### Post by aravindvnair99 on 2019-11-21
> **howefield said:**
> Thread moved to the "*Server Platforms*" forum.

Hey @howefield

Apologies for the confusion, I actually am on Ubuntu 19.10 Desktop and not the Server edition although I use my system as a home server.

---

### Post by uRock on 2019-11-21
This is the best place for it, since you're trying to use it as a headless server.

---

### Post by aravindvnair99 on 2019-11-21
> **uRock said:**
> This is the best place for it, since you're trying to use it as a headless server.

Hey @uRock

Thanks for the clarification. Will keep in mind. Not sure, if this is the right place to ask (I'm new to this forum), but could you please tell me how to tag or mention a user? Am I doing it right because I don't see any hyperlink or suggestions when using the "@".

---

### Post by LHammonds on 2019-11-22
I'm confused when seeing "headless" and "teamviewer" in the same sentence.  Isn't TeamViewer a GUI (graphical user interface) to access a desktop GUI?  If so, headless isn't the right word.

If you are trying to access the "headless" server (no GUI), the normal procedure is using text terminal software such as PuTTY or Telnet.

With Linux, you can open a terminal and SSH into the server.
With Windows, you can use PuTTY and SSH into the server.
With Android, you can use Termius and SSH into the server (but I do not have any Android devices).

LHammonds

---

### Post by aravindvnair99 on 2019-11-22
> **LHammonds said:**
> I'm confused when seeing "headless" and "teamviewer" in the same sentence.  Isn't TeamViewer a GUI (graphical user interface) to access a desktop GUI?  If so, headless isn't the right word.

If you are trying to access the "headless" server (no GUI), the normal procedure is using text terminal software such as PuTTY or Telnet.

With Linux, you can open a terminal and SSH into the server.
With Windows, you can use PuTTY and SSH into the server.
With Android, you can use Termius and SSH into the server (but I do not have any Android devices).

LHammonds

Hey @LHammonds

Thanks for replying. Yes, you're right. I probably wasn't clear enough. So I have three situations:

[LIST]
[*]One is where I have a monitor connected and I am using the system which works perfectly.
[*]The second is when I have no monitor connected and I SSH into the server. And yes, I use terminal from Linux, Termux on Android and Git Bash on Windows which all work fine.
[*]The third is when I have no monitor connected and I want to use TeamViewer to connect which is where I'm facing the difficulty. When I install the 'xserver-xorg-video-dummy' package, it works as intended and as I expect it to. I can confirm the system does boot up without monitor because I can SSH into it. But TeamViewer doesn't capture it as there is nothing to mirror in graphics output. I am trying to get 'xserver-xorg-video-dummy' to work properly now. Or any alternatives to that so that there's a virtual monitor for TeamViewer to capture. That package works fine, just that I am unable to login. When I try to log in, it accepts the password and then puts me back to the lock screen.
[/LIST]

Apologies for not being clear. Any ideas or suggestions?

I did get the GUI to show up on TeamViewer by following [https://askubuntu.com/a/1087551/707371](https://askubuntu.com/a/1087551/707371). But I am unable to login by typing my username and password. Once I type in, it tries to login and then I guess it logs out and puts me back on the lock screen. SSH works perfectly fine when I try to log in. Any suggestions?

---

### Post by LHammonds on 2019-11-23
So, when you say "have a monitor connected and I am using the system which works perfectly." you are saying that you have some kind of GUI desktop environment such as GNOME, KDE, Mate, etc.?

I only ever use SSH or the text-based terminal that is standard with the server when I interface with it.  So I don't know enough about a GUI system on the server beyond using "dialog" to create pretty text menus.  My experience is limited to headless servers.

Sorry.  I hope someone can help you that uses a GUI add-on but this certainly is not considered a headless server.  I'm not doggin' on that...to each their own.

LHammonds

---

### Post by aravindvnair99 on 2019-11-23
> **LHammonds said:**
> So, when you say "have a monitor connected and I am using the system which works perfectly." you are saying that you have some kind of GUI desktop environment such as GNOME, KDE, Mate, etc.?

I only ever use SSH or the text-based terminal that is standard with the server when I interface with it.  So I don't know enough about a GUI system on the server beyond using "dialog" to create pretty text menus.  My experience is limited to headless servers.

Sorry.  I hope someone can help you that uses a GUI add-on but this certainly is not considered a headless server.  I'm not doggin' on that...to each their own.

LHammonds

Hey @LHammonds

Yes, I do have GNOME installed. Having a monitor is just one of the use cases. I usually SSH into the server. But there are times when I need to use the GUI. So that's why I have GNOME and TeamViewer installed just in case when the need arises. No issues, thanks for responding! Appreciate your time! :)

---

### Post by LHammonds on 2019-11-23
> **aravindvnair99 said:**
> Having a monitor is just one of the use cases.Well, a monitor does not demand a GUI. It can display the CLI just as well.

> **aravindvnair99 said:**
> there are times when I need to use the GUI.Just curious, but what do you need the GUI for?

---

### Post by aravindvnair99 on 2019-11-25
I figured out how to get it working. I changed my GRUB config. I shall post the answer once I'm done testing in a few days.

> **LHammonds said:**
> Well, a monitor does not demand a GUI. It can display the CLI just as well.

True. I agree. I have both GUI and CLI use cases.

> **LHammonds said:**
> Just curious, but what do you need the GUI for?

To test few GUI applications I make, run VMs and couple of other GUI only applications I use.

---

### Post by TheFu on 2019-11-25
Another option?  I have zero idea if this works on 19.10.  Way, way, too new for me.

I use x2go, which isn't tied into any GPU.  Local or remote access are separate, so the x2go desktop is separate from the X11 session if you happen to be logged in.  Some programs, mostly web browsers will only allow 1 instance running per username by default. There are ways to override that for most or just run each in a private firejail container.

My main desktop runs inside a virtual machine and the VM host doesn't have GUI libraries loaded.  x2go works fine, but it doesn't like heavy GUIs like Gnome3.  There are plenty of other DE/WM options which work fine. openbox, fvwm, Mate, and other gnome2-based DEs should all work fine.

One liability of x2go is that it uses ssh tunnels, part of the NX protocol, so external ssh connectivity is required. Also, an x2go client must be loaded on the clients. Many NX tools have slightly different interfaces which make them incompatible.

Don't know if x2go is useful for your needs.

---

### Post by aravindvnair99 on 2020-02-14
Here's what I did and it's been perfectly working for me:


Step 1: Open Terminal and paste ```
sudo nano /etc/default/grub
```
Step 2: Update the line ```
GRUB_CMDLINE_LINUX_DEFAULT
``` to include ```
nomodeset
```.
Step 3: ```
sudo update-grub && sudo reboot
```

At this point, TeamViewer should be able to load, and you should be able to log in. But the resolution is bad and the graphics aren't good either.

Step 4: Open Terminal and paste ```
sudo apt install xserver-xorg-video-dummy -y
```

Step 5: Make a script called ```
monitor.sh
``` with contents as ```
sudo rm /usr/share/X11/xorg.conf.d/xorg.conf
``` and ```
nomonitor.sh
``` with contents as ```
sudo cp xorg.conf /usr/share/X11/xorg.conf.d/
```. This can be kept in home folder for easier accessibility.


Step 6: The contents of ```
xorg.conf
``` are as follows:


```
Section "Device"
    Identifier  "Configured Video Device"
    Driver      "dummy"
EndSection


Section "Monitor"
    Identifier  "Configured Monitor"
    HorizSync 31.5-48.5
    VertRefresh 50-70
EndSection


Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    DefaultDepth 24
    SubSection "Display"
    Depth 24
    Modes "1366x768"
    EndSubSection
EndSection

```

Step 7: Now all that's required is to run one of those scripts according to the situation (monitor connected or disconnected) and TeamViewer, VNC, AnyDesk, etc will start working fine with any resolution.

> **TheFu said:**
> Another option?  I have zero idea if this works on 19.10.  Way, way, too new for me.

I use x2go, which isn't tied into any GPU.  Local or remote access are separate, so the x2go desktop is separate from the X11 session if you happen to be logged in.  Some programs, mostly web browsers will only allow 1 instance running per username by default. There are ways to override that for most or just run each in a private firejail container.

My main desktop runs inside a virtual machine and the VM host doesn't have GUI libraries loaded.  x2go works fine, but it doesn't like heavy GUIs like Gnome3.  There are plenty of other DE/WM options which work fine. openbox, fvwm, Mate, and other gnome2-based DEs should all work fine.

One liability of x2go is that it uses ssh tunnels, part of the NX protocol, so external ssh connectivity is required. Also, an x2go client must be loaded on the clients. Many NX tools have slightly different interfaces which make them incompatible.

Don't know if x2go is useful for your needs.

@TheFu Thanks for the suggestion. I'll have a look at this as well. Right now, I have got it working perfectly fine. Just needed some additional configuration.

@howefield @uRock This thread can be closed.

---

