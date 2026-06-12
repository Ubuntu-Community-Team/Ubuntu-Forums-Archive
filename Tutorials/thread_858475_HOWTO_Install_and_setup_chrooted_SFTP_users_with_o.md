---
title: "HOWTO: Install and setup chrooted SFTP users with openssh-5.0p1 from scratch"
date: 2008-07-13
forum: Tutorials
---

### Post by lusixhan on 2008-07-13
I've been wanting to set up an encrypted FTP server for a while (sftp) in a chroot'ed environment, so I did a few hours of half-baked-blog parsing and keyboard-pounding in order to figure this out in a way that would work consistently, even if it isn't 100% efficient (your noob-dar should be flashing right about now ;)). Since version 4.8, openssh has had the ability to (fairly) easily chroot sftp users into a specified directory using a new sshd_config directive, ChrootDirectory. The purpose of this guide is to demonstrate how to set up a simple chrooted sftp system from square one implementing this self-contained chroot mechanism (using *only* openssh without the need for rssh), and how to add users under this paradigm.

This guide was tested from start to finish on a fresh install of Kubuntu 8.04.1 on a Dell Inspiron 1501.

**The only version tested under this guide is openssh-5.0p1.**

_(1) Package Installation_

In case you already have openssh (the older repo version) installed, you'll want to get rid of it.

**BE WARNED:** the following command should not only uninstall ssh but will also purge your system of any associated configuration files, so make sure they're backed up if you think you might need them later.

```
$ sudo apt-get purge ssh openssh-*
```

Reboot and make sure your ssh server isn't running (it shouldn't be, it's gone!):

```
$ ps ax | grep ssh # shouldn't show openssh-server
```

It's ok if 'grep ssh' is returned. There might still be a startup script in /etc/init.d which you may want to get rid of (again, back it up if you think you'll need it later):

```
$ sudo rm /etc/init.d/ssh
```

{Ku,Xu,U}buntu doesn't come with the libraries needed to build openssh from source, so you'll need to instruct apt to install everything else necessary to compile an end-package from scratch (in this case, the package is openssh-server) using the following command:

```
$ sudo apt-get build-dep openssh-server
```

There's a "privilege separation" method in openssh which shuffles root-level operations off to a privileged monitor process (stolen shamelessly from the README file). Set it up as follows (ignoring any 'File exists' messages):

```
$ sudo mkdir /var/empty
$ sudo chown root:sys /var/empty
$ sudo chmod 755 /var/empty
$ sudo groupadd sshd
$ sudo useradd -g sshd -c 'sshd privsep' -d /var/empty -s /bin/false sshd
```

Next, you're going to need the actual openssh source package. You can retrieve it from one of a slew of mirrors [here]("http://www.openssh.org/portable.html"), or wget it per the example below. Once downloaded (you did download openssh-5.0p1.tar.gz, right?), the preparation/build process is simple as usual:

```
$ wget ftp://ftp5.usa.openbsd.org/pub/OpenBSD/OpenSSH/portable/openssh-5.0p1.tar.gz # optional (don't bother if you've downloaded it elsewhere)
$ tar xvf openssh-5.0p1.tar.gz
$ cd openssh-5.0p1/
$ ./configure
$ make
$ sudo make install
```

Now we're going to make a quick change to the sftp handler. Installing from source puts your main config file (sshd_config) in /usr/local/etc/ by default; open sshd_config there with your favorite text editor (I use emacs).

```
$ sudo emacs /usr/local/etc/sshd_config
```

Find the line that starts with the word "Subsystem". It should appear in a block that looks something like this:

```
# override default of no subsystems
Subsystem sftp /usr/local/libexec/sftp-server
```

Comment it out like so:

```
# override default of no subsystems
# Subsystem sftp /usr/local/libexec/sftp-server
```

Just beneath it, add this line:

```
Subsystem sftp internal-sftp
```

This causes openssh's sftp server to run in a mode which allows you to chroot someone without having to copy over shells, libraries, etc.
Save and exit your editor.

If you'd like this to start when your computer boots, go edit /etc/rc.local using your favorite text editor.

```
$ sudo emacs /etc/rc.local
```

There should be a line at the end that says "exit 0". Just above this line, add the following:

```
/usr/local/sbin/sshd
```

Save and exit your editor. We're now ready to add users.

-----------------------------------------------

