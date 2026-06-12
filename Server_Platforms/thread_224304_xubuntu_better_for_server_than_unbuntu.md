---
title: "xubuntu better for server than unbuntu?"
date: 2006-07-27
forum: Server Platforms
---

### Post by printmkr on 2006-07-27
If I have installed ubuntu desktop, and want to add apache, etc after the fact (and feel comfortable with a GUI) would using xubuntu over ubuntu make a performance difference?

---

### Post by Sigur on 2006-08-14
What I tried (and works best in your case also), is install LAMP server which includes everything (Apache,PHP,Mysql) and then install the desktop (sudo apt-get install xubuntu-desktop).
You won't need GNOME and KDE as xubuntu is lighter and easy.

---

### Post by tlyczko on 2006-08-14
If I install Xubuntu like this, how do I then Start or Stop Xubuntu??

I presently have the command-line interface and I only want the Xfce interface if I want to do something with a GUI, most of the time I will not need the GUI.

Thank you, Tom

---

### Post by tlyczko on 2006-08-14
Are there any simpler window managers than Xubuntu??
I'd like something that just puts an understandable/usage GUI covering over the command line if possible.
Thanks, Tom

---

### Post by lvanderree on 2006-08-14
Why not try webmin, so you can configure your server from an other pc with a browser.

over here you can find a ubuntu install package:
[http://www.webmin.com/download.html](http://www.webmin.com/download.html)

which you can download from the command prompt with:
wget [http://surfnet.dl.sourceforge.net/sourceforge/webadmin/webmin_1.290.deb](http://surfnet.dl.sourceforge.net/sourceforge/webadmin/webmin_1.290.deb)

and install with:
sudo dpkg -i webmin_1.290.deb

This way you also don't have to change passwords for the webmin user, if I remember it correctly.

---

### Post by tlyczko on 2006-08-14
Thank you, webmin is exactly what I need, don't need window managers etc. any more!!

Thanks, Tom

---

