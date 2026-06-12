---
title: "Lock user account after false authentications ..."
date: 2015-09-18
forum: Server Platforms
---

### Post by fakedave on 2015-09-18
Hello,

I am almost new to Ubuntu (and more generally linux) so I already apologize if I'm slow to understand ...
I've been owning some Synology servers (NAS) for years but I have to setup a new server because a customer of mine is requiring some security policy I did not know how to match with my NAS.
One of them is to lock a user account if more than x failing authentication account.
So I setup a Ubuntu server 14.04 LTS machine. This server will be only for hosting network directories and svn (over ssh) repositories.
Therefore I'd like to be able to apply that rule over ssh and samba. It does not have to apply to my tty keyboard because physical access is secured.

I'm looking for the last 48h at fail2ban but I understood earlier that it does not apply to that usage.
Then pam_tally2. I'm struggling to understand what all the files in /etc/pam.d are doing.
I have the feeling that it's the right place but I can't find any tutorial applied to Ubuntu, I can't find any explanation about which file does what, etc.
Basically ... I'm lost but eager to understand!!

Can anybody help me or point me in a good direction?

Thanx a lot in advance and be prepared to see me around a bit :-)

BR

---

### Post by TheFu on 2015-09-18
Fail2ban can be setup to watch log files for failures, then take action - usually a firewall rule - based on those failures.  That means you can use it for ssh and samba failures.  I've never done this, but suspect you could lock an account too - don't think that would matter to either samba or ssh with key-based authentication, however.

I haven't screwed with PAM in years.  TLDP and debian admin guides is where I'd start.
[http://tldp.org/HOWTO/User-Authentication-HOWTO/](http://tldp.org/HOWTO/User-Authentication-HOWTO/)
[https://www.debian.org/doc/manuals/debian-reference/ch04.en.html](https://www.debian.org/doc/manuals/debian-reference/ch04.en.html)

Was the 2nd answer here [https://unix.stackexchange.com/questions/78182/how-to-lock-users-after-5-unsuccessful-login-tries](https://unix.stackexchange.com/questions/78182/how-to-lock-users-after-5-unsuccessful-login-tries) not clear?

---

### Post by fakedave on 2015-09-18
> **TheFu said:**
> Was the 2nd answer here [https://unix.stackexchange.com/questions/78182/how-to-lock-users-after-5-unsuccessful-login-tries](https://unix.stackexchange.com/questions/78182/how-to-lock-users-after-5-unsuccessful-login-tries) not clear?
I found this one. One of my multiple issues on the topic is the naming of the files. In Ubuntu you have common-xxx, in other distributions you have xxx-auth and so on. I never find any proper explanations for Ubuntu. So I'd appreciate to understand what the following files do:
```
-rw-r--r--   1 root root  179 May 13 20:59 accountsservice
-rw-r--r--   1 root root  384 Feb 17  2014 chfn
-rw-r--r--   1 root root   92 Feb 17  2014 chpasswd
-rw-r--r--   1 root root  581 Feb 17  2014 chsh
-rw-r--r--   1 root root 1208 Sep 17 00:03 common-account
-rw-r--r--   1 root root 1306 Sep 18 15:54 common-auth
-rw-r--r--   1 root root 1696 Sep 18 15:43 common-password
-rw-r--r--   1 root root 1489 Sep 17 22:26 common-password.bak
-rw-r--r--   1 root root 1470 Sep 17 00:03 common-session
-rw-r--r--   1 root root 1435 Sep 17 00:03 common-session-noninteractive
-rw-r--r--   1 root root  527 Feb  9  2013 cron
-rw-r--r--   1 root root   81 Mar  7  2014 dovecot
-rw-r--r--   1 root root 4788 Feb 17  2014 login
-rw-r--r--   1 root root   92 Feb 17  2014 newusers
-rw-r--r--   1 root root  520 Jan 31  2014 other
-rw-r--r--   1 root root   92 Feb 17  2014 passwd
-rw-r--r--   1 root root  255 Mar  4  2015 polkit-1
-rw-r--r--   1 root root   84 Apr  1  2014 samba
-rw-r--r--   1 root root 2139 May  2  2014 sshd
-rw-r--r--   1 root root 2305 Feb 17  2014 su
-rw-r--r--   1 root root  239 Feb 10  2014 sudo
```

I will look into your other links for answers.

I'd definitely like to understand what I'm doing here so I can reproduce it later and eventually, that's been one of my wish for some time now, move my work and personal machines to Linux.
I cannot really afford to go back in possibilities, at least for work. It's another story.

I keep welcoming suggestions until I have properly setup my server and know what is going on.

Thanx for your input.

---

### Post by fakedave on 2015-09-18
Well, I have an issue now and I don't know how that happened --> I cannot log into my samba shares, my authentication is denied (another share with guest ok is still fine).
I'm looking at the samba logs and I don't see much.
Anybody has an idea about what could have happened? (shoot me)

---

### Post by Vegan on 2015-09-18
if you can log into the server you can take a look at your config files and see if they have been damaged

---

### Post by fakedave on 2015-09-19
> **Vegan said:**
> if you can log into the server you can take a look at your config files and see if they have been damaged
Well, I did that but I have seen nothing.
I spent some time trying to revert some changes but I did not find.
Basically, I've been playing with setting up samba shares & user authentication and I don't know at what point the samba authentication stopped working for my user.
No clue.

At this point I have 2 choices:
[LIST]
[*]either find a log that tells me what's happening but I haven't found anything either
[*]reinstall the whole server before it's operational but I hate to have to do that because I would actually need to be able to maintain the server in the long run.
[/LIST]

So at this point, any help is much appreciated ](*,)

I guess I should at least learn some stuff from that --> need to backup config files before any update and check the whole functionalities after every update. My fault.

---

### Post by TheFu on 2015-09-19
> **fakedave said:**
> Well, I have an issue now and I don't know how that happened --> I cannot log into my samba shares, my authentication is denied (another share with guest ok is still fine).
I'm looking at the samba logs and I don't see much.
Anybody has an idea about what could have happened? (shoot me)

1) What files have been changed?  Use "find" to find all the files that changed in the last day. Anything familiar?
2) Whenever asking for help, please post the config files involved and any relevant parts of the log files. Look for warning and error in the logs.  For all text postings, please, please, please use "code tags" so things line up.
3) Modifying a config file usually doesn't make it reused.  To force that to be reloaded most people just restart the service. Did you do that with samba or anything else after modifying those files?

