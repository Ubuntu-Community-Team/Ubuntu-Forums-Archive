---
title: "Virtualbox Gparted VDI Resize"
date: 2009-03-07
forum: Virtualisation
---

### Post by bf109 on 2009-03-07
Hi all,

My first post in these forums so I apologize if this is the wrong place to be asking this.

I followed these instructions to start a VDI resize and I am seeing this take a long time and there isn't any visible progress bar or indication of the amount of time it will take to complete (posted in thread on VirtualBox.org):

[INDENT][COLOR="Blue"]Hi,

You could try something like this (see also Tutorial - All about VDIs: How can I resize the partitions inside my VDI?):

   1. Create a new VDI of the desired size.
   2. Boot GParted Live in a VM with both old and new VDIs attached.
   3. Check in the partition editor (opened automatically after booting) what your old and new disk locations are. (It'll be something like /dev/hda and /dev/hdb.)
   4. Copy contents from old to new disk. This will take a fair amount of time. (Here /dev/hdX is your original disk and /dev/hdY the new one).

      Code: Select all   Expand viewCollapse view
          dd if=/dev/hdX of=/dev/hdY

          * Warning: Make sure you do not mix up your input and output disks or you'll wipe all information from your original disk! (if= specifies the input and of= specifies the output.)
   5. Reboot (again with GParted-Live). Now you should be able to increase the Windows partition size on the new disk.

Once you've verified the larger VDI boots Windows fine (and disk size is as you'd expect) you can of course delete the old smaller VDI.

Edit: Instead of rebooting before you resize the partition you should be able to run partprobe and the hit CTRL+R in GParted instead.

Regards,
VT[/COLOR][/INDENT]

The original VMI is only 3.16GB and the new VMI is 4.7GB. Both are NTFS and I am in the copy phase.

Anyone have any experience with this that could tell me the time it may take? Sitting here at Starbucks having an Americano and hoping I have the battery power left to complete. ;-) (Wont mater if it dies, these are just XP Pro test OS's).

bf109

---

### Post by bf109 on 2009-03-07
My bad. It finished the copy about 1 minute after I posted. :oops:

I then tried to boot the new VDI but it would not boot. I get an error that says:

A disk read error occured. 
Press ctrl+alt+del to restart.

I went back into GParted and tried to set the flag to "boot" not really knowing what that is supposed to do and it then gave me the error listed above (it was just sitting at a blank screen before that). I guess that copy process in GParted isnt actually creating an image then huh? No clue what to do now. :( I am just going to reinstall the OS if I can't get this to work but I would really like to know how to do this. ](*,) Any ideas?

---

### Post by bf109 on 2009-03-08
I saw a post about having to repair the boot sector on the new VDI so I boot the XP installation disk and in Recovery Console tried a "fixboot" and a "fixmbr" after trying to boot the OS again to no avail.

](*,) Help...anyone...anyone...Bueller...

---

### Post by bf109 on 2009-03-09
I tried to create a new VDI of 5.19g to see if that would make any difference since I found a post of someone who tried using different size VDI after experiencing the exact same issues I am and it did not work for me. The copy went off fine and this time the "bootable" flag was already marked but I am still getting the same error message as before when trying to boot. Its frustrating because I am seeing multiple posts of people following the exact same procedure as I am and having it work. Have no idea why it's not working for me. Karma? I'm stumped! :(

---

### Post by bf109 on 2009-03-11
I tried to make another .vdi file since I wasnt sure if I chose dynamically expanding or fixed the first time thinking that that may be the issue and got the exact same results.

I also find it surprising that absolutely no one in this forum has anything to offer me in the way of help. Have I broken some rule of forum conduct? ;) There has got to be someone in here that has run in to this same problem before, no?

---

### Post by ericy on 2009-03-11
> A disk read error occured. 

could be a machine-level issue. Did you remove the old drive (and attach the new drive as the primary drive)?

---

### Post by bf109 on 2009-03-11
Yes I did. I saw several tutorials that were quite specific about that, specifically making the newly created .vdi the primary master.

---

### Post by Ing.M.V. on 2009-03-27
> **bf109 said:**
> My bad. It finished the copy about 1 minute after I posted. :oops:

I then tried to boot the new VDI but it would not boot. I get an error that says:

A disk read error occured. 
Press ctrl+alt+del to restart.

I went back into GParted and tried to set the flag to "boot" not really knowing what that is supposed to do and it then gave me the error listed above (it was just sitting at a blank screen before that). I guess that copy process in GParted isnt actually creating an image then huh? No clue what to do now. :( I am just going to reinstall the OS if I can't get this to work but I would really like to know how to do this. ](*,) Any ideas?

I've got the same problem
I think I tried all the tips I found... but allways  the same result

A disk read error occured. 
Press ctrl+alt+del to restart

Any more ideas?

---

### Post by cyberb on 2009-04-19
Same problem.


1. Created new vdi disk (tried dynamic and fixed)
2. Booted to GParted iso.
3. Copy ntfs partition to new disk (aksed to create msdos partition table)
4. Tried to leave the size as is, but gparted said that destination partition is smaller than source partition. So extended partition in the copy dialog.
4. Set boot flag
4. Reboot
5. Unable to boot from new disk with the error:
"A disk read error occured.
Press ctrl+alt+del to restart."

If I boot with both attached disks original and new one (as secondary) windows will run checkdisk and I think fix something.

VB Version: 2.2.0-45846_Ubuntu_intrepid
GParted: 0.4.3-2.iso

Should I downgrade?

---

### Post by cyberb on 2009-04-19
Found the solution in that post [http://forums.virtualbox.org/viewtopic.php?t=1878:](http://forums.virtualbox.org/viewtopic.php?t=1878:)

   1. Install Boot Builder in your working virtual machine. [http://www.majorgeeks.com/Roadkils_Boot_Builder_d4980.html](http://www.majorgeeks.com/Roadkils_Boot_Builder_d4980.html)
   2. Launch Boot Builder
   3. Read the boot sector from the new disk (Drive D: in my case)
   4. Change the heads setting to 255
   5. Write the modified boot sector back to the same disk (Drive D: again)

Worked for me.
Hope it'll help you.

---

### Post by dakebusi on 2009-05-19
Hi,

The solution of using Boot Builder to change the number of heads to 255 does not always work. It can make the newly resized disk boot XP, but depending on the new size, this can be wrong (e.g. I got an 8 GB disk showing only 1.5 GB - the size of the disk I had cloned). 

To solve this, I used [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"). After installing it on your XP guest, I did the following (I found the instructions on [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")):
[LIST]
[*] Create a log file (doesn't really matter)
[*] Select your hard drive
[*] Select Intel partition table-type
[*] Select Advanced / Filesystem Utils
[*] Highlight your Vista Partition
[*] Select Boot / Boot Sector Recovery
[*] Select Rebuild Boot Sector (this will take some time while it searches MFT [Master File Table])
[*] Should say "Extrapolated boot sector and current boot sector are different"
[*] Select Write Boot Sector
[*] Reboot, You should see Windows giving you a simple DOS-type "configuration changed" error
[/LIST]

After that, I got my new disk with the right size.

---

### Post by Horizon on 2009-05-22
Thanks **cyberb**, boot builder worked great!

---

