---
title: "New to Ubuntu Server, some questions"
date: 2011-03-04
forum: Server Platforms
---

### Post by wolfbuddy on 2011-03-04
Hi,

I'm in the process of an Atom based server to use at home as a replacement for a Synology box and I have decided, from what I have read, that Ubuntu Server is the OS I'm going to use. I have a few questions though before I start that I'm hoping some of you gurus can help me with. :)

1. I only have one 2tb drive available to begin with but I want to add a second at some point for RAID1. With the Synology box I know it was possible to add the second drive later and it would create the array without loosing the data on the first drive. Is this possible with Ubuntu Server or do I need to wait until I have both HDDs?

2. All of the PCs that will be accessing the server are windows machines, is SMB the correct and only option or should I be considering another share? the server is used as the main storage point for most stuff, very little data is stored locally.

3. I understand that I only need to install mdadm and webmin, is this correct or are there other packages I should install/consider? 

4. I use my Synology as an ftp as well so that I can access it when I'm not at home, what do I need for this or is this included/an option during installation?

5. Will Ubuntu Server have the necessary drivers for the Atom board I am using or do I need to install these separately? It's a Gigabyte GA-D525TUD that I will put 2GB RAM into.

6. the Atom board is 64-bit, should I install the 64-bit OS or will that make things more complicated?

Many thanks, and apologies if any of these are stupid questions! :)

---

### Post by kgatan on 2011-03-04
Hello,

2. Samba is the way to go when accessing from windows machines. There is some support for NFS on windows 7 but i believe it is limited.

3. Mdadm is installed by default if i remember correctly and webmin is a good compliment for configuration but requires you to have apache installed as well.
You want to install OpenSSH as well for remote terminal login and encrypted FTP.

4. I use SFTP to access my files remotely which uses SSH and is encrypted.
Ex. on free windows ftp software for SFTP is WinSCP.

---

### Post by wolfbuddy on 2011-03-04
Hi, thanks for the prompt reply. I'll look into everything there. :)

If anyone else has anything to chime in on that would be great.

---

### Post by CharlesA on 2011-03-04
Webmin has it's own http server installed and doesn't need apache.

EDIT: You can check out a tutorial I wrote up on my site: [http://charlesa.net](http://charlesa.net)

---

### Post by rubylaser on 2011-03-04
1. Yes, you'll be able to do this later.  Basically, you create a degraded RAID1 on the new disk, then copy the contents of your original disk over to the new one, change your /etc/fstab for mounting, and finally add your original disk to the RAID set.

2. NFS works fine on Windows 7  if you add the Services for NFS.  But, if you don't need fast throughput (greater than 30 MB/s then SMB should be fine for you).

3. mdadm is not installed by default on the Server version.  You'll get it like this...
```
sudo apt-get install mdadm
```

4. WinSCP works fine, or you could setup VSFTPD, but frankly SFTP is easier for a single user.

---

### Post by wolfbuddy on 2011-03-04
Wow this community is brilliantly helpful, thank you for more excellent input. Lots of info there for me to research.

I'm very intrigued by the performance comments of NFS as I am keen to achieve the best performance possible, but have no experience with it. Would I still be able to map the network drive and use it in the same way that I do now with the Synology unit (which I believe works as SMB?).

Does anyone have any comments on the drivers for the Atom board and opinions on whether I should go 32 or 64 bit version of Ubuntu Server?

---

### Post by CharlesA on 2011-03-04
Not sure about NFS, but if you use Samba, you'll be able to map it exactly the same way you did before.

If you have a CPU that supports 64-bit, go with 64-bit. :)

---

### Post by rubylaser on 2011-03-04
Yup, you can map a drive like normal on a Windows machine.  Here are some directions...
```
http://ubuntuforums.org/showthread.php?t=310168
```

---

### Post by wolfbuddy on 2011-03-05
Up and running now. :) 

