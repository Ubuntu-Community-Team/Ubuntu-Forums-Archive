---
title: "Using a USCutter Refine MH1351 Vinyl Cutter with Inkscape in Linux (Easy)"
date: 2010-06-18
forum: Tutorials
---

### Post by musicman3569 on 2010-06-18
If you're like me and have been looking everywhere for a way to use one of these vinyl cutters (works for other types of vinyl cutters, too), this is the place!  Thanks to [this extension]("http://inkcut.sourceforge.net/") called InkCut for Inkscape, you can output directly to the cutter.  No more Windows and that SignBlazer junk the cutter came with!

1) First, you will need Inkscape 0.47 or higher for the extension to work.  This is what comes with Ubuntu 10.04, which is what I tested this on.  You can get it from [here]("http://inkcut.sourceforge.net/"); I also have it attached to this post just in case.  Go to where you downloaded the file, right-click, and Extract Here.

2) You should get an InkCut-1.0 folder.  Open that folder, and select both the inkcutext1.inx and inkcut folder, and copy them to /home/yourusername/.config/inkscape/extensions.  This installs the extension so it will be available in Inkscape.

3) Connect the vinyl cutter.  I used USB on a USCutter Refine MH1351.  The USB port on the cutter is really just a serial port emulator, but fortunately, the driver is preinstalled in the kernel.  If you want to make sure it connected, just run:
```
dmesg | tail
```
You should see something like:
```
[ 4723.116132] usb 2-1: new full speed USB device using uhci_hcd and address 5
[ 4723.312345] usb 2-1: configuration #1 chosen from 1 choice
[ 4723.321355] ftdi_sio 2-1:1.0: FTDI USB Serial Device converter detected
[ 4723.321502] usb 2-1: Detected FT232RL
[ 4723.321518] usb 2-1: Number of endpoints 2
[ 4723.321533] usb 2-1: Endpoint 1 MaxPacketSize 64
[ 4723.321548] usb 2-1: Endpoint 2 MaxPacketSize 64
[ 4723.321562] usb 2-1: Setting MaxPacketSize 64
[ 4723.322254] usb 2-1: FTDI USB Serial Device converter now attached to ttyUSB0
```
Now we know that it is connected as /dev/ttyUSB0.  I never had to do anything with this, but now you know just in case.

4) Now for the fun!  Go into Inkscape, open some file you want to try cutting (maybe make a star if you don't have anything).  Be sure to change all objects to paths.  Start by ungrouping everything.  Then select everything and go to Path > Object to path.  Now select everything and go to Path > Union.  Now you have a single path that's ready to cut!

5) Select your new path, and go to Extensions > Cutter / Plotter > InkCut.  For me, all the defaults were fine -- I didn't have to mess with the properties at all.  It didn't show anything for device, but don't worry, it still works.  If you are having trouble, you can go to the Properties button, I had "Serial" for the interface, and then expand the Serial tree and the port should be what was listed in step 3 on the output (/dev/ttyUSB0 for me).  If you hit "Test Connection" the vinyl should move.

6) You can make any adjustments you need to the material size/margins, but in general you can just go for testing purposes.  Hit the "Plot Paths" button and then "Send".  It should cut it out.  Woohoo!

I imagine this can be adapted for other cutters, but I know for this model I didn't find anything indicating any hope for Linux, so here it is.  Enjoy!

---

### Post by kmrs75 on 2010-06-23
i have been looking at that too but i cant get ver 1.0 to work 

i use tux plot - its a stand alone program so you can use it for any program your not limited to just inkscape 

graphtec ce series

---

### Post by diesel_here on 2010-07-06
I started using this Inkscape extension today and thought I would share my experience.

Installed Inkscape, downloaded Inkcut 1 and extracted files to the correct directories as above.

Upon first, eager try, it would not work.  Upon some searching I found that I needed two files to be installed for it to work:

librsvg2-common
python-serial (as mentioned in readme)

After this, it worked perfect, apart from cutting in reverse!

I did check the invert Y axis, but it spat out the material.  I will try altering the start point or just keep clicking the horizontal flip before plotting.

I'm very happy with this, for me this really is a great leap forward in Linux.  This actually ran a Creation plotter that my expensive sign program in win would not!

Great work

---

### Post by frmdstryr on 2010-07-19
> **musicman3569 said:**
> 
I imagine this can be adapted for other cutters, but I know for this model I didn't find anything indicating any hope for Linux, so here it is.  Enjoy!
Thanks for posting this, and continue to post away! But if you can, please post a link to the **[sourceforge project page]("http://inkcut.sourceforge.net")**. That way users can post messages to the forums etc..

Happy cutting :D

---

### Post by slick_nick on 2011-06-16
Thanks for the awesome post!

I just spent less time installing Ubuntu alongside Windows 7 on my work computer (exclusively Ubuntu at home for years now) and doing a test cut than I did searching and worrying about getting our USCutter Ecocut to run under 64bit Windows 7. Ubuntu FTW!

---

### Post by Canuckian84 on 2013-05-10
With a few minor tweaks using chmod, and Udev, i got this running fine with my 12.04 laptop and my USCutter Model SC. Now i don't have to mess with the aging winxp computer our engraver is slaved to! :D

---

### Post by holotone on 2013-10-07
> **Canuckian84 said:**
> With a few minor tweaks using chmod, and Udev, i got this running fine with my 12.04 laptop and my USCutter Model SC. Now i don't have to mess with the aging winxp computer our engraver is slaved to! :D

It took me about an hour of looking to figure out what Canuckian84 did here - For future reference it may be nice to leave notes instead of teasing us. :D

Here's the extra command to get the USCutter SC Series plotter to work with InkCut

```
chmod 666 /dev/ttyUSB0
```

Replace ttyUSB0 with the location of your plotter.

---

### Post by lordoja-3x6 on 2014-06-05
So i've been trying to get this going on 14.04LTS... bit of a hiccup :(
When i go under Extensions > Cutter/Plotter nothing comes up but a little line... according to apt-get all the stuff needed for the extension are up to date.
The only thing i had to do differently was -C to /usr/share/inkscape/extensions instead of .config because it kept returning a "no such file..." error.
HALP PLS! i wanna ditch win7 already lol

---

### Post by SamSung on 2014-11-27
Hi I am having the same issue with installing inkcut to 14.04lts does anyone have any ideas. I have posted on inkcut sourceforge page as well.

Thanks in advance

---

