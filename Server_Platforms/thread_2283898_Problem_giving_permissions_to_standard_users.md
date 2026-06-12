---
title: "Problem giving permissions to standard users"
date: 2015-06-25
forum: Server Platforms
---

### Post by peter1897 on 2015-06-25
I want to give a permission to standard users on Ubuntu server to read and write in this directory and all files inside it: /var/www/html

I created the group **webdev** and added the standard users **mark** and **alec** to the group. Then i changed the ownership of the **html** folder and the files inside it with this command: **chown -R :webdev html**. Then i changed the permissions for the directory and the files inside it with this command: **chmod -R 660 html**

```
drwxr-xr-x  3 root root   4096 Jun 25 08:19 ./
drwxr-xr-x 13 root root   4096 Jun 25 08:19 ../
drw-rw----  2 root webdev 4096 Jun 25 13:40 html/
```

I changed the permissions for group **webdev** to read and write but users **mark** and **alec** can't even access the directory **html**, i get "permission denied". Why is this happening? Can i make the both users to write and read in this directory without adding them to the **sudo** group?

---

### Post by Frogs Hair on 2015-06-25
Moved to *Server Platforms *

---

### Post by Lars Noodén on 2015-06-25
The directory /var/www/html will have to be 775 or, better yet, 2775 with the group setGID bit on.  Other needs read access because the web server needs to read the files.    The files can be 664, because while the group needs read-write access, the web server needs to be able to read the files and does that as Other.  In GNU/Linux, if you are sharing a directory as a group, you need the setGID bit on so that files added to that directory inherit the right group membership.

---

### Post by peter1897 on 2015-06-25
Thanks, i changed the permission for **html** directory with this command **chmod 775 html** and now the two users can read and write inside the directory.

Is this the right command to set the group setGID bit on:

**chmod g+s webdev**

---

### Post by Lars Noodén on 2015-06-25
> **peter1897 said:**
> Thanks, i changed the permission for **html** directory with this command **chmod 775 html** and now the two users can read and write inside the directory.

Is this the right command to set the group setGID bit on:

**chmod g+s webdev**

It would be **chmod g+s  /var/www/html** if the target is  /var/www/html and that directory already has the group webdev.

---

### Post by peter1897 on 2015-06-26
If i understand correctly setGID command assign the group **webdev** to every new created file and directory inside the html directory, so every user that belong to this group can modify the file or directory, correct?

Also, why when user mark, for example, create a new file in **html** directory the permissions for the file are -rw-rw-r-- (664) and not 775 because i had run this command for the html directory **chmod -R 775 html**?

---

