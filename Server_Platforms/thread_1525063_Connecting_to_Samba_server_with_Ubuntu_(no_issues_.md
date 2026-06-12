---
title: "Connecting to Samba server with Ubuntu (no issues using windows)"
date: 2010-07-06
forum: Server Platforms
---

### Post by rvause on 2010-07-06
I have two servers, both with almost (different shares) identical samba server configurations. 

Server 1, works fine. I can connect with Windows 7 and I can connect using 'Places > Network' in Ubuntu 10.04

Server 2 is funny. I can connect with Windows 7 but I can not connect using 'Places > Network' in Ubuntu 10.04

Until recently, I was able to access Server 2's samba shares with 'Places > Network' in Ubuntu 10.04 but without warning it started spitting the 'Failed to mount' error at me.

I am guessing this is a server problem (even though server 1's smb.conf is the same up to defining shares) as I have tried from multiple clients running Ubuntu 10.04, all of which fail.

Any help would be appreciated.

---

### Post by Saorex on 2010-07-06
You might wanna try in command line. Here's the one I use and always works great for me:

```
 sudo mount -t smbfs //some_pc/share_name /home/my_user/some_folder/ -o username=windows_username
```

Then the prompt asks for your Windows password. This may not be your long term solution, but it might help you trouble shoot the problem.

---

### Post by Morbius1 on 2010-07-06
If the only thing that's different between Server1 and Server2 ( except the name ) is the share definitions then why not post Server2's shares:

```
testparm -s
```
I don't know what could possibly be in a share definition that allows a Windows client access but not a Linux client, but ...........

---

### Post by capscrew on 2010-07-06
> **Saorex said:**
> You might wanna try in command line. Here's the one I use and always works great for me:

```
 sudo mount -t [COLOR="Red"]**smbfs**[/COLOR] //some_pc/share_name /home/my_user/some_folder/ -o username=windows_username
```
The above (noted in red) will cause problems with later Windows shares.  You shuld use [COLOR="Blue"]**cifs**[/COLOR]>  instead.

Then the prompt asks for your Windows password. This may not be your long term solution, but it might help you trouble shoot the problem.

---

### Post by Saorex on 2010-07-06
> **capscrew said:**
> The above (noted in red) will cause problems with later Windows shares.  You shuld use [COLOR="Blue"]**cifs**[/COLOR]

Really? Thanks for letting me know. I'll do some reading...

---

### Post by capscrew on 2010-07-06
> **Saorex said:**
> Really? Thanks for letting me know. I'll do some reading...
 You can start [**_here_**]("http://manpages.ubuntu.com/manpages/lucid/man8/mount.cifs.8.html").

---

