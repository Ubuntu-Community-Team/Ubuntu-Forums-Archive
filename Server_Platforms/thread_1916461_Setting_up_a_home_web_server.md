---
title: "Setting up a home web server"
date: 2012-01-28
forum: Server Platforms
---

### Post by flaneurism on 2012-01-28
Hello,

I'm thinking of setting up a web server at home using an old PC I have access to. I can't find anything against it in my ISP TOS, so I'm assuming I'm good to go - but I do have some questions.

**1. Security risks** - there are several computers connected to my home wireless network. Would establishing a web server make them vulnerable in any way?

**2. IP Address** - is there a way to make my website accessible by typing in an IP address as a URL??

**3. Operating System** - What is the best choice for a web server? I'm definitely going with something Linux-based, but I'm not sure which distribution would be best for a server.

**4. Control Panel** - I'm assuming I will need to install some kind of control panel (like cPanel). Is this required? If so, what are some open-source, free alternatives to cPanel?

**5. FTP** - Is there a way to set up FTP, so I can access the server remotely?

I'm sure I have asked some fairly obvious questions here, but please forgive me as I am fairly new with regards to home server setups.

Thank you.

---

### Post by lisati on 2012-01-28
*Thread moved to **Server Platforms**.*

---

### Post by Savio2010 on 2012-01-28
[QUOTE=]Hello,

I'm thinking of setting up a web server at home using an old PC I have access to. I can't find anything against it in my ISP TOS, so I'm assuming I'm good to go - but I do have some questions.

**1. Security risks** - there are several computers connected to my home wireless network. Would establishing a web server make them vulnerable in any way?

**2. IP Address** - is there a way to make my website accessible by typing in an IP address as a URL??

**3. Operating System** - What is the best choice for a web server? I'm definitely going with something Linux-based, but I'm not sure which distribution would be best for a server.

**4. Control Panel** - I'm assuming I will need to install some kind of control panel (like cPanel). Is this required? If so, what are some open-source, free alternatives to cPanel?

**5. FTP** - Is there a way to set up FTP, so I can access the server remotely?

I'm sure I have asked some fairly obvious questions here, but please forgive me as I am fairly new with regards to home server setups.

Thank you.[/QUOTE]


1.
Security is good thing to think first,
If you are going to use it for your internal network there won't be any risk, because all your PC are your own and your know them well. The important thing is keep all the devices from your PC to the server updated and patched.


