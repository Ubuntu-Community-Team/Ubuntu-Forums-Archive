---
title: "Allow ONE script to execute w/o Password"
date: 2011-05-12
forum: Security
---

### Post by Binary-Synapse on 2011-05-12
Hello.
 
I want to a allow a *single* bash script to run with root permissions (without me typing in the password).
 
The script is located in *[COLOR=red]/home/john/Documents/[/COLOR]*
Eventually the script, will try to execute a program which is located at *[COLOR=red]/home/john/Documents/programs[/COLOR]*
 
At the moment, my sudoers file is like this:
 
```
 
# This file MUST be edited with the &#8216;visudo&#8217; command as root.
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
# See the man page for details on how to write a sudoers file.
 
Defaults env_reset
 
# Host alias specification
 
# User alias specification
 
# Cmnd alias specification
 
# User privilege specification
root ALL = (ALL:ALL) ALL
 
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
 
# Allow members of group sudo to execute any command
%sudo ALL=(ALL:ALL) ALL
 
#includedir /etc/sudoers.d

```
 
And also, I've read it somewhere before but I can't remember... Can someone explain to me the line of code [COLOR=red]*root ALL = (ALL:ALL) ALL *[/COLOR][COLOR=black]present in the sudoers file?[/COLOR]
I mean what does each [COLOR=red]*ALL *[/COLOR][COLOR=black]specifically do?[/COLOR]
 
How do I change my sudoers file to accomplish running one single script file?
 
PS: I'm using **ubuntu 11.04** 32bit
 
Thank you

---

### Post by kerry_s on 2011-05-12
```
%sudo ALL=NOPASSWD: /path/to/script
```

"man sudoers" in terminal will tell you.

---

### Post by DaithiF on 2011-05-12
Hi, just to point out that /home/john/Documents will not be a good place to leave that script.  When you configure sudo to allow a script to be run as root without a password, you have to protect that script to prevent it being amended to do something you didn't intend.  e.g. someone could edit your script and replace your content with **sudo -i**
the result being that someone could then run the script as sudo, and get to a root prompt.

So,
1. the script needs to be owned by root and only writable by root, and
2. it needs to be in a directory which is only writeable by root (e.g. /usr/local/bin)

---

### Post by Binary-Synapse on 2011-05-12
> **kerry_s said:**
> ```
%sudo ALL=NOPASSWD: /path/to/script
```
 
"man sudoers" in terminal will tell you.
 
 
Hello.
 
Hum... I changed it like this and it didn't work!
When I run the terminal for "the first time" the command still asks me for john's password.
How do I know if john belongs to sudo?
 
 
```
 
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
 
# Host alias specification
 
# User alias specification
 
# Cmnd alias specification
 
# User privilege specification
root      ALL = (ALL:ALL) ALL
**[COLOR=red]%sudo   ALL=NOPASSWD: /home/john/Documents/[/COLOR]**
 
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
 
# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL
 
#includedir /etc/sudoers.d
 

```

---

### Post by DaithiF on 2011-05-12
**admin **is the group name you want i think.

[B]groups
[/B]will tell you what groups your user id is a member of

---

### Post by Binary-Synapse on 2011-05-12
Hello
 
If I type groups in terminal I get:
```
 
john adm dialout cdrom plugdev lpadmin admin sambashare

```
 
 
I'm sorry did you told me to modify it like this??
 
```
 
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
 
# Host alias specification
 
# User alias specification
 
# Cmnd alias specification
 
# User privilege specification
root      ALL = (ALL:ALL) ALL
%admin   ALL=NOPASSWD: /home/john/Documents/
 
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
 
# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL
 
#includedir /etc/sudoers.d

```
 
 
One question:
If I try to execute a command or script located inside a subdirectory of /home/john/Documents will it still execute without asking for a password?
 
Thank you for your help.

---

### Post by DaithiF on 2011-05-12
> **Binary-Synapse said:**
> 
I'm sorry did you told me to modify it like this??
 
yes
> 
One question:
If I try to execute a command or script located inside a subdirectory of /home/john/Documents will it still execute without asking for a password?
 
yes it will, but as per my post above it would not be good practice to leave it there.

---

### Post by kerry_s on 2011-05-12
go into users & groups, add yourself to the sudo group.

> %sudo   ALL=NOPASSWD: /home/john/Documents/

won't work, you ending at a folder. needs to be like this:

```
%sudo   ALL=NOPASSWD: /home/john/Documents/script.sh
```

```
%admin ALL=(ALL) ALL
```

will override the NOPASSWD, that's why it's better to use a different group, i don't mess with admin, cause if you screw up you lose root privileges, then you'll have to use recovery.

---

### Post by Binary-Synapse on 2011-05-12
Ah. OK.
 
Got it to work now.
 
If I put it like this it works without asking for a password:
 
```
 
# See the man page for details on how to write a sudoers file.
#
Defaults env_reset
 
# Host alias specification
 
# User alias specification
 
# Cmnd alias specification
 
# User privilege specification
root ALL=(ALL:ALL) ALL
 
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
 
# Allow members of group sudo to execute any command
%sudo ALL=(ALL:ALL) ALL
john ALL = NOPASSWD: /home/john/Documents/script.sh
 
#includedir /etc/sudoers.d

```
 
 
The problem is that the line [COLOR=red]john A[/COLOR][COLOR=red]LL = NOPASSWD: /home/john/Documents/script.sh[/COLOR] has to be **below** line [COLOR=red]%sudo ALL=(ALL:ALL) ALL[/COLOR]

[COLOR=black]So, if I now call the script like this:[/COLOR]
[COLOR=blue]sudo ./Documents/script.sh[/COLOR]
Everything is OK.
Script starts running imediately without asking for password and then finishes perfectly.
 
 
But if I start it like this:
[COLOR=#0000ff]./Documents/script.sh[/COLOR]
[COLOR=black]I still have to type the password for the script to work.[/COLOR]
 
How can I bypass that?
 
Thank you

---

### Post by Binary-Synapse on 2011-05-12
Because the purpose is to double-click the script's name so it starts running imediately.
 
Thank you.

---

### Post by kerry_s on 2011-05-12
you got 2 %sudo lines the last 1 is used.

```
%sudo ALL=(ALL:ALL) ALL
```

cancels out

```
%sudo ALL=NOPASSWD: /home/agostinho/Documents/myscript.sh
```

remove

```
%sudo ALL=(ALL:ALL) ALL
```

---

### Post by Binary-Synapse on 2011-05-12
> **kerry_s said:**
> you got 2 %sudo lines the last 1 is used.
 
```
%sudo ALL=(ALL:ALL) ALL
```
 
cancels out
 
```
%sudo ALL=NOPASSWD: /home/agostinho/Documents/myscript.sh
```
 
remove
 
```
%sudo ALL=(ALL:ALL) ALL
```
 
 
 
Ah. OK.
 
Got it to work now.
 
Thank you all.

---

