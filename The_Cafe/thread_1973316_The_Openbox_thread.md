---
title: "The Openbox thread"
date: 2012-05-04
forum: The Cafe
---

### Post by mips on 2012-05-04
So I'm currently using Openbox on a Xubuntu base install (waiting for xfce 4.10) and have been using it for a few days now. Actually getting very comfortable and not really missing all the extras of a DE.

I thought I would start this thread for all Openbox users to contribute their setups, ie bashrc, menus, tint2, conky, themes, favourite apps etc etc so feel free to post your config files & screenshots of your openbox stuff.

---

### Post by chamber on 2012-05-04
I love openbox. Tends to be my go to window manager of choice. My bashrc is in my github link along with some other configs. I'll load up my tint2 config tomorrow when I'm back on my pc. 

Am thinking of using openbox on my desktop too. Arch and openbox are a great combo and I'm not overly fussed on gnome anymore, I don't need all the fancy effects.

---

### Post by m_duck on 2012-05-04
Long time Openbox user checking in. That said, not used it for a little while but it is a fantastic WM. I will see if I can find some of my configs at some point. Keybinds, keybinds for everything.

---

### Post by dniMretsaM on 2012-05-04
I like Openbox a lot. Although I don't use it all that much (I mainly use XMonad, but I do use Openbox on my Debian Wheezy running Razor-qt), it's one of my favorite minimalistic, non-tiling WMs.

---

### Post by Lucradia on 2012-05-04
I like openbox a lot, and it's amazing how you can make it more like a desktop like GNOME, etc. with just a few things.

Link here: [http://forums.debian.net/viewtopic.php?f=20&t=50703](http://forums.debian.net/viewtopic.php?f=20&t=50703)

Only problem is, you have to make your user be able to use shutdown so that you can bypass sudo's limitations for xmessage input. (And Ubuntu's PCManFM, unless they finally updated it, doesn't have the Desktop tab, so a configuration on obmenu won't bring up the correct desktop wallpaper config.)

openbox --exit is also supposed to log you out to terminal, but doesn't seem to do such anymore (just causes X to continue running, wallpaper and all, just no openbox or stalonetray.)

---

### Post by ratcheer on 2012-05-04
Am I welcome to post about my OpenBox on Arch Linux? Or, would it confuse things?

Tim

---

### Post by Tibuda on 2012-05-04
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

@ratcheer: openbox is openbox

---

### Post by ratcheer on 2012-05-04
> **Tibuda said:**
> 

@ratcheer: openbox is openbox

Cool, thanks.

Those of you who use wallpaper backgrounds, do you have to "restore" them each time you start OpenBox? I have automated it, but I do have to do it. I guess I'm not sure I understand why it needs to be done each time, instead of retaining a setting.

Tim

---

### Post by Version Dependency on 2012-05-04
> **ratcheer said:**
> Cool, thanks.

Those of you who use wallpaper backgrounds, do you have to "restore" them each time you start OpenBox? I have automated it, but I do have to do it. I guess I'm not sure I understand why it needs to be done each time, instead of retaining a setting.

Tim

I use Nitrogen to manage the wallpaper.  In my startup file I have the following line:

```
nitrogen --restore &
```

---

### Post by ratcheer on 2012-05-04
> **Version Dependency said:**
> I use Nitrogen to manage the wallpaper.  In my startup file I have the following line:

```
nitrogen --restore &
```

Yes, so do I. My question is, why does this have to be done? Do most desktops do it this way, or do they just store a setting somewhere that says, this is the wallpaper? Maybe other desktops are doing the same thing somewhere, but it is just hidden from the user.

It just seems odd to me.

Tim

---

### Post by BrokenKingpin on 2012-05-05
Openbox is awesome, but still prefer a full DE (Xfce). By the time I setup my full system I end up with something that is pretty close to LXDE with a bunch of Xfce stuff. So I find it easier just to run Xfce, which gives me everything I need and is still pretty light.

