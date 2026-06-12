---
title: "LXDE 0.3 - Lightwght and Fast Desktop Environment (apt repo is provided)"
date: 2008-03-29
forum: The Cafe
---

### Post by PCMan on 2008-03-29
Lightweight X11 Desktop Environment, as known as LXDE, is a project launched in 2006 aimed to provide a modern lightweight desktop environment for X11.
It tries hard to get maximal usability from minimal resource usage, and provide a usable desktop for low end machines.
It's less known, but it's absolutely worth trying, especially when today's desktop environments are getting more and more bloated.  **In most cases, LXDE is lighter and even a little bit faster than XFCE.**

Project page: [http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)
Video - LXDE on EeePC (much faster then the built-in Xandros system): 
[http://video.google.com/videoplay?docid=6910499829356532385&hl=en](http://video.google.com/videoplay?docid=6910499829356532385&hl=en)

Add this apt repo to your /etc/apt/sources.list, or add this via Synaptic:
```
deb http://ppa.launchpad.net/lxde/ubuntu hardy main
deb-src http://ppa.launchpad.net/lxde/ubuntu hardy main
```

If you are using Gutsy, use this unofficial repo. (The packages here are out of date)
```
deb http://people.linux.org.tw/~pcman/ubuntu ./
```

Then, you  can get the basic LXDE desktop with this apt-get.
```

sudo apt-get update
sudo apt-get install lxde
```

After the installation, you can login to LXDE by choosing it from gdm.

This apt repo is maintained by LXDE developers. It only contains the most basic components of LXDE. More applications will be available via this repo after more testing is finished.

To see what LXDE looks like, here is the screenshots.

**The Whole Desktop - Simple, Fast, and Elegant**
[IMG]http://lxde.sourceforge.net/screenshots/desktop.png[/IMG]

**Easy & Fast File Management with PCManFM**
[IMG]http://lxde.sourceforge.net/screenshots/pcmanfm.png[/IMG]

**LXPanel Provides Everything You Expect For A Desktop Panel**
[http://lxde.sourceforge.net/screenshots/lxpanel_menu.png](http://lxde.sourceforge.net/screenshots/lxpanel_menu.png)

**The panel can be configured from GUI preference dialog, and there is no need to edit config files**
[IMG]http://lxde.sourceforge.net/screenshots/lxpanel_pref.png[/IMG]

**We also provides a "Run" dialog with autocompletion in the panel**
You can open this dialog with ```
lxpanelctl run
``` while lxpanel is running.
[IMG]http://lxde.sourceforge.net/screenshots/run_dlg.png[/IMG]

**Fast and Easy Image Viewing with GPicView**
[IMG]http://lxde.sourceforge.net/screenshots/gpicview.png[/IMG]

To see more screenshots, go to our project page please.
[http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)

---

### Post by kerry_s on 2008-03-29
koool

---

### Post by Changturkey on 2008-03-29
May I suggest a remaster of Ubuntu with this D.E?

---

### Post by mrgnash on 2008-03-29
> **Changturkey said:**
> May I suggest a remaster of Ubuntu with this D.E?

Lubuntu?

---

### Post by zmjjmz on 2008-03-29
Luxbuntu...
EDIT: Holy ***** ****** on a ***** sandwich with a side helping of ****** that was fast!

---

### Post by potrick on 2008-03-30
This looks awesome. I'll have to try this. Which versions of Ubuntu does the repository work with? I'm using Feisty right now.

---

### Post by chucky chuckaluck on 2008-03-30
very nice looking. clean and pretty. would you happen to have another video of it (that one looks like it was shot on a dirt road)?

---

### Post by whitefang5412 on 2008-03-30
sudo apt-get install lxde does not work..

---

### Post by TenPlus1 on 2008-03-30
I installed LXDE without any problems, and logging out and changing session worked fine...  I logged into a nice bar/menu and a huge error message stating something was wrong with GDM and no theme/icons specified...  

I could use the new DE for a while but clicking ok on the error requester instantly logged me out...  ho hum, was worth a go...  Any ideas how-to fix this ?

---

### Post by Ender Black on 2008-03-30
I installed LXDE on my EEE PC and all I can say is, WOW!  Smoking fast compared to to eeeXubuntu's XFCE DE.  Absolutely flawless so far for me.  Say hello to my new DE!

---

### Post by Barrucadu on 2008-03-30
That looks good. I'm looking to create a minimal Arch install on my pendrive (for 'maintenance' purposes, yeah, maintenance, that's right...) and this certainly seems very light.

---

### Post by RadenMu'az on 2008-03-30
It seems that ubuntu LXDE repo doesn't have LXAppearance (LXDE icon&theme changer) yet.
I have compiled the tgz to deb with checkinstall, and uploaded to Savefile.com

EDIT:
Download lxappearance.deb here: [http://www.savefile.com/files/1475263]("http://www.savefile.com/files/1475263")
(Thanks Ender Black for corrected the link.)

---

### Post by sports fan Matt on 2008-03-30
im taking it for a spin now...

---

### Post by sports fan Matt on 2008-03-30
This may be my new default since it loads much faster then gnome..i'll test it for a week and decide :)

---

### Post by Ender Black on 2008-03-30
> **RadenMu'az said:**
> It seems that ubuntu LXDE repo doesn't have LXAppearance (LXDE icon&theme changer) yet.
I have compiled the tgz to deb with checkinstall, and uploaded to Savefile.com
Get the deb [here]("http://http://dl1u.savefile.com/3d8a11e5fc18d55bea2c0ff517a49dd1/lxappearance_0.1-1_i386.deb")
:)

correct url here[http://dl1u.savefile.com/3d8a11e5fc18d55bea2c0ff517a49dd1/lxappearance_0.1-1_i386.deb]("http://dl1u.savefile.com/3d8a11e5fc18d55bea2c0ff517a49dd1/lxappearance_0.1-1_i386.deb")

---

### Post by Ender Black on 2008-03-30
actually...I still can't get a window decoration other than the black bar regardless of the theme I select.  

One other thing...is there a way to run conky in the LXDE environment?

---

### Post by RadenMu'az on 2008-03-31
> **Ender Black said:**
> correct url here[http://dl1u.savefile.com/3d8a11e5fc18d55bea2c0ff517a49dd1/lxappearance_0.1-1_i386.deb]("http://dl1u.savefile.com/3d8a11e5fc18d55bea2c0ff517a49dd1/lxappearance_0.1-1_i386.deb")

Uh... Savefile.com gave 'invalid download session'. Uploaded again.

Download here: [http://www.savefile.com/files/1475263]("http://www.savefile.com/files/1475263")

---

### Post by drascus on 2008-03-31
wow this is by far the best light weight D.E. That I have ever used. Lxbuntu anyone???

---

### Post by Changturkey on 2008-03-31
+1 for Luxbuntu.

---

### Post by chris4585 on 2008-03-31
this is a awesome DE, the only thing i dislike is that it uses pcmanfm, but its easily changable and not really that bad of a choice its just my personal prefference

But for those who want to test this on a fresh install, install ubuntu server edition

you can do these commands after install to get a fresh system with this DE

sudo apt-get install xorg gdm

sudo nano /etc/apt/sources.list

add deb [http://people.linux.org.tw/~pcman/ubuntu/](http://people.linux.org.tw/~pcman/ubuntu/) ./

to the sources.list

ctrl+o to save, then ctrl+x to exit

sudo apt-get update

sudo apt-get update

sudo apt-get install lxde

and this should work! just like any other DE

---

### Post by drascus on 2008-03-31
I just installed this on a ubuntu hardy beta; Old IBM pentium 2 with 313 MB of ram. Runs much smoother then it did with XFCE. Thanks pcman.

---

### Post by Acglaphotis on 2008-03-31
looks cool.

---

### Post by TheOrangePeanut on 2008-03-31
I'll definitely be trying this out when I go to my parents house where my older computer is.

---

### Post by plun on 2008-04-01
Fantastic...:D

The first light weight environment I like.

Thanks !

(lxpanel crashes for me during start but works OK after terminal restart)

EDIT also the cube is working...:lol:  (controlled with fusion-icon)

[[img]http://pix.nofrag.com/4/f/2/1bee78ba3e966236a12de9cccc42bt.jpg[/img]](http://pix.nofrag.com/4/f/2/1bee78ba3e966236a12de9cccc42b.html)

---

### Post by Odd-rationale on 2008-04-02
Really cool. I can't wait to try!

Would like to see this in the official repos...

---

### Post by timjohn7 on 2008-04-03
I've installed LXDE and have some new apps under Apps, but how do I log into LXDE and make it the default DE?  If it's already running, I cant see any difference in speed or appearance.  How can I find out if it is running?
Please excuse noobness!

---

### Post by PryGuy on 2008-04-04
Very cool! Is there a keyboard layout switcher plugin?

---

### Post by DJiNN on 2008-04-04
Anyone know if this will run on a 64bit system? I know OpenBox works on 64 bit, but not sure about this. Really great DE though, and certainly is fast on my Linux Mint install. :)

---

### Post by thiefghost on 2008-04-05
Not yet. LxDE do not work on 64-bit system now, but i think it is coming soon. :)

Let me talk about some news of LXDE:
Currently, we solve some bugs and design new features everyday.
In SVN, main part of LXPanel already be re-designed, so lxpanel has less memory usage now.

To Odd-rationale:
we are trying to push LXDE to official repos for debian and ubuntu now.
I think that you will see LXDE in the official repos after few days. I hope... :P

Fred.

---

### Post by PCMan on 2008-04-05
> **thiefghost said:**
> Not yet. LxDE do not work on 64-bit system now, but i think it is coming soon. :)
Fred.
Fred means, binary packages for 64-bit system are not available yet.
However, the programs themselves `do' support 64-bit.
You just need to compile them from source code on 64-bit systems.
We are not able to provide 64-bit packages since we don't have 64-bit systems.

---

### Post by SunnyRabbiera on 2008-04-05
I kind of like this, its primitive yes but has potential.

I am hoping to see some of these features:
a themer (but it I know you are working on it already)
a menu editor
trashcan support (as opposed to a plain delete function)
and maybe a better way to customize the panel apps, but so far so good :D

---

### Post by Saint Angeles on 2008-04-05
looks good and most people here seem pretty satisfied. i'm gonna try this when i get to work on monday.

(its a PIII running hardy)

---

### Post by andrewabc on 2008-04-05
I'll be testing this on my old computer sometime in the future. The computer is only used for firefox(+wireless), so as long as firefox 3 and plugins/extensions work that would be great.
Maybe include a firefox 3 screenshot so people know what it looks like with this distro?

pentium4 1.8ghz 768mb ram 32mb tnt2

Keep up the good work.

---

### Post by Odd-rationale on 2008-04-05
> **thiefghost said:**
> 
To Odd-rationale:
we are trying to push LXDE to official repos for debian and ubuntu now.
I think that you will see LXDE in the official repos after few days. I hope... :P

Fred.
Wow! thanks!

---

### Post by Odd-rationale on 2008-04-05
There seems to be a slight bug with the notification area in lxpanel. For example, here's a screenshot of nm-applet.

---

### Post by johnraff on 2008-04-05
I see file icons on that desktoop screenshot (post #1)!
Does that mean it's now OK to use that feature in pcmanfm 0.3.6?

(pcmanfm has had the option of drawing the desktop for a while, but in the documentation it's not recommended to use it, for some reason.)

---

### Post by Istonian on 2008-04-05
Check out PUD. It's Ubuntu based and uses LXDE.


[http://pud-linux.sourceforge.net/index.en.html](http://pud-linux.sourceforge.net/index.en.html)

---

### Post by PCMan on 2008-04-05
> **johnraff said:**
> I see file icons on that desktoop screenshot (post #1)!
Does that mean it's now OK to use that feature in pcmanfm 0.3.6?

(pcmanfm has had the option of drawing the desktop for a while, but in the documentation it's not recommended to use it, for some reason.)

In 0.3.6.2, that bug is fixed.
Besides, in 0.3.9.10, that part is totally re-written and it's much better than 0.3.6 series.

---

### Post by sports fan Matt on 2008-04-05
I love this manager but im wondering when that version you mentioned will be released

---

### Post by johnraff on 2008-04-06
> **sox fan Matt said:**
> I love this manager but im wondering when that version you mentioned will be released

You can often get the latest version here:
[http://www.getdeb.net/app/PCMan+File+Manager](http://www.getdeb.net/app/PCMan+File+Manager)
:)

---

### Post by rytmisk on 2008-04-11
Hi guys!

LXDE is mighty cool! Looks nice and the menu actually is quite usable out of the box.

But - I want to configure some things to my own tastes and I can`t seem to find the docs ([http://lxpanel.sourceforge.net/docs.html](http://lxpanel.sourceforge.net/docs.html) is down). So how do I....

1) I'd like to have the menubar to automatically appear when I move my mouse to it and then disappear when I have no more need for it.

2) I'd like to have gnome network applet and a few other applets start automatically - where do I put the startup file - what is it supposed to be named and is it supposed to a standard bash executable?

Nice work by the way!!

Ketil

---

### Post by orduek on 2008-04-14
OK. I installed it on a old PIII celeron 700 with 300mb RAM.
Only problem is I can't connect to the wireless network in my house (even after installing ndiswrapper)  - on the same computer running Xubuntu I have no such problem.

---

### Post by wannadumpwindows on 2008-04-14
It's certainly getting a test run on my Eeepc . . . . .

---

### Post by DJiNN on 2008-04-14
> **orduek said:**
> OK. I installed it on a old PIII celeron 700 with 300mb RAM.
Only problem is I can't connect to the wireless network in my house (even after installing ndiswrapper)  - on the same computer running Xubuntu I have no such problem.

If you're running LXDE on top of Xubuntu base (Effectively using LXDE instead of XFCE) then your wireless should be picked up automatically, the same as it was in Xubuntu using XFCE?

What is your wifi? Built in, card, stick? Do you have the firmware/drivers installed? (I'm assuming you do if it works in Xubuntu).

---

### Post by wannadumpwindows on 2008-04-14
Everything worked flawlessly for me. I didn't have to mess with anything. Everything fired right up. Wireless even auto-connected. Insanely fast on my Eeepc. I'm pretty sure I just found a new default. Especially with more functionality on the way. Don't see how I could go wrong . . . . .

---

### Post by orduek on 2008-04-14
> **DJiNN said:**
> If you're running LXDE on top of Xubuntu base (Effectively using LXDE instead of XFCE) then your wireless should be picked up automatically, the same as it was in Xubuntu using XFCE?

What is your wifi? Built in, card, stick? Do you have the firmware/drivers installed? (I'm assuming you do if it works in Xubuntu).

My wireless is TP-LINK. It has a restricted hardware driver.
but I wasn't able to connect to my WEP ASCII wireless network. for some reason I wasn't able to pick it up from nowhere.

---

### Post by marquee moon on 2008-04-14
> **chris4585 said:**
> this is a awesome DE, the only thing i dislike is that it uses pcmanfm, but its easily changable and not really that bad of a choice its just my personal prefference
 
But for those who want to test this on a fresh install, install ubuntu server edition
 
you can do these commands after install to get a fresh system with this DE
 
sudo apt-get install xorg gdm
 
sudo nano /etc/apt/sources.list
 
add deb [http://people.linux.org.tw/~pcman/ubuntu/](http://people.linux.org.tw/~pcman/ubuntu/) ./
 
to the sources.list
 
ctrl+o to save, then ctrl+x to exit
 
sudo apt-get update
 
sudo apt-get update
 
sudo apt-get install lxde
 
and this should work! just like any other DE
 
Looking at what's included in the Ubuntu LXDE repository [here]("https://launchpad.net/~lxde/+archive"), wouldnt you also need a window manager, like openbox, as described in the[ minimal install page]("https://help.ubuntu.com/community/Installation/LowMemorySystems") ?
 
So install server, uncomment repositories, add the PCManFC repository, update & *upgrade*, then:
 
[I]sudo aptitude install openbox obconf openbox-themes 
 
sudo aptitude install lxde xorg xdm xterm synaptic firefox idesk 
 [/I]

not yet done this, so any comments? 
 
 
MM

---

### Post by dizee on 2008-04-14
> **marquee moon said:**
> Looking at what's included in the Ubuntu LXDE repository [here]("https://launchpad.net/~lxde/+archive"), wouldnt you also need a window manager, like openbox, as described in the[ minimal install page]("https://help.ubuntu.com/community/Installation/LowMemorySystems") ?
 
So install server, uncomment repositories, add the PCManFC repository, update & *upgrade*, then:
 
[I]sudo aptitude install openbox obconf openbox-themes 
 
sudo aptitude install lxde xorg xdm xterm synaptic firefox idesk 
 [/I]

not yet done this, so any comments? 
 
 
MM
Openbox is installed along with LXDE anyway :)

Must say from first impressions it is very impressive - really nice looking and blazing fast! Great work.

---

### Post by bigbrovar on 2008-04-14
> Openbox is installed along with LXDE anyway 

Must say from first impressions it is very impressive - really nice looking and blazing fast! Great work.
exactly .. i installed if for my window hating friend .. on his ultra light sony vaio notebook...it sure rock as hell and its blazingly fast

---

### Post by fluteflute on 2008-04-14
Just installed it and I have to agree with a previous comment: it's the first lightweight environment (minus XFCE) I like. And it's super fast.

I'm hoping my old laptop willl run it with decent speed.

---

### Post by marquee moon on 2008-04-15
This is great! I installed this from a clean server install last night. Very, very fast: it opens firefox in the blink of an eye.
It strikes a lovely balance between a lightweight, simple desktop & a good looking, user friendly desktop. 
Its got the speed of a tiny desktop with the feel of a big desktop. 

I also love PCManFC. The ability to "open as root" is very useful. 


Only one problem for me, though: LXDE tried to pick up my **gtkrc-2.0 ** but becuase I didnt have gnome installed it couldnt find it. It popped up with a message when I first logged in, which gave some advice on how to solve this problem.  I found a document (from PCman?) giving the same explanation that I need to add  a ~/.gtk-rc2.0 file stipulating my theme. But this appears not to help. So the theme cannot be adjusted at all.  
Not sure what I'm doing wrong.....Also, I cant get icons on the desktop- any ideas? 

Either way, its very fast & has a very smooth feel. 

Nice work PCman!

{edit: can the gtkrc-2.0 issue be resolved by using  [ LXAppearance](http://www.gnomefiles.org/app.php/LXAppearance) ?}

{further edit, I read that LXDE requires GTK+ and I dont think this is installed with the server installation. So I guess to resolve this issue I will install GTK+. I presume LXAppearance is a theme manager which manages GTK+...? }

---

### Post by eriqjaffe on 2008-04-15
> **marquee moon said:**
> I presume LXAppearance is a theme manager which manages GTK+...?Yep.

---

### Post by orduek on 2008-04-16
sorry for the stupid question but...
I didn't find the place were I change my screen resolution in LXDE.
am I missing something here?

---

### Post by andrewabc on 2008-04-16
Will a new version be released when the release candidate is released in a couple days? Or will you be waiting until 8.04 final is released before new version?

I want to test this out but don't want to spend bandwidth if it is going to be updated in a week when rc/final is released.

EDIT:
I guess what I meant above is that on your website you list an ubuntu linux live cd called PUD GNU/Linux:. You know anything about that? Is is Taiwanese only? would running pud give me a good idea of what lxde is like resource wise?

Or would the best way to install it on a minimal system would be to use alternate ubuntu cd and install everything from scratch?

---

### Post by Odd-rationale on 2008-04-16
I have a few quick questions:

1) Will lxde be in the hardy repos? or will a separate repo be needed?
2) For Gutsy, which repo is reccommended:
deb [http://ppa.launchpad.net/lxde/ubuntu](http://ppa.launchpad.net/lxde/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/lxde/ubuntu](http://ppa.launchpad.net/lxde/ubuntu) gutsy main
or
deb [http://people.linux.org.tw/~pcman/ubuntu/](http://people.linux.org.tw/~pcman/ubuntu/) ./
3) Why is lxappearence not in any of the repos?
4) When will lxnm be out?

Thanks!

---

### Post by marquee moon on 2008-04-17
Odd Rationale:

In Gutsy, I used 

deb [http://people.linux.org.tw/~pcman/ubuntu](http://people.linux.org.tw/~pcman/ubuntu) ./

(**NOTE**:* no forward slash at the end of ubuntu*, then space, dot, forward slash). 

This worked fine. 

If you use 
deb [http://people.linux.org.tw/~pcman/ubuntu/](http://people.linux.org.tw/~pcman/ubuntu/) ./

you wont get very far.

---

### Post by TeeLicht on 2008-04-24
What about proposing [Parcellite]("http://code.google.com/p/xyhthyx/") as the default Clipboard for LXDE on your webpage?

---

### Post by firmit on 2008-04-29
> **rytmisk said:**
> 
2) I'd like to have gnome network applet and a few other applets start automatically - where do I put the startup file - what is it supposed to be named and is it supposed to a standard bash executable?
Ketil

I answered this here:
[http://ubuntuforums.org/showpost.php?p=4833608&postcount=3](http://ubuntuforums.org/showpost.php?p=4833608&postcount=3)

Simply add LXFE to OnlyShowIn in the .desktop file - appz you want to autostart ~/.config/autostart

---

### Post by firmit on 2008-05-02
I have a problem. It might be some kind of setting I have not done yet, so any help will be highly appreciated.

I installed xubuntu 8.04 alt. cli only. Then added the repo, and 
```
$ sudo apt-get install xorg lxde dbus hal obconf
```

On lxde.sourceforge, it states that if I do NOT have a display manager installed, I should create .xinitrc with startlxde: 
```
$ echo startlxde > ~/.xinitrc
```
Now I issued
```
startx
```

Now my problems. 
1) automount does not work
2) Theme's do not work proberly. lxapperance, once installed, do not change the window behavior (title bar, border etc), only icons and theme inside of windows. 
3) .Xresources is NOT loaded / used - I have configured xterm here.

Okei - so I delete the .xinitrc file. And new startx with new sets of problems:

1) automount works!
2) I am not able to edit ~/.config/openbox/lxde-rc.xml with to my liking. With obconf I get error while saving. 
2b) Window theme follows some kind of rule... actually - I do not know which, because I am not able to change any option with obconf. Guessing it comes from the std. file.
3) .Xresources is loaded
4) Alt-F2 keybinding for the RUN dialog (lxpanelctl run) is not working

