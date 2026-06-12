---
title: "Installing Flash Player the easy way in Linux, just a little trick of mine ;)"
date: 2007-10-05
forum: The Cafe
---

### Post by RAV TUX on 2007-10-05
I have found the easiest way to install the Flash Player is to simply go to the purevolume page and launch the purevolume player in Firefox.

[http://www.purevolume.com/](http://www.purevolume.com/)

Upon launching the player, it will prompt you to install the latest Flash Player and it does this with out fail in any Linux distro I use.
The bonus is you can listen to your favorite music that you have saved in purevolume.

I know there are other ways to do this but this has always worked for me and I enjoy listening to good music right away.

btw my purevolume page is:
[http://www.purevolume.com/listeners/oicurmt](http://www.purevolume.com/listeners/oicurmt)

If you sign up be sure and friend me ;)

---

### Post by smartboyathome on 2007-10-05
You can just go to any page. And, as of gutsy, this is the best way (I tried installing flash from the repos, didn't turn out too well).

---

### Post by RAV TUX on 2007-10-05
> **smartboyathome said:**
> You can just go to any page. And, as of gutsy, this is the best way (I tried installing flash from the repos, didn't turn out too well).

I do have to say that Ubuntu has fixed this problem incredibly.

unfortunately it does not work on every web page.

I was surprised when I came across a wma file and Xubuntu automatically prompted me to install the necessary codex and everything I need to play the file. Awesome work Ubuntu devs!

I'm using Xubuntu 7.04 just for reference.

---

### Post by forrestcupp on 2007-10-05
Any web page with Flash content works.  Firefox recognizes that it needs the Flash plugin and asks if you want to install it.  I think the fact that it's this much easier is because of the advancements of Firefox and the Firefox Flash plugin.

---

### Post by RAV TUX on 2007-10-05
> **forrestcupp said:**
> Any web page with Flash content works.  Firefox recognizes that it needs the Flash plugin and asks if you want to install it.  I think the fact that it's this much easier is because of the advancements of Firefox and the Firefox Flash plugin.I have come across many websites that it does not work on and it ask you to do a manual install well over 90%, not in Ubuntu but many other distros, but they may have been using an older version of Firefox.

---

### Post by epimer on 2007-10-05
```
pacman -S flashplugin
```

=P

---

### Post by RAV TUX on 2007-10-05
> **RAV TUX said:**
> 
I know there are other ways to do this but this has always worked for me and I enjoy listening to good music right away.
  

> **epimer said:**
> ```
pacman -S flashplugin
```=P

Awesome Thanks for the code, as stated in the OP, I know there are other ways to do this this I just do it out of habit. ;)

---

### Post by forrestcupp on 2007-10-05
> **RAV TUX said:**
> I have come across many websites that it does not work on and it ask you to do a manual install well over 90%, not in Ubuntu but many other distros, but they may have been using an older version of Firefox.

Well, I am using Gutsy, so that may be why it worked for me.  I keep forgetting that.

---

### Post by coffeecat on 2007-10-05
> **epimer said:**
> ```
pacman -S flashplugin
```=P

I was intrigued by this post, with no qualifying comment. 'pacman -S flashplugin' will certainly do the trick [in Arch Linux]("http://wiki.archlinux.org/index.php/Pacman"), but does any other distro use the pacman package manager? I've not come across one.

Just for fun I tried it in Feisty, and got:

```
****@feisty-amd:~$ pacman -S flashplugin
The program 'pacman' is currently not installed.  You can install it by typing:
sudo apt-get install pacman
Make sure you have the 'universe' component enabled
bash: pacman: command not found
****@feisty-amd:~$ 
```"Interesting," I thought. So I looked in Synaptic and, yes, there it is. The package description says:

> Chase Monsters in a Labyrinth
You are Pacman, and you are supposed to eat all the small dots to get to
the next level. You are also supposed to keep away from the ghosts,
if they take you, you lose one life, unless you have eaten a large dot,
then you can, for a limited amount of time, chase and eat the ghosts.
There is also bonus available, for a limited amount of time.
An X gives just points, but a little pacman gives an extra life.:lol:

Just thought I'd post in case an Ubuntu newbie wondered why it wouldn't work.

---

### Post by n3tfury on 2007-10-05
> **forrestcupp said:**
> Any web page with Flash content works.  Firefox recognizes that it needs the Flash plugin and asks if you want to install it.  I think the fact that it's this much easier is because of the advancements of Firefox and the Firefox Flash plugin.

yep, ever since feisty for me.  none of this manual garbage anymore.

---

### Post by RAV TUX on 2007-10-05
> **coffeecat said:**
> I was intrigued by this post, with no qualifying comment. 'pacman -S flashplugin' will certainly do the trick [in Arch Linux]("http://wiki.archlinux.org/index.php/Pacman"), but does any other distro use the pacman package manager? I've not come across one.

Just for fun I tried it in Feisty, and got:

```
****@feisty-amd:~$ pacman -S flashplugin
The program 'pacman' is currently not installed.  You can install it by typing:
sudo apt-get install pacman
Make sure you have the 'universe' component enabled
bash: pacman: command not found
****@feisty-amd:~$ 
```"Interesting," I thought. So I looked in Synaptic and, yes, there it is. The package description says:

:lol:

Just thought I'd post in case an Ubuntu newbie wondered why it wouldn't work.

That is very intriging I tried it and it installed PacMan for me automatically(enabled feisty/universe pacman)
```
ravtux@CafeLinux:~$ sudo apt-get install pacman
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  pacman
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.6kB of archives.
After unpacking 164kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com feisty/universe pacman 10-16ubuntu2 [29.6kB]
Fetched 29.6kB in 0s (39.4kB/s)
Selecting previously deselected package pacman.
(Reading database ... 159835 files and directories currently installed.)
Unpacking pacman (from .../pacman_10-16ubuntu2_i386.deb) ...
Setting up pacman (10-16ubuntu2) ...
```Now if they can only enable Emerge! ;)
```

ravtux@CafeLinux:~$ sudo apt-get install emerge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package emerge
```

---

### Post by yabbadabbadont on 2007-10-05
cokehabit actually had portage working on Ubuntu at one point but he didn't implement it correctly and borked his system.  Portage is almost entirely python by the way.  What he should have done, and I told him this on the Gentoo forums, was to modify portage so that it built a proper deb archive from the install image in the sandbox.  Then have it call dpkg or apt or aptitude to handle the actual install.

---

### Post by RAV TUX on 2007-10-05
This is funny so after installing pacman, I ran the command:

```
 pacman -s flashplugin
```Both with and without sudo, I get this:

```
ravtux@CafeLinux:~$ sudo pacman -s flashplugin
Password:
sudo: pacman: command not found
ravtux@CafeLinux:~$ pacman -s flashplugin
```;)

