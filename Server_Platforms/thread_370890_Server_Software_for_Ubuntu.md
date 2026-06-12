---
title: "Server Software for Ubuntu"
date: 2007-02-26
forum: Server Platforms
---

### Post by termin8tor on 2007-02-26
Hi, I'm interested in running a server on a spare dedicated box I have at home.
I was just curious as to what server software people on here tend to use and why?

I know apache is a popular one, I was just wondering what other stuff is available and if it has advantages / disadvantages over apache and what those might be.
Preferably i'm thinking of opensource servers (did I really need to type that?) :) 

Anyway thanks in advance!

---

### Post by thenebcouk on 2007-02-26
Hi, it's good to really experiment and see what suits you.
With any OpenSource software there's many different levels at which you can implement any services.

Certainly apache is a very popular choice, it still is the number one webserver being used on the web.

But if you just want to poke around I'd suggest using apache, ssh/sftp and other services such as printers. But it really depends what you are looking to do with that machine in the future.

---

### Post by houstonbofh on 2007-02-26
I installed Ubuntu-server with the LAMP option.  I also installed ProFTPd, and ssh.  To secure it you **Need** fail2ban ASAP.  I also installed vtiger crm.  It is the only thing not in the repositories.

---

### Post by doogy2004 on 2007-02-26
[LIST=1]
[*]LAMP server
[*]SSH - so i don't have to sit in my closet for the rest of the process
[*]enable all repos
[*]upgrade dist (sudo apt-get update) then (sudo apt-get dist-upgrade), this will keep the current distro version
[*]winbind
[*]dnsmasq
[*]samba
[*]smbfs
[*]vmware server - if you are using a CLI server i have instructions on what all packages that you will need for vmware server to run
[*]vmware server mui - allows you to monitor VMs and system resources
[*]democracy - if you have a gui, then share the folder where the content gets downloaded
[*]phpbb
[*]mediawiki
[*]no-ip
[*]x11vnc - if you are running a gui on your server
[*]wildfire - jabber server
[*]automatix - gui app that installs commonly used programs
[*]azureus
[*]mythtv - backend
[/LIST]

here is a like to a thread in the automatix forum that i posted the instructions on how to install/configure some of these application [http://www.getautomatix.com/forum/index.php?showtopic=210](http://www.getautomatix.com/forum/index.php?showtopic=210)

send me a message if you want instuctions on the steps to take to get this all together

---

