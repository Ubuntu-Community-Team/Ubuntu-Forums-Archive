---
title: "Multi user lamp server"
date: 2011-05-25
forum: Server Platforms
---

### Post by DanHorniblow on 2011-05-25
Hi, I am looking to create a multi-user LAMP server.

For example the domain name behind my curent server is "example.no-ip.org"

I would like user1 to have "example.no-ip.org/user1" and user2 "example.no-ip.org/user2"

How would i go about doing something like this?

---

### Post by tapi0n on 2011-05-25
I would just make virtual hosts in apache.

Create the required dirs in /var/www, for example

```

mkdir /var/www/user1
mkdir /var/www/user2
```and assign .htaccess files in each on these folders which allow user1 to browse to *example.no-ip.org/user1*.Likewise for user2.

I'm still learning things in this area, but at the moment I can only suggest that. If anyone cares to correct me with a better way please do since I am also still learning :)

---

### Post by DanHorniblow on 2011-05-25
Ok, but then how would I set permissions to user1 and user2 so that they only had access to their directory?

---

### Post by lykwydchykyn on 2011-05-25
Are you trying to set up an ISP/webhost type arrangement, or just trying to give a few people a convenient way to host some files?

Simply enabling the "userdirs" module of apache will give you the classic "http://myserver.example.com/~someuser/" addresses.

Otherwise, you can set it up manually by creating symlinks from a "www" folder in each user's directory to your web root -- like so:

```

sudo mkdir /home/someuser/www
sudo chown someuser /home/someuser/www
sudo ln -s /home/someuser/www /var/www/someuser

```

If you need more of an isp/webhost configuration, there are some software packages out there like ISPconfig, and no end of tutorials on how to set them up if you search for "ubuntu isp howto"

---

### Post by DanHorniblow on 2011-05-25
I am setting up a public facing testing server at my work with use of no-ip.
There will be aprox 20 to 30 users, what would you recomend?

I have setup ubuntu LAMP servers before but only single user.

---

### Post by lykwydchykyn on 2011-05-25
> **DanHorniblow said:**
> Ok, but then how would I set permissions to user1 and user2 so that they only had access to their directory?

That depends on how they'll be connecting to upload things.  Samba?  FTP?  SSH?

If you take either of the first two approaches, the actual data resides in the users' home directory; in which case, it's just a question of corralling the user in his home.  Most file sharing packages have some sort of easy switch for that scenario.

---

### Post by tapi0n on 2011-05-25
> **DanHorniblow said:**
> Ok, but then how would I set permissions to user1 and user2 so that they only had access to their directory?

All of that can be done in the htaccess file. There is some very good and extended information over [here]("http://httpd.apache.org/docs/1.3/howto/auth.html") on the subject :)

Also what *lykwydchykyn* mentioned looks interesting too. Gonna look into it when I got some time.

---

### Post by lykwydchykyn on 2011-05-25
> **DanHorniblow said:**
> I am setting up a public facing testing server at my work with use of no-ip.
There will be aprox 20 to 30 users, what would you recomend?

I have setup ubuntu LAMP servers before but only single user.

I'd recommend the symlink method I described above.  "Userdirs" saves some setup time, but (1) you have to deal with the tilde in the name, and (2) I've had situations where php pages simply refused to run under userdirs, but ran fine from the same directory when symlinked.

---

### Post by lykwydchykyn on 2011-05-25
> **tapi0n said:**
> All of that can be done in the htaccess file. There is some very good and extended information over [here]("http://httpd.apache.org/docs/1.3/howto/auth.html") on the subject :)

Also what *lykwydchykyn* mentioned looks interesting too. Gonna look into it when I got some time.

htaccess files tell apache various things about how to serve the files.  If the intention is to restrict who can *view* the files (via Apache), then an htaccess file is needed.

If the intention is to restrict only who can *write* to the files, then it's a question of how you are giving them access to write to the files in the first place.  That won't be through apache (well, unless you want to use webDAV, I guess, but I know zip about that).

---

### Post by DanHorniblow on 2011-05-25
I want all users to be able to view each others directory via the browser. But only be able to write to their own.

This is so we can see each others work and share ideas.

I would prefer them to be connecting via SSH or FTP as we use dreamweaver in the office, and it is very simple to setup dreamweaver to interact with either of them internally and externally.

---

### Post by tapi0n on 2011-05-25
Ah ok :)

Didn't know what his intentions were when I first posted though. 

That's what I like about this forum. Even if you're wrong, you still learn something new ^^

---