It took a few hours to get to that stage though as I got stuck trying to edit the sources.list file. I finally realised that I need to use the 'sudo' command otherwise it was opening in read only! ](*,) Well, you only learn by doing so I'm getting there now.

A couple of oddities though. There's a folder called 'lost+found' in my shared folder which I cannot access, any ideas what that's for?

Also, I have found that only the PC that creates something on the share can delete it. I checked in Webmin/File Manager and the folder that I'm sharing doesn't have the option for 'Only owners can delete files' option checked. I'm a bit stuck with that one. :confused:

Lastly, I've noticed that on the status page it says that I have used 95GB but I haven't copied any files to it yet! Also, the status bar doesn't match that. Is it a bug or something?

[IMG]http://img340.imageshack.us/img340/6209/webmin.png[/IMG]

---

### Post by CharlesA on 2011-03-05
lost+found is on any ext* partition. You can find more info about it [here]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html").

Webmin counts total disk space, and that includes the drive that the OS is running on.

---

### Post by wolfbuddy on 2011-03-05
> **CharlesA said:**
> 
Webmin counts total disk space, and that includes the drive that the OS is running on.

Even still, the OS is only about 1GB so I wonder if it should say 95MB? No hang on that doesn't make sense either! :oops:

Anyone got any ideas why I can only delete stuff from the machine that created it? I want to start filling the share but I don't want to do that until I've fixed this issue. I have just let webmin update all the packages so I'll reboot and see if that has fixed anything.

---

### Post by CharlesA on 2011-03-05
It sounds like a permission thing. How do you have Samba configured? I haven't used webmin in a long time, so I'm not quite sure how well it handles Samba.

---

### Post by wolfbuddy on 2011-03-05
Just like in this guide;

[http://www.smallnetbuilder.com/nas/nas-howto/30573-build-your-own-atom-based-nas-part-2?showall=&start=3](http://www.smallnetbuilder.com/nas/nas-howto/30573-build-your-own-atom-based-nas-part-2?showall=&start=3)

---

### Post by CharlesA on 2011-03-05
So you have the permissions set to 755?

How do you have your users set up?

---

### Post by wolfbuddy on 2011-03-05
Yep, looks like that was the key. The permissions were not fully set for the shared folder. There is an option for **Force Unix file mode **and **Force Unix directory mode **so I set these to 775 as well as forcing the user and group for that folder to the same one. Seems to of worked. If I'm honest I'm not 100% what these permission options mean but I'll find out.

Your assistance is very much appreciated Charles, thanks. I'm looking forward to setting up the FTP, trying out NFS and general fiddling about with something new! :D

I'd love to know where my 95GB has gone though.

---

### Post by CharlesA on 2011-03-05
If you've got shell access, you can run this:

```
df -h
```

To see how much disk space has been used.

---

### Post by wolfbuddy on 2011-03-06
OK, thanks. I can run that in webmin. I'll have a look once I've copied all of my data across.

Does Ubuntu server have a recycle bin?

---

### Post by Demented ZA on 2011-03-06
> **wolfbuddy said:**
> OK, thanks. I can run that in webmin. I'll have a look once I've copied all of my data across.

Does Ubuntu server have a recycle bin?

No, Ubuntu server does not have a recycle bin, at least not for files deleted over network through Samba. You however implement this feature by following [this post]("http://ubuntuforums.org/showthread.php?t=155763"). Its further down, posted by FredSambo. I've implemented this a couple of times and it works great!

---

### Post by CharlesA on 2011-03-06
> **Demented ZA said:**
> No, Ubuntu server does not have a recycle bin, at least not for files deleted over network through Samba. You however implement this feature by following [this post]("http://ubuntuforums.org/showthread.php?t=155763"). Its further down, posted by FredSambo. I've implemented this a couple of times and it works great!

Thanks for the link. That looks like a handy thing to have. :)

---

### Post by wolfbuddy on 2011-03-06
Yeah thanks, looks good. It's gone on my ever growing to do list! :-k :)

