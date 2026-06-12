---
title: "HowTo: Change disk checking/fsck at boot frequency"
date: 2006-11-15
forum: Tutorials
---

### Post by Old Pink on 2006-11-15
Hi, 

Nearly all Ubuntu users know, that every 30 boots their system performs what is know as an "fsck" to make sure your hard drive has no errors.

If you go through periods of frequent rebooting, these checks can become annoying.
[U][B]
To change how often these boot up checks occur, run this command in a terminal:[/B][/U]
```
sudo tune2fs -c **50** /dev/**hda1**
```The two things in bold can be modified.

First, the number "50", which chooses how often you want the check performed. 1 makes it scan at every boot, 0 stops scanning altogether, and all other numbers mean the scan will be performed every ** boots, 20 for 20, 30 for 30, 40 for 40 and so on.

Next, the "hda1" which you simply change to match the location of your hard drive, be it hda1,2,3 or even sda1,2,3.

Setting the scan to never happen isn't recommended, I'd say between 50-100 is safe. :) 

- Matt

---

### Post by bodhi.zazen on 2006-11-16
Nice How-to Old Pink

This thread has been added to the UDSF wiki.

[Change Disk Check Frequency](http://doc.gwos.org/index.php/ChangeDiskCheckFrequency)

I took the liberty of adding some basic information about fstab:

[b]fstab options
/etc/fstab[/b] is a system configuration file and is used to tell the Linux kernel which partitions (file systems) to mount and where on the file system tree.

A typical fatab entry may look like this:```
/dev/hda1 / ext3 defaults 1 **1**
/dev/hdb1 /home ext3 defaults 1 **2**
```

The 6th column (**in bold**) is a fsck options.
[list][*]0 = Do not check.
[*]1 = First file system (partition) to check;
[list][*]** / (root partition) should be set to 1**.[/list]
[*]2 = ALL OTHER file systems to be checked.[/list]

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by Charles Hand on 2006-11-21
Short of turning it off completely (not recommended) it's still going to happen by surprise and on the computer's timetable. Is there any way to tie into the mechanism that counts the boots and run a little program that says "you're going to have a forced check three boots from now"? Maybe a log file that tells how may boots are left, which could be grepped?

---

### Post by Sam on 2006-11-21
There is also the -i switch to set an interval before the check.
```
-i interval-between-checks[d|m|w]
```
Example combining both methods:
```
$ sudo tune2fs -c 50 -i 1m /dev/hda1
```

---

### Post by Charles Hand on 2006-11-21
> **Charles Hand said:**
> Short of turning it off completely (not recommended) it's still going to happen by surprise and on the computer's timetable. Is there any way to tie into the mechanism that counts the boots and run a little program that says "you're going to have a forced check three boots from now"? Maybe a log file that tells how may boots are left, which could be grepped?

Here it is:
```
sudo dumpe2fs -h /dev/sdb1 | grep -i 'mount count'
```

Output: 
```

dumpe2fs 1.38 (30-Jun-2005)
Mount count:              5
Maximum mount count:      30

```

---

### Post by kvonb on 2006-12-10
Search the forums for "bonager", it is a panel app that warns you of impending scans and lets you postpone them :)

---

### Post by MaineDave on 2007-05-08
There's also a showfsck package (I'm using Edgy in case that matters) with the command "showfsck" to show how many reboots remain before a fsck runs.

---

### Post by lunamystry on 2007-07-09
how do i get the Ubuntuuser icon for my website?

---

