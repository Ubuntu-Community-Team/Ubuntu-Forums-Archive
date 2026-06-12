---
title: "some unity8 setbacks should give workable preview for the brave"
date: 2016-09-29
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-09-29
Come 16.10 we should have a workable technical preview for unity8 desktop. Developers are hard at work with fixes for yakkety without the ppa.  I would appreciate if those who have been testing unity8 to continue to do so up to release of yakkety and beyond.

 It is the next new shiny thing and it is what we do at UDV. :)

Regards..

---

### Post by simonsaysthis on 2016-09-29
Will definitely do come the final release. Can you just install it alongside without breaking anything if it's removed?

---

### Post by ventrical on 2016-09-29
> **simonsaysthis said:**
> Will definitely do come the final release. Can you just install it alongside without breaking anything if it's removed?

Yes...

currently it is:

```

sudo apt-get install unity8-desktop-session
sudo apt-get install libertine libertine-scope

```


Regards..

---

### Post by simonsaysthis on 2016-09-29
Great will try it now. I shall blame you if it breaks the system :)

---

### Post by terry_gardener on 2016-09-29
do you know if it works with either nouveau for gtx960 or the officiasl nvidia driver yet

---

### Post by ventrical on 2016-09-29
> **simonsaysthis said:**
> Great will try it now. I shall blame you if it breaks the system :)

Yes .. mea culpa ;)

---

### Post by ventrical on 2016-09-29
> **terry_gardener said:**
> do you know if it works with either nouveau for gtx960 or the officiasl nvidia driver yet

Stick with nouveau-firmware. nVida set will break it and send it into continuous loop.

Regards..

---

### Post by terry_gardener on 2016-09-30
thanks ventrical

now that i am using the 4.8 kernel it now loads unity 8, however i can't seem to do much as when i click browser it loads the homepage and then crashes the system, and only other icon i have is system settings which seems to load ok. how do i get #
libertine to work so i can use other apps.

---

### Post by mc4man on 2016-09-30
> **terry_gardener said:**
> thanks ventrical

now that i am using the 4.8 kernel it now loads unity 8, however i can't seem to do much as when i click browser it loads the homepage and then crashes the system, and only other icon i have is system settings which seems to load ok. how do i get #
libertine to work so i can use other apps.
your best bet atm is to log in to a unity7 session, open libertine, create &  then populate a container there. Then those apps will be available in a unity8 session.
The container creation can take some time, I've seen it take upwards of 10+ minutes. There should be a spinning wheel, wait till it stops. You can also click on the container name in that window to get a verbose output of what's occurring.
I'd suggest you add nautilus as atm many app menus can be hard to open rendering them useless in some cases so an open with > whatever is a fallback. I'd put menus opening at about 25% of the time at best so one can also keep attempting till they finally appear.

For media players sound output must be alsa, that can be a chore to achieve at times with 3rd party players, the included players only support the 'free' codecs & have virtually no controls.

---

### Post by ventrical on 2016-09-30
> **terry_gardener said:**
> thanks ventrical

now that i am using the 4.8 kernel it now loads unity 8, however i can't seem to do much as when i click browser it loads the homepage and then crashes the system, and only other icon i have is system settings which seems to load ok. how do i get #
libertine to work so i can use other apps.

mac4man is right.

We have to use libertine through unity7 (regular ubuntu-desktop default). If anything, one can sort of built a 'personal-desktop' experience with multiple containers. As I am advised by developers (on irc)  this  unity8 desktop cycle for 16.10 will be a 'technical preview' but with using Libertine we can keep  an interest in experimenting with containers so testing it is not a complete waste of time.  I encourage all memebers of UDV (U+1)to continue testing unity8 until release and during the next cycle.

Regards..

---

### Post by terry_gardener on 2016-09-30
thanks ventrical and mc4man i used libertine in unity 7 and set it up. managed to load several xapps. gnome-terminal, files, gnome-software, firefox, rhythmbox and solitaire. 

there is still lot of functionality missing but guessing this will come in time.

---

### Post by ventrical on 2016-09-30
Even got other-sofware app to work..
Synaptic will not work like it did before. Now it just blanks out.

---

### Post by ventrical on 2016-09-30
Nautilus seems a little more cleaned up.

---

### Post by ventrical on 2016-09-30
> **terry_gardener said:**
> thanks ventrical and mc4man i used libertine in unity 7 and set it up. managed to load several xapps. gnome-terminal, files, gnome-software, firefox, rhythmbox and solitaire. 

there is still lot of functionality missing but guessing this will come in time.

There are some apps that work really well but many gnome apps will not work like gnome-disks or gnome-terminal. Keep experimenting. Create other containers, install firefox and see if you can get two multiple sessions on desktop from each separate container.

