---
title: "How to chroot ssh user using Jailkit"
date: 2006-09-01
forum: Tutorials
---

### Post by trawler on 2006-09-01
After setting up my secure ftp server (vsftpd) I needed a solution to allow users to log in, without giving them access to the entire system.

This is my first "How To" so i hope it'll be able to help someone :).

In order to set up the ssh enviroment, I used Jailkit. You can get it [here]("http://olivier.sessink.nl/jailkit/jailkit-2.0.tar.gz").


_**Installation**_
After downloading it, compile and install it:
```
tar -zxvf jailkit-2.0.tar.gz
```
```
cd jailkit-2.0
```
```
./configure
```
```
make
```
```
sudo make install
```


_**Setting The "Jail" Up**_
After you've installed it, it's time to set up the "root" directory (the directory to which the users will be jailed to).
```
sudo mkdir /jail 
```
```
sudo chown root:root /jail
```


_**Creating the Proper Environment**_
The following lines will allow the logged in user to use whichever set of programs you won't to allow:
```
sudo jk_init -v /jail basicshell 
sudo jk_init -v /jail editors 
sudo jk_init -v /jail extendedshell 
sudo jk_init -v /jail netutils 
sudo jk_init -v /jail ssh 
sudo jk_init -v /jail sftp
``` 


_**Creating and Jailing the User**_
```
sudo adduser thomas
```
```
sudo jk_jailuser -m -j /jail thomas
```
In /etc/passwd thomas' line should look something like that:
```
thomas:x:1001:500::/jail/./home/thomas:/usr/sbin/jk_chrootsh
```
Don't forget to set the password while you're at it:
```
sudo passwd thomas
```


_**Setting Up the Home Directory**_
To the users logging in to this secured environment "/jail" will just show up as the "/" directory, so setting up a home directory is also needed:
```
sudo mkdir -p /jail/home/thomas
```
```
chown thomas:thomas /jail/home/thomas
```


_**Passwords**_
edit the /jail/etc/passwd and /jail/etc/group files with your favorite editor and add these lines (The numbers mentioned are the user and groups id, which you can check by opening the /etc/passwd file and look for the appropriate user):
```
sudo vi /jail/etc/group

paste and save this:
thomas:x:500:
```
```
sudo vi /jail/etc/passwd

paste and save this:
thomas:x:1001:500::/home/thomas:/bin/bash
```


One last thing:
```
sudo cp /home/trawler/.bashrc /jail/home/thomas
```
```
sudo chown thomas:thomas /jail/home/thomas/.bashrc
```

And that should do it! :)
you can check the configuration by "ssh'ing" your machine:
```
ssh thomas@localhost
```
And make sure everything's ok.

If anything's gone wrong /var/log/auth.log will give you the needed details:
```
tail /var/log/auth.log
```

---

### Post by trawler on 2006-09-02
Edited:

Added instructions for adding the .bashrc file to the new home directory... otherwise you get a funky defaultive [bash] prompt...

---

### Post by peabody on 2006-09-02
Pretty nice looking.  How does jailkit compare to just setting up a minimum system in a folder via debootstrap?

---

### Post by trawler on 2006-09-02
Never tried debootstrap, so i can't really comment on it, but I like the versatility and simplicitly of jailkit... once you've figured out how to set it, jailing more users with different environments is simply a matter of a couple or more command lines.
anyway, it works great for me :)

---

### Post by denver on 2006-09-19
Thanks ALOT! I have been looking for a way to jail sftp users and i have been banging my head with a howto but with no success.
You're HOWTO worked like a charm! Thanks loads!

---

### Post by trawler on 2006-09-30
Thanks a bunch *blush*.
glad i was able to help.

---

### Post by Clochard on 2006-10-20
Really excited about this, but it doesn't seem to be working.  When I try to run the jk_jailuser command it complains that the shell is missing.  Sure enough the entire /jail/usr/sbin directory is missing!

```

kirk@Spontaneity:~$ sudo adduser community
Adding user `community'...
Adding new group `community' (1003).
Adding new user `community' (1003) with group `community'.
The home directory `/home/community' already exists. Not copying from `/etc/skel'
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
Changing the user information for community
Enter the new value, or press ENTER for the default
        Full Name []:
        Room Number []:
        Work Phone []:
        Home Phone []:
        Other []:
Is the information correct? [y/N] y

```

So then the failure...
```

