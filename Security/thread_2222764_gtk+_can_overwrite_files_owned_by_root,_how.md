---
title: "gtk+ can overwrite files owned by root, how?"
date: 2014-05-08
forum: Security
---

### Post by thehighhat2 on 2014-05-08
Can anyone verify that that the /home/username/.local/share/recently-used.xbel file can be overwritten, even if owned by root?

I was trying to prevent the recently used file from being updated.  I tried symlinking to /dev/null, chmod 000, chattr +i, and setting ownership to root:root.

This file appears in my $HOME/.local/share folder.  I have removed all of the nasty bits of zeitgeist and the like from the system.  14.04 with Unity desktop.  Every time I open a file with nautilus, this recently-used.xbel gets updated.  I also noticed that firefox can read and write to this file.  

I dont like it so I tried to prevent.  The only thing that works is making the file immutable with chattr +i.

But the strange thing is, that every other strategy causing the file to be replaced with a new version.  *even if the file is owned by root:root and having ugo-rwx

So my question is, what unprivileged? desktop related process is running that has capability to overwrite a file owned by root and marked not writeable?

Try it:

  cat $HOME/.local/share/recently-used.xbel

    note the contents

  echo "some junk" > $HOME/.local/share/recently-used.xbel
  sudo chmod 000 $HOME/.local/share/recently-used.xbel
  sudo chown root:root $HOME/.local/share/recently-used.xbel
  
    now open any file using the file manager

  cat $HOME/.local/share/recently-used.xbel

    note the contents

---

### Post by papibe on 2014-05-08
Hi thehighhat2.

I believe your main concern goes beyond this question, but just concentrating in the permissions part:

The permissions to create and remove a file it is place on the directory that holds the file. If you are seeing new content in the file, my guess is that the DE is removing the file, and recreating it.

For instance:
```
$ mkdir temp
$ cd temp
~/temp$ ls -l
total 20
drwxr-xr-x  2 user user 4096 May  8 01:42 ./
drwxr-xr-x 67 user user 16384 May  8 01:42 ../

~/temp$ sudo touch dummy
[sudo] password for user: 

~/temp$ ll
total 20
drwxr-xr-x  2 user user  4096 May  8 01:43 ./
drwxr-xr-x 67 user user 16384 May  8 01:42 ../
-rw-r--r--  1 root  root      0 May  8 01:43 dummy

~/temp$ rm dummy 
rm: remove write-protected regular empty file `dummy'? y


~/temp$ ll
total 20
drwxr-xr-x  2 user user  4096 May  8 01:43 ./
drwxr-xr-x 67 user user 16384 May  8 01:42 ../

$
```
Does that help?
Regards.

---

### Post by HermanAB on 2014-05-08
Gnome is probably the culprit - it runs as root.  You can get more fine grained control over file accesses with ACLs and App Armor.

---

