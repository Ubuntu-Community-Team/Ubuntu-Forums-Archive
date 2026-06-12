---
title: "installed lamp, have questions!"
date: 2007-07-22
forum: Server Platforms
---

### Post by lunaz on 2007-07-22
well the install went good i guess. :P
i installed vsftpd & got openssh-server working. yaaay!

questions so far:

how do i add users to vsftpd? i want to the the ONLY user that has access to this. either locally or from the internets.

making an index.html file in /var/www/ gives permission denied!

is there anything i need to do to keep things secure? i'm still windows paranoid. :(

btw, i'm 6.06 command line only; no desktop yet, till roommate gets back home.

---

### Post by zanglang on 2007-07-22
There are two ways to do this:
1. If you enable "local_enable" in /etc/vsftpd.conf any local user on your Ubuntu system can login with their Ubuntu user name and password. Just make sure that this user has file permissions to /var/www. This is the easiest way.

2. The sophisticated way is to set up 'virtual users' that don't actually exist in your Ubuntu system, but are mapped to a certain existing user. You can read this documentation for more details.
> /usr/share/doc/vsftpd/EXAMPLE/VIRTUAL_USERS/README.gz

If you have time, read the other files in the vsftpd documentation folder as well, especially FAQ.gz and SECURITY, they're very important. ;)

---

### Post by elst on 2007-07-22
> **lunaz said:**
> 
how do i add users to vsftpd? i want to the the ONLY user that has access to this. either locally or from the internets.


If you are the only user then you don't actually need an FTP service at all - SSH includes FTP-like file transfer, covered by the same security as the remote terminal access. On Windows, the FileZilla FTP client and WinSCP both support SSH file transfer.

Often the largest weakness of a Web server is the Web applications that it runs. Products like PHPMyAdmin have been exploited in the past, so you need to run a system update regularly, and keep up with security releases for any product that you install by hand. 

If you write your own code, then be sure to read up on secure programming: the basics are simple, but many programmers don't know them...one survey found that 15% of sites used code that was vulnerable to "SQL injection" attacks, even though it is easy to write code that is not vulnerable to such exploits.

I should probably add this to my sig or something:

[http://www.elsn.org/main/LinuxSecurityBasics]("http://www.elsn.org/main/LinuxSecurityBasics")

---

### Post by lunaz on 2007-07-22
thanks for the replies. :P lots of questions, all of them noob: :D

i removed vsftp. is there a way i can use putty to make files on /var/www/ or transfer them from this computer to the server? if not i'll go get filezilla. :)

i found this command while searching for /var/www/ permissions, but before i use it i want to make sure i understand it... :P

```

sudo chown yourusername:www-data -R /var/www/
sudo chmod 770 -R /var/www/

```

this would put my username in a group called www-data & allow me + that group to rwx, but everyone else no permissions to the /var/www dir?

should i enable the root account? right now it's just me on there.

since a server is on all the time should i stay logged in as my username all the time? or what?

is there any noob friendly books i can pick up to learn more about this?

---

### Post by zanglang on 2007-07-23
> **lunaz said:**
> thanks for the replies. :P lots of questions, all of them noob: :D

i removed vsftp. is there a way i can use putty to make files on /var/www/ or transfer them from this computer to the server? if not i'll go get filezilla. :)
Yep, for transferring you use 'scp' or 'sftp' for that. I think if you're not that familiar with the commandline yet Filezilla would be a great GUI choice for accessing your server via SFTP. Otherwise you can just login via SSH with PuTTy, directly edit files with vim, nano or your terminal editor of choice.

> i found this command while searching for /var/www/ permissions, but before i use it i want to make sure i understand it... :P

```

sudo chown yourusername:www-data -R /var/www/
sudo chmod 770 -R /var/www/

```

this would put my username in a group called www-data & allow me + that group to rwx, but everyone else no permissions to the /var/www dir?
Close! It means you're changing the ownership of all files inside /var/www to yourself and the www-data group. The -R means recursive, so you're not just changing the folder but subfolders and files in it as well. The first digit in the chmod parameter is for you, the owner. 7 = read, write and execute. Second digit is group, which you assigned to www-data. Third digit is everyone else, which you've specified no read-write-execute access. So yes, only you and other users in the www-data group (e.g. the user your webserver will run as) will be able to access the files inside /var/www. For more info read this:
[http://en.wikipedia.org/wiki/File_system_permissions](http://en.wikipedia.org/wiki/File_system_permissions)

> should i enable the root account? right now it's just me on there.

since a server is on all the time should i stay logged in as my username all the time? or what?
You can... but you really don't need to. Just 'sudo' whenever you need admin privileges. 

> is there any noob friendly books i can pick up to learn more about this?
I would recommend Apress Beginning Ubuntu Linux - From Novice to Professional and O'Reilly's Ubuntu Hacks - Tips and Tools for Exploring, Using and Tuning Linux.

---

### Post by lunaz on 2007-07-23
sweet, ty for the info :D will read this tomorrow asap.

---

