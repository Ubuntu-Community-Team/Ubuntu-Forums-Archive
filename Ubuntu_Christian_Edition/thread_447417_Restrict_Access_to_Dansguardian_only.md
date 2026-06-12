---
title: "Restrict Access to Dansguardian only"
date: 2007-05-18
forum: Ubuntu Christian Edition
---

### Post by seismicmike on 2007-05-18
Hey is there anyway to apply a separate password to Dansquardian other than the admin password - or to restrict access to only that program or whatever b/c I want to protect myself from the temptation to turn it on/off when I'm on (it's more for me right now than any kids I have b/c.... well I don't have any yet), but I still want to be the one to run system updates and be in charge of the system in general...

ie... I don't want to have to call my wife over to run a simple apt-get update of, say, firefox or something that has nothing to do with dansguardian directly.

Thanks

---

### Post by trent dillman on 2007-05-18
...

---

### Post by urukrama on 2007-05-21
I believe there might be a way of accomplishing this through editing the /etc/sudoers file. I've seen this suggested, but never confirmed. It is possible to limit directories that certain users/groups can access through sudo. See, for example, [this]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo") site:

> **Granting Access To Specific Users To Specific Files **
This entry allows user peter and all the members of the group operator to gain access to all the program files in the /sbin and /usr/sbin directories, plus the privilege of running the command /usr/local/apps/check.pl. Notice how the trailing slash (/) is required to specify a directory location: 
```
peter, %operator ALL= /sbin/, /usr/sbin, /usr/local/apps/check.pl
```Notice also that the lack of any username entries within parentheses () after the = sign prevents the users from running the commands automatically masquerading as another user. This is explained further in the next example.

You could add all other directories, except dansguardian's /etc/dansguardian/ and /etc/init.d/dansguardian. You'd still have full rights over all the other (except /etc/) root directories, but I'm not sure though if that would still allow you to install new applications (and create new folders in /etc/).

The [sudoers manual]("http://www.gratisoft.us/sudo/man/sudoers.html") might also be useful. You get some info on using wildcards, which may or may not be useful for accomplishing this. From that site:

> An exclamation point ('!') can be used as a logical not operator both in an alias and in front of a Cmnd. This allows one to exclude certain values. Note, however, that using a ! in conjunction with the built-in ALL alias to allow a user to run ``all but a few'' commands rarely works as intended (see SECURITY NOTES below).
 
[...]
```
 pete           HPPA = /usr/bin/passwd [A-z]*, !/usr/bin/passwd root
```The user pete is allowed to change anyone's password except for root on the HPPA machines. Note that this assumes passwd(1) does not take multiple usernames on the command line.


(There are some limitations to this approach, though, as mentioned later on that page.)

I've never tried any of this, and have no idea whether this would work or screw up your computer (make sure to back up the sudoers file if you will try this out!). But it might be worth a shot. Please let us know whether it works or not.

---

### Post by Linux_Maths on 2007-05-27
I really want to know this too. Did the previous post worked for you? Please let me know.

---

### Post by dailychoices on 2008-05-07
Obviously you would need to create another account that would have the rights to edit the sudoers file. Otherwise you could go right in and remove the line you entered to restrict your access. So along with restricting access to DansGuardian you will also need to restrict access to the sudoers file as well.

I will be working with my wife to nail this down and let you know how it goes.

---

### Post by izak on 2008-06-18
If anyone has a solution to this I will be interested to know it...

---

### Post by Cyclops_ on 2008-07-11
This is EXACTLY what I have been trying to accomplish for the last couple of hours with no success.  I mean, I will get to a point I think is foolproof, only to find another way around it.  What I want is to allow myself full access to all commands possible while blacklisting anything that has anything to do with Dansguardian.  visudo is where I turned.

Here is my current methodology:

first, I give myself full access:

```

myusername   ALL = ALL

```OK, now I have all access...  so, lets start the blacklisting...

First, disallow the ability to disable, restart, etc, anything to do with DG programs:
```

Cmnd_Alias    D = /etc/init.d/dansguardian,/etc/init.d/firehol,/usr/sbin/service,/etc/init.d/tinyproxy,/sbin/iptables,/sbin/ip6tables, /usr/sbin/service

```And modify the user line accordingly:
```

myusername   ALL = ALL, !D
 
```OK... so far so good.  Now, we don't want to be able to touch anything in the dansguardian folders.  Of course the "*" character doesn't work recursively (I really really wish it did!) so, we have to have multiple declarations for each directory.  

