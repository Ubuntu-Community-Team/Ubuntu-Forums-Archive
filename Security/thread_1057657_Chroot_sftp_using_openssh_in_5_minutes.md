---
title: "Chroot sftp using openssh in 5 minutes"
date: 2009-02-02
forum: Security
---

### Post by Impotence on 2009-02-02
Hi, 

Chrooting sftp users will allow you to 'hide' the parts of the file system that they do not need access to, or rather, to deny them access to everything and then select what you want them to be able to access. This has obvious security benefits if done correctly. [wikipedia chroot]("http://en.wikipedia.org/wiki/Chroot").

After spending many hours trying (and failing) to get scponlyc to work on a 64bit system i found that openssh allows you to chroot users by adding just 4 lines into your sshd config file, creating a group for sftp only users and changing a few permissions. 

Required packages: openSSH version 4.9 or greater (at the time of writing 5.1 is in use), so if your using Intrepid (8.10) or newer then you should be fine. 

Parts one and two will only take a few minutes, the time required for part 3 is Dependant on how you want to set everything up.

**[B]Part one, editing your sshd config file:**[/B]

1. Backup your sshd config file
```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup.sftpmod
```
2. Open your sshd config file in your favorite editor (i use nano, you might use kate or gedit)
```
sudo nano /etc/ssh/sshd_config
```
3. Change the following line (near the end of the file) 
```
Subsystem sftp /usr/lib/openssh/sftp-server
```
to
```
Subsystem sftp internal-sftp
```
4. Add the following to the very end of your sshd config (MUST be at the end of the file).
```

Match Group sftponly
        ChrootDirectory /home/%u
        ForceCommand internal-sftp
        X11Forwarding no
        AllowTcpForwarding no

```
5. You will need to restart you ssh server for the changes to take effect (be careful, this will disconnect any logged in users)
```
sudo /etc/init.d/ssh restart
```
6. if you get the following message move on to part two
```

 * Restarting OpenBSD Secure Shell server sshd                                                     [ OK ]

```
If you have made any mistakes in the the sshd_config file then your ssh server might not start until you correct them (and certainly won't do what you want it to until you fix them), you can restore the backup with the following command 
```
sudo cp /etc/ssh/sshd_config.backup.sftpmod /etc/ssh/sshd_config

[B]Part two, creating and adding users to the sftp group
[/B]
1. Create the group 'sftponly'
[CODE]sudo groupadd sftponly
```
2. Create a new user (even if you want to do this to existing users i would recommend you create a test user first)  
```
useradd -m username
```
3. Add the new user to the sftponly group (or add existing users, again please use a test user first!)
```
sudo usermod -g sftponly username
```
4. Remove the new users shell access
```
sudo usermod -s /bin/false username
```
5. Change the ownership/group of the users home directory to root:root (required or the ssh server will disconnect them)
```
sudo chown root:root /home/username
```
6. Unless we change the users home directory to '/' or create '/home/username' inside the chroot they will be unable to login! i would suggest you opt for creating a the home directory inside the chroot as you can also make it writable for them.

Create the 'fake' home directory 
```
sudo mkdir -p /home/username/home/username
```
Make the user the owner of their fake home directory
```
sudo chown username:username /home/username/home/username
```

**Part 3, Adding access to specific directories**

This section has deliberately been left blank, i am not confident enough in my understanding of file permissions to write this as a step by step guide (anyone else in the same situation copying and pasting my commands could end up with improperly set privileges), if someone else believes they do have a decent understand of how to do this then post below and i will add it in (giving credit and linking to the post in the list of contributors at the end of this guide).

I will however, give some hints at how it might be done. You can mount other directories inside the chrooted home directory with the following.
```
mount -o bind /some/directory/ /home/username/somewhere
```
You should be very careful with this though, as you need to set permissions correctly (and perhaps mount it read-only if suitable), you could also create a directory common to a group of sftp users (ie a uploads directory), for this to remain after a reboot you will have to edit your fstab.

_**Contributors**_

[LIST]
[*]albinootje
[INDENT][LIST=1]
[*]Ubuntu release versions this should work on. [Link]("http://ubuntuforums.org/showpost.php?p=6665274&postcount=3")
[*]Providing a link to another guide suggesting /home/%u instead of %h for the chroot in sshd_config which makes it easier to drop the user into a writable directory inside the chroot (and prevents chrooting to the wrong directory by getting the location of home wrong). [Link]("http://ubuntuforums.org/showpost.php?p=6665274&postcount=3")
[/LIST][/INDENT]
[*] You, if you know anything that would be helpful to anyone reading this guide!
[/LIST]

---

### Post by cjacobsen on 2009-02-02
Nice guide! I've actually been looking for this and just stumbled upon it here. Great! :p

---

### Post by albinootje on 2009-02-02
> **Impotence said:**
>  After spending many hours trying (and failing) to get scponlyc to work on a 64bit system i found that openssh allows you to chroot users by adding just 4 lines into your sshd config file, creating a group for sftp only users and changing a few permissions. 

Required packages: openSSH version 4.9 or greater (at the time of writing 5.1 is in use).


Thanks a lot for mentioning this! :)

