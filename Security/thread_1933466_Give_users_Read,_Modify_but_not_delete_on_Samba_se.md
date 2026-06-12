---
title: "Give users Read, Modify but not delete on Samba server"
date: 2012-02-29
forum: Security
---

### Post by Karim_992 on 2012-02-29
guys i need your help and i really appreciate it. 

i am a windows system administrator and lately my manager want me to change the system to Unix.

i still studding and reading, what i really need is exactly this case i  need to configure my Samba server permissions to allow read,write but  not delete for a group or user. 

[[ i am configuring a file server ]] 
i need this option for groups so users can access the departments files  and modify them and get the data they need but not to delete this files 

The scenario i am trying to build is 
client X [read,modify but not delete files or subfolders]
Group X [read,modify but not delete files or sub folder]
root[read,modify and delete] i think this is the normal case for the root

---

### Post by emiller12345 on 2012-02-29
I think 'modify' and 'delete' may fall under the same permissions. If someone can modify a file, then they can modify the contents of a file to nothing.

---

### Post by CharlesA on 2012-02-29
> **emiller12345 said:**
> I think 'modify' and 'delete' may fall under the same permissions. If someone can modify a file, then they can modify the contents of a file to nothing.
I think that's how it works too.

---

### Post by bab1 on 2012-02-29
> **CharlesA said:**
> I think that's how it works too.

Nah!  A file is deleted only when it is unlinked from the inode that describes it.  A 0 byte file is empty but not deleted (unlinked).  If you set the chattr +i attribute no user *including root* have the ability to unlink the file.  Root would have to reset the chattr to -i to be able to unlink.

In addition, the sticky bit on a file should work stop file deletion too.

---

### Post by emiller12345 on 2012-02-29
*nix also has three main types of permissions: read, write and executable.
For the *nix permissions it appears that if the writable bit is not set for a directory for a given user ( or group ) then a file in that directory can't be deleted, but can be edited if the writable bit is set for the file.
However, new files cannot be created in the directory with the writable bit not set.

For Samba I'm not sure, Samba has three main permission settings: read only, writeable, and guest ok.
You might have to play around with those to figure that out.

---

### Post by bab1 on 2012-03-01
> **emiller12345 said:**
> *nix also has three main types of permissions: read, write and executable.
For the *nix permissions it appears that if the writable bit is not set for a directory for a given user ( or group ) then a file in that directory can't be deleted, but can be edited if the writable bit is set for the file.
However, new files cannot be created in the directory with the writable bit not set.

For Samba I'm not sure, Samba has three main permission settings: read only, writeable, and guest ok.
You might have to play around with those to figure that out.

Linux permissions trump Samba settings.  There are actually 4 bits used for permissions the 3 main bits (rwx) plus an  extended bit for suid and sgid and the sticky bit.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for more  info.  That page is pretty good reference on Linux permissions.

---

### Post by CharlesA on 2012-03-01
> **bab1 said:**
> Nah!  A file is deleted only when it is unlinked from the inode that describes it.  A 0 byte file is empty but not deleted (unlinked).  If you set the chattr +i attribute no user *including root* have the ability to unlink the file.  Root would have to reset the chattr to -i to be able to unlink.

In addition, the sticky bit on a file should work stop file deletion too.
Good point. Doesn't the sticky bit only prevent deletion from anyone except the owner?

---

### Post by bab1 on 2012-03-01
```

```> **CharlesA said:**
> Good point. Doesn't the sticky bit only prevent deletion from anyone except the owner?

In the post above (#6) I have a link to a page that describes what sui, sgid and sticky bits.

From the chmod man page```
RESTRICTED DELETION FLAG OR STICKY BIT
       The  restricted  deletion  flag  or  sticky  bit is a single bit, whose
       interpretation depends on the file type.  For directories, it  prevents
       unprivileged  users  from  removing or renaming a file in the directory
       unless they  own  the  file  or  the  directory;  this  is  called  the
       restricted  deletion  flag  for the directory, and is commonly found on
       world-writable directories like /tmp.
```

At the present time the sticky bit is not used for files.  In the past it held files in RAM, hence the sticky in "sticky bit".  :-)

