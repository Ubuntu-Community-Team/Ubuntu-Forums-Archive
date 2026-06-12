---
title: "Cinelerra not working on Hardy"
date: 2008-04-27
forum: Ubuntu Studio
---

### Post by casagan on 2008-04-27
Hello all.

It is only for asking if there is some problem with cinelerra in Hardy. I have just upgraded to Hardy Heron, and reinstalled cinelera following instructions from [http://cinelerra.org/getting_cinelerra.php#hardy](http://cinelerra.org/getting_cinelerra.php#hardy). The problem comes when I open the program , open some project, and the interface is not responding (more precisely, the timeline scrubbing). I hope is there some solution, I would like to finish some projects at home. Thanks in advance.

Casagan.

---

### Post by aokneufi on 2008-04-27
try    

sudo aptitude install  kdenlive

---

### Post by eldragon on 2008-04-27
i would sugest to reinstall cinelerra from the comunity version repository here: [http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php)

cheers

---

### Post by johnapeterson on 2008-04-27
I am having pretty much the same problem.  Cinelerra will open, I get the tip of the day, but If I go to the program window, none of the drop-down menus will open, ad I have to kill the program thru the system monitor.

Any suggestions?
John

---

### Post by Bartje on 2008-04-28
I've got the same problem here. Cinelerra hangs when using certain other buttons too, when you keep the tip of the day open. I've read something about a bug, [http://bugs.cinelerra.org/show_bug.cgi?id=383]("http://bugs.cinelerra.org/show_bug.cgi?id=383").

Luckily I've got 7.10 on my other harddrive, I'll work on that one for now, until a real fix is ready.

---

### Post by KoenW on 2008-04-28
Have this problem for more then a week now ;-) There were some answers given at the maintainers website (search on akirad): sudo chmod user:user ~/.bcast, disabling compiz and 'sudo cinelerra'. The first two did not work for me. However i could start en use cinelerra with 'sudo cinelerra'. 

Of course I want to work with cinelerra as a normal user (I have more Gig's free in /home than in /root). The next workaround I found on the mailinglist of cinelerra: it seems to be that there's an issue with GDM. 
This is what I did: 
Log out of gnome
go to virtual terminal via CTRL ALT F2
login 
sudo /etc/init.d/gdm stop
sudo startx
if startx doesn't work: install xfce4 and do 'sudo startxfce4'
open a terminal in the new session
cinelerra

Et voila: it works likes a charm as an normal user. 

Can someone try this out to see if it works? 

Kind regards, 

Koen W.

---

### Post by johnapeterson on 2008-04-28
"Sudo cinelerra" is working for me.  Hope they have the bug fixed sometime.

Thanks,
John

---

### Post by cotcot on 2008-04-28
Compile cinelerra yourself. It is not difficult.
I use it in 64 and 32 bit.

---

### Post by KoenW on 2008-04-29
A fresh compilation did not solve the problem for me. 
Found yet another solution: login via ssh on your own computer.
 
You first have to install openssh-server. 
Open a terminal in Gnome
Login on your own pc: ssh -X your-username@localhost
provide your password
cinelerra

This seems to be an old bug: [http://bugs.cinelerra.org/show_bug.cgi?id=383](http://bugs.cinelerra.org/show_bug.cgi?id=383) 
Does anyone know how to compile without XCB? 

Koen

---

### Post by casagan on 2008-04-29
Thanks for this workarounds. But I would wait for a real fix. In the meantime I will try to finish my personal projects in Kino. 

Regards,
Casagan.

---

### Post by pfluegl on 2008-04-29
The above mentioned (stopping GDM, starting xfce4) works for me.
Also sudo works for me.

---

### Post by Dragonchase on 2008-05-08
Hello all,

I have Cinelerra installed in the Ubuntustudio 8.04 that recently came out.

I took Cinelerra from Akirad.  It appears to function except for audio. The Cinelerra sites advise setting audio to esound and port 7007.  The Cinelerra "meters" do nothing nor does Pulse. If I select OSS or ALSA in Cinelerra, the meters work fine but still no audio from either of my sound cards. It appears Cinelerra is trying to work but the audio is not getting handed off. I'm using an amd 32 bit, Nvidia set-up.

Kino works fine but I'm used to Premier. I am hoping to get Openmovieeditor working with the 2008 version. It has node editing which the older version in Ubuntustudio does not.

Anyway I need Premier (c) like features.

Any ideas from you are most appreciated!

---

### Post by Camille Harang on 2008-05-29
It seems that the problem comes from XCB linked with Xlib. The best way to make Cinelerra working under Hardy is to recompile it without XCB support (but it will disable Compiz effects). You can download and install my packages from [http://garbure.org/~mammique/soft/xlib-hardy-noxcb/](http://garbure.org/~mammique/soft/xlib-hardy-noxcb/) if you trust it and use i386 machine.

If not you can rebuild the package as follows:

```
apt-get source libx11-6

sudo apt-get install build-essential fakeroot xtrans-dev x11proto-core-dev x11proto-kb-dev x11proto-input-dev x11proto-xext-dev x11proto-xf86bigfont-dev libxcb1-dev libxcb-xlib0-dev x11proto-xcmisc-dev x11proto-bigreqs-dev
```

cd the xlib directory, edit debian/rules and add **--without-xcb** after **../configure**

```

rm debian/libx11-xcb1.install
rm debian/libx11-xcb-dev.install

sudo dpkg -i ../libx11-6_1.1.3-1ubuntu2_YOURARCH.deb ../libx11-data_1.1.3-1ubuntu2_all.deb
```

---

### Post by monkotronic on 2008-05-30
i solved the  problem of no mouse response by turning off my fancy 3d desktop functions in the appearance program and then using the system monitor to quit compiz from running in the background.  everything works now.  so it appears the problem is an incompatibility issue with compiz.

---

### Post by ubundah001g on 2008-05-31
There are a few posts that I made about the same problems on this post. I was able to run Cinelerra in User Mode on Ubunutu Studio 8.04 using the Non-Real Time kernel. If you install the Generic linux kernel, and then select that as the kernel that you want to use during boot, and verify it at the command line by typing "uname -a", then you should be able to run Cinelerra in User Mode without having the problems of not being able to select any of the menu widgets.

Does anyone know why the RT kernel does not work in User Mode with Cinelerra in 8.04?

---

### Post by Jovaro on 2008-06-12
I am not sure if this will help anyone, but it seems to have helped for me.

I was having the same issue as johnapeterson, cinelerra becoming unresponsive after starting it. I tried to run it from a terminal to check for any error messages and instead of giving errors, it just worked fine.

After this I can start cinelerra from the menus as well and it will work just fine.

---

### Post by johnapeterson on 2008-06-14
Got mine going.
Apparently, Cinelerra needs to run thru PulseAudio to run correctly in 8.04.  To get PulseAudio working correctly follow 

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

And then changes the preferences for Cinelerra from this site:
[http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

---

### Post by mateuszbaranski on 2008-06-26
I found the solution. At least on my configuration:
ubuntu (studio) 8.04 on 32-bit intel, 
nvidia GeForce4 Ti 4200 AGP 8x graphic card 

I worked on cinelerra without problems on ubuntu studio 7.10. From the past experience I know that it is better to finish the movie project BEFORE upgrading the system. 
As expected after upgrade to hardy (8.10) I found the same problems as noted before by others  (no response to any clicks with the mouse).

I checked different kernel versions (I prefer real-time kernels):
on 2.6.24-18-rt kernel (which was installed by the upgrade) cinelerra doesn't work.
BUT
in June there was an upgrade of kernel to:
2.6.24-19-rt kernel on which cinelerra WORKS in user mode ! 
But what is strange after update of kernel to 19 the defaul kernel in grub is still 18 (!) so I had to manually choose "19" during startup.

Futher problems - even when running the "19" kernel nvidia restricted modules didn't work (see the /etc/X11/Xorg.log)- I couldn't start in graphic mode. 
The solution: run the system in "18" kernel and REINSTALL the 
linux-restricted-modules-2.6.24-19-rt
Run again using "19" kernel" and graphic mode works fine and  Cinerella too.

Hope it helps somebody.

---

### Post by dariosicily on 2008-08-06
> **KoenW said:**
> Have this problem for more then a week now ;-) There were some answers given at the maintainers website (search on akirad): sudo chmod user:user ~/.bcast, disabling compiz and 'sudo cinelerra'. The first two did not work for me. However i could start en use cinelerra with 'sudo cinelerra'. 

Of course I want to work with cinelerra as a normal user (I have more Gig's free in /home than in /root). The next workaround I found on the mailinglist of cinelerra: it seems to be that there's an issue with GDM. 
This is what I did: 
Log out of gnome
go to virtual terminal via CTRL ALT F2
login 
sudo /etc/init.d/gdm stop
sudo startx
if startx doesn't work: install xfce4 and do 'sudo startxfce4'
open a terminal in the new session
cinelerra

Et voila: it works likes a charm as an normal user. 

Can someone try this out to see if it works? 

Kind regards, 

Koen W.

Hey Koen,
just want to say a big THANKS !!!
This approach solved my unbearable troubles with Cinelerra ! I'm using xfce4 now and apparently I have no crashes / bugs now !
I was really about to switch to Winzoz as for my video editing....

Thanks !

---

### Post by henkm on 2008-08-14
There is a new version of cinelerra 4, with special ubuntu builds.

[http://www.heroinewarrior.com/cinelerra.php3#download]("http://www.heroinewarrior.com/cinelerra.php3#download")

These seems to work better

---

### Post by deflagmator on 2008-08-19
I'm using ubuntu hardy and I used this solution:

[https://bugs.launchpad.net/ubuntu/+source/libxcb/+bug/185311/comments/159]("https://bugs.launchpad.net/ubuntu/+source/libxcb/+bug/185311/comments/159")

This solves for me all the problems, and I can use Compiz.
****

:)

---

