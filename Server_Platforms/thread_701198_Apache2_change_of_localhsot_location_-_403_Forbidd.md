---
title: "Apache2 change of localhsot location - 403 Forbidden Error"
date: 2008-02-19
forum: Server Platforms
---

### Post by alingham on 2008-02-19
Hi Everyone!

I've got a bit of a humdinger - searching the web for days for a solution. Lots of similar problems but none are the same!

I've just installed Apache2 on my Ubuntu 7.10 Gutsy.

I edited /etc/apache2/sites-enabled/000-default and changed the server locations from /var/www/ to a directory in my home folder. (We'll call is home/alingham/Websites/)

I need this because that is a folder linking to my Windows partition on which all my websites from a previous life in Windows are...

Upon restarting Apache, I go to [http://localhost/](http://localhost/) and it comes up with a 403 Forbidden Error, You don't have permission to access / on this server.

I've chmodded the directory home/alingham/Websites to no avail...

---

### Post by faulkes on 2008-02-19
There are a number of possible reasons for this you receiving a 403 message.

The most likely culprit being that windows tends to end html files with the extension of ".htm" which is not likely a recognized directory indiex.

There is also the consideration that windows->unix file conversion hasn't taken place and that windows files tend to have ^M's at the end of each line.

If the files in the directory you have specified do have the ".htm" extension, you would likely have to add the DirectoryIndex directive to your 000-default file.

```

DirectoryIndex index.html index.htm

```

I would also make sure that apache has proper permissions to read from the directory you are pointing (as you say it is on a windows partition).

Faulkes

---

### Post by alingham on 2008-02-19
Most of the files i'm using are PHP, and this has been added to the Directory Index. 
I've had this setup working before with Kubuntu 7.04 and 7.10... 
The windows partition is mounted using ntfs-3g so it is able to read/write (and I have tried this. There's no windows>unix conversions going on....

---

### Post by alingham on 2008-02-19
Any other suggestions??? I've read other solutions where people have just given up and shifted their files to /var/www...
This isn't really good enough as I have left the majority of the space in the partition on the Windows side of things, so I want as many of my documents there, rather than on the Linux partition.

All suggestions or solutions are most welcome. Thank you in advance.

---

### Post by faulkes on 2008-02-20
> **alingham said:**
> Most of the files i'm using are PHP, and this has been added to the Directory Index. 
I've had this setup working before with Kubuntu 7.04 and 7.10... 
The windows partition is mounted using ntfs-3g so it is able to read/write (and I have tried this. There's no windows>unix conversions going on....

Windows files, when created have a different format than if you created them on a unix machine.

i.e. create a file on windows, then vi the same file on unix.

You will notice that the end of each line typically has a ^M

I'm not saying that is the issue, but it is one thing to check out.

Faulkes

---

### Post by alingham on 2008-02-20
I've been able to do this before, setup exactly the same just in Kubuntu 7.10 instead of Ubuntu.
Didn't have any trouble with it being Windows files then...

---

