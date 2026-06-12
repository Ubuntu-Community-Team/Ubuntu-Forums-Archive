---
title: "WSL 2 Ubuntu - Running GUI Programs from an Existing Ubuntu Installation"
date: 2021-11-13
forum: Virtualisation
---

### Post by UbuntuWho on 2021-11-13
Hello, long time no see! I'm here about Windows Subsystem for Linux, this time.

I've updated my Windows machine to Windows 11, and I've installed WSL 2 and the Ubuntu app. Then, I installed my old Ubuntu drive from my laptop and managed to "plug it in" to WSL via Powershell. Then, I mounted it under WSL Ubuntu to the path */mnt/UbuntuDrive* and chrooted into it as root. After a bit of fiddling, I now have managed to give it internet access using the same hostname settings as WSL Ubuntu, but now I have run into a problem.

Whenever I try to run a GUI app on my Ubuntu drive, say Nautilus or Firefox, they refuse to open, and most programs print the error:
```
Cannot open display:
```

I am able to run GUI apps from the WSL Ubuntu installation using VcXserv, but I can't seem to run the same type programs from my Ubuntu drive this way. I'm pretty sure it can be done, but I just need to know what I'm missing here. Any help would be appreciated. Many thanks!

---

### Post by MAFoElffen on 2021-11-13
LOL. This article from MS only cam out 3 days ago as experimental for Win11.
[https://docs.microsoft.com/en-us/windows/wsl/tutorials/gui-apps](https://docs.microsoft.com/en-us/windows/wsl/tutorials/gui-apps)

I thought this worked with hacks for Win10 already(?)

---

### Post by UbuntuWho on 2021-11-13
Yes, but I already know how to run GUI apps from WSL Ubuntu. What I want is to run GUI apps from *an existing Ubuntu installation, one that is bootable from the BIOS and on an ext4 partition.* I have such a drive mounted to the WSL Ubuntu, and I can chroot into it, but it refuses to run GUI apps due to the error above.

---

### Post by sudodus on 2021-11-13
Maybe it helps with [**xhost**](https://askubuntu.com/questions/961967/why-dont-gksu-gksudo-or-launching-a-graphical-application-with-sudo-work-with-w/961978#961978) and/or to set the **DISPLAY** variable?

---

### Post by MAFoElffen on 2021-11-13
Or a combination "Plus"?

For running an Ubuntu Desktop from WSL2 in Win10, in ~/.bashrc I have to add these two lines 
```

export DISPLAY=$(awk '/nameserver / {print $2; exit}' /etc/resolv.conf 2>/dev/null):0
export LIBGL_ALWAYS_INDIRECT=1

```
And add an inbound rule in my firewall to open up port 6000 to xserver in WSL2.

I then use VcXScr to connect/display it and use "Turn Off Access Control" (in Extra Options) to enable public access to the XServer in WSL.

It is slow, has other problems, and the video still tears. I'm not happy with running Ubuntu under WSL. It can be done, but is not a great solution. Faster and better performance and graphics is running it as a VM or as dual boot and be running it native. 

Even the WSL2 terminal session (all by itself) is very noticeably slow... I don't want to accuse anything like that is an "on purpose" kind of thing, but...

I know, you just want to run app's... which an option in VcXScr is for that also, from WSL.

---

### Post by UbuntuWho on 2021-11-13
> **MAFoElffen said:**
> Or a combination "Plus"?

For running an Ubuntu Desktop from WSL2 in Win10, in ~/.bashrc I have to add these two lines 
```

export DISPLAY=$(awk '/nameserver / {print $2; exit}' /etc/resolv.conf 2>/dev/null):0
export LIBGL_ALWAYS_INDIRECT=1

```
And add an inbound rule in my firewall to open up port 6000 to xserver in WSL2.

I then use VcXScr to connect/display it and use "Turn Off Access Control" (in Extra Options) to enable public access to the XServer in WSL.

It is slow, has other problems, and the video still tears. I'm not happy with running Ubuntu under WSL. It can be done, but is not a great solution. Faster and better performance and graphics is running it as a VM or as dual boot and be running it native. 

Even the WSL2 terminal session (all by itself) is very noticeably slow... I don't want to accuse anything like that is an "on purpose" kind of thing, but...

I know, you just want to run app's... which an option in VcXScr is for that also, from WSL.
That would be great, except I've found out that I'm running WSL Preview, which replaces the need for VcXserv. That works well for WSL Ubuntu, but not Ubuntu on my ext4 partition.

I found out how you can run the desktop interface of WSL via RDP: [https://dev.to/darksmile92/linux-on-windows-wsl-with-desktop-environment-via-rdp-522g](https://dev.to/darksmile92/linux-on-windows-wsl-with-desktop-environment-via-rdp-522g) It *almost* worked running the Ubuntu drive, chrooted into WSL Ubuntu, but sudo gives me the error:
```
sudo: no tty present and no askpass program specified
```
...And it doesn't matter what user I select or what password, it hangs after trying to logon. I don't know if I have XRDP set up wrong?

Desktop or no desktop, I just want to be able to launch my Ubuntu apps on my Ubuntu drive!

---

### Post by UbuntuWho on 2021-11-14
All right, so I've removed the WSL Preview app from the Windows Store, made sure that the WSL feature built into Windows 11 was still active and fully updated (had to remount my Ubuntu drive to WSL Ubuntu again), and made sure I was still using WSL 2. GUI apps still won't work from my Ubuntu drive, and running XRDP from there still seems broken, as I am still not able to log in (i.e. the aforementioned problems still exist). I still think something is set up wrong somewhere - maybe the X server for the Ubuntu drive is not configured properly, components missing, or simply not compatible with WSL.

I've tried the options X.org, VNC, and Neutrino; none of these options seem to work. They either produce a "some error" error message, or the login prompt disappears with no desktop or GUI interface showing. Sooo... now what?

---

### Post by sudodus on 2021-11-14
Did you try with xhost and DISPLAY?

---

### Post by UbuntuWho on 2021-11-14
> **sudodus said:**
> Did you try with xhost and DISPLAY?
Not exactly sure how to do that under WSL. It tells me that the display doesn't exist, basically.

---

### Post by sudodus on 2021-11-15
- In my WSL [FONT=Courier New]**xhosts**[/FONT] exists and it works according to [this link](https://askubuntu.com/questions/961967/why-dont-gksu-gksudo-or-launching-a-graphical-application-with-sudo-work-with-w/961978#961978).

- In my WSL I can run

```

$ echo $DISPLAY
:0

```

and it returns a relevant value.

Using [FONT=Courier New]**xhosts**[/FONT] and setting the DISPLAY variable makes it possible for me to run GUI applications with elevated permissions. (I have nothing to chroot into, so I cannot check that.)

[hr][/hr]
Edit: I can even start GUI applications via putty in Windows 11, for example

```

$ DISPLAY=:0 gnome-terminal

```

will start a terminal window that can be used to start [other] GUI applications.

---

### Post by UbuntuWho on 2021-11-15
> **sudodus said:**
> - In my WSL [FONT=Courier New]**xhosts**[/FONT] exists and it works according to [this link](https://askubuntu.com/questions/961967/why-dont-gksu-gksudo-or-launching-a-graphical-application-with-sudo-work-with-w/961978#961978).

- In my WSL I can run

```

$ echo $DISPLAY
:0

```

and it returns a relevant value.

Using [FONT=Courier New]**xhosts**[/FONT] and setting the DISPLAY variable makes it possible for me to run GUI applications with elevated permissions. (I have nothing to chroot into, so I cannot check that.)

[hr][/hr]
Edit: I can even start GUI applications via putty in Windows 11, for example

```

$ DISPLAY=:0 gnome-terminal

```

will start a terminal window that can be used to start [other] GUI applications.

Thank you very much! I will keep this in mind.

I have managed to solve most of my display problems. I wanted to use MATE desktop environment, but no corresponding window manager loads. GNOME doesn't even start on my Ubuntu drive, even though it exists. So, I am now using XFCE 4. There are still some kinks to be ironed out, but I have almost reached my goal.

Thank you all so ever for tips! This thread will be updated if I have further problems with GUI apps from my Ubuntu drive running through WSL Ubuntu.

---

### Post by UbuntuWho on 2021-11-16
All right, so more problems with my setup:

* I've managed to get XFCE to run and with a desktop, but many windows appear transparent. I'm thinking this is an issue with GTK not initializing properly.
* Several programs that are still installed *and* used to work when I could boot to my Ubuntu drive on my laptop now do not work anymore; either exiting with a "No such file or directory" error or not opening at all.
* The Ubuntu drive *has* internet, but for some reason it isn't able to connect through XRDP.
* I still can't open a terminal, as I get the "can't connect to PTY - no such file or directory" error.
* I am not able to open a package manager and install packages, but that's mainly for the reasons stated above.

Every non-GUI command I type into my Ubuntu drive connected to, and running through, WSL Ubuntu works. These problems are frustrating, and I'm having to do many workarounds. Further help would be appreciated.

Keep in mind: I am running a desktop interface of Ubuntu installed on a bare metal drive through XRDP, which I executed via WSL Ubuntu when I attached the drive to it. I am pleased that I now have a desktop, but these other problems interfere with what I want to use it for.

---

### Post by MAFoElffen on 2021-11-16
You probably already know this... But the port for XRDP is 3389... which would need to be open on the guest and host... Right?

---

### Post by UbuntuWho on 2021-11-16
> **MAFoElffen said:**
> You probably already know this... But the port for XRDP is 3389... which would need to be open on the guest and host... Right?

I don't think that really relates to my problem? I can connect to XRDP just fine; it's the apps running through it that don't work.

---

### Post by MAFoElffen on 2021-11-17
Let's back up a bit... The errors and such are like you are missing a piece somewhere.

You have Windows 11 with WSL2 right? Just becasue you have a mount shouldn't matter with the graphics display...It needsto render the OpenGL of, because WSL2 says it supports both X11 and Wayland.

Do you have one of the 3 required Windows 11 WSL NVidia, Intel or AMD GPU drivers installed to support Virtual GPU's (vGPU) that supports OpenGL rendering for WSL2? You only need one of the 3 that supports the type GPU you have...

---

### Post by UbuntuWho on 2021-11-17
> **MAFoElffen said:**
> Do you have one of the 3 required Windows 11 WSL NVidia, Intel or AMD GPU drivers installed to support Virtual GPU's (vGPU) that supports OpenGL rendering for WSL2? You only need one of the 3 that supports the type GPU you have...

I have an AMD Ryzen 3 2200G with Vega 8 Graphics chipset. I have enabled SVM support in my BIOS. I am using the same username under WSL Ubuntu as I have in my Ubuntu drive. The drive is using port 3390 and WSL Ubuntu is using 3395. I start XRDP under both, then connect to WSL Ubuntu with Windows remote desktop and type in the credentials for the user account registered under the Ubuntu drive. For some reason, it works, and I am able to load a desktop, but apps don't seem to function right.

Yes, something is missing; I know that much, but what? Is there something else I left out?

---

### Post by MAFoElffen on 2021-11-17
I don't know... I also use the Windows Store App "GWSL"... which is based on VcXScr... And that is also how that is connecting and displaying Xserver from the WSL Ubuntu instance. GWSL, as an app, automates the details of the Display connection details of XServer to/through WSL. I can confirm that it does not work as easy as it is advertised, but it does work. There were some applications start details that I had to do manually to connect to already installed applications. 

It confirms nt it's own app menu's that it connects through the windows firewall to a specific screen (0)... And all my Ubuntu app's seem to work and display correctly on it, on the Windows Desktop.

I don't think it's the app's itself. I'm sure if I was mounting another drive from within Ubuntu on WSL and chrooted into it like you, that it would react and display the same... to the apps that were installed in that chroot. 

I'm with you and others, that it seems to be either the connection to the specific screen in XServer in WSL and what you are rendering it from... Or the specific route that it needs to make that connection... Saying that and rereading what I typed, it seems like I am saying the same thing, but I am meaning the connection between or the rendering of what is being transported between.

Logically, that makes sense to me, and this intrigues me why your's is not working... It is certainly good test case to try to get working.

---

### Post by UbuntuWho on 2022-04-07
Hey, all! Just had to unplug my Ubuntu drive the other day due to hardware readjustments - I think my motherboard was complaining about too much power being used, because it kept beeping whenever I turned it on until I unplugged the drive. I was using a MOLEX to SATA adapter; maybe go native SATA next time?

Anyway, I haven't worked on my issue lately, but any further ideas on the matter would be appreciated. Just posting this as a status update, really.

---

