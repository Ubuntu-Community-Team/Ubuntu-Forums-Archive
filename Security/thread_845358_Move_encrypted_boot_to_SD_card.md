---
title: "Move encrypted /boot to SD card"
date: 2008-06-30
forum: Security
---

### Post by Tubes6al4v on 2008-06-30
I would like to make my encrypted Hardy system (using the built in LUKS file system encryption) boot from my SD card. To put it another way, I want Ubuntu to only boot when I have this card in the built-in reader, and still require me to enter my password.

I have read up on a few different ways of making keyfiles and whatnot, but so far I have not found anything that does not require reformating. I would prefer to keep my stable setup intact.

Does anyone have any suggestions for me?

Thanks!

---

### Post by hyper_ch on 2008-06-30
/boot can't be encyrpted

---

### Post by Tubes6al4v on 2008-06-30
Hmm, I guess I just assumed that one. It does make sense that it wouldn't be able to be encrypted. So how would I go about moving my /boot to the SD card?

---

### Post by hyper_ch on 2008-06-30
can you boot from your sd card?

---

### Post by Tubes6al4v on 2008-06-30
I suppose that is a good question... No, it does not seem to give me that option. I would like to avoid using a USB flash  as it is very obvious. 

I suppose simply having boot on the SD then would not work. I remember in another thread asking if I could have both a Key file on an SD card and still have to enter a password (i.e. requiring both). This seems like it would take a fresh install. Do you have any suggestions for this?


BTW, thanks for your help thus far.

---

### Post by hyper_ch on 2008-06-30
I have no clue when sd cards are being mounted... but I don't think the bios can mount them, hence yuo can't load anything from them...

Hence why I asked if you can boot from it... because if you can, the bios can mount it, otherwise it will be the OS that will have to mount the sd card and in order to mount the sd card it first needs to mount it....

what's wrong with usb key? why do you want to put /boot on the sd card?

---

### Post by Tubes6al4v on 2008-06-30
An SD card sits flush with my system and is easy to miss. A USB stick is quite a bit more obtrusive. It would work, but not quite for what I am looking for. 

I want to be able to lock down my computer in various regards. Just in case. That is the same reason for the encryption. 

Is there any way to mount the SD card before booting into the OS?

---

### Post by hyper_ch on 2008-06-30
it is possible if the motherboard supports it ;) whether some motherboard does, no clue...

just have a powerkill button... press it, power gone... everything encrypted... I still don't see what benefit a sd card would give...

---

### Post by Tubes6al4v on 2008-06-30
Bummer man. I suppose that is one more thing for me to look out for as I plan for my next Desktop build. 

Thanks again for the help, reading up on hardware is always exciting, so I will be busy for a while.

---

### Post by hyper_ch on 2008-06-30
something like this:

[IMG]http://www.media-halle.de/shop/catalog/images/premium-line.jpg[/IMG]

Press the button, everything's off

---

### Post by Tubes6al4v on 2008-06-30
My problem is that I am running a Laptop at the moment, so cutting the power will just switch it to battery mode. My Power button is defaulted to 8 sec before forced shutdown.

---

### Post by chunkymonkey on 2008-07-01
Hi,

From what I understand, you've already got a Hardy setup with full encryption.  

You just want to use an encrypted SD card, so that you need the card in the slot and want it to prompt you for a password as well?

I've managed to get my laptop to require an SD card for a keyfile.  While messing around with getting this to work, I managed to come up with a script that will only boot *IF* you have the SD card in the slot.

From what I understand (I'm brand new to this...) if you've already got an encrypted HDD setup, you should be able to follow the steps in a howto to make an encrypted SD card and then just change parts of the bootscript so that it looks for an encrypted SD card.

In other words.  No need to reformat your entire system.  
1) Just create an encrypted SD card.  
2) Generate a keyfile.  
3) Set the system to accept the keyfile.  
4) Change the bootscript to look for the keyfile on the SD card on boot.

---