2.
This the the easiest, you can access the web server just like you access your WiFi router. example [http://192.168.5.254/](http://192.168.5.254/)


3
Your best choice depends on various factors :
What you what to store on the server?
The configuration of the server?
etc etc

Some home server that I know
[http://openmediavault.org/](http://openmediavault.org/)
[http://www.freenas.org/](http://www.freenas.org/)
Or Ubuntu with Apache

FreeNAS and Open Media Vault are file servers not web servers.
FreNAS is based on FreeBSD not Linux
OMV is based on Debian Linux (Squeeze) OS


4
Free NAS and OMV both have web based administration Interface, so you can control it through your web browser.

You select any distro you can configure ftp on ii.

Hope it help.:)

---

### Post by flaneurism on 2012-01-28
> **Savio2010 said:**
> 1.
Security is good thing to think first,
If you are going to use it for your internal network there won't be any risk, because all your PC are your own and your know them well. 

I'm using it as a web server, not a local server.

> **Savio2010 said:**
> 
This the the easiest, you can access the web server just like you access your WiFi router. example [http://192.168.5.254/](http://192.168.5.254/)


Okay, excellent.

> **Savio2010 said:**
> 
Your best choice depends on various factors :
What you what to store on the server?
The configuration of the server?
etc etc


Just something that can deal with mysql and php. I'd mostly be running WordPress and other PHP/MySQL based CMS and other applications, as well as associated files (images, videos, audio, etc.)

---

### Post by a2j on 2012-01-28
> **flaneurism said:**
> 


Just something that can deal with mysql and php. I'd mostly be running WordPress and other PHP/MySQL based CMS and other applications, as well as associated files (images, videos, audio, etc.)

whatever you feel comfortable running. Most common linux distros (like debian or redhat based) will do.

---

### Post by shumifan50 on 2012-01-28
> 
1. Security risks - there are several computers connected to my home wireless network. Would establishing a web server make them vulnerable in any way?

2. IP Address - is there a way to make my website accessible by typing in an IP address as a URL??

3. Operating System - What is the best choice for a web server? I'm definitely going with something Linux-based, but I'm not sure which distribution would be best for a server.

4. Control Panel - I'm assuming I will need to install some kind of control panel (like cPanel). Is this required? If so, what are some open-source, free alternatives to cPanel?

5. FTP - Is there a way to set up FTP, so I can access the server remotely?


1. Whenever you open a port to the outside world it opens a possible route for attacks. This can be safeguarded by patching up to date and installing anti-virus software. Most web servers have exploits that are exposed/undiscovered so far.
2. That depends on whether you have a static IP or a dynamic IP Most standard service providers give you a dynamic IP which means it can change anytime. If you know your IP at any moment in time it can be accessed as mentioned above. You can also set up a DDNS (like no-ip.org) that allows you to access your server using a domain name, and it handles dynamic IPs for you - but you will need a domain name.
3. Linux is most likely the best to use as all the software you want to use is free. Easiest is to use Ubuntu; you can install desktop and add the server bits you need; that way you have a GUI for most functions.
4. Using apache there is good documentation to configure it by hand (not much needed for a simple website).
5.FTP can be set up quit ealy but defintely requires good ocking down.

---

### Post by Dangertux on 2012-01-28
I had written a guide for this a while back unfortunately wordpress ate it and I don't have a backup (I know bad dt bad...)

That being said I will touch on the basics and answer your questions the best I can. 

Security - web server security particularly with apache comes down to two things most of the time. The configuration of the service and associated permissions and the content being hosted. The biggest issues for webservers (again I'm talking about apache) is actually exploitation of the applications they run either to achieve cross site scripting/cross site request forgery or SQL injection. These will be your biggest threats. Ultimately the quality of the code in your web application (content management system) plays the largest factor there. Also if combined with a decent apache configuration a well written application can be pretty secure. Memory corruption exploitation (traditional buffer overflows) don't happen that often in Linux and even less so against apache as it's source code is pretty mature at this point. So your key areas should be choosing (or writing) a good web application , properly configuring permissions and if you want an extra layer of protection consider a web application firewall or external appliance like tipping points devices (these are expensive) alternatively cloudflare has some cheap solutions that work pretty well. 

As far as what OS, all of them can be hardened and serve as a good web hosting platform (even windows server) but in terms of Linux I personally like CentOS/RHEL for servers. Ubuntu is great as well but Ubuntu does many things in a nonconventional manner even more so than Debian. I would AT LEAST choose CentOS or Debian stable. If you do use Ubuntu I would recommend 10.04 or when 12.04 comes out that as you will want the stable long term service release for a server. 

For FTP I would really shy away from it. It is very difficult to configure FTP to be reasonably secure and even then it is not as secure as SFTP which is well supported and easy to set up. 

The dynamic ip issue I recommend no-ip they offer free dynamic dns for subdomains and relatively cheap 30 bucks dynamic dns for top level domains. 

Also you dont NEED a control panel, though if you want one I hear webmin is decent. Personally I prefer just using ssh. If you're familiar with Linux and the CLI (or willing to do author bit of learning) it's preferable in my opinion. As always adding more applications adds security risks webmin/cpanel are no exception to the rule
Hopefully this helps

---

### Post by sandyd on 2012-01-28
> **flaneurism said:**
> Hello,

I'm thinking of setting up a web server at home using an old PC I have access to. I can't find anything against it in my ISP TOS, so I'm assuming I'm good to go - but I do have some questions.

**1. Security risks** - there are several computers connected to my home wireless network. Would establishing a web server make them vulnerable in any way?
[B]Normally, you setup a server thats behind a NAT firewall by forwarding ports. 
Thats fine. The only problem comes when someone breaches your server security, and takes control of it.

[/B] **2. IP Address** - is there a way to make my website accessible by typing in an IP address as a URL??

**Forward port 80 to your server. Your ISP might block it.**

**3. Operating System** - What is the best choice for a web server? I'm definitely going with something Linux-based, but I'm not sure which distribution would be best for a server.

**4. Control Panel** - I'm assuming I will need to install some kind of control panel (like cPanel). Is this required? If so, what are some open-source, free alternatives to cPanel?

[B]You don't need to. In fact, its better if you don't. A control panel is a major security hole. Just one easy password, and someone will have access to your server. However, if you only allow the control panel to be accessed in your local network, this is not a problem.

The problem only comes if you want to access the control panel over the internet.
[/B]
**5. FTP** - Is there a way to set up FTP, so I can access the server remotely?

**vsftp,pure-ftpd,tftpd.**

I'm sure I have asked some fairly obvious questions here, but please forgive me as I am fairly new with regards to home server setups.

Thank you.
.

---

### Post by TheFu on 2012-01-29
Others answered most of your questions nicely, however, using FTP should be avoided these days. Use secure, easier to use alternatives based on ssh instead. Very few people should be using FTP anymore.  

Why you need to stop using FTP: 
* [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
* [http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)

If you are using MS-Windows, the WinSCP program or FileZilla are great sftp clients.
After you setup ssh, be certain to install fail2ban from the repository to actively protect your server from unauthorized access.

---

### Post by rubylaser on 2012-01-30
> **Dangertux said:**
> I had written a guide for this a while back unfortunately wordpress ate it and I don't have a backup (I know bad dt bad...)

That being said I will touch on the basics and answer your questions the best I can. 

Security - web server security particularly with apache comes down to two things most of the time. The configuration of the service and associated permissions and the content being hosted. The biggest issues for webservers (again I'm talking about apache) is actually exploitation of the applications they run either to achieve cross site scripting/cross site request forgery or SQL injection. These will be your biggest threats. Ultimately the quality of the code in your web application (content management system) plays the largest factor there. Also if combined with a decent apache configuration a well written application can be pretty secure. Memory corruption exploitation (traditional buffer overflows) don't happen that often in Linux and even less so against apache as it's source code is pretty mature at this point. So your key areas should be choosing (or writing) a good web application , properly configuring permissions and if you want an extra layer of protection consider a web application firewall or external appliance like tipping points devices (these are expensive) alternatively cloudflare has some cheap solutions that work pretty well. 

As far as what OS, all of them can be hardened and serve as a good web hosting platform (even windows server) but in terms of Linux I personally like CentOS/RHEL for servers. Ubuntu is great as well but Ubuntu does many things in a nonconventional manner even more so than Debian. I would AT LEAST choose CentOS or Debian stable. If you do use Ubuntu I would recommend 10.04 or when 12.04 comes out that as you will want the stable long term service release for a server. 

For FTP I would really shy away from it. It is very difficult to configure FTP to be reasonably secure and even then it is not as secure as SFTP which is well supported and easy to set up. 

The dynamic ip issue I recommend no-ip they offer free dynamic dns for subdomains and relatively cheap 30 bucks dynamic dns for top level domains. 

Also you dont NEED a control panel, though if you want one I hear webmin is decent. Personally I prefer just using ssh. If you're familiar with Linux and the CLI (or willing to do author bit of learning) it's preferable in my opinion. As always adding more applications adds security risks webmin/cpanel are no exception to the rule
Hopefully this helps


Dangertux, if you want to restore your previous guide, you could just grab it from Google's cache.  Here's a link to the [cache of your guide]("http://webcache.googleusercontent.com/search?q=cache:0t4ZCsRvqZ4J:dangertux.wordpress.com/tutorials/reasonably-secure-ubuntu-homesmall-business-server-tutorial/+&cd=1&hl=en&ct=clnk&gl=us").

---

### Post by Dangertux on 2012-01-30
Thanks appreciate it ;-)

---

