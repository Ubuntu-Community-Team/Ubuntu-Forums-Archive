---
title: "ownership of www folder, write permissions"
date: 2013-12-23
forum: Server Platforms
---

### Post by support3 on 2013-12-23
1) I have installed a lamp server in a virtual machine 
2) I have moved my www directory to under my home folder example home/{username}/www
3) I have changed the apache conf file to point at the new destination for the www folder
This works correctly and when I enter the IP address I am taken to the destination of the new index.html file

Currently the www folder is owned by myself, I checked this by running ls -l command
I have control over this folder, so I can upload, download, create directories 

I noticed an issue with a .php script, it wouldn't allow me to upload a file to the www directory. The script is 100% correct.
After much searching  it was because www-data is not the owner/group of the www folder, only me

So the question I wanted to ask now is how do I add www-data to this  folder as well as myself, so I have the correct write permissions to  upload files using a .php script?

I hope this makes some sort of sense.

---

### Post by CharlesA on 2013-12-24
Add the www-data user to the group your user is in and give the group write permission to the folder.

---

### Post by support3 on 2013-12-24
> **CharlesA said:**
> Add the www-data user to the group your user is in and give the group write permission to the folder.

Thanks for the tips,

I have progressed since this last post I made. Went back to the start as it only takes a few minutes to install a new VM.
I am currently at the following junction

1) Install Ubuntu Server as virtual machine
2) Located www directory under /home/{username}/www
3) Changed apache conf file 
4) Installed php,mysql

Then I did the following
sudo adduser {username} www-data
sudo chown -R www-data:www-data /home/{username}/www
sudo chmod -R g+rw /home/{username}/www

This works fine. I uploaded a .php script so that I can upload any file from the browser 192.168.0.8/upload.php 
It works and places the file under the www directory as expected

I added a new folder under www named uploads /www/uploads
I changed the php script to reflect this

When I run the script the file says it has uploaded, but when accessing the uploads directory nothing has been written to the directory.

Basically what I need to happen is whatever folder I create under www, it has the same permissions as www so I can upload files.

I am nearly there.....

---

### Post by CharlesA on 2013-12-24
What are the permissions on the new folders?

---

### Post by support3 on 2013-12-24
Because I cannot copy and paste from the terminal this is what I have for both www and uploads folders. Without making things more confusing for myself, I can see below that the uploads folder is owned by me whereas the www is owned by www-data

**www**
775 drwxrwxr-x
Uid www-data
Gid www-data

**uploads**
775 drwxrwxr-x
Uid devuser
Gid devuser

---

### Post by SeijiSensei on 2013-12-24
> **support3 said:**
> Basically what I need to happen is whatever folder I create under www, it has the same permissions as www so I can upload files.

[http://www.library.yale.edu/wsg/docs/permissions/sgid.htm](http://www.library.yale.edu/wsg/docs/permissions/sgid.htm)

---