---

### Post by wolfbuddy on 2011-03-12
Well, it's all going really well (I hope I don't speak too soon!) and that's largely down to the help and advice I've received here. This is such a brilliantly helpful and friendly community. 

So I've set up the recycle bin and it's working brilliantly, albeit it takes ages to empty the content of especially if I do it from my laptop over the wireless network, so I just need to add a script to delete the content locally. Shouldn't be too difficult now that I'm beginning to get my head around the command line stuff.

I've also managed to set up my USB backup drive and get rsync sorted to incrementally backup my shared folder to it, and in NTFS so that I can always plug it into one of my windows machines should anything happen to the server. This was again thanks to a guide, that I found via google, on this very forum. I then added a scheduled task to run the backup script all on my own! :)

I still have a few things to sort out/decide on;

1. Find that missing disk space. Reported used space is 1.23TB but the total size of all folders is 1.14TB. When I set up the HDD, I selected an option to build the RAID array with a missing disk so that I can add it later, because I want to run RAID1 but only have 1 disk at the moment. I'm hoping that when I add the second HDD it will sort itself out, maybe!

2. I've been considering whether I should install an anti-virus onto the server. I'm keen to hear what people's thoughts are on this?

3. I've noticed that the server does not shut down when I press the power button, and I would like it too do so. I'm guessing that I need to run some kind of command so that the OS knows what I want it to do when I press the power button (and reset button as well I suppose). I haven't had a chance to research this yet so if anyone has any ideas that'd be great.

Thanks again, apologies if I'm waffling. :)

Edit; also just remembered that I can't seem to get the cd command to work, any ideas why? I've tried the sudo command first as well.

---

### Post by CharlesA on 2011-03-12
You mean like press and release the power button? I usually just ssh in and run 'halt' if I want the machine to power off.

If you hold it down, the machine will power off. Same with the reset button, press it and the machine resets.

---

### Post by wolfbuddy on 2011-03-13
Yeah, exactly that. If you think it's OK to just power it off, without shutting down the OS, then I'll just leave it. I'm used to being able to set what I like the power button to do with my PCs.

---

### Post by cariboo on 2011-03-13
You could possibly do some damage to the file system, if you use the power button to shut things down. It's far safer to do what CharlesA said, and ssh in and use the halt command. There are several other commands you can use to shut the system down,  have a look at:

[LIST]
[*]shutdown
[*]poweroff
[/LIST]

I'm sure some of the other members will have more suggestions.

---

### Post by wolfbuddy on 2011-03-13
I think I've been slightly misunderstood. I know that it's bad to just power off the system so I want it to run the halt command when the power button is pressed. Just like you can with a Windows machine. That way I wouldn't have to log in remotely just to shut down properly.

It's no biggy, just though it would be something obvious or straight forward. :)

---

### Post by wolfbuddy on 2011-03-17
I'm still struggling to figure out why I am missing space on my arrays. I've added the two 1.5TB drives, that I had previously in the DS210j, and I am missing space from that array too. Not the exact same amount, slightly less, so I think it's a percentage thing. The array is completely empty (apart from the lost+found folder) but windows and Ubuntu is reporting that 60ishGB or so is used out of 1.3ishTB. :confused:

I thought I might try and set it up, in the exact same way, as two separate drives and see if it's a RAID set up thing. If anyone has any ideas, I'm keen to hear them. :)

Thanks

---

### Post by CharlesA on 2011-03-17
What does this say when the array is mounted?

```
df -h
```

---

