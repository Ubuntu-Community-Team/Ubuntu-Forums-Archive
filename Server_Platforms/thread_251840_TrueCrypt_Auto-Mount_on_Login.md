---
title: "TrueCrypt Auto-Mount on Login"
date: 2006-09-06
forum: Server Platforms
---

### Post by Razor X on 2006-09-06
I have a dual boot system and I’m trying to use TrueCrypt to protect my /home directory. On Windows, TrueCrypt can be set to load and mount volumes on login; however I am having little luck with Ubuntu.

Currently, in order to mount /home I have to login, double click on a launcher I made that runs the command: sudo truecrypt  /dev/sda3 /home (then I enter the sudo and volume passwords). Then I have to log off, and re-log in (otherwise the desktop never updates and other weird stuff happens). After that, it works ok.
  

So, first of all, and most importantly, does anyone know how to simply have TrueCrypt auto-launch on login and mount /home without me having to log off and re-log in?
  

Also, entering the passwords is annoying too, and if anyone is up the task, I thought there might be a way to bypass all the password entering:
  See, I don’t have much experience with this so I can’t really explain exactly how it would be implemented, but my basic idea is to make a text file that contains the TrueCrypt volume passwords (hashed or not). That text file is encrypted with a linux encryption program (like EncFS) that decrypts the file on login (kind of how in order to use EFS on windows, all a user has to do is login using the windows password). Then there is a shell script that parses the text file and passes the passwords to TrueCrypt when it tries to mount the volume. That way everything is taken care of after the initial login.
  

Anyway, all I’m looking for it to make things easier without compromising security (assume the Ubuntu login password is very secure).  Anyone think I’m on to something? Anyone feel like trying to figure out what that script might look like?
  

Thanks!


  Oh, also, I noticed the volume does not dismount on log-out, does anyone know how to issue a dismount command automatically on log-off?

---

### Post by rafalr on 2006-09-08
Hi,

I am also just a beginner in truecrypt but did some reading recently.

Apart from the fact that automount at login seems to be countering the very idea of using encryption, if you use script to automount you should not be forced to log-off and in, there is something wrong with the setup.

Possibly you should enable truecrypt to be used withouth sudo:
sudo chmod u+s /usr/bin/truecrypt

then it is sure you will not need to enter the sudo password, just the truecrypt password. Possibly you will also get rid of the log-off / in problem.

As far as truecrypt password, there may be some options available in truecrypt. You may want to use 
$man truecrypt

I know there is a similar option in EncFS with FUSE, there could be something similar in truecrypt. Below part of EncFS man.

Option:
--extpass=program

Specify an external program to use for getting the user password. When the external program is spawned, the environment variable ``RootDir'' will be set to contain the path to the root directory. The program should print the password to standard output. EncFS takes everything returned from the program to be the password, except for a trailing newline (\n) which will be removed.

For example, specifying --extpass=/usr/lib/ssh/ssh-askpass will cause EncFS to use ssh's password prompt program.

Maybe this will help.
Rafal

---