Regarding automount: I am member of 'plugdev'.
](*,)
What am I doing wrong? Kind of embarrassed for how long it took for me to see the symptoms :(

---

### Post by skymera on 2008-05-02
So whats the differences in memory usage compared to Gnome? and more importantyl, how quick does it login?

---

### Post by chochem on 2008-05-04
> Now my problems. 
1) automount does not work
2) Theme's do not work proberly. lxapperance, once installed, do not change the window behavior (title bar, border etc), only icons and theme inside of windows. 
3) .Xresources is NOT loaded / used - I have configured xterm here.

Okei - so I delete the .xinitrc file. And new startx with new sets of problems:

1) automount works!
2) I am not able to edit ~/.config/openbox/lxde-rc.xml with to my liking. With obconf I get error while saving. 
2b) Window theme follows some kind of rule... actually - I do not know which, because I am not able to change any option with obconf. Guessing it comes from the std. file.
3) .Xresources is loaded
4) Alt-F2 keybinding for the RUN dialog (lxpanelctl run) is not working

Regarding automount: I am member of 'plugdev'.
](*,)
What am I doing wrong? Kind of embarrassed for how long it took for me to see the symptoms :(

**automounting:** I cannot see how this should be linked to your desktop environment, as the daemons that should take of it are loaded way before lxde kicks in. First off, is udev working, i.e. do the devices you're trying to mount show up as /dev/sd[a letter and a number]? if you have assigned labels to your devices, i.e. MYUSBSTICK, you can also check the directory /dev/disk/by-label. Secondly, are the daemons running? You can install 'bum' to check up on the services the machine is running on startup. My final two cents are somewhat more practical: My standard apt-get install line on a fresh system includes 'dbus' and 'dbus-x11' though I can't say for sure if one doesn't come with the other as a dependency (packages search site seems to be down). Can't remeber where I picked it up.

**lxappearance** writes the ~/.gtkrc-2.0 file. Which doesn't have information on you window manager theme (that's in you rc.xml). So lxappaerance should not do what you're asking for. Use obconf for that. Also be aware, that the root user has it's own theme settings independent of the regular user. So for instance, Synaptic will not comply with your regular settings.

I suspect that given the **obconf** error and your **malfunctioning shortcuts** that your rc.xml has been corrupted somehow. I'd suggest deleting it and starting over afresh - I don't know how much pcman has changed standard openbox settings (i'm on an regular openbox system and just picks out a few of his tools here and there) but you can probably get a fresh rc.xml by copying one from /etc/xdg/openbox/ (or something like that - try exploring /etc/xdg/ anyhow). If you've added a lot to the rc.xml and don't want to delete it, I'd suggest putting it through some sort of [xml validation]("http://www.google.com/search?hl=en&q=xml%20validation") that will tell you where the error is.

---

### Post by DJiNN on 2008-05-04
> **skymera said:**
> So whats the differences in memory usage compared to Gnome? and more importantyl, how quick does it login?

I don't have figures, but from using it on several different machines for the last month or 2, quite a lot.  Smaller footprint, a bit like XFCE but a lot lighter than that even. It's worth a go, especially on older (resource limited) hardware. Runs really well on even a modest setup.

---

### Post by naycon on 2008-05-05
I've been trying to install LXDE but it keeps looking for pcmanfm 0.3.9.10, but in the provided repo (if I open it in firefox) there's a newer version of that file. I'm not a linux guru, but I guess this is connected some how to the package list that apt-get update fetches, which I also guess is still pointing at the old file. Anyone have any idea on how I can solve this? Here's the output from apt-get install lxde:

Err [http://people.linux.org.tw](http://people.linux.org.tw) ./ pcmanfm 0.3.9.10-1~pcman1
  404 Not Found
Failed to fetch [http://people.linux.org.tw/~pcman/ubuntu/./pcmanfm_0.3.9.10-1~pcman1_i386.deb](http://people.linux.org.tw/~pcman/ubuntu/./pcmanfm_0.3.9.10-1~pcman1_i386.deb)  404 Not Found

---

### Post by DJiNN on 2008-05-05
It seems that both LXDE as a suite & PCmanFM are being developed quite a lot & changing regularly, which is great, but can cause problems such as you're experiencing. 

Here's a few links that may help your PCmanFM problem at least. :)

[The latest tarball]("http://www.gnomefiles.org/app.php/PCMan_File_Manager") (Source - v0.4.0) for compiling (Released May 4th)

[Version 0.3.9.10]("http://www.getdeb.net/release.php?id=2374") as a deb (Compiled to run on Gutsy)

So if you're running Gutsy & want a quick fix, then get the 2nd one. If you want the very latest version, and are prepared to compile, then get the first. :)

Hope that helps

---

### Post by firmit on 2008-05-05
> **DJiNN said:**
> I don't have figures, but from using it on several different machines for the last month or 2, quite a lot.  Smaller footprint, a bit like XFCE but a lot lighter than that even. It's worth a go, especially on older (resource limited) hardware. Runs really well on even a modest setup.

Mysetup shows a ram usage of 39.98 MB after firing up - at least that's what Conky tells me :) Though, I have Debian Lenny as the core. This is significantly smaller than my Xubuntu 8.04 which uses about 110 MB after firing up.

---

### Post by DJiNN on 2008-05-05
> **firmit said:**
> Mysetup shows a ram usage of 39.98 MB after firing up - at least that's what Conky tells me :) Though, I have Debian Lenny as the core. This is significantly smaller than my Xubuntu 8.04 which uses about 110 MB after firing up.

Well, that's quite a reduction eh? :)  I'm currently using it with an antiX base on a P3 and it flies just as fast as fluxbox/openbox  ever does, but it's always good to see some figures eh? BTW, how did you get conky on the desktop?  Tried it here but pcmanfm doesn't seem to like it. :)

Shame about Xubuntu as well..... such a great distro, but fast becoming heavier with each release.

PS: Like your blog. +1

---

### Post by firmit on 2008-05-05
> **DJiNN said:**
> (..) 
BTW, how did you get conky on the desktop?  Tried it here but pcmanfm doesn't seem to like it. :)

It works fine here - not sure why pcmanfm should not approve of conky...
Getting conky on the desktop is merely a matter of defining the right variables in your .conkyrc. My setup is in this *[post]("http://firmit.wordpress.com/2008/04/29/conky-x-system-monitor/")* on my blog :)

I have used the same setup on LXDE and XFCE. Don't know if pcmanfm requires you to have "Show file icons on desktop" selected in preferences - I do...

[QUOTE=DJiNN]
Shame about Xubuntu as well..... such a great distro, but fast becoming heavier with each release.
[/QUOTE]
I believe the growing back-end of ubuntu has taken its toll on xubuntu.

[QUOTE=DJiNN]PS: Like your blog. +1[/QUOTE]
Ty! :)