### Post by wolfbuddy on 2011-03-17
```
**> df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/server01-root
                      3.2G  1.6G  1.5G  51% /
none                  991M  232K  991M   1% /dev
none                  999M  4.0K  999M   1% /dev/shm
none                  999M  1.4M  998M   1% /var/run
none                  999M     0  999M   0% /var/lock
none                  3.2G  1.6G  1.5G  51% /var/lib/ureadahead/debugfs
/dev/sda1             228M   44M  172M  21% /boot
/dev/md0              1.8T  1.2T  575G  68% /mnt/public
/home/nick/.Private   3.2G  1.6G  1.5G  51% /home/nick
/dev/sdf1             1.4T  1.2T  229G  84% /mnt/USBbackup
/dev/md1              1.4T   23G  1.3T   2% /mnt/public2

```

It doesn't make sense why that says 2% used as it is really 6% used, or not as the case may be with it being empty! 68% and 84% is the same as reported in windows and webmin for the other storage spaces.

It's been suggested to me that some space may of been allocated to root for some reason, does that sound feasible?

---

### Post by CharlesA on 2011-03-17
5% is allocated to root IIRC, but I don't think that would show up in df.

---

### Post by wolfbuddy on 2011-03-17
Usage reported in webmin;

[IMG]http://img231.imageshack.us/img231/8996/serverstorage.png[/IMG]

and in windows

[IMG]http://img69.imageshack.us/img69/1344/serverstoragewindows.png[/IMG]

---

### Post by CharlesA on 2011-03-17
Try this: ```
cd /mtn/public2
du -h
```

---

### Post by wolfbuddy on 2011-03-17
> **CharlesA said:**
> 5% is allocated to root IIRC, but I don't think that would show up in df.

Just reading up on the 5% reserved by the system and found this in 'man mkfs'

```
-m reserved-blocks-percentage
              Specify the percentage of the filesystem blocks reserved for the
              super-user.   This  avoids  fragmentation, and allows root-owned
              daemons, such as syslogd(8), to continue to  function  correctly
              after non-privileged processes are prevented from writing to the
              filesystem.  The default percentage is 5%.

```

Do I need that on a storage array?

Could the other missing 1-2% be the journal (haven't figured out what that's for yet)?

---

### Post by wolfbuddy on 2011-03-17
> **CharlesA said:**
> Try this: ```
cd /mtn/public2
du -h
```


```
16K	/mnt/public2/lost+found
20K	/mnt/public2

```

---

### Post by SeijiSensei on 2011-03-17
It would probably be okay to reduce the percentage a bit on really large drives, but I'd never set it zero.  That 5% figure has been the default for as long as I can remember, while drive capacities have grown by orders of magnitude over that same time period.

As for the journal, it's used by ext3/4 filesystems to recover from drive failures like loss of power.  It limits the need to run fsck on a drive if it was not cleanly dismounted.  ext3 was invented to add journalling to the older ext2 standard when drives became relatively huge like they are today.  Without it, an unclean dismount could require hours to check and clean the filesystem before remounting it.

---

### Post by wolfbuddy on 2011-03-17
Would 1% be OK? That's still nearly 20GB on a 2TB array.

I just need to figure out how to adjust it! :-k

---

### Post by CharlesA on 2011-03-17
I set the reserved blocks to 0% on data drives, but that's just me.

---

### Post by wolfbuddy on 2011-03-18
Can it only be changed when creating the file system?

---

### Post by CharlesA on 2011-03-18
> **wolfbuddy said:**
> Can it only be changed when creating the file system?
No, you can use tune2fs. Check out the man page [here]("http://linux.die.net/man/8/tune2fs").

---

### Post by wolfbuddy on 2011-03-18
Great, how does this look?

```
sudo tune2fs -m 0 /dev/md1


```

---

### Post by CharlesA on 2011-03-18
Should work. I'm not sure if the drive has to be unmounted or not, but I always unmount before running any file system commands.

---

### Post by wolfbuddy on 2011-03-18
OK, that sounds like good advice. I have all the data on the full array backed up on the USB drive anyway, just incase! :-O I'll try it out on the empty one first.

Thanks for all the help. :)

---

### Post by wolfbuddy on 2011-03-19
Result! :)

[IMG]http://img600.imageshack.us/img600/9600/serverstoragefixedwindo.png[/IMG]

