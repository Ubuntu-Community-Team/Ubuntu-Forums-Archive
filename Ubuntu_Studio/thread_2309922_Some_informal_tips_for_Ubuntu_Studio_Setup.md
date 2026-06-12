---
title: "Some informal tips for Ubuntu Studio Setup"
date: 2016-01-14
forum: Ubuntu Studio
---

### Post by yoshii on 2016-01-14
These are the DAW optimizations that I implemented for my 32-bit Ubuntu Studio v14.04.3 LTS installed in December 2015.  
I also implemented this in a newer installation of 32-bit Ubuntu Studio v16.04 LTS installed in 2016.  

Most of these optimizations were learned from [http://wiki.linuxaudio.org/wiki/system_configuration](http://wiki.linuxaudio.org/wiki/system_configuration)
However, as that site is becoming dated, and as I avoid compiling at all costs, I didn't implement everything listed there.  
Also, Ubuntu and PulseAudio are in the process of improving, so I don't feel all those tweaks will be necessary.  
Lastly, one of the tweaks listed there disabled my desktop's trash can so of course I no longer implement that one. 

I created this page to help bring up to date the available guides on how to install and use Ubuntu Studio Linux. 
When I first started using Ubuntu Studio, I had to do a bit of reading and searching for answers.  
Discretion was needed to filter out the old information from the new information.  I have experience doing this, 
so it wasn't as hard for me as it might be for others.  And so I wanted  to hopefully make this process easier for others in the future. 

It's important to understand that I primarily use Windows 32-bit Reaper v5.x (in WASAPI mode) as my main DAW program,
and use Windows 32-bit EnergyXT v3 beta as my secondary DAW program. 
I am not against using Linux DAWs, but I don't use them much YET.  I still use Windows VST instruments and effects. 
For reasons beyond the scope of this document, I don't YET use JACK Audio Connection Kit. 

I primarily use my DAW programs for composing MIDI music and rendering the outputs of VST instruments to WAV files. 
I primarily work at 48 kHz 32-bit float and render to 16-bit 48 kHz FLAC after archiving the 32-bit float versions. 
This information is meant as a guideline for anyone setting up a similar modest yet powerful DAW. 

This document is not an authoritative expert reference.  It includes my  preferences based upon intermediate experiences and readings. 
Most of my experience with computers is with Windows computers although I  am now retired from the Windows Operating systems fiasco. 
This document is an abbreviation of all the steps taken to get my system running as wanted, but it's also a documentation of the
main DAW-oriented changes made to my system.  Most other changes made  were cosmetic or part of the basics that every user learns. 
This guide doesn't explain everything in great detail.  So you will still need to consult others for help if needed. 

OK, so here we go...

Prepare your BIOS for use with Linux and as a DAW.  The actual  formatting you can do with gParted from within a booted LiveCD of Linux.  
I chose to format as MBR for simplicity and backwards compatibility.   MBR formatting sets the maximum number of partitions to four (4). 
MBR stands for Master Boot Record, and is an alternative to GPT, which allows for more than four partitions. 
Modern day Windows systems require GPT, but the other Windows systems were OK with MBR. 

I don't use Windows any more, but occasionally I use Puppy Linux, which  still often involves MBR-oriented boot loaders, boot menus, and support.  

You need to know this if you have future plans for other partitions or operating systems.  Personally, I am OK with this. 
Another limitation of MBR formatting is that the there can be no partitions larger than 2 Terabytes. 
Using MBR mode requires setting the BIOS for "legacy" MBR / BIOS compatibility instead of UEFI boot mode. 
Disable any unneeded features or hardwares.  Set all BIOS preferences to settings sensible for DAW and not server use. 

Installed with internet OFF to avoid a potential installation bug for Ubuntu Studio v14.014.3 LTS
Installed internet updates AFTER configuring some system preferences and rebooting. 

All peripheral hardware was connected BEFORE the install so that the installation would detect these devices. 
This includes my USB MIDI keyboard, and my USB audio interface/powered monitors.  Both are USB Class Compliant. 
USB Class Compliant means that drivers don't need to be manually installed on any OS. 
The devices naturally comply with the USB standards of operation, so are recognized automatically. 

You will need to enable DVD and MP3 playback manually after you have your system set up. 

4 GB SWAP primary partition, and an ext3 System primary partition created using gParted. 
Ubuntu Studio v14.04.3 was installed into the ext3 System partition. 
Ext3 is a good combination of forward and backwards compatibility with stable journaling. 
Yet, ext4 has some performance and data integrity stability advantages over ext3 and ext2.  
Nicely, ext4 is backwards compatible.  

Some unneeded services were disabled with override files: 
```

/etc/init/avahi-cups-reload.override
/etc/init/apport.override
/etc/init/samba-ad-dc.override
/etc/init/reload-smbd.override
/etc/init/winbind.override
/etc/init/nmbd.override
/etc/init/cups.override
/etc/init/bluetooth.override
/etc/init/smbd.override
/etc/init/cups-browsed.override

```
Each file contains one line with the word "manual". 
These overrides include BlueTooth and printing and Samba amongst other things. 
If you need the function, don't create the .override file. 

Apport was overridden because sometimes it is very fussy with errors and crashes even while reporting minor errors. 
This can give the false impression of an instable system. 

CPU scaling was set to Performance and attempts were made to disable all screensaving functions:  ( from [http://wiki.linuxaudio.org/wiki/system_configuration](http://wiki.linuxaudio.org/wiki/system_configuration) )

CPU frequency scaling

If your CPU supports frequency scaling and the CPU frequency scaling  governor is set to ondemand (which is the default on a lot of distros)  you could run into xruns. The ondemand governor scales the frequency  according to the CPU load, the more the load, the higher the frequency.  But this is happening independently from the DSP load on your system so  it could happen that the DSP load suddenly rises for instance, demanding  more CPU power, and that the scaling daemon kicks in too late,  resulting in xruns because the DSP load maxes out. A solution would be  to use a CPU frequency scaling daemon that scales the frequency  according to the DSP load on your system like jackfreqd or to simply  disable CPU frequency scaling altogether. The latter can be achieved by  setting the scaling governor to performance.

To check which governor is active:
```

cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

```
Setting the governor to performance:
```

echo -n performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

```
You could also add a line to your /etc/rc.local file for instance to set the governor to performance at boot time:
```

echo -n performance > /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

```
Ubuntu

On Ubuntu systems the command in your /etc/rc.local file only works if you disable the ondemand service:
```

sudo update-rc.d ondemand disable

```

/etc/fstab was edited to include "noatime" to disable file access logging to speed up disk actions: 
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>            <mount point>          <type>  <options>                 <dump>  <pass>
UUID=[System partition UUID here] /               ext3    noatime,errors=remount-ro 0       1
UUID=[SWAP partition UUID here] none              swap    sw                        0       0

```
Edited part of /etc/pulse/daemon.conf for better latency: 
```

default-fragments = 4
default-fragment-size-msec = 2

```
Edited part of /etc/pulse/default.pa for better latency:  (add " tsched=0")
```

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect tsched=0
.else
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect
.endif

```
Wine was upgraded to the development version, and a new menu shortcut  was manually created for winecfg ( located within /opt/wine-devel/bin/  ). 
Wine Configuration (winecfg) was run and PulseAudio was set as the audio driver in all instances. 
Windows 7 mode was selected in winecfg for optimal backwards and forwards compatibility and stability. 

Windows Freeware Rapid Environment Editor was downloaded and run to set  the Windows Temporary directories for both system and user to "Z:\tmp"

Windows Core Fonts and other common and preferred Windows fonts were installed into the c:\Windows\Fonts folder. 
 
A certain humongous pack of Linux free fonts was removed using the Software Center. 

Other tools to have available to make things easier: 

QupZilla web browser (for those times when FireFox won't run due to temporary upgrade bugs). 

Essential FireFox addons:  CHMfox; Mozilla Archive Format (MAFF) or UnMHT, whichever functions in FireFox for you. 
CHMfox allows for easy reading of .CHM help files from within FireFox. If it doesn't work, just use the default Wine settings of HH.exe or whatever the default Windows WinHLP32.exe is.  
MAFF allows entire web pages to be saved as a single .MHT archive which  is still readable on nearly all Windows computers as well. 
This makes archiving internet help pages much easier. 


K3b (Disc Authoring tool, for creating and burning .ISO images)
Foobar2000 (v1.3.9 or greater, for audio file conversions and meta data tag editing)
OcenAudio (v3.0.4 Linux Mint or greater, for audio file editing and conversions)
DeaDBeef (v0.6.2 Portable or greater, for audio file jukebox-style playing)
UbuntuTweak (v087-1_trusty2_all or greater, for ONLY carefully assigning filetypes to programs)
IrfanView (v4.4.1 or greater, with plugins, for viewing and minor editing of images)
XnView Multi Platform (v0.76.1 or greater, for viewing and minor editing of images)
VLC Media Player (v2.1.6 or greater, for viewing videos and DVD's)
BleachBit (v1.8 or greater, for removing junk files and unneeded history; use with caution!)

After the system was upgraded and no other updates were found, the system was taken OFFLINE to preserve the stability. 
Backups were kept available of manually-installable .DEB, .7z, and .ZIP archives; and of various instructions and manuals. 

Caveats: 

In order to edit system files, you will need to "sudo gedit" or "sudo leafpad" or "sudo geany" your files. 
Be sure to have disabled spelling and grammar checking when editing system or configuration files. 
Also, do not use Windows programs for editing Linux system files or vice-versa.  
The text formatting is slightly different between operating systems and you may risk minor data corruption. 

I did install 32-bit Windows FL Studio v12.1.3 Registered Fruity Edition. 
Before you install FL Studio, historically it has been necessary to install what is known as the Microsoft Core Fonts.  
These are the system fonts that Windows Operating System uses.  These  can still be found, yet with some difficulty, on the internet.  
If you can't find them, and you own Windows, you can actually copy the  .TTF font files from C:\Windows\Fonts into the equivalent directory on  Linux.  
It won't literally be "C:\Windows\Fonts"  It will be to "/home/username/.wine/drive_c/windows/Fonts/".  
Without the MS Core Fonts, FL Studio's menu and window texts might be blank and therefore unusable.  

Although the FL Studio step editor works excellently, I was not able to  achieve the kind of CPU performance that I had hoped for. 
It seems as if the multicore functions of the computer are not recognized by FL Studio. 
Contact with Image-Line gave me the impression that Image-Line chooses  to ignore Linux support for now out of a kind of all or nothing  perfectionism. 
They explicitly told me they will not support Linux via wine even though the system nearly works.  

In my personal experiences, I was not able to attain stability using WineASIO and JACK within Reaper. 
Eventually, I gave up and focused on achieving good enough results  within PulseAudio which is now a standard Linux install element. 
This was disappointing because JACK is known for it's lower-latency abilities. 

Linux hardware support is not 100%, so you may need to seek out pro audio hardware that is either USB Class Compliant,
or already has modern Linux drivers available.  Anything else, probably  will fail to work at all or will have limited functionality at best. 

Last but not least, be aware that while Wine is a constantly-improving interoperability system,
it is not without some issues depending ultimately upon each Windows program's design. 
Also, be aware that it does not emulate the Windows Explorer desktop and contextual menus. 
It is mainly a way of launching Windows programs within Linux with  bidirectional compatibility with the Linux environment at best. 

It is my understanding that PulseAudio and Wine are only recently joining forces in terms of strong development,
and while this is entirely welcome and should be respected, it means that PulseAudio support in Wine is still young. 
We have good things to look forward to with both of them.

Here are some important screenshots to help you with the optimizing...
(Click an image to enlarge it in a new window)

[[IMG]https://s31.postimg.org/u4eo68e6f/etc_default_pa.png[/IMG]]("https://postimg.org/image/u4eo68e6f/")
editing of pulse audio settings
[[IMG]https://s31.postimg.org/md2jlezev/etc_fstab_noatime.png[/IMG]]("https://postimg.org/image/md2jlezev/")
disabling file access logging for ext
[[IMG]https://s31.postimg.org/woewe2r47/etc_pulse_daemon_conf.png[/IMG]]("https://postimg.org/image/woewe2r47/")
more pulse audio settings
[[IMG]https://s31.postimg.org/401yauoxz/Pulse_Audio_Volume_Control.png[/IMG]]("https://postimg.org/image/401yauoxz/")
editing of hardware settings in pulse audio
[[IMG]https://s31.postimg.org/l1uscy3t3/QAS_Mixer.png[/IMG]]("https://postimg.org/image/l1uscy3t3/")
inportant QasMixer settings for hardware
[[IMG]https://s31.postimg.org/bil3jhgav/Rapid_Environment_Editor.png[/IMG]]("https://postimg.org/image/bil3jhgav/")
setting the TEMP and TMP directories for Wine
[[IMG]https://s31.postimg.org/r7w8joxqf/Wine_Configuration.png[/IMG]]("https://postimg.org/image/r7w8joxqf/")
pulse audio Wine settings

---

### Post by yoshii on 2016-02-20
I made a downloadable archive of my current (Feb 2016) working DAW settings for Reaper, FL Studio, and EnergyXT, but with a focus on Reaper.  The document displayed above is included as a text file also.  You will need a 7-zip decompressor such as 7-zip or PeaZip to decompress the archive.  
Included are annotated screen shots of currently working settings.  
I can't seem to find a decent file hosting site anymore but if you need the archive, send me a PM with your email address and I can try to email it to you.

---

### Post by MartyBuntu on 2016-02-20
> **yoshi2 said:**
> T
Another limitation of MBR formatting is that the there can be no partitions larger than 2 Terabytes. 


You sure about that?

I have multiple 3TB drives formatted as ext3 and ext4 (as GPT) in machines with all UEFI options disabled...

---

### Post by yoshii on 2016-02-22
> **MartyBuntu said:**
> You sure about that?

I have multiple 3TB drives formatted as ext3 and ext4 (as GPT) in machines with all UEFI options disabled...

Sorry for the confusion.  

As I understand it, MBR formatting of drives is the older format VS GPT formatting which is newer.  
[b]GPT does allow for greater than 2 terabytes, but MBR (and the implied MS-DOS partition table) doesn't.  
GPT is the alternative to the Master Boot Record (usually an MS-DOS partition table) and GPT allows for more than 4 primary partitions.  
You can't have GPT and MBR at the same time on the same drive.  [/b]

How each machine's firmware (BIOS/legacy mode and/or UEFI startup) handles the situation varies somewhat from manufacturer to manufacturer.  

I don't know as much about UEFI but my understanding is that UEFI requires GPT to boot, but I could be wrong about that.  
Probably your computer's firmware is user-friendly enough to allow you to boot.  

I'm not an expert on these things and I know that there are more details than this about GPT and partition tables and UEFI and the BIOS.  
If you want to find out for sure what works on your system... if you have a spare blank hard drive and a Live CD to install, you could experiment with different formats using gParted and play around with different BIOS/legacy or GPT/UEFI settings and see which ones can boot.  

But it does vary just a little bit between manufacturers and can vary even between different BIOS versions of some manufacturers.

---

### Post by yoshii on 2016-02-22
I just took a quick glance at the Wikipedia entry for GPT and it's rather thorough and mentions with good details the history and purpose and compatibility of GPT/UEFI.  
[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)

I think the main answers are here:  

[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#UEFI_booting](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#UEFI_booting)
[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#CSM_booting](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#CSM_booting)

and added for completeness:  [https://en.wikipedia.org/wiki/Master_boot_record](https://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by yoshii on 2016-03-12
I just updated the first entry in this thread to let you know that you will need the Microsoft Windows Core Fonts installed before you attempt to install FL Studio.  
There is more to know about how to install FL Studio, such as that you need to import your valid registry key first (and how to do that).  
I will add that information later on.

---

### Post by kazakore on 2016-06-12
Some interesting and useful notes. I really should keep a better track of the changes I make each time as every time I do a new install or try something different I have to go and learn it all again and start reasearching again from scratch. I guess that way I might pick up different little bits of information each time which may sink in though...

Anyway I'm mainly replying for something a little off-topic from one of your later comments not related to the audio side.


> **yoshi2 said:**
> 

MAFF allows entire web pages to be saved as a single .MHT archive which is still readable on nearly all Windows computers as well. 
This makes archiving internet help pages much easier. 




Why not use the Firefox (and assumedly other browser's) Print To File option and save the pages as .pdf files that way? Almost everything can open pdf these days and it's there already by default. ;)

---

### Post by yoshii on 2016-06-13
> **kazakore said:**
> 
Why not use the Firefox (and assumedly other browser's) Print To File option and save the pages as .pdf files that way? Almost everything can open pdf these days and it's there already by default. 

I prefer the MHT format instead of PDF because it renders to the browser window EXACTLY as it did before it was saved.  With PDF you have to adjust the display format.  Also, the MHT format preserves the HTML links and not all PDF viewers do.  Also, the MHT files can be loaded into an XML text editor and if you are careful, you can edit the text to fix grammar and spelling errors.  PDF files usually can't be edited after they are created; I think it's related to their compression.  Also, Microsoft Windows of every version can open MHT files without needing to download any other programs.  Also, I don't like how bloated the Adobe PDF reader is and so I moved away from it a long time ago.  MHT files can store animated GIF's too.  And the MAFF format can store videos and sound.  I don't think PDF's can do that at all.  In the past, when I did use some PDF printing functions, it cropped my data and spoiled it.  The MHT format doesn't do that.  Also, some PDF programs convert PNG's into JPEG's which reduces their quality.  Last but not least, I don't own a printer, so I haven't looked at the Print menu in years.  So thanks for letting me know there is a PDF function there.

---

### Post by kazakore on 2016-06-13
All perfectly good reasons. Didn't know any of that, sounds like a pretty powerful format :)

To be fair I most often save webpages as proof of payment and similar (especially when it comes to the likes of MASWings airline who actually don't send you a email confirmation at all, it can prove quite useful then!) so editing, formatting or extensive media support isn't so important to me, as long as I can read it and put it on a usb key or email to be printed in an internet cafe. For this Print To File > .pdf is perfectly suited :)

---

### Post by CrocoDuck on 2016-06-14
> **yoshii said:**
> I prefer the MHT format instead of PDF because it renders to the browser window EXACTLY as it did before it was saved.  With PDF you have to adjust the display format.  Also, the MHT format preserves the HTML links and not all PDF viewers do.  Also, the MHT files can be loaded into an XML text editor and if you are careful, you can edit the text to fix grammar and spelling errors.  PDF files usually can't be edited after they are created; I think it's related to their compression.  Also, Microsoft Windows of every version can open MHT files without needing to download any other programs.  Also, I don't like how bloated the Adobe PDF reader is and so I moved away from it a long time ago.  MHT files can store animated GIF's too.  And the MAFF format can store videos and sound.  I don't think PDF's can do that at all.  In the past, when I did use some PDF printing functions, it cropped my data and spoiled it.  The MHT format doesn't do that.  Also, some PDF programs convert PNG's into JPEG's which reduces their quality.  Last but not least, I don't own a printer, so I haven't looked at the Print menu in years.  So thanks for letting me know there is a PDF function there.

Actually PDF can do most of this, but it is much harder to achieve. It actually makes sense only when you have to embed multimedia in a document you are preparing from scratch. Exporting a webpage in a not-web format to preserve its interactivity and links seems not a very sensible idea to me.

---

### Post by yoshii on 2016-06-14
CrocoDuck, it works fine for me (MHT) because I save the files on flash drive, then open them up at home on my offline computer so I can read webpages I didn't have time to read to completion.  They look nearly exactly as they did on the online system.  Also, it's preferable for me when I use a library computer that doesn't offer print to PDF options but does allow webpages to be saved as MHT.  And of course, you can still print from MHT to file or printer if you have that capability.  And the images are embedded so you can extract those too if those are what you need.  I do save PDF files from downloads too, and they do often look cleaner than a webpage which might have ads, but I use ad-blocking software and I like having a realistic snapshot of what the webpage looked like.  The filesizes aren't a problem either.

---

### Post by yoshii on 2016-06-15
UPDATE:  I added some important screenshots to the informal guide on the first page of this thread.  
Click on the thumbnail images to enlarge them.

---

### Post by CrocoDuck on 2016-06-16
Yeah yeah, saving webpages with web formats (like MHT) makes a whole more much sense. I was just pointing out that PDF is not as limited as it was emerging from your post, although intended for other tasks first.

Cool pictures. I think it would be cool to also have the code lines enclosed like this:

```

ls -la

```

it would make the post easier to read. Give it a go if you fancy the idea.

Cheers.

---

### Post by yoshii on 2016-06-21
CrocoDuck, thanks for the reply.  I didn't mean to sound so critical of PDF.  Thanks for the discussion.  
Also thanks for suggestion to use "```
lsb_release -a && uname -a
```".  That was a good idea.  

I just hope that this stuff helps people.  
I wasn't able to run Reaper without buffer errors until I implemented these things.  (mainly the pulseaudio edits--includeing tsched=0, cpu performance, disabled services, and noatime)

---

### Post by kazakore on 2016-06-22
So what do you suggest for opening .mht files in Ubuntu? I just found one in my eBook collection and it has no associated program, searching Synaptic for mht brings up surprisingly few results none of which I have installed or look like readers and it doesn't display as a webpage when opened by Firefox.

EDIT: Obviously with the plugin you mention in your first post. But it does show that it clearly doesn't have anywhere near the support that pdf does if you need to install Add-Ons to view it.

EDIT2: Actually MAFF didn't work for viewing! It just constantly put me in a loop of asking what I wanted to do with the file (Open With/Save To...). I had to install UnMHT to be able to actually view them although MAFF claims View and Save in its blurb.

---

### Post by yoshii on 2016-06-29
Sorry for the confusion.  
I don't use the MAFF function of the MAFF plugin.  The MAFF plugin comes with MHTML (MHT) support for open and save.  I use that because I ran into problems with UnMHT.  
I admit it's not ideal using a plugin instead of Linux native tools, but that's what I'm used to.  MHT was invented by Microsoft.  That's what the M stands for in MHTML.  

MAFF is made by Mozilla.  You have to install the MAFF .XPI file from the [https://addons.mozilla.org](https://addons.mozilla.org) official website using FireFox.

---

### Post by yoshii on 2016-07-31
EDIT:  september 2016

I was mistaken in believing that ext4 was any better than ext3.  
From my standpoint, there are plenty of reasons to work with ext3 or whichever else filesystem you prefer for your own reasons.

---

### Post by CrocoDuck on 2016-08-02
Have a look at the [Arch Wiki]("https://wiki.archlinux.org/index.php/File_systems"). There is plenty of good info and links.

---

### Post by yoshii on 2016-08-02
Hey thanks so much, CrocoDuck.  i will look at that.  
i was able to successfully convert my Xubuntu laptop without even doing a backup.  
But I am always willing to learn more info on these topics.

---

### Post by yoshii on 2016-08-10
Ext4 may not be any more stable than ext3, depending upon how and when (version numbers of all related components) it's implemented on your system.  

Note:  The threadirqs tweak should probably help a system regardless of being ext3 or ext4 based.  

I recently sidegraded to ext4 and it introduced some instability into the systems I tried it with and it's error messages indicated that it wasn't living up to expectations.  

Nevertheless, here are some performance and stability tweaks for ext4 filesystem users on Linux:

[[IMG]http://s9.postimg.org/xx9xzp8jv/fstab.png[/IMG]]("http://postimg.org/image/xx9xzp8jv/")

(click to enlarge image)

[[IMG]http://s9.postimg.org/d1nnogccr/grub.png[/IMG]]("http://postimg.org/image/d1nnogccr/")

(click to enlarge image)

---

### Post by CrocoDuck on 2016-08-11
> **yoshii said:**
>   
i was able to successfully convert my Xubuntu laptop without even doing a backup.  


What that means? Did you change the filesystem of a running partition? Then I am surprised, I did not know it was even possible. It does not really strike me as a wise thing to do tho: once you format a partition and install an OS on it you should stick to it or format and re-install from scratch: I think that otherwise your system will become at least unstable, if not really giving you death messages eventually. Which brings me to:


> **yoshii said:**
> 
I recently sidegraded to ext4 and it introduced some instability into  the systems I tried it with and it's error messages indicated that it  wasn't living up to expectations.  


ext4 is rock stable. I would imagine that the instability spawns from what you did to "convert" the filesystem. Finally:


> **yoshii said:**
> 
I am currently undecided about whether or not ext4 is indeed superiour to ext4 for DAW use. 


You would need to run two OS prepared in the same way on two different partitions of the same computer to make a fair comparison. Even then, I don't think that you will never see any noticeable difference. Although the way you access hard drives pays sometimes a central role for audio performances (see booting with noatime parameter) audio involves CPU and RAM first. I think that setting up good drive IO just helps the OS performing tasks smoothly rather than audio itself and appears to me that IO is more important than filesystem. I don't think that shifting between ext3 and ext4 actually makes much of a difference for audio, especially given that they are pretty similar in a way. Actually the choice of the filesystem should be made upon kernel support. For example, I avoid Btrfs as it is known to [give issues with RT kernels]("https://wiki.archlinux.org/index.php/Btrfs#Linux-rt_kernel").

[This]("https://linuxmusicians.com/viewtopic.php?f=27&t=15378") might be interesting for you.

---

### Post by yoshii on 2016-08-12
@CrockoDuck,

Converting Ext3 to Ext4 can be done to a filesystem that is not currently mounted.  I used another Linux LiveCD to do this.  This is not unusual.  I followed the instructions from the Ext4 website as well as the Instructions here at Ubuntu.  They both say pretty much the same things, except that the Ext4 website has a kernel parameter tip in case the kernel doesn't know to boot using ext4.  I didn't try to convert a live mounted filesystem.  That would be bad, of course.  

I think the problems I have had turned out to be from gParted Live which is what I used for the formatting.  It turns out that the current version of gParted has a newer version of filesystem tools e2fsprogs or whatever it's called.  Their version is so new that some other distros arent using it yet.  This kind of upsets me that there wasn't a clear warning of this.  I downloaded the version labeled "stable", but as it turns out from some careful reading, all of their versions are based upon Debian UnStable(?) I think, either that or it's Debian Testing.  But it's definately NOT Debian Stable.  

The main error I get is that it's trying to do an fsck on boot, and it fails due to operational error even though there are no filesystem errors.  An operational error is different from a filesystem error.  This is in the man pages of ext4.  Since I have my boot messages turned on without the splashscreen, I'm able to see this.  Today I noticed a message that "fsck needs to be updated to a newer version" type of thing.  Also it's mentioning stuff about checksum features too.  I don't really want to get into it until after I fix all this.  

I'm still able to use my system without crashes or data loss so far, but I am going to change things so I can rest assured there won't be problems.  

You can verify this from the entries at [http://DistroWatch.org](http://DistroWatch.org)

As it turned out, gParted was implementing into the ext4 format features that my system can't completely deal with yet.  I learned that from the operational errors and from looking at the errors from using an older version of gParted that is more common.  

So I am actually now trying to learn how to downgrade ext4 to ext3 since my original ext3 install was stable and gave no errors.  Ext3 doesn't handle large files as well and eventually gets more fragmented, but not as much as Windows probably.  I think if I enable the "barrier" in ext3, it will overcome the main stability limitation described in the documentation.  There's still some performance gains from just having an ext4 driver mouting ext3.  

I agree with you about avoiding btrfs and stuff like that.

---

### Post by CrocoDuck on 2016-08-13
I see. Just to make sure I am understanding properly, did you change the file-system of the root partition or of just a data partition?

Well, if you changed root, that is why I think it is unwise to make such deep transformations of file-systems on which you are going to to run an OS. The fact is that you are changing many things upon which the installed system was previously configured and the chances to get it to work smoothly appear very low to me. Moreover, when you do these sort of things, you should never do it without a backup. There are few things as potentially disruptive as playing with file-systems and it could start haunting you at any point in the future.

About Debian branches, Testing just has a more up to date software base. According to Debian jargon and definitions it cannot be said stable, but Debian standards are so strict that for most users of other distro also Testing appears pretty much stable. A Debian Testing environment is usually more stable of Ubuntu environments. Without getting into details, there are many people that don't like how the software release cycle works on the Testing branch tho.

Good luck with your experiments and trust the old duck: do a backup. Anything should go wrong, you are covered.

---

### Post by yoshii on 2016-08-13
Hey thanks CrocoDuck.  

I was able to get things working mostly normal again.  Details here:  [https://ubuntuforums.org/showthread.php?t=2333752](https://ubuntuforums.org/showthread.php?t=2333752)
It wasn't so simple though you'll notice if you read the whole thread. 

I still get a (hopefully) minor error about journal checksumming not being availble during a remount.  So I will later today remove that parameter from my /etc/fstab and see if that fixes it so that it doesn't have to remount during boot or if it does, it won't have to ignore that parameter and spit an error message.  

I understand what you are saying about the risks of working on filesystems and stuff.  But I followed the directions and even before I fixed most of the issues with a slightly tricky e2fsprogs update, I was still able to boot my system and access all my files.  It's just that I think the journaling would have failed when I needed it after a serious crash.  And that, I agree, like you said, is worrisome.  

I am trying to learn how to do backups.  I tested out a few backup softwares and they failed!  That's so uncool.  So far the only one I trust is Clonezilla but that has some drawbacks.  

Also, it's nearly impossible to convert back to ext3 for an average user like me.  I tried a few things, but I don't want to waste all that time on something risky like that.  
One interesting thing I did discover... forensic computing peoples have ways of mounting ext3 filesystems as ext2 without a journal. Thats pretty cool.  I wish I knew how to do that, because it sometimes might work on ext4 theoretically.

Yeah, turns out gParted is based upon Debian "Sid" (UnStable).  This was in the release notes/changelog.  
As far as I know, even the Ubuntu version of gParted Live is based upon Debian UnStable.  But I have to double-check that.

---

### Post by CrocoDuck on 2016-08-14
> **yoshii said:**
> 
I am trying to learn how to do backups.  I tested out a few backup softwares and they failed!  That's so uncool.  So far the only one I trust is Clonezilla but that has some drawbacks.  


I am an old style duck, so I actually just copy and paste my files to an external drive. I got a 2 TB USB3 Seagate external drive that makes a wonderful job. To be honest, I am an external memory & cloud guy. As such I keep sensible and large files in my external drive and projects under current work in my clouds, so my sensible files are always secure and I can work on my projects regardless of where I am. I don't really like to have many files on my local PC memory: they tend to grow unorganized. And I like my system clean.

I used clonezilla only once. I think it is good if you need to backup entire drives state.

---

### Post by yoshii on 2016-08-16
Thanks CrocoDuck.  I can relate to what you are saying, minus the cloud computing part.

---

### Post by yoshii on 2017-01-29
UPDATE:  

Due to some tragic events in my personal life, I lost my apartment and most of my personal belongings, including my DAW computer and gear.  
Because of this, I won't be able to provide as many in-depth interactive updates until I get another working DAW.  

Fortunately, I have recovered from the event, (I'm not homeless anymore), and I recently acquired another computer to use for internet use.  
But I don't yet have a DAW computer.  :(

Also, my internet access is somewhat limited due to my local public library closing down due to their systemic failures.  
I now will have to go to non-free hotspots which limits my online access times.  

Luckily, however, I was able to retrieve some of my DAW programs via cloud storage.  
**So, you can expect me to continue to try to provide support to Linux DAW users, especially after I acquire my MIDI and related hardwares.**

P.S. - About MAFF vs. UnMHT...  Lately I'm finding MAFF doesn't work, so I recommend UnMHT instead.  Also, UnMHT is reputedly less likely to corrupt an archive.  It is easier to install than MAFF, but UnMHT does require it's settings to be configured carefully, which makes it somewhat harder to use if you don't choose the right settings.

---

### Post by CrocoDuck on 2017-01-30
> **yoshii said:**
> 
Due to some tragic events in my personal life, I lost my apartment and most of my personal belongings, including my DAW computer and gear.  
Because of this, I won't be able to provide as many in-depth interactive updates until I get another working DAW.  


Oh no!!! I hope you can keep on recovering. Glad to see you have an accommodation again. It must be hell. Let us know if we can be of any help.

Best wishes.

---

### Post by yoshii on 2017-02-21
Thanks.  CrocoDuck.  
Thus far, I am in the process of re-downloading some .ISO's and stuff.  
I will probably be eventually running Lubuntu with selected Ubuntu Studio programs and low-latency kernel on top of that.  
Or, if that doesn't work, probably Xubuntu with selected Ubuntu Studio programs and low-lantency kernel on top.  
I find Ubuntu Studio to be a bit bloated even though it's good.

---

### Post by yoshii on 2017-03-03
UPDATE:    Well, after all, I will be running Ubuntu Studio again.  I had some minor difficulties with Lubuntu's compatibility with PulseAudio even though it really is nice for basic use at wifi hotspots, etc.   I suppose I could try Xubuntu with the low-latency kernel... that's worked out OK in the past.  But all in all, at least Ubuntu Studio has all the codecs and main programs I need and want.   Luckily, I recently ordered the same USB Class Compliant audio interface and monitors I used to use before.  So I will be able to pretty much give more updates about DAW use as time goes by.   Next month I will probably get a USB MIDI keyboard.    A lot of Linux things are getting better, so it's a good time to learn.  (Wine is improving, the Linux kernel is improving, more used computers are stronger than in the past, Ubuntu versions have improved too)

---

### Post by yoshii on 2017-07-17
Another quick update:  due to personal tragedy within my life, I lost my DAW computer and hardware and backup discs.  
I do have a replacement computer for now, but it's not ready for Digital Audio Workstation work.  

[B]I will still try to provide support to this forum and related Ubuntu / Linux audio forums for composers seeking to run Windows VST(i)'s via WINE on Linux.  
My original posts here seem to have been the most stable:  32-bit Ubuntu Studio Version 14.04 LTS, using ext3 on a refurbished computer.  

I did successfully have a time at running 64-bit Ubuntu Studio v16.x, yet it wasn't as stable as the version I just mentioned.  As is documented by the WINE HQ, WINE is more stable and complete on 32-bit Linux with 32-bit WINE.  This is what I will most likely revert to in the future.  

I mention this stuff, just so people have a point of reference about which kind of Ubuntu I was using and will likely use again once my life goes back to normal.  
In the meantime, I found this to be a great tip provided by somebody else here at the forums:  [/B][https://ubuntuforums.org/showthread.php?t=2366769](https://ubuntuforums.org/showthread.php?t=2366769)
[B]It's a tip on managing kernel updates more effectively.  It could probably be adjusted  to handle extra kernels between low-latency and generic.  

Good luck to all you guys.  [/B]

Also, if you need to contact me on another forum, my username is "Daggit" at IDMforums.com and my newer music website is [https://hearthis.at/daggit-gr/](https://hearthis.at/daggit-gr/)
If my SoundCloud webpage isn't available, use that as a backup.  I am still known as "Nystagmus" at [http://gearsz.com](http://gearsz.com)

Peace.

---

