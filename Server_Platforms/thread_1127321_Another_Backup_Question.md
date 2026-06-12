---
title: "Another Backup Question"
date: 2009-04-16
forum: Server Platforms
---

### Post by Buntubailey on 2009-04-16
This has probably already been covered but I certainly can't find what i'm looking for. I've just set up a ubuntu server in my small office with only windows boxes connecting to it via SAMBA. I used a simple RAID 1 array. However, I would like to have a program on one of my windows boxes that would pull all the information off the server to another external drive connected to my windows box, say, every sunday night or something when the network is not so busy. Is there a simple program that can do this task, sorry for such a noob question but i can't seem to find anything on how to do this,

Regards,

---

### Post by bruno9779 on 2009-04-16
wouldn't it be easier and quicker if it was the ubuntu server backing itself up?

what you are trying to do is:

server > network > desktopPC > HDD

and :

Server > HDD

would undoubtedly be easier and quicker

---

### Post by Buntubailey on 2009-04-16
The reason I thought of doing it this way was to keep the backup disk separate from the server, I understand that I could just move it after backup but knowing me i will probably get lazy and leave it there then if something were to happen to the server, i.e. flood, fire, then the backup would be safe in another office.

---

### Post by ugm6hr on 2009-04-17
RSync should do this.

Set up the RSync server on the Ubuntu server, and use DeltaCopy on the Windows machine.  You should be able to create a scheduled action for DeltaCopy (I haven't though).

I use this on my FreeNAS server with Ubuntu desktops.  As long as the backup is always Ubuntu server -> Windows PC, this should work OK.

Of course, the other option is to set up a second NAS server as a backup for the first server.  Potentially, this could even be in a different location (i.e. backup over the web by forwarding port 873 TCP), giving greater protection from fire, flood etc.  After the initial backup (which could be done locally), all subsequent backups are incremental, so should not use excessive bandwidth.

---

### Post by BkkBonanza on 2009-04-17
I would use a simple script with rsync and cron. With cron you can setup a periodic mirroring operation to the drive on the other machine. A few lines in a script would do this nicely. For example, it could check if the backup machine is reachable and then do an rsync to it from the server. If Samba is active and you have the backup drive shared then no other tools are needed. Rsync only copies the changed files and even then can compress the data so the overheard and actual copied data would be pretty small unless you have continual big file changes. Doing it this way the backup could always be, say, an hour behind the main server.

Just as another idea, and because I do this too, there is also a cmdline tool for Amazon S3 that would enable making a backup to S3 as part of the process. Not that you'd want to backup everything that way but if you have some core of critical data that you wouldn't want to lose under any circumstances then it's fairly easy to add in a couple lines to keep a copy of that data on S3. It's offsite and so will not be affected by any fire or other disaster. And for small data sets S3 is incredibly cheap. I keep a backup of all my important server files and web site databases there with daily incremental changes for about 30 cents/mo. The same script rotates my logs and several other maintenance tasks.

---

### Post by Buntubailey on 2009-04-18
I am pretty new to ubuntu, and your method sounds like a good solution using cron and rsync. Would anybody be able to point me in the direction of a simple tutorial that may help me to set this method up? That would be great if possible, i have looked around but can't really find anything I can understand.

Many thanks,

---

### Post by BkkBonanza on 2009-04-18
I can give you some info here. There are quite a few tutorials out there. Google can help with that but you will find that often you have to mix-n-match to get want you want as rarely is a tutorial exactly right for what you need.

rsync is fairly easy to use but it does have lots of options that can lead to confusion. There are a few ways to go about this. 

1. Assume backup drive mounted via samba and then rsync to that location.
2. Run rsync daemon on backup machine and rsync direct to it.
3. Run sshd on backup machine and then use that with rsync direct to it.

I think probably option 3 is the most common and simplest one to use. Most always sshd is running on servers anyway, so it makes the process painless. Lets assume that way then. You don't need to setup the rsync daemon nor have samba sharing the backup machine - though you could have it and go method 1.

Typical rsync commands are like this,

rsync -options src dest

where src and dest are machine:/path (and local machine can be dropped)

So if your backup machine has a name "backup" (though an ip works just as well) you can write like this, and test it at the console before getting to cron,

**sudo rsync -vztpre "ssh -2" /var/myfiles backup:/var/myfiles**

Type **man rsync** to read about those options I gave. I'm assuming you will need root for some files, hence sudo, but if all the files are owned by you then you may be able to drop that. 

Briefly options I have are, v=verbose, z=compress w/gzip, t=keep file times, p=keep file permissions, r=recurse subdirs, e=use shell that follows, and I tell it to use ssh with version 2 cipher only. ssh is real nice, and a veritble swiss army knife tool. In this case it knows to start rsync at the other end for you and complete the transfer. So that command will copy files from /var/myfiles on this machine to /var/myfiles on the backup machine. Note that it automatically only copies changed parts so reduces data transferred. If very little or no data has changed in the whole /var/myfiles subtree then only a very brief file check and xfer will occur. 

So that could be close to your basic command here and you can test it manually. Once it works you may want to drop the v option so it doesn't spit out so much text. And, of course, you'll want to use your real file path not /var/myfiles - that's just for example. Also this assumes you have the same user on both machines (you). If not then you will want to prefix the machine with a user name like this, someuser@backup:/blahblah (it will prompt for the user's password).

