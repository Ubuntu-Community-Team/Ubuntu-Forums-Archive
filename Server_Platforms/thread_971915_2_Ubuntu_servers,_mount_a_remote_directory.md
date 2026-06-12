---
title: "2 Ubuntu servers, mount a remote directory"
date: 2008-11-05
forum: Server Platforms
---

### Post by Emjx on 2008-11-05
I think this may be a case of me searching for the wrong thing and not finding the answer which is probably readily available...

I have two Ubuntu servers, one running as an FTP server (servera) and one to be purely a file server (serverb). I would like to mount a directory that exists in B on A (i.e the directory /opt/ftpstore is on B, I would like this to be available on server A as /opt/ftpstore). I know as much as that I need to use mount but am unsure what the actual syntax is - any help would be appreciated!

---

### Post by Iowan on 2008-11-05
Depending on what filesystem you use, [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") or [SSHFS]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/") might be useful.

---

### Post by Emjx on 2008-11-06
Thanks - NFS worked a treat.

---

