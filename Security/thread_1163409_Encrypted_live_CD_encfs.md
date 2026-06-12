---
title: "Encrypted live CD encfs"
date: 2009-05-18
forum: Security
---

### Post by [3w`Sparky] on 2009-05-18
Hi All, I have been a ubuntu user for sometime but i'm unable to get the info i need in order to complete my project / Task, i'm looking to create a cd that contains an encrypted squashfs that would be decrypted at boot time and load up the o/s 

I have added the packages to allow encfs and have considered going two ways with the encryption , making a squashfs that contains each file encrypted seperatly or the squashfs file it's self being encrypted, i'm thinking the latter is the better, i run a mksquash but it seemed inviting for people to try and crack it & messy to look at. 

I have created the encrypted squash but need to know a few things 

I'm guessing i need to add the encfs support to initrd.gz so its able to decrypt the squash if so i need to rebuild the initrd.gz with that support and dependancies - how to ?

Where would i find the script that mounts the squash as i will need to tweak the path to include the mounting of the encfs encrypted file(squash) and then pointing to the decrypted squash.

does this make sense to everyone ?

---

### Post by dstempfley on 2009-05-19
If I understand what your asking.  You are modifying the system to support encfs file systems on boot and need to modify the code that mounts the file system to include support for the new mount procedure.

I'm certainly no expert.  I'm struggling with a different but related problem.  But here's a few things.

You will need to extract the files in initr.gz:
   mkdir extdir
   cd extdir
   zcat $pathtoinit/initrd.gz | cpio -iv


Make sure add the modules you need in the etc/modules

The mounting procedures are found in scripts/casper scripts/casper-helpers
and other related scripts.

Good luck.

/Dion

---

### Post by [3w`Sparky] on 2009-05-20
thanks for that you understood correctly, i shall have alook at this in a day or two and get back to you.

---

### Post by [3w`Sparky] on 2009-05-20
I have added all the dependencies, if i boot into the initfs prompt without loading the squash i can run the command encfs from the shell and it lists the help assuming i made a type so that looks to be functioning as required. 

I'm making a Help Request for someone that has spent many months locked inside of a initrd.gz file and knows there way around it, i have looked through many files within the scripts directory but have had no joy in finding anything that looks to be mounting the squashfs file, does anyone have any ideas what file i need to look at and / or line number range ?

many thanks

---

### Post by uljanow on 2009-05-20
There's a fork of casper named live-helper in Debian which supports encrypted squashfs images.

---

### Post by dstempfley on 2009-05-20
Just a few observations I've found.  I'm still working with this myself.

Looking in /scripts/casper and /scripts/casper-helper  A call tree looks like this:

     mount_images_in_directory() -> setup_unionfs()

In setup_unionfs() is a loop that searches the /cdrom/casper directory for squashfs files and mounts them.  

Hope that helps.

/Dion

---

### Post by [3w`Sparky] on 2009-05-21
I have Been looking at a file called casper quite large in size, 


around line 466 i have been looking at commands as follows 

fstype=$(get_fstype "${devname}")
    if is_supported_fs ${fstype}; then
        mount -t ${fstype} -o ro,noatime "${devname}" $mountpoint || continue
        if is_casper_path $mountpoint && \
           ([ "$skip_uuid_check" ] || matches_uuid $mountpoint); then
            echo $mountpoint
            return 0
        else
            umount $mountpoint
        fi

i have tried the following but with no luck , i'm really struggling with this at the mo as there are loads of $ references

fstype=$(get_fstype "${devname}")
    if is_supported_fs ${fstype}; then
mkdir clean
encfs ${devname} clean
echo ****************************************************************
        mount -t ${fstype} -o ro,noatime "clean" $mountpoint || continue
        if is_casper_path $mountpoint && \
           ([ "$skip_uuid_check" ] || matches_uuid $mountpoint); then
            echo $mountpoint
            return 0
        else
            umount $mountpoint
        fi


but it just keeps showing an error of cdrom_id[number]: main: no device
after about 40 of these it drops to the BusyBox Prompt 

is the code i edited being run at the time of the error showing as i never see my echo command and was wondering if there is a something i can pass at the boot menu to show everything that is taking place?

---

### Post by dstempfley on 2009-05-21
The place you are adding the code is probably not where you want it.

You are modifying the check_dev() function which is called as part of the function that finds the device containing the live media (cdrom, usb flash, etc.).  

