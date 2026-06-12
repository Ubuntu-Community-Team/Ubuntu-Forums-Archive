---
title: "HOWTO: Mount SSH Shares"
date: 2005-12-14
forum: Tutorials
---

### Post by sciurus on 2005-12-14
sshfs has the advantage over a KIOslave or GnomeVFS that any program can use it. For instance, in Kubuntu Amarok wasn't able to play my remote music through fish:/ but worked fine using sshfs.

1) Install the software
sudo apt-get install sshfs

2) Add fuse to /etc/modules
sudo nano /etc/modules

3) Add yourself to the 'fuse' group, then log out and log in again.
sudo adduser your-username fuse

4) Create a mountpoint and give yourself ownership
sudo mkdir /media/mount-name
sudo chown your-username /media/mount-name

5) Mount the filesystem
sshfs remote-system-name:/remote-folder /media/mount-name

6) Unmount the filesystem
fusermount -u /media/mount-name

Directions taken from [http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/) More info on sshfs is available at [http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)

I've run into a strange problem on two Kubuntu machines where, after using sshfs, you're unable to unlock your own computer. Logging in works fine, but you can't return from a password-protected screensaver. My solution was to start a new session, change my password, then return to the old session and use the new password to unlock it.

---

### Post by cdean on 2006-01-02
```
[cdean@frog ~]$ sshfs 192.168.1.3: linuxbox
cdean@192.168.1.3's password:
fuse: failed to exec fusermount: Permission denied
```

I'm getting that error after following the HOWTO...

---

### Post by Gandalf on 2006-01-03
isn't NFS far more better? i use NFS to connect any linux laptop to my external HDD and windows clients use samba, everything is extremely fast and just amasing

---

### Post by Drain on 2006-01-03
[QUOTE=Gandalf]isn't NFS far more better? i use NFS to connect any linux laptop to my external HDD and windows clients use samba, everything is extremely fast and just amasing[/QUOTE]

I think that the security of the encrypted connection that SSH provides is the major advantage here. Also, on a local network, NFS and Samba are just fine (they'd be presumably blocked behind a firewall?), but if you want to have access to those shared directories from an "outside" network, you can just re-use the SSH port.

---

### Post by Gandalf on 2006-01-03
[QUOTE=Drain]I think that the security of the encrypted connection that SSH provides is the major advantage here. Also, on a local network, NFS and Samba are just fine (they'd be presumably blocked behind a firewall?), but if you want to have access to those shared directories from an "outside" network, you can just re-use the SSH port.[/QUOTE]
yes actually i have a firewall and i don't allow access to prtmap/nfs ports, anyway my ssh port is not the default how to make it use another port then 22?

---

### Post by freelsjd on 2006-01-03
I did this and it worked fine.  However, how can I verify the mount (other than using it)?  In other words, the "df" command does not show the sshfs mounted drive.   How to view the mount ?

---

### Post by GrammatonCleric on 2006-01-04
[quote=Gandalf]yes actually i have a firewall and i don't allow access to prtmap/nfs ports, anyway my ssh port is not the default how to make it use another port then 22?[/quote]

With sshfs -p option.

- GC

---

### Post by Chris Tucker on 2006-01-04
[QUOTE=cdean]```
[cdean@frog ~]$ sshfs 192.168.1.3: linuxbox
cdean@192.168.1.3's password:
fuse: failed to exec fusermount: Permission denied
```

I'm getting that error after following the HOWTO...[/QUOTE]

Well perhaps reading the instructions might help.. ```
5) Mount the filesystem
sshfs remote-system-name:/remote-folder /media/mount-name

```
ie: home folder on remote system, and /media/dot3home .. just persay..
sshfs 192.168.1.3:/home/cdean /media/dot3home

---

### Post by GrammatonCleric on 2006-01-04
[quote=cdean]```
[cdean@frog ~]$ sshfs 192.168.1.3: linuxbox
cdean@192.168.1.3's password:
fuse: failed to exec fusermount: Permission denied
``` 
I'm getting that error after following the HOWTO...[/quote]


I believed that fusemount is installed so root only and execute it try the following.

```
sudo chmod +x /usr/bin/fusermount
```

- GC

---

### Post by floyd27 on 2006-01-04
thanx for the guide..:)

---

### Post by freelsjd on 2006-01-04
[QUOTE=freelsjd]I did this and it worked fine.  However, how can I verify the mount (other than using it)?  In other words, the "df" command does not show the sshfs mounted drive.   How to view the mount ?[/QUOTE]

try a last time: anyone know the answer to this question ?  I did see that a "ps aux" shows the repeat of the command, but that is it so far...

---

### Post by sciurus on 2006-01-04
[QUOTE=GrammatonCleric]I believed that fusemount is installed so root only and execute it[/QUOTE]

This will not be the case if you follow step 3.

3) Add yourself to the 'fuse' group, then log out and log in again.
sudo adduser your-username fuse

