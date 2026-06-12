---
title: "Apache: how to create the remote folder"
date: 2006-07-24
forum: Server Platforms
---

### Post by kenquad on 2006-07-24
Hi again all:

Can you tell I'm having a long day with a Linux server?  I don't know if anyone out there has knowledge of Macromedia Dreamweaver 8, but perhaps this question is platform-neutral enough that the particular design software isn't relevent.  I'm trying to use my new LAMP server for a test pod for a new PHP-MySQL browser application, but Dreamweaver asks for a remote folder to store PHP scripts and that kind of thing.  This folder has to be in the web server's root folder.  Does anyone know exactly what this means and how I can creat such a folder with the appropriate permissions?

Thanks,
Ken Ha Quad

---

### Post by harisund on 2006-07-24
I am assuming you have a proper LAMP stack on machine with the IP 192.168.0.3 and you are working on your Windows box with IP 192.168.0.2 on the same local LAN. Your user on the Linux machine is kenquad.

I would suggest you first execute ```
sudo a2enmod userdir
```. Next in the home directory of your default user (let's assume it is kenquad) create a directory called public_html. You could do this by ```
mkdir public_html
``` in your home directory.

From now on, whatever you save in the public_html directory can be accessible with [http://192.168.0.3/~kenquad/](http://192.168.0.3/~kenquad/). For example a sample.css in the public_html directory would be accessible in [http://192.168.0.3/~kenquad/sample.css](http://192.168.0.3/~kenquad/sample.css) and so on. 

Next, in order to access the public_html folder on your Linux machine (at 192.168.0.3) from the Windows box running Dreamweaver on (192.168.0.2) you have the following choices: 
1. install samba. This will allow you to "see" the public_html folder from your Windows box, and Dreamweaver can save directly into it. 
2. Get a FTP server. Then your 192.168.0.3 box becomes like a regular web hosting machine, and you can set up your Dreamweaver to 'upload' the files in kenquad user's public_html directory in the 'ftp server' 192.168.0.3. Get my point? 

Tell me your choice, and I will try to explain how to get it done. But remember whatever method you want to use, always save php scripts and html files in the public_html directory, as that is the only directory that apache sees to server web pages.

---

### Post by kenquad on 2006-07-25
Harisund:

Thanks for the reply!  I followed your instructions, but got the rror message ```
Module is already running!
``` after running ```
sudo a2enmod userdir 
``` ???

Ken Quad

---

### Post by kenquad on 2006-07-25
Wait a minute, it worked!  I just hadn't put the html file I was using for the test into the correct directory!  Thanks!

OK, now for the options of Samba or FTP.  Using Samba sounds easier to me.  What do you think?

---

### Post by harisund on 2006-07-25
Hmm.. I am thinking these days apache comes with the userdir module already enabled (besides, next time you get a "already enabled" error message, consider it a good thing and not an error :D )

Now, if you want samba, here is what I would do. 

First up, ```
sudo aptitude install samba smbfs
```

(Once again, I am making the same assumptions as earlier)

Next do ```
sudo smbpasswd -a kenquad
``` where you would replace kenquad with the appropriate user name. You will be asked to enter a password. 

Finally, I would edit /etc/samba/smb.conf in the following way. Remember, this is only for a local home network and wouldn't work across a domain or something like that .. 

So, inside the smb.conf 

First, you will see a "workgroup" directive. Change it if you wish, otherwise don't bother. 

Head down to the "Share Definitions" section. I only changed the "writeable" to "yes" instead of "no." Have a look at the rest if you are interested. 

Once you are done, ensure you do ```
sudo invoke-rc.d samba restart
``` to get samba running. 

Now head over to your Windows box, open up explorer, go to "Tools->Map Network drive". Enter in your IP of the Linux box (\\192.168.0.3\kenquad\public_html" and give it Z:\ or something. 

From then on, anything you do in dreamweaver save it in Z:\ and you can access it from [http://192.168.0.3/~kenquad](http://192.168.0.3/~kenquad)

Of course this would only work from local LAN and not if you have a router or something in between your Windows and Linux box

---

### Post by kenquad on 2006-07-25
Harisund:

Thanks for the detailed instructions!  I followed them as exactly as I could (filling in my IPs, etc.) but I get an unable to connect error from Windows Explorer when attempting the last step.  Can you think what I might be doing wrong?  Incidentally, the Win2k box can ping the Linux server with no problem.

Thanks

---

### Post by kenquad on 2006-07-25
Never mind, I got it working.  Just had to specify in smb.conf to share all user's home dirs.  I know that's not the best way, but security isn't an issue at the moment.  Also had to force a refresh of workgroup computers.  I then browsed from Explorer into the public_html folder.  BTW, how does Apache know that the public_html folder is the one to display?

---

### Post by harisund on 2006-07-25
I am no Apache pro, but I can get my way around :D

Here are some documentation that might come in handy for you. 

[http://httpd.apache.org/docs/2.2/mod/mod_userdir.html](http://httpd.apache.org/docs/2.2/mod/mod_userdir.html)
[http://httpd.apache.org/docs/2.2/howto/public_html.html](http://httpd.apache.org/docs/2.2/howto/public_html.html)

I think I too did make all directories browseable. As you said perhaps there are some security implications that I am willing to overlook. 

> Also had to force a refresh of workgroup computers
Hope you didn't have to restart anything? On Linux you could have merely done "sudo invoke-rc.d samba restart" to put into effect any changes you might have done. On Windows however you might have to restart, not sure. I don't use the Workgroup concept and instead directly use the IP address, so I do not know.

So everything works? You want to try FTP too?

---

### Post by kenquad on 2006-07-25
Harisund:

Everything works splendidly; thanks again.  I'm all ready to get started programming PHP.  On FTP, I will probably want to do that eventually.  You see, the current platform is for web development.  I plan to use a similar setup to host the final site (or more correctly, database application) on the server.  This will entail removing the server from the local LAN, so Samba will no longer be a good option.  Does Apache have an FTP server?  Also, what does one do to get a domain name - a very very un-cool domain name.  (It doesn't matter since it's not for public access.)

Ken Ha Quad

---

### Post by harisund on 2006-07-25
Good to hear that you are all set and ready to go. 

First up, Apache is purely a HTTP server and not a FTP server of any sort. Consequently you will want to install one. There are plenty of ones (I would suggest you search through the forums) and try out as many as you want. I could suggest one, but in the case of FTP servers it is highly likely that some one will come along and make a post saying my choice absolutely sucks and the FTP server they recommend is the industry standard, totally secure, flawless one or whatever.

Next, one option you have is to actually buy a domain name and web hosting.

However for convenience sake the simplest would be to head to somewhere like [http://no-ip.com](http://no-ip.com) or [http://www.dyndns.com](http://www.dyndns.com) and get yourself a free domain name. You will end up having something like kenquad.something.com where that 'something' will be decided by the no-ip or dyndns website when you register. 

again, if you are behind a router, remember to forward the appropriate port (if you don't understand what I am talking about, we will go over that next) and also remember your ISP is most likely to block port 80 so you might want to either run your webserver on another port (not necessary) or just forward another port to your webserver's port 80 (easiser).

---