I can definitely see why people run Openbox though,and why LXDE uses as the default WM. Fast, configurable, and gets the job done.

---

### Post by Lucradia on 2012-05-05
If you want just a login manager rather than to do startx, SLiM can do that for you. No need for a DE or deps from one.

---

### Post by chamber on 2012-05-05
> **Lucradia said:**
> 
openbox --exit is also supposed to log you out to terminal, but doesn't seem to do such anymore (just causes X to continue running, wallpaper and all, just no openbox or stalonetray.)

Just use oblogout. Edit you menu.xml so that exit calls this.

---

### Post by mips on 2012-05-05
> **ratcheer said:**
> Am I welcome to post about my OpenBox on Arch Linux? Or, would it confuse things?

Tim

You are more than welcome Tim, the configs & stuff are pretty universal across distros.

I'm a big Arch lover but not using it due to bandwidth constraints wrt frequent updates.

Post away ;)


Nice to see some action in this thread, when I created it I thought it was just gonna fade away as you don't really here much about it here or see much of it in the screenshot thread.

---

### Post by mips on 2012-05-05
> **Lucradia said:**
> 
Only problem is, you have to make your user be able to use shutdown so that you can bypass sudo's limitations for xmessage input. (And Ubuntu's PCManFM, unless they finally updated it, doesn't have the Desktop tab, so a configuration on obmenu won't bring up the correct desktop wallpaper config.)

openbox --exit is also supposed to log you out to terminal, but doesn't seem to do such anymore (just causes X to continue running, wallpaper and all, just no openbox or stalonetray.)

I've got lightdm installed and exiting openbox from the menu takes me back to the lightdm screen from where I can shutdown or restart via the top right icon.


> **Version Dependency said:**
> I use Nitrogen to manage the wallpaper.  In my startup file I have the following line:

```
nitrogen --restore &
```

This ^^ Use nitrogen

---

### Post by chamber on 2012-05-05
> **ratcheer said:**
> Yes, so do I. My question is, why does this have to be done? Do most desktops do it this way, or do they just store a setting somewhere that says, this is the wallpaper? Maybe other desktops are doing the same thing somewhere, but it is just hidden from the user.

It just seems odd to me.

Tim

This is how openbox handles it.  It gives you the option of what you want to autostart.  Other DE will be doing something similar but will just autoconfigure it.  

One of the reasons I like openbox is the configuration options you have.  I don't like not being able to decide exactly how I want things, if I want to modify my log in screen I should have the choice etc.

---

### Post by mips on 2012-05-05
> **ratcheer said:**
> Yes, so do I. My question is, why does this have to be done? Do most desktops do it this way, or do they just store a setting somewhere that says, this is the wallpaper? Maybe other desktops are doing the same thing somewhere, but it is just hidden from the user.

It just seems odd to me.

Tim

Keep in mind that Openbox is **only** a Window Manager, it's not a Desktop Environment that comes with a host of integrated modules to perform tasks like this. You can compare openbox to the xfwm4, kwin window managers in xfce & kde but without all the default stuff that comes with the DE.

Because you don't have all these components of a DE you have to use external applications like nitrogen etc to set your wallpaper and call those via config files seeing there is no integration to speak of.

---

### Post by m_duck on 2012-05-05
> **ratcheer said:**
> Yes, so do I. My question is, why does this have to be done? Do most desktops do it this way, or do they just store a setting somewhere that says, this is the wallpaper? Maybe other desktops are doing the same thing somewhere, but it is just hidden from the user.

It just seems odd to me.

Tim

Because, as mips said, Openbox is *just* a WM, you have to do some extra bits yourself. Desktop environments handle this themselves as they automatically have start up items that take care of it.

In GNOME, I think it is Nautilus that looks after the wallpaper. In OB, you can choose. Nitrogen is a good choice; I usually use feh, requiring **one** of the following in autostart (from memory):
```

eval `cat $HOME/.fehbg` &
sh $HOME/.fehbg &

```
I think they both work...

---