Edit:  To cap this all off -- If you create a file structure that has these 3 things: a. A directory with the sticky bit set on.  b. The group forced (sgid)to one that is NOT a group with the samba users in it (i.e webadmin) and c. The file permissions set read and write to the file, those users will be able to read and write to that file, but not delete the file.

The directory should be set to 3775 and the files to 0664.  If you want to set this recursively you need to use chmod with symbolic bits, like this```
sudo chmod -R u=rwX,g=rwX,o=r,a=t $somedir
```

Hint: the large X set eXecute only on the directories.

---

### Post by CharlesA on 2012-03-01
Thanks for clearing that up. Quite handy. :)

---

### Post by emiller12345 on 2012-03-02
> **bab1 said:**
> The directory should be set to 3775 and the files to 0664.

In addition, you will probably want to set the umask 113 for files new files create so they will have permissions 0664. I think there should be a way to do that in samba, which is probably how most new files will mainly be created.

EDIT:
Disregard the above umask of 113, it is work.  smb.conf has entries for 'create mask' and 'directory mask' but I'm not sure how you'd set the octals for them.

---

### Post by bab1 on 2012-03-02
> **emiller12345 said:**
> In addition, you will probably want to set the umask 113 for files new files create so they will have permissions 0664. I think there should be a way to do that in samba, which is probably how most new files will mainly be created.
A umask of 113 will provide you with files with the following permissions u=rx,g=rx,o=wx.  Why would you want read and exexute on Users and groups and write plus execute on others is beyond me.  Maybe you miscalculated?

The kernel has a default of 666 for all file creation. This is rw for all.  The umask alters this, so a umask of 022 provides 644 and a umask of 002 provides 664.  If we apply your umask we have 666 - 113 which provides 553.

I set my umask to 002 on all hosts that provide file sharing (664) and 022 for hosts that are used by individuals.  This is be set globally at /etc/profile.  

Samba provides a series of mask definitions that are set in the share definition.

I am curious how you got to a umask of 113.  Can you explain?

---

### Post by emiller12345 on 2012-03-02
> **bab1 said:**
> I am curious how you got to a umask of 113.  Can you explain?
Ah, yes, I'm wrong. For some reason I was thinking 022 was the mask for files with the executable bit set and that they needed to be changed by one to remove the executable bit. And I messed up the order.
But aside from my mistakes, it will be important to have the correct masks in your smb.conf

---

### Post by bab1 on 2012-03-02
> **emiller12345 said:**
> 
... smb.conf has entries for 'create mask' and 'directory mask' but I'm not sure how you'd set the octals for them.

This is what I put in my share definitions```

create mask = 0664
directory mask = 3775
```

The first line is for file creation The leading 0 is where you define extended bits and we don't need them on the file creation.

The second line is for directory configuration and I am using the extended bits 1=sticky bit and 2=sgid bit: total=3
 
The default directory settings in the kernel is 777 and a umask (in /etc/profile) setting of 002 provides 775 (7-2=5). 

Note Samba defines this differently in the smb.conf but the results are the same.

---

### Post by Dangertux on 2012-03-02
Slightly different method than the one already provided but samba 4  provides cifs support. Thus allowing modify without delete windows style. jist another alternatove for you.

---

### Post by bab1 on 2012-03-02
> **Dangertux said:**
> Slightly different method than the one already provided but samba 4  provides cifs support. Thus allowing modify without delete windows style. jist another alternatove for you.

Samba3 has CIFS support too.  what does "*modify without delete windows style *mean?

Up front I will say; I don't use Samba 4 and have no familiarity with it other that what I have read.  I'm just curious as to what you are referring to.  I'm hoping this is a learning experience.  I follow your security posts -- very informative.

---

### Post by Dangertux on 2012-03-02
> **bab1 said:**
> Samba3 has CIFS support too.  what does "*modify without delete windows style *mean?

Up front I will say; I don't use Samba 4 and have no familiarity with it other that what I have read.  I'm just curious as to what you are referring to.  I'm hoping this is a learning experience.  I follow your security posts -- very informative.

Thanks I appreciate the compliment. I am not a very avid user of samba. However in  Windows permissions there is a "modify" option that works alot like the permission schema that was being discussed earlier. Incidentally it's a check box type thing. I believe (if I'm understanding correctly.) That this is what the OP is looking for. Incidentally upon doing further research Samba 3.25 + also supports this functionality. Basically there is advanced functionality more like the Windows' permission scheme of modify as well as the ability to prevent linking etc, essentially the way I understand it, it is an "override" if you will of default POSIX permissions. The catch being I would assume the POSIX permissions set in place would have to be "greater than or equal to" the specialized permissions granted by Samba.

