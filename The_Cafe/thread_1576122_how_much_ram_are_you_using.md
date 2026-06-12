---
title: "how much ram are you using?"
date: 2010-09-16
forum: The Cafe
---

### Post by chris200x9 on 2010-09-16
post a screen shot of "free -m" and tell us what wm, which distro and what's running.

wm: fluxbox

distro: archlinux

what's running:

1 instance of k9copy
2 instances of epdfview
1 instance of firefox with 9 tabs
1 instance of lxterminal with 8 tabs
1 instance of geany with 10 tabs
1 instance of pidgin
1 instance of gnome-mplayer playing a dvd from iso
1 instance of pcmanfm

[[IMG]http://img534.imageshack.us/img534/2640/screenshotkl.th.png[/IMG]](http://img534.imageshack.us/i/screenshotkl.png/)

edit: tl;dr 3718

---

### Post by NovaAesa on 2010-09-16
```


[ps@pris ~]$ free -m
             total       used       free     shared    buffers     cached
Mem:          3958       3860         98          0        150       2946
-/+ buffers/cache:        763       3195
Swap:         4502          0       4502
[ps@pris ~]$ 

```

Distro: archlinux
DE: gnome

Running:
3x chrome
1x moc
4x nautilus
3x emacs
6x gnome terminal
1x vlc

---

### Post by mr_hangman on 2010-09-16
```
             total       used       free     shared    buffers     cached
Mem:          2014       1595        418          0        310        657
-/+ buffers/cache:        627       1386
Swap:         2047          0       2047
```Distro: archlinux
DE: gnome

Running: guayadeque, ff4.0b7 with 20+ tabs

---

### Post by Simian Man on 2010-09-16
CentOS, no DE, a lot running:
```
             total       used       free     shared    buffers     cached
Mem:            31         31          0          0          0         24
-/+ buffers/cache:          6         24
Swap:           11          0         11

```

---

### Post by malspa on 2010-09-16
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          2023       1277        746          0         42        698
-/+ buffers/cache:        536       1486
Swap:         1992          0       1992
```

In PCLinuxOS KDE 2010.07.  chromium-browser running with 7 tabs open.  Also running Exaile, and of course Konsole to run this command.

---

### Post by Noz3001 on 2010-09-16
```
nathan@GLaDOS:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3707       1876       1831          0         30        950
-/+ buffers/cache:        895       2811
Swap:            0          0          0


```

How do the arch guys use more? I'm on Ubuntu 10.10

---

### Post by Old Marcus on 2010-09-16
I am glad to say that I am using less than one byte of RAM. I have 6 gigs in my box, money well spent I reckon.

---

### Post by malspa on 2010-09-16
> **Old Marcus said:**
> less than one byte of RAM

???

---

### Post by Cuddles McKitten on 2010-09-16
I'm usually around 1.5GB since I do all my work in a virtual machine and keep Firefox open with two metric buttloads of tabs.  I use GNOME.

---

### Post by Rasa1111 on 2010-09-16
Ubuntu 10.04./GNOME

```
free -m
             total       used       free     shared    buffers     cached
Mem:          1001        903         97          0         71        417
-/+ buffers/cache:        414        587
Swap:         1609          0       1609

```

Chromium x2 , 6 youtube tabs in one, 6 various tabs in the other, ubuntu forums, space.com, emails,etc. lol
Songbird
Terminal
Pidgin
Pandora Radio, in AWN dock

---

### Post by chris200x9 on 2010-09-16
> **Noz3001 said:**
> 

How do the arch guys use more? I'm on Ubuntu 10.10

How much are you running?

---

### Post by Half-Left on 2010-09-16
```
             total       used       free     shared    buffers     cached
Mem:          3964       3025        939          0        199       1888
-/+ buffers/cache:        937       3026
Swap:        11612          0      11612

```

Ubuntu 10.4 64bit/GNOME

Chrome, xchat, empathy, rhythmbox, docky.

---

### Post by cj.surrusco on 2010-09-16
Distro: Ubuntu 10.04 64-bit
DE: Gnome
```
cj@RAID5-X4:/$ free -m 
             total       used       free     shared    buffers     cached
Mem:          2008       1949         59          0         53       1094
-/+ buffers/cache:        801       1207
Swap:         1996          0       1996

```
1-Rhythmbox
1-Chromium
4-Gnome-terminal
1-Evolution
1-Pidgin

---

### Post by Phrea on 2010-09-16
```
             total       used       free     shared    buffers     cached
Mem:          3962       2938       1024          0         33       1260
-/+ buffers/cache:       1643       2318
Swap:         6750        271       6479

```

Distro: Ubuntu 10.04 64-bit
DE: Gnome

1 terminal
1 Opera [5 tabs]
1 Mplayer
1 Nautilus
1 Pidgin
1 Xchat

---

### Post by e79 on 2010-09-16
```
 total       used       free     shared    buffers     cached
Mem:       6118496    6077380      41116          0     200428    1848128
-/+ buffers/cache:    4028824    2089672
Swap:     10482404       8956   10473448
```

WM : Nautilus
Distro : Ubuntu 10.04 64bit

2x Virtual Machines
5x Firefox tabs
1x VLC (HD)
1x Evolution Mail
2x Terminal
3x WM opened
1x CD tray opened to support coffee mug.

---

### Post by libssd on 2010-09-16
I figured a screencap would be more useful than just the contents of a terminal window. It's interesting that free -m and system monitor report very different stats.

Ubuntu 10.04 (last updated 9/14)
Chrome (updated today) with three tabs
Terminal
System Monitor

---

### Post by Rasa1111 on 2010-09-16
> 1x CD tray opened to support coffee mug.

 haha, for real?

---

### Post by smellyman on 2010-09-16
> **libssd said:**
> I figured a screencap would be more useful than just the contents of a terminal window. It's interesting that free -m and system monitor report very different stats.
 
Ubuntu 10.04 (last updated 9/14)
Chrome (updated today) with three tabs
Terminal
System Monitor
 
 
system monitor doesn't inlcuded cache into used ram.  free -m does.

---

### Post by CharlesA on 2010-09-16
```
charles@thor:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5981       5924         56          0         97       3106
-/+ buffers/cache:       2720       3260
Swap:        12401          5      12396

```

Ubuntu 10.04.1 x64
No DE
Few VMs running.

---

### Post by sandyd on 2010-09-16
```
           total       used       free     shared    buffers     cached
Mem:          3928       3090        838          0        470       1364
-/+ buffers/cache:       1255       2672
Swap:         2996          0       2996

```
recompiling firefox. seems to be very crashy.

---

### Post by 98cwitr on 2010-09-16
wm: gnome

distro: 10.04

what's running:

1 Skype
1 Evolution
1 RhythmBox
2 Chrome tabs
1 System Monitor

Sys Mon says 459.3MB used

```

             total       used       free     shared    buffers     cached
Mem:          2012       1035        976          0         79        489
-/+ buffers/cache:        466       1546
Swap:         2380          0       2380

```

---

### Post by e79 on 2010-09-16
> **Rasa1111 said:**
> haha, for real?

Yup yup  :p

---

### Post by Linye on 2010-09-16
```
 free -m
             total       used       free     shared    buffers     cached
Mem:          3014       1070       1944          0         72        486
-/+ buffers/cache:        511       2503
Swap:         8831          0       8831

```Ubuntu 10.04
gnome
cardapio menu
nautilus
awn
firefox 4.0b7pre (2 tabs)
guayadeque
pidgin (3 tabs)
liferea
terminal

---

### Post by Legendary_Bibo on 2010-09-17
```

             total       used       free     shared    buffers     cached
Mem:          3709       2529       1180          0         77        911
-/+ buffers/cache:       1540       2168
Swap:        10865          0      10865

```

I'm running Rythmbox, Vuze, Firefox with two tabs, gnomenu, compiz, cairo-dock with open gl. I'd say a good chunk of that is going to my eyecandy. :D

---

### Post by Legendary_Bibo on 2010-09-17
> **e79 said:**
> ```
 total       used       free     shared    buffers     cached
Mem:       6118496    6077380      41116          0     200428    1848128
-/+ buffers/cache:    4028824    2089672
Swap:     10482404       8956   10473448
```WM : Nautilus
Distro : Ubuntu 10.04 64bit

2x Virtual Machines
5x Firefox tabs
1x VLC (HD)
1x Evolution Mail
2x Terminal
3x WM opened
1x CD tray opened to support coffee mug.

I hope that's in kilobytes otherwise you've got like 6TB of RAM.

---

### Post by Khakilang on 2010-09-17
koh@koh-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1502        852        649          0         49        333
-/+ buffers/cache:        470       1032
Swap:         4398          0       4398
koh@koh-desktop:~$ 

Ubuntu 10.04 64bits, running only Firefox.

---

### Post by Blackra1n on 2010-09-17
total       used       free     shared    buffers     cached
Mem:          2012        531       1481          0         37        236
-/+ buffers/cache:        257       1755
Swap:         2382          0       2382

Running: gnome-terminal, Firefox

---

### Post by The Real Dave on 2010-09-17
```
dave@tecra:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        918         83          0         46        536
-/+ buffers/cache:        335        666
Swap:          952          0        952

```


Ubuntu 10.04 with Openbox. 

As close to a full list of running apps as I'm willing to get;
Openbox,
Conky
Tint2
Firefox 4 Beta 6
gnome-terminal
Empathy
gnome-bluetooth-applet
battmon
nm-applet
A nautilus browser window
Nitrogen

---

### Post by ubunterooster on 2010-09-17
Ubuntu 10.10: Firefox and reactos (in a VM)

```
ubunterooster@ubunterooster-mobile:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3705       2267       1438          0        132       1620
-/+ buffers/cache:        513       3192
Swap:            0          0          0
ubunterooster@ubunterooster-mobile:~$ 

```

---

### Post by Bachstelze on 2010-09-17
813M, Ubuntu, Gnome, a gnome-term with SSH, firefox with 5 tabs, thunderbird, pidgin, and whatever is running in the background.

---

### Post by e79 on 2010-09-22
> **Legendary_Bibo said:**
> I hope that's in kilobytes otherwise you've got like 6TB of RAM.
 
Of course it's in Kilobytes ! I have 6GB of RAM actually in my rig  :)

---

### Post by fatality_uk on 2010-09-22
total       used       free     shared    buffers     cached
Mem:          3923       1110       2812          0         97        453
-/+ buffers/cache:        559       3363
Swap:         7627          0       7627

---

### Post by Roasted on 2010-09-22
2.0gb flat.

1.0gb dedicated to an XP VM I'm running.

---

### Post by CraigPaleo on 2010-09-22
Kubuntu 10.10 Beta 

The first run only had these two apps running.

Rekonq
Konsole

The second run had:

Rekonq (3 tabs)
Konsole
K3b
KSnapshot
Okular
Dragon Player
Amarok
Dolphin


[IMG]http://img814.imageshack.us/img814/3848/freem1.png[/IMG]

---

### Post by Spice Weasel on 2010-09-22
```

             total       used       free     shared    buffers     cached
Mem:          2013       1959         53          0         35       1531
-/+ buffers/cache:        392       1621
Swap:         4031          0       4031

```

---

### Post by twinaxel on 2010-09-22
gizmo@gizmo-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          4014       1224       2789          0        114        666
-/+ buffers/cache:        443       3570
Swap:         9202          0       9202
gizmo@gizmo-desktop:~$ 

Just firefox running

---

### Post by ubunterooster on 2010-09-22
W/ browser running I use 108 mb RAM... on my Droid ;)

---

### Post by Calash on 2010-09-22
```


             total       used       free     shared    buffers     cached
Mem:          5726       5636         89          0         98       1582
-/+ buffers/cache:       3955       1771
Swap:        11225          1      11224

```

10.04 x64. Running Windows XP 2 virtual machines, 1 uses 2.0gb and the other uses 1.3gb of memory.  The remaining top 5 memory users are Xorg and Chrome(taking 3 spots currently)

---

### Post by mcduck on 2010-09-22
```
             total       used       free     shared    buffers     cached
Mem:           497        171        325          0         68         60
-/+ buffers/cache:         42        454
Swap:          397          0        397
```
I have to admit that I only have a couple of terminals open on that system at the moment. But still pretty lightweight for a GUI with even some compositing and stuff running... :)

---

### Post by cj.surrusco on 2010-09-22
> **mcduck said:**
> ```
             total       used       free     shared    buffers     cached
Mem:           497        171        325          0         68         60
-/+ buffers/cache:         42        454
Swap:          397          0        397
```
I have to admit that I only have a couple of terminals open on that system at the moment. But still pretty lightweight for a GUI with even some compositing and stuff running... :)

What GUI is it that you are using?

---

### Post by t0p on 2010-09-22
```

t0p@deimos:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2006        858       1148          0         23        484
-/+ buffers/cache:        350       1656
Swap:            0          0          0

```

Distro is **Eeebuntu 3** (basically Jaunty with a few hardware-specific tweaks).  Running Firefox X4, System Monitor, Nautilus X2, and I have a terminal open.

---

### Post by mcduck on 2010-09-22
> **cj.surrusco said:**
> What GUI is it that you are using?

Openbox, with xcompmgr for compositing and no DM running (I do have automatically starting X, though, I just configured X to autostart when logging in through TTY1).

---

### Post by Dustin2128 on 2010-09-22
standard flux, nm-applet and a few firefoxes with about 40 tabs open in all.
```

   total       used       free     shared    buffers     cached
Mem:          1883        658       1224          0        151        271
-/+ buffers/cache:        234       1648
Swap:            0          0          0

```

---

### Post by emanuel.landeholm on 2010-09-22
```
root@jel-desktop:~# echo "1" > /proc/sys/vm/drop_caches && free -m
             total       used       free     shared    buffers     cached
Mem:          2011        597       1414          0          0        113
-/+ buffers/cache:        483       1528
Swap:         4008          0       4008

```

Running: liferea. Chrome Beta w. 7 open tabs, one nautilus browser, one gedit with 3 tabs and a gnome terminal.

---

### Post by trekrem on 2010-09-23
```
             total       used       free     shared    buffers     cached
Mem:          7812       1937       5875          0        292       1025
-/+ buffers/cache:        619       7192
Swap:         3814          0       3814
```

Ubuntu 10.04.1 x86-64
Linux 2.6.32-24-generic
8192MB RAM (4x2048MB)
Firefox (multiple tabs), Terminal and Empathy running.

---

### Post by powerpleb on 2010-09-23
```
             total       used       free     shared    buffers     cached
Mem:          3962        839       3122          0         41        293
-/+ buffers/cache:        504       3457
Swap:         9538          0       9538

```
Just running GNOME, Chromium with a couple of tabs open and Htop; which says I am using 549/3962MB.

---

### Post by t6ti00 on 2010-09-23
Right now 

```
total       used       free     shared    buffers     cached
Mem:          3023        607       2415          0         55        254
-/+ buffers/cache:        296       2726
Swap:         8856          0       8856
```

I have Firefox (4 tabs open), gedit and nautilus open.

---

### Post by NightwishFan on 2010-09-23
Not nearly enough.. *Starts virtual machine of Haiku, loads compositing and docky, and begins to convert a video*

```
             total       used       free     shared    buffers     cached
Mem:          2985        797       2187          0         35        358
-/+ buffers/cache:        403       2581
Swap:         4000          0       4000
```

DARN STILL NOT ENOUGH!

---

### Post by l-x-l on 2010-09-23
```
l-x-l@ubuntu-linx:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3275       3106        169          0        580       1981
-/+ buffers/cache:        544       2730
Swap:         4102          0       4102

```

Ubuntu 10.04.1
Gnome
Firefox 1 tab
Terminator
Compiz
Redshift
MPD

---

### Post by inobe on 2010-09-23
OpenSuSe 11.3 64bit kde




i can transcode/ encode video and still can't use swap, i want the system to use all i got, it's why i have it ;)

```
free -m
             total       used       free     shared    buffers     cached
Mem:          3961       1098       2862          0         40        591
-/+ buffers/cache:        466       3494
Swap:         2053          0       2053
```

---

### Post by K.Mandla on 2010-09-23
Under 18Mb, just barely.

```
 Private  +   Shared  =  RAM used	Program 

 80.0 KiB +  29.5 KiB = 109.5 KiB	agetty
 92.0 KiB +  37.5 KiB = 129.5 KiB	init
160.0 KiB +  18.5 KiB = 178.5 KiB	dhcpcd
136.0 KiB +  88.0 KiB = 224.0 KiB	centerim.sh
136.0 KiB +  89.0 KiB = 225.0 KiB	elinks.sh
140.0 KiB +  89.0 KiB = 229.0 KiB	mc.sh
140.0 KiB +  91.0 KiB = 231.0 KiB	vim.sh
332.0 KiB +  87.5 KiB = 419.5 KiB	htop
448.0 KiB +  60.0 KiB = 508.0 KiB	hnb
348.0 KiB + 288.5 KiB = 636.5 KiB	udevd (3)
796.0 KiB + 208.0 KiB =   1.0 MiB	screen-4.0.3 (2)
904.0 KiB + 475.5 KiB =   1.3 MiB	bash (3)
  1.5 MiB +  76.5 KiB =   1.6 MiB	wyrd
  1.7 MiB +  53.0 KiB =   1.8 MiB	vim
  1.8 MiB + 189.5 KiB =   1.9 MiB	mc
  2.0 MiB + 169.0 KiB =   2.2 MiB	elinks
  2.3 MiB + 249.5 KiB =   2.6 MiB	centerim
  2.5 MiB + 207.5 KiB =   2.7 MiB	alpine
---------------------------------
                         17.9 MiB
=================================

 Private  +   Shared  =  RAM used	Program 
```
Using the python script from [here]("http://www.pixelbeat.org/scripts/ps_mem.py") to calculate. :P

Not the best I've done though. [This]("http://kmandla.wordpress.com/2009/08/29/looking-close-at-memory-usage/") is more impressive, really.

---

### Post by NightwishFan on 2010-09-24
I got around 8 or so with Debian, 13 with Ubuntu. I try not to waste if there is no real need.

---

### Post by karthick87 on 2010-09-24
```
karthick@Ubuntu-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2001        551       1449          0         66        246
-/+ buffers/cache:        239       1761
Swap:         1587          0       1587

```

---

### Post by Windows Nerd on 2010-09-24
> **Cuddles McKitten said:**
> I'm usually around 1.5GB since I do all my work in a virtual machine and keep Firefox open with two metric buttloads of tabs.  I use GNOME.

Same here, my ram usage is almost solely attributed to the buttload of Chromium tabs I keep open.

---

### Post by Windows Nerd on 2010-09-24
> **K.Mandla said:**
> Under 18Mb, just barely.

```
 Private  +   Shared  =  RAM used	Program 

 80.0 KiB +  29.5 KiB = 109.5 KiB	agetty
 92.0 KiB +  37.5 KiB = 129.5 KiB	init
160.0 KiB +  18.5 KiB = 178.5 KiB	dhcpcd
136.0 KiB +  88.0 KiB = 224.0 KiB	centerim.sh
136.0 KiB +  89.0 KiB = 225.0 KiB	elinks.sh
140.0 KiB +  89.0 KiB = 229.0 KiB	mc.sh
140.0 KiB +  91.0 KiB = 231.0 KiB	vim.sh
332.0 KiB +  87.5 KiB = 419.5 KiB	htop
448.0 KiB +  60.0 KiB = 508.0 KiB	hnb
348.0 KiB + 288.5 KiB = 636.5 KiB	udevd (3)
796.0 KiB + 208.0 KiB =   1.0 MiB	screen-4.0.3 (2)
904.0 KiB + 475.5 KiB =   1.3 MiB	bash (3)
  1.5 MiB +  76.5 KiB =   1.6 MiB	wyrd
  1.7 MiB +  53.0 KiB =   1.8 MiB	vim
  1.8 MiB + 189.5 KiB =   1.9 MiB	mc
  2.0 MiB + 169.0 KiB =   2.2 MiB	elinks
  2.3 MiB + 249.5 KiB =   2.6 MiB	centerim
  2.5 MiB + 207.5 KiB =   2.7 MiB	alpine
---------------------------------
                         17.9 MiB
=================================

 Private  +   Shared  =  RAM used	Program 
```
Using the python script from [here]("http://www.pixelbeat.org/scripts/ps_mem.py") to calculate. :P

Not the best I've done though. [This]("http://kmandla.wordpress.com/2009/08/29/looking-close-at-memory-usage/") is more impressive, really.
I see your blog post on how you run an old laptop with 16 mb of RAM. I have an even older laptop with 8 mb of RAM and a 170 mb hard drive and a 133 mz Pentium Processor (probably a 486 I believe). Could I sandwitch Crux on there? It only has a floppy drive.

---

### Post by Señor Banana on 2010-09-24
```
             total       used       free     shared    buffers     cached
Mem:          7929       1532       6397          0         46        571
-/+ buffers/cache:        915       7014
Swap:        16127          0      16127
Total:       24057       1532      22525
``````
             total       used       free     shared    buffers     cached
Mem:       8120008    1575424    6544584          0      47216     587784
-/+ buffers/cache:     940424    7179584
Swap:     16514816          0   16514816
Total:    24634824    1575424   23059400

```
Kubuntu 10.04
KDE
Firefox 1 tab
Konsole
Songbird
Thunderbird
Ktorrent
Kopete

---

### Post by Ocxic on 2010-09-24
```

             total       used       free     shared    buffers     cached
Mem:          8003       7948         55          0          0       2868
-/+ buffers/cache:       5079       2923
Swap:            0          0          0

```

firefox
2 vm's running in virtualbox (10.04 Server & Windows 7)
tvtime
Azureus (Vuse)
Banshee

---

### Post by MasterNetra on 2010-09-24
Around 190MB atm. It of course usually depends on what I'm doing.

---

### Post by MooPi on 2010-09-24
Just right :-)

---

### Post by inobe on 2010-09-25
```
free -m
             total       used       free     shared    buffers     cached
Mem:          3962       1843       2119          0        121        914
-/+ buffers/cache:        807       3155
Swap:         6236          0       6236

```

this time kubuntu 10.04 64bit

lots of stuff going yet no swap usage.

---

