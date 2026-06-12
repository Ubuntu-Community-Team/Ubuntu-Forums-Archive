---
title: "VSFTPD Lesson"
date: 2009-12-17
forum: Server Platforms
---

### Post by Canha on 2009-12-17
Hello. I can't seem to solve this:
I want my vsftpd server to allow me to upload stuff with the chroot() username i have. Fresh copy of ubuntu server 9.10, just me and my server. I can access it and check files but I can't upload. Please give me a lesson on how to manage users :\

---

### Post by oneloveamaru on 2009-12-17
"chroot username"??? chroot stands for change root and has to do with root of the file system. It's mainly used for security

If you are logging in as a non-privileged user, which you should be, you need to upload everyting to your home directory, as that's the ONLY directory you will have full permissions on. 

If you try to upload anywhere else, it will fail. Once it's uploaded, move it with sudo commands. That is your best bet. 

The last resort is to enable root by giving it a password and then logging in as root, then you can drop your files anywhere you want.

---

### Post by Canha on 2009-12-17
> **oneloveamaru said:**
> "chroot username"??? chroot stands for change root and has to do with root of the file system. It's mainly used for security

If you are logging in as a non-privileged user, which you should be, you need to upload everyting to your home directory, as that's the ONLY directory you will have full permissions on. 

If you try to upload anywhere else, it will fail. Once it's uploaded, move it with sudo commands. That is your best bet. 

The last resort is to enable root by giving it a password and then logging in as root, then you can drop your files anywhere you want.

Well I read something about using usernames from chroot, anyway I enabled local users to access FTP but still gives me error 550 Permission denied. while uploading through my FireFTP on Firefox.

---

### Post by oneloveamaru on 2009-12-17
You can use any SFTP client to access a server running SSH, you honestly don't even need VSFTPD if you are allowing just local users anyways. Unless you really only want to use FTP and not SFTP.

A 550 error means you don't have permissions to write, wherever it is you are trying to upload to.

Find out where you are trying to upload to, log in to the server and give yourself write permissions in that directory.

---

### Post by Canha on 2009-12-17
> **oneloveamaru said:**
> You can use any SFTP client to access a server running SSH, you honestly don't even need VSFTPD if you are allowing just local users anyways. Unless you really only want to use FTP and not SFTP.

A 550 error means you don't have permissions to write, wherever it is you are trying to upload to.

Find out where you are trying to upload to, log in to the server and give yourself write permissions in that directory.

Forgot to mention I'm uploading to home directory, I made it so that local users can only see their home folder. I really wanna use FTP yeh :p

How do I give write permissions, I'm new to this :P

Thanks

---

### Post by oneloveamaru on 2009-12-17
If it's your home directory, then you have write permissions.

Does VSFTPD have its own read/write permissions in the conf file? You may want to check that, I know FileZilla does.

---

### Post by Canha on 2009-12-17
Found the problem, write_enable variable was commented, and the default is no. Thanks for the clarifications though :)

---

