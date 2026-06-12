---
title: "Bluefish 1.0"
date: 2005-01-14
forum: Ubuntu Backports
---

### Post by Smash on 2005-01-14
Hello!

Someone wants to build a Bluefish 1.0 package in backports? It's possible?

---

### Post by jdong on 2005-01-14
[http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=bluefish](http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=bluefish)

Debian Sid only has 0.13. I don't want to go too bleeding edge.

---

### Post by HiddenWolf on 2005-01-14
Whoa. 0.13 - 1.0? That's a big jump.

---

### Post by jeremy on 2005-01-15
I've installed bluefish 1.02 from debian sid by adding
deb [http://ftp.carnet.hr/pub/debian/](http://ftp.carnet.hr/pub/debian/) sid main non-free contrib
to my sources.list
-works perfectly

---

### Post by jdong on 2005-01-15
[http://ftp.carnet.hr/pub/debian/pool/main/b/bluefish/](http://ftp.carnet.hr/pub/debian/pool/main/b/bluefish/)

I see 0.13 and 0.7.

---

### Post by jeremy on 2005-01-16
Sorry, too many things going on in my head!!!
fter trying and failing to install from source, I downloaded [http://pkedu.fbt.eitn.wau.nl/~olivier/downloads/bluefish-1.0-1.fc3.src.rpm](http://pkedu.fbt.eitn.wau.nl/~olivier/downloads/bluefish-1.0-1.fc3.src.rpm)
and did;
sudo alien -d && sudo dpkg -i

---

### Post by jdong on 2005-01-16
Umm, I don't think I want to backport from another distro with a completely different packaging format! I'll wait for some sort of Debian package.

---

### Post by Smash on 2005-01-17
[QUOTE=jeremy]Sorry, too many things going on in my head!!!
fter trying and failing to install from source, I downloaded [http://pkedu.fbt.eitn.wau.nl/~olivier/downloads/bluefish-1.0-1.fc3.src.rpm](http://pkedu.fbt.eitn.wau.nl/~olivier/downloads/bluefish-1.0-1.fc3.src.rpm)
and did;
sudo alien -d && sudo dpkg -i[/QUOTE]

Does not work  :( 

@ Jdong: i don't want to stress you, have you planned a backport? If yes, when? Days? Weeks? Month?
I tried to compile it, but i miss some libraries. I need it....  ;)

---

### Post by jdong on 2005-01-17
[QUOTE=Smash]@ Jdong: i don't want to stress you, have you planned a backport? If yes, when? Days? Weeks? Month?
I tried to compile it, but i miss some libraries. I need it....  ;)[/QUOTE]

As soon as Debian Sid or Experimental packages start rolling out, I'll backport them. Debian likes to customize major new releases, and I don't want to create a lower-than-Sid quality package.

---

### Post by Smash on 2005-01-17
[QUOTE=jdong]As soon as Debian Sid or Experimental packages start rolling out, I'll backport them. Debian likes to customize major new releases, and I don't want to create a lower-than-Sid quality package.[/QUOTE]

This works!!!!  :D 

[http://pkedu.fbt.eitn.wau.nl/~olivier/downloads/bluefish_1.0_unoficial-1_i386.deb](http://pkedu.fbt.eitn.wau.nl/~olivier/downloads/bluefish_1.0_unoficial-1_i386.deb)

This is the installation (in italian):
```

# dpkg -i bluefish_1.0_unoficial-1_i386.deb
Selezionato il pacchetto bluefish, che non lo era.
(Lettura del database ... 73272 file e directory attualmente installati.)
Spacchettamento di bluefish (da bluefish_1.0_unoficial-1_i386.deb) ...
dpkg: problemi con le dipendenze impediscono la configurazione di bluefish:
 bluefish dipende da libgnomevfs2-0 (>= 2.8.3-7); comunque:
  La versione di libgnomevfs2-0 nel sistema è 2.8.2-0ubuntu1.
dpkg: errore processando bluefish (--install):
 problemi con le dipendenze - lasciato non configurato
Sono occorsi degli errori processando:
 bluefish

```

There are some missing dependencies, but it works. I hope it will be stable  8-)

---

### Post by cabu on 2005-01-17
I got the same thing when I installed the unofficial .deb(in english though  :) ). And it worked on my system too. I then decided to 'apt-get remove it', and went ahead and compiled from source. I had to apt-get libgtk2.0-dev and libpcre3-dev to get it to compile. Works perfect.

---

### Post by jdong on 2005-01-17
ok, I'll build it during the next few days.

---

### Post by Smash on 2005-01-17
[QUOTE=jdong]ok, I'll build it during the next few days.[/QUOTE]

Thank you!!!!!  =D>

---

### Post by Tato on 2005-01-18
I could send it to you if you dont want to go trough all the trouble of making it. The title needs to be fixed because I added the description by mistake. Let me know if you need it.

---

### Post by albersag on 2005-01-25
I works marvellous ;)

Thanks . 

At today 25/01 is not backported i think.

---

### Post by techn9ne on 2005-02-08
I got it installed using the .deb that previous poster recommended. I can start it up and it runs great and adds a icon to the gnome menu but it gave me this error on install and when I try to apt-get upgrade:

The following packages have unmet dependencies:
bluefish: Depends: libgnomevfs2-0 (>= 2.8.3-7) but 2.8.2-0ubuntu1 is installed

---

### Post by jdong on 2005-02-11
[http://pkedu.fbt.eitn.wau.nl/~olivier/downloads/bluefish-1.0.tar.bz2](http://pkedu.fbt.eitn.wau.nl/~olivier/downloads/bluefish-1.0.tar.bz2)

I'll see what I can do given that tarball.

---

### Post by techn9ne on 2005-02-11
Thanks Jdong for all the work you put in.

---

### Post by jdong on 2005-02-12
Currently compiling.

---

