---
title: "FTP server or shared folders?"
date: 2009-03-18
forum: Server Platforms
---

### Post by kidux on 2009-03-18
I'm new in the server arena, and want to setup a media/file server. Would an FTP server be the way to go to share files, including ripped movies and music, on my local home network, or just share folders a la NFS. I was using SMB to share, but transfers kept timing out on me, so want something that works.

Also, what about MythTV? I'll do some research on it, but just wanted quick ideas or opinions on it.

Thanks!

---

### Post by kidux on 2009-03-20
*crickets*

---

### Post by Dr Small on 2009-03-20
If it's on the local network, FTP would be fine. I personally would use SFTP, but not everyone likes to use SSH to connect.

---

### Post by kidux on 2009-03-20
> **Dr Small said:**
> If it's on the local network, FTP would be fine. I personally would use SFTP, but not everyone likes to use SSH to connect.
I really wouldn't have any problems either way, just curious as to the best way to set it up. Are we talking Apache or something else?

---

### Post by hyper_ch on 2009-03-20
if it's just for a lan then use samba.

---

### Post by HermanAB on 2009-03-20
FTP is the easiest thing to get to work.  NFS is better, but then you have to ensure that the user GID and UID is the same on all machines.  Of all the ways to share data, Samba is the most difficult to get to work.

Cheers,

Herman

---

### Post by Almighty on 2009-03-20
Since you only want to share files on your local LAN, I'd stick to NFS if it's not a mixed OS network. Keep it simple.

---

### Post by hyper_ch on 2009-03-20
samba is simple... well, it depends what setup you've got. If you have windows clients then go for samba... if not, you might want to use nfs or sshfs.

---

### Post by kidux on 2009-03-20
> **hyper_ch said:**
> if it's just for a lan then use samba.
I was using that but transfers kept timing out for some reason.

---

### Post by Ape3000 on 2009-03-20
I prefer SFTP on LAN file transfers. You can share your folders by installing openssh-server. Then move to another computer on the LAN and open nautilus. Type sftp://the_ip_of_the_computer_with_the_ssh_server/ and login with your username and password.

---

### Post by kidux on 2009-03-20
> **Ape3000 said:**
> I prefer SFTP on LAN file transfers. You can share your folders by installing openssh-server. Then move to another computer on the LAN and open nautilus. Type sftp://the_ip_of_the_computer_with_the_ssh_server/ and login with your username and password.

Is there a way to keep that linked, or perhaps a network browser. I prefer XFCE as well, so I know I need to do some tweaking to get Thunar to see network shares.

---

### Post by Ape3000 on 2009-03-20
> **kidux said:**
> Is there a way to keep that linked, or perhaps a network browser. I prefer XFCE as well, so I know I need to do some tweaking to get Thunar to see network shares.

It is possible to mount SFTP with something like this: [http://www.spencerstirling.com/computergeek/lufs.html](http://www.spencerstirling.com/computergeek/lufs.html)

If you want to keep the folders always mounted NFS would be also a good option: [http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

---