_(2) User Setup_
[B]
This section should be repeated for each user to whom you grant sftp-only access.[/B]

Because sftp (as included with openssh) wraps around ssh, your users are going to need system accounts. Let's prepare a user named johndoe (replace johndoe with whatever new user account you wish). The user johndoe should, in this case, only be able to log in using sftp (as opposed to ssh) once we're done.

```
$ sudo mkdir /home/johndoe
$ sudo useradd johndoe
```

We'll have to set their home directory permissions appropriately. It's important that root owns this and that its group ID is identical to the username, and that the permissions are set so that only root can write:

```
$ sudo chown root:johndoe /home/johndoe
$ sudo chmod 755 /home/johndoe
```

Force the normal login directory just in case:

```
$ sudo usermod -d /home/johndoe johndoe
```

Now give him a password:

```
$ sudo passwd johndoe
```

[INDENT]_(2a) Public/Private Key Authentication (optional)_

Public/private key pairs allow you to log in using signing "certificates" indicating that an entity (in this case, the sftp client-side computer) is implicitly trusted ("friendly"). Configuring OpenSSH to use these allows you, in short, to log in without requiring a password, or using a password of the client's choice. Let's get down to business, then:

On the client-side (i.e., the computer you will be using to access the sftp server), you'll need to generate a public/private key pair. Let us herein refer to the client-side as "johndoe's computer" (johndoes-computer) so there's no question which one we're talking about vs. your server device (sftp-host).

For the moment let's change the owner of the sftp user's home directory so that they can write to it remotely.

```
[sftp-host]$ sudo chown johndoe:johndoe /home/johndoe
```

Unless you are sitting in front of johndoe's computer (in which case this command is redundant), ssh into it (assuming openssh-server is installed on it, either from the repos or via step (1)):

```
[sftp-host]$ ssh someuser@johndoes-ip
```

Now we generate our key pair. Generally speaking 1024 bits is an adequate key length, but you can modify the size (powers of 2 between 1024 and 32768 ) and type (dsa or rsa) at your discretion:

```
[johndoes-computer]$ mkdir -p ~/.ssh
[johndoes-computer]$ chmod 700 ~/.ssh
[johndoes-computer]$ cd ~/.ssh
[johndoes-computer]$ ssh-keygen -b 1024 -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/someuser/.ssh/id_rsa): # Leave blank
Enter passphrase (empty for no passphrase): # leave blank if you want to login without a password
Enter same passphrase again: # leave this blank also if you want to login without a password
Your identification has been saved in /home/someuser/.ssh/id_rsa.
Your public key has been saved in /home/someuser/.ssh/id_rsa.pub.
The key fingerprint is:
01:23:45:67:89:ab:cd:ef:01:23:45:67:89:ab:cd:ef someuser@johndoes-computer # Something similar to this
```

Keep in mind that if you do set a passphrase for your RSH key, that will be your login password. Otherwise you will log in to sftp automatically without requiring one.