[[IMG]http://cafelinux.org/OptickleArt/albums/userpics/normal_snapshot14%7E0.png[/IMG]]("http://cafelinux.org/OptickleArt/displayimage.php?album=lastup&cat=0&pos=0")

A nice game of pacman would be fun...LOL!

---

### Post by Polygon on 2007-10-05
firefox tries to install it on ubuntu but it fails

in gutsy there is a firefox extension which will download the flashplugin-nonfree package from the repos if you try to run flash and dont have it installed. dunno if this applies to anything else (like java...)

---

### Post by yabbadabbadont on 2007-10-05
Just download the installer from Adobe and run it as your user, no need for sudo.  It will install the plugin into your ~/.mozilla/plugins directory and works fine.

---

### Post by Polygon on 2007-10-05
i find it easier to just do a 

```
sudo apt-get install flashplugin-nonfree
```

then it works for all browsers including opera

---

### Post by yabbadabbadont on 2007-10-05
> **Polygon said:**
> i find it easier to just do a 

```
sudo apt-get install flashplugin-nonfree
```

then it works for all browsers including opera

Except that it fails every time that Adobe releases a new version.  (at least until the maintainers update the md5sum check in the installer... ;))

---

### Post by RAV TUX on 2007-10-05
> **Polygon said:**
> i find it easier to just do a 

```
sudo apt-get install flashplugin-nonfree
```then it works for all browsers including opera

Thats the command I can never remember...Thanks I'll have to commit this to memory! ;)

