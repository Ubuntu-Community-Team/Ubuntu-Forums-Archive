---
title: "Ubuntu is very heavy on my (not too old) laptop . :("
date: 2006-07-11
forum: The Cafe
---

### Post by darwish on 2006-07-11
Hi Everybody. Please don't consider this a flame on Ubuntu. I love it and I hope the best for it. I am a Debian and Linux from scratch user for a year now. After all the good talk about Ubuntu on the net, I decided to install it and be a Ubuntu developer if I liked it.

Well, It seems a huge work from the community, I really loved it. 

I have a Dell D505 laptop with a:
* Pentium-M 1.5 GHz, 1MB L2 cache
* 512MB 333MHz Ram
* 1.5 GB swap space
* Integrated 64Mb i810 video card

As you see it's not too old. I think Ubuntu should work with a good speed on it as LFS, Debian and XP do. But really Gnome shipped with Ubuntu is bloated. Here's the results:

* Nautilus takes about a second to view any folder, even if the folder has files with no thumbnails.
* when moving any window above the desktop icons, They got erased and redrawn after a while.
* Any program even a small game like Nibbles takes about 2 seconds to load !
* Gnome menues takes a while to load icons when viewing the menu the first time
* Rythimbox and totem takes about 3 seconds to begin playing a song.
* Moving any big window above a smaller window erase the small window (becomes totally white) for a while
* Moving a window quickly makes it move in pieces. (moving it slowly activate the new metacity option of tilting the lower part of the window a little as XGL do)

As you can see, The overall speed of the system is very low. Comparing above results with the latest Debian Stable (Gnome 2.6) and LFS (Gnome 2.14) I use.

* Nautilus takes no-time to view any folder even if the folder has a lot of pics and videos (displaying thumbnails).
* Most of other programs opens in no-time except OpenOffice as all the community know.

I even tried to disable displaying pics/videos thumbnails, disabling location bar and the "trackerd" daemon in Ubuntu's Nautilus. But it's still bloated.

To be fair, I also tried Ubuntu 6.06 on a new friend's laptop. 
It's a Lenovo 3000 N100 with Intel Duo and 512 Ram. I was very surprised!, It has even been much slower than my old laptop and Nautilus takes a long long time to view folders. Even gedit takes time to open !.

anyway, Iam tryin to track the problem and fix it if I can. (The Open Source way ;)). I thought it's a problem in the i810 Xserver module but direct rendering is working fine with 700 Fps in glgears!.

Bottomline: Ubuntu is too sexy and easy but it's much heavier than other distros (I know it's much better than them) and even heavier than XP.

Love u all.
-----------------
Edit:
Strangely Enough, I've found that Xorg uses the vesa instead of the i810 module. Using the i810 module, All the bad graphical effects mentioned above disappeared. 
```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo sed -i 's/vesa/i810/g' /etc/X11/xorg.conf
```

---

### Post by MetalMusicAddict on 2006-07-11
Thats too bad sir. Im running Dapper on:
[LIST]
[*]Dell inspiron 2200
[*]Celeron 1.4
[*]768megs RAM
[*]no swap
[*]Integrated 64meg (maybe 32) i810 video card
[/LIST]

Very base model. $600 and honestly it runs fine. Ive turned off alot of unneeded services also. Maybe try this?

Ive recently fell in love with Xubuntu though and I think Im gonna put it on the laptop. Might be an option for you? Comming from LFS though *every* binary distro might seem slow. :)

---

### Post by K.Mandla on 2006-07-11
I second that. Xubuntu is the only way to go. I run it on a 1.7Ghz 1Gb machine and a 750Mhz 512Mb machine, and have no problems whatsoever. I save Gnome for the 2Ghz+ machines.

---

### Post by daniel of sarnia on 2006-07-11
I have a dell D500, slower then you're laptop buy a bit. I really have not had any of kind of truble with it. I use KDE through, however I had gnome on it with xgl too. So I really don't think it's a ubuntu problem.

---

### Post by daniel of sarnia on 2006-07-11
forgot to say that in contrast, it runs faster then windows XP did on my laptop. I did put 700 MB of swap on it. It only has 256 MB of ram, 64 of it is shared with video and it's only a 1.3 Ghz cpu.

---

### Post by kop316 on 2006-07-11
That is really strange. 
I have a 1.3 Ghz Celeron processor, 256 mb RAM, 9200 radeon PCI (yes only PCI) card, and 2 GB swap, and Ubuntu flys on it, even when I have 5 gdesklets running. The only time it is slow is when I run Limewire (I think the Java is the issue). 
Maybe the reason I think it's fast is because all I have for comparision is when I used to run XP on this (now there was a bloated nightmare).

