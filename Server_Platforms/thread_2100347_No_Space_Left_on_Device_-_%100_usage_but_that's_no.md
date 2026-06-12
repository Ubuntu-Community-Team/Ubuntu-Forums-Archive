---
title: "No Space Left on Device - %100 usage but that's not true !!!"
date: 2013-01-01
forum: Server Platforms
---

### Post by Oxii on 2013-01-01
I have a Linux server ( ubuntu 12.4 ) which serve my web application (20 MB) on apache httpd. a few days ago I upgrade it to 12.10, then copied one folder (30 GB) to www folder. suddenly the server hang and I got the **Low Graphics Mode** message (My screen card is Intel ). So I removed the huge folder and restarted the computer but still got the same message. when I searched here for solutions and tried some of them I got this message: **No Space Left on Device** 
then I typed: **df -h**, I surprised that the usage is %100 !!
here is my partitions table:
```
Number|Start|End|Size|File System|Name Flags
1|17.4k|20.0MB|20.0MB|fat16|boot
2|20.0MB|489GB|489GB|ext4
3|489GB|500GB|10.6GB|linux-swap(v1)
```
 
I can't access the my files anymore!
Is there anyway to save me and my server without a format ?

---

### Post by Cheesemill on 2013-01-01
Can you post the outputs of:
```
sudo fdisk -l
df -h
```

---

### Post by volkswagner on 2013-01-01
20MB for /boot seems scary small.  I have one kernel installed on my Debian6 machine and /boot is exactly 20MB. 200MB for /boot would be recommended.

In addition to the above recommended commands the following may help pinpoint the large dir.

```
sudo du -h / --max-depth=1
```

If suspect the problem is in /var then modify the above like:

```
sudo du -h /var --max-depth=1
```

---

### Post by darkod on 2013-01-01
I think that's just the boot flag but not a /boot partition. The filesystem is fat16. Could /boot work on FAT?

---

### Post by SeijiSensei on 2013-01-02
> **darkod said:**
> I think that's just the boot flag but not a /boot partition. The filesystem is fat16. Could /boot work on FAT?

I doubt it.  My preference is ext2 for /boot since it is small enough that journaling is unnecessary.

---

### Post by Oxii on 2013-01-02
> **Cheesemill said:**
> Can you post the outputs of:
```
sudo fdisk -l
df -h
```

```
df -h
```
```
Filesystem|Size|Used"Avail|Use%|Mounted on
/dev/sda2|449G|0|100%
```


```
sudo fdisk -l
```
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'!
Disk /dev/sda: 500.1 GB
Units = sectors of 1 * 512 = 512 bytes