---

### Post by CharlesA on 2011-03-19
Outstanding. So it was the disk space that was being reserved for root?

Learn something new every day. :)

---

### Post by wolfbuddy on 2011-03-19
Yep, and I ran that command on the full array as well and it recovered 5% back from there as well, no problems.

---

### Post by CharlesA on 2011-03-19
Awesome. Glad you got it sorted. :)

Don't forget to mark yer thread as solved if everything is working now.

---

### Post by wolfbuddy on 2011-04-29
Quick update to one of my earlier issues. To get the power button on the case working to shut down the machine properly I installed the acpid package and started the service. 

```
apt-get install acpid
service acpid start

```

:)

---

### Post by wolfbuddy on 2011-08-27
Apologies for bumping this thread but I've come across an issue with my Server build that I can't find an answer to elsewhere.

It appears that for some reason, my Ubuntu server install has grown without me realising and now the OS drive is full (4GBish) so I keep getting error messages in Webmin about 'no space left on the device'. This means that I can't apply any of the updates that are available.

Does anyone know if there are a load of temp files somewhere that need deleting or some way I can free up some space? Any help is much appreciated. :)

---

### Post by CharlesA on 2011-08-27
You can run this to find out what is using most of your disk space:

```
du --max-depth=1 -h / 2> /dev/null
```

You'll get permission denied errors if you run it as a non-root user, but you can ignore them (which is why 2> /dev/null is there).

---

### Post by wolfbuddy on 2011-08-27
Thanks for the prompt reply Charles.

Nothing happens when I run that command, just returns to another line. I tried with sudo first as well and nothing. :confused:

---

### Post by CharlesA on 2011-08-27
Hmm, try it without the redirect:

```
du --max-depth=1 -h /
```

---

### Post by wolfbuddy on 2011-08-27
OK, I found some commands to show the size of each folder and I've narrowed it down to /var which is nearly 2GB and then in that is /var/mail/root which is reported as being almost 1GB.

I tried to delete the mail for root with.........

```
cat /dev/null > /var/mail/root
```

...........but it returned a permission denied message so I edited the permissions for that file and tried again. This time it worked but upon checking the size of the file it was still 82M so more investigation needed.

I only use the mail server for sending me emails about system problems, updates etc so are copies of these all stored here?

Edit; I've found that I can read the mail that is in this file now that I have changed the permissions for it but I can't delete the remaining messages. They are all from 'Cron Daemon'. :confused:

---

### Post by CharlesA on 2011-08-27
They are mails to tell you if cron failed or succeeded iirc.

---

### Post by wolfbuddy on 2011-08-27
Right, I see. Well, I've managed to delete all of the remaining mail so I just need to figure out how to alter the settings so that mail for cron jobs is sent to my email address like the RAID ones do. Otherwise I'll have to remember to keep deleting them on a regular basis.

---

### Post by CharlesA on 2011-08-27
I think the default for cron is to send it to the owner of the cronjob.

Check out the page here: [http://www.cyberciti.biz/faq/linux-unix-crontab-change-mailto-settings/](http://www.cyberciti.biz/faq/linux-unix-crontab-change-mailto-settings/)

On my server I just set the cronjobs for redirect to /dev/null so they don't send mail.

---

### Post by wolfbuddy on 2011-08-27
That's brilliant, thanks. :) There are lots of options in webmin for the cron jobs but not for the emails it sends. 

I've added the line MAILTO=*myname*@gmail.com to the crontab file. I'll just have to wait and see what happens. :popcorn:

Also, now that I have freed up some space on the OS drive, I have restarted the minidlna server and that is working properly again now. :)

---

### Post by CharlesA on 2011-08-27
Awesome, glad you were able to get it working. :)

---

### Post by wolfbuddy on 2011-08-29
Only thanks to your, as valuable as as ever, assistance. :)

---

