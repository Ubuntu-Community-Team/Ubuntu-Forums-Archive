---
title: "Webmin or ebox, which one to use"
date: 2008-05-11
forum: Server Platforms
---

### Post by rgotten on 2008-05-11
I have being looking and even thought a lot of people have used Webmin, i see that ebox is kind of new and not a lot of people have big input into it. I am new into doing server and would like to know if anybody have done the appropiate research and have a good recomendation on this...A good comparison and analisys will be appreciated

rgotten

---

### Post by Dr Small on 2008-05-11
I have never used ebox, so I have no opinion there. But I have been using Webmin, and works good to suit my needs.

Dr Small

---

### Post by Thirtysixway on 2008-05-11
Like dr. small, I haven't used eBox but I do have webmin.  I like webmin because of the ease of use, upgrading, and configuring it.  It has great security options and I can manage pretty much everything from it.

Looking at the ebox web site, it doesn't seem to have as many features as webmin does.  If I were you, I'd use webmin.

---

### Post by mbarak on 2008-05-11
If you were to use ebox you should be careful because (at least from my experience) it doesn't honour your previous settings (for example: dhcp settings), and doesn't save them in the location you would think (ex: /etc/dhcp3/dhcpd.conf) all the configuration files are saved within the ebox folder

After playing around a bit with it (this is, of course, before i figured out it broke my home network) it looked like a good way to integrate everything easily, and to configure everything online.

if you haven't already started configuring anything, give ebox a try - the ubuntu developers seem to like it better than webmin (seeing as ebox is in the repository but webmin is not)

having said that - i like webmin a lot, it works very well and saves all your configuration where you would expect them to be. webmin configures each server seperately while ebox seems to be able to integrate different parts of their configuration (ex: making global acl's)

of course, i may be completely wrong as welcome anyone to point it out to me before i cause any significant harm :)

---

### Post by Brazen on 2008-05-12
I've been a happy user of webmin for years.  I tried out ebox on Hardy and didn't like it.  It pulled in a LOT more dependencies and takes up more space and cpu/mem resources.  All that and it doesn't have near the configurability and features of Webmin.

For now, I'm sticking with Webmin.

---

### Post by MemoryDump on 2008-05-12
webmin hands down

---

### Post by dacool25 on 2008-05-12
Might want to look into [ISPConfig]("http://www.ispconfig.org") too.  I love it

---

### Post by rgotten on 2008-05-12
Ok, so i believe that WEBMIN is the way to go, sorry for my ignorance, if i install WEBMIN, how eill that compare to have a GUI over the server edition of ubuntu?

Thanks

rgotten

---

### Post by rgotten on 2008-05-14
OK, i would like to install webmin, how do i install it from teh command line from ubunt8u server edition?

rgotten

---

### Post by mbarak on 2008-05-14
```

wget http://superb-west.dl.sourceforge.net/sourceforge/webadmin/webmin_1.410_all.deb
dpkg -i webmin_1.410_all

```

---

### Post by rgotten on 2008-05-14
I am getting an error: error processing webmin_1.410_all
cannot access archive: no such file  or directory

Then i tryed 
sudo dpkg -i webmin_1.410_all.deb.1 and it started reading and unpacking but then again got errors processing ..etc

What should i do?

rgotten

webmin_1.410_all

---

### Post by mbarak on 2008-05-14
oops...sorry you're right, you should type the whole filename (including .deb)
and what sort of errors did you get?
did you try again? maybe it installed anyways?
or maybe the download was corrupt?

---

### Post by la3875 on 2008-05-14
I'm in the process of doing the same thing and glad this question was asked. The real question is why did Ubuntu drop Webmin in favor of eBox if so many are perfectly happy with the result?

---

### Post by inportb on 2008-05-14
Hm... broken dependencies, maybe? In that case:

sudo apt-get -f install

---

### Post by rgotten on 2008-05-14
Thanks, i was a ble to install after following your command

rgoten

---

