---
title: "First time Ubuntu server user"
date: 2012-03-06
forum: Server Platforms
---

### Post by chrismamo1 on 2012-03-06
I recently installed Ubuntu server 11.10 on my old Dell box for the purpose of running a simple database server for my FTC Robotics team. This is my first time running my own server, so I was kind of hoping that it could be a learning experience, but I immediately hit several problems:
1.) I have been having some trouble using the terminal interface. I've gradually been getting used to it, but I still feel like I could be getting more out of it, at least in the short term, if I installed some sort of GUI on it.
2.) I have been unable to connect to the internet at all, neither wirelessly nor through eth0 (which I was able to do on my old 11.04 desktop installation on the same box). I have found that I might be able to fix this by adding the line "auto eth0" to "/etc/network/interfaces", but have not yet had a chance to try this. These connectivity issues have in turn led to several other problems, such as not being able to install software packages, especially the aforementioned GUI, which leads me to my third issue
3.) How could I install packages stored on compact disks using apt-get? Also, how could I get packages in an installable state onto such a disk?

I apologize in advance for any overly amateurish questions, and I hope that you will be able to answer some of my questions.

Thanks,

Chris

---

### Post by papibe on 2012-03-07
Hi chrismamo1.

Could you post the content of the file /etc/network/interfaces ?

Also could you post the result of this command?
```
ifconfig
```
Regards.

---

### Post by gordintoronto on 2012-03-07
If you need every bit of available performance, Ubuntu Server is a good choice. If performance is not an issue, you might as well use Ubuntu Desktop and install the database server on it.

---

### Post by Habitual on 2012-03-07
> **gordintoronto said:**
> If you need every bit of available performance, Ubuntu Server is a good choice. If performance is not an issue, you might as well use Ubuntu Desktop and install the database server on it.

+1. a server install is a bit of over-kill for a mysql db but is an excellent learning experience.

---

### Post by chrismamo1 on 2012-03-08
I managed to fix my connectivity issues, and as of tonight I managed to get php and html file serving working. I got my ethernet connection running by adding the lines:

```
auto eth0
eth0 inet dhcp
```

To my /etc/network/interfaces file
(Note: I think I might have left out some of the code on the second line, but it works on the server.)

I have also grown highly accustomed to the command line interface, even figuring out how to use the VI editor in the terminal. Thank you for all of your help.

---

### Post by darkod on 2012-03-09
Just a note, that depending what you selected during the install, the network should have been configured with DHCP or static IP.

For a server, you might wanna consider having a static IP rather than DHCP.

For editors, take a look at nano too, I find it easier than vi/vim.

---

