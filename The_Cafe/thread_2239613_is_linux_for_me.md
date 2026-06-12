---
title: "is linux for me?"
date: 2014-08-14
forum: The Cafe
---

### Post by Rainelogan on 2014-08-14
i installed ubuntu when i found my xp 32bit can't make use of the extra 4 gig of ram i just installed.  since installing ubuntu i've realised even if my winxp os could make use of the extra ram it wouldn't because i don't do anything on my comp that requires it.  so that was an expensive lesson and waste of money buying the extra ram. 

being completely new to linux i had to do a lot of googling for info and in the process got quite sold on the testimonials i came across with common keywords such as, "free", "virus-free", "freedom", "bloat-free".  who can resist all that "*free*" stuff right?

after installing ubuntu alongside my winxp, and spending hours lost in the alien landscape i found my way here to the *beginners forum*.  that's where i got really disheartened.  for supposed n00bs the language in even the beginners forum suggests i'm in way over my head.  all i got from there and the few posts i could decipher was a second realisation that it's a complete miracle i was able to install linux at all with no problems.  :shock:

so my problems are thus:

i feel completely lost using ubuntu - i don't know where anything is.  i hate the layout of the desktop. i don't know how to use the terminal in any useful way.  my attempt to install the iron browser failed.  the chrome browser i did get installed has fonts i couldn't figure out how to change much or live with.  i could go on but you get the picture.  bottom line is i'm use to knowing my way around my comp and being able to fix issues etc so it's hard for me to be this lost with a new OS.  

when i rethink the selling points of linux i have to consider virus's, spyware etc aren't an issue for me with windows. costs are minimal - i've only upgraded computers when necessary and never been bothered changing from an xp os.  

so i really need to know if there is any point in me persisting with linux?  if so let me know. 

if not - is there a way i can keep the linux os but get my comp to automatically load windows without having to select it at boot?

---

### Post by VE6EFR on 2014-08-14
I felt the same way when I first started using Ubuntu. But I stayed with it and little by little I became more at home with the o/s. Now if I boot into Windows it feels awkward and very uncomfortable. Don't give up on Ubuntu and give yourself time to adjust. It will happen.

---

### Post by MrSteve on 2014-08-14
if you are having problems with the ubuntu desktop which is similar to mac OSX try kubuntu which has a similar desktop to windows
that should make you feel more at home the rest will come with usage ...

---

### Post by PondPuppy on 2014-08-14
When I installed Ubuntu I did it back-to-back with a Windows 7 install. For my money the Ubuntu install was faster and easier, and it had all the drivers I needed whereas Windows 7 lacked an internet card driver. Not a big deal, though. I don't think it's miraculous that you installed without problems. Modern graphical installers make it pretty easy, really, both in Windows and in Linux.

If you hate the Ubuntu desktop, try Linux Mint. The install process is similar, just install it to the place you put Ubuntu.

For myself, I very much like having a wide choice of systems. I haven't much appreciated what I've seen of Win 8, and I'm pleased not to be dependent on whatever Microsoft chooses to do with their interfaces. Also pleased to be off the windows upgrade cycle, which appears to be tightening up. But that's just me.

---

### Post by Rainelogan on 2014-08-14
hi and thanks for your replies. 

i will keep trying with ubuntu for a bit and try to figure out where to put more specific questions.  

thanks again.

---

### Post by Frogs Hair on 2014-08-14
See the Ubuntu guide in my signature and look through the stickies in the New to Ubuntu sub forum. I forgot to mention typing help into Unity dash .

---

### Post by JetStorm on 2014-08-14
Lubuntu might be a better choice if you're accustomed to the XP interface.
As with most other ubuntu-based distros, you can try it without installing and decide whether you like it or not.

---

### Post by user1397 on 2014-08-14
> **Rainelogan said:**
> so my problems are thus:

i feel completely lost using ubuntu - i don't know where anything is.  i hate the layout of the desktop. one thing is not knowing where anything is, that's expected.  you can pretty much google any question about ubuntu, there are so many resources and info written about it that it's gonna be hard to come up with something that hasn't been asked before.  as far as "hating" the layout of the desktop, seems a bit harsh to have a stance like that from the get-go.  It's not meant to look the same as windows or anything else; it is its own interface, and it might be a little different from what you're used to, but take comfort in knowing that millions of people use this interface and like it very much.  Others don't, and what's good about linux is that your choices aren't limited to windows or unity desktop (the default desktop for ubuntu).  There's kubuntu, xubuntu, lubuntu, and not to mention a thousand other "distributions" of linux that each have their own sets of defaults and configurations.  

> i don't know how to use the terminal in any useful way.  my attempt to install the iron browser failed.  the chrome browser i did get installed has fonts i couldn't figure out how to change much or live with.  i could go on but you get the picture.  bottom line is i'm use to knowing my way around my comp and being able to fix issues etc so it's hard for me to be this lost with a new OS.   you don't need to know your way around the terminal to get started with ubuntu.  sure some guides ask you to type in some terminal commands, but thats usually a straight forward copy & paste, and a lot of guides use terminal commands because it is a lot easier to say "here, type this and voila" instead of going "okay, now right click on this button, then go down to where it says menu so and so, and then click on this item" and show a bunch of pictures.  as far as for any specific problems you're having, there's these forums, as well as askubuntu.com and the wiki and most importantly google.  and sure, you may feel lost at first, but that's part of the excitement :)

> when i rethink the selling points of linux i have to consider virus's, spyware etc aren't an issue for me with windows. costs are minimal - i've only upgraded computers when necessary and never been bothered changing from an xp os.  

so i really need to know if there is any point in me persisting with linux?  if so let me know.only you can answer that question.  the only way of finding out it trying it out. it might not be for you, or it might be.  no one's forcing you to change, so if you don't like it or want to stick with your old way of doing things, there's no one stopping you. 

> if not - is there a way i can keep the linux os but get my comp to automatically load windows without having to select it at boot?yes, there is.  basically, open up the terminal by pressing the windows key on your keyboard, then typing "terminal" and hit enter.  

in the terminal, you want to type ```
sudo gedit /etc/default/grub
```In the text file that pops up, edit the line that says GRUB_DEFAULT=0 and change it to the value where your windows entry is (usually going to be 3 or 4 but you might have to reboot the computer and when you see the screen where you can select ubuntu or windows, count how many entries down the windows entry is.  It always starts with 0, so the first entry is number 0, second entry is number 1, third entry is number 2 etc)

So for example, change it to GRUB_DEFAULT=3, then save and close the text editor.

Now back in the terminal, type ```
sudo update-grub
``` and when that's done reboot and see if you go automatically to windows.

Hope that helps.

---

### Post by slooksterpsv on 2014-08-14
There's lot of information, and yes there are some sections of the forums which are glorified with commands and information that even I don't understand, but I try to learn it.

Here's some things to help you get started:
Ubuntu uses what's called Unity, the bar on the left is the Unity bar, and clicking on the icon at the top brings up dash (dashboard/hud) where you can open your applications. There's an icon that looks like the letter A with a pencil or something like that, that's where you can find your applications. You then click on Installed and it will show you a list of installed programs - not very intuitive if you ask me. So you can browse and use any apps there or use Software Center to locate any additional software you need.

Key Terms:
Distrobution - simplistically a distrobution is a version of Linux that others can derive from. Ubuntu uses a lot of Debian configuration and usage, Ubuntu is a distrobution (distro for short). Ubuntu has variants of it as well such as Kubuntu, Lubuntu, Ubuntu Gnome, Xubuntu, Edubuntu, UbuntuKylin, and more. They are also known as distros
Terminal - a command line interface (CLI) like a dos prompt
Desktop Environment - A desktop environment is a group of applications that generally use from the same programming base. XFCE is a Desktop Environment, it uses xfce packages (programs) and had it's own libraries to develop apps with. 
Window Manager - a way the windowing system is laid out - think Windows 3.11 vs Windows XP, those use 2 different windowing managers, well Linux has a ton. XFWM is XFCE's window manager. I think mutter is Ubuntu.
Compiz - Compiz really is a composition renderer - meaning nice graphical effects on windows, applications loading, shadows etc. you'll see this referenced a lot.

