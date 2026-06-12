---
title: "sudo does not read /etc/shadow"
date: 2016-03-21
forum: Server Platforms
---

### Post by daften on 2016-03-21
When i issue e.g. sudo ls it asks for my password, when I enter it, it notifies me to try again, as if my password is incorrect.
I have checked two items:
[LIST]
[*]Checked if my password is correct: by logging in over SSH with my password
[*]Checked if my sudo configuration is correct: by changing the sudo line that gives me sudo rights to give the rights passwordless
[/LIST]

The only conclusion I can draw is that sudo doesn't use /etc/shadow correctly, which is very strange. PAM is not enabled on my machine, so that can't be the reason.

How can I trace this problem further?

thanks in advance!

---

### Post by TheFu on 2016-03-21
Create a new userid and see if that behaves differently.
Also, look in the log files for anything related to the failures.  

PAM is always enabled - how else would any login or authentication happen? I don't understand that statement. Perhaps you meant to say that you haven't touched anything related to pam.d/?

If you are stuck (can't create new users because you can't sudo), then use any of the standard methods to login when you have physical access. Lots of guides for that - grub, use a liveCD, etc.

Oh - welcome to the forums.

---

### Post by nerdtron on 2016-03-21
What is your sudo configuration for that user?

---

### Post by daften on 2016-03-21
@nerdtron:
The user is in the group sysadmin (checked with groups; output daften sysadmin).
Sudo rights through /etc/sudoers.d/sysadmin with contents %sysadmin ALL=(ALL) ALL

@TheFu:
PAM is indeed untouched. The server is bootstrapped with chef and I have a second server that's setup exactly the same. The users are inserted with the users cookbook. And the /etc/shadow is the same (except for user id's) between the two servers.
I have now manually added a new user (test) with a password through useradd, added it to the sysadmin group, and the exact same behaviour occurs. Is there a way to debug how sudo works?

Thanks @both for the quick responses and thanks for the welcome message :)

---

### Post by bab1 on 2016-03-22
> **daften said:**
> @nerdtron:
The user is in the group sysadmin (checked with groups; output daften sysadmin).
Sudo rights through /etc/sudoers.d/sysadmin with contents %sysadmin ALL=(ALL) ALL

@TheFu:
PAM is indeed untouched. The server is bootstrapped with chef and I have a second server that's setup exactly the same. The users are inserted with the users cookbook. And the /etc/shadow is the same (except for user id's) between the two servers.
I have now manually added a new user (test) with a password through useradd, added it to the sysadmin group, and the exact same behaviour occurs. Is there a way to debug how sudo works?

Thanks @both for the quick responses and thanks for the welcome message :)
Why reinvent the wheel?  You can add the user to the sudo group and that user becomes a sudoer.  

Did you uncomment the include directive in /etc/sudo when using the /etc/sudoers.d/ directory?

---

### Post by daften on 2016-03-22
This is because this is done through standard chef cookbooks, which use this group.
And like I said in my first post, I checked sudo rights, and the problem is NOT there. If I change the sysadmin file to give sudo rights passwordless, I can issue sudo commands without problem.
The problem lies in sudo checking the password!!!

---

### Post by daften on 2016-03-22
Anybody that has any hints on what I can do to trace this further.
To re-iterate, I'm 100% sure the password is correct and the sudo rights are correct!

---

### Post by TheFu on 2016-03-22
I use ansible, not chef - but attended a 4 hr chef class - so I have an understanding.  Anyways, looked at the permissions for /etc/sudoers using ansible across all the hosts I manage;
```
-r--r----- 1 root root 840 Oct  4  2012 /etc/sudoers
```
That is what I'd check first.
And shadow:
```
-rw-r----- 1 root shadow 819 Apr 29  2013 /etc/shadow
``` These permissions are identical across all the ubuntu systems here too.

