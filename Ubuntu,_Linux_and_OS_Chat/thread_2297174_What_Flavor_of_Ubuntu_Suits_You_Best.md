---
title: "What Flavor of Ubuntu Suits You Best?"
date: 2015-10-01
forum: Ubuntu, Linux and OS Chat
---

### Post by oldefoxx on 2015-10-01
I'm looking at downloading and installing a different version of Ubuntu.  I don't care for Dash. so reverted to the classical gnome interface.   I can't control my screen brightness setting on reboot or after a suspend, which is a problem in 14.04.  That needs fixing.  I can't get a screen magnifier program to work on the 64-bit version of 14.04, although the needed library is supposedly in a RPM package for Fedora.  And as a final, I can download and install some new apps, but then the only way I know of to start them is to execute a command in a terminal.

But rather than just do a try-this, try-that approach, I thought I would just ask the community:  What's your opinion of the different interfaces offered?  Any you know rhat would handle my issues for me?  What's their down side as well?

I have the impression that Ubuntu is mainstream.  That's what you find download links for when you go looking.  That's what you find central to some third party software like Virtualbox, which I also have and use.

At 74, with problem eyesight, I'm just looking for a place to roost and do a few things while I've time left.  A big challenge is to learn enough PureBasic that I can write a few utilities, the sort of stuff I once did under DOS and Windows using all manner of Basics, until I decided to drop Microsoft altogether.  PureBasic is different, but different in a good way, just as Linux is different, but also in a good way.  Now what's the best of Linux?  Most specifically, what flavor of Ubuntu might suit me best?

---

### Post by TheFu on 2015-10-01
Can't answer which is best for you. We are all different.

I don't use **any** of the pre-built desktop distros. For my needs, they are all too heavy - even Lubuntu is too heavy.

Rather, I load Ubuntu Server - and for systems with desktop needs, I'll add a minimal GUI like openbox or fvwm-crystal.

Never heard of PureBasic.  For simple little programs, bash scripting and perl and ruby are my tools of choice.

Good luck in finding what you seek.

---

### Post by mystics on 2015-10-01
I have a sort-of odd system. I use Xubuntu as the default but replaced Xfwm4 with KWin. Overall, I enjoy the Xfce desktop environment, so Xubuntu was a natural choice. It's flexible, easy-to-use and modify (though it would help if they merged some of the settings categories together), has a good set of applications like Whisker Menu and Thunar, and finds a good balance between traditional and modern in its design. However, I did want some more flexibility and animations with the window manager, and KWin did a good job of offering what I wanted. So while I'm sure there are some Xfce purists who have just had a heart attack at the thought someone tainted the lightweight experience with KWin, I really enjoy the overall experience it offers. 

But if you don't want to go through the trouble of setting up KWin or want to keep things lightweight, Xfwm4 is a good window manager in its own right. It may have screen tearing issues even with the compositor configured properly, though, so you may need to use Compton to fix that. Plenty of tutorials and copy/paste stuff for that.

---

### Post by mikodo on 2015-10-01
Hi oldefoxx.

 I now, just read your post. I commented in the thread after reading only  mystics post. I've deleted the rest of my post as it doesn't address *your user-needs.

Edit2:

I had asked over at #ubuntu-devel for possible inclusion of "inverse" being written into MIR. The lead dev for Unity (I forget his name), and one of the devs working on MIR (vanvugt) responded that first, I should submit a bug for a request of this under Unity8. Vanvugt ran with it as a personal project for the MIR end of this, during his off hours, and is hopeful that, someone will do the work in Unity-next to provide support  for "accessibility features" in it, for the future.

None of that helps you now plus, you don't want to use Unity. That's cool, not everyone here does.

I wish for you, helpful responses. In contrast to mine ...

My best.


Link to bug if you are in any way interested. [https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1400580](https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1400580)

---

### Post by mikodo on 2015-10-01
@oldefoxx