Hard to help without **any** facts.  ssh in and gather some facts.

If you touch a server, then you need to plan to maintain it.  First thing to learn is how to do daily, automatic, backups AND to test those through a restore to different hardware. A backup without a full restore test is just like crossing your fingers. You *hope* it will work, but don't really know it *will* work. There are many threads here on how to learn Linux and on how to backup Linux systems. Time to learn.

Also - make sure you patch the systems every few weeks.  I'm up doing that now for my systems. That's was early Saturday morning is about here.  Usually it is 20 min to patch 20 systems. I use ansible as my devops tool.

---

### Post by fakedave on 2015-09-19
Hi TheFu,

thanx for looking at that. I agree with you, you don't have much information to work with. At the moment this is a bit because I don't really know how to get any.
However, I did some research and here's what I come up with:
File updated under /etc in the last 2 days: unfortunately I have a lot because I'm setting up the server
```
./shadow./bash_completion.d
./init.d
./shadow-
./rc6.d
./rc6.d/K99fail2ban
./subgid
./rc4.d
./rc4.d/S99fail2ban
./mtab
./gshadow-
./gshadow
./ld.so.cache
./passwd
./rc0.d
./rc0.d/K99fail2ban
./subuid
./rc2.d
./rc2.d/S99fail2ban
./rc5.d
./rc5.d/S99fail2ban
./login.defs
./logrotate.d
./pam.d
./pam.d/common-password
./pam.d/other
./pam.d/common-auth
./pam.d/samba
./pam.d/other.bak
./pam.d/common-password.bak
./rc3.d
./rc3.d/S99fail2ban
./samba
./samba/dhcp.conf
./samba/smb.conf
./fail2ban
./fail2ban/jail.conf.backup
./fail2ban/jail.conf
./fail2ban/action.d
./fail2ban/jail.local
./fail2ban/filter.d
./subversion
./rc1.d
./rc1.d/K99fail2ban
./passwd-
./group-
./security
./security/opasswd
./security/limits.conf
./default
./group

```

I looked at logs:
This is a log content of /var/log/samba/xxx, last file updated after failed login to a samba share.
```
cat log.workstation 


[2015/09/19 19:43:24.957943,  0] ../source3/param/loadparm.c:4094(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/ owned by uid 0 is not a regular file
[2015/09/19 19:55:35.918027,  0] ../source3/param/loadparm.c:4094(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/ owned by uid 0 is not a regular file
[2015/09/19 20:01:23.008269,  0] ../source3/param/loadparm.c:4094(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/ owned by uid 0 is not a regular file
  
```

Then I found the following: *testparm -s*
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Dropbox]"
Processing section "[Mellonne]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    logon drive = M:
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[Dropbox]
    comment = Dropbox share access
    path = /volume1/samba/dropbox
    force user = nobody
    force group = nogroup
    read only = No
    guest ok = Yes


[Mellonne]
    comment = Mellonne share access
    path = /volume1/samba/mellonne
    force user = nico,test
    read only = No



```

I also created a new user --> test. Attributed him a passwd and a [FONT=Arial][COLOR=#333333]smbpasswd (the same), added him to the smb.con and checked. I restarted the service in the mean time --> [/COLOR][/FONT]*sudo service smbd restart*[FONT=Arial][COLOR=#333333]
Same result, cannot login. The share with guest ok is working fine but not the one requiring a authentication.
Here's the directory configuration for the shares:
[/COLOR][/FONT]```
drwxr-xr-x 4 root   root       4096 Sep 17 09:04 ./
drwxr-xr-x 4 root   root       4096 Sep 17 09:02 ../
drwxr-xr-x 2 nobody nogroup    4096 Sep 17 11:25 dropbox/
drwxr-xr-x 2 root   sambausers 4096 Sep 18 17:15 mellonne/

