---
title: "Setting up permission for an SFTP account"
date: 2014-09-21
forum: Security
---

### Post by Shimon_Dekel on 2014-09-21
Hi,
In short:  I need to enable an SFTP user to gain access to my entire web site for development.
In details:
I am running Ubuntu on AWS
On this server I am running a Drupal 7 sites (multi site) and am using NetBeans as a development environment.
I connect from MS Windows  using ssh with puTTY using a public/Private key, logging in using the name "ubuntu".
Then Using "sudo" I was able to install Drupal and all the tools  needed.
Drupal is now, able to create files and have no problem functioning.
In order to connect NetBeans I setup a sftp account named "dekelroot" (NetBeans can connect via FTP or SFTP) and I am able to connect and read the directories and files.
I can also edit files as long as I change permissions to 777.
I am having problem creating new files (permission wise) I can create a new file using ssh' change the permission 777 and than I am good to go.
Everything I have to change or create is under drupal/sites/all…
Getting a file listing "ls –l" I get:
In some cases the owner is "www-data" the group is "dekelroot"
Other cases are root:root and yet the Drupal orginal installation is 6226:6226
 
The ultimate goal is to get everything working so I can create and manipulate files using my SFTP account and to this end I need some help setting the permissions right.
I would appreciate any help.
Thanks
Shimon Dekel

---

### Post by Lars Noodén on 2014-09-21
Drupal may need some additional permission changes but the general settings for the web directory (and below) should be 755 or 775.  For files it should be 644 or 664.  If you and at least one other person are collaborating then you'll need to work using groups and should make a new group for that task.

```

# do once
sudo addgroup webmasters
sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs,o=rx "{}" \;
sudo find /var/www -type f -exec chmod g=rws,o=r "{}" \;

# repeat for each user:
sudo gpasswd --add sdekel webmasters

```

That will get you write access to /var/www or whatever directory you are using for your site's documentroots.  If you want to keep the projects separate, then use separate groups for each DocumentRoot.  

Drupal itself, though, is another question.

---

### Post by Shimon_Dekel on 2014-09-25
Worked!
Thanks so much

---

