---
title: "Help recover data from corrupted VDI file"
date: 2011-02-27
forum: Virtualisation
---

### Post by JKyleOKC on 2011-02-27
This afternoon my email client, which had been running flawlessly for a couple of years in a VBox installation of WinXP Pro, blue-screened for no obvious reason. When I shut down the VM using "vboxtool stop" and subsequently tried to re-start it, the XP boot sequence went into an infinite loop. After several attempts to diagnose the problem, I created a new VM and copied a working XP Pro VDI file from another box, with the intent of attaching the original VDI as the primary slave hard drive in order to recover my email files prior to a complete rebuild of the email VM.

This new VM worked perfectly, but when I attached the original VDI as its second hard drive, it again went into the infinite loop during the boot sequence. It would get as far as displaying the XP splash screen, then gave a brief glimpse of a blue screen and returned to the vbox splash screen for the next pass around the loop.

Attaching another, known good, VDI as the second drive works properly, so I believe the vbox installation itself is in good shape. Apparently that original VDI file has been corrupted in such a way that Windows cannot recognize it as a valid device.

At this point all I'm looking for is a way to recover my email data files, since I don't have current backups of all of them.

Pertinent data: I'm currently running vbox 3.2.12; the crashed VM was running headless at the time and being accessed alternately from rdesktop on a remote box, and rdesktop-vrdp on its host. The initial symptom of trouble was that it would not display via rdesktop-vrdp but would (at least one time) via rdesktop. I use vboxtool to autostart it at boot time, and to save it when the host shuts down. After the infinite loop appeared, I had to use "vboxtool stop" to shut down the VM so that I could (a) break the loop and (b) begin troubleshooting.

All ideas are welcome!

---

### Post by JKyleOKC on 2011-02-27
I've done some searching and came across a thread elsewhere that tells how to mount a VDI file as a loop device in order to access its content from Linux. It involves locating the start of the data in the VDI file, and starting the mount at that offset. With the help of hex editor hexdump I did locate the MBR and the NTFS header, and attempted to mount the file for examination. Here's the result: ```
jk@xubuntu:~$ sudo mount -t ntfs -o ro,noatime,noexec,loop,offset=155648 savemail.vdi mailsave
[sudo] password for jk: 
Failed to read last sector (62894411): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/loop0': Invalid argument
The device '/dev/loop0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```I suspect that the problem is one of the last two possibilities suggested but would welcome any suggestions of ways to repair it sufficently to access one directory and its subdirectories to recover the mail data.

However, it's possible that I need to use "losetup" first, to associate /dev/loop0 with the VDI file, and then try mounting it. Suggestions, anyone?

---

### Post by Hedgehog1 on 2011-02-27
> **JKyleOKC said:**
> 
Attaching another, known good, VDI as the second drive works properly, so I believe the vbox installation itself is in good shape. Apparently that original VDI file has been corrupted in such a way that Windows cannot recognize it as a valid device.


I think you were on the right track with this; but may I suggest doing this the other way around:

Attached the 'damaged' VDI as a second 'D:' drive on a different, working XP vbox.  Then startup the good Vbox, and copy your data to the good 'C:' drive.  this way you don't need the OS on the bad VDI at all...

This is what I would do for a real drive whose XP went south.

Just a thought.

:KS

---

### Post by JKyleOKC on 2011-02-28
> **Hedgehog1 said:**
> I think you were on the right track with this; but may I suggest doing this the other way around:

Attached the 'damaged' VDI as a second 'D:' drive on a different, working XP vbox.  Then startup the good Vbox, and copy your data to the good 'C:' drive.  this way you don't need the OS on the bad VDI at all...That's what I tried to do, but when I did so, the working XP vbox refused to finish booting. It gave a quick flash of blue screen but that went by so fast I had no chance to see what it said before the vbox splash screen came up for the next attempt.

The error message in my post #2 above seems to shed a bit more light on what is wrong. It's possible that the file got truncated, since it's supposed to be 30 GiB but is actually only 27.5 -- I've made a copy to experiment on, and plan to try editing its partition table manually in hopes that will allow it to be mounted as a second drive for copying. If I can get it to mount, either in a good XP vbox or direct in Linux, I'll at least be able to see whether anything can be salvaged from it...

Thanks for the suggestion!!!

---

### Post by Hedgehog1 on 2011-02-28
You are in uncharted waters for me now.  But please continue to share what you are learning.

Someday it might be me <gasp!> who needs to do this...

I do hope you are successful!

---

### Post by JKyleOKC on 2011-02-28
Will do!

