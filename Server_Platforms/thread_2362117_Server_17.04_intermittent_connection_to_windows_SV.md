---
title: "Server 17.04 intermittent connection to windows SVR 2012 R2 shares"
date: 2017-05-24
forum: Server Platforms
---

### Post by spardha on 2017-05-24
Hi,

I'm trying to connect server 17.04 to my Windows Domain shares.  I've had a previous installation of 16.04 working without issue but don't have that box anymore and can't remember how I got it working.

So to start I've edited the /etc/fstab with the following:
//192.168.1.253/Movies /home/docker/library/Movies cifs credentials=/home/.smbcredentials,rw,uid=1000,gid=1000,nounix,iocharset=utf8,sec=ntlm  0 0

the smbcredentials contains the following:
username=USERNAME
password=xxxxxxxxxx
domain=HOMESPACE

the above works with a sudo mount -a

but the share will drop after so long, not sure how long though haven't been able to time it.  Then after a reboot or another mount -a it'll work again.

Scouring the net i have tried different combinations of the above line but nothing keeps the connection alive permanently.  Any help will be appreciated

---

### Post by slickymaster on 2017-05-24
*Thread moved to **Server Platforms**.*

---

### Post by Michael_McKenney on 2017-05-24
I am having the same type of issue.  Upgraded from 16.10 to 17.04.   SAMBA works with Windows 7 x64.   It no longer works with Windows XP x64.  I was going to uninstall and reinstall SAMBA first.  If that does not work, go back to 16.10.

---

### Post by spardha on 2017-05-24
Didnt think it would be an issue got all my applications running and before trying to connect to the shares... didn't really want to have to start again but maybe 17.04 isn't ready for this sort of thing.

---

