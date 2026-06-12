---
title: "FTP Server Setup"
date: 2008-08-25
forum: Server Platforms
---

### Post by gjr5017 on 2008-08-25
How can I set up an FTP server in Ubuntu? I want to be able to share my documents folder so I can access it at work if I forget some documents which happens often.

---

### Post by mssever on 2008-08-26
I prefer not to use FTP because it's insecure. I'd rather use SSH/SCP (or maybe SFTP). To install an SSH server: ```
sudo aptitude install openssh-server
```You can then ssh into your machine, or use scp to copy files. If you must use Windows to access your box, PuTTY is the best Windows SSH client that I know of.

---

### Post by gjr5017 on 2008-08-26
I got vsftpd installed but I'm not sure how to access it at all and how to change the directory that it shares on the FTP server...

On note of SSH, I need it to be accessed by Windows (thats what my office uses). Whats the difference between SSH and FTP? Is one easier to use than others? I might need to be able to share some files with friends as well and if they need special software or anything on their computer or if I need special software on my work computer to access the SSH then it's not going to work. FTP would be easy because all you need is a web browser.

---

### Post by mssever on 2008-08-26
> **gjr5017 said:**
> I got vsftpd installed but I'm not sure how to access it at all and how to change the directory that it shares on the FTP server...

On note of SSH, I need it to be accessed by Windows (thats what my office uses). Whats the difference between SSH and FTP? Is one easier to use than others? I might need to be able to share some files with friends as well and if they need special software or anything on their computer or if I need special software on my work computer to access the SSH then it's not going to work. FTP would be easy because all you need is a web browser.See these links:

