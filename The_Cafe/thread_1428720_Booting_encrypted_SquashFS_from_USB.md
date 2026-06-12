---
title: "Booting encrypted SquashFS from USB"
date: 2010-03-13
forum: The Cafe
---

### Post by adamliq on 2010-03-13
I have been working on a project for booting an encrypted squashfs from usb.
Essentially what i have been doing is creating a container and encrypting it with luks.
Placing the filesystem.squashfs into the container renaming the container to be filesystem.squashfs.  Editing the intrd.gz to mount encrypted filesystem.  using remastersys to create a CDFS iso and then using USB startup disc creator.  However have been hitting problems such as will sit at a blank screen and flash with cursor after ubuntu loading symbol has come up.   The following instructions I grabbed from remote-exploit.org and are designed for BT4 and they have been what i followed.
The instructions mention persistant changes partition which I haven't wanted so I haven't followed that step.  ANY HELP WOULD BE APPRECIATED.

HI all, I recently wrote a guide on full disk encryption with hard drive installs on BT4 (It can be found [here]("http://forums.remote-exploit.org/backtrack-4-howto/25369-howto-bt4-pre-final-full-disk-encryption-2.html")). Due to my usual paranoia about my data, it was great that I had my hdd install of BT4 encrypted but what about the copy I keep on my usb drive? I feel that usb drives are more at risk for having data stolen considering how easy they are to lose.

I've been working with an encrypted usb BT4 for around a week now and I have noticed that performance is slightly slower. It is still perfectly usable for me but you might feel different. It is possible to backup your changes partition before starting and you will not lose any of your changes to your current usb BT4. I will not cover this extensively however; there may be one or two little notes in the guide below regarding this. Read to give it a try? read on.

This guide is not written for a newcomer to BT, or Linux for that matter, to follow. We will be setting up encrypted partitions and loop devices and editing the initrd. If you have no idea what that stuff is, let me direct you towards Google now. I aslo very highly recommend that you know how to install BT to an unencrypted usb drive before attempting this guide. Additionally, all commands in this guide should be run as root, not sudo. That being said, let's get started.


1.) OPTIONAL – The first thing you should do is overwrite your usb drive with random data. This step is optional but it will ensure that no data is left behind from whatever you had on your usb drive before. Note that this can take a long time depending on the size of your drive.
     Code:
     dd if=/dev/urandom of=/dev/sdX 
Obviously, replace the sdX with the appropriate letter. Depending on your level of paranoia you can use /dev/random as the if parameter which generates truly random data. This is considerably slower however and can lock up your system. Also, you can do /dev/zero as your if parameter after filling the drive with random data to make it look like random data was never written to the drive. It’s all up to you and how secure you want to be.


2.) You will need to partition your flash drive the same way as you would with an unencrypted usb BT install. That is, two partitions, one for the base filesystem (the filesystem.squashfs file) and whatever other data you like to keep on your drive and a second for the changes. In my experience I have found that 2-3gb should be good for the changes the partition, but that depends on how many changes you are planning to make. We will be formatting the second partition later so the filesystem type does not matter now.


3.) Depending on what distro you are using, you may have to load a kernel module. It doesn't hurt anything if it is already loaded.
     Code:
     modprobe aes-i586 

4.)  First thing is to download a new copy of BT4. Open the iso and extract the files.
     Code:
     mount -o loop /path/to/iso /mnt/bt4/ 
Head over to /mnt/bt4/ and under the casper directory you will find a file called filesystem.squashfs. Copy that to your home directory or some other temporary place. This file contains the entire filesystem wrapped up. We're going to create a luks container and put that file inside of it.

Also, in the BT iso you just mounted, under the boot directory, copy the initrd.gz to where you copied the filesystem.squshfs file.

You can unmount the BT iso now.


5.) Now we can start encrypting things.The first thing we need to encrypt is the filesystem.squashfs file. To do this we will create a luks container that is slightly bigger than the filesystem.squashfs file. I will use 1.5GB but you are free to choose any size, as long as it is larger than the filesystem.squashfs size of course.
     Code:
     # We will first make the container. The size is dictated by the count parameter in the dd command (in megabytes). Feel free to use /dev/random or /dev/zero instead of urandom.
# Note that this will take a few minutes.
dd if=/dev/urandom of=filesystem bs=1M count=1500

