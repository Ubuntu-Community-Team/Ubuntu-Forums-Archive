---
title: "extending the file system partition?"
date: 2010-08-24
forum: Server Platforms
---

### Post by =ChAoS= on 2010-08-24
Hi, I'm still pretty new to servers and ubuntu and have ran into something i could see being a problem in the future. On a dedicated remote server I have installed a web server using the "How To Forge - Perfect server set up for ubuntu 10.04 and ispconfig". I have a forum and email up and running and shoutcast radio and teamspeak3 servers also. We can also nx into it if need be.
 
I can reformat the 1T hdd remotely from my provider control panel and ssh is installed at the same time and a new root password is sent via email. the thing is i now realise that by default the file system is written to a 10gig partition. This might usually be ok but ispconfig uses the /var/www folder on the file system to house the forum i host and the partition is filling up. 
 
My mate i co rent with is talking about starting a parrot/bird owners forum and i might eventually like to have a gaming forum as well. I realise i should probably have set things up differently but like i said im new at all this and tbh the home directorys never going to have much in it so theres 900 gig doing nothing. 
 
So my question is can i use anything to enlarge that partition remotely? I know theres gparted on disc and all the articles i found say i need to use a disc which obvously is out of the question so what i think i need is some sort of partition magic for ubuntu. I would really like to expand it so all my current files etc on it would stay as is. 
 
Could someone please tell me if this is possible?
 
I'm also currently looking into back up methods and wondered if that would be the way to go? Back up my file system and home directories and then reformat and make the partition larger?
 
Or could i copy the entire www folder to a newly created folder in /home and re write the site enabled files to point to it? Would this work and if so what else would i need to edit?
 
If i'm talking nonsense please tell me but if there is a way i'm prepared to try.
 
Thanks =ChAoS=

---

### Post by BkkBonanza on 2010-08-24
You don't need to resize/re-partition. 
The easiest way to solve this is by either changing your mounts or with symbolic links depending on what you really want to do.

eg.
/var/www contains a variety of sites
/var/www/site1
/var/www/site2
etc.

The simplest solution is to rename /var/www/ to /var/old-www. Then change your 900G partition to mount at /var/www instead of where it mounts now (/home maybe?) by editing /etc/fstab. Then move the files from /var/old-www over to the new /var/www mount. Now they are on the 900G partition mount at /var/www as needed.