Here's an article which has a little bit of a different approach :
[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

It also says minimum version is "4.8p1 for the GNU/Linux port" needed.
That would be :
[http://packages.ubuntu.com/search?keywords=openssh-server](http://packages.ubuntu.com/search?keywords=openssh-server)
Intrepid and newer only.

And this changelog for openssh 4.9 :
[http://www.openssh.com/txt/release-4.9](http://www.openssh.com/txt/release-4.9)
says this :
> 
New features:

  * Added chroot(2) support for sshd(8), controlled by a new option
    "ChrootDirectory". Please refer to sshd_config(5) for details, and
    please use this feature carefully. (bz#177 bz#1352)

I wonder what the "please use this feature carefully" would be about.

For the rest, mount --bind is indeed a nice option to use within the chrooted dir, but I remember reading that older 2.6.x Linux kernel only support read/write mount --bind, and not read-only mount --bind.

Thanks again for posting this! :)

---

### Post by Impotence on 2009-02-03
According to the debain-administration article the home directory is relative to the chroot so, if you wanted too, you should be able to drop the user into a writable directory that they own... I will try it and let everyone know.

PS Fixed a few typo's and omissions from the guide (such as forgetting to put 'username' after some of the commands that needed it), if there is a 'standard format' for guides here or any mistakes i have made, improvements etc please point them out

EDIT: changing the chroot directory to /home/%u and home to /home/username works quite well (you obviously have to create /home/username inside the real /home/username), you could also just set the home to /home if your not trying to emulate a normal setup (of users having a directory inside /home), updating the guide now :) I'm not going to attach a credit to xyz to every piece of text that i did not create anymore (this will make it harder to read over and look cluttered) instead i think a list of contributors at the end of the guide (with details to what they provided) would be more suitable :) (feel free to object albinootje and i will add your credit next to your submissions you have made so far, all new submissions go at the end though!)

---

### Post by Impotence on 2009-02-04
I seem to be having problems using "filezilla" with sftp accounts chrooted created in this way, if anyone else has followed these instructions it would be very helpful if you could take a minute to test this.

How to install filezilla
```
sudo apt-get install filezilla
```

---

### Post by albinootje on 2009-02-04
> **Impotence said:**
> I seem to be having problems using "filezilla" with sftp accounts chrooted created in this way, if anyone else has followed these instructions it would be very helpful if you could take a minute to test this.
[/CODE]

I would like to test the build-in chrooted sftp soonish.
Yesterday I've installed a newer openssh server version on my Ubuntu 8.04 desktop, and made changes to the sshd_config file, next step for me is to do some more reading first :)

---

### Post by albinootje on 2009-02-04
I've used the instruction from the Debianadmin webpage link (and I don't see much difference at all with your instructions), and it works fine with FileZilla, just as with WinSCP (with Wine in Ubuntu, with and without the scp fallback).

---

### Post by Impotence on 2009-02-22
Sorry for taking so long to post a followup.

The problem with filezilla was found, filezilla ignores the password you enter in the quick connect bar if you are logging into an account with the username 'anonymous' ([bugzilla ticket + workarounds]("http://trac.filezilla-project.org/ticket/4206")).

---

### Post by fozzyuw on 2009-02-25
This has been a very helpful tutorial.  However, I have a question on how to slightly modify this tutorial to fit my own organizational needs.

I have a master user called "masterftp".  I want to chroot this guy.  Basically, the tutorial given would be fine for this guy.

Now, I want to create users who have a Chroot directory inside the masterftp directory.  So, it would look like this...


/home/masterftp/ - master ftp directory
/home/masterftp/client1 - a clients ftp directoy that is chroot for them
/home/masterftp/client2 - another chrooted client directory
[...]

This case, the masterftp user will be able to see and access all the clients, but the clients will only see their respected directories.

How might I get something like this setup?

Thanks!
Fozzy

ps. for the record, I was able to follow the tutorial and get it to work

---

### Post by albinootje on 2009-02-25
> **fozzyuw said:**
>  How might I get something like this setup?

Sounds like you can just assign different home directories for your users.
/home/masterftp/ will be the home directory for your masterftp user.
/home/masterftp/client1 will be the home directory for the first client. And so on.

---

### Post by fozzyuw on 2009-02-25
> **albinootje said:**
> Sounds like you can just assign different home directories for your users.
/home/masterftp/ will be the home directory for your masterftp user.
/home/masterftp/client1 will be the home directory for the first client. And so on.
Yes, that's basically what I'm thinking too, except theirs the whole sftponly group setup with the chrootdirectory = '/home/%h' thing.  I'm wondering if I have to setup a second group or edit this parameter.

I'm fairly new to managing Linux.  I can see what sort of going on, but not 100% certain how it's interacting.

I'm going to give the home directory thing a try in a second.  I've already got one test user setup.  Just have to assign him the group and see if he'll login.

---

### Post by albinootje on 2009-02-25
> **fozzyuw said:**
>  I'm going to give the home directory thing a try in a second.  I've already got one test user setup.  Just have to assign him the group and see if he'll login.

I've just quickly tested the following :
1) Changed /etc/ssh/sshd_config to look like this :
```

Match user masterftp
         ChrootDirectory /home/%u
         X11Forwarding no
         AllowTcpForwarding no
         ForceCommand internal-sftp

Match group sftponly
         ChrootDirectory /home/masterftp/%u
         X11Forwarding no
         AllowTcpForwarding no
         ForceCommand internal-sftp

```
2) Restarted ssh server with /etc/init.d/ssh restart
3) Created the home directory inside /home/masterftp for the new normal user.
4) Added the user masterftp and a normal user.
5) Tested logging in with sftp for both user masterftp and the normal user, and that worked. 
The user masterftp could see the content of the home directory of the normal user.

