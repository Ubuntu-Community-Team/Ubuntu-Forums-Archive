---
title: "Ran out of space?"
date: 2006-08-22
forum: Server Platforms
---

### Post by psychomonkey on 2006-08-22
This is going to sound like such a noob question. I have an 80GB hard drive. The actual "/" partition is 68GB in size. I recently got a message while using apt-get to install a program that there wasn't enought space and sure enough, i had 33MB of free space. 

Now this is odd because I don't have the GUI installed and am only using this for VHCS (Virtual Hosting) Software with 1 domain currently.

My question is this: Is there a way to tell what programs are taking up the most space or is there a way to clear out old cached info that might be taking up my free space? I realize I'm thinking like a Windows user, but there must be someway to figure out or "clean house" on old data that's not being used.

Please help.

---

### Post by moma on 2006-08-22
1) Report  disk free (df)
$ [COLOR="Green"]df[/COLOR]
or 
$ [COLOR="Green"]df -h [/COLOR]

2) Search all files that are over 10MB in size 
The search starts from root-filesystem (/) so it will take some time to complete.
$ [COLOR="Green"]sudo find / -size +10M -ls[/COLOR]

/media directory contains other, mounted file systems. You can exclude (prune) them  
$ [COLOR="Green"]sudo find / -path /media -prune -o -size +10M  -ls[/COLOR]

3) "Baobab" disk analyzer would be helpful but it cannot be installed in Ububtu 6.06 (Dapper) very easily because of library requirements.  Baobab is included in Edgy Eft CD (next buntu).
[http://www.marzocca.net/linux/baobab.html](http://www.marzocca.net/linux/baobab.html)

[COLOR="Red"]EDIT:[/COLOR]  The Baobab's webpage says:  """Baobab is currently in Debian unstable/testing and Ubuntu Dapper repositories. These users can just apt-get it. (please check latest version)"""
-------------

4) LiveCD: Boot up with your Ubuntu CD.
And use "gparted" to resize the existing partitions.
$ [COLOR="Green"]sudo -s [/COLOR]
# [COLOR="Green"]gparted [/COLOR]

---

### Post by psychomonkey on 2006-08-22
Thanks for the info. Do you know if Baobab can be used without the GUI?

Right now, my server runs with just the console.

---

### Post by moma on 2006-08-22
No. 
AFAIK, Baobab is GUI based.
You can probably run it from a LiveCD (eg. Edgy Eft pre release).

Use "find" to filter out suspiciously large files.

If you are running a server then check /var/log/ carefully.

$ [COLOR="SeaGreen"]du -h /var/log[/COLOR]

---

### Post by psychomonkey on 2006-08-22
You are a life saver. :D

I just recently installed Gnump3d and it turns out there is a log file in /var/log/gnump3d that is 64GB!

Next question. The log file is labled "error.log.1". Does anyone know if this file is necessary or if I can deleted it? I tried to open the file to view it but it says "File to large, failed to open".

Any additional help would be appreciated.

---

### Post by moma on 2006-08-23
You can delete or truncate it because it is simply an error log file.

$ [COLOR="Green"]cd /var/log/gnump3d[/COLOR]   # cd to log directory

$ [COLOR="Green"]echo ""  | sudo tee  error.log.1[/COLOR]
or
$ [COLOR="Green"]echo ""  | sudo tee  error.log.*[/COLOR]

Check also Gnump3d's configuration.
Set Gnump3d to truncate log files at startup. 
Look for  "truncate_log_files" field.

Read: [http://www.gnu.org/software/gnump3d/config.html#Config](http://www.gnu.org/software/gnump3d/config.html#Config)

---

### Post by psychomonkey on 2006-08-23
Thanks a bunch. I ended up deleting it, but I'll keep an eye on it in the future to see if this happens again. If so, I will do as you suggested.

Thanks again.

---