---

### Post by DJiNN on 2008-05-05
> **firmit said:**
> It works fine here - not sure why pcmanfm should not approve of conky...
Getting conky on the desktop is merely a matter of defining the right variables in your .conkyrc. My setup is in this *[post]("http://firmit.wordpress.com/2008/04/29/conky-x-system-monitor/")* on my blog :)

I have used the same setup on LXDE and XFCE. Don't know if pcmanfm requires you to have "Show file icons on desktop" selected in preferences - I do...

Hi firmit, thanks for the reply.

Hmmm, it seems that whenever i enable that feature from within the prefs dialog in pcmanfm, conky is no longer visible. When i "disable" it conky comes back....???   I don't mind too much because i don't use icons that much anyway, and i think i'd rather have conky available than not, but it would be nice to have both of course. :)

> I believe the growing back-end of ubuntu has taken its toll on xubuntu.It certainly has, and it's a real shame, because by the time you get to the power required to run Xubuntu efficiently, you're almost in Gnome/KDE territory. :)

---

### Post by eriqjaffe on 2008-05-05
> **DJiNN said:**
> Hi firmit, thanks for the reply.

Hmmm, it seems that whenever i enable that feature from within the prefs dialog in pcmanfm, conky is no longer visible. When i "disable" it conky comes back....???I've run into that, too.  I find that setting own_window_type to "Normal" works fine.  Otherwise, it fights with PCManFM to write to the root window.

---

### Post by firmit on 2008-05-05
The only unwanted behaviour I have experienced, is that I would like conky to be sticked to the background - even when I click "show desktop"=minimize all. For the time being it gets minimized along with the other open applications.

---

### Post by DJiNN on 2008-05-05
> **firmit said:**
> The only unwanted behaviour I have experienced, is that I would like conky to be sticked to the background - even when I click "show desktop"=minimize all. For the time being it gets minimized along with the other open applications.

Now that i've finally got it working (Thanks to some of your conky settings) i'm finding the same thing. It's no great problem as i very rarely use that feature, but it would be nice to be able to get it working as it should. :)

---

### Post by TrD on 2008-05-10
This Desktop Environment is great. Im using it on my hp nc6000, with 256 of RAM and it is very light and good looking at the same time. Right now my computer is using 180MB of RAM with firefox, deluge and emesene running. Thank you.

---

### Post by chris4585 on 2008-05-10
how do you get lxappearance to work properly? I have openbox, not LXDE, when I try to switch themes or icons, nothing happens.

---

### Post by vexorian on 2008-05-10
> It tries hard to get maximal usability from minimal resource usage, and provide a usable desktop for low end machines.
It's less known, but it's absolutely worth trying, especially when today's desktop environments are getting more and more bloated. In most cases, LXDE is lighter and even a little bit faster than XFCE.Sorry, but the world has taught me to avoid buying those statements easily.

Is this GTK or QT based, or what?

---

### Post by capink on 2008-05-10
> **vexorian said:**
> Sorry, but the world has taught me to avoid buying those statements easily.

Is this GTK or QT based, or what?

It is based on GTK 2.0. So all the themes for gnome can be used for LXDE, except the window manager (openbox) ofcourse, which have its own theme.

---

### Post by vexorian on 2008-05-10
First impressions:
- How do you change the theme, really?
- The initial theme tries to hard to look like vista, and fails terribly, it really needs to find its own identity.
- The panel allows transparency but can't render transparent PNGs.
- It ran compiz? Is this a bug? (I had compiz disabled before trying)
- How do you enable multiple desktops?
- It doesn't seem to know that files that end with ~ are considered hidden.

It is very fast, but I just wish I could fix the theme and change the icons to something that's not as ugly as vista, then I could actually use this DE... If anything, it would be awesome as a for-show face, it is running compiz and it is still smooth, that's incredible...

Edit: So lxappearance allows me to change the gtk theme, now it looks good, but can't change the window title color, ideas? I changed the icon theme but it still uses these ugly vista like icons I can't stand...

If I get that fixed and I got virtual desktops I would actually give it a try for a week.

Edit II: Hey, a warning, it will startup all the programs you got in session init settings, even those who are unchecked...

---

### Post by capink on 2008-05-10
To change the window decoration you need to use openbox GUI config. I don't use openbox, but I think it have a settings manager called obconf, you can start it by pressing ALT+F2 and typing obconf.

Also I have never used lxappearence, as it has just been released, and I have been using lxpanel for sometime now. For changing themes, I edit the file ~/.gtkrc-2.0. Here is my the output of my ~/.gtkrc-2.0:

```
include "/usr/share/themes/Glossy P/gtk-2.0/gtkrc"
gtk-icon-theme-name = "snowish"

```

After editing this file you will need to relog for the changes to take effect.

Edit: Virtual Desktops can be configured via obconf as well.

---

### Post by kagashe on 2008-05-10
I have installed LXDE in Hardy Heron.

Logout button does not work.

---

### Post by eriqjaffe on 2008-05-11
I've been toying around with lxpanel a bit, but I can't figure out how to make the system tray and clock "stick" on the right side of the screen...is that possible?

---

### Post by firmit on 2008-05-12
> **eriqjaffe said:**
> I've been toying around with lxpanel a bit, but I can't figure out how to make the system tray and clock "stick" on the right side of the screen...is that possible?
Not quite sure what you mean - but I am guessing you have not checked "expand" on the "open applications" when you edit the panel. Each applet use its assigned space. You need to expand one of them. The applets on each side of the expanded applet will be "pushed" out to each side. You will then get the clock and system-tray "sticked" :)

I don't think you can use the "space" for this. You need to expand an applet.

---

### Post by Half-Left on 2008-05-12
Tried it on my wifes laptop, logout dont work and wireless network applet dont connect after added the network key. I compiled it on my x64 machine and seems to work better, runs like lightning.

---

### Post by frenchn00b on 2008-05-12
check it out , my pcmanfm (file browser) was eating my CPU of over 30pct !!!! amazign 
lol

---

### Post by frenchn00b on 2008-05-12
> **Half-Left said:**
> Tried it on my wifes laptop, logout dont work and wireless network applet dont connect after added the network key. I compiled it on my x64 machine and seems to work better, runs like lightning.

for women, I would advice: kde or gnome or icewm
My experience with openbox, fvwm ... was a disaster. She got peaced of too complex a windows manager :) KDE was the winner (otherwise that a windows back ) lol

---

### Post by bash on 2008-05-12
Does Compiz work on/with LXDE?

---

### Post by Half-Left on 2008-05-12
Yes compiz does.

I was looking for something lighter than GNOME for her and this seemed to do the job but it's buggy, only has a Celeron 1.5Ghz/512mb laptop with Wubi, for some reason memory is higher and in swap with 512mb.

---

### Post by chochem on 2008-05-12
> **bash said:**
> Does Compiz work on/with LXDE?

Compiz is a window manager. LXDE is a desktop enironment, meaning it's a collection of software that makes up a 'desktop', including a window manager, Openbox. Installing Compiz on top of LXDE will simply discard Openbox in favour of Compiz. Mind you, Compiz will drag som many Gnome dependencies in with it that you might as well have installed Gnome but as Troy McClure said to Dolores Montenegro in "Calling All Quakers": "Have it *your* way, Baby!!" ;)

---

### Post by eriqjaffe on 2008-05-13
> **firmit said:**
> Not quite sure what you mean - but I am guessing you have not checked "expand" on the "open applications" when you edit the panel. Each applet use its assigned space. You need to expand one of them. The applets on each side of the expanded applet will be "pushed" out to each side. You will then get the clock and system-tray "sticked" :)

I don't think you can use the "space" for this. You need to expand an applet.Holy moly, I can't believe I didn't notice that.  Thanks!

---

### Post by rolypolycat on 2008-05-14
WoW! I love this desktop! I'm running it on a Compaq 4400 presario-1300 mhz and it flies!:KS
Got some questions, though:
1. How do I add an item to the Applications menu? Some of my programs don't show up. 
2. Is there any way to change the clock to AM-PM time instead of  24 hours?
3. Right now, I'm running this as a session with xfce. I intend to re-do the computer with just LXDE tonight. If I do a minimal install, this shouldn't drag in anything from gnome, kde, etc; all that junk I don't use and clogs up my machine? This brings in  HP printer support, automount drives, etc? Or is there something I should install at the time to ensure I get this support? I'd really rather not go through all the effort to install LXDE, only to find I can't print, can't automount my backup cd's. If anyone can give me any pre-install advice, I'd greatly appreciate it. From what I've read on this thread, folks here seem to be pretty knowledgable about installing this stuff.
Thanks in advance!:)

---

### Post by eriqjaffe on 2008-05-14
Most drivers are going to be part of the Kernel, so building up from a CLI shouldn't affect that.

You shouldn't have any troubles with mounting devices, as PCManFM seems to handle that pretty easily - at least, it does on my laptop.

I don't know about manually editing the application menu, but you can always just create a .desktop file in /usr/share/applications for whatever you want.  Just use an existing .desktop file as a template - LXPanel auto-builds based on those files.

---

### Post by firmit on 2008-05-14
> **rolypolycat said:**
> WoW! I love this desktop! I'm running it on a Compaq 4400 presario-1300 mhz and it flies!:KS
Got some questions, though:
1. How do I add an item to the Applications menu? Some of my programs don't show up. 
2. Is there any way to change the clock to AM-PM time instead of  24 hours?
3. Right now, I'm running this as a session with xfce. I intend to re-do the computer with just LXDE tonight. If I do a minimal install, this shouldn't drag in anything from gnome, kde, etc; all that junk I don't use and clogs up my machine? This brings in  HP printer support, automount drives, etc? Or is there something I should install at the time to ensure I get this support? I'd really rather not go through all the effort to install LXDE, only to find I can't print, can't automount my backup cd's. If anyone can give me any pre-install advice, I'd greatly appreciate it. From what I've read on this thread, folks here seem to be pretty knowledgable about installing this stuff.
Thanks in advance!:)

1) The lxpanel uses whatever is in the /usr/share/applications/ - so edit wthe .desktop files as you see fit. A tip though: copy the ones you need to   ~/.config/autostart and edit them there. In that way - if you do something "wrong" (as if you can do anything wrong in linux :--) ) you can simple delete these files, and the default settings/files are kept.

2) Clock format: right click - change from "%R" to: "%r" :)

3) I had difficulty installing LXDE with ubuntu minimal. I "converted" back to Debian. Mainly because of dependency issues between debian and the ubuntu packages. And frankly, this is my recommendation: install Debian Etch with no desktop environment - then update to Lenny or Sid. Add the DEBIAN deb in /etc/apt/sources.list (from lxde.sf.net) and install xorg and lxde. I believe these packages are more up-to-date than the ubuntu packages. I did this. There may be a How-to soon on my blog :) (see signature).

You can not get away of installing a lot of libraries if you intend to run Abiword and Gnumeric. But so what - libraries are used when needed!

Another thing - PCMANFM do NOT automount - it simply mount's on demand - when you click the folder/mount-point the device gets mounted. If you wish to automount devices, I would recommend ivman.

ps: I love LXDE - I only use this DE now - even on my duo core 2.2GHz 2GB ram - it uses <40MB ram which is quite low :)

---

### Post by firmit on 2008-05-14
Another thing - the Clock applet is not really a clock-applet per se. Well it is - BUT - you may type whatever you want pretty much. 

%R -default 24 hour clock
%r - 12 hour clock am/pm
anytext - displays "anytext"

Same goes for Tooltip format.

Action - maybe run "xterm" or any terminal emulater? Your choice! I like the standard calender. If you like, you may even run a script to open whatever you like!

---

### Post by eriqjaffe on 2008-05-14
> **firmit said:**
> Another thing - PCMANFM do NOT automount - it simply mount's on demand - when you click the folder/mount-point the device gets mounted. If you wish to automount devices, I would recommend ivman.To a large extent, that is close enough to automounting for most people - the device shows up in the pane on the left, click on it, it mounts, and the contents show up in the right pane.  Not true automounting, but it's almost a matter of semantics.

