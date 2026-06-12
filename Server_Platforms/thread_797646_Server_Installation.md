---
title: "Server Installation"
date: 2008-05-17
forum: Server Platforms
---

### Post by Popcorned on 2008-05-17
Hi,

I am planning to run a local development / testing server for web services using Ubuntu Server 8.04. 

I have only used Windows to control my local environment before by using an all in one package named "Web Developer Suite".

I will also want to be learning how to use Linux so when I purchase a VPS account I can jump right in.

The server will be used to provide hosting for a PHP application using a mySQL backend. I also need a way to emulate a VPS hosting package so I need some kind of file transfer system in place, My friends are telling ssh and scp. I was going to use plain ftp, what are your recommendations here?

I also had the idea of using an svn client to commit changes to the server? Good / Bad idea ?

With ftp, how would I lock a user into their respective web directory?

Many thanks
-Mathew Davies.

---

### Post by lemming465 on 2008-05-17
> ..I need some kind of file transfer system in place, My friends are telling ssh and scp.

Believe them.  FTP uses plaintext authentication, which isn't safe enough.

>  using an svn client to commit changes to the server? 
Subversion is a perfectly good centralized version control system, if you don't need a lot of heavy duty merge support.  I'm not sure what you are after here; *svn ci* is going to go from a local working copy into a remote repository.  The repository is binary; you can't use it as a web root.  If the goal is to track a web site with subversion, typically you'd use rsync over ssh to go from the working copy to the webroot.

> With ftp, how would I lock a user into their respective web directory?

If you are using, say *vsftpd*, by turning on the chroot functionality and setting the webroot as the home directory.  That filesystem probably needs to be mounted with the *nodev* option, among other security things.

---

### Post by Popcorned on 2008-05-18
> If you are using, say vsftpd, by turning on the chroot functionality and setting the webroot as the home directory. That filesystem probably needs to be mounted with the nodev option, among other security things.

Do I need have the home directory on its own partition for this to work? I am used to FileZilla having its own user system, but with vsftpd I assume it uses the system users?

> Subversion is a perfectly good centralized version control system, if you don't need a lot of heavy duty merge support. I'm not sure what you are after here; svn ci is going to go from a local working copy into a remote repository. The repository is binary; you can't use it as a web root. If the goal is to track a web site with subversion, typically you'd use rsync over ssh to go from the working copy to the webroot.

Basically the idea was to have a local machine as the development server, then be able  to commit the changes to the project on the testing server. One of my friends mention having the svn do a checkout to the webroot each time a change is committed. 

I will also look into rsync now.

---

### Post by lemming465 on 2008-05-18
> **Popcorned said:**
> Do I need have the home directory on its own partition for this to work? I am used to FileZilla having its own user system, but with vsftpd I assume it uses the system users?

I believe vsftpd will use for home directories whatever the /etc/passwd file specifies for the users.  Which doesn't have to be /home; it can be anything you want.  If people are FTP'ing into a web tree, the webroot should probably be a separate filesystem.  How many filesystems is negotiable; I often run home machines with just two (root and swap), and servers with a dozen more more (separate /boot / /tmp /var /usr /usr/local /opt and maybe a few others particular to the server usage.)

>  ... having the svn do a checkout to the webroot each time a change is committed.

This can work, yes.  Typically you would do *svn update* to sync a working copy with a repository; checkout is a one time operation.  If you don't want .svn subdirectories running around your web tree, then you are back to an rsync.  There a lots of ways to do this; anything that accomplishes your goals is fine.

---

