---
title: "Off-line Ubuntu/Linux"
date: 2010-12-08
forum: The Cafe
---

### Post by zer010 on 2010-12-08
This is something that has bugged me about Ubuntu, and to an extent, Linux in general. There is an assumption that EVERYONE has unfettered access to internet these days.  While more people are online now than ever before, there is still a large population of people that either don't have internet, or have very limited access through other's computers. 
In discussing this, I've heard so many people talk about APTonCD and Keryx, but let's face it, these are hardly ideal.  APTonCD requires that the downloading computer runs the same version that the install computer uses, if there is such a computer at all.  Next, Keryx assumes that you will be able to install it on someone's Win* computer. These users are already scared of anything new and hardly lend themselves as benefactors especially if it is a Public Library that keeps their computers on constant lock-down denying even USB or CD access.  
Some argue that .debs are the way to go but sometimes they do not include all of the dependencies and the same goes with compiling as they can require tools that aren't available for an off-line PC. 
So I ask, what is the ultimate solution for those that are stuck with an off-line PC?

---

### Post by Sub101 on 2010-12-08
Almost every OS runs under the same assumption.

In general, with an offline pc most updates are not important as they tend to be security based.

However, as you say the main issue is regarding installing new applications, where the only options really are, like you say, aptoncd and the like.