I apologize for the double post. But, I have been thinking about this since, I read your post.

One recommendation I suggest for your situation, is that you take a look at Ubuntu Mate. One of the official Ubuntu derivatives.

Ubuntu Mate is a continuation of sorts of the old Gnome2 DE (with ongoing current development, I think it has been ported to GTK3 as an example). It is quick running, and esthetically pleasing. More importantly here is, that the dev/maintainer in Ubuntu, (he is also a packager in Debian) has incorporated the compositor Compiz, so it can run in Ubuntu Mate. Compiz has accessibility features that you might find helpful.

Here is Ubuntu Mate's official site:  [https://ubuntu-mate.org/](https://ubuntu-mate.org/)

An example of Compiz's accessibility features is seen here, (a plugin): [http://wiki.compiz.org/Plugins/Ezoom](http://wiki.compiz.org/Plugins/Ezoom)

There used to be more accessibility features in Compiz that I used in the past but, I haven't used it in a few years now so, I don't know what all it has now.

Edit: again, sorry ...

Here is Martin Winpress the developer of Ubuntu Mate OS, and a general  developer of the Mate Desktop and maintains it with other distos too,  talking about the Compiz feature in, Ubuntu Mate. 

[https://www.youtube.com/watch?v=k_nk02XELi4](https://www.youtube.com/watch?v=k_nk02XELi4)

He talks about the Ezoom feature that I linked above and how to enable other features of Compiz on Ubuntu Mate, (ccsm). 

 I just read that the desktop cube effect has been removed from this OS, due to problems.

Martin is reputed to be very accessible to the community and can probably be tracked down from this page:

[URL="http://flexion.org/pages/about.html"]http://flexion.org/pages/about.html

[/URL]If you get to the place of wondering about which version of any Ubuntu derivatives to install, ask a separate question in the support sections, to be offered advice. (New to Ubuntu, General Help, or Installation and Upgrade) will all garner advice replies for you.

That's all.

---

### Post by oldefoxx on 2015-10-02
I'm in the process of using a torrent client to download Mate while I write this reply to your posts.  I want you to know I appreciate your efforts and recommendations.  You are the third person to speak well of Mate, so I will give it a spin.  I followed your other link to Compize and Ezoom. and it looks promising.  There is nothing to show the effects of all this, and I did a quick search and found this video:  [https://www.youtube.com/watch?v=sI03Xr-55uw](https://www.youtube.com/watch?v=sI03Xr-55uw)

The interesting thing is that the magnifying effect is exactly what you would want, AND IT IS ON UBUNTU 14.04 to boot!  No real need to move to a different interface if that is true.  But what did they have to do to put it together?

in reading the info about Ezoom, it makes mention of a <super> key and the use of the mouse.  Now some magnifiers rely on the mouse having a 3rd input, what's called the "Scroll" wheel.  That feature is not duplicated in laptops, that have a touchpad and two buttons.  So it's uncertain if the plugin is fitted to my hardware or not.  A few keys were sacriticed on the HP Envy keyboard as well, so I lost the right Ctrl, Alt, and Menu buttons.

At least it is a possibility.  I think some poor vision users would be more than pleased that there might be something available to help them, and the video is worth the look.

---

### Post by mikodo on 2015-10-02
Hi again.

In that YT video that I linked you to, with Martin Winpress doing the compiz effects in Ubuntu Mate 15.04, there is no mention of Zooming with a mouse. He was using a 10 year old Thinkpad, for the screen-casting of it. He also states that the the Zoom in and out are controlled by the super key (window key) and the M + N keys. This of course, after he installed ccsm (Compiz Configuration Settings Manager). I think you probably have those keys. 

Addendum. 

I hope I am not giving you information you know already. But, I have a few minutes here and I think it is better to say this and risk offending you than, it not being said and you not knowing this. I mentioned about inquiring about which version of Ubuntu Mate to install in case you didn't know this yet:

a. Ubuntu and all its' derivatives are in the development release cycles right now, and 15.04 will reach end of life (EOL), 9 months from when it became available in April this year. That means it will reach EOL in Jan 2016. The next interim release will be released in Oct 2015, (this month). It too will be supported for only 9 months. In April 2016 Ubuntu and all its' derivatives will have available the next LTS (Long-Term Support cycle), which varies between 3 - 5 years of support between which OS one installs, (Ubuntu is for 5 years, and I am guessing but don't know for sure, Ubuntu Mate will be too and if not it would be expected to have 3 years of support. 

What does that mean for you? If you do decide on installing Ubuntu Mate 15.04 to take advantage of the compiz configurations inherent in it, you will need to either re-install with Ubuntu Mate 15.10 before Ubuntu Mate 15.04 reaches EOL. Or, do an upgrade with the Ubuntu Mate 15.04 install. Then, when Ubuntu Mate 16.04 is available, you would need to either update or upgrade to it, shortly after it is released in April 2016. Then, you would have a LTS release, with much longer support.

b. I indicated earlier in this post that the Zooming feature was available after Martin had installed ccsm. I might be wrong, and he may have enacted it, without installing ccsm. I don't know for sure, and I can't check easily as, I don't have Ubuntu Mate installed.

2. An other alternative to Ubuntu Mate and Compiz, is to do what mystics mentioned in his post. Install Xubuntu, another light official derivative of Ubuntu, and install Kwin (has a Zoom feature) as the window manager in place of the Xfwm. I've done that a few years ago, and we could help you with doing that too, if Ubuntu Mate doesn't work out for you, or you want to try another option.

3. A third option is installing Kubuntu, a more resource using Ubuntu official derivative, and use Kwin with it. I hear it is going through some growing pains right now, and I don't that know that disro, so I can't advise you with that. It is not thought to be a newbie friendly distro. But, the ones that know it well, love its' customability, apps and work flow.

I hope this helps.

---

### Post by oldefoxx on 2015-10-02
Hey, that's all important stuff.  I've been with Ubuntu since about 8,04, and I only move up when another LTS becomes available.  But due to vision issues, I may have to break with that habit now.

The thing that I really learned to hate about Windows was all the relearning going on.  Not just the OS, but all the apps.  Then keeping it sorted out as to how it is done here and how it was done there.  And the money and time wasted in this endless pursuit of fattening MS's pockets.  I heard on the news about a week ago that Bill Gates is the richest man in the world.  How come I wasn't surprised to hear that?

I figure to let this thread continue on and bring forth more ideas.from different people.  There was never any risk of offending me, and this will all act to serve my needs and those of others.  Mostly I am looking at getting the iLiveCD so image downloads, then configuring grub to boot from that image on either my internal drive or an attached USB hard drive and test drive it for a bit.  I have a small store of DVD RW disks I can use if I decide to go with any of them on a permanent bases

Now there are techniques for getting new entries added to grub, where it will then boot off an iso image on a drive rather than on a DVD disk, and that you can run the LiveCD that way, but there is a bug in the install process where it has a file open on sda1 so it can't unmount that partition as part of the install process, so the install hangs.  A method of force unmounting has been devised and the bug reported, so I am asking for more info on doing this technique and expecting a bug fix in the future.

The other thing I've learned is that new hardware is making new demands on the boot process, and you have to sometimes upgrade your OS to keep pace.  Either that of have the latest version of Boot Repair Disk burned to a CD to recover a failed distro install that made your PC unbootable.  The OS is on there, but the boot method is flawed, so now the experts behind Boor Repair Disk need a shot at fixing it.

---

### Post by Habitual on 2015-10-02
the mini.iso

---

### Post by mikodo on 2015-10-02
Ya, I leapt to conclusions in the middle of the night, when I was already tired, in that when I read about your work with writing utilities with dos, that you were new here. Sorry. Interestingly, I started with Ubuntu in 8.04 too, only for me, that was with this my first and only computer after owning it for 6 months. Being 62 now, that's an odd combination of being an old newbie ... lol

Now, I just finished reading your thread about Browsers. You are not whom I thought I was addressing at all, last night.

Good luck with working around the bug with ?persistent grub2 instances. Whatever it should be called ...

---

### Post by forrestcupp on 2015-10-02
I haven't used it for a while, but I used to be partial to Kubuntu. I like KDE a lot. I'm more about features than lightweight, though.

And it's not Ubuntu, but I hear Cinnamon is coming along pretty well in Mint. I haven't used it since its early days, but I've heard it's pretty great now.

---

### Post by oldefoxx on 2015-10-03
HEY!  THERE IS A MAGNIFICATION FIX ALREADY IN UVUNTU 14.04!  But nobody has mentioned it.  I don't need bigger pictures, I just need bigger text.  And I wasn't getting it.  Not across the board.  Now I have bigger text and bigger images, using a simple tool that you can use "sudo apt-get install dconf-tools" to fetch for you. Or you can do it from a terminal window with one instruction.  But let's discuss the tool first:

It's the dconf-editor and it provides one GUI way of changing many systems settings.  Now with dconf-editor, which appears under System Tools (or can be called from the command line directly), if there is an arrow in front of of the term, you must click on the arrow itself.  It toggles a view of what is filed under that term.  If no arrow, then click on the term to open it up and show/change its contents in the right pane.  The advantage of dconf-editor is that you can work your way down the branches until you find what you want.  That's handy.

Where you have to go is org >> gnome >> desktop >> .interface >> text-scaling-factor, which is defaulted to 1.0.  Change the value to something like 1.2 or 1.25.  The difference is dramatic and immediate.

Or. if you want to do it in one single step from a terminal window, enter the following at the prompt:
```
gsettings set org.gnome.desktop.interface text-scaling-factor 1.2

```

You can also explore the settings available by using gsettings itself, like so:
```
gsettings list-recursively > tmp.2; cat tmp.2 | less
```
If you know only that it has to do with text, you can add a grep filter like so;
```
oldefoxx@don-HP-K073:~$ gsettings list-recursively > tmp.2; grep "text" tmp.2 > tmp.3; cat tmp.3 | less; rm tmp.?

```

Man, this is it!  I can read everything now.  I get the effects of a smaller screen made larger, but without having to toy with changing my screen resolution, which just didn't work out.  Now if I had two script files set up with hot keys, I could zoom in and zoom out whenever I want.  Fact is, with this new setting for the Desktop. I'm going to have to downsize some of my previous efforts to make things larger.

You can change the grep filter above to search for "gedit", and find the setting for:
```
 org.gnome.gedit.preferences.editor editor-font  'Monospace 12'
```,  It says '12' on my laptop, because that is what I changed it to.  It was smaller.  I tried it at '16' and '20', and decided that '12' was good enough.  Again, it is just using "gsettings set", the complete name, and what you want to set it to.  It can help to see what it is already set to, so change "set" to "get" and find out.  Or look at the output from the string of commands above.

Hey, I guess I am sticking to 14.04 for awhile longer.

---

### Post by yoshii on 2015-10-06
I use Ubuntu Studio because I compose electronic music and do some digital illustrations and photo editing as well.  It uses Xfce so it's probably similar to Xubuntu.  
Ever since I disabled Apport it's been smooth sailing.  I use Wine a lot for some portable Windows freewares and a few paywares, such as Reaper and FL Studio.

---

### Post by forrestcupp on 2015-10-06
> **yoshi2 said:**
> I use Ubuntu Studio because I compose electronic music and do some digital illustrations and photo editing as well.  It uses Xfce so it's probably similar to Xubuntu.  
Ever since I disabled Apport it's been smooth sailing.  I use Wine a lot for some portable Windows freewares and a few paywares, such as Reaper and FL Studio.

Reaper is pretty cool, but it's not really better than Ardour is it? I think it would be better to use a native app for recording.

---

### Post by NathanRodriguez on 2015-10-06
Looks like someone needs to donate before can download latest Ardour version...

---

### Post by forrestcupp on 2015-10-06
> **NathanRodriguez said:**
> Looks like someone needs to donate before can download latest Ardour version...

Is Ardour not in the repos anymore? I think at one time, it used to be installed by default in Ubuntu Studio.

Edit: I went to Ubuntu Studio's website, and it still lists Ardour as being a default install.

---

### Post by @Tornado on 2015-10-07
I like using Ubuntu 15.04 with the Cinnamon Desktop Environment but it doesn't work so well with dual monitors. I ended up using Ubuntu 15.04 GNOME.

---

### Post by Joelb955 on 2015-10-09
I prefer Kubuntu, but that's just me. Regular Ubuntu is beautiful and has a snappy look to it. Honestly I'm not sure what version of Ubuntu is better since you have eyesight problems. If you want me to I can check around for packages that would make it easier for you!

---

### Post by Ruediger_Gmach on 2016-04-01
In search of a magnifying glass on Ubuntu with Unity and LXDE to choose from login, I ran accross [http://magnifier.sourceforge.net/](http://magnifier.sourceforge.net/) and works super easy on my ubuntu 14.04.
This magnifier seems to be simply based on pure X11 - so it should work on top of ANY X11 desktop environment.
It is super simple to install - you can even decide to simply unpack it somewhere in your homedir and run it from there.
I tested and used it successfully on Unity and LXDE. In LXDE I  then modified/extended the keyboard shortcuts so I can launch magnifier with Meta-M, You can then move the magnifying rectangle with your mouse around, and Esc makes it go away.
I mainly use it for software demos with high resolution, to point out details of the displayed screen to my audience.
just my 0.02

P.S. I am in search of a most lightweight Desktop mgr using as few as possible memory and CPU because I mainly run multiple mem & cpu heavy VMs for demo purposes. I will give MATE a try - looks good - I hope cube spinning the desktop does not kill itself when my VMs are on heavy load.

PPS. I dont understand, why these nowadays Desktop Environments are often built so heavy (CPU & Mem). That gives away the advantage of Linux' inherent lightweightness opposed to other Desktop OSs like MS or Apple. Less is more !

---

### Post by light_yagami2 on 2016-04-06
So far I have tried Ubuntu Unity and liked it, but had frequent WiFi Problems. Not only that but Unity *was* kinda annoying. So I switched to Ubuntu GNOME last night and everything is running smoothly. I installed MATE Desktop on it to and it works fine! I really like Gnome 3 though [IMG]http://www.emojimeanings.net/img/whatsapp-smileys/whatsapp-smiley-with-heart-eyes-1F60D.jpg[/IMG]

---

### Post by yoshii on 2016-04-06
> **forrestcupp said:**
> Reaper is pretty cool, but it's not really better than Ardour is it? I think it would be better to use a native app for recording.

Well, I'm not against using native Linux programs, but I have a large collection of 32-bit Windows VST instruments and effects, both freeware and payware.  I am able to use those within Reaper via Wine.  The VST instruments and effects form my artistic palette.  I know there are some workarounds using FeSTige, but I don't know how to use those yet.  So I just keep composing with Reaper and sometimes with EnergyXT 32-bit Windows for the same reason.  

The only thing I don't like about Ubuntu Studio is the use of alacarte instead of menulibre for the system menu, and I don't like all the extra stuff that gets installed.  
I think next time I might install Xubuntu instead, then change to a low-latency kernel, and manually install the graphics and video and sound programs that I like.  
I've tried to prune down the Ubuntu Studio install, but it's not so easy to do because of entangled dependencies.  Also, my internet connection is not so fast, so it's a bit easier dealing with the smaller Xubuntu .ISO instead of the huge full DVD sized Ubuntu Studio.

---

### Post by Bucky Ball on 2016-04-06
Go[ xubuntu-core ]("http://xubuntu.org/news/introducing-xubuntu-core/")16.04 LTS then install the audio bits you want.

---

### Post by poorguy on 2016-04-06
Deleted.

---

### Post by farrinux on 2016-04-08
I use the vanilla LTS. Currently 14.04.  I have thought about trying a different desktop.  Just haven't done it. I am sure though between customizability and the different flavors of ubuntu that one should be able to find a happy medium.

---

### Post by sammiev on 2016-04-08
I'm testing 16.04 on most flavors. Likely Xubuntu is my most used.

---

### Post by vasa1 on 2016-04-08
> **sammiev said:**
> I'm testing 16.04 on most flavors. Likely Xubuntu is my most used.
Can you please see which other flavors offer this: [https://help.ubuntu.com/16.04/ubuntu-help/net-wireless-adhoc.html](https://help.ubuntu.com/16.04/ubuntu-help/net-wireless-adhoc.html) ?

---

### Post by QDR06VV9 on 2016-04-08
With a little work they all can.
To easily create a wifi AP on ubuntu and other distros, use the hotspotd daemon &#8211; Opensource, available on github.


To install:

```
wget [https://github.com/prahladyeri/hotspotd/raw/master/dist/hotspotd-0.1.4.tar.gz](https://github.com/prahladyeri/hotspotd/raw/master/dist/hotspotd-0.1.4.tar.gz)
tar xvf hotspotd-0.1.tar.gz
cd hotspotd-0.1/
sudo python setup.py install
```
Source: [https://prahladyeri.wordpress.com/2013/05/26/how-to-turn-your-linux-machine-into-a-wifi-access-point/](https://prahladyeri.wordpress.com/2013/05/26/how-to-turn-your-linux-machine-into-a-wifi-access-point/)

---

### Post by vasa1 on 2016-04-08
> **runrickus said:**
> With a little work they all can.
To easily create a wifi AP on ubuntu and other distros, use the hotspotd daemon &#8211; Opensource, available on github.


To install:

```
wget [https://github.com/prahladyeri/hotspotd/raw/master/dist/hotspotd-0.1.4.tar.gz](https://github.com/prahladyeri/hotspotd/raw/master/dist/hotspotd-0.1.4.tar.gz)
tar xvf hotspotd-0.1.tar.gz
cd hotspotd-0.1/
sudo python setup.py install
```
Source: [https://prahladyeri.wordpress.com/2013/05/26/how-to-turn-your-linux-machine-into-a-wifi-access-point/](https://prahladyeri.wordpress.com/2013/05/26/how-to-turn-your-linux-machine-into-a-wifi-access-point/)

Thanks for that !

I'll try it tomorrow with a Live USB of Lubuntu 16.04.

Oops! Looks like quite a bit of rocket science. I don't think I'll be able to follow the instructions.

---

### Post by sammiev on 2016-04-08
> **vasa1 said:**
> Can you please see which other flavors offer this: [https://help.ubuntu.com/16.04/ubuntu-help/net-wireless-adhoc.html](https://help.ubuntu.com/16.04/ubuntu-help/net-wireless-adhoc.html) ?

Hi vasa1,

Seems the HotSpot has a few bugs in Gnome and Unity. Haven't tried the others yet.

Will look at runrickus post now.

---

### Post by vasa1 on 2016-04-08
> **sammiev said:**
> Hi vasa1,

Seems the HotSpot has a few bugs in Gnome and Unity. Haven't tried the others yet.

Will look at runrickus post now.That link is just too complicated for me. 

It seems that Kubuntu also has a simple set-up and that it is possible to install Kubuntu's network manager, plasma-nm, along with several dependencies and use that instead of the default network manager. I haven't checked that out.

---