---

### Post by sciurus on 2006-01-04
[QUOTE=freelsjd]I did this and it worked fine.  However, how can I verify the mount (other than using it)?  In other words, the "df" command does not show the sshfs mounted drive.   How to view the mount ?[/QUOTE]

I'm not at my system to check, but I would expect an entry in /etc/mtab. df is [known ]("http://tips.linux.com/article.pl?sid=05/11/11/176206&tid=100")not to work: "Certain command-line tools (such as df) do not work properly due to shortcomings in the OpenSSH implementation of sftp. To work around these holes, sshfs has to estimate disk usage and free space, which could complicate its usage for some tasks."

---

### Post by nehalem on 2006-01-05
This kind of a solution is sooo much better than KDE and Gnomes vfs stuff.  Can't wait till the desktops just use this.

---

### Post by GrammatonCleric on 2006-01-05
[quote=sciurus]This will not be the case if you follow step 3.

3) Add yourself to the 'fuse' group, then log out and log in again.
sudo adduser your-username fuse[/quote]

And if you read cdean's comments he stated that he "DID" following the instructions.  So if this infact was the case and it still did not allow him to execute fusemount my post would fix the problem.

- GC

---

### Post by Chris Tucker on 2006-01-05
heh.. just got to thinking.. any way to get windows XP or older to login to a ssh server like this and mount a remote folder and such? would be great, seeing as how i have wifi here and samba is a little insecure.. i could use samba for the read-only side and should i ever be in windows and need to upload something, instead of messing with SCP, just find a mounted drive?

---

### Post by nehalem on 2006-01-06
When I try and move a file to my fuse mounted folder it says the following:
mv: failed to preserve ownership for `/media/prod_server/DownArrow.png': Permission denied

Is this like NFS and you have to have the same user ID stuff set up?

---

### Post by sciurus on 2006-01-06
[QUOTE=GrammatonCleric]And if you read cdean's comments he stated that he "DID" following the instructions.  So if this infact was the case and it still did not allow him to execute fusemount my post would fix the problem.[/QUOTE]

He could have missed a step, misstyped something, forgotten to reboot, etc. I know I make little mistakes all the time. If he followed the directions, and as a member of the fuse group he cannot execute a file which is *-rwsr-xr--  1 root fuse* then there is a problem with his sytem that shouldn't be glossed over.

---

### Post by sciurus on 2006-01-06
[QUOTE=nehalem]When I try and move a file to my fuse mounted folder it says the following:
mv: failed to preserve ownership for `/media/prod_server/DownArrow.png': Permission denied
Is this like NFS and you have to have the same user ID stuff set up?[/QUOTE]

No, sshfs is just like normal ssh, you only need an account on the remote machine. If you look in /etc/mtab when you have a sshfs filesystem mounted you should see a line like

```
sshfs#bob@192.168.1.10:/home/bob /home/jane/sshfs fuse rw,nosuid,nodev,max_read=65536,user=jane 0 0

```

In this example, jane is connected as bob to his home directory on another machine. All files owned by bob will appear to be owned by jane. I'm not sure why you received that error.

---

### Post by jmeadows111 on 2006-01-06
Great howto -- works like a charm!

Thanks very much; it was just what I was looking for! :smile:

---

### Post by David Olivier on 2006-01-07
[QUOTE=freelsjd]I did this and it worked fine.  However, how can I verify the mount (other than using it)?  In other words, the "df" command does not show the sshfs mounted drive.   How to view the mount ?[/QUOTE]

