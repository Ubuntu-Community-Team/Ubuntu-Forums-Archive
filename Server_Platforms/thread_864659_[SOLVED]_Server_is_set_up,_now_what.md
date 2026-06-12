---
title: "[SOLVED] Server is set up, now what?"
date: 2008-07-19
forum: Server Platforms
---

### Post by sp0nge on 2008-07-19
***Warning- I'm in new teritory so feeling a bit No0b-ish***

I have gotten the server all configured (I think). I want to load a couple simple web pages to it, but I'm not sure where to put them. 

I was able to access the server from my desktop through firefox, and I presume the page I saw was the pre-loaded page within Apache. How can I determine the directory the HTML files belong in?

I also need some direction with setting up FTP between the server and the machine on my network that has the HTML files I would like to load. I presume that I can FTP into the server, but are there FTP user names and passwords that need to be setup? 

Thanks for the input and encouragement in advance!

---

### Post by Dr Small on 2008-07-19
Have you installed a webserver, such as Apache already? What about ProFTP for an FTP Server?

The default htdocs directory for Apache2 is /var/www

Dr Small

---

### Post by sp0nge on 2008-07-19
I have installed apache and proftp. I believe I have configured everything correctly, as I can put the IP into the address bar in firefox and see what I presume is a pre-loaded page from apache (one sentance, "It works!"). 

Thanks for your direction, I found the files in /var/www. So I can load my files into this directory, I presume via FTP since proftp is running?

---

### Post by Dr Small on 2008-07-19
I don't use ProFTP, so I really don't know how the default configuration works with it, but you can certainly try and see what happens when you connect via FTP. You may have to configure it first to get it to work properly, though.

---

### Post by windependence on 2008-07-20
> **sp0nge said:**
> I have installed apache and proftp. I believe I have configured everything correctly, as I can put the IP into the address bar in firefox and see what I presume is a pre-loaded page from apache (one sentance, "It works!"). 

Thanks for your direction, I found the files in /var/www. So I can load my files into this directory, I presume via FTP since proftp is running?

You don't even need an ftp server to put your files into the directory. On a Windoze machine you can use WinSCP to get them there securely and on a Linux desktop you can use Nautilus or Konqueror with sftp without installing any additional software or running any servers.

-Tim

---

### Post by sp0nge on 2008-07-21
Thanks for the suggestion, I suppose I had never really thought of the insecurity of FTP. I'll be downloading winSCP on my window$ machines, and are there any benefits to Nautilus over Konqueror or vice-versa?

---

### Post by Titan8990 on 2008-07-21
Not really. One is for the KDE desktop and the other is for the Gnome desktop.

---

### Post by sp0nge on 2008-07-21
Thank you.

---

