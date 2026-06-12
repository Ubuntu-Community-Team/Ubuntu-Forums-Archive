---
title: "Can you please include yet another 'shell/tool' as default?"
date: 2018-05-24
forum: Server Platforms
---

### Post by alienquake on 2018-05-24
Hi,


Can you please include yet another 'shell/tool' as default? I'm talking about Powershell. I need this to do my stuff and having it as default system component would be a life savior.

---

### Post by cariboo on 2018-05-24
If you really need powershell try here:

[https://gist.github.com/supermamon/853442a06d13de088c4a43153facecf9](https://gist.github.com/supermamon/853442a06d13de088c4a43153facecf9)

---

### Post by alienquake on 2018-05-25
> **cariboo said:**
> If you really need powershell try here:

[https://gist.github.com/supermamon/853442a06d13de088c4a43153facecf9](https://gist.github.com/supermamon/853442a06d13de088c4a43153facecf9)
Thanks but it's not what I've asked. I know how to install it but that's not the point. The point is to have it ready out-of-the-box. It brings significant value for me and what I do for customers.

Just for clarification - this is the right place? I mean, does Ubuntu developers will see such request? Or maybe there is a issue tracker/other place?

---

### Post by kerry_s on 2018-05-25
> this is the right place? I mean, does Ubuntu developers will see such request? Or maybe there is a issue tracker/other place? 

this is a user forum, where users get help from other users.

i very much doubt they will even consider it, since it's just for you. otherwise people would be asking for all kinds of things just for them.

if ya want something done, best to do it yourself. [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

this seems easier-> [https://askubuntu.com/questions/741753/how-to-use-cubic-to-create-a-custom-ubuntu-live-cd-image](https://askubuntu.com/questions/741753/how-to-use-cubic-to-create-a-custom-ubuntu-live-cd-image)

---

### Post by slickymaster on 2018-05-25
> **alienquake said:**
> Thanks but it's not what I've asked. I know how to install it but that's not the point. The point is to have it ready out-of-the-box. It brings significant value for me and what I do for customers.

Just for clarification - this is the right place? I mean, does Ubuntu developers will see such request? Or maybe there is a issue tracker/other place?

I'd recommend you to address your query to the Ubuntu Server Development mailing list: [email]ubuntu-server@lists.ubuntu.com[/email] or try to ping a server team member on chat.freenode.net at #ubuntu-server

---

### Post by kerry_s on 2018-05-25
[https://www.ostechnix.com/create-custom-ubuntu-live-cd-image/](https://www.ostechnix.com/create-custom-ubuntu-live-cd-image/)

this ones much easier to follow. good luck.

---

### Post by spjackson on 2018-05-25
I think that there is very little chance of getting it included as a "default system component" for Ubuntu when it isn't in Debian, even if requested through the appropriate channels. I could be wrong.

---

### Post by alienquake on 2018-05-25
Thanks for lot of userful information. Much appropriated.

---

### Post by uRock on 2018-05-25
> **cariboo said:**
> If you really need powershell try here:

[https://gist.github.com/supermamon/853442a06d13de088c4a43153facecf9](https://gist.github.com/supermamon/853442a06d13de088c4a43153facecf9)

Learn something new every day. Thanks! 

I highly doubt they'd ever make this part of a standard install. If it were, then it would be one of the first things I'd remove.

---

### Post by TheFu on 2018-05-26
> **uRock said:**
> Learn something new every day. Thanks! 

I highly doubt they'd ever make this part of a standard install. If it were, then it would be one of the first things I'd remove.

+1.  I already have to purge nano with every install so purging powershell wouldn't be too much added hassle in our ansible scripts.  PowerShell isn't exactly known for great security on other platforms.

People have been trying to make Unix systems more like Windows for some time.  Heck, I did too, when I was learning.  Then something "clicked" and I started going the other way - trying to get Windows to be more Unix-like.  When that failed, I finally just decided to use each sort of OS for those things it was best at.

---

