---
title: "Blocking users from SSH login"
date: 2008-08-22
forum: Server Platforms
---

### Post by G1ZmO65 on 2008-08-22
I have been using Webmin to add unix users to my server and have the option selected ON to automatically create Samba users when a Unix user is created. The reason being that I want to create Samba users and cant see an option for only creating a user in the Samba config page.

Now I don't want the new users to be able to connect via puTTY on the SSH connection. 

How do I block them?

Thanks

---

### Post by windependence on 2008-08-22
As usual, in Linux, there are a few ways you can do it. The best way would probably be to change the default user template so that when you create a new user they don't get automatic access. You couls also set up a group called, oh, I don't know ssh maybe and require that users be a part of that group to be allowed to ssh. That way, you can just add the users you want to have ssh access to the group and your good to go.

-Tim

---

### Post by G1ZmO65 on 2008-08-22
Thanks Tim

Where are the default templates normally stored?

---

### Post by Ximbiot on 2008-08-22
> **G1ZmO65 said:**
> Where are the default templates normally stored?

Tim's second suggestion may be easier to implement: Set "AllowGroups" to "ssh" in /etc/ssh/sshd_config to allow only members of the "ssh" group to login.

Otherwise, I'm not sure if webmin uses "adduser" to manipulate the user database as it probably should, or "useradd", or what, but if it uses one of these, then /etc/adduser.conf contains the adduser defaults and /etc/default/useradd contains the useradd settings and /etc/skel is copied by both programs to create new home directories for new users, but I'm not sure how you would use any of this to prevent shell access by default.  Perhaps by setting "DSHELL=/usr/sbin/nologin" in adduser.conf or "SHELL=/usr/sbin/nologin" in /etc/default/useradd?

---

### Post by windependence on 2008-08-22
I agree, using groups would be the cleanest way to do this now that I think about it.

-Tim

---

### Post by G1ZmO65 on 2008-08-22
I'm getting the impression that maybe using Webmin is overcomplicating matters and that I should just learn how to do the whole caboodle in the CLI. Yes? No?

I kind of managed to get round it by 
- Creating a unix user (thus automatically creating the samba user)
- Deleting the unix user (but not allowing the samba user to be deleted) 

This is probably not a good way to do it though lol

"AllowGroups" was not in the /etc/ssh/sshd_config file so I added it but it didnt seem to make any difference. I added myself to the ssh group but another unix user who is not in the ssh group can still log in via ssh.

These are the defaults for both the files you mentioned:

```
# /etc/adduser.conf: `adduser' configuration.
# See adduser(8) and adduser.conf(5) for full documentation.

