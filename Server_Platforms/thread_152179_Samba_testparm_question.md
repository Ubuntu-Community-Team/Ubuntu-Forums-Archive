---
title: "Samba testparm question"
date: 2006-03-29
forum: Server Platforms
---

### Post by jamesr on 2006-03-29
I hope this is the correct forum, if not redirecte to the correct forum.

I am trying to setup a an old system as a archival file server (console only) on a home intranet
I want to use a 2nd disk /samfiles as a common file transfer volume for the network. But I stuck at the very beginning
Samba is installed and working, I believe ??

smbstatus returns the header information but no information as yet.

I use a script```
sudo testparm -s /etc/samba/smb.conf_working /etc/samba/smb.conf
``` to test the test the smb.conf file but it returns an error 
-bash: /etc/samba/smb.conf: Permission denied

but I do not seem to able to change permissions.

Also another error but with bash 
command >file1 2>file2     output to file 1 and errors to file2
do not seem to work
any suggestions

---

### Post by Iowan on 2006-03-29
Please excuse my being dense, but what's the second filename (/etc/samba/smb.conf)? I had to look up the format for the testparm instruction (to see what **-s** means) and see the synopsis as: > testparm [-s] [-h] [-v] [-L <servername>] [-t <encoding>] {config filename} [hostname hostIP] It would appear (at first glance) that that file is being interpreted as a second instruction.

---

### Post by jamesr on 2006-03-29
Thanks for the quck reply but sorry I had typed the line incorrectly. The script came from the Samba site I believe.

```
sudo testparm -s /etc/samba/smb.conf_working > /etc/samba/smb.conf
```

That is why I would the other bash instruction to work as well so that I do not have typing errors

---

### Post by jamesr on 2006-03-30
The -s is used to strip the comments out of a file, to generate an abbreviated smb.conf file which runs faster. The error is a that I cannot write the output file because of permissions but I thought the use of sudo should get round the problem.

---

### Post by Iowan on 2006-03-30
This may be one of those awkward **sudo** instances I read about somewhere.  I don't remember the specifics, but the solution was to put braces, ticks, quotes, parentheses, or *something* around the entire command so the shell would interpret the entire line as a **sudo** instruction.

---

### Post by jamesr on 2006-03-30
Any suggestions as to where I may look for the information.

---

### Post by jamesr on 2006-03-30
Thanks for the clue, 
the correct syntax is ```
sudo testparm "-s /etc/samba/smb.conf_working > /etc/samba/smb.conf"
``` now just get it into a working script

---

