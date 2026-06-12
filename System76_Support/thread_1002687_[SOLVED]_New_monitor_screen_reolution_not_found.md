---
title: "[SOLVED] New monitor screen reolution not found"
date: 2008-12-05
forum: System76 Support
---

### Post by ewg on 2008-12-05
System 76 Sable
Ubuntu 8.10

Sable Video = Integrated nVidia GeForce 6150

Just got a LG W2241T WS monitor. It can take 1680x1050 resolution at 60Hz. But in configure display all I can get to is 1280x1024 at 50/51Hz. It says "rotation not supported". The monitor is not detected. 
Is there a way to fix this?

Thanks,

---

### Post by ladgrove on 2008-12-05
Hi ewg, can you please post the contents of your xorg.conf (in a terminal, sudo cat /etc/X11/xorg/conf) file and the output of xrandr (simply xrandr in a terminal). 

Do you know which sort of drivers you are using for your card? Are you using restricted drivers for instance? Google about or scan these forums to see if anyone else has used particular drivers for your card.

---

### Post by ewg on 2008-12-05
I did do a google search and found no matches for the monitor drivres.

Here is the output you requested:

[sudo] password for ewg: 
cat: /etc/X11/xorg/conf: No such file or directory
ewg@ubuntu:~$ xrandr
Screen 0: minimum 320 x 240, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      50.0     51.0* 
   1280x960       52.0  
   1152x864       53.0     54.0     55.0     56.0  
   1024x768       57.0     58.0     59.0  
   960x600        60.0  
   960x540        61.0  
   896x672        62.0  
   840x525        63.0     64.0     65.0     66.0  
   832x624        67.0  
   800x600        68.0     69.0     70.0     71.0     72.0     73.0  
   800x512        74.0  
   720x450        75.0  
   680x384        76.0     77.0  
   640x512        78.0     79.0  
   640x480        80.0     81.0     82.0     83.0  
   576x432        84.0     85.0     86.0     87.0  
   512x384        88.0     89.0     90.0  
   416x312        91.0  
   400x300        92.0     93.0     94.0     95.0  
   320x240        96.0     97.0     98.0  
ewg@ubuntu:~$

---

### Post by ladgrove on 2008-12-05
Ok, with the first command, you don't need a colon : there so, assuming you are aware of the sudo pwd, simply type:

sudo cat /etc/X11/xorg.conf

OK, it seems as though the graphics card drivers have been limited to 1280x1024, but there should be a way to boost that up.

Without seeing the xorg.conf file, it's a bit difficult, but maybe take a look at these links and see if they help out.

Once we have the output of your xorg.conf file, we can ascertain whether you're using vesa, nvidia, nv or some other drivers and go from there.

I would suggest, though I may not be 100%, that your best bet is to:

1)Ensure you're using the 'appropriate' driver - nv, nvidia, vesa, this requires some experimentation

2)Try adding a custom modeline to the xorg.conf file (But always make a backup of this file first!) Custom modelines are generated in the terminal by, for eg

>> cvt 1680x1050 60.0

which outputs

[FONT="Courier New"]
# 1680x60 50.22 Hz (CVT) hsync: 3.82 kHz; pclk: 8.00 MHz
Modeline "1680x60_60.00"    8.00  1680 1728 1888 2096  60 63 73 76 -hsync +vsync
[/FONT]

*Note that the line that starts with the hash is a comment, eg, you could put anything here, it's just information*

3)Try adding a custom modeline using xrandr, you'll have to use the commands --newmode & --addmode I believe, but I'm no expert. If you type 

>>xrandr -h | more

into a terminal and have a read through, this might help out.

Sorry I can't be more helpful, but also check out these links and see if they provide any food for thought.

**Changing Resolution in xorg.conf**
[http://ubuntuforums.org/archive/index.php/t-83973.html](http://ubuntuforums.org/archive/index.php/t-83973.html)

That's about as much as I can help out, but please post your xorg.conf file and that might explain some things and hopefully some other users can offer their suggestions too, as I'm by no means an expert. Please  be patient though, things like this can be frustrating, but once they're sorted, it's well worth it :)

---

### Post by chongzi889 on 2008-12-08
Mud Valve is one of api 6a **[gate valve](http://www.valvesupplier.net/index.htm)**,operated by double actuated thread, and featuring tight structure. The series [gate valve]("http://www.valvesupplier.net/index.htm") had been widely used in oil field, crude exploitation

---

