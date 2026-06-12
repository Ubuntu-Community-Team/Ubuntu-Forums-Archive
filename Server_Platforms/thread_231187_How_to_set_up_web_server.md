---
title: "How to set up web server???"
date: 2006-08-07
forum: Server Platforms
---

### Post by zoon_unit on 2006-08-07
I've successfully installed a Ubuntu Server LAMP system, and everything is working.  I can access my development server through my local network, and read web pages from windows.

Here's my problem:  I'm using Dreamweaver for web development on my XP system, but when I go to log in to the Ubuntu server, it asks for a login and password.  I've tried typing in my primary user name and root password from my linux server, to no avail.

I'm sure I need to set up an external user and password, but how to do it??  How do I configure my Apache server to allow logging in from a remote system such as Dreamweaver??  (I want to emulate the conditions that my hosting service will provide)

Thanks in advance.  As you can tell, I'm a total Linux newbie.  :-)

---

### Post by zoon_unit on 2006-08-07
Just wanted to bring this back up in the queue.

How does one set up an "account" like shared ISP servers on my Ubuntu server so that I can log in using dreamweaver/frontpage??

---

### Post by stormblue on 2006-08-07
Typically you do this is FTP.  Do you have an FTP server running?

---

### Post by zoon_unit on 2006-08-07
Not yet, but Dreamweaver allows access to local network servers without FTP.  However, even though I've got Samba installed, I can't access my Linux development server from Windows.  However I CAN access my Windows shared folders from Linux!

When I try to log into my Linux server from Windows, it asks for a login and password.  I type in my admin login and password, but it doesn't work.

However, I can access Windows files from Linux painlessly.  I guess this problem is the first one I should solve.  :-)

Any ideas??

---

### Post by stormblue on 2006-08-07
Is it WebDAV that you're trying to set up?

---

### Post by chrisfay on 2006-08-07
I was unaware that Dreamweaver supports samba file sharing for transfers. Just set up a simple ftp server and close it off to your externel network; if you're only using it to transfer web files to a development machine. That's how I have it setup and it works perfect...

---

### Post by Tortanick on 2006-08-07
I'd use apt-get install openSSH

Then get PSCP from [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/) install on windows and use that to transfure files over (it will be windows to Linux only though) 

Also make sure that port 22 cannot be accessed on your server from the internet. Otherwise you'll get password cracking atempts.

---

### Post by Endwin on 2006-08-07
If you want to transfer files to your linux box from windows with OpenSSH I would use WinSCP in windows. It works very well. Nice drag and drop interface.

[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

Make sure you have openssh server installed. 

sudo apt-get openssh-server in the terminal or look for openssh-server in the package manager.

---

### Post by zoon_unit on 2006-08-07
Actually, my original intent was to simulate the exact conditions I would encounter when transferring my CMS files to my ISP.  I wanted to set up an "account" on my local server to emulate that setup.

I haven't succeeded in that yet, BUT I have discovered that Dreamweaver works just fine over a Samba connection!

I finally managed to get Samba to work properly from XP to Linux.  (it always worked from Linux to XP, go figure)  Now I have a direct connection to my server files from Dreamweaver.  Cool!

---