### Post by Lars Noodén on 2015-06-26
It's permission in two parts: Yes, setGID means that the group, in this case webdev, is applied to every new file or directory created there.  GNU/Linux systems have to be told to do that, BSD systems naturally inherit the group without needing that bit set.  And, yes, if that directory or the files in it have write permission for that group, any member of that group can write to the file or directory.  However, some of that is dependent on the user's umask settings.  umask is why new files are 664 and not 644 or 444 etc.  (FWIW only directories and executables need the exec bit set, regular files don't)  umask can be changed but applies to all of the user's activities not just the one directory or set of directories.  I think the whole arrangement could be better, but we have what we have.

---

### Post by peter1897 on 2015-06-26
Thanks, that makes some things more clear.

I have another problem. I want to give ssh access to the user mark. So far only the user Ubuntu have ssh access to the ubuntu server. Ubuntu is member of the sudo group, mark is not.

To create the key pair i switched to user mark and run **ssh-keygen -t rsa**. I didn't enter a pass phrase for the key. After this i downloaded the private key with WinSCP to my local machine which is Windows 7, connection through Ubuntu user sftp account. On my Windows 7 machine i am using Cygwin to connect to the Ubuntu server but when i try to connect using the private ssh key for user mark i get error **Permission denied (publickey)**

The permissions for the public key on Ubuntu server are this:

```
-rw-r--r-- 1 mark mark  402 Jun 26 08:27 mark_key.pub
```

Also, in user mark home directory i don't see .ssh directory like in the Ubuntu user home directory.

What could be the reason for this Permission denied error?

---

### Post by darkod on 2015-06-26
1. All users should have ssh access by default unless configured otherwise. First try ssh access by password to see if it works. Whether a user has sudo rights is another matter, not related to his ssh access.

2. That's not how you create ssh key for remote access. You started with creating the key on the server you want to access. You need to create the key on the client that you wish to access from.

In your case the client seems to be windows. Why are you using cygwin? Cygwin is ssh server to allow connections to that machine, you don't need it to make connections from that machine. Simply client sw like putty is enough.

For creating ssh key on windows you can use puttygen and upload/paste that key in /home/username/.ssh/authorized_keys of the user you want to use to connect. Note that ssh is strict with security and you better make the .ssh folder with permissions 700 and the files inside 600.

---

### Post by peter1897 on 2015-06-26
The ssh access by password doesn't work. If i type **ssh mark@ip_address** i get the same error: Permission denied (publickey)

I made a mistake to edit the sshd_config file and added the line **AllowUsers ubuntu mark** and after this i couldn't access the server with neither of the user accounts, getting the same permission denied error. It was good it is a test vps server, i don't know how i could gain access again if it was my real vps server.

---

### Post by darkod on 2015-06-26
I haven't used that option but it looks correct. The problem would be if you also disabled ssh by password. Did you do that?

Leave the pass login enabled until you set up all keys, then test key access for all needed users, and then disable pass login for ssh.

---

### Post by peter1897 on 2015-06-26
The password login was disabled by default. These lines were set to "no" and i changed them to "yes":

```
ChallengeResponseAuthentication
PasswordAuthentication
```

Now when i type **ssh mark@ip_address** and then the password for mark i can login.

Also, i generated key pair with putty generator on my Windows machine. Then on the ubuntu server i created .ssh folder in mark home directory and set the permissions for directory to 700. After this i uploaded the public key to .ssh directory and set the permission for the key to 600. 

**drwx------ 2 mark mark 4096 Jun 26 16:40 .ssh/**

**-rw------- 1 mark mark  468 Jun 26 15:56 mark_key.pub**

Now i am able to connect to the Ubuntu server with user mark account with this command:
**ssh -i mark_key.ppk mark@ip_address**

But before connecting i get this message: **Enter passphrase for key 'mark_key.ppk':** and i press Enter because i didn't set passphrase for the key file. But then i get another message **Password:** and i have to enter the password for the user mark and after this i am able to connect.

Why i am getting these messages? When i login with the Ubuntu user account i don't get messages for key passphrase and user password.

---

### Post by Lars Noodén on 2015-06-26
> **peter1897 said:**
> Why i am getting these messages? When i login with the Ubuntu user account i don't get messages for key passphrase and user password.

I can't address PuTTY on Windows or how / whether the keys it generates are usable.  But what is happening when the SSH server asks you for the password is that login process is not using the key.  Since the key itself never ever leaves the client, then problem with the key, if everything else is set up ok, would be with the client.   In order to be set up ok, you need your public/private key pair.  The public key gets copied to the server and inserted into ~/.ssh/authorized_keys on a line of its own.  How did you get the public key into authorized_keys on the server for the user mark?

---

### Post by peter1897 on 2015-06-26
I didn't have .ssh directory nor authorized_keys file in mark home directory. I created the .ssh directory and then uploaded the public key file **mark_key.pub** in the .ssh directory without changing its name. Now i changed the name of the file to authorized_keys but i still can't connect with user mark using the key file authentication.

The public key file generated by putty look like this:

```
---- BEGIN SSH2 PUBLIC KEY ----
Comment: "rsa-key-20150626"
AAAAB3NzaC1yc2EAAAABJQAAAQEAjTtebJCGIfHHD2gnExyDqszmVO+MoOVjt6C9
u5oEfH9bViFi8H2/QBoxb5elnAIOzQPZlV+Zv9HAOyvnxoeI2AE1AopbrOH6B765
iwKPiFr5AZlVHehRYFEYw/SJ8Q+cwOk+iIa24k8TDlK7SGeFuXLRls2hAzMuRyES
IRZSydfWjug0ycbd8DbB0UVfnxVKYxOuJwZzrqfKldbm+PbcMvMuePlQxs8ANIlB
Mt7lBzIvn85/dbcwTnUDztK/Q60I1rsTJC3XgCkwTvUkEAtUIpacK7Gk4jqsIKM2
95FwG/trrW8LyIrfjJs+740/PubMW87YnpGZC+8iHk15p2Ep2w==
---- END SSH2 PUBLIC KEY ----
```

---

### Post by Lars Noodén on 2015-06-26
There is something wrong with the PuTTY-generated key.  I'm not sure but there might be a way to convert it to a normal public key.   

It should looks something like this:

```

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC3ixscPCPENMc8WS6fOAqqSOd7s8IVsbqoT2tMzMwEB58KVWR9A4UKiOLZiHnzIMC9zzObk+56AcXRJeVS1kVGq+UrlnIOstxX2vjel8SAARh1zAUMm1opla5IpBoGqLMF4Mg37P3rqMRFYNgS/iNZGnwxUhMYKbVeyVS8cn2Cqsbukgt1Pz9ZwbTBimMcnoHZWY1kEaqtvl1JyO3RQYFQZhkwIqPB3ygwbLXV6UeQUJJmaTf7gC+cbunPlH+oVX4gYFlbQKmDElrLrbOFQAt2WEfCHgHfoFU6e7mL+Dn4vUM8SQZTUEUSAtgZn1EuAKVMTyx3PX3kHg47YkOYug7Z mark@somemachine.somewhere

```

The tail end is actually a comment and though the default is often user name and machine name I'd recommend setting explicitly to something which will help you identify it over on the client.

---

### Post by Lars Noodén on 2015-06-26
Can you strip out the == signs and the linebreaks to make it like this and try it in authorized_keys?

```

ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEAjTtebJCGIfHHD2gnExyDqszmVO+MoOVjt6C9u5oEfH9bViFi8H2/QBoxb5elnAIOzQPZlV+Zv9HAOyvnxoeI2AE1AopbrOH6B765iwKPiFr5AZlVHehRYFEYw/SJ8Q+cwOk+iIa24k8TDlK7SGeFuXLRls2hAzMuRyESIRZSydfWjug0ycbd8DbB0UVfnxVKYxOuJwZzrqfKldbm+PbcMvMuePlQxs8ANIlBMt7lBzIvn85/dbcwTnUDztK/Q60I1rsTJC3XgCkwTvUkEAtUIpacK7Gk4jqsIKM295FwG/trrW8LyIrfjJs+740/PubMW87YnpGZC+8iHk15p2Ep2 Comment: "rsa-key-20150626"

```

---

### Post by darkod on 2015-06-26
I didn't mention this when I saw it in one of your earlier posts, and you did it again. You DO NOT upload the .pub file, it doesn't work like that. All you need is the key in OpenSSH format (the line starting with ssh-rsa, all of it, be careful to copy it perfectly).

When you created the key with puttygen (or when you open it now with Load), in the center it gives you the ssh-rsa value you need (it actually says Key in OpenSSH format to copy to remote host, or something like that).

What you need to do is login as mark, delete the id_rsa.pub and create authorized_keys file inside .ssh. Make the file 600. Open it, and copy/paste the openssh value from puttygen window. Make sure it's correct. Save and close the authorized_keys file.

In putty when trying the connection you need to go into the Connection-SSH-Auth option and load the .ppk private key puttygen created. Also you can go in Connection-Data and set the login username (mark). That way it will use it automatically and will not ask you for username nor password.

See how that goes...

PS. Attaching puttygen image, note the whole center part saying this is the value you need to paste into authorized_keys. Of course I deleted the info... :)

PPS. [COLOR=#ff0000]I just reread the last few posts and noticed you renamed the .pub in authorized_keys. It can not work like that[/COLOR], putty saves the keys in PEM format unless I'm wrong. The value/key it gives you inside the puttygen window (look at attachment) is the value you need to paste in authorized_keys. You can not simply rename the .pub file.

On the other hand, I also noticed you said you tried ssh -i... Where are you trying that from, cygwin? In windows you simply open putty and put in the details for the connection you want to establish. I have never tried it in any form of ssh -i in command prompt...

---

### Post by Lars Noodén on 2015-06-26
darkod, the screen shot shows only [deprecated 1024 bits](http://arstechnica.com/uncategorized/2007/05/researchers-307-digit-key-crack-endangers-1024-bit-rsa/).  More is needed these days, at least 2048 bits.

---

### Post by cariboo on 2015-06-26
There is a pretty good howto for Key-based ssh  login using putty [here]("https://www.howtoforge.com/ssh_key_based_logins_putty"). When I used putty, I used this method login, to my server. The one thing I would do different, is that the article mentions setting the user as root, seeing as the root account isn't enabled on Ubuntu or any of the flavours, I'd suggest using your regular user name, and use sudo when you need to escalate privileges.

---

### Post by darkod on 2015-06-26
> **Lars Noodén said:**
> darkod, the screen shot shows only [deprecated 1024 bits]("http://arstechnica.com/uncategorized/2007/05/researchers-307-digit-key-crack-endangers-1024-bit-rsa/").  More is needed these days, at least 2048 bits.

Point taken Lars. I wanted to make another example with the attachment, where to find the ssh key value to paste. The bit count is different topic.

---

### Post by peter1897 on 2015-06-26
I finally made it work. The keys generated with putty for some reason didn't work so i delete them. 

Then i used Cygwin and generated new key pair, mark.pub and mark, with the command: **ssh-keygen -t rsa**. Then i uploaded mark.pub to /home/mark/.ssh and renamed the file to authorized_keys. After this i was able to connect with user mark through key authentication. I have to say that  renaming the public key file, in my case mark.pub, to authorized_keys, instead of pasting the key also works.

Another question: Is it possible to disable the login with password authentication for all users but enable it only for specific users?

---

### Post by Lars Noodén on 2015-06-26
Yes.  You can disable the login with password authentication for all users but enable it only for specific users, or for specific subnets, or specific users on specific subnets using the [Match](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html) directive.  Set the rules you want to apply to all users then use **Match** to set the rules you want to apply to a particular group.  In general it is more maintainable and definitely more scalable to work with groups for permissions rather than lists of individual users.  Be sure to test in a second terminal and leave the original terminal logged in until you have verified that you can get back in.

---

### Post by darkod on 2015-06-26
> **peter1897 said:**
> I finally made it work. The keys generated with putty for some reason didn't work so i delete them. 

Then i used Cygwin and generated new key pair, mark.pub and mark, with the command: **ssh-keygen -t rsa**. Then i uploaded mark.pub to /home/mark/.ssh and renamed the file to authorized_keys. After this i was able to connect with user mark through key authentication. I have to say that  renaming the public key file, in my case mark.pub, to authorized_keys, instead of pasting the key also works.

Another question: Is it possible to disable the login with password authentication for all users but enable it only for specific users?

FYI, this worked from cygwin because cygwin with ssh-keygen creates the key in openssh format directly. So uploading the .pub file and renaming it can work.

Putty keys are different, but it also works. Not with renaming though. I am using them for connections to many servers.

As I mentioned earlier about cygwin, the only implementations I have seen are to allow ssh access to the windows computer. It's rarely used for connection from that computer. You don't need to install ssh server for that (and cygwin is a ssh server, if you check Services there should be a ssh server service). But if you like using it, it's up to you.

---

### Post by peter1897 on 2015-06-27
I am trying to confine the user mark in this directory /var/www/html and make it have only sftp access.

I run this command to forbid him login with ssh:
**sudo usermod -s /usr/sbin/nologin mark**

Then i changed his home directory with this command:
**sudo usermod -d /var/www/html mark**

This is the info about user mark in /etc/passwd

```
 mark:x:1001:1001:,,,:/var/www/html:/usr/bin/nologin
```


But now the key authentication login for mark doesn't work because the .ssh folder is in the old home folder /home/mark. Is it possible to make user mark login with key authentication without moving the .ssh folder from the old home folder /home/mark to the new home folder /var/www/html?

---

### Post by Lars Noodén on 2015-06-27
You should be able to connect with a key and SFTP even if the user is chrooted, but you need to change the home directory back to normal.  

```

Match Group webusers
        ChrootDirectory /var/www/html
        ForceCommand internal-sftp

```

That will chroot all the users in the group webusers into the /var/www/html directory and force them into using SFTP.  

Or another way, if there is no home directory, ... If you modify [sshd_config with AuthorizedKeysFile](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html), you can add a second authorized key file somewhere else in a new folder say */etc/ssh/authorized_keys/* and then give each chrooted user a file with their user name containing the key(s):

```

Match Group webusers
        ChrootDirectory /var/www/html
        ForceCommand internal-sftp
        AuthorizedKeysFile /etc/ssh/authorized_keys/%u

```

sshd substitutes %u with the real user name as needed.  So the user 'mark' would get the file '/etc/ssh/authorized_keys/mark' for their key(s) if 'mark' is in the group 'webusers'.

---

### Post by peter1897 on 2015-06-27
I think i made it work now. I changed back the home directory for user mark to its original location:
```
mark:x:1001:1001:,,,:/home/mark:/usr/bin/nologin
```

Then i edited the sshd_config file and added this line in the end of the file:
**Subsystem sftp internal-sftp**

And after this these lines:

[B]Match Group webdev
ChrootDirectory /var/www/html
ForceCommand internal-sftp[/B]

I want mark and other users that belong to the webdev group to be able to access the html folder through sftp and be confined there.

Now when i type **sftp -i mark mark@ip_address** user mark is able to connect through sftp with key authentication.

My other concern is the security. Is it possible to prevent users that belong to the group webdev do a harm, like deleting files and folders in html directory, because they will have read and write permissions?

---

### Post by Lars Noodén on 2015-06-27
If they can write (edit), they can delete even if it is to just zero out the contents of the file.  If you are only concerned about them removing files or directories then you /could/ whitelist or blacklist SFTP protocol requests with some work.  I see 'remove' and 'rmdir' there:

```

$ /usr/lib/sftp-server -Q requests
open
close
read
write
lstat
fstat
setstat
fsetstat
opendir
readdir
remove
mkdir
rmdir
realpath
stat
rename
readlink
symlink
posix-rename
statvfs
fstatvfs
hardlink
fsync

```

But one can go to a lot of effort and still not cover all the bases.  It comes down to being mostly a social problem not a technical one.  Either you can trust them or you can't.

---

### Post by Lars Noodén on 2015-06-27
Another way, if you want to track changes, is to store your web site in a version control system like Git or SVN.  That way you can see who changed what and even roll back specific changes.  

Yet another way which is a little in between would be to have them upload only to a mirror site and then once changes are verified push them out to the main site by key personnel.  The mirror site does not have to be public.

---

### Post by peter1897 on 2015-06-27
Thanks, i will look in these security options.

What should be the permission for the main folder that contain the website files /var/www/html and which group should be the owner - webdev or root? I read in some tutorials that the main folder - html, should be owned by root user and group root, but if i set the user and group owner to root and the permission to 755 the sftp user mark can connect to the html directory but can not write inside it:

```
drwxr-xr-x  2 root root 4096 Jun 27 07:53 html/
```

And if i set the permission for html directory to 775 the user mark can't connect to the html directory at all.

What should be the right permission, and user and group owner for the main directory that contains the website files?

---

### Post by Lars Noodén on 2015-06-27
One way is that you could chroot to /var/www and then have the SFTP subsystem automatically change the directory:

```

Match Group webdev
        ChrootDirectory /var/www
        ForceCommand internal-sftp -d html

```

But that could give access to anything under /var/www so if that is not what you want, then you have to plan the directories a little more and maybe modify the web server's DocumentRoot to point to the new subdiretory.

Edit:  The target of [ChrootDirectory must be owned by root and not writable by anyone else](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html).  However, any files or subdirectories can be writable.

---

### Post by peter1897 on 2015-06-27
I changed the chroot directory to /var/www and also the group owner of html directory from root to webdev, and set the permission for html directory to 775. Now sftp user mark can read and write in html directory.

That means the folder that contain the website files should not be owned by both, root user and root group. I guess some tutorials about this on internet are misleading.

---

### Post by Lars Noodén on 2015-06-27
Yeah, many leave it out or are unclear.  Though it's in the manual page for sshd_config in the section ChrootDirectory that the prerequisite is that the target can only be owned by root and not writable by anyone else.  So the directories have to be planned out a little more carefully.  Most often, an extra subdirectory is added, as it is in this case with /var/www/html instead of just /var/www  There are a number of other variations that can be set up depending on what else you have in /var/www.  But if it's otherwise empty, this set up works.

---

### Post by peter1897 on 2015-06-27
Yes, i think i learned some new things about chroot.

I am trying to connect to the apache server from the browser but if i type the IP address of the VPS i get "The connection has timed out". The apache server is running. Am i missing something? I thought i should be able to connect to the apache server just for typing the VPS ip address. I also tried ip_address:80 but it didn't work also.

---

### Post by Lars Noodén on 2015-06-27
If you are sure Apache2 is running and it shows up as listening in [netstat](http://manpages.ubuntu.com/manpages/trusty/en/man8/netstat.8.html)'s output(*netstat -ntlp*) as listening to ports 80 and 443, then does UFW have ports 80 and 443 open?

```

sudo ufw status verbose 

```

---

### Post by peter1897 on 2015-06-27
This is the output from netstat -ntlp

```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      4201/sshd
tcp6       0      0 :::22                   :::*                    LISTEN      4201/sshd
tcp6       0      0 :::80                   :::*                    LISTEN      2114/apache2
```

And this is the output from sudo ufw status verbose

```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip
```

The UFW was disabled so i enabled it and accidentally closed my ssh session before realizing that the default ufw settings are to block incoming connection and i can't connect to the server now. Is this the default ufw rules for each new Ubuntu server install or these idiots from Amazon AWS service are making the life of their users intentionally unpleasant?

---

### Post by Lars Noodén on 2015-06-27
It is both.  :O  But I should have anticipated and mentioned to allow 22, 80, and 443 before turning on UFW, if it was not already on:  I had thought that UFW was already on and allowing SSH.  The official Ubuntu policy, last I tried to get it changed, was that the default for the server edition is to have *no* services listening, not even SSH.  OpenBSD, in contrast, allows 22 in if the filter PF fails to get a valid configuration, and the default configuration itself allows SSH and most everything else in.

Presumably there is some console equivalent there at Amazon.  Can you get in again?

---

### Post by peter1897 on 2015-06-27
I don't know if i can get in again, i sent email to the support. But this is a test server anyway, i wouldn't host my real websites there.

I created a new virtual machine with Ubuntu server and i found that the problem to not be able to connect to apache server is that you have to create a security group for http traffic and assign this security group to the virtual machine. Otherwise you will not be able to connect even if apache server is running and netstat show that 80 port is listening.

Now i am able to connect to the apache server by typing the IP address of the vps in the browser. Will try to assign a domain name to see how this work.

---

### Post by peter1897 on 2015-06-27
It seems that to assign a single domain is simple, just point the domain to the server ip address, but i am confused about creating virtualhosts for hosting multiple websites on single ip.

I tried to implement this but without success. I created a folder for the second site: /var/www/site2. Then in /etc/apache2/sites-available i created a file and name it site2. In the file i added these lines:

```
<VirtualHost *:80>
DocumentRoot /var/www/site2
ServerName site2

</VirtualHost>
```

After this i restarted the apache server and tried to run the command: **sudo a2ensite site2** to enable the second site but i get this error: **ERROR: Site site2 does not exist!**

Why i am getting this error?

---

### Post by Lars Noodén on 2015-06-27
> **peter1897 said:**
> After this i restarted the apache server and tried to run the command: **sudo a2ensite site2** to enable the second site but i get this error: **ERROR: Site site2 does not exist!**

Why i am getting this error?

The a2ensite and (I think) a2dissite scripts tack on .conf on the end.  If you rename your file to site2.conf then it should work.  Or you could just build the symlink manually to sites-enabled.

---

### Post by peter1897 on 2015-06-27
I changed the name of the file site2 to site2.conf and was able to execute the command **a2ensite** successfully. After this i added a real domain name for ServerName in virtualhosts file and was able to connect to the second site typing the domain name in the browser. 

I am planning to give access to the server to people that will work on my website. I don't know yet if they will need only sftp access with clients like WinSCP and access to phpMyAdmin panel to manage the MySQL database or they will need ssh access too. How can i monitor their activities, for example, what commands they are executing? Also, if i grant to someone ssh access as a standard user is it possible for him to do damage even if he doesn't have admin rights?

---

### Post by Lars Noodén on 2015-06-27
If they have SSH access as a standard user, most of the damage they could do would be limited to their own account and any other area they have write access to, as far as data loss or corruption goes.  But there's an awful lot of mischief they could get into from that shell account in regards to looking for local exploits or bothering remote computers.  Again it comes down to trust and them acting grownup.  If they need a shorter leash, then you might consider rbash as their shell and set up some directories with (hard links or symlinks to) the programs they need and then set their $PATH to be those directories.

---

### Post by peter1897 on 2015-06-27
Thanks, i will keep that in mind.

---