I seem to remember that df *did* show the mounted drive! I'm not at work now, so I can't check it.

Perhaps I typed "df -a" or something. I seem to remember that "df" with no parameters showed a limited list. Or try "df /myMountPoint".

Another way to verify the mount: list the contents of the mountpoint! That works of course if the mounted disk is not empty.

---

### Post by piedamaro on 2006-01-07
Nice tip, thanks.

---

### Post by ZylGadis on 2006-01-14
"df -a" shows it, as does "cat /etc/mtab" :)

---

### Post by PMO6022 on 2006-01-15
I've followed the how-to, but am still having a problem.  Any help is appreciated.  I have ssh set up and working between my client (laptop) and server (desktop).  I've installed sshfs and its dependencies.  I've created a user-owned mountpoint on the client machine.  I added fuse to /etc/modules, and ```
pmorris@ubuntu:~ $ lsmod | grep fuse
fuse                   36748  0
``` confirms that the fuse module is loaded.  However, when I issue the sshfs command, (sshfs 192.168.1.103:</path/to/share> </path/to/mountpoint>, I get the following error:```
fusermount: failed to create device node: Operation not permitted
fusermount: fuse device not found, try 'modprobe fuse' first
``` The only info I've been able to find regarding this error is to do a "sudo modprobe fuse", which is already loaded in my case.  Any ideas?

---

### Post by GrammatonCleric on 2006-01-15
> 192.168.1.103:</path/to/share> </path/to/mountpoint>, I get the following error:```
fusermount: failed to create device node: Operation not permitted
fusermount: fuse device not found, try 'modprobe fuse' first
``` The only info I've been able to find regarding this error is to do a "sudo modprobe fuse", which is already loaded in my case.  Any ideas? 



Have you logged off, or rebooted,  and logged back in?

---

### Post by PMO6022 on 2006-01-15
[quote=GrammatonCleric]Have you logged off, or rebooted,  and logged back in?[/quote]Yes, I've done that more than once.  I also added myself to the "fuse" group.

Update:
Well, I got it working.  I changed the group of /dev/fuse from root to fuse, and reinstalled sshfs, and fuse-utils, and it's working now.  I don't know exactly what was wrong, but it's working now.

---

### Post by kaamos on 2006-02-19
Thanks, it worked!

The only problem is that nautilus thinks that the ssh shares have 0kb free space, so I can't create new files. I can edit the old ones just fine though.. Does anyone have any ideas what could be done about this?

---

### Post by jonny on 2006-03-08
I too was tearing my hair out with the ```
fusermount: mount failed: Operation not permitted
```error message.  I found the answer on the fuse website itself - I needed this command:```
chmod 4755 /usr/bin/fusermount
```Oddly enough only one of my several ubuntu boxes was affected, and reinstalling the packages didn't help at all.  Odd.

---

### Post by i3dmaster on 2006-03-09
```

Filesystem           1M-blocks      Used Available Use% Mounted on
sshfs#yj@ubuntu:/home/yj/
                        976563         0    976563   0% /mnt/remote_home

cat /etc/mtab:
sshfs#yj@ubuntu:/home/yj/ /mnt/remote_home fuse rw,nosuid,nodev,max_read=65536 0 0

sudo ls -lad /mnt/remote_home:
drwxr-xr-x 1 yj users 6328 2006-03-08 17:49 /mnt/remote_home

id:
uid=1000(yj) gid=114(fuse) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),107(scanner),108(admin),114(fuse),1000(yj)

BUT:
cd /mnt/remote_home:
bash: cd: /mnt/remote_home: Permission denied

