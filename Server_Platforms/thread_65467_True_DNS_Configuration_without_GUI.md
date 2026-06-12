---
title: "True DNS Configuration without GUI"
date: 2005-09-14
forum: Server Platforms
---

### Post by MistaED on 2005-09-14
Hello,

I have had a slackware 9.1 server running 24/7 on a simple network doing various simple jobs like sharing printers and files with CUPS/Samba and it worked fine, but I really enjoyed the .deb package system and APT so I moved the server to Ubuntu Server. (the network is a bog-standard d-link 4-port router with various clients hooked up to it, and the server just tags off of it).

Although the problem I see with the Ubuntu Server install is that I cannot see an easy way to configure static IP addresses with an easy-to-use script (possibly the server installer needs a nice network configurator?). I managed to edit /etc/network/interfaces successfully and that works fine. My real problem now is configuring the nameserver. I cannot use apt-get on the server, and configuring the nameserver in resolv.conf doesn't work because it is being overwritten every boot-up, and modifying the startup scripts to prevent it from being overwritten as a 'hack' solution given on other threads has been very hit and miss.

The server has no gnome, so it doesn't have that nice GUI to set static IP addresses, DNS names, etc. on it so I'm pretty stuck. It seems as though the only way to "clean-up" DNSes with static IP addresses is through gnome's little network configurator :( please, can someone help me? This is quite dumb as it seems that ubuntu server requires X11/gnome for it to be configured properly. :(

I'll probably install debian sarge on the next server when I get more storage for it and I use dad's old 1.2ghz athlon instead :)

Thank you very much

-MistaED

---

### Post by John Nilsson on 2005-09-17
[QUOTE=MistaED]Hello,

I have had a slackware 9.1 server running 24/7 on a simple network doing various simple jobs like sharing printers and files with CUPS/Samba and it worked fine, but I really enjoyed the .deb package system and APT so I moved the server to Ubuntu Server. (the network is a bog-standard d-link 4-port router with various clients hooked up to it, and the server just tags off of it).

Although the problem I see with the Ubuntu Server install is that I cannot see an easy way to configure static IP addresses with an easy-to-use script (possibly the server installer needs a nice network configurator?). I managed to edit /etc/network/interfaces successfully and that works fine. My real problem now is configuring the nameserver. I cannot use apt-get on the server, and configuring the nameserver in resolv.conf doesn't work because it is being overwritten every boot-up, and modifying the startup scripts to prevent it from being overwritten as a 'hack' solution given on other threads has been very hit and miss.

The server has no gnome, so it doesn't have that nice GUI to set static IP addresses, DNS names, etc. on it so I'm pretty stuck. It seems as though the only way to "clean-up" DNSes with static IP addresses is through gnome's little network configurator :( please, can someone help me? This is quite dumb as it seems that ubuntu server requires X11/gnome for it to be configured properly. :(

I'll probably install debian sarge on the next server when I get more storage for it and I use dad's old 1.2ghz athlon instead :)

Thank you very much

-MistaED[/QUOTE]
 What init process is overwrinting reolv.conf? I checked my setup and all I can see that mentions resolv.conf is ppp stuff. Disable those scripts and you should be fine.

---

### Post by az on 2005-09-17
Etherconf is a nice ncurses interface to configuring ethernet devices.

sudo apt-get install etherconf

sudo dpkg-reconfigure etherconf 
to make changes.

---

### Post by jlist on 2005-09-18
[QUOTE=azz]Etherconf is a nice ncurses interface to configuring ethernet devices.

sudo apt-get install etherconf

sudo dpkg-reconfigure etherconf 
to make changes.[/QUOTE]
Tried this and got an error: Couldn't find package etherconf. Removed?

---

### Post by az on 2005-09-19
[QUOTE=jlist]Tried this and got an error: Couldn't find package etherconf. Removed?[/QUOTE]
I think it is in the universe repository.

---

### Post by jlist on 2005-09-19
[QUOTE=azz]I think it is in the universe repository.[/QUOTE]
Oh, first time heard of it. Can you tell me how to access it?

---

