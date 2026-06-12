---
title: "Firewire dv camcorder"
date: 2008-05-06
forum: Ubuntu Studio
---

### Post by eevargas on 2008-05-06
I have a JVC camcorder that work perfectly on feisty with kino, it's stop working on gusty. I'm on Hardy now and still not luck. I need to access my movies to burn it on DVD. What is going on with firewire since feisty and how can I resolve it? I don't want go back to windows dual booting!

Please, raw1394 is loaded and I did the "sudo chmod a+rw /dev/raw1394" thing
still no luck!

---

### Post by scott_g on 2008-05-09
Can you try running Kino in a terminal (open a terminal and type: kino)?  This will start Kino, yet will show what it is doing in the terminal.  Can you post what it says in the terminal after you try to capture from you camera?

Oh; and this may be a silly question, but is the camera plugged in? (Don't laugh; I spent 4 hours trying to figure this one out, and the camera was unplugged....)

Scott

---

### Post by eevargas on 2008-05-09
Ja, ja . . . yes is plug it! I will try kino on the command line a let you know. Thanks!

---

### Post by eevargas on 2008-05-09
~$ kino
> help language code en
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
> Kino Common being built
> Creating page editor
> Creating Capture Page
> Creating Export Page
> Creating Export1394 Page
> Creating ExportAVI Page
> Creating ExportStills Page
> Creating ExportAudio Page
> Creating ExportMJPEG Page
/usr/share/kino/scripts/dvdauthor/growisofs.sh
/usr/share/kino/scripts/dvdauthor/dvdauthor-k3b.sh
/usr/share/kino/scripts/dvdauthor/none.sh
/usr/share/kino/scripts/dvdauthor/dvdauthor.sh
/usr/share/kino/scripts/dvdauthor/qdvdauthor.sh
> Initializing MJPEG Export Page settings from Preferences
> Creating ExportPipe Page
/usr/share/kino/scripts/exports/extract_chapters
/usr/share/kino/scripts/exports/mencoder.sh
/usr/share/kino/scripts/exports/ffmpeg_flv.sh
/usr/share/kino/scripts/exports/ffmpeg_mp3.sh
/usr/share/kino/scripts/exports/ffmpeg_divx_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_mp4.sh
/usr/share/kino/scripts/exports/ffmpeg_3gp.sh
/usr/share/kino/scripts/exports/ffmpeg_h264.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd_dual.sh
/usr/share/kino/scripts/exports/ffmpeg2theora.sh
/usr/share/kino/scripts/exports/ffmpeg_h264_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_mp4_dual.sh
/usr/share/kino/scripts/exports/rawplay.sh
/usr/share/kino/scripts/exports/ffmpeg_utils.sh
/usr/share/kino/scripts/exports/ffmpeg_xvid_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_divx.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd.sh
/usr/share/kino/scripts/exports/ffmpeg_xvid.sh
/usr/share/kino/scripts/exports/ffmpeg_vcd.sh
> Creating page trim
>>> Image Create: Colour Range
>>> Image Create: Fixed Colour
>>> Image Create: From File
>>> Image Create: Gradient
>>> Image Create: Random noise
>>> Image Filter: No Change
>>> Image Filter: Black & White
>>> Image Filter: Kaleidoscope
>>> Image Filter: Fade In
>>> Image Filter: Fade Out
>>> Image Filter: Flip
>>> Image Filter: Mirror
>>> Image Filter: Reverse Video
>>> Image Filter: Sepia
>>> Image Transition: Dissolve
>>> Image Transition: Barn Door Wipe
>>> Image Transition: Differences
>>> Image Transition: No Change
>>> Image Transition: Push Wipe
>>> Image Transition: Switch
>>> Audio Filter: No Change
>>> Audio Filter: Dub
>>> Audio Filter: Fade In
>>> Audio Filter: Fade Out
>>> Audio Filter: Gain
>>> Audio Filter: Mix
>>> Audio Filter: Silence
>>> Audio Transition: Cross Fade
>>> Audio Transition: No Change
> Creating Magick Page
>> Searching /usr/lib/kino-gtk2 for plugins
>>> Registering plugin /usr/lib/kino-gtk2/libtimfx.so
>>> Registering plugin /usr/lib/kino-gtk2/libdvtitler.so
>>> Registering plugin /usr/lib/kino-gtk2/libkinoplus.so
>>> Image Filter: Blur
>>> Image Filter: Colour Hold
>>> Image Filter: Soft Focus
>>> Image Transition: Luma Wipe
>>> Image Filter: Superimpose
>>> Image Filter: Titler
>>> Image Filter: Colour Average
>>> Image Filter: Charcoal
>>> Image Filter: Jerky
>>> Image Filter: Levels
>>> Image Filter: Pan and Zoom
>>> Image Filter: Pixelate
>>> Image Transition: Composite
>>> Image Transition: Blue Chroma Key
>>> Image Transition: Green Chroma Key
>> Starting Editor

At this point Kino its up and running, then I click on capture and it 
start this output until i close it.

>>> iec61883Writer::iec61883Writer port 0 channel 63
>> Creating undo/redo buffer
>> Kino Common newFile
>>> Received playlist to store at position 0
>>>> Adding to end
>> Leaving Editor
>> Left Editor
>> Starting Capture
>> AV/C Enabled
>>> Using iec61883 capture
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0...
(it keeps repeating this until i change back to edit)

How do I know that my firewire card is correctly recognize by the system?
What about my camera, is there some test to probe that my camera is accessible?

---

### Post by eevargas on 2008-05-09
new error . . .
I started raw1394 and kino as root and there is no more error about raw1394 read/write thing, but it said now that there is 

No A/V compliant cam connected or not switched on?

but my camera is conected and it is on!

---

### Post by scott_g on 2008-05-09
Ok; I'm still not entirely sure what is causing the problem...  Maybe someone else will know.  Anyways, this is what I've found so far:

[This]("http://ubuntuforums.org/showthread.php?t=531566") seems kinda similar.

As does [this]("http://www.fedoraforum.org/forum/showthread.php?p=848338").

As for finding out if the hardware is detected properly, you can look at your system log; when you plug in your camera, it should be detected by the system and recorded in this log.  I know in 7.10 there was a hardware database you could look up how Ubuntu recognized your hardware, but I this seems to have dissappeared.  Sorry I can't be of more help; hopefully someone else will have another suggestion.

Scott

---

### Post by Dai777 on 2008-05-17
Try this it worked for me

To set up kino to use raw1394 on Ubuntu Hardy Heron do the following:
type in the following in to the terminal:

sudo gedit /etc/udev/rules.d/40-permissions.rules
type in your password

copy the line 
KERNEL=="raw1394",			GROUP="disk"
and paste it so the are are two of them.

now change the second line so it reads.
KERNEL=="raw1394",			GROUP="video"

and comment out the first line

reboot your system and Kino should be set up to capturte video.

here is an example:
# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
#KERNEL=="raw1394",			GROUP="disk"
KERNEL=="raw1394",			GROUP="video"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"

---

### Post by shane19174 on 2008-08-22
Hi,
I've got the same problems with my Panasonic PV-GS59 connected via firewire (running Hardy). Kino doesn't recognize it at all. Not only does AV/C not work, but it won't even capture when I start the playback manually on the camera. Dvgrab is installed, but also reports that no camera exists. I've tried the solutions mentioned here and all others I could find (adding user to groups "disk" and "video", running kino as root, changing permissions on raw1394, etc), but to no avail. I'm sure I'm overlooking something basic, as I'm relatively new to Linux (but willing to learn!). I really don't want to have to go back to Windows just to capture video, but until I get firewire support I don't have much choice. Any help would therefore be greatly appreciated!

---

### Post by Erlander on 2008-08-22
I've uninstalled Kino for the present so can't try and see what mine does.

However if I connect a video camera via firewire and turn it on then I see that it has been recognised in dmesg.

Try it.

Rob

---

### Post by shane19174 on 2008-08-22
First of all, thanks for your reply. As I'm relatively inexperienced, though, could you please tell me what I should be looking for in dmesg?

Also, if any other output is needed, let me know.

Thanks again,
shane

---

### Post by Erlander on 2008-08-22
If you turn your connected camera on after the computer then the lines concerning it will be at the end of dmesg.

Here is what I get:

```
[  694.929190] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[  695.036760] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[080046010311af60]
[  695.037728] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[  695.123887] NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. Use raw1394 instead
```

Yes,  I'm getting some interesting code that when I re-install Kino etc I will need to look into.

However just to get a response when you turn the camera on is a start.  Previously I was able to grab video in Kino.

Rob

---

### Post by shane19174 on 2008-08-22
Hi Rob,
Thanks once again for your reply. I'm attaching the output of dmesg as a txt file in case it helps. I'm still not sure exactly what's relevant and what's not. However, when I searched for "1394" these are the only things I found (scattered throughout the output):

[   25.457365] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]

