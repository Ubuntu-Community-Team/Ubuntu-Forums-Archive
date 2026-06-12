---
title: "HOWTO: BIOS Update on Dell Vostro 200"
date: 2009-11-06
forum: Tutorials
---

### Post by mafitzpatrick on 2009-11-06
I recently added additional memory to my Vostro taking the total up to 4gb, however, an out of date BIOS meant that not all of this was available to Ubuntu. 

Dell provides a method for updating many system BIOS using firmware-tools packages and [the process outlined here]("http://en.community.dell.com/blogs/direct2dell/archive/2007/12/05/37446.aspx"). Unfortunately, the Dell Vostro 200 and a number of other systems are [not supported]("http://linux.dell.com/wiki/index.php/Firmware/Systems_Missing_RBU"). As an alternative, it is suggested that you can use the Dell [biosdisk project]("http://linux.dell.com/projects.shtml#biosdisk."), however, if you try this you'll quickly realise it does not work - attempting the upgrade spits out the rather cryptic "Error! udosexe = -5". You also get this error attempting to use [the method in this howto]("http://ubuntuforums.org/showthread.php?t=318789").

The error is caused because the Dell BIOS updater is a compressed archive containing both the BIOS image (2mb) and an installer. Unpacking that on a 1.44MB disk will not work. Frustratingly, it will also not work on a 2.88MB disk, because the compressed archive+unpacked contents is too big!

At this point you have two options - either create a bootable USB stick on Windows or do what I did (below):

First we want to create a 2.88MB disk image (1.44MB is too small for the 2MB BIOS code) and mount it.  Note that FreeDOS don't provide an 'empty' 2.88MB boot disk so we need to delete the fdos folder to get space.

```

cd ~
wget http://www.fdos.org/bootdisks/autogen/FDSTD.288.gz
gunzip FDOEM.288.gz
mkdir /tmp/floppy
sudo mount -t vfat -o loop,quiet,umask=000 FDSTD.288 /tmp/floppy
rm -rf /tmp/floppy/fdos

```

Next we need to install dosemu (a DOS emulator) so we can extract the BIOS files from the Dell installer but with unlimited diskspace.

```

sudo apt-get install dosemu
dosemu

```

You should get a window pop up that looks like DOS with the C drive active. What you are actually seeing is a dosemu 'virtual' drive, who's actual location on your Ubuntu system is ~/.dosemu/drive_c

Go to the Dell website and click to download the BIOS updater and choose where to save it. In the file box go to your home folder, right click in the folder list and select 'Show hidden files'. You should now be able to see the .dosemu folder and the drive_c one within. Save the file into the drive_c folder and once download is complete type the following in the DOS box:

```

dir

```

You should see your file listed there.

Type the name of the BIOS file and hit return to start it up. You should see a 'Copyright (c) Foxconn LTD 2001-2007...' message and importantly messages 'Decompress the exe file' and 'Decompress the bin file'. Unfortunately, you'll also notice that there is an error message and 'ALL Files removed!' at the bottom. So this is where you need to get quick with your fingers!

Run the BIOS upgrade file again in the DOS box, and wait until it says 'Decompress the bin file'. Now press Ctrl-C on the keyboard to cancel and exit the program. As the exe file was already decompressed it will now be on the drive.

```

dir

```

You should see (along with a lot of other files) another file with an EXE extension. In my case this is AFU877.EXE but it may differ if you're doing a different update (e.g. not on a Vostro 200) let me know. Note it down and make sure you amend any following instructions if needed.

Now we need to copy this file to our boot image disk. In the shell window (not the DOS box) type:

```

cp ~/.dosemu/drive_c/afu877.exe /tmp/floppy/afu877.exe

```

Now we need the BIOS update BIN file. So back in th DOS box, rerun the BIOS update file. Now you need to be very quick at this bit! Wait until after the 'Decompress the bin file' has finished, the first message is 'begin to check the bin file!'. Hit Ctrl-C again to cancel the deletion of the files. It doesn't matter if you miss it, just re-run the program until you get it right. Note that you will still get the 'ALL Files removed!' message, but it hasn't happened. You can check the file is there by typing:

