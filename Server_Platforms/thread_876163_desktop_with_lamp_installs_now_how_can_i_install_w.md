---
title: "desktop with lamp installs now how can i install webmin ?"
date: 2008-07-31
forum: Server Platforms
---

### Post by dxlwebs on 2008-07-31
hey all i have ubuntu desktop installed and i have installed LAMP and SHH server thing from the symtics package but i would like to install webmin now but i have no idea on where to even start does anyone have any ideas

thank you for your help

---

### Post by jimv on 2008-07-31
Open Synaptic, search for 'webmin', check it, and install it.

OR 

Open a terminal and run this command:

```
sudo apt-get install webmin
```

You will then be able to open webmin by going to [https://yourcomputersaddress:10000](https://yourcomputersaddress:10000)

---

### Post by dxlwebs on 2008-07-31
hey i did the search and it came back with no resaults what do i do ?

---

### Post by dxlwebs on 2008-07-31
does no one know ?

---

### Post by bodhi.zazen on 2008-07-31
See if this helps :

[http://www.howtoforge.com/installing_webmin_ubuntu_feisty](http://www.howtoforge.com/installing_webmin_ubuntu_feisty)

---

### Post by 3rods on 2008-07-31
I just installed it yesterday. I had to go download the .deb package from webmin site. 

```
mkdir /home/**username**/webmin
wget http://prdownloads.sourceforge.net/webadmin/webmin_1.420_all.deb
sudo ipkg -i webmin_1.420_all.deb

```

This will throw an error about dependencies, but just copy the two things it wants and do an apt-get for them. I forget what they are - something about ssl and a perl module.

Then run ipkg command again.

---

### Post by bodhi.zazen on 2008-07-31
> **3rods said:**
> I just installed it yesterday. I had to go download the .deb package from webmin site. 

```
mkdir /home/**username**/webmin
wget http://prdownloads.sourceforge.net/webadmin/webmin_1.420_all.deb
sudo ipkg -i webmin_1.420_all.deb

```This will throw an error about dependencies, but just copy the two things it wants and do an apt-get for them. I forget what they are - something about ssl and a perl module.

Then run ipkg command again.

Just a FYI :

If you get dependency errors when using dpkg, use apt-get to resolve them, the -f option will resolve them automatically :

```
sudo dpkg -i webmin*.deb
sudo apt-get install -f
sudo dpkg -i webmin*.deb
```

---