---

### Post by Impotence on 2009-02-25
Interesting setup! (but makes perfect sense in your situation). you could probably have achieve the same outcome with a single group (ie ftpchroot) and using bind to give masterftp access to each users chrooted home. But that would require editing /etc/fstab every time you add a new user! (in addition to creating the users home dir and adding them to the sftponly group). if your going to be adding / deleting users on a semi regular basis you would probably benefit from scripting this.

What have you set your users home directories too?

> I'm fairly new to managing Linux. I can see what sort of going on, but not 100% certain how it's interacting.

I would appreciate some detailed feedback about the instructions i provided, mainly how could it be improved, should each step be explained in more detail, is anything potentially misleading or unclear etc (all constructive criticism appreciated!).

---

### Post by fozzyuw on 2009-02-26
> **Impotence said:**
> What have you set your users home directories too?This FTP server is for our engineers and their customers.  They'll be transferring large files between the two.

I want a directory structure like such:

/home/engftp/[company division]/[customer name]

There's a master user "engftp" who's home directory is "_/home/engftp_".  Then a customer for division1 named "Delta Company" might have a directory "_/home/engftp/division1/delta_".

Delta gets their login info "*deltalogin:password*" and they only see a chroot directory of their home directory.

While the "engftp" account will be able to see it all.

Ideally, I'd probably want to break up the engineers into groups by division and chroot them into their divisions.  But in the short term, engineers can all be given a master account status.

I've tried modifying the file as suggested by **albinootje** but I failed to get it to work, but I'm going to clear some stuff out and try again with some additional testing that I think I might be doing wrong.

> **Impotence said:**
> you could probably have achieve the same outcome with a single group (ie ftpchroot) and using bind to give masterftp access to each users chrooted home.
I probably could, but that's already over my head on Linux.