# The DSHELL variable specifies the default login shell on your
# system.
DSHELL=/bin/bash
```

```
# Default values for useradd(8)
#
# The SHELL variable specifies the default login shell on your
# system.
# Similar to DHSELL in adduser. However, we use "sh" here because
# useradd is a low level utility and should be as general
# as possible
SHELL=/bin/sh
```

Q: Am I likely to lock myself out if I mess with these or will it only affect new users?

....Did it anyway lol....

Modified /etc/default/useradd with SHELL=/usr/sbin/nologin and created another user via webmin but the user can still log in via ssh

Modified /etc/adduser.conf with DSHELL=/usr/sbin/nologin and created another user via webmin but the user can still log in via ssh


Wondering if webmin uses its own method of creating users...

---

### Post by G1ZmO65 on 2008-08-22
Hmm Ok I used useradd to create a new user and found that I couldnt log in via SSH with that user.

The module config for webmin for adding users has the option:

```
Build list of shells from:
Builtin list  
Existing users  
/etc/shells
```

and the /etc/shells file reads:

```
# /etc/shells: valid login shells
/bin/csh
/bin/sh
/usr/bin/es
/usr/bin/ksh
/bin/ksh
/usr/bin/rc
/usr/bin/tcsh
/bin/tcsh
/usr/bin/esh
/bin/dash
/bin/bash
/bin/rbash
```

I dont see any reference to ssh there though.

(groping in the dark here a bit lol)

---

### Post by windependence on 2008-08-22
You're always better of using the CLI. I was where YOU are a few years back. I tried every GUI tool there was. I had a friend who was a *BSD nut. He was always laughing at me and making jokes. Now I know why. When you use the CLI, you get to know HOW things work, not just  that they work (and sometimes they don't). Webmin can be a great tool but it can also be a crutch. All those tools are is a fancy web front end for something on the back end that does exactly what we do at the CLI, except you don't have control over it like the CLI. 

Paul, I have seen you solve some problems here. You have the ability and are smart enough to use the command line. Ditch the crutch and join the "enlightened ones". You'll get a lot done faster.

-Tim

---

### Post by G1ZmO65 on 2008-08-22
Heh thanks Tim,

My problems are that I can only do this stuff for a few minutes every hour or so at work so can't really get "stuck into" it for any length of time. Family restricts my time at home too so I feel that I'm not getting anywhere fast.

I know I really need to learn the basics of WHY I need to do some stuff and not just the HOW to do it. I just don't know the basics like what shells are what and where the various system files are kept so I end up pottering about trying to find out where the configuration options are for stuff I don't yet understand. 

Frustrating lol

---

### Post by Ximbiot on 2008-08-22
> **G1ZmO65 said:**
> I'm getting the impression that maybe using Webmin is overcomplicating matters and that I should just learn how to do the whole caboodle in the CLI. Yes? No?

As Tim said, quite possible.  I'll second most of what he said with the addition that I have occasionally fallen back on some GUI (even webmin) when I've found documentation for some task to be incomplete, then studied the config file changes the GUI made when the GUI worked and switched back to the command line for future modifications.  :)

> **G1ZmO65 said:**
> "AllowGroups" was not in the /etc/ssh/sshd_config file so I added it but it didnt seem to make any difference. I added myself to the ssh group but another unix user who is not in the ssh group can still log in via ssh.

You may need to restart SSHD for the config file change to take effect (`/etc/init.d/sshd restart').  From my sshd_config man page:

```
     AllowGroups
             This keyword can be followed by a list of group name patterns,
             separated by spaces.  If specified, login is allowed only for
             users whose primary group or supplementary group list matches one
             of the patterns.  Only group names are valid; a numerical group
             ID is not recognized.  By default, login is allowed for all
             groups.  The allow/deny directives are processed in the following
             order: DenyUsers, AllowUsers, DenyGroups, and finally
             AllowGroups.
```

> **G1ZmO65 said:**
> Q: Am I likely to lock myself out if I mess with these or will it only affect new users?

It will only affect new users.

> **G1ZmO65 said:**
> Wondering if webmin uses its own method of creating users...

Probably.

-Derek

---

### Post by G1ZmO65 on 2008-08-22
Thanks Derek!

I did /etc/init.d/ssh restart and now the users which are not in the ssh group cannot log in via ssh :)

Another thing learned :)

Cheers

---

### Post by StevenChan on 2008-08-22
I am now encounting the same issue as Paul.

Unlike Paul, I have built my web server manually using CLI but not Webmin.

How can I stop non-sudoers(normal users) from remotely loggin on using SSH?

I have an idea but it seems too troublesome when adding new users...

The idea is...

edit /etc/passwd so as to give non-sudoers a "special" shell, nologin shell, in a bid to avoid them from accessing the server other than using FTP.

As it requires editing manually, it seems not a good way when i have many non-sudoers users.

Thanks a lot.

---

### Post by G1ZmO65 on 2008-08-23
Just on the webmin issue. Is it best to uninstall Webmin completely or just not use it and persevere with the CLI but leave Webmin installed for reference?

---

### Post by windependence on 2008-08-23
> **G1ZmO65 said:**
> Just on the webmin issue. Is it best to uninstall Webmin completely or just not use it and persevere with the CLI but leave Webmin installed for reference?

My opinion? take it off if you really want to force yourself to learn the CLI. That's what I did. I installed OpenBSD with NO X. Then I set up and ran my web site on that box. I had no choice but to use the CLI. It's been great ever since.

-Tim

---

### Post by G1ZmO65 on 2008-08-26
Excuse what is probably a silly question but 

The server is to be just a file server for about 20 users to access from windows xp machines. 
I want to put users into groups for access to some folders with some groups having readonly or no access and some having full r/w access.
Do I need Samba or can the shares be set without it?
If I do need Samba then can I configure it through the CLI?

Thanks again,

---

### Post by G1ZmO65 on 2008-08-26
Actually, I've answered my own question. 
Looks like I do need Samba

am reading the server guide now:

[https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html](https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html)

---