```
ravtux@CafeLinux:~$ sudo apt-get install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.7kB of archives.
After unpacking 111kB of additional disk space will be used.
Get:1 http://security.ubuntu.com feisty-security/multiverse flashplugin-nonfree 9.0.48.0.0ubuntu1~7.04.1 [15.7kB]
Fetched 15.7kB in 0s (28.8kB/s)          
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 159843 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.0ubuntu1~7.04.1_i386.deb) ...
Setting up flashplugin-nonfree (9.0.48.0.0ubuntu1~7.04.1) ...
Downloading...
--17:44:03--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.130.70
Connecting to fpdownload.macromedia.com|72.247.130.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,608,602 (2.5M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  163.58 KB/s
   50K .......... .......... .......... .......... ..........  3%  132.06 KB/s
  100K .......... .......... .......... .......... ..........  5%  301.98 KB/s
  150K .......... .......... .......... .......... ..........  7%  183.31 KB/s
  200K .......... .......... .......... .......... ..........  9%  188.62 KB/s
  250K .......... .......... .......... .......... .......... 11%  183.49 KB/s
  300K .......... .......... .......... .......... .......... 13%  183.38 KB/s
  350K .......... .......... .......... .......... .......... 15%  188.58 KB/s
  400K .......... .......... .......... .......... .......... 17%  183.48 KB/s
  450K .......... .......... .......... .......... .......... 19%  188.79 KB/s
  500K .......... .......... .......... .......... .......... 21%  104.83 KB/s
  550K .......... .......... .......... .......... .......... 23%  825.23 KB/s
  600K .......... .......... .......... .......... .......... 25%  183.51 KB/s
  650K .......... .......... .......... .......... .......... 27%  188.59 KB/s
  700K .......... .......... .......... .......... .......... 29%  182.36 KB/s
  750K .......... .......... .......... .......... .......... 31%  183.20 KB/s
  800K .......... .......... .......... .......... .......... 33%  188.95 KB/s
  850K .......... .......... .......... .......... .......... 35%  183.34 KB/s
  900K .......... .......... .......... .......... .......... 37%  188.75 KB/s
  950K .......... .......... .......... .......... .......... 39%  183.46 KB/s
 1000K .......... .......... .......... .......... .......... 41%  188.62 KB/s
 1050K .......... .......... .......... .......... .......... 43%  183.55 KB/s
 1100K .......... .......... .......... .......... .......... 45%  188.78 KB/s
 1150K .......... .......... .......... .......... .......... 47%  183.22 KB/s
 1200K .......... .......... .......... .......... .......... 49%  183.59 KB/s
 1250K .......... .......... .......... .......... .......... 51%  188.64 KB/s
 1300K .......... .......... .......... .......... .......... 52%  183.51 KB/s
 1350K .......... .......... .......... .......... .......... 54%  153.42 KB/s
 1400K .......... .......... .......... .......... .......... 56%  236.14 KB/s
 1450K .......... .......... .......... .......... .......... 58%  188.65 KB/s
 1500K .......... .......... .......... .......... .......... 60%  183.46 KB/s
 1550K .......... .......... .......... .......... .......... 62%  188.59 KB/s
 1600K .......... .......... .......... .......... .......... 64%  183.54 KB/s
 1650K .......... .......... .......... .......... .......... 66%  183.51 KB/s
 1700K .......... .......... .......... .......... .......... 68%  188.77 KB/s
 1750K .......... .......... .......... .......... .......... 70%  183.33 KB/s
 1800K .......... .......... .......... .......... .......... 72%  188.63 KB/s
 1850K .......... .......... .......... .......... .......... 74%  183.51 KB/s
 1900K .......... .......... .......... .......... .......... 76%  188.59 KB/s
 1950K .......... .......... .......... .......... .......... 78%  183.51 KB/s
 2000K .......... .......... .......... .......... .......... 80%  188.77 KB/s
 2050K .......... .......... .......... .......... .......... 82%  183.34 KB/s
 2100K .......... .......... .......... .......... .......... 84%  183.53 KB/s
 2150K .......... .......... .......... .......... .......... 86%  120.00 KB/s
 2200K .......... .......... .......... .......... .......... 88%  413.33 KB/s
 2250K .......... .......... .......... .......... .......... 90%  188.78 KB/s
 2300K .......... .......... .......... .......... .......... 92%  183.51 KB/s
 2350K .......... .......... .......... .......... .......... 94%  188.64 KB/s
 2400K .......... .......... .......... .......... .......... 96%  183.32 KB/s
 2450K .......... .......... .......... .......... .......... 98%  188.58 KB/s
 2500K .......... .......... .......... .......... .......   100%  185.81 KB/s

17:44:17 (185.15 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [2608602/2608602]

Download done.
Flash Plugin installed.
```

---

