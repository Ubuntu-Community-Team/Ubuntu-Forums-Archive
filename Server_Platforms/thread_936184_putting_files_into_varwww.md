---
title: "putting files into /var/www"
date: 2008-10-02
forum: Server Platforms
---

### Post by spynappels on 2008-10-02
Hi guys,

  i hope one of you can help me. I need some help getting some files to the /var/www directory of my server. Do I need to install an FTP package and will this allow me to place files in any directory I want? its a little difficult to visualise the directory tree when I am only using command line (yes I am a relative noob) I just want to host an extremely simple web page to start with, so I'll only be uploading an 'index.html' file and a CSS file to begin with, but nano justis to cumbersome for me to use to produce and correct these files.

 Any help or how-tos would be very much appreciated.

  Thanks

---

### Post by whitegourd on 2008-10-02
You can install samba ...

   sudo apt-get install samba

And create a link from your home directory on the server to point to /var/www ...

   ln -s /var/www /home/username/www
      (username = your username)

Then from your desktop just navigate to the server's share \\server\username\www

---

### Post by lykwydchykyn on 2008-10-02
Kind of depends on what your workstations are running.

FTP is pretty universal.
Samba is best for windows clients, but will work with others as well.
NFS is good if you only have linux clients(OSX too?)
SSHFS or SFTP (both only require openssh-server on the server) are good if you have Linux clients.  I prefer these myself, though I've worked with others.

---

### Post by spynappels on 2008-10-02
OK thanks for your help so far. I usually administrate the server using ssh from a terminal in my Ubuntu Desktop or from a putty connection on my WinXPmachine, (WinXP and Ubuntu dual boot machine).
Does this mean that the necessary package for SSHFS is already installed on my server? If so, how does it work? I've never used it, so some help in the form of a walkthrough or how to would be helpful.

 I'd like to be able to do it from both the WinXP and Ubuntu Desktop machines, but instructions for either would be great.

 Thanks again.

---

### Post by jamesr on 2008-10-02
Hi,

If I have understood your problem correctly, I personally use 1 of 2 ways  to transfer my files to my /var/www directory.

Method 1, 
Install a FTP server on my server see howtoforge.com "perfect server for Ubuntu 8.04.". This means I can connect to the var/www directory using "ftp surfer" from my windows machine and a standard FTP from the linux PCs. This was my standard method with my previous server. I also doubled as the method used to upload to a commercial server.

Method 2,
Install midnight commander on the server and use that to edit the files. You can also nano if you are prepared to use a text editor. To first, load the web sites, I use a USB key to copy from my windows system to my server. Again you could use remote access.

PS how big are the files index.html and the css file.

Best Wishes
Jim R

---

### Post by spynappels on 2008-10-02
OK, a little progress. I can mount the /var/www folder on my Ubuntu Desktop using sshfs and open the files and edit them, but when I try to save the edited versions, I get a "you do not have permission" dialog. How do I change the permissions of the files on the server so that I can edit them on my Ubuntu Desktop?

 Also, can I use sshfs across a putty connection from a windows machine? I think I'd run into trouble specifying a mount point, so I don't think it is possible, but I stand to be corrected on this point. If this is not possible, I need help the FTP to send files from my WinXP machine to the server's /var/www folder.

  I'll get there in the end...

---

### Post by spynappels on 2008-10-02
> **jamesr said:**
> Hi,

If I have understood your problem correctly, I personally use 1 of 2 ways  to transfer my files to my /var/www directory.

Method 1, 
Install a FTP server on my server see howtoforge.com "perfect server for Ubuntu 8.04.". This means I can connect to the var/www directory using "ftp surfer" from my windows machine and a standard FTP from the linux PCs. This was my standard method with my previous server. I also doubled as the method used to upload to a commercial server.

Method 2,
Install midnight commander on the server and use that to edit the files. You can also nano if you are prepared to use a text editor. To first, load the web sites, I use a USB key to copy from my windows system to my server. Again you could use remote access.

PS how big are the files index.html and the css file.

Best Wishes
Jim R
  The files are very small, as I'm just using it to get started with HTML and CSS web design, but eventually I want to add photos etc.  The FTP probably sounds easiest, and if I get that working, could I use the FTP built into Dreamweaver to publish sites to Ubuntu Apache servers?

  Thanks for the help so far...

---

### Post by Iowan on 2008-10-02
**/var/www** by default is owned by root.  You can use **chown** (change owner) to make it more accessible (more info via **man chown**).

---

### Post by spynappels on 2008-10-03
> **Iowan said:**
> **/var/www** by default is owned by root.  You can use **chown** (change owner) to make it more accessible (more info via **man chown**).

So what do I need to set the owner and group to to ensure I have read and write permission from my SSHFS session?

---

### Post by lykwydchykyn on 2008-10-03
Whatever account you are logging in to the server as.

---

### Post by spynappels on 2008-10-03
Ok, I'm sorry for being thick here, but I chown the folder and I still can't save an edited version of index.html

 When running the chown command, do you need to run it on a folder AND its contents, or just on the folder and the contents automatically in herit the changed ownership?  There was a reference in the man chown to recursive and this rings a very faint bell wrt to the change applying to everything in the folder, but its very very faint.

  Thanks again for your help so far.

  Stef.

---

### Post by lykwydchykyn on 2008-10-03
You need to run it on all.  Just use the -R switch when running it on the folder, that will do the contents as well, e.g.:
```

chown -R myuser:users /var/www

```

---

### Post by jamesr on 2008-10-03
Hi spynappels,

what permissions do you have set up on the directory /var/www and what permissions do the files have? Could you post the results of the following```
ls -l
```

---

### Post by Rich78 on 2008-10-03
If you have a *nix box at both ends then you can use the following command to copy files over ssh, which is how I would normally transfer files.

scp [[user@]from-host:]source-file [[user@]to-host:][destination-file]

---

### Post by spynappels on 2008-10-03
Great work people. I can use gedit on my Ubuntu desktop to edit the index.html and ex1.css files in/var/www folder of server. Thank you for all your help. My next question will have to do with FTP settings, but I'll open a separate question for that.

  Thanks again people.

   Stefan.

---

