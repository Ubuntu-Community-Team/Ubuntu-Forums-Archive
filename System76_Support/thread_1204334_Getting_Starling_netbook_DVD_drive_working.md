---
title: "Getting Starling netbook DVD drive working"
date: 2009-07-04
forum: System76 Support
---

### Post by hfoster on 2009-07-04
We just received our Starling netbook yesterday, and have had pretty good luck in setting up and getting started. I purchased an external DVD drive with the netbook and have not been able to get it to work. First, what should I plug in and where? The USB cable that comes with the drive has two 'A' plugs - I assume that both need to be plugged into USB ports on the computer?

With the drive plugged in and a disc in the drive, I can see the disc in the right hand pane of the desktop, but when I click the eject icon next to it I get this message:

[FONT=Courier New]Cannot eject volume

There was an error ejecting the volume or drive.

org.freedesktop.Hal.Device.Volume.UnknownFailure: eject: unable to find or open device for: `/media/cdrom1'Cannot eject volume[/FONT]

I vaguely understand that some software needs to be installed and followed the instructions in the system help:

[FONT=Courier New]Install the libdvdnav4, libdvdread4, gstreamer0.10-plugins-bad and gstreamer0.10-plugins-ugly packages.
            
If you would like to play encrypted DVDs, press Applications &#9656; Accessories &#9656; Terminal and type the following into the screen which appears, followed by the Enter key: 
            
sudo /usr/share/doc/libdvdread4/install-css.sh

Enter your password if prompted. The libdvdcss2 package will be downloaded and installed from a website.
       
Insert a DVD into your drive. It should open automatically in the Movie Player.[/FONT]
            
These steps apparently worked (no error messages). I inserted a DVD in the drive but the Movie Player did not open. I launched Movie Player and clicked Movie - Play Disc. I got this message:

[FONT=Courier New]Totem was not able to play this disc.

You are not supposed to show G_IO_ERROR_FAILED_HANDLED in the UI.[/FONT]

What do I need to do to get this working?

---

### Post by hfoster on 2009-07-05
Followup: I plugged the DVD drive into my PowerBook and inserted a disc. The drive appeared on my desktop, DVD Player launched, and the movie started playing. It appears that the drive itself is functional, must be some issue with setting up Ubuntu or the Starling.

---

### Post by thomasaaron on 2009-07-06
Follow the instructions here...

[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

NOTE: Follow the 32-bit instructions.

You also might want to install vlc...

sudo apt-get install vlc

I get better results with vlc than with Totem.

---

### Post by hfoster on 2009-07-06
Thank you. I followed those instructions but am still getting the same errors from movie player.

I installed vlc and it does indeed play my movie. I find the user interface to be a little harder to use, so if anyone can offer some assistance in getting movie player working I'd appreciate it.

---

