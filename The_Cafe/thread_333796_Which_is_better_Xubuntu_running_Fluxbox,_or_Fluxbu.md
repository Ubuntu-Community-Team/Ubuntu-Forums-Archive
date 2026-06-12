---
title: "Which is better: Xubuntu running Fluxbox, or Fluxbuntu?"
date: 2007-01-07
forum: The Cafe
---

### Post by shellhrs on 2007-01-07
I have been using Xubuntu with Fluxbox for a few months now. It's been a continuous improvement with the help of this forum. :D

However, I feel that my system (IBM Thinkpad 600e with 96MB RAM) is not running fast enough. I guess that's because I installed Xubuntu first (I didn't know about Fluxbox or Fluxbuntu until a couple of weeks ago). Running Fluxbox as my WM is definitely faster than running XFCE, but with all the add-ons, I feel the system is slowing down, so now I'm thinking about starting a clean install.

I tried Fluxbuntu LiveCD, and I think it will run well on my system. I especially need the ability to place icons on the desktop (which I have been unable to do now). :-k 

BTW, I managed to have the transparent terminal & sound running (I haven't tried playing MP3 though, Automatix failed to install the codecs because of the internet connection problem I have this last couple of weeks). I want these (and to have desktop icons) to be available in the new installation.

I am divided between installing Xubuntu and Fluxbox, or Fluxbuntu. Any suggestion?

---

### Post by lyceum on 2007-01-11
I find Fluxbuntu faster than Xubuntu. It works better on older PCs.

---

### Post by K.Mandla on 2007-01-11
I would vote for a clean Fluxbuntu installation. Xubuntu adds a lot you wouldn't need under Fluxbox, and I've tried the Fluxbuntu CD and been very satisfied. Give it a shot.

---

### Post by PriceChild on 2007-01-11
I did a sever install and then isntalled xfce4 (NOT xubuntu-desktop) Much quicker :)

---

### Post by kerry_s on 2007-01-11
I would also go custom for those specs, just decide what you want out of that old laptop and build it up to your needs. That way you get exactly what you need with out extra crap getting in the way. Something like this to start->

