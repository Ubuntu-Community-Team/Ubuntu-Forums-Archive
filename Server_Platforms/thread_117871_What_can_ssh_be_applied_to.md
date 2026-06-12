---
title: "What can ssh be applied to?"
date: 2006-01-15
forum: Server Platforms
---

### Post by Zensunni on 2006-01-15
I want to know more about ssh, but I'd like to know what the comon applications of it are. For instance, can ssh be used for http server security handshakes or am I way off track? Or, is it more like a linux terminal that can be accessed through other machines? If so, what do I need to install if I wanted to access it over a windows box? Does it work with telnet, or is it essentually like telnet?

Thanks for any info.

---

### Post by drogoh on 2006-01-15
In one sense, call it encrypted telnet.  There's a little more to it but that summary should suffice.

---

### Post by bobyang on 2006-01-15
Actually after windows2000, it supports telnet, but just limited function, not too much things that you can do in windows if there is no gui, right?

---

### Post by imagine on 2006-01-15
SSH creates an encrypted tunnel between two computers, which can be used for basically everything. Be it remote controlling a box, forwarding the graphical user interface and the ouput of applications or whole desktops, transferring data over ftp/http whatever, mounting folders and so on. You can also create tunnels over multiple hosts and thereby reaching computers which aren't even connected to the internet but only some local network. It's lightweight, secure and reliable and therefore used very often in the Linux/Unix world.
However when talking about handshakes with HTTP servers you maybe are mixing SSH up with Secure Socket Layer (SSL).

About Windows: As long as Windows is the client everythings fine. PuTTY is an excellent SSH client. But Windows may not really be suited for a SSH server, depeding on what you want to do. Windows has no built-in SSH server and you also cannot control Windows just over the command line. Of course if you have enough bandwidth you can simply forward the complete Windows desktop through your SSH tunnel.

---

### Post by Zensunni on 2006-01-17
Thanks, imagine

I'm just curious on what forwarding a desktop/GUI means. Does that mean it'd be like remote desktop, or is it like transporting the whole system config of a server's to your box via config files, etc?

I also want to clarify that it is a terminal with a prompt, right? Would it be just like logging onto your own linux terminal? If so, can you change what commands a user can and cannot make?

Sorry for the 50 questions. Thanks for bearing with me :P. You guys have been very helpfull.

---

### Post by Gustav on 2006-01-17
If you ssh to another machine you can see it as you have access to that machines terminal and you can do anything from your machine as you can do on the other machine.

You can start programs that have guis although they will probably be a little slow since all the graphics must be transported over the net.

All the work will be done on the server machine.

---

### Post by art2003 on 2006-01-18
I have ubuntu on my desktop and fedora on a headless server (just a power cable and a network cable, no keyboard or monitor or cdrom or floppy drive ) with ssh working fine.

Can I install ubuntu remotely through ssh to upgrade the fedora machine (which has no cdrom or floppy drive but lots of hard drive space)

---

### Post by LordHunter317 on 2006-01-18
[QUOTE=Zensunni]I want to know more about ssh, but I'd like to know what the comon applications of it are. For instance, can ssh be used for http server security handshakes or am I way off track?[/quote]No.

>  Or, is it more like a linux terminal that can be accessed through other machines?In essence.  It also has  VPN/tunneling capabilites.

>  If so, what do I need to install if I wanted to access it over a windows box?PuTTY.

---

### Post by OneSeventeen on 2006-01-18
Just a quick update, for transferring files between my windows machine at work and my ubuntu server at work, I uninstalled FTP servers (which I installed while following webserver setup tutorials) and just use SSH via [WinSCP](http://winscp.net/eng/index.php)

I also ssh in to install/remove/configure/etc using putty.

And if you have another linux box, you can just use various file transfer apps, I'm pretty sure including gftp, plus you can mount remote folders in Gnome via SSH very easily.

So, for me, SSH is primarily used for an FTP replacement, and remote terminal access, although you can do just about anything else with it.

(oh, and Macromedia Dreamweaver MX 2004 and above can use an SSH connection instead of FTP.  They call it SFTP)

---

