---
title: "Selective persistence, optional user session and more with Ubuntu live CD"
date: 2015-08-24
forum: Ubuntu, Linux and OS Chat
---

### Post by Robin_Singh on 2015-08-24
I have pieced together some things which lets you use ubuntu sd as a portable and secure workstation with selective persistence. IMHO think it is a convenient option for journalists and educators.

It lets you boot into -

1. Standard read only state, OR
2. A state with custom install in which you have the option to save the system state if you are happy with it. 

When you boot in the custom state, you have the option to -

a. Load saved user data (browser session etc.) from a truecrypt volume
b. Start fresh user session

**HOW-TO**

First and foremost, I used gparted to partition my 8GB micro sd into 3 partitions -

1. Primary FAT32 partition called DATA. I use this to download any file and this is the only partition visible if I plug it into my windows machine (or android phone), so I can access my downloaded files on any system without exposing my OS partition. Also, I can use this to have "portable apps" on this.
2. Primary FAT32 partition called OS (flagged bootable) where I will install Ubuntu using "startup disk creator". For some reason, if this is ext2, startup disk creator does not see it.
3. Primary EXT2 partition so if I need to install wine or dropbox, I can. Dropbox-dist script needs to be executable and FAT32 does not have attributes.  I can also use this partition to keep some portable linux utils.

Once I installed Ubuntu on OS partition using startup disk creator with no persistence option. I plugged the sd into my current system and this is what I did roughly -


1. Modify /syslinux/txt.cfg
```

nano  /media/os/syslinux/txt.cfg

```

and replace top five lines with -

```

default live-splabel live-sp
  menu label ^Ubuntu (custom state, writeable area, optionally save state) 
  kernel /casper/vmlinuz
  append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper showmounts persistent initrd=/casper/initrd.lz splash --
label live
  menu label ^Ubuntu (fresh, NO writeable area)
  kernel /casper/vmlinuz
  append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz splash --

```

2. Modify the casper-snapshot script that comes with the install. To do this, we have to edit it's copy in /casper/filesystem.squashfs

```

cd 
mkdir squash
sudo mount -o loop /media/os/casper/

```

find this code block and comment it out

```

if [ ! -L /home/$USERNAME/Desktop/casper-snapshot ]; then
            ln -s "${MOUNTP}" /home/$USERNAME/Desktop/casper-snapshot
fi

```



find this line 
```

REAL_DIM="`expr ${DU_DIM} + ${DU_DIM} / 20`" # Just 5% more to be sure, need something more sophistcated here...

```

and add this below it

```

echo $REAL_DIM;
echo $COW;
DEST=$SNAP_OUTPUT;    
echo $DEST;

```

save the file and unmount the volume

```

umount -l ~/squash

```

3. Use your sd/usb to boot now and use the custom-state option

4. Once into the system, connect to a network

