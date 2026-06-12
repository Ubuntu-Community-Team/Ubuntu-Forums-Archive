---
title: "HOWTO: Hauppauge WinTV PVR-USB2"
date: 2006-04-13
forum: Tutorials
---

### Post by ErikTheRed on 2006-04-13
After buying this tuner I was frustrated with the terrible linux driver support for it. I was finally able to get it working with the drivers from [http://www.isely.net/pvrusb2/pvrusb2.html]("http://www.isely.net/pvrusb2/pvrusb2.html")

I'll now go through the process I went through to get my drivers installed and working. As a note I am using Dapper along with a 2.6.16 kernel I compiled myself, but I believe this should work for 2.6.15 as well. The main driver page has some tips for older kernels (I'll try to put these in my howto).

1. Download the latest driver package from this page: [http://www.isely.net/pvrusb2-download.html]("http://www.isely.net/pvrusb2-download.html")

2. Extract the driver package
> ~$ tar -xvjf pvrusb2-mci-20060329.tar.bz2

3. Extract the tuner's firmware from the Windows driver package.
For this step I had to use the drivers straight off of the driver CD.
Navigate to the utils directory
> cd pvrusb2-mci-20060329/utils
There are several ways to extract the firmware:

a. run the fwfind.sh script (this method did not work for me)
> sh fwfind.sh
This will try and extract the firmware automatically (I believe it scans your cdrom for the appropriate files, so make sure you have your driver CD inserted.)

b. run the extractfw.pl script (this didn't work for me either)
First off you'll need to make a win_driver folder within the utils folder.
> ~/pvrusb2-mci-20060329/utils$ mkdir win_driver
Next you'll need to copy the driver files from your CD or from the driver package from Hauppauge's site to the win_driver directory.
If this process is successful you will have the following two files in your utils directory:
> v4l-pvrusb2-29xxx-01.fw
v4l-cx2341x-enc.fw

c. run the older firmware extract script. (This is what I had to do)
This script is named "old-extract-firmware.pl"
I had to edit two lines before it worked for me:
> my $fx2pos = **03774540**;
my $xxxpos = **00774540**;
Now run the script (Obviously you'll need to change the path to wherever HCWUSB2.sys resides.)
> ~/pvrusb2-mci-20060329/utils$ perl old-extract-firmware.pl /media/cdrom/HCWUSB2.sys
The old script gives you two files in the utils folder, which you'll have to rename
(original files being on the left and the renamed on the right):
> pvrusb2.f1 -> v4l-pvrusb2-29xxx-01.fw
pvrusb2.f2 -> v4l-cx2341x-enc.fw

4. Install the .fw files
Reguardless of how you obtain these files you'll need to copy them to the /lib/firmware/"your kernel"/ directory:
> ~/pvrusb2-mci-20060329/utils$ sudo cp *.fw /lib/firmware/'uname -r' 

5. Compile and install the driver.
Navigate to the "driver" directory within the pvrusb2 package.
Now compile and install the driver:
> sudo make
sudo make install

(5B) **LOWER THAN 2.6.15 ONLY**
For those using a kernel below 2.6.15 you will need to compile and install ivtv. The driver package includes a snapshot of ivtv in the ivtv folder. You will need to compile and install this:
> sudo make
sudo make install
You may want to restart after installing ivtv.


6. Initialize the driver
To start the driver run the following commands:
> sudo depmod -a
sudo modprobe pvrusb2

That should do it. I'm currently in the process of setting up MythTV, and I'll let you know if it works.

---

### Post by ErikTheRed on 2006-04-16
Unfortunately my Kubuntu install decided to go haywire. I'll reinstall and try to see if the tuner works with MythTV.

I want to get this working so badly.

---

### Post by ErikTheRed on 2006-05-10
I didn't have any success getting the tuner to work with MythTV. For some reason the driver seemed to install fine, but I couldn't seem to read the stream with anything. The author of the driver has reorganized his site and rewritten his install instructions, I may give them another try.

---

### Post by kyleabaker on 2009-03-15
Anyone had any luck with this in Intrepid (or Jaunty)? I've been thinking about trying to get mine setup to convert some home vhs videos to dvds, but I wasn't sure if it was worth the effort in Linux or not.

---

### Post by netmanny on 2009-03-16
You can try the method suggested in this web page is not for the specific one but you already have the bases for yours...
[http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)

---

### Post by markackerman8@gmail.com on 2010-04-17
I am trying my fourth!! Tuner card to get analog cable working with MythTV.  I have done everything in the Mythtv/WinTV-PVR-USB2 SITE and [http://www.isely.net/pvrusb2](http://www.isely.net/pvrusb2), but still NO LUCK when I select "watch tv".

Has anyone got this to work (its 4 years old and reported to work with mythtv, so I would hope so), and help me troubleshoot?

My dmesg compared to a known working one is identical with the exception of any mention of cx88XX?  Does this mean anything here is my dmesg, and I surely promise replies to any responses, 

thanks so much in advance.  :KS

---

### Post by markackerman8@gmail.com on 2010-04-17
sorry double posted. so I deleted its text,

I managed to get it working with MythTV, and a problem with the livetv was that I needed to have the storage folders permissions set to mythtv:mythtv (user:group).  I just changed my mysql database mythconverg to myloginNAME and myloginPASSWORD and that solved it.

This seems like a dead thread but if anyone needs any more info I would be glad to help

---

### Post by markackerman8@gmail.com on 2011-08-20
This is in response to an email from William Fanning, for help.  So I thought I would claen up my own how to notes a bit and post them here.  They are still a bit disjointed (I appolobgize) but may help some one, none the less.  To start off, my pvrusb2 is working without any driver or firmware efforts in ubuntu's present kernel (often hit and miss with new kernels though).  So if one sees the card using "device manager" from synaptic or using the dmesg command, then it is likely something to do with the setup of mythtv.


Mythtv -in mythbackend setup use as tuner card type -  IVTV-MPEG
 &#8728; type in the card even if it does not display it in dropdown,   ex. /dev/video1
   &#8227; then the name hvr pvrusb2 should show up
• last got working after cleaning up old kernels &
  &#8728; also v4l update though it seemed to be compiling into old kernel
  &#8728; also erased old kernel folders in /lib/modules
  &#8728; loaded v4l-cx25840.fw firmware was the only one of 3 showing in dmesg, and still worked

• # You must (sometimes) compile and install the pvrusb2 driver itself.
• # You must obtain and install the required firmware images.
  &#8728;  this tarball. It can be found at [http://dl.ivtvdriver.org/ivtv/firmware/](http://dl.ivtvdriver.org/ivtv/firmware/)
    &#8227; [http://www.steventoth.net/linux/hvr1950/v4l-pvrusb2-73xxx-01.fw](http://www.steventoth.net/linux/hvr1950/v4l-pvrusb2-73xxx-01.fw)
  &#8728; Driver compilation and installation
    &#8227; Note: Even if you choose to run the in-kernel version or V4L hosted version of this driver, you will still need to obtain (extract or otherwise fetch) and install the firmware.
    &#8227; Compilation and installation of the in-V4L driver (standalone is mikes more up to date)
      &#8227; see note v4l-dvb, 
    &#8227; You must have udev or its equivalent installed in order for this driver to work
  &#8728; Firmware retrieval and installation
    &#8227; OK here we go I got the firmware process started from [http://www.isely.net/pvrusb2/setup.html#Firmware](http://www.isely.net/pvrusb2/setup.html#Firmware) starting in WinTV-PVR-USB2/pvrusb2-mci-20100221/utils/ directory
    &#8227; you should then see the following three firmware files:
      • v4l-pvrusb2-24xxx-01.fw	       8 KB
      • v4l-cx2341x-enc.fw                368 KB
      • v4l-cx25840.fw                         16 KB
    &#8227; Copy the firmware images to the appropriate location from
      • cd /home/ack/System/Ubuntu_Apps/LinuxTV/PVR-USB2/24xxx_Firmware/
      • sudo cp *.fw /lib/firmware/2.6.3*-**-generic/         (put in the right *'s)
      • On my Debian system, viable locations include:
        &#8728; /lib/firmware/2.6.##.##-generic  ? it is the place for 950Q firmware?
        &#8728; /lib/firmware
        &#8728; /usr/local/lib/firmware XX
        &#8728; /usr/lib/hotplug/firmware  XX
        &#8728; /usr/src/linux-headers..../firmware
 

I hope this helps someone !

---

### Post by saedelaere on 2011-10-07
Just in case someone is searching for a lightweight app to watch and record TV with the Hauppauge PVRUSB2 or similar ivtv devices you could have a look at [TV-Viewer]("http://tv-viewer.sourceforge.net/mediawiki/index.php/Main_Page").

Regards

---

