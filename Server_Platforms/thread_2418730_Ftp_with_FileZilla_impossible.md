---
title: "Ftp with FileZilla impossible"
date: 2019-05-10
forum: Server Platforms
---

### Post by ralphot on 2019-05-10
Getting 530 error

[COLOR=#000000][FONT=&amp]Status: Connecting to 192.168.1.90:21...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Status: Connection established, waiting for welcome message...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Status: Initializing TLS...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Status: Verifying certificate...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Status: TLS connection established.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Command: USER raffe2[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Response: 331 Please specify the password.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Command: PASS *********[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Response: 530 Login incorrect.[/FONT][/COLOR]
[FONT=Lucida Grande][COLOR=#000000]Error: Critical error: Could not connect to server[/COLOR][/FONT]

[FONT=Lucida Grande][COLOR=#000000]I know my username and password are correct.[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]FileZilla forum could not help me. Ftp client created in ISPConfig.[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]What could be wrong?[/COLOR][/FONT]

---

### Post by TheFu on 2019-05-10
FTP doesn't have encryption.
If you seek an encrypted file transfer, use sftp.

I have no experience with ISPConfig.

---

### Post by Morbius1 on 2019-05-10
How to fix “530 Login authentication failed” for ISPConfig FTP logins?: [https://ma.juii.net/blog/fix-ispconfig-ftp-logins](https://ma.juii.net/blog/fix-ispconfig-ftp-logins)

Since I have never used ISPConfig I used their demo and created an FTP user. It adds a prefix to the user name given so I'm wondering if Step 1 in the above link is the issue with you.

---

### Post by ralphot on 2019-05-13
I have realised that it's **my server** that has the problem. I have connected another ubuntu server
here and to ftp directly into that works fine but not the other way around.

SOLVED!!

It was [COLOR=#DD1144][FONT=Monaco]pure-ftpd-mysql that was missing!

Thank all for your help.[/FONT][/COLOR]

---

### Post by ralphot on 2019-05-13
HURRAY! Thanks a lot for the link, *_**it was [COLOR=#DD1144][FONT=Monaco][/FONT][/COLOR][COLOR=#008000][FONT=Monaco]pure-ftpd-mysql[/FONT][/COLOR][COLOR=#DD1144][FONT=Monaco] that was missing! Now it works as a charm!![/FONT][/COLOR]**_*

---