### Post by Tubes6al4v on 2008-07-01
Thank you Chunky for reviving my interest (though it barely decreased in one day) in setting this up. Actually, reading through your guide was what had initially piqued my intest (the guide can be found [here]("http://ubuntuforums.org/showthread.php?t=843571") ).

I must admit, however, that reading through that guide surely made me feel like much more of a novice than you. If you could help guide me through this process, it would be greatly appreciated. It seems as though this may be something interesting for more than just us two.

I added the modules as indicated. Next I ran:
```
fdisk -l
```

Which gave me the output below. It appears that our SD drives are in the same location ( /dev/mmcblk0p1 ):
```
Disk /dev/mmcblk0: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         984      991747+   6  FAT16

```


I read through [http://wejn.org/how-to-make-passwordless-cryptsetup.html](http://wejn.org/how-to-make-passwordless-cryptsetup.html) to get some idea of how it works. But I stopped short of actually working with it since I am unsure of how it will play into this application.

---

### Post by chunkymonkey on 2008-07-09
Sorry for the tardy reply Tubes... Real life got in the way. :roll:

I really am very new to linux in general, but I hope between the two of us we can get this to work. :D

First there's one important thing that I want to check.

1) Your HDD is already encrypted with LUKS (which is what I'm assuming because you've mentioned that you don't want to start from scratch again.)

[COLOR="Red"][B]***IMPORTANT*** I haven't actually tested this on my system yet, but from what I understand this should be what you need to get it to work on yours.
[/B][/COLOR]

If it is, we can then start this (I've taken bits from both [[http://mazeoflies.com/articles/2008/06/09/ubuntu-hard-drive-encryption-with-external-key](http://mazeoflies.com/articles/2008/06/09/ubuntu-hard-drive-encryption-with-external-key)]("http://mazeoflies.com/articles/2008/06/09/ubuntu-hard-drive-encryption-with-external-key") and [http://wejn.org/how-to-make-passwordless-cryptsetup.html]("http://wejn.org/how-to-make-passwordless-cryptsetup.html"))

So we're going to prepare an encrypted SD Card to hold the keyfile for the HDD.

We're not going to do this from the Live CD, but from the booted system.

So since you know which device you're going to use /dev/mmcblk0p1

we can go straight to filling the SD card with random bits

```
dd if=/dev/urandom of=/dev/mmcblk0p1
```

(It's not really required to do this, but it will make things harder for someone who gets a hold of the card to crack it if we do this.  If you want to make it even better, use /dev/random instead of /dev/urandom but it'll take a much longer time to fill the card)

Next we format the SD card with 
```
cryptsetup luksFormat --hash=sha512 --cipher=aes-cbc-essiv:sha256 --key-size=256 /dev/mmcblk0p1
```

This will ask you to provide a password for your SD Card.

Now we mount the SD Card

```
cryptsetup luksOpen /dev/mmcblk0p1 cryptkeys
```

And format as ext2.

```
mkfs.ext2 /dev/mapper/cryptkeys

```

Now since you HDD is already setup, we skip to the second howto and add the newly generated keyfile to the keys for your HDD.

From [http://wejn.org/how-to-make-passwordless-cryptsetup.html]("http://wejn.org/how-to-make-passwordless-cryptsetup.html")

> **Part One - adding password file to LUKS**

First you have to determine which partition is encrypted -- you can do that by inspecting contents of /etc/crypttab:

# cat /etc/crypttab
sda5_crypt /dev/sda5 none luks

So, we have sda5 encrypted. Good to know.

Now, we need to generate key file which we'll name root.key (for instance):

# head -c 2880 /dev/urandom | uuencode -m - | head -n 65 | tail -n 64 > root.key

If the command sequence fails for any reason, you don't have sharutils installed. Fix that via:

# apt-get install sharutils

and retry the previous password file generation one-liner.

You should end up with something like this:

# wc -l root.key
64 root.key
# head -n 3 root.key
9iDTzZlOy6P44YnoW7etVwVK7Xjj6SCvRNUkpTUPy1KjvQ3IsF8Q4hQ+Yda6
5XkXGJC8ylvAqc1ZvLMLEhIb2L73O90WCZhoj3GUkvTeohHDWLguBl23k1AX
wfVtPDZre3gpPuHhZNb3vOFzwjihfR2yMxykp6uuXjFlWLK4JNc4TLgRSWIq

Now we need to add the key file to that partition key pool:

# cryptsetup luksAddKey /dev/sda5 root.key

You will be asked for password, which is the boot-up password you've been using so far.

Cool. Now we have the password file registered as a valid key, so we just copy it over to USB stick and go about changing initramfs-tools setup. 

**Part Two - setting up (known) safe boot option**

We should make backup of existing initrd before attempting to tinker with the boot setup. Here's how:

Go to "/boot" and copy existing initrd image with -safe extension, to have known good copy.

In my case it looks like this:

# cd /boot/
# ls -1 init*
initrd.img-2.6.18-5-amd64
initrd.img-2.6.18-5-amd64.bak
# cp initrd.img-2.6.18-5-amd64 initrd.img-2.6.18-5-amd64-safe

Now we need to add the safe option to Grub (or your favorite boot manager).

Open /boot/grub/menu.lst, locate the kernel you're booting into, copy that block under the "END DEBIAN AUTOMAGIC KERNELS LIST" line.

Change "initrd" definition by adding "-safe" at the end and change "title" to indicate it's your safe option.

In my case the end of /boot/grub/menu.lst now looks like this:

# tail -n 7 /boot/grub/menu.lst
### END DEBIAN AUTOMAGIC KERNELS LIST

title           Debian GNU/Linux, kernel 2.6.18-5-amd64 (safe version)
root            (hd0,0)
kernel          /vmlinuz-2.6.18-5-amd64 root=/dev/mapper/vg-root ro 
initrd          /initrd.img-2.6.18-5-amd64-safe
savedefault

and I've created that from boot option that looked like this:

title           Debian GNU/Linux, kernel 2.6.18-5-amd64
root            (hd0,0)
kernel          /vmlinuz-2.6.18-5-amd64 root=/dev/mapper/vg-root ro
initrd          /initrd.img-2.6.18-5-amd64
savedefault

[B]Part Three - making our boot process run passwordless
[/B]
So, now we need to make few adjustments to make it all work.

First we need to add couple of modules to be loaded to the ramdisk:

# echo -e "vfat\nfat\nnls_cp437\nnls_iso8859_1" >> /etc/initramfs-tools/modules

because I assume you have your USB keychain with FAT filesystem and therefore you need vfat, fat, nls_cp437, and nls_iso8859_1 modules to mount it. 

Here we diverge from the second Howto...

But because we're using an SD card we also have to add
```
mmc_core 
ricoh_mmc 
mmc_block 
sdhci
```

to the end of /etc/initramfs-tools/modules

(since we formatted the SD card as ext2 we probably don't need all the FAT filesystem modules, but just the SD card ones... but it won't hurt keeping them in anyway)

back to the howto

> Next we need to change /etc/crypttab to accept our custom "keyscript" with proper key file. Mine looks like this, after the modification:

# cat /etc/crypttab
sda5_crypt /dev/sda5 root.key luks,keyscript=/usr/local/sbin/crypto-usb-key.sh

So I've changed the "key" option from "none" to "root.key" (which is the name of our pwfile) and added "keyscript" option which says to the init scripts to run that script in order to get password. 

So far so good.

Now we need the keyscript ... add this: 

This is where we make another change from the howto

We need to use a keyscript that mounts the encrypted SD card and then loads the required file from it.

I'm going to modify my SD card keyscript to make it work.

```
#!/bin/sh

# Part of passwordless cryptofs setup in Debian Etch.
# See: http://wejn.org/how-to-make-passwordless-cryptsetup.html
# Author: Wejn <wejn at box dot cz>
#
# Updated by Rodolfo Garcia (kix) <kix at kix dot com>
# For multiple partitions
# http://www.kix.es/
#
# Updated by Cromwel Flores <cromwel dot flores at gmail dot com>
# For Encrypted MMC/SD card using code from http://mazeoflies.com/files/keyscript
# 

# Disk partition type (ext2 or vfat)
PARTTYPE=ext2
# Key file in the disk
KEYFILE=root.key

# # # # # CODE # # # # #
MD=/tmp-mount

if [ "x$1" = "x" -o "x$1" = "xnone" ]; then
	KEYF=$KEYFILE
else
	KEYF=$1
fi

USBLOAD=0
FSLOAD=0
MMCLOAD=0
cat /proc/modules | busybox grep usb_storage >/dev/null 2>&1
USBLOAD=$?
cat /proc/modules | busybox grep $PARTTYPE >/dev/null 2>&1
FSLOAD=$?
cat /proc/modules | busybox grep mmc >/dev/null 2>&1
MMCLOAD=$?

#Check if all the required modules have been already loaded
if [ $USBLOAD -gt 0 ] || [ $FSLOAD -gt 0 ] || [ $MMCLOAD -gt 0 ]; then
	modprobe usb_storage 
	modprobe mmc_core 
	modprobe ricoh_mmc 
	modprobe mmc_block 
	modprobe sdhci 
	modprobe $PARTTYPE 
fi

OPENED=0

ls -d /sys/block/sd* >/dev/null 2>&1
SDS=$?

if [ $SDS -eq 0 ]; then
	echo "Trying to get the keyfile from physical keychain ..." >&2
	mkdir -p $MD

	#*** [Modified from http://mazeoflies.com/files/keyscript] ***
	# open the SD card, with 3 retries on the password
	count=0
	openstat=0
	while [ $count -lt 3 ]; do
	    count=$(( $count + 1 ))
	    if [ ! -e /dev/mapper/bootkey ]; then
	        echo -n "Enter Passphrase ==> " > /dev/console
	        cryptsetup luksOpen /dev/mmcblk0p1 bootkey > /dev/null 2>&1
	        openstat=$?
	    else
	        break
	    fi
	done

	# check for failure
	if [ $openstat -ne 0 ]; then
		echo "Failed to open device" > /dev/console
		exit 1
	#*** [/Modified from http://mazeoflies.com/files/keyscript] *** 
	else
		# Try getting file from SD Card
		echo "> Looking for keyfile in SD Card ..." >&2
		mount /dev/mapper/bootkey $MD -t $PARTTYPE -o ro 2>/dev/null
	
		if [ -f $MD/$KEYF ]; then
			cat $MD/$KEYF
			umount $MD 2>/dev/null
			OPENED=1
		else
			echo "> Could not find keyfile in SD Card ..." >&2
		fi
	fi
	umount $MD 2>/dev/null
	rmdir $MD 2>/dev/null
fi

```

I knocked up the keyscript without testing it, so it might need some ironing out.  [B][COLOR="Red"]Note: Do not delete your HDD password until you're sure that this script is bulletproof... cause otherwise you are SOL.

[/COLOR][/B]Now we return to the howto

> as /usr/local/sbin/crypto-usb-key.sh and chmod it a+x ...
Finishing line! All you need to do now is to update your initrd:

```
update-initramfs -u all

```
and you're ready to reboot! :-) 



Try rebooting.
The way things are setup right now, you should be prompted for the password for your SD Card.  You have 3 tries to get it right.
If you mess up or it can't find the keyfile on the SD Card your machine won't allow you to decrypt your HDD.

You'll have to restart and press esc when grub comes up and choose the safe boot option that will prompt you for your HDD password instead of trying to get the key from the SD card.

Once you're sure that everything is working, then you can go ahead and delete the HDD password using cryptsetup luksDelKey
(remember that if you do this and lose your SD card, you are so outta luck...)

I'm not gonna have stable net access for a week or so after Friday, but drop me a pm and let me know how things work out for you.

Good luck. :)

---

### Post by kevdog on 2008-07-09
To to be rude, but I about cra**ed my pants when I saw the Chucky had posted a rather detailed, informative, instructional reply.  Holy cow -- is the sky falling?

---

### Post by Tubes6al4v on 2008-07-09
I certainly did not expect you to do this! Thank you very much for the write-up. I had been chasing this down (staring at your script for way too long, trying to figure it out), and ran into the same problem I get here:

When I enter:
```
cryptsetup luksFormat --hash=sha512 --cipher=aes-cbc-essiv:sha256 --key-size=256 /dev/mmcblk0p1
```

I got:
```
cryptsetup luksFormat --hash=sha512 --cipher=aes-cbc-essiv:sha256 --key-size=256 /dev/mmcblk0p1
```

I did fdisk -l and found that my MMC card has 16 sectors. Looking into some documentation, I could not find any direct correlation between the sector size and the cypher used.

Using cat /proc/crypto lists sha256 as supported.


I just thought I would update you as far as I have gotten with this. I'll update more as I go along.


UPDATE:

Using:
```
cryptsetup -c aes-cbc-essiv:md5 -y -s 8 luksFormat /dev/
```
leaves me with the same message, but saying that my card meeds to have 16 sectors (which fdisk confirmed I have). Bummer. I'll try a work around with Truecrypt.

---

### Post by chunkymonkey on 2008-07-09
> **kevdog said:**
> To to be rude, but I about cra**ed my pants when I saw the Chucky had posted a rather detailed, informative, instructional reply.  Holy cow -- is the sky falling?

Huh? Do you mean that my other posts weren't informative? :confused: Or am I being mixed up with someone else? 

@Tubes6al4v
You're welcome. =D

Although, all I really did was just cut and paste selected bits from two other walkthrough to try and get this thing to work.

I don't actually know much about how cryptsetup works... :( we're  both gonna be stuck poring over the documentation for it.  (but I have a feeling that you didn't correctly copy the error message in your post?)

All that line is supposed to do is to make your SD card encrypted...  So you should be able to do that with TrueCrypt but I'm not familiar with TrueCrypt so I don't know if the mishmash of a keyscript I put together will work properly with it or not.

Good luck and keep us posted.

---

### Post by chunkymonkey on 2008-07-09
Actually, while I'm thinking about it what happens if you try this?
(I'm at work atm, so I can't test this out.)

```
 cryptsetup luksFormat /dev/mmcblk0p1

```

And then let it prompt you for all the options?

Also I'm not sure if the card is supposed to be unmounted before you do this.

---

### Post by Tubes6al4v on 2008-07-09
Final Reply Before bed:

I dropped the "p1" off of /dev/mmcblk0p1"

And that got me through to the end.

When I attempt to "sudo update-initramfs -u all" I get this response:

```
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
cryptsetup: WARNING: target sda5_crypt has an invalid keyscript, skipped
cryptsetup: WARNING: target sda5_crypt has an invalid keyscript, skipped

```

I have tried to play with different angles. Anyway, I'll pick this up tomorrow evening. Thanks!

---

### Post by chunkymonkey on 2008-07-09
=D Awesome.

Umm... Did you set the permissions correctly for the keyscript?
(again from memory)
```
 sudo chmod a+x /usr/local/sbin/crypto-usb-key.sh 
```

---

### Post by Tubes6al4v on 2008-07-09
Well, I guess it is good I stayed awake. I completely glossed over the chmod (Doh!). I updated without any issue. I will reboot now...

---

### Post by Tubes6al4v on 2008-07-09
Ok, I had to run:

```
sudo update-initramfs -u **-k** all
```
in order to get all of the Kernels to update.

I get this when booting:
```
Trying to get the keyfile from physical keychain ...
Enter Passphrase ==>
```

After entering my HDD password, nothing happens. I can hear the CPU fan spinning, but not either of the HardDrives.

well, I will take a look at what I did tomorrow. 

Thanks again brother.

---

### Post by chunkymonkey on 2008-07-10
> **Tubes6al4v said:**
> 
After entering my HDD password, nothing happens. 

This is prompting for the SD Card password.  Not the HDD Password.
(Sorry, cause I just mashed that keyscript together, its not very helpful or informative.  Especially if it gets the wrong password.  Depending where you're looking at things, it won't even tell you that it couldn't load the SD Card.)

---

### Post by simonapnic on 2008-07-10
> **hyper_ch said:**
> something like this:

[IMG]http://www.media-halle.de/shop/catalog/images/premium-line.jpg[/IMG]

Press the button, everything's off

[http://volatilesystems.blogspot.com/](http://volatilesystems.blogspot.com/)
This should make you aware of the fact that data from the RAM can be recovered shortly after a system has been powered off.

---

### Post by Tubes6al4v on 2008-07-10
After entering my dm-crypt passphrase for the sdcard I get the response:
"Could not find keyfile in SD Card ..."

I tried using cp to copy the file root.key to /dev/mmcblko, but that ends up making my passphrase not work. Any suggestions?

---

### Post by hyper_ch on 2008-07-11
> **simonapnic said:**
> [http://volatilesystems.blogspot.com/](http://volatilesystems.blogspot.com/)
This should make you aware of the fact that data from the RAM can be recovered shortly after a system has been powered off.

This "shortly" depends on various factors as that harvard study has shown ;)

---

### Post by chunkymonkey on 2008-07-11
> **Tubes6al4v said:**
> After entering my dm-crypt passphrase for the sdcard I get the response:
"Could not find keyfile in SD Card ..."


Oks... So we can open the SDCard. =D  Which means that we're able to decrypt the SDCard.

When you mount your SD card, is root.key actually present in the SD card?  

> 
I tried using cp to copy the file root.key to /dev/mmcblko, but that ends up making my passphrase not work. Any suggestions?

I'm not sure what you mean by it makes your passphrase not work.  Which passphrase?  The SD or HDD one?

When you try copying the file to the SD card, remember that you have to use cryptsetup first and then the normal mount command 
(so something that looks like this.)

```

cryptsetup luksOpen /dev/mmcblk0p1 <SomeMadeUpName>
mount /dev/mapper/<SomeMadeUpName> <SomeTmpDirectory> -t ext2 -o ro 
```

I'll be bereft of internet for a week or so, so good luck and I'll check in after that.

:D

---

### Post by Tubes6al4v on 2008-07-21
So I took quite a break from this, while getting myself ready to move out of the country. Well, I tried to pick this back up and came across an interesting note when performing "fdisk /dev/mmcblk0"

```
The number of cylinders for this disk is set to 31000.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
```

When I use fdisk to create create a partition from cilinder 1 to 1024, I run into the same issue I had before with /dev/mmmblk0p1 (which this is again)


To answer your last question, I cannot even see the contents of /dev/mmcblk0 However, I do not receive any errors when using the mounting code you gave.

---

### Post by chunkymonkey on 2008-07-22
> **Tubes6al4v said:**
> 
To answer your last question, I cannot even see the contents of /dev/mmcblk0 However, I do not receive any errors when using the mounting code you gave.

Ok, the error message at boot

> 
"Could not find keyfile in SD Card ..."

Will only occur if the card has been successfully mounted and decrypted but the file root.key is not present.

So you'll need to make sure that root.key is present on the SD Card.

The way I did this was to use the GUI and just drag and drop the file into the SD Card on the desktop.

I don't really know how SD Cards are setup and I have nfi why there's /dev/mmcblk0, /dev/mmcblk0p1 etc.  So can't even begin to guess know why fdisk is complaining.

When mounting a SD Card, I think it automounts as /media/disk

So just try copying the file there.

---

