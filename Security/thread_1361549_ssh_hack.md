---
title: "ssh hack?"
date: 2009-12-22
forum: Security
---

### Post by shade5 on 2009-12-22
Hi,
actually I am pretty sure that it would not work, but actually I just want to know why..

If we connect to a sshd and the account does not provide mkdir for example but we still got write right, would it then be possible to modify the ssh client that it can create directories alone?

Thanks!

---

### Post by BkkBonanza on 2009-12-22
I don't think there's a need to modify the ssh client. You can just use some other method to create directories like rsync or sftp. Probably others too. I haven't read the source but I'm fairly sure that they create directories by a system call rather than calling the mkdir program. They wouldn't bypass any permissions though. And of course with ssh you could always copy a new binary of mkdir over and use that, assuming you have write permissions somewhere at all.

---

### Post by shade5 on 2009-12-22
System call.. I see. I am looking forward to learn Linux programming.

So would it be possible to modify ssh to do these system calls?

The reason why I ask: I want to give write access but only for programs I choose. Now I fear that other programs can be used to still create files I do not want.

---

### Post by lavinog on 2009-12-22
> **shade5 said:**
> System call.. I see. I am looking forward to learn Linux programming.

So would it be possible to modify ssh to do these system calls?

The reason why I ask: I want to give write access but only for programs I choose. Now I fear that other programs can be used to still create files I do not want.

you could create a user with write access to whatever folders, and run those programs with that user.

---

### Post by shade5 on 2009-12-22
Good, that is what I also planned to do. If that would work flawless I feel very redeemed. 

But I still suppose that you can modify your ssh client to do system calls until a programmer told me that it is not possible.

---

### Post by BkkBonanza on 2009-12-22
Well, you can modify ssh or create a new program that can use system calls but as mentioned above system calls (which are a normal part of any program) cannot bypass file permissions. So as long as you make sure your permissions are correct then you'll be fine. That's the whole purpose of the permissions system - to secure files and who can do what. Programs always run as a certain user so which user and what permissions they have determines what they are able to do.

---

