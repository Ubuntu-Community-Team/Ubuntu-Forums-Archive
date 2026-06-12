---
title: "Connect to computer with USB’s  for file transfers."
date: 2017-03-03
forum: Server Platforms
---

### Post by irv on 2017-03-03
I have an old laptop that I am not using and I have 2 USB drives that I use for backups. I have the laptop setup and running with 2 large USB drive connected for backups.
I don’t really need to connect to the Internet, just my local network.
All my computers are running Linux (I have no Windows PC’s in my house.)
I tried an online program called TeamViewer12 and it works but it is overkill. I have all my computer registers with them and I can connect just fine to transfer files, but there is got to be a better way to do this.
Should I just setup the old laptop as a file server and then use something like FileZilla to backup files? Some ideas would be nice. I am just looking for an easy way to do this.

I did have a server setup for this, but I move the server to a completely different location. I can still get to it over the Internet, but I don’t want to do backups that way.
Thanks for the suggestions ahead of time.

---

### Post by irv on 2017-03-03
After all is said and done, I think the best way is to just setup a OpenSSH Server on the laptop and that is what I am going to do. I will mark solved and leave this for others who want to do the same.
[https://help.ubuntu.com/14.04/serverguide/openssh-server.html]("https://help.ubuntu.com/14.04/serverguide/openssh-server.html")

---

### Post by howefield on 2017-03-03
Sshfs might be useful too, allowing you to mount network storage, folders and files and interact as if it were local.

---

### Post by irv on 2017-03-05
> **howefield said:**
> Sshfs might be useful too, allowing you to mount network storage, folders and files and interact as if it were local.

I don't have it installed, but yes, it would work also. I am just going to use openSSH. I can just get to everything with that via file browser (Nautalis).

---

