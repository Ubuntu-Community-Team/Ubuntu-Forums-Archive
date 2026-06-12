---
title: "Creating guest account SSH"
date: 2009-05-20
forum: Server Platforms
---

### Post by tomster2300 on 2009-05-20
Hello, 

I have setup the OpenSSH client and server on my Ubuntu 9.04 desktop so I can run a simple file server off of it.  I setup a non-password keypair between it and my Macbook, but I would also like to create a passworded guest account that would allow others to login and drop / take files.  I am doing some freelance website work this summer and need a place where clients can securely send me their content.  

Problem is, I don't really know how to do this.  My guess is - 

1)  Create a guest account in linux
2)  Edit the sshd_config file to allow password authentication 
3)  The Guest would log into their own home/usr folder - in there I would create a "drop-box" that would have a symbolic link back to a folder on my admin account.   The drop-box would have permissions set to only drop items into but not open.  

I'm not sure where to go from here.  How do I make the guest account not have root access, and how do I keep them from going anywhere but their own home folder?

Thanks!

---

### Post by sickdude on 2009-05-21
Why is it that you want to use ssh for a fileserver? Is it because of security reasons? If so why do you want to do this without a password? Thats not very secure...

Anyway you have to exchange key's, this is kinda transparent for a user. You dont have to type in a password when you want to login.

little tut is over here:

[http://www.petefreitag.com/item/532.cfm](http://www.petefreitag.com/item/532.cfm)

If you want to read a bit more check out this website:

[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

---

### Post by cdenley on 2009-05-21
> **tomster2300 said:**
> Hello, 

I have setup the OpenSSH client and server on my Ubuntu 9.04 desktop so I can run a simple file server off of it.  I setup a non-password keypair between it and my Macbook, but I would also like to create a passworded guest account that would allow others to login and drop / take files.  I am doing some freelance website work this summer and need a place where clients can securely send me their content.  

Problem is, I don't really know how to do this.  My guess is - 

1)  Create a guest account in linux
2)  Edit the sshd_config file to allow password authentication 
3)  The Guest would log into their own home/usr folder - in there I would create a "drop-box" that would have a symbolic link back to a folder on my admin account.   The drop-box would have permissions set to only drop items into but not open.  

I'm not sure where to go from here.  How do I make the guest account not have root access, and how do I keep them from going anywhere but their own home folder?

Thanks!

Ordinary users won't have root permission when they login, and can't do anything too malicious. I would suggest using a restricted shell such as scponly just to be safe, though. Restricting users to specific directories would require a chroot, which makes things much more difficult.
[http://ubuntuforums.org/showthread.php?p=7271431#post7271431](http://ubuntuforums.org/showthread.php?p=7271431#post7271431)

An alternative you might want to consider is using FTP with SSL encryption.

---

### Post by tomster2300 on 2009-05-22
> **sickdude said:**
> Why is it that you want to use ssh for a fileserver? Is it because of security reasons? If so why do you want to do this without a password? Thats not very secure...

Anyway you have to exchange key's, this is kinda transparent for a user. You dont have to type in a password when you want to login.

little tut is over here:

[http://www.petefreitag.com/item/532.cfm](http://www.petefreitag.com/item/532.cfm)

If you want to read a bit more check out this website:

[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

No, I have already created a keypair login for myself, and I want to create a guest account that DOES require a password...

Thanks to all for the info.  I think using ftp might be the smartest way to do this.

---

### Post by mellowd on 2009-05-22
To add a user simply type: useradd username

They will not be administrator, and will only have full access to files in /tmp and /home/username

They will however have read access to a bunch of files, you can tie this down though.


But yes, if you just want people to upload and download files you want to use ftp

---

