---
title: "Increase resolution, virtualbox &amp; Ubuntu/Ultimate Edition"
date: 2011-01-21
forum: Virtualisation
---

### Post by Dutch70 on 2011-01-21
Hi all, I apologize for the long post.
 I am trying to increase the resolution to 1440x900 with Ubuntu 10.10 host & (Ubuntu based) Ultimate Edition 2.6 guest.

 I have installed the latest guest additions & tried the following steps in Terminal.

Output of... sudo nano /etc/X11/xorg.conf
gedit gave same result.
```
[COLOR="Lime"]Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection[/COLOR]
```

Also... from this tutorial... [***_[COLOR="Red"]HERE[/COLOR]_***]("http://ubuntuforums.org/showthread.php?t=720709&page=3")
```
david@david-desktop:~$ xrandr --newmode "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932
david@david-desktop:~$ xrandr --addmode "140x900"
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
david@david-desktop:~$ xrandr -s "1440x900"
Size 1440x900 not found in available modes

```

And from this one...[***_[COLOR="Red"]HERE[/COLOR]_***]("http://ubuntuforums.org/showthread.php?t=720709&page=3")
```
david@david-desktop:~$ gtf 1440 900 60

  # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

david@david-desktop:~$ xrandr --newmode "`gtf 1440 900 60 | grep Modeline | sed 's/.*Modeline //'`"
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
david@david-desktop:~$ 

```

As you can see, I've worked long & hard on this, as I have on this post.:tongue:, 
but I still can't get anything better than 800x600. I posted at their website/forums several days ago to no avail.

I would greatly appreciate if someone could tell me how to accomplish this. I know somewhere, someone has it running in a better resolution than 800x600.

Note: I've given the VM 1GiB of RAM & 64 MiB of video memory. PCLinuxOS & Linux Mint 10 run great with it in 1440x900.

Thanks in advance, I realize this is a monster of a problem/thread.   ](*,)
But we do love a good challenge, don't we! :P

---

### Post by Dutch70 on 2011-01-23
Well, I guess I made this post too long. Anyway, the problem has been solved from a thread I had in the Virtualbox forum.
 
Kudos to PerryG at Virtualbox.org. 

Here is a link to the Thread, in case anyone else needs it. 

[[COLOR="Blue"]http://forums.virtualbox.org/viewtopic.php?f=7&t=38350&p=172126#p172126[/COLOR]]("http://forums.virtualbox.org/viewtopic.php?f=7&t=38350&p=172126#p172126")

All I ended up doing is deleting my xorg.conf file. The part that is now in green at the top of post #1. Save it & update-grub.

---

### Post by J0hnny12Gage on 2012-03-10
Just thought I'd post this for others having this issue and run across this. What worked for me is:

1. Open terminal
2. type this
```
sudo apt-get install virtualbox-guest-dkms
```3. restart virtual machine


I'm now getting 1920x1080 resolution

p.s. got this from this thread: [http://ubuntuforums.org/showthread.php?t=1930200](http://ubuntuforums.org/showthread.php?t=1930200)

---

### Post by Bouvet on 2012-06-24
Thanks for the tips everyone.
I just installed Ultimate Ed. in VB
and instantly wanted the large view.
I'll follow what you guys did.

---

### Post by Bouvet on 2012-06-24
> **Bouvet said:**
> Thanks for the tips everyone.
I just installed Ultimate Ed. in VB
and instantly wanted the large view.
I'll follow what you guys did.

):P**Follow Up**: I installed the Guest Edition and
I was able to get a nice full screen.
I'm really liking UEd.

---

