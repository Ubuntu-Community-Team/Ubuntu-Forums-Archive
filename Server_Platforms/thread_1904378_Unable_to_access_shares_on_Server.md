---
title: "Unable to access shares on Server"
date: 2012-01-04
forum: Server Platforms
---

### Post by AndesHelp on 2012-01-04
I had hoped that by installing the Ubuntu Server to a new system I would finally be able to have a file server on my home network.  However, that does not appear to be the case.

All I need is a simple file server for my home network and I keep running into the same issue.  I can see the Ubuntu Server, but I keep getting the error message that I do not have permission to access it.

I have been through the guides for setting up samba and none of those actions have helped.  It doesn't help when some of the instructions are outdated and the paths they specify no longer exist.  For example:  > sudo /etc/init.d/samba restart  That directory does not exist.  What directory is the executable samba in now?  After setting the workgroup and netbios name I just did a system reboot instead. :confused:

Only my Windows XP can even see the server.  Windows 7 doesn't even list it.

What do I need to do?  If you want a copy on my smb.conf, that will take a while since I will have to manually copy it.

Thanks

---

### Post by LERecords on 2012-01-04
> **AndesHelp said:**
> I had hoped that by installing the Ubuntu Server to a new system I would finally be able to have a file server on my home network. However, that does not appear to be the case.
 
All I need is a simple file server for my home network and I keep running into the same issue. I can see the Ubuntu Server, but I keep getting the error message that I do not have permission to access it.
 
I have been through the guides for setting up samba and none of those actions have helped. It doesn't help when some of the instructions are outdated and the paths they specify no longer exist. For example: That directory does not exist. What directory is the executable samba in now? After setting the workgroup and netbios name I just did a system reboot instead. :confused:
 
Only my Windows XP can even see the server. Windows 7 doesn't even list it.
 
What do I need to do? If you want a copy on my smb.conf, that will take a while since I will have to manually copy it.
 
Thanks
 
hello.. I'm currently working through the same thing, but lets see if i can help.
 
did you setup the share directory in the smb.conf file?
did you create the directory on the hard drive?
did you chown and chmod the directory to allow access (this one is often overlooked and caused me 2 days of headaches before i figured out that i needed to do that)

---

### Post by AndesHelp on 2012-01-04
> **LERecords said:**
> hello.. I'm currently working through the same thing, but lets see if i can help.
 
did you setup the share directory in the smb.conf file?
did you create the directory on the hard drive?
did you chown and chmod the directory to allow access (this one is often overlooked and caused me 2 days of headaches before i figured out that i needed to do that)

This is a new install and what you are asking is not part of any of the installation instructions.  The share directory should have been the users home directory.

I did set-up the workgroup and net bios name as required.  I'll go back into the smb.conf and see if I can find what you are referring to.

---

### Post by LERecords on 2012-01-05
even in the /home/ directory, you may have to chmod the folder you want to use as a share.

---

### Post by Morbius1 on 2012-01-05
You know, none of us here know how you set up your shares or how you've configured Samba so if you can post the output of the following command it would help those who want to help you:
```
testparm -s
```

---

### Post by AndesHelp on 2012-01-05
> **Morbius1 said:**
> You know, none of us here know how you set up your shares or how you've configured Samba so if you can post the output of the following command it would help those who want to help you:
```
testparm -s
```

That is the question.  I did not manually set-up any shares I just followed the installation instructions.  The only configuration I did to Samba was to uncomment the [homes] and the entries in it.  

Thanks.  I will get the testparm -s reading, it will take me a while since I have to manually copy and then type it in here, until I can get ubuntu to allow shares.

---

### Post by LERecords on 2012-01-05
i would just try chmod 0755 /homes/ ..  it worked for me

---

### Post by AndesHelp on 2012-01-16
Sorry Folks,

I was away for Jury Duty last week.  I ended up doing a complete erase the hard drive and reinstall the Ubuntu Server.

I set my /home to chmod 0777.  I know, it should only be 0755 but I was tired of not being able to see anything.  

The original install of Samba had errors and would not allow me to see the server.  I did an apt-get remove samba.  Then did an apt-get install samba.

Now I can see the server named file3.  My next step is to transfer my documents and websites to a directory on file3 so that they can be accessed by any of my systems.  I have, through necessity for customer support, Windows XP Home, XP Pro, Windows 2000, Windows Vista and now Windows 7 32-bit and 64-bit versions.  I have both laptops and desktops in the office and workshop.

I would appreciate any help in setting this up.  The samba.conf has not been touched.  What is my next step.  I have tried to do it on my own before and could never make the files available.

Thanks

---

### Post by bubylou on 2012-01-17
I used this [link]("https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html") to start off my first samba server. its pretty easy to understand and sounds like its just want you want.

---

### Post by AndesHelp on 2012-01-17
Thank You! :D
Thank You! :D
Thank You! :D

I can now copy the files I want to share to the new Ubuntu Server and see them on all of my systems.  With this set-up I can now have a central system for my work.  I was so tired of fighting with the Micro$oft network sharing.

Next will be adding a 1.5TB Hard Drive to the new Sever and doing my Data Back-ups.

Thank You again. :D

---