Next step is to add that to a cron. You should read one of the tutorials on cron out there for background. Any decent tutorial from google:cron should do. What you basically do is type,

**crontab -e**
to start editing your cron file. If you want to run as root then sudo in front. Again you may need that if files are owned by many users.

Now you need to enter a line telling it how often and what command to run. There can be several lines for multiple cronjobs so if some are already present don't erase them but add the new one as a new line. For example,

**0 * * * *  sudo rsync -vztpre "ssh -2" /var/myfiles backup:/var/myfiles**
(I'm going by memory here so I may have the wrong number of * there, please double check - also if you sudo crontab then you don't need sudo in the cron command as it already is running as root)

This will run the cron every hour on the hour. 0 0 * * * would be every day at midnight. (0 minute, 0 hour) You can adapt the values as you see fit. One thing is that crontab has a default editor and I think it's vi on some systems. I don't recall now if Ubuntu uses nano or if I changed mine to nano. In either case you'll have to get very briefly familiar with whatever editor it's configured for. It can be changed and I prefer nano as it's easier to use. So after you save that it will update the cron. You can type,

**crontab -l**
to check it and make sure it's there. So that's the basics. You can fine tune this and add extra details as you figure out more about what you need. While this may seem a bit much at first it is fairly typical of server admin work and both of these tools are really good to know about and very useful, hence, good to jump in and learn. 

If you wanted to use samba or don't have sshd running on the backup machine then it's pretty similar you just leave off the -e "ssh -2" and alter the destination to reflect the samba location in the same way as if simply copying files on the same machine.

There are other refinements too. You could use tar to create dated archives of data and then rsync them for example.

If you get caught up on something then just ask here.

---

### Post by BkkBonanza on 2009-04-18
BTW I just realized you wanted to backup to a Windows machine. It won't have rsync nor sshd installed normally. So you would need to install rsync there using cygwin. There are some tutorials around for that and also at least one easy to install premade package now. I had forgotten about this as I get so used to doing this between linux servers. When I think about times I've setup cygwin on Windows I almost hesitate to recommend this path. I actually think an easier route is to install VirtualBox on Windows and then install the minmimal Ubuntu server into that. It's quite easy and pretty fast to setup and then it has sshd and rsync by default. You can then put the cron in that virtual server on the windows machine (rather than the real server) so that it does the backup whenever it's up and running. But the src and dest values for rsync would be slightly different as you have to indicate the server machine (and user) not the local desktop machine.

Or you may want to read up on a prevoius poster's idea of using deltacopy. I haven't used that but on the windows end it may end up being easier than a plain rsync solution. It sounds like then you would need **rsyncd** installed on the server. Just a note here - **rsync** is a program to copy files (with optimization, only changes) but **rsyncd** is a daemon (background process) that runs listening on a server port for any requests to complete an rsync operation. 

Now I've probably just made everything even more confusing...

---

### Post by Buntubailey on 2009-04-18
Thanks BKKBonanza for all your patience on this. Ideally it would be good to back up to the windows box but there is an alternative if it will save me lots of time and headache, I have one box running ubuntu desktop 8.04, I assume this would be much easier to send the backup files to? 

