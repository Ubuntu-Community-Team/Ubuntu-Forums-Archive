---
title: "Samba file server help!"
date: 2010-06-18
forum: Server Platforms
---

### Post by w1ll1am on 2010-06-18
Hello I have been trying to set up a samba file server for a few days now and i can not figure out what i am doing wrong.

samba is installed
smb.conf is configured with two shares

[homes]
   comment = Home Directories
   browseable = yes
   read only = no
   creat mask = 0775
   directory mask = 0775
   valid users = my user name

[test]
path = /home/my user name/test
valid users = my user name
read only = no
browseable = yes
writable = yes

I created the path

mkdir /home/my user name/test

I have created the user 

smbpasswd -a my user name

and enabled 

smbpasswd -e my user name

global settings are set to 

security = user

workgroup = my work group

everything else has been kept the same as if it was an original smb.conf file

I have ubuntu 9.10 server edition installed the 32-bit version.

I can see the server in windows XP my network places. When I try to access my server from one of my windows xp machines i receive the error message 

\\UBUNTUFILESERVERubuntufileserver server (Samba,Ubuntu) is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permission.

The parameter is incorrect

my servers name is Ubuntufileserver.

One time it worked I got in is asked for my username and password I did so and I tried to make a folder and it would not let me so I tried to change something and then I had not access like above so I put the smb.conf file back the way it was and still nothing.

Any help would be highly appreciated thanks in advance

---

### Post by Wayne_V on 2010-06-18
Try testparm (see 'man testparm')

Try to see if smbclient shows what you expect:

ubuntufileserver> smbclient -L ubuntufileserver -U <your user name>

Make sure you are restarting smb after every change.

Check out SWAT ([http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html)) It's a great tool.

---

### Post by Morbius1 on 2010-06-18
Ubuntufileserver is 16 characters long. Close but no cigar. Must be 15 characters or less. Easiest way to fix it:

Add the following line in the [global] section of smb.conf:
```
netbios name = UbuntuFS
```Then restart samba. In Ubuntu 9.1 the command is:
```
 sudo service samba restart
```
Also what are the permissions of /home/username/test ?

Also2, if you're going to use swat make a copy of your current smb.conf since swat is destructive in the sense that it doesn't edit your existing smb.conf it creates a new one:
> SWAT is no longer actively maintained, and its default configuration is not secure for use over an untrusted network.  SWAT will also rewrite smb.conf, rearranging the entries and deleting all comments as well as include= and copy= options, so is not suitable for use in conjunction with hand-edited smb.conf files or the default package-managed configuration.

---

### Post by w1ll1am on 2010-06-18
> **Morbius1 said:**
> Ubuntufileserver is 16 characters long. Close but no cigar. Must be 15 characters or less. Easiest way to fix it:

Add the following line in the [global] section of smb.conf:
```
netbios name = UbuntuFS
```Then restart samba. In Ubuntu 9.1 the command is:
```
 sudo service samba restart
```
Also what are the permissions of /home/username/test ?

Also2, if you're going to use swat make a copy of your current smb.conf since swat is destructive in the sense that it doesn't edit your existing smb.conf it creates a new one:


Holy crap your a genius thanks that worked now i just have to set up the permissions right i can't make folders. If you have any advices it would help thanks

---

### Post by Foeburner on 2010-06-18
Heres a tip, if you want to setup a backup folder and dont want it visible to everyone, just turn browseable to no 
```
browseable = no
```

Now that your issue is solved, please switch this thread to solved.  :)

---

### Post by w1ll1am on 2010-06-18
How do I set permissions so i can write to folders

---

### Post by winhaung on 2010-06-19
I set up samba file server on ubuntu 8.04 server. first, i can call it form windows. i try to share another file and restart the services again. i got the error " network path is not found". i can ping the server. how should i do?
thz

---

### Post by Morbius1 on 2010-06-19
> **w1ll1am said:**
> How do I set permissions so i can write to folders

What's confusing me is this:
> [test]
path = /home/my user name/test
valid users = my user name
read only = no
browseable = yes
writable = yesFirst you created a folder called "test" in your own home directory.
By default that would have set up a folder with owner = "my user name" and permissions set to 0755. "my user name" will have read / write access ( the "7" part ) and all others would have read only access ( the "5" part ).
Then you created the above share that will allow only "my user name" to gain access.

This is textbook and "my user name" should have write access to that share assuming you created a samba user named "my user name".

---

### Post by w1ll1am on 2010-06-19
I figured it out i did not chmod the path now it works thanks for the help

---

### Post by w1ll1am on 2010-06-19
> **winhaung said:**
> I set up samba file server on ubuntu 8.04 server. first, i can call it form windows. i try to share another file and restart the services again. i got the error " network path is not found". i can ping the server. how should i do?
thz

Do you have the netbios name under the global section of your smb.conf file?

---

