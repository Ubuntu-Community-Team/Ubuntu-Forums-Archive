---
title: "DVDs dont play"
date: 2008-04-22
forum: System76 Support
---

### Post by iheartubuntu on 2008-04-22
Getting this error message:

> Totem could not play "dvd:/".

The source seems encrypted, and cant be read. Are you trying to play an encrypted DVD without libdvdcss?

I checked Synaptic and libdvdcss is installed already.

---

### Post by eddietours on 2008-04-22
try this 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by iheartubuntu on 2008-04-23
The problem is it already installed. libdvdcss is installed too and yet playing a DVD movie doesnt work. The drive itself works fine.

---

### Post by iheartubuntu on 2008-04-23
Any suggestions from System76? Thanks.

---

### Post by shortylonglegs on 2008-04-23
This happened to me too.  I installed Totem-xine rather that the default.  I think I also installed Automatix and some codecs from in there, but try totem-xine first.

---

### Post by asmiller-ke6seh on 2008-04-23
> **shirteesdotnet said:**
> Any suggestions from System76? Thanks.

I am sure that System76 folks would appreciate it is you also posted which machine you have - I remember something that was model specific related to this situation.

---

### Post by iheartubuntu on 2008-04-23
Its a System76 Serval Performance. Model number is either FL92 or SERP4

---

### Post by SunnyRabbiera on 2008-04-23
what player are you using?
if you are using totem-gstreamer use totem-xine instead.

---

### Post by iheartubuntu on 2008-04-23
VLC or Mplayer.

---

### Post by betes on 2008-04-23
I have a gazv5 and a similar problem.  If I put a dvd into the drive it will automatically open it and play it in totem.  But if I close that window and try to open the dvd with totem I get an error saying i don't have the appropriate plugins. (if i try to open it with mplayer or vlc they both just crash with no error message). I also already have libdvdcss installed. The strange thing is dvds were playing fine for a long time and only a couple of months ago quit working, but  can't figure out why.

---

### Post by iheartubuntu on 2008-04-23
Well I did install Automatix. I wonder if thats the prob. We never tested a movie DVD beforehand.

---

