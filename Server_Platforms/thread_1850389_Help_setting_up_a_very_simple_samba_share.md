---
title: "Help setting up a very simple samba share"
date: 2011-09-26
forum: Server Platforms
---

### Post by vassie on 2011-09-26
Hello

I have partitioned and formatted a second hard drive connected to my Ubuntu Server, mounted it to /media/storage and have created a folder called "Share" (full path is /media/storage/Share), I have also taken ownership of that folder by running:

```
sudo chown ben:ben /media/storage/Share
```

I now want to share this folder via Samba to my Windows 7 desktop and laptop, my Ubuntu Server username is ben and my Windows username is Ben, both have the same password, I also want to give my WDTV Live box read only access to the share, using the Windows username WDTVLive

Can someone assist me in setting this up? I'd be very grateful, thanks

Ben

---

### Post by kerry_s on 2011-09-26
Right click on the folder & select share. 
You can fine tune the settings in /etc/samba.conf

---

### Post by vassie on 2011-09-26
> **kerry_s said:**
> Right click on the folder & select share. 
You can fine tune the settings in /etc/samba.conf

I'm using Ubuntu Server, I need to create the share by editing my smb.conf file, but I not too sure what I need to do

---

### Post by Morbius1 on 2011-09-26
Add this to the bottom of smb.conf:
```
[Share]
path = /media/storage/Share
read only = Yes
write list = ben
valid users = ben, wdtvlive
```Restart samba:
```
sudo service smb restart
```Only thing I'm not sure about ( well, there are many things I'm not sure about ... ) is the capitalization difference between "Ben" and "ben"

You may need to edit the following file to make one the same as the other:
```
/etc/samba/smbusers
```and add:
```
ben = Ben
```And then make sure in your smb.conf you have a line in the [global] section:
```
username map = /etc/samba/smbusers
```

---

### Post by vassie on 2011-09-26
> **Morbius1 said:**
> Add this to the bottom of smb.conf:
```
[Share]
path = /media/storage/Share
read only = Yes
write list = ben
valid users = ben, wdtvlive
```Restart samba:
```
sudo service smb restart
```Only thing I'm not sure about ( well, there are many things I'm not sure about ... ) is the capitalization difference between "Ben" and "ben"

You may need to edit the following file to make one the same as the other:
```
/etc/samba/smbusers
```and add:
```
ben = Ben
```And then make sure in your smb.conf you have a line in the [global] section:
```
username map = /etc/samba/smbusers
```

Thanks, what about the wdtvlive user? That is a Windows only account

---

### Post by capscrew on 2011-09-26
> **vassie said:**
> I'm using Ubuntu Server, I need to create the share by editing my smb.conf file, but I not too sure what I need to do

Ops; slow fingers this morning. Morbius1 has the right idea.

---

### Post by Morbius1 on 2011-09-26
> Thanks, what about the wdtvlive user? That is a Windows only accountNot sure what you mean by that. If you don't have a local account for that user on the server create one:
```
sudo useradd -s /bin/true WDTVLive
```Then give him / it a samba password:
```
sudo smbpasswd -a WDTVLive
```
[COLOR=Blue]EDIT: Sorry, doing too many things at once here.[/COLOR]
If you added a user  WDTVLive then change the definition to this:
> [Share]
path = /media/storage/Share
read only = Yes
write list = ben
valid users = ben, WDTVliveI'm not used to doing things with caps in them and I lost focus.

I'll be away for about an hour or so but luckily you have capscrew looking over things so you're in good hands.

---

### Post by vassie on 2011-09-26
Thanks for your help, everything seems to be working fine now

---

