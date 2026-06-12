---
title: "GPG error, again."
date: 2005-10-18
forum: Repositories &amp; Backports
---

### Post by Emerzen on 2005-10-18
Hi all,

I've been getting the GPG error persistently...

1) I have removed all occurrences of "us" in the sources.list and this fixes it

2) I have run  sudo rm /var/lib/apt/lists/partial/*  and
                      sudo rm /var/lib/apt/lists/*
    which also fixes the problem.

However, the problem keeps recurring after so many reloads of the repositories, and I have to rerun #2 above to fix it.

Questions:
Is anyone else having the problem recur?
Am I missing updates because of this?
Does anyone know a permanent fix or what the cause may be?

---

### Post by matthew on 2005-10-18
I was having this problem and solved it by:

```
$ sudo cp /etc/apt/sources.list /etc/apt/sources.listbackup
$ sudo gedit /etc/apt/sources.list
``` 
and removing EVERYTHING in the file and saving an empty file

then

```
$ sudo apt-get update
``` 
to reset the cache

then reverse the process to restore my sources

```
$ sudo mv /etc/apt/sources.listbackup /etc/apt/sources.list
``` 
this overwrites the empty file with my original sources.list

```
$ sudo apt-get update
```

I haven't had a recurrence of the GPG error since I did this yesterday I don't have long-term effectiveness data, though.

---

### Post by Emerzen on 2005-10-18
Mathew, thank you very much.  I'm going to give it a try now.

---

### Post by Emerzen on 2005-10-18
Mathew...so far so good, thanks again!

---

### Post by Emerzen on 2005-10-18
Mathew, it came back after a reboot.  Any other ideas?

---

### Post by matthew on 2005-10-18
[quote=Emerzen]Mathew, it came back after a reboot.  Any other ideas?[/quote]
Hmm... I don't know why it has worked for me, even after multiple reboots, and not for you. It's a weird problem anyway and one that I am just trying to figure out myself. I am not sure what to try next. Anyone else have any ideas??

---

### Post by Dr. Nick on 2005-10-19
Havent tried that method, I was having trouble getting packages plus a few gpg errors until I removed "us" before every url in sources.list and re-ran apt-get update

---

### Post by joshmachine on 2005-10-19
I am getting the same error, and don't have any us archives in my sources.list.  even so, this is an automatic signing process that should work for both the main archive and mirrors as well.  

I have created a bug for this issue

[https://bugzilla.ubuntu.com/show_bug.cgi?id=18088](https://bugzilla.ubuntu.com/show_bug.cgi?id=18088)

you can add yourself to the cc list if you want to be kept apprised of the official response.

Cheers,
Josh

---

### Post by Emerzen on 2005-10-19
joshmachine...I filed a bug report on this a day ago.  The reply was that this is a repository problem and not a bug.

---

### Post by joshmachine on 2005-10-19
Thanks emerzen,

I'm sure it's a repository error.  It is however a bug in the distribution.  I'll see what response I get and see if I can track down whoever is in charge of repository maintenance.

Cheers,
Josh

---

### Post by Emerzen on 2005-10-19
Sounds good, I'll keep an eye on the thread!

---

### Post by gary79 on 2005-10-20
Hi guys,

I'm in the same boat, noithing I do seems to clear the GPG error. Oh well, I'm sure people will get it sorted.

It does leave one question for me...

If my apt-get does not work, will it down load broken/incomplete packets that would break my system? Should I hold off adding stuff via apt-get until it is fixed?

---

### Post by mjwood0 on 2005-10-20
I've watched these errors with some interest.  However, as of yet <tap on wood> I've not experienced any problems -- even with the "us" in the repo names.

Exactly what repos are giving you the errors?

---

### Post by Dr. Nick on 2005-10-20
[QUOTE=gary79]Hi guys,

I'm in the same boat, noithing I do seems to clear the GPG error. Oh well, I'm sure people will get it sorted.

It does leave one question for me...

If my apt-get does not work, will it down load broken/incomplete packets that would break my system? Should I hold off adding stuff via apt-get until it is fixed?[/QUOTE]

It should tell you that some files couldnt be retrieved and "ask to continue?" I wouldn't worry about adding programs, Most likely you would either get all the files needed or none. I might think twice about dist-upgrading to breezy as that may or may not work right.

---

