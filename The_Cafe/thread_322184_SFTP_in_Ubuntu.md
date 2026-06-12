---
title: "SFTP in Ubuntu?"
date: 2006-12-20
forum: The Cafe
---

### Post by Aleksandersen on 2006-12-20
Hi,

Is it possible to use [SFTP](http://ask.com/web?q=SFTP) in any FTP clients in Ubuntu? Does GFTP support it? Any other clients?

---

### Post by frodon on 2006-12-20
I believe gFTP support it [http://gftp.seul.org/](http://gftp.seul.org/) in its latest version, anyway if you use firefox there's an extention called fireFTP which is an FTP client with support for almost all the existing FTP protocols.
BTW, when you say SFTP, do you mean FTP with TLS/SSL encryption or FTP over SSH ?

---

### Post by raggari on 2006-12-20
Ary you sure about Fireftp support?

From FAQ:
When will FireFTP support SFTP or SSH?
Oh, man. Maybe one day. I think I'm saving it for FireFTP 2.0...and I'm not even at 1.0 yet!

---

### Post by frodon on 2006-12-20
I'm using it with firefox 2.0 and FTP with TLS/SSL encryption without any problem, i haven't tested FTP over SSH but i believe saw the option in the connection menu.

EDIT: indeed i seems that there's no options for FTP over SSH

---

### Post by Aleksandersen on 2006-12-20
> **frodon said:**
> BTW, when you say SFTP, do you mean FTP with TLS/SSL encryption or FTP over SSH ?
Oh, I don't really know... ^^

Whatever that works and is more secure than FTP.

I cannot see an SFTP option in GFTP. Hovewer I see an SSH2 optioin, but I cannot select it.

---

### Post by frodon on 2006-12-20
Yes the gFTP in the repositories don't support FTP with TLS/SSL encryption that's why i use fireFTP instead.
About security, both FTP with TLS/SSL encryption and FTP over SSH are secure, both encrypt the username/password and the datas sent so both are good to use.

---

### Post by Aleksandersen on 2006-12-20
Hm, OK. Thanks for the clarification!

Why does not the repository version of GFTP support secure connections? It see that it is the same version number as on the project's Website.

Does anyone happen to know whether I can use one of the more secure FTP protocols with a [GoDaddy Apache (Linux) hosting plan](https://www.godaddy.com/gdshop/hosting/shared.asp?se=%2B&ci=260)? I tried looking in their support section, but could not find any information about it.

---

### Post by AgenT on 2006-12-20
You already have an sftp client installed on your system by default. It is called sftp (surprise!).

For more information, type:
```
man sftp
```But maybe you are talking about a different kind of sftp. In that case, open up the package manager Synaptic and search for ftp using only the "name" option. You will find about 10 clients to choose from.

If you want a really advanced ftp client with ssh support, try lftp.

If you want just a simple sftp connection without anything advanced, try the built in GNOME network connect at Places -> Connect to Server -> Other option and type in the address like so:
```
sftp://username@server
```

---

### Post by Aleksandersen on 2006-12-21
Oh, never mind. I just had an e-mail discussion with GoDaddy. Apparently they consider it a security risk to allow users to access their accounts via secure FTP connections. There goes that idea...

---

