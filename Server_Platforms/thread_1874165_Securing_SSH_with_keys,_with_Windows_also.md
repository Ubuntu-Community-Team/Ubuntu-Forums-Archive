---
title: "Securing SSH with keys, with Windows also"
date: 2011-11-02
forum: Server Platforms
---

### Post by EPops on 2011-11-02
I am a complete noob to Ubuntu and Linux.

I recently installed Ubuntu Server 11.10 on a Dell Latitude D820, with 80GB hard drive, Core 2 Duo, and 2GB memory.

I am setting up OpenSSH on the server, and would like to be able to log in not only when I am on my home network, but also when I am away from home.

I want to use key authorization, and have generated public/private key pair on the server, but cannot figure out how to generate keys in Windows then send them to the server.  I am doing this for Windows only clients, while the only linux os is the server.

A couple of questions:
1.) Can I use any port number for SSH?

2.) In the /etc/ssh/sshd_config file, I see #AuthorizedKeysFile %h/.ssh/authorized_keys
Am I supposed to remove the # to allow key authentication?

3.) How do I generate keys on Windows and send them to the server?

If you could help, thanks.

---

### Post by papibe on 2011-11-02
> **EPops said:**
> I recently installed Ubuntu Server 11.10 on a Dell Latitude D820, with 80GB hard drive, Core 2 Duo, and 2GB memory.
Nice machine. Although, you may need to add more HD space depending on its use (I also started with 80GB, now its 1.5Tb).

> **EPops said:**
> I am setting up OpenSSH on the server, and would like to be able to log in not only when I am on my home network, but also when I am away from home.
There are several concepts you need to understand to do that. I always find that this [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video tutorial from the revision3 channel explains all basics concepts very well. It is on the Windows-side-of-things, but I think is a very good start.

> **EPops said:**
> 
1.) Can I use any port number for SSH?
Not exactly but yes, almost any. It has to be a port that not other applications is using. You can change that in the file /etc/ssh/sshd_config. The line to change is the one that says 'Port 22'

> **EPops said:**
> 
2.) In the /etc/ssh/sshd_config file, I see #AuthorizedKeysFile %h/.ssh/authorized_keys
Am I supposed to remove the # to allow key authentication?
It is not necessary.

> **EPops said:**
> 
3.) How do I generate keys on Windows and send them to the server?
There's a free Windows software called [Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/"). It is almost a complete suit of ssh for Windows. Here's a [video]("http://www.youtube.com/watch?v=ioGYnsxzL94") tutorial to create keys and connect to server using it.

I hope that helps,
Regards.

---

### Post by collisionystm on 2011-11-02
> **EPops said:**
> I am a complete noob to Ubuntu and Linux.

I recently installed Ubuntu Server 11.10 on a Dell Latitude D820, with 80GB hard drive, Core 2 Duo, and 2GB memory.

I am setting up OpenSSH on the server, and would like to be able to log in not only when I am on my home network, but also when I am away from home.

I want to use key authorization, and have generated public/private key pair on the server, but cannot figure out how to generate keys in Windows then send them to the server.  I am doing this for Windows only clients, while the only linux os is the server.

A couple of questions:
1.) Can I use any port number for SSH?

2.) In the /etc/ssh/sshd_config file, I see #AuthorizedKeysFile %h/.ssh/authorized_keys
Am I supposed to remove the # to allow key authentication?

3.) How do I generate keys on Windows and send them to the server?

If you could help, thanks.

[http://www.howtoforge.com/ssh_key_based_logins_putty](http://www.howtoforge.com/ssh_key_based_logins_putty)

---

### Post by EPops on 2011-11-03
Wow, this all helps a lot.  I vaguely remember using Putty to sign-in remotely to my college's Unix server from home, but have forgotten how to set it up so now I will refresh my knowledge.  Thank you for your response.

---