The manpage has some interesting error message descriptions - check the log files for those:
```
     unable to open/read /etc/sudoers
       The sudoers file could not be opened for reading.  This can happen when
       the sudoers file is located on a remote file system that maps user ID 0
       to a different value.  Normally, sudoers tries to open sudoers using
       group permissions to avoid this problem.  Consider either changing the
       ownership of /etc/sudoers or adding an argument like &#8220;sudoers_uid=N&#8221;
       (where &#8216;N&#8217; is the user ID that owns the sudoers file) to the end of the
       sudoers Plugin line in the sudo.conf(5) file.
```
and
```
     /etc/sudoers is owned by uid N, should be 0
       The sudoers file has the wrong owner.  If you wish to change the
       sudoers file owner, please add &#8220;sudoers_uid=N&#8221; (where &#8216;N&#8217; is the user
       ID that owns the sudoers file) to the sudoers Plugin line in the
       sudo.conf(5) file.

     /etc/sudoers is world writable
       The permissions on the sudoers file allow all users to write to it.
       The sudoers file must not be world-writable, the default file mode is
       0440 (readable by owner and group, writable by none).  The default mode
       may be changed via the &#8220;sudoers_mode&#8221; option to the sudoers Plugin line
       in the sudo.conf(5) file.

     /etc/sudoers is owned by gid N, should be 1
       The sudoers file has the wrong group ownership.  If you wish to change
       the sudoers file group ownership, please add &#8220;sudoers_gid=N&#8221; (where &#8216;N&#8217;
       is the group ID that owns the sudoers file) to the sudoers Plugin line
       in the sudo.conf(5) file.

```

So while we don't know if these are the issues - the surest way to be wrong is to claim you are not. ;)  Just sayin'.

I've done some nasty things (bad ideas, but required) with sudoers over the years. If you'll post the complete sudoers, maybe we'll see something you don't?

My systems don't have a sudo.conf - all defaults - but if yours does, that could radically alter the behavior too.  Automation is great, until we assume that everything which worked on a slightly different system will continue to work on a new one.  I've made this assumption and be schooled by Unix many times.

---

### Post by daften on 2016-03-22
Ok, thanks for the update, but to re-iterate.
I have changed ONE thing is one sudo file so sudo rights are given to the sysadmin group, but passwordless. And then sudo works. So sudo only fails when it needs to check the password. I have checked the log files before as well to check for errors, no errors.
The only relevant lines are:
> Mar 22 16:08:07 aegir1 sudo: pam_tally2(sudo:auth): /var/log/tallylog is either world writable or not a normal file
Mar 22 16:08:11 aegir1 sudo: pam_tally2(sudo:auth): /var/log/tallylog is either world writable or not a normal file
Mar 22 16:08:11 aegir1 sudo: pam_unix(sudo:auth): conversation failed
Mar 22 16:08:11 aegir1 sudo: pam_unix(sudo:auth): auth could not identify password for [daften]
Mar 22 16:08:11 aegir1 sudo:   daften : 1 incorrect password attempt ; TTY=pts/2 ; PWD=/home/daften ; USER=root ; COMMAND=/bin/ls

Does this help in tracing it?

---

### Post by TheFu on 2016-03-22
I'm reaching ... used **visudo** for edits to the sudoers - or used a chef recipe?

All users are local, not LDAP?

DevOps tools have a way of changing files we didn't intend. I've asked for a few to check trying to help.  Please help us to help you and answer those. 

```
$ more /etc/pam.d/sudo 
#%PAM-1.0

auth       required   pam_env.so readenv=1 user_readenv=0
auth       required   pam_env.so readenv=1 envfile=/etc/default/locale user_read
env=0
@include common-auth
@include common-account
@include common-session-noninteractive

```
Does that look like yours?

---

### Post by daften on 2016-03-23
I understand, but I'm certain the sudo configuration in itself is correct. 2 sets of servers have been bootstrapped at the same time with the same config, and only one has the problem.

The PAM file looks like this:
```
chef@aegir1:~$ more /etc/pam.d/sudo
#%PAM-1.0

auth       required   pam_env.so readenv=1 user_readenv=0
auth       required   pam_env.so readenv=1 envfile=/etc/default/locale user_readenv=0
@include common-auth
@include common-account
@include common-session-noninteractive
```

The only difference is env=0 in your file, but I don't know pam enough to know the implication of that line.

All users are indeed local.
All configuration files are always put in place by chef.

For completeness:
/etc/sudoers
```

#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        mail_badpass
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

```

And /etc/sudoers.d/sysadmin
```

# This file is managed by Chef.
# Do NOT modify this file directly.

%sysadmin ALL=(ALL) ALL

```

Thanks all for the help, anything that could help me figure this out is greatly appreciated. It seems hard since sudo doesn't have a debug mode (as far as i know).

---

### Post by bab1 on 2016-03-23
> **daften said:**
> I understand, but I'm certain the sudo configuration in itself is correct. 2 sets of servers have been bootstrapped at the same time with the same config, and only one has the problem.
...

All users are indeed local.
All configuration files are always put in place by chef.

For completeness:
/etc/sudoers
```

#
# This file MUST be edited with the 'visudo' command as root.
#
[I]# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
[COLOR="#FF0000"]# See the man page for details on how to write a sudoers file.[/COLOR]
#[/I]
...

[B]# See sudoers(5) for more information on "#include" directives:
[/B]
[COLOR="#660077"]***[SIZE=3]#includedir /etc/sudoers.d[/SIZE]***[/COLOR]

```