Here's the latest: I tried using "VBoxManage clonehd" to create a "raw" version of the file. The process started, but apparently hung before getting to the 10% point on the progress line in CLI. After some 20 minutes of waiting with no progress and no apparent disk activity, I canceled that attempt and tried again with a different output file path of "$HOME/tryit" instead of "./tryit" which had tried to create the raw file in my vbox sub-directory. This time, it totally froze the system. No response to CTRL-C, unable to launch the file manager, could not log in on TTY1 even. I was considering doing a power-down to get out of the mess but tried tty6 (CTRL-ALT-F6) and got some error messages there, followed by successful login. This let me kill the "term" process that was hogging the system and brought everything back to life.

At this point I think that manually changing the partition table within the VDI file, on the assumption that the file was truncated, is the logical next step. However due to the size of the file I need to find a way to edit it in place! Making the actual change won't be a problem; I've written tools before to work with partition tables and am familiar with the format. Finding an editing tool, though, may be difficult -- I may have to stream everything through and use "sed" to make the change, which will be a bit tricky!

---

### Post by JKyleOKC on 2011-03-01
Quick update: I found some tools already present in my Xubuntu system that offer some hope, and definitely confirmed that the file had been truncated by some 2.5 GB. I'm about to try pasting a zero-filled padding to the end of (a copy of) the file to bring the partition back to the size shown in the table, and see whether that makes it possible to mount the file as a loop device and copy out at least some of the critical data. If it does, I'll then try mounting it as a second drive in vbox to see if I can get a full current backup of it!

I'll post a full report in this thread a bit later, including the commands I used to verify the damage and links to the threads in other places that gave me the leads to follow...

---

### Post by JKyleOKC on 2011-03-01
As promised, here's the full report.

The tools are hexdump (also known as hd), losetup, and sfdisk. The hexdump program displays content of a file in hex format, and here's how to use it to search for specific things in that file: ```
hd FILENAME | less
```which is purely brute force. If you have any idea of where to start looking, use ```
hd -s 155648 savemail.vdi |less
```instead to look at offset 155,648 in the file. I got that number from trial and error, based on links found at [http://ubuntuforums.org/archive/index.php/t-840996.html](http://ubuntuforums.org/archive/index.php/t-840996.html) and elsewhere; it's where the first partition starts in the "savemail.vdi" file. The MBR in the file is 63*1024 bytes earlier, at offset 123392.

The losetup program sets up a loop device, and using it as ```
sudo losetup -o 123392 -r -f savemail.vdi
```created /dev/loop1 (a loop0 device already existed on that system for some unknown reason). Having such a device let me move on to sfdisk, which I first invoked as ```
sudo sfdisk -d /dev/loop1
```This gave me a report ```
# partition table of /dev/loop1
unit: sectors

/dev/loop1p1 : start=       63, size= 62894412, Id= 7, bootable
/dev/loop1p2 : start=        0, size=        0, Id= 0
/dev/loop1p3 : start=        0, size=        0, Id= 0
/dev/loop1p4 : start=        0, size=        0, Id= 0

``` that showed a single partition, 62,894,412 sectors in size (or half that many 1024-byte blocks). Running it again as```
sudo sfdisk -V /dev/loop1
```reported that "partition 1 extends past end of disk" which verified that the file had been truncated.

My next step was to create a "pad" file with "dd" and then append it to the savemail.vdi file: ```
dd if=/dev/zero of=$HOME/pad bs=1K count=2609398
cat pad >>savemail.vdi

```The count was determined by subtracting the actual size of the file from the (adjusted) expected size, and converting to blocks. This brought the file back to being large enough. The final step was this: ```
sudo mount -t ntfs -o ro,noatime,noexec,loop,offset=155648 savemail.vdi mailsave

```The too-short problem was solved, but it still didn't work. The error message indicated that the Master File Table was apparently missing; it must have been in that 2.7 GB that got chopped off of the end!

Without the MFT, I don't think additional recovery efforts are warranted -- but I'm still willing to try most anything if an NTFS expert happens along. Meanwhile, I've installed Thunderbird on another system and am reconstructing my email filing system, starting over from scratch (and some 3-year-old backups of parts of it).

---

### Post by Hedgehog1 on 2011-03-01
Well, you get an A+ for effort.

Thanks for the follow up report!

---

### Post by molejo on 2013-03-21
> **Hedgehog1 said:**
> Well, you get an A+ for effort.

Thanks for the follow up report!

that's great :) I feel like I've done all things I wanted to do with my 250 GB backup restoration without doing it :D

now beeing more serious - I've got similar problem, but I'm trying to rescue broken hard drive. I'm rescuing it through resuce DD and what I get is many big pieces of drive needed to be joined.

I just wanted to be sure that I can/cannot see what's on rescued DD files BEFORE join them all.
Is it possible at all?

---

### Post by wildmanne39 on 2013-03-26
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