Anyway, I am no longer in the office as it is late here in asia, but I am testing the rsync method you described to me at home, basically i have a samba share on the server for the windows users called accounts, I want to back this up to my ubuntu desktop machine so I input the command:

sudo rsync -vztpre "ssh -2" /accounts gordon-laptop:/home/gordon/Desktop/backup123

But it is always giving me an error saying no such file or directory. Am I inputting the above correctly or is there some extra software I need to install on ubuntu desktop? once again your help is much appreciated, many thanks.

---

### Post by Buntubailey on 2009-04-18
Here is the exact error I get when trying to backup from server to laptop.

 sudo rsync -vztpre "ssh -2" /accounts //gordon-laptop/home/gordon/Desktop/Backup123
sending incremental file list
rsync: mkdir "//gordon-laptop/home/gordon/Desktop/Backup123" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(594) [receiver=3.0.3]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(635) [sender=3.0.3]

---

### Post by BkkBonanza on 2009-04-18
You've got a typo at //gordon-laptop...
That would be the syntax if using samba but for ssh/rsync it should be,
sudo rsync -vztpre "ssh -2" /accounts gordon-laptop:/home/gordon/Desktop/Backup123

This assumes that gordon-laptop is a valid name. So it would be defined in your /etc/hosts file or by dhcp/dns. If in doubt you can try with the local ip address instead of gordon-laptop. 

Also this assumes sshd is running on the laptop. If it isn't but it is on the server then it can work the other way around. ie. on the laptop do the command like this, 
sudo rsync -vztpre "ssh -2" server-name:/accounts /home/gordon/Desktop/Backup123
(this way it contacts ssh on the server and asks it to start an rsync session).

Also I realized after that if you have a samba share on your windows desktop then you don't need ssh/rsync at all on windows. Rsync can handle it via network share with a simpler command like,

sudo rsync -vztpr /accounts /backup-share-name
(it just copies like a regular filesystem then - that would be the way to do windows backup).

I'm here in Bangkok, it's late too. If you're still up then I'll be around for a while longer.

---

### Post by Buntubailey on 2009-04-18
small world, i live in phuket, i'm sure i'll be in touch soon, many thanks

---

### Post by Buntubailey on 2009-04-18
Hello again,

Ok, I tried below:

sudo rsync -vztpre "ssh -2" /accounts gordon-laptop:/home/gordon/Desktop/Backup123
ssh: Could not resolve hostname gordon-laptop: Name or service not known
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(635) [sender=3.0.3]


So i tried with the IP way:

sudo rsync -vztpre "ssh -2" /accounts 192.168.2.102:/home/gordon/Desktop/Backup123
root@192.168.2.102's password:
sending incremental file list
accounts/
accounts/testquickbooks. (Backup Mar 27,2009  03 11 PM).QBB
accounts/testquickbooks. (Backup Mar 28,2009  02 02 PM).QBB
accounts/vsftpd.tar.gz

So the IP way works, although, I would prefer to use the computer name as the ip could change on the ubuntu desktop in the office as it connects to the network via dhcp, would i have to set a static ip or can i do something to make it recognise the computer name.

---

### Post by Buntubailey on 2009-04-18
Also here is a copy of my hosts file.