```

dir

```

You're looking for a file named 713D1S49.BIN that is 2MB (2,097,152). Once you've got that you can give the hands a rest.  Now back in the shell type the following:

```

cp ~/.dosemu/drive_c/713d1s49.bin /tmp/floppy/713d1s49.bin

```

That's it for the DOS stuff so you can close the DOS box down. Now to tidy up and prepare to run the update.

```

sudo umount /tmp/floppy
rmdir /tmp/floppy
sudo mv FDSTD.288 /boot/biosupdate.img
sudo apt-get install syslinux
sudo cp /usr/lib/syslinux/memdisk /boot/

```

You now need to add the biosupdate boot image to your grub menu. You can do this from the command line as shown below, or run your favourite text editor (e.g. gedit or kate) as root.

```

sudo vim /boot/grub/menu.lst

```

Once you have the file open, simply add the following lines to the end.

```

title       BIOS upgrade
kernel      /boot/memdisk
initrd      /boot/biosupdate.img

```

Save the file and restart your computer. At the grub menu press 'ESC' and scroll down the list to select the final entry. FreeDOS should now start up and you will get a prompt whether to load various things (HIMEM/etc.) press 'N' until you get to the end with an A:> prompt. 

Start the BIOS update by typing the following:

```

afu877 713d1s49.bin

```

All done! Thanks for [ciscosurfer's howto]("http://ubuntuforums.org/showthread.php?t=318789") which formed the basis for getting this working!

---

### Post by joris1977 on 2010-01-09
Thanks worked real well!

No thanks to dell for not providing an easy linux solution to flash this bios. Especially because I choose dell for their ubuntu support. Dell doesn't sell ubuntu computers in my country so I bought a vostro 200 with Vista. Hoping that dell would support it for ubuntu. Seems to be a stupid decision now.

---

### Post by davidmb on 2012-01-04
Great tutorial. Thanks very much.

I managed to make it work with a few changes:

[LIST=1]
[*]Instead of dosemu, I used dosbox because it was already present in my system.
You can get both files at once by closing the emulator window right when "begin to check the bin file!" pops up. It takes so long that I thought the process hung up.
I did this three times and kept the files after each run (AFU877.EXE and 713D1S50.BIN) to compare them with diff (just an additional check to make sure the extracted files were always the same).
[*]To launch the image from grub2, I followed [this amazing trick]("http://blog.snow-crash.org/2010/11/cool-things-with-grub2-and-syslinux---booting-floppy-and-iso-images.html").
I copied biosupdate.img to /boot/images.
And then saved the script to /etc/grub.d/50_images and gave it execute permission.
[/LIST]
 Now the computer is running BIOS version 1.0.16 and the PAE Linux kernel can see all the installed RAM! :-)

---

### Post by lambart on 2012-05-08
Thank you very much mafitzpatrick for your detailed instructions!

After **three** hours plinking around with Dell's hapless biosdisk utility and trying to follow other instructions found on the web, I finally found this thread and was able to make it work! Of course, Ubuntu now uses Grub 2 so that part is out of date.

Hoping to save others a lot of the trouble I went through, I updated the [Ubuntu Wiki]("https://wiki.ubuntu.com/DellBIOS") page. Look for the **Updating the BIOS without without using biosdisk** section.

I liberally plagiarised your instructions and added the steps for modern systems with Grub 2. Hopefully folks will find that page easier to find than this HOWTO thread.

Eric

---

### Post by erlenddavidson on 2012-10-30
Thank you very much for this!  Almost a year ago I put more RAM in my parents' computer, but they could only see 2.3GB of it until I did this upgrade.

In the end I had to use the $_cpuspeed option in dosemu.conf to slow dosemu down so that I could press ctrl+c at precisely the right time.

Erlend

---

