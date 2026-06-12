---
title: "Multiple users using same logon"
date: 2011-09-15
forum: Server Platforms
---

### Post by Almeister9 on 2011-09-15
Hi All.

I would like to ask a question of the learned peoples here.

I have a machine that has a fresh install of Ubuntu Server 11.04

I wish it to act as a simple, standalone File Sever for a small office of 10 or so Macs, ranging from OSX 10.5 to 10.6 (and probably, before long 10.7)

I have run into many "permissions bugs" using Samba with 10.6 (acknowleged by Apple support who stated that they had no intention of fixing it and refunded me the $60 odd they demanded from me to bring it to their attention).

I have installed AFP and Avanti with a share and it seems to work very well, and is quite fast. The only problem is that if someone saves a file to the server/share, then only they have write permissions to it.

I have seen others get over this by running a chmod 777 -R on a cron job every hour to re-write the permissions, but I need something a little better than this.

My idea is this.

I have users: "apple", "orange", "pear" (Mac OSX machines).
I create a user on the Ubuntu Server "banana".
Each of the Mac OSX machine's signs on to the AFP share of the Server using the credentials of "banana".
That way all files ever written to the server will be accessible and writable for all users (signed on as banana).

Can anybody here see any problems with this?
It would mean having around 10 machines, all logged onto the Ubuntu/AFP/share as "banana" at the same time, all the time.

The server mainly holds InDesign documents and jpg's used in said InDesign documents as well as word docs and xl spreadsheets. I need everyone in the office to have unlimited access to all files in the share at all times.

I would be very grateful to any opinions or technical information shared on this topic.

Thank you all in advance.
Cheers, Al.

---

### Post by Wim Sturkenboom on 2011-09-16
The weakest point in such a setup is that it's about impossible to track who modified / deleted / corrupted documents. Related to that is that if an employee leaves the company, one should actually change the password for banana.

Also,what happens if multiple users edit the same document and save it one after another. The last one who saves will win (unless there is some kind of locking).

Have you considered a version control system?

---

### Post by Jonathan L on 2011-09-16
> **Almeister9 said:**
> [...]
I have installed AFP and Avanti with a share and it seems to work very well, and is quite fast. The only problem is that if someone saves a file to the server/share, then only they have write permissions to it.

I have seen others get over this by running a chmod 777 -R on a cron job every hour to re-write the permissions, but I need something a little better than this.
[...]

Hi

What you're describing is pretty much exactly what the groups system was designed for.  Have you considered creating a group 'fruits' for all the users?

The steps would be