So we get :
```

Cmnd_Alias   DG = /bin/* /etc/dansguardian/*,/bin/* /etc/dansguardian/*/*, /bin/* /etc/dansguardian/*/*/*, /bin/* /etc/dansguardian/*/*/*/*
Cmnd_Alias   DG2 = /usr/bin/* /etc/dansguardian/*,/usr/bin/* /etc/dansguardian/*/*,/usr/bin/* /etc/dansguardian/*/*/*,/usr/bin/* /etc/dansguardian/*/*/*/*
 
```and again modify the user line accordingly:
```

 myusername   ALL = ALL, !D, !DG, !DG2
  
```There are 2 problems to this portion.  First, is that you could move an executable, say vim, from there to another path, and use it, like so:
```

sudo mv /usr/bin/vim ~/Desktop && cd ~/Desktop && sudo vim /etc/dansguardian/exceptionsitelist

```To this problem, we add the following:
```

Cmnd_Alias    CP_RENAME = /bin/cp /usr/bin/*,/bin/mv /usr/bin/*,/usr/bin/rename /usr/bin/*
Cmnd_Alias    CP_RENAME2 = /bin/cp /bin/*,/bin/mv /bin/*,/usr/bin/rename /bin/*

```Such that we cannot use the cp / rename / mv commands to copy another command elsewhere and circumvent the block in the first place.

