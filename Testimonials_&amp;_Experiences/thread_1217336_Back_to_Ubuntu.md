---
title: "Back to Ubuntu"
date: 2009-07-19
forum: Testimonials &amp; Experiences
---

### Post by drvista on 2009-07-19
[SIZE="5"][COLOR="Red"]Hey Do you Remember Me ???[/COLOR][/SIZE]
**couple of months ago i posted** 
#"I am out "
[http://ubuntuforums.org/showthread.php?t=1053162](http://ubuntuforums.org/showthread.php?t=1053162)
#"future of ubuntu"
[http://ubuntuforums.org/showthread.php?t=977415](http://ubuntuforums.org/showthread.php?t=977415)
But jaunty make me come back :)
I am using Jaunty now and very happy with it WHY ?? i can tell you

My Hardware 
I am  using a fujitsu Siemens Amilo PI1505 LAPTOP 
1.86GHZ Centrino Duo with 2MB cache
3GB of DDR2 RAM
256 Intel GMA 945
Harddisk WD160GB

I moved out to windows vista from ubuntu after struggle to get a usable Desktop but with jaunty i found most have gone well. 

 Problems I found gone after install that was here in previous releases
1. bluetooth works great now :)
2. boot time is great better than ever (still slower than windows 7)
  thanks to EXT4
3. Firefox flash website crash solved :)
4. battery life improvements 
5. better search tool with tracker ( last time i used ubuntu i used beagle that sucked my resources 
6. better SMB
7. Better Video experience than intrepid even i use jaunty that has issues with intel graphics still have the tearing issue ( solved with unredirect full screen in compiz )
8. Banshee is now better than ever 

what is have fixed my self 
1. Fix for Fn + F5 or Fn + F6 causes keyboard to crash >>
   Bug reported at 
                [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/320793](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/320793)
   Solution found at 
                [http://ubuntuforums.org/showthread.php?t=974723](http://ubuntuforums.org/showthread.php?t=974723)
2. Audio Jack sense issue causes pluging in the audio jack never mute the laptop speakers 
    
Fix 

$ sudo nano /etc/modprobe.d/alsa-base 

and adding the line:

options snd-hda-intel model=fujitsu-pi2515

To the end as it was the nearest model to mine.


then installed some apps to make ubuntu bloat enough :)
 then after i made my perfect ubuntu desktop i followed the solution found in 
[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)
to make it live cd and carry it with me on my usb stick using 
unetbootin
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

please what do you think :)

---

### Post by HappyFeet on 2009-07-19
[Welcome back]("http://www.youtube.com/watch?v=QVS3WNt7yRU")

---

### Post by barkej on 2009-07-19
Welcome back!

---

### Post by philcamlin on 2009-07-19
good to see you back :D

---

### Post by binbash on 2009-07-20
Welcome Back

---