server/command-line install
login
sudo su
nano /etc/apt/sources.list
comment(#) out the cdrom & uncomment all the repos
apt-get update
apt-get dist-upgrade
apt-get install x-window-system-core gdm fluxbox rox-filer leafpad eterm synaptic
type> reboot
select fluxbox from the session menu & log in to the gui 
use synaptic to continue the build up.

---

### Post by nutts4life on 2007-01-30
Hey how you doing,

I thought i might post as i have done exactly what you are doing and have some great advice.

I have a Thinkpad 570. I am not sure whether you are familiar with this machine but it came out a bit before yours (600e). I am also familar with your model as well.

I set out with the same task as finding a distro to run on my thinkpad.
I had ubuntu and xubuntu on my mahcine at home, so would have loved to go that way.

I tried:
xubuntu: Installed well from command line install, but took a long while to start up and was slow on running.
zenwalk: I liked this more than xubuntu as it was quicker and used xfce which is a prefered interface. But it was still too slow. I wanted something that was the speed of a modern PC running Windose.

so i started looking at DSL and Puppy. These were great as they were quick. BUT i felt they were moving away from the point of the whole idea. DSL especially is designed to be super small ( too small) and i was leaving my idea of a common distro of ubuntu.

That's when i came across fluxbuntu... I imagine you are crying at this oscar winning explanation by now!

I tried the install disk from the fluxbuntu site, which didn't work as it uses the GUI interface.

Basically it's a no brainer. Do what the guys above said. But instead:

- Install the xubuntu command line interface (xubuntu server install)
- apt-get install : flux box, xdm, rox 

This is the site i got the ideas from:

[http://techbycolin.com/?p=88](http://techbycolin.com/?p=88)

I can't emphasize enough how quick this setup is, the xubuntu server is quick and familiar. And once tweaked a little the fluxbox interface is trully superb.

As for your sound card. have a look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=141605](http://www.ubuntuforums.org/showthread.php?t=141605)

It's a common problem with the 600e, but you have a huge community in ubuntu to solve it.

---

### Post by Brunellus on 2007-01-30
server install + fluxbox.  but that's probably too stripped-down for you, if you're considering fluxbuntu as a viable solution.

I have an old Thinkpad--570e--and I went with Xubuntu/Fluxbox.  I will likely wipe & reinstall with a very very cut-down server/Fluxbox setup.

---

### Post by shellhrs on 2007-02-04
Guys, thanks for the response!

nutts4life: Oscar-winning explanation! :-D Really appreciate the links.

Brunellus: I guess you're right. Server install + fluxbox is a too much stripped down. I guess I will install from the Fluxbox LiveCD instead.

---

### Post by Brunellus on 2007-02-04
I report success on my minimal-install + fluxbox.  No display manager, no frills, no unnecessary services and BLAZING FAST performance on an old laptop.  w00t.

---

### Post by SZF2001 on 2007-02-04
So... Does Fluxbuntu work like Ubuntu? Not in the sense of being GNOME or KDE or XFCE, but by using the same repositories, a package manager, etc.?

---

### Post by ButteBlues on 2007-02-04
> **SZF2001 said:**
> So... Does Fluxbuntu work like Ubuntu? Not in the sense of being GNOME or KDE or XFCE, but by using the same repositories, a package manager, etc.?
Yes. It just uses Fluxbox as its DE.

---

### Post by Brunellus on 2007-02-05
> **SZF2001 said:**
> So... Does Fluxbuntu work like Ubuntu? Not in the sense of being GNOME or KDE or XFCE, but by using the same repositories, a package manager, etc.?
yes.  Fluxbuntu as a metapackage/install option should be thought of in the same way as all the other (U|Ku|Xu)buntu variants:  the base system, a window manager, plus a stack of supporting applications.  If you're satisfied with Fluxbuntu's choice of apps/services, go with that, and it should save a lot of bother at install time.  If your needs (like mine) are a bit more specialized/narrowly-defined, then it makes more sense to use the alternate install disc for Ubuntu and install a command-line only system, over which you can pick and choose the packages you need (and no more).

---

### Post by shellhrs on 2007-02-07
I've finally installed Fluxbuntu in my IBM TP 600e. It ran perfectly the first time -- I just need to type "startx" after logging in. Strangely, after twice rebooting, my system started directly into x-desktop :confused: :-D

Starting up is taking a little longer than Xubuntu, but after I get the desktop, it ran noticeably faster than before. Also moving between tabs in Firefox after moving from one desktop to another, didn't require much time (apparently the swap wasn't used -- unlike before).

In my first post I mentioned that I need to place icons on the desktop. Rox allowed this, although it's quite difficult (sorry, but Windows is simpler :-)). Anyway, Rox also messed up my background setting. I was unable to change the wallpaper. Putting fbsetbg -l in the ~/.fluxbox/startup file didn't work. I was finally able to change the wallpaper by changing the rootCommand setting in the ~/.fluxbox/init file. But sadly, I had to disable Rox in the startup file, so now I am left without desktop icons. :( Oh well, I can always edit the menu for shortcuts....

I used the directions [**here**]("http://www.ubuntuforums.org/showthread.php?t=283332") to get transparent terminal. I tried using aterm, but I could get rid of the borders, so I use Eterm instead (it's already installed by default).

I am still working on getting audio. Found [**this**]("http://www.ubuntuforums.org/showthread.php?p=1117587#post1117587"). I will definitely try the script. My modem & network card is in a PCMCIA card, so they're not a problem here.

So far, I am satisfied with Fluxbuntu. :) :) :)

Now if only I can get my audio and my desktop icons....

---

### Post by mips on 2007-02-07
> **shellhrs said:**
> 
Now if only I can get my audio and my desktop icons....

Dunno about the icons but I know the sound on the 600 series could be a little tricky. There are however a lot of thread out there on the sound issue, just search for *600 sound* and you should find some alternatively have a look at thinkwiki.

---

### Post by shellhrs on 2007-02-08
I had one more problem.

Fluxbuntu login screen doesn't have a shutdown option, so even though I chose "Exit" from the desktop menu, I was still unable to shutdown the computer.

I tried adding "sudo shutdown now" to ~/.fluxbuntu/menu but there's no response from the system. It didn't even ask for my password.

When I use the terminal to input the command above, the x desktop was shut down, but then I was sent to a text terminal as root (not my login). And even then, only "reboot" worked. Typing "shutdown now" didn't work.

Anyone have the same problem?

---

### Post by bionnaki on 2007-02-08
here's another great writeup that I've used to great success: [http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/](http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/)

---

### Post by wrinkols on 2007-02-08
> **shellhrs said:**
> I had one more problem.