kirk@Spontaneity:~$ sudo jk_jailuser -m -j /jail community
invalid shell, /jail/usr/sbin/jk_lsh does not exist
enter jail directory:
aborted..
kirk@Spontaneity:~$
kirk@Spontaneity:~$ ls -l /jail
total 2
drwxr-xr-x 2 root root  896 2006-10-19 23:13 bin
drwxr-xr-x 2 root root   96 2006-10-19 23:13 dev
drwxr-xr-x 4 root root  408 2006-10-19 23:13 etc
drwxr-xr-x 2 root root   48 2006-10-19 23:12 home
drwxr-xr-x 3 root root 1040 2006-10-19 23:13 lib
drwxr-xr-x 5 root root  120 2006-10-19 23:13 usr
kirk@Spontaneity:~$

```

I've seen no errors other than this following the HOWTO - why is my sbin not being copied over and/or created properly?  Any ideas?

---

### Post by tintax on 2006-10-20
Please bear in mind I have only enough knowledge of jailkit to be dangerous - and anything security related should be properly researched - but try:

```
sudo jk_init -v /jail jk_lsh
```

This ought to copy the 'limited shell' and any associated libraries into your jail. Hope this helps.

---

### Post by trawler on 2006-10-21
Another workaround is to follow the tutorial :)

> 
sudo vi /jail/etc/passwd

paste and save this:
thomas:x:1001:500::/home/thomas:/bin/bash


the default line would be **thomas:x:1001:1001:,,,:/home/thomas:/usr/sbin/jk_lsh**

which needs to be changed to:
**thomas:x:1001:1001:,,,:/home/thomas:/bin/bash**

---

### Post by Clochard on 2006-10-21
Indeed, that did the trick - I was able to run the comand and get a new error message!  But when I try a second time with no changes it lists the user as already jailed.  I suppose the only way to test this is to log in as the user and try to get out?  But that doesn't sound very robust.

```

kirk@Spontaneity:~$ sudo jk_init -v /jail jk_lsh
Password:
/jail/lib/libnsl.so.1 exists
/jail/lib/libnss_compat.so.2 exists
/jail/lib/libnss_files.so.2 exists
/jail/etc/nsswitch.conf exists
creating directory /jail/usr/sbin
copying /usr/sbin/jk_lsh to /jail/usr/sbin/jk_lsh
/jail/lib/tls/i686/cmov/libc.so.6 exists
/jail/lib/ld-linux.so.2 exists
creating directory /jail/etc/jailkit
copying /etc/jailkit/jk_lsh.ini to /jail/etc/jailkit/jk_lsh.ini
user root exists in /jail/etc/passwd
group root exists in /jail/etc/group
kirk@Spontaneity:~$ sudo jk_jailuser -m -j /jail community
Traceback (most recent call last):
  File "/usr/sbin/jk_jailuser", line 297, in ?
    main()
  File "/usr/sbin/jk_jailuser", line 288, in main
    jailuser(jail, username, movehome, config)
  File "/usr/sbin/jk_jailuser", line 177, in jailuser
    shutil.copy(oldhome, newhome)
  File "/usr/lib/python2.4/shutil.py", line 81, in copy
    copyfile(src, dst)
  File "/usr/lib/python2.4/shutil.py", line 47, in copyfile
    fsrc = open(src, 'rb')
IOError: [Errno 21] Is a directory
kirk@Spontaneity:~$ sudo jk_jailuser -m -j /jail community
Password:
home directory /jail/./home/community is already inside the jail
kirk@Spontaneity:~$

