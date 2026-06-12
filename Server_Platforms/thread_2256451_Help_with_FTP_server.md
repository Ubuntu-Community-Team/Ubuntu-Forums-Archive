---
title: "Help with FTP server?"
date: 2014-12-12
forum: Server Platforms
---

### Post by jestin2 on 2014-12-12
Hello people, first: Sorry for my bad English, I'm Dutch.

But I have a question:
I have installed 'vsftpd' on my Ubuntu Dekstop(I use it as a Server :p ), and I have a question.

How do I setup the config, I want that only people that I say can login to the ftp en 'Anonymous' not, and every user that login,comes to the folder /serverfiles (I have already made it,the folder)

Can someone give me some staps, or a completly config? I searched already to tutorials, but I can't find a good tutorial.



-Thanks

---

### Post by Lars Noodén on 2014-12-13
Welcome.  

Are you sure you want [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) at all?  Anonymous FTP is one of the few remaining use cases for it and even then [deployment of FTP is a little irresponsible](https://www.marc.info/?l=openbsd-misc&m=139579420802409&w=2)  ;)

If you are just wanting to transfer files, but safely, over the Internet my first recommendation would be to install openssh-server and use SFTP instead, since it is secure and now supported by pretty much all clients.  Those clients include the file managers.  For example, go to [Nautilus and press ctrl-L](https://www.youtube.com/watch?v=9S4DV1PluzA) then enter the URI for your server account, something like this: *sftp://jestin2@server.example.org/home/jestin2/Documents/some/long/path/*.  That will give you graphical control over your remote documents just like they were local.

But if you do need FTP itself, say how it will be used and that will guide what kind of settings you need in the configuration file.

---

### Post by TheFu on 2014-12-14
sftp is much better for 99.99999% of the use-cases.
Plain FTP should have died out around 1995.

---

### Post by kevdog on 2014-12-15
Just chiming in here.  SSH server is technically much more secure, however you'd need to configure ssh a little bit differently.  From my understanding, this type of server isnt good for annoymous file transfer.  If you'd want to use the credentials as guest:guest for example as the username and password, you're going to have to set up an account for this. I'd also recommend using no interactive shell, and even possibly putting this type of setup in a jail using the openssh method or jailkit.  Yes this is a lot more work than a straightforward ftp server

---

