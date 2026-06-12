---
title: "Samba fileserver filled with viruses"
date: 2010-09-23
forum: Security
---

### Post by LtPitt on 2010-09-23
Hello everybody!
I've prepared a Samba fileserver at work without much too problems and I've prepared a batch file to mount it as z: letter on windows machine at startup.
As a sad result the share gets filled with many viruses and became a vehicle of infection.
I could solve the problem on the windows side just this way

folder1 ----> folder2 and many other files and folders

folder1 has a condivision access read and write for everyone so I get no problems with passwords for all those who have access but i use ntfs security to do it read only (viruses act like if a pendrive is connected and mainly put infected files just in the "root" of it, in my case in folder 1) and then give everyone full control in folder2.

I've been trying to understand how to do this but I'm quite new to linux and smb.conf really scared me.
I've tried samba graphical tool which was a lot easier but I'm not able to achieve this kind of result: no need of user password for users to mount the share and no write possibilities in folder 1 and full control in folder 2.

Can anybody provide even a little help or a hint on what to look for?

Fair thanks!

---

### Post by SeijiSensei on 2010-09-23
First, you should investigate why this malware is appearing on the Samba share.  It sounds like you think it's a rather normal condition, which is disturbing.  Do you have no control over the client machines?  Are they all running virus checking, etc.?  

That said, you can try running [ClamAV]("http://www.clamav.net/") on the Samba server to scan the shared directories for viruses and other icky stuff.  To install it, open a Terminal then type 

sudo apt-get install clamav
sudo freshclam

which will install the ClamAV antivirus program and download its database of virus signatures.  (In the future, Ubuntu will automatically run freshclam to update the database every day.)

Now let's suppose you're exporting a directory called /home/me/publicdata to your Windows users.  You can scan that directory by typing 

sudo clamscan /home/me/publicdata

and see what it reports.  You can tell clamscan to remove infected files automatically (type "man clamscan" for details), but I suggest the first time out you look at the clamscan report and determine for yourself what files look suspicious.

After you've cleaned everything up, you'll probably want to run clamscan every day, or if your users are out of control, every hour.  Here's a simple script that runs clamscan and mails a report to the address in NOTIFY.  Replace "me@example.com" with the address to which you want reports to be sent, and "/home/me/publicdata" with the directory you want scanned (clamscan will automatically examine all the subdirectories of this directory as well):

```

#!/bin/sh
TARGET=/home/me/publicdata
NOTIFY=me@example.com

clamscan $TARGET 2>&1 | mail -s 'Clamscan report' $NOTIFY

```

(You may not have the "mail" program installed.  Run "sudo apt-get install mailx" if it's missing.)

Use an editor to create that file in /usr/local/sbin.  I recommend the nano editor because it has help menus.  At the prompt in a Terminal, type

sudo nano /usr/local/sbin/virusscan.sh

then copy the code above into that file.  Hold down the Ctrl key and type S; say "yes" to save the file, then hold down Ctrl and type X to exit nano.

Only two more tasks await.  First, you must make the script executable by running the command:

sudo chmod u+x,go-x /usr/local/sbin/virusscan.sh

This will allow the "root" (administrative) user, and only the root user, to execute this script.  Finally, to make this script run every hour, you should create a "symbolic link" to the file (rather like a Windows "shortcut") in the directory /etc/cron.hourly like this:

sudo cd /etc/cron.hourly
sudo ln -s /usr/local/sbin/virusscan.sh

This will run the script once each hour.  (You can limit it to once a day by replacing "cron.hourly" with "cron.daily" above.)

All of this is still secondary to answering the question, "why do I have malware on this share, and what can I do to keep people from putting it there?"  That's a "user management" issue, or potentially a bigger problem if you're administering a company's network.  I'd put most of my time and energy into keeping the malware off the client machines; scanning and removing infected files on a shared filesystem is only a secondary line of defense.

---

### Post by CharlesA on 2010-09-23
Maybe it's just me, but ClamAV has given me nothing but false positives.

I'm currently running BitDefender on my Samba shares.

But yeah, if you have a malware/virus problem, it comes down to controlling the network/clients.

---

### Post by LtPitt on 2010-09-24
@SeijiSensei

Woah! THAT's an accurate answer :D
Really thanks...
I'm able to fiddle with crontab and little scripting so I think I can manage to set an hourly scan thanks to your precious and accurate help.
I'm almost just arrived in this new (and horrible) situation.
We have more or less 300 clients...
No domain.
All administrators with blank passwords...
Many pc have not an antivirus...
Sounds like the far west but it's just Italy :D

So I know I have to take care of client's mess but I don't want to feed the beast before I put up a domain and join all the clients.

An hourly scan sounds great and I'll implement it anyway but a lock for writing privilege on main folder thanks to samba would be more than 90% of the solution (infected autorun.ini and similar stuff).

Thanks anyway to you and CharlesA for kind help :)

---

### Post by LtPitt on 2010-09-24
I did the automated scan and here's the problem I get:

/autorun.inf: Worm.autorun-2191 FOUND

That's why I say that the network share gets treated like a pendrive and if I'm able to lock the writing permission on the root folder of the smb share I'll be safe :)

Otherwise I'll be removing for ages this same damn file...

Thank to everybody :)

---

### Post by LtPitt on 2010-09-27
I've solved the problem and it was actually a piece of cake!

I've set samba on user permission and guest allow using webmin then I've created a folder named test1 from the filesystem and a folder called test2 from the filesystem.

In this situation nobody was allowed to do a single file creation anywhere.

So I did:

sudo chmod 777 test2

and therefore I am able to create folder and files inside the test2 folder.

Happy times!

It was really easy I just don't know because I wasn't able to realize this before.
Now all virus saving in the main smb folder (99% of them) are out of order :)

---

### Post by teejaybee on 2010-09-28
Your "chmod 777" solution is definitely not the answer. I think the proper solution resides in a correct smb.conf listing for your shares. The config file should not be daunting for you - just dive in with a copy of the documentation to guide you and sort it out properly. Just by reading a few quick google results i've found a "read only = yes|no" option in share definitions. That solves your first question. There's also a force user option which may help. But, if it was me, i'd use the fact that computers are dropping viruses into your samba shares as a tool to track down which machines are infected and fix them. Either touch the files and chmod 000 them (a virus cant be written over the empty file so people cant get infected from those files on your smb share) or make the share read only, then view the samba logs and watch for PC's trying to drop those files in there. There's your list of machines to fix first. There are heaps of free client-side antivirus programs out there like comodo, avg etc that should help to keep your environment virus free.

With compromised machines on the local network, it's probably best to have a separate network you can place freshly formatted machines on to receive updates and install antivirus software. Sounds like you have a lot of backing up important files and formatting / reinstalling to do ;)

---

### Post by SeijiSensei on 2010-09-30
> **LtPitt said:**
> @SeijiSensei

Woah! THAT's an accurate answer :D
Really thanks...

You're welcome.

> Sounds like the far west but it's just Italy :D

I was just there this summer with my daughter, but if you need some help I'd be happy to fly back!  Your dime, of course.

---