### Post by NuK on 2007-08-01
I'm learning bash and I wrote this script that shows the "mount count" for each partition. It works fine for me... I hope it helps!
```

#!/bin/bash

# this directory must exist to execute the script
if [ -d /dev/disk/by-id/ ]; then :; else echo 'ERROR: /dev/disk/by-id/ does not exist'; exit 1; fi

# root user is necessary
if [ $UID -gt 0 ]; then	echo 'ERROR: You have to be root'; exit 1; fi

# list ALL partitions and exclude the SWAP ones
declare -a SWAPS=( $(cat /proc/swaps | grep /dev/ | awk '{print$1}') )
lsParts="ls -l /dev/disk/by-id/ | grep --regexp=-part[0-9] | awk '{sub(\"../../\",\"/dev/\");"
for i in $(seq 0 $((${#SWAPS[@]} - 1))); do
	lsParts=${lsParts}' sub("'${SWAPS[$i]}'", "");'
done
lsParts=${lsParts}" print\$10}'"
declare -a PARTITIONS=(`eval $lsParts`)

# format TEMP file
for i in $(seq 0 $((${#PARTITIONS[@]} - 1))); do
	PARTITION=${PARTITIONS[$i]}
	if [ -n $PARTITION ]; then
		# first line, device name
		echo $PARTITION >> .temp.$$
		# mount info
		sudo dumpe2fs -h $PARTITION | grep 'Filesystem volume name' >> .temp.$$
		sudo dumpe2fs -h $PARTITION | grep 'Mount count' >> .temp.$$
		sudo dumpe2fs -h $PARTITION | grep 'Maximum mount count' >> .temp.$$
		sudo dumpe2fs -h $PARTITION | grep 'Last mount time' >> .temp.$$
		sudo dumpe2fs -h $PARTITION | grep 'Last checked' >> .temp.$$
		echo '-------------------------------' >> .temp.$$
	fi
done

# show and delete TEMP file
clear
cat .temp.$$
rm -f .temp.$$

# TUNE help
echo
echo 'HOWTO'
echo -e "- Change Filesystem volume name:\n\tsudo tune2fs -L NewLabel /dev/hda1\n\tsudo e2label /dev/hda1 NewLabel"
echo
echo -e "- Change Maximum mount count:\n\tsudo tune2fs -c 50 /dev/hda1"
echo
echo -e "- Modify reserved space:\n\tsudo tune2fs -m 1 /dev/hda1"
echo

exit 0

```

Remember that you can call the script like this:
```
sudo bash ./scriptname.sh
```

But if you want to use it more than once, it's better to change the execute permissions and call it without the "bash" command:
```
chmod 755 ./scriptname.sh
sudo ./scriptname.sh
```

---

### Post by ntlam on 2007-08-29
> **Old Pink said:**
> Hi, 

Nearly all Ubuntu users know, that every 30 boots their system performs what is know as an "fsck" to make sure your hard drive has no errors.

If you go through periods of frequent rebooting, these checks can become annoying.
[U][B]
To change how often these boot up checks occur, run this command in a terminal:[/B][/U]
```
sudo tune2fs -c **50** /dev/**hda1**
```The two things in bold can be modified.

First, the number "50", which chooses how often you want the check performed. 1 makes it scan at every boot, 0 stops scanning altogether, and all other numbers mean the scan will be performed every ** boots, 20 for 20, 30 for 30, 40 for 40 and so on.

Next, the "hda1" which you simply change to match the location of your hard drive, be it hda1,2,3 or even sda1,2,3.

Setting the scan to never happen isn't recommended, I'd say between 50-100 is safe. :) 

- Matt

Nice guide

---

### Post by mallow on 2007-10-17
OK, thanks for that. It`s helpfull. But is there a way to skip this check on startup? I man for example that I`m in a hurry and when I boot up ubuntu fsck starts. How to skip this and postpone to another boot? Is it possible or will it be in gutsy?

---

### Post by TearDownAllSigns on 2007-10-27
To skip on startup and move to shutdown you can use AutoFsck

