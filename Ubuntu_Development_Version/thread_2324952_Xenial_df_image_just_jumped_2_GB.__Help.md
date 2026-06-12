---
title: "Xenial df image just jumped 2 GB.  Help?"
date: 2016-05-17
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2016-05-17
Goofed up.  Downloaded Ubuntu Raspbian for Raspberry Pi3, it's a zip, unzipped, and totally filled up the Xenial partition.
Partition full.
Moved the Raspbian to another partition, deleted the partly unzipped img file, Oops, Xenial still way too big with the Raspbian stuff removed.
Files didn't show any other huge files.
Did:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
 
which recovered somewhat.  df Xenial still 2GB bigger than it was.

Any way to delete some temp file or cache that's gobbling up all that space?  Poked around haven't found anything yet...

Only recourse, install another Xenial.  Went to the ubuntu site, downloaded the xenial .iso from the recommended site, which took 12 hours (!).

Thanks,

BTW, when unzipped, the Ubuntu Raspbian is a 4 gb file to be copied to an SD memory for the Raspberry Pi3..

---

### Post by cariboo on 2016-05-17
Ubuntu seems to be taking up more hard drive space with every releases, I used to be able to get away with a 10GiB / partition, but that is getting to be not quite enough space. I have taken to using 20GiB for Ubuntu on a single partition in vbox, as I was always running out of space. On my regular install on this system, which is the one I use for day-to-day stuff df -h looks like this:

```

df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.6M  1.6G   1% /run
/dev/sda1        96G  5.4G   86G   6% /
tmpfs           7.8G  9.8M  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda2        99M  3.6M   95M   4% /boot/efi
/dev/sdb3       675G  412G  230G  65% /home
tmpfs           1.6G   80K  1.6G   1% /run/user/1000
/dev/sr0        7.7G  7.7G     0 100% /media/cariboo/BUFFY_S6_D2
```

As you can see /dev/sda1 is using 5.4G, I'm pretty scrupulous in keeping / clean, regularly running:

```
sudo apt autoremove
sudo apt autoclean
sudo apt clean
```

If I don't pay attention / just keeps getting larger and larger.

---

### Post by vasa1 on 2016-05-18
Somewhat off-topic, somewhat related: [http://www.omgubuntu.co.uk/2016/05/ubuntu-image-size-increase-2gb](http://www.omgubuntu.co.uk/2016/05/ubuntu-image-size-increase-2gb) for 16.10

---

### Post by jerrylamos on 2016-05-19
Thanks for looking at this. Here's my printout:
```

~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev             1.7G     0   1.7G    0% /dev
tmpfs            344M   5.8M  338M   2% /run
/dev/sdb2         9.5G  7.4G  1.7G     82% /     <<----- was 5.6G
tmpfs             1.7G   33M   1.7G   2% /dev/shm
tmpfs             5.0M  4.0K   5.0M   1% /run/lock
tmpfs            1.7G     0    1.7G   0% /sys/fs/cgroup
cgmfs            100K     0   100K   0% /run/cgmanager/fs
tmpfs            344M   68K   344M   1% /run/user/1000

```
"Used" was about 5.6 G until the partition space was all used up by the failed unzip.  
After erase and clean as in Caribou's note  it's still  7.4 G.  
Ubuntu has now used up about 1.8 G for I don't know what.  Is there some massive cache somewhere?

Thanks, Jerry

---

### Post by sudodus on 2016-05-19
Maybe you can use ***baobab*** to find the culprit. If you have access problems, maybe you can use

```
sudo -H baobab
```

---