# If you receive an error such as "/dev/loop0: No such device or address", try /dev/loop1 and use that inplace of /dev/loop0 in the commands below.
losetup /dev/loop0 filesystem

# Choose a strong passPHRASE here. It's pointless to go through all this trouble to encrypt everything and then choose a weak password.
cryptsetup luksFormat /dev/loop0

# Now that we have our container lets open it, put a filesystem in it, and put the filesystem.squashfs file in.
cryptsetup luksOpen /dev/loop0 container
mkfs.ext3 /dev/mapper/container
mkdir /mnt/container
mount /dev/mapper/container /mnt/container
mv filesystem.squashfs /mnt/container

# Cleaning up...
umount /mnt/container
rm -rf  /mnt/container
cryptsetup luksClose /dev/mapper/container
losetup -d /dev/loop0

# Now we have the filesystem.squashfs file encrypted inside the filesystem container. We need to rename it. Simply...
mv filesystem filesystem.squashfs 
Alright. We now have the filesystem.squashfs file encrypted. Half way there.


6.) Now we need to encrypt the changes partition. You should have your flash drive partitioned already. The commands below will destroy all data on the partition you run them on. We will be encrypting your changes partition so replace the XX below with the appropriate number & letter (eg, /dev/sda1).
     Code:
     # Same thing as above with the passphrase you choose.
cryptsetup luksFormat /dev/sdXX
crypsetup luksOpen /dev/sdXX changes
mkfs.ext3 -L "casper-rw" /dev/mapper/changes 
That's it. We don't have anything to put inside yet so there's no need to mount it. However, if you backed up your changes before you started, this is when you want to put your changes back in. The commands would be something like...
     Code:
     # Note that this is only for putting backed-up changes back into the changes directoy!
mkdir /mnt/changes
mount /dev/mapper/changes /mnt/changes
cp -R /path/to/backed-up/changes /mnt/changes
umount /mnt/changes 

7.) We now have everything encrypted but this won't do us any good because our initrd doesn't know that what it is looking for is encrypted. Let's fix that. We will be using the initrd.gz that we downloaded and extracted from the BT iso earlier.
     Code:
     # First lets copy the initrd.gz file to its own directory and extract it.
mkdir ~/initrd
cp initrd.gz ~/initrd
gunzip initrd.gz
cpio -id < initrd

# While we're at it, delete the archives we just extracted so they don't get in the way when we compress everything again.
rm initrd
rm initrd.gz

# Now we can edit the startup script files.
cd scripts 
Open "casper-helpers" for editing (via nano, vi, gedit, etc). Starting on line 122 is the "setup_loop" function.
We need to make that function look like below.
     Code:
     setup_loop() {
    local fspath=$1
    local module=$2
    local pattern=$3
    local offset=$4

    modprobe ${MP_QUIET} -b "$module"
    /sbin/udevadm settle

    if [ "$module" = loop ]; then
        if [ ! -e /dev/loop0 ]; then
            # temporary workaround for kernel bug
            for i in 0 1 2 3 4 5 6 7; do
                mknod "/dev/loop$i" b 7 "$i" || true
            done
        fi

        dev="$(losetup -f)"
        if [ "$dev" ]; then
            if [ -n "$offset" ]; then
                losetup -o "$offset" "$dev" "$fspath"
            else

        # Encryption Changes Begin
        mkdir /mnt

        losetup "$dev" "$fspath"
        echo "Password: " >&6
        cryptsetup luksOpen "$dev" luksloop >&6

        # workaround (part 2):
        mount -t ext3 /dev/mapper/luksloop /mnt
        dev="$(losetup -f)"
        losetup "$dev" /mnt/filesystem.squashfs
        # Encryption Changes End

            fi
            echo "$dev"
            return 0
        else
            panic "No loop devices available"
        fi
    else
        for loopdev in $pattern; do
            if [ "$(cat $loopdev/size)" -eq 0 ]; then
                dev=$(sys2dev "${loopdev}")
                if [ -n "$offset" ]; then
                    losetup -o "$offset" "$dev" "$fspath"
                else
                    losetup "$dev" "$fspath"
                fi
                echo "$dev"
                return 0
            fi
        done
        panic "No loop devices available"
    fi
} 
My changes are marked between the comments "Encryption changes begin/end". 
Either replace the whole function with what I have posted above or just add in my changes between the two comments mentioned.

