---
title: "Microphone in Gazelle Professional stops working afer closing laptop lid"
date: 2013-09-27
forum: System76 Support
---

### Post by LBAWinOwns on 2013-09-27
I recently got myself a  gazp9 (Gazelle Professional 9), and now I'm experiencing an easy to reproduce issue with the microphone:

[LIST=1]
[*]Start computer
[*]Open 'Sound' application - Microphone works! :)
[*]Close laptop lid
[*]wait 5 seconds for it to hibernate
[*]Open lid
[*]Open 'Sound' applicatoin - Microphone doesn't work. :(
[*]
[/LIST]

By work I mean that  when I go to the "Input" tab, I can say something and the meter actually increases decreases with the loudness of my tone. When it's "broken", the meter is stuck at zero. I've actually tried skype with the two configurations (before and after a hibernation) and it seems to only work before hibernation. As expected.

**Additional info:**

I run Ubuntu 13.04. I *did* reinstall Ubuntu once when I got the computer (to partition my drive). I've installed the system76 drivers (apt-get install it, then run system76 as root and click on install and rebooted)

Not that I think it matters but here are all the details of my computer:

```

Gazelle Professional ( gazp9 )     Quantity: 1     Price Per Item: $1,356.00 $1,356.00
Base System Price     $829.00
Ubuntu 13.04 64 bit    
5 Free GB of Ubuntu One Online Storage and Sync    
15.6" 1080p Full High Definition ColorPro IPS Display with Matte Surface ( 1920 x 1080 )     +$59.00
Intel® HD Graphics 4600    
4th Generation Intel® Core™ i7-4800MQ Processor ( 2.7 GHz 6MB L3 Cache - 4 Cores plus Hyperthreading )     +$189.00
8 GB Dual Channel DDR3 SDRAM at 1600MHz - 2 X 4GB     +$49.00
United States Keyboard Layout    
240 GB Crucial M500 Series mSATA Solid State Drive     +$195.00
No Secondary Hard Drive    
8X DVD±R/RW/4X +DL Super-Multi Drive    
Killer™ Wireless-N 1202 802.11 A/B/G/N Wireless LAN + Bluetooth 4.0 Combo Module     +$35.00 

```

---

### Post by LBAWinOwns on 2013-10-09
I got help from the System76 support here. Basically there are two temporary solutions that "works for me (tm)":

1. Put anything in your microphone jack and pull it out. Then the regular microphone starts working again (yuo can also put in earphones)
2. Do (1.) but through software. The software `pavucontrol` ([https://apps.ubuntu.com/cat/applications/pavucontrol/](https://apps.ubuntu.com/cat/applications/pavucontrol/)) does this.

Would be even better to do this through the command line and of course even better to have a permanent fix.

---