Fluxbuntu login screen doesn't have a shutdown option, so even though I chose "Exit" from the desktop menu, I was still unable to shutdown the computer.

I tried adding "sudo shutdown now" to ~/.fluxbuntu/menu but there's no response from the system. It didn't even ask for my password.

When I use the terminal to input the command above, the x desktop was shut down, but then I was sent to a text terminal as root (not my login). And even then, only "reboot" worked. Typing "shutdown now" didn't work.

Anyone have the same problem?

This is my first post.  I'm still a bit new to linux, but been trying out different distros.

Anyways, just try using halt.  I believe that works to stop your system.  Suspend may also work but i'm not sure.

---

### Post by wrinkols on 2007-02-08
> **shellhrs said:**
> 
Now if only I can get my audio and my desktop icons....

I run fluxbox on my gentoo desktop.  I didn't see much about using icons except that you're supposed to run idesktop i believe (which is what I do).  With idesktop running you can configure your desktop and add/configure icons and whatnot.  It seems to be pretty light, but i'm not totally sure because this system runs well with any programs really.

currently it says 0.0 for cpu and 0.0 for mem.  So i'm not sure if that's an accurate way to asses how light it runs or not.

---

### Post by simoncifer on 2007-02-08
I have just started using Fluxbuntu for about 2 weeks, and I am glad to see someone else is also using Fluxbuntu.  

> **shellhrs said:**
> 
In my first post I mentioned that I need to place icons on the desktop. Rox allowed this, although it's quite difficult (sorry, but Windows is simpler :-)). Anyway, Rox also messed up my background setting. I was unable to change the wallpaper. Putting fbsetbg -l in the ~/.fluxbox/startup file didn't work. I was finally able to change the wallpaper by changing the rootCommand setting in the ~/.fluxbox/init file. But sadly, I had to disable Rox in the startup file, so now I am left without desktop icons. :( Oh well, I can always edit the menu for shortcuts....


As to your desktop icons problem, I think that because in order to display the icons on desktop, ROX-Filer put a screen over the original Fluxbox desktop.  So, if you try to change the wallpaper of fluxbox desktop, you won't see any changes with the desktop icons turn on (as you have find out).  You need to change the wallpaper of ROX-Filer Desktop if you have the desktop icons turn on.

To do that, there are a couple of ways, I find the easiest is to turn on the desktop icons first, then right click on one of the desktop icons.  A context menu will pop up, select the last entry named "Backdrop".  A new window will pop up, and just click on the button "Show" and select the wallpaper you want.

> When I use the terminal to input the command above, the x desktop was shut down, but then I was sent to a text terminal as root (not my login). And even then, only "reboot" worked. Typing "shutdown now" didn't work.

I believe the command is "sudo shutdown -h now", I think if you leave out the "-h" it would just put you to "runlevel 1" state instead (which is what you got).

As for putting it into menu, you would need a GUI version of sudo.  I think gksu should do the trick.  It is installed by default on my computer.  So, just put "gksu shutdown -h now" into the menu should work (I have tried this myself).

Personally, I am looking for a dockable app to do the shutting down (I think I saw one when I was browsing [dockapps.org]("http://dockapps.org") )

(A dockable app is a program/app that can be put into the "slit", which is the region where that pager is right now.  If you run a dockable app, it would be group with that pager.)

You can know more about slit and other things about Fluxbox via their [FAQ here]("http://fluxbox.sourceforge.net/docs/en/faq.php")  and 
[documentation here]("http://fluxbox.sourceforge.net/docbook/en/html/chap-slit.html")

Hope that help.


P.S.  This is my first post, so please be gentle :)

---

### Post by jdackle on 2007-02-08
That was a GREAT first post, simoncifer!!! :cool:

---

### Post by shellhrs on 2007-02-09
Simoncifer, thanks for the input, especially about Rox managing the desktop. I've read about it somewhere, but:

> A context menu will pop up, select the last entry named "Backdrop". A new window will pop up, and just click on the button "Show" and select the wallpaper you want.

That's the problem. When I right-clicked the file, there was no "Backdrop" in the menu. This is the reason I disable Rox in startup file.

> As for putting it into menu, you would need a GUI version of sudo. I think gksu should do the trick. It is installed by default on my computer. So, just put "gksu shutdown -h now" into the menu should work (I have tried this myself).

