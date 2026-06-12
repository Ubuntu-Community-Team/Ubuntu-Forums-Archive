---
title: "Safe home question"
date: 2009-11-18
forum: Security
---

### Post by jensen1604 on 2009-11-18
Hi guys!
I'm a fairly new Linux user, but so far I've only encountered awesomeness considering Ubuntu :)

I'm trying to learn about the Linux system, so I read through the post sticky Ubuntu Security and stumbled over the "Safe home" header in the thread. More specifically I'm talking about the ```
chmod 700 $HOME
```, which is a very nifty command for securing your private data in case your computer gets stolen for example. I ran the command and tested it through the Live CD and it worked perfectly and I were not able to access my /home/username in any way. :p Though questions came to my mind afterwards.

Let's say my system crashes and I have to reinstall and/or back up my private files, but I am not able to enter my user session. How would I then be able to retrieve my private data again without access to my user? 

Thanks in advance!
jensen1604! ;)

---

### Post by teward on 2009-11-18
> **jensen1604 said:**
> Hi guys!
I'm a fairly new Linux user, but so far I've only encountered awesomeness considering Ubuntu :)

I'm trying to learn about the Linux system, so I read through the post sticky Ubuntu Security and stumbled over the "Safe home" header in the thread. More specifically I'm talking about the ```
chmod 700 $HOME
```, which is a very nifty command for securing your private data in case your computer gets stolen for example. I ran the command and tested it through the Live CD and it worked perfectly and I were not able to access my /home/username in any way. :p Though questions came to my mind afterwards.

Let's say my system crashes and I have to reinstall and/or back up my private files, but I am not able to enter my user session. How would I then be able to retrieve my private data again without access to my user? 

Thanks in advance!
jensen1604! ;)

the user "root" can access all files, and can copy out your user's home directory for example, lets say I want all the data for the user "juser," and I want to copy it to another location.  Then in a terminal window...

NOTE: DO NOT DO THIS UNLESS YOU ARE COMFORTABLE USING ROOT!  IF YOU ARE NOT, YOU CAN SERIOUSLY KILL YOUR COMPUTER!  WHEN FINISHED, LOG OUT OF ROOT!
```
# sudo su
Password: <your password goes here>
root@compName:/# cp -r /home/juser *<destination directory*>
root@compName:/#exit
#
```The above will copy juser's home directory to somewhere else, and will copy over EVERYTHING in there.  Just replace juser with your user name, and specify a second directory to copy everything to.

However, if your computer refuses to boot even to the hard drive or console, try running off a LiveCD, and using the console there.  NOTE: Others are more experienced with the console than I, however I have completely reimaged a hard drive with this method by copying over my entire filesystem.  :P


NOTE: I would not EVER in my life do this to my folder or any other folder on my computer, because I have information that I cannot allow others to gain access to (I run an FTP server off my computer with openssh, lol).

---

### Post by jensen1604 on 2009-11-18
> **TrekCaptainUSA said:**
> the user "root" can access all files, and can copy out your user's home directory for example, lets say I want all the data for the user "juser," and I want to copy it to another location.  Then in a terminal window...

NOTE: DO NOT DO THIS UNLESS YOU ARE COMFORTABLE USING ROOT!  IF YOU ARE NOT, YOU CAN SERIOUSLY KILL YOUR COMPUTER!  WHEN FINISHED, LOG OUT OF ROOT!
```
# sudo su
Password: <your password goes here>
root@compName:/# cp -r /home/juser *<destination directory*>
root@compName:/#exit
#
```The above will copy juser's home directory to somewhere else, and will copy over EVERYTHING in there.  Just replace juser with your user name, and specify a second directory to copy everything to.

However, if your computer refuses to boot even to the hard drive or console, try running off a LiveCD, and using the console there.  NOTE: Others are more experienced with the console than I, however I have completely reimaged a hard drive with this method by copying over my entire filesystem.  :P


NOTE: I would not EVER in my life do this to my folder or any other folder on my computer, because I have information that I cannot allow others to gain access to (I run an FTP server off my computer with openssh, lol).

Thanks mate :) Exactly what I needed.. Basically there is an option for me to retrieve my private data, even if my computer won't boot, but then again not anyone can do it because they would need the password for the user account that encrypted the location in the first place right? :D Correct me if I'm wrong ;)

Another question: "chmod 700" is a form of encryption of a directory, so only I can read/write/exec the data inside right? And the encryption is made based on my user password, which would be needed to decrypt it?

---

### Post by teward on 2009-11-18
Well, to answer the first part, root is the system admin.  If you don't have the password for root, you're kinda screwed unless you can login to the terminal as an admin, then just do: sudo su.

***EDIT: POOF!  Incorrect information has been obliterated by the poster.***

---

