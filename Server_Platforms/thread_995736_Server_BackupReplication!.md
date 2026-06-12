---
title: "Server Backup/Replication?!"
date: 2008-11-28
forum: Server Platforms
---

### Post by matey3 on 2008-11-28
Hello I am pretty new in Ubuntu so please bear with me...(or is it bare with me?? lol I am new to inglish too) ;)
j/k...
but really I need to backup my A server (the production server running Ubuntu 7.04 Feisty) into B server (my backup w/same OS) as quick as possible. 
 I heard using **rsync** would be one way to do it but I dont want to make a mistake and write over the Production server's files !

Can anyone help please (any methods, links etc.) would be appreciated!

Oh our A (Production) server is off site (miles away) but the B (backup) server is right here and I can ssh to both of them no problem.

BTW The A server has 3 Xen guest servers running off of it and I used xen and lvm to create replicas under the backup server cuz I though you could not really copy over Virtual machines?! I am not so sure though.

Again, any hints or links would be appreciated.
Thanks!

---

### Post by m_l17 on 2008-11-28
List of backup solutions:

[http://www.debianhelp.co.uk/backup.htm]("http://www.debianhelp.co.uk/backup.htm")

I like rsnapshot: 

[http://www.rsnapshot.org/]("http://www.rsnapshot.org/")

How to:

[http://www.rsnapshot.org/howto/](http://www.rsnapshot.org/howto/)

[http://www.debianhelp.co.uk/rsnapshot.htm]("http://www.debianhelp.co.uk/rsnapshot.htm")

---

### Post by andguent on 2008-11-29
matey3, did you figure out your problem? If not can you give more details on what files you are trying to backup? 

* Is this an entire partition to get backed up, or just a couple directories?
* Can either of your servers ssh directly to the other?  It doesn't matter which way, just one way is fine.
* What speed connection is between your two servers? Internet speeds I assume?
* Do you have a spare external drive?

I personally use rsync very heavily for these types of things. It is smart in how it resumes file copying. Do WATCH OUT that it gets weird when you give a directory that ends in a forward slash '/' as that means to go into that directory rather then use it directly.

The next nice feature about rsync is that if you can ssh to the remote box, you usually can rsync too. Rsync can copy files right through the ssh port & software.

Rsync command examples:
```

rsync -va --dry-run RemoteServerIP:/directory/to/backup /local/directory/destination
rsync -va --dry-run /local/directory/to/backup RemoteServerIP:/remote/dir/destination
rsync -va --dry-run /local/directory/to/backup /external/hard/drive/destination

```

The --dry-run flag means "don't make any actual changes, just show me what you would copy". You need to run rsync without that to actually copy files. The -va switches simply mean 'show me what you are doing' (Verbose) and 'maintain all details about the files that you can' (Archive). See 'man rsync' for more info then you wanted to know.

Hopefully you got your challenges all straitened out already. Please post back and mark the thread solved if you did.

---

### Post by matey3 on 2008-12-01
> **m_l17 said:**
> List of backup solutions:

[http://www.debianhelp.co.uk/backup.htm]("http://www.debianhelp.co.uk/backup.htm")

I like rsnapshot: 

[http://www.rsnapshot.org/]("http://www.rsnapshot.org/")

How to:

[http://www.rsnapshot.org/howto/](http://www.rsnapshot.org/howto/)

[http://www.debianhelp.co.uk/rsnapshot.htm]("http://www.debianhelp.co.uk/rsnapshot.htm")

sorry for late reply, but Thank You for the links:
Regards;

---

### Post by matey3 on 2008-12-01
> **andguent said:**
> matey3, did you figure out your problem? If not can you give more details on what files you are trying to backup? 

* Is this an entire partition to get backed up, or just a couple directories?
* Can either of your servers ssh directly to the other?  It doesn't matter which way, just one way is fine.
* What speed connection is between your two servers? Internet speeds I assume?
* Do you have a spare external drive?

I personally use rsync very heavily for these types of things. It is smart in how it resumes file copying. Do WATCH OUT that it gets weird when you give a directory that ends in a forward slash '/' as that means to go into that directory rather then use it directly.

The next nice feature about rsync is that if you can ssh to the remote box, you usually can rsync too. Rsync can copy files right through the ssh port & software.

Rsync command examples:
```

rsync -va --dry-run RemoteServerIP:/directory/to/backup /local/directory/destination
rsync -va --dry-run /local/directory/to/backup RemoteServerIP:/remote/dir/destination
rsync -va --dry-run /local/directory/to/backup /external/hard/drive/destination

```

The --dry-run flag means "don't make any actual changes, just show me what you would copy". You need to run rsync without that to actually copy files. The -va switches simply mean 'show me what you are doing' (Verbose) and 'maintain all details about the files that you can' (Archive). See 'man rsync' for more info then you wanted to know.

Hopefully you got your challenges all straitened out already. Please post back and mark the thread solved if you did.


Thanks very much for the reply:
No I am still working on it, made a little progress but cant take big chances on the real server...

Yes I would like to copy over the entire server so if the main server fails, the backup can take over (main thing is so that our web page would never go down for a long time).

And Yes I used ssh-keygen to setup ssh between the 2 servers without having to log in.

And the speed is not really that great (it is a problem some times here in this part of this country)!

And I can & will get an external HDD but it will be a USB ( and not scsi).Or I could use my personal one (I sent my 500GB back to WD (WesternDigital), for repair but they sent me a 750 GB back, clean!) ?

But I really do appreciate you posting this message I will copy and paste it to a local gedit for later, lots of useful information. 

Thank You Very Much Indeed!

---

### Post by andguent on 2008-12-01
If you are looking for a complete server clone option, the link below has some good info. Admittedly it is working with cloning a real server into a virtual server, so it is not 100% what you want. However I have successfully taken pieces of the guide and used it clone an old red hat server from failing hardware onto new hardware. My old baby lives on in a server twice as fast and three times as small.

[http://www.linuxjournal.com/article/9942](http://www.linuxjournal.com/article/9942)

If all you care about is the web server portions, then backup all of /etc, and all of /var/www (or wherever your web files sit). /etc/apache* is probably where your apache configuration is, but I always like to grab all of /etc just incase.

---

### Post by matey3 on 2008-12-03
> **andguent said:**
> If you are looking for a complete server clone option, the link below has some good info. Admittedly it is working with cloning a real server into a virtual server, so it is not 100% what you want. However I have successfully taken pieces of the guide and used it clone an old red hat server from failing hardware onto new hardware. My old baby lives on in a server twice as fast and three times as small.

[http://www.linuxjournal.com/article/9942](http://www.linuxjournal.com/article/9942)

If all you care about is the web server portions, then backup all of /etc, and all of /var/www (or wherever your web files sit). /etc/apache* is probably where your apache configuration is, but I always like to grab all of /etc just incase.

Oh yeah that is what I was looking for..
Thank you very much indeed andguent for the link!It's got every thing I needed...

:idea:

---

### Post by HermanAB on 2008-12-03
"Rsync is your friend."

Rsync also has a BW parameter that allows you to slow it down, so it doesn't gobble up all available bandwidth while it is running.  Do read the man page.

Cheers,

H.

---

