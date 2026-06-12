---
title: "Ubuntu One - Stop Sharing"
date: 2010-05-07
forum: Ubuntu One (CLOSED)
---

### Post by gerowen on 2010-05-07
I was browsing some files and right clicked to "Copy" something and accidentally clicked "Sync with Ubuntu One".  Now my computer is trying to sync over 10GB of data to Ubuntu One.  How do I tell it to stop trying to sync that folder?

---

### Post by awam66 on 2010-05-07
> **marcusdean.adams said:**
> I was browsing some files and right clicked to "Copy" something and accidentally clicked "Sync with Ubuntu One".  Now my computer is trying to sync over 10GB of data to Ubuntu One.  How do I tell it to stop trying to sync that folder?

Right click on the folder and you will see the option "Stop syncing on Ubuntuone"

---

### Post by duanedesign on 2010-05-07
and if that does not work you can do this from the Terminal.

You can stop synchronizing a file by running the following command in a terminal session (Applications->Accessories->Terminal):

```
u1sdtool --list-folders
```

The first command should return something like this:

id=[COLOR="Red"]c4d1e6f9-931b-45c6-8fac-830390815242[/COLOR] subscribed=True path=/home/username/Documents

Copy the part that comes after "id=", which in the example above would be "[COLOR="Red"]c4d1e6f9-931b-45c6-8fac-830390815242[/COLOR]" and put it in the next command where it says [COLOR="Red"]ID-FROM-COMMAND-ABOVE[/COLOR].

```
u1sdtool --unsubscribe-folder=[COLOR="Red"]ID-FROM-COMMAND-ABOVE[/COLOR]
```

That should stop synchronizing that folder for you.

---

### Post by joshuahoover on 2010-05-11
> **duanedesign said:**
> 

Copy the part that comes after "id=", which in the example above would be "[COLOR=Red]c4d1e6f9-931b-45c6-8fac-830390815242[/COLOR]" and put it in the next command where it says [COLOR=Red]ID-FROM-COMMAND-ABOVE[/COLOR].

```
u1sdtool --unsubscribe-folder=[COLOR=Red]ID-FROM-COMMAND-ABOVE[/COLOR]
```That should stop synchronizing that folder for you.

And in this situation (where a folder was accidentally selected to sync) you probably want it completely deleted, in which case you would run the following command in a terminal session:

```
 u1sdtool --delete-folder=ID-FROM-COMMAND-ABOVE
```

That command will completely remove the folder and all files from the server.

Thank you,

Joshua

---

### Post by User Abuser on 2010-07-05
> ```
 u1sdtool --delete-folder=ID-FROM-COMMAND-ABOVE
```

That command will completely remove the folder and all files from the server.

Thank you,

Joshua
Just did it and no luck, my folder is still uploaded. execution doesnt seem to end, I had to break it.

---

