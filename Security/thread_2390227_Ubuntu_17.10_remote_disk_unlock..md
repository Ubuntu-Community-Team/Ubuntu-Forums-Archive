---
title: "Ubuntu 17.10 remote disk unlock."
date: 2018-04-26
forum: Security
---

### Post by goldenstrike on 2018-04-26
Hey guys!

I have a question about setting up remote unlock with Ubuntu's built-in disk encryption. 

I know there are ways to do it with dropbear but I'm not sure. 

So here is what I am wanting to do. 

Our company manages a number of large crypto currency mines across the US and Canada. We have a specialized mining software that is installed on a server that is placed within the facility. 

Now because the software is written in python, we needed a way to allow the client to be able to monitor there mine, but not get our code. 

We this was done by giving the client a black box with full encryption, we are the only ones that know the keys. But here is the issue. 

If the system reboots, someone currently has to manually enter in the key. We cant have a tech come every time the system gets rebooted either as only management has access to the disk encryption keys on the servers.  

What we need done is when the system reboots, it sshs into the keyserver (IP restrictions will be set to only accept incoming connections from certain IP addresses) retrieves the key file that will unlock the drive, unlock the drive, then delete the key file from the facility server.  

I know you can do this with dropbear, but every example I have seen you need to issue an ssh command TO the encrypted client from the keyserver. We want it the opposite, so the client requests the key file from the keyserver. 

If anyone knows a good tutorial on how to do this, or if someone could point me in the right direction, it would help me and the team quite a bit. 

Thanks!

~Kevin

---

### Post by goldenstrike on 2018-04-30
Anyone?

---

