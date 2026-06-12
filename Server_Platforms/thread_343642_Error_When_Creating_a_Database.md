---
title: "Error When Creating a Database"
date: 2007-01-21
forum: Server Platforms
---

### Post by gunderwood on 2007-01-21
Hi All,

I'm setting up an Xubuntu Edgy on a box that will be a dedicated MythTV box. 

I,

1. did the base install
2. used automatix to add the extra non-free stuff needed
3. installed mysql and set the root password
4. installed mythtv and mythtv-themes

While installing mythtv it failed with the following error:

ERROR 1006 (HY00) Can't create database 'mythconverg' (errNo: 13)

perror 13 tells me that the errror is a permission denied error so I check some permissions.

I logged into mysql and checked my root accounts permissions, all access, all good.

I then checked the permissions of the mysql data directory; the directory and it's contents are oned by the mysql user and is set with sufficient read and write privliges.

I checked the mysql process and it's being run by the mysql user.

Can anyone help me figure this out, I very rarely use mysql and it's been quite sometime since I last set it up manually.

Thank you in advance,
Greg

---

### Post by DagonX on 2007-01-22
I had the same problem, and my solution is fairly ugly. Their has to be a better solution. But what I did was go to snaptic and remove anything that remotely had to do with mysql, I also told it
to remove all the configuration files, which in my case it didn't do. 

Then I reinstalled everything I had totally removed. Mysql had password problems so I followed:[https://help.ubuntu.com/community/MysqlPasswordReset?highlight=%28mysql%29]("https://help.ubuntu.com/community/MysqlPasswordReset?highlight=%28mysql%29")

I was then able to create and populate tables.

I would suggest trying the password rest link first. It is less effort and easier. 

One suggestion I found that is suppose to make life easier make sure you have a "mysql" group and make the "mysql" group owner of /var/lib/mysql (that is where the database files wind up).

If you find a better solution I would like to hear it.

Charles
[email]Charles@upyours.us[/email]

---

### Post by gunderwood on 2007-01-22
> **DagonX said:**
> I had the same problem, and my solution is fairly ugly. Their has to be a better solution. But what I did was go to snaptic and remove anything that remotely had to do with mysql, I also told it
to remove all the configuration files, which in my case it didn't do. 

Then I reinstalled everything I had totally removed. Mysql had password problems so I followed:[https://help.ubuntu.com/community/MysqlPasswordReset?highlight=%28mysql%29]("https://help.ubuntu.com/community/MysqlPasswordReset?highlight=%28mysql%29")

I was then able to create and populate tables.

I would suggest trying the password rest link first. It is less effort and easier. 

One suggestion I found that is suppose to make life easier make sure you have a "mysql" group and make the "mysql" group owner of /var/lib/mysql (that is where the database files wind up).

If you find a better solution I would like to hear it.

Charles
[email]Charles@upyours.us[/email]

I followed your advice and afteer what seems like to much work to fix a permission problem it all works. Oh well, I didn't have anything better to do.

Thanx, 
Greg

---

