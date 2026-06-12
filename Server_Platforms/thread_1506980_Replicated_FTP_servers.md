---
title: "Replicated FTP servers"
date: 2010-06-11
forum: Server Platforms
---

### Post by ssheikh on 2010-06-11
Hello all,
 
I am looking for a way to setup replicated FTP servers. The environment is:

[LIST=1]
[*]Three offices. In VA, TX, and CA.
[*]company uses FTP to share videos (600 MB to 4GB in size) with its customers and contractors.
[*]Each office has an FTP server that local users/internal staff in that office will use to upload and fetch files from.
[*]The way DNS are aliases are setup, [ftp.company.com]("ftp://ftp.company.com") points to the local DNS server for internal users.
[*]For the customers of the company, [ftp.company.com]("ftp://ftp.company.com") points to the server in TX.
[/LIST]Here is what I would like to achieve is:

[LIST=1]
[*]All ftp servers be mirror replicas of each other.
[*]Should be able to upload a file to any FTP server and it should replicate to the other FTP servers.
[*]While a file is getting replicated to a server, it should not be available for download from that server.
[/LIST]For the FTP server itself, my preference is to use vsftp unless some other free package provides such replication capabilities internally. 
 
Does anyone know of a replication package or script that can do this?
 
Thanks,
 
Shahid.

---

### Post by Ryan Dwyer on 2010-06-11
You can probably use rsync to do this, but I've never used it.

---

### Post by HermanAB on 2010-06-11
Rsync is your friend.

NFS version 4 also has a replication feature.

---

### Post by ssheikh on 2010-06-11
Yes, rsync can be made to work. But the amount of scripting required to get a full 3 way synchronization to work is something I was hoping to avoid. 
 
I have to make this as bullet proof as possible. In all the solutions that had been implemented in a past, users were always trying to grab files from their local ftp server before the replication had completed. 
 
When I was researching rsync, I came across tsync which seems like a very good fit in my case, again with the exception of not being able to mask the file until the sync was complete. But unfortunately, tsync seems to be dead. Compiling is requires some old libraries that I have not been able to track down yet.
 
NFSv4 is promising. But the complexity level on it is high. And I am not sure how well it will work over WAN links. Not to mention, I have not seen any working examples of it. My connection between the sites is 10 mbps and there is fair amount of other traffic running on it.
 
I looked at other distributed file systems as well. AFS and GlusterFS. Again, I'm not sure I want to go the route of replica supporting file system when a file based replication should suffice. And then there is the complexity factor with those packages.
 
Right now the two two solutions that seem the most appealing are:
[LIST=1]
[*]lftp
[*]ftpsync.pl
[/LIST]Thanks for the replies so far. Please keep the suggestions coming.

---

### Post by HermanAB on 2010-06-11
Rsync is hard to beat and scripting it is a one liner.  The main advantage over FTP is speed.  Rsync only sends changed blocks.  FTP will always send the whole file even if only one bit changed.

---

### Post by ssheikh on 2010-06-11
I do use rsync for variety of other things but in this case rsync doesn't buy me much over regular ftp. The files on the ftp server that I want to sync are never changed. They are always either added or removed.
 
Also, i was not very successful in creating an rsync script that would do a transparent 3 way full cross mesh replication in which any file could be added or removed from any one of the servers and that would get synchronized to the other server. So if you have any pointers on how to set that up, I would like to know. 
 
Really, tsync seems to be way better in doing that than rsync. Here is a description of tsync: [http://tsyncd.sourceforge.net/#intro](http://tsyncd.sourceforge.net/#intro)

---

### Post by HermanAB on 2010-06-11
To sync between 3 servers, you would need a few more lines in your script, but basically, you first synch two machines, then the third one - not all at the same time.

There is also a program called 'unison' which is similar to 'rsync' and which does a bidirectional sync.

---

### Post by ssheikh on 2010-06-11
That is what I am trying to do - sync all at the same time if possible.
 
I have looked at Unisen as well. That is great for syncing files between two devices. But when trying to sync between N devices, you have to run N-1 instances of Unisen.

---

### Post by edenCC on 2010-06-12
If I were you, I would choose Rsync as they are mostly large files. Otherwise, ionotify should be better.

For the third requirement, I'd suggest you please some tricks on rsync.

For example, it takes long time for syncing from server A to server B, but it takes only 1-2 seconds for moving file A from /dir1 to /dir2 (supposing /dir1 and /dir2 are in the same disk partition).

---

### Post by HermanAB on 2010-06-12
"to sync between N devices, you have to run N-1 instances of Unisen"

So?

You can put all N-1 lines in a single Bash script.  Three servers, two lines - I think you are overestimating the complexity for some obscure reason.

---

### Post by ssheikh on 2010-06-12
rsync in combination with inotify may work. 
 
Main problem with rsync running as a recurring job is file deletes. A deleted file on one server gets rsynced back from the other server if rsync runs in that direction first. 
 
inotify triggering rsync to prune the remote directory for deleted files would probably work.
 
The other problem is complaints from users that the files they download are corrupt most of the time. That is because a customer calls and says they have uploaded a file and the users try to download the file without giving enough time for it to finish rsyncing.
 
For that I just started looking at proftpd. It apparently writes to a temporary file and then renames the temp file when the transfer is complete.
 
That in combination with inotify which triggers an ftp to the two remote servers will work. Want to use ftp instead of rsync to keep the users at the remote site to start downloading as soon as rsync starts.
 
That leaves rsync.

---

