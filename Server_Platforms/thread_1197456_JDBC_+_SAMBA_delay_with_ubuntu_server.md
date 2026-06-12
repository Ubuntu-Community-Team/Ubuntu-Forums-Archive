---
title: "JDBC + SAMBA delay with ubuntu server"
date: 2009-06-26
forum: Server Platforms
---

### Post by sexus6 on 2009-06-26
I have a ubuntu server 9.10 and a w2003 server.

At w2003 server there is a window app that works with Foxpro database. The database is located at one shared folder with windows sharing, and there is not possible to move that bd from here.

At Ubuntu I code some stuff with java that make sql querys to that database. Foxpro is not a "real" bd like mysql, and the only way to access remotely to the foxpro bd, is to mount the windows share in ubuntu. I mount this share with:
```
smbmount //windows2003/sharedfolder /mnt/database -o username=user,password=pass
```

At this way, I connect HXTT jdbc to the folder /mnt/database, and I can make sql querys with my java code. I use SQuirrell SQL too, a JAVA app that use jdbc thix HXTT driver to connect to the shared foxpro files from database.

At this point I have a problem. The inside data from database, not refresh correctly. If I add data to a table (with the windows app that use this database) , and I go to the ubuntu server and make a sql query (from my java program or SQLuirrell SQL)  sometimes fails and there is not returned the new data that I put. Seems that the data is not refresh correct. Sometimes works well, sometimes there is a delay.

I make some tests

- If I open directly the table with DBF VIEWER at windows, the data is here.
- If I close the program (tomcat or SQLuirrell) and open againt, there is no resulta. 
- If I close program, and smbumount the share, and smbmount and open the program again... WORKS.
- If I make a txt file at this shared folder, with the w2003, the txt file appears at samba share at ubuntu. If I modify this txt file, the hour and the mod is visible instantly.

With this tests I think that is samba problem...except the last test... 

I test to put at smb.conf:

refresh=1

and

socket options = TCP_NODELAY

But there is no result.

I'm desesperate... because I have no idea what's wrong. 
Please, some help

---