[   26.730894] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0001396067]

[   33.245912] ieee1394: raw1394: /dev/raw1394 device initialized

Is this good, bad, relevant at all?

Thanks again,
Shane


PS: the txt file is too big for the forum, so let me know if it's needed and I'll try to compress it or something.

---

### Post by shane19174 on 2008-08-22
Trying to narrow things down, I booted up a Hardy live-CD and did a dmesg both before and after turning on my camcorder. The only entries with "1394" in them were these two, which were IDENTICAL in the before and after scenarios:

[   46.248148] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]

[   47.531884] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0001396067]

Clearly, raw1394 isn't there because I didn't load it up in the live environment. But the other two, because they are identical with dmesg's output in my working installation, suggest to me that absolutely nothing is happening when I turn on the camera.

Just to clarify, I'm positive that the camera is connected correctly, and I know that both it and the firewire port to which it's connected work, because I have no problems capturing video with just this hardware under Vista (into which I dual boot if and when I have to).

Any suggestions for getting my firewire and camera working would be more than appreciated!

Thanks,
shane

---

### Post by Erlander on 2008-08-23
Sorry.

I don't know either.

---

### Post by shane19174 on 2008-08-23
Anyone any ideas?
Thanks,
Shane

---

### Post by Erlander on 2008-08-23
Shane,

