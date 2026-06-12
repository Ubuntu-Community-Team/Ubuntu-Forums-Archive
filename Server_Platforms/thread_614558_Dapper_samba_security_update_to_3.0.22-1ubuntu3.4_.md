---
title: "Dapper samba security update to 3.0.22-1ubuntu3.4 breaks nmbd"
date: 2007-11-16
forum: Server Platforms
---

### Post by bash.gordon on 2007-11-16
After updating samba to 3.0.22-1ubuntu3.4 nmbd segfaults on both of our dapper servers (1 x86 and 1 x86_64) on startup.

Thank you for any hint!
Andreas
------------
Following panic action e-mail is sent (after installing samba-dbg):

The Samba 'panic action' script, /usr/share/samba/panic-action,
was called for pid 6380 (/usr/sbin/nmbd).

Below is a backtrace for this process generated with gdb, which shows
the state of the program at the time the error occurred. 

If the problem persists, you are encouraged to first install the 
samba-dbg package which contains the debugging symbols for samba 
binaries. Then, submit the provided information as a bug report to Ubuntu.
For information about the procedure for submitting bug reports, please
see [http://www.ubuntulinux.org/support/bugs/document_view](http://www.ubuntulinux.org/support/bugs/document_view)

Using host libthread_db library "/lib/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread 46912522285168 (LWP 6380)]
0x00002aaaab9d30c4 in waitpid () from /lib/libc.so.6
#0  0x00002aaaab9d30c4 in waitpid () from /lib/libc.so.6
#1  0x00002aaaab97d5ff in strtold_l () from /lib/libc.so.6
#2  0x0000000000490264 in smb_panic2 (
    why=0x4d0b48 "push_ascii - dest_len == -1", 
    decrement_pid_count=<value optimized out>) at lib/util.c:1545
#3  0x000000000047b44d in push_ascii (dest=0x7fffffca5800, 
    src=0x6802ec "BioCog NAS", dest_len=18446744073709551615, flags=5)
    at lib/charcnv.c:844
#4  0x0000000000430d7b in send_announcement (subrec=0x67da50, 
    announce_type=<value optimized out>, from_name=0x6801e8 "NOSTROMO", 
    to_name=0x67dc9c "BIOCOG", to_type=29, to_ip={s_addr = 4289729163}, 
    announce_interval=60, server_name=0x6801e8 "NOSTROMO", server_type=0, 
    server_comment=0x6802ec "BioCog NAS") at nmbd/nmbd_sendannounce.c:119
#5  0x0000000000430f8c in send_host_announcement (subrec=0x67da50, 
    work=0x67dc70, servrec=0x6801d0) at nmbd/nmbd_sendannounce.c:210
#6  0x00000000004312af in announce_my_server_names (t=1195203564)
    at nmbd/nmbd_sendannounce.c:257
#7  0x00000000004204b6 in main (argc=2, argv=0x0) at nmbd/nmbd.c:449
------------
nmbd.log states (almost identical on both machines):

[2007/11/16 10:06:20, 0] nmbd/nmbd.c:main(727)
  Netbios nameserver version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2007/11/16 10:06:21, 0] lib/util.c:smb_panic2(1544)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 6457]
[2007/11/16 10:06:21, 0] lib/util.c:smb_panic2(1552)
  smb_panic(): action returned status 0
[2007/11/16 10:06:21, 0] lib/util.c:smb_panic2(1554)
  PANIC: push_ascii - dest_len == -1
[2007/11/16 10:06:21, 0] lib/util.c:smb_panic2(1562)
  BACKTRACE: 8 stack frames:
   #0 /usr/sbin/nmbd(smb_panic2+0x66) [0x4901a6]
   #1 /usr/sbin/nmbd(push_ascii+0xed) [0x47b44d]
   #2 /usr/sbin/nmbd [0x430d7b]
   #3 /usr/sbin/nmbd [0x430f8c]
   #4 /usr/sbin/nmbd(announce_my_server_names+0xcf) [0x4312af]
   #5 /usr/sbin/nmbd(main+0x436) [0x4204b6]
   #6 /lib/libc.so.6(__libc_start_main+0xdb) [0x2aaaab95f49b]
   #7 /usr/sbin/nmbd [0x41ef4a]

---

### Post by bender3000 on 2007-11-16
> 
After updating samba to 3.0.22-1ubuntu3.4 nmbd segfaults on both of our dapper servers (1 x86 and 1 x86_64) on startup.


I had same problem.

Managed to downgrade to 3.3 ,wasn't easy though

Now I can Samba on worktime again:)

---

### Post by jtc on 2007-11-16
> **bender3000 said:**
> 
Managed to downgrade to 3.3 ,wasn't easy though

