---
title: "Custom 12.04 LTS live cd using chroot. :)"
date: 2013-05-02
forum: Tutorials
---

### Post by joshuariley on 2013-05-02
I created a custom live cd of 12.04 using chroot for my linux class and wanted to share in the hopes of helping someone in the future that may have questions. I did my best to create this as easy as I possibly could so almost any skill level can hop on and follow along. 

   **Creating a customized Live Ubuntu 12.04 LTS CD. ** 
 

 I removed everything except english from the language packs.  
 Update all software to be current as of April 30 2013.  
 Enable universe and multiverse repositories.  
 Added network tools such as traceroute, wireshark, kismet, iptraf.  
 Include Firefox with flash-nonfree plugin, mp3 support VLC and divx.  
 Include ndiswrapper support (Wireless support for my RTL8187)  
 

 Let's do it.  
 1. Download the current Ubuntu Precise pangolin 12.04 LTS Live CD image. Mine was saved to my Desktop just as ubuntu.iso.   
   
 Using terminal add squashfs-tools to be able to rebuild the custom squashfs.  
 

 **$ sudo apt-get install squashfs-tools ** 
 

 Mount the .iso under /tmp/livecd:  
 **$ mkdir /tmp/livecd ** 
 **$ sudo mount -o loop ~/Desktop/ubuntu.iso /tmp/livecd ** 
 

 **(when it tells you it is mounted as read only, don't freak out. Just continue on and smile.)**
 

 Create a directory for the future CD in ~/livecd and copy the CD content excluding casper/filesystem.squashfs in our ~/livecd/cd directory:  
 

 **$ mkdir ~/livecd ** 
 **$ mkdir ~/livecd/cd ** 
 **$ rsync --exclude=/casper/filesystem.squashfs -a /tmp/livecd/ ~/livecd/cd ** 
 

 This copies all but the squashfs file, which is the compressed file containing our live CD filesystem.  
 

 Next mount casper/filesystem.squashfs into a directory called ~/livecd/squashfs in order to copy its content into a directory where our live CD filesystem will be customized ~/livecd/custom  
 

 **$ mkdir ~/livecd/squashfs ** 
 **$ mkdir ~/livecd/custom ** 
 **$ sudo modprobe squashfs ** 
 **$ sudo mount -t squashfs -o loop /tmp/livecd/casper/filesystem.squashfs ~/livecd/squashfs/ ** 
 **$ sudo cp -a ~/livecd/squashfs/* ~/livecd/custom ** 
 

 Copy /etc/resolv.conf and /etc/hosts to our ~/livecd/custom/etc to enable access to the network from within the image being customized as chroot  
 

 **$ sudo cp /etc/resolv.conf /etc/hosts ~/livecd/custom/etc/ ** 
 

 2. chroot into image being created:  
 

 To customize the image, chroot into ~/livecd/custom directory, mount the necessary pseudo-filesystems (/proc and /sys). Then, customize the Live CD.  
 

 **$ sudo chroot ~/livecd/custom ** 
 **# mount -t proc none /proc/ ** 
 **# mount -t sysfs none /sys/ ** 
 **# export HOME=/root ** 
 

 Let’s customize...  
 

 3. Customizing our future live CD  
 

 Remove unwanted packages  
 

 To see a list of all packages type,  
 

 **# dpkg-query -W --showformat='${Package}\n' | less ** 
 

 I removed non-english language packsas well as gnome-games and libreoffice as I don't use them.  
 

 **# apt-get remove --purge libreoffice-* ** 
 **# apt-get remove --purge `dpkg-query -W --showformat='${Package}\n' | grep language-pack | egrep -v '\-en'` ** 
 **# apt-get remove --purge gnome-games* ** 
 

 Next update the existing image  
 

 Update the /etc/apt/sources.list in order to enable universe and multiverse repos along with precise-updates, partner repos and the precise-security repos.  
 

 Open and edit /etc/apt/sources.list and add repos.  
 

 **# sudo nano /etc/apt/sources.list ** 
 

 *deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted universe multiverse * 
 

 *deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted universe multiverse * 
 

 *deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted universe multiverse * 
 

 *deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted universe multiverse * 
 

 *deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted universe multiverse * 
 

 *deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted universe multiverse * 
 

 *deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner * 
 

 *deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner * 
   
 Now update the image by running  
 

 **# apt-get update ** 
 **# apt-get upgrade ** 
 **# apt-get dist-upgrade ** 
 

 If you have kernel issue warnings, you may also have to sudo rm /etc/kernel/*/zz-update-grub and then apt-get dist-upgrade again.  
 This happened to me and drove me bonkers  
 

 Install any wanted new packages  
 

 **# apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg vlc mplayer mplayer-fonts ** 
 **# /usr/share/doc/libdvdread4/install-css.sh ** 
 **# apt-get install virtualbox ** 
 

 A little extra security with peerguardian as well as some utilities that I consider handy, like networking tools to make wireless work on live cd and firefox plugins.  
 

 **# sudo add-apt-repository ppa:jre-phoenix/ppa ** 
 **# apt-get install rar unrar unace-nonfree mc ** 
 **# apt-get install ndiswrapper-common ndiswrapper-utils-1.9 cabextract unshield iw ** 
 

 **# apt-get install wget wireshark nmap traceroute etherape iptraf ** 
 **# apt-get install flashplugin-installer mozilla-plugin-vlc ** 
 

 

 That’s it for my cd. You can add more packages, or remove packages you don't want on the Live CD.  
 

 4. Cleaning up the chroot  
 

 When we install packages, apt caches them, we will need to remove them in order to save some space:  
 

 **# sudo apt-get clean&&sudo apt-get autoremove ** 
 

 Also, there still are some files in /tmp that need to be removed:  
 

 **# rm -rf /tmp/* ** 
 

 Before chrooting, we added these files: /etc/hosts and /etc/resolv.conf, remove them:  
 

 **# rm -f /etc/hosts /etc/resolv.conf ** 
 

 Clean the older non-used kernels to save space:  
 

 **# dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge ** 
 

 Unmount /proc and /sys  
 Finally, exit the chroot and repack the CD.  
 

 **# umount /proc || umount -lf /proc ** 
 **# umount /sys || umount -lf /sys ** 
 **# exit ** 
 

 Rebuild some manifest files, regenerate the squashfs and recreate the ISO.  
 

 5. Recreating the ISO  
 Recreate the manifest files:  
 

 **$ chmod +w ~/livecd/cd/casper/filesystem.manifest ** 
 **$ sudo chroot ~/livecd/custom dpkg-query -W --showformat='${Package} ${Version}\n' > ~/livecd/cd/casper/filesystem.manifest ** 
 **$ sudo cp ~/livecd/cd/casper/filesystem.manifest ~/livecd/cd/casper/filesystem.manifest-desktop ** 
 

 Regenerate the squashfs file:  

 

 **$ sudo mksquashfs ~/livecd/custom ~/livecd/cd/casper/filesystem.squashfs ** 
 **$ sudo rm ~/livecd/cd/md5sum.txt ** 
 **$ sudo -s ** 
 **# (cd ~/livecd/cd && find . -type f -print0 | xargs -0 md5sum > md5sum.txt) ** 
 

 Create the ISO with the following commands  
 

 **$ cd ~/livecd/cd ** 
 **sudo mkisofs -D -r -V "$IMAGE_NAME" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ../ubuntu-custom.iso . ** 
 

 That's it. All done. Next I'm going to load the Live CD on to my microSD card inside of my android and then use that to load the custom Ubuntu I just created onto a 500gig hard drive. This hard drive I have hidden inside of a still fully functioning Nintendo. This is so I can have a fully functional custom linux setup that I feel is completely secure that no one knows even exists. If the guys who wrote the code for facebook or napster had a pc that was inside a nintendo and they never told anyone, they might not have gotten their code stolen and they could be rich. :)  

If anyone is following along and you have any questions at all feel free to post them and I will respond as soon as possible.

---

### Post by Bucky Ball on 2013-05-02
*Thread moved to **Tutorials & Tips***

Welcome to the forums and well done. Normally people want to know how to do their homework and/or assignment (against forum Code of Conduct) so this is a pleasant change. Thanks for sharing. ;)

---

### Post by nndurj on 2013-09-05
I'm behind proxy so uck didn't work. your method worked like a charm. thanks

---

### Post by Bucky Ball on 2013-09-06
Just reading this again and wondering a Linux From Scratch could inspire an easier variation, or even starting with the mini.iso (which has the base kernel and you add everything else, including desktop, but possibly still have language packs: LFS as far as I know doesn't).

---

### Post by jonesgabriel21 on 2013-09-26
This is good stuff. I just finished adding several repositories as I am now trying to dig deeper into the meat of 12.04 and I am experimenting with xubuntu 12.04 server and this is going to help greatly in making sure that my several hours worth of installing/ uninstalling programs will not be in vain. I decided to break away from the 12.04 desktop UI and installed the overlay of Cinnamon with the backup of xfe as a fall back and the possibilty of making a live cd with these instructions is great. Thanks.

---