Have a look at this and see if it helps.

Rob

[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

---

### Post by Bunyak on 2008-08-24
Hi, folks.  I'm with Shane on this one.  Using 8.04.  Tried it all.  Did the dmesg as well... the camera is recognized.  Changed permissions, added groups, yadda.  Here's an interesting thing, though... I have no file "raw1394" in /dev.  wassup with that?

Please help.

---

### Post by Erlander on 2008-08-24
Make sure you have libraw1394-8 installed.

A synaptic search for raw1394 will find it for you.

Rob

---

### Post by Erlander on 2008-08-24
Its also worth reading /usr/share/doc/libraw1394-8/README.debian

Rob

---

### Post by shane19174 on 2008-08-24
Rob,
Thanks again for your help. It looks like your last suggestion has provided the solution (though I need to test some more). The file /usr/share/doc/libraw1394-8/README.debian suggested executing the following command:

grep IEEE1394 /boot/config-`uname -r`

When I did this, I got the following:

CONFIG_IEEE1394=m
CONFIG_IEEE1394_DV1394=m
CONFIG_IEEE1394_ETH1394=m
CONFIG_IEEE1394_ETH1394_ROM_ENTRY=y
CONFIG_IEEE1394_OHCI1394=m
CONFIG_IEEE1394_PCILYNX=m
CONFIG_IEEE1394_RAWIO=m
CONFIG_IEEE1394_SBP2=m
# CONFIG_IEEE1394_SBP2_PHYS_DMA is not set
# CONFIG_IEEE1394_VERBOSEDEBUG is not set
CONFIG_IEEE1394_VIDEO1394=m

The readme says that I will have to do a modprobe raw1394 because of the "m" following RAWIO (I assume that m means manual). This modprobe was nothing new to me (having read about this in countless forum threads), but I noticed an "m" following IEEE1394, which suggested to me that firewire itself was not automatically enabled. So I ran modprobe ieee1394, followed by modprobe raw1394, started up kino, headed to edit, preferences, capture, and what do you know? Panasonic PV-GS59 is indicated under AV/C devices!!!

I haven't had time to actually capture video yet, but it looks like there's nothing standing in the way anymore!

Again, thanks for all your efforts. I hope this might help someone else as well.

One last question: how do I get both ieee1394 and raw1394 to load automatically on bootup?

Shane

---

### Post by shane19174 on 2008-08-24
Or: assuming that loading the two modules at boot is too much of a security risk (?), is there any way to get them to load when I start kino? Could this be as simple as editing the menu entry for kino with alacarte and adding the modprobes before kino?

Also, I'm wondering about what exactly the right permissions and other settings related to 1394 really are. I've changed so many things in my attempts to get things working, and I'm afraid I may have added some potentially dangerous settings that are not even necessary.

My request, then, would be for some people with working firewire and camera control in kino to post some output and suggested settings.

Thanks,
Shane

---

### Post by Erlander on 2008-08-24
This is the answer on how to get raw1394 to load at boot:

> Method 5. 'GROUP=video'

In order to enable dv capturing with Feisty you just have to modify the file "/etc/udev/rules.d/40-permissions.rules" and change

KERNEL==”raw1394&#8243;, GROUP=”disk” to KERNEL==”raw1394&#8243;, GROUP=”video”

Then just add "ieee1394" (without quotation marks) to "/etc/modules" 

Its the last bit about adding to the file /etc/modules that gets it to load at boot.

It turns out that I didn't un-install Kino.  Its still there and I've just been trying it out.

To avoid the use of gksudo to start it I used the part of changing the group from disk to video.

Like you I have changed so manny settings over time that I am no longer sure what should be what.  I suspect that the only way I will get it back is a clean install.  But then I would have to go through getting it all to work again.

Rob

---

### Post by shane19174 on 2008-08-24
Rob,
Thanks, that seems to be what I was looking for. I had added raw1394 to my /etc/modules, but not ieee1394. Should I remove the raw1394 entry? Is it overkill, or does it perhaps even compromise security?
Shane

---

### Post by Erlander on 2008-08-24
Shane,

I think the only problem with security is if other people you don't trust have physical access to your computer.  If they are knowledgeable enough they could then gain access via the firewire port.

I'm leaving it in /etc/modules myself as I'm the only one who uses this home computer.

I've learnt as I went along on this.  The research helped me get my installation working properly.

Now I only have to get the high definition capture and editing from my new hard disk camera sorted out.

Rob

---

### Post by shane19174 on 2008-08-25
Thanks, Rob. Unless someone can show me a better way, I'll be keeping the entries in /etc/modules as well.
And to follow up, DV capture in Kino is now working without problems. Hopefully this thread will help others with similar problems.
As to Bunyak's question, I would check (as Rob suggested) that libraw1394-8 is installed, and then see post #20 in this thread (i.e., make sure to do a
 
modprobe ieee1394 

and 

modprobe raw1394

to load the modules as necessary). If that doesn't work, please post back. Who knows? Even though I haven't been using Ubuntu very long, maybe I will have stumbled across the appropriate answer in my attempts to get my own setup working.
Shane