### Post by chamber on 2012-05-05
> **m_duck said:**
> 
```

eval `cat $HOME/.fehbg` &
sh $HOME/.fehbg &

```
I think they both work...

They do.  You just have to run something like 

```
feh --bg-scale /path/to/image.file
```

first in order to set the options for the fehbg file

---

### Post by F.G. on 2012-05-05
just wanted to say, been using crunchbang (also known as !#, debian + openbox) on my netbook for a while now, and love it. so much so that this morning i just installed archbang (arch + openbox) on my desktop, in preference to arch + kde. and am loving that too.

---

### Post by ratcheer on 2012-05-05
Thanks for the answers on having to restore the wallpaper everytime OpenBox is started. Yes, I now understand that the desktop is a bunch of components that are not integrated. I should have seen it from the start, as I have to configure every one of them!

I posted a screenshot in this thread (post 8 ), if anyone is interested. [http://ubuntuforums.org/showthread.php?t=1973347](http://ubuntuforums.org/showthread.php?t=1973347)

Tim

---

### Post by Version Dependency on 2012-05-05
> **ratcheer said:**
> Thanks for the answers on having to restore the wallpaper everytime OpenBox is started.


You shouldn't have to do anything to restore your wallpaper after initially putting that line about nitrogen in your startup file.  You shouldn't need to manually type a command or execute a script.  It should be automatic every time your login.

---

### Post by ratcheer on 2012-05-05
> **Version Dependency said:**
> You shouldn't have to do anything to restore your wallpaper after initially putting that line about nitrogen in your startup file.  You shouldn't need to manually type a command or execute a script.  It should be automatic every time your login.

You don't understand what I said. In my first post on the question, I said that I had automated it, but that I did not understand why it had to be done at all. I do not have to manually intervene, and my questions have never been about that.

From post # 8:
> I have automated it...

Sorry about the confusion.

Tim

---

### Post by chamber on 2012-05-05
> **F.G. said:**
> just wanted to say, been using crunchbang (also known as !#, debian + openbox) on my netbook for a while now, and love it. so much so that this morning i just installed archbang (arch + openbox) on my desktop, in preference to arch + kde. and am loving that too.

I started using #! in 2008 on my old laptop and it was brilliant.  Used Archbang for a while but preffered doing my own Arch install, was a very good distro though.

Currently using subtle but my root users log in uses openbox incase I need to fix something.

---

### Post by mips on 2012-05-05
I just installed SpaceFM and it looks amazing and very powerful.
Have a look at the screenshots [http://ignorantguru.github.com/spacefm/screenshots.html](http://ignorantguru.github.com/spacefm/screenshots.html)

This could just be my new file manager of choice! Just have to learn how all it's features work. I already like the built in search function and multiple panes. Also gonna check out all the plugins, [https://github.com/IgnorantGuru/spacefm/wiki/plugins/](https://github.com/IgnorantGuru/spacefm/wiki/plugins/)

If you want to try it out here is how to install it:

Add the developers repo to your sources.list, deb [http://ignorantguru.github.com/debian/](http://ignorantguru.github.com/debian/) unstable main

```
sudo gpg --keyserver keys.gnupg.net --recv-keys 0x01937621 0x107165A1
sudo bash -c 'gpg --export -a 01937621 107165A1 | apt-key add -'
sudo apt-get update
sudo apt-get install spacefm
```

---

### Post by chamber on 2012-05-05
> **mips said:**
> I just installed SpaceFM and it looks amazing and very powerful.
Have a look at the screenshots [http://ignorantguru.github.com/spacefm/screenshots.html](http://ignorantguru.github.com/spacefm/screenshots.html)

This could just be my new file manager of choice! Just have to learn how all it's features work. I already like the built in search function and multiple panes. Also gonna check out all the plugins, [https://github.com/IgnorantGuru/spacefm/wiki/plugins/](https://github.com/IgnorantGuru/spacefm/wiki/plugins/)

If you want to try it out here is how to install it:

Add the developers repo to your sources.list, deb [http://ignorantguru.github.com/debian/](http://ignorantguru.github.com/debian/) unstable main

```
sudo gpg --keyserver keys.gnupg.net --recv-keys 0x01937621 0x107165A1
sudo bash -c 'gpg --export -a 01937621 107165A1 | apt-key add -'
sudo apt-get update
sudo apt-get install spacefm
```

In arch

```
pacman -S spacefm
```

It was in the AUR but got moved to Community.


[[img]http://img32.imageshack.us/img32/6097/newthemet.th.png[/img]](http://img32.imageshack.us/img32/6097/newthemet.png)

It's awesome.

---

### Post by ohnonot on 2012-05-07
i have 3 questions...

first:
i've been using blackbox with windows. since i changed to linux (god bless!) i haven't tried *box, i wonder, does openbox (or fluxbox) use similar plugins, like bbinterface and slit and whatnot (see [here]("http://bb4win.sourceforge.net/plugins.html"))?

second:
> **mips said:**
> I just installed SpaceFM and it looks amazing and very powerful.
Have a look at the screenshots [http://ignorantguru.github.com/spacefm/screenshots.html](http://ignorantguru.github.com/spacefm/screenshots.html)

This could just be my new file manager of choice! Just have to learn how all it's features work. I already like the built in search function and multiple panes. Also gonna check out all the plugins, [https://github.com/IgnorantGuru/spacefm/wiki/plugins/](https://github.com/IgnorantGuru/spacefm/wiki/plugins/)

If you want to try it out here is how to install it:

Add the developers repo to your sources.list, deb [http://ignorantguru.github.com/debian/](http://ignorantguru.github.com/debian/) unstable main

```
sudo gpg --keyserver keys.gnupg.net --recv-keys 0x01937621 0x107165A1
sudo bash -c 'gpg --export -a 01937621 107165A1 | apt-key add -'
sudo apt-get update
sudo apt-get install spacefm
```- it doesn't work! "can't locate package spacefm" - isn't it possible to just add a ppa?

[edit: this [http://igurublog.wordpress.com/downloads/ppa/](http://igurublog.wordpress.com/downloads/ppa/) seems to help]

third:
> **BrokenKingpin said:**
> Openbox is awesome, but still prefer a  full DE (Xfce). By the time I setup my full system I end up with  something that is pretty close to LXDE with a bunch of Xfce stuff. So I  find it easier just to run Xfce, which gives me everything I need and is  still pretty light.

I can definitely see why people run Openbox though,and why LXDE uses as  the default WM. Fast, configurable, and gets the job done.- i'm using xfce myself, replaced thunar with pcmanfm, trying spacefm now - so this sounds very intersting to me! care to elaborate?

---

### Post by urukrama on 2012-05-07
> **ohnonot said:**
> i wonder, does openbox (or fluxbox) use similar plugins, like bbinterface and slit and whatnot (see [here]("http://bb4win.sourceforge.net/plugins.html"))?

The "slit" in bb4win is the "dock" in Openbox. It is where the "dockapps" go. Most of these are fairly ugly or have an outdated aesthetic, but there are a few useful ones: docker (as a notification system/system tray), bbdock ([a simple dock]("http://urukrama.wordpress.com/2008/12/02/changing-the-size-of-bbdock/")), bbpager (as a desktop pager), lal/lalcal/tdc for a clock and calendar, etc.

Most dockapps were created for WindowMaker. You can find a lot of dockapps [here]("http://web.cs.mun.ca/~gstarkes/wmaker/dockapps/") and [here]("http://dockapps.windowmaker.org/").

You can also use panels, docks, and anything else you'd like to use in Openbox, even if those are not really Openbox "plugins". There is a slightly outdated list of such things in the Openbox guide linked to in my signature.

> **ohnonot said:**
> second:
- it doesn't work! "can't locate package spacefm" - isn't it possible to just add a ppa?

You should be able to do this just as you do so in Gnome or Unity or whatever else you're used to. If you use Openbox you just use a different window manager to manage your windows. Below that, everything else still works the same.

---

### Post by user1397 on 2012-05-07
> **chamber said:**
> In arch

```
pacman -S spacefm
```

It was in the AUR but got moved to Community.


[[img]http://img32.imageshack.us/img32/6097/newthemet.th.png[/img]](http://img32.imageshack.us/img32/6097/newthemet.png)

It's awesome.love your music choice in that screenshot :)

---

### Post by m_duck on 2012-05-07
Small contribution now: a BASH pipe menu (that gets rewritten after every install due to forgotten backups) to display some configs, ready for editing:
```

#!/bin/bash

editor="geany"
home_files=( .bash_aliases .bash_profile .bashrc .conkyrc .inputrc .vimrc .xinitrc .Xresources )
openbox_files=( autostart environment menu.xml rc.xml )

echo "<openbox_pipe_menu>"

echo "<separator label=\"Dotfiles\" />"

for i in "${home_files[@]}"; do
	tmpFN="$HOME/${i}"
	echo "<item label=\"${i}\">"
	echo "<action name=\"Execute\">"
	echo "<command>${editor} ${tmpFN}</command>"
	echo "</action>"
	echo "</item>"
done

echo "<separator label=\"Openbox\" />"

for i in "${openbox_files[@]}"; do
	tmpFN="$HOME/.config/openbox/${i}"
	echo "<item label=\"${i}\">"
	echo "<action name=\"Execute\">"
	echo "<command>${editor} ${tmpFN}</command>"
	echo "</action>"
	echo "</item>"
done

echo "</openbox_pipe_menu>"

```
Referenced in menu.xml as:```
<menu id="configs-menu" label="Configs" execute="/home/username/scripts/openbox/pipe-configs.sh"/>
```

---

### Post by mips on 2012-05-07
Any ideas on easily mounting partitions in SpaceFM, gvfs is installed. This is simple in Thunar but when using openbox I would prefer to use spacefm.

Btw, these drives/partitions don't appear in /etc/fstab. oh, and thunar will also remain installed.

---

### Post by BrokenKingpin on 2012-05-08
What do people have against Thunar... works great for me? Is it just that it does not support tabs?

---

### Post by mips on 2012-05-08
> **BrokenKingpin said:**
> What do people have against Thunar... works great for me? Is it just that it does not support tabs?

I love dual/triple pane file managers, just makes things so much easier.

Coming from Amiga back in the day with Directory Opus which is the best file manager I have ever used.

---

### Post by neu5eeCh on 2012-05-08
> **mips said:**
> I love dual/triple pane file managers, just makes things so much easier.

Same here. If Thunar were capable of double or triple pane file browsing, I would be more tempted to use it. [troll] The Thunar devs, however, are drooling "light weight" fetishists. It must have nearly killed the Luddites to make it anything but a command-line browser. [/troll]

---

### Post by mips on 2012-05-08
> **VTPoet said:**
> Same here. If Thunar were capable of double or triple pane file browsing, I would be more tempted to use it. [troll] **The Thunar devs, however, are drooling "light weight**" fetishists. It must have nearly killed the Luddites to make it anything but a command-line browser. [/troll]

Thing is Thunar is actually not that 'lightweight', it's actually pretty slow as well.

All I need in Openbox is for all my drives/partitions to be mounted and seen by SpaceFM. Removeable media should behave the same way as it does in any DE.

---

### Post by Lucradia on 2012-05-08
I'd use PCManFM even though it's only dual-pane (One for folders / files, one for tree, as per normal windows :V which I want.)

---

### Post by chamber on 2012-05-08
Arch laptop is in getting some work done so thought I would knock together a quick openbox arch vm to tide me over.

Clean and dirty pics below.

---

### Post by mips on 2012-05-08
Nice!

That Giant's Causeway in the back. Reminds me of table mountain in CT.

---

### Post by chamber on 2012-05-08
Thanks, I used to live near there when I went to uni.

---