You said you wanted an encrypted squashfs. look at the code in the setup_unionfs() function.  You probably want to add your check inside the loop that sets up the backing device.  Another place to look would be in the get_backing_device() function.

/Dion

---

### Post by [3w`Sparky] on 2009-05-26
Before i start hacking at the code I am trying to see where the output is so that i can debug it when it doesn't work. 

I added some echo's to the orginal casper script 

-------------------------------------
    for image_type in "ext2" "squashfs" "dir" ; do
        for image in "${image_directory}"/*."${image_type}"; do
            imagename=$(basename "${image}")
            if [ -d "${image}" ]; then
                # it is a plain directory: do nothing
                rofsstring="${image}=${roopt}:${rofsstring}"
                rofslist="${image} ${rofslist}"
echo "888888888888888888888888888888888888888888888888888888"
echo "image is in plain"
echo "888888888888888888888888888888888888888888888888888888"
            elif [ -f "${image}" ]; then
                backdev=$(get_backing_device "$image")
                fstype=$(get_fstype "${backdev}")

echo "888888888888888888888888888888888888888888888888888888"
echo "image is in image"
echo "888888888888888888888888888888888888888888888888888888"

                if [ "${fstype}" = "unknown" ]; then
                    panic "Unknown file system type on ${backdev} (${image})"

echo "888888888888888888888888888888888888888888888888888888"
echo "image is in unknown"
echo "888888888888888888888888888888888888888888888888888888"
                fi
------------------------------------------------------------------

however i see none of this echo'ed. 

do i have to pass something to the kernel to see the above echo's ?

---

### Post by bmullan on 2009-05-26
> **'[3w`Sparky] said:**
> Hi All, I have been a ubuntu user for sometime but i'm unable to get the info i need in order to complete my project / Task, i'm looking to create a cd that contains an encrypted squashfs that would be decrypted at boot time and load up the o/s 

I have added the packages to allow encfs and have considered going two ways with the encryption , making a squashfs that contains each file encrypted seperatly or the squashfs file it's self being encrypted, i'm thinking the latter is the better, i run a mksquash but it seemed inviting for people to try and crack it & messy to look at. 

I have created the encrypted squash but need to know a few things 

I'm guessing i need to add the encfs support to initrd.gz so its able to decrypt the squash if so i need to rebuild the initrd.gz with that support and dependancies - how to ?

Where would i find the script that mounts the squash as i will need to tweak the path to include the mounting of the encfs encrypted file(squash) and then pointing to the decrypted squash.

does this make sense to everyone ?

If I understand what you are trying to do is

*...create a bootable but encrypted/protected USB or CD *?
 
then I thought this was a good article to read 

**[Linux.com article -- System Administration - Running Debian GNU/Linux from an encrypted USB drive By Avi Rozen on February 19, 2008]("http://www.linux.com/archive/feature/125625")**

see if it helps you with your project.

---

### Post by yogg on 2009-05-27
Hi I also try to create an encrypted live CD.

How  do you get encfs work in the initramfs? I have tried to add encfs and fuse in the /user/share/initramfs-tools/modules config file.

uptadet-initramfs -v -u 

But that seems to be the wrong way, because it does not work :/

Can you please give me a short overview what steps are needed to get encfs work.

@ bmullan
in this link they work with an USB HD. But we need an read only solution ;)  (CD is read only and flash memory has limited write cycles)

---

### Post by [3w`Sparky] on 2009-05-27
the Problem with using something like luks is that it requires a partition to be encrypted , i dont' beleive that this is possible with a CD media, this was the reason for going down the encfs path as it can sit stright onto a cd and will only be readable once encfs decrypts it, this seems a very good if the only solution to encrypt a live bootable cd. 

anybody got any idea's

PS. I added the encfs + Dependencies to the initd.gz 

encfs into the /bin location 

dependencies into the /lib 

your know when it works once your at the initram prompt just type encfs and hit enter 

should give you help not just complain about something being missing

---

### Post by dstempfley on 2009-05-27
> **'[3w`Sparky] said:**
> 
------------------------------------------------------------------

however i see none of this echo'ed. 

do i have to pass something to the kernel to see the above echo's ?


Look in /var/log/casper.log after the system boots.

Also, consider adding "set -x" to the top of the casper script.

/Dion

BTW I wouldn't ignore the suggestions about other existing solutions, but If you keep following this path, I'll help as much as possible.

---

### Post by dstempfley on 2009-05-27
> **'[3w`Sparky] said:**
> the Problem with using something like luks is that it requires a partition to be encrypted , i dont' beleive that this is possible with a CD media, this was the reason for going down the encfs path as it can sit stright onto a cd and will only be readable once encfs decrypts it, this seems a very good if the only solution to encrypt a live bootable cd. 



luks works fine with a loopback filesystem.  So it doesn't have to be an actual encrypted partition.

---

### Post by [3w`Sparky] on 2009-05-28
so your saying i could use luks with the squashfs if i encrypted the squashfs first? 
How would I encrypt the squashfs to luks , the only posts i have found reguarding luks all state that it has to be a seperate partition. 

hmmmmmmmmmmmmm

---

### Post by dstempfley on 2009-05-28
Luks works fine with loopback files, you can pretty much wrap any kind of data in a luks container.  Here is a guide to help you with luks encrypted squashfs. [Compressed and Encrypted Backup with Luks and Squashfs]("http://martin.elwin.com/blog/2008/05/backups-with-squashfs-and-luks/")

---

### Post by yogg on 2009-06-03
I think I have it nearly.

I have changed in initrd.gz /scripts/ the casper script:
function -> mount_images_in_directory() {
```

mkdir /decryptfs
encfs /cdrom/casper/cryptfs /decryptfs

```The encrypted fs lies in ~/work/image/casper/cryptfs (@ live cd = /cdrom/casper/cryptfs)
I also added a symlink 
```

cd ~/work/image/casper
ln -s /decryptfs/filesystem.squashfs filesystem.squashfs

```@ Live CD the link points from /cdrom/casper/filesystem.squashfs to /decryptfs/filesystem.squashfs (so I don't have to change any of the paths in casper/init/... scripts)

This seems to work. If I boot the CD the system hangs at boot (here I have to type in the password "blind" -> the complete standart output is directst to /casper.log -> so I cant see the "please insert your password" text :/ ).

If I type in the wrong password. The boot procedure breaks and I get the initramfs bash (here i can see that /decryptfs is clear). But if I type the right password the system also dies with:
```

run-init: nuking initramfs contents: No such file or directory
[37.516074] Kernel panic - not syncing: Attampted to kill init!

```Anyone an idea how to fix this? The same error accours if I boot from an regular filesystem.squashfs file (no symlink) and only run the mkdir and encfs command. It seems like run-init has problems with the encryped data that is linked to the cdrom.

---

### Post by [3w`Sparky] on 2009-06-04
Sorry I haven't posted recently guy's I fully intend to spend a lot of time on this soon , just tight for time, hoping to get going again tomorrow and most of next week.   will keep you all posted.

---

### Post by [3w`Sparky] on 2009-06-08
Hi , Yogg 

I am trying to get to the same place as you to try and overcome the filesystem not found error , can you attach you casper file so i can compare it to mine.

Cheers

---

### Post by [3w`Sparky] on 2009-06-08
I'm also looking at the luks method posted by DStempfley, this looks hopeful I have got to add the cryptsetup support to the initrd.gz but am trying both methods here. 

i am alittle confused tho , how is the file .img mountung with the cryptsetup command and no mention of the squashfs in the command line , is the file a squashfs or not or what ?

---

### Post by yogg on 2009-06-08
The only thing I have changed is the following function:
```

mount_images_in_directory() {
    directory="$1"
    rootmnt="$2"

    # my changes begin
    mkdir /mymount
    mkdir /mymount/decrypt
    encfs /cdrom/casper/crypt /mymount/decrypt
    # my changes end

    if match_files_in_dir "$directory/casper/*.squashfs" ||
        match_files_in_dir "$directory/casper/*.ext2" ||
        match_files_in_dir "$directory/casper/*.dir"; then
        setup_unionfs "$directory/casper" "$rootmnt"
    else
        :
    fi
}

```And the second important thing is the symlink (initramfs):
```

ls -lsa /cdrom/casper
...
... filesystem.squashfs -> /mymount/decrypt/filesystem.squashfs
...

```For creating the live CD I have used the following link:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

Here I have a /work/image/casper directory
In this directory I have moved the filesystem.squashfs file into the crypt folder (encfs ...) and created the symlink
```

cd /work/image/casper
ln -s /mymount/decrypt/filesystem.squashfs filesystem.squashfs
ls -l
drwx------ 2 user user     4096 2009-06-03 10:23 crypt
-rw-r--r-- 1 root root    14153 2009-05-27 11:50 filesystem.manifest
-rw-r--r-- 1 root root    14094 2009-05-27 11:50 filesystem.manifest-desktop
lrwxrwxrwx 1 user user       27 2009-06-08 11:58 filesystem.squashfs -> /mymount/decrypt/filesystem.squashfs
-rw-r--r-- 1 user user 11853741 2009-06-08 12:43 initrd.gz
-rw-r--r-- 1 user user  2251504 2009-06-03 10:10 vmlinuz

```I hope this will help to get my error :roll:
If not -> ask

---

### Post by [3w`Sparky] on 2009-06-08
Well so far i have failed to get the encfs to work as required, i think i'm struggling with the symbolic links, the o/s wouldn't let me create the link where i wanted so i created it somewhere else then cp it to the location i required, i was questioning if that would work (no longer shown in blue) however when i did a vi on the link it pointed me to the real folder. 

as for the luks method , I managed to get output when booting that method which was complaining about the losetup not being able to loop and check that the kernel has this.

I wonder can this forum support file uploads , maybe we could share out initrd.gz files ?

I have been trying the mounting method's by creating a usb memory stick that has the same structure as the cdrom , boots the o/s fine same as the cd, i have been using this to make the changes as it A saves on CD's and B is much faster.

[http://tigger-and-eric.co.uk/initrd.gz](http://tigger-and-eric.co.uk/initrd.gz)

---

### Post by yogg on 2009-06-09
Thank you for your initrd.gz file. Here is mine

[http://www.file-upload.net/download-1691895/initrd.gz.html](http://www.file-upload.net/download-1691895/initrd.gz.html)

I have also added fusermount to the /bin folder so I can unmount the decrypt folder for some tests.

By the way. Is it possible to make a running system read only? And has maybe someone a tutorial/how to or something else?

---

### Post by [3w`Sparky] on 2009-06-09
I have been working on this again today , unable to generate your error still which is odd as i'm using your initrd.gz file yogg, 

i made sure i have the sym link in the casper folder 

casper --------------filesystem.squashfs   <- (ln -s) reference to /mymount/decrypt

                            crypt ------------------------ filesystem.squashfs <- (encfs squashfs) O/S


odd

it is yet to beat me ! 

interestingly with the luks setup when i hit the initram i can cd /cdrom and it contains all the folders from the cd , but with the encfs it doesn't - wondering if the "is a nice device" bit is saying that this isn't what it was looking for ?

not sure why luks would be happy with that tho? (maybe it's where i placed the cryptsetup "beginging of the casper file"



editing post ~
***********************************
really must go home now , but 

i thought i had encfs the cd , inserted booted and it pointed to the crypt folder inside casper and booted the cd to gui 

cd /mymount/decrypt showed the filesystem.squashfs 

wasn't prompted for a password , guessing because it didn't have one ? 
if so how did it mount the file into decrypt using the encfs command !
***********************************

********** was booting from Hdd instead of cdrom - whoops

---

### Post by [3w`Sparky] on 2009-06-10
question , does fat or more importantly cdfs support placing symbolic links on its file structure ? 

is this why there is a file not found?

---

### Post by [3w`Sparky] on 2009-06-12
Hi all , it seems all have given up with this , well i think i have almost cracked this, i can boot the cd if i use initrd25enc.gz " see link " it will boot to busybox and crap out , if i cd /cdrom it has mounted the cd which is handy , if i then run modprobe fuse and then type the command that is in the casper file "encfs -o nonempty /cdrom/casper /eclear it will prompt for my password if i enter it then cd to /eclear it even shows the decrypted files. 

I have made a couple of tweaks to do what i thought was required to fix it , however it now sits at booting stage loop: module loaded "i thought it was awaiting the password" but it seems it's waiting for something else not sure what. 

please see my attached files 

i have moved the initrd.gz into /cdrom this way i could encrypt the casper folder that contains just the filesystem.squashfs and a text file called Status this file has the following text inside it "this file is decrypted" handy when you want to confirm its encryption status 
cat Status 


I am unsure how to get the cd to look for the kernel & inited.gz under /cdrom rather than /cdrom/casper so in the boot menu you have to press f6 and remove casper from the path. and the kernel is copied to the casper folder once its encrypted and unmounted (boggie) 

SO SO close on this one , just a case of finding whats stopping it from booting and getting the /eclear path right for mounting the squashfs. 

[http://tigger-and-eric.co.uk/initrd2.5enc.gz](http://tigger-and-eric.co.uk/initrd2.5enc.gz)
[http://tigger-and-eric.co.uk/initrd2.5benc.gz](http://tigger-and-eric.co.uk/initrd2.5benc.gz)

the fact that once it craps out and you enter the command manually which is successful means it has everything it need apart from someone who knows what there doing with the code better than myself!

---

### Post by yogg on 2009-06-15
No not given up on I only made some other things ^^

Now I have a encrypted live CD, but with the wrong OS (ok its nearly the same :D). I gave live-helper a second chance and found the error why the CD does break down with an error. Only thing to do is download the loop-aes-utils package extract it and add all files to the initrd1.img file.

Now I have an encrypted debian lenny live CD. Next I try to replace the debian filesystem.squashfs file with an ubuntu filesystem. I hope this works without any problems.

---

### Post by [3w`Sparky] on 2009-06-15
are you able to post your inird.gz , even tho its debian based , i would love to have alook at what you have managed to do. 


well done yogg

---

### Post by yogg on 2009-06-16
Here is my initrd file:
[http://www.file-upload.net/download-1705977/initrd1.img.html](http://www.file-upload.net/download-1705977/initrd1.img.html)

Maybe the live-helper link is also use full for you (its to easy with this tool :D)
[http://ram.squat.net/tech/live/encrypted_debian_live.html](http://ram.squat.net/tech/live/encrypted_debian_live.html)

---

### Post by [3w`Sparky] on 2009-06-16
Hi Yogg, 

I downloaded debian as a starting point to test this concept -Debian GNU/Linux 5.0 r0 "Lenny"

I mounted a local HDD for the image to be built on and ran through the guide as per the website, if i then boot off of the memory stick that the image is copied to it works a treat, however if i then move the folders into the existing iso and burn it to cd when i boot from the cd i receive a kernel panic - 

while booting these are the last 3 messages 

list of all partitions: 
no filesystem could mount root, tried:
Kernel panic - no syncing: vfs: unable to mount root fs on unknown-block(104,3) 

it works great from the memory stick tho , have you actually burnt this to a pysical cd and tested it ?

---

### Post by yogg on 2009-06-16
No I only tested it with VirtualBox from an iso file. Have you used the right option?

-b iso   # create an iso9660 image, for CD
-b usb-hdd   # create an image for USB keys or HD

But the way to Ubuntu is short. If I only could add the aes-i586 module to the initramfs it would work. I have tested to copy the losetup code (from debian live-helper to casper-helper) and vmlinuz from the debian live CD to mine. My Ubuntu ask for the code and after that it starts up (with a few minor failures :P). But if I try to startx the mouse and keyboard does not work. So I now try to add all needet functions to my initrd.

Have you an idea how I can add the aes module? I have copied the aes-i586 file from /lib/module .... to my initrd but that does not work. Modprobe aes-i586 in initramfs also don't work. Cat /proc/crypto says only the md5 module is loaded. Lsmod does not work in initramfs :(

losetup -e aes256 /dev/loop0 /cdrom/casper/filesystem.squashfs
gives me
ioctl: loop_set_status: invalid argument, requested chiper or key lenght (256 bts) not supported by kernel

---

### Post by [3w`Sparky] on 2009-06-16
I will have alook around for the aes i586 module and adding of it , 

I was looking at going the other direction with this , 

I am going to try a couple of things , 

Moving the squashfs from ubuntu and the linuz to the debian iso and see if the initrd will boot them , and or move both of the above + the scripts folder from the debian initrd to the ubuntu initrd scripts folder. 

my thinking is yeah the kernel might be missing the support but we have already added the encryption methods to the initrd, also you need the right kernel for the squashfs and the two are as a pair, running the kernel from one o/s onto another o/s is going to cause some real issues i beleive.

shame there isn't a casper-helper script builder - that would solve the whole thing simple pimple. 

had a quick play with the above in the last hour , no joy as yet , looking to follow your root yogg if i can't get any joy soon, have you got your initrd.gz working yet ? if so can you post the link.

---

### Post by yogg on 2009-06-18
Ok I have a working Ubuntu live CD :)
I now used luks, because someone told me cryptoloop is not secure (Watermark Attack)

[B]
[SIZE=4]How to:[/SIZE][/B]
Build your own live CD. (I used [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch))
**Install cryptsetup to your live CD**!

Encrypt your filesystem.squashfs:
```

// set count to a value you need for the filesystem.squashfs (take ~50MB more or so for luks header, ...)
dd if=/dev/urandom" of=filesystem bs=1M count=400
sudo losetup /dev/loop0 filesystem
sudo cryptsetup luksFormat -c "aes-cbc-essiv:sha256" /dev/loop0
// YES, Passwd, ...

sudo cryptsetup luksOpen /dev/loop0 luksloop

// now we must use a wourkarount because of
sudo mksqashfs ... /dev/mapper/luksloop -> ends up with an error
see: http://ubuntuforums.org/showthread.php?t=1189797

// workaround (part 1):
sudo mkfs.ext3 /dev/mapper/luksloop
sudo mkdir /mnt/cryptfs
sudo mount /dev/mapper/luksloop /mnt/cryptfs
sudo mv filesystem.squashfs /mnt/cryptfs

sudo umount /mnt/cryptfs
sudo rm -r /mnt/cryptfs // only remove the dir if you no longer need it
sudo cryptsetup luksClose /dev/mapper/luksloop
sudo losetup -d /dev/loop0

// rename the encrypted ext3 filesystem (with the included filesystem.squashfs :/ )
mv filesystem filesystem.squashfs

```So now we must modify the startscript:
unzip the initrd.gz (I used the GUI -> no need for console commands :cool: )
Open scripts/casper-helpers and search for setup_loop()
```

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

        # my changes begin
        # don't know how to load them automatically
        modprobe aes
        modprobe dm-crypt
        modprobe dm-mod
        modprobe sha256
        modprobe cbc
        modprobe blkcipher
        mkdir /mnt

        losetup "$dev" "$fspath"
        echo "Please enter your password (QWERTY layout!)" >&6
        cryptsetup luksOpen "$dev" luksloop >&6

        # workaround (part 2):
        mount -t ext3 /dev/mapper/luksloop /mnt
        dev="$(losetup -f)"
        losetup "$dev" /mnt/filesystem.squashfs
        # my changes end

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

```Now repacking everything (the GUI does not work for this :( )
```

find ./ | cpio -H newc -o > initrd
gzip -c initrd > initrd.gz

```And replace the old initrd.gz

Now create the ISO image (or whatever) and you should have an encrypted live CD (if I have nothing forgotten :D )

My initrd.gz
[http://www.file-upload.net/download-1710345/initrd.gz.html](http://www.file-upload.net/download-1710345/initrd.gz.html)

Hope it works.

---

### Post by [3w`Sparky] on 2009-06-18
tied up with a microwave config at the mo , not the type that cook dinner! 

I will give this ago yogg, if all goes well then i should be running encrypted very soon.  

here is to hoping!

---

### Post by [3w`Sparky] on 2009-06-18
Hi Yogg, 

I followed your guide, made my count=550 as my image is abit bigger. 

done everything as per your guide, but when booting it pauses at mounting filesystem, then kicks out to raminitfs 

cat casper.log says that no filesystem could be found,

I wonder tho - your script creates a dir called /mnt 

if i ls the root of raminitfs it only shows the contents of the initrd.gz file it doesn't show a folder called /mnt 

do you think it's crapping out before it reaches this point ? 
is there a step missing? also if i cd /cdrom that is also blank so its not able to pull anything from the source device. 

i tried my own initrd.gz and your one that i know is a working one as you have managed to crack it.

---

### Post by yogg on 2009-06-19
Its strange sometime in my preview tests /cdrom was also clear.

But make a test.
rename the filesystem.squashfs to something else (filesystem.shashfs.noboot) and start the CD with the original initrd.gz file.

After that you should land in the initramfs. Here you can make some tests.
ls /cdrom -> hopefully not clear
if clear
mount /dev/scd0 /cdrom

No make the same step by step that the script does:

1 load modules:
```

modprobe aes
modprobe dm-crypt
modprobe dm-mod
modprobe sha256
modprobe cbc
modprobe blkcipher 

```

check if the modules are loadet
```

cat /proc/modules | grep aes
cat /proc/modules | grep dm
...

cat /proc/modules | more
does not work in initramfs :(

```

2 create the first loop:
```

// get the first free loop device
losetup -f

// enter what loopsetup -f says
losetup /dev/loop0 /cdrom/casper/filesystem.squashfs.noboot

//should now give you the next device
losetup -f

// you can also test with
cat /dev/loop0
// but this ends with many strange characters and a system hang :D
// strg + c also don't work in my case :/

```

3 decrypt and mount the device:
```

cryptsetup luskOpen /dev/loop0 luksloop
mkdir /mnt
mount /dev/mapper/luksloop -t ext3

ls /mnt
// here you should see the filesystem.squashfs file

```

4 make last loop + mount it:
```

losetup /dev/loop1 /mnt/filesystem.squashfs
mkdir filesystem
mount /dev/loop1 /filesystem -t squashfs

ls /filesystem
// you now should see alle the folders and files (/etc, /dev, /proc, ...)

```

If that works without problems the same way should work in a script. Only the last mount (mount /dev/loop1 /filesystem -t squashfs) is not necessary, the script makes this automatically.

O and don't forget the >&6 in your script after cryptsetup!!!!!!!
If you don't use this a variable will be destroyed and the system does not boot

---

### Post by [3w`Sparky] on 2009-06-19
I think its a kernel issue , your initrd.gz /lib/modules contains 2.6.27-14-generic 

I'm using 2.6.27-7-generic, i can't seem to find the sources to obtain everything your have in the /modules/2.6.27-14-generic/crypto to add the support to my kernel. 

do you think squashing the -14 kernel onto the cd might work ?

i also am unable to find the any source to remove the following error when trying to do a luksFormat

command failed: Failed to setup dm-crypt key mapping.
check kernel for support for the aes-cbc-essiv:sha256 cipher spec and verify that the /dev/loop1 contains at least 133 sectors

---

### Post by [3w`Sparky] on 2009-06-19
Yogg , are you using mini ubuntu by chance ?

---

### Post by yogg on 2009-06-23
> **'[3w`Sparky] said:**
> 
check kernel for support for the aes-cbc-essiv:sha256 cipher spec and verify that the /dev/loop1 contains at least 133 sectors

Looks like a module is missing. Which output you get from "cat /proc/modules | grep ..." ?

Is there a howto or something else for an mini Ubuntu live CD/DVD? Sounds interesting.

---

### Post by [3w`Sparky] on 2009-06-23
[http://www.crealabs.it/ubuntu-mini-remix/](http://www.crealabs.it/ubuntu-mini-remix/)

 this is the mini ubuntu 

about 180MB i think from memory , I'm not sure what it's lacking to squeeze it down to that size, office org bits but unsure what else. 

I am stuck back on microwave at the mo but will have another battle with that blooming CD before next week. 

cheers for all your help so far though yoggs

does this forum have a magic star rating or something (bit like tek-tips)

---

### Post by teh_drizzle on 2009-07-02
> **yogg said:**
> I think I have it nearly.

I have changed in initrd.gz /scripts/ the casper script:
function -> mount_images_in_directory() {
```

mkdir /decryptfs
encfs /cdrom/casper/cryptfs /decryptfs

```The encrypted fs lies in ~/work/image/casper/cryptfs (@ live cd = /cdrom/casper/cryptfs)
I also added a symlink 
```

cd ~/work/image/casper
ln -s /decryptfs/filesystem.squashfs filesystem.squashfs

```@ Live CD the link points from /cdrom/casper/filesystem.squashfs to /decryptfs/filesystem.squashfs (so I don't have to change any of the paths in casper/init/... scripts)

This seems to work. If I boot the CD the system hangs at boot (here I have to type in the password "blind" -> the complete standart output is directst to /casper.log -> so I cant see the "please insert your password" text :/ ).

If I type in the wrong password. The boot procedure breaks and I get the initramfs bash (here i can see that /decryptfs is clear). But if I type the right password the system also dies with:
```

run-init: nuking initramfs contents: No such file or directory
[37.516074] Kernel panic - not syncing: Attampted to kill init!

```Anyone an idea how to fix this? The same error accours if I boot from an regular filesystem.squashfs file (no symlink) and only run the mkdir and encfs command. It seems like run-init has problems with the encryped data that is linked to the cdrom.

Hey yogg,

I followed your instructions for the LUKS setup and I'm experiencing the same issues you experienced with the kernel [panicing] (before you tried LUKS XD) when run-init tries to nuke the contents of initramfs.

I've seen a few patches to eliminate the panic if run-init fails to remove all files, but they have been for debian and I have not had time to look for an Ubuntu equivalent.  

If anyone was able to solve this issue, please let me know :P

I'll be back next week with more testing results. 

Thanks!

---

### Post by [3w`Sparky] on 2009-07-06
It might be worth Posting / Hosting the Kernel and init.rd ? 

we can all pretty much get the orginal cd to customize but its the kernel support and init.rd config thats the issue. 

anyone have an FTP server ?

---

### Post by teh_drizzle on 2009-07-06
I actually figured it out.

It seems to be an issue with run-init trying to nuke mounts that exist within sub directories.

I was trying to be creative and had mounted the encrypted image to /mnt/encrypt, then I'd mount the squashfs from /mnt/encrypt/filesystem.squashfs to /filesystem.squashfs. 

When I changed the mount point to just /mnt (like yogg did in his example script) it worked just fine. :)

Here's an old bug report which helped me solve the problem:
[https://bugs.launchpad.net/ubuntu/+source/klibc/+bug/31762](https://bugs.launchpad.net/ubuntu/+source/klibc/+bug/31762)

Thanks for your help! :p

---

### Post by adamliq on 2010-03-13
Hi I am trying to do a similar concept but I want to try it with a usb stick.  I have been using the link [http://forums.remote-exploit.org/backtrack-4-howto/25768-howto-bt4-pre-final-usb-encryption.html](http://forums.remote-exploit.org/backtrack-4-howto/25768-howto-bt4-pre-final-usb-encryption.html).
Essentially I want to boot a USB stick with a squashFS and the SquashFS has been encrypted with Luks.
I am using Ubuntu and not BT4.

---

### Post by bodhi.zazen on 2010-03-13
> **adamliq said:**
> Hi I am trying to do a similar concept but I want to try it with a usb stick.  I have been using the link [http://forums.remote-exploit.org/backtrack-4-howto/25768-howto-bt4-pre-final-usb-encryption.html](http://forums.remote-exploit.org/backtrack-4-howto/25768-howto-bt4-pre-final-usb-encryption.html).
Essentially I want to boot a USB stick with a squashFS and the SquashFS has been encrypted with Luks.
I am using Ubuntu and not BT4.

If you first make a live CD as the post above yours suggests, you would then put it on a usb with unetbootin.

Personally, I would simply just make an encrypted data partition rather then encrypting the entire install.

---

### Post by adamliq on 2010-03-13
Hi created bootable linux with unetbootin however. Typed live from selection menu Showed Ubuntu Loading symbol for 6 minutes Then black screen with flashing white cursor.  I dont know what the error or problem is seeing as it doesnt display anything.  Is there any way to have it boot in verbose displaying all actions rather than displaying ubuntu load screen and not tell me what its doing.

---

### Post by [3w`Sparky] on 2010-04-22
just put nosplash at the end of the boot commnds

---

### Post by tjbradford on 2011-05-11
old but bumping for version 11.04

i have had the encrypted CD's working on version 8 and 9 of ubuntu but on version 11.04 im having issues

here is what i did 

extracted the contents of the initrd from the cd

gzip -dc /cdrom/casper/initrd.gz | cpio -i

edited the casper-helper by adding > 

        modprobe aes
        modprobe dm-crypt
        modprobe dm-mod
        modprobe sha256
        modprobe cbc
        modprobe blkcipher
        mkdir /mnt

        losetup "$dev" "$fspath"
        echo "Please enter the decryption password" >&6
        cryptsetup luksOpen "$dev" luksloop >&6


        mount -t ext3 /dev/mapper/luksloop /mnt
        dev="$(losetup -f)"
        losetup "$dev" /mnt/filesystem.squashfs


saved the above and repackaged using the following 

find ./ | cpio -H newc -o > initrd
gzip -c initrd > initrd.gz

add the initrd.gz file to the iso image where the encrypted filesystem.squashfs is already inplace

boot the iso via vm at the boot menu i remove quiet and splash so i can see whats happening and view the password prompt. 

below is the output 
>
please enter the decryption password
Enter passphrase for /dev/loop0: 
<

it then just sits there no matter what i type or do press rtn etc. 

seems like it won't pass the input across , i tried removing the >&6 from both above statements to see if it would input in clear text but still no joy. 

any ideas whats changed anybody ?

---

### Post by tjbradford on 2011-05-12
ok the story so far. 

I believe this to be some sort of security improvement or just keyboard input not processed at that point.

basically I replaced the cryptsetup luksOpen  command and added a keyfile inplace of the password, this then processes and mounts fine and continues to boot to gui 

this means that the code is good the initrd.gz is good pointing the finger at a problem with keyboard input. 


anyone aware of changes to the point of keyboard support being enabled with the initrd.gz ?

---

### Post by tjbradford on 2011-05-12
it seems that plymouth is the problem here 

if i edit /init-top/plymouth and remove /bin/plymough show-splash 

it then boots, you dont see any services starting nor do you have any output echo'ed but if you guess its waiting for the password and enter it, then it continues and boots. 

ideas on how to get some nice echo out of it still tho ? 

screw any splash screens just echo and OK's during boot is all im after

---

