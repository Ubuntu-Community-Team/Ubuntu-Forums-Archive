---
title: "ssl vsftpd login"
date: 2008-10-09
forum: Server Platforms
---

### Post by Sid1980 on 2008-10-09
I am currently running ssl based vsftpd on ubuntu 8.04 and is running successfully with FTP core client; My Q is, can i also make web based ssl vsftpd ??  

Thx

---

### Post by cdenley on 2008-10-09
> **Sid1980 said:**
> I am currently running ssl based vsftpd on ubuntu 8.04 and is running successfully with FTP core client; My Q is, can i also make web based ssl vsftpd ??  

Thx

What?
apache = web-based (http)
vsftpd = ftp

By web-based, you mean something a user can use in their web browser, correct? Are you looking for a php script which lets you browse, download, and upload files? Or are  you looking for a java applet which functions as an FTP client which supports SSL encryption?

---

### Post by Sid1980 on 2008-10-09
> **cdenley said:**
> What?
apache = web-based (http)
vsftpd = ftp

By web-based, you mean something a user can use in their web browser, correct? Are you looking for a php script which lets you browse, download, and upload files? Or are  you looking for a java applet which functions as an FTP client which supports SSL encryption?

I wanna access ssl based FTP through browser like IE, Netscape or firefox etc.

---

### Post by cdenley on 2008-10-09
> **Sid1980 said:**
> I wanna access ssl based FTP through browser like IE, Netscape or firefox etc.

You mean like this?
[https://addons.mozilla.org/en-US/firefox/addon/684](https://addons.mozilla.org/en-US/firefox/addon/684)
I don't think any browser will do this by default. Do YOU want to do this, or do you want your users to be able to do this?

---

### Post by Sid1980 on 2008-10-09
> **cdenley said:**
> You mean like this?
[https://addons.mozilla.org/en-US/firefox/addon/684](https://addons.mozilla.org/en-US/firefox/addon/684)
I don't think any browser will do this by default. Do YOU want to do this, or do you want your users to be able to do this?

Lemme Explain this lil more pls,
I wanna setup FTP for 300 clients but since FTP doesn't support encryption i have introduced ssl option in vsftpd, but now problem is none of my client wanna use FTP client. Now i cant let plain data and pwd to travel on internet :( , 
Is there any script or applet which can integrate itself in browser and let user logon on ssl based FTP  ??

---

### Post by cdenley on 2008-10-09
> **Sid1980 said:**
> Lemme Explain this lil more pls,
I wanna setup FTP for 300 clients but since FTP doesn't support encryption i have introduced ssl option in vsftpd, but now problem is none of my client wanna use FTP client. Now i cant let plain data and pwd to travel on internet :( , 
Is there any script or applet which can integrate itself in browser and let user logon on ssl based FTP  ??

I'm not familiar with any, but a quick google search gave me a few possibilities such as:
[http://www.anyclient.com/](http://www.anyclient.com/)
I asked in my first post if you wanted an applet!
I use uber-uploader with SSL through apache instead of FTP, but I don't require browsing, downloading, or authentication. My only requirement is javascript. If you want to use SSL over FTP, your clients will need an FTP client, java, or a browser add-on.

---

