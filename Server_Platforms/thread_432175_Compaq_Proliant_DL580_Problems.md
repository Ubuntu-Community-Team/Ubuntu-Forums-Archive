---
title: "Compaq Proliant DL580 Problems"
date: 2007-05-03
forum: Server Platforms
---

### Post by Dazman85 on 2007-05-03
hey guys,
i have a compaq proliant dl580 and when i try to install ubuntu server 6.06 it wont load into the installer it just give a bug error. with 7.10 it will load the installer but when it gets to partitioning the disk it says it cannot determin the geometer of the disk.
i can install windows 2003 on the machine fine and ipcop has installed and run fine. currently the disk are set on the compaq smartarray to RAID 0 and there are 3 x 18.2gb drive.
also i have tryed booting into ubunut desktop 6.06, 7.10 (6.06 give same error as the server edition, 7.10 get to loading gpm and freezes)
i have also tried a gentoo live disk and sysresccd both get to gpm and again freezees.

has anyone had this problem or know how to fix it?

any help would be great.

cheer
Dazman85

---

### Post by matthewburke on 2007-06-01
I'm curious if you ever came to any resolution. We just recieved a Proliant DL580 and we're getting roughly the same problems from what I have read. Once we get to the partitioning section fo the install using Ubuntu Server 7.10 we get errors that Ubuntu cannot locat the disk(s). Thus far we've come to the conclusion that it's only seeing the the scsi raid controller but nothing beyond that.

Anyone have any tips for me?

-Matthew

---

### Post by obimeister on 2007-06-02
Configure raid in smart array controller bios.

---

### Post by matthewburke on 2007-06-06
We have done that. We are able to install Windows 2003 Server without any problems. From the RAID BIOS we are able to run its disk checking utility and all drives set to RAID 5 (Four drives in total) check out as 'ok'.

I fire the system up with the Ubuntu 7.04 Server install disk in place and all seems well. When I get to the section for setting up the partitions it basically craps out erring: " Unable to determine geometry of file/device. You should not use Parted unless you really know what you're doing!        Warning!        Ignore   Cancel ". When I choose 'Ignore' I get the error: " Failed to partition the selected disks. This probably happened because the selected disk or free space is too small to be automatically partitioned ". Based on the errors we're receiving it sounds to me like the install is viewing the RAID controller as the storage device opposed to the drives connected to the RAID controller. Anyone know how I can get around this.

---

### Post by matthewburke on 2007-06-19
Any thoughts on this yet? I'm at a loss and atm this new...used server is primarily acting as a paper weight. :(

I mean we could put it to use somehow as a Win2k3 server, but we bought it with the intension of creating a new *NIX mail server. I'm boggled that Windoze installs flawlessly and Ubuntu can't even see my storage devices by default.

Thanks again for any help with this.
- Matthew

---

### Post by jaydeel on 2007-06-19
I got it installed!! I’m doing this on Compaq Prolinea ML370, using feisty fawn. But the problems seem exactly similar for any compaq server with the compaq smart array controller.

Since, the problem is a conflict between the compaq smart array and sym53c8xx module. I managed to get the install working by creating a custom install cd image, i modified the initrd.gz and removed the folder for the sym53c8xx_2 module. Recompiled the ISO image, and it's recognizing my compaq smart array RAID. 

Here are the steps I completed.

To create the custom CD…..

Mount the install…

```
mount /dev/scd0 /cdrom
```

Copy the CD.

```
mkdir -p /opt/cd-image
cp -r /cdrom/* /opt/cd-image
cp –r /cdrom/.disk /opt/cd-image

```
Extract the initrd.gz from the cd image

```
mkdir extract
cd extract

zcat /opt/cd-image/install/initrd.gz | cpio -i 
```

Delete the modules in sym53c8xx_2 directory 

```
rm –rf ./extract/lib/modules/2.6.20-15-generic/kernel/drivers/scsi/sym53c8xx_2
```

Repack the modified files.

Cd back to to your extract directory
```

find . | cpio -o --format='newc' |   gzip -9 > ~/initrd.gz.new
```

Put the new file into our CD replacing the old one.

```
cp ~/initrd.gz.new /opt/cd-image/install/initrd.gz
```

Now create the iso image.

```
IMAGE=custom.iso
BUILD=/opt/cd-image/

mkisofs -r -V "Custom Ubuntu Install CD" \
            -cache-inodes \
            -J -l -b isolinux/isolinux.bin \
            -c isolinux/boot.cat -no-emul-boot \
            -boot-load-size 4 -boot-info-table \
            -o $IMAGE $BUILD
```

Burn the image to CD and you should be able to install to your Compaq Smart Array controller.

But, during the installation another kernel is installed and when you reboot you will see “cpqarray: error sending ID controller”

Reboot off your custom install cd, and select the Rescue option. Mount your root partition and execute a shell on it.

(if you have /usr or /var on other partitions you should mount them before continuing)

Now execute the commands 

```
# echo "cpqarray" >> /etc/initramsfs-tools/modules
```

```
# update-initramfs -u
```

After the command finishes, remove the cd, reboot your system and everything should be gravy. 

See my other thread for an ISO of the customized server install cd...

[http://ubuntuforums.org/showthread.php?t=384319&page=2&highlight=compaq+smart+array]("http://ubuntuforums.org/showthread.php?t=384319&page=2&highlight=compaq+smart+array")

References.

[https://help.ubuntu.com/community/InstallCDCustomization]("https://help.ubuntu.com/community/InstallCDCustomization")
[http://www.tundranerd.com/2007/02/14/cpqarray-error-sending-id-controller/]("http://www.tundranerd.com/2007/02/14/cpqarray-error-sending-id-controller/")
[http://www.extremetech.com/article2/0,1697,2132616,00.asp]("http://www.extremetech.com/article2/0,1697,2132616,00.asp")

---

### Post by doggybs on 2007-11-10
Hi.

Thanks jaydeel, that is mega!! works a treat :-)

There was just the one typo in 
'# echo "cpqarray" >> /etc/initramsfs-tools/modules' which had me confused for ages, too many s' in initramfs. he he.

Cheers

---