---

### Post by djsroknrol on 2006-07-12
I'm sorry for rehashing this, but I just posted on another sub forum that I just put Dapper on my T21 Thinkpad (was running Breezy just fine). It's an 800Mhz 128 MB Ram and it's not running that bad...and everything worked OOTB, unlike Breezy, where my Eth0 needed tweaking because of the 3com ethernet adapter.In fact, I'm using it now....Dapper continues to suprise me...

---

### Post by jnev on 2006-07-12
try KDE. I'm running kubuntu on a 366mhz pentium 2 with 256mb ram, and it runs just fine. I tried xubuntu and it was faster (not by much though), but I didn't like xfce. on boot kde only uses 52mb of ram (!).

---

### Post by LostInSwiss on 2006-07-12
> **djsroknrol said:**
> I'm sorry for rehashing this, but I just posted on another sub forum that I just put Dapper on my T21 Thinkpad (was running Breezy just fine). It's an 800Mhz 128 MB Ram and it's not running that bad...and everything worked OOTB, unlike Breezy, where my Eth0 needed tweaking because of the 3com ethernet adapter.In fact, I'm using it now....Dapper continues to suprise me...

I am also using ThinkPad T21 (same specs). But I have exactly the problems described by the thread owner ](*,) . If anyone figures this out please say. Nice to hear suggestions about other distributions but don’t people always say how Linux is great because you don’t have to keep re-installing like with windows?

---

### Post by prizrak on 2006-07-12
Try looking at your system monitor, there is a bug that makes gnome-cups-icon take up 100% of the CPU you might be experiencing that. I am not entirely sure how to turn it off as it restarts but if you make a topic on the forum someone should be able to help you.

---

### Post by Johnsie on 2006-07-12
There's a few ways to speed up your gnome desktop:

> sudo gconf-editor /apps/nautilus/preferences

When that comes up.. uncheck the show_desktop box

That stops nautilus from managing the icons on your desktop. If you really need your icons you can use another lighter desktop manager to show them


Another way I've heard that might speed things up a little is: 
(in terminal)
> sudo gedit /etc/sysctl.conf


and add the line:
> vm.swappiness=10

If these methods work you should see some improvement after reboot.

---

### Post by K.Mandla on 2006-07-12
> **K.Mandla said:**
> I second that. Xubuntu is the only way to go. I run it on a 1.7Ghz 1Gb machine and a 750Mhz 512Mb machine, and have no problems whatsoever. I save Gnome for the 2Ghz+ machines.
I should append this to say that while Gnome will run on these machines, I find it less snappy than XFCE. So I don't use Xubuntu because I *can't* so much as *I want to*. Just so I'm clear. :D

---

### Post by ubuntu_demon on 2006-07-14
> **Johnsie said:**
> 
Another way I've heard that might speed things up a little is: 
(in terminal)

sudo gedit /etc/sysctl.conf

and add the line:

vm.swappiness=10

If these methods work you should see some improvement after reboot.

In my personal experiences the default vm.swappiness=60 is okay for most users who don't like tweaking.

You'll get a bigger speed improvement by using icewm / fluxbox instead of default xubuntu(which uses xfwm4 as a window manager) if you want to sacrifice (some) ease of use for a lighter memory foot print. You don't need to reinstall. Just install either fluxbox or icewm on top of xubuntu and choose it from the "sessions" option in your login screen (gdm).

icewm and fluxbox are both lighter than xubuntu. They both use little memory and diskspace. It's a matter of taste which one you like more. If you want to go for the Ubuntu gnome look I recommend icewm with the icebuntu theme ( [http://themes.freshmeat.net/projects/icebuntu](http://themes.freshmeat.net/projects/icebuntu) )

You can icewm install it by :
$sudo apt-get install icewm 

To get more useful stuff for icewm :
$sudo apt-get install iceconf iceme menu  icewm-themes icepref

For fluxbox :
$sudo apt-get install fluxbox
To get more useful stuff for fluxbox :
$sudo apt-get install menu fluxconf 

log out of gnome and choose a fluxbox/icewm session from gdm.

Also try opera (from the new dapper commercial repository) instead of firefox. You should go to the preferences dialog of opera in order to make sure it doesn't use too much memory for caching(tools->preferences->advanced->history->memory cache->off). I think opera uses less memory than firefox after having it running for a while.

If you decide to go for even more tweaking. Now is the time for some swappiness tweaking :

In my case I have 1 gb of memory and a large part isn't used (or only used for cache) I choose to prevent swapping as much as possible by vm.swappiness=0. For 512 mb of memory this is also the best setting if you use xubuntu and be careful (about not using too much memory).

