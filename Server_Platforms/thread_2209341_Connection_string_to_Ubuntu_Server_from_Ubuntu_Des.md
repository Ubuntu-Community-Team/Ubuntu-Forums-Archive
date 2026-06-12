---
title: "Connection string to Ubuntu Server from Ubuntu Desktop"
date: 2014-03-05
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2014-03-05
Hi all

If this is the wrong forum, apologies.

Have a LAN with a mix of Windows boxes, a Ubuntu Server 12.04 LTS and now a Ubuntu Desktop 13.10

The Ubuntu server has USB drives attached and the following notes relate to connecting to the USB drives through the 'Connect to Server' dialog from another Ubuntu server.

# To access another server's USB drive(s)
# Home Folder > File > Connect to Server...
# Server: econel
# Type: Windows share
# Share: Share name
# Domain: WORKGROUP
# User name: user
# Password: password

# Check 'Remember this password'

# Connect and save as Bookmark

However the 'Connect to Server' dialog in 13.10 desktop does not have anywhere to enter the data.

Is it possible to create a string containing the required data, please?

TIA

---

### Post by cariboo on 2014-03-06
You may get more help here.

---

### Post by ChrisRChamberlain on 2014-03-07
cariboo907

Thanks for the redirection

---

### Post by steeldriver on 2014-03-07
In 13.10 it has been split into 2 dialogs - you enter the server details in the 1st one, then when you press Connect a second dialog will pop up asking for the remaining data

---

### Post by ChrisRChamberlain on 2014-03-07
steeldriver 

Thanks for you reply

The first connection string is:-```
smb://econel/
```

The second dialog is a list of shares on the server without the facility to enter any further data.

All the conventional shares allow access as they do not require credentials.

Selecting a share that is a USB device produces the messagebox error message:-> Unable to access location

Failed to mount Windows share: Permission denied

Credentials are theoretically not required for the USB drives, either.

Linux Mint has the full dialog and works as expected so why not Ubuntu Desktop?

---

### Post by nerdtron on 2014-03-07
The file manager of Linux Mint is different from the file manager of Ubuntu 13.10.

On the URL bar of the file manager in Ubuntu 13.10 type:
```
sftp://user@IPaddress
```

You'll be asked for the credentials and automatically be directed to the home folder of that user.

---

### Post by ChrisRChamberlain on 2014-03-07
nerdtron

Thanks for your reply.

Your suggestion indeed takes you to the home folder of the server.

So how do you navigate to a Windows share accessible as './media/sharename'?

---

### Post by Morbius1 on 2014-03-07
EDIT: Completely misunderstood your earlier post.

As far as the usb devices are they formatted to NTFS?

What are the permissions of /media/sharename?
```
 ls -al /media/sharename
```

---

### Post by ChrisRChamberlain on 2014-03-07
Morbius1

Thanks for your reply.

Yes, formatted to NTFS

folder permissions are :- drwx------ 

except root which is :- drwxr-xr-x

---

### Post by Morbius1 on 2014-03-07
Try this first:

In Connect to Server enter the server/share this way:
```
smb://username@econel/sharename
```
You will be prompted for a password.

This issue here is not a samba error but a Linux permissions error. The way I suggest above will work if the owner of the mounted partition is "username". If not then we need to fix the share definition so that you can access the share. For that we need the output of the following command:
```
testparm -s
```

---

### Post by ChrisRChamberlain on 2014-03-07
Morbius1 

```
smb://username@econel/sharename
```

That did it!

Many thanks to all who replied - why it had to be so difficult defeats me :confused:

---

### Post by Morbius1 on 2014-03-07
>  why it had to be so difficult defeats me :confused:
I may have an answer for that but it's going to be a rant so apologies in advance.

Gnome is trying it's best to copy Apples OSX. This is Connect to Server in OSX:
[ATTACH=CONFIG]250935[/ATTACH]
Look familiar?

Don't get me wrong if you are going to copy the desktop of another OS the one in OSX is a fine choice. But in this case the old Gnome version was supperior becase the new way requires the user to know the syntax of how to connect and how it changes from what type of server.

---

