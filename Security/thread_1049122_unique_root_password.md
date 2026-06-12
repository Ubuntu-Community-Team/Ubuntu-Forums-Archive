---
title: "unique root password"
date: 2009-01-24
forum: Security
---

### Post by Post Monkeh on 2009-01-24
sorry if this is the wrong place.

i'm fairly new to ubuntu and linux in general *cough 2 weeks cough*, though i'm not exactly a computer illiterate.

i've been doing quite a bit of tinkering and so on so i've gotten to know my way about 8.10 pretty well for a beginner, but i still don't know enough to understand the complex discussions going on about older systems when i've been trying to find out the answer to this question.

to put it simply, is it possible to leave the root account disabled (ie you can't log into it), and have one password that can be used in conjunction with the sudo command from ANY other account to perform administrative actions.  
ie i log in as "will" with my own password, but whn i "sudo" something i have to enter a totally different password?  
it's probably quite simple, but i don't want to screw anything up by changing user settings without knowing the outcome before i do it.

i dont care if enetering my own password gives the same results (ie i can sudo and enter my own password or a different one), i'd just like a global password that can be used on any account set up to give root access.

thanks in advance.

---

### Post by SunnyRabbiera on 2009-01-24
Sudo cuts root out of the equation, technically you are the root if you are the main user but only when you enable those privileges.
Now it is possible if you add more users to give them sudo rights as well but they will have their own passwords too.

---

### Post by hyper_ch on 2009-01-24
if you want someone to be able to access sudo as you can right now, then add them to the admin group.

---

### Post by Post Monkeh on 2009-01-24
no, what i mean is, i understand anyone can be given admin rights to use sudo, however what i want to know is if it's possible for me to use the same admin password for ALL accounts, regardless of the actual account password.

essentially i want one "super-password" so that if, say, i was away from home and someone else with a "normal" account needed to do something, i could give them the admin password to do what they needed to without having to give their account specific admin rights that lets them do whatever they want all the time, and also saves me having to give out my own password (i realise that with a password giving access to sudo commands they could gain access to my account anyway, but my family really aint that smart :D)

---

### Post by gjoellee on 2009-01-24
> **Post Monkeh said:**
> no, what i mean is, i understand anyone can be given admin rights to use sudo, however what i want to know is if it's possible for me to use the same admin password for ALL accounts, regardless of the actual account password.

You mean like this:
the normal user password: 123
then the root password (which is the same): 123

yes that works

---

### Post by Post Monkeh on 2009-01-24
> **gjoellee said:**
> You mean like this:
the normal user password: 123
then the root password (which is the same): 123

yes that works

not exactly.

what i mean is
account 1 logs in with 123. 123 will not allow them to sudo.
account 2 logs in with 321. 321 will not allow them to sudo.
password 456 allows BOTH accounts to use sudo.

---

### Post by sisco311 on 2009-01-24
> **Post Monkeh said:**
> no, what i mean is, i understand anyone can be given admin rights to use sudo, however what i want to know is if it's possible for me to use the same admin password for ALL accounts, regardless of the actual account password.

essentially i want one "super-password" so that if, say, i was away from home and someone else with a "normal" account needed to do something, i could give them the admin password to do what they needed to without having to give their account specific admin rights that lets them do whatever they want all the time, and also saves me having to give out my own password (i realise that with a password giving access to sudo commands they could gain access to my account anyway, but my family really aint that smart :D)

Create a new admin account or

enable the root account, but [COLOR="Red"]DON'T[/COLOR] ENABLE THE ROOT LOGIN.
Change the Authentication Mode to su in gksu-properties.
Set up a strong root password and change it often.

IMO the first solution is easier and much more secure.
The second is more or less what you want. They will have to use su instead of sudo.

---

### Post by carml on 2009-01-24
The administration password is unique,and it's required only to upgrade the system,setting the connetion(if there's more than one avaible,like on a notebook),and so on.For all other purposes it isn't required.
I hope this may help you.

---

### Post by gjoellee on 2009-01-24
> **Post Monkeh said:**
> not exactly.

what i mean is
account 1 logs in with 123. 123 will not allow them to sudo.
account 2 logs in with 321. 321 will not allow them to sudo.
password 456 allows BOTH accounts to use sudo.

what? I was using "123" as an pasword example for user and root. Root and normal user can use the same password.

> **sisco311 said:**
> Create a new admin account or

enable the root account, but [COLOR=Red]DON'T[/COLOR] ENABLE THE ROOT LOGIN.
Change the Authentication Mode to su in gksu-properties.
Set up a strong root password and change it often.