### Post by lykwydchykyn on 2011-05-25
> **DanHorniblow said:**
> I want all users to be able to view each others directory via the browser. But only be able to write to their own.

This is so we can see each others work and share ideas.

I would prefer them to be connecting via SSH or FTP as we use dreamweaver in the office, and it is very simple to setup dreamweaver to interact with either of them internally and externally.

Ok, htaccess files are not needed in this case then.

What you probably want to use is SSH, but you want to chroot jail users to their own directories.  There's a tutorial on that here: 
[http://ubuntuforums.org/showthread.php?t=1057657](http://ubuntuforums.org/showthread.php?t=1057657)

FTP will work too, and there are a lot of good options for it on Ubuntu (I prefer proftpd myself).  Pretty much all of them have a simple option to chroot users to their home directories.

---

### Post by Lars Noodén on 2011-05-25
> **DanHorniblow said:**
> Ok, but then how would I set permissions to user1 and user2 so that they only had access to their directory?

You make groups for the users and the put the users into their respective groups and then assign those groups to the document root of their respective web servers.

```

sudo groupadd group1
sudo groupadd group2

groups user1
sudo usermod -G group1,user1,... user1

groups user2
sudo usermod -G group2,user2,... user1

```

Then set the permissions for the web directories:
```

sudo mkdir -p /var/www/site1
sudo chgrp group1 /var/www/site1
sudo chmod u=rwx,g=rwxs,o=rx /var/www/site1

sudo mkdir -p /var/www/site2
sudo chgrp group2 /var/www/site2
sudo chmod u=rwx,g=rwxs,o=rx /var/www/site2

```

Then edit the two vhosts in **/etc/apache2/sites-available** pointed at their respective directories.

---

### Post by Lars Noodén on 2011-05-25
You can then configure **sshd** to use SFTP to box them into their respective web site's folders:

```

Subsystem sftp internal-sftp

Match Group group1
        ChrootDirectory /var/www/site1
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

Match Group group2
        ChrootDirectory /var/www/site2
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

---

### Post by DanHorniblow on 2011-05-25
Thank you very much for all your help so far.

But my next question is, when a user new account is created in ubuntu, could that new user login to MySQL with their ubuntu credentials. Or have i got to duplicate each ubuntu user with a MySQL user?

Thanks in addvance

---

### Post by lykwydchykyn on 2011-05-26
I'm not aware of any way to tie mysql users to login accounts, though that doesn't mean it doesn't exist.  I typically have to create them manually.

Probably the best idea is to figure out everything that each user is going to need and write a "setup script" that will allow you to get all the necessary resources for a user (sftp login, mysql, symlink, etc).

---

### Post by DanHorniblow on 2011-05-26
```

sudo mkdir /home/someuser/www
sudo chown someuser /home/someuser/www
sudo ln -s /home/someuser/www /var/www/someuser

```

I have done exactly this, but when I type "192.168.1.25/webuser1" in a client apache just shows the folder "/var/www/webuser1/" with a link to then to go the publc_html filder in "/home/webuser1/public_html/"

Check screen shot

---

### Post by Lars Noodén on 2011-05-26
> **DanHorniblow said:**
> I am setting up a public facing testing server at my work with use of no-ip.
There will be aprox 20 to 30 users, what would you recomend?

I have setup ubuntu LAMP servers before but only single user.

Then you'll want to work with groups rather than individual users.  Take a second look at the steps in #13 and #14.

---

### Post by DanHorniblow on 2011-05-26
> **lykwydchykyn said:**
> Ok, htaccess files are not needed in this case then.

What you probably want to use is SSH, but you want to chroot jail users to their own directories.  There's a tutorial on that here: 
[http://ubuntuforums.org/showthread.php?t=1057657](http://ubuntuforums.org/showthread.php?t=1057657)

FTP will work too, and there are a lot of good options for it on Ubuntu (I prefer proftpd myself).  Pretty much all of them have a simple option to chroot users to their home directories.

I have decided to use FTP for the users to upload files, as I have only allowed one user to connect to the server via SSH. Is there a FTP program out there that will allow a users to login with the ubuntu credentials?

---

### Post by Lars Noodén on 2011-05-26
> **DanHorniblow said:**
> ...I have only allowed one user to connect to the server via SSH. Is there a FTP program out there that will allow a users to login with the ubuntu credentials?

Since you have SSH running you already have SFTP installed, configured and available.  If you modify the SSHd configuration as described in #14 above, then your users will a) be logging in with their ubuntu credentials and b) only able to see and access their own web folder, and c) be able to use any number of [GUI SFTP clients](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients).

No extra software is needed for SFTP and it is secure.  FTP is insecure, difficult to configure, and requires special software, so it is past time to retire it.

---

### Post by DanHorniblow on 2011-05-26
> **Lars Noodén said:**
> Since you have SSH running you already have SFTP installed, configured and available.  If you modify the SSHd configuration as described in #14 above, then your users will a) be logging in with their ubuntu credentials and b) only able to see and access their own web folder, and c) be able to use any number of [GUI SFTP clients](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients).

No extra software is needed for SFTP and it is secure.  FTP is insecure, difficult to configure, and requires special software, so it is past time to retire it.

Ok, I have enable sftp for the accounts that will be needing it. But i am having a problem that I always run in to and can never find a fix. When I upload large amounts of files using sftp the server disconnect and reconnect at random and files will get skipped, this is quite anoying when I am trying to upload about 700 files.

Any ideas?

---

### Post by Lars Noodén on 2011-05-26
> **DanHorniblow said:**
> Ok, I have enable sftp for the accounts that will be needing it. But i am having a problem that I always run in to and can never find a fix. When I upload large amounts of files using sftp the server disconnect and reconnect at random and files will get skipped, this is quite anoying when I am trying to upload about 700 files.

Any ideas?

Myself, I've only ever transferred small numbers of files so have not encountered the error you describe.

The transfers should be 100% reliable so if they are not, then there is something wrong.  If you can trigger that error consistently then it is worth a bug report in launchpad.

---

### Post by DanHorniblow on 2011-05-26
I only need to transfer these files once, They are all part of a webmail and wiki system that we use which are currently on another server which we are replacing with this one.

Would it be possible to use a USB memory stick as such, I have never used them in ubuntu server before?

---

### Post by lykwydchykyn on 2011-05-26
> **DanHorniblow said:**
> ```

sudo mkdir /home/someuser/www
sudo chown someuser /home/someuser/www
sudo ln -s /home/someuser/www /var/www/someuser

```

I have done exactly this, but when I type "192.168.1.25/webuser1" in a client apache just shows the folder "/var/www/webuser1/" with a link to then to go the publc_html filder in "/home/webuser1/public_html/"

Check screen shot

Whatever folder you link from their home directory will be the webroot for that user.  If you want to use public_html as the folder, then the command would be:
```

sudo ln -s /home/someuser/public_html /var/www/someuser

```
It doesn't matter what you call it, I've seen them called "public_html", "www", "htdocs", etc.  The point is, /var/www is the system's webroot.  Any folders or symlinks under that folder will be accessible by the same relative path, e.g. /var/www/blah/snap.html becomes [http://server/blah/snap.html](http://server/blah/snap.html).

Make sense?

> **DanHorniblow said:**
> I have decided to use FTP for the users to upload files, as I have only allowed one user to connect to the server via SSH. Is there a FTP program out there that will allow a users to login with the ubuntu credentials?

I personally like to use proftpd, it does this by default.  You can set it up to limit users to their home directories easily.

You can't go wrong using SFTP, though.

---

### Post by SeijiSensei on 2011-05-26
For mass transfers like these, I recommend using **rsync**.  A USB drive will work as well.  In that case, I'd recommend creating a tar archive of the source directories, put the tarball on the USB, then extract the tarball to the target.

---

### Post by Lars Noodén on 2011-05-26
+1 for rsync.  That's what I usually use.

The USB stick will work, too, but it will be a little slow.

---

### Post by lykwydchykyn on 2011-05-26
> **DanHorniblow said:**
> I only need to transfer these files once, They are all part of a webmail and wiki system that we use which are currently on another server which we are replacing with this one.

Would it be possible to use a USB memory stick as such, I have never used them in ubuntu server before?

I had a server at one point with either a bad NIC or a NIC that had a buggy driver, and periodically files copied over ssh would corrupt and the transfer would fail.  This is one possibility, but it's hard to say offhand what might be causing this.

You can use a USB stick too.  There are several ways to do it, and I am not sure of the official "friendly" way , but here's more-or-less what I do:

 - plug in usb stick
 - run "dmesg|tail" to see what name it got assigned (sdb or sdc, most likely)
 - mount with mount command:
```

sudo mount /dev/sdb1 /some/empty/folder -o users

```

There are probably easier ways to do it that don't involve sudo, I'm just old-school (and work with other distros that have different tools).


EDIT: oh yeah, and +2 for rsync.  Though if your NIC is corrupting ssh traffic, it'll do that to rsync too.  At least then you'll have some confirmation, though!

---

