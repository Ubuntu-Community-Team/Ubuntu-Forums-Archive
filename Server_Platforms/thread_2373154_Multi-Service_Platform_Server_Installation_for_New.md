---
title: "Multi-Service Platform Server Installation for Newbie"
date: 2017-10-03
forum: Server Platforms
---

### Post by ulrichkenneth on 2017-10-03
Hello, 

1. If I am posting in the wrong part of the forum, kindly let me know.
2. If my Subject/Title isn't sufficient enough, I apologize, I wasn't sure how to describe my idea.

I am wanting to turn my server into a multi-service platform. I know it has more enough of the RAM, CPU, and Disk Storage to handle it. 

But from a security, cross platform service, I want to ensure that it is only secure and able to access from particular logins(I know I can handle majority with UFW).

I want to use my server for the following applications.

[LIST]
[*]Ajenti Web Server
[*]Plex
[*]File Storage
[/LIST]

Is it wise to have all 3 of these applications on the same Ubuntu Server 16.04 or would it be better for a Virtual Machine environment? If one OS can handle all 3, would usernames that are strictly for those directories/applications be best?

If VM environment is suggested, Like I stated above, I am running Ubuntu Server 16.04 CLI Only. What would be a good Virtual Machine application that would work with that?

Thank you in advance.

---

### Post by DuckHook on 2017-10-03
I have moved your post to *Server Platforms* as the more appropriate forum.

What you describe is certainly doable. But it tends to be the solution of commercial vendors due—at least in part—to the fact that every commercial OS licence is a redundant cost. So horking together multiple services on one box is common practice: MS Small Business Server, for example. However, I don't feel this to be either safe or optimal.

In the Linux world, redundant OS costs are a non-issue. Therefore, in my opinion, the VM route is far preferable, not least for the security considerations. There is also a degree of isolation for app failures and sandboxing of (again) security penetrations. The drawbacks are:

[LIST=1]
[*]Multiple VMs are more complicated to manage than a single OS instance and take up more resources.
[*]The arrangement is more brittle because there is still only one point of HW failure.
[/LIST]
For above reasons, I separate all of my server needs into different physical boxes. This is greatly facilitated by the fact that HW is so cheap these days. A basic server can be assembled from scratch for less than $300 and often much less if you go the RPi or used-equipment routes.

There are many VMs to choose from. I used to use VirtualBox which is very user-friendly and well documented, but have recently switched to QEMU/KVM because KVM is native to Linux and is baked into the kernel by default. VMWare is another option (though closed-source and you must pay for commercial use). Another open-source option is Zen, but it's very obscure and tends to be restricted to hard core users as a result.

Info on VMs: [https://help.ubuntu.com/community/VirtualMachines](https://help.ubuntu.com/community/VirtualMachines)

---

### Post by SeijiSensei on 2017-10-03
I've run servers that support multiple services for decades.  Right now I have four Linodes in service that support different combinations of HTTP, SMTP, POP3, IMAP4, DNS, PostgreSQL, MySQL, Sphinx Search, and probably a few I've forgotten. Your list includes none of these except for HTTP, where I'm using Apache, and you're using something I've never heard of. Unix was designed from the ground up as a multiuser, multitasking operating system.  All these years later it still performs remarkably well at that task.

---

### Post by DuckHook on 2017-10-03
@ulrichkenneth

Important to state that SeijiSensei is server Jedi; I am not.

---

### Post by mastablasta on 2017-10-04
> **ulrichkenneth said:**
> 

[LIST]
[*]Ajenti Web Server
[*]Plex
[*]File Storage
[/LIST]



there is no need for WM

Ajenti is a GUI manager for server. it is using apache web server and runs on python if i remember correctly. there is plenty you can lock down in apache. e.g. login only from lan or certain IP, fail2ban... if this is not accessed from outside of lan then it is all even easier.

plex is media server, file storage - well you are storing files what is so special about that?

i am not sure about plex system requirements but the other two need very little. i doubt you will use more than 100 MB ram for the two of them.

if oyu are running apache webserver and you intend to open it to internet you will need to setup at least something like fail2ban and perform general server security hardening.

services on server run separate from each other anyway. the difference between the services and desktop apps is that services listen to outside and are actually made so you can access them from outside of server.

---

