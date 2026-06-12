---
title: "Xubuntu as webserver, can use XAMPP?"
date: 2010-11-04
forum: Server Platforms
---

### Post by flameproof on 2010-11-04
I want to convert an old PC to a webserver, mainly to work as a webcrawler and store results into mysql.

Due to the PCs 512Mb RAM I think Xubuntu may run better. However, I don't see any Xubuntu-Server distribution.

Is Xubuntu as server useful anyway? Can it work with XAMPP or do I need to install Apache and MySQL separately?

---

### Post by P4man on 2010-11-04
xubuntu uses xfce as desktop environment. ubuntu-server has no desktop environment (so no gnome, xfce, kde or whatever). If you want, you can install xfce on top of it, if you want a GUI.

---

### Post by s1nch4n on 2010-11-04
> **flameproof said:**
> I want to convert an old PC to a webserver, mainly to work as a webcrawler and store results into mysql.

Due to the PCs 512Mb RAM I think Xubuntu may run better. However, I don't see any Xubuntu-Server distribution.

Is Xubuntu as server useful anyway? Can it work with XAMPP or do I need to install Apache and MySQL separately?
ubuntu server doesn't use GUI...

but u can install XAMPP, as long as u don't install Apache, Mysql, FTP from main repository...

download XAMPP seperately, use wget command....

---

### Post by flameproof on 2010-11-04
Was really easy!

1. install Xubuntu

2. D/L Xampp here:  [http://sourceforge.net/projects/xampp/files/XAMPP%20Linux/1.7.3a/xampp-linux-1.7.3a.tar.gz/download](http://sourceforge.net/projects/xampp/files/XAMPP%20Linux/1.7.3a/xampp-linux-1.7.3a.tar.gz/download)

3. Put the d/l file on the Desktop

4. In Terminal do: CD Desktop

5. In Terminal do: sudo tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt

6. Start XAMPP in Terminal: sudo /opt/lampp/lampp start


However, since my old PC doesn't have keyboard and I don't want to switch keyboards all the time I also installed Remote Desktop with this instruction: [http://www.ehow.com/how_6980234_enable-xubuntu-remote-desktop.html](http://www.ehow.com/how_6980234_enable-xubuntu-remote-desktop.html)

Now to put files onto my web directories I had to install Samba.... But so far all works perfectly.

---

