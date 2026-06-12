---
title: "ftp localhost (laptop) using filezilla /var/www directory - permission problems?"
date: 2013-05-02
forum: Server Platforms
---

### Post by eranariel on 2013-05-02
Problems accessing my laptop as localhost using ftp... filezilla... /var/www directory

 

  I would like to update my applications in /var/www using files from  my home directory...
 

 ls -l /var/www  shows me the following permissions:
 

 -rwxr-xr-x  1 eranariel www-data  242 Apr  8 21:32 index.html~ 
 -rwxr-xr-x  1 eranariel www-data   20 Apr  7 19:55 info.php 
 drwxrwxr-x  6 eranariel www-data 4096 Apr 11 08:39 op 
 lrwxrwxrwx  1 eranariel www-data   21 Apr  7 20:07 phpmyadmin -> /usr/share/phpmyadmin 
 drwxrwsr-x 14 eranariel www-data 4096 Apr  8 16:48 zencart 
 

 However,  I am  uncertain as to the granted permissions in this directory...Filezilla only responds to user name “anonymous” on localhost – accordingly, anonymous does not have permissions to edit or upload anything to var/www.   
 

 I tried my Ubuntu administrator login and password, however, all I get is “not connected to any server”
 I am not sure what I did, however, previously, I was receiving an error 553 which is supposed to be permissions related.  
 

 Any suggestions?  
 

 Thanks in advance...
 

 Eran

---

### Post by Lars Noodén on 2013-05-02
Since you have FileZilla, you could try SFTP.  At least that way you'll be making secure transfers rather than broadcasting your user name and password all over the net.  

About the directory permissions.  If you are the only user of /var/www, then it is enough to [chown](http://manpages.ubuntu.com/manpages/raring/en/man1/chown.1posix.html) it.  www-data should not own anything and not be one of the groups.

```
 
sudo chown -R eranarie:eranarie /var/www

```

If there are others you will share the directory with, then you will need to use groups for the permissions.

---

### Post by lykwydchykyn on 2013-05-02
Why are you using FTP to move around files on your local machine?

/var/www is owned and writeable by root only by default.

---

### Post by cariboo on 2013-05-02
Moved to Server Platforms.

---

### Post by eranariel on 2013-05-03
the user name and password are on my localhost laptop behind NAT...  thanks so much for your assistance... I'll give this an attempt to see how it goes...

Eran

---

### Post by eranariel on 2013-05-03
> **lykwydchykyn said:**
> Why are you using FTP to move around files on your local machine?

/var/www is owned and writeable by root only by default.


I am using filezilla, as  to manage the method in which I upload and edit files and directories - I just "drag-and-drop" from one window in the the other and vice-versa, wheres the former window would list my /var/www directory and the former would list a directory located on my desktop in which my revised files are contained.

---

### Post by darkod on 2013-05-03
> **eranariel said:**
> I am using filezilla, as  to manage the method in which I upload and edit files and directories - I just "drag-and-drop" from one window in the the other and vice-versa, wheres the former window would list my /var/www directory and the former would list a directory located on my desktop in which my revised files are contained.

This still doesn't make any sense. You should be able to copy paste with Nautilus (if this is the desktop OS), or simply use cp on the command line (if you have CLI only server OS).

From the ls -l you posted, you seem to be the owner of the folder/files in /var/www, so using Nautilus or cp should be fine.

Like you said yourself, Filezilla is allowing only anonymous login which doesn't have rights on /var/www. You are only complicating it if you insist on using Filezilla. Besides, if you insist on using ftp client to copy files, you have to have ftp server running on the other end. Do you?

It doesn't work simply like that. For ftp client to conenct and authorize a user, there has to be ftp server listening on the other end.

---

### Post by eranariel on 2013-05-03
> **darkod said:**
> This still doesn't make any sense. You should be able to copy paste with Nautilus (if this is the desktop OS), or simply use cp on the command line (if you have CLI only server OS).

From the ls -l you posted, you seem to be the owner of the folder/files in /var/www, so using Nautilus or cp should be fine.

Like you said yourself, Filezilla is allowing only anonymous login which doesn't have rights on /var/www. You are only complicating it if you insist on using Filezilla. Besides, if you insist on using ftp client to copy files, you have to have ftp server running on the other end. Do you?

It doesn't work simply like that. For ftp client to conenct and authorize a user, there has to be ftp server listening on the other end.

You are correct, I  can use the Nautilus... :) I initially started by installing vsftpd in conjunction with filezilla. From that point, I chowned the relevant /var/www directory...filezilla as my ftp client.  I was able to  access the ftp server via the shell but unable to access the ftp server via filezilla.From that point,  I uninstalled both, vsftpd and filezilla, and then reinstalled only filezilla, which succesfully  accessed my localhost using "anonymous" but with limited privaledges..

However, for the record, it would be interesting to know what caused this configuration to function in the mannerr that it did... 

Thanks again for your assistance and godspeed...

Eran

---

### Post by darkod on 2013-05-03
Without vsftpd there is no ftp service active and listening to requests. I guess that's why filezilla gives only some limited anonymous access.

As for why it didn't work with vsftpd and filezilla client, I don't know. One reason could be that vsftpd was set only for secure access, something like SSL, etc, which is the recommended way, but you were connecting with filezilla to the normal ftp port 21. If you have FTPS (secure) only running on the server, the ftp client would not connect on the standard non-secure ftp port.

---