### Post by madscientist on 2007-10-31
Every time I try this I get:
```
...
 6850K .......... .......... .......... .......... ..........100%   11.44 MB/s
 6900K                                                       100%    0.00 B/s

14:07:55 (11.02 MB/s) - `./install_flash_player_9_linux.tar.gz' saved [7065600/7065600]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
```
But then dpkg thinks it IS installed.  I've run "aptitude purge flashplugin_nonfree" and use locate to ensure I don't have any other instances of any files with "flashpl" or "flash_pl" in the name.

One thing that might be a problem: when I use wget to download the install_flash_player_9_linux.tar.gz file by hand (because the DEB package removes it again before exiting), I see that it's actually not a compressed file; it was either not compressed on the server or the retrieval process caused it to be uncompressed (I've seen this happen with some misconfigured web servers).

So, maybe the md5sum in the DEB is for the compressed version of this file, but somehow something has been changed so that the file it gets (despite the .gz extension) is not compressed any longer?

---

### Post by Polygon on 2007-10-31
someone else posted that if adobe releases a new version of the player, if you try to install it, it will fail because the md5sum is for the older version and your downloading the newer version

best way to get around is either to wait for the maintainer to update the package...or to just manually install it

---

### Post by madscientist on 2007-11-01
> **Polygon said:**
> someone else posted that if adobe releases a new version of the player, if you try to install it, it will fail because the md5sum is for the older version and your downloading the newer version

best way to get around is either to wait for the maintainer to update the package...or to just manually install itWell, I've been waiting since Gutsy was released, almost two weeks ago, and I'm not seeing anyone else complaining or any bugs filed.

But I discovered why: it's my company's web proxy solution they put in a month or so ago that's causing the problem  ](*,)

If I do the wget of the install package from my system at home it comes back just fine.  If I do it from my system at work, even though the filename still says .tar.gz, the file on my disk has been magically decompressed.  Thus, the md5sum fails and even if it didn't the unpack would fail since the file is not compressed any longer.  Sigh.

---

### Post by Gremlinzzz on 2007-11-01
I found that this command takes care of flashplayer and alott of other basic installs.
sudo apt-get install ubuntu-restricted-extras
to see which flashplayer it installs go too.
[http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)

---

### Post by madscientist on 2007-11-08
> **madscientist said:**
> But I discovered why: it's my company's web proxy solution they put in a month or so ago that's causing the problem  ](*,)

If I do the wget of the install package from my system at home it comes back just fine.  If I do it from my system at work, even though the filename still says .tar.gz, the file on my disk has been magically decompressed.  Thus, the md5sum fails and even if it didn't the unpack would fail since the file is not compressed any longer.  Sigh.If anyone else has this problem you can resolve it like this: first, get a "good" copy of the compressed tarball, using another site or similar.  Then install the flashplugin-nonfree package using something like: ```
sudo apt-get install flashplugin-nonfree
```It should ask you where to find the tarball; just enter the name of the file you downloaded.  If it doesn't ask you but just fails, then after it fails run:```
 sudo dpkg-reconfigure flashplugin-nonfree
