---
title: "Where to Store a Shared File on the Boot Disc"
date: 2017-02-06
forum: Server Platforms
---

### Post by damo12 on 2017-02-06
I am in the process of updating our headless Ubuntu server and will be changing to a much faster and more powerful one.

The server is used as a file server using Samba to share files with Windows machines in the office.  Most of the work in the office is carried out on an split Access database with the back end stored on a drive in the server which is separate from the "boot drive".  The database is currently mounted at:
```
/media/drive1/database
```

The new server will have an SSD as its "boot disc" and to speed up access to the database back end, I would like to place the back end on this disc and then share it using Samba.  The problem is, I'm not sure where I should place the database.  There does not seem to be a standard place to use.  Some guides suggest placing it at the top of the /home directory, others have suggested using /svr or /var but in each of those guides, someone else has pointed out problems with the suggestion.

Any help you can offer is greatly appreciated.

---

### Post by darkod on 2017-02-06
I would avoid using /home for anything like this. Those folders are not for file sharing or DB files.

Apart from that, you can basically put it anywhere you like. You can even create new custom folder, like /data or /databases and use that.

Just make sure the SSD has enough space for current DB size and future growth of course. That's a bigger problem than deciding on the path where to put it.

You can also use the /srv or /var as you mentioned. As for opposing views, there will always be such. Unless they managed to explain valid reasons NOT to use those locations, why wouldn't you? In fact, as far as I know /var/... is the default location for many database apps.

PS. Having said the above, using /var wouldn't work if you have separate disk mounted at /var, but I guess you already understand that. Linux mount points are very "fluid". The location /var is not always inside the / disk because you can mount other disk at /var. On many linux servers in fact /var is separate disk or partition and in such case the file created there might not be on the SSD OS disk. But in your case you are controlling your own server and if /var is inside / then no problem using it.

---

### Post by damo12 on 2017-02-06
Thanks darkod,

That all makes perfect sense.  With regards to storage space, this should not be an issue.  The current hard drive is 160Gb with about 8.5Gb actually in use.  The SSD is 120Gb and the database back end is less than 1Gb including local backups and associated files.

I think that I will locate in in /var/database as this seems to be the most suitable point.  All of the internal drives are mounted at /media with external USB drives mounted at /mnt (I now know that they should be the other way round) so I won't have any issues with mouth points.

---

