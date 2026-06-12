---
title: "server all of a sudden doesn't allow remote logins"
date: 2012-09-19
forum: Server Platforms
---

### Post by kkoffler on 2012-09-19
I'm having a small problem logging onto my outside dns server using ssh.  All of a sudden it  will not allow remote logins, I can login from my local network just  fine, but the box will just say "Access Denied" when I try to login from  across the internet, nothings changed on the box.

I checked and port 22 is open...I checked and ssh is installed.

Any help on this would be greatly appreciated....Just a side note, this is my second week working on ubuntu so if ask a stupid question please be kind :D

---

### Post by darkod on 2012-09-19
Copied from the other thread. Did you try to use telnet over the internet and see if it detects the service listening on that port?

                                  **Re: OpenSSH server all of a sudden doesnt allow remote logins wtf**             
                                                                     Quote:
                                                                      Originally Posted by **kkoffler**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12248063#post12248063")                 
                 *Ok I will open a new request as you asked....yes I verified that ssh was installed and port 22 is open.*
                                 
That's not the same. The service running on the server has nothing  to do with testing with telnet if you can see it from another location.  We can continue the discussion in the new thread.

On linux, the telnet test would be something like:
telnet <server ip> 22

It should say something like Listening...

PS. Does it ask you for a login and refuses it, or doesn't even get that far?

---

### Post by kkoffler on 2012-09-19
Yes I received a good response on the telnet

I'm able to get the login but when I enter in the password I receive the Access denied error.

---

### Post by steeldriver on 2012-09-19
any interesting sshd messages in the server's /var/log/auth.log ?

---

### Post by kkoffler on 2012-09-19
SSHD [2546] Bad Protocol Version Identification clear

---

### Post by steeldriver on 2012-09-19
> **kkoffler said:**
> SSHD [2546] Bad Protocol Version Identification clear

that's probably just a result of trying to telnet to an sshd port, I think

---

### Post by kkoffler on 2012-09-19
How can I read the SSH_config and SSHD_config file without making changes to the files?  I found gedit which isn't installed I tried nano but it looks like it's creating a new file.

---

### Post by darkod on 2012-09-19
nano will read, just use sudo nano <filename> for opening system files and also make sure you have the path and filename right, otherwise it will consider it new empty file if the path/file doesn't exist (not correct).

---

### Post by kkoffler on 2012-09-20
how do you open a linked file or a cat file?  I tried to google it but can't find the right command.

---

### Post by kkoffler on 2012-09-20
I figured it out how to open a CAT file

---

### Post by Lars Noodén on 2012-09-20
If you just want to browse a text file read-only, then [less](http://manpages.ubuntu.com/manpages/precise/en/man1/less.1.html) is a good option.

```

less /etc/ssh/sshd_config

```

---

### Post by kkoffler on 2012-09-20
Ok here is the latest...we copied a good sshd_config file to the problem server.  For a short time I was able to log onto this server using ssh.  I walked away for a couple of minutes now when I try logging in I receive access is denied again.  Any help on this would be greatly appreciated!

---

### Post by kkoffler on 2012-09-20
thank you Lars Nooden

---