```[COLOR=#333333][FONT=Arial]
and both users belong to the group [/FONT][/COLOR][FONT=Arial][COLOR=#333333]sambausers.

Does it help a bit more?
If not, what else?

Next step for me is, like you said, to setup a good daily backup if the full server. What tool do you use for that?

Thanx in advance![/COLOR][/FONT]

---

### Post by TheFu on 2015-09-20
You are using options that I've never touched.
"force user" - seems to say nico, but the file permissions only allow root to write into mellonne/. Could that be an issue?

Never used "logon drive" either. Seems like that would be tied to [Homes] and that section isn't in the conf file.

Have you tried turning up the logging level to see more details?

For backups, I use rdiff-backup. Search these forums. Lots of people use it, but we aren't the "backup every bit" group.  We backup the stuff we need to recreate an install like it was last night, not to 1-click restore all the bits from last night.  I can do a fresh install and restore our email in about 45 min from the backups, while still saving about 4G of backup files that we do NOT backup - the OS and libraries.  These are not image-based backups - there isn't a good way to do those on a running box.

---

### Post by fakedave on 2015-09-20
Excellent, thank again.
I tried to remove options that you never touched --> I updated & restarted server & tested one after another and the answer is "force user".
Although my login name is 'nico', it does not work. I saw it in another tutorial (or somewhere) but it does not seem to work for me. No big deal in my case.

So I'm back to where I was --> how to lock an account after x unsuccessful authentication over ssh or samba?

> [COLOR=#000000]I haven't screwed with PAM in years. TLDP and debian admin guides is where I'd start.
[http://tldp.org/HOWTO/User-Authentication-HOWTO/](http://tldp.org/HOWTO/User-Authentication-HOWTO/)
[https://www.debian.org/doc/manuals/d...e/ch04.en.html]("https://www.debian.org/doc/manuals/debian-reference/ch04.en.html")

Was the 2nd answer here [https://unix.stackexchange.com/quest...ul-login-tries]("https://unix.stackexchange.com/questions/78182/how-to-lock-users-after-5-unsuccessful-login-tries") not clear?
[/COLOR]

I'm sorry but those links do not help me. I read all of them and I'm lost between 'auth' 'password', 'session' ... i do not understand what is doing what. I'm lost.

Each time I try to implement a limit, it cannot lock the user.
Could anybody point me in a new direction? Or tell me how to use fail2ban for achieving this lock as I don't find any tutorial?

Thanx!!

---

### Post by fakedave on 2015-09-25
Well, I'm lost.
I've read all the mans, many sites, tutorials and I thought I actually understood the stuff.
I thought I was gonna try some pam updates on my samba connection.
So my /etc/pam.d/samba looks like that:
```
auth required pam_tally2.so deny=3 magic_root unlock_time=3600
@include common-auth
@include common-account
@include common-session-noninteractive
```

My expectation was that my test user was going to be locked after 3 failing login into my samba share ...
Well, it did not work so I'm unsure that my update worked

So I put this into the /etc/pam.d/samba file
```
auth required pam_deny.so
@include common-auth
@include common-account
@include common-session-noninteractive
```

and I was expecting not to be able to login into the samba share at all ...
Well, it did not work either!!!

I checked, there is no pam.d service to restart, it's dynamic so I'm missing something big but I don't have a clue why.

Pleaaassssssseeeeeeee heeeelllllllpppppppppp !!

:-(

---

### Post by fakedave on 2015-09-28
I've continued my reasearch.

So I added to common-auth
```
auth required pal_tally2.so [COLOR=#000000][FONT=Ubuntu Mono]deny=3 magic_root unlock_time=3600[/FONT][/COLOR]
```
and added to common-account
```
account required pam_tally2.so
```

If I add those lines at the beginning of the files then I can see the ssh login failures when I perform a pam_tally2 command. But no account locking happens.
If I move them to the end of the files then I do not see any failure anymore, like it's not happening.

I'm desperate to understand how pam files actually work. There's a logic I don't understand and I have not found any information about that yet.
It's always natural in the blogs or forums but it's not to me yet.

Can anybody enlighten me on this please?

Thanx

---

### Post by Bembot on 2015-10-27
common-auth file should read at the top:
[FONT=courier new][I][B]auth required pal_tally2.so onerr=fail [COLOR=#000000]deny=3 magic_root unlock_time=3600

[/COLOR][/B][/I][COLOR=#000000]common-account file should read at the top:
***account required pam_tally2.so onerr=fail deny=3 magic_root unlock_time=3600***
[/COLOR]**[COLOR=#000000][/COLOR]**[COLOR=#000000][/COLOR][COLOR=#000000][/COLOR][/FONT]

---