( step by step )
mv /var/www /var/old-www
mkdir /var/www
sudo nano /etc/fstab  (and change /home to /var/www)
umount /home
mount /var/www
cp /var/old-www/* /var/www
(check all works ok before removing /var/old-www)
(also this now leaves /home in the same partition as root)

It's also easy to resolve this using symbolic links if you don't want to move everything over. eg. mkdir www dir on the 900G partition and copy over only some subdirs from /var/www to that new dir. Then add a symbolic link to map the location. Let's say the 900G partition is mounted at /home, then,

(step by step)
mkdir /home/www
mv /var/www/site1 /home/www
ln -s /home/www/site1 /var/www/site1

causes all access to /var/www/site1 to instead find files at /home/www/site1

It is a good idea to have logs, tmp and web data on a separate partition from system (root) partition so that if something goes crazy and consumes all the space it doesn't bring the system to a stop.

(You may have to use sudo for these commands depending on permissions. Actually you will have to fix up permissions on most of these dirs after to make the web access work correctly. They need to be the same as the current /var/www permissions. So the above steps are a rough outline only.)

---

### Post by =ChAoS= on 2010-08-24
Thanks for the reply and the instructions. It all sounds straight forward enough and would solve my issues. I know it could have been set up different originally i set it up so the sites were in /home but after a problem went the ispconfig root.
 
Would either of these solutions cause a mysql problem and would i have to change any permissions as the forum folders are owned by client9 etc as set up by ispconfig? And is leaving home in the same partition a bad thing?
 
Thanks =ChAoS=

---

### Post by BkkBonanza on 2010-08-24
Check my last post as I edited it after and added a bit.
You can do the same for your mysql data dir. It usually is separate from the web sites.
eg. often it's located at /var/lib/mysql/data
and you could make a new /home/mysql and then copy files over and add a symbolic link so that mysql can get them there. Likewise, the permissions would have to match up the same to work. Usually they need rw perm for user mysql, but best thing is to make sure any new dirs match perms with the old ones.

Changing the locations of /var/www would not directly affect mysql. So it's up to you if you want to move mysql. Actually, often the mysql data is much larger than the web site files so it may be that you want to leave the /var/www where it is and just move the mysql data dir.

---

### Post by theDaveTheRave on 2010-08-25
Hello all.

This is something that I have been annoyed with in the past and ultimately used the solution as suggested by BkkBonaza.

However be careful when adding in a physically new disk to your system, and putting this into the same mount point will case the info on the old one to 'dissappear' (unless as BkkBonanza says you rename the original folder).

Apparently on the 'alternate install' CD the ability to 'extend any disk / partition' onto another is possible, however with the standard 'graphical install' (which I assume is the more common install method) this function isn't possible.

It is something that would be nice to add, but currently isn't causing me any real issues. Until I start using MythTV in real anger my 40GB of server disk space is just fine!

anyway that is me adding my few pennies worth.

David.

---

### Post by =ChAoS= on 2010-08-25
Thanks Rave i'll bear the adding drive bit in mind when i try out ubuntu on my home desktop pc (which is gonna be a test as i'm a gamer :p) but thats not an option on my server as it is remote. 
 
I'm just reviewing if my gaming will suffer greatly on my newly built desktop which consists of ... AMD Phenom II X6 Black Edition 1090T, MSI 890GXM-G65 AMD 890GX and 8 gig of ocz DDR3 1600MHz AMD Black Edition ram. It currently has 1x1T sataIII hdd with the os etc on and my older 1T sataII hdd with data. I want to add 2 more 1T sataIII hdds and making raid 5 with them and just having a smaller hdd for the os/os's if i dual boot. 
 
I'm just preparing to try BKKBonaza's suggestions on the server before i set up dual boot on my desktop. 8-[

---

### Post by =ChAoS= on 2010-08-28
OK i was busy with other things and today i went back to this issue of gaining more space for my forum. As i explained before ispconfig installs sites/forums in the default /var/www folder and this in my case is restricted to a default 10gig file system partition pre installed by my provider on a 1T hdd. I had took a look about and thought this might work ...
 
I copied the complete /var/www folder to /home. The folders/files included were ...
 
apps, clients, ispconfig, php-fcgi-scripts, vencha.org (my sites folder), webalizer and webmail. There was also index.html and index.html.1. 
 
All these folders were made either when i installed them or by ispconfig. I made sure all owners/permissions were intact and then set about editing the sites-enabled files. I edited all /var/www references to /home/www and then reloaded apache. 
 
Everything worked fine with no apache errors and i could still access the ispconfig web page and all the other items worked ... except for my forum. I got a 500 - Internal server error.
 
Could someone please tell me if i'm looking at this too simplistically or if i'm on the right track? Also would mysql be an issue or should that just work seeing as it wasn't moved or touched? 
 
I felt i was nearly there and yet just this one error caused me to re write the "sites-enabled" files back and all was well again. If i was close, it doesn't take long to edit them back and anything else that might be needed. I get the feeling ispconfig could have created a new site folder in /home/www but that would mean starting my forum over again.
 
Any ideas please?
 
Thanks =ChAoS=

---

### Post by BkkBonanza on 2010-08-28
There is probably some hard coded config paths in the forum config file(s). If you can locate the forum config and view it, you may see paths like /var/www/... and would need to fix'm up to the new location.

Often 500 error is caused by php settings or a php file not being run correctly. That's why I would suspect an incorrect setting in the forum config.

---

### Post by =ChAoS= on 2010-08-29
I was wrong about ispconfig. I changed it back and again got the 500 error and when i went into ispconfig and created a new account it made it in /var/www. It seems theres something i need to change in ispconfig to look for the forum in /home. 
 
So i either need to find out what to change, probably on the ispconfig forum or remove it completely tho i'm wondering if the latter would stop my forum from working? I'll check there site and see.

---

### Post by =ChAoS= on 2010-08-29
Ok so i got a reply on the ispconfig site and was told it was best to [**Follow This Tutorial**]("http://www.howtoforge.com/forums/showthread.php?p=236150#post236150")
 
I'm not sure what size the /home directory would end up? I'm presuming that /var now becomes 900+gig? 
 
If so is it possible to cut my existing 900gig home directory in half and swap /var to that?
 
Thanks for any replys =ChAoS=

---

### Post by theDaveTheRave on 2010-08-29
Chaos,

if BKKBonanza is correct regarding the php config stuff (and I have no reason to think he is wrong), it may simply be a part of the apache config.

Apache allows perl scripts to run only from certain locations, the same may also be true for php, if you moved everything over to your < /home/www > you need to make sure the relevant apache config line is adjusted also.

so the apache config file is...

```

/etc/apache2/httpd.conf
```

If I'm correct you need to check the < UserDir > directive, and point it to your new location.

For the php stuff you may need to change the <filesMatch ./php> also, but as I say I'm not sure.

However I don't know if a perl error would give the same result, in which case you definately need to look into changing the location where perl scripts can run from, this is part of the <Directory> directive, and you will need to point this also to your new /home/ directory.

As I say, you'll have to test each of these as I may not be correct regarding the php conifg with regard to apache.

Also you may need to check the php config file directly, I don't have any notes close to hand on this though, so I will have to leave you too search it for yourself, sorry...

hope this may help put you in the correct direction, or at least someone else may say that this info is wrong and stop you going down a blind alley..

David

---

### Post by =ChAoS= on 2010-08-29
Yeah cheers rave it seems it is. The tutorial on the other page is said to work only it leaves my /home directory on the 10gig partition. I'm looking into using the idea posted but trying to partition the 900gig in half and moving /var to that. I'll let you know how i get on lol

---

### Post by =ChAoS= on 2010-08-29
Ok this is where i'm at ... 
 
I have split my 900 0dd gig home directory in 2 and mounted the new partition at / and called it data.
 
I have used the command cp -r /var /data to copy said files over.
 
Now i need to use e2label to swap partition labels. The command used is (change /dev/sda# to suit) ...
 
```
e2label /dev/sda3 /var
e2label /dev/sda5 /data
```
 
This is where i'm a little confused. I can obviously see the data mount but not any var mount. Will it just find it if i use /dev/sda1 /var where my file systems mounted? I just need to check before i bugger any thing up. :lolflag: What i have so far is ...
 
/dev/sda1 * 1 1275 10241406 83 Linux <= File system i'm guessing?
/dev/sda2 1276 65975 519702750 83 Linux <= /home
/dev/sda3 121536 121601 523488 82 Linux swap / Solaris
/dev/sda4 65976 121535 446285700 83 Linux <= /data - The one i created
 
Thanks for any help =ChAoS=

---

### Post by theDaveTheRave on 2010-08-30
Chaos

I've just had a thought, can you not simply link the contents of your external HDD to the local drive, then whatever is in there will appear in (to the computer) to be in the  principle directory? Then all you need to do is point your forum's config info to write to the sup partition of the 1TB drive? Or is this techicaly incorrect / impossible?

I have done something like this to enable jsp pages to be served from the correct location on the apache server (where editing requires root permisions), but so as I can easily edit them from within my /home directory - and so I don't risk accidentally buggering up some other config file if I need root permissions for opening an editor


also if you are playing with your mount points remember the community docs at [HTML]https://help.ubuntu.com/community/Fstab[/HTML], and the forum help here [HTML]http://ubuntuforums.org/showthread.php?t=283131[/HTML]

David

---

### Post by BkkBonanza on 2010-08-30
The drive labels have no bearing on where they get mounted.
You can mount a drive to any location with the mount command, eg.

**sudo mount /dev/sd4 /data**
or
**sudo mount /dev/sd4 /var/www**

The target directory must exist.

If you mount it where there is already data the data is not "lost" it is just temporarily "covered up" by the new mount. Use **umount** to unmount it and the original data is still there.

Once you have it where you want then you want to record the mount position in /etc/fstab if you want it to mount on booting in future.

---

### Post by =ChAoS= on 2010-08-30
@ Rave ... Thanks for the input mate but this is about increasing the size of the /var/www folder where my forum/other sites are stored on a remote rented server so there's no usb whatever involved just 1 x 1TB internal. :wink:
 
@ Bkk ... Thanks i'm still new at this untill 1 month ago i had never messed with either a server of this kind or ubuntu so im learning all this in an effort to run it enough to suit my needs. 
 
The original post ... [**HERE on Sourceforge**]("http://www.howtoforge.com/forums/showthread.php?p=237953#post237953") is about swapping the usual /var directory which is confined by the non expanding file system partition, in my case 10gig, with the /home directory that can use the rest of the drive. Seeing as i wanted to keep half the 900gig left for /home i created a 400gig /data directory for the swap. 
 
From what Bkk as said and what it appears in the post it doesn't seem to matter as long as the path is correct. In the example using e2label to swap partition labels I was just a little confused as i could clearly see the /dev/sda2 /home entry but not a dev/sda# /var entry. 
This is the example swap ...
e2label /dev/sda3 /var
e2label /dev/sda5 /home
 
The /data drive is mounted its just the label part i'm confused with.

---

### Post by =ChAoS= on 2010-08-30
Ok so i think i've screwed things up. I had mounted /var at /dev/sda4 so i thought and done everything right. I rebooted and now nothing works. I tried un mounting it again but still nothing. Ssh, teamspeak and my shoutcast server are working fine but no ftp apache or nx.
 
I checked the mounts with putty and it seems that var is still mounted but i can't unmount it as it says the device is busy. Is there a command i can force unmount with? Or how do i find whats ruuning so i can stop it?
 
Does anybody please know what i should try before i just reformat and start again?
 
Thanks =ChAoS=

---

### Post by BkkBonanza on 2010-08-30
Change the settings in /etc/fstab and reboot. While program have open files on /var it will be busy and not allowed to be unmounted. But when the system boots and sets mounts according to /etc/fstab the changes will take effect.

I can't see what you've done so have no idea now what may be wrong. If the /var/www directory doesn't have the same contents as before you changed the mountings then likely that is why the web/ftp stuff isn't working. But you should be able to fix that by copying over the previous (correct) content - and it's very important the permissions are as as before as well, including /var and /var/www if changed.

btw, you have the terms backwards. It's /dev/sda4 (the device) that is mounted at /var (the mount point). I know what you mean, or at least hope you did it that way, but confusing when worded backwards.

---

### Post by =ChAoS= on 2010-08-31
Thank you Bkk that did the trick. 
 
I wasn't thinking clearly and used a combination of storage device manager and putty commands to try to change things. Thats the noob coming out. :lolflag:
 
After changing fstab i was able to log into nx and change what i did there. Alls back as it was and the sites back. I tend to do these things over night when its quiet and sometimes i'm a bit tired and not thinking properly.
 
So i'm back where i was but atleast everythings working. Time for some more reading i think before trying to move /var again. 
 
As for the backwards bit, i'm not sure what you mean but yeah that would be a typo on my part.
 
I tried to leave a thank you on your profile but i haven't made enough posts yet. So again ..... THANK YOU for all your help.

---

