---
title: "Uninstall software"
date: 2010-03-04
forum: Server Platforms
---

### Post by webdirector on 2010-03-04
Hi I am new to ubuntu.

I installed Ubuntu 9.10 server on a HP Proliant DL380 G3 for testing.

I neede to install some software from HP (Value add software pack)

In this software pack I was unable to get one software up and running ( called [COLOR=#000000][FONT=Arial][SIZE=2]hprsm )

I tried installing several times and allways ended with " The hprsm RPM installation failed! "

I then tried to uninstall the software " [/SIZE][/FONT][/COLOR][I][COLOR=#000000][FONT=Arial][SIZE=2]dpkg  --purge ... " and "rpm -e ... " and even " rpm -e --force-debian .... " but I can not uninstall it.

Now when I install other software i keep getting " [/SIZE][/FONT][/COLOR][/I][COLOR=#000000][FONT=Arial][SIZE=2]The hprsm RPM installation failed! "

when I do " find / -name hprsm " I get :

/opt/compaq/hprsm
/opt/compaq/hprsm/hprsm
/etc/init.d/hprsm
/usr/share/doc/hprsm

How can I uninstall this software ? just delet these files ?

Thanks for help


any way I can uninstall this software ? 
[/SIZE][/FONT][/COLOR]

---

### Post by wojox on 2010-03-04
What does this tell you:

```
sudo dpkg -S /opt/*
```

---

### Post by webdirector on 2010-03-04
I get this:

cpqacuxe, hpacucli, cmanic, hpasm, hprsm: /opt/compaq
hpadu, cmanic, hp-openipmi, hpsmh, hpasm: /opt/hp


Thanks for help

---

### Post by wojox on 2010-03-04
This should work:

```
sudo dpkg -P hprsm
```

Take it you came from Red Hat or Fedora?

---

### Post by webdirector on 2010-03-04
Thanks that worked !

I will try to find the meaning of the "-P"

---

### Post by wojox on 2010-03-04
-P means to purge. It will delete the file and all it's config files. ;)

---

### Post by wojox on 2010-03-04
Look around for an **alien** how-to. Never used it but it converts .rpm to .deb so Ubuntu can install them correctly.

---