I put the command in my menu, but when I clicked on it, nothing happened. Maybe your system's different than mine? I had to resort to pulling up a terminal, then type "sudo shutdown now". It brought me to a text terminal, then I retyped the command.

---

### Post by jdackle on 2007-02-09
> **shellhrs said:**
> 



I put the command in my menu, but when I clicked on it, nothing happened. Maybe your system's different than mine? I had to resort to pulling up a terminal, then type "sudo shutdown now". It brought me to a text terminal, then I retyped the command.

Try **gksudo** instead of gksu.

---

### Post by simoncifer on 2007-02-11
> **shellhrs said:**
> Simoncifer, thanks for the input, especially about Rox managing the desktop. I've read about it somewhere, but:

That's the problem. When I right-clicked the file, there was no "Backdrop" in the menu. This is the reason I disable Rox in startup file.


Oh, see, when I right click on an icon on my desktop, I get a different menu than the regular fluxbox menu.  I have attached a screenshot to show the menu.

[Here is a screenshot of the default fluxbox menu]("http://wiki.fluxbuntu.org/index.php?title=Main_Page") that came with fluxbuntu.

This is beyond me, you probably could get some help from the [fluxbuntu forum]("http://community.fluxbuntu.org/index.php") :(

---

### Post by chick penguin on 2007-02-11
Really like Xubuntu and Fluxbox and Dillo. Didn't know about Fluxbuntu will have to get a copy. Trying out IceWM as well. Can still do a lot with this old machine. Getting it nice and clean. Stripped down. Fast

---

### Post by Brunellus on 2007-02-12
yeesh.  fluxbox + bloat?

---

### Post by chick penguin on 2007-02-12
Exploring the various flavors of U/Xubuntu and the wm.  Old hardware definitely works faster in Xubuntu with Flux box. Dapper just too heavy for this machine. I am liking the idea of fluxbuntu and am starting to read the threads to learn more. Would definitely like to go with it but have some questions. 

Right now I am interested in learning as much as I can about all these distributions in their various combinations. Just for interest sake.

So cluttering up my hard drive with a whole bunch of stuff is not a problem right now. Later when I find the right distribution for this machine then I will do a fresh install and go to work with it.

Question1:
Can I install Fluxbuntu and still keep the Ubuntu, Xbuntu and all my other wmanagers. I don't want to wipe out that part as I am having fun exploring it all.

Question2:
I know next to nothing about Linux and very little about any distribution. It sort of looks like Fluxbuntu might not be as user friendly as Xubuntu and esasy to install like Ubuntu. And then will I have to struggle to get the printer working and the screen resolution and all that. 

My console skills are also almost nil and my typing skills are not much better which is why I have stayed away from CLI. 

Maybe Fluxbuntu would be too difficult for a beginner.

I will keep reading.

---

### Post by kerry_s on 2007-02-12
Fluxbuntu is live cd so you can try it without installing. Fluxbuntu is like any other distro, you just have to play with it. Keep in mind the distro may change but most of the applications will be familiar as you move from distro to distro.

Also you should try DSL for fluxbox and jwm it gives you a good idea of what can be accomplished with a little time, it's very hard to squeeze what they have into 50mb but they did it.-> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

Once you get a good idea of what applications work for a low resource systems you should try the ubuntu server/command-line install build up and make the system to your needs.

---

### Post by kerry_s on 2007-02-12
> **shellhrs said:**
> Simoncifer, thanks for the input, especially about Rox managing the desktop. I've read about it somewhere, but:



That's the problem. When I right-clicked the file, there was no "Backdrop" in the menu. This is the reason I disable Rox in startup file.



I put the command in my menu, but when I clicked on it, nothing happened. Maybe your system's different than mine? I had to resort to pulling up a terminal, then type "sudo shutdown now". It brought me to a text terminal, then I retyped the command.



In rox options click the compatiabilty tab and check the top 3 boxs, that should get your fluxbox menu back.

---

### Post by Brunellus on 2007-02-13
> **kerry_s said:**
> Fluxbuntu is live cd so you can try it without installing. Fluxbuntu is like any other distro, you just have to play with it. Keep in mind the distro may change but most of the applications will be familiar as you move from distro to distro.

Also you should try DSL for fluxbox and jwm it gives you a good idea of what can be accomplished with a little time, it's very hard to squeeze what they have into 50mb but they did it.-> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

Once you get a good idea of what applications work for a low resource systems you should try the ubuntu server/command-line install build up and make the system to your needs.
the latter option is highly recommended for those people who can do it.  

Ubuntu 'server' starts, by default, a metric buttload of services that simply aren't needed on an older computer that isn't serving anything.  My laptop doesn't need RAID or Apache or anything of that sort.  It's a pain to have to go back and remove those packages when they are installed by default on the Dapper "server" install.

Edgy and subsequent releases have a 'command line system only' option, which installs only ubuntu-minimal.  This is preferred.  

On the continuum of desktop installs, from heaviest to lightest:

Kubuntu/Ubuntu>>>>>Xubuntu>>>>>Fluxbuntu>>>>>(ubuntu-minimal)

The three main *buntus eat up a lot of resources (comparatively) because they either use GDM or KDM to manage logins graphically.

---

### Post by shellhrs on 2007-02-15
> **jdackle said:**
> Try **gksudo** instead of gksu.

Tried it, and nothing happens.

But if I typed it in Terminal, the system went to shutdown. So now I removed the command from my menu, and just go to Terminal to shutdown. Or anyone have any suggestions?

Maybe it's just my system :confused:

---

### Post by penquin on 2007-02-15
I have tryed to run fluxbuntu on my own old thinkpad and it wouldn't boot up.  It just went to a screen like you get in terminal(sorry brainfart).  I did get my sound to work though in xubuntu dapper.  I used "snd-cs4232 index=0 port=0x530 cport=0x538 isapnp=0 dma1=1 dma2=0 irq=5" in etc/modules, but when I upgraded to edgy it didn't work

can I install fluxbuntu?  I thought it was a live cd.

---

### Post by DigitalDuality on 2008-06-03
it's probably just best to install ubuntu server and add fluxbox on top.

I'm currently playing with flux ontop of opensuse and loving it.  Using mostly commandline apps, with the exception of firefox and thunderbird (irssi, naim, snownews, rtorrent, etc)

---

### Post by Istonian on 2008-06-03
> **PriceChild said:**
> I did a sever install and then isntalled xfce4 (NOT xubuntu-desktop) Much quicker :)