### Post by wolfbuddy on 2011-09-17
Just a quick question. If I wanted to set up a mail server on my Ubuntu Server, where would I look for information? Is it a simple enough process? I'm kind of assuming it would be because I am already receiving mail from it about admin stuff.

Apologies if this is a stupid question but I've never studied e-mail systems. I tried to research it but found all sorts of outdated and fragmented information.

Thanks. :)

---

### Post by CharlesA on 2011-09-17
It shouldn't be too hard to set one up. I use exim as a gmail relay since my ISP blocks port 25 in order to prevent spam (and their ToU prohibits the running of servers, which is why mine is not hosting my web site)

If you are already getting email, then it would seem that it's already set up. ;)

---

### Post by wolfbuddy on 2011-09-17
Hmm, do I need to check with my ISP then?

What I was hoping for was to have a fully personalised email address. Like *wolfbuddy@wolfbuddyshouse.co.uk* sort of thing and be able to get them on my phone's mail client. So will my server be a pop server or something like that? It appears to be running the postfix mail server and the emails I get about package updates come from *webmin@server1* (no .co.uk or anything and *server1* is the name I gave to the server when I set it up). Just trying to understand how it all works.

The other thing I just thought is that I will need to find the locations for mail storage as I would imagine the defaults will fill up my OS drive again?

---

### Post by CharlesA on 2011-09-17
I'm not sure about that. If you have a domain name, you could probably set up the mail server to send from that, but I don't have any idea how to do that.

I found a [page]("http://rimuhosting.com/support/settingupemail.jsp?mta=postfix") a while ago but it seemed a bit over my head at the time. I just use exim and leave it at that, less stuff for me to deal with. :p

---

### Post by wolfbuddy on 2011-09-17
It was all the stuff about MX records etc that I wasn't sure about and finding information on it in layman's terms appears tricky. Lots of studying may be required for this one then! 

Thanks for the link, looks like a good one.

---

### Post by CharlesA on 2011-09-17
That was what confused me too. At least there are docs about it. ;)

---

### Post by ulnagar on 2011-09-19
Wolfbuddy. Hopefully I can be of assistance. The document at this link: [HowToForge.com]("http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2") shows you how to install the "perfect" server. I have used Falkos documents to build my last 3 Ubuntu Servers without any fuss. There will be certain features in there that you don't need, but you shouldn't have too much trouble finding them and skipping over them.

The MX records for mail servers are for DNS. If someone was to send you an email at [email]wolfbuddy@wolfbuddyshouse.co.uk[/email] the server that was sending the email would need to know how to find your server to give you the email. The MX record basically says "any emails for anyone from @woldbuddyshouse.co.uk needs to go to this server".

I ran my own mail server at home for a few years, but in the end I just ended up redirecting it to gmail. I have a free account there with over 7gb of space. I changed my MX settings so that any email that is sent to my private domain goes to a single gmail account, and I can then get the gmail account on any pc worldwide, or even on my phone, tablet etc.

I don't know what DNS hosting you use, but check out [ZoneEdit.com]("http://www.zoneedit.com/"). They have a free service that can manage your A, MX and other DNS entries with an easy interface.

If you need any other help, let me know. I have had an Ubuntu server sitting in my loungeroom for the last 3-4 years and have reinstalled the thing from scratch atleast twice a year since then. I am about to build a new server using the GA-D525TUD (which is how I found your post) with a 4x2tb Sata Raid5 array so I can retire my old box.

---

### Post by wolfbuddy on 2011-09-19
> **ulnagar said:**
> Wolfbuddy. Hopefully I can be of assistance. The document at this link: [HowToForge.com]("http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2") shows you how to install the "perfect" server. I have used Falkos documents to build my last 3 Ubuntu Servers without any fuss. There will be certain features in there that you don't need, but you shouldn't have too much trouble finding them and skipping over them.

Thanks for the reply, I actually have the server all set up and running brilliantly now and have done for some time. I just use this thread to discuss the services I am choosing to add gradually, like recycle bins, dlna and mail. That link is very good though and I will certainly keep it for future reference. 