127.0.0.1	localhost
127.0.1.1	gordon-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by BkkBonanza on 2009-04-18
It depends on how your names are set. If you have a router doing dhcp to assign dynamic (or static) ips (typical) then it should be settable there. I know that is supposed to work but also on mine it still doesn't seem to do it and I just add a line in /etc/hosts - which is still manual. It may require another setting in Ubuntu so that it accepts it's name from the dhcp server. I didn't explore it further but it would be a setting in /etc/network/interfaces or dhclient.conf I expect. This way at the same time the machine gets it's ip it also gets a name. This works because on other machines when they get a name they ask the dns server in your router where it is. So the other thing is that your /etc/resolv.conf file would have to be set for your router too. This is often by default anyway, it may be something like,
nameserver 192.168.2.1 (if that's your router ip). If there isn't a router between these two machines then it would have to be done manually or by running a dhcp or dns server on one of them.

---

### Post by BkkBonanza on 2009-04-18
I assume that's the hosts file on gordon-laptop since it assigns the local address to that name. But on your server it doesn't know about that setting in the hosts file on your laptop. You either have to add it manually like this,

192.168.2.102 gordon-laptop

or configure something to handle name assignment across the network.

---

### Post by BkkBonanza on 2009-04-18
I was curious so I read up a bit more. It seems by default if you don't have a line in /etc/dhcp3/dhclient.conf like,
send host-name "gordon-laptop"
then it should send the hostname specified in the file /etc/hostname (which I think is set by the hostname command). So I would check that /etc/hostname file and make sure it's correct. 

At boot dhclient should request an ip from your router dhcp server. At that time it should send the hostname and the router should grab it and updte it's local dns server with the info. To check you can use a command like,
**nslookup gordon-laptop**
or
**dig gordon-laptop** (dig isn't installed by default, part of dnsutils, sudo apt-get install dnsutils)
and it should report back the correct local ip. 

If it doesn't then you know it's not quite setup the right way. It will depend on your router (assuming you have one). Mine is a linksys with dd-wrt firmware so it runs dnsmasq which handles both dhcp and dns. When it gets a local name during dhcp it copies it over to the dns half so that names resolve correctly.

---

### Post by Buntubailey on 2009-04-18
Thanks so much you are being extra helpful, I will play with the stuff mentioned above tomorrow, what i have just tried to do was to create a cron job using webmin which lays things out nice and straightforward, although when i put the command in and set it to run the script at the time i asked it to, nothing happened, i purposely put another test file into the server and waited for the minute to arrive that i had set the cron up for. But when i check my backup folder there is no extra file in there, then I was wondering, when i run this script manually it asks for the password of my laptop, how does the cron deal with this password request?

---

### Post by BkkBonanza on 2009-04-18
In this case your best option is to use public key authentication instead of a password. It's a fairly painless 2 step process of generating a key and copying it to the server. If you want to use it in cron then the key would need to have a blank password. So basic steps are,

**ssh-keygen -t dsa**
which will generate a key and put it in your home .ssh directory.

Then use the ssh-copy-id script to send it to the server like this,

**ssh-copy-id gordon@server**
(or whatever user you are accessing as).

After that the ssh/rsync process will run by using key authentication and not need a password.

The best security is to have a password on the key as well and then use ssh-agent to handle the password for repeated sessions. However, when running cron you just don't have a chance to enter the password at any point so often people will create a special user account for handling these automated tasks and give it no login shell so that normal logins won't be allowed but it would have a blank password for the key. This means that anyone who can get into the user account on one machine can access the same account on the other machine because the key is not further protected. This is little different from someone knowing the password for the user on one machine also knowing the same password on the other machine. Keys are more secure than passwords though just by nature of their length.

Regarding your cron job not doing anything. You may see a message in /var/log/messages or /var/log/cron about what happened. I'm sure the lack of password is a problem and I had forgotten about that. I have keys setup on my machines already so haven't run into it for a long time.

---

### Post by Buntubailey on 2009-04-29
Hello BkkBonanza and thanks for all your help, everything is working fine now as you said. one small problem I am having though, is that when I delete things from the server and an rsync command takes place. It doesn't delete anything from the original backup, so it only backs up new files and doesn't take them away when I delete from the server. I understand that there is the --delete command but after playing around with it for a bit today I appear to be doing it all wrong as the command reports errors when I try to use it. For example. The command I used is: 
> sudo rsync -vztpre --delete "ssh -2" /Admin gordon@192.168.2.23:/media/BACKUP/SERVER
I was hoping that when I deleted from the server that this would then delete from the backup but unfortunately not. Can you see where I am going wrong here?

---

### Post by BkkBonanza on 2009-04-29
I think it should work but I'm not familiar with that. I don't use it myself. What is the error message that you get?

From your command it looks like you run as root on the sending side but as gordon on the receiving side. So possibly a permissions error for the deletion of files not owned by gordon? If so, I'm not too sure how best to workaround it except maybe don't keep permissions (remove -p) if feasible. But then they are owned by gordon I believe and it may make it troublesome in a restore.

---

