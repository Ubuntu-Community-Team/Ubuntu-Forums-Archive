---
title: "Home uses of Ubuntu Server"
date: 2012-12-21
forum: Server Platforms
---

### Post by cclloyd9785 on 2012-12-21
So I have an old-ish desktop that we were going to get rid of and upgrade, but then I wondered.

What are the home uses of installing Ubuntu Server on it?

If I install U.S. on it, can I manage it from Windows 8?

If I install the right software, can I host my own website on there (no bought domain name, just the IP address)

Can I share media like movies on it to Windows 8?

---

### Post by 2F4U on 2012-12-21
> If I install U.S. on it, can I manage it from Windows 8?

What do you mean by manage? You can login via SSH and do all the stuff that you would when logged in locally.

> If I install the right software, can I host my own website on there (no bought domain name, just the IP address)

Yes.

> Can I share media like movies on it to Windows 8?

Samba allows you to share files between different operating systems, among them Linux, Windows, and Mac OSX.

---

### Post by JoeSabido on 2012-12-22
Yes, you can manage it using SSH as 2F4U said, bur you can also manage it using anything with a browser (like your smartphone!) using Webmin.

Yes, you can host your website, Ubuntu Server comes with LAMP pre-installed and pretty much pre-configured.

Yes, you can put all the files you want to share on a folder in your home folder, and share it. The folder will be accessible from Windows.

;)

---