If you want, you can change the echo line that says "Password" to something else, like an error so that anyone that tries to boot BT may think it doesn't work and move on. If not, keep the password or remove the line entirely. Whatever works.

8.) Now that the initrd can mount the filesystem we need to make it mount the changes partition. First we will need the UUID of your changes partition. To get this run...
     Code:
     blkid /dev/sdXX 
Copy the seemingly random letters and numbers in between the quotes after UUID="XXXXXX..."

In the same directory as the "casper-helpers" directory, open the file "casper" for editing. Around line 334 you will find the "setup_unionfs" function. To conserve space, I will not post the entire function. Instead, scroll down and find the "# Looking for "${root_persistence}" device or file" comment and then find the "# Adding other custom mounts" comment. They should be around lines 385 and 400 respectively. Replace the text between those two comments with this...
     Code:
         # Looking for "${root_persistence}" device or file
    if [ -n "${PERSISTENT}" ]; then
        echo "Changes Password: " >&6
    cryptsetup luksOpen /dev/disk/by-uuid/ENTER-UUID-HERE casper-rw >&6
        cowprobe=/dev/mapper/casper-rw
        if [ -b "${cowprobe}" ]; then
            cowdevice=${cowprobe}
            cow_fstype=$(get_fstype "${cowprobe}")
        cow_mountopt="rw,noatime"
        else
            [ "$quiet" != "y" ] && log_warning_msg "Unable to find the persistent medium"
        fi
    fi

    mount -t ${cow_fstype} -o ${cow_mountopt} ${cowdevice} /cow || panic "Can not mount $cowdevice on /cow"

    mount -t ${UNIONFS} -o noatime,dirs=/cow=rw:$rofsstring ${UNIONFS} "$rootmnt" || panic "${UNIONFS} mount failed"

    # Adding other custom mounts 
Paste your UUID in where is the says "ENTER-UUID-HERE, and save the file. 

his part is the reason I can't just post my initrd; it will be different for every person.


9.) One more thing to change in the initrd. Go up one directory, and enter into the "conf" directory. Open the "modules" file for editing and make it look like this...
     Code:
     fbcon 
vesafb 
fuse
fan
thermal
unix
aes
dm-crypt
dm-mod
sha256
cbc
blkcipher 
Save that, and cd up one directory.

10.) We're all done editing the initrd. We now need to put it all back together. You must be in the ~/initrd (or whatever you named it) for this command. If not you will get a init not found error when booting BT.
     Code:
     find ./ | cpio -H newc -o > initrd
gzip -c initrd > initrd.gz 
11.) Alright. The only thing left to do is put everything back together and test it out. The easiest way for me to explain this is to tell you to install BT to your flash drive as normal. [This guide]("http://forums.remote-exploit.org/backtrack-4-howto/24696-howto-bt4-usb-persistent-changes-how-n00b-succeeded.html") does an excellent job of explaining that process.

The two things that are different now are as follows:
Replace the "filesystem.squashfs" file with the encrypted one we made and then replace the "initrd.gz" file with the one we modified.

You have to enter your password twice. First the one for the "filesystem.squashfs" file and the second for the changes partition. You could get around this by using [keyfiles]("http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile") but if someone gets a hold your keyfile, there goes the security provided by the encryption.

Also, it will seem that the system hangs after "aufs 2-standalone.tree-29-20090518" (which is right after you enter your second passphrase). Hit any random key followed by the enter key and your system will continue booting. I have no clue why this happens. I spent a lot of time searching through the initrd for what causes this came up with nothing. It's really nothing more than a minor annoyance but if you know how to prevent this, please be kind enough to share.

Okay, cross your fingers and hope it works now!

---

### Post by Kip Ingram on 2012-07-08
This is precisely what I'm looking for - I have a system that boots an iso from a usb stick in RAM, and then runs everything from there.  I use Remastersys to configure things just the way I want them before creating the stick.  

The problem, though, is that my pre-configured system is already logged into a number of websites and has some other sensitive information on it.  I never worry about leaving traces of this on the pc - it's all in RAM and as soon as I turn it off it's gone.  But I hate the idea of losing the USB stick.  If I could encrypt the squashfs file I'd be home free.

How has this worked out for you?

-- Kip

---

### Post by wildmanne39 on 2012-07-08
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

