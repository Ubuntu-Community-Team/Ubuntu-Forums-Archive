---
title: "Lucid Server hard drive full !"
date: 2010-08-19
forum: Server Platforms
---

### Post by damarusama on 2010-08-19
I created a security server with snort, ntop, nessus, webmin, installed mysql, tweaked a little here and there, nothing major - created a web interface to link all of these together (simple html with frames to create some sort of integration). 

Run fine for a month or 2 then the hard drive gets full - and I have no Idea how to trace where the hard drive gets full. Playing with the 'du' to try to track where it would come from. 

Is there an easy way to track where the disk space is taken? Would webmin or other software would help in that process?  Is Ntop knows to gather too much data and use disk space ?

I clearup most of my mysql data in case that would be the problem (trough phpmyAdmin) but that didn't freed up much space. 

Any clue would be appreciated - when my hdd space is too low nothing can start (mysql freaks out so then a lot of other software just don't start) 

thanks !

---

### Post by arrrghhh on 2010-08-19
Well, there's a great tool called Disk Analyzer, but it doesn't work so well on the server edition (require's X, etc).

A quick google search turned up a tool called [Discus](http://www.debianadmin.com/manpages/discusmanpage.txt) which is text-only.  Just looks like df, but prettier.

You can also perhaps narrow it down a little by doing a ```
du -sh /*
``` - breaks down usage by each main branch of the / tree.

---

### Post by samosamo on 2010-08-19
inodes are full?  try:

```
$ df -i
```

---

### Post by damarusama on 2010-08-19
inodes ?

damaru@oni:~$ df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/mapper/oni-root 9379840 3042655 6337185   33% /
udev                  256033     649  255384    1% /dev
none                  256033       1  256032    1% /dev/shm
none                  256033      23  256010    1% /var/run
none                  256033       4  256029    1% /var/lock
none                  256033       1  256032    1% /lib/init/rw
/dev/sda5             124496     164  124332    1% /boot

33% doesn't seems full - but ???

---

### Post by brettg on 2010-08-19
Sometimes files can be left open by a misbehaving app meaning that they don't show up when you issue the df command but the space is still seen to be in use by the system.

I wrote a script to created sorted output from the du command mentioned earlier. [More details here]("http://tuxnetworks.blogspot.com/2009/11/sort-du-output-in-readable-format.html")

---

### Post by damarusama on 2010-08-19
discuss looks nice - but I can't even istall this!! ho my - I am trying the other du / and see what I can pull out of it 

thanks

---

### Post by samosamo on 2010-08-19
Wait a second -- it's not full anymore, so what happened?  What did you do to fix it?  Reboot?

---

### Post by damarusama on 2010-08-19
stil 98% full 

are you saying it's not full anymore because of the df -i ? is that supposed to show 100%?

---

### Post by damarusama on 2010-08-19
wo - I can even vim anymore - cant write to swap...
using the df :

damaru@oni:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/oni-root 147681760 140191956         0 100% /
udev                   1024132       208   1023924   1% /dev
none                   1024132         0   1024132   0% /dev/shm
none                   1024132        40   1024092   1% /var/run
none                   1024132         0   1024132   0% /var/lock
none                   1024132         0   1024132   0% /lib/init/rw
/dev/sda5               233335     14891    205996   7% /boot
damaru@oni:~$ df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/mapper/oni-root 9379840 3042207 6337633   33% /
udev                  256033     649  255384    1% /dev
none                  256033       1  256032    1% /dev/shm
none                  256033      25  256008    1% /var/run
none                  256033       4  256029    1% /var/lock
none                  256033       1  256032    1% /lib/init/rw
/dev/sda5             124496     164  124332    1% /boot

---

### Post by TwoEars on 2010-08-19
Right, here's what you need to do.

```
df -h
```

This will take you how much actual data storage is being used up. Of course, we know how much is being used - you already know. Inodes are something used by every file - it is possible to have full inodes, such that you can not actually write to disk. Anyway, this isn't what has happened here.

I imagine that you either have a huge log file, or a backup cron job gone wrong, or something along those lines.

I suggest you run```
du -ch /var/log
``` and post the output here. Do **NOT** delete the log files yet, you'll need them for troubleshooting.

---

### Post by arrrghhh on 2010-08-19
Did the output of ```
du -sh /*
``` point you in the right direction...?  You seemed completely baffled by the usage, as if you had no clue where it was coming from....

I have definitely seen /var/log get out of control if there's something wrong, and a log file gets data written to it constantly.  I had a log file put about 8mb every minute once, I'm sure there's been worse as well ;)

---

### Post by damarusama on 2010-08-19
damaru@oni:~$ sudo du -ch /var/log
4.0K    /var/log/mysql
4.0K    /var/log/news
4.0K    /var/log/landscape
7.3M    /var/log/squid3
12K     /var/log/fsck
4.0K    /var/log/netmrg
4.0K    /var/log/apparmor
27M     /var/log/logzilla
4.0K    /var/log/dist-upgrade
8.0K    /var/log/dbconfig-common
4.0K    /var/log/Bastille/revert/backup
8.0K    /var/log/Bastille/revert
4.0K    /var/log/Bastille/Assessment
4.0K    /var/log/Bastille/old-config
20K     /var/log/Bastille
52K     /var/log/apt
12K     /var/log/mrtg
340K    /var/log/installer/cdebconf
1.1M    /var/log/installer
1.4M    /var/log/ntop
1.6M    /var/log/apache2
184K    /var/log/squid
70M     /var/log
70M     total

logs are quit small - I did delete the log about a month ago thinking it would help - to no avail 

the du -sh /* shows a lot of stuff there but nothing big (I have a 150gb hard drive only few gb were in use after the complete install  so I was expecting so see a lot of stuff over 100mb - there are few big folder but nothing alarming )

a lot of the folder I cannot see with the du -sh /* when I sudo du -sh /* it tends to die on me right after the /usr

I wanted to create the script that was provided earlier but vim wouldn't want to save since there wasn't enough space :S

discus is cute but doesn't get me too far :

damaru@oni:~$ discus
Mount           Total         Used         Avail      Prcnt      Graph
/              140.84 GB    133.70 GB      7.14 GB    94.9%   [*********-]
/sys                0 KB         0 KB         0 KB     0.0%   [----------]
+onnections         0 KB         0 KB         0 KB     0.0%   [----------]
+rnel/debug         0 KB         0 KB         0 KB     0.0%   [----------]
+l/security         0 KB         0 KB         0 KB     0.0%   [----------]
/dev             0.98 GB       208 KB     999.9 MB     0.0%   [----------]
/dev/shm         0.98 GB         0 KB      0.98 GB     0.0%   [----------]
/var/run         0.98 GB        40 KB      0.98 GB     0.0%   [----------]
/var/lock        0.98 GB         0 KB      0.98 GB     0.0%   [----------]
+ib/init/rw      0.98 GB         0 KB      0.98 GB     0.0%   [----------]
/boot           227.9 MB      14.5 MB     213.3 MB     6.4%   [*---------]
damaru@oni:~$ discus -r
Mount           Total         Used         Avail      Prcnt      Graph
/              140.84 GB    133.70 GB         0 KB   100.0%   [**********]
/sys                0 KB         0 KB         0 KB     0.0%   [----------]
+onnections         0 KB         0 KB         0 KB     0.0%   [----------]
+rnel/debug         0 KB         0 KB         0 KB     0.0%   [----------]
+l/security         0 KB         0 KB         0 KB     0.0%   [----------]
/dev             0.98 GB       208 KB     999.9 MB     0.0%   [----------]
/dev/shm         0.98 GB         0 KB      0.98 GB     0.0%   [----------]
/var/run         0.98 GB        40 KB      0.98 GB     0.0%   [----------]
/var/lock        0.98 GB         0 KB      0.98 GB     0.0%   [----------]
+ib/init/rw      0.98 GB         0 KB      0.98 GB     0.0%   [----------]
/boot           227.9 MB      14.5 MB     201.2 MB    11.7%   [*---------]
damaru@oni:~$

---

### Post by TwoEars on 2010-08-19
In that case, I suggest you run ```
sudo apt-get clean; sudo apt-get autoclean
```

After running this, you will have a little more space(possibly a LOT more space).

So, run ```
du -ach /* >> $HOME/output.txt && echo "Finished"
``` and post the contents of $HOME/output.txt

You will have to be patient, this could take a while, don't do anything until it's finished.

---

### Post by arrrghhh on 2010-08-20
Also, do a ```
ls -lah /
```... it almost looks like there's something right at the root that's filling the drive.  Very strange.  Definitely try the apt-get clean & autoclean, it can't hurt.

[quote=damarusama]a lot of the folder I cannot see with the du -sh /* when I sudo du -sh /* it tends to die on me right after the /usr[/quote]

That's a little disturbing... Are you sshing into the box or doing this locally?  Shouldn't matter either way, just curious.

---

### Post by Kaput1982 on 2010-08-20
I am having a similar problem though on the 64 bit desktop edition.  My hard drive will be reported as full, then after a shut down it is back to normal (it has to be shut down a reboot doesn't do it).  It is a re-occurring problem, but I haven't been able to spot a pattern.

---

### Post by Confucius! on 2010-08-20
What is the size of /tmp? Something my be wrong and filling up your drive.

---

### Post by Kaput1982 on 2010-08-20
It isn't in /tmp.  Disk analyzer says it's in my home directory, but I haven't been able to figure out where.

---

### Post by Confucius! on 2010-08-20
Press Ctrl+H to show hidden files. Then take a look at each folder size. Press it again to hide them again. You could also do a du -ah from the command line. The command du -sh that you ran earlier does not do hidden file that is probably why you did not see it.

---

### Post by damarusama on 2010-08-21
Ok back on this puzzle 

damaru@oni:~$ ls -lah /
total 21M
drwxr-xr-x  22 root root 4.0K 2010-08-02 11:16 .
drwxr-xr-x  22 root root 4.0K 2010-08-02 11:16 ..
drwxr-xr-x   2 root root 4.0K 2010-04-21 12:03 bin
drwxr-xr-x   4 root root 1.0K 2010-04-21 12:04 boot
drwxr-xr-x   3 root root 4.0K 2010-04-23 12:53 build
lrwxrwxrwx   1 root root   11 2010-04-20 18:47 cdrom -> media/cdrom
drwxr-xr-x  17 root root 3.4K 2010-08-19 08:57 dev
drwxr-xr-x 103 root root 4.0K 2010-08-19 16:18 etc
drwxr-xr-x   3 root root 4.0K 2010-04-21 11:27 home
lrwxrwxrwx   1 root root   32 2010-04-20 18:51 initrd.img -> boot/initrd.img-2.6.31-14-server
drwxr-xr-x  11 root root  12K 2010-04-21 15:10 lib
lrwxrwxrwx   1 root root    4 2010-04-20 18:47 lib64 -> /lib
drwx------   2 root root  16K 2010-04-20 18:47 lost+found
drwxr-xr-x   4 root root 4.0K 2010-04-20 18:47 media
drwxr-xr-x   2 root root 4.0K 2009-10-19 19:18 mnt
drwxr-xr-x   3 root root 4.0K 2010-04-22 09:49 opt
dr-xr-xr-x 132 root root    0 2010-08-19 08:56 proc
drwx------   5 root root 4.0K 2010-05-19 16:16 root
drwxr-xr-x   2 root root 4.0K 2010-04-26 16:36 sbin
drwxr-xr-x   2 root root 4.0K 2009-10-19 18:48 selinux
-rwxrwxrwx   1 root root  21M 2010-08-02 16:46 size
drwxr-xr-x   2 root root 4.0K 2010-04-20 18:48 srv
drwxr-xr-x  13 root root    0 2010-08-19 08:56 sys
drwxrwxrwt   5 root root 4.0K 2010-08-19 18:28 tmp
drwxr-xr-x  10 root root 4.0K 2010-04-20 18:48 usr
drwxr-xr-x  16 root root 4.0K 2010-05-19 16:15 var
lrwxrwxrwx   1 root root   29 2010-04-20 18:51 vmlinuz -> boot/vmlinuz-2.6.31-14-server
-rw-r--r--   1 root root 2.1K 2010-05-19 16:15 webmin-setup.out

this is the output :

[http://dl.dropbox.com/u/3372484/output.txt](http://dl.dropbox.com/u/3372484/output.txt)

really weird it tells me that there is only 1.7gb  in use 

I decided to sudo the du -ach but that seems to hang in the middle - I guess getting some disk space of some tmp stuff might crash or something. I'll leave it running for a while and see if it does end. I am in ssh to the server, here is the output and where it hangs :

damaru@oni:~$ sudo du -ach /* >> $HOME/output.txt && echo "Finished"
du: cannot access `/proc/8609/task/8609/fd/3': No such file or directory
du: cannot access `/proc/8609/task/8609/fdinfo/3': No such file or directory
du: cannot access `/proc/8609/fd/3': No such file or directory
du: cannot access `/proc/8609/fdinfo/3': No such file or directory

even the script that was provided earlier hangs on the same place (the script is really nice by the way, I called it sizemeall) :

damaru@oni:/$ /home/damaru/sizemeall 
du: cannot access `./proc/8842/task/8842/fd/3': No such file or directory
du: cannot access `./proc/8842/task/8842/fdinfo/3': No such file or directory
du: cannot access `./proc/8842/fd/3': No such file or directory
du: cannot access `./proc/8842/fdinfo/3': No such file or directory


The sudo apt-get clean stuff have given me a bit of space, but only few mb - which is good. 

What would take space on the hard drive and not show up on the du ?

I know it's simple to resintall the whole server but I did that few time in the last year and now I would really like to understand what is going on :S

thanks for all your help

---

### Post by arrrghhh on 2010-08-22
Anything in /proc won't actually take up space - it's a virtual filesystem.  And du unfortunately doesn't give much ouput - it may be cranking and you don't even know it.  A hdd light on the server is a good indication that it's still working.

---

### Post by TwoEars on 2010-08-23
If you run ```
sudo du -ach /* > $HOME/output.txt && echo "Finished"
``` then upload the file again, it will give a clearer output. Notice only one > this time, to delete anything previously in output.txt :)

My guess at the moment is either huge root-owned folders, a faulty hardware problem or a faulty software problem.

---

### Post by damarusama on 2010-08-25
ok - it's started - will post shortly

---

### Post by damarusama on 2010-08-25
ok thanks for your perssitance - 

I finally found the culprit - the du function took about 20 minutes to finalise a 200mb file. The folder that was full is the ntop folder - I'll look how to stop ntop from getting so much data - hopefully there are some setting to have a maximum disk usage for ntop

thanks again ! 

now got to get to work on ntop

---

### Post by damarusama on 2010-08-26
are you a bot or just making fun of me ?  (in which case I agree that my knowledge with ubuntu laughable)

---

### Post by TwoEars on 2010-08-26
You might want to check those ntop log files, by the way, before you delete them.

If you're running it on a cron job, try setting it to a different period of time.

---

### Post by CharlesA on 2010-08-26
> **damarusama said:**
> are you a bot or just making fun of me ?  (in which case I agree that my knowledge with ubuntu laughable)
It's a bot.

Check the logs and see if there is anything strange going on.

---

### Post by Kaput1982 on 2010-09-01
Quick update.  I found the problem. .xsession-errors.old in my home directory was massive.  64Gb.  I wonder if it's because I'm running gnome shell.  Any ways it isn't that hard to get rid of the file.

---

### Post by arrrghhh on 2010-09-01
Ha, yet another reason to NOT put Gnome on a server....

If you want Gnome, start with ubuntu-desktop, not server.  You can build/run all the same services just as well, plus get a GUI without the headache.

---

### Post by irondesk29 on 2010-09-03
Sorry to hijack this thread, but I'm having the same problem and I can't seem to resolve it following the advice given so far.

It says my OS drive is 100% used but I can't seem to find where all the space is going...
[FONT=Courier New]
[/FONT]```
root@server:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G   34G     0 100% /
none                  971M  224K  970M   1% /dev
none                  975M     0  975M   0% /dev/shm
none                  975M  2.7M  972M   1% /var/run
none                  975M     0  975M   0% /var/lock
none                  975M     0  975M   0% /lib/init/rw
none                   36G   34G     0 100% /var/lib/ureadahead/debugfs
/dev/md0              917G  175G  697G  21% /media/raid
```[FONT=Courier New]
[/FONT]```
[FONT=Courier New]root@server:/# du -sh /*
6.4M    /bin
47M     /boot
4.0K    /cdrom
224K    /dev
7.5M    /etc
32K     /home
0       /initrd.img
0       /initrd.img.old
310M    /lib
16K     /lost+found
175G    /media
4.0K    /mnt
4.0K    /opt
du: cannot access `/proc/18655/task/18655/fd/3': No such file or directory
du: cannot access `/proc/18655/task/18655/fdinfo/3': No such file or directory
du: cannot access `/proc/18655/fd/3': No such file or directory
du: cannot access `/proc/18655/fdinfo/3': No such file or directory
0       /proc
44K     /root
6.3M    /sbin
4.0K    /selinux
4.0K    /srv
0       /sys
20K     /tmp
697M    /usr
161M    /var
0       /vmlinuz
0       /vmlinuz.old
4.0K    /webmin-setup.out[/FONT]
```I've also run "du -ach /* > /media/raid/out.txt" which doesn't show anything different.
Running "apt-get clean" and "apt-get autoclean" didn't help.

What am I missing?

---

### Post by willis11of12 on 2012-07-12
I've found the same problem with my computer, except it's  /home/willis/.xsession-errors as opposed to  /home/willis/.xsession-errors.old.  So is it okay to delete this file?   Or should I just delete it's contents?  Or would doing either of those  things be a bad idea?  Please let me know what you did to correct the  problem.  Thanks!!

---

### Post by willis11of12 on 2012-07-12
So at first I moved this file to another hard drive in case it was important, but then after reading more about this file in another thread it turns out that this file is turned into the "old" file upon restarting the computer and it then makes a new clean slated version of the original and is supposed to have them both cleared out every two restarts then.  Since I rarely restart, I determined there was no serious harm in just deleting it and that's what I did.  I did have to restart the computer though for the folder to recognize that there was a lot more free space again, even though disk analyzer noticed it right away.  Cheers!

---

