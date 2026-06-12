---
title: "User permissions on /var/www  Dreamweaver upload issue"
date: 2011-09-30
forum: Server Platforms
---

### Post by dryflys on 2011-09-30
Hi Forestpiskie!
My name is Tom and I have been using Linux for a long time and ubuntu since Red hat split to fedora and RHEL.  I registered to try to find a solution to a nagging issue that I really should already know how to deal with but it has proved intractible to me.
One of my ubuntu servers is used as an intranet portal to provide internal folks with useful information. I am using apache 2.0 and MySQL with mostly PHP and some javascript and a acouple of PEAR apps. I do my authoring using dreamweaver on an M$ Windows box.  the root of the site is at /var/www.
My issue is that I am unable to use the dreamweaver upload to the server because my user does not have permission to write to the root of the web site. I have to upload everything to my user area and then sudo cp files into the web site.  I like ubuntu but am ready to go to another distro for this box if I cannot solve the issue.

---

### Post by nothingspecial on 2011-09-30
Moved to Server Platforms

---

### Post by eric_1982 on 2011-10-02
Sounds like it is just a simple permissions things. Just need to add your user to the group that has permissions to that directory. 

You could use **ls -l** command in the directory and see who the user and group owners are. Then just add your user to that group. 

Another quick fix if you have permission is to set the root password on your box and use that ID to upload the files.

---

