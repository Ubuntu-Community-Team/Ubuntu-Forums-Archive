---
title: "Flashback session fails to boot"
date: 2018-02-08
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2018-02-08
Just tried this morning in Bionic and after selecting flashback w/metacity I still boot to the Ubuntu desktop. I've tried rebooting also as I know gdm is funky.

---

### Post by kansasnoob on 2018-02-08
Must be a gdm3 thing because it works OK with lightdm and lightdm-gtk-greeter.

---

### Post by ventrical on 2018-02-10
It works very well  on the unity-session  with lightdm.

regards..

---

### Post by QIII on 2018-02-10
^^ And?  This has what to do with the original post?  In what way is this helpful?  Is Unity part of any Ubuntu development version?

---

### Post by mc4man on 2018-02-10
> **kansasnoob said:**
> Just tried this morning in Bionic and after selecting flashback w/metacity I still boot to the Ubuntu desktop. I've tried rebooting also as I know gdm is funky.
Just because a new added session is shown on the gdm greeter doesn't mean it's actually selected. If you had just switched off & then back to your added session in the dropdown you would have gotten the expected results.
When it comes to [alternative]("https://www.google.com/search?client=ubuntu&channel=fs&q=alternative+defination&ie=utf-8&oe=utf-8") sessions I've found lightdm to provide a better experience. You may or may not find that to be the case with your chosen alternative session. With some use you may be able to discern any benefits if they exist.

---

### Post by kansasnoob on 2018-02-10
> **mc4man said:**
> Just because a new added session is shown on the gdm greeter doesn't mean it's actually selected. If you had just switched off & then back to your added session in the dropdown you would have gotten the expected results.
When it comes to [alternative]("https://www.google.com/search?client=ubuntu&channel=fs&q=alternative+defination&ie=utf-8&oe=utf-8") sessions I've found lightdm to provide a better experience. You may or may not find that to be the case with your chosen alternative session. With some use you may be able to discern any benefits if they exist.

That was not the case this time. Even after repeated reboots selecting flashback w/metacity still just booted to the default DE. I haven't followed up since then to see if that's still the case. I probably need to test on a fresh install because that one has been too heavily modified to serve as a good out-of-box experiment.

---

### Post by kansasnoob on 2018-02-10
> **ventrical said:**
> It works very well  on the unity-session  with lightdm.

regards..

But not with gdm3?

It's really no big deal to use lightdm. For the unity session which lightdm greeter do you use?

---

### Post by mc4man on 2018-02-10
> **kansasnoob said:**
> But not with gdm3?

It's really no big deal to use lightdm. For the unity session which lightdm greeter do you use?

unity-greeter is a dependency of lightdm so if using lightdm one might as well use it

"Even after repeated reboots selecting flashback w/metacity still just booted to the default DE"
Just in case I wasn't being clear, I think one could reboot till the cows come home, won't change. What I was meaning was you would have to actually select another session in the greeter, then re-select flashback. 

So here when I installed flashback & rebooted at the greeter it showed flashback as being selected. However logging in produced the ubuntu session instead. Logging back out, selecting ubuntu, then selecting flashback did produce the fb session.

---

### Post by ventrical on 2018-02-11
> **QIII said:**
> ^^ And?  This has what to do with the original post?  In what way is this helpful?  Is Unity part of any Ubuntu development version?

unity-session shell is in the universe and is loaded on Bionic beaver amd64.iso using lightdm and boots just fine. You said we could discuss unity-session, not Ubuntu Development Version. so my reply is directly related to OP.

---

### Post by ventrical on 2018-02-11
> **kansasnoob said:**
> But not with gdm3?

It's really no big deal to use lightdm. For the unity session which lightdm greeter do you use?

```

sudo apt-get install lightdm

```

Thats it. If you have gdm3 installed it will ask you to choose. I remove gdm3 first then install lightdm.

unity-session is a shell in the universe.   It is like xmonad and razorqt etc.. which can be run on xorg and gnome3.

---

### Post by Claus7 on 2018-02-11
Hello,

I upgraded the other day from ubuntu 16.04 to bionic 18.04 development release. I had the ubuntu flashback (compiz) desktop environment at that time. After the update I cannot login to ubuntu flashback. In the meantime I tried the following:

1)remove lightdm
2)remove gdm3
also I checked that unity-session was already installed for my system so I let it as it is
3)install lightdm
[since my system has only one of the two(gdm3, lightdm), as *ventrical* mentions, there is not need to choose by issuing the command: sudo dpkg-reconfigure lightdm] 
4)reboot
5)select flashback and shutting down right away
when coming back to the login screen the flashback was not selected, so I selected it, tried to boot, returned back to the greeting screen (loop) and then I did shutdown (I cannot select reboot at the greeting screen)
6)then I tried to select the other options (like metacity, ubuntu, ubuntu xorg e.t.c.)
the options with the "foot" icon are not booting not even the ubuntu xorg (I have two of them one with the foot icon which does not boot and the other without the foot icon which boots and which I can use)
7)the ubuntu flashback still does not boot