``` and it will ask about the name of the file that time.

Run these commands from within a terminal program of course.

---

### Post by FuturePilot on 2007-11-08
I find this an easy way also
[Clicky]("apt://flashplugin-nonfree")
;)

---

### Post by bruce89 on 2007-11-08
> **FuturePilot said:**
> I find this an easy way also
[Clicky]("apt://flashplugin-nonfree")
;)

Or better yet, [Clicky]("apt://mozilla-plugin-gnash")

---

### Post by aysiu on 2007-11-08
> **bruce89 said:**
> Or better yet, [Clicky]("apt://mozilla-plugin-gnash")
I've had no luck getting Gnash to work properly.

---

### Post by bruce89 on 2007-11-08
> **aysiu said:**
> I've had no luck getting Gnash to work properly.

Depends what you need flash for.  Perhaps Firefox is Gutsy is buggered, but I never use it.

To be honest, flash things only a load of adverts.

---

### Post by Polygon on 2007-11-08
> **bruce89 said:**
> Depends what you need flash for.  Perhaps Firefox is Gutsy is buggered, but I never use it.

To be honest, flash things only a load of adverts.

unless you dont count youtube, google video, countless other stream videos, flash videos, website logins, other various things on websites

flash is a good invention, but it sucks how its a proprietary standard.

---

### Post by bruce89 on 2007-11-08
> **Polygon said:**
> unless you dont count youtube, google video, countless other stream videos, flash videos, website logins, other various things on websites

Youtube works on Gnash here, but it's not much to want to see anyway.

If a website uses flash to log in, it's not worth it.

---

### Post by mcduck on 2007-11-08
> **Gremlinzzz said:**
> I found that this command takes care of flashplayer and alott of other basic installs.
sudo apt-get install ubuntu-restricted-extras
to see which flashplayer it installs go too.
[http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)

Yes, ubuntu-restricted-extras would be really useful metapackage, its just that I believe it also installs acrobat reader :P

But I can't see any problem in either using apt-get or installing the plugin from Synaptic. After instaling a new Ubuntu system I'll need to install a bunch of codecs and other stuff from Synaptic anyway, so getting the flash plugin at the same time just makes more sense to me than any other way..

---

### Post by -grubby on 2007-11-08
I always install flash by playing a video at google video and it always asks me to automatically install it

---

### Post by bruce89 on 2007-11-08
> **mcduck said:**
> Yes, ubuntu-restricted-extras would be really useful metapackage, its just that I believe it also installs acrobat reader :P

But I can't see any problem in either using apt-get or installing the plugin from Synaptic. After instaling a new Ubuntu system I'll need to install a bunch of codecs and other stuff from Synaptic anyway, so getting the flash plugin at the same time just makes more sense to me than any other way..

Surely this meta package just installs a few packages which could be installed manually.

```
bruce@Scooby-Dum:~$ apt-cache depends ubuntu-restricted-extras 
ubuntu-restricted-extras
  Recommends: gstreamer0.10-plugins-ugly
  Recommends: gstreamer0.10-plugins-ugly-multiverse
  Recommends: msttcorefonts
  Recommends: flashplugin-nonfree
  Recommends: sun-java6-plugin
  Recommends: unrar
  Recommends: gstreamer0.10-plugins-bad
  Recommends: gstreamer0.10-plugins-bad-multiverse
  Recommends: gstreamer0.10-ffmpeg
  Recommends: liblame0
  Recommends: libdvdread3

```

---

### Post by yatt on 2007-11-08
> **forrestcupp said:**
> Any web page with Flash content works.  Firefox recognizes that it needs the Flash plugin and asks if you want to install it.  I think the fact that it's this much easier is because of the advancements of Firefox and the Firefox Flash plugin.That doesn't work on 64bit FF. But flashplugin-nonfree in the repos does.

---

### Post by mcduck on 2007-11-09
> **bruce89 said:**
> Surely this meta package just installs a few packages which could be installed manually.

```
bruce@Scooby-Dum:~$ apt-cache depends ubuntu-restricted-extras 
ubuntu-restricted-extras
  Recommends: gstreamer0.10-plugins-ugly
  Recommends: gstreamer0.10-plugins-ugly-multiverse
  Recommends: msttcorefonts
  Recommends: flashplugin-nonfree
  Recommends: sun-java6-plugin
  Recommends: unrar
  Recommends: gstreamer0.10-plugins-bad
  Recommends: gstreamer0.10-plugins-bad-multiverse
  Recommends: gstreamer0.10-ffmpeg
  Recommends: liblame0
  Recommends: libdvdread3

```

Hmm. No acroread there. I guess from this on I'll save a couple of seconds by installing that package instead of finding those included packages myself.. ;)

---

### Post by lawksalih on 2007-12-06
OK.  I am sorry to bring this up but as I was searching the forum for a solution, I am still having hard time resolving my flash issues.  I just downloaded Ubuntu 7.10 today and I have been a windows user for the past 10 years.  

So please assist me to solve this problem.  

Anytime I visit YouTube, I get a notification from FF to install the adobe flash plugn but then, I get this error message:

cannot find flashplugin-nonfree

I would appreciate any assistance.  

Best,

Lawk Salih

---

### Post by yatt on 2007-12-06
> **lawksalih said:**
> OK.  I am sorry to bring this up but as I was searching the forum for a solution, I am still having hard time resolving my flash issues.  I just downloaded Ubuntu 7.10 today and I have been a windows user for the past 10 years.  

So please assist me to solve this problem.  

Anytime I visit YouTube, I get a notification from FF to install the adobe flash plugn but then, I get this error message:

cannot find flashplugin-nonfree

I would appreciate any assistance.  

Best,

Lawk Salih
Search the repos for flashplugin-nonfree. It is in Universe/Multiverse IIRC.

---

### Post by lawksalih on 2007-12-06
Will do, thanks.

---