IMO the first solution is easier and much more secure.
The second is more or less what you want. They will have to use su instead of sudo.

+1

_***[COLOR=Red]PS: Yeah post # 1 000[/COLOR]***_

---

### Post by Post Monkeh on 2009-01-24
> **gjoellee said:**
> what? I was using "123" as an pasword example for user and root. Root and normal user can use the same password.


yeah but i mean i want to have DIFFERENT passwords.

ie log in with one username/password, open a terminal, use a sudo command, and have to use a different password.

maybe i'm making it sound more complicated than it should be.

can i log in to a normal user account, open a terminal, and use a sudo command with an admin username/password, or can sudo commands ONLY be initiated from a full fledged admin account?

---

### Post by KIAaze on 2009-01-24
I think the easiest would be to enable the root account.
The root account will only have one password and that's the one you'll use.
Then you just:
```
sudo -u root COMMAND
```

Perhaps sudo COMMAND also works if the user is not an admin, but I'm not sure.
Alternative:
```
su -c COMMAND
```

---

### Post by brandon88tube on 2009-01-24
I think what he is asking is, if he can make an the sudo password for any user in the admin group to be the same. Ex: user1 pass=111, user2 pass=222, user3 pass=333. sudo pass=987. This way user1 even though his password is 111 has to use 987 as the password for sudo. The same for user2, user2 has to enter 987 for sudo instead of 222.

I hope I understood correctly and hope this helps others to understand.

---

### Post by KIAaze on 2009-01-24
As far as I know, one account = one password. I never heard about one user being able to have multiple passwords.

So the easiest is one root account usable by all those who know the root password which is different from their account password.

Otherwise:
user1, admin1
user2, admin2
...
=>Each user has one account password and one admin password.

---

### Post by brandon88tube on 2009-01-24
Does sudo have to use the user's password though or can you set it to be something?

---

