---
title: "idiot looking for help installing php"
date: 2006-05-08
forum: Server Platforms
---

### Post by happytechie on 2006-05-08
Hi all, thanks for reading.

I'm a complete novice with ubuntu and linux in general and am trying to install apache, MySQL etc on a server install.  I'm following this guide:

[http://easylinux.info/wiki/Ubuntu#Apache_HTTP_Server](http://easylinux.info/wiki/Ubuntu#Apache_HTTP_Server)

and it's fine untill I run a sudo apt-get install php4

when I get:

$sudo apt-get install php4
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package php4

can anyone help?

I can see the welcome to apache page when I access the box from another machine on my network so it's doing something :D

edit:

php5 installed just fine so that's done but now I get the same error with proftpd :(

Paul

---

### Post by Omnios on 2006-05-08
Hi just checked it in Synaptic. It is there its under univers/web which means you probably do not have etra repositores set up.

Ubuntu wiki link on adding exttra repositories.
[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse]("http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse")

---

### Post by happytechie on 2006-05-08
thanks for the swift help,
I think I've added the required repositories to the sources.list file but I'm still getting:

:E Couldn't find package protoftp when I try to Apt-get install protoftp

Any ideas

Paul

---

### Post by Omnios on 2006-05-08
Just did a quick synaptic check for it and they dont seem to have it.

---

### Post by Omnios on 2006-05-08
Not shure where to get this program from but you could probably wget it.

---

### Post by happytechie on 2006-05-09
thanks for your help. I'm more than a little bit lost in this world of apt-get but I'm sure I'll get there.  I managed to get a different ftp package installed (vsftpd I think) but I still need to configure it all.  I shut the machine down last night before I went to bed and this morning the network hasn't started so that's my firtst task tonight

Can anyone point me at some decent instructions for getting the ftp server and apache to the state where I can create directories in the ftp directory and have these appear as directories under the web root?  eg if I create ~ftp/mynewsite this will appear in apache as [http://whizz/mynewsite/](http://whizz/mynewsite/) where whizz is the machine's name?

Thanks in advance

paul

---

### Post by Omnios on 2006-05-09
There are two main ways to get info here. Furum search and ftp.
Pure Ftp how to
[http://ubuntuforums.org/showthread.php?t=91052]("http://ubuntuforums.org/showthread.php?t=91052")
Ftp server WIki page
[https://wiki.ubuntu.com/PureFTP?highlight=%28ftp%29]("https://wiki.ubuntu.com/PureFTP?highlight=%28ftp%29")
[https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=apache]("https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=apache")

 There is also a web server admin page that lets you set up and use your server from another machine but forget what it is called.

---

### Post by happytechie on 2006-05-10
Thanks for your hel[p, I get the ftp server and webmin installed and workig last night :D

I'm sure I'll have more questions soon....

HT

---