> **ulnagar said:**
> The MX records for mail servers are for DNS. If someone was to send you an email at [EMAIL="wolfbuddy@wolfbuddyshouse.co.uk"]wolfbuddy@wolfbuddyshouse.co.uk[/EMAIL] the server that was sending the email would need to know how to find your server to give you the email. The MX record basically says "any emails for anyone from @woldbuddyshouse.co.uk needs to go to this server".

I ran my own mail server at home for a few years, but in the end I just ended up redirecting it to gmail. I have a free account there with over 7gb of space. I changed my MX settings so that any email that is sent to my private domain goes to a single gmail account, and I can then get the gmail account on any pc worldwide, or even on my phone, tablet etc.

I don't know what DNS hosting you use, but check out [ZoneEdit.com]("http://www.zoneedit.com/"). They have a free service that can manage your A, MX and other DNS entries with an easy interface.

This has really helped me get a better, basic, understanding of how mail system works. It's definitely food for thought and I still have more reading to do before I decide if I want to run my own mail server. Can I ask, did you find there was no way to use your mailserver as a pop server so that you could get your emails on your phone? This is a deal breaker for me I think if it's not possible.

> **ulnagar said:**
> If you need any other help, let me know. I have had an Ubuntu server sitting in my loungeroom for the last 3-4 years and have reinstalled the thing from scratch atleast twice a year since then. I am about to build a new server using the GA-D525TUD (which is how I found your post) with a 4x2tb Sata Raid5 array so I can retire my old box.

Thanks again for your reply. Just like yourself, you'll find there is always some knowledgeable soul around here that is willing to help out. :) Good luck with your new build. Actually, I just realised that I never posted that much information about the hardware for mine;

This is the case I used. It's very quiet since I added an adapter to reduce the speed of the big fan on the back.

[IMG]http://img233.imageshack.us/img233/1449/388601l.jpg[/IMG]

Motherboard

[IMG]http://img39.imageshack.us/img39/8238/gigabytegad525tudextra1.jpg[/IMG]

And the IDE module for OS storage

[IMG]http://img846.imageshack.us/img846/3189/ak166504r.jpg[/IMG]

It's now got 2x1.5tb in RAID1 and 2x2tb in RAID1 in it but is fast filling up! :D

Lastly a shot of the brilliant browser based admin tool Webmin that I use.

[IMG]http://img202.imageshack.us/img202/6209/webmin.png[/IMG]

Total cost of the build (without HDDs) was £225. :)

---

### Post by ulnagar on 2011-09-19
> **wolfbuddy said:**
> Can I ask, did you find there was no way to use your mailserver as a pop server so that you could get your emails on your phone? This is a deal breaker for me I think if it's not possible.

I actually used an IMAP server configuration, since it doesn't do a local-copy of the mailbox, but either POP or IMAP will allow you to use them from mobile devices. My concerns were with the high availability needs of a mail server (if the server is not connected to the internet when the email gets sent, there's a risk it'll just get lost/dropped/rejected) and the costs associated with finding an ISP that allows servers to be run over ADSL, etc. In the end, the GMAIL solution really trumped it. It's free (other than the domain name) and you don't have to worry about configuration, updates, etc etc.

I have actually purchased the exact same case and mobo (just waiting for it all to arrive) but I am considering using a small portion of the RAID set as the OS. It basically runs NFS, SMB, DHCP and DNS (internal only) plus my torrent server.

I've used WebMin before, however I found that you need to use the packages it expects otherwise it wont be able to configure them. e.g. the FTP Server they can configure didn't have all the features I wanted so I had to use another one. Since WebMin couldn't configure it, there didn't seem to be much point in using it. It's great if you're happy to use the packages it expects, however.

---

