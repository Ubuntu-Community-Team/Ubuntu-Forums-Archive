---
title: "HOWTO: Install LessFS (De-duplicating FS) on 10.04"
date: 2010-06-03
forum: Server Platforms
---

### Post by Bubbel on 2010-06-03
Thumbs up  HOWTO: Install LessFS (De-duplication FileSystem) on 10.04/lucid
LessFS is a relatively new FS. The primary goal for LessFS is an on-disk backup & archiving filesystem.
Features of LessFS:
[LIST]
[*]On-line De-duplication
[*]On-line Compression
[/LIST]
I created a similar howto for the 9.10 version. But time has changed, and so did Ubuntu, as well as my hardware setup. This week it was time to reinstall a fresh OS, with lessfs.

LessFS creates a growable file that represents the LessFS filesystem.
My configuration is as follows: 5 Harddisks of varying sizes, concatenated to two disks/volumes using LVM2. The data partition formatted as btrfs. Although the btrfs is experimental it has a unique advantage to other filesystems and that is the snapshotting feature. I use it to create point-in-time copies of the lessfs filesystem.

I've installed LessFS as follows:

Open a Terminal on your server.

    * Get the prerequisites:
```
sudo apt-get install build-essential libselinux1-dev libsepol1-dev  checkinstall pkg-config libfuse-dev libmhash-dev libtokyocabinet-dev

```
[LIST]
[*]Download & Extract LessFS: Download .tar.gz package from
[http://sourceforge.net/projects/lessfs/files/](http://sourceforge.net/projects/lessfs/files/). Extract like
[/LIST]
```
tar xzf *.tar.gz

```
[LIST]
[*]Other Option, All-in one (Note: check for the newest version number at wwww.lessfs.com):
[/LIST]
```
wget -O- [http://sourceforge.net/projects/lessfs/files/lessfs/lessfs-1.0.8/lessfs-1.0.8.tar.gz/download](http://sourceforge.net/projects/lessfs/files/lessfs/lessfs-1.0.8/lessfs-1.0.8.tar.gz/download) | tar xz

```
[LIST]
[*]cd into lessfs folder and run
[/LIST]
```
./configure

```
This gives a lot of text. Check for errors.
[LIST]
[*]Run
[/LIST]
```
make && sudo checkinstall

```
Checkinstall asks a few trivial questions. The defaults will suffice, mostly.

You are done installing. Now configuring:

** note: The next piece of text needs to be cleaned. Will do that soon. **

LessFS isn't made natively on Debian/Ubuntu. That is to see in the startup scipt. I tweaked it a bit, but I must say it's a quick-and-dirty hack. The tweaked script is provided as an attachment (lessfs.sh).
Download it and save it to /etc/init.d
Edit the file if you want to change the mountpoint to something other than /data.
Then do:
Code:

sudo update-rc.d lessfs.sh enable

This creates the correct startup scripts. This isn't nessecary. You can always hand-start lessfs.

The next part is important though:
From the lessfs source folder copy the etc/lessfs.cfg file. Copy it to /etc
Then edit the new /etc/lessfs.cfg
change the file paths to your liking (tip: Do the data folder 'dta' as the only one on your large partition. For performance reason)
Alter the cache settings in a way that it fits your memory.

After saving the file, create the mta, dta subfolders at the places you stated above.
Also create the mount point folder.

do the following to create the folder:
Code:

sudo mklessfs -c /etc/lessfs.cfg

And you're done Start Lessfs with:
Code:

sudo invoke-rc.d lessfs.sh start

or restart.

Happy Less-ing

Bubbel

PS: Thanks to PhracturedBlue for filtering out some errors.

---

### Post by gshalev on 2010-07-02
Hi,
It seems you forgot the attachment.

Thanks,
Guy

---

### Post by tiger74 on 2010-07-15
Thanks for the cool howto.
Now, there is little issue ^^
How do we use it?

I have it mounted under /data
So, we just create another subdirectory like /data/backup
and copy anything we want to save there?

Thanks.

---

### Post by Cocacl on 2011-02-11
"The tweaked script is provided as an attachment (lessfs.sh)."

except there is no attachment.. what are you talking about??

---

### Post by jbcola on 2011-10-15
It's included in the etc folder in the lessfs tar file

---

### Post by Daveski on 2013-03-17
Trying the latest version on 12.04 which seems to have all the dependancies in the repos, but although lessfs compiles and appears to work I have a few weird issues. Anyone running this in 12.04?

---