And /etc/sudoers.d/sysadmin
```

# This file is managed by Chef.
# Do NOT modify this file directly.

%sysadmin ALL=(ALL) ALL

```

From the README file in the /etc/sudoers.d/ directory
```

#       [COLOR="#660077"]**[SIZE=3]#includedir /etc/sudoers.d[/SIZE]**
[/COLOR]#
# This will _cause sudo to read and parse any files in the /etc/sudoers.d_
# directory that do not end in '~' or contain a '.' character.

```
I don't think it matters whether sudo is configured by hand or using Chef.   

As I said before > Did you uncomment _the include directive in /etc/sudo when using the /etc/sudoers.d/ directory_? 
I don't see how your  /etc/sudoers.d/sysadmin file is parsed by sudo  if the include statement is commented out.

---

### Post by daften on 2016-03-24
Please look at the manual in detail. The line there is also "commented". It is btw a directive, not a comment, see e.g. [https://fedorahosted.org/augeas/ticket/188](https://fedorahosted.org/augeas/ticket/188)
Try the configuration out, just change the sysadmin file so it gives the sudo rights passwordless. (%sysadmin     ALL=(ALL) NOPASSWD:ALL), it works!

I feel like a broken record, but the sudo configuration itself (/etc/sudoers and /etc/sudoers.d/...) is NOT the problem!

---

### Post by TheFu on 2016-03-24
No difference using user_readenv. From the manpage:
```
       user_readenv=0|1
           Turns on or off the reading of the user specific environment file.
           0 is off, 1 is on. By default this option is off.
```

#include and #includedir are normal directives for sudoers - check the manpage (around line 665).  Guess the creators come from C/C++ and liked those macros?  The manpages around sudoers are extensive.
```
   Other special characters and reserved words
     The pound sign (‘#’) is used to indicate a comment (unless it is part of
     a #include directive or unless it occurs in the context of a user name
     and is followed by one or more digits, in which case it is treated as a
     uid).  Both the comment character and any text after it, up to the end of
     the line, are ignored.

```

So, I'm convinced that everything is as you say. Thanks for posting the files.

I have seen issues entering passwords when the LANG character-set was changed from when the password was created, but that never happened on a console, just for GUI programs that were confused.  

Also, there was a bug in Arch where the underlying system dependencies weren't correct and sudo needed a newer version of some support libraries for passwords to work correctly. apt-get update/upgrade current?

Still reaching here.

---

### Post by daften on 2016-03-24
It seems I have fixed the problem.

This section in /var/log/auth.log
```
Mar 24 16:07:38 aegir1 sudo: pam_tally2(sudo:auth): /var/log/tallylog is either world writable or not a normal file
Mar 24 16:07:39 aegir1 sudo: pam_unix(sudo:auth): authentication failure; logname=daften uid=1007 euid=0 tty=/dev/pts/2 ruser=daften rhost=  user=daften
Mar 24 16:07:41 aegir1 sudo: pam_tally2(sudo:auth): /var/log/tallylog is either world writable or not a normal file
Mar 24 16:07:53 aegir1 sudo: pam_unix(sudo:auth): conversation failed
Mar 24 16:07:53 aegir1 sudo: pam_unix(sudo:auth): auth could not identify password for [daften]
Mar 24 16:07:53 aegir1 sudo:   daften : 1 incorrect password attempt ; TTY=pts/2 ; PWD=/home/daften ; USER=root ; COMMAND=/bin/ls
```

Seemed worrysome.

After checking /var/log/tallylog and comparing to the other server, it was indeed world writeable and the group was not correct. After deleting it, sudo worked again.

How this came to be must indeed be because of the cookbooks. In hindsight, the solution was simple it seems :s

THanks all for the help and I hope nobody will ever need this thread to fix this problem :)

Can I mark this as answered somehow?

---

### Post by TheFu on 2016-03-24
sudo and ssh are really picky about file permissions.  Lesson to be learned.  That was why we were to keen on file permissions. I learned that the hard way decades ago.

Didn't/don't know what tallylog is, so I assumed it was unrelated and didn't look at anything more. There is no substitute for local knowledge.

Mark the thread solved using the thread tools near the top.

---

### Post by daften on 2016-11-07
Some more information, the only entry in /var/log/tallylog when one of my colleagues couldn't sudo, was this:
> 
/dev/pts/0
         >X/dev/pts/2]


What could have caused this entry? :s

---