Ubuntu wasn't for me. Now here's my recommendations for my personal favorites:
elementary OS - very intuitive, you have a dock at the bottom (like mac os x) called plank, you have gala (I believe) which is the appications menu at the top left, you click on it and there's your apps - plus what's already in your dock. Its very simple, intuitive, and easy to use.

Xubuntu - Awesome XFCE distro it has 2 bars (both are configurable and moveable) one at the bottom which initially acts like a dock, but can be modified. The top one has what's called Whisker Menu - it's a start menu essentially - and the notification area in the top right - like the notification area in the bottom right on Windows XP with a default profile.

Kubuntu - Very graphically appealing distro, it's styled a lot more like Windows and has a bunch of apps built from KDE (Kubuntu uses KDE which KDE is a Desktop Environment as well as an SDK (software development kit)), its very similar to Windows and doesn't use compiz, I believe it has a KDE Window Decorator that handles its fancy effects.

It's a lot to learn, yes, but it comes quickly. If something every fails to work, and you prompt us for help, we will tell you to open terminal and type in a command. Try these out as these are basic safe commands - and yes the terminal is **case-sensitive**:

```

echo "Hello"
ls -alh
cd Downloads
ls
echo "DId you find world?" | grep world
cat /var/log/dmesg > ~/dmesg.log
cat ~/dmesg.log | grep eth0

```
the | is the SHIFT + \ key

Welcome to the Forums and I hope we can assist you in your journal on Linux =D

---

### Post by coldraven on 2014-08-15
For me the beauty of using a Linux based OS is the ease of installing it.
No more looking at Windows asking me "Have you got the driver for something?". It took hours to install XP. I also spent hours running anti-virus etc. checks. I spent more time trying to keep Windows working than actually using it!
If I suddenly decide to install a different version of Linux it will take half an hour and not ask me for any drivers at all.
If your computer is old then I would suggest Xubuntu. You can either download it and create a bootable USB stick to try it or just install the Xfce desktop to your existing installation. Then at the login screen you can choose between Unity and Xfce. 
Then if you like it you can disable the "Login at startup" and it will boot to your last choice.
See here for details:
[http://askubuntu.com/questions/223536/how-can-i-install-xfce-along-side-unity](http://askubuntu.com/questions/223536/how-can-i-install-xfce-along-side-unity)

---

### Post by Erik1984 on 2014-08-15
It depends on how much you are willing to learn and where you use your PC for. But anyway: Welcome to the Linux world :P

---

### Post by mörgæs on 2014-08-15
First of all Windows XP is out of support and hence a security risk (even worse than when it was supported). I would not use it for anything important nor store anything sensitive here.

---

### Post by kc1di on 2014-08-15
Yes the learning curve can be steep , but the pay off when you get there is a solid and great experience.  Don't give up , enjoy learning and you'll be there before you know it.  unity is quite a different paradigm from Windows xp  -- so it's normal to have a little Desktop shock, As some have mentioned you may want to give kubuntu a try - it may lesson the shock for awhile.   But with time you'll get there either way.  

The Linux foundation is offering free linux on line course that covers the basics. in small bites that may interest you you can [find out more here]("https://www.edx.org/course/linuxfoundationx/linuxfoundationx-lfs101x-introduction-1621#.U-3fSXVdWbk").

---

### Post by fkkroundabout on 2014-08-15
try a different desktop environment - a desktop environment is just how things look and where the menus and buttons are placed - one more like windows. install lubuntu-desktop from the ubuntu software centre

others are available here
[http://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available)


as for this:
> **mörgæs said:**
> First of all Windows XP is out of support and  hence a security risk (even worse than when it was supported). I would  not use it for anything important nor store anything sensitive  here.

[URL="http://news.softpedia.com/news/Windows-7-Suffers-from-Bigger-Infection-Rate-than-Windows-XP-441641.shtml"]http://news.softpedia.com/news/Windows-7-Suffers-from-Bigger-Infection-Rate-than-Windows-XP-441641.shtml
[/URL]not that i could ever go back to XP, but still

thread should be moved to: new to ubunutu

---

### Post by craig10x on 2014-08-15
If you aren't accustomed to using docks (which is what the unity launcher is) it might take a little time to get use to it but i would say give it at least 2 to 3 weeks of use before deciding to move to another type of desktop (as various posters have suggested)...I myself (after leaving windows and before discovering linux) spent about a year with an apple (Mac) computer so the transition was quite easy for me but i can understand how coming from windows it may seem a little strange...it's actually very easy to use and after a while you may really begin to like it ;)

Best way to use it, is to put favorites and frequently used apps on the unity launcher for quick 1 click access...and for less used apps, you can simply bring them up in the dash search on top...you can also shrink the size of the icons, auto hide of course, and even put the menus back in the windows (just go to appearance section of system settings)...

---

### Post by stalkingwolf on 2014-08-15
You might want to try the mint desk top environment.  You can install it from synaptic package manager.  once installed you can add an extra panel (tool bar)  and easily add
workspace changer ( multiple desk tops)  and  custom menu bar, an app that give you choices Applications  places   system instead of just a menu.  a bit easier to find things.

---

### Post by donkeyoatmeal on 2014-08-15
I love ubuntu! I was a hard core windows guy but im stuck now!! :)