```

---

### Post by trawler on 2006-10-23
Once you've already configured everything, you'll notice these error messages since the environment has already been set. The only thing you changed was the bash environment, so there's no need to run it all again.

---

### Post by jgreenleaf on 2007-03-12
I followed these instructions to the letter and confirmed that the jail is working. My problem however is that sftp does not work for the user that I have jailed. When I run the following command (sudo jk_init -v /jail sftp) I get the following error: 

/jail/lib/libnss_dns.so.2 exists
/jail/etc/resolv.conf exists
/jail/etc/host.conf exists
/jail/etc/hosts exists
/jail/etc/protocols exists
/jail/lib/libnsl.so.1 exists
/jail/lib/libnss_compat.so.2 exists
/jail/lib/libnss_files.so.2 exists
/jail/etc/nsswitch.conf exists
/jail/usr/lib/sftp-server exists
source file /usr/libexec/openssh/sftp-server does not exist
source file /usr/lib/misc/sftp-server does not exist
device /jail/dev/urandom does exist already

The user can ssh in and is successfully jailed to his home folder however, when running FileZilla for SFTP over SSHv2, he cant connect. Here is the error log:

Mar 12 14:28:59 ubuntu sshd[4667]: Accepted password for brandon from xxx.xxx.xxx.xxx port 36189 ssh2
Mar 12 14:28:59 ubuntu sshd[4669]: (pam_unix) session opened for user brandon by (uid=0)
Mar 12 14:28:59 ubuntu sshd[4669]: subsystem request for sftp
Mar 12 14:28:59 ubuntu jk_chrootsh[4670]: now entering jail /jail for user brandon (1009)
Mar 12 14:28:59 ubuntu sshd[4669]: (pam_unix) session closed for user brandon

I cant figure out how to get this user to use SFTP using FileZilla. It looks like the connection is being made but since SFTP was not installed (see errors above), he is kicked out. Any suggestioins?

---

### Post by jcarlock on 2007-04-16
I was able to get past one of the two errors by editing the /etc/jailkit/jk_init.ini and changed libexec to lib for the /openssh/sftp-server.

Nonetheless it still does not work.  I have remoed all the users and the jail and tried again, but I get the exact same errors.

JC

---

### Post by dutchcowboy on 2007-05-29
Hi,

I'm having a problem. I followed the instructions to a T, but when I try to sftp to my ubuntu box it authenticates successfully, but then just closes the connection. Here's what auth.log is showing:

May 29 15:21:19 zasfosftp sshd[11085]: subsystem request for sftp
May 29 15:21:19 zasfosftp jk_chrootsh[11086]: now entering jail /home/Jail for user mmad (1001)
May 29 15:21:19 zasfosftp sshd[11085]: (pam_unix) session closed for user mmad

Ubuntu version 7.04
Jailkit version 2.0

Any one have any ideas as to how I should try to trouble shoot this?

Thanks for your help,

Dutch Cowboy :)

---

### Post by evilbunnyfufu on 2007-05-31
the pain of the sftp failure..
fixed with one simple change..
one simple line..
one simple /dev/null

bash ing my head on the wall i found a magic fairy hiding with an error giving me the key to unlock my beloved sftp

..
one fine eve, i logged into my jailed.. account ssh'ed i did.. out of wonder and confusion i ran the sftp-server command.. wondering what worlds may await.. presented with an error, surely from the error fairy it is!

bobcat@ftp:/usr/lib/openssh$ ./sftp-server
Couldn't open /dev/null: No such file or directorybobcat@ftp:/usr/lib/openssh$

bloody hell i cried out, my /dev/null has been /dev/null'ed

quickly i ran to my best editor vi.. vi i cried out.. edit 

```
 vi /etc/jailkit/jk_init.ini 
```

as fast as my keyboard could take me, i went to the sftp section of the file.. and looked deeply and low n behold i found..

```

[sftp]
comment = ssh secure ftp
executables = /usr/lib/sftp-server, /usr/lib/openssh/sftp-server, /usr/lib/misc/sftp-server
includesections = netbasics, uidbasics
devices = /dev/urandom 
```

no /dev/null i cryied out.. with the quickest of fingers i added my beloved /dev/null

```

[sftp]
comment = ssh secure ftp
executables = /usr/lib/sftp-server, /usr/lib/openssh/sftp-server, /usr/lib/misc/sftp-server
includesections = netbasics, uidbasics
devices = /dev/urandom, /dev/null 
```

and saved the file.. then gave the order for sftp to be installed..

```
 jk_init /jail/bobcat sftp 
```

nothing happen it said nothing, my nervs rattled at the deathly nothing.. i did the only thing i could..

```

