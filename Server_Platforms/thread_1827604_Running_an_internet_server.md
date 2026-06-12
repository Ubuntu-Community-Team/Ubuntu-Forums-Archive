---
title: "Running an internet server"
date: 2011-08-18
forum: Server Platforms
---

### Post by gameguy on 2011-08-18
I have a server running ubuntu (desktop) 11.04. I want to run it as an web server. I know how to port forward, but wanted a few things to happen.
Firstly, to edit the HTML files, and to do various other things, I wanted to connect to the server.
This would be from a windows machine (win7 home premium). Any ideas on how to map a linux network drive? samba is confusing me...

Secondly, I need a script to run the server over the lan (port forwarding to the internet I can handle). I can find one online (I need a python script, BTW), but is there any reccommendation for one which I could edit?

Thirdly, I need some sort of user/pwd combination (with several different users) which can be displayed in the web browser.

---

### Post by hawk2010 on 2011-08-18
The real question is whether you want to do this task from the internet side or from the LAN side. The recommended way would be for you to VPN in to your LAN network and then via WinSFTP do the job.

---

### Post by gameguy on 2011-08-18
No need for VPN. It's all on a lan. This is a home server I'm running, not a professional one.

---

### Post by PierreRobiquet on 2011-08-18
I would recommend using SCP to transfer files but if you really want to map a drive in Windows samba is the only way to go. I created a new user for each Samba user then setup a directory in /home/samba for each of these new users, so I would do useradd -d /home/samba/www -s /bin/false smb-www then just do smbpasswd on the smb-www user and point Apache to use /home/samba/www as your root. 

That should resolve any of the permission errors that you may be having as smb-www will own the directory as it's the home, you might want to add the Apache user to the smb-www group (it's been a while I don't remember the username it uses) and allow group write to the home directory.

I'm sure there might be a better way of doing it as I personally haven't used Apache too much and I'm following my own Samba setup as such I would wait for someone more experienced who may have a better answer.

---

### Post by gameguy on 2011-08-18
I don't mind what protocol is used, as long as it can be accessed through windows explorer.
I'll try it tomorrow and see if it works. Thanks

---

### Post by gameguy on 2011-08-19
Got the website working using MySQL login and apache.
Does anyone know how to change the website directory to "/home/server/Desktop/Web\ Server"?
Also, still need to know how to access the linux file system from windows

---

### Post by gameguy on 2011-08-20
I have come across some problems. Firstly, on the root directory (where index.html is), it has favicon.ico, but it still doesn't display that in the browser. Secondly, I am getting a problem with my .php files (eg login.php) where it tries to download them instead of run the php and html on the page. Does anyone know the solution to that?
Thanks

---