Device Boot|Start|End|Blocks|Id|System
/dev/sda1|1|976773167|488386583+|ee|GPT
```




> **volkswagner said:**
> 20MB for /boot seems scary small.  I have one kernel installed on my Debian6 machine and /boot is exactly 20MB. 200MB for /boot would be recommended.

In addition to the above recommended commands the following may help pinpoint the large dir.

```
sudo du -h / --max-depth=1
```

If suspect the problem is in /var then modify the above like:

```
sudo du -h /var --max-depth=1
```

```
sudo du -h / --max-depth=1
```
```
4.0K  /mnt
3.1G  /usr
..
..
244M  /root
16K  /media
8.8M  /bin
[COLOR="Red"]444G  /var[/COLOR] 
```

```
sudo du -h /var --max-depth=1
```
```
4.0K  /var/tmp
235M  /var/www
[COLOR="red"]444G  /var/log[/COLOR]
..
..
```


So, the log is huge!! and when I try:
```
sudo apt-get autoclean
sudo apt-get autoremove
```

**I got: Error! No space left on device**

So, I don't know how to delete log files!
I'm kinda stuck!




> **darkod said:**
> I think that's just the boot flag but not a /boot partition. The filesystem is fat16. Could /boot work on FAT?
I have no idea how to do that

---

### Post by darkod on 2013-01-02
My post was just reflecting that the 20MB partition can't be your /boot, it wasn't meant for you to do anything.

Yeah, your root partition is 100% full. Wait for someone more experienced to tell you what you can and can not delete, but while waiting you can have a better look. Enter the log folder and check all folders and files sizes with:
```
cd /var/log
du -sf *
```

That will list all files/folders sizes. When you want to delete something, you can do it by simply:
```
sudo rm <filename>
```

BUT be careful what you delete. :)

Usually older logs can be deleted without problems. Often there is a current log of some application called 'filename.log' and there are older archived logs named like 'filename.log.1', 'filename.log.2', etc. That's how log files rotate. In most cases deleting an older log file is not dangerous, only you lose the information inside.

But right now it's more important to get some free space than losing the old log files information.

---

### Post by The Cog on 2013-01-02
You will probably need to delete some log files by hand. Use "ls -l foldername" to list the files and directories in a folder- for instance 
```
sudo ls -lh /var/log
```and once you find a large log file that you feel you can remove: "sudo rm filename" to delete that file, e.g.
```
sudo rm /var/log/apache2/access.log.gz.3
```
The gz log files are zipped up older log files. It's probably best to go for these. After you've made a bit of space, you might find that autoremove works again.

---

### Post by CharlesA on 2013-01-02
Run this to see where the huge log file are:

```
sudo du -h /var/log --max-depth=1
```

That might help you narrow down what the deal is and hopefully find a way to fix it.

---

### Post by spynappels on 2013-01-02
When you find which log file has grown too large, we can also see why it has run away and hopefully prevent it from happening again.

When you find out which file it was, please share, so that we can give some tips on diagnosing why.

---

### Post by Oxii on 2013-01-05
Found it!
it's ```
/var/log/cups
```

and when I list its files, I got:

```
-rw-r----- 1 root adm 758 DEC 30 07:37 access_log.1.gz
..
..
..
[COLOR="Red"]-rw-r----- 1 root adm 444G JAN 5 08:09 error_log[/COLOR]
-rw-r----- 1 root adm 245 DEC 29 13:17 error_log.1.gz
```

So, what's next ?

---

### Post by spynappels on 2013-01-05
Firstly, do you use CUPS for printing, i.e. is your server a print server?

If you don't, you could disable the CUPS service.

I'd also check what errors are in the log. Can you post the output of
```
tail -25 /var/log/cups/error_log
```
please?

---

### Post by cariboo on 2013-01-05
the first thing I'd do is stop cups:

```
sudo service cups stop
```

Next, remove the log file:

```
sudo rm /var/log/cups/error_log
```

Then restart cups:

```
sudo service cups start
```

let it run for about 5 minutes, then:

```
cat /var/log/cuos/error_log
```

this should give you and idea what is causing the error.

---

### Post by Oxii on 2013-01-05
```
sudo service cups stop
```
I got: ```
sudo: unable to write to /var/lib/sudo/username/tty2: No space left on device
```

```
tail -25 /var/log/cups/error_log
```

I got:  ```
tail: cannot open '/var/log/cups/error_log' for reading: No such file or directory
``` !!!!

---

### Post by CharlesA on 2013-01-05
> **Oxii said:**
> Found it!
it's ```
/var/log/cups
```

and when I list its files, I got:

```
-rw-r----- 1 root adm 758 DEC 30 07:37 access_log.1.gz
..
..
..
[COLOR="Red"]-rw-r----- 1 root adm 444G JAN 5 08:09 error_log[/COLOR]
-rw-r----- 1 root adm 245 DEC 29 13:17 error_log.1.gz
```

So, what's next ?

error_log sounds like a Web server thing (same with access_log).

I checked on my server and the apache logs are error.log, not error_log, but on my hosted site, the logs are listed as error_log.

Hmm....

Run this please:

```
find /var/log -name "error_log"
```

---

### Post by lykwydchykyn on 2013-01-05
> **CharlesA said:**
> error_log sounds like a Web server thing (same with access_log).


They are... they're the error_log and access_log for the CUPS web interface.

I'd just delete the thing and reboot.  If you want to know what errors filled up the log, there's a good chance you'll be getting plenty more of them, or that they're in the rotated 256MB logfile.

Could be someone trying to DDOS or hack you on your cups port (631) if this is a public server.  Otherwise, CUPS just went nuts.

---

### Post by CharlesA on 2013-01-05
> **lykwydchykyn said:**
> They are... they're the error_log and access_log for the CUPS web interface.

Interesting, I didn't know CUPS had a web interface.

---

### Post by cariboo on 2013-01-05
Try:

[http://localhost:631](http://localhost:631)

---

### Post by Oxii on 2013-01-06
Something weird happened!
When I unplugged the computer then replugged it. it works fine and problem gone!! the /var size is completely normal!

But I'm afraid of facing it again. I think my main problem is because of the partitions:

```
sudo parted -l
```

```
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number|Start|End|Size|File System|Name|Flag
1|17.4K|20.0MB|20.0MB|fat16| |boot
2|20.0MB|489GB|489GB|ext4
3|489GB|500GB|10.6GB|linux-swap(v1)
```

as you see, the home and root are together and not separated. do I have to create a new partition for home? 

Anyone has another idea how to avoid that issue again ?

---

### Post by darkod on 2013-01-06
You don't have to create separate /home partition, but you can if you want to. Anyway, your problem was with /var, are you more worried about /home now?

I would be more worried whether the same problem with the logs happens again.

And creating separate /home might be complicated, depending on your experience with ubuntu. Unless you buy a new hdd and put /home there, you will have to shrink / first to make space to create a new partition for /home. You will need to shrink / from live mode because it needs to be unmounted. Also, you will need to have a full backup first because repartitioning can sometimes go wrong.

If you are separating partitions (mount points) I would rather separate /var first than /home.

---

### Post by Oxii on 2013-01-06
> **darkod said:**
> You don't have to create separate /home partition, but you can if you want to. Anyway, your problem was with /var, are you more worried about /home now?

I would be more worried whether the same problem with the logs happens again.

And creating separate /home might be complicated, depending on your experience with ubuntu. Unless you buy a new hdd and put /home there, you will have to shrink / first to make space to create a new partition for /home. You will need to shrink / from live mode because it needs to be unmounted. Also, you will need to have a full backup first because repartitioning can sometimes go wrong.

If you are separating partitions (mount points) I would rather separate /var first than /home.

ok so you think I don't need to create a new partition?
I will postponed that.

What can I do to make sure that I won't face the log files problem again ?

---

### Post by darkod on 2013-01-06
If the problem continues the same log file will start to get filled again. Post part of the messages in the log so that people more experienced with log errors can take a look and figure out what is going on.

---

### Post by Oxii on 2013-01-06
the past few days I faced a strange issue with my computer. I discussed it here:
[http://ubuntuforums.org/showthread.php?t=2100347](http://ubuntuforums.org/showthread.php?t=2100347)

Shortly, log files (in cups folder) grow so fast! I did solve the problem but I'm afraid of facing it again. I need to know what cause it so that I can avoid it.

I'm not sure but does the fact that I don't separate the root and /home relevant ?

---

### Post by howefield on 2013-01-06
Threads merged.

---

### Post by Oxii on 2013-01-06
[SIZE="4"]**UPDATE**[/SIZE]

the problem is back :(

the /var/log/sups is full again (444GB) 

I didn't even do anything !

```
ls -l /var/log/cups/

