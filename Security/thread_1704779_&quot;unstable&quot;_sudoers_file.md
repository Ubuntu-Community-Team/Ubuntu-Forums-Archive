---
title: "&quot;unstable&quot; sudoers file"
date: 2011-03-11
forum: Security
---

### Post by Borgond on 2011-03-11
Hi,

I am having problems on a server installation (9.10) with a kind of unstable sudoers file. Logging in as a user of group [FONT="Courier New"]admin[/FONT] allows only sometimes to issue sudo commands.

Most of the time I am getting a "not in sudoers file" errror.

```
$ sudo COMMAND
[sudo] password for USER:
USER is not in the sudoers file.  This incident will be reported.
```

USER is a member of group [FONT="Courier New"]admin[/FONT]

This is my sudoers file

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

After logging in/out a few times it sometimes works to issue sudo commands. But this unpredictable behavior is somehow unnerving :(

As a temporary fix I added USER as the last line in the sudoers file via visudo:

```
%USER ALL=(ALL) ALL
```

Now sudo works for this USER without problems (so far) - but I'd rather find a working solution without adding specific users to the sudoers file.

Did anybody encounter a similar problem?

Thanks in advance!

---

### Post by cariboo on 2011-03-11
The only difference I can see in you sudoers file, is this:

```
# %sudo ALL=NOPASSWD: ALL
```

in my default sudoers file on my server I have this:

```
%sudo ALL=(ALL) ALL
```

the above line allows anyone with admin privileges to use sudo. It looks like you are trying to allow admin functions without a password, which on an outward facing server is not a very good idea.

---

### Post by Borgond on 2011-03-14
actually the line in question is commented out - so it shouldn't be a problem.

```
# %sudo ALL=NOPASSWD: ALL
```

but I found the fact that I have two group files in /etc

```
# ls -la group*
-rw-r--r-- 1 root root 900 2011-02-23 13:29 group
-rw------- 1 root root 892 2011-02-23 13:28 group-
```

is this normal? - doing a web search I wasn't able to find something about a [FONT="Courier New"]group-[/FONT] file.

---

