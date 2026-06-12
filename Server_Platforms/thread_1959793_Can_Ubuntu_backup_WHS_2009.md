---
title: "Can Ubuntu backup WHS 2009?"
date: 2012-04-16
forum: Server Platforms
---

### Post by Alistair C on 2012-04-16
Abosolute Ubuntu novice alert . . .

I've set up a Windows Home Server in my small office mostly because of ease of use. It seems to be running fine and the simple hd plugin feature to add server space seems to work well for most drives.

I live in a country with crime problems and want to back up the server itself. Since it has a 1tb drive and a 2tb drive, it seemed obvious to purchase a Seagate 3tb drive, insert it into an hd enclosure and add it as a USB drive to WHS as a drive which is used to backup the server.

My bad.

WHS only sees this drive as 800gb or there abouts. Apparently there is no way of getting my version of WHS to see the 3tb drive at all!

As a workaround, I formatted the drive inside an Ubuntu computer into two partitions - 2tb and 1tb. While WHS could see the first, smaller partition, the larger partition was not seen. Also, the whole setup seemed flakey and not something one would want to be used for backups.

As an absolute Ubuntu beginner I was most pleased to get the wife's netbook talking to the WHS server. It's accessing the printer and shared folders just fine and it's also run an Ubuntu backup to its user folder. 

So, I was wondering if I could use the wife's netbook as a go-between to backup the server in the other direction back to the USB drive.

The long way around would be to copy all the files and folders across and back to the USB drive through the netbook manually.

I was hoping there was a more streamlined way though? 

On Ubuntu, is there some kind of backup software that would basically run a task to copy all folders from the server back to the 3tb usb drive (or a partitioned 1tb and 2tb split drive)?

I like the way Ubuntu stores the home folder on the WHS server in a neat zipped package. Any way of getting the same result running in the other direction - pushing the WHS stored folders back through the network in the other direction?

Advice and assitance much appreciated.

Regards
Alistair C

---

### Post by CharlesA on 2012-04-16
I think the problem you are going to run into is the way WHS deals with drives - with the space expander thing. You'd probably be better off just hooking the 3TB drive to another machine and copy from the WHS box to the external over the network, which could take a very long time.

You could clone the drive but the data wouldn't be readable until you restored it, so that is probably not an option.

EDIT: With all that being said - I haven't really dealt with WHS outside of looking into it briefly and deciding it wouldn't work for my needs.

---

### Post by Gyokuro on 2012-04-16
Hi

The WHS 2003 supports only 2TB drives - so you have to share the drive through your wifes netbook.

1.) setup SAMBA on your wife's netbook (be cautious with her data - angry wife is more dangerous as everything else)

2.) write a script to copy the files with robocopy and place it on your server (maybe this link is useful: [http://www.howtogeek.com/53144/windows-home-server-backup-to-lan/](http://www.howtogeek.com/53144/windows-home-server-backup-to-lan/))

3.) scheduling the robocopy task (link: [http://social.technet.microsoft.com/Forums/en-US/ITCG/thread/ec6c84d1-0e4b-4710-a60a-d21adacc2f03/](http://social.technet.microsoft.com/Forums/en-US/ITCG/thread/ec6c84d1-0e4b-4710-a60a-d21adacc2f03/))

I think this should help to achieve your goal.

---

### Post by CharlesA on 2012-04-16
Huge +1 to robocopy, that's what I've been using for copying stuff from Windows to my Linux server.

---

### Post by roelforg on 2012-04-16
Anyone thought of booting from livecd,
and using dd to create a hdimg? Those backups are as good as you can get 'em!

---

### Post by CharlesA on 2012-04-16
> **roelforg said:**
> Anyone thought of booting from livecd,
and using dd to create a hdimg? Those backups are as good as you can get 'em!

The problem is the way WHS does data storage - data is spanned across multiple drives, but it's not RAID. It's an odd way to do it but I guess they went for convenience for the home user.

---

### Post by kgatan on 2012-04-16
You can also use WinSCP to backup from Windows to Linux.
Great if you want to backup over internet using SSH.

Can be scripted and scheduled.

Below example synchronizes the target folder.
WinSCP examplefile, example.txt

```
open name-of-saved-winscp-session
synchronize remote -delete "folder/file to synch" "target folder"
exit
```Scheduled bat-file, example.bat (I guess you can also just schedule winscp with the additonal parameters)
```
"C:\Program Files\WinSCP\winscp.exe" "/console" "/script=C:\Program Files\WinSCP\example.txt"
```You can do a ton of other stuff with the scripting but this does what i need.

---

### Post by roelforg on 2012-04-16
> **CharlesA said:**
> The problem is the way WHS does data storage - data is spanned across multiple drives, but it's not RAID. It's an odd way to do it but I guess they went for convenience for the home user.
Still, you can hdimg every drive using dd seperately and write it back in the right order to restore.

---

### Post by CharlesA on 2012-04-16
> **roelforg said:**
> Still, you can hdimg every drive using dd seperately and write it back in the right order to restore.
True. Maybe using something like Clonezila would work too - without copying the entire drive, bit for bit.

---

### Post by Alistair C on 2012-04-16
Thanks for all the suggestions. Reading them through trying to figure out what some of them mean ;)

 I take it the standard Win backup I found while poking around in WHS is old, clunky and does not support incremental backups?

I did notice that it could backup, say, the shared folders to a network location.

---