Or I could just be making this up, I've never tried it and as I've stated, I'm by no means a Samba expert. This was actually an idea relayed from a coworker who I presented with the OP's question while I was browsing this forum. So without additional research I couldn't answer it more in depth at this time.

In doing further research (a quick google search), though -- it appears that my coworker may have been misinformed, there appears there is not a way to do this without setting sticky bit and setgid. Which would make sense.

Too bad, that would have been cool

---

### Post by bab1 on 2012-03-02
> **Dangertux said:**
> Thanks I appreciate the compliment. 
I am not a very avid user of samba. However in  Windows permissions there is a "modify" option that works alot like the permission schema that was being discussed earlier. 
Samba never trumps the OS file system, so it must invoke what we have been talking about.> 
Incidentally it's a check box type thing. I believe (if I'm understanding correctly.) That this is what the OP is looking for.
It may look like Windows, but we know its not.  ;-)> 
Incidentally upon doing further research Samba 3.25 + also supports this functionality. Basically there is advanced functionality more like the Windows' permission scheme of modify as well as the ability to prevent linking etc, essentially the way I understand it, it is an "override" if you will of default POSIX permissions. The catch being I would assume the POSIX permissions set in place would have to be "greater than or equal to" the specialized permissions granted by Samba.

Or I could just be making this up, 
Been there done that.  A painful condition. ;-)> 
I've never tried it and as I've stated, I'm by no means a Samba expert. This was actually an idea relayed from a coworker who I presented with the OP's question while I was browsing this forum. So without additional research I couldn't answer it more in depth at this time.

In doing further research (a quick google search), though -- it appears that my coworker may have been misinformed, there appears there is not a way to do this without setting sticky bit and setgid. Which would make sense.

Too bad, that would have been cool
But of course!.  CIFS allows Linux to talk to windows hosts, not directly to Linux hosts.  IF connect Linux to Linux and use Samba (I do) then the flow is posix<>CIFS<>--network--<>CIFS<>posix.

I assume your co-worker is a Jr. Admin or worse yet, a power user;  Hahaha.

---

### Post by Dangertux on 2012-03-02
He's an admin, and he's pretty smart, I don't think he has much experience with Samba though, not like I have any room to talk. 

My experience with it involves making it do things it shouldn't lol. 

Though I've been looking into this more now that I've actually had some time to think about it, and to OP I think that your best bet is the solution that has been presented thus far. Sadly -- this is one of the areas it would seem the default nix permissions set is lacking at least in terms of intuitive usage.

bab1 thanks for the clarification, cifs can be a confusing beast when you get down to the nitty gritty of it , it would seem.

---

### Post by matt_symes on 2012-03-02
Hi

Excellent explanation bab1.

As for umask though..

> This is be set globally at /etc/profile. 

I was under the impression this was now handled by pam_umask in Ubuntu; i may be wrong though.

As for samba, i will be setting up my own samba server over the weekend so kudos to all of you who posted. It will help me out as well :)

Kind regards

---

### Post by bab1 on 2012-03-02
> **matt_symes said:**
> Hi

Excellent explanation bab1.

As for umask though..



I was under the impression this was now handled by pam_umask in Ubuntu; i may be wrong though.

As for samba, i will be setting up my own samba server over the weekend so kudos to all of you who posted. It will help me out as well :)

Kind regards

I just set up another Samba server (10.04.3).  I set the umask in /etc/profile.  It was 022 (the ubuntu default).  When I set it to 002 all the files created are now rw-rw-r--

... In looking at the man pages the first thing that jumps out at me is```
PAM_UMASK(8)                   Linux-PAM Manual                   PAM_UMASK(8)

NAME
       pam_umask - PAM module to set the file mode creation mask

SYNOPSIS
       pam_umask.so [debug] [silent] [usergroups] [umask=mask]

DESCRIPTION
 The PAM module tries to get the umask value from the following places
       in the following order:

       ·   **[COLOR="Red"]umask= argument[/COLOR]**

       ·   umask= entry of the users GECOS field

       ...

```

