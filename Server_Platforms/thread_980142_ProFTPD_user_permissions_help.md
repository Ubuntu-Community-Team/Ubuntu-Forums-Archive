---
title: "ProFTPD user permissions help"
date: 2008-11-12
forum: Server Platforms
---

### Post by cwsterling on 2008-11-12
I am having some problems here and haven't been able to figure out what I need to do. I have a version of ubuntu server running and installed proftpd on it. I have it enabled so users are directed to /var/www where apache2's root directory is. The only problem that I am having is that when a user uploads or creates a directory, the only apache can edit files inside the folder is if I login to ssh and chown the folder and all the files to www-data.

I have tried adding the user to the www-data group and I don't think that made much of a difference.

So to basically go back to the beginning, I removed all users from the www-data and ftpusers so I can just start over with some good directions.

So if anybody has any suggestions, can you point me towards them please.

Chris

---

### Post by martien on 2008-11-12
> **cwsterling said:**
> I am having some problems here and haven't been able to figure out what I need to do. I have a version of ubuntu server running and installed proftpd on it. I have it enabled so users are directed to /var/www where apache2's root directory is. The only problem that I am having is that when a user uploads or creates a directory, the only apache can edit files inside the folder is if I login to ssh and chown the folder and all the files to www-data.

I have tried adding the user to the www-data group and I don't think that made much of a difference.

So to basically go back to the beginning, I removed all users from the www-data and ftpusers so I can just start over with some good directions.

So if anybody has any suggestions, can you point me towards them please.

Chris
Make sure that when you add the user to the www-data group you set the chmod for the folder with read permissions for the group part.

---

### Post by cwsterling on 2008-11-12
Well, I guess I was going the wrong way about it. Thanks

---

### Post by oneloveamaru on 2008-11-12
THere are a couple ways you can go about it. Add www-data to the users groups who are accessing it, set up special permissions on the folder so that any file created, is created with the group www-data or run a cron job to change the permissions every once in a while.

---

### Post by cwsterling on 2008-11-13
ok I need a little bit more help.

When I do an ls -l on a directory that i created I get this

```

drwxrwxr-x 11 cwsterling www-data  4096 2008-11-11 21:50 administrator

```
(With the permissions like that I get 403 Forbidden when I try to access the folder online)

I tried a little more editing and got this

```

drwxrwxr-x 11 cwsterling cwsterling  4096 2008-11-11 21:50 administrator

```
(I can now view the site, just not sure if I can create stuff)


If it looks like that can www-data write to the folder even though I create the folder in ftp

Just so you can see what I did, here is the www-data goup
```

www-data:x:33:justin,bcm,www-data,cwsterling

```

and then here is the cwsterling group

```

cwsterling:x:1001:www-data

```

If the answer is adding the user www-data to the usergroup for the username, is there any way around that?

Chris

---

### Post by oneloveamaru on 2008-11-13
can you verify apache is running as www-data? There are a lot of variables with permissions and it's hard to tell what I would do exactly. Go read up on Linux permissions and get a good understanding of how they work.

---

### Post by cwsterling on 2008-11-13
I blieve I have gotten it for the time being. I went and added www-data to the individual user groups and now it seems to work. I hope it stays that way.

Chris

---

