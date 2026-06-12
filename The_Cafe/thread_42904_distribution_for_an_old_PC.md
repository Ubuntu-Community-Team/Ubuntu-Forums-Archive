---
title: "distribution for an old PC?"
date: 2005-06-19
forum: The Cafe
---

### Post by CoriolisSTORM on 2005-06-19
Guys, my old PC does not fit the bill for Ubuntu sadly (it does not meet the requirements), so I need to find a distribution that will work well on it.  Okay, it has:
Intel Pentium 1 Processor w/ MMX @ 200MHz
96 MB EDO DRAM
4.3 GB Quantum Bigfoot HDD
24x Goldstar CD-ROM
onboard ATI VT-3 video card
Sound Blaster 16 PCI (currently not working due to Windows 95b conflicts)
currently it only boots Windows 95b.
I would like something that would run decently on it, yet will be fully featured and easy to use and set up.  Ideas?

---

### Post by TravisNewman on 2005-06-19
you could try Ubuntu with XFCE instead of Gnome. Install Ubuntu using the "custom" boot parameter on the install cd, which will give you a barebones system. Then just install XFCE after you get into it and you'll have it. I don't guarantee that it will work well, I haven't seen a 200 mhz in action for a looong time.

---

### Post by WildTangent on 2005-06-19
i got a stripped down installation to work on my old computer, its basically the same as yours, Pentium MMX 200, 128MB RAM, 3GB HDD, 8x CD-ROM. havent been able to get XFCE on it, or any other DM, i dont know how lol. someone care to inforrm me?

-Wild

---

### Post by gil-galad on 2005-06-19
Damn small linux is actually pretty nice.

---

### Post by bored2k on 2005-06-19
BeaTRIX

---

### Post by Nimefurahi on 2005-06-19
I have had success installing Debian Sarge, Libranet, Trustix, and various Knoppix derivatives on a 75mHz Pentium with half the RAM as you have. The key to success would be to install, as with the steps that panickedthumb suggested, a bare-bones system along with a light weight window manager/desktop such as fluxbox, blackbox, IceWM or XFCE. Admittedly, I have not yet done this with Ubuntu. Perhaps in the next few days I'll give it a try and if I do, I'll give you step-by-step instructions. 

I'll be following this post.

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=gil-galad]Damn small linux is actually pretty nice.[/QUOTE]

I second this. For a PC this old its either Damn Small Linux or Feather Linux.

---

### Post by benplaut on 2005-06-20
[QUOTE=poofyhairguy]I second this. For a PC this old its either Damn Small Linux or Feather Linux.[/QUOTE]

BeaTRIX?

<<edit>>

skipped right over you, bored2k  :roll:

---

### Post by az on 2005-06-20
Hopefully, Breezy will have a LightWeightDesktop version aimed for a 200Mhz computer with 64 megs of ram.
[http://udu.wiki.ubuntu.com/LightweightDesktop](http://udu.wiki.ubuntu.com/LightweightDesktop)

For Hoary, use "server" when installing instead of "custom" since that was changed.

Once you have the base system installed, log in and do:

Add the universe repository to your sources.list

sudo nano /etc/apt/sources.list
(uncomment the line with universe in it)

Then:
sudo apt-get update
sudo apt-get install x-window-system-core gdm synaptic mozilla-firefox icewm rox-filer abiword

And you have a light system!

---

### Post by sksbir on 2005-06-20
hi!
i'm in the same situation : P200 (not even MMX!), 128Mb ram edo. But i inserted two ethernet cards, installed ubuntu with server option and this PC is now a good ICS server.

I don't install xwindows nor any enduser applications. just sshd in order to connect from my enduser PC.

It works great   :)

---

### Post by nrayever on 2005-06-21
it's a bit bizarre, but i have here an old computer, is a pentium2 - 350 mhz, 128 mb of ram, a 15 gb hd and a "pcchips mobo" maybe. i was through the same problem: "which distro will boot on this computer??"

it was really funny, beacuase i tryed a lot of distros:
mandrake 8
mandrake 9
mandrake live cd
ubuntu 5.04
ubuntu 5.04 live cd
knoppix 3.6
knoppix 3.7
redhat 7
insert - from insert cd or ultimate boor cd 3.2
debian sid - network install cd
dead cd
slax - last one of it
libranet 2.8
suse 9.2

and no one of this list could make this old pc boot. the problem with these distros were:

a)kernel panic
b)blank screen after uncompressing vmlinux

a friend recommend me to try with beatrix. and when i did it the first try didn't worked, but at a second try it worked. with beatrix i got some problems when i installed it. so as a last hope i tried with slackware 10.1

i didn't really believed what i read on slckaware's site: slack works with 486 to pentium 4, etc.... and it really did. i was surprised with slackware. i believe that slackware secret is that it's a very light distro, design to really boot on old pc's. 

but in the other hand we have all the other distros, they don't really think that a final user will install the os on a museum computer such as this one i have. i make this comment not to offend any distro, cause i actually use ubuntu on my amd64 and i love it. cause i think it's a pure 64 bits distro.

