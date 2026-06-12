---
title: "Moving files no longer displayed"
date: 2014-10-14
forum: Server Platforms
---

### Post by nathanhawthorne12 on 2014-10-14
Morning.

I had a list of files in a folder under /var/lib which were owned by a user.  To move these files to a samba share i made the owner nobody:nogroup.  I then moved the files to /srv/samba/Share/ which is also owned by nobody:nogroup.  now when i view the /srv/samba/Share under windows the files do not show, although they do show when i cd to the directory and ls -l

---

### Post by volkswagner on 2014-10-14
What command did you use to move the files?

Double check your command history using "less" program.  You can view your commands by logging in as the user you
ran move commands with then run:
```
less ~/.bash_history
```

While viewing inside less, you can search for strings by first typing the slash and your string, so if file name
was file.txt you'd type the following in less.
```
/file.txt
```

or simply

```
/Share
```

Do realize the file system is case sensitive, perhaps you moved files to "/srv/samba/share"???

You can also search the file system for the missing files to see where they landed.

```
find / -name file.txt
```
The above will search entire file system, if your certain they are in /srv you can run the following for a quicker result.
```
find /srv -name file.txt
```

---

### Post by nathanhawthorne12 on 2014-10-14
Since files were owned by another user  sudo mv /var/lib/*** /srv/samba/Share I then changed ownership sudo chown -R nobody:nogroup ****.  

Problem is now solved, it took a while 20 minutes but eventually showed up under windows, don't know why the delay was their as they DID show under /srv/samba/Share when I ssh'd to the machine immediately after moving them.

---

