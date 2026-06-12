---
title: "Made a file server, now how do I make it accessable from the internet?"
date: 2008-02-23
forum: Server Platforms
---

### Post by adamprawitz on 2008-02-23
I am fairly new to Ubuntu.  I just set up a simple home file server using [this]("http://www.howtoforge.com/perfect_server_ubuntu7.10") tutorial.  The server works great, while I'm connected to my LAN, (wired or wireless).  But it doesn't work over the internet.  How do I set that up?

My server is an old Pentium III Gateway with Gutsy Gibbon Server running on it.

---

### Post by .nedberg on 2008-02-23
Just skimmed through the how-to. I assume you are behind a router with a firewall. You need to open up the ports you use and direct them to you server.

Have a look at [http://portforward.com/]("http://portforward.com/") to see how to open up ports with your router. And set a static IP if you didn't already!

What ports you need to open depends on what services you run.

---

### Post by adamprawitz on 2008-02-23
Thank you for your help.  I knew it was simple but I just didn't know how to do it.  

I changed the settings but I don't know how to test it without going somewhere to use the internet outside of my LAN.  Is there a way to do that?

Otherwise, I will check it later today from somewhere other than home.

---

### Post by .nedberg on 2008-02-23
I don't really know of any other way than change to another LAN. But if you have a webserver running you could try a web proxy like hidemyass.com.

Else you could get someone else to try to connect to your computer.

---

### Post by adamprawitz on 2008-02-23
Ok, I had someone check my server from the internet for me.  It did not work.  I told them to try and connect to [ftp://192.168.1.x](ftp://192.168.1.x) and they could not.  Is this the proper way to test it?  

I attached a screen shot of my router configuration.  Is that how it should look?  With the final boxes filled in with the rest of my static ip of course.

---

### Post by .nedberg on 2008-02-23
No, that is not the way. But you are getting there!

Your friend needs to connect to you external IP.

You can find your external IP [here]("http://www.nedberg.net/ip.php").

You probably want to set up a no-ip.com account and use the 'no-ip' client to update if your external IP changes.

---

### Post by adamprawitz on 2008-02-23
But do I have the port forwarding setup correctly?

I was able to the [http://[external](http://[external) ip] but when I try the ftp:// it prompts me for user name and password, like usual, but then it just hangs?

edit:  I can also ssh to the server with the external ip.

---

### Post by faulkes on 2008-02-23
> **adamprawitz said:**
> But do I have the port forwarding setup correctly?

I was able to the [http://[external](http://[external) ip] but when I try the ftp:// it prompts me for user name and password, like usual, but then it just hangs?

edit:  I can also ssh to the server with the external ip.

The issue you are seeing with ftp is likely related to PASSV and how the ftp 
server expects to see the connection.

There is a documented solution in this thread:

[http://ubuntuforums.org/showthread.php?t=692355](http://ubuntuforums.org/showthread.php?t=692355)

Although it applies to people using dynamic dns, it applies equally as well if
you have a static ip address.

Faulkes

---

### Post by .nedberg on 2008-02-23
> **adamprawitz said:**
> But do I have the port forwarding setup correctly?


That part looks fine!

---

### Post by adamprawitz on 2008-02-23
> There is a documented solution in this thread:

[http://ubuntuforums.org/showthread.php?t=692355](http://ubuntuforums.org/showthread.php?t=692355)

I tried that stuff, but I am very confused.  Not sure if I did it right.  Do I have to use that script to check my ip address all the time?  I thought I set that to be static!

---

### Post by .nedberg on 2008-02-23
You sat it to get a static IP from your router. The router (probably) still gets a dynamic IP from your ISP.

It should however work even with dynamic IP. Problem is that you need to know if i changed. That is what no-ip can help you with.

---

### Post by adamprawitz on 2008-02-24
> That is what no-ip can help you with.

I also own a domain name, how do I go about setting up the server with the domain?  Is that what you were talking about?

---

### Post by .nedberg on 2008-02-25
I have an equal setup. I own a domain (nedberg.net) and I run some servers at home.

I wanted to use something.nedberg.net for every server at home, and nedberg.net should still point to the host I use for my web page.

I made an alias on my domain called server.nedberg.net which pointed to my no-ip address which pointed to my dynamic IP. It is a dirty way of doing things, but it works!

On no-ip you can get a domain name like adamprawitz.my-ftp.org or similar.

I suggest you first get things to work using your IP, then try with no-ip, then with a domain alias. Skipp the no-ip part if you get a static IP from your ISP.

---

### Post by .nedberg on 2008-02-25
By the way:
Why did you open the port for the MySQL server? Are you sure you need that? It is not needed if all you want is to serve web pages using php and MySQL. It is only needed if you connect directly to your MySQL server externally. I don't think it is recommended to keep it open like this...

Only keep it accessible if you know you need it!

---

### Post by adamprawitz on 2008-02-25
I did not know that I didn't need the MySQL port open.  Thank you for letting me know I do not need it.  I will stop forwarding it.  Thanks for your help.  I'm still not all the way where I want to be yet, but moving in  good direction.

---

### Post by .nedberg on 2008-02-25
Just glad I can help!

The next thing I would recommend you do is have a look in the logs.

FTP: cat /var/log/vsftpd.log (if you use vsftp)
SSH: cat /var/log/auth.log | grep ssh

I moved my ssh server to a different port and disabled root login via ssh. It is a bit of "security through obscurity", but it makes me sleep better at night :).

Don't be scared if you see a lot of login attempts in the ftp log! I had over 9000 failed attempts in one hour when I first sat up my server (all from the same IP). We can deal with that later if you want.

---

### Post by adamprawitz on 2008-02-25
I am having a problem now..... :(  

I changed some bind settings and now I can't "Connect to Server...." from the Places menu.  But I can SSH to it from terminal and I can FTP to it with FireFTP.

---

### Post by .nedberg on 2008-02-26
Well, my first advice would be to change it back... Remember to restart the ftp-service.

I like to change things one by one and keep backups of the confiogfiles along the way.

If ftp and ssh works from terminal then the problem is probably not your server.

---

