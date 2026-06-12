---
title: "How does it know which way to send files?"
date: 2009-07-13
forum: Ubuntu One (CLOSED)
---

### Post by RealG187 on 2009-07-13
So how does Ubuntu One know which way to go?

For example.

I have file 1 on my laptop and on the server.

I delete files 1 from my laptop. I am sure Ubuntu One would delete file 1 from the server too, but how does it know now to download file 1 to the computer? Like what if file 1 was uploaded from another computer and that's the reason that it's on the server but not the computer?

Likewise I make file 2 on my Laptop, Ubuntu One will upload it to the server. How does Ubuntu One know to upload it and not delete it, like lets say file 2 was on the server, but deleted from another computer in that case it would be deleted on my Laptop.

So if a file exists only on the computer there are two options:
* Upload it so it exists on the server too
* Delete it so it exists nowhere

And if a file exists only on the server there are two options:
* Download it to the computer to it exists there too
* Delete it from the server so it exists no where.

How does it know?


Say my /home/Ubuntu One folder got cleared out by accident, would Ubuntu one download all the files to it, or delete them on the server too?

---

### Post by chriskin on 2009-07-15
wouldn't that be about which one was modified last? ...

---

### Post by lucio.torre on 2009-07-15
Hi!

syncdaemon (the part of ubuntu one that synchronizes files against the server) keeps some metadata on each file it knows about and reacts to events that come from the server or the filesystem (inotify).

This is hugue state machine that defines what action to take.

Files can have metadata asociated or not. If they do, they can be files or directories. And they keep track of the hash the files has locally and on the server side. We also have a flag for trying to upload. With this information we sintethize a state for the file that can be:
- NONE: the file is in sync. (ie, hashes match)
- SERVER: the server has the newer version of the file (hashes dont match and we are trying to download it)
- LOCAL: we have the latests version (hashes dont match and we are not trying to download it, ergo, we are trying to upload it)

So, for example, talking about delete. When you delete a file in your system syncdaemon will receive a message from INOTIFY that will be transformed into the FS_FILE_DELETE message. Our big state machine will look for the file and its state in the metadata and look for the transition that it should execute when the FS_FILE_DELETE event comes and the file is in this state. Then call that function.

In this case, it will queue a command to delete the file in the server and delete the local metadata. The server will eventually reply: SV_FILE_DELETE_OK or ERROR, and the logic continues each way.

If the file was deleted on another computer, syncdaemon will just see a SV_HASH_NEW for the parent directory when the file is deleted. When comparing the directory with the server directory, syncdamon will send an SV_FILE_DELETED event. This will make the state machine call a function that deletes the file locally but does not send any commands to the server.

If you want to know what happens in each case, you can take a look at u1fsfsm.ods and sync.py in the ubuntuone-client code.

---

### Post by RealG187 on 2009-07-15
That is really confusing.

---

### Post by zekopeko on 2009-07-16
> **RealG187 said:**
> That is really confusing.

that's because you are a civilian not a programmer :)

---

### Post by RealG187 on 2009-07-16
I am not a programmer. I know lots about computers but almost nothing about programming (I know batch and HTML, they may or may not be considered programming codes but they are close)

---

### Post by Maheriano on 2009-07-16
Never heard of Ubuntu One, is this some sort of synchronizing application with a remote server?

---

### Post by chriskin on 2009-07-16
you know that you are posting at the "ubuntu one" section of these forums right? :P

there is a thread on the top of this subforum, there is wikipedia and google, but anyway : ubuntu one is just like dropbox , at least yet. (a LOT buggier , but works the same)

---

### Post by RealG187 on 2009-07-16
> **Maheriano said:**
> Never heard of Ubuntu One, is this some sort of synchronizing application with a remote server?Basically

---

### Post by lucio.torre on 2009-07-17
> **RealG187 said:**
> I am not a programmer. I know lots about computers but almost nothing about programming (I know batch and HTML, they may or may not be considered programming codes but they are close)
Well, the synchronization part is complicated, yes. Id like to believe that our state machine "agile formal" approach makes all this complication manageable.

---