### Post by wolfbuddy on 2011-09-19
> **ulnagar said:**
> I actually used an IMAP server configuration, since it doesn't do a local-copy of the mailbox, but either POP or IMAP will allow you to use them from mobile devices. My concerns were with the high availability needs of a mail server (if the server is not connected to the internet when the email gets sent, there's a risk it'll just get lost/dropped/rejected) and the costs associated with finding an ISP that allows servers to be run over ADSL, etc. In the end, the GMAIL solution really trumped it. It's free (other than the domain name) and you don't have to worry about configuration, updates, etc etc.

Your comments on running a mail server reliably are similar to those I've read elsewhere, and I think the reason I'm still undecided. I don't have any issues with my ISP as they don't block any traffic and I have a fixed IP. Ideally, I'd like to set it up to try and see how I get on running it. Just send and receive some test emails for a few weeks and see how I get on. Which mail server did you use, postfix?

> **ulnagar said:**
> I've used WebMin before, however I found that you need to use the packages it expects otherwise it wont be able to configure them. e.g. the FTP Server they can configure didn't have all the features I wanted so I had to use another one. Since WebMin couldn't configure it, there didn't seem to be much point in using it. It's great if you're happy to use the packages it expects, however.

This seems to be the main issue with Webmin, the limited availability of packages. I've even found packages where I've needed to edit the config files directly to get it to do what I want.

Still, it means that that those that are supported are simpler to admin as well as things like the file browser which makes life easier for someone with less experience, like me. Also, it doesn't stop me from using other packages that can't be accessed with webmin.

---

### Post by ulnagar on 2011-09-19
> **wolfbuddy said:**
> Which mail server did you use, postfix?

I used Postfix and Courier. I experimented with LDAP, mySQL and other authentication and account methods. If you want to check it out you can read the How To I linked earlier and just ignore everything that isn't related to the mail server functions.

---

### Post by wolfbuddy on 2012-01-09
Upgrade time! :)

At the moment I have 2x2tb in RAID1 and I'm thinking of adding 2 more for 6TB in RAID5. If I add the two drives will it be able to rebuild the array to RAID 5 without loosing any of the data, or do I need to transfer all the data elsewhere first and then copy it back again? I know that linuxRAID is very clever and I figured it might be possible with to do that with it.

---

### Post by CharlesA on 2012-01-09
Not sure how that would work, but make a copy of your data in case you need to rebuild the array.

Also, I would suggest running RAID6 with 4 drives, since you can handle 2 drives going down, but you do lose quite a bit of storage capacity, since you are using 2 drives for parity. RAID5 would probably work fine if you have backups and would give you 6TB of storage space instead of 4TB with RAID6.

---

### Post by wolfbuddy on 2012-01-09
Hmm, I was really thinking of RAID5 so that I get the extra space due to the really high HDD prices. So RAID5 can only handle one drive failing? I didn't know that, needs some more thought then!

---

### Post by CharlesA on 2012-01-09
> **wolfbuddy said:**
> Hmm, I was really thinking of RAID5 so that I get the extra space due to the really high HDD prices. So RAID5 can only handle one drive failing? I didn't know that, needs some more thought then!
Yeah, RAID 5 can only handle 1 drive going down. That's what I run on my server, but I only have 3 drives in the array and do a backup daily.

---

### Post by wolfbuddy on 2012-01-09
Thanks for the advice.

I don't have any way of backing up that much data but with the price of drives now I really want to maximize the space. The 2TB drives that I bought last year are twice the price now! :(

I suppose that I just need to decide how much of a risk it is and whether I'm happy with that.

---

### Post by CharlesA on 2012-01-09
> **wolfbuddy said:**
> Thanks for the advice.

I don't have any way of backing up that much data but with the price of drives now I really want to maximize the space. The 2TB drives that I bought last year are twice the price now! :(

I suppose that I just need to decide how much of a risk it is and whether I'm happy with that.
Understandable. I guess the best thing to do would be to backup the stuff you can't replace and go from there.

---

