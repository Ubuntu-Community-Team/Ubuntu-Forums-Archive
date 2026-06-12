---
title: "Help with backup"
date: 2011-04-20
forum: Server Platforms
---

### Post by david.garceau on 2011-04-20
Hey guys, i am setting up an offsite backup. I have around 6tb worth of data. The problem i am running into, is that once all of the data is off site, a lot of renaming and moving happens. The next day when the backup starts theres about 60gb that needs to be transferred, when realistically theres only 1gb of new data. Has anyone had any luck with software, or methods of fixing this?

---

### Post by ktrnka on 2011-04-20
What you might want to look at is something with data deduplication [BackupPC]("http://backuppc.sourceforge.net/") might be useful for you. The other option would be [rdiff-backup]("http://www.nongnu.org/rdiff-backup/"). Both are efficient and do almost exactly what you're looking for.

---

### Post by usatonycuba on 2011-04-20
> **david.garceau said:**
> Hey guys, i am setting up an offsite backup. I have around 6tb worth of data. The problem i am running into, is that once all of the data is off site, a lot of renaming and moving happens. The next day when the backup starts theres about 60gb that needs to be transferred, when realistically theres only 1gb of new data. Has anyone had any luck with software, or methods of fixing this?
(Double thread?) you might want to see this thread [http://ubuntuforums.org/showthread.php?t=1734515](http://ubuntuforums.org/showthread.php?t=1734515)

---

### Post by Lars Noodén on 2011-04-21
> **david.garceau said:**
> Hey guys, i am setting up an offsite backup. I have around 6tb worth of data. The problem i am running into, is that once all of the data is off site, a lot of renaming and moving happens. The next day when the backup starts theres about 60gb that needs to be transferred, when realistically theres only 1gb of new data. Has anyone had any luck with software, or methods of fixing this?

[rsync](http://linux.die.net/man/1/rsync) over SSH does that very well.  It transfers only the changes.

---

### Post by HermanAB on 2011-04-21
Howdy,
 
The answer to your trouble is called 'Deja Dup Backup Tool'.  It is in the repos.

[https://launchpad.net/deja-dup](https://launchpad.net/deja-dup)

---

### Post by collisionystm on 2011-04-21
I will tell you the same thing I tell everyone else. Just use Rsync. Dont use other programs. Do not .tar your files. JUST USE RSYNC. It does 1 complete backup of your files and then every time its scheduled to run thereafter it only sends the information of changed files. 
 
rsync -rqa <source> <destination>
 
If you are sending your backups to a linux box, you can just included the ssh parameter in the rsync. If your destination is some kind of ntfs, fat32 or other file system, you will need to mount it with samba and add it your /etc/fstab to make the mount permanent.
 
Let me know which one you need and I can help you elaborate the commands to do it right.

---

### Post by david.garceau on 2011-04-21
Thanks for all the replys, it will be from ubuntu 10.04 to an ubuntu 10.04 server. I did toy with rsync, but i suppose i just did not do the correct commands, i would love to hear more on this from you.

---

### Post by Lars Noodén on 2011-04-21
> **david.garceau said:**
> Thanks for all the replys, it will be from ubuntu 10.04 to an ubuntu 10.04 server. I did toy with rsync, but i suppose i just did not do the correct commands, i would love to hear more on this from you.

Here are some [examples of rsync with SSH](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup).

---

### Post by david.garceau on 2011-04-21
> **usatonycuba said:**
> (Double thread?) you might want to see this thread [http://ubuntuforums.org/showthread.php?t=1734515](http://ubuntuforums.org/showthread.php?t=1734515)


Mine is more geared towards fixing a problem that i am having with the data not being renamed/moved.

---

### Post by collisionystm on 2011-04-21
> **david.garceau said:**
> Thanks for all the replys, it will be from ubuntu 10.04 to an ubuntu 10.04 server. I did toy with rsync, but i suppose i just did not do the correct commands, i would love to hear more on this from you.
 
 
Ubuntu to ubuntu. 
 
PERFECT.
 
First things first.
 
I assume you are backing up to your ubuntu server.
 
on your server
 
```

 
sudo apt-get install ssh
 

```
 
This installs the SSH Server and Client.
 
Do the same on your Ubuntu Desktop.
 
 
Now we need to make a folder on the server to backup to, and set the permissions for the folder so we can dump files.
 
```

 
mkdir /home/<username>/backup
 
chmod 770 -R /home/<username>/backup
 

```
 
 
chmod uses 3 digits 99.9% of the time.
 
first digit is OWNER, second is GROUP, third is OTHERS
 
Here are what they mean:
 
> 
 
7 rwx read, write, execute
6 rw- read, write
5 r-x read, execute
4 r-- read
3 -wx write, execute
2 -w- write
1 --x execute
0 --- no permissions
 

 
You can do 
 
```

 
ls -lh ( LS -LH ) to check your folders permissions
 
I.E. cd /home<username>
ls -lh
You can see your permissions for your backup folder
 
 
 
Now that we have SSH server installed on ubuntu server, we can access it from the desktop. On your desktop open 2 terminal windows, one for desktop, other for server. On the terminal you opened for the server, type
 
[code]
 ssh <username>@<ipaddressofserver>

```
 
If prompted, press yes to connect
 
Enter the passcode.
 
Now that you are connected, we need to generate an RSA to allow your ubuntu server to connect to your desktop automatically without being prompted for a passcode eachtime.
 
In your ubuntu server terminal do this
 
```


[LIST=1]
[*][FONT=LucidaSansTypewriter, monospace][SIZE=3]sudo ssh-keygen -t rsa[/SIZE][/FONT]
[SIZE=3]This will prompt for a passphrase. Just press the enter key. It'll then generate an identification (private key) and a public key. Do not ever share the private key with anyone! [FONT=LucidaSansTypewriter, monospace]ssh-keygen[/FONT] shows where it saved the public key. [/SIZE]
[*][SIZE=3]This is by default [/SIZE][SIZE=3][FONT=LucidaSansTypewriter, monospace]~/.ssh/id_rsa.pub[/FONT]:[/SIZE]
[*][FONT=LucidaSansTypewriter, monospace][SIZE=3]Your public key has been saved in root/.ssh/id_rsa.pub[/SIZE][/FONT]
[*][FONT=Courier New][SIZE=3]sudo bash[/SIZE][/FONT]
[*][FONT=Courier New][SIZE=3]enter sudo password[/SIZE][/FONT]
[*][FONT=Courier New][SIZE=3]cd /root/.ssh[/SIZE][/FONT]
[*][FONT=Courier New][SIZE=3]vi id_rsa.pub[/SIZE][/FONT]
[*][FONT=Courier New][SIZE=3]copy the code ( highlight, right click, copy)[/SIZE][/FONT]
[*][FONT=Courier New][SIZE=3]:q!   < --- this quits VI[/SIZE][/FONT]
[/LIST]
```
 
NOW, back to your Ubuntu Desktop terminal
 
Do the same code, all we really need is the folders, but its faster anyways. But do not copy any keys from the id_rsa.pub, we dont need the desktop key
 
In the desktop terminal type
 
```

 
sudo bash
enter passcode
cd /root/.ssh
 
nano authorized_keys
 

```
 
Remember the code you copied from the Server's id_rsa.pub ???
 
Paste that into this nano 
 
type
 
CTRL+X and Y to save
 
now if you go to your server, you should be able to ssh to your desktop without any kind of pasword.
 
ssh <usernameondesktop>@<ipaddressofdesktop>
 
yes to connect
 
No password prompt??? Good.
 
On your server is where you will be doing your rsync commands
 
So in the server terminal, type 
 
exit
 
to get out of ther ssh session with the desktop
 
type rsync --help to look at the rsync options
 
```

 
rsync - <options> -e /usr/bin/ssh <username>@<ipaddressofdestkop>:/<pathoffolder>/* /home/<username>/backup
 
I.E. 
 
rsync -rqaHpEAXogt -e /usr/bin/ssh root@172.16.64.2:/home/*  /home/me/backup/
 
 

```
 
 
Make sure you include the colon : at end of <ipaddressofdesktop>
 
and make sure to include the asterisk * at the end of <pathtofolder>/
 
the * is a wildcard to grab everything in there
 
So that code is ssh to your desktop, grabbing the files in the folder path, and dumping them to the backup folder that we created in your home directory on the server.
 
Now you add it to crontab so the server backs it up automatically
 
crontab -e
 
if its your first time, use nano 
 
Here is an example of what to enter:
 
```

 
0 1 * * *      rsync -rqaHpEAXogt -e /usr/bin/ssh root@172.16.64.2:/home/*  /home/me/backup/
 

```
 
 
This code backs it all up at 1 am every day
 
hit 
 
```

 
CTRL+X and then Y to exit
 

```
 
'crontab successfully installed'
 
you are now good to go.
 
Whew. That was alot of typing. :P

---

### Post by david.garceau on 2011-04-21
Wow, thanks for the howto ill begin working on it now.

---

### Post by david.garceau on 2011-04-21
collisionystm,


By doing it that way, will this situation be fixed...


Folder1 has 10gb worth of data in it.

I rename Folder1 to Folder2.

Backup solution then copies the 10gb instead of renaming Folder1 to Folder2.

---

### Post by collisionystm on 2011-04-21
If you are renaming folders, you would need to adjust it in your rsync command. The rsync must have a valid working path or you wont be able to back anything up.

Are you looking for a way to do daily backups so you can go back in time? Read up on Rsnapshot.

It comes with ubuntu already

---

### Post by david.garceau on 2011-04-21
Heres the layout...

6tb worth of data transferred off site.

There are multiple levels of folders.
1.Folder 1
     a.Subfolder 1
     b.Subfolder 2 (20gb)

I set up rsync to backup 1. Folder 1


(day 1) initial backup.
(day 2) Name of Subfolder 2 gets change to Subfolder 24


I need to make sure that the 20gb doesnt get transferred again. 

On average there is 150gb a day that will get moved/renamed.

---

### Post by collisionystm on 2011-04-21
Well that presents a problem for any backup program. Once your folder is renamed, it is looked at as a new folder by rsync, therefore copying all of the data again.

You can use the --delete command switch when using rsync.

This deletes files on the reciever that are not being sent by the sender.

In other words, it will delete the old named folder and download the new folder. But it will have to redownload the entire folder.

Unless someone chimes in with an amazing superman script, you might just have to do it that way. If your network is fast enough you should be ok. ssh transfers go at  20mb a second or more.  You can send 150gb in no time.

> 
[INDENT]   --delete
      This  tells  rsync to delete extraneous files from the receiving  side (ones that aren&#8217;t on the sending side), but  only  for the  directories  that  are  being synchronized.  **You must have asked rsync to send the whole directory (e.g. "dir" or "dir/")   without using  a  wildcard  for  the directory&#8217;s contents (e.g.   "dir/*") since the wildcard is expanded by the shell and rsync thus    gets a  request  to  transfer individual files, not the files&#8217;   parent directory.**  Files that are excluded from the transfer   are    also excluded from being deleted unless you use the --delete-excluded  option or mark the rules as only matching on  the  sending side                 (see the include/exclude modifiers in the FILTER RULES   section).


[/INDENT][INDENT]via [http://unix.stackexchange.com/questions/5451/delete-extraneous-files-from-dest-dir-via-rsync](http://unix.stackexchange.com/questions/5451/delete-extraneous-files-from-dest-dir-via-rsync)




 [/INDENT]

---

### Post by david.garceau on 2011-04-21
Well thats where my problem lies. The server is off site. Located somewhere else in the state.

---

### Post by collisionystm on 2011-04-21
What are your operating hours there? Start the Rsync with crontab at 5:15 if thats when everyone leaves at 5

---

### Post by david.garceau on 2011-04-21
Well if there was 150gb moved and renamed on the server, then that would mean there would be 150gb that will need to be transferred. Which would take around a day.

---

### Post by collisionystm on 2011-04-21
Correct. But like I said, you will run into this with any backup program, Unless you can find someone to make one hell of a script. I unfortunately do not have those powers

Try reading up on the rsync options under rsync --help

> 

--exclude=PATTERN       exclude files matching PATTERN



maybe that is useful?

---

### Post by SeijiSensei on 2011-04-21
I can see a strategy for doing this, though I'm not going to write the script to do so.

First, run "rsync -avn" to create the list of updated files.  (The -n switch tells rsync to go through the motions but not transfer files.  With -v you'll get a nice list of the files that would be transferred.)

Next, iterate over the list and use scp to copy the changes to a new directory on the remote.

```

FILES=$(rsync -avn source target)

TODAY=$(date %Y%m%d)
STALE=$(date %Y%m%d --date='8 days ago')

ssh root@remote "mkdir /target/directory/$TODAY"

for f in $FILES
do 
    scp $f root@remote:/target/directory/$TODAY
done

ssh root@remote "rm -rf /remote/target/directory/$STALE"

```

This maintains a rotation of eight days worth of updates.

You need to do some futzing to handle filenames with embedded spaces properly.  (Pro tip:  Don't use spaces in filenames!)

---

### Post by david.garceau on 2011-04-23
Damn, I think thats a bit above my level.

---

