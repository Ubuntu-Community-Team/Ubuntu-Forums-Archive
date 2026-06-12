---
title: "Permissions for Multiple User Apache/SSH/FTP Access"
date: 2009-07-27
forum: Server Platforms
---

### Post by adnymarc on 2009-07-27
I am running Ubuntu 8.04 LTS Server and Apache 2 as my web server. I have domains successfully located in /var/www/vhosts/domainname.com but have to modify files as root in order to add/change files for the domains. I dislike the Plesk interface and the mess it makes of a lot of things, but appreciated its ability to allow multiple people access to different domains on a server. I have most everything setup the way I would like it, but am having issues with permissions for my domain directories.  I would like to setup access with the following criteria: 
 
 1. Each domain can have a user assigned to it (and allow for the same user to manage multiple domains - could even create symlinks in their home folder to their domains) 
   2. Certain users will have shell access and may be chrooted to the domain directory they control 
 3. FTP needs to be setup and able to correctly access the domains so that content editors for each domain can upload/download without permissions issues 
 
I am relatively new to linux sysadmin and have searched for a good guide to help solve these issues but haven't been able to find one yet. The closest information I have found was an unanswered post on this forum from last year, which I have copied below.  Thanks in advance for your help.


> **Apache Virtual Host & FTP File Permissions (from [http://ubuntuforums.org/showthread.php?t=662352](http://ubuntuforums.org/showthread.php?t=662352))**             
                                                                Hello,

I have several virtual hosts set up under Apache which are working just fine. I want to begin to allow users to FTP to these directories as well. FTP is setup and users can connect, but cannot modify any files.

Assuming it was a permissions issue, I looked at the permissions of all the folders that contain the virtual hosts. Their current owner:group is root:root so I am sure this is the problem.

What is the favored or standard approach? Do I make a new system user and/or group? Or do I set the ownership to a user that already exists like the user for the FTP server or WWW server?

I guess I am looking for feedback on others accomplish this.

Thanks.


---

