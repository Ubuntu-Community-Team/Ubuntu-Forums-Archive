---
title: "No directory logging in with HOME=/,  Ubuntu Server 9.04"
date: 2009-09-14
forum: Server Platforms
---

### Post by vl72 on 2009-09-14
Hello!
I receive the message “No directory logging in with HOME=/”
every time when boot and login in Linux Ubuntu Server 9.04.
My HD is alive and folders /root, /home and others exist and are in a good condition.
When I login as a “root”, I haven’t this message and I be located in /root  folder.
I supposed my problem related with SSH, but I doubt about it now .
I  typed 
ssh 127.0.0.1 and received the message
“…..Connection refused “
and command
/etc/init.d/ssh status  
“sshd is not running”

Users' folders have permissions "rwxr-xr-x".
They are their owners.
File /etc/passwd has permission "rw-r--r--", owner "root" . 
This file has next lines:
user_name: ... /home/user_name : /bin/bash 

File .bash_history and directory ./mc ( I use Midnight Commander) appeared
in root directory "/".
My last commands in file /home/myname/.bash_history are next:
ssh-copy-id
ssh-keyscan
"myname" is user name who I type every time when I login.
I removed deb-package openssh-server with the help of aptitude command, but the message 
“No directory logging in with HOME=/” appeared again when I typed login "myname".

I decided to do a small experiment.
I created a new user account "userx" .

useradd userx -m -s /bin/bash
passwd userx

Then I looked file /etc/passwd and I saw fields for user 'userx' in the last line:
userx: ... :/home/userx:/bin/bash
The home directory /home/userx was created and consist of 3 files
.bash_logout, .bashrc &#1080; .profile 
Folder/home/userx has next permissions: "rwxr-xr-x".
I entered login and password for new user "userx" 
and saw the message “No directory logging in with HOME=/” on the screen.
I looked  /var/log/auth.log.
The last record of my folder "/home/myname" was of the 4th August,
when I used SSH. 

Does anyone know what the problem is?

Has anyone experienced this problem? 

What can I do to fix this?

P.S.  Excuse me for my bad English.
Thanks for the help.

---

### Post by jondkent on 2009-09-14
check the permissions on the actual user directory itself rather than just /home, should be :

drwx------

and should be owned by user and whatever group you assigned the user to.

Check that the .[dot] files are also readable within the user's home directory (though this shouldn't cause this problem).

If the permission are incorrect you'll need to use chmod (very carefully) to change them to the permissions, and chown (again, carefully) to change the ownership if the required.

I've only ever seen this type of problem when NFS fail, never seen it for local accounts before unless the account permission where incorrect hence the suggestions above.

---

### Post by jondkent on 2009-09-14
Another option could be that your passwd file is corrupt somehow.

Try:

cd ~userx

If that fails, you have a corrupt passwd file.  To be sure, run the command:

*pwck*

This will verify the sanity of the passwd and show you any errors.  You should then be able to correct by hand using:

*vipwd*

**ONLY**.  In case you don't know this version of vim will ensure you do not create a corrupt passwd file.

---