---

### Post by rolypolycat on 2008-05-15
Thanks for the info, everybody; I've printed it out, and I'm going for the re-install. I'll let you know how it turns out. thanks again!

---

### Post by graabein on 2008-05-15
Can LXDE be modified or built for tablet devices like the Nokia [N800]("http://europe.nokia.com/A4305063") and [N810]("http://europe.nokia.com/A4568593")? 

Would probably have to lay out the desktop a bit different and adjust font size, among other things. Onscreen keyboard must be easily accessible.

---

### Post by DJiNN on 2008-05-15
> **firmit said:**
> 1) The lxpanel uses whatever is in the /usr/share/applications/ - so edit wthe .desktop files as you see fit. A tip though: copy the ones you need to   ~/.config/autostart and edit them there. In that way - if you do something "wrong" (as if you can do anything wrong in linux :--) ) you can simple delete these files, and the default settings/files are kept.

That's good to know. For some reason, i always seem to forget that it's the .desktop files that are key here. :)  Thanks firmit.

> 3) I had difficulty installing LXDE with ubuntu minimal. I "converted" back to Debian. Mainly because of dependency issues between debian and the ubuntu packages. And frankly, this is my recommendation: install Debian Etch with no desktop environment - then update to Lenny or Sid. Add the DEBIAN deb in /etc/apt/sources.list (from lxde.sf.net) and install xorg and lxde. I believe these packages are more up-to-date than the ubuntu packages. I did this. There may be a How-to soon on my blog :) (see signature).

Looking forward to seeing the howto. :)   I've installed LXDE on several machines now, and have found that, if you install the "meta-package" (apt-get install lxde) then you get loads of stuff, including GDM (Which i didn't want as i prefer SLiM) but if you do an "apt-cache search lxde" then take note of the seperate apps (lxpanel, lxsession-lite, lxde-common etc etc) and just install them using apt-get (along with gpicview, pcmanfm and openbox of course) then you end up with a lighter lxde and one without GDM.  

> ps: I love LXDE - I only use this DE now - even on my duo core 2.2GHz 2GB ram - it uses <40MB ram which is quite low :)

I agree! It's a great DE, and even though i use fluxbox on my main machine, i often boot into LXDE just because it makes a nice change, and it's still very light & fast, but full featured. :)

---

### Post by TrD on 2008-05-15
Is there a way to make web links open in Opera? Something like the "Preferred Aplications" (I don't know if this is what it is called, mine is in portuguese: "Aplicações Preferidas")

---

### Post by rolypolycat on 2008-05-16
Bwah, ha, ha,! It lives!!:lolflag:
I did a minimal install, tossed lxde on top of it, and aside from a few quirks, it runs pretty well. I especially like switching to root on the fly for when I just need a little special work. 

I just have a few questions, nothing really earthshaking:

1.I have both lxappearance and obconf installed. So far they both seem to be playing nicely with each other. This won't cause any trouble down the road, will it?
2. I downloaded obmenu, which is supposed to add menu items to the menu. It doesn't add them. Could it be conflicting with something, or maybe I'm just doing something wrong? If there's a menu file it creates, where do I find this?
3. How do I add icons to the desktop for most my used programs? I only have a few, but it would be handy.
4. when I mount some cd's or my memory stick, sometimes there's more than one listing. This isn't a sign of something wrong, is it? Should I just ignore the extras?
5. Tried to switch themes in obconf, and got this error message: When changing themes in Openbox config manager, an error acurred while saving the config file '/openbox/lxde-rc. Why is it fussing?
6. How do I add icon themes, and change them? I found some nice cursor and icon themes, but I don't see them in the config menus.

Other than this, it seems to be quite nice and speedy even with the extra gnome stuff;when I get a little better at linux, I'll try the debian install mentioned earlier. Right now, I'm gonna play with this for a while until I get the hang of it.
Thanks again for all advice!:)

---

### Post by DJiNN on 2008-05-16
> **rolypolycat said:**
> Bwah, ha, ha,! It lives!!:lolflag:
I did a minimal install, tossed lxde on top of it, and aside from a few quirks, it runs pretty well. I especially like switching to root on the fly for when I just need a little special work. 

LOL!! Excellent. LXDE saves another machine! :)

> 1.I have both lxappearance and obconf installed. So far they both seem to be playing nicely with each other. This won't cause any trouble down the road, will it?

I'm not 100% sure, but i think they'll be fine. I've been running LXDE (in several different forms) for a while now, and no problems so far (Apart from the ones that i've created myself by tinkering!) :)

> 2. I downloaded obmenu, which is supposed to add menu items to the menu. It doesn't add them. Could it be conflicting with something, or maybe I'm just doing something wrong? If there's a menu file it creates, where do I find this?

I don't really use the OB menu much when i'm using LXDE, but it's very easy to edit by hand if you only want to put a few things in there. I think you'll find it in ~/.config/openbox. If it's not there then it may well be in /etc/xdg/openbox  or maybe even /etc/xdg/lxde or something like that. I can't remember which one it uses, but a quick look in an editor will tell you. I've just had a quick check on my system, and i "think" it's the one in /etc/xdg/openbox - 

> 3. How do I add icons to the desktop for most my used programs? I only have a few, but it would be handy.

If you're letting pcmanfm control your desktop, then i think just putting the relevant .desktop files (You can find them in /usr/share/applications) into your desktop folder in your /home dir should do the trick. 

> 4. when I mount some cd's or my memory stick, sometimes there's more than one listing. This isn't a sign of something wrong, is it? Should I just ignore the extras?

I get that as well, even when i'm NOT using LXDE.... maybe it's something to do with pymount or ivman or whatever you're running to mount your drives. 

> 5. Tried to switch themes in obconf, and got this error message: When changing themes in Openbox config manager, an error acurred while saving the config file '/openbox/lxde-rc. Why is it fussing?

Never had any probs with obconf so can't help you with that one. Maybe check the r/w properties of the relevant file/folder (ie: /openbox/lxde-rc)

> 6. How do I add icon themes, and change them? I found some nice cursor and icon themes, but I don't see them in the config menus.

You should be able to do this (at least for icons) using lxappearance. The icons need to be copied to either /usr/share/icons (as root) or you could put them in the .icons dir in your /home dir. Not sure about the cursor themes though. 

> Other than this, it seems to be quite nice and speedy even with the extra gnome stuff;when I get a little better at linux, I'll try the debian install mentioned earlier. Right now, I'm gonna play with this for a while until I get the hang of it.
Thanks again for all advice!:)

It's a pretty neat little DE isn't it?..... especially so as it's only in it's early stages. It's a lot lighter than XFCE for sure, and almost as fast as plain old fluxbox. :)

---

### Post by angry_johnnie on 2008-05-17
> **kagashe said:**
> I have installed LXDE in Hardy Heron.

Logout button does not work.

A sort of quick and dirty fix for it is to create a file called lxde-logout.desktop in /usr/share/applications.

Here's what I did:

```
sudo nano /usr/share/applications/lxde-logout.desktop
```

and added this:

```
[Desktop Entry]
Name=Logout
GenericName=logout
Comment=End session
Encoding=UTF-8
Exec=/usr/bin/lxde-logout
Icon=/usr/share/icons/crystalsvg/48x48/actions/exit.png
Terminal=false
Type=Application
Categories=System;
StartupNotify=true
```

Save the file (Ctrl+O) and exit (Ctrl+X).
Then, right-click on the panel and go to:

Add/remove panel items > Panel applets > Application Launch Bar > Edit > Add

then, look for **lxde-logout.desktop** and add it.

There will be a logout button on the panel, and it will work fine :-)


EDIT:  Replace **Icon=/usr/share/icons/crystalsvg/48x48/actions/exit.png** with an icon of your liking.

---

### Post by kagashe on 2008-05-19
Initially I added LXDE to full Ubuntu Hardy install and there was no problem. But I want to make the desktop even lighter, therefore, I am trying to install on Ubuntu Hardy Cli.

When I try to install the meta package lxde it complains of unmet dependencies. Then I am trying to install the dependencies but there are uninstallable dependencies like xscreensaver (there are other few).

I am not interested in trying PUD LXDE version etc. but build my own.

Please help.

kagashe

---

### Post by kagashe on 2008-05-19
> **kagashe said:**
> Initially I added LXDE to full Ubuntu Hardy install and there was no problem. But I want to make the desktop even lighter, therefore, I am trying to install on Ubuntu Hardy Cli.

When I try to install the meta package lxde it complains of unmet dependencies. Then I am trying to install the dependencies but there are uninstallable dependencies like xscreensaver (there are other few).

I am not interested in trying PUD LXDE version etc. but build my own.

Please help.

kagasheI downloaded the following .deb files from Debian and installed them through dpkg:
libnetpbm10_10.0-11.1+etch1_i386.deb
netpbm_10.0-11.1+etch1_i386.deb
xscreensaver_5.04-2_i386.deb

This resolved all dependencies and I could install lxde meta package.

I am happy to install LXDE on Ubuntu Hardy Cli and starting it on Cli through startx. There is a big difference in memory usage compared to LXDE on full Ubuntu install and login through GDM.

Memory usage full Ubuntu install & login through GDM:
	Total 	used	free
Mem:	312	255	56
buffers/cache	74	237

Memory usage Ubuntu Cli and using startx:
	Total 	used	free
Mem:	312	166	146
buffers/cache	44	268

Note: Memory figures are on the desktop with xterm only running.

I recommend it to all Ubuntu LXDE users.

kagashe

---

### Post by kagashe on 2008-05-22
> **PryGuy said:**
> Very cool! Is there a keyboard layout switcher plugin?> $ sudo apt-get install fbxkb
$ fbxkb
It will appear near the clock applet. I don't know how to autostart it on reboot. I don't use any login manager and start lxde through .xinitrc file. I have added fbxkb to the file.

kagashe

---

### Post by PCMan on 2008-05-23
Hi all, we have new apt repository for LXDE now.
There is no update in my personal apt repository for quite a long time because I don't have ubuntu anymore. Ubuntu 8.04 performed poorly on my laptop, and there are a lot of unresolved problems, so I removed ubuntu, and switched to ArchLinux recently.
Fortunately, we found another package maintainer - [michael r < michael.r@spamfreemail.de>]("https://launchpad.net/~michael-r"). He built up a new repo on Launpad PPA of LXDE for us.

For Ubuntu 8.04 hardy
```

deb http://ppa.launchpad.net/lxde/ubuntu hardy main
deb-src http://ppa.launchpad.net/lxde/ubuntu hardy main
```

For Ubuntu 7.10 gutsy
```

deb http://ppa.launchpad.net/lxde/ubuntu gutsy main
deb-src http://ppa.launchpad.net/lxde/ubuntu gutsy main
```

From now on, our official ubuntu repo will be moved to Launchpad PPA service.
Currently, i386, amd64, and lpa packages of the latest LXDE are provided for Hardy. Please upgrade now!!

Alternatively, you can use the repository provided by [Ubuntulite]("http://ubuntulite.tuxfamily.org/") project.
This is a lightweight branch of Ubuntu. They [switched to LXDE in Ubuntulite 0.8 release]("http://ubuntulite.tuxfamily.org/?q=node/96").

Cheers!!

---

### Post by rolypolycat on 2008-05-24
Hi folks!

This desktop rocks! On my 1300 mhz Compaq, it flies!
I have a few questions, though:

1. I can change gtk themes through lxappearance, but not openbox themes through obconf. All the themes are in /usr/share/themes-both openbox and gtk. Why doesn't openbox find it's own themes? It says: "an error accurred while saving the config file: '/openbox/lxde-rc.xml. The problem is, I don't have an '/openbox lxde-rc.xml file in .config. Do I have to make one, then? And how?
2. I installed what gtk themes in the repos I could find. In my home directory, there's a whole bunch of files labeled /gtkrc-tmp-10, or 11 - up to 22, although it skips some numbers. All of these files say the exact same thing:
#THEME AUTO WRITTEN DO NOT EDIT
include "/usr/share/themes/Xeneon/gtk/gtkrc
include '/home/shell/.gtkrc.mine (shell is my username, not the bash shell)
I'm not using the Xeneon theme, either, but Cleanice-Dark.Why do they all say the same thing? Do I need all these files?
I have no .gtkrc.mine directory; do I have to make this, too? Is this why obconf can't find it's files?
3. How do I change the cursor? I found the cursor themes, but theres no dialog to change the cursor. I like a big cursor.
4. If I download any more themes gtk-based, I guess I should put them in the /usr/share directory, so lxappearance will find them?
Thanks for any help. I've tried a few suggestions on this thread and others, but I keep getting error messages not mentioned.
Now if I can just get menumaker to work, since obmenu doesn't add items to it's own menu, I'd be a very happy woman.

---

### Post by chochem on 2008-05-24
The upgrade to pcmanfm in the new repos claims hal as a dependency...? (amongst several other new ones)

As I've recently ditched hal in favour of manual/keyboard-shortcut mounting, this means no more pcmanfm for me, I'm sorry to say. Nevertheless, I'm curious as to the reasons for this dependency - I just checked nautilus and thunar and neither requires it... Pcman?

---

### Post by joninkrakow on 2008-05-24
I tried to install LXDE on U. 7.04, and all kinds of dependency problems. I upgraded it to 7.10, and the same. I finally took it to 8.04, and one last problem. Using the repository given in the first post, for Ubuntu, apt-get claims that LXDE requires pcmanfm 0.3.9.5, but what Ubuntu installs is 0.3.2.2-2--a significantly lower number. So, why does the lxde install for Ubuntu require a version of pcman that I can't install without going to source? And if I try installing from source, will it have depencencies which also require updates? So, my question.... is this something that is fixable? What are the workarounds?

---

