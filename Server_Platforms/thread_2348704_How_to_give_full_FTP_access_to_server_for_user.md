---
title: "How to give full FTP access to server for user"
date: 2017-01-06
forum: Server Platforms
---

### Post by fredsmith3 on 2017-01-06
Hi all,

My first post here, I am a bit of a noob, but can usually figure things out for myself... however, this has me stumped...

I have set up a remote webserver running 14.04, apache2, mysql, wordpress and php to host a website.

I want to give another user full ftp access to the server to allow them to upload files to any folder on the server, but he especially needs access to the wordpress folders.

I have installed vsftpd, which seems to be working ok, and added a user. The user can log in with filezilla, but only has access to /home/user/files (which is a directory I set up for them). The user is sudo.

How do I give this user full access to the server through ftp?

Thanks in advance.

---

### Post by TheFu on 2017-01-06
Don't use plain FTP. There are only a few good reasons for that, under very special situations. Plain FTP shouldn't be used 99.9999% of the time.

Do use sftp. This is part of ssh.  **sudo apt-get install openssh-server**. Then any ssh, scp, sftp client can access the machine. Prevent brute force attacks using **fail2ban**.  The defaults are reasonable.  Filezilla is an sftp client.  WinSCP is too. On Linux, any file manager is too, just use sftp:// or ssh:// in the URL.  Of course, you can also use shell programs.

You cannot allow a normal user access to upload files to any directory - BTW, folders are for different OSes.  

Oh ... and purge vsftpd. It isn't needed.

To provide a use with specific access to specific directories isn't hard. Just learn to use normal, Unix file and directory permissions.  This learning needs to be hands on and will save you hours, days, months of frustration. It is a simple, elegant, flexible, solution.
[http://askubuntu.com/questions/83/how-do-file-permissions-work](http://askubuntu.com/questions/83/how-do-file-permissions-work)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Open a few terminals, create a few userids (at least 4) and different groupids.  Move into the /tmp/ directory and create some subdirectories under there to play around.  Use
* mkdir
* ls -l  - to see the permissions
* chmod - 
* touch - creates empty files
* umask - controls defaults
* less/cat/more - to view contents
to create files and control permissions.  Setup files that can be read by 1 but not the other userid.  Setup files that can be edited by 2, 3, 4 of the userids, but not any others.  Setup a directory that lets people edit files, but not create or delete those files.  Be curious - do other things.

When you have that done, it should take about 20-40 minutes of playing around, you'll have a concrete understanding. Nothing else will be hard related to permissions again.  Under Linux (or any Unix OS), processes run under userids.  So, the directory and file ownership, group membership and permissions are central to Unix security. **If you are running a public server, this is absolutely critical to understand AND master.** One of the most common wordpress hacks takes advantage of incorrect permissions and incorrectly installed addons.

And [don't use plain FTP]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp").  If the hosting provider doesn't allow sftp, fire them now. Today. Immediately.  They don't respect you or the security of their systems.

---

### Post by ramah2 on 2017-01-26
I agree with TheFU on using SFTP over openssh, if you still need to do this from vsftp you will need to edit /etc/vsftpd.conf and edit the following setting:

# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=**NO**

---

### Post by SeijiSensei on 2017-01-27
A more basic question is why the other user needs direct connections to the server at all.  What can he not do using the site's WordPress dashboard and the other standard methods for uploading content that WP provides from the editor interface?  I post items with a mix of text and graphics all the time, and I never need any other access other than that offered by WordPress.

---