I will see what I have to try next.

[EDIT: tampering with the .Xauthority file did not change anything.]

Regards!

---

### Post by Claus7 on 2018-02-17
Hello,

I will describe what I have tried thus far. There is not any success yet, yet I discovered some things which might be helpful. Just to mention that in general I can log in, yet I cannot login to ubuntu session flashback (compiz) and a couple of other sessions.

Searching the net I came across solutions about login loops (while entering username and password in the login screen, instead of logging in you are back in the login screen).
(A display manager, or login manager, is typically a graphical user interface that is displayed at the end of the boot process and presents the user with a login screen and a user can start a session when successfully enters a valid combination of username and password.)

Many suggested that someone should change the display manager. The ones I tried are:
lxdm 
lightdm
gm3

Concerning the first one I did the following:
i) while in the gnome desktop session (gnome 3, which I can successfully login from the first moment after the upgrade) I pressed the combination Ctrl+ALT+F3
ii) then I dropped in a shell where provided the command: sudo apt-get install lxdm
iii) in the middle of the installation a window appeared asking me to choose which display manager I wanted and after the end of the installation I typed: sudo reboot
iv) system rebooted and I did not have any graphics in the login screen, so I tried all combinations of Ctrl+ALT+FX, where X=1 till 7,
and at the last combination I came across the lxdm display manager.

I followed similar procedures with the other display managers, yet with the others I was invoking the shell while being at the login screen. No luck with any of them. Just to mention that with the other display managers I did not have to try the Ctrl+ALT+F7 combination. The manager, every time I rebooted, was displayed normally.

I have many sessions in my login screen including (using the lightdm):

[table="width: 500, class: grid"]
[tr]
	[td]session type[/td]
	[td]icon[/td]
	[td]login successful[/td]
[/tr]
[tr]
	[td]Cairo-Dock (gnome)[/td]
	[td]no[/td]
	[td]only mouse displayed[/td]
[/tr]
[tr]
	[td]GNOME[/td]
	[td]yes[/td]
	[td]no (after the loop it becomes the 5th session)[/td]
[/tr]
[tr]
	[td]GNOME Flashback (Compiz)[/td]
	[td]yes[/td]
	[td]no[/td]
[/tr]
[tr]
	[td]GNOME Flashback (Metacity)[/td]
	[td]yes[/td]
	[td]no[/td]
[/tr]
[tr]
	[td]GNOME on Xorg[/td]
	[td]yes[/td]
	[td]no[/td]
[/tr]
[tr]
	[td]GNOME on Xorg[/td]
	[td]no[/td]
	[td]yes[/td]
[/tr]
[tr]
	[td]LXDE[/td]
	[td]no[/td]
	[td]yes[/td]
[/tr]
[tr]
	[td]Openbox[/td]
	[td]no[/td]
	[td]broken[/td]
[/tr]
[tr]
	[td]Plasma K[/td]
	[td]K icon[/td]
	[td]broken[/td]
[/tr]
[tr]
	[td]Ubuntu (Default)[/td]
	[td]ubuntu icon[/td]
	[td]no[/td]
[/tr]
[tr]
	[td]Ubuntu on Wayland[/td]
	[td]no[/td]
	[td]yes[/td]
[/tr]
[/table]

Just to add that the difference between lightdm and lxdm is that when logging in to the ubuntu on Wayland, with the latter the windows have the buttons minimize, maximize, close, something that is missing with lightdm.

Taking into consideration that gedit has trouble displaying properly choosing different environments I suppose that is a problem due to the alpha version of ubuntu.