root@ftp:/var/log# sftp bobcat@localhost
Connecting to localhost...
bobcat@localhost's password:
sftp> quit 
```

For Joy! For Joy! the god and goddess have provided me with the magic that is SFTP!! 

and now i depart this tale, this tale of sorrow this tale of happiness and hope you leave knowing what the error fairy told me.. knowing a bit more of life. :D

---

### Post by ess on 2008-01-08
I have followed the instructions provided above and didn't work for me.

I googled and search the net for instructions and was not successful either. 

eventually, I visited the the following howto from jailkit and it worked from the first try

[http://olivier.sessink.nl/jailkit/howtos_chroot_shell.html](http://olivier.sessink.nl/jailkit/howtos_chroot_shell.html)

I am not 100% sure why it didn't work first time around, but it might have something to do with not having created a tmp directory.

Cheers
~E

---

### Post by netscribe on 2008-02-04
Along these lines ... can one su to another privleged / non-jailed user once logged in?   I'm trying to have all SSH users on a box be jailed at first, but those with admin capabilities can su out... would that work?

---

### Post by netscribe on 2008-02-04
nevermind - I decided to allow those admins different access, and everyone else - chroot/jail ... Thanks anyway

---

### Post by Falcon4ever on 2008-04-11
> **ess said:**
> I have followed the instructions provided above and didn't work for me.

I googled and search the net for instructions and was not successful either. 

eventually, I visited the the following howto from jailkit and it worked from the first try

[http://olivier.sessink.nl/jailkit/howtos_chroot_shell.html](http://olivier.sessink.nl/jailkit/howtos_chroot_shell.html)

I am not 100% sure why it didn't work first time around, but it might have something to do with not having created a tmp directory.

Cheers
~E

those instructions worked fine here in dapper, but i would like to have some compiler tools available to my users. Is it possible to add those with jailkit?

---

### Post by frenchn00b on 2008-05-11
> **Falcon4ever said:**
> those instructions worked fine here in dapper, but i would like to have some compiler tools available to my users. Is it possible to add those with jailkit?

  
Please those you managed to make SFTP work... please could you post 

all you have ?
/etc/jailkit content
+ permissions of the folders 
+ a complete ls -la of the /home/jail ?

thanks a lot for others who are fighting (like hell with that program) !:)

---

### Post by s0l1dsnak3123 on 2008-05-24
I also followed the instructions, but I also can't get it to work :/

The main difference between my situation and other people's is that I am dedicating an entire partition to the jailed user, I don't want write access, and the partition is fat32.

When I ssh into local host I get this:

```
snak3@snak3untu:~$ ssh anon@localhost
anon@localhost's password: 
Linux snak3untu 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Sat May 24 18:59:39 2008 from localhost
Connection to localhost closed.
snak3@snak3untu:~$ ssh anon@localhost
anon@localhost's password: 
Linux snak3untu 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Sat May 24 18:59:59 2008 from localhost
Connection to localhost closed.

```

When I tail the logfile mentioned in the first post I get this:

```

snak3@snak3untu:~$ tail /var/log/auth.log
May 24 19:01:42 snak3untu jk_chrootsh[7598]: path /media/disk/./home/anon is not owned by user 1002
May 24 19:01:42 snak3untu jk_chrootsh[7598]: path /media/disk/./home/anon is not owned by group 1002
May 24 19:01:42 snak3untu jk_chrootsh[7598]: abort, path /media/disk/./home/anon is not owned by 1002
May 24 19:01:42 snak3untu sshd[7597]: pam_unix(sshd:session): session closed for user anon
May 24 19:02:27 snak3untu sudo:    snak3 : TTY=pts/0 ; PWD=/home/snak3 ; USER=root ; COMMAND=/usr/bin/nano /media/disk/etc/group
May 24 19:02:27 snak3untu sudo: pam_unix(sudo:session): session opened for user root by snak3(uid=0)
May 24 19:02:27 snak3untu sudo: pam_unix(sudo:session): session closed for user root
May 24 19:03:24 snak3untu sudo:    snak3 : TTY=pts/0 ; PWD=/home/snak3 ; USER=root ; COMMAND=/usr/bin/nano /media/disk/etc/passwd
May 24 19:03:24 snak3untu sudo: pam_unix(sudo:session): session opened for user root by snak3(uid=0)
May 24 19:03:24 snak3untu sudo: pam_unix(sudo:session): session closed for user root

```

my fstab is as follows:

```

/dev/sda2                                  /media/disk     vfat         uid=root,gid=root           0  0  

