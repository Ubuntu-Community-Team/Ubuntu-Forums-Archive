---
title: "keep harddisc synchronized with girlfriend?"
date: 2006-11-10
forum: The Cafe
---

### Post by weatherman on 2006-11-10
Hello everybody, I have the following problem.
My girlfriend and I live in two different houses. We both connect our pc to the internet through dsl and are using kubuntu. We also both have accounts on each others computer. Now what I would like is that our home folders are kept synchronized. How can I do this? The problem is that either her or my pc might be turned off during the day, so I guess something like setting up a server wouldn't work right? I know very little about this though.
Thanks for any hint.

---

### Post by sethmahoney on 2006-11-10
You could do like an FTP server, but using something like SSH would probably be easier.  Have a look on the forums and the wiki to see what you can do with SSH.

---

### Post by ciscosurfer on 2006-11-10
A great program for this is called [Unison]("http://www.cis.upenn.edu/%7Ebcpierce/unison/") and is a file-synchronization tool for *nix and Windows. You can grab it from the repos if you enable your universe repository.```
sudo aptitude install unison unison-gtk
```It will then be in your Internet menu.

---

### Post by PapaWiskas on 2006-11-10
The title of this post had me worried that the content was going to be scandalous or sordid...much to my disappointment it was not.  Ah well.....:p :p

---

### Post by .t. on 2006-11-10
^ Agreed with above :)

Look into rsync?

---

### Post by roderikk on 2006-11-10
> **.t. said:**
> ^ Agreed with above :)

Look into rsync?
It seems to me that Unison would be the tool to use since that allows for changes on both machines to be merged, even though I am really not sure on how this works. I have never used it but just did a search ( [unison]("http://www.cis.upenn.edu/~bcpierce/unison/index.html") ). Rsync is just a backup tool, or am I mistaken?

---

### Post by ciscosurfer on 2006-11-10
Unison is a more advanced tool.

---

### Post by .t. on 2006-11-10
Yeah; I'll look into that (I share my home directory across two systems, and use rsync for that; but it's inadequate).

---

### Post by weatherman on 2006-11-11
thank you very much for all your answers. Sorry to disappoint some hehe. I'll look into unison.

---

### Post by frup on 2006-11-11
In a situation with several thousand 3-10mb files, often being changed on both sites through out a day where an error in sync could potentially waste a weeks work OR an all out error (a mistake caused by the human having the wrong revision not a failure to backup) could cost lots, would this program work?

The current method is having all the files on a server and accessing them over a costly VPN connection when ever it is needed. obviously this means a minutes of downloading or so.. big waste of time over the day.

Files are AutoCAD .dwgs, Mistakes cause law suits.

---

### Post by Stew2 on 2006-11-11
Just get her to move in with you! :D :D :D 

(Just kidding)

Regards,
Stew2

---