(Note: One and only one keypair must be generated per user on johndoes-computer who wishes to log into the remote sftp server via pub/priv key authentication. However, various johndoes-computer users' public keys must be copied over for each sftp account said users hold on the remote server (as described in a moment).)

This generates two files, "id_rsa" and "id_rsa.pub". "id_rsa" is your private key (which is not to leave johndoe's computer) and "id_rsa.pub" is your public key which must be securely copied to the sftp host, into (IMPORTANT!) johndoe's user (sftp) account home directory.

```
[johndoes-computer]$ scp id_rsa.pub johndoe@sftp-host:id_rsa.pub
```

We're now done working on johndoe's computer, and return to the sftp host to add the key to an authorized list and set permissions appropriately, then change the owner of the folder back to root.

```
[sftp-host]$ sudo mkdir -p /home/johndoe/.ssh
[sftp-host]$ sudo chown johndoe:johndoe /home/johndoe/.ssh
[sftp-host]$ sudo chmod 707 /home/johndoe/.ssh # so we can cat into that folder, might have permission problems otherwise
[sftp-host]$ sudo cat /home/johndoe/id_rsa.pub >> /home/johndoe/.ssh/authorized_keys
[sftp-host]$ sudo chmod 700 /home/johndoe/.ssh
[sftp-host]$ sudo chmod 600 /home/johndoe/.ssh/authorized_keys
[sftp-host]$ sudo chown johndoe:johndoe /home/johndoe/.ssh/authorized_keys
[sftp-host]$ sudo mv /home/johndoe/id_rsa.pub /home/johndoe/.ssh/
[sftp-host]$ sudo chown root:johndoe /home/johndoe
```

Done! Continue below with user setup on the sftp host machine.

-----------------------[/INDENT]

_(2) User Setup (continued)_

Set the new user a dummy shell (so they don't have real shell access).

```
$ sudo usermod -s /bin/false johndoe
```

Now we need to indicate that this particular user must be jailed into their home directory. We go back to edit /usr/local/etc/sshd_config ...

```
$ sudo emacs /usr/local/etc/sshd_config
```

... and add the following at the very end of the file:

```
Match User johndoe
      ChrootDirectory /home/johndoe
      ForceCommand internal-sftp
```

As of now, user johndoe should have read access to his home directory. Let's give him a place to upload stuff:

```
$ sudo mkdir /home/johndoe/upload
$ sudo chown johndoe:johndoe /home/johndoe/upload
$ sudo chmod 755 /home/johndoe/upload
```

Done! You can stop here if you want.

-----------------------------------------

_(3) Giving SFTP users read access to some other directory_

As an interesting aside, let's say you (the sysadmin) have a common info/media/data directory you wish to share with your sftp users without actually copying all that data over (or allowing it to be edited/deleted/corrupted). We can do this by mounting it read-only somewhere in their login directory. They're going to need a place to get to it:

```
$ sudo mkdir /home/johndoe/readonly
```

Now we mount our directory of choice (in this example, /home/sysadmin/junk/shared-data) as read-only in said folder:

```
$ sudo mount -r --bind /home/sysadmin/junk/shared-data /home/johndoe/readonly
```

It might help to add the above command to /etc/rc.local so that it happens automatically on startup. Anything added to rc.local will run as root at startup, so there is no need to indicate 'sudo'. In other words, you would add this command to /etc/rc.local as follows (before the 'exit 0' of course):

```
mount -r --bind /home/sysadmin/junk/shared-data /home/johndoe/readonly
```

Note: You cannot mount more than one folder/device/partition/netshare in a particular location. Doing so won't damage anything, but the mount point will only display the object mounted last in sequence.

-----------------------------------------

Reboot your computer. Now you should have the following:

1) You are able to login using the command:

   ```
$ sftp johndoe@sftp-host
```

or using a client which supports sftp.

2) You are unable to navigate above the indicated root directory (this means chroot worked!).

3) You can read from directories, locally-mounted volumes, or files inside the chroot jail (as far as permissions allow).

4) You can read-write within the designated "upload" directory.

5) You cannot login johndoe using ssh.

Hope that helps! :)

---

### Post by GoldWing on 2008-07-18
great howto :guitar:

just something to add: there is a script ssh in /etc/init.d that should be deleted, as it still contains the startup to the standard ssh.
I also can't login anymore with a private key. I checked my sshd_config but can figure out why.

I wrote a little script to create a user with 1 command, as I have to created about 100 sftp users with a lot of 'binded' directories.

---

### Post by lusixhan on 2008-07-21
> **GoldWing said:**
> I also can't login anymore with a private key. I checked my sshd_config but can figure out why.

