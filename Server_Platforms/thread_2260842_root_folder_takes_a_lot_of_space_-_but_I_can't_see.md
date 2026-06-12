---
title: "/root folder takes a lot of space - but I can't see where?"
date: 2015-01-14
forum: Server Platforms
---

### Post by mikael7 on 2015-01-14
Hello!

This is my first here at the forums. I have searched but found no results.

I have a headless server running Ubuntu 10.04.1 LTS. I wondered what took so much space on the server. I found out that /root folder contained ca 39 GB! I checked inside for clues, but got no. There are a couple of folders and files but nothing more than 1 GB. Where is the rest? Could it be hidden files? cache? I have tried with du -h and max-depth but it always lists all folders inside root folder and then /root itself with 39 GB next to it. 

I'd appreciate any help!

---

### Post by Dennis N on 2015-01-14
Just to be clear, are you talking about / or about /root containing the 39GB?

---

### Post by mikael7 on 2015-01-14
> **Dennis N said:**
> Just to be clear, are you talking about / or about /root containing the 39GB?

It's the folder named "root" that is placed in root :) Path would be /root

I guess it's the user folder for the user root.

---

### Post by deadflowr on 2015-01-14
Do you delete a lot?
Then sure, it's probably hidden folders, like .Trash
<snip>
maybe see if anything is in /root/.local/share/Trash.
If you tried deleting stuff while the root user, then it'll probably be in there.

---

### Post by darkod on 2015-01-14
There is also another command to try. If you already know /root is 39GB you need to look one level further.
```
du -sh /root
```

Not sure if that counts hidden files/folders. There is probably an option to add to -sh to display hidden too. You can always try 'man du'.

---

### Post by Habitual on 2015-01-14
/root may be mounted under /

```
df -hT
``` output please.

---

### Post by volkswagner on 2015-01-15
Please post output of the following:

```
sudo du -h /root --max-depth=1
```
```
sudo ls -alh /root
```
```
mount
```

---

### Post by mikael7 on 2015-01-15
I think I found i from command *du -h /root --max-depth=1*

38G	/root/.cache

What should I do about the cache?

---

### Post by TheFu on 2015-01-15
Delete it.

Also - stop running so many GUI programs as root. It is poor practice and defeats much of the built-in security of Linux,
Basically the correct number of GUI programs to run as root is 2
a) synaptic
b) some backup tool
Nothing else - definitely NOT email or browsers.

---

### Post by mikael7 on 2015-01-15
> **TheFu said:**
> Delete it.

Also - stop running so many GUI programs as root. It is poor practice and defeats much of the built-in security of Linux,
Basically the correct number of GUI programs to run as root is 2
a) synaptic
b) some backup tool
Nothing else - definitely NOT email or browsers.

It's a server, no GUI whatsoever. 

Delete it with rm?

---

### Post by TheFu on 2015-01-15
Look at the files below there. What caused them to be written?  Then you have a decision to make. Keep or delete.

Most non-GUI servers don't have anything there IME.  BTW, I just checked 6 servers here and that directory had 1 zero-length file, motd.legal-displayed.

---

### Post by mikael7 on 2015-01-15
[FONT=Menlo]38G	/root/.cache/duplicity

Backup software I don't use anymore[/FONT]

---

### Post by MAFoElffen on 2015-01-15
I'm thinking if you echo the environmental variables $TMPDIR, $TEMP or $TMP... that one of these is /root/.cache... Duplicity uses those Vars when it creates it's tempfile (unless it gets an --tempdir override parameter)

---

### Post by mikael7 on 2015-01-16
I'll echo these later. If I'm not using Duplicity any more, it should be no problems right to delete the cache? What if I use Duplicity (but don't know it), what might happen if I delete cache?

---