Modifying the user line thus:
```

myusername   ALL = ALL, !D, !DG, !DG2, !CP_RENAME, !CP_RENAME2

```Problem 2 ( and I haven't come up with a solution to this yet ) is that you can always download an executable from the internet and use it.  Boom, instant access! (arg)

Next problem is that we don't want to be able to use the root user in any way, or we will have absolute control.  So we add:
```

Cmnd_Alias    HIJACK_ROOT = /usr/bin/su *root*,/usr/bin/su [-]*

```and the new user line:
```

myusername   ALL = ALL, !D, !DG, !DG2, !CP_RENAME, !CP_RENAME2, !HIJACK_ROOT

```but this doesn't address the ability to:
```

sudo -i

```I haven't found a fix for that one yet, either.

Finally, and this is the abolute worst problem of all with this...  typically any command when run with sudo automatically gains access to anything it wants.  It has now taken on sudo access.  One thing you could do is, for example, open vim, and the do what is called a "Shell Escape", which is to execute a command from vim, but this command automatically has root powers.   The way to do this is with some special command.  In vim it's ":!<command>", such that you could:
```

:! /etc/init.d/dansguardian restart

```or
```

:! gvim /etc/dansguardian/exceptionsitelist

```Well it turns out that visudo (sudoers) has a way to turn that off.  It's called NOEXEC, and there are a couple of ways to use it.  One is that you can set up NOEXEC for specific commands (say /usr/bin/gvim, for example), or you can disable it all together.  Problem with specific commands is that there are so MANY that you could possibly use to shell exec.  The other problem is, even if you got them all, you haven't got them all.  Consider this set of commands:
```

cat > newprog
#!/bin/bash
gvim /etc/dansguardian/exceptionsitelist
<Control-C>
chmod +x newprog
sudo ./newprog

```With this, how could you ever get NOEXEC on only some specific progs to fit your needs?

OK, so you turn on NOEXEC globally.  PROBLEM!  Now you can't execute a host of commands that you wanted to access in the first place.  Like /etc/init.d/apache2 restart, for example.  That command relies on the ability to execute other system processes as a privileged user.

So, what now?  You start white-listing all the commands that you need to have able to have NOEXEC power.

PROBLEM!  What if you edit one of those now white-listed files, and, say, append "gvim /etc/dansguardian/exceptionsitelist" to the end of it, and then execute it?  BOOM!  Instant Access.

I'm tearing my hair out here, because I, too, would really like to be able to do anything but not have the temptation to touch Dansguardian.  I am looking for a solution.  Can anyone help?   Come up with any answers or ideas?

HELP!!!!!!

---

### Post by eric.duveau on 2008-07-11
As for me, God gave me the wisdom to give up dansguardian. I think dansguardian is good provided that you never got root access. As I am a computer passionate. I bought a good router with filtering in it. I have personnally tested Zywall 2 plus and Fortigate 50B. Although it is a bit expensive. You can work with less temptation as you would have given the router password to your friend/wife.

---

### Post by Cyclops_ on 2008-07-14
Maybe I _will_ have to get a router...
BUT... I am ALMOST there!!!  Here is the latest revision to /etc/sudoers (via visudo):

```

# Cmnd alias specification
Cmnd_Alias    ALL_OK             = /bin/,/usr/,/usr/*/*,/sbin/,/etc/init.d/
Cmnd_Alias    ALL_CROSS_POLLEN   = /bin/* /bin/*,/bin/* /usr/*,/bin/* /usr/*/*,/bin/* /sbin/*,/bin/* /etc/init.d/*,\
                                   /usr/* /bin/*,/usr/* /usr/*,/usr/* /usr/*/*,/usr/* /sbin/*,/usr/* /etc/init.d/*,\
                                   /usr/*/* /bin/*,/usr/*/* /usr/*,/usr/*/* /usr/*/*,/usr/*/* /sbin/*,/usr/*/* /etc/init.d/*,\
                                   /sbin/* /bin/*,/sbin/* /usr/*,/sbin/* /usr/*/*,/sbin/* /sbin/*,/sbin/* /etc/init.d/*
Cmnd_Alias    ALL_DANSGUARDIAN   = /etc/init.d/dansguardian,/etc/init.d/firehol,/etc/init.d/tinyproxy
Cmnd_Alias    ALL_DG_RESTRICTED  = /bin/* /etc/dansguardian/*,/usr/* /etc/dansguardian/*,/usr/*/* /etc/dansguardian/*,/sbin/* /etc/dansguardian/*,/etc/init.d/* /etc/dansguardian/*
Cmnd_Alias    ALL_DG_RESTRICTED2 = /bin/* /etc/dansguardian/*/*,/usr/* /etc/dansguardian/*/*,/usr/*/* /etc/dansguardian/*/*,/sbin/* /etc/dansguardian/*/*,/etc/init.d/* /etc/dansguardian/*/*
Cmnd_Alias    ALL_DG_RESTRICTED3 = /bin/* /etc/dansguardian/*/*/*,/usr/* /etc/dansguardian/*/*/*,/usr/*/* /etc/dansguardian/*/*/*,/sbin/* /etc/dansguardian/*/*/*,/etc/init.d/* /etc/dansguardian/*/*/*
Cmnd_Alias    ALL_ROOT           = /usr/bin/sudo,/usr/bin/passwd root,/bin/su,/usr/sbin/visudo
Cmnd_Alias    ALL_OTHERS         = /usr/bin/passwd superuser
Cmnd_Alias    SHELLS             = /bin/sh,/bin/csh,/bin/ksh,/usr/local/bin/tcsh,/bin/rsh,/usr/local/bin/zsh,/bin/bash


# User privilege specification
root    ALL=(ALL) ALL
mruser   ALL = ALL_OK, !ALL_DANSGUARDIAN, !ALL_DG_RESTRICTED, !ALL_DG_RESTRICTED2, !ALL_DG_RESTRICTED3, !ALL_ROOT, !ALL_OTHERS, !SHELLS, !ALL_CROSS_POLLEN
superuser ALL = ALL #This user I would not have the password to (my wife would), but it is available in case of need...

```This addresses EVERYTHING _except_ the Shell Escape.  But instead of taking a blacklist approach, it's more of a whitelist...  but with just about every command you'd ever want.

In all technicality I could (to fix the noexec thing):

1. Turn on no_exec globally
2. Whitelist commands that I would want to be able to have exec caps
3. Blacklist the use of any type of editors on the files that have exec caps

Not sure just how tedious that would be just yet... but I'll search for another solution for it first.  I was looking at sudoedit and setfacl.  Anyone know enough to tell me whether I'm heading down the wrong road?

Thanks!

---

### Post by Cyclops_ on 2008-07-26
All right...  I think I have just about everything that I can think of at this point... let me know what you think of this?

```

Defaults    env_reset

# Cmnd alias specification
Cmnd_Alias    ALL_OK             = /bin/,/sbin/,/etc/init.d/,/usr/,/usr/bin/,/usr/sbin
Cmnd_Alias    ALL_CROSS_POLLEN   = /bin/* /bin/*,/bin/* /usr/*,/bin/* /usr/bin/*,/bin/* /usr/sbin/*,/bin/* /sbin/*,/bin/* /etc/init.d/*,\
                                   /sbin/* /bin/*,/sbin/* /sbin/*,/sbin/* /usr/*,/sbin/* /usr/bin/*,/sbin/* /usr/sbin/*,/sbin/* /etc/init.d/*,\
                                   /usr/* /bin/*,/usr/* /sbin/*,/usr/* /usr/*,/usr/* /usr/bin/*,/usr/* /usr/sbin/*,/usr/* /etc/init.d/*,\
                                   /usr/bin/* /bin/*,/usr/bin/* /usr/*,/usr/bin/* /usr/bin/*,/usr/bin/* /usr/sbin/*,/usr/bin/* /sbin/*,/usr/bin/* /etc/init.d/*,\
                                   /usr/sbin/* /bin/*,/usr/sbin/* /usr/*,/usr/sbin/* /usr/bin/*,/usr/sbin/* /usr/sbin/*,/usr/sbin/* /sbin/*,/usr/sbin/* /etc/init.d/*
Cmnd_Alias    ALL_DANSGUARDIAN   = /etc/init.d/dansguardian,/etc/init.d/firehol,/etc/init.d/tinyproxy
Cmnd_Alias    ALL_DG_RESTRICTED  = /bin/* /etc/dansguardian/*,/usr/* /etc/dansguardian/*,/usr/bin/* /etc/dansguardian/*,/usr/sbin/* /etc/dansguardian/*,/sbin/* /etc/dansguardian/*,/etc/init.d/* /etc/dansguardian/*
Cmnd_Alias    ALL_DG_RESTRICTED2 = /bin/* /etc/dansguardian/*/*,/usr/* /etc/dansguardian/*/*,/usr/bin/* /etc/dansguardian/*/*,/usr/sbin/* /etc/dansguardian/*/*,/sbin/* /etc/dansguardian/*/*,/etc/init.d/* /etc/dansguardian/*/* 
Cmnd_Alias    ALL_DG_RESTRICTED3 = /bin/* /etc/dansguardian/*/*/*,/usr/* /etc/dansguardian/*/*/*,/usr/bin/* /etc/dansguardian/*/*/*,/usr/sbin/* /etc/dansguardian/*/*/*,/sbin/* /etc/dansguardian/*/*/*,/etc/init.d/* /etc/dansguardian/*/*/*
Cmnd_Alias    ALL_ROOT           = /usr/bin/sudo,/usr/bin/passwd root,/bin/su,/usr/sbin/visudo
Cmnd_Alias    ALL_OTHERS         = /usr/bin/passwd superuser
Cmnd_Alias    ALL_SHELLS         = /bin/sh,/bin/csh,/bin/ksh,/usr/local/bin/tcsh,/bin/rsh,/usr/local/bin/zsh,/bin/bash
Cmnd_Alias    ALL_NOEXECS        = /usr/bin/*edit*,/usr/bin/*vi*,/usr/bin/emacs,/usr/bin/less,/bin/more,/usr/bin/pager,/usr/bin/php,/usr/bin/perl
Cmnd_Alias    ALL_EXEC           = /usr/sbin/synaptic,/usr/bin/apt*

# User privilege specification
root    ALL=(ALL) ALL
mruser   ALL=ALL_OK, NOEXEC: ALL_NOEXECS, !ALL_ROOT, !ALL_OTHERS, !ALL_SHELLS, !ALL_DANSGUARDIAN, !ALL_DG_RESTRICTED, !ALL_DG_RESTRICTED2, !ALL_DG_RESTRICTED3, !ALL_CROSS_POLLEN, EXEC: ALL_EXEC

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

Basically with the sudoers file like this (by using visudo, of course), I have the following setup:

mruser (the primary user account) is NOT in the admin group.
superuser IS in the admin group.

mruser can do just about anything that doesn't meddle with dansguardian.  If anything needs to get done on the DG side of things, I have my wife:

```

su superuser <enter>
(put her password in) <enter>
sudo **** (whatever)

```

And with her there, I can explain what it is that I am doing.

Cool?

---

### Post by Cyclops_ on 2008-07-26
Small modification...  needed to make it so that commands with arguments would also be denied:

Change the following Cmnd_Aliases to reflect:

```

Cmnd_Alias    ALL_OK             = /bin/,/sbin/,/etc/init.d/,/usr/,/usr/bin/,/usr/sbin
Cmnd_Alias    ALL_CROSS_POLLEN   = /bin/* /bin/*,/bin/* /usr/*,/bin/* /usr/bin/*,/bin/* /usr/sbin/*,/bin/* /sbin/*,/bin/* /etc/init.d/*,\
                                   /sbin/* /bin/*,/sbin/* /sbin/*,/sbin/* /usr/*,/sbin/* /usr/bin/*,/sbin/* /usr/sbin/*,/sbin/* /etc/init.d/*,\
                                   /usr/* /bin/*,/usr/* /sbin/*,/usr/* /usr/*,/usr/* /usr/bin/*,/usr/* /usr/sbin/*,/usr/* /etc/init.d/*,\
                                   /usr/bin/* /bin/*,/usr/bin/* /usr/*,/usr/bin/* /usr/bin/*,/usr/bin/* /usr/sbin/*,/usr/bin/* /sbin/*,/usr/bin/* /etc/init.d/*,\
                                   /usr/sbin/* /bin/*,/usr/sbin/* /usr/*,/usr/sbin/* /usr/bin/*,/usr/sbin/* /usr/sbin/*,/usr/sbin/* /sbin/*,/usr/sbin/* /etc/init.d/*\
\
                                   /bin/* * /bin/*,/bin/* * /usr/*,/bin/* * /usr/bin/*,/bin/* * /usr/sbin/*,/bin/* * /sbin/*,/bin/* * /etc/init.d/*,\
                                   /sbin/* * /bin/*,/sbin/* * /sbin/*,/sbin/* * /usr/*,/sbin/* * /usr/bin/*,/sbin/* * /usr/sbin/*,/sbin/* * /etc/init.d/*,\
                                   /usr/* * /bin/*,/usr/* * /sbin/*,/usr/* * /usr/*,/usr/* * /usr/bin/*,/usr/* * /usr/sbin/*,/usr/* * /etc/init.d/*,\
                                   /usr/bin/* * /bin/*,/usr/bin/* * /usr/*,/usr/bin/* * /usr/bin/*,/usr/bin/* * /usr/sbin/*,/usr/bin/* * /sbin/*,/usr/bin/* * /etc/init.d/*,\
                                   /usr/sbin/* * /bin/*,/usr/sbin/* * /usr/*,/usr/sbin/* * /usr/bin/*,/usr/sbin/* * /usr/sbin/*,/usr/sbin/* * /sbin/*,/usr/sbin/* * /etc/init.d/*
Cmnd_Alias    ALL_DANSGUARDIAN   = /etc/init.d/dansguardian,/etc/init.d/firehol,/etc/init.d/tinyproxy
Cmnd_Alias    ALL_DG_RESTRICTED  = /bin/* /etc/dansguardian/*,/usr/* /etc/dansguardian/*,/usr/bin/* /etc/dansguardian/*,/usr/sbin/* /etc/dansguardian/*,/sbin/* /etc/dansguardian/*,/etc/init.d/* /etc/dansguardian/*\
                                   /bin/* * /etc/dansguardian/*,/usr/* * /etc/dansguardian/*,/usr/bin/* * /etc/dansguardian/*,/usr/sbin/* * /etc/dansguardian/*,/sbin/* * /etc/dansguardian/*,/etc/init.d/* * /etc/dansguardian/*
Cmnd_Alias    ALL_DG_RESTRICTED2 = /bin/* /etc/dansguardian/*/*,/usr/* /etc/dansguardian/*/*,/usr/bin/* /etc/dansguardian/*/*,/usr/sbin/* /etc/dansguardian/*/*,/sbin/* /etc/dansguardian/*/*,/etc/init.d/* /etc/dansguardian/*/*\
                                   /bin/* * /etc/dansguardian/*/*,/usr/* * /etc/dansguardian/*/*,/usr/bin/* * /etc/dansguardian/*/*,/usr/sbin/* * /etc/dansguardian/*/*,/sbin/* * /etc/dansguardian/*/*,/etc/init.d/* * /etc/dansguardian/*/* 
Cmnd_Alias    ALL_DG_RESTRICTED3 = /bin/* /etc/dansguardian/*/*/*,/usr/* /etc/dansguardian/*/*/*,/usr/bin/* /etc/dansguardian/*/*/*,/usr/sbin/* /etc/dansguardian/*/*/*,/sbin/* /etc/dansguardian/*/*/*,/etc/init.d/* /etc/dansguardian/*/*/*\
                                   /bin/* * /etc/dansguardian/*/*/*,/usr/* * /etc/dansguardian/*/*/*,/usr/bin/* * /etc/dansguardian/*/*/*,/usr/sbin/* * /etc/dansguardian/*/*/*,/sbin/* * /etc/dansguardian/*/*/*,/etc/init.d/* * /etc/dansguardian/*/*/*
Cmnd_Alias    ALL_ROOT           = /usr/bin/sudo,/usr/bin/passwd root,/bin/su,/usr/sbin/visudo
Cmnd_Alias    ALL_OTHERS         = /usr/bin/passwd superuser
Cmnd_Alias    ALL_SHELLS         = /bin/sh,/bin/csh,/bin/ksh,/usr/local/bin/tcsh,/bin/rsh,/usr/local/bin/zsh,/bin/bash
Cmnd_Alias    ALL_NOEXECS        = /usr/bin/*edit*,/usr/bin/*vi*,/usr/bin/emacs,/usr/bin/less,/bin/more,/usr/bin/pager,/usr/bin/php,/usr/bin/perl
Cmnd_Alias    ALL_EXEC           = /usr/sbin/synaptic,/usr/bin/apt*

```

---

### Post by eric.duveau on 2008-07-28
very interesting, indeed

---

### Post by dardack on 2009-01-09
Cyclops can you verify this completely works?

I'm all confused by this myself, but can you modified that sudoers file?

---

### Post by Cyclops_ on 2009-01-09
Actually, I discovered that there are still issues with this.... big, gaping issues.  2 of them that really stand out to me.

First, is that the sudoer thing only checks the path of the command given.  And NOT the path of the file being operated on.  for example, if, with sudoers you deny access for someone to be able to:

```

vim /etc/init.d/dansguardian

```

they can still do this:

```

cd /etc/init.d/ && vim dansguardian

```

The second thing, I can't remember, but it had to do with a limitation in sudoers file that could easily be rectified by implementing regular expression support....   I'll have to get back to you when I remember what it was...

The reason that #1 above matters is that I could go into /etc/init.d/ and edit, say, apache2, and add the line:

```

sudo gnome-terminal

```

... Then I could do:

```

sudo /etc/init.d/apache2

```

and bang, I have a stinking root gnome-terminal.... (arg).  I'm still trying to figure a way out of this.... so if ANYONE has any ideas(!!!) I would LOVE to hear them.

---

### Post by dardack on 2009-01-10
What if you:
(found in diff forum for diff problem)

What we did was create groups using "User Administrator" is the easiest

Then after the different groups are all created add the users to these groups as you feel fit.

Then if you kdesu konqueror. You can find the directories of the programs and then just change the access for the groups required.

Then check that the files in the bin directories are changed also to the configuration you want.

By altering the programs directories and the bin files you make sure that they cannot get to execute any part of the program you are restricting. Some programs will embed parts of the other program with out actually using the executable.

---

### Post by dardack on 2009-01-10
For now i'm just installing the machine with wife near me, and just letting her username have admin, i'll survive.

---

### Post by eric.duveau on 2009-01-31
> **dardack said:**
> What if you:
(found in diff forum for diff problem)

What we did was create groups using "User Administrator" is the easiest

Then after the different groups are all created add the users to these groups as you feel fit.

Then if you kdesu konqueror. You can find the directories of the programs and then just change the access for the groups required.

Then check that the files in the bin directories are changed also to the configuration you want.

By altering the programs directories and the bin files you make sure that they cannot get to execute any part of the program you are restricting. Some programs will embed parts of the other program with out actually using the executable.

It is an interesting idea but it seems time consumming to make this. 

Did you try it finally?

---

### Post by eric.duveau on 2009-04-14
[COLOR="Blue"]It may be useful for someone who wants to keep some freedom to install packages:[/COLOR]

_to install a package:_

**sudo aptgetintall < a_package >**

**cat  aptgetintall**
#/bin/bash
apt-get install $1

_to upgrade_

**sudo aptgetupgrade**

**cat aptgetupgrade**
#/bin/bash
apt-get upgrade
[COLOR="Blue"]
User will be able to install and upgrade[/COLOR]

**sudo -l**
aptgetintall, aptgetupgrade

```
 **cat /etc/sudoers**
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

User_Alias MES_USERS = duveau
Host_Alias MES_ORDIS = localhost, duveau-laptop
Cmnd_Alias MES_COMMANDES = /usr/local/pkgm/bin/aptgetinstall, /usr/local/pkgm/bin/aptgetupdate,/usr/local/pkgm/bin/aptgetupgrade




# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
# %admin ALL=(ALL) ALL
#

MES_USERS MES_ORDIS=(root)NOPASSWD:MES_COMMANDES
```

---

### Post by Carl Hamlin on 2009-05-14
Stop me if I've missed something obvious, but it sure sounds like we're not talking about filtering internet content for a child, here.

If you want to watch porn on the net, by all means do so - some of it can be quite educational.

That this issue should involve giving admin rights over your personal box to your spouse so you can 'avoid temptation' is frankly pretty silly. You're a big boy - make your own decisions.

---

### Post by Cyclops_ on 2009-05-14
Perhaps you *have* missed something, Carl.  I don't know if you have ever heard of something called an addiction.  Many of us out here have not only heard of it, but been rather unfortunate victims of its destructive paths -- and the fact that we are either posting or reading this thread may be evidence sufficient to suggest that perhaps we are not interested in being held captive any longer -- and that we are quite interested in doing all that we can to end its effects in our lives.  I, by profession, am a programmer.  And as such, require certain rights on my machine.  At the same time, I do not wish to be tempted by the many evils out there.  Yes, I am a big boy.  But it was a little version of myself who got tempted into trying something that would inevitably destroy much good in his life, and begin a chain of destructive, addictive behaviors that are *not* trivial to overcome.  And it certainly would not help to have the ever present possibility of simple mouse clicks to get some of us back to a place so dark and so utterly painful it can veritably be termed "hell".

Thank you for your interest in helping those of us who need it.  :)

---

### Post by ocarinahuff on 2009-05-14
There might be one way.  Get an old computer, Pentium 4 level or so, with an internal ethernet router card and wireless card.  install linux on it and dansguardian, and use that computer as a router/filter.  I believe there is software to decode a DSL signal from a phone line without the need for an external router.  Give someone else admin rights to that computer, including grub and BIOS password.  You can use that computer as a router with dansguardian filtering and wireless capability.
I haven't tried it, I just use someone else for admin rights to my computer, simple, annoying, but necessary for me.  Let me know if this idea would work.

---

### Post by Cyclops_ on 2009-05-14
ocarinahuff - 

Thank you for that comment.  I have been toying with something like that for a little while.  I have an old box that would work for the job.... i just need to figure out how that would work, and what hardware would be required.

I would like for it to be my main access point for all the computers on the network (including the wireless laptop).

What might be the exact configuration needed?  (I have a wireless card and an EXTRA lan card I can use.  My actual router also needs to be able to forward ports to certain computers.)

Any thoughts?

Thanks Again!  :)

---

### Post by elatre on 2009-06-02
Another approach could be to install Ubuntu Server and the minimum of software that allows you to have dansguardian and a virtual machine with Ubuntu Desktop.

---

### Post by eric.duveau on 2009-06-02
This solution seems to be effective for Laptop or Netbook

---

### Post by eric.duveau on 2009-06-02
> **eric.duveau said:**
> [COLOR="Blue"]It may be useful for someone who wants to keep some freedom to install packages:[/COLOR]

_to install a package:_

**sudo aptgetintall < a_package >**

**cat  aptgetintall**
#/bin/bash
apt-get install $1

_to upgrade_

**sudo aptgetupgrade**

**cat aptgetupgrade**
#/bin/bash
apt-get upgrade
[COLOR="Blue"]
User will be able to install and upgrade[/COLOR]

**sudo -l**
aptgetintall, aptgetupgrade

```
 **cat /etc/sudoers**
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

User_Alias MES_USERS = duveau
Host_Alias MES_ORDIS = localhost, duveau-laptop
Cmnd_Alias MES_COMMANDES = /usr/local/pkgm/bin/aptgetinstall, /usr/local/pkgm/bin/aptgetupdate,/usr/local/pkgm/bin/aptgetupgrade




# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
# %admin ALL=(ALL) ALL
#

MES_USERS MES_ORDIS=(root)NOPASSWD:MES_COMMANDES
```

This solution seems to be effective for Laptop or Netbook connected on a public hotspot

---

### Post by eric.duveau on 2009-06-02
> **ocarinahuff said:**
> There might be one way.  Get an old computer, Pentium 4 level or so, with an internal ethernet router card and wireless card.  install linux on it and dansguardian, and use that computer as a router/filter.  I believe there is software to decode a DSL signal from a phone line without the need for an external router.  Give someone else admin rights to that computer, including grub and BIOS password.  You can use that computer as a router with dansguardian filtering and wireless capability.
I haven't tried it, I just use someone else for admin rights to my computer, simple, annoying, but necessary for me.  Let me know if this idea would work.

unfortunately, if you have a laptop, you may expect to use it outside your office or your house.

---

### Post by eric.duveau on 2009-06-02
> **elatre said:**
> Another approach could be to install Ubuntu Server and the minimum of software that allows you to have dansguardian and a virtual machine with Ubuntu Desktop.

did you try it?

---

### Post by elatre on 2009-06-03
I didn't try it, I have no time now, but I would be very interested if someone could do it.

---

### Post by elatre on 2009-08-31
It works. 

I have tinyproxy and dansguardian on the host. I have Jaunty in a virtual machine (VMware). If the Network Adapter is NAT and if I point firefox to the proxy 192.168.18.2:8080 (192.168.18.2 = host, 8080 = dansguardian), the traffic goes through dansguardian.

Now I have to disable the bridged Network Adapter and I have to make the proxy transparent in the host. I guess I have to do both via the firewall, but I don't understand iptables. Can anybody help?

---

### Post by Duke555 on 2009-10-08
i am new to ubuntu. i am trying to accomplish exactly the same thing with dansguardian.

which file is being edited?
thank you

---

### Post by ocarinahuff on 2009-11-28
> **Cyclops_ said:**
> Actually, I discovered that there are still issues with this.... big, gaping issues.  2 of them that really stand out to me.

First, is that the sudoer thing only checks the path of the command given.  And NOT the path of the file being operated on.  for example, if, with sudoers you deny access for someone to be able to:

```

vim /etc/init.d/dansguardian

```

they can still do this:

```

cd /etc/init.d/ && vim dansguardian

```

The second thing, I can't remember, but it had to do with a limitation in sudoers file that could easily be rectified by implementing regular expression support....   I'll have to get back to you when I remember what it was...

The reason that #1 above matters is that I could go into /etc/init.d/ and edit, say, apache2, and add the line:

```

sudo gnome-terminal

```

... Then I could do:

```

sudo /etc/init.d/apache2

```

and bang, I have a stinking root gnome-terminal.... (arg).  I'm still trying to figure a way out of this.... so if ANYONE has any ideas(!!!) I would LOVE to hear them.

In answer to the first problem, how about this?

dansguardian, /danguardian, /*/danguardian, /*/*/danguardian

combine this with disallowing the mv and copy commands with these as args, or rather any command with these args.

---

### Post by alexm0428 on 2010-08-13
Hi.

I just want to know if the virtual machine solution did work. Right now I can't use another pc for the filtering or buy a router with filtering in it; so this seems to be the best option to me.

Did it work?

> **elatre said:**
> It works. 

I have tinyproxy and dansguardian on the host. I have Jaunty in a virtual machine (VMware). If the Network Adapter is NAT and if I point firefox to the proxy 192.168.18.2:8080 (192.168.18.2 = host, 8080 = dansguardian), the traffic goes through dansguardian.

Now I have to disable the bridged Network Adapter and I have to make the proxy transparent in the host. I guess I have to do both via the firewall, but I don't understand iptables. Can anybody help?

thanks.

---

### Post by elatre on 2010-08-13
> **alexm0428 said:**
> Hi.

I just want to know if the virtual machine solution did work. Right now I can't use another pc for the filtering or buy a router with filtering in it; so this seems to be the best option to me.

Did it work?

thanks.

Yes, it worked. I did it with VirtualBox, not VMWare. I don't use it now because I don't have enough RAM. 

Some questions I didn't solve (due to lack of time): a) how to put sound to work, b) some issues about permissions.

---

### Post by alexm0428 on 2010-08-14
Ok, then I will give it a try. Thanks.

---

### Post by elatre on 2010-08-14
> **alexm0428 said:**
> Ok, then I will give it a try. Thanks.
I have some incomplete notes of what I did. Can you read spanish or german?

---

### Post by alexm0428 on 2010-08-16
> **elatre said:**
> I have some incomplete notes of what I did. Can you read spanish or german?

Yes. I'm colombian so I can read spanish even better than english.

Thanks.

---

### Post by elatre on 2010-08-16
Hier you are:

---

### Post by ocarinahuff on 2011-01-13
The problem is the password.  If you're the admin user, then no amount of effort will completely block you from dansguardian's internals.  We need something similar to net nanny.  They have an internal password, which is required to grant access to the configuration GUI, or to grant access to blocked sites temporarily, or even to run the uninstaller.  I know linux doesn't uninstall the same way, we're out of luck there.  But if some clever programmer can take dansguardian, tinyproxy or some other transparent proxy, and all the config files, and roll it all into a single binary complete with guis to access the necessary settings and such.  No text files to tamper with, and we can have an internal program password that is required to change settings, grant temporary site access, and for starting/stopping/restarting the service.  This has to be all in one binary, or at least, in several binaries.  That way, the password can't be tampered with, and the settings aren't accessible from outside the program.
So even if you're the root user, if you attempt to stop the service, it'll ask for the program password.  If you forcibly remove it, you'll have to manually restore the network settings(it's a pain, if dansguardian is uninstalled improperly), and come up with a convincing story for your wife as to what happened to the program.(Good luck there, don't forget your pillow on your trip to the dog house).

---

### Post by tumelo on 2011-02-16
I'm in the same boat. When I was a windows user I used naomi and my wife(well girlfriend at the time) held the password for it. If only dansguardian could be as simple. Hopefully they come out with an update to resolve this issue. But it is important to be able to access it somehow, as it blocks legitimate things sometimes.

I'm not savvy enough to bypass stuff with terminal commands and/or config files like what Cyclops is talking about so if anybody has a simple solution that will keep a moderate noob off the GUI then I'd love to here it. Plus even if I did know how I'm too lazy to go out of my way to sin. Temptation's gotta be convenient or it's not that tempting :p

---

### Post by ocarinahuff on 2011-04-08
A possible alternative is apparmor/selinux.  Both say they are able to restrict root access.  I don't know how I would go about implementing that, tho.  Apparmor appears to be installed by default in Ubuntu, but is left in a very light, permissive mode.  Perhaps we could make a new user, and have apparmor generate a profile that restricts all access to anything dansguardian related for all users except the new user we created.  Anyone with enough experience willing to try this?

---

### Post by mpnordland on 2011-04-09
I found it easier to use accountability software instead of dansguardian. Net-Responsibility is what I use. It was so helpful that I joined the development team. You can download it at [http://www.netresponsibility.com/](http://www.netresponsibility.com/)

---

### Post by Jordy_224 on 2011-04-17
> **tumelo said:**
> I'm in the same boat. When I was a windows user I used naomi and my wife(well girlfriend at the time) held the password for it. If only dansguardian could be as simple. Hopefully they come out with an update to resolve this issue. But it is important to be able to access it somehow, as it blocks legitimate things sometimes.

I'm not savvy enough to bypass stuff with terminal commands and/or config files like what Cyclops is talking about so if anybody has a simple solution that will keep a moderate noob off the GUI then I'd love to here it. Plus even if I did know how I'm too lazy to go out of my way to sin. Temptation's gotta be convenient or it's not that tempting :p


I came across the same issue, created when installing dansguardian on a local machine. One suggestion is to create two accounts. The first is an admin account and the second is your main daily use account. 

```

1. admin -> edit dansguardian config & installs
2. myaccount -> normal function.
```

The trick is to create a random admin account pw then: 
   a. give it to a friend/spouse
   b. leave it in a different location ( at work, at school, safety deposit box ) .. any place that allows you to cool off. 

Its not a fool proof method but it works for casual linux users

good luck

---