[https://wiki.ubuntu.com/AutoFsck]("https://wiki.ubuntu.com/AutoFsck")

I haven't used it myself so I can't vouch but from the thread it sounds like it is working for people.

[http://ubuntuforums.org/showthread.php?t=566058&highlight=fsck+on+startup&page=2]("http://ubuntuforums.org/showthread.php?t=566058&highlight=fsck+on+startup&page=2")

---

### Post by ssam on 2007-11-03
> **TearDownAllSigns said:**
> To skip on startup and move to shutdown you can use AutoFsck

[https://wiki.ubuntu.com/AutoFsck]("https://wiki.ubuntu.com/AutoFsck")


i am using this. its only run once so far (only had it installed a few weeks).

seem to work exactly as it says.

---

### Post by j1solutions on 2008-05-26
> **Old Pink said:**
> Hi, 

Nearly all Ubuntu users know, that every 30 boots their system performs what is know as an "fsck" to make sure your hard drive has no errors.

If you go through periods of frequent rebooting, these checks can become annoying.
[U][B]
To change how often these boot up checks occur, run this command in a terminal:[/B][/U]
```
sudo tune2fs -c **50** /dev/**hda1**
```The two things in bold can be modified.

First, the number "50", which chooses how often you want the check performed. 1 makes it scan at every boot, 0 stops scanning altogether, and all other numbers mean the scan will be performed every ** boots, 20 for 20, 30 for 30, 40 for 40 and so on.

Next, the "hda1" which you simply change to match the location of your hard drive, be it hda1,2,3 or even sda1,2,3.

Setting the scan to never happen isn't recommended, I'd say between 50-100 is safe. :) 

- Matt

Thanks Old Pink, I know this is an old post, but I just found it and it's well explained!

---

### Post by akhil.t on 2008-06-18
I tried this command and it said that the frequency has been changed. But the fsck is still taking place every time I boot. If I do not press skip, the check stops and 50% and the system prompts me to do a manual fsck.

Any help? :-|

---

### Post by scorp123 on 2008-06-18
> **akhil.t said:**
> the check stops and 50% and the system prompts me to do a manual fsck. Then I suggest you do as the system tells you because it's obvious you have a corrupted disk and are about to lose your data soon.

---

### Post by akhil.t on 2008-06-18
> **scorp123 said:**
> Then I suggest you do as the system tells you because it's obvious you have a corrupted disk and are about to lose your data soon.

Thank you scorp123. :)
I did that once. Ended up with a blank screen after almost 2 hrs of check. Had to reinstall the OS. 

I am unable to understand why the command is not having the desired effect.

---

### Post by bodhi.zazen on 2008-06-18
You need to run that command from a live CD with the partition Unmounted.

```
fsck -rfv /dev/sdxy
```

where /dev/sdxy = the partition needing to be checked. Sometimes the problem can not be solved automatically in which case you may need to attempt manual recovery. 

If automatic recovery fails, however, you usually have a serious hardware problem and you may need data recovery tools ... 

How to fsck: [http://www.linux.com/feature/32026](http://www.linux.com/feature/32026)

---

### Post by akhil.t on 2008-06-18
> **bodhi.zazen said:**
> You need to run that command from a live CD with the partition Unmounted.

```
fsck -rfv /dev/sdxy
```

where /dev/sdxy = the partition needing to be checked. Sometimes the problem can not be solved automatically in which case you may need to attempt manual recovery. 

If automatic recovery fails, however, you usually have a serious hardware problem and you may need data recovery tools ... 

How to fsck: [http://www.linux.com/feature/32026](http://www.linux.com/feature/32026) Thank you bodhi. I'll try it out. :)

---

### Post by directcharitycontribution on 2008-10-08
> **Old Pink said:**
> Hi, 

Nearly all Ubuntu users know, that every 30 boots their system performs what is know as an "fsck" to make sure your hard drive has no errors.

If you go through periods of frequent rebooting, these checks can become annoying.
[U][B]
To change how often these boot up checks occur, run this command in a terminal:[/B][/U]
```
sudo tune2fs -c **50** /dev/**hda1**
```The two things in bold can be modified.

First, the number "50", which chooses how often you want the check performed. 1 makes it scan at every boot, 0 stops scanning altogether, and all other numbers mean the scan will be performed every ** boots, 20 for 20, 30 for 30, 40 for 40 and so on.

Next, the "hda1" which you simply change to match the location of your hard drive, be it hda1,2,3 or even sda1,2,3.

Setting the scan to never happen isn't recommended, I'd say between 50-100 is safe. :) 

- Matt

[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/) the options are shown with terminal > man fsck OR man tune2fs

and thread [http://ubuntuforums.org/showthread.php?t=937345](http://ubuntuforums.org/showthread.php?t=937345)

---

### Post by dannyman on 2008-11-19
I boiled this down into a "universal" command:

```
sudo tune2fs -c 0 `mount | awk '$3 == "/" {print $1}'`
```

I posted further explanation on my web site:
[http://dannyman.toldme.com/2008/11/19/e2fsck-frog-off/](http://dannyman.toldme.com/2008/11/19/e2fsck-frog-off/)

---

### Post by yangeryanger on 2009-02-25
hi. i run a home server running 24/7 day and night and data is always moving from one hdd to another or some sorts.. is there a way to make it fsck more often? should i just lower the number in the *sudo tune2fs -c **50** /dev/hda1* to *sudo tune2fs -c **2** /dev/hda1* or something?

oh, edit: i'm using ext3 on the main boot, and on my other drives, jfs...

thanks guys.

---

### Post by bodhi.zazen on 2009-02-25
Well, you should not need to run it any more often, especially if you are moving files like that.

Also fsck should not be run on a mounted partition, so it runs at boot.

You should be able to run fsck at next boot if you like :

[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

---

### Post by wamukota on 2009-05-05
> **dannyman said:**
> I boiled this down into a "universal" command:
```
sudo tune2fs -c 0 `mount | awk '$3 == "/" {print $1}'`
```


I don't use the 'c' (for count) between checks, but the 'i' (for interval).

So to set the interval every 2 weeks the command becomes:
```
sudo tune2fs -i 2w `mount | awk '$3 == "/" {print $1}'`
```

Every 10 days becomes
```
sudo tune2fs -i 10d `mount | awk '$3 == "/" {print $1}'`
```

Every 3 months becomes
```
sudo tune2fs -i 3m `mount | awk '$3 == "/" {print $1}'`
```

Using the interval allows you to predict more or less when the check will take place (ie every sunday, if you run the command on a sunday with an interval of 7 days)

---

### Post by ciderpunx on 2009-06-03
> **Charles Hand said:**
>  Is there any way to tie into the mechanism that counts the boots and run a little program that says "you're going to have a forced check three boots from now"? Maybe a log file that tells how may boots are left, which could be grepped?

Using the solutions already suggested you can do something like this:

```
$ dumpe2fs -h /dev/sda1 2>&1 | grep -i 'mount count' | perl -ne '$i++;chomp;s/.*://;s/\s//g;$arr[$i]=$_;print "Next fsck in " . ($arr[$i] - $arr[1]) . " mounts\n" if($i==2);'
```You can send that to a file by appending:
```
> /path/to/file
```If you have zenity installed, you can have a popup appear by appending this instead:
```
| zenity --text-info --title "fsck info"
```I have the last version saved as a shell script which can be set up to run in my startup applications (system|preferences|startup applications|startup programs). Here's that version, which is a bit tidier.

```
#!/bin/bash
# fsck mount dialogue hack, by ciderpunx#

dumpe2fs -h /dev/sda1 2>&1 \
| grep -i 'mount count' \
| perl -ne '$i++;
            chomp;
            s/.*://;
            s/\s//g;
            $arr[$i]=$_;
            print "Next fsck in " . ($arr[$i] - $arr[1]) . " mounts\n" if($i==2);' \
| zenity --text-info --title "fsck info"
```

---

### Post by ario on 2009-06-12
Thanks. it saved my time a lot:p

---

### Post by COKEDUDE on 2012-03-28
Great thread :). I know its but I wanted to bring it back to life :).

---