The umask argument here (in red) is, I believe, set via /etc/profile.

My umask argument is```
$ umask
0002

```
This is not the default, but as I set it in /etc/profile.

---

### Post by matt_symes on 2012-03-02
Hi

```
pam_umask.so [debug] [silent] [usergroups] [COLOR="Red"][umask=mask][/COLOR]

·   [COLOR="Red"]umask= argument[/COLOR]
·   [COLOR="Green"]UMASK entry from /etc/login.defs[/COLOR]

```

I see. I was under the impression that the umask you highlighted in red was the parameter passed to pam_umask.so that i have highlighted above. I thought it fell through to the option i have highlighted in green.

Working through the configuration files... 

```
matthew@matthew-Aspire-7540:~$ grep -i umask /etc/skel/.profile 
# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022
matthew@matthew-Aspire-7540:~$ 
```

```
matthew@matthew-Aspire-7540:~$ grep -i umask /etc/profile
# The default umask is now handled by pam_umask.
# See pam_umask(8) and /etc/login.defs.
matthew@matthew-Aspire-7540:~
```

```
DESCRIPTION
       pam_umask is a PAM module to set the file mode creation mask of the current environment. The umask affects the default permissions assigned to newly created
       files.

       The PAM module tries to get the umask value from the following places in the following order:

       ·   umask= argument

       ·   umask= entry of the users GECOS field

       ·   pri= entry of the users GECOS field

       ·   ulimit= entry of the users GECOS field

       ·   UMASK= entry from /etc/default/login

       ·   UMASK entry from /etc/login.defs

```

```
matthew@matthew-Aspire-7540:~$ egrep -i "umask|USERGROUPS_ENAB" /etc/login.defs
#       UMASK           Default "umask" value.
# UMASK is the default umask value for pam_umask and is used by
# 022 is the "historical" value in Debian for UMASK
# If USERGROUPS_ENAB is set to "yes", that will modify this UMASK default value
UMASK           022
# Enable setting of the umask group bits to be the same as owner bits
USERGROUPS_ENAB yes
matthew@matthew-Aspire-7540:~$ 
```

I came accross this a while ago when i found out that motd has gone to pam (i wanted to customise my ssh motd).

I have not worked through the boot process of these scripts so i am not sure if this is redundant or the new way to define umask.

I will look into this.

Kind regards

---

### Post by bab1 on 2012-03-02
> **matt_symes said:**
> Hi

```
pam_umask.so [debug] [silent] [usergroups] [COLOR="Red"][umask=mask][/COLOR]

·   [COLOR="Red"]umask= argument[/COLOR]
·   [COLOR="Green"]UMASK entry from /etc/login.defs[/COLOR]

```

I see. I was under the impression that the umask you highlighted in red was the parameter passed to pam_umask.so that i have highlighted above. I thought it fell through to the option i have highlighted in green.

Working through the configuration files... 

```
matthew@matthew-Aspire-7540:~$ grep -i umask /etc/skel/.profile 
# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022
matthew@matthew-Aspire-7540:~$ 
```

```
matthew@matthew-Aspire-7540:~$ grep -i umask /etc/profile
# The default umask is now handled by pam_umask.
# See pam_umask(8) and /etc/login.defs.
matthew@matthew-Aspire-7540:~
```

```
DESCRIPTION
       pam_umask is a PAM module to set the file mode creation mask of the current environment. The umask affects the default permissions assigned to newly created
       files.

       The PAM module tries to get the umask value from the following places in the following order:

       ·   umask= argument

       ·   umask= entry of the users GECOS field

       ·   pri= entry of the users GECOS field

       ·   ulimit= entry of the users GECOS field

       ·   UMASK= entry from /etc/default/login

       ·   UMASK entry from /etc/login.defs

```

```
matthew@matthew-Aspire-7540:~$ egrep -i "umask|USERGROUPS_ENAB" /etc/login.defs
#       UMASK           Default "umask" value.
# UMASK is the default umask value for pam_umask and is used by
# 022 is the "historical" value in Debian for UMASK
# If USERGROUPS_ENAB is set to "yes", that will modify this UMASK default value
UMASK           022
# Enable setting of the umask group bits to be the same as owner bits
USERGROUPS_ENAB yes
matthew@matthew-Aspire-7540:~$ 
```

