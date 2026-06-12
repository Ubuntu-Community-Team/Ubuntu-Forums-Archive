---
title: "SSH Authentication fails from outside LAN"
date: 2010-03-29
forum: Server Platforms
---

### Post by kma_jg on 2010-03-29
Hi all,

My first post here. I've been using Ubuntu to run our internal mail server for a while now on Ubuntu server 9.04 and ISPconfig 2. 

I've read a lot of threads on poeple that have difficulty connecting to their server using SSH from  outside the LAN and it is not the same problem I have. Well, not entirely the same.

My problem is that my authentication fails from outside the LAn, but I can connect to the SSH port from outside my LAN. 

The other threads pointed towards checking the router port forwarding etc, but I can see my SSH log in asking for my username and password. So, at this stage I know the port forwarding worked, otherwise I wouldn't even see the log in  prompt.

Has anyone see this before where you can connect, but the authentication fails? I can use the correct username and password from inside the LAN, but using the same credentials from outside fails.

Thanks for your support.

---

### Post by Jakob Lundberg on 2010-03-30
Have ssh access been restricted using the AllowUsers parameter in /etc/ssh/sshd_config ?

---

### Post by s_ø on 2010-03-30
Are you connecting from the same machine inside/outside the LAN?
You need to specify the user to login as, if your local and remote user name dont match.
Also try connecting with the -v option (it shows debug info)

---

