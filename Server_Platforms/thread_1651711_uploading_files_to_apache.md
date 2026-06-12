---
title: "uploading files to apache"
date: 2010-12-23
forum: Server Platforms
---

### Post by Lordbyronxxiv on 2010-12-23
Hi All,
I have set up a very basic apache server to host my own website (have not set up sql or database or php yet) and I am trying to find out how to fpt or copy my website. I am creating the site in windows and need to know how to transfer it to the server, preferably into the /var/www folder directly.

-Mike

---

### Post by windependence on 2010-12-24
What works great for me and is secure is WinSCP. You can just drag and drop the files in Windoze and it even lets you edit permisssions and ownership. Great tool and free too.
 
-Tim

---

### Post by Lordbyronxxiv on 2010-12-24
I have tried to use both filezilla and that winSCP, the problem I am getting is that I don't have permission to write to that location, is there some way I can set it up to let me get root permissions for the transfer (kinda like sudo)?

---

### Post by windependence on 2010-12-24
Adding yourself to the wheel group might give you more juice.
 
-Tim

---

### Post by Lordbyronxxiv on 2010-12-25
> **windependence said:**
> Adding yourself to the wheel group might give you more juice.
 
-Tim

I appreciate the information- unfortunatly I am still pretty new to linux administration, so I don't know what you mean wheel group, what exactly are you refering to?

---

### Post by furlabs on 2010-12-25
wheel is the name of the group in Red Hat that gives you superuser access. In Ubuntu the default superuser group is admin.

Since you know about sudo, I assume you are already in the admin group. However, I don't believe winscp will allow you to sudo. What you need to do is winscp the files into your home directory, and then ssh into the server and use sudo to copy them into the /var/www directory.

---

### Post by Vegan on 2010-12-25
I use SAMBA then I can access my web folder easily and use Windows tools for editing web content.

My server does not even have a GUI. Not needed, everything is web administrated.

---

### Post by ask21900 on 2010-12-26
What are your permissions on /var/www?  If you have group write permissions this should do the trick:

```

sudo usermod -a -G www-data <username>

```

Otherwise, please post the output of
```
ls -l /var/www
```

---

