---
title: "Can't mount Windows 7 share with fstab, working with &quot;mount -t cifs&quot;"
date: 2011-08-31
forum: Server Platforms
---

### Post by Katsche on 2011-08-31
Hi all,
 
I am referring to the post below, which was asked by me in the "**Mount samba shares with utf8 encoding using cifs"**-Guide about a weak ego. Since I didn't get any help there, I would like to ask this question again here:
 
> **Katsche said:**
> Hi all,
 
I am new to Linux, but think that this will be a love story... :P
 
I am running Ubuntu Server Linux 64Bit (11.04) in VirtualBox (4.1.0) and would like to connect to a share on the Windows 7 64Bit host. I already did this with the following command, sadly I am not able to mount this drive automatically by adding it to fstab. Find my fstab entry and the error message below, too.
 
When I enter this, I am asked for the Windows password. After entering the password the mount works completely fine:
```
sudo mount -t cifs //MW7XM76LYPUH0D/Users/nachname.vorname /media/splunk -o username="dir/nachname.vorname",uid=0,gid=0,nls=utf8

```
 
 
This somehow is giving me the following errors. If i try to test the changes in fstab with "sudo mount -a" I am asked for the password, too but it won't work like with the one above:
```
//MW7XM76LYPUH0D/Users/nachname.vorname /media/splunk cifs username="dir/nachname.vorname",uid=0,gid=0,nls=utf8 0 0

```
 
```
[ 897.066624] CIFS VFS: Send error in SessSetup = -13
[ 897.071901] CIFS VFS: cifs_mount failed w/return code = -13
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```
 
This doesn't work, too:
 
```
//MW7XM76LYPUH0D/Users/nachname.vorname /media/splunk cifs username="dir/nachname.vorname",rw,nounix,uid=0,gid=0,nls=utf8 0 0 
```
 
Kind regards
Katsche
 
 
P.S.: Another question: the password of the windows user contains special characters. How do I write such a password (just to give u an example: tGu39fl?! ) so that I can save it within the smbcredentials file or just add it to the mount options using "password="?
 
Kind regards,
Katsche

---

### Post by volkswagner on 2011-08-31
From your /etc/fstab:
```
//MW7XM76LYPUH0D/Users/nachname.vorname /media/splunk cifs username="dir/nachname.vorname",uid=0,gid=0,nls=utf8 0 0
```

Three things stand out to me.

[LIST=1]
[*]Your Windows 7 machine name (net bios name) is kinda long.  Try to keep it less than 12 characters I think.
[*]It also helps if you include your workgroup/domain name for your windows box.
[*]You also need local DNS working or you can try using the machine ip address vs. machine name.
[/LIST] 

You can use the credentials file method or put everything in the /etc/fstab entry.  I prefer to use credentials file method.

Try using the following in your /etc/fstab:

```
//MW7XM76LYPUH0D/Users/nachname.vorname /media/splunk cifs credentials=/root/smb/credentials,uid=0,gid=0,nls=utf8 0 0
```

You can add the following to /root/smb/credentials:

```
username=windowsUserName
password=secretPassword
domain=WORKGROUP

```

Change the above to match your actual conditions for username, password and the workgroup your windows machine is part of.

Also change the permissions for the credential file so it is only readable by root.

---

### Post by Morbius1 on 2011-08-31
@volkswagner, I don't disagree with anything you posted ( except netbios names can be 15 characters or less not 12 ) but I think the problem is his P.S.:
> Another question: the password of the windows user contains  special characters. How do I write such a password (just to give u an  example: tGu39fl?! ) so that I can save it within the smbcredentials  file or just add it to the mount options using "password="?I've never had to deal with this myself but perhaps you can place single quotes around it in a manual mount: 
```
password='tGu39fl?!'
```Problem is I don't think fstab or a credentials file allows single quotes.

---

### Post by Katsche on 2011-09-01
> **Morbius1 said:**
> Problem is I don't think fstab or a credentials file allows single quotes.So i will have to change the password? I am not sure, if this is possible, there are password rules at my workplace.

---

### Post by Katsche on 2011-09-05
This is really important to me. Please help... :(

---

### Post by digital_alchemy on 2011-09-05
> **Katsche said:**
> This is really important to me. Please help... :(

Create the credential file as describes above with your windows login and password.

Then try making the /etc/fstab entry with the following format:


```
//<server_name>/<windows_share>  /<path_to_local_mnt_point>  cifs credential=/home/<your_username>/.credentials,iochart=utf8,file_mode=0777,dir_mode=0777  0  0
```

---

### Post by Katsche on 2011-09-06
This so so great, I just did it. I just have to test, if it is working on startup.
 
The problem was, that I was always using " or ' in the credentials file at the beginning and end of username and password. It is working without any quotes. I am using a fstab entry, which looks like the one from digital_alchemy.
 
Thank you all VERY VERY much! ):P

---

