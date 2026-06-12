---
title: "Sharing Home Directories"
date: 2010-05-11
forum: Server Platforms
---

### Post by kentish on 2010-05-11
Hello 

I was wondering if someone could give me some advice. I am running an ubuntu server and three ubuntu lucid machines at home with three different users using the machines - myself, wife and daughter.

I would like keep all the users files in the home directories on server and share them out to the three machines - 2 desktop PC and one laptop. 

As far as I have read - mostly in the forums I have three possibly four(?) options.

1) LDAP - difficult to set and a bit excessive for three users
2) NFS and NIS - I understand the NIS is insecure but easy to set up
3) SAMBA - I know I can export home directories to a windows box, so I guess that I could do the same on ubuntu.
4) RSYNC - regularly sync the files back to the server - this could be the easiest - i guess.

At present all the machines have a fresh install of Ubuntu on them 

Any suggestions or comment would be appreciated. I am happy to go off and read further just need someone to point me in the right direction.

Thank You


Kentish

---

### Post by terazen on 2010-05-11
Depending on the size of the files that you want to share, you could also try UbuntuOne or Dropbox.  For both I believe you get 2GB of space for free on their servers.  Other than that I'd say samba.

The advantage to samba is that it's internal to your home so it would have faster transfer speeds and you would have a lot more storage space.  The advantage to UbuntuOne and Dropbox (also a couple others) is that you would have access to your files on your laptop from anywhere in the world with an internet connection.  Dropbox works for windows and linux.

---

### Post by kentish on 2010-05-11
Thanks Terazen

As for the amount of files - about 10 gig of music for my daughter and 50 gig for me. 

So it looks like I will give Samba ago, I've already been using it to share video files with everyone but didn't think about the home directories.

Cheers

Kentish

---

### Post by Iowan on 2010-05-12
For an all-Ubuntu network, [NFS]("http://ubuntuforums.org/showthread.php?t=249889") should work.

---

### Post by kentish on 2010-05-13
Wouldn't I need to to NIS to authenticate the home directories shares?

---

### Post by kentish on 2010-05-15
Well after some testing and some mistakes. I have found out that I don't really need to share the home directories! A sensible option would be to syncronize them!

Look like I have a couple of options - as usual!

Unison - [http://www.ubuntugeek.com/unison-file-synchronization-tool.html]("http://www.ubuntugeek.com/unison-file-synchronization-tool.html")
Rsync - [https://help.ubuntu.com/community/rsync]("https://help.ubuntu.com/community/rsync")

---

### Post by HermanAB on 2010-05-15
Howdy,

If you only have a handful of users, then you do not need a directory service like NIS or whatnot.  Al you need to do is ensure that each user has account on each machine with the exact same UID and GID.  Ferinstance, the user IDs are by default assigned starting at 500.  

You will probably be OK since you installed the machines and will be 500 everywhere by default.  If you create the second account for your wife on a machine, then she will be 501 and and your daughter 502.  Make sure that, that sequence is the same everywhere.  Problems will arise when your wife is 501 on one machine and 502 (or whatever else) on another.

If you keep the UIDs and GIDs under control manually, then NFS will work transparently over all the machines.

---

### Post by kentish on 2010-05-17
Thanks for that info.

---

