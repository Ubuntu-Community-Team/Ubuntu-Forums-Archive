---
title: "Cant SSH with putty but terminal ssh session works"
date: 2009-12-28
forum: Server Platforms
---

### Post by buntolith on 2009-12-28
I have just built an ubuntu 9.10 server back home. At the moment it is just a SSH server but I will make it a NFS file server when I have time. I have also just reinstalled Kubuntu & Ubuntu 9.10 on my laptop. I am using RSA keys and I have copied the private and public keys plus the known host file into my ~/.ssh folder. 

When I try to login remotely using putty I get the following:

login as: (so I punch in my login name and a window pops up saying)

Disconnected. No supported authentication methods available

Strangely enough I can start a ssh session with my server using my terminal. 

What can I do to fix this? Are there any files missing or any settings I haven't done yet?

---

### Post by Bachstelze on 2009-12-28
PUTTY doesn't use the keys stored in your ~/.ssh folder. You need to convert them to the PUTTY key format and configure your PUTTY session to use them.

---

### Post by buntolith on 2009-12-28
Ok, how can I do that?

I just logged out from kubuntu and logged in to ubuntu. I have ubuntu and kubuntu on 2 different partitions but they share the same /home.

I didn't have putty installed on ubuntu so I installed it and tried to login to my server. It worked fine. I think that when I installed putty on kubuntu I didn't have the keys in the ~/.ssh folder so i uninstalled putty and reinstalled it again using synaptics. I also clicked on the complete removal option. With putty installed on kubuntu again I tried to login again but with the same result. It didn't work.

I don't think I removed everything when I uninstalled putty on kubuntu. What is the command to use for a complete removal in terminal. It is something with purge...(: If I do that and then reinstall putty once again with the keys in the ~/.ssh folder I think it would work...

---

### Post by buntolith on 2009-12-28
Ok so I'm trying > puttygen ~/.ssh/id_rsa -o rsa1.ppk but it is not enough. Any suggestions?

---

### Post by buntolith on 2009-12-29
Äsch. I didn't get it to work so I uninstalled PuTTY. I really don't need it anyway since I can use the terminal just as well. FileZilla is also working so I am happy. 

BTW. When I set up FileZilla it created a PuTTY key and I guess I could have used that one. But I won't...

---

