---
title: "editing the sql.conf file"
date: 2008-03-20
forum: Server Platforms
---

### Post by ade234uk on 2008-03-20
I need to edit the MySQL conf file.

I need to change the bind address from localhost to 127.0.0.1 so that I can connect to MySQL from a site that is on another server.

I dont like using nano through the terminal. Can I download the file using winscp, make my changes in Notepad upload it and restart MySQL through the terminal.

Thank you for your help.

---

### Post by cdenley on 2008-03-20
The file is owned by root. The only way you can overwrite it with scp is to either change the permissions on the file, or allow ssh connections with the root account and set a root password. I would recommend neither.

You could download it, edit locally, upload the copy somewhere else, then replace the original with the updated copy using sudo. Probably easier just to use nano.

---

### Post by ade234uk on 2008-03-20
I hava dedicated server cheap thing from Webfusion :confused: so I do have root access

I decided to edit the file using nano, but nano was not installed so I apt-get install nano

I then opended the mysql.cnf in nano and to my suprise MySQL is already set to bind to 127.0.0.1

I have again checked .php connection information on the other server. The db name, username and password are all correct but its still not outputting info from the database.

If I commented out the bind address totally in mysql.cnf file using nano would this work then?

I know the server will be left wide open, but this is doing my head in.

---

### Post by koenn on 2008-03-20
> **ade234uk said:**
> I need to edit the MySQL conf file.

I need to change the bind address from localhost to 127.0.0.1 so that I can connect to MySQL from a site that is on another server.


localhost = 127.0.0.1
to connect to mysql from another server, you need to bind it to the ip address of the server that runs mysql.

---

