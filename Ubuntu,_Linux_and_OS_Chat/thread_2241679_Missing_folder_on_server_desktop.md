---
title: "Missing folder on server desktop"
date: 2014-08-27
forum: Ubuntu, Linux and OS Chat
---

### Post by jesse22 on 2014-08-27
I recently installed Ubuntu 14.04.1 lts and setup up a Samba server. I configured the Samba server with Webmin. Everything was running fine until I ran an update.  After I ran the update, the folder I had on my desktop was missing. I didn't notice this folder was missing until a day or two after the update. Honestly, I'm not 100% sure it was the update that caused it.  But it was the only thing I had done prior to it going missing.  

If I try creating a new folder on my desktop named the same thing (IT), it asks me if I would like to replace it, so I know it is still there somewhere.  When I try opening the desktop through the file system explorer, it gives me an error stating "No such device or address". I am hoping that someone here on this forum would have the knowledge to help me out. That folder has a lot of things I need.  Thank you for your time.

Here are a few pictures of the messages I receive. 

[Link 1]("https://www.dropbox.com/s/5ngzo99n32ahd9c/createfolderit.PNG?dl=0")
[Link 2]("https://www.dropbox.com/s/zflpzfere43vdo2/error%202.PNG?dl=0")
[Link 3]("https://www.dropbox.com/s/xm8ucbdph6lw06k/ubuntudesktoperror.PNG?dl=0")
[Webmin]("https://www.dropbox.com/s/shosnmyulyuyr73/webminoverview.PNG?dl=0")
[Samba Server Config]("https://www.dropbox.com/s/c5n8uxvs7pl29an/itservershare.PNG?dl=0")

-Jesse

---

### Post by jesse22 on 2014-08-28
I figured it out.  I re-installed the full Ubuntu desktop and restarted the server.  Not sure what happened to cause that.  When the server loaded the desktop, the folder was there with all my files.

---