### Post by KIAaze on 2009-01-24
From man sudo:
> If the invoking user is root or if the target user is the same as the invoking user, no password is required. Otherwise, sudo requires that users authenticate themselves with a password by default (NOTE: in the **default configuration** this is the user's password, not the root password). 

So this implies that things can be configured.
And indeed they can!

Look at the sudoers manual for the following entries:
**runas_default**
rootpw
targetpw
runaspw 

Here's the manual page:
[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

> runas_default

    The default user to run commands as if the -u flag is not specified on the command line. This defaults to root. Note that if runas_default is set it must occur before any Runas_Alias specifications.


> runaspw

    If set, sudo will prompt for the password of the user defined by the runas_default option (defaults to root) instead of the password of the invoking user. This flag is off by default.


> targetpw

    If set, sudo will prompt for the password of the user specified by the -u flag (defaults to root) instead of the password of the invoking user. Note that this precludes the use of a uid not listed in the passwd database as an argument to the -u flag. This flag is off by default.

> rootpw

    If set, sudo will prompt for the root password instead of the password of the invoking user. This flag is off by default.

But I still think it's easier to run "sudo -u root COMMAND" than configuring /etc/sudoers to do what you want...

More sudo configuration help:
[http://www.gentoo.org/doc/en/sudo-guide.xml](http://www.gentoo.org/doc/en/sudo-guide.xml)

---

### Post by Post Monkeh on 2009-01-24
> **brandon88tube said:**
> I think what he is asking is, if he can make an the sudo password for any user in the admin group to be the same. Ex: user1 pass=111, user2 pass=222, user3 pass=333. sudo pass=987. This way user1 even though his password is 111 has to use 987 as the password for sudo. The same for user2, user2 has to enter 987 for sudo instead of 222.

I hope I understood correctly and hope this helps others to understand.

this is what i mean.

---

### Post by Post Monkeh on 2009-01-24
> **KIAaze said:**
> From man sudo:


So this implies that things can be configured.
And indeed they can!

Look at the sudoers manual for the following entries:
**runas_default**
rootpw
targetpw
runaspw 

Here's the manual page:
[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)





But I still think it's easier to run "sudo -u root COMMAND" than configuring /etc/sudoers to do what you want...

More sudo configuration help:
[http://www.gentoo.org/doc/en/sudo-guide.xml](http://www.gentoo.org/doc/en/sudo-guide.xml)

that's great, just what i needed. might have a look to see if it can be set to automatically run any "sudo" command as root but the sudo -u root will do just what i want.

---

### Post by brandon88tube on 2009-01-24
I'm glad that I was able to help clear things up for you.

---

### Post by hyper_ch on 2009-01-25
I haven't tried it but

(1) login with your user account (that is in the admin group)
(2) run
```

sudo -i

```
to get root access while you're logged in
(3) run
```

su USERNAME

```
That should authorize you as USERNAME because you were running as root before without being asked for a password.

---

### Post by Post Monkeh on 2009-01-26
oh dear.

i thought i would try out this "su" idea, but i seem to have wrecked things a little.

i created a user called "user", and another user called "admin"

i'm beginning to think creating that "admin" user was a bit of a  mistake due to the fact the default administration group is also called "admin"

once i'd created them, i could no longer perform administration to the users and groups through my normal account (will in the will group) or the admin account.

i managed, with the help of "sudo addgroup" to get my main "will" account added to the admin group and was able to gain control of the users/groups setings long enough to give myself control over everything by checking all the boxes.  i'm beginning to think this was a mistake too, especially since after deleting the admin account hoping it would reset the admin group to normal i have now totally lost control of my users and groups settings :D

any way to just reset it all to normal?

---

### Post by Post Monkeh on 2009-01-26
also, my network is pissing about.  when i first start the computer, i can connect to the network but can't do anything without first loading a firewall (either gufw or firestarter) but to run the firewall it asks me for my password. i can't remember it doing that before.  and from a normal user account i can't run them.

it's strange, i can sudo from the terminal yet i can't access users and groups, it tells me 
"could not authenticate.
an unexpected error has occurred"

i'm guessing the permissions work slightly in reverse (ie when my main users permissions screen was up, a lot of the boxes were unchecked. i think because i checked them, anyone under this group level now cannot perform these tasks.

---

### Post by KIAaze on 2009-01-26
I'm not sure I can help you, but it might help if you posted the following files:
/etc/passwd
/etc/sudoers
/etc/group

---

### Post by Post Monkeh on 2009-01-26
/etc/passwd

```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
hplip:x:103:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:104:112:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
gdm:x:105:113:Gnome Display Manager:/var/lib/gdm:/bin/false
pulse:x:106:115:PulseAudio daemon,,,:/var/run/pulse:/bin/false
saned:x:107:118::/home/saned:/bin/false
messagebus:x:108:119::/var/run/dbus:/bin/false
polkituser:x:109:120:PolicyKit,,,:/var/run/PolicyKit:/bin/false
avahi:x:110:121:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:111:122:Hardware abstraction layer,,,:/var/run/hald:/bin/false
will:x:1000:1000:William Martin,,,:/home/will:/bin/bash
clamav:x:113:126::/var/lib/clamav:/bin/false
uml-net:x:112:128::/home/uml-net:/bin/false
```


/etc/sudoers

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

/etc/group

```
root:x:0:will
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:will
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:will
fax:x:21:will
voice:x:22:
cdrom:x:24:will
floppy:x:25:
tape:x:26:will
sudo:x:27:
audio:x:29:pulse,will
dip:x:30:will
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:will
sasl:x:45:
plugdev:x:46:will
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:will
nvram:x:105:
fuse:x:106:will
ssl-cert:x:107:
lpadmin:x:108:will
crontab:x:109:
mlocate:x:110:
ssh:x:111:
avahi-autoipd:x:112:
gdm:x:113:
netdev:x:114:will
pulse:x:115:
pulse-access:x:116:
pulse-rt:x:117:
saned:x:118:
messagebus:x:119:
polkituser:x:120:
avahi:x:121:
haldaemon:x:122:
admin:x:1002:will
will:x:1000:will
sambashare:x:124:will
winbindd_priv:x:125:
clamav:x:126:
slocate:x:127:
uml-net:x:128:
```

cheers big ears


btw, following a reset i now do have control of the users/groups settings again, however it still isn't right.  my main user still has every selection checked, and is a member of the will, admin and root groups.

i'm gonna delete it from the root group now, but i know originally i was never a member of the admin group (which i think may have been stuffed up anyway because i created an admin user)

---

### Post by KIAaze on 2009-01-26
Being part of the "will" group is normal (when you create a user account it also creates a group with the same name by default).

You must be part of the "admin" group to use sudo.

Being part of the "root" group isn't normal as far as I know.

---

### Post by Post Monkeh on 2009-01-26
i'm more worried about the fact that i changed the permission settings in my user account (before i would say half the permissions were unchecked, and had been unchanged since my ubuntu was installed so i'm guessing that was normal), and added an "admin" user, presumably stuffing up some of the settings for the admin group.

---

### Post by e1mer on 2009-01-26
The short answer is no, you cannot disable root but have
a common admin password.

The long answer is closer to what you want, I think.

Create a new user, something like 'captainahab'
with a strong password.

Add captainahab to the admin group in /etc/password.

Now, when you want a non-sudoer to be able to sudo,
give him the captainahab account and password,
then next time it is possible for you, change the
captainahab password to a new strong password.

There is some discussion in sudoers examples about 
doing something similar but restricting the commands
that captainahab can use in the sudoers file.

I strongly suggest that you learn that so that captainahab
cannot subsequently vi /etc/group and add admin to himself
(or read other peoples mail, etc)

---

### Post by KIAaze on 2009-01-30
_**How to make sudo ask for the root password instead of the user password:**_

**IMPORTANT 1: Only use visudo to edit /etc/sudoers!**
It makes sure you don't save a sudoers file with syntax errors.
Command:
```
sudo visudo
```

**IMPORTANT 2: Make sure you activate the root account first!**
cf: [http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html](http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html)
If you can log in as root by using the "su" command and entering the chosen root password, everything is OK.

All you have to do for sudo to ask the root password is add those two lines to /etc/sudoers:
```
Defaults targetpw   # ask for the password of the target user i.e. root
ALL ALL=(ALL) ALL   # WARNING! Only use this together with 'Defaults targetpw'!

```

I haven't tested it yet, but I tested the opposite on OpenSUSE, i.e. make OpenSUSE ask the user password instead of the root password.
All I had to do was comment them out. :)

Just for reference, here's the /etc/sudoers file of an OpenSUSE system, which is set up so that it asks for the root password instead of the user password:
```

# sudoers file.
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the sudoers man page for the details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults specification

# Prevent environment variables from influencing programs in an
# unexpected or harmful way (CVE-2005-2959, CVE-2005-4158, CVE-2006-0151)
Defaults always_set_home
Defaults env_reset

Defaults env_keep = "LANG LC_ADDRESS LC_CTYPE LC_COLLATE LC_IDENTIFICATION LC_MEASUREMENT LC_MESSAGES LC_MONETARY LC_NAME LC_NUMERIC LC_PAPER LC_TELEPHONE LC_TIME LC_ALL LANGUAGE LINGUAS XDG_SESSION_COOKIE"
# Comment out the preceding line and uncomment the following one if you need
# to use special input methods. This may allow users to compromise  the root
# account if they are allowed to run commands without authentication.
#Defaults env_keep = "LANG LC_ADDRESS LC_CTYPE LC_COLLATE LC_IDENTIFICATION LC_MEASUREMENT LC_MESSAGES LC_MONETARY LC_NAME LC_NUMERIC LC_PAPER LC_TELEPHONE LC_TIME LC_ALL LANGUAGE LINGUAS XDG_SESSION_COOKIE XMODIFIERS GTK_IM_MODULE QT_IM_MODULE QT_IM_SWITCHER"

# In the default (unconfigured) configuration, sudo asks for the root password.
# This allows use of an ordinary user account for administration of a freshly
# installed system. When configuring sudo, delete the two
# following lines:
Defaults targetpw   # ask for the password of the target user i.e. root
ALL ALL=(ALL) ALL   # WARNING! Only use this together with 'Defaults targetpw'!

# Runas alias specification

# User privilege specification
root	ALL=(ALL) SETENV: ALL

# Uncomment to allow people in group wheel to run all commands
# and set environment variables.
# %wheel	ALL=(ALL) SETENV: ALL

# Same thing without a password
# %wheel	ALL=(ALL) NOPASSWD: SETENV: ALL

# Samples
# %users  ALL=/sbin/mount /cdrom,/sbin/umount /cdrom
# %users  localhost=/sbin/shutdown -h now


```

---

### Post by bodhi.zazen on 2009-01-30
But if you do as [KIAaze]("http://ubuntuforums.org/member.php?u=240158") suggests you have opened a potential security hole be enabling the root account.

So, set the root shell to /bin/false

and to get a root shell use

sudo -c /bin/bash

This will allow you to obtain a root shell but not log in as root.

To be honest, at the end of the day, it is easier to use a single admin accoutn for sys admin and log in as a non - privileged user for daily use.

To obtain a root shell, su to the admin account, or 

With the second method you have one PW to log in, and another to access root and there is no need to set a root password.

---

