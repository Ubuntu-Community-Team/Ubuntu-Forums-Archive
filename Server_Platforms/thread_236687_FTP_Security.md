---
title: "FTP Security"
date: 2006-08-15
forum: Server Platforms
---

### Post by Slychilde on 2006-08-15
Doing a little research on the forums, I have noticed that many people recommend not setting up an FTP server, as it is a security issue.  What exactly are the security issues with FTP, can it be set up at all so it's locked up tight?  Is there one FTP server program that is more secure than another?

I also noticed many people recommended SSH for file transfers instead of FTP.  I have Putty for my Windows laptop, but all I know how to do is remotely log into an open-ssh server and get the commandline.  1.)Is an SSH server more secure. 2.)How does that work if you have other family members that would like to access it? 3.)How do  you transfer files through both linux and winblows with SSH and is it hard?

Thank you for the enlightenment, I really do appreciate it. :)

Oh....P.S. (I guess)  is there any way that I can test how secure my box is?

---

### Post by lamego on 2006-08-15
> Doing a little research on the forums, I have noticed that many people recommend not setting up an FTP server, as it is a security issue. 
It is a security issue on the sense that unsing FTP the user and password and the files are sent over the next in plain text, meaning that anyone on the connection path could debug the network and look your user/password during connection attempts.
> What exactly are the security issues with FTP, can it be set up at all so it's locked up tight? Is there one FTP server program that is more secure than another?
Any internet service had its security issues, some versions are considered more secure because they had less exploits or just because they use some type of options as default, the more secure version is the one you understand better.

With SSH the login information and the file contents are sent encrypted so it does not pose the problem described above.
You can browse a server using ssh/sftp just as you do with ftp using an SSH capable client.
On windows you can use FileZilla or WinScp, both support ssh. On Linux you can use Nautilus.

---

### Post by Slychilde on 2006-08-18
Thanks for the help, lamego!

> It is a security issue on the sense that unsing FTP the user and password and the files are sent over the next in plain text, meaning that anyone on the connection path could debug the network and look your user/password during connection attempts.

Wow, I didn't know that...yikes.  That is not something I particularly want, but to understand this better, how do people even get in the way of the connection path, especially if I change the default ftp port to a different one?  I've also made the ftp accts shell set to /bin/false, and locked them in their default dir.  Is there anything else that can be done to make it more secure?

I think I'll just switch to SSH for now, but understanding the ftp thing is still nice/helpful - thank you for showing me that.

---

### Post by lamego on 2006-08-18
> Wow, I didn't know that...yikes. That is not something I particularly want, but to understand this better, how do people even get in the way of the connection path, especially if I change the default ftp port to a different one? I've also made the ftp accts shell set to /bin/false, and locked them in their default dir. Is there anything else that can be done to make it more secure?
They can get into the connection path if they have administrator privilege on a computer/device which routes your ftp connection.
They can get your login info no matter the port beeing used by using a traffic analyzer for all the net traffic, wthey can easly search for "login:" and "password", it is enough to catch the ftp info.
Your security measures are ok, you could try to setup a chrooted ftp, chroot is a system limitation scheme that can be used with any kind of service, but you do have some experience to set it up, at least for services which don't support it out-of-the-box :)

---

