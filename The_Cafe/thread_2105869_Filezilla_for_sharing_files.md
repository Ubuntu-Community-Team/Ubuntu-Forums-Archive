---
title: "Filezilla for sharing files"
date: 2013-01-17
forum: The Cafe
---

### Post by rmcellig on 2013-01-17
I am trying to share files between two computers in my house using Filezilla. Here is the error I am getting:

Status:	Connecting to 192.168.2.19:21...
Status:	Connection attempt failed with "ECONNREFUSED - Connection refused by server".
Error:	Could not connect to server
Status:	Waiting to retry...

What do I need to do to get this working? Both computers have Linux installed. What do I need to set up?

---

### Post by Petro Dawg on 2013-01-17
I just use Ubuntu1 to share files between my Ubuntu and Win7 partitions  as well as various computers (in my home and across the country) as well  as my phone.  

Its rather easy to set up and works well.

Others prefer DropBox, either is fine for simply sharing files between computers.

I think to set up a proper network across your computers you may need to use Samba or NFS.  But I never felt the need to use either of them.

---

### Post by 2F4U on 2013-01-17
Since FileZilla is a FTP/SFTP client, do you have a server running at the computer you are trying to connect to?

---

### Post by rmcellig on 2013-01-17
No I don't. I don't think Filezilla is available as a Server app for linux.

---

### Post by CharlesA on 2013-01-17
You can use Filezilla to connect to the ftp subsystem of a machine running openssh-server.

What sort of files are you wanting to share?

---

### Post by rmcellig on 2013-01-17
Actually I am digitizing my record collection so I record them to an old Dell 3000 which is connected to my sound system. Ten, I would like to be able to access them from my old HP laptop for further editing etc...

---

### Post by CharlesA on 2013-01-17
Just use [NFS]("https://help.ubuntu.com/12.04/serverguide/network-file-system.html") or Samba if you feel like it.

Now that I think about it, you could also use sshfs if you really wanted to.

---

### Post by rmcellig on 2013-01-17
Thanks! I will give Samba another shot. I just wanted to know how to set up FTP as a second alternative in case things went wrong with Samba. So you are saying that as long as I install an FTP server on one of my machines, I can use the Filezilla client to connect to it? If so, I will search for an FTP server with a GUI, if there is such a thing. :)

---

### Post by CharlesA on 2013-01-17
> **rmcellig said:**
> Thanks! I will give Samba another shot. I just wanted to know how to set up FTP as a second alternative in case things went wrong with Samba. So you are saying that as long as I install an FTP server on one of my machines, I can use the Filezilla client to connect to it? If so, I will search for an FTP server with a GUI, if there is such a thing. :)

Yes.

As for Samba, I [wrote something up]("http://charlesa.net/tutorials/debian/debiansamba.php").

---

### Post by rmcellig on 2013-01-17
Thanks!! Appreciate it!

---

### Post by rmcellig on 2013-01-17
You mentioned in the document that there are easier and better ways to share files if using Linux or OSX. I have an iMac and two laptops running Linux. What methods are there that are easier than Samba? FTP or is there something else? My line PC running XP Pro is my wife's. I would use Samba to share with her but now I am interested in the other methods.

Thanks!!

---

### Post by CharlesA on 2013-01-17
NFS is supposed to be easier to set up than Samba and it should work with OSX, not sure about WinXP though.

I haven't used NFS as I've got Samba running just fine, so I do not know how easy/difficult it is to get running. Most of the documentation I have seen for it mentions storing a machine's home directory on a server instead of locally.

---

