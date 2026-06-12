---
title: "problem in file permissions"
date: 2011-05-14
forum: Server Platforms
---

### Post by NabiVakili on 2011-05-14
I'm new in Ubuntu! I searched and found how to install Apache on Ubuntu 10.04.
I configured Apache server in Ubuntu 10.04 successfully, also I prepared a FTP server on it  for transferring files to server.

there is two user in the server. The root and X.

The X user transfers files by FTP to server (into var/www), the file permission needed in this folder is 755 but when X transfers files into the "www" folder, file permissions is 600.

How can I configure the server to solve this problem. I want to have 755 file permissions for every new and old file in "www" folder automatically.

I tried these :

[LIST]
[*]I used chmod command and changed permissions manually, It solved the problem, but for every new file that transferred I should execute it again, and sometimes I don't know when X want to change a file in "www" folder!
[*]I changed the "www" folder permissions to 755, I thought when the parent folder has 755 permissions , every new file in the child folders will have 755. but it's not right!
[*]The owner of var/www folder was root by default, I changed it to X but the problem is still exist.
[/LIST]
sorry for my poor English!
Thanks

---

### Post by matthewgreyling on 2011-05-14
I think you may need to run the chmod command on /var/www and also on /var/www/* to get the child folders to have the same permissions.

---

### Post by NabiVakili on 2011-05-14
I know that.
as I said, I did that, but I don't know when new files has been transferred until I use chmod to change file permissions.

after a new transfer, the X user emails me and I change file permissions manually.
But I want to find a better way : with every new file transfer, file permissions becomes 755 instead of 600 automatically.

---

### Post by doas777 on 2011-05-14
one answer to this is [umask]("http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html"), but it can be complicated. check the link to see which configurations match your needs.

---

### Post by NabiVakili on 2011-05-14
I checked that link.
I inserted this line to .bashrc :
```
umask 022
```
now the default permission should be 755.

but for a new folder permission is 700 and for a new file permission is 600

:(

---

### Post by doas777 on 2011-05-14
apache appears to have it;s own mechanism for setting it;s personal umask, and is probably overriding your setting. 

check here:
[http://ubuntuforums.org/showthread.php?t=549457](http://ubuntuforums.org/showthread.php?t=549457)

---

### Post by NabiVakili on 2011-05-15
I checked it and I used "umask 022" as same as that post.

But the problem remains yet

---

### Post by Lars Noodén on 2011-05-15
The following might help

```

# make a group
sudo addgroup webmasters

# add yourself to the group
sudo usermod -G webmasters,adm,dialout,cdrom,plugdev,lpadmin,sambashare,admin nabivakili

# log out and log in again so that the group permissions take effect

# assign the web server directory to that group
sudo chgrp -R webmasters /var/www

# make the directory writable by that group, 
# set also the sticky bit so that file are created in that group
sudo chmod g=rws /var/www

```

---

### Post by bab1 on 2011-05-15
> **NabiVakili said:**
> I checked it and I used "umask 022" as same as that post.

But the problem remains yet

You can define an Apache only umask inside **/etc/apache2/envvars** on Debian, and Ubuntu systems.

---

### Post by NabiVakili on 2011-05-16
#8 : 
[INDENT]I used step by step that code, but it was not a solution.

[/INDENT]#9 : 
[INDENT]I had wrote "umask 022" in envvar file.

[/INDENT]anyone knows any new solution?

---

### Post by Lars Noodén on 2011-05-16
> **NabiVakili said:**
>  
[INDENT]I had wrote "umask 022" in envvar file.

[/INDENT]anyone knows any new solution?

Using 002 instead will give the files created by the web server group write access.

---

### Post by NabiVakili on 2011-05-16
I got new problem!!
I used #8 codes, and now when I want to use "sudo" I get this problem : 

> nabivakili is not in the sudoers file.  This incident will be reported.

I think it's because I changed the group of my user name to "webmasters" [Lars said in post #8]

I searched and found that I should change the group of my user name to %admin using usermod command, but it says there is no %admin group!

---