total 464543116
-rw-r----- 1 root adm 0 DEC 30 07:47 access_log
-rw-r----- 1 root adm 587 DEC 30 07:37 access_log.1.gz
-rw-r----- 1 root adm 259 DEC 29 07:59 access_log.2.gz
-rw-r----- 1 root adm 258 DEC 28 07:41 access_log.3.gz
-rw-r----- 1 root adm 255 DEC 27 07:23 access_log.4.gz
-rw-r----- 1 root adm 252 DEC 26 07:04 access_log.5.gz
-rw-r----- 1 root adm 230 DEC 25 07:44 access_log.6.gz
-rw-r----- 1 root adm 161 DEC 24 12:18 access_log.7.gz
-rw-r----- 1 root adm 475691855862 Jan 7 07:50 error_log
-rw-r----- 1 root adm 245 DEC 29 14:34 error_log.1.gz
-rw-r----- 1 root adm 0 Feb 29 29 2012 page_log
```

---

### Post by Oxii on 2013-01-07
> **cariboo907 said:**
> the first thing I'd do is stop cups:

```
sudo service cups stop
```

Next, remove the log file:

```
sudo rm /var/log/cups/error_log
```

Then restart cups:

```
sudo service cups start
```

let it run for about 5 minutes, then:

```
cat /var/log/cuos/error_log
```

this should give you and idea what is causing the error.


file removed successfully, but:
```
cat /var/log/cuos/error_log
```

I got: **No such file or directory**

now the problem gone but I'm sure it will be back again!
what can do now ?

---

### Post by lykwydchykyn on 2013-01-07
> **Oxii said:**
> file removed successfully, but:
```
cat /var/log/cuos/error_log
```

I got: **No such file or directory**

now the problem gone but I'm sure it will be back again!
what can do now ?

There was a typo in the command.  It should be:

```

cat /var/log/cups/error_log

```

---

### Post by Oxii on 2013-01-07
> **lykwydchykyn said:**
> There was a typo in the command.  It should be:

```

cat /var/log/cups/error_log

```

ok, it has been 10 min and this command still working

---

### Post by lykwydchykyn on 2013-01-07
> **Oxii said:**
> ok, it has been 10 min and this command still working

Probably "tail" would have been better than "cat".  And if there's anything in the file at all, I'd recommend shutting down cups so it doesn't become monstrously huge again and make it difficult to inspect.

---

### Post by Wim Sturkenboom on 2013-01-07
Stop de command with <ctrl>C . Those files are big so you have to analyze them manually; scrolling text on a screen does not help ;)

Use _less_ instead of _cat_ and you can scroll trough the pages
```

less /var/log/cups/error_log

```

---

### Post by Oxii on 2013-01-07
> **lykwydchykyn said:**
> Probably "tail" would have been better than "cat".  And if there's anything in the file at all, I'd recommend shutting down cups so it doesn't become monstrously huge again and make it difficult to inspect.

is it okay to shut it down forever ?! my application offers a "print page" to users, would that be affected ?

---

### Post by Oxii on 2013-01-07
I tried to stop it by:

```
sudo service cups stop
```

but it's still alive and growing so fast!
I checked the services by: ```
chkconfig
```, the cups is off already!
so why it's still being filled?

---

### Post by CharlesA on 2013-01-07
> **Wim Sturkenboom said:**
> Stop de command with <ctrl>C . Those files are big so you have to analyze them manually; scrolling text on a screen does not help ;)

Use _less_ instead of _cat_ and you can scroll trough the pages
```

less /var/log/cups/error_log

```

What they said.

> **Oxii said:**
> 
so why it's still being filled?

Have you looked at the log to see what it wrong?

Check it out via the command Wim Sturkenboom mentioned and post any error messages you find.

---