```

Thanks for help in advance :)

s0l1dsnak3123

---

### Post by teamanx on 2008-06-09
> **frenchn00b said:**
> Please those you managed to make SFTP work... please could you post 

all you have ?
/etc/jailkit content
+ permissions of the folders 
+ a complete ls -la of the /home/jail ?

thanks a lot for others who are fighting (like hell with that program) !:)

Hi, french. I have SFTP working, but I cannot post the info you request to a public forum (this would compromise the security of my server). Just try this howto: [http://olivier.sessink.nl/jailkit/howtos_sftp_scp_only.html](http://olivier.sessink.nl/jailkit/howtos_sftp_scp_only.html)
Then try to log in remotely to SFTP, and if you cannot, please post here the result of "tail auth.log", an I'll see if I can help.
;)

---

### Post by Razzack71 on 2008-09-20
Hi all. Got the same problem as dutchcowboy. -The connection closes right after beeing established. This is what my auth has to say about it:

Sep 20 20:14:19 Moonlight jk_chrootsh[10198]: now entering jail /jail for user thomas (1003)
Sep 20 20:14:19 Moonlight jk_chrootsh[10198]: ERROR: failed to execute shell /usr/sbin/jk_lsh for user supplier (1003), check the permissions and libraries of /jail//usr/sbin/jk_lsh
Sep 20 20:14:19 Moonlight sshd[10197]: pam_unix(sshd:session): session closed for user thomas

-What have I missed here besides learning a bit more Linux? :)

---

### Post by cycloptivity on 2008-10-18
Razzack71 & Dutchcowboy;

Try chaging your <jail>/etc/passwd to read something like this
```
swilson@services:~$ cat /jail/etc/passwd 
kahn:x:1001:1001:Sam Wilson,,,:/home/kahn:/bin/bash
swilson@services:~$ 

```

rather then the shell being /bin/jk_lsh (I forget exactly what it was :P)

Has anyone had problems getting xterm running in the chroot? I have been fighting for a hour or two now with no luck :( Will post back with a breakthrough soon hopefully

- Kahn

---

### Post by alexbroe on 2008-10-22
Hi,

great how to, nevertheless it doesn´t work for me... :confused:

I have Ubuntu 8.04 Desktop with openssh-server and ftpd-ssl on it. Works fine, but without the jail...

I get the problem right at the beginning. Your 3rd command is 

```
./configure
```

where I get 

> 
gvl-ftp@gvl-ftp:~/jailkit-2.0$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
gvl-ftp@gvl-ftp:~/jailkit-2.0$ pwd
/home/gvl-ftp/jailkit-2.0
gvl-ftp@gvl-ftp:~/jailkit-2.0$


In the config.log it says

> 
Thread model: posix
gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
configure:1658: $? = 0
configure:1660: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:1663: $? = 1
configure:1686: checking for C compiler default output file name
configure:1689: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:1692: $? = 1
configure: failed program was:
| /* confdefs.h.  */
|
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "jailkit"
| #define VERSION "2.0"
| #define _GNU_SOURCE 1
| /* end confdefs.h.  */
|
| int
| main ()
| {
|
|   ;
|   return 0;
| }
configure:1731: error: C compiler cannot create executables
See `config.log' for more details.


and 

> 
configure: exit 77


any idea?

best regards

Alexander Broemmelsiek

---

### Post by trickyhu on 2008-11-22
Hey,

If you modify the setting up of the jail user from:

```
sudo jk_jailuser -m -j /jail thomas
```

to:

```
sudo jk_jailuser -m -s /bin/bash -j /jail thomas
```

You won't have to manually override it in the passwd file for setting the default shell.

Doug

---

### Post by obg123 on 2008-11-26
Is this "jail kit" just a new shell? Then what happens if you try to run bash (or plain sh or any shell) from within this? You're still in jail?

---

### Post by victorbrca on 2009-01-22
I'm trying to delete my history at logout but it's not working. Does anyone knows if .bash_logout is read for the jailkit user?


Vic.

---

### Post by pallee on 2009-04-06
Hi, I have just successfully set up jailkit 2.0.

At first (or the entire day) I got the same auto-disconnect error when trying to use sftp, as many of you guys until i, by chance, did a

```
sudo apt-get update
sudo apt-get upgrade
```

and saw that openssh-server whas held back from the upgrade. So i did an

```
sudo apt-get install openssh-server
```

and that solved my problem.
hopfully this helps you to!
Cheers, Paul

---

### Post by komitaltrade on 2010-05-29
I have proble.

After 

sudo jk_jailuser -m -j /jail user

I have

invalid shell, /jail/usr/sbin/jk_lsh does not exist
enter jail directory:

What now (it is version 2.11)?

---

### Post by georgoz on 2011-05-20
Just take a look at rssh. It allows you to jail user just for some specific commands like rssh scp, sftp, cvs, svn, rsync or rdist.

```
sudo apt-get install rssh
```

---

### Post by thematrixuum on 2012-03-23
Can we use this tutorial for existing users and folders?

---

