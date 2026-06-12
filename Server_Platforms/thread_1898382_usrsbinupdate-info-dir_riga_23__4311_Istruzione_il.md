---
title: "/usr/sbin/update-info-dir: riga 23:  4311 Istruzione illecita"
date: 2011-12-21
forum: Server Platforms
---

### Post by tpi on 2011-12-21
Hi, everyone. I'm using Ubuntu Server 9.
When I try to make any installation from the server, I get these messages:

```
Configurazione di install-info (4.13a.dfsg.1-4ubuntu1)...
/usr/sbin/update-info-dir: riga 23:  4311 Istruzione illecita     cp $INFODIR/dir $INFODIR/dir.old
dpkg: errore nell'elaborare install-info (--configure):
 il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 132
Configurazione di proftpd-basic (1.3.2-3)...
Illegal instruction
dpkg: errore nell'elaborare proftpd-basic (--configure):
 il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 132
dpkg: problemi con le dipendenze impediscono la configurazione di gadmin-proftpd:
 gadmin-proftpd dipende da proftpd-basic; comunque:
  Il pacchetto proftpd-basic non  ancora configurato.
dpkg: errore nell'elaborare gadmin-proftpd (--configure):
 problemi con le dipendenze - lasciato non configurato
Non  stata scritta alcuna segnalazione apport poich il messaggio di errore indica che  un errore da un fallimento precedente.
         Si sono verificati degli errori nell'elaborazione:
 install-info
 proftpd-basic
 gadmin-proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

This happens since when I installed proftpd and gadmin-proftpd (that seem to work both correctly). I tried to reinstall  proftpd-basic package but I recieve the same messages, please can you give me any piece of advice?

Thank you in advance.
Federica

---

### Post by tpi on 2011-12-21
I just add what I recieve typing the command
sudo cat /var/log/dpkg.log

```
2011-12-21 12:36:56 startup packages configure
2011-12-21 12:36:56 configure install-info 4.13a.dfsg.1-4ubuntu1 4.13a.dfsg.1-4ubuntu1
2011-12-21 12:36:56 status half-configured install-info 4.13a.dfsg.1-4ubuntu1
2011-12-21 12:36:56 configure proftpd-basic 1.3.2-3 1.3.2-3
2011-12-21 12:36:56 status half-configured proftpd-basic 1.3.2-3
2011-12-21 12:36:58 startup packages configure
2011-12-21 12:36:58 configure install-info 4.13a.dfsg.1-4ubuntu1 4.13a.dfsg.1-4ubuntu1
2011-12-21 12:36:58 status half-configured install-info 4.13a.dfsg.1-4ubuntu1
2011-12-21 12:36:59 configure proftpd-basic 1.3.2-3 1.3.2-3
2011-12-21 12:36:59 status half-configured proftpd-basic 1.3.2-3
2011-12-21 15:11:21 startup packages configure
2011-12-21 15:11:21 configure install-info 4.13a.dfsg.1-4ubuntu1 4.13a.dfsg.1-4ubuntu1
2011-12-21 15:11:21 status half-configured install-info 4.13a.dfsg.1-4ubuntu1
2011-12-21 15:11:21 configure proftpd-basic 1.3.2-3 1.3.2-3
2011-12-21 15:11:21 status half-configured proftpd-basic 1.3.2-3
```


Hope someone can find this information helpful.
Please, suggest me something to try...

---