### Post by PCMan on 2008-05-24
> **chochem said:**
> The upgrade to pcmanfm in the new repos claims hal as a dependency...? (amongst several other new ones)

As I've recently ditched hal in favour of manual/keyboard-shortcut mounting, this means no more pcmanfm for me, I'm sorry to say. Nevertheless, I'm curious as to the reasons for this dependency - I just checked nautilus and thunar and neither requires it... Pcman?

Nautilus depends on gnome libs such as gnome-vfs/gvfs, and they depends on HAL. Other addons like gnome-volume-manager depends on HAL.

Thunar depends on xfce libraries, such as libexo, and libexo depends on HAL. Also, its thunar-volman depends on HAL.

PCManFM doesn't depend on any external libs from specific desktop, and do all of this itself, so it depends on hal. I think this is quite reasonable.

There is no point in refusing to use HAL. Most of the modern desktop environments need that. Also, performance impact caused by HAL is minimal, and not visible by the users. With HAL the usability of many desktop apps can be improved.

PCManFM can be configured to turn off HAL support, if you build it from source. (pcmanfm-nohal is provided for debian, but in this repo, we didn't build that)

---

### Post by PCMan on 2008-05-24
> **joninkrakow said:**
> I tried to install LXDE on U. 7.04, and all kinds of dependency problems. I upgraded it to 7.10, and the same. I finally took it to 8.04, and one last problem. Using the repository given in the first post, for Ubuntu, apt-get claims that LXDE requires pcmanfm 0.3.9.5, but what Ubuntu installs is 0.3.2.2-2--a significantly lower number. So, why does the lxde install for Ubuntu require a version of pcman that I can't install without going to source? And if I try installing from source, will it have depencencies which also require updates? So, my question.... is this something that is fixable? What are the workarounds?
There should be newer versions in our repo. We just built version 0.4.1.1 and 0.4.4 experimental. The pcmanfm package in Ubuntu is quite old. 0.3.2.2 was released in 2006. Using the official ubuntu package is hence discouraged. Debian has 0.3.6 which was released in 2008 earlier but Ubuntu was freezed due to 8.04 release, so that's the problem.

---

### Post by rolypolycat on 2008-05-24
Hello!

I seem to have a big problem here. I did a manual update of lxpanel through update manager. I also installed a few new themes and ran fslint on only my home directory. But now, I can't delete anything in my home! Even if I change permissions-to read, write, execute- that particular file, it goes through the motions, then says "permission denied". If I don't change permissions, then delete is grayed out on the menu. I have to go into root mode to do anything in my home folder!:(
Would simply using update-manager and updating lxpanel do this?:confused: I tried to re-install in Synaptic, but the options were either greyed out or it needed another version of some other software. 
How do I get my permissions back for my own folder?!
Any help is greatly appreciated!

---

### Post by johnraff on 2008-05-24
> **rolypolycat said:**
> I can't delete anything in my home! Even if I change permissions-to read, write, execute- that particular file, it goes through the motions, then says "permission denied".  I have to go into root mode to do anything in my home folder!
How do I get my permissions back for my own folder?!I'm afraid I can't help you with lxpanel/upgrade issues, but if you just want to get your home folder back, go into root mode again and check who owns the /home/*yourusername* folder. If it's not you, but root or something, change it back to you, and change the permissions, recursively, to give you read write and execute permissions on everything in the folder. Pcmanfm makes this fairly easy (select the folder, right-click, properties, permissions) but you can do it from a terminal too:```

sudo chown -R *yourname*:*yourname*  /home/*yourname*
sudo chmod 770 -R /home/*yourname*
```where *yourname* is your actual user name.

---

### Post by jw5801 on 2008-05-24
> **johnraff said:**
> I'm afraid I can't help you with lxpanel/upgrade issues, but if you just want to get your home folder back, go into root mode again and check who owns the /home/*yourusername* folder. If it's not you, but root or something, change it back to you, and change the permissions, recursively, to give you read write and execute permissions on everything in the folder. Pcmanfm makes this fairly easy (select the folder, right-click, properties, permissions) but you can do it from a terminal too:```

sudo chown -R *yourname*:*yourname*  /home/*yourname*
sudo chmod 770 -R /home/*yourname*
```where *yourname* is your actual user name.

Just to clarify, you DON'T want execute permissions on everything in your home folder, just read and write. The command is the correct one however!

---

### Post by rolypolycat on 2008-05-25
Well, I managed to screw something up grandly. I thought if I re-installed pcmanfm it might fix the home directory problem I was having. Synaptic tells me the version is wrong. I added the new repos to my apt-sources list, and things got really messed up; I couldn't install anything because there was a problem with pcmanfm. So I did a total minimal install with Hardy, added the new repos- and pcmanfm is still screwed up. I couldn't delete what was there, and I couldn't download a version that would work with lxde. It did no good to use the old repos; the install still wouldn't work, or if it did, it got hung up somewhere. No matter what I tried to do, or what program I tried to install, every install hung up on pcmanfm! Finally, since I desperately need a working system, I re-installed Xubuntu Gutsy.:(
I still like LXDE, though, and I'd like to use it, but until the problem in the repos for pcmanfm is fixed, I can't. I'm not really sure what the problem was, either; I think the versions were wrong for pcmanfm and lxde, or some library pcmanfm needs is the wrong version. And it's just no fun re-installing over and over again.
If anyone can tell me why pcmanfm won't install, or why Hardy minimal install doesn't like pcmanfm, I'd be happy to try installing LXDE again. Or if someone can show me any way to do a minimal install without Ubuntu, if that's what's screwing things up.
Right now, I have Gutsy Xubuntu installed. If I add the old Gutsy repo (the one from //people.linux.org, then install lxde, will this give me the setup I had before I added the Hardy repos?  (And screwed everything up royally when I tried to update lxpanel in update manager.)That is, it will download the right version of pcmanfm with the right version of LXDE? I finally got my desktop running again, and I don't want another episode of the file manager that won't go away and won't return. On the other hand, if this fixes everything so I'm at least back where I was when I installed LXDE over a minimal Gutsy install, then I'll try again. If all goes okay, I can just uninstall all of xfce, right? I don't understand why updating one program in the bunch would have caused all the trouble, though, but that's what started it all. Once I did that, then I couldn't do anything in my home folder without being root.My linux fixing skills obviously need some work ;)
Please pardon all the questions; I'm sort of in-between when it comes to my linux knowledge.

---

### Post by TheIdiotThatIsMe on 2008-05-25
> **PCMan said:**
> There should be newer versions in our repo. We just built version 0.4.1.1 and 0.4.4 experimental. The pcmanfm package in Ubuntu is quite old. 0.3.2.2 was released in 2006. Using the official ubuntu package is hence discouraged. Debian has 0.3.6 which was released in 2008 earlier but Ubuntu was freezed due to 8.04 release, so that's the problem.

You can get an updated version of pcmanfm from [www.getdeb.net](www.getdeb.net), although it is listed only for Gutsy you can still install it just fine under hardy.

---

### Post by gajotrengo on 2008-05-25
How can i change screen resolution on lxde?
I cant ind any option.

---

### Post by PrimoTurbo on 2008-05-27
> **gajotrengo said:**
> How can i change screen resolution on lxde?
I cant ind any option.


There is no option to change it, you need to edit your /etc/X11/xorg.conf and set the highest resolution you want to use. Otherwise it defaults to the highest.

Also my Firefox icon doesn't seem to show up in the panel. How do I fix this?

---

### Post by Kowalski_GT-R on 2008-05-27
I opened a thread on LXDE [here]("http://ubuntuforums.org/showthread.php?t=808130&highlight=lxde") in "desktop environments"

maybe forum admins can merge the threads....


still, i cannot download and install LXDE having added the repos in my sources list. Has anyone experienced the same thing?

---

### Post by jw5801 on 2008-05-27
The 64-bit branch of the repo has some interesting packaging:
```
[ ~ ] sudo apt-get install lxde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  lxde: Depends: lxde-common (>= 0.3.2.1-12~lxde) but it is not going to be installed
E: Broken packages
[ ~ ] sudo apt-get install lxde lxde-common 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  lxde-common: Depends: lxde-settings-daemon but it is not going to be installed
E: Broken packages
[ ~ ] sudo apt-get install lxde lxde-common lxde-settings-daemon 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  lxde-settings-daemon: Depends: lxde-common (= 0.3.2.1-11~lxde) but 0.3.2.1-12~lxde is to be installed
E: Broken packages
```

Apparently lxde-settings-daemon depends on a specific (old) version of lxde-common, rather than that version or greater, if this is necessary then lxde-settings-daemon should probably have been updated at the same time as lxde and lxde-common.

---

### Post by rolypolycat on 2008-06-02
Hello!
I'm trying to install LXDE over an xubuntu install. Every time I try to install the lxde meta package, I get this error message:
lxde:
 Depends: gpicview but it is not going to be installed
 Depends: lxappearance but it is not going to be installed
 Depends: lxpanel but it is not going to be installed
 Depends: openbox but it is not going to be installed
 Depends: pcmanfm but it is not going to be installed

Any other component of lxde: lxpanel, lxappearance, gives me messages about libcairo >= what's on my machine. I have the gutsy repos added, because that is the version I'm using of xubuntu, and trying to use with lxde.
I installed pcmanfm, openbox, openbox-themes,fbpanel, gsetroot,obconf(can't seem to find obmenu in synaptic) separately without any problems, but adding anything for lxde just gives error messages. I thought  that lxpanel, lxappearance, etc., could be used independently of lxde? Enabling the hardy repos for lxde still gives the same error messages when I try to install lxpanel or others:
depends: libcairo2(>=1.6.0) but 1.4.10-1ubuntu4.4 is to be installed. (It already is installed)
depends:(libglib2.0-0(>=2.16.0) but 2.14.1-1ubuntu is to be installed (Already there)
depends:(libpango(1.0-0(>=1.20.1)but 1.18.3-0ubuntu is to be installed. (likewise)
 Any idea how to fix this without doing a complete re-install of minimal gutsy or another full xfce install?:confused: 
I like how much faster lxde is on my 1300mhz machine than anything I've tried so far. And can I just uninstall xfce components to get rid of it once I get Openbox set up? (Assuming I can't get lxde working, I'm going to try using Openbox, following Urukrama's guide).
Any help is greatly appreciated!
(sorry about the smilies in the error messages; I'm not sure how they got there??)

---

### Post by brazz43 on 2008-06-02
I installed the PUD distribution on my eeePC. Initially it worked well, I had a nice environment LXDE :). Unfortunately, I wanted to do an upgrade for the latest versions of software ...:( Now, when I started, I did more than wallpaper (which is always beautiful!) With the Home icon and that's all I can run! Have you had this kind of problem or it is I who am cursed :confused: !
Sorry for my bad english!

---

### Post by hotweiss on 2008-06-03
Wow, I'm impressed. LXDE is fast! I'm sticking with it, if I don't have any bugs that bother me to much.

Just 2 problem:

a) after a reboot LXDE cannot find any wireless networks

b) there is not Firefox icon in the menu or in my quicklaunch bar

---

### Post by kagashe on 2008-06-06
I am running lxde on Ubuntu Hardy Cli.

I understand that pcmanfm does not automount the pendrive but displays it in /media folder and it can be mounted by right click.

When I am plugging the pendrive it does not show on pcmanfm /media folder.

I have installed gnome-volume-manager which is supposed to help me mounting the pendrive.

What is missing?

kagashe

---

### Post by rolypolycat on 2008-06-06
I can't seem to install lxde from a command line install. Apt can't find a version of pcmanfm that it likes to use with lxde. However, if I install lxde over a complete xubuntu hardy install (or cli xubuntu gutsy, too), it has no problem finding everything. I added the new repos, but no luck. What's more, when installing from the cli, I can't get apt to stop looking for pcmanfm! Even if I open my sources.list, comment out the lines, it still won't install ANYTHING (and I mean anything) because it gets hung up on a program it isn't even supposed to look for any more!:mad:
I thought I'd try using Openbox by itself, along with thunar, following urukrama's guide, and no matter what I did, it wouldn't install because of pcmanfm. So I finally went back to xubuntu hardy.
I'm a bit puzzled as to why the install is so different when done from a command line, and from a complete installed system. Does anyone know what ubuntu's minimal install cd doesn't have, or doesn't add, that it does for a full install cd? :confused: And with the extra lines commented out of the sources.list, aptitude shouldn't even be able to find that repo, so it shouldn't keep stalling on a program I don't want? Or once I've tried to install something, updated the sources.list, it still has that command in memory or something?
I'm thinking of trying again from my xfce install, but I want to delete xfce afterward. On the other hand, if installing lxde and then removing xfce is going to destroy a working desktop, I'd like to know why and how to avoid all the damage.:(
Any help anyone can give is really appreciated. Right now, I'm just a bit confused as to why the difference with the two types of installations.

---

### Post by kagashe on 2008-06-07
> **rolypolycat said:**
> I can't seem to install lxde from a command line install. Apt can't find a version of pcmanfm that it likes to use with lxde. However, if I install lxde over a complete xubuntu hardy install (or cli xubuntu gutsy, too), it has no problem finding everything. I added the new repos, but no luck. What's more, when installing from the cli, I can't get apt to stop looking for pcmanfm! Even if I open my sources.list, comment out the lines, it still won't install ANYTHING (and I mean anything) because it gets hung up on a program it isn't even supposed to look for any more!:mad:
I thought I'd try using Openbox by itself, along with thunar, following urukrama's guide, and no matter what I did, it wouldn't install because of pcmanfm. So I finally went back to xubuntu hardy.
I'm a bit puzzled as to why the install is so different when done from a command line, and from a complete installed system. Does anyone know what ubuntu's minimal install cd doesn't have, or doesn't add, that it does for a full install cd? :confused: And with the extra lines commented out of the sources.list, aptitude shouldn't even be able to find that repo, so it shouldn't keep stalling on a program I don't want? Or once I've tried to install something, updated the sources.list, it still has that command in memory or something?
I'm thinking of trying again from my xfce install, but I want to delete xfce afterward. On the other hand, if installing lxde and then removing xfce is going to destroy a working desktop, I'd like to know why and how to avoid all the damage.:(
Any help anyone can give is really appreciated. Right now, I'm just a bit confused as to why the difference with the two types of installations.I have installed LXDE on Hardy Cli and here is [my post]("http://ubuntuforums.org/showpost.php?p=4993178&postcount=101") describing it on this thread.

I downloaded some .deb packages from Debian repository and installed them to satisfy the dependencies.

Please see whether it helps you.

kagashe

---

### Post by rolypolycat on 2008-06-07
Hi!
Thank you for the tip; I'll try another install later. Just to be sure, can I just download those packages, or do I need to add the debian repos, too?
And can I do a dual boot with the new install if it goes well, later removing the xubuntu install? I assume repartioning would wipe it out, but spare the new lxde install. What program would be best for this job for a person with moderate partitioning knowledge? Or does anyone reccommend another, better way to do the install without trashing my working xubuntu desktop, until I'm ready to remove it for lxde?
Thanks for any advice!

---

### Post by kagashe on 2008-06-07
> **rolypolycat said:**
> Hi!
Thank you for the tip; I'll try another install later. Just to be sure, can I just download those packages, or do I need to add the debian repos, too?
And can I do a dual boot with the new install if it goes well, later removing the xubuntu install? I assume repartioning would wipe it out, but spare the new lxde install. What program would be best for this job for a person with moderate partitioning knowledge? Or does anyone reccommend another, better way to do the install without trashing my working xubuntu desktop, until I'm ready to remove it for lxde?
Thanks for any advice!I did not add the Debian repo, downloaded the .deb and installed through dpkg.

Yes. You can do dual boot install with xubuntu. If you have to create new partition by resizing the partition of existing xubuntu install, I suggest you install gparted and do the partitioning in existing xubuntu.

kagashe

---

### Post by starpause on 2008-06-21
i'm always excited to see another light weight desktop solution out there so i gave LXDE a go on my eee 701. 

it's snappier than XFCE but the pannel handling in XFCE is much nicer. i really like XFCE's floating pannels that don't limit the size of your windows (a big deal on the tiny screen of an eee). the XFCE panels are also more mature with many plugins/items written for them. 

the other thing XFCE does better than LXDE is keyboard hotkeys. even though XFCE has a strange way of doing window manager shortcuts differently than other shortcuts, they are quite easy to set and behave like you would expect.

anyway, i hope that LXDE continues to mature and addresses some of these issues!

---

### Post by firmit on 2008-06-22
> **starpause said:**
> 
the other thing XFCE does better than LXDE is keyboard hotkeys. even though XFCE has a strange way of doing window manager shortcuts differently than other shortcuts, they are quite easy to set and behave like you would expect.


LXDE handles keyboard shortcuts quite well, I think - given that OPENBOX is very configurable and does this for you. Or did you mean something else?

---

### Post by starpause on 2008-06-23
> **firmit said:**
> LXDE handles keyboard shortcuts quite well, I think - given that OPENBOX is very configurable and does this for you. Or did you mean something else?

yes, more explicitly: i prefer xfce's graphical configuration for keyboard shortcuts. it's very intuitive to highlight an action, hit edit, then touch the keys you want to perform the action. it especially saves me time when i'm trying to figure out what they keyword is for the windows, menu, and nested function keys on my laptop.

that said, xfce isn't quite as nice and configurable as KDE and the applications people write to fit in with it. 

and of all the *box WM, i do like openbox the best. it seems like LXDE has a good direction and i hope the project thrives!

---

### Post by known on 2008-06-27
I have installed LXDE on my Hardy Heron (8.04)laptop. 
It is working fine.

Please let me know what all packages I can remove safely from default 8.04 installation.

I also wanted to disable any unwanted daemons to keep the system as light as possible.
 
Please guide me.

---

### Post by joninkrakow on 2008-06-27
> **known said:**
> I have installed LXDE on my Hardy Heron (8.04)laptop. 
It is working fine.

Please let me know what all packages I can remove safely from default 8.04 installation.

I also wanted to disable any unwanted daemons to keep the system as light as possible.
 
Please guide me.


Make that two of us... :-D I would love to know what's running, and what I could let go. I only have Xubuntu, though, and am not sure how to turn things off, nor what packages to uninstall. I've looked, but haven't found anything like Gnome's tools.

-Jon

---

### Post by firmit on 2008-06-27
> **known said:**
> I have installed LXDE on my Hardy Heron (8.04)laptop. 
It is working fine.

Please let me know what all packages I can remove safely from default 8.04 installation.

I also wanted to disable any unwanted daemons to keep the system as light as possible.
 
Please guide me.

My tip - is to download the 8.04 alternativ install cd - install only a command line system - add the repo to lxde, and apt-get. Then you will have a fresh install with minimal software and daemons (like update-manager etc). However, I found that the 8.04 is somewhat bloated - if you plan on doing this, I would rather use debian lenny. But - instead of 8.04, I would choose 7.10 which is lighter - either probably works just fine :)

---

### Post by known on 2008-06-27
> **joninkrakow said:**
> Make that two of us... :-D I would love to know what's running, and what I could let go. I only have Xubuntu, though, and am not sure how to turn things off, nor what packages to uninstall. I've looked, but haven't found anything like Gnome's tools.

-Jon

This page has some useful tips.

[http://www.ubuntu-unleashed.com/2007/09/howto-speed-up-ubuntu-boot-process-way.html](http://www.ubuntu-unleashed.com/2007/09/howto-speed-up-ubuntu-boot-process-way.html)

---

### Post by firmit on 2008-06-28
> **known said:**
> This page has some useful tips.

[http://www.ubuntu-unleashed.com/2007/09/howto-speed-up-ubuntu-boot-process-way.html](http://www.ubuntu-unleashed.com/2007/09/howto-speed-up-ubuntu-boot-process-way.html)

Sure - but for new-linux-ubuntu users - be sure to read and understand what it is you are doing in case something goes wrong. But great tip :)

---

### Post by known on 2008-07-05
Some more tips
[http://wiki.dennyhalim.com/ubuntu-minimal-desktop](http://wiki.dennyhalim.com/ubuntu-minimal-desktop)

---

### Post by El Flavio on 2008-07-06
I'm in sort of a pickle. I was playing around with the desktop settings and clicked something like "no icons on desktop" or something and now i have a black wallpaper and no icons and can no longer right click on my desktop. how do i get icons and wallpaper back on my desktop???:confused:

---

### Post by smartboyathome on 2008-07-06
> **El Flavio said:**
> I'm in sort of a pickle. I was playing around with the desktop settings and clicked something like "no icons on desktop" or something and now i have a black wallpaper and no icons and can no longer right click on my desktop. how do i get icons and wallpaper back on my desktop???:confused:

Run pcmanfm, then go to Edit, Preferences, Desktop, and check Show file icons on desktop.

---

### Post by believe it or not on 2008-07-06
> **mrgnash said:**
> Lubuntu?
i like that idea

---

### Post by smartboyathome on 2008-07-06
You can't use the "ubuntu" or "buntu" names if you are making an LXDE-based Ubuntu, as it uses external repos. You may only use it if you are using stuff from the official repos.

---

### Post by El Flavio on 2008-07-07
> **smartboyathome said:**
> Run pcmanfm, then go to Edit, Preferences, Desktop, and check Show file icons on desktop.

Thank you! I would of never figured that out : )

---

### Post by RATM_Owns on 2008-07-07
Well we should make some Lubuntu.
(Me wants some Lubuntu)

It's a great idea.

---

### Post by keiichidono on 2008-07-07
I would totally download Lubuntu if someone took the time to make it, i might go for it myself if no one picks up the idea.

---

### Post by PCMan on 2008-07-07
> **CalvinB said:**
> I would totally download Lubuntu if someone took the time to make it, i might go for it myself if no one picks up the idea.

Isn't the existing Ubuntulite enough? It's one of the ubuntu derivatives, and it uses LXDE now.

Most of the LXDE packages are now entering Debian official repository.
So, there are chances that they can enter the ubuntu repo in next release.
If anyone want to make a new distro with them, please go ahead.

Comprehensive documentation for LXDE is now provided in our wiki.
[http://lxde.org/wiki/](http://lxde.org/wiki/)
There are much useful info regarding configuration.

It's not completed yet, but we are already working on it to get all details fully-documented for users, packagers, and distribution makers.
Please help editing the wiki, if you find something missing or incorrect in it.

---

### Post by PCMan on 2008-07-07
> **CalvinB said:**
> I would totally download Lubuntu if someone took the time to make it, i might go for it myself if no one picks up the idea.

Isn't the existing Ubuntulite enough? It's one of the ubuntu derivatives, and it uses LXDE now.

Most of the LXDE packages are now entering Debian official repository.
So, there are chances that they can enter the ubuntu repo in next release.
If anyone want to make a new distro with them, please go ahead.

Comprehensive documentation for LXDE is now provided in our wiki.
[http://lxde.org/wiki/](http://lxde.org/wiki/)
There are much useful info regarding to configuration.

It's not completed yet, but we are already working on it to get all details fully-documented for users, packagers, and distribution makers.
Please help editing the wiki, if you find something missing or incorrect in it.

---

### Post by keiichidono on 2008-07-07
I haven't really tried out Ubuntulite, i might give it a shot to see how far along they are. If i don't like how far along they are then i might create my own project

---

### Post by kagashe on 2008-07-09
I had installed lxde on Ubuntu Hardy command line earlier but certain things did not work like mounting of partitions, icons on application launcher.

Today I discovered another way of installing lxde on minimum Ubuntu and it is full proof and it works.

1. Install complete Ubuntu Hardy Heron.
2. Add lxde and login to it.
3. Remove Gnome completely through the following command:
> $ sudo apt-get remove alacarte bluez-gnome brltty brltty-x11 bug-buddy capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet diveintopython ekiga eog espeak evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet firefox-3.0-gnome-support firefox-gnome-support gconf-editor gedit gedit-common gimp-gnomevfs gimp-python gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data gnome-doc-utils gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-settings-daemon gnome-spell gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-tools gtkhtml3.14 gvfs gvfs-backends gvfs-fuse hwtest hwtest-gtk launchpad-integration libalut0 libao2 libarchive1 libart2.0-cil libcdio-cdda0 libcdio-paranoia0 libcompizconfig0 libcurl3 libdecoration0 libdeskbar-tracker libdirectfb-1.0-0 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libglade2.0-cil libglew1.5 libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgnomevfs2-extra libgpgme11 libgpod-common libgpod3 libgtk2.0-cil libgtkhtml3.14-19 libgtkhtml3.16-cil libgtksourceview2.0-0 libgtksourceview2.0-common libgvfscommon0 libgweather-common libgweather1 libicu38 liblpint-bonobo0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmtp7 libmusicbrainz4c2a libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libopal-2.2 libopenal0a libopenobex1 libpam-gnome-keyring libpisock9 libpisync1 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpth20 libpulsecore5 librarian0 libsamplerate0 libsdl1.2debian libsdl1.2debian-alsa libsgutils1 libsmbclient libsoup2.4-1 libsqlite0 libtracker-gtk0 libvorbisfile3 libwpg-0.1-1 libwps-0.1-1 libx11-xcb1 libxml2-utils mesa-utils metacity mono-common mono-gac mono-jit mono-runtime mousetweaks nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share o3read obex-data-server openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-style-human openoffice.org-writer pkg-config pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 python-gmenu python-gtksourceview2 python-uno rdesktop rhythmbox rss-glx scim-bridge-agent scim-bridge-client-gtk seahorse sound-juicer sqlite sqlite3 ssh-askpass-gnome tangerine-icon-theme tomboy totem-mozilla tracker tracker-search-tool tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-sounds usplash-theme-ubuntu vino whois xdg-user-dirs xdg-user-dirs-gtk xsane xsane-common xsltproc xulrunner-1.9-gnome-support yelp
The command has been copied from [psychocats.net]("http://psychocats.net/ubuntu/purexfce").

kagashe

---

### Post by firmit on 2008-07-09
> **kagashe said:**
> I had installed lxde on Ubuntu Hardy command line earlier but things like mounting of partitions through pcamnfm did not work.

Today I discovered another way of installing lxde on minimum Ubuntu and it is full proof and it works.

1. Install complete Ubuntu Hardy Heron.
2. Add lxde and login to it.
3. Remove Gnome completely through the following command:

The command has been copied from [psychocats.net]("http://psychocats.net/ubuntu/purexfce").

kagashe

I really feel this is somewhat unnecessary. Make sure you also have HAL installed when you install CLI-only. PCManfm needs HAL to mount on demand. If you need automounting in CLI - you'd also need ivman. Regarding partitions - you may need to edit your /etc/fstab. I have no trouble with partitions - infact, I want them gone :)

There should not be this much trouble installing LXDE - have you checked out lxde.org/wiki?

---

### Post by kagashe on 2008-07-09
> **firmit said:**
> I really feel this is somewhat unnecessary. Make sure you also have HAL installed when you install CLI-only. PCManfm needs HAL to mount on demand. If you need automounting in CLI - you'd also need ivman. Regarding partitions - you may need to edit your /etc/fstab. I have no trouble with partitions - infact, I want them gone :)

There should not be this much trouble installing LXDE - have you checked out lxde.org/wiki?Yes. I have HAL installed and it does not work. Please reply to my post on [this thread]("http://ubuntuforums.org/showthread.php?t=853156") providing solution and I can test it since I still have that installation on another partition. I don't need automounting but it should mount on double click.

Moreover, I faced dependencies problem trying to install lxde on Ubuntu Hardy Cli. I had to get those dependencies from Debian. I have posted about it [elsewhere on this thread]("http://ubuntuforums.org/showpost.php?p=4993178&postcount=101"). There is no solution provided for the dependencies on the wiki.

There is no harm if 245 Gnome packages are removed through a single command as described above if it gives fully working lxde desktop.

kagashe

---

### Post by fluteflute on 2008-07-09
> **PCMan said:**
> Most of the LXDE packages are now entering Debian official repository.
So, there are chances that they can enter the ubuntu repo in next release.
LXDE is now in the Ubuntu Intrepid repository.

---

### Post by graabein on 2008-07-23
I got Xubuntu running at home and installed LXDE along side it. LXDE is now my default session over Xfce. I love it! Thanks for the great work!

---

### Post by joninkrakow on 2008-07-23
I've been loving and enjoying LXDE, but this past weekend, a test run of another distro from CD somehow scrambled a part of my hard drive, taking out the config files from /etc/xdg, and who knows where else. I tried completely uninstalling lxde, and re-installing it, but this hasn't repopulated this directory, and I still can't launch lxde. It just dies out, and brings me back to gdm. BTW, I also lost xfce in this scrambling. Fortunately, I still have icewm. ;-) Anybody have any ideas how to get lxde running again?

Maybe this is something to look into so one doesn't get locked out if config files get scrambled/removed accidently.

-Jon

---

### Post by jittopjose on 2008-07-26
i installed lxde on my hardy system. its really nice DE. i love it lot... its cool fast and eyecandy. lots of problems are still there. but i hope the development team will sort it all shortly. any way nice work. i wish if there is a lxde based ubuntu something like  Lubuntu.....:)
thanks
jittos....

---

### Post by sengines on 2008-07-27
How do you get the window list aka taskbar to show icons? I've been at this all week but can't find the workaround I compiled the latest LXPanel 0.3.8.1

---

### Post by knedlyk on 2008-08-11
Hi,
LXDE is the best I ever seen, but lxpanel doesn't resume after hibernation. I need manually start it from console: lxpanel -p LXDE &. Is there any way for fully restore hibernated session? Or maybe it is my local bug...

---

### Post by wersdaluv on 2008-08-11
How do I change my screen resolution on LXDE? The resoultion is too big.

---

### Post by knedlyk on 2008-08-11
> **wersdaluv said:**
> How do I change my screen resolution on LXDE? The resoultion is too big.

Answer is there: [http://ubuntulite.tuxfamily.org/?q=node/144](http://ubuntulite.tuxfamily.org/?q=node/144)

---

### Post by known on 2008-08-11
Can someone please share the output of pkgs installed for Ubuntu (minimal) + LXDE
 
 ```
dpkg-query --show --showformat='${Package;-50}\t${Installed-Size}\t${Status}\n' | sort -k 2 -n | grep "install ok installed" | awk '{print    f "%.3f MB \t %s\n", $2/(1024), $1}'
 
```

---

### Post by mikjp on 2008-08-11
I like LXDE, too. Just wrote about it a review in my blog :-)

mikko

---

### Post by OZFive on 2008-08-11
Hello!   I installed LXDE on my old desktop (Current laptop is backing up all data, it is having some hard drive issues) and must say it is pretty responsive and pretty easy to coinfigure.  

The one issue I am really having so far is the volume control.  The applet for the LXPanel is not working controlling the volume at all.  It blasts sound out at full volume every time and I have to control each sound source individually.  

Any ideas?

---

### Post by knedlyk on 2008-08-11
Yeap, volume control dosn't control all mixer's features. Did you try alsamixer? As for now it is only way to control fully sound. I use it, but waiting for normal volume conrol applet.

---

### Post by oni5115 on 2008-08-13
I can't seem to install it at all yet (Gutsy), I tried adding the launchpad deb section, but it won't install due to dependency issues with pcmanfm, gpicview, lxpanel, and maybe another that I forgot.

Will the gutsy repos be fixed, or will I have to find the .debs from the previous posts?  (Or install from source?)

On a side note:  Does this work well (or at all) with Fluxbox?  Are there any guides to setting up lxde with fluxbox as opposed to openbox?

---

### Post by joninkrakow on 2008-08-14
> **oni5115 said:**
> I can't seem to install it at all yet (Gutsy), I tried adding the launchpad deb section, but it won't install due to dependency issues with pcmanfm, gpicview, lxpanel, and maybe another that I forgot.

Will the gutsy repos be fixed, or will I have to find the .debs from the previous posts?  (Or install from source?)

On a side note:  Does this work well (or at all) with Fluxbox?  Are there any guides to setting up lxde with fluxbox as opposed to openbox?

Are you using the sources given in the first post? If so, I think those won't work. The proper ones are posted later and on the LXDE home page. Also, on the LXDE site, you can find instructions for changing the WM to whatever you want, and I think Fluxbox should work. 

If I'm wrong on either of thsee points, I hope my being wrong prompts a correct answer. ;-)

-Jon
longing to use LXDE again

---

### Post by RiceMonster on 2008-08-14
Honestly, LXDE feels like someone took openbox and made it suck. That said, I like to use lxappearance with openbox, so I'll give them credit for that.

---

### Post by oni5115 on 2008-08-14
> **joninkrakow said:**
> Are you using the sources given in the first post? If so, I think those won't work. The proper ones are posted later and on the LXDE home page. Also, on the LXDE site, you can find instructions for changing the WM to whatever you want, and I think Fluxbox should work. 

If I'm wrong on either of thsee points, I hope my being wrong prompts a correct answer. ;-)

-Jon
longing to use LXDE again

Followed:
[http://lxde.org/wiki/Ubuntu](http://lxde.org/wiki/Ubuntu)

The repos have broken dependencies, at least for gutsy. They do however work for hardy  However, LXPanel didn't seem to load at all.  I got loaded into a nice looking background... with no 'task bar' or way to open a terminal.  :(   This is a cli install of hardy, so no gnome.  I just ran install xorg gdm lxde and the above is what I got on login.  GDM also complained about not having a theme.  :lolflag:

---

### Post by sigmabetatooth on 2008-08-17
> **orduek said:**
> OK. I installed it on a old PIII celeron 700 with 300mb RAM.
Only problem is I can't connect to the wireless network in my house (even after installing ndiswrapper)  - on the same computer running Xubuntu I have no such problem.
I'm also having issues with wifi.  Running hardy haron on a compaq presario c7000 with an atheros card which was working just fine with madwifi drivers.  The wireless worked the first time I switched over to LXDE.  After that... no dice.  I've seen a number of folks on here commenting on wifi issues but everyone just seems to say "it's just a window manager" so it shouldn't mess with your wifi, but we can't all be crazy.  Or can we :confused:  Any help would be much appreciated.

---

### Post by FlyingIsFun1217 on 2008-08-17
If you are having troubles with your wireless, check out wicd. The default install uses network-manager, which seems to be gnome only. Wicd seems to work wonders with it for me ;)

FlyingIsFun1217

---

### Post by mips on 2008-08-21
> **chucky chuckaluck said:**
> very nice looking. clean and pretty. would you happen to have another video of it (that one looks like it was shot on a dirt road)?

[http://video.google.com/videoplay?docid=2851202765906830953&vt=lf&hl=en](http://video.google.com/videoplay?docid=2851202765906830953&vt=lf&hl=en)
[http://video.google.com/videoplay?docid=-4441355406782684570&vt=lf&hl=en](http://video.google.com/videoplay?docid=-4441355406782684570&vt=lf&hl=en)

---

### Post by oni5115 on 2008-08-21
I managed to get it installed on my good laptop just fine, but I can't seem to get audio working at all.  Any way to get pulse audio working?  I tried following:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739) 

Neither seemed to work right for me as I don't have gnome and can't exactly go to System>Preferences>Sound.   =/

Tried both lxde and ubuntulight just to see if either worked right, and neither seem to have sound for me.

---

### Post by LossLess on 2008-08-22
This has already completely changed my Ubuntu experience. Thank you so much. I'd do that "Thank" thing but I haven't figured out how it works yet. I'm replying now from my LXDE environment, and I'm loving it! I use Ubuntu in a VirtualBox VM, primarily, and it could get a little long in the response time tooth, this is tremendously better!

---

### Post by kagashe on 2008-08-22
> **LossLess said:**
> This has already completely changed my Ubuntu experience. Thank you so much. I'd do that "Thank" thing but I haven't figured out how it works yet. I'm replying now from my LXDE environment, and I'm loving it! I use Ubuntu in a VirtualBox VM, primarily, and it could get a little long in the response time tooth, this is tremendously better!
There is an icon (with yellow star) on right hand bottom corner of every post. When you click on that icon you thank that poster. The icon does not appear on your own posts so that you can't thank yourself.

kagashe

---

### Post by oni5115 on 2008-08-23
> **kagashe said:**
> I had installed lxde on Ubuntu Hardy command line earlier but certain things did not work like mounting of partitions, icons on application launcher.

Today I discovered another way of installing lxde on minimum Ubuntu and it is full proof and it works.

1. Install complete Ubuntu Hardy Heron.
2. Add lxde and login to it.
3. Remove Gnome completely through the following command:

The command has been copied from [psychocats.net]("http://psychocats.net/ubuntu/purexfce").

kagashe

By doing this, were you able to get a working pulseaudio at all?  I've tried a lot of things so far and I just can't seem to get pulseaudio working with LXDE - it looks right, pulseaudio volume meter was even showing audio - but no sound at all.  I've re-installed numerous times trying different things cli, normal, etc.  Only time I ever had any sound so far with standard ubuntu desktop installed.

Update:
Well, I did a fresh install of ubuntu from the hardy normal cd, and installed LXDE over it.  Working perfectly, I had to manually start pulseaudio -D and padevchooser, but I'm sure I can find out to make them auto start on reboots.  I guess my only question now is, did sound still work for you after you manually removed all of ubuntu-desktop?  I've installed a dozen times in the past day or two, and really just rather leave it be if it's gonna explode (again).  lol   However, the system at the moment takes about 100-110 Mb, and I know on a clean install it was about 50-70 Mb.  =/   Oh well, it's still ~100 Mb lower than XFCE or Gnome.

---

### Post by kagashe on 2008-08-23
> **oni5115 said:**
> By doing this, were you able to get a working pulseaudio at all?If you go through the long command you will notice that following packages are getting removed:
> pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11I think this removes the pulseaudio itself.
> did sound still work for you after you manually removed all of ubuntu-desktop?Yes. It works, pulseaudio or no pulseaudio.

kagashe

---

### Post by oni5115 on 2008-08-23
Glad to hear that audio should still work if I do decide to remove gnome - though I might have to reinstall pulseaudio, not too difficult.  =)

So far even with gnome, LXDE is amazing... ~90-110 Mb on idle vs. 160-180 in XFCE or ~170-190 on Gnome.  Not to mention it runs faster.  

I do hope future versions work better with conky. I got it finally working, but it minimizes when I use the 'show desktop' button - even with the sticky window hint.  =/  I often use the show desktop buton to see conky, so it sort of defeats the whole purpose.  :lolflag:  Maybe there is a key binding (or I can make one) to force a window to be sticky? (or does openbox just not support that?)

Is there is a way to edit the 'start' menu.  So far it doesn't have wine, or its sub applications on the menu.  It also isn't in alphabetical order - which is just a minor annoyance.  I haven't been able to find the config file for the actual menu entires yet.  If I right click the menu it brings up a menu with "Menu Settings" grayed out, I assume there is a package I am missing - or it is a planned feature for future releases?

If you have xcompmgr/transset can you make an application auto start to a certain transparency level? (for example - slightly transparent terminals)

So far it is really awesome, and I'd love to see an official lobuntu - as in low resource ubuntu.  LXDE is definitely way less resources than XFCE or Gnome.

---

### Post by RiceMonster on 2008-08-23
> **oni5115 said:**
> I do hope future versions work better with conky. I got it finally working, but it minimizes when I use the 'show desktop' button - even with the sticky window hint.  =/  I often use the show desktop buton to see conky, so it sort of defeats the whole purpose.  :lolflag:  Maybe there is a key binding (or I can make one) to force a window to be sticky? (or does openbox just not support that?)

It's probably whatever is drawing the desktop in LXDE. Conky works just fine with Openbox.

---

### Post by oni5115 on 2008-08-23
It is PCmanFM that is doing, but I do like PCManFM, so I'm hoping future versions of it are more conky friendly.

---

### Post by pikaia on 2008-09-17
Ok.

So far I'm really impressed with the LXDE.  It really flies on my old thinkpad.  However, (you knew that was coming right) I can't get lxappearance to see any other themes that are installed.  I don't even see an 'Add' option.  Is there a config file?  It currently only has Raleigh listed as availabe themes, however I have several themes in the share/themes folder.  

BTW, I did a Hardy CLi and added LXDE.  

Also I accidently clicked the 'show menu when desktop is clicked' and now can't figure out how to restore the desktop settings menu... any help?  Is there a way to replace change the xterm launcher on the panel to mrxvt?  I've tried several times to add it or change the one currently on there, but no luck so far.

Thanks

---

### Post by firmit on 2008-09-18
For those experiencing difficulties with LXDE - a new site is up. They converted to a new wiki, and have started a forum++. The wiki is not yet up-to-date, but it will be. You may also try to post you LXDE problems there.

[http://wiki.lxde.org](http://wiki.lxde.org)
[http://forum.lxde.org](http://forum.lxde.org)

---

### Post by Lonthong on 2008-09-19
> **pikaia said:**
> 
So far I'm really impressed with the LXDE.  It really flies on my old thinkpad.  However, (you knew that was coming right) I can't get lxappearance to see any other themes that are installed.  I don't even see an 'Add' option.  Is there a config file?  It currently only has Raleigh listed as availabe themes, however I have several themes in the share/themes folder.

Those window themes belong to obconf. You must install obconf if you haven't done it before

> 
Also I accidently clicked the 'show menu when desktop is clicked' and now can't figure out how to restore the desktop settings menu... any help?  Is there a way to replace change the xterm launcher on the panel to mrxvt?  I've tried several times to add it or change the one currently on there, but no luck so far.
Thanks

pcmanfm - edit - prefences - desktop - untick: show menu provided by....

right click on launch bar - remove xterm entry - add mrxvt
however, you must have mrxvt.desktop in /usr/share/applications
if not, you can just simply copy the entry for xterm (it can be opened with any text editor) and adjust the command, replace the name, edit "exec=" to execute mrxvt, make sure "icon=" pointing to the right icon.

On a separate note, you can fix entries in the menu with no icon by editing its relevant "entry.desktop". Just provide "icon=" the right path to the relevant icon

---

### Post by tgellen on 2008-10-13
I'm setting up a test LXDE environment on my laptop and was wondering if there is any way to organise the menu alphabetically? 

In the screenshot [http://lxde.org/sites/default/files/images/lxpanel_menu.thumbnail.png](http://lxde.org/sites/default/files/images/lxpanel_menu.thumbnail.png) all the subitems are alphabetically arranged but the main menu items are not i.e. the first menu item is Games instead of Accesories. Any ideas?

---

### Post by firmit on 2008-10-13
> **tgellen said:**
> I'm setting up a test LXDE environment on my laptop and was wondering if there is any way to organise the menu alphabetically? 

In the screenshot [http://lxde.org/sites/default/files/images/lxpanel_menu.thumbnail.png](http://lxde.org/sites/default/files/images/lxpanel_menu.thumbnail.png) all the subitems are alphabetically arranged but the main menu items are not i.e. the first menu item is Games instead of Accesories. Any ideas?

This is a good question. After I installed geany and glade interface designer, the Development tab appeared in my menu - as number 2 from the top - but Game with Freecol was on top... Go figure. Maybe it's arranged alphabetically in the native language of the developers...

I will ask the LXDE-list and get back to you.

FYI:
Also - you should be aware of the official lxde site: lxde.org - they now have a wiki and a forum, including the lxde-list on sourceforge, as their official channels.

---

### Post by Shippou on 2008-10-13
Cool man!

When I installed it today it only asked to download 7386kB...

It really IS small..

---

### Post by firmit on 2008-10-13
> **Shippou said:**
> Cool man!

When I installed it today it only asked to download 7386kB...

It really IS small..

And that was with the recommended appz I guess?

Try
```
sudo aptitude install lxde --without-recommends 
```

It should be even smaller now ;)

---

### Post by Mark76 on 2008-10-26
I downloaded and installed lxpanel from the debian repositories.  I like it, but I notice that right click menu settings options for show desktop, menu, pager, cpu usage monitor and volume control and all greyed out; as can be seen from the screenshot attached

---

### Post by johnnybirdman on 2008-10-27
Thanks for this.  Was using/testing xubuntu II 8.10 on an old Dell Cpxj 650mhz and was okay but with LXDE there seems to be an great increase in the DE response time.  Added the II repo, apt-get install and worked like a charm, no problems.
Thanks again.
J.

---

### Post by rtom on 2008-10-28
I guess you need some more packages: to cpu usage monitor probably lmsensor, to volume control volumecontrol.app and so on. Search the debian repo for further packages.

---

### Post by Mark76 on 2008-10-28
There doesn't seem to be a package called lmsensor in the repos.

Ah. You forgot the -, it's lm-sensors

And I already have it installed.

---

### Post by jjgomera on 2008-10-28
lm-sensors installed and working, what do you have in a console with the command **sensors**?
if noone, try to detect sensors with:
**sudo sensors-detect**

---

### Post by Mark76 on 2008-10-28
If I run the command "sensors" in a terminal I get

> k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +20.0 C                                    
Core0 Temp:  +12.0 C                                    
Core1 Temp:  +19.0 C                                    
Core1 Temp:   +8.0 C      

Which seems to indicate it's working just fine

---

### Post by rtom on 2008-10-30
Do you have sensor-applet or such a think in the repo? I guess the problem is that you installed only lxpanel, which has not installed all the dependencies.

What repo are you using at all?

---

### Post by picpak on 2008-12-15
I've made debs for LXPanel 0.4.0 beta below. Enjoy!

---

### Post by dannytatom on 2008-12-15
I installed this last night, and it's pretty cool.  I'm having a couple problems, though.

1) When I log off and back in, it loads my old panel config (that I screwed up) instead of loading the new (not messed up) one.

2) Same with openbox.  It loads the default openbox config, even though the only one in /home/user/.config/openbox/ is the one I made.  

If I kill openbox or lxpanel and restart them, it works fine, they just won't start right by themselves.

What's the deal? :(

**Edit:** Also, thanks for the new debs. :)

---

### Post by sloggerkhan on 2008-12-15
I like lxde quite a bit, but haven't used it regularly because I don't like the level of customization and config file hacking needed to get an install nice.

Still, it's defaults do evolve pretty well. The first time I tried it it didn't even work with network manager or have an effective network applet.

I'm a particular fan of the LX Launcher [http://wiki.lxde.org/en/LXLauncher](http://wiki.lxde.org/en/LXLauncher) .
What I'd really like to see is a verticaly oriented variant of the LXpanel.

---

### Post by SomeGuyDude on 2008-12-15
Did you try Wicd?

Anyway, LXDE is what got me into Openbox. It's an excellently full-featured DE that keeps things light, and it's got a few things I can't part with:

- LXTerminal
- LXAppearance
- LXTask

Also, PCManFM is the best filemanager, bar none. Nautilus destroys my system resources, Thunar lacks tabs and a few other things, ROX just looks ugly as sin.

---

### Post by Changturkey on 2008-12-15
Gonna give this a try. Looks awesome.

---

### Post by CJ Master on 2008-12-15
Hello,

Love this de! You did a great job!

Just quick questions though, is it possible to add the "Applications, places, system" thing on the LXDE bar, and what about Add/remove programs?

---

### Post by jimi_hendrix on 2008-12-15
themes?

or just that default?

---

### Post by bigbrovar on 2008-12-16
i love lxde but one thing that keeps me from it is the network manager that comes with it by default. its very limited and makes it hard to configure your network. is there a way to make it use wicd on ubuntu?

---

### Post by dannytatom on 2008-12-16
I use the gnome network manager and it works fine, doesn't hog any extra resources or anything.

---

### Post by bigbrovar on 2008-12-16
> **dannytatom said:**
> I use the gnome network manager and it works fine, doesn't hog any extra resources or anything.

how were you able to do that.. i found it impossible to add the gnome network manager to the lxde panel. or am i missing something?

---

### Post by dannytatom on 2008-12-16
Well I installed lxde on top of Ubuntu without installing the lxnm package, then used the "Remove Ubuntu" longasscommand from [here]("http://http://www.psychocats.net/ubuntu/purekde") (keeping a few things like synaptic, update manager, etc) to get rid of gnome.

Logged out, logged back in, and it was using the gnome network manager by default.

So, really, I have no idea WHY it does it.  But, that's how it got that way, and it works for me. :P

---

### Post by jw5801 on 2008-12-16
> **bigbrovar said:**
> i love lxde but one thing that keeps me from it is the network manager that comes with it by default. its very limited and makes it hard to configure your network. is there a way to make it use wicd on ubuntu?

```
echo "deb http://apt.wicd.net intrepid extras" | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update && sudo apt-get install wicd
```

Should be about all you need to get wicd up and running. It is a most excellent wireless manager.

---

### Post by elitefox on 2009-01-26
Yup all I can say is it is very very lightweight on the system as I installed it in my Intrepid Ibex server... The only reason that I want a gui is because of synaptic manager, gives a good list of apps. ok no synaptic at least a terminal... oh no terminal, darn I can't find it, run is not responsive... then again went to reformating and having a fresh installed intrepid :popcorn:

I just realize then how important command line is though.:D


P.S. Nice gui and very resource efficient though the following apps that I want aren't there just that... any ways to fix this?

---

### Post by manilaph on 2009-02-18
i still believe in having a remastered lxde+ubuntu = lxbuntu or lubuntu

it will take away all the necessary configurations.

by the way, have you seen this other[ LXDE distro]("http://cap.gediam.de/index-en.htm")

---

### Post by adamlau on 2009-02-18
I'll start using PCMan File Manager when 'My Documents' can be hidden and when it starts supporting customizeable actions (ala Thunar).

---

### Post by Mark76 on 2009-02-18
/home/you/.My Documents not working?

What are customizable actions?

---

### Post by DeusEx on 2009-02-19
I am amazed by LXDE! I have it installed next to my Gnome+Compiz Ubuntu installation which was running a bit slow. LXDE seems to regain some speed, even with Compiz enabled in LXDE.

Minor problem: My hotkeys for volume control that work in Gnome don't work in LXDE environment, also the Volume Control panel applet doesn't seem to run.

Another minor problem: Keyboard Led doesn't respond to Scroll Lock or Numlock, but it does show the Caps Lock status correctly.

Where do I start looking?

---

### Post by northwestuntu on 2009-02-26
i love the speed it has.  what a change from ubuntu in terms of speed :p

how do you mount a slaved hard drive though? in ubuntu it automounts it for me. can lxde do that?

also the taskbar doesn't have a icon for the program or folder that is open.
does it need it's own theme package or something?

---

### Post by Mark76 on 2009-02-26
Surely you mean what a change from Gnome/KDE/Whatever you were using before. :?

Unless you're using LXDE with some other distro.

---

### Post by manilaph on 2009-03-13
I was able to successfully install **Debian 5.0 XFCE-LXDE CD** on my laptop and my pc... both using a wired connection during the installation since my laptop needed the iwlwifi driver package before going wireless. And I used wicd instead of the networkmanager package. I find wicd much better.

The set-up was pretty easy (easier for the PC) and there was a "standard" system already to choose from.

_Does Ubuntu have a similar standard system to start with? _

I think the minimal cd is just too minimal.

The Debian 5.0 XFCE-LXDE had a graphical installer so there was no problems for newbies like me.

The reason as to why I want to have an Ubuntu version is simply because I find the Ubuntu forum community more responsive to any inquiries.

I saw a tutorial regarding the minimal install cd but still got confused since there is no graphical installer.

---

### Post by manilaph on 2009-03-18
XFCE is noticeably slower than LXDE.

Just from GDM to LXDE is a split second. While on GDM to XFCE takes a few seconds.

File transfer or copy+paste files under Thunar is slower than under PCManFM.

But if you patient since there are just a couple of seconds difference... it would not matter.

Just don't know how to install my own wallpaper on LXDE. All i have is the blue, red or green wallpaper.

---

### Post by yabbadabbadont on 2009-03-18
> **manilaph said:**
> Just don't know how to install my own wallpaper on LXDE. All i have is the blue, red or green wallpaper.

The wallpaper is being set using pcmanfm (like nautilus does in gnome).  

In pcmanfm, Edit->Preferences->Desktop tab.

---

### Post by jw5801 on 2009-03-18
I'm curious as to the status of PCManFM. The last release was 0.5, and that was nearly 9 months ago - haven't seen a peep since then. Is there still any development going on, that anyone knows about?

---

### Post by graabein on 2009-03-18
Take a look at the [LXDE planet feed]("http://planet.lxde.org/"). Not sure about PCManFM specifically...

---

### Post by rolypolycat on 2009-04-11
Hello!

I'm running Intrepid after a command line install with lxde. I can't find any way to add items to the main menu. How do I put things on the menu; edit a file,run some software, etc? And if it's a file I have to edit by hand, what is it, and where is the file?
Thanks in advance!

---

### Post by SomeGuyDude on 2009-04-11
> **jw5801 said:**
> I'm curious as to the status of PCManFM. The last release was 0.5, and that was nearly 9 months ago - haven't seen a peep since then. Is there still any development going on, that anyone knows about?

I dunno. Frankly it's still awesome. Kicks the crap outta thunar, I'll say that much.

---

### Post by jjgomera on 2009-04-11
> **rolypolycat said:**
> Hello!

I'm running Intrepid after a command line install with lxde. I can't find any way to add items to the main menu. How do I put things on the menu; edit a file,run some software, etc? And if it's a file I have to edit by hand, what is it, and where is the file?
Thanks in advance!
lxde is openbox, so the menu is in the file /home/<user>/.config/openbox/menu.xml

you can edit manually or, easily, you can use obmenu to edit it graphically.

---

### Post by johnraff on 2009-04-13
> **jjgomera said:**
> lxde is openbox, so the menu is in the file /home/<user>/.config/openbox/menu.xmlThat's the Openbox menu of course, which might come up with a right-click to your desktop, depending on what LXDE desktop setting you've chosen. You can tie it to a key in the /home/<user>/.config/openbox/rc.xml file too.

The LXDE main menu which usually sits at the end of lxpanel is harder to edit. One way to add an item is to put a .desktop file in your /home/<user>/.local/share/applications folder (make it if necessary). Have a look at the .desktop files in /usr/share/applications to see what's needed.

---

### Post by dashnak on 2009-04-17
Everything works great except for the fact that I'm unable to run firefox in fullscreen:
In GNOME, when I hit F11, the menubar, as well as the status and the bookmarks would disappear, leaving only the webpage I was browsing at the time.
In LXDE, when I do the same, only the status bar disappears.
Has anyone run into this issue? If so, how did you fix it?
Thanks.
Love the DE.

---