This was the best setting for laptop with only 64 mb of memory running icewm / fluxbox : vm.swappiness=100. Because with that amount of memory swapping is needed anyway so better to do it as soon as possible.

In cases between 128 mb and 512 mb of memory you need to try and tweak and find out what works best for you. You can use "$free -m" to see whether swap is used.

-If you (almost) succeed in not using swap at all then set vm.swappiness to 0 

-if your computer still needs to swap much set vm.swappiness to 100

-if you don't notice any difference go for vm.swappiness=60

You can find more information about "free -m" and swappiness here :
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by oss_monkey on 2006-07-15
> **ubuntu_demon said:**
> You'll get a bigger speed improvement by using icewm / fluxbox instead of xubuntu if you want to sacrifice (some) ease of use for a lighter memory foot print.

...

You can icewm install it by :
$sudo apt-get install icewm 

To get more useful stuff for icewm :
$sudo apt-get install iceconf iceme menu  icewm-themes icepref

For fluxbox :
$sudo apt-get install fluxbox
To get more useful stuff for fluxbox :
$sudo apt-get install menu fluxconf 

Thanks for these tips! I realized that I put some premium on the GUI, so I decided to stick with Xfce.

My problem is: how do I remove these things? Should I simply type:
$sudo aptitude remove iceconf iceme menu  icewm-themes icepref
... and repeat in reverse order? :-k

Thanks in advance.

---

### Post by ahaslam on 2006-07-15
> **darwish said:**
> I have a Dell D505 laptop with a:
* Pentium-M 1.5 GHz, 1MB L2 cache
* 512MB 333MHz Ram
* 1.5 GB swap space
* Integrated 64Mb i810 video card
I have a very similarly specked laptop and have the same bloated feeling while running Dapper. I have also tried xubuntu & kubuntu, strangely xfce was a lot slower than gnome but kde seemed a little snappier. I stayed with gnome because it's my favourite and Ubuntu because it's by far the best  OS for my needs. I do wish that it was more responsive when using the menus and browsing files & folders.


Tony.

---

### Post by fuscia on 2006-07-15
you could try using bum to shut off some of the stuff you don't need running.

---

### Post by ubuntu_demon on 2006-07-15
> **oss_monkey said:**
> Thanks for these tips! I realized that I put some premium on the GUI, so I decided to stick with Xfce.


I added some desktop performance tweaks on my blog :
[http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/](http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/)

The CFQ tweak might be nice.

Prelinking IMHO makes no sense if you have little memory and a slow harddrive becuase then prelinking will take ages.

The vm.swappiness tweak might be nice if you have problems with swapping (a lot of swapping going on on moments you don't like)

The gnome tweak is for gnome and therefor not relevant :)

> **oss_monkey said:**
> 
My problem is: how do I remove these things? Should I simply type:
$sudo aptitude remove iceconf iceme menu  icewm-themes icepref
... and repeat in reverse order? :-k

Thanks in advance.

The order doesn't matter as long as you mention them all. You can also leave it on your system as it takes very little space and will cost you no performance at all.

On a side note :
There might be a couple of packages that were installed as dependencies left on your system but if that's the case don't worry about them because they will only take very little space and won't slow your system down. You can use debfoster / deborphan / gtkorphan to clean leftover libraries and dependencies in general. But it is an advanced topic which is more suitable to power users and you don't need to do it (though I can help you if you insist on it).

---

### Post by ahaslam on 2006-07-15
> **fuscia said:**
> you could try using bum to shut off some of the stuff you don't need running.
Thanks Fuscia, that's a great little app.
I removed some unwanted services & Nautilus now seems a little quicker when opening large system folders. ;) 

Thanks again, 

Tony.

---

### Post by fuscia on 2006-07-15
my pleasure, tony.

---

### Post by chestnut1969 on 2006-07-17
Try a Debian SID [unstable] net install, add only packages that you need, and recompile the kernel.

Works a treat on my old Dell Laptop.

Cheers

---

### Post by thinklife on 2006-11-14
Gedit took time to load!!!
My slow computer takes 4 seconds to load that.
So you should be pretty happy that you have a pretty fast computer.
But of course in my case my com is 1113 mhz and only 256 mb of ram....
Sad.....
And slow.....

---

### Post by Sef on 2006-11-14
So if it is slow, try Xubuntu.  My laptop is 128 mb ram and 700 MHz and it flies with Xubuntu.

---

### Post by mips on 2006-11-14
You could also do a ubuntu server install and then add X, Gnome/KDE/XFCE/Fluxbox or what ever tickles your fancy and then add your apps. Do not use the Ubuntu/Kubuntu Desktops as they are the full shebang of stuff

---