A quick howto, or perhaps a pointer in the right direction?

---

### Post by bender3000 on 2007-11-16
> 
A quick howto, or perhaps a pointer in the right direction?


Aptitude is your friend

Now if I could remember correctly what was the right path. I fumbled around at first a bit.
[LIST=1]
[*]Find samba package /samba
[*]Examine ie. press enter on it
[*]Scroll down to Versions
[*]Mark 3.4 to be deleted 
[*]examine e:
[*]From suggestions select downgrade, and press 'g' as go
[/LIST]

Procedure is Something like that

---

### Post by Rich99 on 2007-11-16
I have the exact same issue - updated to 3.0.22-1ubuntu3.4 & immediately got segfaults from nmbd.

I couldn't work out how to downgrade samba from synaptic without losing gnome-desktop package too, so I took the easy route & downloaded the 3.0.22-1ubuntu3.3 debs for my architecture from the ubuntu server (smbclient, libsmbclient, samba, samba-common from [ftp://ftp.ubuntu.com/ubuntu/pool/main/s/samba](ftp://ftp.ubuntu.com/ubuntu/pool/main/s/samba))

and then ran 
dpkg -i libsmbclient_3.0.22-1ubuntu3.3_i386.deb samba-common_3.0.22-1ubuntu3.3_i386.deb samba_3.0.22-1ubuntu3.3_i386.deb smbclient_3.0.22-1ubuntu3.3_i386.deb

to install them all.  After that samba works fine again.  Hopefully they'll fix this soon - has anyone filed a bug report so that they know of the issue?

---

### Post by raphha on 2007-11-16
Hello everybody,
same problem,, the downgrade solution with apt-get on the command line is:

1) VER=3.0.22-1ubuntu3.3 // Define the version we want to have installed

2) sudo apt-get -s install samba=$VER // Test run (option "-s")

3) Check the output of 2) and add all necessary packages to the command line

4) I used for example: sudo apt-get install samba=$VER samba-common=$VER smbfs=$VER smbclient=$VER

5) Check again the actions proposed by apt-get

6) If all is fine, go ahead, samba will be downgraded.

---

### Post by jtc on 2007-11-16
Bender, rich and raphha: Thanks for all the instructions

Now I only have to decide whatever I actually want to downgrade, compile my own samba from source or simply wait for Ubuntu to release a fix. Not much use of the computers labs I administer today, and if there is a fix by tomorrow, so...

---

### Post by bash.gordon on 2007-11-16
> **Rich99 said:**
>  Hopefully they'll fix this soon - has anyone filed a bug report so that they know of the issue?
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/163042](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/163042)
Best regards,
Andreas

---

### Post by jamesmanning on 2007-11-16
I can't downgrade, even after another apt-get update to make sure I'm in sync.

% grep security /etc/apt/sources.list
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted

% sudo apt-get -s install samba=3.0.22-1ubuntu3.3
Reading package lists... Done
Building dependency tree... Done
E: Version '3.0.22-1ubuntu3.3' for 'samba' was not found

When I check the contents of [http://security.ubuntu.com/ubuntu/pool/main/s/samba/](http://security.ubuntu.com/ubuntu/pool/main/s/samba/) I can see that the package is there, though.

However, when I check the contents of [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz) I see that only the 3.4 versions are listed, so I'm guessing that doing the apt-get update actually broke my downgrade scenario, since it updated to a packages file that only lists 3.4 - does this sound right, and if so, is there an easy downgrade?  

I don't necessarily mind downloading the files and downgrading manually, but it seems like this is a concern in the general case of needing to downgrade, so I'd like to learn what else is possible.

On a semi-related note, I couldn't install samba-dbg either (trying to get the symbols) due to 403 from the server:

% sudo apt-get install samba-dbg
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  samba-dbg
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 9811kB of archives.
After unpacking 25.2MB of additional disk space will be used.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main samba-dbg 3.0.22-1ubuntu3.4
  403 Forbidden
**Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-dbg_3.0.22-1ubuntu3.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-dbg_3.0.22-1ubuntu3.4_i386.deb)  403 Forbidden**
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by bash.gordon on 2007-11-16
@jamesmanning
> **jamesmanning said:**
> 
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main samba-dbg 3.0.22-1ubuntu3.4
  403 Forbidden
**Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-dbg_3.0.22-1ubuntu3.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-dbg_3.0.22-1ubuntu3.4_i386.deb)  403 Forbidden**
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
According to this message 
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/163042/comments/6](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/163042/comments/6)
the 3.4 binaries should be inaccessible by now. Maybe this also applies to samba-dbg?

Regards,
Andreas

---