5. Install [COLOR=#000000][FONT=Arial]genext2fs 

6. Download truecrypt binary in your home dir. Run it and create a truecrypt volume as /media/data/userdata[/FONT][/COLOR]

7. Create a shell script for system startup

```

nano ~/startup.sh

```
--
```

#!/bin/bash


fnReturnFunction()
{
        unlink ~/Desktop/casper-snapshot
    sudo rm -f ~/Desktop/ubiquity-gtkui.desktop
    
    VL=$((zenity --entry --title="Load user data" --hide-text --text="$1" --width=100 --height=6)2>&1)


    if [ -n "$VL" ]; then
        output=`~/truecrypt -t --non-interactive /media/data/[COLOR=#000000][FONT=Arial]userdata[/FONT][/COLOR] --slot=10 --password=$VL 2>&1`
        if [ -n "$output" ]; then
            #echo $output
            $(fnReturnFunction "Enter your truecrypt password to load user data, or press cancel to start fresh.")
        else
            # livecd blanks out the password, even if we write pwd to shadow- and shadow b4 saving state!    
            sudo cp /etc/shadow- /etc/shadow            
            
            rm -rf ~
            ln -fs /media/truecrypt10/home/$USER ~
        
            sudo rm -rf /etc/NetworkManager/system-connections 
            sudo ln -fs /media/truecrypt10/etc/NetworkManager/system-connections /etc/NetworkManager/system-connections 


            sudo service network-manager restart
            
        fi
    fi
}
echo $(fnReturnFunction "Enter your truecrypt password to load user data, or press cancel to start fresh.")

```
--
```

chmod +x ~/startup.sh

```


8. Lets make sure startup.sh is set to start on system start

```

[COLOR=#111111][FONT=Consolas]nano ~/.config/autostart/startup.sh.desktop[/FONT][/COLOR]

```
--
```

[Desktop Entry]
Type=Application
Exec=/home/ubuntu/startup.sh
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=startup
Name=startup
Comment[en_US]=startup script
Comment=startup script

```

9. Lets ensure we have a way to save the system state

```

nano ~/save-state.sh

```
--
```

#!/bin/sh


echo "You can do 'watch ls -l /cdrom/casper-sn*' to monitor progress."


sudo rm -rf /tmp/*
sudo rm -rf /var/log/*
sudo rm -rf /var/tmp/*
sudo rm -rf ~/.cache/*
sudo rm -rf /cow/tmp/*
sudo rm -rf /var/crash/*
sudo mv /var/cache/apt /tmp/
sudo rm -rf /var/cache/*
sudo mv /tmp/apt /var/cache/




# unlink as startup process otherwise complains about this already existing
sudo unlink /etc/NetworkManager/system-connections
sudo unlink /cow/etc/NetworkManager/system-connections


# unlink so system is usable even without running the startup script
unlink ~


# so if passwd has been changed, we update the - files that have come in the livecd (we use them too now, see the startup script)
sudo cp /etc/shadow /etc/shadow- 


# to save space, first overwrite the old older file
sudo mv /cdrom/casper-sn  /cdrom/casper-sn-old
sudo casper-snapshot -t ext2 -o /cdrom/casper-sn.ext2


# !!! should only do this if the above command succeded! 
sudo mv /cdrom/casper-sn.ext2 /cdrom/casper-sn


# relink
sudo ln -fs /media/truecrypt10/etc/NetworkManager/system-connections /etc/NetworkManager/system-connections


# relink
ln -fs /media/truecrypt10/home/$USER ~



```
--
```

chmod +x ~/save-state.sh

```


10. Set your password, save the state and reboot!

```

passwd
~/save-state.sh
sudo reboot now

```





I had to do a bit of finaggling for the screen to lock in the custom state and for wine and dropbox to work smoothly. I have not added any information about that here to keep this as simple as possible. 

If there is a way that this all process can be simplified so people can turn their out of the box usb install into this, I will like to learn about it. I am mostly into animal welfare and new to tinkering with linux but am very excited about it.

---

### Post by sudodus on 2015-08-25
Welcome to the Ubuntu Forums :-)

Is it important for you to get encrypted persistance or are you just doing this for fun? I guess you know that there are standard tools that make persistent live systems without encryption.

Now you have a working system, which is good, but remember to backup your system, because pendrives can fail without warning.

If you want people to use your system, I think you need to describe also the 'finaggling', or provide an easy fix for it (for example a script). And be aware that it is very difficult to develop and test an encrypted system, and to close all known security holes. An adversary might have time and money to buy experts to decrypt the information.

An alternative that works in many cases is to ***install*** an Ubuntu family system, for example Lubuntu which is small and light (using less cpu and less RAM compared to standard Ubuntu. Such an installed system will consider a USB drive like an internal drive, and typical things that can cause problems are drivers for graphics and wifi. Avoid proprietary drivers if you want portability between computers.

And finally, when you install Lubuntu, you can install it with 'encrypted disk', which uses encrypted LVM partitions. It is one of the options in the installer, so it is rather easy to create.

If you need extreme security, you should consider ***[SIZE=3]tails[/SIZE]***.

See also the sticky threads at our [Security Forum](http://ubuntuforums.org/forumdisplay.php?f=338) and [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by Robin_Singh on 2015-08-29
Thanks for your response. I have tried ***tails ***and also the ***install*** option of ***Lubuntu ***(and Ubuntu) but they do not not have the feature I need. I needed persistence to be "selective". So instead of making the changes permanent as I am installing and uninstalling things, I wanted the ability to save the state *only* if I am happy with it, which is handy when I am letting students play with Ubuntu. This also gives me an option to *version control *my system state easily by saving a copy of casper-cn file. I can even have a few depending on whether I am teaching a programming class or graphic design class. Another benefit of not using an install is that this method reduces the writes on the USB.

The other aspect is the user data. Having it encrypted is not for super high security, but just to protect from misuse in case the drive is lost. As an additional benefit, user data can easily be backed up by just copying one file (the truecrypt volume).

Since there is no part of the system encrypted, there is nothing to test. The only things being written to the encrypted volume is what would have been written to home.

I will provide the steps I took to implement a screen lock ASAP for anyone who is interested.

---

### Post by sudodus on 2015-08-29
I see your point and I agree that the encryption you use is OK to protect against a casual intruder :-)

---

