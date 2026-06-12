---
title: "HELP! I used CHOWN and CHMOD on my private folder and now..."
date: 2014-08-24
forum: Security
---

### Post by oobnuker on 2014-08-24
... I can't login or access the files. 

I was logged in as my user account and was having trouble accessing some files so I decided to CHOWN root:root everything and CHMOD 777 everything as well. Recursively. I know it was not a good idea, but it's done. Everything was fine until I rebooted. Now when I attempt to login, I get a black screen and then get booted back out to the login screen. I used CTRL-ALT-F6 and got a console and am able to login to my user account that way but all I see in my home folder are the two files telling me how to access my private data. I also tried logging in from a LiveCD and get the same issue. The worst part is that the encryption key was stored in a text file, IN my home directory...

Any help or ideas? Thanks!

---

### Post by Bashing-om on 2014-08-24
oobnuker; YUK !

> **oobnuker said:**
> ... I can't login or access the files. 

I was logged in as my user account and was having trouble accessing some files so I decided to CHOWN root:root everything and CHMOD 777 everything as well. Recursively. I know it was not a good idea, but it's done. Everything was fine until I rebooted. Now when I attempt to login, I get a black screen and then get booted back out to the login screen. I used CTRL-ALT-F6 and got a console and am able to login to my user account that way but all I see in my home folder are the two files telling me how to access my private data. I also tried logging in from a LiveCD and get the same issue. The worst part is that the encryption key was stored in a text file, IN my home directory...

Any help or ideas? Thanks!

Hooo Boy !
> 
The worst part is that the encryption key was stored in a text file, IN my home directory...

If you do not know the encrytion key, and can not access that file system; You are up that creek without any paddle. There is no way for a common user to defeat that encryption !

I hope you have made backups of those files you consider important !

[INDENT][INDENT]a fact in ubuntu'n
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-08-24
Did you do this just to /home or entire system?

If just /home you may be able to chroot and reset back to you. 

This is chroot instructions to reinstall grub which you can skip, but once at command line you can change to the mounted location of your /home and rerun the correct settings. But some may need special settings.

Your mount inside a chroot will not be the same, $USER is your name, and since chrooted, I think you have to use your login name not the system variable.
IF you are in your system the variable works.
fred@trusty-DT:~$ echo $USER
fred

 sudo chmod -R a+rwX,o-w /home/$USER

 sudo chown $USER:$USER /home/$USER


All directories will be 775.
All files will be 664 except those that were set as executable to begin with.

If you know passphrase & it works.

 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

### Post by oldfred on 2014-08-24
Did you do this just to /home or entire system?

If just /home you may be able to chroot and reset back to you. 

This is chroot instructions to reinstall grub which you can skip, but once at command line you can change to the mounted location of your /home and rerun the correct settings. But some may need special settings.

Your mount inside a chroot will not be the same, $USER is your name, and since chrooted, I think you have to use your login name not the system variable.
IF you are in your system the variable works.
fred@trusty-DT:~$ echo $USER
fred

 sudo chmod -R a+rwX,o-w /home/$USER

 sudo chown -R $USER:$USER /home/$USER


All directories will be 775.
All files will be 664 except those that were set as executable to begin with.

If you know passphrase & it works.

 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

### Post by oobnuker on 2014-08-25
Thanks for responding! I MAY have done it on the entire drive. I definitely do not have the passphrase key anywhere other than in the encrypted folder. I ran CHOWN on my home directory and am now able to at least login to the system with my user account but I am no closer than I was before. I tried the commands that oldfred suggested and didn't get anywhere. The best I can do is see the encrypted files.

Any other ideas?

Thanks!

---

### Post by mozalmy on 2014-08-25
Have you tried changing back your permission?

```
sudo chmod 755 /etc
sudo chmod 755 /etc/ssh
sudo chmod 600 /etc/ssh/ssh_host_dsa_key
sudo chmod 600 /etc/ssh/ssh_host_rsa_key
sudo chmod 640 /etc/shadow
```

Source: Read line #6 in this old thread [http://ubuntuforums.org/showthread.php?t=1267670](http://ubuntuforums.org/showthread.php?t=1267670)

---

### Post by oldfred on 2014-08-25
My chown was missing the -R for recursive in the command above. It would only have changed the first level.

If you changed the entire system which is why you have to be careful and only use those commands rarely and only on your data folders, then reinstall may be the only option.

The links above also has ways to mount an encrypted folder from a chroot, but if you log in you should also be able to do that.

---

