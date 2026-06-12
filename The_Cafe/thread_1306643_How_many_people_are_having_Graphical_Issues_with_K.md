---
title: "How many people are having Graphical Issues with Karmic?"
date: 2009-10-30
forum: The Cafe
---

### Post by HardcoreSSG on 2009-10-30
Just curious if it's a minor bug or a bigger one.

---

### Post by Giblet5 on 2009-10-30
I'm guessing >= 1.

---

### Post by OpenGuard on 2009-10-30
What are you talking about ? What issues ?

---

### Post by Uncle Spellbinder on 2009-10-30
> **HardcoreSSG said:**
> Just curious if it's a minor bug or a bigger one.

"it"

What 'bug' are you talking about. **Specifics** would be wonderful.

---

### Post by luqeliverpudlian on 2009-10-30
The Desktop effect doesnt work on intel 82945G, it hangs 30 seconds after i enabled it, any ideas to solve it?:(

---

### Post by informer2000 on 2009-10-30
Just upgraded to Karmic on my laptop.. After reboot I thought everything was ok. But the graphics are too slow. I have lags in almost anything I do. Switching between FireFox tabs takes at least two seconds before the contents of the newly selected tabs render. Same issue with minimizing and maximixing and even scrolling. And I don't even have desktop effects enabled!

```
Below is my lspci output:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
        Subsystem: Hewlett-Packard Company Device 3602                                       
        Flags: bus master, fast devsel, latency 0                                            
        Capabilities: <access denied>                                                        
        Kernel driver in use: agpgart-intel                                                  
        Kernel modules: intel-agp                                                            

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Hewlett-Packard Company Device 3602                                                              
        Flags: bus master, fast devsel, latency 0, IRQ 16                                                           
        Memory at d0000000 (64-bit, non-prefetchable) [size=4M]                                                     
        Memory at c0000000 (64-bit, prefetchable) [size=256M]                                                       
        I/O ports at 9110 [size=8]                                                                                  
        Capabilities: <access denied>                                                                               

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Hewlett-Packard Company Device 3602                                                       
        Flags: bus master, fast devsel, latency 0                                                            
        Memory at d6500000 (64-bit, non-prefetchable) [size=1M]                                              
        Capabilities: <access denied>                                                                        

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
        Subsystem: Hewlett-Packard Company Device 3602                                        
        Flags: bus master, medium devsel, latency 0, IRQ 16                                   
        I/O ports at 90e0 [size=32]                                                                                                                              
        Capabilities: <access denied>                                                                                                                            
        Kernel driver in use: uhci_hcd                                                                                                                           
        Kernel modules: uhci-hcd                                                                                                                                 
                                                                                                                                                                 
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)                                                                   
        Subsystem: Hewlett-Packard Company Device 3602                                                                                                           
        Flags: bus master, medium devsel, latency 0, IRQ 21                                                                                                      
        I/O ports at 90c0 [size=32]                                                                                                                              
        Capabilities: <access denied>                                                                                                                            
        Kernel driver in use: uhci_hcd                                                                                                                           
        Kernel modules: uhci-hcd                                                                                                                                 

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
        Subsystem: Hewlett-Packard Company Device 3602                                                      
        Flags: bus master, medium devsel, latency 0, IRQ 19                                                 
        Memory at dc705c00 (32-bit, non-prefetchable) [size=1K]                                             
        Capabilities: <access denied>                                                                       
        Kernel driver in use: ehci_hcd                                                                      
        Kernel modules: ehci-hcd                                                                            

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 3602                                   
        Flags: bus master, fast devsel, latency 0, IRQ 22                                
        Memory at dc700000 (64-bit, non-prefetchable) [size=16K]                         
        Capabilities: <access denied>                                                    
        Kernel driver in use: HDA Intel                                                  
        Kernel modules: snd-hda-intel                                                    

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
        Flags: bus master, fast devsel, latency 0                                     
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0                  
        I/O behind bridge: 00008000-00008fff                                          
        Memory behind bridge: db600000-dc6fffff                                       
        Prefetchable memory behind bridge: 00000000d0400000-00000000d13fffff          
        Capabilities: <access denied>                                                 
        Kernel driver in use: pcieport-driver                                         
        Kernel modules: shpchp                                                        

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
        Flags: bus master, fast devsel, latency 0                                     
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0                  
        I/O behind bridge: 00006000-00007fff                                          
        Memory behind bridge: da600000-db5fffff                                       
        Prefetchable memory behind bridge: 00000000d1400000-00000000d24fffff          
        Capabilities: <access denied>                                                 
        Kernel driver in use: pcieport-driver                                         
        Kernel modules: shpchp                                                        

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
        Flags: bus master, fast devsel, latency 0                                     
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0                  
        I/O behind bridge: 00005000-00005fff                                          
        Memory behind bridge: d9600000-da5fffff                                       
        Prefetchable memory behind bridge: 00000000d2500000-00000000d34fffff          
        Capabilities: <access denied>                                                 
        Kernel driver in use: pcieport-driver                                         
        Kernel modules: shpchp                                                        

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
        Flags: bus master, fast devsel, latency 0                                     
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0                  
        I/O behind bridge: 00004000-00004fff                                          
        Memory behind bridge: d8600000-d95fffff                                       
        Prefetchable memory behind bridge: 00000000d3500000-00000000d44fffff          
        Capabilities: <access denied>                                                 
        Kernel driver in use: pcieport-driver                                         
        Kernel modules: shpchp                                                        

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
        Flags: bus master, fast devsel, latency 0                                     
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0                  
        I/O behind bridge: 00003000-00003fff                                          
        Memory behind bridge: d7600000-d85fffff                                       
        Prefetchable memory behind bridge: 00000000d4500000-00000000d54fffff          
        Capabilities: <access denied>                                                 
        Kernel driver in use: pcieport-driver                                         
        Kernel modules: shpchp                                                        

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
        Flags: bus master, fast devsel, latency 0                                     
        Bus: primary=00, secondary=07, subordinate=09, sec-latency=0                  
        I/O behind bridge: 00002000-00002fff                                          
        Memory behind bridge: d6600000-d75fffff                                       
        Prefetchable memory behind bridge: 00000000d5500000-00000000d64fffff          
        Capabilities: <access denied>                                                 
        Kernel driver in use: pcieport-driver                                         
        Kernel modules: shpchp                                                        

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
        Subsystem: Hewlett-Packard Company Device 3602                                        
        Flags: bus master, medium devsel, latency 0, IRQ 20                                   
        I/O ports at 90a0 [size=32]                                                           
        Capabilities: <access denied>                                                         
        Kernel driver in use: uhci_hcd                                                        
        Kernel modules: uhci-hcd                                                              

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
        Subsystem: Hewlett-Packard Company Device 3602                                        
        Flags: bus master, medium devsel, latency 0, IRQ 19                                   
        I/O ports at 9080 [size=32]                                                           
        Capabilities: <access denied>                                                         
        Kernel driver in use: uhci_hcd                                                        
        Kernel modules: uhci-hcd                                                              

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
        Subsystem: Hewlett-Packard Company Device 3602                                        
        Flags: bus master, medium devsel, latency 0, IRQ 16                                   
        I/O ports at 9060 [size=32]                                                           
        Capabilities: <access denied>                                                         
        Kernel driver in use: uhci_hcd                                                        
        Kernel modules: uhci-hcd                                                              

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
        Subsystem: Hewlett-Packard Company Device 3602                                        
        Flags: bus master, medium devsel, latency 0, IRQ 18                                   
        I/O ports at 9040 [size=32]                                                           
        Capabilities: <access denied>                                                         
        Kernel driver in use: uhci_hcd                                                        
        Kernel modules: uhci-hcd                                                              

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
        Subsystem: Hewlett-Packard Company Device 3602                                                      
        Flags: bus master, medium devsel, latency 0, IRQ 20                                                 
        Memory at dc705800 (32-bit, non-prefetchable) [size=1K]                                             
        Capabilities: <access denied>                                                                       
        Kernel driver in use: ehci_hcd                                                                      
        Kernel modules: ehci-hcd                                                                            

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
        Flags: bus master, fast devsel, latency 0                                  
        Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32              
        Capabilities: <access denied>                                              

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 3602                       
        Flags: bus master, medium devsel, latency 0                          
        Capabilities: <access denied>                                        

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
        Subsystem: Hewlett-Packard Company Device 3602                                         
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2296                           
        I/O ports at 9108 [size=8]                                                             
        I/O ports at 911c [size=4]
        I/O ports at 9100 [size=8]
        I/O ports at 9118 [size=4]
        I/O ports at 9020 [size=32]
        Memory at dc705000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 3602
        Flags: medium devsel, IRQ 11
        Memory at dc706000 (64-bit, non-prefetchable) [size=256]
        I/O ports at 9000 [size=32]
        Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
        Subsystem: Hewlett-Packard Company Device 3602
        Flags: fast devsel, IRQ 11
        Memory at dc704000 (64-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
        Subsystem: Intel Corporation Device 1211
        Flags: bus master, fast devsel, latency 0, IRQ 2295
        Memory at db600000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
        Subsystem: Hewlett-Packard Company Device 3602
        Flags: bus master, fast devsel, latency 0, IRQ 2297
        I/O ports at 6000 [size=256]
        Memory at d1410000 (64-bit, prefetchable) [size=4K]
        Memory at d1400000 (64-bit, prefetchable) [size=64K]
        Expansion ROM at d1420000 [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169


```

---

### Post by informer2000 on 2009-10-31
Ok, replying to myself here.. I figured out the cause of my problems. I was using the old kernel instead of the one that Karmic installed! All is well now.

---

### Post by HardcoreSSG on 2009-10-31
Graphical Issues as in:

Your graphics are really laggy.
Black screen
No desktop Effects
Etc.

Edit-- Wow the poll is almost even -- wasn't expecting that.

---

### Post by Uncle Spellbinder on 2009-10-31
> **HardcoreSSG said:**
> Graphical Issues as in:

Your graphics are really laggy.
Black screen
No desktop Effects
Etc.

Not seeing any of those. What graphics card do you have?

---

### Post by HardcoreSSG on 2009-10-31
> **Uncle Spellbinder said:**
> Not seeing any of those. What graphics card do you have?

Oh I don't have all of those, just the laggy graphics.
Here's my graphics card  (probably most of the problem)

VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller

I'm trying to find some fixes, with no luck.

@Uncle Spellbinder -- man your avatar freaks me out! LOL

---

### Post by dan_bwv1987 on 2009-10-31
Same issue here (same card)!! 
='(

---

### Post by dan_bwv1987 on 2009-10-31
> **The Desktop effect doesnt work on intel 82945G, it hangs 30 seconds after i enabled it, any ideas to solve it?luqeliverpudlian said:**
> 
='(

Same issue here (same card)!!

---

### Post by clhsharky on 2009-10-31
Not me

ATI X1650 open sourse stack Ubuntu 9.10 64-bit
My graphics has never been better.

---

### Post by Ter Rymon on 2009-11-02
VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller

Same card, problems GL 3D effects slow and choppy... no it is driver problem somewhere cause have another drive in machine with Pupppy Linux installed and works great...

It is an Integrated card on mother board so can't really see any need to buy one.   

Got compiz to operate but not function properly, lots of black or white squares where graphics and/or text should be.

Does not recognize monitor resolutions.

---

### Post by Minolan on 2009-11-03
Intel 82945g

Karmic doesn't detect any monitors. Works only in default mode 800x600 without any acceleration.

No luck with solution search.

---

### Post by jnew93 on 2009-11-03
> **Minolan said:**
> Intel 82945g

Karmic doesn't detect any monitors. Works only in default mode 800x600 without any acceleration.

No luck with solution search.

Try writing your own x-org.conf file, and make sure your graphics drivers are installed and specified in the conf file. Worked for me when my monitor wasn't detected.

This thread might help? [http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

---

### Post by knutola on 2009-11-03
I get a black screen. After upgrade from 9.04 to 9.10 or the Ubuntu 9.10 Live CD. I did the i915.modeset=0 workaround (as boot parameter). That worked kind of, but the graphic is getting slower each minute. Compiz is not working. I have a Lenovo G550 with Intel Core 2 Duo (Centrino 2) P8700, Mobile Intel GM45 Express 4500MHD
Now I am back in Ubuntu 9.04 that is working perfectly.

---

### Post by budge on 2009-11-03
Unfortunately I've had a poor experience with Karmic upgrade.

Almost immediately beset with problems regarding the screen brightness flickering after start up.

This is a well documented bug on launchpad I noticed (after upgrading..!)

Also at the moment I have no access to my Desktop after switching from Netbook Desktop to Classic Desktop. All I have now is a blank screen with the daisywheel "working" icon on the screen.
I have access to only a right click menu. But nothing else.

All this on a Medion Akoya E1210 (MSI Wind U100)  

Anyone know how to get Gnome working again?
Quite depressing as I'm having to write this message from a Windows machine...reinstall seems to beckon and back to Jaunty at that...any help much apprieciated.

---

### Post by ratcheer on 2009-11-03
I had issues immediately after the upgrade, but was able to fix them by installing the latest nVidia driver. The major obstacle to doing this was an inability to log in because of the rapidly flashing text screen.

Tim

---

### Post by Frantic_Earthling on 2009-11-03
My screen flickers.

Please see my previous post:

[http://ubuntuforums.org/showthread.php?t=1309617](http://ubuntuforums.org/showthread.php?t=1309617)

---

### Post by Regenweald on 2009-11-03
Kernel 2.6.31-14
nvidia on board GeForce 6150SE nForce 430
Driver 190.42

Video and effects fine.

---

### Post by Sunflower1970 on 2009-11-03
Yes. One minor, and one major.

Minor:
nVidia 7600GT. When I booted in to a fresh 9.10 install, I got the blinking screen of death. After some fiddling & reading on the forum, I was able to correct the problem and now have a perfectly working desktop--with effects. Very happy with this set up on the desktop.

Major:
ATI Radeon 7500 Mobility M6 LY. I know this graphics card works flawlessly with Compiz, since it did in 8.10 but I'm having a difficult time trying to figure out--when I have either Compiz or just normal effects on--I get strange white lines--kind of like TV snow--across only the top portion of my screen--and it's *only* on the wallpaper. Not on the taskbar, or in any programs I open. Very weird. I've tried a whole bunch of things and so far I've not found any fix for this. Oh, and turning off all effects really isn't an option because that causes a whole bunch of other problems--and I have no clue why that would be. I'm using the radeon driver. Tried the ati driver and that just causes the desktop to freeze.

I don't know if this may be a cause, but I'm using ext4 on all partitions.

---

### Post by edin9 on 2009-11-03
Open source ATi + Kubuntu Karmic = More artifacts than a museum.

---

### Post by NJC on 2009-11-03
Ubuntu 9.10 is issuing a crash report after Suspend, but my machine is still usable. But another problem I have is when the display is shut off via Power Management (not Suspend), it's not waking up. What a PITA, as I have to reboot the system. It appears to be this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/470926](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/470926)

---

### Post by SunnyRabbiera on 2009-11-03
Karmic is fine here

---

### Post by JayKay3000 on 2009-11-03
just decided to upgrade rather than fresh install because lazy and the newest nvidia driver running 9500gt keeps defaulting to negative image on video playback even when you re-set to normal, reverted to the old driver and is fine but the interface is a bit laggy on the old driver.

Ho hum.

Might try fresh install sometime to see if it fixes it with the newest driver.

---

### Post by scummy on 2009-11-03
I upgraded from 9.04, and I'm getting the same sorts of problems I saw in 9.04 with my Intel graphics (actually, I think it's worse than it was in 9.04). I did the x.org reversion in 9.04, and that worked well, but I was under the impression that this was going to be fixed for Karmic?

---

### Post by Redundant Username on 2009-11-03
My integrated graphics are working fine.  If only Karamic didn't freeze after login. T_T

---

### Post by John 19 on 2009-11-16
I had better performance with my Intel 4500 MHD GPU on Vista, I played some Nexuiz and with lower settings (aka everything off) same resolution as i used on vista 1280 x 800 and I can't get it past 35 fps in Ubuntu but on vista with the same and slightly better settings I could get 40-55 fps with some decent detail enabled. If I went to the lowest resolution, 640 x 480 on vista with all detail off I could get past 100 fps, Ubuntu 50 fps... weird.



Toshiba A305-S6872 3 GB RAM PC2-6400 800MHz, Intel Core 2 Duo T5800 2.0GHz, Intel 4500 MHD 128-1700?MB RAM

---

### Post by dca on 2009-11-16
A lot could stem from this:
 
[http://www.workswithu.com/2009/05/06/the-ubuntu-904-intel-graphics-fiasco/](http://www.workswithu.com/2009/05/06/the-ubuntu-904-intel-graphics-fiasco/)
 
...I know, I know, but I never perform upgrades, I only do fresh installs when I feel it necessary to update my systems. I always figured it (upgrading) never works w/o a hitch in Mac or Windows, why should I not expect issues w/ desktop Linux...

---

