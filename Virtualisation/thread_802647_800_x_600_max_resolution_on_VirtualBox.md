---
title: "800 x 600 max resolution on VirtualBox ?"
date: 2008-05-21
forum: Virtualisation
---

### Post by Osvaldo on 2008-05-21
Hi.

I'm using Xubuntu on a VirtualBox 1.6.0 and the screen only shows at 800x600. I would like to use it in 1024x768.

I've used other distros (Slax, Puppy, DSL) and all OK. All of them allow 1024x768.

Best,

Osvaldo

---

### Post by shifty_powers on 2008-05-21
so it does not give you the option for 800*600?

have you tried going into the xorg.conf file?

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by p_quarles on 2008-05-21
Moved to Virtualization.

Have you installed the Guest Extras package for VirtualBox? That is necessary to get full resolution in most guest OSes.

---

### Post by Osvaldo on 2008-05-21
Hi.

How do I install Guest Extras package for VirtualBox? I Google it and I didn't found an howto.

I'm using an Intel Mac and VB1.6.0

/etc/X11/xorg.conf doesn't give me any information about the monitor resolution.

Thank you very much for your help.

Best

Osvaldo

---

### Post by Skeet on 2008-05-21
You must open your Virtualbox image, I think its xxxxxxxx.vmx, where the x's are your image name.

Open it in a text editor, and add the following lines:

```

svga.maxWidth = "1400"
svga.maxHeight = "900"

```

Or whatever resolution you want. This should unlock the resolution you need in the display properties of your guest OS.

---

### Post by Osvaldo on 2008-05-22
Skeet: Thanks for the help, but as I didn't found the files I looked in Google and the procedure you described is for Vmware. I'm using VirtualBox on the Mac.


Does anyone knows how to force Vesa card and 1024x768 ? I guess the reason that works in other OS'es is that they use this.


Best

Osvaldo

---

### Post by Osvaldo on 2008-05-22
SOLVED:

Here's how I did it:

1 - I've boted SLAX (A Linux Live CD distro) using xVesa for the graphics

2 - I've copied the file in Slax:

/etc/X11/xorg.conf

to an USB Pen

3 - I've copied the Ubuntu xorg.conf to the same USB

4 - I've edited the ubuntu file replacing some elements by the elements in the slax file.

5 - I've loged in Xubuntu in the terminal mode and then:

sudo cp ./xorg.conf /etc/X11/xorg.conf

exit

6 - Just logged in normally.
-----------------------

---

### Post by Skeet on 2008-05-22
Ah I didn't check what os you were using. I wasn't too sure if it worked in VirtualBox. Good job figuring it out though.

Have fun!

---

### Post by Osvaldo on 2008-05-22
In case anyone needs it, the sections I've replaced:

-------------------------

Section "Device"
    Identifier  "VESA Framebuffer"
    Driver      "vesa"
    #VideoRam    4096
    # Insert Clocks lines here if appropriate
EndSection

Section "Monitor"
  	Identifier  "My Monitor"
    	HorizSync   31.5 - 150.0
    	VertRefresh 75-85
EndSection

Section "Screen"
    Identifier  "Screen 1"
    Device      "VESA Framebuffer"
    Monitor     "My Monitor"

# If your card can handle it, a higher default color depth (like 24 or 32)
# is highly recommended.

#   DefaultDepth 8
#   DefaultDepth 16
   DefaultDepth 24
#   DefaultDepth 32

# "1024x768" is also a conservative usable default resolution.  If you
# have a better monitor, feel free to try resolutions such as
# "1152x864", "1280x1024", "1600x1200", and "1800x1400" (or whatever your
# card/monitor can produce)

    Subsection "Display"
        Depth       8
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       32
        Modes "1024x768" "800x600" "640x480"
    EndSubsection

EndSection

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Simple Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.  In this example, screen 2 is located to the
# right of screen 1.

    Screen "Screen 1"

EndSection




-------------------------------------

---

### Post by BobLand on 2008-05-23
I have this same problem.  Host=Gutsy, guest=Kubuntu 8.04 w KDE4.0.4.  I copied my existing xorg.conf to the guest.  Lost the graphical interface.  Copied the original back.  Tried the sample code at Innotek.  That didn't work either.

CPU Intel DualCore
RAM 2G
Video GeForce 8400
Monitor Samsung 226BW

I did see enough of Kubuntu to determine that I will install it as a dual boot.  However, my wife needs to run XP and doesn't like dual booting so I'm hoping that I can get a full screen XP in VirtualBox.

bobland

---

### Post by quonsar on 2008-05-23
i had the same problem with kubuntu 8.04 but solved it completely by mounting /usr/share/virtualbox/VBoxGuestAdditions.iso, opening it in Dolphin and double clicking on the install script for linux guest additions. then I just restarted the virtual machine and i got my max resolution, seamless mode, automatic guest screen resizing and the whole works.

---

### Post by Osvaldo on 2008-05-24
Bobland: Have you tried to:

1) Boot Slax in VESA ( 1024x768 )
2) Copy the xorg.conf sections above to a usb stick
3) Replace the same sections in your Kubuntu

Don't forget to make a backup of your old xorg.conf


It worked for me.


Best,

Osvaldo

---

### Post by LycanKing on 2009-10-01
I found the best way to fix this was to install the guest additions option.

1) Load up Ubuntu in Sun VirtualBox
2) Click "Devices" at the top left
3) Choose "Install Guest Additions"

This will then put a picture of a cd on your desktop. 

4) Open this cd up to view the files


5) Double click autorun.sh
6) At the prompt click "Run in Terminal"

This will then install a few moduals onto your Ubuntu Guest OS, once it has successfully installed restart and your graphics res problem should be fixed, PLUS you should be able to use seemless mode and the mouse intergration option. Both very fun to play with :-)

Hope this helps!

Regards,

Kevin

---

### Post by TheBuzzSaw on 2009-10-01
This thread is a year and a half old. O_o

---

### Post by Technical on 2010-05-27
> **shifty_powers said:**
> so it does not give you the option for 800*600?

have you tried going into the xorg.conf file?

```
gksudo gedit /etc/X11/xorg.conf
```

My xorg.conf file is empty.
I can't reconfigurate Ubuntu 10.04 monitor resolution into VirtualBox.
I've looked in a lot of threads and places, Googled...
Does anybody know a real solution?
Of course I have the latest VirtualBox and the latest Guest Addons installed.

---

