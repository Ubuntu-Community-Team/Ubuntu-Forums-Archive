---
title: "Newby Help Setting up FTP"
date: 2010-08-11
forum: Server Platforms
---

### Post by jcnewman83 on 2010-08-11
OK, go easy on me as I am very new to this,

I am setting up a basic FTP server and need help setting up the folder permissions so that users are only able to access the folders they have access to.

I have used vsftp and set up some groups and users, I have set the vsftpd.config file to not allow anonymous access etc and I have confirmed that the server is accessible and working, now to the part I am getting stuck on.

I have a basic folder structure, at the root I have a folder called FTPFolder and within that I have 2 folders, one called private and one called public. I have set up 2 groups (publicaccess and privateaccess) and want to set so that you can only access the private folder if you are a member of the privateaccess group and vice versa for the other folder.

Is there a simple way of archiving this, I have had a stab but when I access the folders using the account that I want to be the most restrictive account, I am able to keep browsing up a level until I eventually get to the root and I definitely do not was that! 

Is anyone able to point me down the correct path?

---

### Post by msandoy on 2010-08-11
I have used a tool called GADMIN-proftpd with good results. This can be installed via Synaptics package manager. It is a GUI for setting up FTP. Might be easier than editing text files, if you are more familiar with other operating systems.

---

### Post by mickwombat on 2010-08-11
Hi,
I have used pure-ftp and proftp and in both cases setup 'virtual users'.  This creates a user in the ftpgroup (or whatever) without having to create seperate unix accounts.  The user gets chrooted into the directory specified when the account is created and cannot browse out of their folder.
For pure-ftp, this explains it really well.
[http://download.pureftpd.org/pub/pure-ftpd/doc/README.Virtual-Users]("http://download.pureftpd.org/pub/pure-ftpd/doc/README.Virtual-Users")
Hope it helps
;-)

---

### Post by edkasky on 2010-08-12
I have set up a number of ftp servers using Wuftp and found the easiest way to restrict a user to their home directory is to edit the passwd file thusly:

user:x:513:515:Full Name:/path/to/folder/./:/bin/sh

Notice the /./ at the end of the path - it works.

I also set other access defaults in ftpaccess so that the permissions remain intact so they can upload when and where needed.  We have a number of clients who transfer their accounting files this way.

HTH some...

Ed

---

