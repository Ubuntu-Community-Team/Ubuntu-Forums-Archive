---
title: "How do i set networking between Ubuntu server and Kubuntu desktop?"
date: 2009-03-22
forum: Server Platforms
---

### Post by Grey08 on 2009-03-22
Hello

I have an Ubuntu server, and another kubuntu desktop, and the problem is, how do i save files into ubuntu server? In windows we open the folder in server's directory and save the files into it, so, is this can be done in Ubuntu server and Kubuntu desktop?

Regards,
Grey08

---

### Post by hyper_ch on 2009-03-22
depends what you want to do...

you can use:

- sshfs
- nfs
- samba
- ftp
- sftp

---

### Post by Grey08 on 2009-03-22
Thanks for your reply, hyper_ch, but is there any software comes with GUI? i mean, just like go to [network place], and it shows all the rest pc which are connected in same subnet, so i can click on particular pc and open the folder that have been shared to save a file into it.

Regards
Grey08

---

### Post by hyper_ch on 2009-03-22
well, first you need to know what you need/want and then you can think about its implementation.

Is it just linux/unix on the network or also Windows machines?

Do you want to have things permanently mounted or use a file transfer program like filezilla?

---

### Post by Grey08 on 2009-03-23
i m thinking to have linux and windows on the network, and, permanently mounted.
Because i think this way is much more faster to transfer files among the server/host and client/computer.

Regards
Grey08

---

### Post by hyper_ch on 2009-03-23
then you want to setup samba. There's an excellent howto in the tutorials section. I think it was created by St0rmbringer or something like that. I'm sure you can find it.

---

### Post by Iowan on 2009-03-23
> **hyper_ch said:**
> then you want to setup samba. There's an excellent howto in the tutorials section. I think it was created by St0rmbringer or something like that. I'm sure you can find it.That'd be [this]("http://ubuntuforums.org/showthread.php?t=202605") one.  
[Another]("http://ubuntuforums.org/showthread.php?t=288534") one you should see.

---

### Post by Grey08 on 2009-03-26
I have solved it with FTP client. At least it is a GUI client and let my family members "see" where and how to upload/download files.

---

