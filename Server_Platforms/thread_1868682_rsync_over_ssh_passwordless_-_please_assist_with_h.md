---
title: "rsync over ssh passwordless - please assist with helping me set this up properly"
date: 2011-10-24
forum: Server Platforms
---

### Post by greavette on 2011-10-24
Hello,

I want to use rsync over ssh (passwordless) to sync my source servers /usr/local/citadel/  folders and files to my destination server:  10.100.x.x:/usr/local/citadel/ 

Both servers are Ubuntu Lucid (10.04) and both are up to date.  Here is what I've done:

I've installed webmin on both servers and can see that the /usr/local/citadel folders and files on both servers are mostly setup (by default when Citadel was installed) with root as the User and root as the group.  There are some files and folders though that are setup with citadel as the user and citadel as the Group.

I use this page to assist with setting up my passwordless ssh:  [http://www.serveradminblog.com/2011/09/scp-ssh-and-rsync-without-prompting-for-password-howto/](http://www.serveradminblog.com/2011/09/scp-ssh-and-rsync-without-prompting-for-password-howto/)

On my Source server I login with my userid and I do not elevate using sudo su.  I  do the following to create my keys:

```
# ssh-keygen -t rsa
```

I accept the default location and It prompts me for a passphrase but do not enter anything. Instead, I just press the enter key. 
It generates an identification (private key) and a public key.
The public key is generated in ~/.ssh/id_rsa.pub. 

I then issue this command:

```
# cat id_rsa.pub >> /root/.ssh/authorized_keys
```

I get an error that says:  "-bash:  /root/.ssh/authorized_keys: Permission denied"

So, I elevate my privileges and use sudo su.

I issue this command again:
```
# cat id_rsa.pub >> /root/.ssh/authorized_keys
```
This time there is no error I'm successful.

I issue the following successfully next:
```
# chmod 700 /root/.ssh/authorized_keys
```

I exit out of sudo su.  I'm now back to my login id.

I now want to copy this key I created to my destination server.  I issue the following command:

```
ssh-copy-id 10.100.x.x
``` 
(where 10.100.x.x) is the ip of my source server.
I'm asked for the password of the destination servers user (the user is the same on both my source and destination servers).
I successfully copy the public id to my destination server.

I then do a test from my source server to my destination server:

```
ssh 10.100.x.x
```

Success, I connect and it doesn't ask for a password!

Since I can successfully connect without a password from my source server to my destination server, I'm ready to try an rsync command.  From my source server...Here goes:

```
rsync -va /usr/local/citadel/ 10.100.x.x:/usr/local/citadel/ 
```

Doesn't work...I get failed:  permission denied errors on the files and folders that are owned by the citadel user/group. 

So, after this long-winded post...what do I do.  I don't want to change the owners or permissions on the existing users/groups.  But how do I add the user/group root to also have access to these folders that are owned by citadel user/group?

Any help you can provide would be greatly appreciated.

Thank you.

---

### Post by karlson on 2011-10-24
> **greavette said:**
> 
Since I can successfully connect without a password from my source server to my destination server, I'm ready to try an rsync command.  From my source server...Here goes:

```
rsync -va /usr/local/citadel/ 10.100.x.x:/usr/local/citadel/ 
```

Doesn't work...I get failed:  permission denied errors on the files and folders that are owned by the citadel user/group. 


Have you tried:
```

rsync -e ssh -va <src> <dst>

```

---

### Post by greavette on 2011-10-24
I tried your suggestion..Nope...still the errors I saw before:

```

sending incremental file list
rsync: opendir "usr/local/citadel/data" failed:  Permission denied (13)
rsync: opendir "usr/local/citadel/network/spooltmp" failed:  Permission denied (13)
rsync: delete_file: unlink(citadel) failed:  Permission denied (13)
could not make way for new directory: citadel
rsync: delete_file: unlink(citadel) failed:  Permission denied (13)
could not make way for new directory: citadel
*** Skipping any contents from this failed directoy ***
```

What permissions do I need to update to get this working?

---

### Post by karlson on 2011-10-24
> **greavette said:**
> I tried your suggestion..Nope...still the errors I saw before:

```

sending incremental file list
rsync: opendir "usr/local/citadel/data" failed:  Permission denied (13)
rsync: opendir "usr/local/citadel/network/spooltmp" failed:  Permission denied (13)
rsync: delete_file: unlink(citadel) failed:  Permission denied (13)
could not make way for new directory: citadel
rsync: delete_file: unlink(citadel) failed:  Permission denied (13)
could not make way for new directory: citadel
*** Skipping any contents from this failed directoy ***
```

What permissions do I need to update to get this working?

You need to have read permission on the source directory and everything below for the user your are doing this as and Read/Write/Execute on the destination.

---

### Post by collisionystm on 2011-10-24
Easy way to do this.

Open a terminal for both servers on your computer. You will need to be able to copy and paste.

In each terminal do the following.

First, login with the username you plan to use to connect. I will assume its root.

sudo bash

ssh-keygen

enter through all prompts, no password.


Now, on server # 1

vi /root/.ssh/id_rsa.pub

copy everything in here.

:q! to quit

Open terminal for Server #2

sudo bash

nano /root/.ssh/authorized_keys

Paste contents from server #1's id_rsa.pub

CTRL + X then Y to save and exit.

Server # 1 can now ssh to server #2 without a password

I.E. 

ssh root@server#2

Do the same steps in the other direction if you desire. Really you only need to do this on one server.

rsync works as 

rsync SOURCE DESTINATIOn

rsync -ra /usr/local/citadel/* root@10.100.x.x:/usr/local/citadel

/usr/local/citadel/* is source

/usr/local/citadel is destination

follow my context and only put /'s where you see them.


> EDIT: If you are not going to use ROOT, remove the SUDO from my directions. Just make sure you are using the same username on both sides.

---

### Post by collisionystm on 2011-10-24
if you want to watch the progress when you rsync make sure to make it look like this

rsync -ra --progress /usr/local/citadel/* root@10.100.x.x:/usr/local/citadel

---

### Post by greavette on 2011-10-24
Thank you for your assistance karlson.

This is my question also...since I'm connecting to the destination server as root and I am trying to copy files and folders from source to destination as root...how do I add root to the permissions so this sync can be done, and yet not mess up my current permissions on my Citadel mail server?

Once I have my permissions setup properly, this should work.

Thank you.

---

### Post by greavette on 2011-10-24
Whoops...sorry collisionystm...didn't see your responses till now.  Thank you for the suggestions.  I will try them tonight and let you know how it works!

---

### Post by RyanRahl on 2011-10-24
Not sure if this will help but here is a script I use to backup with rsync and it has a couple options for using or not using passwords. I set this script on a cron job for once a day and I never have issues. It will also mail you a report! 

```

############
###Variables
############

subject="Subject Line"    			          # Email subject line
email="nobody@nodomain.edu"			          # Email recipient address
emailmsg=/absolute/path/to/emailmessage.txt	     # Path to message text (pick somewhere you have permissions to write too)
password=password				               # SSH password (not recommended over insecure networks)
localdir=/local/directory                         # Local directory to be synced to remote host
remdir=/remote/directory                          # Directory on remote host to sync too
user=ryan                                         # Remote user name
remhost=127.0.0.1                                 # Remote IP address or host name
remport=22                                        # Port of remote server (usually 22)


############
###Functions
############

## sync directories from local machine to remote host with pubkey authentication
function sync_docs
{
	rsync -aviz --progress --rsh='ssh -p$remport' $localdir $user@$remhost:$remdir > emailmessage.txt
}

## sync directories from local machine to remote host with password authentication
function sync_docs_pw
{
	SSHPASS=$password rsync -aviz --progress --rsh='sshpass -e ssh -p$remport' $localdir $user@$remhost:$remdir > emailmessage.txt
}

## mail success report
function mail_success
{
	SUBJECT="Success - scannerbox rsync"
	EMAILMESSAGE="$emailmsg"
	/usr/bin/mail -s "$SUBJECT" "$EMAIL" < $EMAILMESSAGE
}

## mail failure report
function mail_fail
{
	SUBJECT="Failure - scannerbox rsync"
	EMAILMESSAGE="$emailmsg"
	/usr/bin/mail -s "$SUBJECT" "$EMAIL" < $EMAILMESSAGE
}

## remove automatically created text file containing progress report for email
function rm_emailtxt
{
	rm $emailmsg
}

################
### Main Routine
################

## modify this main routine by choosing 'sync_docs' or 'sync_docs_pw' by commenting/uncommenting respective to your authentication method
if sync_docs; then
#if sync_docs_pw; then
	mail_success
else
	mail_fail
fi
rm_emailtxt
exit

```



Hope you get your permissions fixed, that's what your issue looks like to me. Can you give us an 'ls- l' of both the source and destination directories?

---

### Post by greavette on 2011-10-25
collisionystm, I have tried to copy the entire key from my source to destination servers, but I'm not sure how best to do this.  I connect to these servers using putty (the servers are a VM on a Windows CP host).  I'm not familiar with vi so I'm trying to copy then entire key using nano but I can't copy the key using putty.  Is there specific instructions I should follow to copy these keys?



RyanRahl, here are my permissions from both my source and destinatation folders.  I agree that once I fix my permissions, this problem should be corrected.

Source:
```
root@Source:/usr/local/citadel$ ls -l
total 4532
-rwxr-xr-x  1 root    root     227240 2011-10-19 14:59 aidepost
-rwxr-xr-x  1 root    root      16699 2011-10-19 14:59 base64
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 bio
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 bitbucket
-rwxr-xr-x  1 root    root     222310 2011-10-19 14:59 chkpw
-rwxr-xr-x  1 root    root      10005 2011-10-19 14:59 chkpwd
-rwxr-xr-x  1 root    root     535837 2011-10-19 14:59 citadel
-rw-------  1 citadel citadel    3228 2011-10-24 12:08 citadel.config
-rw-------  1 citadel root         32 2011-10-24 12:08 citadel.control
-rw-r--r--  1 root    root         41 2011-10-19 14:59 citadel-easyinstall.sum
-rw-r--r--  1 root    root      14776 2011-10-19 14:59 citadel.rc
-rw-r--r--  1 root    root       2039 2011-10-19 14:59 citadel.schema
srwxrwsrwx  1 root    root          0 2011-10-24 12:08 citadel.socket
-rw-r--r--  1 root    root        617 2011-10-19 14:59 citadel_urlshorteners.rc
-rwxr-xr-x  1 root    root     223152 2011-10-19 14:59 citmail
-rwxr-xr-x  1 root    root    1518737 2011-10-19 14:59 citserver
-rwxr-xr-x  1 root    root     224753 2011-10-19 14:59 ctdlmigrate
drwx------  2 citadel root       4096 2011-10-19 15:04 data
-rwxr-xr-x  1 root    root       3138 2011-10-19 14:59 database_cleanup.sh
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 docs
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 files
-rw-r--r--  1 root    root       2299 2011-10-19 14:59 funambol_newmail_soap.xml
-rwxr-xr-x  1 root    root     314516 2011-10-19 14:59 getmail
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 help
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 images
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 info
srwxrwsrwx  1 root    root          0 2011-10-24 12:08 lmtp.socket
srwxrwsrwx  1 root    root          0 2011-10-24 12:08 lmtp-unfiltered.socket
drwxr-xr-x 13 root    root       4096 2011-10-19 14:59 locale
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 messages
-rwxr-xr-x  1 root    root        860 2011-10-19 14:59 migrate_aliases.sh
-rwxr-xr-x  1 root    root      16407 2011-10-19 14:59 msgform
drwxr-xr-x  6 citadel root       4096 2011-10-19 15:04 network
-rw-r--r--  1 root    root        138 2011-10-19 14:59 notify_about_newmail.js
-rw-r--r--  1 root    root        279 2011-10-19 14:59 public_clients
-rw-r--r--  1 root    root        488 2011-10-19 14:59 README.txt
-rw-r--r--  1 root    root       5689 2011-10-19 14:59 rfc2739.schema
-rwxr-xr-x  1 root    root     313350 2011-10-19 14:59 sendcommand
-rwxr-xr-x  1 root    root     257152 2011-10-19 14:59 setup
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 techdoc
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 unstripped
-rwxr-xr-x  1 root    root     300470 2011-10-19 14:59 userlist
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 userpics
-rwxr-xr-x  1 root    root     304599 2011-10-19 14:59 whobbs

```

Destination:

```
root@destination:/usr/local/citadel# ls -l
total 4532
-rwxr-xr-x  1 root    root     227240 2011-10-24 08:58 aidepost
-rwxr-xr-x  1 root    root      16703 2011-10-24 08:58 base64
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 bio
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 bitbucket
-rwxr-xr-x  1 root    root     222310 2011-10-24 08:58 chkpw
-rwxr-xr-x  1 root    root      10005 2011-10-24 08:58 chkpwd
-rwxr-xr-x  1 root    root     535841 2011-10-24 08:58 citadel
-rw-------  1 citadel citadel    3228 2011-10-24 08:59 citadel.config
-rw-------  1 citadel root         32 2011-10-24 08:59 citadel.control
-rw-r--r--  1 root    root         41 2011-10-24 08:58 citadel-easyinstall.sum
-rw-r--r--  1 root    root      14776 2011-10-24 08:58 citadel.rc
-rw-r--r--  1 root    root       2039 2011-10-24 08:58 citadel.schema
srwxrwsrwx  1 root    root          0 2011-10-24 08:59 citadel.socket
-rw-r--r--  1 root    root        617 2011-10-24 08:58 citadel_urlshorteners.rc
-rwxr-xr-x  1 root    root     223152 2011-10-24 08:58 citmail
-rwxr-xr-x  1 root    root    1518737 2011-10-24 08:58 citserver
-rwxr-xr-x  1 root    root     224753 2011-10-24 08:58 ctdlmigrate
drwx------  2 citadel root       4096 2011-10-24 08:59 data
-rwxr-xr-x  1 root    root       3138 2011-10-24 08:58 database_cleanup.sh
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 docs
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 files
-rw-r--r--  1 root    root       2299 2011-10-24 08:58 funambol_newmail_soap.xml
-rwxr-xr-x  1 root    root     314516 2011-10-24 08:58 getmail
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 help
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 images
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 info
srwxrwsrwx  1 root    root          0 2011-10-24 08:59 lmtp.socket
srwxrwsrwx  1 root    root          0 2011-10-24 08:59 lmtp-unfiltered.socket
drwxr-xr-x 13 root    root       4096 2011-10-24 08:58 locale
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 messages
-rwxr-xr-x  1 root    root        860 2011-10-24 08:58 migrate_aliases.sh
-rwxr-xr-x  1 root    root      16407 2011-10-24 08:58 msgform
drwxr-xr-x  6 citadel root       4096 2011-10-24 08:59 network
-rw-r--r--  1 root    root        138 2011-10-24 08:58 notify_about_newmail.js
-rw-r--r--  1 root    root        279 2011-10-24 08:58 public_clients
-rw-r--r--  1 root    root        488 2011-10-24 08:58 README.txt
-rw-r--r--  1 root    root       5689 2011-10-24 08:58 rfc2739.schema
-rwxr-xr-x  1 root    root     313350 2011-10-24 08:58 sendcommand
-rwxr-xr-x  1 root    root     257152 2011-10-24 08:58 setup
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 techdoc
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 unstripped
-rwxr-xr-x  1 root    root     300470 2011-10-24 08:58 userlist
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 userpics
-rwxr-xr-x  1 root    root     304603 2011-10-24 08:58 whobbs

```

---

### Post by collisionystm on 2011-10-25
> **greavette said:**
> collisionystm, I have tried to copy the entire key from my source to destination servers, but I'm not sure how best to do this.  I connect to these servers using putty (the servers are a VM on a Windows CP host).  I'm not familiar with vi so I'm trying to copy then entire key using nano but I can't copy the key using putty.  Is there specific instructions I should follow to copy these keys?



RyanRahl, here are my permissions from both my source and destinatation folders.  I agree that once I fix my permissions, this problem should be corrected.

Source:
```
root@Source:/usr/local/citadel$ ls -l
total 4532
-rwxr-xr-x  1 root    root     227240 2011-10-19 14:59 aidepost
-rwxr-xr-x  1 root    root      16699 2011-10-19 14:59 base64
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 bio
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 bitbucket
-rwxr-xr-x  1 root    root     222310 2011-10-19 14:59 chkpw
-rwxr-xr-x  1 root    root      10005 2011-10-19 14:59 chkpwd
-rwxr-xr-x  1 root    root     535837 2011-10-19 14:59 citadel
-rw-------  1 citadel citadel    3228 2011-10-24 12:08 citadel.config
-rw-------  1 citadel root         32 2011-10-24 12:08 citadel.control
-rw-r--r--  1 root    root         41 2011-10-19 14:59 citadel-easyinstall.sum
-rw-r--r--  1 root    root      14776 2011-10-19 14:59 citadel.rc
-rw-r--r--  1 root    root       2039 2011-10-19 14:59 citadel.schema
srwxrwsrwx  1 root    root          0 2011-10-24 12:08 citadel.socket
-rw-r--r--  1 root    root        617 2011-10-19 14:59 citadel_urlshorteners.rc
-rwxr-xr-x  1 root    root     223152 2011-10-19 14:59 citmail
-rwxr-xr-x  1 root    root    1518737 2011-10-19 14:59 citserver
-rwxr-xr-x  1 root    root     224753 2011-10-19 14:59 ctdlmigrate
drwx------  2 citadel root       4096 2011-10-19 15:04 data
-rwxr-xr-x  1 root    root       3138 2011-10-19 14:59 database_cleanup.sh
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 docs
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 files
-rw-r--r--  1 root    root       2299 2011-10-19 14:59 funambol_newmail_soap.xml
-rwxr-xr-x  1 root    root     314516 2011-10-19 14:59 getmail
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 help
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 images
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 info
srwxrwsrwx  1 root    root          0 2011-10-24 12:08 lmtp.socket
srwxrwsrwx  1 root    root          0 2011-10-24 12:08 lmtp-unfiltered.socket
drwxr-xr-x 13 root    root       4096 2011-10-19 14:59 locale
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 messages
-rwxr-xr-x  1 root    root        860 2011-10-19 14:59 migrate_aliases.sh
-rwxr-xr-x  1 root    root      16407 2011-10-19 14:59 msgform
drwxr-xr-x  6 citadel root       4096 2011-10-19 15:04 network
-rw-r--r--  1 root    root        138 2011-10-19 14:59 notify_about_newmail.js
-rw-r--r--  1 root    root        279 2011-10-19 14:59 public_clients
-rw-r--r--  1 root    root        488 2011-10-19 14:59 README.txt
-rw-r--r--  1 root    root       5689 2011-10-19 14:59 rfc2739.schema
-rwxr-xr-x  1 root    root     313350 2011-10-19 14:59 sendcommand
-rwxr-xr-x  1 root    root     257152 2011-10-19 14:59 setup
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 techdoc
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 unstripped
-rwxr-xr-x  1 root    root     300470 2011-10-19 14:59 userlist
drwxr-xr-x  2 root    root       4096 2011-10-19 14:59 userpics
-rwxr-xr-x  1 root    root     304599 2011-10-19 14:59 whobbs

```Destination:

```
root@destination:/usr/local/citadel# ls -l
total 4532
-rwxr-xr-x  1 root    root     227240 2011-10-24 08:58 aidepost
-rwxr-xr-x  1 root    root      16703 2011-10-24 08:58 base64
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 bio
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 bitbucket
-rwxr-xr-x  1 root    root     222310 2011-10-24 08:58 chkpw
-rwxr-xr-x  1 root    root      10005 2011-10-24 08:58 chkpwd
-rwxr-xr-x  1 root    root     535841 2011-10-24 08:58 citadel
-rw-------  1 citadel citadel    3228 2011-10-24 08:59 citadel.config
-rw-------  1 citadel root         32 2011-10-24 08:59 citadel.control
-rw-r--r--  1 root    root         41 2011-10-24 08:58 citadel-easyinstall.sum
-rw-r--r--  1 root    root      14776 2011-10-24 08:58 citadel.rc
-rw-r--r--  1 root    root       2039 2011-10-24 08:58 citadel.schema
srwxrwsrwx  1 root    root          0 2011-10-24 08:59 citadel.socket
-rw-r--r--  1 root    root        617 2011-10-24 08:58 citadel_urlshorteners.rc
-rwxr-xr-x  1 root    root     223152 2011-10-24 08:58 citmail
-rwxr-xr-x  1 root    root    1518737 2011-10-24 08:58 citserver
-rwxr-xr-x  1 root    root     224753 2011-10-24 08:58 ctdlmigrate
drwx------  2 citadel root       4096 2011-10-24 08:59 data
-rwxr-xr-x  1 root    root       3138 2011-10-24 08:58 database_cleanup.sh
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 docs
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 files
-rw-r--r--  1 root    root       2299 2011-10-24 08:58 funambol_newmail_soap.xml
-rwxr-xr-x  1 root    root     314516 2011-10-24 08:58 getmail
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 help
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 images
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 info
srwxrwsrwx  1 root    root          0 2011-10-24 08:59 lmtp.socket
srwxrwsrwx  1 root    root          0 2011-10-24 08:59 lmtp-unfiltered.socket
drwxr-xr-x 13 root    root       4096 2011-10-24 08:58 locale
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 messages
-rwxr-xr-x  1 root    root        860 2011-10-24 08:58 migrate_aliases.sh
-rwxr-xr-x  1 root    root      16407 2011-10-24 08:58 msgform
drwxr-xr-x  6 citadel root       4096 2011-10-24 08:59 network
-rw-r--r--  1 root    root        138 2011-10-24 08:58 notify_about_newmail.js
-rw-r--r--  1 root    root        279 2011-10-24 08:58 public_clients
-rw-r--r--  1 root    root        488 2011-10-24 08:58 README.txt
-rw-r--r--  1 root    root       5689 2011-10-24 08:58 rfc2739.schema
-rwxr-xr-x  1 root    root     313350 2011-10-24 08:58 sendcommand
-rwxr-xr-x  1 root    root     257152 2011-10-24 08:58 setup
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 techdoc
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 unstripped
-rwxr-xr-x  1 root    root     300470 2011-10-24 08:58 userlist
drwxr-xr-x  2 root    root       4096 2011-10-24 08:58 userpics
-rwxr-xr-x  1 root    root     304603 2011-10-24 08:58 whobbs

```


It's hard to copy the entire key with nano and that is why i suggested VI.

do this

vi the key

when you copy it

type 

:q! to exit

colon, q, exclamation point

---

### Post by RyanRahl on 2011-10-26
> But how do I add the user/group root to also have access to these folders that are owned by citadel user/group?

You can add root to the citadel group by

```
usermod -a -G citadel root
```

But I'm not sure that is your issue. You said:

> Doesn't work...I get failed: permission denied errors on the files and folders that are owned by the citadel user/group.

but I noticed in your errors:

> ```
sending incremental file list
rsync: opendir "usr/local/citadel/data" failed:  Permission denied (13)
rsync: opendir "usr/local/citadel/network/spooltmp" failed:  Permission denied (13)
rsync: delete_file: unlink(citadel) failed:  Permission denied (13)
could not make way for new directory: citadel
rsync: delete_file: unlink(citadel) failed:  Permission denied (13)
could not make way for new directory: citadel
*** Skipping any contents from this failed directoy ***
```

that one of the files in question:

> ```
drwx------  2 citadel root       4096 2011-10-19 15:04 data

```

has no group read permissions and can only be read by the the owning user, citadel. Notice the rest of your directories have 
```
rwxr-xr-x
```
permissions so they can be read by the group. So if the 'data' directory is only readable by the citadel user then the root user will not be able to read it. You need to allow group read permissions on the directory or you need to do the rsync for those individual files as the citadel user. The second file with the error is a directory inside the directory you ls'ed but I'm guessing it has the same problem. So I would try this:

```
root@Source:/#chmod g+r /usr/local/citadel/data
root@Source:/#chmod g+r usr/local/citadel/network/spooltmp
```

I know you said you don't want to change any permissions but as I am seeing it there is really no way around it. I think adding group read permissions is pretty minimal and I don't believe it to be a security risk considering the group is root.

---

### Post by collisionystm on 2011-10-26
Did you get this working?

---

### Post by greavette on 2011-10-31
I'm sorry for the delay in responding.  

I've been able to rsync my Citadel mail data from our Production Server to our backup server now under a root account that doesn't ask for a password.  My new mail server isn't connecting properly from Thunderbird...but that's a different problem.  ;)  For now, I have confirmed that all my mail has successfully transferred to our backup server.

Thanks so much to all that helped me with this task...it's been dogging me for over 2 years on how to do this.  

I will post exactly what I did for future hits on this post.

Thanks again Ubuntu community!

---

### Post by RyanRahl on 2011-12-14
> I will post exactly what I did for future hits on this post.
:popcorn:

---