[LIST=1]
[*][http://en.wikipedia.org/wiki/Ssh](http://en.wikipedia.org/wiki/Ssh)
[*][http://en.wikipedia.org/wiki/Ftp](http://en.wikipedia.org/wiki/Ftp)
[/LIST]
FTP is easier to use, if you don't mind the fact that anyone who wants to can read all traffic, including your password. Because of ftp's security issues, I refuse to use it, nor do I know how to configure vsftpd (though most programs keep their configuration in /etc or in dotfiles in your home directory). However, SSH can be a complete replacement for FTP.

---

### Post by gjr5017 on 2008-08-26
Okay. That makes a little more sense now. What would you say would be the best way to set up SSH or even SFTP so that I could set my documents folder to be shared on the SSH/SFTP server (whichever I set up) so that a windows machine could access it with a normal web browser - preferrably an easy way to go about this as I am still learning the ins and outs of Linux (just switched a month or so ago from windows).

Also, how would I go about accessing the server outside of my house be it at a friends house or at work.

I'd also like to thank you for your help so far :)

---

### Post by Seti on 2008-08-26
I have to agree that if you're going to be accessing home stuff from work, you're best off using ssh; you traffic is encrypted so you don't have to worry about the goons in IT (assuming they are THAT competent) getting your ftp user password. Ssh is always one of the first packages I install when I set up a Ubuntu box.
```
sudo apt-get install ssh
```
Apt will know what to do. Just type your password.
The next thing you will have to do is forward the port on your router's firewall settings (assuming you're behind a router).
By default ssh works on port 22, but its always a good idea to change that to another port, otherwise you're going to be constantly slammed by brute-force dictionary attacks on your ssh server. Edit your /etc/ssh/sshd.config file accordingly. I always include a line:

```
AllowUsers 'user'
```
where 'user' is your username. Don't include the ''s!
If you have a dynamic IP address with your ISP, look into setting up a dynamicDNS account with dyndns.org, so that your server is always available online; its a pain in the *** to memorize your IP address IMHO.
Finally, A good Windows client for ssh is putty. To use file-transfers over ssh, use scp. Winscp is a good program for this.
Good luck!

---

### Post by gjr5017 on 2008-08-26
Is there a way to access SSH without a client? I would much rather be able to use a web broswer than to install a program wherever I need to access my computer...sorry if my questions seem dumb as I am new to the subject and this is the first time I've set something up along these lines and thanks for your patience. It is greatly appreciated :)

Also, is the AllowUsers 'user' the username of the person accessing the SSH or the account on my computer that I want to allow access to?

---

### Post by mssever on 2008-08-26
> **gjr5017 said:**
> Is there a way to access SSH without a client?I just typed in sftp://my-ssh-server in Firefox and it worked. I don't know if that works all the time, though. I've never messed with SFTP. Installing WinSCP is easy enough for me. So, in short, I don't know if there's a way in Windoes to access SSH without a client.

> Also, is the AllowUsers 'user' the username of the person accessing the SSH or the account on my computer that I want to allow access to?
Those two are the same thing. If you want to be able to allow others to access your machine via SSH, you should create an account for that purpose (or multiple accounts) and only allow that account access to what it needs to access.

---

### Post by gjr5017 on 2008-08-26
So how do I pick which users have access to which files/folders?
What do I type in firefox's URL Bar to be able to access the SSH client or will it allow me to pick what goes there?

---

### Post by mssever on 2008-08-26
> **gjr5017 said:**
> So how do I pick which users have access to which files/folders?By setting the files' permissions, just like you'd do in a multi-user system. Google "unix permissions" for details.
> What do I type in firefox's URL Bar to be able to access the SSH client or will it allow me to pick what goes there?I typed in ```
sftp://username@scott-desktop.mss
```where scott-desktop.mss is the domain name of my server. I don't know if that works in Windows or not.

---

### Post by gjr5017 on 2008-08-26
I think I'm just going to go with FTP.
I installed proftpd and gproftpd so that I have a gui to work with. I can get to the ftp site but it doesn't ask me for a password or anything (i have it set so that it requires a password...i think haha) but it doesnt show any of the folders that i have set up to be shown for each user so maybe its just because I'm on the same IP as the server.

---

### Post by y@w on 2008-08-26
I'd recommend using something like [Webmin]("http://webmin.com") to manage your FTP sites and users. It gives a nice web management front-end for a lot of things, but proftpd is one of them.

---

### Post by y@w on 2008-08-26
I'd also like to point out that SSH is not necessarily an alternative to FTP.. It allows file transfer very easily, yes, but it also opens your system up for users to have shell access. If you don't have a lot of time to tweak and are concerned about permissions, shell access is a dangerous thing to give out. Both have their pros and cons, but it sounds like FTP is a better fit for you.

---

### Post by gjr5017 on 2008-08-26
I installed webmin but I have no idea how to open it or access it to change my settings and all that jazz.

Scratch that...I just figured that out but I'm not sure how to go about setting up an FTP server in this...there is nothing under server that has FTP. theres just windows samba file sharing, ssh, and read user mail.

Scratch that one too....refreshed the modules and got the proftpd server on the side, not sure how to go about setting this up though. Help would be greatly appreciated.

---

### Post by gjr5017 on 2008-08-27
I'm not really sure how to go about setting it up like what settings I need, if I need to create users on my actual laptop and not just on the server side and all that stuff.

---

### Post by gjr5017 on 2008-08-27
Anyone at all? Please.

---

### Post by mssever on 2008-08-27
You haven't really asked a question. If you want to know how to configure your server, a good place to start is by reading the server's documentation. If you still don't understand things, then you can ask a specific question.

Specifically, I don't understand what you're saying about creating users on your laptop vs. on your server. Of course, I know as much about configuring an FTP server as you do, since I have no use for FTP.

---

### Post by lswb on 2008-08-27
If you have installed vsftpd, take a look at the file /etc/vsftpd.conf. It is the configuration file for vsftpd and is fairly well decumented. For more detail read the man pages for vsftpd and vfstpd.conf. (type the command "man vsftpd" and 
"man vsftpd.conf" in a terminal) The conf. file comments and man pages will explain how to configure it for your purposes. Sometimes the documention can be difficult to get through, if you still have questions after checking the documentation post again.

Oh, one thing not mentioned in the man pages, when installing vsftpd in ubuntu, it will add an item to your Main Menu/System/Admin/Services menu for an FTP server. By default this is enabled when vsftpd is installed but if you want to disable it while leaving vsftpd installed, this is a handy way to do so.

---

