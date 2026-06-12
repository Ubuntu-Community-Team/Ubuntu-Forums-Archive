---
title: "Linux distro for old PC?"
date: 2011-06-02
forum: The Cafe
---

### Post by grobar87 on 2011-06-02
Hi,
I want to install linux on 10 years old PC.This is the output of 'lspci':
```
$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 44)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
00:0c.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
00:10.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
00:12.0 Multimedia audio controller: Yamaha Corporation YMF-724 (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

```
CPU is Celeron 850Mhz,RAM 384Mb,Hard Disk 20Gb.
I'm not sure is there any nvidia driver for this old card... anyway what linux distro will be the best choice for me?I want to use this PC for watching movies and sometimes for internet.
Thanks and sorry for my english. :)

---

### Post by zealibib slaughter on 2011-06-02
Lubuntu may run good on it, Puppy will run great and so will DSL.  I would try Lubuntu first though.

---

### Post by NormanFLinux on 2011-06-02
Bodhi Linux would run great on it.

---

### Post by silex89 on 2011-06-02
CrunchBang Linux :D

---

### Post by 3Miro on 2011-06-02
CentOS and Scientific should do well, but replace Gnome with LXDE or a standalone WM.

---

### Post by Noz3001 on 2011-06-02
Slackware with OpenBox or some other light window manager ^^

---

### Post by jerenept on 2011-06-02
> **grobar87 said:**
> Hi,
I want to install linux on 10 years old PC.This is the output of 'lspci':
```
$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 44)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
00:0c.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
00:10.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
00:12.0 Multimedia audio controller: Yamaha Corporation YMF-724 (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

```
CPU is Celeron 850Mhz,RAM 384Mb,Hard Disk 20Gb.
I'm not sure is there any nvidia driver for this old card... anyway what linux distro will be the best choice for me?I want to use this PC for watching movies and sometimes for internet.
Thanks and sorry for my english. :)

I think that nvidia card would be well serviced by the FOSS drivers (it's not like high-performance drivers are even possible)

Recommend LuPu or maybe Debian with LXDE or IceWM.

Movies sound pretty implausible (maybe mplayer from cli?), but Dillo will run super-fast, even on such limited specs.

---

### Post by Dustin2128 on 2011-06-02
> **Noz3001 said:**
> Slackware with OpenBox or some other light window manager ^^
Well of course bob would say that. 

@OP a legacy driver *should *exist for even such an ancient card. As for distro, SliTaz I say!

---

### Post by vehemoth on 2011-06-03
I would suggest a cut back debian squeeze with a lightweight windows manager, that way it's stable lightweight and not too distant from ubuntu. A good suggestion is crunchbang.

There's plenty of choice out there so look at a few suggestions before deciding.

---

### Post by ivanovnegro on 2011-06-03
There is also [AntiX]("http://antix.mepis.org/index.php?title=Main_Page"), a very lightweight distro to choose from the big pool of them.

---

### Post by Legendary_Bibo on 2011-06-03
Peppermint.

---

### Post by vehemoth on 2011-06-03
> **Legendary_Bibo said:**
> Peppermint.

Sounds like it should be based on mint.
I think the de/wm should be also of great consideration if you are planning to use it a lot.

---

### Post by RoflHaxBbq on 2011-06-03
You will find that for older computers, the kind of distros that have everything done for you, such as Ubuntu (not bashing), are a bit too bogged down.

I suggest downloading just CD1 of Debian Squeeze. At tasksel time (the part of installation when it asks what parts to install), just select Core and Standard. After that just install your DE piece by piece. I suggest LXDE.

---

### Post by lucazade on 2011-06-03
Simply Ubuntu.
With a bit of tuning (disable unecessary services and startup programs, disable compiz and choose a lighter gtk engine and theme).
Gtk+ toolkit performs the same way in any DE based on it (gnome,xfce and lxde.. use gtkperf to bench) and memory consumption doesn't affect general performances.
Another good alternative is CrunchBang Linux, which is probably the only Ubuntu derivatives I consider good.

---

### Post by ivanovnegro on 2011-06-03
> **lucazade said:**
> Simply Ubuntu.
With a bit of tuning (disable unecessary services and startup programs, disable compiz and choose a lighter gtk engine and theme).
Gtk+ toolkit performs the same way in any DE based on it (gnome,xfce and lxde.. use gtkperf to bench) and memory consumption doesn't affect general performances.
Another good alternative is CrunchBang Linux, which is probably the only Ubuntu derivatives I consider good.

Yes Crunchbang is really good but it is not an Ubuntu derivative anymore, its based on plain Debian. :)

---

### Post by lucazade on 2011-06-03
> **ivanovnegro said:**
> Yes Crunchbang is really good but it is not an Ubuntu derivative anymore, its based on plain Debian. :)

I did a gaffe! XD

---

### Post by betterhands on 2011-06-03
reading the answers to the original question, i wonder if asking which distro(s) should be avoided might have garnered more helpful answers :?:

---