I came accross this a while ago when i found out the motd has gone to pam (i wanted to customise my ssh motd).

I have not worked through the boot process of these scripts so i am not sure if this is redundant or the new way to define umask.

I will look into this.

Kind regards

let us know what you find.  Right now I have a functioning server and  loathe to make changes to it.  But, as Ubuntu (and Debian itself) changes so must we.  Time to put my thinking cap on...

---

### Post by bab1 on 2012-03-02
@matt_symes,

This appears to be a "Tempest in a Teapot".  The PAM module (pam_umask.so) does indeed provide consistent umask values across all applications (shell or no).  It uses the value of the last value check as you suspected, but.... at least on my servers, the only line that has any value is the one I highlighted before.  All the others are non existent or commented out by default (e.g /etc/login.defs).  On my machines this is the line (in context)```
# UMASK usage is discouraged because it catches only some classes of user
# entries to system, in fact only those made through login(1), while setting
# umask in shell rc file will catch also logins through su, cron, ssh etc.
#
# At the same time, using shell rc to set umask won't catch entries which use
# non-shell executables in place of login shell, like /usr/sbin/pppd for "ppp"
# user and alike.
#
# Therefore the use of pam_umask is recommended as the solution which
# catches all these cases on PAM-enabled systems.
# 
# This avoids the confusion created by having the umask set
# in two different places -- in login.defs and shell rc files (i.e.
# /etc/profile).
#
# For discussion, see #314539 and #248150 as well as the thread starting at
# http://lists.debian.org/debian-devel/2005/06/msg01598.html
#
# Prefix these values with "0" to get octal, "0x" to get hexadecimal.
#
ERASECHAR	0177
KILLCHAR	025
# 022 is the "historical" value in Debian for UMASK when it was used
# 027, or even 077, could be considered better for privacy
# There is no One True Answer here : each sysadmin must make up his/her
# mind.
**[COLOR="Red"]#UMASK		022[/COLOR]**

```

So what we have is a pam_umask that by default applies the value set in /etc/profile across all instances that umask is needed.  A long and winding road indeed.

I'm interested in what you find on your machines.

> **matt_symes said:**
> Hi

```
pam_umask.so [debug] [silent] [usergroups] [COLOR="Red"][umask=mask][/COLOR]

·   [COLOR="Red"]umask= argument[/COLOR]
·   [COLOR="Green"]UMASK entry from /etc/login.defs[/COLOR]

```

I see. I was under the impression that the umask you highlighted in red was the parameter passed to pam_umask.so that i have highlighted above. I thought it fell through to the option i have highlighted in green.

Working through the configuration files... 

```
matthew@matthew-Aspire-7540:~$ grep -i umask /etc/skel/.profile 
# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022
matthew@matthew-Aspire-7540:~$ 
```

```
matthew@matthew-Aspire-7540:~$ grep -i umask /etc/profile
# The default umask is now handled by pam_umask.
# See pam_umask(8) and /etc/login.defs.
matthew@matthew-Aspire-7540:~
```

```
DESCRIPTION
       pam_umask is a PAM module to set the file mode creation mask of the current environment. The umask affects the default permissions assigned to newly created
       files.

       The PAM module tries to get the umask value from the following places in the following order:

       ·   umask= argument

       ·   umask= entry of the users GECOS field

       ·   pri= entry of the users GECOS field

       ·   ulimit= entry of the users GECOS field

       ·   UMASK= entry from /etc/default/login

       ·   UMASK entry from /etc/login.defs

```

```
matthew@matthew-Aspire-7540:~$ egrep -i "umask|USERGROUPS_ENAB" /etc/login.defs
#       UMASK           Default "umask" value.
# UMASK is the default umask value for pam_umask and is used by
# 022 is the "historical" value in Debian for UMASK
# If USERGROUPS_ENAB is set to "yes", that will modify this UMASK default value
UMASK           022
# Enable setting of the umask group bits to be the same as owner bits
USERGROUPS_ENAB yes
matthew@matthew-Aspire-7540:~$ 
```

I came accross this a while ago when i found out that motd has gone to pam (i wanted to customise my ssh motd).

I have not worked through the boot process of these scripts so i am not sure if this is redundant or the new way to define umask.

I will look into this.

Kind regards

---

