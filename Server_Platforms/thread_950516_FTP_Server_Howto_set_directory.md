---
title: "FTP Server: Howto set directory?"
date: 2008-10-17
forum: Server Platforms
---

### Post by Revo___ on 2008-10-17
Hello there.

I've recently installed the latest Ubuntu Server-Edition.
I've installed an FTP Server.
Every local user can login and put files to himself's home directory.

Now I wanted to create one user, who is aloud to add files to a special directory (the public web directory).

I've read the manual and still don't know how to do that.
So I hope you can help me with that problem.

Greetings
Revo___

edit: spelling mistake

---

### Post by vegas588 on 2008-10-17
Hey! 

I am trying to do the same thing and have been unsuccessful too.

Need to create one user that will have access to read/write to one directory /home/ftp

looked all over and I still cannot get it to work either. 

Thanks for your help.

---

### Post by Revo___ on 2008-10-18
If you need some more information to help us you may ask.

---

### Post by lykwydchykyn on 2008-10-18
Well first off, which ftp server did you install?

---

### Post by henlij on 2008-10-18
i'm using openssh and i'd like to know how to either change the directory that a user sees when logging in or add a user that can see /var/www/ when they login. Thanks!

---

### Post by Revo___ on 2008-10-19
I've used
```
apt-get install vsftpd
```
to install my Ftp-Server,
if this is, what you need to know ...

---

### Post by lykwydchykyn on 2008-10-19
It's been my experience that vsftpd does not allow for more complicated setups like this, but you can probably work around that if you don't want to setup a different server.  Simplest way to accomplish what you want is this:

 - create your user, let's call him "webadmin":
```

sudo adduser webadmin

```
 -move the contents of the webroot to a folder in webadmin's home (you'll have to stop apache first):
```

sudo /etc/init.d/apache2 stop
sudo mv /var/www /home/webadmin/www
sudo chown -R webadmin /home/webadmin/www

```
 - create a symbolic link from /var/www to the www folder in webadmin's home and restart apache:
```

sudo ln -s /home/webadmin/www /var/
sudo /etc/init.d/apache2 start

```

Now, when webadmin logs in, he can put anything into ~/www and it's in the public web root.

---

### Post by Krupski on 2008-10-19
> **Revo___ said:**
> Hello there.

I've recently installed the latest Ubuntu Server-Edition.
I've installed an FTP Server.
Every local user can login and put files to himself's home directory.

Now I wanted to create one user, who is aloud to add files to a special directory (the public web directory).

I've read the manual and still don't know how to do that.
So I hope you can help me with that problem.

Greetings
Revo___

edit: spelling mistake

Most FTP servers have config files that allow setting the location of the ftp directory. However, there's an easier way. Simply create the user "ftp" with the directory you want defined.

First, check to see if the user "ftp" exists:

```

sudo cat /etc/passwd | grep -i ftp

```

If it returns a string, the account exists. If it returns nothing, the user does not exist.

If the user "ftp" exists, delete the account:

```

sudo userdel ftp

```

Now, (re)create the "ftp" user account. Here you can specify the home directory of the user (which is what the FTP server will use):

```

sudo useradd -d [COLOR="Red"]**/home/ftp**[/COLOR] -s /bin/false -r ftp

```

That command means "add a user, the home directory (-d) is '/home/ftp', the shell (-s) is /bin/false, which does nothing (i.e. it's not a real shell) and create a system account (-r) named 'ftp'".

The string highlighted in red is the user's home directory. Change it to anything you wish.

Note that the home directory of the user 'ftp' does not have to exist at the time you create the account (i.e. useradd won't complain), but an FTP login will fail UNLESS there actually is a directory at the proper place.

Good luck!

-- Roger

---

### Post by Krupski on 2008-10-19
> **lykwydchykyn said:**
> It's been my experience that vsftpd does not allow for more complicated setups like this,

For vsftpd, all you have to do is edit the /etc/vsftpd.conf file and add a line that says "anon_root = /home/ftp" (/home/ftp is an example - you can use anything you wish - as long as it exists!) :)

-- Roger

---

### Post by lykwydchykyn on 2008-10-19
> **Krupski said:**
> For vsftpd, all you have to do is edit the /etc/vsftpd.conf file and add a line that says "anon_root = /home/ftp" (/home/ftp is an example - you can use anything you wish - as long as it exists!) :)

-- Roger

Wouldn't that create an anonymous ftp site?  I'm thinking that's not what you'd want for your web root.

Unless I'm misunderstanding what he means by public web directory -- public writable?

I'm understanding the problem (revo please clarify) that he's got users logging in to their home directories, and now wants to add an (authenticated) account which will log in to the web directory.  I've never found a way with vsftpd to give an individual user a unique login directory other than its home, unless you make everyone log in to the same directory.  If I'm wrong I'd be interested to know how this is done, it'd be useful to me.

---

### Post by Revo___ on 2008-10-20
I meant with "public webdirectory" that everybody can read it - but not everybody should be able to write.

Your posts helped alot.
Everything I wanted works ...

---

### Post by MaindotC on 2009-01-19
One thing I did was create the user's home directory in the location they could ftp into.  I don't want people in /home b/c if /home gets too big then I can't log in (dunno how to set/remove disk quotas yet but I will).  So if the user I want to add is "esko", and the directory I want him to use is on a different hard drive mounted in /media/disk, I used the following command:
```

useradd esko -m -d /media/disk/esko

```

I also enabled the configuration in /etc/vsftpd.conf to allow regular users to log in and use their home directories.  Thank you all (especially Krupski) for stimulating my thinking.

---

### Post by mudz on 2009-09-09
i have the same prpblem with this issue, and now i've solved it with the lykwydchykyn way, but now new problem comes, i.e. my web server don't run well, the error message "Forbidden. You don't have permission to access / on this server." appear when i open the web.
 
i've try to googling but i dont fount yet the solution. what is the wrong?

---

### Post by lykwydchykyn on 2009-09-09
> **mudz said:**
> i have the same prpblem with this issue, and now i've solved it with the lykwydchykyn way, but now new problem comes, i.e. my web server don't run well, the error message "Forbidden. You don't have permission to access / on this server." appear when i open the web.
 
i've try to googling but i dont fount yet the solution. what is the wrong?

What are the permissions on the web folder?  The www-data user needs read permissions on the folder and contents.  Actually, execute permissions might be required on the folders as well, but try without it first.

---