### Post by netlogic on 2007-11-16
Oh man...
This doesn't look good for LTS Ubuntu. Had to fix few machines... Mistakes like this will make people go back to RHEL. Samba is super important package.

---

### Post by netlogic on 2007-11-16
i also had to reset all the passwords after the downgrade. i feel bad for people who had hundreds of users using samba passwords that don't sync with unix passwords.

---

### Post by jvxz on 2007-11-16
there unavailable now

and you cant upgrade to 7.10 without them:(

---

### Post by netlogic on 2007-11-16
Yea, this isn't good at all. Now, I am afraid to automate updates now. I am going to disable the automatic daily updates on the cron on all servers and manually check them in the VM before the deployment. Maybe, I will change it to once a week.

---

### Post by jvxz on 2007-11-16
hmm... im new-ish to ubuntu,

but it seems unlikely to me to happen agen now they know to test thing on more configs

---

### Post by questant on 2007-11-16
Comment from netlogic ## 11 and 14

This problem is apparently not related to Ubuntu per se but also to other distributions including RH and is a Samba issue regardless of platform.  You're right, it's not good.  But I suspect it will be addressed rather more quickly than it would if we were viewing the computer world's problems  from another vista.

See comment #8 at the following link:
[http://ubuntuforums.org/showthread.php?t=463944&highlight=samba+403](http://ubuntuforums.org/showthread.php?t=463944&highlight=samba+403)

So this is apparently biting all sorts of folks on the back side of the lap, regardless of distribution.

---

### Post by Roidhun on 2007-11-16
> **questant said:**
> Comment from netlogic ## 11 and 14
So this is apparently biting all sorts of folks on the back side of the lap, regardless of distribution.

I feel the pain too - right where the sun doesn't shine! :frown:

Is this the thread to monitor for a solution?

---

### Post by jamesmanning on 2007-11-16
> but it seems unlikely to me to happen agen now they know to test thing on more configs

Maybe I'm cynical, but that seems naive :)

> So this is apparently biting all sorts of folks on the back side of the lap, regardless of distribution.

That makes it even more frightening - it's not just bad engineering practices (lack of sufficient testing before security patch distribution) at one of the distributions, it's many of them.

---

### Post by mo1tomax on 2007-11-16
> **raphha said:**
> Hello everybody,
same problem,, the downgrade solution with apt-get on the command line is:

1) VER=3.0.22-1ubuntu3.3 // Define the version we want to have installed

2) sudo apt-get -s install samba=$VER // Test run (option "-s")

3) Check the output of 2) and add all necessary packages to the command line

4) I used for example: sudo apt-get install samba=$VER samba-common=$VER smbfs=$VER smbclient=$VER

5) Check again the actions proposed by apt-get

6) If all is fine, go ahead, samba will be downgraded.

Thank you, thank you, thank you...  3 hrs of sleep in 24 hours, interrupted by work, for this wonderful, 5 minute fix...

And now, all is good in my Dapper world.

---

### Post by jerrylamos on 2007-11-16
Received an upgrade notice on my Gutsy 7.10 CVE-2007-4572 which gets the following failure:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)

  403 Forbidden

From reading the preceding posts, I'm glad the installation failed.

Jerry Amos

---

### Post by ixfnak on 2007-11-18
The security updates I applied this morning (2007-11-18) Central European Time fixed the problem. nmbd is now working and with it NetBIOS name resolution from a Windows XP client.

---

### Post by MJN on 2007-11-19
> **netlogic said:**
> Yea, this isn't good at all. Now, I am afraid to automate updates now. I am going to disable the automatic daily updates on the cron on all servers and manually check them in the VM before the deployment. Maybe, I will change it to once a week.
 
You should never, ever, automate system upgrades on (important) servers for exactly the problem(s) discussed here - it's all too easy for one small mishap to fundamentally disrupt the server operation and if that server is part of a common pool with updates automated on all of them then your whole outfit becomes out of action in one fell swoop.
 
Mathew

---

### Post by netlogic on 2007-11-19
You are right, but I never had this problem on Debian. For the LTS, Ubuntu better understand they should slow down and make sure things work before they release. This is just purely a bad move by them. Apache, NFS, Samba, Ftp,SQL and other server related applications need special attention. They don't need to patch everything right away. Their goal should be everything should be running. It is LTS... It supposed to be outdated and stable version. Most admins don't manage one or two servers. If they have to test 1000s patches each distro patches, they would never go home and think they should have stuck with MS.

---

### Post by MJN on 2007-11-19
I hear what you're saying, however this incident has shown that things don't always work out quite as we might hope!
 
Maybe we should all be using cifs anyway and not smbfs now that it's been deprecated! ;)
 
Mathew

---