### Post by FuturePilot on 2009-11-18
> **jensen1604 said:**
> 

Another question: "chmod 700" is a form of encryption of a directory, so only I can read/write/exec the data inside right? And the encryption is made based on my user password, which would be needed to decrypt it?

No, it's a permission, nothing more. Everything is still in clear text and as mentioned above, the root user could still access your files. If your computer got stolen, it would be trivial for someone to access your files. If you want encryption look into using the Encrypted LVM option in the alternate Ubuntu installer or look into using "ecryptfs" to encrypt your /home directory.

> **TrekCaptainUSA said:**
> 
For the second part, to decrypt the home directory,
No, see above. chmod 700 <something> does not encrypt it. It's only a permission

---

### Post by teward on 2009-11-18
> [quote]something TrekCaptainUSA said[/quote]I thought I removed the incorrect information.  How'd you get it to correct me?  :p


Also, the code I posted above, it includes examples of what might be shown, so only type into the terminal the parts after the # or after the root@compName:/#

---

### Post by jensen1604 on 2009-11-18
> **TrekCaptainUSA said:**
> Well, to answer the first part, root is the system admin.  If you don't have the password for root, you're kinda screwed unless you can login to the terminal as an admin, then just do: sudo su.

For the second part, to decrypt the home directory, you'll need access as root to change its permissions so you can access it, so sudo su or the method I posted would allow you to use root and its powers to decrypt it.  The files, however, would still be copied, and you'd need to change the permissions back on the destination folder so you can access them without root or the terminal.

So even after I've copied my files to another media I still can't access them because the data is still encrypted? So I would have to change the permissions for the files through root.
Would this command be suitable for that:
```
myname@mycomputer:~$ sudo su
[sudo] password for myname <passphrase>
root@mycomputer:~$ chmod 755 /mystuff/private
root@mycomputer:~$exit
```And then my private data would be decrypted right? :)

EDIT:
> **FuturePilot said:**
> No, it's a permission, nothing more. Everything is still in clear text and as mentioned above, the root user could still access your files. If your computer got stolen, it would be trivial for someone to access your files. If you want encryption look into using the Encrypted LVM option in the alternate Ubuntu installer or look into using "ecryptfs" to encrypt your /home directory.


No, see above. chmod 700 <something> does not encrypt it. It's only a permission

Oh.. So if my HDD got stolen the thief could use his root user to change the permission of my private data? Meh :S

---

### Post by Mis_Puchatek on 2009-11-18
As FuturePilot have said, do not mistake encryption with permission.
With any permission :
- If 'one' has an physical access to your hd, permission will not help you. All your data belong to 'one'.
With encryption :
- even if they have an access to your data, they are encrypted and safe(depends on method of encryptions, and few more issues).

I encourage to read a little about permissions and encryption issues on wikipedia, or anywhere. It will help you.

---

### Post by teward on 2009-11-18
> **jensen1604 said:**
> So even after I've copied my files to another media I still can't access them because the data is still encrypted? So I would have to change the permissions for the files through root.
Would this command be suitable for that:
```
myname@mycomputer:~$ sudo su
[sudo] password for myname <passphrase>
root@mycomputer:~$ chmod 755 /mystuff/private
root@mycomputer:~$exit
```And then my private data would be decrypted right? :)

no, it would just allow others to access it.  it wouldn't decrypt anything because chmod 755 <anything> is just changing the permissions on the folder.  It doesn't encrypt the data.  Even if its got 700 permissions, if I had your hard drive, and used root on my Linux, I'd be able to see and access everything.  So nothing was ever encrypted by you using chmod 700

---

### Post by jensen1604 on 2009-11-19
> **TrekCaptainUSA said:**
> no, it would just allow others to access it.  it wouldn't decrypt anything because chmod 755 <anything> is just changing the permissions on the folder.  It doesn't encrypt the data.  Even if its got 700 permissions, if I had your hard drive, and used root on my Linux, I'd be able to see and access everything.  So nothing was ever encrypted by you using chmod 700

I see, thanks guys :) I'm gonna read up on encryption possibilities when I get home from work.. I should have read more up upon chmod, but now it's clear to me. Chmod just set the read, write and execute permissions on one computer, but any root would be able to go past that :p

---

### Post by teward on 2009-11-19
> **jensen1604 said:**
> I see, thanks guys :) I'm gonna read up on encryption possibilities when I get home from work.. I should have read more up upon chmod, but now it's clear to me. Chmod just set the read, write and execute permissions on one computer, but any root would be able to go past that :p

Yup.  Root can do anything on the computer.  And chmod doesn't mess with your encryption or anything.  That's a whole different issue.  Oh, crap, someone just killed my Ubuntu install on my desktop (see what I mean about not logging out of root?  :P  they deleted everything.  *goes off to doom the person who killed his Desktop*)

---