[LIST]
[*]Create the group (ultimate shows in /etc/groups) and put banana etc in it: see adduser(8)
[*]Change the group of the shared files (ultimately it's chgrp -R fruits /sharedstuff) see chgrp(1)
[*]Change the permissions of the shared files (ultimately it's chmod -R g+wX /sharedstuff) so they're writeable by the group: see chmod(1)
[*]Change the umask from default 022 to 002 so new files are writeable by the group: see login.defs(5) and others, as umask can be set in many places see umask(2) and also the file server software, which may have a setting for umask.
[*]And lastly change the permissions of the shared directories to be group-sticky: which means that files created inside them inherit their group from the enclosing directory, not the creating process (ultimately some kind of chmod g+s /sharedstuff/every/subdirectory)
[/LIST]
That last point is the fiddly one.  If your shared things are all on a single filesystem, you can mount the filesystem with an option 'bsdgroups' to give this behaviour.

The plus-side of this system is that everybody logs in with their own credentials, so you have proper audit trail of who is doing what and so on.  The downside is it's a little fiddly to set up if you haven't worked with multi-user systems much.  But in essence all you're doing is saying writing down in the computer the rules for who is allowed to do what to the files.

It's the classical way to achieve the kind of control you're describing, and has been used in thousands of places, sometimes with hundreds of thousands of users.  Though I'll confess I've not tried it with AFP, I have used it with Samba, NFS, FTP and so on.

Hope that's of some use: happy to elaborate if you need help on any point

Regards,
Jonathan.

---

### Post by Almeister9 on 2011-09-17
Hi Jonathon, thanks for your reply.

What you describe sounds exactly what I am after, however, the implemntation of it is beyond me at this stage.

I know that in Samba, the umask is set in the "shares definition" part of the Samba conf file, but I dont know how to do it in AFP.

I have been able to create a group in Ubuntu Server and add the usrs to the group. Then in the AFP (Netatalk) conf file there is a single definitions line where you can add the path to the share and the users allowed access
i.e allow: apple,orange,pear
or
allow: @fruit  (being the group).

I have been through the AFP (Netatalk) manual but cannot find a way to define umask in that line, and I don't know where else I could set it.

As for permissions to be group-sticky, I have no idead about this.

Any further assistance that you could give would be greatly appreciated.

---

### Post by Jonathan L on 2011-09-19
> **Almeister9 said:**
> Hi Jonathon, thanks for your reply.

What you describe sounds exactly what I am after, however, the implemntation of it is beyond me at this stage.

I know that in Samba, the umask is set in the "shares definition" part of the Samba conf file, but I dont know how to do it in AFP.

I have been able to create a group in Ubuntu Server and add the usrs to the group. Then in the AFP (Netatalk) conf file there is a single definitions line where you can add the path to the share and the users allowed access
i.e allow: apple,orange,pear
or
allow: @fruit  (being the group).

I have been through the AFP (Netatalk) manual but cannot find a way to define umask in that line, and I don't know where else I could set it.

As for permissions to be group-sticky, I have no idead about this.

Any further assistance that you could give would be greatly appreciated.

Hi Al

Take it in stages and you'll get there soon enough.  First off I'll just say please make a test area to do your experiments that's separate from your real data!

Sounds like you've got the groups part right.  I'd test this by making some files in your shared area, and forcing them to be the right ownership and so on.  I'll imagine you've made a directory 'test'  with some files in it from banana in the shared area.

On the server's command line: we change the permissions on the directory, the permissions on the files, and the group of the files:
```
cd /blahblah/sharedarea/test
sudo chmod g+wx .
sudo chmod g+w *
sudo chgrp fruits . *
```This should make all your files in that directory be group-writable by the group 'fruits'

I'd test that through netatalk from apple and orange and so on: can you read and write files like you want to?  (NB new files won't work right yet, but the files we've just modified should.)

Then I'd look to solve the umask

Find out the current umask by creating a new directory and a new file in you test area, _from banana_, then doing ls _on the server_
```
ls -l /blahblah/sharedarea/test/newfile
ls -ld /blahblah/sharedarea/test/newdir
```It's difficult (for me) to continue without knowing what the answer is, let us know what you found and we'll take it from there.

Also could you let me know how you start netatalk on your server?

You're nearly there: stick with it.

All best
Jonath_a_n.

---

### Post by Almeister9 on 2011-09-20
Hi Jonathan,
Thank you so much for your help with this.

The box I am using has been built for testing purposes so no critical data is stored on there.

The box is called "kiku" and the directory that is shared using Netatalk is /var/kiku

I have created a new folder: /var/kiku/newtestfolder
and in it I have placed a file TEST1.indd (InDesign file)

I then ran the commands you suggested
cd /var/kiku/newtestfolder
> sudo chmod g+wx .
sudo chmod g+w *
sudo chgrp scribal . *
The office was extremely busy yesterday so I didn't get a chance to see if it is writable from other machines as yet. but the output of the two commands you gave me are:
> root@kiku:/var/kiku/data1# ls -l TEST1.indd
-rw-r--r-- 1 almeister scribal 2457600 2010-02-24 14:54 TEST1.indd
and
> root@kiku:/var/kiku/data1# ls -l testnewfolder
total 2400
-rw-r--r-- 1 almeister scribal 2457600 2010-02-24 14:54 TEST1.indd
"almeister" is the username of the machine logged in that I created the new directory with and copied the file TEST1.indd in with before running the chmod commands. "almeister" is a user that I created on the Ubuntu Server with the same password as the OSX Machine's user 'almeister' and is a member of the group "scribal".
As I say, we were flat out yesterday so I may have done something wrong there and I will attempt again this morning to see if the results are the same.

The following are the settings for Netatalk:
> /etc/netatalk# vi afpd.conf
- -transall -advertise_ssh
> /etc/netatalk# vi AppleVolumes.default
/var/kiku "Kiku" allow:@scribal options:usedots,upriv
> vi /etc/default/netatalk

CNID_METAD_RUN=yes

AFPD_RUN=yes

TIMELORD_RUN=yes

I believe that Netatalk is started when the server starts and is always running. I use Avanti to broadcast the share so that it shows up in Finder.

Thanks Once again for your help with this and if I get different results when I test it this morning, I will let you know.

---

### Post by Almeister9 on 2011-09-20
Hi Jonathan,

I re-did the commands this morning with a different result
```
root@kiku:/var/kiku/data1/testnewfolder# ls -l
total 2400
-rw-rw-r-- 1 almeister scribal 2457600 2010-02-24 14:54 TEST1.indd
```
but unfortunately, this doesn't work. The InDesign file opens as read only.
Puting a text file in there has the same result,
```
-rw-rw-r-- 1 almeister scribal 2457600 2010-02-25 12:57 test1.rtf
``` but it cant be edited- "Could Not Save File".

Also, if I tried to do this commands not logged in as root (using sudo) I get the error message:
```
sudo: unable to resolve host kiku.scribal.com
```
but if I log in as root, the commands go through fine.

---

### Post by Almeister9 on 2011-09-21
The ```
sudo: unable to resolve host kik.scribal.com
``` was because of a change I had made in the /etc/hosts file on the advice of some other post when I was trying to get the Avanti to work.
I have now changed the line back to ```
10.1.1.76 kiku.scribal.com kiku
``` and the sudo commands work fine now, but even though the files say -rw-rw--r, they cannot edited by other users, and other users cannot save files into the folder.

---

### Post by Jonathan L on 2011-09-21
> **Almeister9 said:**
> Hi Jonathan,

I re-did the commands this morning with a different result
```
root@kiku:/var/kiku/data1/testnewfolder# ls -l
total 2400
-rw-rw-r-- 1 almeister scribal 2457600 2010-02-24 14:54 TEST1.indd
```but unfortunately, this doesn't work. The InDesign file opens as read only.
Puting a text file in there has the same result,
```
-rw-rw-r-- 1 almeister scribal 2457600 2010-02-25 12:57 test1.rtf
``` but it cant be edited- "Could Not Save File".



Hi Al

Thanks for output.  Looks like you missed the 'd' for directory on one of the commands, which is the one which shows the ownership and details of the directory:
```
ls -ld /var/kiku/data1/testnewfolder
ls -ld /var/kiku/data1/
ls -ld /var/kiku
```Would you be able to do those?  (As root, if necessary, from the server.)

I'll be able to write up next steps this afternoon.

Kind regards,
Jonathan.

---

### Post by Almeister9 on 2011-09-21
Hi Jonathan,

I really do appreciate your help with this.
The output of those commands is:```
root@kiku:/home/alan# ls -ld /var/kiku/data1/testnewfolder
drwxrwsr-x 3 almeister scribal 4096 2011-09-21 12:53 /var/kiku/data1/testnewfolder

root@kiku:/home/alan# ls -ld /var/kiku/data1/
drwxrwsr-x 4 almeister scribal 4096 2011-09-21 12:53 /var/kiku/data1/

root@kiku:/home/alan# ls -ld /var/kiku
drwxrwxrwx 15 root scribal 4096 2011-09-21 13:53 /var/kiku
```

---

### Post by Jonathan L on 2011-09-22
> **Almeister9 said:**
> Hi Jonathan,

I really do appreciate your help with this.
The output of those commands is:```
root@kiku:/home/alan# ls -ld /var/kiku/data1/testnewfolder
drwxrwsr-x 3 almeister scribal 4096 2011-09-21 12:53 /var/kiku/data1/testnewfolder

root@kiku:/home/alan# ls -ld /var/kiku/data1/
drwxrwsr-x 4 almeister scribal 4096 2011-09-21 12:53 /var/kiku/data1/

root@kiku:/home/alan# ls -ld /var/kiku
drwxrwxrwx 15 root scribal 4096 2011-09-21 13:53 /var/kiku
```

Hi Al

This is looking good.

The goal is to get all your shared files to be [FONT=monospace]like this
[/FONT]```
-rw-rw-r-- 1 almeister scribal 2457600 2010-02-24 14:54 TEST1.indd
```And all directories should be like this:
```
drwxrwsr-x 3 almeister scribal 4096 2011-09-21 12:53 /var/kiku/data1
```The features are:

[LIST]
[*]All files and directories are in the group scribal
[*]Files are writable by their group as well as their owner (rw-r[COLOR=Red]w[/COLOR]-r--)
[*]Directories are writable by their group as well as their owner and are 'set-group-id' (drwxrw[COLOR=Red]s[/COLOR]r-x)
[/LIST]
_**THEORY**_

Basically what you have to think about is what the system does when you create a new file.  The program (netatalk, in this case) simply says "create new file".

[LIST]
[*]**Permissions**: Almost always, the program tries to give the file permissions 666 (ie, rw-rw-rw-).  The operating system masks this with the current umask (which we want to be 002), which will give us 664 (ie, rw-rw-r--).  When you make a new directory, it tries to give it 777 (rwxrwxrwx), which will be masked to, for example, 775 (rwxrwxr-x).
[*]**Owner**: The operating system will give the new file the ownership of the process which created it.
[*]**Group**: This is the tricky one.  There are two schemes: the "System V" method and the "BSD" method.  The System V method gives the new file the primary group of the process which created it.  In Linux including Ubuntu, this will typically be a group with only one user in it, the current user.  The BSD method gives the new file the same group as the directory the file is created in.
[/LIST]
Group-inheritance is pretty simple to see but complex to explain!  First the explanation:

By default, Linux (including Ubuntu) uses the System V method for groups, which for is isn't very convenient.  You can make it use the much-more-helpful BSD group method for

[LIST]
[*]a **whole file system**, as an option to mount which you could put into fstab (it's called 'bsdgroups')  Because this is very unusual, I don't recommend it.
[*]an **individual directory**, by using the 'set-group-id' or 'setgid' bit, which is a nearly-invisible part of the permissions, and is set by chmod g+s.  The setgid-bit inherits: so if you make a new directory inside a setgid directory, the new directory will also be setgid.
[/LIST]
**For group sharing to work properly, you MUST have BSD-type groups.  My examples below use the second method, the setgid bit, which is what I recommend.**

_**EXAMPLE**_

We'll make a pair of directories and set them to be the two methods.
```
$ mkdir /tmp/test
$ cd /tmp/test
$ umask 2
$ mkdir bsd sysv
$ chmod g+s bsd
$ chgrp admin sysv bsd
$ ls -l
total 8
drwxrw[COLOR=Red]s[/COLOR]r-x 3 jonathan admin 4096 2011-09-22 09:47 bsd
drwxrw[COLOR=Red]x[/COLOR]r-x 3 jonathan admin 4096 2011-09-22 09:47 sysv
```Note that these directories are identical, with an unusual group (admin) and are both 775 but the bsd directory is also setgid.

Now when we make new files and directories we get the following results
```
$ touch bsd/f sysv/f
$ mkdir bsd/d sysv/d
$ ls -l bsd
total 4
drwxrw[COLOR=Red]s[/COLOR]r-x 2 jonathan [COLOR=Red]admin[/COLOR] 4096 2011-09-22 09:47 d
-rw-rw-r-- 1 jonathan [COLOR=Red]admin[/COLOR]    0 2011-09-22 09:47 f
$ ls -l sysv
total 4
drwxrw[COLOR=Red]x[/COLOR]r-x 2 jonathan [COLOR=Red]jonathan[/COLOR] 4096 2011-09-22 09:47 d
-rw-rw-r-- 1 jonathan [COLOR=Red]jonathan[/COLOR]    0 2011-09-22 09:47 f
```Notice that the new file and directory inside bsd is group admin: that's what we were trying to achieve.

_**PRACTICE**_


_Step 1.  Get tree in right shape._

At the top of your shared tree you make the entire exported tree

[LIST]
[*]Group owner to be the shared group
[*]Permissions to be group-writable
[*]Directories to be set-group-id
[/LIST]

You can do these in lots of ways, but the easiest is probably
sudo chgrp scribal /var/kiku/data1
sudo chmod -R ug+rwX,o-w,o+rX /var/kiku/data1
sudo find /var/kiku/data1 -type d -exec chmod g+s '{}' ';'

Then check that you have the correct settings at various points in your tree.

Make a couple of new files on the command line of the server while logged in as an appropriate user, and check that the new files and directories have the correct settings.

_Step 2.  Umask_

I could find very little for umask with netatalk either.  Though -m looks promising, it says it's only for directories.  Worth an experiment though.
[http://netatalk.sourceforge.net/2.0/htmldocs/afpd.8.html](http://netatalk.sourceforge.net/2.0/htmldocs/afpd.8.html)

I'd experiment with /etc/profile and /etc/login.defs

_Step 3.  Users_

I'll also take a little look at the authentical method of netatalk which I'm unfamiliar with.  I've got a Mactinosh for the day so should be able to experiment.



Again, hope this is helping you.  Let me know how you get on.

All best,
J.

---

### Post by Almeister9 on 2011-09-23
Hi Jonathan,

I really do appreciate your help so far, unfortunately it is not working.

I deleted all files and folders in /var/kiku,
then from the machine 'almeister'(Mac OSX 10.5) I created a directory called "DATA1" and in it I copied some files,
a png - Pictur 1.png
an InDesign file - TEST1.indd
a text file - testtext.rtf

I then did the commands```
sudo chmod g+wx .
sudo chmod g+w *
sudo chgrp scribal . * 
``` and checked the permissions
```
alan@kiku:/var/kiku$ ls -ld DATA1
drwxrwsr-x 3 almeister scribal 4096 2011-09-23 15:24 DATA1
```
```
alan@kiku:/var/kiku/DATA1$ ls -l
total 3316
-rw-rw-r-- 1 almeister scribal  931379 2010-07-16 16:35 Picture 1.png
-rw-rw-r-- 1 almeister scribal 2457600 2010-02-24 14:54 TEST1.indd
-rw-rw-r-- 1 almeister scribal     349 2011-09-23 15:24 testtext.rtf
```
All seems correct.
I then went to another Mac machine called 'ja'(Mac OSX 10.6) which is also in the users group scribal.
I opened the text file and added some characters. I tried to save it and I recieved an error message "The Document 'testtext' could not be saved".
I tried to open the InDesign file and it opened as Read Only.
Mac machine 'ja' shows all files permissions as "Read Only".

It seems that the server (Ubuntu) is doing everything right but the Macs just don't want to play.

---

### Post by Jonathan L on 2011-09-25
Hi

To me it looks like you're doing everything right and it was really starting to puzzle me!  So I found a moment to install netatalk and try with a Macintosh with (eventually!) great success once I'd found the little magic word: "upriv".

Here's the detail of what I have working.

_**VERSIONS**_

Netatalk installed by package add (Synaptic, on my laptop)
afpd -v gives afpd 2.0.5 - Apple Filing Protocol (AFP) daemon of Netatalk
Ubuntu is 10.04 LTS Desktop (running on a laptop).  There is no reason  to think other versions would be any different.  I still recommend 10.04  server for your purpose.
Macintosh is OSX 10.5.8 on a Mac Book Pro.

_**SERVER**_

Users look like this in /etc/passwd:
```
macbod:x:1001:1001:Mac User,,,:/home/macbod:/bin/bash
```and this in /etc/group
```
mac:x:9999:jonathan,macbod
```Added a directory to export:
```
$ sudo mkdir /var/macs
$ sudo chgrp mac /var/macs
$ sudo chmod g+w /var/macs
$ sudo chmod g+s /var/macs
$ ls -ld /var/macs
drwxrwsr-x 11 root mac 4096 2011-09-25 20:51 /var/macs

```[U][B]NETATALK CONFIGURATION
[/B][/U]
All config files in /etc/netatalk are default (in particular, afpd.conf is empty except for comments) with one change to AppleVolumes.default to add the volume as follows:
```
/var/macs "jmacs" [COLOR=Red]options:upriv[/COLOR] allow:@mac
```I am not entirely clear what "upriv" does but it clearly gets the behaviour we want.  /var/macs is the directory on the server; 'jmacs' is the name it will show up as on the clients; @mac is the name of the group of users who are permitted to use it.

NB These are users, not client machines.  I recommend that you do your access control based on people who know passwords, rather than which computer they're on.

_**TESTS**_

After changing groups for a user, that user logs out and back in again.
After changing appletalk configs,
```
sudo /etc/init.d/netatalk restart
```Made from command line on server with simply 'mkdir one'.  Because umask was 2, everything comes out as we want it: setgid 775, group 'mac':
```
drwxrwsr-x 5 jonathan mac 4096 2011-09-25 21:22 /var/macs/one

```I connected from the Mactinosh (Finder > Go > Connector to Server > afp://... log in as 'macbod' with password I'd made the account with)

And then, from the Macintosh finder, Inside that directory I created a Word document, made a new directory, and copied an existing file made by user 'jonathan'.  Listing on server shows:

```
-rw-rw-r-- 1 macbod   mac 19456 2011-09-25 20:50 frommac.doc
drwxrwsr-x 3 macbod   mac  4096 2011-09-25 20:49 newdir
-rw-rw-r-- 1 jonathan mac    29 2011-09-25 21:27 jonathanmadethis
-rw-rw-r-- 1 macbod   mac    29 2011-09-25 21:27 jonathanmadethis copy

```I found the details buried in the man page for [AppleVolumes.default]("http://netatalk.sourceforge.net/2.0/htmldocs/AppleVolumes.default.5.html") and seems to be exactly what you're looking for.

[B][U]IDEAS

[/U][/B]It is clear (from this [bugreport]("http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/649e575e7f4094ce/7380c402ceca9eaf") amongst others) that sometimes the permissions don't come out right because of either bugs or misdesign in the various versions of Mac OSX and perhaps the applications.  So netatalk has a way to fake the permissions requested by the client application, called dperm and fperm, which you might need.  
The example there also has dperm and fperm, which you might find you need, depending on the applications you're using.  (If you find that some applications don't have the right permissions, I'd try dperm:0777 and fperm:666, not the 0770 and 0660 that you'll see in various examples.)

There are probabably other options you might want, such as usedots and invisibledots, which I see others have found useful.

I noticed that the full permissions details showed up strangely on the Macintosh when I looked at them.  You might want to think about how you allocate your users and groups.  But first get the functionality.

I see [here]("http://jamescanspel.blogspot.com/2009/09/accessing-linux-file-server-from-os-x.html") some interesting notes and especially something for controlling .DS_Store files.

Also, you need to decide whether you're a umask 2 kind of place (you can read everything, even if you can't write it) or a umask 7 kind of place (if you can't write it you can't read it either).  It might not matter if you're a small group, and there are some good ways to organise directories to get the best of both worlds, but that will keep for another time.


Give that AppleVolumes.default settings a go and let me know if you get the same success, but I'm confident you'll get there from here.

All best,
Jonathan

---

### Post by Almeister9 on 2012-04-19
Hi Jonathan,

Due to different work commitments, I had to take a break from this endeavor, but I am ready to give it another go.

I have a fresh install of Ubuntu 11.10 Server with Netatalk 2.2.1 as per [http://piku.org.uk/2012/02/04/make-netatalk-work-on-ubuntu-11-10-and-osx/](http://piku.org.uk/2012/02/04/make-netatalk-work-on-ubuntu-11-10-and-osx/)

Did you ever get your test system to work?

Just a quick reminder of my goal.
I wish to make an Ubuntu Server with a single folder that everyone in the office has FULL write access to (Read Write Execute, Create Directories, the lot) using AFP. The machines in the office range from OSX 10.5 to 10.7
I dont really care whether users have to sign in to be able to mount the folder but I would prefer that if they have to, then they only have to once a day, or not at all.

---