### Post by Artemis3 on 2011-06-03
Install [Ubuntu minimal](https://help.ubuntu.com/community/Installation/MinimalCD) (press f4 to choose command line) and then install your favorite DE, say: sudo apt-get install xfce4

Should be good and light enough, like Debian but newer. Just avoid Gnome and Kde...

---

### Post by grobar87 on 2011-06-03
Thanks to all for reply and suggestions :)
I try six distributions and some of them works great.First i try Lubuntu 11.04,Bodhi Linux,Chrunchbang 10,Puppy Linux,Arch Linux with Openbox and Debian 6 with Openbox.All works great and relative fast but seems that i have same problem on all,can not install propritary drivers for nVidia RIVA TNT2 Model 64 Pro.:confused:I need help!
I will try more distributions today and post back here.
Thanks again.

---

### Post by ivanovnegro on 2011-06-03
> **betterhands said:**
> reading the answers to the original question, i wonder if asking which distro(s) should be avoided might have garnered more helpful answers :?:

Not a bad point but I think the mentioned ones are all decent distros, so you have to try them before deciding.

---

### Post by ivanovnegro on 2011-06-03
> **grobar87 said:**
> Thanks to all for reply and suggestions :)
I try six distributions and some of them works great.First i try Lubuntu 11.04,Bodhi Linux,Chrunchbang 10,Puppy Linux,Arch Linux with Openbox and Debian 6 with Openbox.All works great and relative fast but seems that i have same problem on all,can not install propritary drivers for nVidia RIVA TNT2 Model 64 Pro.:confused:I need help!
I will try more distributions today and post back here.
Thanks again.

On Lubuntu try to load additional drivers, on Bodhi maybe also, on Crunchbang start the script after installing the distro but normally it starts automatically if not type in the terminal: cb-welcome, but Crunchbang already comes with proprietary stuff, Arch that could be difficult, you would have to choose it specifically, and Debian wont load anything non-free drivers but with the minimal net install you can choose to include them from the installer or to add the non-free repos into it after install.

---

### Post by Artemis3 on 2011-06-03
You have to use [nvidia driver 71.86.14](http://www.nvidia.com/object/linux-display-ia32-71.86.14-driver.html)

That card is very slow and under-featured so i doubt it very useful to use the proprietary driver vs nouveau... You might as well stick with Debian 6.0 and simply install nvidia's; just remember to re-install any time you update any package with the name "linux" in it (aka kernel).

---

### Post by wolfen69 on 2011-06-03
Puppy should run great on that machine.

---

### Post by Dustin2128 on 2011-06-03
I'm posting this from an old P3 650Mhz with 384Mb RAM and a Rage 128 (written with one of those nice old clicky keyboards), running debian 6 stable. It feels snappy, and although I can't have conky polling for CPU usage every 0.1 seconds (causes it to eat up 80% of the CPU :lolflag:) it runs well enough. Still though, probably ditching gnome for openbox. But debian is pretty nice on resource usage.

---

### Post by grobar87 on 2011-06-03
@ivanovnegro I follow your suggestions,i try to load additional drivers on Lubuntu and it works great,but i think i will stay with Debian for now,pure Openbox runs better over LXDE on my PC.
Thanks for your help.
@Artemis3 I just install nouveau drivers and works fine.Thanks!
@wolfen69 Yes,puppy runs great too.
Thanks again to all for help.My choise is Debian 6 with Openbox. :)

---

### Post by grobar87 on 2011-06-03
> **Dustin2128 said:**
> I'm posting this from an old P3 650Mhz with 384Mb RAM and a Rage 128 (written with one of those nice old clicky keyboards), running debian 6 stable. It feels snappy, and although I can't have conky polling for CPU usage every 0.1 seconds (causes it to eat up 80% of the CPU :lolflag:) it runs well enough. Still though, probably ditching gnome for openbox. But debian is pretty nice on resource usage.

I totally agree with you!I like Debian/Openbox combination on this old machine. :D

---

### Post by ivanovnegro on 2011-06-04
> **grobar87 said:**
> @ivanovnegro I follow your suggestions,i try to load additional drivers on Lubuntu and it works great,but i think i will stay with Debian for now,pure Openbox runs better over LXDE on my PC.
Thanks for your help.
@Artemis3 I just install nouveau drivers and works fine.Thanks!
@wolfen69 Yes,puppy runs great too.
Thanks again to all for help.My choise is Debian 6 with Openbox. :)

Your decision way anyway good, enjoy!

---

### Post by coolbrook on 2011-07-08
I'll try that combination.  I like SliTaz, but my current favourite is MijnPup.

[http://www.browserlinux.com/mijnpup/index.html](http://www.browserlinux.com/mijnpup/index.html)

---

### Post by Bandit on 2011-07-08
> **Dustin2128 said:**
> I'm posting this from an old P3 650Mhz with 384Mb RAM and a Rage 128 (written with one of those nice old clicky keyboards), running debian 6 stable. It feels snappy, and although I can't have conky polling for CPU usage every 0.1 seconds (causes it to eat up 80% of the CPU :lolflag:) it runs well enough. Still though, probably ditching gnome for openbox. But debian is pretty nice on resource usage.

Good info. :)

---