but maybe ubuntu should try to make a really light sub-distro for those types of computers. i hope this thread leads to something.

nrayever

P.H.: i'm using this old pentium2 to make a mp3 player for my car. when i have more advances(cause right know i'm on vacation, hehehe) i will post at least the website of it. if someone wants to cooperate help will be received with arm wide open!! thanks!!.  :)  :)

---

### Post by benplaut on 2005-06-21
[QUOTE=azz]Hopefully, Breezy will have a LightWeightDesktop version aimed for a 200Mhz computer with 64 megs of ram.
[http://udu.wiki.ubuntu.com/LightweightDesktop](http://udu.wiki.ubuntu.com/LightweightDesktop)

For Hoary, use "server" when installing instead of "custom" since that was changed.

Once you have the base system installed, log in and do:

Add the universe repository to your sources.list

sudo nano /etc/apt/sources.list
(uncomment the line with universe in it)

Then:
sudo apt-get update
sudo apt-get install x-window-system-core gdm synaptic mozilla-firefox icewm rox-filer abiword

And you have a light system![/QUOTE]

or, you can switch out IceWM, put in XFCE4 (more complete DE over WM, and very fast), and put in Dillo instead of Firefox (IME, Firefox can be a bit of a CPU hog sometimes)

sudo apt-get install x-window-system-core gdm synaptic dillo xfce4 rox-filer abiword

---

### Post by polo_step on 2005-06-21
I keep waiting for some ubergeek to build a working system around [Tom's RTBT.](http://www.toms.net/rb/)  ;-)

---

### Post by NeoChaosX on 2005-06-21
A few users on LinuxQuestions suggested I use Damn Small Linux for reviving an old 466 Celeron box I had lying around, and it worked out great. It's definately a good choice for older systems.

---

### Post by CoriolisSTORM on 2005-06-21
I might try out Slackware for it.  Sounds like a good idea, or maybe minislackware.  Both I think should work on it.

---

### Post by aledie on 2005-07-07
[QUOTE=benplaut]or, you can switch out IceWM, put in XFCE4 (more complete DE over WM, and very fast), and put in Dillo instead of Firefox (IME, Firefox can be a bit of a CPU hog sometimes)

sudo apt-get install x-window-system-core gdm synaptic dillo xfce4 rox-filer abiword[/QUOTE]


Or you can remove rox-filer from the line, cuz rox-filer is already in XFCE4 dependencies:
sudo apt-get install x-window-system-core gdm synaptic dillo xfce4 abiword

---

### Post by polo_step on 2005-07-07
[QUOTE=azz]Hopefully, Breezy will have a LightWeightDesktop version aimed for a 200Mhz computer with 64 megs of ram.[/QUOTE]
That would be really nice.  I've been thinking a lot about this lately.

There's a lot of talk about how Linux/open-source will be such a big deal in the third world, on obsolete machines scavenged from the discards of the US and Europe.  Whether this is a serious possibility or merely idealistic pipe-dreaming, I am not qualified to say, but those machines really don't have the resources to run a typical Linux like Ubuntu as distributed.

It's quite interesting to see how bloat has overtaken various distros, and Ubuntu is far, far from the worst -- it can at least fit on a single CD -- but will max-out 128M of RAM doing the sort of stuff I routinely do with it.  Popping in a $23 512M module from the computer store down the street was nothing for me, but having lived in the Third World I can imagine the difficulty and expense of doing it in, say, Ecuador or Kenya..

Considering the "social objectives" that append to Ubuntu, I think it would be appropriate to at some point to make a very high-efficiency distribution variant (or possibly even a prepared installation option) for low-resource machines, as the current Ubuntu seems a very First-World distro to me so far.

---

### Post by sonny on 2005-07-07
Well just to make this thread a little bigger... a friend of mine  is testing a box to be a mp3-player, the specs i don't really know all I do is that it was a P1 and had VERY few memory, he tried Ubuntu, but nothing, then DSL without any succes, Beatrix load OK, but then freezed, then he tried Gentoo and it runs very smooth in that old box, after 2 days he messed up the kernel   :grin: .

---

### Post by az on 2005-07-07
[QUOTE=benplaut]or, you can switch out IceWM, put in XFCE4 (more complete DE over WM, and very fast), and put in Dillo instead of Firefox (IME, Firefox can be a bit of a CPU hog sometimes)

sudo apt-get install x-window-system-core gdm synaptic dillo xfce4 rox-filer abiword[/QUOTE]


Have you ever run XFCE4 on a system with only 64 megs?

It becomes as slow as gnome.

Icewm is bare, but will run well on a 200Mhz system with 64 megs of ram.

Anyway, if disk space is not an issue, perhaps if this project makes a release, the cd can have a number of environments available....

---

### Post by papangul on 2005-07-08
I **strongly** recommend [Gentoo Jackass!](http://jackass.homelinux.org/) with Qingy as login manager, IceWM as window manager and Emelfm(not emelfm2) as file manager. IceWM has a menu manager Icemc and a control panel IceWMCP, which you have to install separately. I am using IceWM(with 64megs ram) and it is as fast as twm, the default window manager for X.

---

