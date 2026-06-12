---
title: "install a standard server"
date: 2007-11-20
forum: Server Platforms
---

### Post by Proliant on 2007-11-20
Hi
I'm new to Ubuntu I'm downloading the new 7.10 server I have 7.04 server installed with webmin.

I need to run PH with Apache and MySQL and a FTP server and SAMBA (to share with windows users

but when I use webmin to install MySQL I get errors I got Apache to work but no PHP

Is there a manual to install these servers from the terminal?

where do I start and will webmin see the new servers that I install on the server itself?

Please help

---

### Post by prodezigner on 2007-11-20
If you're doing a clean install of 7.10 there's an option for a LAMP stack automatically (Linux / Apache / MySQL / PHP & Perl). Webmin was dumped from the 7.10 repos cause it's buggy.

I understand a lot of people want some sort of GUI, but after monkeying around with the CLI I've realized I don't need Webmin, myPhpAdmin, SWAT or any other GUI running on my server.

My server (currently) consists of Ubuntu 7.10 Server Edition, LAMP, SSH, SAMBA and Torrentflux. All CLI driven of course, but Torrentflux has a Web UI for downloads and all that good jazz. I've even thought about switching to rTorrent for that, but I have no early clue where to start on that.

But like I said, clean install, just select LAMP, SSH and SAMBA (if your file sharing over a network) and you're set. As for an upgrade, no clue... Anyone?

---