PS: Why is that little devil icon showing up whenever I post?

---

### Post by Bunyak on 2008-08-29
> **Erlander said:**
> Make sure you have libraw1394-8 installed.

A synaptic search for raw1394 will find it for you.

Rob

Yes, have raw1394 :-(

---

### Post by Erlander on 2008-08-30
> **Bunyak said:**
> Yes, have raw1394 :-(

well the next step is to try the other suggestions in this thread beginning with the modprobe steps.

Rob

---

### Post by Bunyak on 2008-09-01
> **Erlander said:**
> well the next step is to try the other suggestions in this thread beginning with the modprobe steps.

Rob

Despite having libraw1394 "installed" (according to synaptic), when I run dvgrab in terminal, I get the message "raw1394 - failed to get handle: No such file or directory." This is consistent with the message i get when i try to capture using Kino "raw1392 kernel module not loaded or failure to read/write dev/raw1394"  I have checked for the file location dev/raw1394, and it does not exist. I have downloaded libraw1394-2.0.0, but as a total Linux newbie, i have no clue how to install this file. I assume, or course, that Kino is looking for raw1394 and cannot find it.

Is this helpful?  Is there any other information I should be providing?  Is it helpful that I am running "Ubuntu Studio?"

Thanks, all.

---

### Post by Erlander on 2008-09-01
Hi Bunyak.

I'm sorry that I don't know Ubuntu Studio.

However in your situation I would use Synapatic to do a complete removal of raw1394 and then a re-install (2 separate steps).  It should show up as a file in the dev folder.  ie at the bottom below all the sub-folders in dev.

The message you are getting when opening dv-grab in Kino is consistent with you not having the permission to open raw1394.  You can test this by starting Kino from Terminal using sudo.  However if you capture using sudo you wont own the files so this would then need fixing.

This is done by > Method 5. 'GROUP=video'

In order to enable dv capturing with Feisty you just have to modify the file "/etc/udev/rules.d/40-permissions.rules" and change

KERNEL==”raw1394&#8243;, GROUP=”disk” to KERNEL==”raw1394&#8243;, GROUP=”video”

You then need to add yourself to the video group. (System/Administration/Users& Groups)

Then to get raw1394 to load at bootup you need to > Then just add "ieee1394" (without quotation marks) to "/etc/modules" 

Rob

---

### Post by Bunyak on 2008-09-01
> **Erlander said:**
> Hi Bunyak.

I'm sorry that I don't know Ubuntu Studio.

However in your situation I would use Synapatic to do a complete removal of raw1394 and then a re-install (2 separate steps).  It should show up as a file in the dev folder.  ie at the bottom below all the sub-folders in dev.

The message you are getting when opening dv-grab in Kino is consistent with you not having the permission to open raw1394.  You can test this by starting Kino from Terminal using sudo.  However if you capture using sudo you wont own the files so this would then need fixing.

This is done by 

You then need to add yourself to the video group. (System/Administration/Users& Groups)

Then to get raw1394 to load at bootup you need to 

Rob

OK... Really cool and AWESOME advice!  Did the modprobes, etc.  Kino now finds raw1394.  Also edited 40-permissions.rules with the kernel-disk-video stuff.  However, the camera name does not appear on the av/c menu in Kino, nor is it given a number.  I also added ieee1394 to /etc/modules.  What do i do next?  Is it a firewire card issue or a camera issue?

---

### Post by Erlander on 2008-09-01
> the camera name does not appear on the av/c menu in Kino

I just fired up the computer I have Kino on and my camera didn't show up either.  I put a tape in it and made sure it was in VCR mode and there it was.

As well as this check your connections and if you still don't have it seen by your pc then I would try it on a Windows pc and see if Windows Movie Maker recognises it.

Rob

---

### Post by remeeraz on 2008-10-14
To get firewire / 1394 to work, and have full control your camera controls through Kino, check out my post on how to make it all work.

[http://ubuntuforums.org/showthread.php?t=946708](http://ubuntuforums.org/showthread.php?t=946708)

---

### Post by remeeraz on 2008-10-14
> **Bunyak said:**
> OK... Really cool and AWESOME advice!  Did the modprobes, etc.  Kino now finds raw1394.  Also edited 40-permissions.rules with the kernel-disk-video stuff.  However, the camera name does not appear on the av/c menu in Kino, nor is it given a number.  I also added ieee1394 to /etc/modules.  What do i do next?  Is it a firewire card issue or a camera issue?

It's not a Firewire card or a Camera issue, it's purely the fact that you don't have ownership of the raw1394 node on your system.

I've written some clear instructions on how to get firewire to work propperly in the following thread.

[http://ubuntuforums.org/showthread.php?t=946708:](http://ubuntuforums.org/showthread.php?t=946708:))

---

### Post by Bucky Ball on 2008-12-15
Well, I have tried everything I can find but no luck with AV/C. Stop works. Recognises camera until I go to Capture window. Then goes blank. Back to Edit window: Camera back. Even the AV/Controls show up as usable. You can click but they just don't operate. Works fine if I operate the camera manually.

---

### Post by merlos on 2009-01-22
Hi all,
I had the same problem described on this thread with my Firewire Samsung VP-D590i DV camera (using Ubuntu/Kubuntu 8.10)
Using Kino and Kdenlive my camera where not detected.

Tried to fix permissions, add user to video group, became root but still no luck :(

Then I think I discovered the problem.
As far I can understand Kino and kdenlive use dvgrab to control the camera and download and import the .dv files. I had a look into the source code of kdenlive and I think Kino do the same.

First of all a look to the kernel side. I have the 2.6.27-9 kernel

> merlos@alligatore:~$ uname -a
Linux alligatore 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
merlos@alligatore:~$

When I plug and power on my camera I receive the following

> merlos@alligatore:/home/merlos$ tail -f /var/log/syslog

Jan 11 10:48:20 alligatore kernel: [ 1919.159874] ieee1394: Node added: ID:BUS[0-00:1023]  **GUID[_0000f0000a2814f5_]**
Jan 11 10:48:20 alligatore kernel: [ 1919.161870] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Jan 11 10:48:20 alligatore kernel: [ 1919.163537] ieee1394: config ROM CRC error
Jan 11 10:48:20 alligatore kernel: [ 1919.302752] ieee1394: raw1394: /dev/raw1394 device initialized
Jan 11 10:48:20 alligatore kernel: [ 1919.322522] NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. Use raw1394 instead.


Last log line can be ignored, is not a problem; the CRC error can be ignored too.

This means that the kernel recognized th deice; in /sys filesystem I have the right new entry for the firewire camera

> merlos@alligatore:**/sys/bus/ieee1394/devices**$ ls -l
total 0
lrwxrwxrwx 1 root root 0 2009-01-11 10:48 0000f0000a2814f5 -> ../../../devices/pci0000:00/0000:00:1e.0/0000:**06:01.0**/fw-host0/0000f0000a2814f5
lrwxrwxrwx 1 root root 0 2009-01-11 10:48 0000f0000a2814f5-0 -> ../../../devices/pci0000:00/0000:00:1e.0/0000:**06:01.0**/fw-host0/0000f0000a2814f5/0000f0000a2814f5-0
lrwxrwxrwx 1 root root 0 2009-01-11 10:16 00e018000387778d -> ../../../devices/pci0000:00/0000:00:1e.0/0000:**06:01.0**/fw-host0/00e018000387778d
lrwxrwxrwx 1 root root 0 2009-01-11 10:16 fw-host0 -> ../../../devices/pci0000:00/0000:00:1e.0/0000:**06:01.0**/fw-host0
merlos@alligatore:/sys/bus/ieee1394/devices$


An lspci confirm that the device is operational (06:01.0 addr)

> merlos@alligatore:/sys/bus/ieee1394/devices$ lspci
[...]
**06:01.0** FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
merlos@alligatore:/sys/bus/ieee1394/devices$

So on kernel side all seems ok :)

Now I tried to use dvgrab to import from my camera; I first looked into source code of kdenlive to try to get the right import command and it seems this one

dvgrab --format raw -i capture - 

so I did the same command from  a console on my Ububox while my camera whas playing and I got an error

> merlos@alligatore:~/kdenlive-0.7.1/src$ dvgrab --format raw -i DVFileName 
send oops                                                                
send oops                                                                
send oops                                                                
Error: no camera exists 

The error is from dvgrab that seems not discover the camera.

Then I did the following 

dvgrab **_--guid 0000f0000a2814f5_** --format raw -i DVFileName

forcing dvgrab using the node with specified hex GUID (from syslog) and :D:D yes naw I can use my camera :)

> merlos@alligatore:~/kdenlive-0.7.1/src$ dvgrab --guid 0000f0000a2814f5 --format raw -i capture                                                                                    
send oops                                                                                                                                                                           
[...]                                                                                                                                                                       
send oops                                                                                                                                                                           
libiec61883 warning: Transmission node has no plugs online!                                                                                                                         
Established connection over channel 63                                                                                                                                              
Warning: Cannot set RR-scheduler                                                                                                                                                    
Warning: Cannot disable swapping                                                                                                                                                    
Going interactive. Press '?' for help.                                                                                                                                              
send oops
send oops
send oopsstopped"  ""          sec
send oops
send oopsstopped"  ""          sec
send oops
send oopsstopped"  ""          sec
send oops
send oopsstopped"  ""          sec
send oops
send oops  ""          sec
send oops
send oops  ""          sec
send oops
send oops  ""          sec
send oops
send oops  ""          sec
send oops
send oops  ""          sec
send oops
send oops  ""          sec
send oops
send oops  ""          sec
send oops
send oops  ""          sec
send oops
send oops  ""          sec
send oops
send oops  ""          sec
send oops
send oopsstopped"  ""          sec
send oops
send oopsstopped"  ""          sec
send oops
send oopsstopped"  ""          sec
send oops
^C  ""          sec
merlos@alligatore:~/kdenlive-0.7.1/src$

On my directory I have the .dv files and I used it on kdenlive and kino. 

REMEMBER: when you launch dvgrab from console the camera must be playing!!

So. In conclusion I think the problem is related to dvgrab that won't recognize some camera; suported camera where recognized without using the --guid switch (looked at someoutput of working camera).

I willo post this on dvgrab forum (hope soon).

Last, my dvgrab version is 3.1

> merlos@alligatore:~$ dpkg-query -l dvgrab
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                    Version                                 Description
+++-=======================================-=======================================-==============================================================================================
ii  dvgrab                                  3.1-2                                   grab digital video data via IEEE1394 and USB links
merlos@alligatore:~$


Hope this help someone out there :)

Cheers 
Giovanni

---

### Post by 4ebees on 2009-01-23
> **shane19174 said:**
> Hi,
I've got the same problems with my Panasonic PV-GS59 connected via firewire (running Hardy). Kino doesn't recognize it at all. Not only does AV/C not work, but it won't even capture when I start the playback manually on the camera. Dvgrab is installed, but also reports that no camera exists. I've tried the solutions mentioned here and all others I could find (adding user to groups "disk" and "video", running kino as root, changing permissions on raw1394, etc), but to no avail. I'm sure I'm overlooking something basic, as I'm relatively new to Linux (but willing to learn!). I really don't want to have to go back to Windows just to capture video, but until I get firewire support I don't have much choice. Any help would therefore be greatly appreciated!

Hi there,

One suggestion would be to join the kino mail group. They're very helpful and may be able to provide a solution for you.


Here's the URL:

[http://www.kinodv.org/article/static/6](http://www.kinodv.org/article/static/6)

Good luck

---

### Post by merlos on 2009-01-26
HI all guys.
I posted the problem on kino-dev ML. This is a known problem.

Stefan Richter (dvgrab devel) posted a patch to Linus for a fix; so this is not related to dvgrab but to the ohci1394 driver 

[http://marc.info/?l=linux1394-devel&m=123247508317615](http://marc.info/?l=linux1394-devel&m=123247508317615)

I hope we will have the fix in next Ubuntu kernel update.

Asap I will try the fix, rebuilding the ohci1394 module

Ciao
Giovanni

---

### Post by narcisgarcia on 2009-02-10
I get a 'read permission' error when trying to capture video (as normal user)

[http://en.wikibooks.org/wiki/Kdenlive/FAQ#I_get_a_.27read_permission.27_error_when_trying_to_capture_video_.28as_normal_user.29](http://en.wikibooks.org/wiki/Kdenlive/FAQ#I_get_a_.27read_permission.27_error_when_trying_to_capture_video_.28as_normal_user.29)

---

### Post by dapple_rose on 2009-07-06
I've come across a similar problem with jaunty 9.04. Clearly permissions related as kino recognised the dv recorder when launched as root.

I think there is a very simple solution using the users and groups application on the system administration menu. The user privileges  page includes a check box to allow the users to capture data from dv recorders.

This may be a simpler option for users without much command line experience.

---