I've just now added a section about public/private key authentication in response to this :). In your situation I'd guess you might have to regenerate/redistribute your public keys though (worst case, you might have to remove entries from the client's ~/.ssh/known_hosts file). If you already have public keys generated you should just be able to recopy them over to the proper directory on the sftp host. You shouldn't actually have to mess with sshd_config, the catch is putting your authorized_keys files in the right places.

---

### Post by rko618 on 2008-08-03
Thanks for the HowTo lusixhan! It worked great for me (so far). I'll let you know if I have any issues.

Thanks again! I love home simple this method is.

---

### Post by cypher35 on 2008-11-01
Just FYI to anyone interested in doing this under Intrepid...  Most of the above steps are no longer necessary as the openssh-server package is now above version 4.8 in Ubuntu 8.10.

Note also that the openssh config you would want to edit is at /etc/ssh/sshd_config, not /usr/local/etc/sshd_config as it is referenced in the tutorial above.

I followed a hybrid of this guide plus the following guide to get me through the process:
[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

---

### Post by kevdog on 2008-11-02
Could you be more specific on how you did this since for now I am using jailkit to provide these capabilities.

---

### Post by karlry on 2008-12-11
Hi.

Thanks for this very usefull guide. I've used it before to setup Openssh succesfully (I only have 2 months of experience with linux though so I appologize if i'm missing something obvious). 

I'm now trying to do the same thing but using Openssh 5.1 (Not sure if I need new features but I suppose that the latest version always is the way to go). In 5.0p1 There was a step where one ran ./configure etc to do the actual install. openssh-5.1.tar.gz contains a folder called ssh that has no configure script. what different steps do I need to go through to get OpenSSH configured on my Hardy after I've unpacked the files?

Ooops seems like I had the wrong package. I'm ment to download a version with p in it....


Thanks

---

### Post by coronafire on 2009-06-22
Hi, thanks for the walkthrough.

Your mention about a bind mount to give external folder access gave me an idea about getting around the annoying top level folder owned by root problem.

 I set up a new folder /var/sftp and made a folder in it for each user I wanted to give sftp access to, ie /var/sftp/webadmin

This folder was then made the home folder for the user (called webadmin)
```
usermod -d /var/sftp/webadmin webadmin
```

In this folder a made another folder for each directory I wanted them to access:
```
mkdir  /var/sftp/webadmin/site1
mkdir /var/sftp/webadmin/site2
```

Then set up permissions (my web server user is called www-data):
```
chown root:root /var/sftp
chown root:root /var/sftp/webadmin
chown webadmin:www-data /var/sftp/webadmin/site1
chown webadmin:www-data /var/sftp/webadmin/site2

chmod -R 755 /var/sftp

```

and then use a bind mount to link these site1/2 folders to the actual web folders in /var/www/*
This way the top level directory is /var/sftp/webadmin which is read only, and I can give full access to the site folders.

Also, to automatically mount on boot, I feel it's more consistent to add it to fstab:

```
/var/www/site1    /var/sftp/webadmin/site1           none    bind  0  3
/var/www/site2    /var/sftp/webadmin/site2           none    bind  0  3
```

(note that this is read/write access, not read only as the original posts bind mount was used for)

It works a treat for me!

Andrew

---

### Post by colossus73 on 2009-12-30
Hi,

thank you for the detailed guide but what about this one?

[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

Dooes one really obtain a chroot as stated in the article?

---

### Post by blacksunseven on 2010-04-16
> **lusixhan said:**
> -----------------------------------------

_(3) Giving SFTP users read access to some other directory_

As an interesting aside, let's say you (the sysadmin) have a common info/media/data directory you wish to share with your sftp users without actually copying all that data over (or allowing it to be edited/deleted/corrupted). We can do this by mounting it read-only somewhere in their login directory. They're going to need a place to get to it:

```
$ sudo mkdir /home/johndoe/readonly
```

Now we mount our directory of choice (in this example, /home/sysadmin/junk/shared-data) as read-only in said folder:

```
$ sudo mount -r --bind /home/sysadmin/junk/shared-data /home/johndoe/readonly
```

It might help to add the above command to /etc/rc.local so that it happens automatically on startup. Anything added to rc.local will run as root at startup, so there is no need to indicate 'sudo'. In other words, you would add this command to /etc/rc.local as follows (before the 'exit 0' of course):

```
mount -r --bind /home/sysadmin/junk/shared-data /home/johndoe/readonly
```

Note: You cannot mount more than one folder/device/partition/netshare in a particular location. Doing so won't damage anything, but the mount point will only display the object mounted last in sequence.

-----------------------------------------

I used to have this set up just fine, having the appropriate entries in my /etc/fstab file like the example below:
```
UUID=XXXX /media/dir1 ext3 defaults 0 0
/media/dir1 /home/guest/dir1 none ro,bind 0 0
```

Since upgrading to 10.04 Beta 2, this no longer works and attempted mounting spits out that the directory is still mounted read-write. Any suggestions?

---

### Post by narcisgarcia on 2010-10-10
I've seen your guide for chrooted SFTP, and I've learnt from a lot of tutorials as yours. Here my compendium to configure better clients and servers:

[http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses](http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses)

(special care of users and permissions)

---

### Post by narcisgarcia on 2012-10-30
A domain name has changed for Lapipaplena. Please update the link for:
[http://wiki.gilug.org/index.php/How_to_mount_SFTP_accesses](http://wiki.gilug.org/index.php/How_to_mount_SFTP_accesses)

---

