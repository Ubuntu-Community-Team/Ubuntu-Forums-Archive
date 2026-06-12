---
title: "Remote GUI for administering FTP?"
date: 2008-07-06
forum: Server Platforms
---

### Post by Igtenio on 2008-07-06
Currently, I've set myself up with a server. It's a Command-line installation of Ubuntu, to which I added SSH, Apache, and Samba, and administer through SSH.

I'd like to add FTP capabilities, but, quite frankly, most of the FTP software is a pain to manually configure. I need an FTP Server that doesn't allow anonymous logins and requires a username and password to log in. Each person can view a universal folder and other users' folders in Read-only mode, and each person has their own Read/Write folder.

I've read tutorials, the Ubuntu documentation, man files, et cetera. I'm not too particularly keen on manually doing it, and I'd prefer a GUI. But all of the GUIs are seemingly for running on the host machine. I'd like something I could access in a web browser.

I've also toyed around with VNC in an attempt to remotely use a local GUI program, but, quite frankly, I'm finding it to be a pain to configure it when the server is headless and only remotely accessible. I haven't read as much on that as FTP configuration, so if anyone can point me towards something simple, I'd be appreciative.

I'd much rather have some sort of browser-based configuration for it, though, and haven't been able to find any.

Any help *at all* would be highly appreciated. Thanks for your time.

---

### Post by Dr Small on 2008-07-06
Just install proftpd and gproftpd if you want an easy FTP server to manage. It's very easy to set up, and can be managed over SSH by gproftpd.

But FTP is an old and unsecure protocol. You might look into SFTP over SSH.

Dr Small

---

### Post by Igtenio on 2008-07-06
Huh. I didn't know I could use gproftp to control proftpd on a different machine. Interesting.

Thanks.

---

### Post by Dr Small on 2008-07-06
Yes, as long as you have SSH installed on the server.

---

### Post by cariboo on 2008-07-06
Webmin will allow you to administer things from a web interface, thats as close to a gui as you are going to get.

This is an older howto, but it should work for any version:

[http://www.howtoforge.com/installing_webmin_ubuntu_feisty](http://www.howtoforge.com/installing_webmin_ubuntu_feisty)

Jim

---

### Post by rubbrduck on 2009-05-04
> **Dr Small said:**
> Yes, as long as you have SSH installed on the server.

Care to explain how?

---