### Post by iheartubuntu on 2008-04-26
I am not longer getting DVD playback errors after setting the DVD region code using "regionset" in the terminal (you'll also have to install regionset before running it).

---

### Post by kevin11951 on 2008-04-26
the problem is 64bit doesnt have a good (or working) libdvdcss2. 

Go to the medibuntu wiki's page (google search).

add the repo, and update your libdvdcss2 (or install it) done!

Detailed How To Coming Soon!

---

### Post by thomasaaron on 2008-04-29
sudo apt-get install libdvdcss2 w64codecs

Also, be careful with regionset. There may be a limit to how many times you can change it before it sticks.

---

### Post by catalyst294 on 2008-06-18
I'm having the same problem with my serval performance (serp4). I've gone through all the mediubuntu stuff, installed libdvdcss2 and w64codecs. I'm running totem-xine and get this error message when I try to play a dvd:

"The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

Since this is a 64-bit problem, I'm assuming, unless someone tells me otherwise, should I expect a solution anytime soon? or will I never get to watch "Reign Over Me" on my laptop? :tongue:

Thanks for any help I can get,

Ryan

---

### Post by kevin11951 on 2008-06-19
JUST INSTALL THIS: [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2_amd64.deb) !!!

---

### Post by catalyst294 on 2008-06-19
It's already installed. That's my problem. I've installed and reinstalled and reinstalled everything this forum and about a dozen others told me to and still nothing. Any other ideas?


Ryan

---

### Post by thomasaaron on 2008-06-19
If you have Automatix installed, that could well be playing into the problem. Historically, we've seen a number of codec related problems with automatix.

I'd try uninstalling it, and then trying Kevin's link above. Or this one (be sure to read the note on 64-bit...)...

[http://www.dailygyan.com/2008/04/how-to-have-dvd-playback-adobe-flash.html](http://www.dailygyan.com/2008/04/how-to-have-dvd-playback-adobe-flash.html)

---

### Post by catalyst294 on 2008-06-19
Ok so I uninstalled the version of libdvdcss2 I originally had and installed the package kevin suggested. I tried to play a dvd and I got the same error. So then I followed the howto. It updated libdvdcss2 back to the one I originally had (from medibuntu repository) and I still get the error. Any other suggestions?


btw I have the medibuntu repository, libdvdcss2, w64codecs. Basically everything I'm suppose to need to play dvds. But I can't. oh and I don't have automatix either.

---

### Post by thomasaaron on 2008-06-19
OK, Here is how I just got perfect DVD playback. This is on a fresh install of Hardy 64-bit, on a GazV5. Run these commands from a terminal.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/ap/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install vlc libdvdcss2 ubuntu-restricted-extras w64codecs

```
```
sudo apt-get install totem-xine

```
```
sudo update-alternatives --config totem

```
**choose 2**

---

### Post by buster8079 on 2008-06-20
> **shirteesdotnet said:**
> I am not longer getting DVD playback errors after setting the DVD region code using "regionset" in the terminal (you'll also have to install regionset before running it).

solution noted here, I had the same problem with a system 76 machine: [http://ubuntuforums.org/showthread.php?t=812570](http://ubuntuforums.org/showthread.php?t=812570) and more detail here: [http://ubuntuforums.org/showpost.php?p=5067999&postcount=363](http://ubuntuforums.org/showpost.php?p=5067999&postcount=363)

> **thomasaaron said:**
> sudo apt-get install libdvdcss2 w64codecs

Also, be careful with regionset. There may be a limit to how many times you can change it before it sticks.

The limit is 5 changes, see: [http://linvdr.org/projects/regionset/](http://linvdr.org/projects/regionset/)

---

### Post by catalyst294 on 2008-06-20
I've already done this, but I did it again. libdvdcss2, w64codecs, totem-xine, and ubuntu-restricted-extras are all the newest version. Also totem is configured to use xine instead of gstreamer. Do you think I should just reinstall ubuntu and see if this will work that way?

Ryan

---

### Post by thomasaaron on 2008-06-20
That might be quicker than trying to figure out where the problem is. But if you want to keep working on it, I can help you.

My approach (above) was on a fresh install of 64-bit Hardy. Worked like a charm.

---

### Post by catalyst294 on 2008-06-20
I think I might try to reinstall since I just got this computer a few weeks ago it won't take me long to get all the programs I need up and running again. One question though, the cd that came with the laptop, will that install the system76 drivers app that shows up in the administration section?

---

### Post by thomasaaron on 2008-06-23
These instructions should cover it all, including the System76 driver.

Install Instructions:

1. Back up important files.

2. Boot from your installation CD and click the "Install" icon. (Make you sure you are loading 64-bit onto your machine.)

3. Choose "Use Entire Disk" when you get to that step of the install, and I recommend caution in keeping configuration files in your current home directory. Occasionally, they will conflict with the new install, particularly if you are upgrading from one version to another.


5. Update your install FROM THE COMMAND LINE. Updating with Update Manager has been linked in our shop tests to a failure to load the proper gstreamer packages. Here are the commands:
sudo apt-get update
sudo apt-get --assume-yes dist-upgrade
sudo reboot

6. Download and install the system 76 driver with these commands:
wget [http://planet76.com/repositories/system76-driver-2.2.2.deb](http://planet76.com/repositories/system76-driver-2.2.2.deb)
sudo dpkg -i system76-driver-2.2.2.deb

7. Go to System > Administration > System 76 Driver
Run the Restore function of the driver

8. Reboot the computer

Now you should have a perfect install.

---

### Post by catalyst294 on 2008-06-23
Ok so I reinstalled and I still have the same problem. i decided to try running a dvd with totem through the terminal to get some more information and I got this output:


> ** 

ryan@ryan-laptop:~$ totem /media/cdrom0
(totem:21363): DEBUG: Init of Python module
** (totem:21363): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:21363): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:21363): DEBUG: Creating Python plugin instance
libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/ryan/.dvdnav/.map'

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1526 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: vm: ifoRead_VOBU_ADMAP vgmi failed
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000320
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000320)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00003460
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00003460)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00007720
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00007720)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001c7440
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x001c7440)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001c7460
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x001c7460)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001e6360
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x001e6360)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001e6380
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x001e6380)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001f1220
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x001f1220)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001f1240
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x001f1240)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003b16a0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_0.VOB (0x003b16a0)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003b16c0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x003b16c0)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003b1800
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_0.VOB (0x003b1800)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003b1820
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x003b1820)!!
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003c25c0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_0.VOB (0x003c25c0)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003c25e0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x003c25e0)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003cbe20
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_0.VOB (0x003cbe20)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003cbe40
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x003cbe40)!!
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003d7400
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_0.VOB (0x003d7400)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003d7420
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_1.VOB (0x003d7420)!!
libdvdread: Elapsed time 1
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 20
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/ryan/.dvdnav/.map'

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1526 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000320
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000320)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00003460
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00003460)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00007720
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00007720)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001c7440
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x001c7440)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001c7460
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x001c7460)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001e6360
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x001e6360)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001e6380
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x001e6380)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001f1220
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x001f1220)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001f1240
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x001f1240)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003b16a0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_0.VOB (0x003b16a0)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003b16c0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x003b16c0)!!
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003b1800
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_0.VOB (0x003b1800)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003b1820
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x003b1820)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003c25c0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_0.VOB (0x003c25c0)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003c25e0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x003c25e0)!!
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003cbe20
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_0.VOB (0x003cbe20)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003cbe40
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x003cbe40)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003d7400
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_0.VOB (0x003d7400)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003d7420
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_1.VOB (0x003d7420)!!
libdvdread: Elapsed time 2
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 21
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.



I dunno if that will help anyone help me. It doesn't make sense since I've followed the steps thomasaaron told me to.

---

### Post by thomasaaron on 2008-06-24
Looks like whatever you're trying to play is encrypted or has a region code that libdvdcss can't understand.

> Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000320)

It may be because the region setting of your drive is different from the region the disk was manufactured in.

> DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

Here are the region codes...

>   1  North America (USA and Canada)
  2  Europe, Middle East, South Africa and Japan
  3  Southeast Asia, Taiwan, Korea
  4  Latin America, Australia, New Zealand
  5  Former Soviet Union (Russia, Ukraine, etc.), rest of Africa, India
  6  China

Your disk is from region 1 (and your dvd drive should be set to that).

To set it to region one...

sudo apt-get install regionset

Then insert the disk and run: ```
regionset
```

You will want to select '1' as the region.

---

### Post by catalyst294 on 2008-06-25
Ok I installed and ran regionset with this output
> ryan@ryan-laptop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:1
New mask: 0xFFFFFFFE, correct? [y/n]:y
Region code set successfully!


Is it suppose to have "mask=)xFF" or "0xFFFFFFFE" instead of numbers for for region code?

But then I tried the dvd again and got a little different error message, with the same result
> ryan@ryan-laptop:~$ totem /media/cdrom0
** (totem:14946): DEBUG: Init of Python module
** (totem:14946): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:14946): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:14946): DEBUG: Creating Python plugin instance
libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/ryan/.dvdnav/.map'
libdvdnav: vm: ifoRead_VOBU_ADMAP vgmi failed
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000320
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00003460
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00007720
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001c7440
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001c7460
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001e6360
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001e6380
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001f1220
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001f1240
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003b16a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003b16c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003b1800
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003b1820
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003c25c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003c25e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003cbe20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003cbe40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003d7400
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003d7420
libdvdread: Elapsed time 0
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 5
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/ryan/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000320
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00003460
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00007720
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001c7440
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001c7460
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001e6360
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001e6380
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001f1220
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001f1240
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003b16a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003b16c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003b1800
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003b1820
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003c25c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003c25e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003cbe20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003cbe40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003d7400
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003d7420
libdvdread: Elapsed time 0
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 0
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
** (totem:14946): DEBUG: Finalizing Python plugin instance



> libdvdnav: Unable to find map file '/home/ryan/.dvdnav/.map'

I looked for this file and the ".dvdnav" directory does not exist, could that be my problem?

---

### Post by thomasaaron on 2008-06-25
> Can't read name block. Probably not a DVD-ROM device.

Are you using a standard dvd? Can you try another dvd in the machine? Something from RedBox perhaps.

> I looked for this file and the ".dvdnav" directory does not exist, could that be my problem? 

I don't have that file on mine either.

If you are using a standard, American DVD, something is pretty badly hosed here. It could be some left-over configuration issue left by previous attempts to fix this.

---

### Post by catalyst294 on 2008-06-25
Ok so I tried every other dvd I could find in my house, like 6, and they all worked perfectly. So I wondered what was wrong with the dvd I tried a few minutes ago, right after I had setup the region code. SO I stuck that dvd in again and it played, no problem. I think we've solved it thank you SO much, you've been a life saver!

---

### Post by thomasaaron on 2008-06-25
> you've been a life saver! 

Ha! Even a blind hog can find an acorn every once in a while! :lolflag:

---

### Post by ackey on 2008-06-27
I think I've seen a similar issue - it was a Doctor Who classic series dvd.  I believe the region was right since the tv-based dvd player had no problems with it, but two linux laptops (both daru2's, different dvd configurations...) kept getting "encrypted dvd" messages and failures.  We wrote it off at the time, but perhaps there is a class of dvd's that the linux libraries can't read

---