### Post by Lars Noodén on 2011-05-16
> **NabiVakili said:**
> I got new problem!!
nabivakili is not in the sudoers file. This incident will be reported. 


If you have the default settings from ubuntu then you must be in the group admin to use sudo.

What does the following give for output?

```

groups nabivakili

```

I think I spot the error in post #8.

---

### Post by NabiVakili on 2011-05-16
when my username was in the group of webmasters, it shows : 
```
nabivakili : nabivakili webmasters
```

and by using "sudo" I got this message :
> nabivakili is not in the sudoers file.  This incident will be reported.

Then I tried to fix the problem, so I used this command : 
```
 usermod -G root nabivakili
```

and then : 
```
nabivakili : nabivakili root
```

but still I get the same error message.

what should I do now?

---

### Post by Lars Noodén on 2011-05-16
NabiVakili, the correct line in #8 should have been:

```

sudo usermod -G webmasters,adm,dialout,cdrom,plugdev,lpadmin,sambashare,admin nabivakili

```

Apologies for the mistake.  If things had gone worse it could still be corrected using the rescue option on the installation CD.  Use it to open a session on the local hard disk and reset the groups for your admin user.

I had tested the line before using it, but on an account that was only a member of a single group, not a member of multiple groups so I missed what should have been obvious.

---

### Post by NabiVakili on 2011-05-16
I solved this problem.
I changed my group to admin : 
```
usermod -G admin nabivakili
```

it fixed.

what's "www-data" ? It's a group in Apache?
Can I use this group to solve the problem?

---

### Post by Lars Noodén on 2011-05-16
> **NabiVakili said:**
> 
what's "www-data" ? It's a group in Apache?

It's a group for the web server itself.  No users should be members.  Only directories were you want the web server itself to write should belong to it.

---

### Post by Lars Noodén on 2011-05-16
> **NabiVakili said:**
> I solved this problem.
I changed my group to admin : 
```
usermod -G admin nabivakili
```

it fixed.



If your confidence is not too shaken, then the steps in post #15 will restore things to the full list of groups.

---

### Post by NabiVakili on 2011-05-16
I used post #15, thank you.
It restored everything to the default settings.

I really disappointed from solving the main problem ...

---

### Post by Lars Noodén on 2011-05-16
> **NabiVakili said:**
> I really disappointed from solving the main problem ...

To get the file permissions to be 755, the usmask for the account writing the file must be 0022.

---

### Post by NabiVakili on 2011-05-16
I wrote 0022 in the envvar file,after restarting Apache, I used "touch test.txt" and the permission for this new file is 644

---

### Post by NabiVakili on 2011-05-16
I wrote "umask 0022" in envvar and in .bashrc file, after rebooting the server, I used "touch test.txt" to make a new file in var/www/ but the permission for this new file is 644.

---

### Post by Lars Noodén on 2011-05-16
> **NabiVakili said:**
> I wrote 0022 in the envvar file,after restarting Apache, I used "touch test.txt" and the permission for this new file is 644

644 is what you want, 755 is for the directories.  The regular data files should not be made executable.

---

### Post by NabiVakili on 2011-05-16
I made a new file using the command line,It's ok,but as I said in first post there is a FTP service on this server that another user uploads some php files into var/www/ . He asked me to configure server in some way that for every new uploading and every new file in that directory, the permissions becomes 755 instead of 600
I uploaded some php files into the var/www using my username, but the permissions is 600 for all of them.
I need a solution that makes the permissions for every new file and folder in var/www/ becomes 755 automatically.

---

### Post by Lars Noodén on 2011-05-16
(Files should be 644, directories should be 755)

If you use [SFTP](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SSH_File_Transfer_Protocol_.28SFTP.29), you can set the sftp-server to a particular umask by setting that in [sshd_config](http://manpages.ubuntu.com/manpages/natty/en/man5/sshd_config.5.html).

Edit:
```

Subsystem sftp internal-sftp -u 0002

```

Combine that with the steps in [#8](http://ubuntuforums.org/showpost.php?p=10818066&postcount=8).

---

