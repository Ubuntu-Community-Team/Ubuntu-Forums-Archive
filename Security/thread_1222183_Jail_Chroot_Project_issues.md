---
title: "Jail Chroot Project issues"
date: 2009-07-24
forum: Security
---

### Post by Cyked on 2009-07-24
I'm trying to create a chroot jail and running into a problem.  I'm using version 1.9 and when I try to create a user with "addjailuser" I get:

```
addjailuser
A component of Jail (version 1.9 for linux)
http://www.jmcresearch.com/projects/jail/
Juan M. Casillas <juanm.casillas@jmcresearch.com>

Adding user chroot in chrooted environment /var/chroot
 Error: Can't add the user.
Done.

```

Any thoughts?

---

### Post by kevdog on 2009-07-24
Do you need to run the command as root?

---

### Post by Cyked on 2009-07-25
> **kevdog said:**
> Do you need to run the command as root?

I've ran is with sudo and as root, no worky.

---

### Post by Cyked on 2009-07-28
Anyone have any experience with this?

---

### Post by bmturney on 2009-07-30
I'm not sure what your issue is here.. I just setup a chroot jail a couple of days ago... and I used jailkit... it worked like a champ.. 

just a thought...

---

### Post by Cyked on 2009-08-03
I'm working with jailkit 2.7 now and running into a WTF did I do moment.

I get down to jk_jailuser and am having an issue. How did I get to this?  Fooling around too much I'm sure...

At any rate... why do I get this long string when trying to jail a user?


```
home directory /home/jail/./home/jail/./home/jail/./home/jail/./home/jail/./home/sftproot/./home/sftproot/./home/sftproot/./home/sftproot/./home/sftproot/./home/sftproot/./home/sftproot/./home/sftp/. does not exist, nothing moved
```

---

### Post by Cyked on 2009-08-04
Any ideas?  Why does doing jailuser just keep building up that line.

---

### Post by Cyked on 2009-08-04
EDIT: I can't read. :D

So what I did, to be more clear:
1) created an account for sftp use
2) jk_init -v -j /home/jaildirectory basicshell extendedshell sftp scp
3) jk_addjailuser -m -j /home/jaildirectory sftpaccount


 

If I use SCP with winSCP to connect I get:


```
2009-08-04 14:49:05.130 Prompt (1, SSH login name, , login as: )
. 2009-08-04 14:49:11.786 Prompt (6, SSH password, , &Password: )
. 2009-08-04 14:49:13.286 Sent password
. 2009-08-04 14:49:13.411 Access granted
. 2009-08-04 14:49:13.443 Opened channel for session
. 2009-08-04 14:49:13.505 Started a shell/command
. 2009-08-04 14:49:13.505 Server sent command exit status 7
. 2009-08-04 14:49:13.505 --------------------------------------------------------------------------
. 2009-08-04 14:49:13.505 Using SCP protocol.
. 2009-08-04 14:49:13.505 Doing startup conversation with host.
. 2009-08-04 14:49:13.568 Skipping host startup message (if any).
. 2009-08-04 14:49:13.568 Disconnected: All channels closed
* 2009-08-04 14:49:13.630 (ESshFatal) Connection has been unexpectedly closed. Server sent command exit status 7.
* 2009-08-04 14:49:13.630 Error skipping startup message. Your shell is probably incompatible with the application (BASH is recommended).
```


If I use SFTP:

```
 2009-08-04 14:48:12.708 Sent password
. 2009-08-04 14:48:12.849 Access granted
. 2009-08-04 14:48:12.911 Opened channel for session
. 2009-08-04 14:48:12.990 Started a shell/command
. 2009-08-04 14:48:12.990 --------------------------------------------------------------------------
. 2009-08-04 14:48:12.990 Using SFTP protocol.
. 2009-08-04 14:48:12.990 Doing startup conversation with host.
> 2009-08-04 14:48:12.990 Type: SSH_FXP_INIT, Size: 5, Number: -1
. 2009-08-04 14:48:12.990 Server sent command exit status 3
. 2009-08-04 14:48:12.990 Disconnected: All channels closed
* 2009-08-04 14:48:13.036 (ESshFatal) Connection has been unexpectedly closed. Server sent command exit status 3.
* 2009-08-04 14:48:13.036 Cannot initialize SFTP protocol. Is the host running a SFTP server?

```

I checked /etc/passwd: 
```
sftpaccount:x:1003:1004::/home/sftpaccount:/usr/sbin/jk_lsh
```

If I change it to /jk_chrootsh:

scp

```
. 2009-08-04 15:53:35.318 Access granted
. 2009-08-04 15:53:35.349 Opened channel for session
. 2009-08-04 15:53:35.396 Started a shell/command
. 2009-08-04 15:53:35.396 Server sent command exit status 111
. 2009-08-04 15:53:35.396 Disconnected: All channels closed
* 2009-08-04 15:53:35.490 (ESshFatal) Connection has been unexpectedly closed. Server sent command exit status 111.
* 2009-08-04 15:53:35.490 Authentication failed.
```

SFTP still gives me the: 
```
Cannot initialize SFTP protocol. Is the host running a SFTP server?
```

---

### Post by Cyked on 2009-08-05
I am determined to make this work  :P..... with marginal success.

I scrapped what I had and carefully started again.

the /etc/password has the shell as /bin/bash now, and everything thing seems ok.  I can SFTP in and create files, BUT I can browse to things outside of /home/sftpaccount.  Am I only jailed to /home/jail/home?  Shouldn't I be jailed to /home/jail/home/sftpaccount?

scp gives me this error in winscp
```
Command 'groups'
failed with return code 127 and error message
/bin/bash: line 30: groups: command not found.

```

Even still, I can get in this way and view everything after the error...

---

### Post by Cyked on 2009-08-10
Can anyone answer this please?

Am I only jailed to /home/jail/home?  Shouldn't I be jailed to /home/jail/home/sftpaccount?

If I am not understanding how the jailkit works, fine.  It just seems the accounts would be jailed to /account name, not /home/jail/home.

Thanks!

---

