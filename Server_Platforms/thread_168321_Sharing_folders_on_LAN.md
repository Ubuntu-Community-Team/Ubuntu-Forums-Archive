---
title: "Sharing folders on LAN?"
date: 2006-04-30
forum: Server Platforms
---

### Post by Rakaan on 2006-04-30
Hiya,

I am a newbie and I have recently installed ubuntu 5.10 without any problems on one of my old boxes. I must say reading through the articles and forums here, I didnt have any problems at all :) You guys are great and everything was easy to set up.

I have a question which I am sure is answered previously but I just couldnt find the post so will appreciate if someone can put me in the right direction.

My ubuntu runs on a desktop and is behind a router. I have installed Apache, FTP and Mail server mentioned as on this site

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

and everything is set up okay. The question is how do I check if my mail server is running fine?

Secondly, how can I see shared folders on the network as other machines are running windows XP. I understand Samba is something which I'll have to installed and configure. I have done the installation but don't know how to configure and share folder on the local network?

Any advise would be appreciated.
Cheers

---

### Post by cilynx on 2006-04-30
The general theory to test a mail server is to try sending and receiving from an off-network email account such a gmail.

To see the shared folders on your Windows network:
Places > Network Servers > Windows Network
or
```

smbclient -L //hostname

```

To setup your shares on the Ubuntu machine:
System > Administration > Shared Folders
I wouldn't advise trying this on on the command line and SMB is annoying..

---