I would do this and then install Fluxbox instead if Flux is what you want. I love base installs.

---

### Post by DarinB on 2008-06-20
Does Fluxbuntu get security updates just like xubuntu

---

### Post by snowpine on 2008-06-20
> **DarinB said:**
> Does Fluxbuntu get security updates just like xubuntu

Not by default, however, you can 'apt-get install update-manager'.

---

### Post by Anzan on 2008-06-20
> **simoncifer said:**
> I have just started using Fluxbuntu for about 2 weeks, and I am glad to see someone else is also using Fluxbuntu.  



As to your desktop icons problem, I think that because in order to display the icons on desktop, ROX-Filer put a screen over the original Fluxbox desktop.  So, if you try to change the wallpaper of fluxbox desktop, you won't see any changes with the desktop icons turn on (as you have find out).  You need to change the wallpaper of ROX-Filer Desktop if you have the desktop icons turn on.

To do that, there are a couple of ways, I find the easiest is to turn on the desktop icons first, then right click on one of the desktop icons.  A context menu will pop up, select the last entry named "Backdrop".  A new window will pop up, and just click on the button "Show" and select the wallpaper you want.



I believe the command is "sudo shutdown -h now", I think if you leave out the "-h" it would just put you to "runlevel 1" state instead (which is what you got).

As for putting it into menu, you would need a GUI version of sudo.  I think gksu should do the trick.  It is installed by default on my computer.  So, just put "gksu shutdown -h now" into the menu should work (I have tried this myself).

Personally, I am looking for a dockable app to do the shutting down (I think I saw one when I was browsing [dockapps.org]("http://dockapps.org") )

(A dockable app is a program/app that can be put into the "slit", which is the region where that pager is right now.  If you run a dockable app, it would be group with that pager.)

You can know more about slit and other things about Fluxbox via their [FAQ here]("http://fluxbox.sourceforge.net/docs/en/faq.php")  and 
[documentation here]("http://fluxbox.sourceforge.net/docbook/en/html/chap-slit.html")

Hope that help.


P.S.  This is my first post, so please be gentle :)

Great stuff. Thank you.

---

### Post by p_quarles on 2008-06-20
Thread locked, since this thread is well more than a year old, and Fluxbuntu is currently in a state of indefinite, umm, flux. (i.e., its future is uncertain).

---