```
**WHY?**

---

### Post by danpre on 2006-04-02
[QUOTE=sciurus]sshfs has the advantage over a KIOslave or GnomeVFS that any program can use it. For instance, in Kubuntu Amarok wasn't able to play my remote music through fish:/ but worked fine using sshfs.
sshfs remote-system-name:/remote-folder /media/mount-name
[/QUOTE]

Hi, great HOWTO

is it possible to add to line:

sshfs usre_name@remote-system-name:/remote-folder /media/mount-name

password?

I woluld like to add this line to KDE start, so I will have share mounted every time a start a computer

---

### Post by Chris Tucker on 2006-04-25
Wow... thats all i can say after doing this myself.. i had a couple of folders totalling a few hundred pictures, on a different computer in the house, that i needed on my laptop... i had been looking for a reason to use sshfs, and i figured SCP would be a bit too long of a command to get all my files from there to here.... and Damn! its fast! even thumbnailing pictures that are 1mb each, over 54mbps wireless, .. it was the same as if the pictures were on this harddrive already! 

My opinion: A HELL of a replacement to samba!. samba is incredibly slow compared to this
next thing for me to try is whatever nfs is... hmmm...

---

### Post by sal on 2006-05-07
i have followed all the steps in the hoiwto but i keep getting this message:
remote host has disconnected

do i have to add the share on my remote system?

any help thanks.

---

### Post by jamesrw on 2006-05-08
thnx! sshfs, why didnt I know before?

---

### Post by Pausanias on 2006-05-09
[QUOTE=sal]i have followed all the steps in the hoiwto but i keep getting this message:
remote host has disconnected

do i have to add the share on my remote system?

any help thanks.[/QUOTE]

I see you are using dapper. So am I. I used sshfs without problems in breezy but now it doesn't work in dapper.

As far as I can tell it's a problem with the kernel used with dapper.  It seems the author of sshfs needs to update the software to deal with this issue. Quite a bummer, as I'm quite used to sshfs by now.

Someone else reported the same problem here and could only resolve it by downgrading the kernel:

[http://sourceforge.net/mailarchive/forum.php?thread_id=10123569&forum_id=47044](http://sourceforge.net/mailarchive/forum.php?thread_id=10123569&forum_id=47044)

---

### Post by Pausanias on 2006-05-10
[QUOTE=Pausanias]
Someone else reported the same problem here and could only resolve it by downgrading the kernel:

[http://sourceforge.net/mailarchive/forum.php?thread_id=10123569&forum_id=47044](http://sourceforge.net/mailarchive/forum.php?thread_id=10123569&forum_id=47044)[/QUOTE]

OK, user stupidity (mine) was at fault here. Apparently the disconnected message happens whenever the named host is nonexistent or unreachable. It should really say "host not found," but it says disconnected instead. So if you get that error message, make sure you are able to ssh in to the host exactly as it's being passed to sshfs.

---

### Post by dmizer on 2006-05-28
[QUOTE=kaamos]Thanks, it worked!

The only problem is that nautilus thinks that the ssh shares have 0kb free space, so I can't create new files. I can edit the old ones just fine though.. Does anyone have any ideas what could be done about this?[/QUOTE]
i also show 0 free space when mounting this way.  i cannot create new files because my client thinks there is no freespace.

i am able to mount this way, and i am able to view the shares.  it just shows 0 free space.

---

### Post by dmizer on 2006-05-28
found it.  according to this thread: [http://ubuntuforums.org/showthread.php?t=174691&highlight=fuse+free](http://ubuntuforums.org/showthread.php?t=174691&highlight=fuse+free)

this is a "glitch" in the sshfs and file transfer can be done by the cli only.

---

### Post by reinibaerli on 2006-10-12
I am using edgy and installed sshfs according to post #1 and I got an error, too: 
> fuse: failed to exec fusermount: Permission denied
So my solution was to 
> sudo chgrp fuse /dev/fuse
and it worked.

Can it be that this is a bug in the installation that should be reported?

Thanks,
Reinhard

---

### Post by jetpeach on 2006-10-30
anybody know how to get write access to a share?  i tried adding to the sshfs command "-o uid=1000" where 1000 is my user id.  it changed the user id of the folders in the mount to mine, but i still can't write to the directories :(

---

### Post by Tomy on 2006-11-18
From jonny's post #28

chmod 4755 /usr/bin/fusermount


Thanks, this solved my problems.

I am using Ubuntu Edgy and could only mount as root and had to access files from the CLI. Now things appear to work properly and I can mount as a user and use Nautilus.

---

### Post by nybbler on 2006-11-29
> **cdean said:**
> ```
[cdean@frog ~]$ sshfs 192.168.1.3: linuxbox
cdean@192.168.1.3's password:
fuse: failed to exec fusermount: Permission denied
```

I'm getting that error after following the HOWTO...

I think you missed the bit about logging back out and back in. You've added yourself to the fuse group with:

> 3) Add yourself to the 'fuse' group, then log out and log in again.
sudo adduser your-username fuse

If you don't logout and back in then your session doesn't pick up the fuser group. I was too lazy to log out so I just did:

 su - my-username

It asked for my password, and hey presto a new session with the new groups. Just type 'groups' to see what groups your session has.

---

### Post by gleenn on 2006-12-31
If you are still getting permission errors, make sure you log out and back in again for the group permissions to be re-evaluated. Otherwise you will have added yourself to the fuse group but not seen the effect.

--G

---

### Post by jtc on 2007-01-10
I've pretty much gotten ssfhs working the way I want.

I works perfectly for file-operations, playing multimedia, etc etc.

Today when I was working in Kword I noticed something disturbing thought. The first time I save my dokument it saves perfectly, but when I continues to save the updated dokument (same filename) nothing happens. It is still the orginal file from the first save with the same timestamp and content. 

Something is registred thought, because at the moment of saving the filname~ (backupfile) is created. No matter how many save I do it is still just a backup of the orginal save.

When I try to reproduce the same problem in OpenOffice-writer and Emacs the saving behaves as it should. They continue to save new content, just as they should.

Anyone who has any idéa why Kword and sshfs don't get along?

Below follow the sshfs-mount in question.

sshfs#mauddib:/home/andreas/Documents on /home/andreas/Documents type fuse (rw,nosuid,nodev,max_read=65536,user=andreas)

---

### Post by jtc on 2007-01-11
Well, I found the solution to the problem with sshfs and koffice, mentioned above.

[http://bugs.kde.org/show_bug.cgi?id=126846]("http://bugs.kde.org/show_bug.cgi?id=126846")
(Additional Comment #5)

In short, you want to use: -o workaround=rename

---

### Post by qgfreire on 2007-01-15
Thanks, it seems Edgy have this problem!
](*,)

---

### Post by motin on 2007-01-24
> **Gandalf said:**
> isn't NFS far more better? i use NFS to connect any linux laptop to my external HDD and windows clients use samba, everything is extremely fast and just amasing

To quote [http://linux.inet.hr/sshfs_secure_and_transparent_access_to_remote_filesystems.html:](http://linux.inet.hr/sshfs_secure_and_transparent_access_to_remote_filesystems.html:)
> While sshfs may not be as fast and featureful as other full-blown network filesystems such as NFS or Samba, it still has some great features:

    * very easy to use, on the server side there's nothing to do, on the client side mounting the filesystem is as easy as logging into the server with ssh
    * provides secure (encrypted) access to remote files
    * has decent performance (multithreaded, caching directory contents and allowing large reads)
    * should work well even over slow and/or unstable links (think dialup), knows how to reconnect to the server when the connection is broken 

A matter of taste and what suits one's needs really. 

Btw - here is a similar thread that goes a bit further: [http://www.ubuntuforums.org/showthread.php?t=324254](http://www.ubuntuforums.org/showthread.php?t=324254)

---

### Post by motin on 2007-01-24
I love sshfs and the fact that the use of it in conjunction with nautilus blows away all other FTP programs available for the Linux and Windows Desktops. Working on webprojects today is much leaner and efficent - not to say more good looking!

---

### Post by noahspurrier on 2007-02-27
To get around this error:
    glib-2.0fuse: failed to exec fusermount: Permission denied
I needed to do this chmod two files:
    $ sudo chmod +x /usr/bin/fusermount
    $ sudo chmod a+rw /dev/fuse
I tried putting my user in the 'fuse' group and logging back in, but that didn't help.

Yours,
Noah

---

### Post by penvzila on 2007-05-01
What if my username on the server I'm trying to log in to is different than my account name in Ubuntu?  I don't see any way for sshfs to handle that.

---

### Post by penvzila on 2007-05-01
Gah nevermined.  It was a typo.

---

### Post by dsauxier on 2007-12-05
FYI, it seems that the location of fusermount has changed as of Gutsy Gibbon (7.10)
It's now in /bin/fusermount instead of /usr/bin/fusermount

---

### Post by qpieus on 2008-01-05
> **penvzila said:**
> What if my username on the server I'm trying to log in to is different than my account name in Ubuntu?  I don't see any way for sshfs to handle that.

You just put your remote username and @ before the remote machine address, like so:```
sshfs **username@**remote-system-name:/remote-folder /media/mount-name
```

---

### Post by darck on 2008-03-10
how to make it other way - mount local folder on remote ssh server.
my computer client's fodler mount to ssh server
?

---

### Post by OfMacandMen on 2008-04-05
I had the same problem and this is what I did to fix it!

#add user to fuse
adduser user fuse 

Then this part is what took me the longest to figure out.

LOGOFF!!

Yep after four hours it dawned on me that maybe in order to reset my group setting I may have to logoff!!

Work great!

---

### Post by misoul on 2008-10-08
I'm compiling fuse for developing. The source was retrieved by apt-get and was compiled naively with no additional option. This is what I got when trying the example in fuse code:

fusermount: mount failed: Operation not permitted

I've looked at all the suggestions in previous threads and I'm sure that there's nothing wrong with my setup. After banging my head on the wall and lots of hair pulling, this is what I've found:

- The binaries in fuse example link against libfuse.so in my compilation, which turns out to be the problem.
- To validate this, I wrote a small program using fuse. Linking against the libfuse.so provided by Ubuntu works just fine, but linking against the one I compiled poses "Operation not permitted".

I thought I missed some option during configure, but it turns out not very likely. So I think Ubuntu is doing something funky here.

And btw, this is Ubuntu Hardy and fuse-2.7.2. I hope this can save some of us lots of frustrating hours.

Cheers.

---

### Post by lwhitmore on 2008-10-21
When I first started to use sshfs a couple of months ago, I found that copying files and browsing directories would cause my system to hang ... only for a couple of seconds - but it was enough to make the system cumbersome.  

Adding the following parameters to the standard 'sshfs' command, made my connection run MUCH faster..  ymmv, but I thought I'd pass on the tip.

-o ServerAliveInterval=15 -o cache_timeout=600

---

### Post by physeetcosmo on 2009-03-30
> **GrammatonCleric said:**
> I believed that fusemount is installed so root only and execute it try the following.

```
sudo chmod +x /usr/bin/fusermount
```

- GC

All,

I was having the same problem until I used an option with sshfs:

```
$ sudo sshfs [COLOR=Red]-o allow_other[/COLOR] <SERVER_SSH_USERNAME>@<SERVER_EXTERNAL_IP>:/<SHARED_DIRECTORY_ON_SERVER> /<WHERE_TO_MOUNT_ON_CLIENT> 
```

The -o allow_other will allow any user on the local client to open the folder. Remember that the read/write is done **on the Server side** not on the client side. But the access to the SSH pipe is determined on the client side. Thus this option is allowing any user to access the ssh pipe!

Ahhhh, encryption!! :)

---

### Post by Nausser on 2010-12-16
I followed the instructions in the initial post with perfect success! Thank you!

---

### Post by Jack Waugh on 2011-03-19
withdrawn

---

### Post by masuch on 2011-09-06
> **sciurus said:**
> sshfs has the advantage over a KIOslave or GnomeVFS that any program can use it. For instance, in Kubuntu Amarok wasn't able to play my remote music through fish:/ but worked fine using sshfs.

1) Install the software
sudo apt-get install sshfs

2) Add fuse to /etc/modules
sudo nano /etc/modules

3) Add yourself to the 'fuse' group, then log out and log in again.
sudo adduser your-username fuse

4) Create a mountpoint and give yourself ownership
sudo mkdir /media/mount-name
sudo chown your-username /media/mount-name

5) Mount the filesystem
sshfs remote-system-name:/remote-folder /media/mount-name

6) Unmount the filesystem
fusermount -u /media/mount-name

Directions taken from [http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/) More info on sshfs is available at [http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)

I've run into a strange problem on two Kubuntu machines where, after using sshfs, you're unable to unlock your own computer. Logging in works fine, but you can't return from a password-protected screensaver. My solution was to start a new session, change my password, then return to the old session and use the new password to unlock it.


Thanks a lot - works.

---

