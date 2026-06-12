---
title: "KXStudio 10.04 LiveDVD is the only distro that Works."
date: 2012-01-31
forum: Ubuntu Studio
---

### Post by JuanPabloCuervo on 2012-01-31
Hi...
after testing a lot...
KXStudio LiveDVD 10.04.3 its the only linux distro that everything works & without effort.

[http://www.linux23.com/torrent/kxstudio-10-04-3-livedvd-32bit:7888a3eb91c426986789b59ec810e615a8e98e9b](http://www.linux23.com/torrent/kxstudio-10-04-3-livedvd-32bit:7888a3eb91c426986789b59ec810e615a8e98e9b)
[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/KXStudio-57237.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/KXStudio-57237.shtml)

[http://www.linux23.com/torrent/kxstudio-10-04-3-livedvd-64bit:3b6974499f68e7af5a40aabe05b53bc3e46f8931](http://www.linux23.com/torrent/kxstudio-10-04-3-livedvd-64bit:3b6974499f68e7af5a40aabe05b53bc3e46f8931)

**things i like:**
its an Ubuntu with a Kubuntu-Desktop = most ATI fglrx drivers work, up to 12.11. with 2.6.35-32-generic
11.12 only works with Natty. 2.6.38-8-generic

**things i don't like:**
can't be upgrated to 10.10 or 11.04 natty.
there is no 10.10 LiveDVD.

**tested:...**
AV Linux 5.0.1 
64Studio v3 "great RT Kernel, but no ext4 support, minimalistic"
Ubuntu 11.04 "installing Kubuntu-Desktop and KXStudio Repos, regsvr32 wineasio.dll, weird issues with flash player, alsa-tools-gui hdsp9632 mixer, etc..."
Kubuntu "No ATI driver support"
TangoStudio1.1 "great RT Kernel, weird update issues"
UbuntuStudio 32&64-Bit, 10&11, "weird issues, no network, no WiFi RTL8187"
KXStudio 10.10 & 11.04 Netboot isos, "useless"
Ubuntu 11.10 "useless"
& many others i cant remember...
[http://linux-sound.org/distro.html](http://linux-sound.org/distro.html)

Thanks to all KXStudio developers.


P.S. if you like KXStudio LiveDVD as much as i do... please seed.

some links:
[http://www.linuxmusicians.com/viewtopic.php?f=24&t=2609&p=12087&hilit=kxstudio+livedvd#p12087](http://www.linuxmusicians.com/viewtopic.php?f=24&t=2609&p=12087&hilit=kxstudio+livedvd#p12087)

---

### Post by 0p7 0u7 on 2012-01-31
Those torrents are giving an unregistered torrent error from the tracker.

---

### Post by 0p7 0u7 on 2012-01-31
Does Wineasio work out of the box? That's all I really need.. And does anyone have a working link?

---

### Post by JuanPabloCuervo on 2012-01-31
KXStudio 10.04.3 both 32bit & 64bit
let me know if this works...

P.S. with KXStudio everything works,
 make a fresh install, 
Primary Partition:
 ext4
 / 
grub: /dev/sda, 
just for the OS, arround 180GB is more than enough.
make a second Linux Swap partition of 10GB,
and a 3rd ext4 partition to keep files there. >800GB. 
the 3rd partition can be NTFS or HFS+ for compatibility, but ext4 is better anyway... 

install & update always using synaptic package manager, forget about muon, kpackage, apt-get.
select us or global server in repos. software sources.

the KXStudio logo looks lo-fi ...

if you have a FullHD display and see letters too small...
Try KXStudio, and adjust Font Size in application/appareance in system Settings, the last option is: Force Fonts DPI to 120dpi,
before Installing KXStudio.

---

### Post by 0p7 0u7 on 2012-01-31
That torrent has no trackers, KX sounds exactly like what I'm looking for. Haven't found a good copy on google either.

---

### Post by JuanPabloCuervo on 2012-02-01
try again:
[ed2k://|file|KXStudio_10.04.3-LiveDVD_32bit_64bit.rar|3717141089|DC98B6EE2212A73249B044110C781CE2|/]("ed2k://|file|KXStudio_10.04.3-LiveDVD_32bit_64bit.rar|3717141089|DC98B6EE2212A73249B044110C781CE2|/")

[magnet:?dn=KXStudio_10.04.3-LiveDVD_32bit_64bit.rar&xt=urn:ed2k:dc98b6ee2212a73249b044110c781ce2&xt=urn:ed2khash:dc98b6ee2212a73249b044110c781ce2&xl=3717141089]("magnet:?dn=KXStudio_10.04.3-LiveDVD_32bit_64bit.rar&xt=urn:ed2k:dc98b6ee2212a73249b044110c781ce2&xt=urn:ed2khash:dc98b6ee2212a73249b044110c781ce2&xl=3717141089")

[ed2k://|file|KXStudio_10.04.3-LiveDVD_32bit_64bit.rar|3717141089|DC98B6EE2212A73249B044110C781CE2|h=BSKUJZ4W7KEODABO343JZXS4DIH7IBY3|/]("ed2k://|file|KXStudio_10.04.3-LiveDVD_32bit_64bit.rar|3717141089|DC98B6EE2212A73249B044110C781CE2|h=BSKUJZ4W7KEODABO343JZXS4DIH7IBY3|/")

---

### Post by sgx on 2012-02-01
> **JuanPabloCuervo said:**
> Hi...
after testing a lot...
KXStudio LiveDVD 10.04.3 its the only linux distro that everything works & without effort.

This may be true for your particular computer setup, but will
not hold true for the masses. You got lucky, a nice side effect
excellent research :)

There is too wide a variety of hardware, and too few man-hours
to code support all the possible combinations. I made one of those
KX live dvds awhile back, and also found it to be excellent.
Cheers

---

### Post by JuanPabloCuervo on 2012-02-01
> **sgx said:**
> This may be true for your particular computer setup, but will
not hold true for the masses. You got lucky, a nice side effect
excellent research :)

There is too wide a variety of hardware, and too few man-hours
to code support all the possible combinations. I made one of those
KX live dvds awhile back, and also found it to be excellent.
Cheers

KXStudio works great with:
Asus Rampage 3 Extreme X58 i7 920, 12GB DDR3 Kingston
RME hdsp9632 (soundcard)
ATI HD6970 (video card.=) had a HD4650 but sold it.
LG DVD
HDDs. Hitachi Ultrastar
Microsoft USB Wireless Keyboard 1000 & Wireless Optical Mouse 2000.

i have other Laptops Gateway & HP with Kubuntu & Ubuntu, Nvidia & ATI,
agree, PulseAudio is better for Laptops & on-board audio.

i do have other board, MSI X58 Eclipse.. but no PSU, no CPU, no GPU,
could test there.

Snow Leopard "works" up to 10.6.7, from then problems start.
HD6970 is only supported with Lion .kext 10.7.x :(, 
& OSX not able to merge folders or ask if want to replace or rename "keep both files" is useless for me.
i dont want to buy an HD_5870, just because OSX.
i want HD7970.

anyway...
i like Ubuntu 11.04 with Kubuntu Desktop more than OSX & Windows.
sadly, the KXStudio Maveric -generic kernel is not as responsive as OSX Darwin Kernel,
i need a -generic Kernel because the ATI drivers. 
"i hear easy, audio clicks&pops when closing windows, while fullhd video is playin & Browsing."

software only developed for OSX is better, 
QuickTime Player for example, for Windows sounds inferior than WMP10/11, but for OSX sounds better than VLC,
WMP9 for OSX only supports WMA WMV files. :(

soundcard drivers exept Jack are better in OSX.
VLC for Linux sounds inferior, even with Oversmapling. 
but i dont think its a Linux fault,.
need more testing.
WMP9/10 in Wine barely works, but sounds nice. specially with ac3filter

the 11.04 Natty: 2.6.38-8-generic #42-Ubuntu SMP x86_64 x86_64 x86_64 GNU/Linux.

is much better, but still i hear small clicks & pops sometimes with audio & fullhd video is playing while browsing the net "the grid".

VLC-->Jack-->qjackctl
buffer size 512, 96khz, 2 cycles, 256 ports, 500ms.
5.1 audio--> mixed in DSP.

i havent found a better distro, i wish it could update to 10.10, everything works "out of the box".
i dont like much the KXStudio Desktop/Logo, but can be solved with:
$ sudo apt-get install kubuntu-desktop

the only things i dont like about Linux is that,
ext4 eats too much CPU moving big files, OSX is CPU-less.
but ext4 is faster than NTFS anyway...

Kubuntu System Monitor eats too much CPU, graphics have a slow refresh rate.
Ubuntu System Monitor is smooth,
Activity Monitor in OSX its not as eye candy, but also low CPU.

---

### Post by hebjuzeb on 2012-02-02
Hi, I'm having the same trouble as most people in the thread. It's a paradox: KXStudio has the reputation of solving the many Jack/routing headaches and making things easier, but it's a nightmare to install from the repositories. So my understanding is they only released the one liveCD, and now it's impossible to find? If anyone can point me to a working iso (tried Juan's and at least it doesn't show an error, but it's not loading) I'll seed. Or, if anyone knows where to find instructions that might make sense to a nube, please let me know.

PS, what am I missing? Is there some reason KX makes people install a virgin Ubuntu, manually replace the kernel, and add all the software from 3rd party repositories?

God I miss Reaper.

---

### Post by sgx on 2012-02-02
Hi, KX Studio dev has moved on to creating a great set of audio
tools that will work in most distros, and is not actively
updating the KX Distro, as fine a work as it is. (Falk, if I
am blowing smoke, please correct this ;) )

People seem to settle on a particular ubuntu that works for their setup,
or audio specialties Tango Studio, AVLinux, RemixOS, Puppy Studio, Dream Studio, or customized mainstream versions of Suse, Fedora etc.

Search google for    falk ubuntu ppa cadence

should take you to latest goings on.

Reaper works fine once qjackctl and wineasio are installed and set up.
Cheers

---

### Post by hebjuzeb on 2012-02-02
Hi, 
Yeah, it looks like the liveDVD is gone for good. I guess I have to learn this stuff anyway, may as well start now. Found what looks like a decent tutorial at ["]http://linuxhomerecording.blogspot.com/2011/12/setting-up-studio-with-ubuntu.html]("http://linuxhomerecording.blogspot.com/2011/12/setting-up-studio-with-ubuntu.html) so I'll give it a try. What I miss more than anything is the wealth of free, quality amp-sim VSTs like Simulanalog and LePou. Is it feasible to run these in realtime, either in Reaper or Ardour, or am I looking at crashes? 
Thanks,
h.

---

### Post by sgx on 2012-02-03
I think they all work fine using festige, or reaper,
probably also in energyXT windows version, and cantabile 1.2 lite.
I only crash things when I forget yoshimi is multitimbral,
and I'm not Yanni  :popcorn:

The guitar things are never a problem. Only Headcase won't work,
due to graphics issues, but A3 and GR5 do, and TSE, Freeamp etc

SoloC fullstack clean channel is a favorite, as is the Hybrit.

The latest Guitarix2 and Rakarrack are also really good, and the
other ampsims can route to them, like anything else.
Calf and Invada LV2 plugins are also keepers.

Cheers

---

### Post by hebjuzeb on 2012-02-04
Hey sgx,
Got KXStudio happening. When I ran the Hydrogen demo and sound actually came out of my speakers, I knew all was well.
I still feel that a live DVD would be hugely helpful . . . you Linux guys know more than you realize, and coming from Windows is a steep learning curve. I'm pretty green, but used to dabble in Ubuntu for virus-free browsing, so I know some of the very basics (ie, how come nothing happens when you try to enter your password in the terminal? etc.) Even one DVD per LTS release would go a long way, and if anyone does find a copy, I'd download and seed just so I can introduce people to Falk's amazing work. Who cares if it's a little out of date?
Hey, do you know if Reaper's in there somewhere? Doesn't show up in search, but I guess it could be hidden amongst the wine stuff. Yeeesh, guess I know what I'll be doing this weekend . . . ;)
Many thanks, 
h.

---

### Post by sgx on 2012-02-05
Reaper must be downloaded and installed. Run windows installers with
the wine command 

wine reaper413-install.exe

following installer defaults is usually best, but I start reaper from the command line, and browse its folder often, so it may save you time in the long run, by installing it in your home/hebjuceb folder

Command history is saved for recycling, its a simple text file called

.bash_history that you can edit as desired, so a command like
wine reaper/reaper.exe     is always just a press or three of the up arrow when a terminal is open.
Cheers

---

### Post by hebjuzeb on 2012-02-05
Hi sgx,
Well the Reaper made an appearance. Turned out it's installed as part of KXStudio, but the program wouldn't start tll I added myself to the Audio Group (just got a message from WINE saying "virtual memory exhausted", which apparently is Linux for "add yourself to the Audio Group!" ReMix jand Puppy don't do that, though they've got problems of their own.
My first impression is that KX is really on to something, the only flaw is documentation . . . there isn't any. Well, back at it . . . 
Thanks, 

h.

---

### Post by sgx on 2012-02-05
there is a textfile  /etc/security/limits.conf

the last lines should look like this

@audi0          -       rtprio           99
@audio          -       nice             -15
@audio          -       memlock          unlimited
# End of file

you should keep the spacing as is seen in the actual file, not how
it appears in this forum-degraded post.

In qjackctl gui the priority can be in the 69 to 89 range. At 89,
the maximum, there is a small chance some system function will fail
because recording is hogging the cpu processes, but it hasn't hindered me,
my system is a skeleton anyway. I see lower values like 70
recommended by people who really know linux as a whole.

The 'nice' value is not carved in stone, I have read where -19
is a good choice. I can't calculate the difference, without burning
time much better spent recording.

Don't ever do system updates! Upgrading important apps as they
become available, is much safer. Doing a clonezilla system image,
and having backups of /home  /etc/ /usr/share is a good idea.

You can change synaptic preferences in its files menu, to keep
downloaded packages in its cache, and copy them elsewhere for
safe keeping. Some can be re-used in emergencies, for customizing
a new barebones linux, and for 'downgrading to what works'
when new versions are borked.

/var/cache/apt/archives

good recordings should be duplicated and stored off-site,
against fire, theft, weather, or accidents.
Cheers

---

