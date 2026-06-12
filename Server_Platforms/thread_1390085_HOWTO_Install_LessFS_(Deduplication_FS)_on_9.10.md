---
title: "HOWTO: Install LessFS (Deduplication FS) on 9.10"
date: 2010-01-25
forum: Server Platforms
---

### Post by Bubbel on 2010-01-25
LessFS is a relatively new FS. The primary goal for LessFS is an on-disk backup & archiving filesystem.
Features of LessFS:
- On-line Deduplication
- On-line Compression

LessFS creates a growable file that represents the LessFS filesystem.
My configuration is as follows: 5 Harddisks of varying sizes, concatenated to one disk, using LVM2. The data partition formatted as ext4, with large file option set.
 
I've installed LessFS as follows:

Open a Terminal on your server.

[LIST]Get the prerequisites:
```
sudo apt-get install build-essential libselinux1-dev libsepol1-dev pkg-configlibtokyocabinet-dev checkinstall

```
[*]Get Fuse 2.8.1: download from [https://launchpad.net/ubuntu/+source/fuse/2.8.1-1.1ubuntu2](https://launchpad.net/ubuntu/+source/fuse/2.8.1-1.1ubuntu2) the packages called libfuse, libfuse-dev and fuse-utils. Download the ones that correspond to your architecture.

[*]Install them like this:
```
sudo dpkg -i *.deb

```
assuming the FUSE files are in the same folder as the shell is.
[*]Download & Extract LessFS: Download .tar.gz package from [http://sourceforge.net/projects/lessfs/files/](http://sourceforge.net/projects/lessfs/files/). Extract like
```
tar xzf *.tar.gz

```
Other Option, All-in one (Note: check for the newest version number at wwww.lessfs.com):
```
wget -O- http://sourceforge.net/projects/lessfs/files/lessfs/lessfs-1.0.1/lessfs-1.0.1.tar.gz/download | tar xz

```
[*]cd into lessfs folder and run
```
./configure

```
This gives a lot of text. Check for errors.
[*] Run
```
make && sudo checkinstall

```
[/LIST]
I didn't test checkinstall, so if it fails, replace "checkinstall" with "make install".

You are done installing. Now configuring:

LessFS isn't made natively on Debian/Ubuntu. That is to see in the startup scipt. I tweaked it a bit, but I must say it's a quick-and-dirty hack. The tweaked script is provided as an attachment (lessfs.sh).
Download it and save it to /etc/init.d
Edit the file if you want to change the mountpoint to something other than /data.
Then do:
```

sudo update-rc.d lessfs.sh enable

```
This creates the correct startup scripts. This isn't nessecary. You can always hand-start lessfs.

The next part is important though:
From the lessfs source folder copy the etc/lessfs.cfg file. Copy it to /etc
Then edit the new /etc/lessfs.cfg
change the file paths to your liking (tip: Do the data folder 'dta' as the only one on your large partition. For performance reason)
Alter the cache settings in a way that it fits your memory.

After saving the file, create the mta, dta subfolders at the places you stated above.
Also create the mount point folder.

do the following to create the folder:
```
sudo mklessfs -c /etc/lessfs.cfg

```
And you're done Start Lessfs with:
```
sudo invoke-rc.d lessfs.sh start

```
or restart.

Happy Less-ing ;)

Bubbel :KS

PS: Thanks to PhracturedBlue for filtering out some errors.

---

### Post by PhracturedBlue on 2010-01-31
I’d recommend using ’sudo checkinstall’ rather than ’sudo make install’ generally. It makes it easier to uninstall packages in the future.
I also use x86_64, so those fuse packages didn’t work for me.
I used the lucid ones instead freom here:
[https://launchpad.net/ubuntu/+source/fuse/2.8.1-1.1ubuntu2](https://launchpad.net/ubuntu/+source/fuse/2.8.1-1.1ubuntu2)
which worked fine on Karmic (need libfuse, libfuse-dev, fuse-utils)

I needed this too:
sudo apt-get install libtokyocabinet-dev

After that installation went smoothly.
I didn't find your attachment for auto-starting lessfs, but I don't need that for my use

---

### Post by Bubbel on 2010-02-01
> **PhracturedBlue said:**
> I’d recommend using ’sudo checkinstall’ rather than ’sudo make install’ generally. It makes it easier to uninstall packages in the future.
I also use x86_64, so those fuse packages didn’t work for me.
I used the lucid ones instead from here:
[https://launchpad.net/ubuntu/+source/fuse/2.8.1-1.1ubuntu2](https://launchpad.net/ubuntu/+source/fuse/2.8.1-1.1ubuntu2)
which worked fine on Karmic (need libfuse, libfuse-dev, fuse-utils)

I needed this too:
sudo apt-get install libtokyocabinet-dev

After that installation went smoothly.
I didn't find your attachment for auto-starting lessfs, but I don't need that for my use

Thank you for the info. I will update the howto. Never heard of checkinstall, so I looked it up. Sounds like a really good solution.
Greets, Bubbel

---

### Post by tlsarles on 2010-02-01
We want ZFS! :-p

---

### Post by stefanlasiewski on 2010-02-04
> **tlsarles said:**
> We want ZFS! :-p

Well, unfortunately we aren't going to get it anytime soon, unless you count the FUSE+ZFS hack (It looks amateurish, and I don't think I would trust it).

This LessFS sounds very interesting though, and I'll check it out soon.

I've used deduplication on DataDomains & Netapp and it rocks. Two years worth of 300GB backups in a fraction of the space.

I would love a smaller solution for my home and smaller office systems.

---

### Post by Tidder on 2010-03-28
> **Bubbel said:**
> LessFS isn't made natively on Debian/Ubuntu. That is to see in the startup scipt. I tweaked it a bit, but I must say it's a quick-and-dirty hack. The tweaked script is provided as an attachment (lessfs.sh).
Download it and save it to /etc/init.d
Edit the file if you want to change the mountpoint to something other than /data.
Then do:
```

sudo update-rc.d lessfs.sh enable

```
This creates the correct startup scripts. This isn't nessecary. 
This did not work for me, however this:
```

sudo update-rc.d lessfs.sh defaults

```
did work.

After watching the logs after a few reboots, I've decided that my LessFS stores needed to be started last and stopped first, so I went ahead and set mine using:
```

sudo update-rc.d lessfs.sh defaults 90 10

```
On a default ubuntu install this should make lessfs.sh the last script started on boot, and the first script stopped on shutdown. Otherwise I was experiencing messages in my log of "Lessfs has not been unmounted cleanly. Rollback to..."

Also, your list of apt-get prerequisites needs a space pkg-configlibtokyocabinet-dev.  That threw me off for a few minutes until I found the correct names of the two packages.

---

### Post by epedersen on 2010-06-16
Excellent write up - thank you!  I've been fighting forever trying to compile TokyoCabinet with no success until finally I find that it's already in the repository!

Just a note: libfuse2, libfuse-dev and fuse-utils are also available from the Lucid (10.04) repository.

---

### Post by seshuvvn on 2011-01-19
It was an excellent cheat sheet, but I stumbled on the last step.  Can anyone help me here?   
 
I followed the cheatsheet, downloaded lessfs.sh and successfully did mklessfs step as following:
    
     update-rc.d lessfs.sh defaults
     mklessfs -c /etc/lessfs.cfg
 
     ( I am running as root, so not adding sudo)
 
Then, I ran the following: 
 
      invoke-rc.d lessfs.sh start
 
      I got the following error:
      fuse: mountpoint is not empty
      fuse: if you are sure this is safe, use the 'nonempty' mount option

     I was trying to use same disk for input and output.
       input: /xfs and output: /xfs/dta and /xfs/mta
     So, I changed and created /xfs2.
     mkdir /xfs2, /xfs2/dta, /xfs2/mta
 
     # invoke-rc.d lessfs.sh start
     invoke-rc.d: initscript lessfs.sh, action "start" failed.
 
     So, I ran the individual command as following:
     
# lessfs /etc/lessfs.cfg /xfs  -o 
kernel_cache,negative_timeout=0,entry_timeout=0,attr_timeout=0,use_ino,readdir_ino,default_permissions,allow_other,big_writes,max_read=131072,max_write=131072 

 
It finished in 1 second without any messages, and I see the following: 

# du -sh /xfs 
4,6M 

#du -sh /xfs2 
73M 
#du -sh /xfs/dta 
9.1M 
#du -sh /xfs/mta 
64M 

 
I know that I am testing with a small data just to see if I can run the tool successfully before moving into bigger and more realistic data.     I would expect /xfs2 to be smaller than /xfs, but it is much much bigger. 
Did the tool run successfully?  Why am I seeing results like these?  
And, how do I convert '.tch' files into normal UNIX (xfs) files?
 
I really appreciate your help.   Thanks a lot in advance,
 
Thanks,
- Seshu

---

### Post by seshuvvn on 2011-01-19
It was an excellent cheat sheet, but I stumbled on the last step.  Can anyone help me here?   
 
I followed the cheatsheet, downloaded lessfs.sh and successfully did mklessfs step as following:
    
     update-rc.d lessfs.sh defaults
     mklessfs -c /etc/lessfs.cfg
 
     ( I am running as root, so not adding sudo)
 
Then, I ran the following: 
 
      invoke-rc.d lessfs.sh start
 
      I got the following error:
      fuse: mountpoint is not empty
      fuse: if you are sure this is safe, use the 'nonempty' mount option

     I was trying to use same disk for input and output.
       input: /xfs and output: /xfs/dta and /xfs/mta
     So, I changed and created /xfs2.
     mkdir /xfs2, /xfs2/dta, /xfs2/mta
 
     # invoke-rc.d lessfs.sh start
     invoke-rc.d: initscript lessfs.sh, action "start" failed.
 
     So, I ran the individual command as following:
     
# lessfs /etc/lessfs.cfg /xfs  -o 
kernel_cache,negative_timeout=0,entry_timeout=0,attr_timeout=0,use_ino,readdir_ino,default_permissions,allow_other,big_writes,max_read=131072,max_write=131072 

 
It finished in 1 second without any messages, and I see the following: 

# du -sh /xfs 
4,6M 

#du -sh /xfs2 
73M 
#du -sh /xfs/dta 
9.1M 
#du -sh /xfs/mta 
64M 

 
I know that I am testing with a small data just to see if I can run the tool successfully before moving into bigger and more realistic data.     I would expect /xfs2 to be smaller than /xfs, but it is much much bigger. 
Did the tool run successfully?  Why am I seeing results like these?  
And, how do I convert '.tch' files into normal UNIX (xfs) files?
 
I really appreciate your help.   Thanks a lot in advance,
 
Thanks,
- Seshu

---

### Post by hariprasadmce on 2011-01-21
Excellent how to.

Steps to install mhash (I spent some time here for googling)
---------------------------------------------------------------

Get mhash version 0.9.9.9
wget [http://sourceforge.net/projects/mhash/files/mhash/0.9.9.9/mhash-0.9.9.9.tar.bz2](http://sourceforge.net/projects/mhash/files/mhash/0.9.9.9/mhash-0.9.9.9.tar.bz2)

Extract 
tar -xjvf mhash-0.9.9.9.tar.bz2

change the dir to extracted folder of the above step

./configure

make

Installation

sudo make install


Steps to install fuse (again i spent some time with google)
-----------------------------------------------------------

Download
wget [https://launchpad.net/ubuntu/+archive/primary/+files/fuse_2.8.1.orig.tar.gz](https://launchpad.net/ubuntu/+archive/primary/+files/fuse_2.8.1.orig.tar.gz)

Extract
tar -xzvf fuse_2.8.1.orig.tar.gz

Change the dir to the folder extracted

./configure
make
sudo make install

---

