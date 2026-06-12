---
title: "Best File Permissions for Webserver"
date: 2015-06-29
forum: Server Platforms
---

### Post by andrewjbarnett on 2015-06-29
Hey All,

I'm looking for some advice on the best way to configure my webserver.

Essentially I am using Nginx with PHP5-FPM.  Nginx & PHP5-FPM runs as user www-data.  There are only two users general access users on the server, myself and a friend, we each have our own user account with home directory.

Essentially the file structure for hosting is:

/home/user1/domain1.com/public
/home/user2/domain2.com/public

Now to allow uploads through WordPress (and editing), I had to change permissions of the files to www-data:www-data. Now the problem is to get that running, it then means that my friend (user2) now can't upload/edit files through SFTP.

Is there a way that I can allow them to be owner of the files so they can use SFTP, but also allow www-data access to upload and modify files through WordPress?

---

### Post by nerdtron on 2015-06-30
This question is asked a lot here and there are a number of solutions to this address the problem. First note that webpage files should be world readable in order for users to browse them on the web browser. Meaning, the "public" folder and all parent folders above it should have the read and execute bit turned on, like 755 or drwxr-xr-x permisson.

For my opinion, you can just leave everything owned to www-data for the webpage folders and setup a different SFTP folder for the other users. Then just manually move the uploaded files to the required directories. This is a bit of work but at least, you can track everything that is happening on the server.

Another option is that make sftp folder (only the folder where www-data upload to wordpress) owned by user2. Then add the www-data user to the group of user2. And then modify the permission of the sftp folder to allow group to write on the directory.

---

### Post by SeijiSensei on 2015-06-30
Only a few directories in WordPress need to be writable by the www-data user.  wp-content/uploads/2015 needs write privileges until the end of the year, when the 2016 directory will be created.  You also need to turn on write permissions in wp-includes during upgrades, but I turn them off again after the upgrade is complete.  All the other content will be written to the database, so permissions won't matter for that. 

I usually run the upgrade function from the Dashboard and watch to see what permissions need to be changed during the process.  After that I switch them back.

With WordPress you shouldn't need SFTP at all.

---

### Post by Drone4four on 2015-06-30
> **SeijiSensei said:**
> With WordPress you shouldn't need SFTP at all.  What would a WordPress admin use as an alternative?

---

### Post by SeijiSensei on 2015-07-02
All the content is written using the tools in the Dashboard and stored in the back-end database.  Objects like graphics are uploaded using the tools in the Dashboard as well.  The whole design of WordPress and similar "content-management systems" is to enable ordinary people to create sites without knowing much if anything about the underlying technologies involved.  Having to upload a site with SFTP would violate that principle.

If you've not used a CMS like WordPress, I suggesting getting a copy from wordpress.org and installing it on a test server so you can see how it works.

As for administration, if you don't have full access to the server, it's tough to administer anything.  I only rent virtual machines (at [Linode](http://www.linode.com/)).  I've never had an interest in hosted web services; they just seem way too restrictive to me.

---

