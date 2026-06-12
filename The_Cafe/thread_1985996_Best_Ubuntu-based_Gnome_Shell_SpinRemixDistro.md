---
title: "Best Ubuntu-based Gnome Shell Spin/Remix/Distro???"
date: 2012-05-24
forum: The Cafe
---

### Post by drawkcab on 2012-05-24
I just came across Luninux the other day:

[http://luninuxos.com/](http://luninuxos.com/)

It's been a while since I've done any serious distrohopping.  Are there any other solid Ubuntu spins or distros focused on Gnome shell? I'd like to try whatever's out there.

---

### Post by markbl on 2012-05-24
> **drawkcab said:**
> Are there any other solid Ubuntu spins or distros focused on Gnome shell? I'd like to try whatever's out there.
Install ubuntu 12.04 and then type "sudo apt-get install gnome-shell". Personally I think it is currently the best debian based gnome-shell experience.

---

### Post by sikander3786 on 2012-05-24
Official Gnome Shell Spin will be available along with Ubuntu 12.10 and later:

[http://www.tuxgarage.com/2012/05/quantal-quetzal-plans-uds-q-summary.html](http://www.tuxgarage.com/2012/05/quantal-quetzal-plans-uds-q-summary.html)

And probably this is the one that inspired them:

[http://ubuntu-gs-remix.sourceforge.net/p/home/](http://ubuntu-gs-remix.sourceforge.net/p/home/)

---

### Post by drawkcab on 2012-05-24
> **markbl said:**
> Install ubuntu 12.04 and then type "sudo apt-get install gnome-shell". Personally I think it is currently the best debian based gnome-shell experience.

Yeah, that's what I've been doing on a couple of my systems.  I was just wondering if anyone else out there has been creatinging anything above and beyond the vanilla Gnome Shell experience like Luninux.

---

### Post by neu5eeCh on 2012-05-24
:popcorn: I just asked [this very same question]("http://ubuntuforums.org/showthread.php?t=1983874") about a day or two ago.  Might as well combine the threads.

I've done some looking around since asking. Some of the *most interesting* (though maybe not the best) are:

[Pear OS]("http://pearlinux.fr/") -- The latest edition, Comice, is still in Beta I think.
[Linux Deepin]("http://www.linuxdeepin.com/") -- This is a Chinese distro with much Gnome tweakage. 
[Pinguy OS]("http://feedproxy.google.com/%7Er/webupd8/%7E3/s9eZTPHsuFc/pinguy-os-1204-beta-available-for.html?utm_source=feedburner&utm_medium=email") -- Just released, today, a Beta based on 12.04. Pinguy is a favorite of a lot of users here.
And then there's Linux Mint, but they've moved and put their effort into Cinnamon and Mate.

Distros like Fedora and Opensuse, as far as I know, simply use the stock Gnome Shell install. Linux Deepin has gotten the most buzz, especially because of its Software Manager (which is available on Ubuntu via PPA, I think). (By the way, the four distros listed above are all Ubuntu based.)

---

### Post by AllRadioisDead on 2012-05-24
Why don't you just customize Ubuntu?

---

### Post by HansKisaragi on 2012-05-24
Linux Mint.. or better yet.. just install Cinnamon on Ubuntu.

---

### Post by neu5eeCh on 2012-05-24
> **AllRadioisDead said:**
> Why don't you just customize Ubuntu?

The point is that some distros have taken the customization further than simply adding extensions from the Gnome Extensions Page; and further than the average user's know-how. It's interesting to see how Gnome has been tweaked by the pros to make it more amenable.

---

### Post by drawkcab on 2012-05-24
> **VTPoet said:**
> The point is that some distros have taken the customization further than simply adding extensions from the Gnome Extensions Page; and further than the average user's know-how. It's interesting to see how Gnome has been tweaked by the pros to make it more amenable.

That's just what I was thinking.  Thanks for your help.  I really liked what pinguy OS has done recently so maybe I will give it a spin too.

---

### Post by drawkcab on 2012-05-24
> **Viiral said:**
> Linux Mint.. or better yet.. just install Cinnamon on Ubuntu.

I ran Cinnamon on Ubuntu 11.10 for a month or so.  I didn't like it because it was sluggish but maybe I'll give it another shot soon.

---

### Post by Copper Bezel on 2012-05-24
[QUOTE=drawkcab]Yeah, that's what I've been doing on a couple of my systems. I was just wondering if anyone else out there has been creatinging anything above and beyond the vanilla Gnome Shell experience like Luninux.[/QUOTE]
On 11.10, I had to remove nm-applet from autostart and remove the notify-osd package. I don't know whether or not this is still necessary on 12.04, because I upgraded rather than doing a fresh install. nm-applet doesn't mess up networking or interfere with the new widget, but it sends notifications that aren't marked as non-persistent, and notify-osd is inconsistent. Those are the only problems I've noted in stock Shell on stock Ubuntu.

It would be nice to see distros take advantage of the extension base to distinguish themselves, but most seem apt to do something more drastic (like Ubuntu, or even Mint) or prioritize keeping things stock.

---

### Post by markbl on 2012-05-24
> **Copper Bezel said:**
> On 11.10, I had to remove nm-applet from autostart and remove the notify-osd package.
I know the problems that notify-osd causes in gnome-shell in 11.10 but removing notify-osd is drastic because it breaks Unity. A better fix in 11.10 is just to type:
```

echo '[ ${DESKTOP_SESSION#ubuntu} = $DESKTOP_SESSION ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy

```
The above stops notify-osd from functioning in anything other than Unity (and Unity 2D) sessions. So both Unity and gnome-shell work properly with this one liner fix.

All this is fixed in 12.04 though so this fix is not needed anymore.

The only 12.04 Unity induced gnome-shell bug that I know of is [bug 965921]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/965921") which is quite annoying and sadly shows a disregard by Ubuntu towards gnome-shell.

---

### Post by Copper Bezel on 2012-05-25
Oh hey, cool. Thanks for the info. My old fixes aren't needed anymore, which is good to know, and thanks to you link to the bug report, I got to fix my keyboard shortcuts. (I was unpleasantly aware that my Metacity-related shortcuts weren't sticking, but I couldn't find the problem.) I'm not too worried about the deeper implications of Ubuntu shipping with a bug like that, but you're right that it's a bad showing for an LTS, at the very least. Still, Gnome 3.4 was one of the reasons (maybe the reason) I upgraded, so I'm actually glad that they didn't play too conservative. (Well worth the minor inconvenience for me.)

My Unity seems broken anyway, but I can't tell whether it's a feature or a bug. = P For instance, clicking items in the Launcher with my trackpad doesn't actually work; it's interpreted as a drag if there's *any* movement of the cursor whatsoever, so I have to use the mouse button. Passing strange.

Edit: I also have Maximize Vertically as the double-click titlebar action now, which almost makes up for the loss of the resize handles on GTK2 apps. So thanks again for pointing me there. = D

---

### Post by drawkcab on 2012-05-30
Finally getting around to installing LuninuX on my x120e.  It's pretty slick so far.  Going to try Pinguy next week.

---

### Post by wilee-nilee on 2012-05-30
You might try fedora it has a gnome-shell version.

---

### Post by szymon_g on 2012-05-30
> **drawkcab said:**
> Are there any other solid Ubuntu spins or distros focused on Gnome shell? I'd like to try whatever's out there.

Just get Fedora :) new version was released yesterday

---

### Post by PC_load_letter on 2012-06-01
> **drawkcab said:**
> I ran Cinnamon on Ubuntu 11.10 for a month or so.  I didn't like it because it was sluggish but maybe I'll give it another shot soon.

Cinnamon 1.4 is much better and now comes with neat effects. I would like it to consume less resources and be more stable, but as of now it is very usable. I installed Mint 13 and it's just awesome w/ Cinnamon.

---

### Post by forrestcupp on 2012-06-01
> **sikander3786 said:**
> Official Gnome Shell Spin will be available along with Ubuntu 12.10 and later:

[http://www.tuxgarage.com/2012/05/quantal-quetzal-plans-uds-q-summary.html](http://www.tuxgarage.com/2012/05/quantal-quetzal-plans-uds-q-summary.html)

That's great news. That's one big thing that would get me to do a clean install, rather than an upgrade.

---

### Post by stlouisubntu on 2012-10-17
> **PC_load_letter said:**
> Cinnamon 1.4 is much better and now comes with neat effects. I would like it to consume less resources and be more stable, but as of now it is very usable. I installed Mint 13 and it's just awesome w/ Cinnamon.


Ubutntu Cinnamon Remix has now been released! It is based on Ubuntu 12.04.1 with the cinnamon desktop as default, classic panel configuration (two panels), weather applet preinstalled, multimedia codecs and plug-ins included, and xscreensaver preinstalled as well.  For maximum compatibility the 32-bit version uses the non-pae kernel (also only non-gl screensavers.) The 64-bit version is also available. During the install, be sure to select the hard drive MBR (the default choice will likely be the usb stick from which you are installing &#8212; Ubuntu upstream bug.) Features Cinnamon 1.6.1

[http://sourceforge.net/projects/cinnamon-remix/files/](http://sourceforge.net/projects/cinnamon-remix/files/)

:)

---

### Post by drawkcab on 2012-10-18
I've just been using the gnome shell respin of 12.04 on my htpc and it's been great.  

I need to upgrade my primary laptop and netbook but I'm going to wait bit to see what 12.10 offers.

---

