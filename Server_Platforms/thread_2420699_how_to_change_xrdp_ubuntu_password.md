---
title: "how to change xrdp ubuntu password"
date: 2019-06-09
forum: Server Platforms
---

### Post by yonited on 2019-06-09
Hi , i had installed xrdp on my ubuntu server 16.4 .... lately i read a lot of articles that there is malware around scanning the internet for available xrdp and hack them by brutal force then resell those available servers on hacker forums
i am a noob and i want to harden my password or secure my xrdp connection so my server doesn't get hacked and be used in illegal actions

---

### Post by TheFu on 2019-06-09
NEVER put rdp or VNC servers directly on the internet.  Only allow "localhost" connections, so that secured, encrypted, tunnels into the localhost are required to access it.

Or you can use x2go, which is based on the NX protocol.  NX uses ssh tunnels. The ssh-part is built-into the NX protocol.  And using ssh for 95% of your remote needs would be smart too, but there are times when a remote desktop is the best answer.  x2go feels 2-3x faster than rdp or vnc options.  You won't be watching videos, but doing normal office productivity stuff feels about the same whether I'm on the same LAN or on a different continent.

Whenever doing authentication over the internet, never use passwords. Always use key-based authentication techniques, like ssh-keys.

---

### Post by yonited on 2019-06-09
so what i do now .. sry i am completely ubuntu noob ... basically i am windows user and i am using xrdp to have access to my server .... do i need to unistall xrdp package and install x2go or i can just leave it installed and i install and start using x2go

---

### Post by TheFu on 2019-06-09
First, you need to get ssh working between the client and server. ssh  is one of the first things I install on every Unix system I touch.  It is THE way that Unix systems communicate. ssh is the 500-way to communicate between Unix systems. It is freakin' amazing.  On the remote "server"
```
sudo apt install openssh-server fail2ban
```
On the local client
```
sudo apt install openssh fail2ban
```
fail2ban will dynamically block brute force attacks on the remote system. It is pre-configured for the default ssh port 22/tcp.  If the server is internet facing, you probably want to have the router perform port translation so your log files don't get filled with denied attempts.  If you don't, expect 100,000 attempts every day.

Second, you need to setup ssh-keys and transfer the public key to the server.
```
ssh-keygen -t ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@remote 
```
Change the userid@remote for your remote login. You can use an IP address or DNS name. If the local userid is same as the remote one, you don't need to include that ... with any ssh-based connection.

Third, you should verify that ssh between the client and server works without requiring a password entered, except to unlock the ssh-key file. It will stay unlocked for some period of use. ssh-agent will handle that for you.
```
ssh userid@remote
```
does that work?  If it doesn't, come back for help.  No use moving forward.

With ssh working, you can create an ssh tunnel for xrdp to use. You can create a SOCKS proxy tunnel for your browser to use. You can remotely access files using sshfs or sftp or scp. Only sshfs requires additional packages to be installed.  The authentication will use that same key you made above and be highly secure.  Pretty much every Linux file manager supports using sftp:// URLs to access remote files.

After all that, now you are ready to install x2go, if you still want.  A remote desktop has all sorts of issues which are best avoided, but sometimes, it is the correct answer.  
On the remote server: [https://wiki.x2go.org/doku.php/doc:installation:x2goserver](https://wiki.x2go.org/doku.php/doc:installation:x2goserver)
On the local client: [https://wiki.x2go.org/doku.php/doc:installation:x2goclient](https://wiki.x2go.org/doku.php/doc:installation:x2goclient)
I use the x2go client from Windows and Linux. Both are very stable.  The x2go server only works on Linux.  
The only trick with any remote desktop is to NOT use a heavy DE, so if you use Mate, XFCE or LXDE, then everything will be fine with the correct keyboard maps.   With Windows, install the full font packages.  DO NOT USE Unity or Gnome3 with x2go. KDE4 might have issues. IDK.

That's all I have time for now.

---