---

### Post by Tar_Ni on 2014-08-15
> **Rainelogan said:**
> i feel completely lost using ubuntu - i don't know where anything is.  i hate the layout of the desktop. i don't know how to use the terminal in any useful way.  my attempt to install the iron browser failed.  the chrome browser i did get installed has fonts i couldn't figure out how to change much or live with.  i could go on but you get the picture.  bottom line is i'm use to knowing my way around my comp and being able to fix issues etc so it's hard for me to be this lost with a new OS. 

Xubuntu 14.04.1 64 bit:

[http://xubuntu.org/](http://xubuntu.org/)

or 

Lubuntu 14.04.1 64 bit

[http://lubuntu.net/](http://lubuntu.net/)

These two operating system are based on Ubuntu and supported by Canonical so you'll have acces to the forum community and all the updates and repo of Ubuntu. The difference with Ubuntu is that they are using different desktop environment XFCE (Xubuntu) and LXDE (Lubuntu). You may like them better but if you encounter any problem that you can't solve feel free to seek assistance on the appropriate sections of the forum.

I used to be lost with Ubuntu but it is a matter of time and experience to get used to it and how the OS basically ''works''. I am no expert but I find my way around much more than a year ago. There is a lot of tutorial on the web about many useful things too. In the end it's different than Windows or OS X and it is not meant to be the same.

---

### Post by linuxyogi on 2014-08-15
I always tell people that I started using Linux from Ubuntu 8.04 but actually thats not the case.

I used to buy a tech magazine which offered 2 DVDs with it. In one of those DVDs I found Kubuntu 5.04 or 5.10 I don't remember correctly.

It was a nightmare. I was using 56K dialup modem those days and I didn't manage to configure Kubuntu's network settings.

There was a PPP dialer but it didn't work. I found that by default there is no support for mp3 or any video formats other than vorbis.

So, my next goal was to install mplayer but since there was no Internet connectivity I had to boot into Windows XP download the 

mplayer deb package and reboot to Ubuntu and every time I tried to install I got a dependency warning and had to reboot to XP to 

download that. I dont remember correctly but after like 10 - 12 reboots I was able to download all the dependencies and install mplayer.



I completely understand your situation but do not give up.

---

