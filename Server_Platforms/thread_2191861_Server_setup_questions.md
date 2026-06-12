---
title: "Server setup questions"
date: 2013-12-04
forum: Server Platforms
---

### Post by johnpsmyth on 2013-12-04
I work for a small educational establishment and have been faced with a challenge.

We hope to run a course in basic Web Design and as part of this the students will be required to upload their finished using ftp.

I have setup a Ubuntu 12.04 server and installed Webmin as the admin GUI.

So far so good. All works OK, I get the It Works message etc. The server is for local use, it is not for web hosting on the internet

So here is the challenge and as a newbie it is causing me a lot of head scratching!

We would like the students to be able to upload to their own directory and have this directory pwd protected from other students. At present the target  directory is /var/www.  I am aware of how to create sub directories on my personal domain, no problem with that as I am the only user. What I cant figure out is how to setup individual directories on this server for the students to access via ftp, upload their work and view the finished results.

I hope my explanation makes sense, I am very new to servers and the terminology I have used may be incorrect, forgive me!

Thanks in advance

John

---

### Post by volkswagner on 2013-12-04
I think you may use [mod_userdir]("http://httpd.apache.org/docs/2.2/mod/mod_userdir.html") 

You can setup ftp to jail users to their home directory.

---

### Post by tgalati4 on 2013-12-04
You would normally set up accounts for each student.  That gives each username a home directory that is protected from other students.  Students could simply put their html files in their home directory and use symbolic links to create subdirectories under /var/www:

username1
username2
username3

Then you can view their pages [http://localhost/username1](http://localhost/username1), etc.

```
sudo ln -s /home/username1 /var/www/username1
sudo ln -s /home/username2 /var/www/username2
```

If you have a lot of students, you could write a script to create all of the links based on a list of usernames.

You may have to change the owership of the /var/www/username1 directories to www-data:www-data to get apache to serve them.

---

### Post by bigmonmulgrew on 2013-12-05
Hi
My situation was not exactly the same as yours I didnt need multi user local access but it should work the same way.

I had a web server and wanted to give my brothers access to host their personal websites on it but for security I didnt want them to see each others files in case they carelessly gave out their passwords. 

The folder structure is 
/var/www/username/domainname

So my older brother who had 2 is

/var/www/brother1/domain1
/var/www/brother1/domain2

Each user then sees their own user directory as the server root directory.
Brother 1 sees
/domain1
/domain2

The way the security works they cant add files to the root directory so I also added a private folder for file storage.

/var/www/brother1/private

I also shared linked some of their domain specific log files and put them a logs folder 
/var/www/username/logs

now brother 1 sees
/domain1
/domain2
/logs
/private

This works well as each user has no access to any one elses, or the servers files. If they try to manually type a file address in they are told it does not exist.

I wrote a guide for setting up Drupal, where the first steps concern the Ubuntu server itself and it shows you how to set things up in this manner. 
Find it here [http://foreverythingit.co.uk/book/drupal-7-superguide]("http://foreverythingit.co.uk/book/drupal-7-superguide")

---