I assume you have read this page but will post just in case - [https://help.ubuntu.com/10.10/add-applications/C/offline.html](https://help.ubuntu.com/10.10/add-applications/C/offline.html)

---

### Post by KIAaze on 2010-12-08
You already mentioned AptOnCD and Keryx, but I'll add a link listing all solutions I know of at the moment: [https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)

> 
So I ask, what is the ultimate solution for those that are stuck with an off-line PC? 
It is almost impossible to give users access to all the software offered on the internet if they have no internet access.

However, having installation CDs/DVDs with almost all (if not all) packages available in the repositories is doable (AptOnCD) and a good solution.

DVDs are already available for Ubuntu, but I don't know if they contain all repository packages:
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#dvd](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#dvd)

Debian has always had lots of CDs/DVDs to download:
[http://cdimage.debian.org/debian-cd/5.0.7/i386/iso-cd/](http://cdimage.debian.org/debian-cd/5.0.7/i386/iso-cd/)
Same thing, I have no idea if they give access to the full repo.

Of course, if no internet is available locally, the CDs/DVDs will have to be downloaded and burned somewhere else and then sent/transported to the offline location.

So the basic principle remains the same as for Keryx&co: get packages at online location (or source/creation location) and install them at offline location.

Customized GNU/Linux distributions are doable and I think it should be possible to create installation media with all necessary programs for an offline location with specific needs.

Did you have any specific example in mind?

---

### Post by inobe on 2010-12-08
i seen a tutorial in tutorials and tips section of this forum on howto make a repo dvd/ dvd's

---

### Post by grahammechanical on 2010-12-08
I got my first version of Ubuntu through a CD/DVD that was given away by a Linux computer magazine. I updated Ubuntu every six months when the magazine included it on its free DVD. Programs were also included. I was always about 2months behind because it took the magazine a couple of months to put the latest distribution on its DVD. Other Distros were distributed in this way. I only had dial-up at the time and I could not afford the cost of long downloads

Regards.

---

### Post by zer010 on 2010-12-08
I only really bring this up because I have faced these challenges at one time when I first got into Ubuntu with Jaunty.  My friend didn't trust anything I wanted to install on his PC so he wouldn't even entertain the idea of running Ubuntu in any form and the local Library is very restrictive as far as "access".  At the time, I would get new Win* software from a magazine(MaximumPC) easily picked up from the local department store and from downloads from my suspicious friend.  Strangely, as long as the downloads were for Win*, he thought they were ok, if I explained their value. 
As you can see, for a beginner in Ubuntu with VERY limited access to the net, getting a good system up and running can be a daunting task.

---

### Post by zer010 on 2010-12-08
I'm actually thinking of creating a spin-off with all the  necessary tools to compile most programs and include the top 100 or so extra dependencies. However, I understand that it may be a futile effort considering how fast things change in the Linux world....

---

### Post by zer010 on 2010-12-08
I do wish that CDs and DVDs of repos were more readily available, but few newcomers are even aware of the publications that offer these.  Advertising these would do a great service towards making Linux more available to more people.

---

### Post by themarker0 on 2010-12-08
> **zer010 said:**
> I do wish that CDs and DVDs of repos were more readily available, but few newcomers are even aware of the publications that offer these.  Advertising these would do a great service towards making Linux more available to more people.

This. A yearly repo CD i wouldn't mind buying, having the latest STABLE release of each program on them.

---

### Post by Khakilang on 2010-12-09
I face the same problem with 8.10. When I try to install program from a Linux magazine it require some dependencies. So I went to an on line computer to download what is require but it end up removing some dependencies and eventually broke it. Installing those program is not as straight forward as Windows. So I had to wait for my internet before I switch to Linux. I was wondering whether they have program in .deb so we can just download and press install much like the .exe?

---

### Post by Rizwanm on 2010-12-09
Hey really i had lot of question in my mind regarding Ubuntu and linux i registered in this forum and for all my question i got answer .... 
Thank u guys ......:)

---

### Post by cascade9 on 2010-12-09
> **KIAaze said:**
> DVDs are already available for Ubuntu, but I don't know if they contain all repository packages:
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#dvd](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#dvd)

Debian has always had lots of CDs/DVDs to download:
[http://cdimage.debian.org/debian-cd/5.0.7/i386/iso-cd/](http://cdimage.debian.org/debian-cd/5.0.7/i386/iso-cd/)
Same thing, I have no idea if they give access to the full repo.

Of course, if no internet is available locally, the CDs/DVDs will have to be downloaded and burned somewhere else and then sent/transported to the offline location.


AFAIK, the ubuntu DVD doesnt have all the repos (not even close!), the debian CDs/DVDs do...well, if you want to dl all 5 DVDs or 30 CDs. 

I ran debian offline for ages, using 2 DVDs I copied from a freinds linux magazine (cant recall which one). I found that those 2 DVDs gave me everything I wanted (even though I was very new at the time and playing with every media player, etc I could find). Well, apart from the nvidia drivers, I had to d/l them manually.

---

### Post by johntaylor1887 on 2010-12-09
Try Ultimate Edition. It comes with just about every major app there is, and then some.

---

### Post by theraje on 2010-12-09
Have you guys by any chance looked at on-disk.com? They will ship DVD sets of the entire Ubuntu repositories. They have the repos for the previous several releases of Ubuntu on DVD.

---

### Post by amsterdamharu on 2010-12-09
As for the question why programs cannot be as simple as windows lies in the way Linux programs work. They usually perform a simple task and rely on other projects/programs maintained by other groups to function.

For example winff doesn't do anything but create commands to be executed by ffmpeg so it will be useless without ffmpeg. Then ffmpeg depends on libraries to encode/decode media files, without it it would not be of much use.

As to why winff doesn't come bundled with all the dependencies is because they don't know what dependencies you already satisfy. They could bundle all of it but it will make some programs unnecessary large and a real pain to maintain.

I've made a re-spin of Mint 8 to include some software I like and update it completely then ran it off a usb (would not fit on a CD anymore). Here are the basic commands I used:
```

# installed squashfs-tools  first
# copy filesystem.squashfs to ~/temp/sqfs mount the iso to find that file by right clicking on the iso and use archive mounter
cd ~/temp/sqfs
# the following will take some time
sudo unsquashfs filesystem.squashfs

sudo cp /etc/resolv.conf squashfs-root/etc/
sudo cp /etc/hosts squashfs-root/etc/
sudo mount --bind /dev/ squashfs-root/dev
sudo chroot squashfs-root # squashfs-root is the name of the extracted squashfs root dir
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts
export HOME=/root
export LC_ALL=C
dbus-uuidgen > /var/lib/dbus/machine-id
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

# view packages
dpkg-query -W --showformat='${Installed-Size} ${Package}\n' | sort -nr | less
# remove packages like openoffice.org-core:
# aptitude purge openoffice.org-core
apt-get update
apt-get upgrade
# install any other stuff with apt-get if you want
# Desktop folder and other stuff for all users can be found here /etc/skel/

# when you're done it's time to clean up:
aptitude clean
rm -rf /tmp/* ~/.bash_history
rm /etc/resolv.conf
rm /etc/hosts
rm /var/lib/dbus/machine-id
rm /sbin/initctl
dpkg-divert --rename --remove /sbin/initctl
umount /proc # if this doesn't work try umount -lf /proc
umount /sys
umount /dev/pts
exit
sudo umount squashfs-root/dev
# re create squashfs (squashfs-root is the name of the extracted and changed dir):
# this will take some time
sudo mksquashfs squashfs-root new_filesystem.squashfs # I removed -nolzma at the end because it's an invalid option
sudo chown myUser:myUser new_filesystem.squashfs 

# to test it copy all the cd stuff to ~/cd and replace the origional filesystem.squashfs with your new one new_filesystem.squashfs
# of course remove the new_ bit from the name
# now make an iso file
# you can get isolinux.bin from isolinux and copy that file to ~/cd
# not sure of 10.x still uses isolinux but this worked for Mint 8
mkisofs -pad -l -r -J -v -V "test live" -no-emul-boot -boot-load-size 4 -boot-info-table -b isolinux.bin -hide-rr-moved -o boot.iso cd
# now use VirtualBox to test the iso (virtually boot from the iso)
```

---

