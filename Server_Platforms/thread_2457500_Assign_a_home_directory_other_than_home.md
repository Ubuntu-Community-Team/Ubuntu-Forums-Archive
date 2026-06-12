---
title: "Assign a home directory other than home?"
date: 2021-02-03
forum: Server Platforms
---

### Post by nick+d on 2021-02-03
Hello all,

I'm new to this.

I have installed Ubuntu Server, then vsftpd, LAMP and phpMyAdmin. It's been a long day but I am making lots of notes and learning lots of new things! The server will host Piwigo and Wordpress, and I will be looking to open these up to users outside of the LAN, but one step at a time!

I intend to install Piwigo in /var/www/html/**photos** and Wordpress in /var/www/html/**ecc** and I can create these directories using the command line.

So, I would like to FTP all of the files to their respective directories and later access the applications at 192.168.../photos and 192.168.../ecc

This means that I need a user with a root directory on the server of /var/www/html and appropriate permissions. vsftpd sets up a user when you install it, their root ftp directory is their home directory. I am happy to either change that user or create a new one. there is some info on the web but there is conflicting advice and when i did settle on one, I got stuck part way through.

Any pointers would be very much appreciated.

Thank you,
Nick.

---

### Post by TheFu on 2021-02-03
Don't use plain ftp.  Use sftp. here are too many reasons to list.  No need for vsftpd. Use openssh-server.  ssh and tools based on ssh are how Unix systems communicate.
> 
This means that I need a user with a root directory on the server of /var/www/html and appropriate permissions. vsftpd sets up a user when you install it, their root ftp directory is their home directory. I am happy to either change that user or create a new one. there is some info on the web but there is conflicting advice and when i did settle on one, I got stuck part way through.
This is incorrect.  You probably want a how-to for sftp-only user setups inside a chroot. Plenty on the internet.

BTW, "root directory" is the incorrect term.  "home directory" is what you want, but the chroot can solve that too or use symbolic links out of the HOME to the other directories.

Bests to never allow phpMyAdmin to be accessed over the internet. Only allow localhost connections - which you'd use over an ssh-tunnel.  I see thousands of attacks daily for both workpress and phpMyAdmin. 
By very careful with the security settings for those webapps.

---

### Post by nick+d on 2021-02-03
> **TheFu said:**
> Don't use plain ftp.  Use sftp. here are too many reasons to list.  No need for vsftpd. Use openssh-server.  ssh and tools based on ssh are how Unix systems communicate.

This is incorrect.  You probably want a how-to for sftp-only user setups inside a chroot. Plenty on the internet.

BTW, "root directory" is the incorrect term.  "home directory" is what you want, but the chroot can solve that too or use symbolic links out of the HOME to the other directories.

Bests to never allow phpMyAdmin to be accessed over the internet. Only allow localhost connections - which you'd use over an ssh-tunnel.  I see thousands of attacks daily for both workpress and phpMyAdmin. 
By very careful with the security settings for those webapps.Hi there,

Many thanks for this advice. I will go and uninstall vsftpd and look for a how-to for sftp-only user setups inside a chroot, I am hoping I can use some kind of graphical interface to transfer files, so I will read up. Thanks for the correction on root directory. I will read up about that, too!

For the forseeable future, everything will be on the LAN, I will look into securing phpMyAdmin before making anything public - I think that may be some way away in any case, for now I just want to get things working on the LAN - that will be a monumental achievement for me.

Again, thanks for your advice.

Nick.

---

### Post by nick+d on 2021-02-03
OK, so I am following this guide and I have got to this part:

```
tail /etc/ssh/sshd_config
Match Group sftpusers
        ChrootDirectory /sftp/%u
        ForceCommand internal-sftp
```

and I don't really know what to do. I have created the group: sftpusers and user: guestuser, as per the guide.

Thanks,
Nick.

---

### Post by TheFu on 2021-02-03
> **nick+d said:**
> Hi there,

Many thanks for this advice. I will go and uninstall vsftpd and look for a how-to for sftp-only user setups inside a chroot, I am hoping I can use some kind of graphical interface to transfer files, so I will read up. Thanks for the correction on root directory. I will read up about that, too!

For the forseeable future, everything will be on the LAN, I will look into securing phpMyAdmin before making anything public - I think that may be some way away in any case, for now I just want to get things working on the LAN - that will be a monumental achievement for me.

Again, thanks for your advice.

Nick.
All linux desktop file managers support sftp:// in URLs to access remote systems. Setup ssh-keys for more secrty and more convenience.
Windows supports sftp with either filezilla or winscp. There is a bug in filezilla versions, so if it doesn't just work, check that.

I've posted here how to use ssh as a socks proxy. Use that method to access admin web-apps.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a beginner book.  Missing the background for how nix works makes Linux harder. There is always a good reason for the way things are and work.  Always.  It doesn't seem that way, but there is. 

And if you don't master unix permissions, life will be hard, especially trying to run and secure servers. Chroot is all about permissions and having access to a minimal set of required system files. I haven't done the chroot thing in some years, so things could have changed.  I'd check the manpages for sftp-server and sshd_config. Details and caveats.

---

### Post by nick+d on 2021-02-03
OK, I do really appreciate your time but this is all way above me, I only just started with the command line very recently.

The book looks really interesting and I will definitely use that.

But is there no friendly how-to for somebody new like me to follow along to set up these two applications?

Thank you,
Nick.

EDIT: OK, so i have reread the code, I see now that I need to paste that at the end of sshd_config. For some reason i thought I needed to enter in the command line. So, i've done that, and this is what I've entered:

```
tail /etc/ssh/sshd_config
Match Group sftpusers
        ChrootDirectory /sftp/guestuser
        ForceCommand internal-sftp
```

Is this right, or am I supposed to be entering the path to the public_html directory in place of /sftp?

---

### Post by TheFu on 2021-02-03
> **nick+d said:**
> But is there no friendly how-to for somebody new like me to follow along to set up these two applications?
 
You've lost me too.  

You know what a file manager is, right?  There is an address bar near the top, usually.  A URL is what goes into that text-entry area.
[http://www.google.com/](http://www.google.com/) is a URL.
sftp://hostname.local/  is a URL, just for a desktop computer on your LAN.  The 'hostname' part needs to be changed to whatever you named the machine during the installation.  This also assumes mDNS and Avahi are running on the Ubuntu machine you want to connect into.  Ubuntu Server doesn't run either by default, but most Ubuntu Desktop variants run both.

sftp just works once you install the 'ssh' package. Just connect using the login username and password. This is a pain and ssh-keys are 100000x more secure and at least that much more convenient. You don't **need** the chroot, but it is a way to make an sftp user only have access to a specific directory, which is what I thought you wanted.  

Also, people running wordpress generally don't want it on their LAN, they want it on the internet, so I make all sorts of assumptions based on that.  Mainly, those assumptions were security related.  A few million wordpress websites are hacked right now.  There are a number of people who post in these forums who have security setups for locking down wordpress systems, except when they perform updates (weekly).  If you don't want your WP server hacked, get used to patching at least weekly, sometimes a few times a week is required. Running servers isn't a setup and forget job.

The other things you don't understand are because you are new.  They are all very standard things. Somehow, you've never been exposed to them previously.  Wikipedia will explain some of them. They are **that** standard - like symbolic links.

---

### Post by nick+d on 2021-02-03
OK, many thanks for your time. Clearly this is all way above me and explaining these basic things must be very tedious for somebody like you. Like I have already said, I don't want this public at the moment, I just want to get it set up on the LAN, particularly Piwigo. I will shelve the project and read up.

All the best,
Nick.

EDIT: If anyone else is struggling with this, I ended up just configuring FileZilla for sftp connection to the server and then creating the first (photos) of my two subdirectories in the html directory.

If I logged in with my ssh user credentials, I could see all directories on the server but did not have the correct permissions to write to the photos subdirectory that I had created. To solve this, I granted permissions to myself and the apache server for the photos directory, by following the steps [here]("https://askubuntu.com/questions/749697/how-do-i-give-myself-access-to-var-www-to-create-and-edit-files-and-folders-in").

After that I connected to the remote photos directory via sftp using FileZilla and loaded up the local files (piwigo installation files) to that directory.

Next I created a database 'piwigo', and a user 'piwigo_user' (granted all privileges) and recorded the password for that user.

Then I visited the LAN address of the server, like 192.168.X.XX/photos. That brings you to the install page of Piwigo. I entered all of the details it asked for and boom, there it was.

Now I am off to read lots about Linux, especially how I might safely make this application available outside of the LAN.

Hope this helps someone.

More EDITING: The only problem this gives me at the moment is that the site is only accessible through http, not https, which the app will force the user to use. I'll look at this and see if I can fix it.

---