> **Impotence said:**
> But that would require editing /etc/fstab every time you add a new user! (in addition to creating the users home dir and adding them to the sftponly group).
New users will be added and removed based on new customers for the engineers, which will happen fairly frequently.

> **Impotence said:**
> if your going to be adding / deleting users on a semi regular basis you would probably benefit from scripting this.
Scripting Linux is beyond my comfort zone at the moment.  I'm a programmer, but I want to get more familiar with Linux and how it works before I dabble with scripts.  Though, it'll be something I'll have to look into because one of the things I'll need to do is have a script daemon that clears out the FTP for files older than a certain time.

> **Impotence said:**
> I would appreciate some detailed feedback about the instructions i provided, mainly how could it be improved, should each step be explained in more detail, is anything potentially misleading or unclear etc (all constructive criticism appreciated!).
I thought the tutorial was very good at my skill level.  The only thing I would have liked is to see more explanation as to what I was doing in the sshd_config file.  Of course, more details are explained in 'man sshd_config', but IMHO it's good to do a little extra explaining in the tutorial to make it clear.

It's a tough balance though.  To keep a nice and concise tutorial, and avoiding too much details and loose the easy step/by/step instructions.

Thanks for the tutorial and the additional help!

---

### Post by fozzyuw on 2009-02-26
Ok, I think I got it worked out but I want to post what I'm doing here to:
a) help anyone else with a similar scenario and 
b) get feedback from those more familiar with that I did and if there might be a problem with it because it deals with security permissions.

1st)
I edited _/etc/ssh/sshd_config_ to add the following code
```
Match group sftponly
	ChrootDiretory %h
	ForceCommand internal-sftp
	X11Forwarding no
	AllowTcpForwarding no
```
This setups the Chroot configuration for OpenSSH and tells OpenSSH to Chroot anyone logging in as a member of the "sftponly" group into the "%h" directory.  %h is the users home directory as set in their user profile ("cat /etc/passwd" to see user profiles and "sudo usermod -d <home directory path>" to change)

2nd)
As root(sudo), I created my directory structure I wanted to use/organize.  I did this because it'll make root the owner for user and group (saving steps later on).

My structure is:
/home/sftp/division1/<customer name>
```
sudo mkdir -p /home/sftp/division1/customer1
```

The "-p" option will create all the directories if they do not exist yet.

3rd)
I create the master ftp user and set there home directory, primary group, and shell access.  Then given them a password.
```
$ sudo useradd -d /home/sftp -g sftponly -s /bin/false mastersftp
$ sudo passwd mstersftp
```

4th)
At this point, the user "mastersftp" should be able to connect via WinSCP and be chrooted into their home directory and be able to see and navigate _/home/sftp/divsion1/customer1_ along with any new directors and files put under this directory.

5th)
Now, I want to create a *customer1* user who is chrooted into the _/home/sftp/division1/customer1_ directory.  I follow the same process as in step 3 above but make sure I use the appropriate home directory.
```
$ sudo useradd -d /home/sftp/division1/customer1 -g sftponly -s /bin/false customer1
$ sudo passwd customer1
```

This user should be able to login via WinSCP and see any files or directors in their chroot-ed directory.

6th)
The last problem is that, since all the directories had to have root:root for user:group ownership, I had to change permissions to the folders to allow write access for anyone, otherwise, they would not be able to upload files to the directory.
```
sudo chmod -R 777 /home/sftp
```