[EDIT: using Oibaf's ppa ([https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)) for the graphics drivers, now I can no longer login to the ubuntu wayland session that I was able to login before]

Regards!

---

### Post by jbicha on 2018-02-19
> **kansasnoob said:**
> Just tried this morning in Bionic and after selecting flashback w/metacity I still boot to the Ubuntu desktop. I've tried rebooting also as I know gdm is funky.

Are you using any relevant PPAs?

Do you have -proposed enabled? (Please don't enable -proposed updates during the development cycle because it can cause these kinds of bugs.)

---

### Post by kansasnoob on 2018-02-20
> **mc4man said:**
> unity-greeter is a dependency of lightdm so if using lightdm one might as well use it

"Even after repeated reboots selecting flashback w/metacity still just booted to the default DE"
Just in case I wasn't being clear, I think one could reboot till the cows come home, won't change. What I was meaning was you would have to actually select another session in the greeter, then re-select flashback. 

So here when I installed flashback & rebooted at the greeter it showed flashback as being selected. However logging in produced the ubuntu session instead. Logging back out, selecting ubuntu, then selecting flashback did produce the fb session.

It pulls in packages I'd just as soon not install:

```
lance@conroe-desktop:~$ sudo apt-get install lightdm -s
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libfcitx-config4 libunity-settings-daemon1 unity-greeter
  unity-settings-daemon
Suggested packages:
  fcitx bindfs lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure remote-login-service
Recommended packages:
  systemd-services
The following NEW packages will be installed:
  libfcitx-config4 libunity-settings-daemon1 lightdm unity-greeter
  unity-settings-daemon
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.

```

But using lightdm-gtk-greeter is no cleaner:

```
lance@conroe-desktop:~$ sudo apt-get install lightdm-gtk-greeter lightdm -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  gnome-icon-theme gnome-icon-theme-symbolic gnome-themes-standard
  gnome-themes-standard-data gtk2-engines-pixbuf
Suggested packages:
  bindfs desktop-base
The following NEW packages will be installed:
  gnome-icon-theme gnome-icon-theme-symbolic gnome-themes-standard
  gnome-themes-standard-data gtk2-engines-pixbuf lightdm lightdm-gtk-greeter
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by kansasnoob on 2018-02-20
Flashback w/metacity boots OK with lightdm using unity-greeter. I had to find out :)

I did a fresh install with the 20180220 iso, installed gnome-panel, rebooted, and selected flashback w/metacity from the gdm3 menu but the default Ubuntu desktop still loaded. This was a fresh install  - the only thing I did was install, update, and turn the screenlock off. So I can be 99.9% sure that this is a gdm3 issue.

---

### Post by kansasnoob on 2018-02-20
> **jbicha said:**
> Are you using any relevant PPAs?

Do you have -proposed enabled? (Please don't enable -proposed updates during the development cycle because it can cause these kinds of bugs.)

Not using any PPA's or proposed updates but that install had been monkeyed with quite a bit so I repeated today with a fresh install and gdm3 loads the default Ubuntu desktop when flashback w/metacity is selected. It works OK with lightdm. In this case I did NOT select auto-login during installation so I've been doing full reboots to change sessions. I'll need to file a bug report soon.

---

### Post by jbicha on 2018-02-21
Your #16 post sounds like [LP: #1749481]("https://launchpad.net/bugs/1749481")

Try this workaround. In the session chooser, select Ubuntu (or something else), then select GNOME Flashback.

---

### Post by cruzer001 on 2018-02-21
I installed 18.04 yesterday and flashback just now.  I chose FB at login and currently in a FB session.  And have not did anything to my DM.

```
apt policy gdm3
gdm3:
  Installed: 3.26.2.1-2ubuntu2
  Candidate: 3.26.2.1-2ubuntu2
  Version table:
 *** 3.26.2.1-2ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status


apt policy gnome-session-flashback
gnome-session-flashback:
  Installed: 1:3.26.0-1ubuntu1
  Candidate: 1:3.26.0-1ubuntu1
  Version table:
 *** 1:3.26.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
        100 /var/lib/dpkg/status


inxi -S
System:    Host: u18 Kernel: 4.13.0-32-generic x86_64 bits: 64
           Desktop: Gnome 3.26.2
           Distro: Ubuntu Bionic Beaver (development branch)

##inxi is not part of the default install???
```

---

### Post by Claus7 on 2018-02-25
Hello,

@*kansasnoob*: I tried many different combinations of sessions and greeters to no avail. No matter what, the ubuntu flashback session was in a constant loop. So from here:
[https://ubuntuforums.org/showthread.php?t=2374885&page=3&p=13735979#post13735979](https://ubuntuforums.org/showthread.php?t=2374885&page=3&p=13735979#post13735979)

I did exactly as proposed:
```
sudo apt remove upstart --purge
```

and rebooted and problem solved! Flashback is booting as normal, using gdm3 display manager.

@*cruzer001*:thank you for your post. I had exactly the same output typing your commands. 

Maybe unnecessary, yet during the process I purged a lot of packages like plasma, openbox, installed and purged vanilla ubuntu. Up to now the (most serious) problem I'm facing is with gedit as a non-root user (every time I use it, I see the background of my screen inside the application), which I think that it will get fixed soon, since we are still in an alpha version. 
[EDIT: open gedit->select options (3 horizontal lines)->Preferences->Fonts & Colors->Color Scheme->3rd option for compact gedit!]
[EDIT2: rm ~/.xinputrc and reboot, this fixed problem in the number area of calculator and the 1st classic color scheme of gedit]

Regards!

---

### Post by cruzer001 on 2018-02-25
Upstart was replaced with systemd long ago; maybe its time for a fresh install.

---

### Post by kansasnoob on 2018-02-27
It seems that this is fixed with the latest version of gdm3 so I'm marking it solved.

---

### Post by kansasnoob on 2018-02-27
I spoke too soon. It's NOT fixed! Testing for this bug requires a fresh install!

---