### Post by Michael_McKenney on 2017-05-24
[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685")

 meantioend changing SMB min protocol back to SMB1 from SMB2.   Posted back to him and looking into it.   

min protocol = SMB2 forces you off of old authenticate they consider risky.   My question to you is I can get Windows 7 x64 to work fine.   2012 R2 = Windows 8.  So why did yours stop working?

---

### Post by spardha on 2017-05-24
> **Michael_McKenney said:**
> [**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685")

 meantioend changing SMB min protocol back to SMB1 from SMB2.   Posted back to him and looking into it.   

min protocol = SMB2 forces you off of old authenticate they consider risky.   My question to you is I can get Windows 7 x64 to work fine.   2012 R2 = Windows 8.  So why did yours stop working?

Not sure what you mean?

---

### Post by Michael_McKenney on 2017-05-24
He said it could be the new SMB standards are blocking shares from working on Windows.   It might be necessary to change the min protocol = something lower than SMB2.

---

### Post by spardha on 2017-05-24
> **Michael_McKenney said:**
> He said it could be the new SMB standards are blocking shares from working on Windows.   It might be necessary to change the min protocol = something lower than SMB2.


I see, is that possible?

---

### Post by Michael_McKenney on 2017-05-24
Yes, I am dealing with authentication issues with Outlook 2016 on Windows 2016/Exchange 2016 that are intermittent in my data center.  What is the error you are getting trying to connect? I get access is denied.

---

### Post by Morbius1 on 2017-05-24
>  //192.168.1.253/Movies /home/docker/library/Movies cifs  credentials=/home/.smbcredentials,rw,uid=1000,gid=1000,nounix,iocharset=utf8,sec=ntlm  0 0
And is it less intermittent when you add the [COLOR=#0000cd]**vers=3.0**[/COLOR] option:
>  //192.168.1.253/Movies /home/docker/library/Movies cifs  credentials=/home/.smbcredentials,rw,uid=1000,gid=1000,nounix,iocharset=utf8,sec=ntlm[COLOR=#0000cd]**,vers=3.0**[/COLOR]  0 0

---

### Post by spardha on 2017-05-25
> **Morbius1 said:**
> And is it less intermittent when you add the [COLOR=#0000cd]**vers=3.0**[/COLOR] option:


Thanks will try this and report

---

### Post by spardha on 2017-05-25
> **spardha said:**
> Thanks will try this and report
Tried to do a manual mount with that string but got parse error

---

### Post by Morbius1 on 2017-05-25
Can you post the line you used?

**EDIT**: When I posted my original suggestion I added the new vers parameter to your original post. But your original post had this:
> iochar  set=utf8
Is that just a forum anomaly or was there an actual space between iochar and set=utf8?

---

### Post by Morbius1 on 2017-05-25
In case anyone is playing the home version of this game what I am  attempting to modify is the version of the SMB dialect that the Linux  client is using to connect to the Windows server.

By default  mount.cifs will use SMB1 which will work for all Windows servers from WinNT on but is  considered "chatty" in a world dominated by SMB3. You correct for this  by using the vers option. From man mount.cifs:
> vers=
SMB protocol version. Allowed values are:

 1.0 - The classic CIFS/SMBv1 protocol. This is the default.

 2.0 - The SMBv2.002 protocol. This was initially introduced in Windows Vista Service Pack 1, and Windows Server
       2008. Note that the initial release version of Windows Vista spoke a slightly different dialect (2.000) that is not
               supported.

2.1 - The SMBv2.1 protocol that was introduced in Microsoft Windows 7 and Windows Server 2008R2.

[COLOR=#0000cd]**3.0**[/COLOR] - The SMBv3.0 protocol that was introduced in Microsoft Windows 8 and **[COLOR=#0000cd]Windows Server 2012[/COLOR]**.


So the line in fstab would be - this time I will put it in ```
 blocks:
[CODE]//192.168.1.253/Movies /home/docker/library/Movies cifs credentials=/home/.smbcredentials,rw,uid=1000,gid=1000,nounix,iocharset=utf8,sec=ntlm,vers=3.0  0 0  
```
Changing protocol levels in smb.conf will do you no good because mount.cifs doesn't look at smb.conf.

If you are getting a parsing error from that line it is something I cannot reproduce.

---

### Post by spardha on 2017-05-26
> **Morbius1 said:**
> In case anyone is playing the home version of this game what I am  attempting to modify is the version of the SMB dialect that the Linux  client is using to connect to the Windows server.

By default  mount.cifs will use SMB1 which will work for all Windows servers from WinNT on but is  considered "chatty" in a world dominated by SMB3. You correct for this  by using the vers option. From man mount.cifs:

So the line in fstab would be - this time I will put it in ```
 blocks:
[CODE]//192.168.1.253/Movies /home/docker/library/Movies cifs credentials=/home/.smbcredentials,rw,uid=1000,gid=1000,nounix,iocharset=utf8,sec=ntlm,vers=3.0  0 0  
```
Changing protocol levels in smb.conf will do you no good because mount.cifs doesn't look at smb.conf.

If you are getting a parsing error from that line it is something I cannot reproduce.

When trying that line I get usage options so the syntax of that string is wrong somewhere

---

### Post by spardha on 2017-05-26
I've change the syntax to:


sudo mount -t cifs //SERVER/Movies /home/docker/library/Movies -o username=username,password=password,domain=homespace,file_mode=0777,dir_mode=0777
this work without issue on a manual mount but not in the fstab.

---

### Post by Morbius1 on 2017-05-26
> When trying that line I get usage options so the syntax of that string is wrong somewhere 				
You don't type that line in a terminal. That's the line you would have in fstab.

If you want to do a terminal mount the line would read:
```
sudo mount -t cifs //192.168.1.253/Movies /home/docker/library/Movies -o credentials=/home/.smbcredentials,rw,uid=1000,gid=1000,nounix,iocharset=utf8,sec=ntlm,vers=3.0
```

---

### Post by spardha on 2017-05-26
> **Morbius1 said:**
> You don't type that line in a terminal. That's the line you would have in fstab.

If you want to do a terminal mount the line would read:
```
sudo mount -t cifs //192.168.1.253/Movies /home/docker/library/Movies -o credentials=/home/.smbcredentials,rw,uid=1000,gid=1000,nounix,iocharset=utf8,sec=ntlm,vers=3.0
```

Yeah it was in the fstab when running a sudo mount -a i was getting a parse error.

---

### Post by Morbius1 on 2017-05-26
I'm done here. I don't know how to explain this any other way. You don't do a "sudo mount -t cifs" in fstab. 

I would suggest you contact whoever added this line to your /etc/fstab file:
```
 //192.168.1.253/Movies /home/docker/library/Movies cifs  credentials=/home/.smbcredentials,rw,uid=1000,gid=1000,nounix,iocharset=utf8,sec=ntlm  0 0
```
And have them add the ",vers=3.0" option to the current options list so that it looks like this:
```
 //192.168.1.253/Movies /home/docker/library/Movies cifs  credentials=/home/.smbcredentials,rw,uid=1000,gid=1000,nounix,iocharset=utf8,sec=ntlm,vers=3.0  0 0
```

---