Regards..

---

### Post by terry_gardener on 2016-10-01
yes i have tried creating a new container and run firefox from each container, it runs from the new container like it is the first time use which is part of the sandbox effect i guess. 
i even used the window snap feature which worked ok.

---

### Post by ventrical on 2016-10-06
test

```

ventrical@ventrical-System-Product-Name:~$ inxi -Fxz
The program 'inxi' is currently not installed. You can install it by typing:
sudo apt install inxi
ventrical@ventrical-System-Product-Name:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Expre            ss Port 5 (rev 02)                                                              
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB U            HCI Controller #1 (rev 02)                                          
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 610] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)
02:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
02:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
03:00.0 Ethernet controller: Qualcomm Atheros Attansic L1 Gigabit Ethernet (rev b0)
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
ventrical@ventrical-System-Product-Name:~$ 

```

pasted from unity8 terminal

Wow.. what a difference a day makes and Libertine now a scope in the apps.

---

### Post by ventrical on 2016-10-06
Just checking..

```

ventrical@ventrical-System-Product-Name:~$ inxi -Fxz
System:    Host: ventrical-System-Product-Name Kernel: 4.8.0-19-generic x86_64 (64 bit gcc: 6.2.0)                                      
           Console: tty 18 Distro: Ubuntu 16.10                     
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx                   
           BIOS: American Megatrends v: 1807 date: 04/15/2009       
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB   
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11980                                                                   
           clock speeds: max: 2995 MHz 1: 2995 MHz 2: 2995 MHz      
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0      
           Display Server: X.org 1.18.4 drivers: nouveau (unloaded: fbdev,vesa)                                                         
           tty size: 68x26 Advanced Data: N/A out of X              
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller    
           driver: snd_hda_intel bus-ID: 00:1b.0                    
           Card-2 NVIDIA GF119 HDMI Audio Controller                
           driver: snd_hda_intel bus-ID: 01:00.1                    
           Card-3 Logitech Webcam C210                              
           driver: USB Audio usb-ID: 001-002                        
           Sound: ALSA v: k4.8.0-19-generic                         
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet      
           driver: atl1 v: 2.1.3 bus-ID: 03:00.0                    
           IF: enp3s0 state: up speed: 100 Mbps duplex: full        
           mac: <filter>                                            
Drives:    HDD Total Size: 80.0GB (14.0% used)                      
           ID-1: /dev/sda model: WDC_WD800HLFS size: 80.0GB temp: 26C                                                                   
           ID-1: / size: 41G used: 7.6G (20%) fs: ext4 dev: /dev/sda1                                                                   
           ID-2: swap-1 size: 3.22GB used: 0.00GB (0%) fs: swap dev: /dev/sda5                                                          
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present                                                                  
Sensors:   System Temperatures: cpu: 34.0C mobo: 35.0C gpu: 37.0    
           Fan Speeds (in rpm): cpu: 4245 psu: 0 sys-1: 0 sys-2: 0  
Info:      Processes: 239 Uptime: 22 min Memory: 1093.4/3007.1MB    
           Init: systemd runlevel: 5 Gcc sys: 6.2.0                 
           Client: Shell (bash 4.3.461) inxi: 2.3.1                 
ventrical@ventrical-System-Product-Name:~$         

```

---

### Post by terry_gardener on 2016-10-09
i have reinstalled 16.10 and and now i have lost the music and video scopes in unity 8 is there a way to get them back

---

### Post by Chanath on 2016-10-09
Anyone using Unity 8 on a touchscreen?

---

### Post by ventrical on 2016-10-10
> **Chanath said:**
> Anyone using Unity 8 on a touchscreen?

I know that unity7 works excellently on touch screens (amd64) and I may get to retry on that machine with unity8 in the near furture.

---

### Post by ventrical on 2016-10-10
> **terry_gardener said:**
> i have reinstalled 16.10 and and now i have lost the music and video scopes in unity 8 is there a way to get them back

yep .. there gone with regular update process also..

---

### Post by terry_gardener on 2016-10-10
if you install unity-scope-mediascanner2 package you get the music and video scopes back

---

### Post by rrnbtter on 2016-10-13
Greetings,
I just received a stable Unity 8 overlay from the ci-train ppa (in yakkety).  Libertine containers and debs working ok with Intel system. As always, use at your own risk but mine is working fine. Incidentally, I have not discontinued the ppa as some here have. It has been a flawed but working piece meal mess until this morning. It's like most of this dev stuff, doesn't come together until the last minute. The deb apps are installing via the CLI.

---

### Post by ventrical on 2016-10-13
> **terry_gardener said:**
> if you install unity-scope-mediascanner2 package you get the music and video scopes back

Yeah .. that works here.

---