This will set a write permissions to _/home/sftp_ and all files/subdirectories below this directory, allowing anyone to write files to these folders, if they can see them.
***warning*** make sure you have the proper directory, this is can be very dangerous if you did this at the root (**/**) level.

The question is, are there any conncerns about giving everyone write access to these folders in this situation?  I mean, they're chroot and shell has been removed for the users, so I'm not sure if there is or isn't.

Otherwise, I'm not sure how I would get this to work.

---

### Post by lunaz on 2009-07-28
i used this guide quite a while ago to get my sftp stuff working but now for whatever reason it says permission denied when i try to upload stuff or make a new dir.

any idea where to start? it's been a while since i've used it but can provide more info as needed.

---

### Post by fordry on 2009-08-14
I got this setup working, works great btw, nice guide.

Im doing a setup for a small company that wants to use ftp for clients to send in their graphics. This is kind of a small issue but would help their ease of use for some of their less knowledgeable clients. Is it possible with this setup to make the /home/username/home/username folder the default folder that an ftp client opens up to? With this setup, the ftp server logs in and opens up the /home/username folder as / with the home directory listed. I would like it to just open up directly to /home/username.

I realize this isn't much of an issue, but it would help make this a little easier for them.

---

### Post by polyrhythmic on 2009-09-29
Just wanted to say, thanks for the awesome guide!  I completed it in under 3 minutes.  I think the only step missing was

```
sudo passwd username
```

and I think the preferred bind syntax (from manpage) is

```
mount --bind olddir newdir
```

:)

---

### Post by roundhay on 2009-11-17
I have tried to follow this tutorial but I can't login using sftp, here are the commands I entered:

```
home@server:~$ sudo nano /etc/ssh/sshd_config
home@server:~$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server sshd                                                                                                     [ OK ] 
home@server:~$ sudo mkdir -p /home/sftp/sftphome/USER1
[sudo] password for home: 
home@server:~$ sudo useradd -d /home/sftp -g sftponly -s /bin/false mastersftp
useradd: group 'sftponly' does not exist
home@server:~$ sudo groupadd sftponly
home@server:~$ sudo useradd -d /home/sftp -g sftponly -s /bin/false mastersftp
home@server:~$ sudo passwd mastersftp
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
home@server:~$ sudo useradd -d /home/sftp/sftphome/USER1 -g sftponly -s /bin/false USER1
home@server:~$ sudo passwd USER1
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
home@server:~$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server sshd                                                                                                     [ OK ] 
home@server:~$ exit
logout
Connection to 192.168.1.101 closed.
```

So I should have 2 users:

mastersftp - has access to /home/sftp & /home/sftp/sftphome/USER1

and

USER1 - has access only to /home/sftp/sftphome/USER1

but when I try to connect to the server from  my desktop PC on the LAN using sftp in FileZilla or using the command line e.g.

```
home@desktop-pc:~$ sftp USER1@192.XXX.X.XXX
Connecting to 192.XXX.X.XXX...
USER1@192.XXX.X.XXX's password: 
Read from remote host 192.XXX.X.XXX: Connection reset by peer
Couldn't read packet: Connection reset by peer
```

the sftp connection is reset

I have added the following to the end of my sshd_config file

```
Subsystem sftp internal-sftp

UsePAM yes

#Added extra config details sftp
Match Group sftponly
        ChrootDirectory /home/%u
        ForceCommand internal-sftp
        X11Forwarding no
        AllowTcpForwarding no
```

I'm not sure what I've done wrong?

If I use the normal server user login and password I can connect using sftp.

---

### Post by roundhay on 2009-11-17
spotted my mistake

```
Match Group sftponly
        ChrootDirectory /home/%u
        ForceCommand internal-sftp
        X11Forwarding no
        AllowTcpForwarding no
```

should have been

```
Match Group sftponly
        ChrootDirectory %h
        ForceCommand internal-sftp
        X11Forwarding no
        AllowTcpForwarding no
```

seems to be working now

Great tutorial

---

### Post by Lars Noodén on 2009-11-18
Out of curiosity where do you have the home directories?
Ubuntu usually had them in /home

---

### Post by roundhay on 2009-11-18
I have now set up 4 user directories and a 'master' user, the directory structure is:

```
/home/sftp/sftphome/USER1
/home/sftp/sftphome/USER2
/home/sftp/sftphome/USER3
/home/sftp/sftphome/USER4
```

Each user is chrooted to their home directory but the 'master' user can access /home/sftp and all of the USER directories

How does this differ the the directory structure your would get if I followed the method you indicated in one of your other posts:

> Try sketching on paper first then.

The users will be locked into the directory specified by the ChrootDirectory directive. They can't go up even a single level from that. They can't go sideways, via symlinks, either.

You can use special symbols with ChrootDirectory

    * %u = user's login name
    * %h = user's home directory


So you need to plan your directory structure and maybe give the various users a special home directory.

usermod -d /home/sftp/$USER $USER

---

### Post by Lars Noodén on 2009-11-19
> **roundhay said:**
> 
How does this differ the the directory structure your would get if I followed the method you indicated in one of your other posts:

It doesn't.  It is just a matter of deciding where the directories will be and who can access what.

Or do you mean /home/sftp/... vs /home/... for the chrooted directory?  

In the latter there is the potential to access other home directories, not just those of the chrooted users.  You'd have to set the permissions and group memberships differently for the existing home directories and then make changes in /etc/skel or /etc/adduser.conf to ensure that they are carried to accounts made later.  

With the former, access is not granted to the other home directories.  If you decide to let one of the accounts have more access, then you can create a symlink in /home to the user's directory in /home/sftp

---

### Post by roundhay on 2009-11-19
I am happy with the directory structure I have and the access seems to work. In an ideal world I would like all of the users to have the same home directory. Is this possible?

Could you set up

```
/home/sftp/sftphome/USER1
```

and make this the home directory for all subsequent USERS?

or if the fiel structure I have coudl you give all USERS access to sftphome?

---

### Post by Lars Noodén on 2009-11-20
If you chroot to /home/sftp/ then the chrooted users will have access (assuming standard directory permissions) to any directory under it. So if you have that for chroot and have user1 and user2 with the home directories /home/sftp/user1 and /home/sftp/user2 then both will be able to at least look in eachother's directories, if the default settings are otherwise left alone.

---

### Post by yug23 on 2010-04-01
Thanks for this tutorial, very useful.

I have a newbie-question though- I want to mount the 'Music' directory in my home directory in the SFTP users' home directories, giving them download access but not write access. At the moment all the files in the Music directory are chmodded to 700. If I change them to 777 then the SFTP users can download them, but this seems like an unnecessary security risk. Anything less than 777 and they can't even read the files, they are just denied access to the directory.

How can I give their user group read and download access to the mounted directory without chmodding everything in it to 777? I know this is probably one of the first things one should learn with linux but I find it difficult to get my head round.

Thanks in advance for any help.

---

### Post by yug23 on 2010-04-02
I'm really stuck with this so I'm going to have to BUMP this thread!

Please help somebody! :)

---

### Post by narcisgarcia on 2010-10-14
I've seen this guide for chrooted SFTP, and I've learnt from a lot of tutorials as this one. Here my compendium for optimal configuration in both clients and servers:

[http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses](http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses)

(special care of users and permissions)

---

### Post by senor_smile on 2010-11-05
> **yug23 said:**
> I'm really stuck with this so I'm going to have to BUMP this thread!

Please help somebody! :)

Another bump.  I have followed the directions to a t.  I have been googling for hours.  My problem is that when the users add files, their files have default file permissions: -rw------- .  I need them to all be -rw-rw-rw- so that the files can be accessible via http(browseable music and pictures).  So, how do you change the sftponly users default permissions on files added via sftp?

---

### Post by narcisgarcia on 2010-11-06
senor_smile, the proposed tutorial opens all the available possibilities about permissions, and from server you cannot force to give permissions: you can only set an umask to remove permissions on new elements.

With a full open pam umask=0000 at server, you only say "Ok, the client can use the umask he wants". For elements to be created with rw-rw-rw- permissions, client needs to use umask=1111 or umask=0000 .

---

### Post by narcisgarcia on 2010-11-10
senor_smile, if you want to sure that clients create elements with all permissions, you can make them to use FileZilla FTP/SFTP client, which uses 0000 umask by default, and supports most platforms (Linux/Windows/Mac):

[http://filezilla-project.org/](http://filezilla-project.org/)

For other cases such as gFTP (rw-rw----), you can join the webserver user to an additional group (sftponly). Example for Apache2:
```
usermod --append --groups sftponly www-data
service apache2 restart
```

---

### Post by senor_smile on 2010-11-11
> **narcisgarcia said:**
> senor_smile, the proposed tutorial opens all the available possibilities about permissions, and from server you cannot force to give permissions: you can only set an umask to remove permissions on new elements.

With a full open pam umask=0000 at server, you only say "Ok, the client can use the umask he wants". For elements to be created with rw-rw-rw- permissions, client needs to use umask=1111 or umask=0000 .

Thanks.  I forgot to post back.  It hadn't occured to me that I was looking at the situation all wrong.  The files I was transferring over from my local machine happened to have some pretty strange permissions on them, so they were carrying over.

---

