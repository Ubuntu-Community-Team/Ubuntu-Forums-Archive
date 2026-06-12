---
title: "problem removing gforge-ldap-openldap"
date: 2004-12-08
forum: Repositories &amp; Backports
---

### Post by willg on 2004-12-08
I am having a problem removing gforge-ldap-openldap. These are the steps I have taken:

<willg@pihlopase dir="willg"/>$ sudo apt-get remove gforge-ldap-openldap
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
The following packages will be REMOVED:
  gforge-ldap-openldap
0 upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
Need to get 0B of archives.
After unpacking 291kB disk space will be freed.
Do you want to continue? [Y/n]
(Reading database ... 51036 files and directories currently installed.)
Removing gforge-ldap-openldap ...
dpkg: error processing gforge-ldap-openldap (--remove):
 subprocess pre-removal script returned error exit status 5
Errors were encountered while processing:
 gforge-ldap-openldap
E: Sub-process /usr/bin/dpkg returned an error code (1)


Ok, so I try:

<willg@pihlopase dir="willg"/>$ sudo dpkg -P --force-depends gforge-ldap-openldap
(Reading database ... 51036 files and directories currently installed.)
Removing gforge-ldap-openldap ...
dpkg: error processing gforge-ldap-openldap (--purge):
 subprocess pre-removal script returned error exit status 5
Errors were encountered while processing:
 gforge-ldap-openldap


Not sure what to do next. 

William

---

### Post by p!=f on 2004-12-08
[QUOTE=willg]I am having a problem removing gforge-ldap-openldap. These are the steps I have taken:

<willg@pihlopase dir="willg"/>$ sudo apt-get remove gforge-ldap-openldap
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
The following packages will be REMOVED:
  gforge-ldap-openldap
0 upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
Need to get 0B of archives.
After unpacking 291kB disk space will be freed.
Do you want to continue? [Y/n]
(Reading database ... 51036 files and directories currently installed.)
Removing gforge-ldap-openldap ...
dpkg: error processing gforge-ldap-openldap (--remove):
 subprocess pre-removal script returned error exit status 5
Errors were encountered while processing:
 gforge-ldap-openldap
E: Sub-process /usr/bin/dpkg returned an error code (1)


Ok, so I try:

<willg@pihlopase dir="willg"/>$ sudo dpkg -P --force-depends gforge-ldap-openldap
(Reading database ... 51036 files and directories currently installed.)
Removing gforge-ldap-openldap ...
dpkg: error processing gforge-ldap-openldap (--purge):
 subprocess pre-removal script returned error exit status 5
Errors were encountered while processing:
 gforge-ldap-openldap


Not sure what to do next. 

William[/QUOTE]

What's dpkg -l gforge-ldap-openldap saying?
Example:
```

:~ $ dpkg -l evolution
ii  evolution                   2.0.2-0ubuntu2              The groupware suite

```
Those two little ii means the package is installed just fine. If you find something else out there (probably pi), try to reinstall the package first
```

sudo apt-get --reinstall install gforge-ldap-openldap

```
and then purge it.

---

### Post by Alex1 on 2005-03-26
not solvede cause:
```
alex@goldrake:/etc$ sudo dpkg -l gforge-ldap-openldap
Desiderato=sconosciUto/Installato/Rimosso/P:eliminato/H:bloccato
| Stato=Non/Installato/file Config./U:spacchett./conf. Fallita/H:inst.parzial.
|/ Err?=(nessuno)/H:bloc./necess.Reinst./X=entrambi (Stato,Err: maiusc.=grave)
||/ Nome           Versione       Descrizione
+++-==============-==============-============================================
ri  gforge-ldap-op 3.1-24         Collaborative development tool - LDAP direct


```

and
```

alex@goldrake:/etc$ sudo apt-get --reinstall install gforge-ldap-openldap
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
0 aggiornati, 0 installati, 1 reinstallati, 0 da rimuovere e 0 non aggiornati.
È necessario prendere 69,6kB di archivi.
Dopo l'estrazione, verranno occupati 0B di spazio su disco.
Continuare? [S/n] S
Get:1 http://it.archive.ubuntu.com hoary/universe gforge-ldap-openldap 3.1-24 [6 9,6kB]
Scaricato 69,6kB in 1s (64,2kB/s)

Preconfiguring packages ...
Selezionato il pacchetto gforge-ldap-openldap, che non lo era.
(Lettura del database ... 92290 file e directory attualmente installati.)
Mi preparo a sostituire gforge-ldap-openldap 3.1-24 (con .../gforge-ldap-openlda p_3.1-24_all.deb) ...
Spacchetto il rimpiazzo di gforge-ldap-openldap ...
Configuro gforge-ldap-openldap (3.1-24) ...
WARNING: Please check referal line in /etc/ldap/slapd.conf
Replacing file /etc/libnss-ldap.conf with changed version
Replacing file /etc/nsswitch.conf with changed version
Replacing file /etc/ldap/slapd.conf with changed version
Stopping OpenLDAP: slapd.
Starting OpenLDAP: slapd.
gforge_base_dn = dc=localdomain
server_base_dn = dc=localdomain
Gforge base DN is under the existing server base DN -- OK
addon =
Gforge base DN is equal to server base DN -- OK
WARNING WARNING WARNING: LDAP Configuration Failed
It seems the LDAP load failed, possibly due to a password mismatch
Please check your passwords (especially /etc/ldap.secret) and try again.
dpkg: errore processando gforge-ldap-openldap (--configure):
 il sottoprocesso post-installation script ha restituito un codice di errore 5
Sono occorsi degli errori processando:
 gforge-ldap-openldap
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

what can i do to resolve it?
i use 5.04 hoary

---

### Post by AzureCerulean on 2005-08-24
Possible "FIX" for BROKEN package  gforge-ldap-openldap

1) Remove SLDAP
2) Install SLDAP

This will NOT allow you to remove  gforge-ldap-openldap  but your packages will no longer be broken,.

Best Wishes

Azure Cerulean

---

### Post by vladanian on 2005-09-20
Does anyone out there know how to excise an unwanted package from a Debian system?  I'm having this exact same problem with gforge and I'm totally pissed off about it!

What if I DON'T WANT this software on my system, and DON'T WANT its dependencies?

Seriously, is this Windows-land, where my only recourse is to reinstall the whole system?  I've googled about forcing a deb to uninstall, no matter what it's fucking post or pre install script says, and I'm coming up empty...

---

### Post by vladanian on 2005-09-20
Ok, I just deleted all the gforge stuff I could find by hand, and dpkg finally obliged my remove request.  I guess I'll see in time whether I messed anything up too badly.

So, the fix on that was:

"locate gforge" & a bunch of "sudo rm -rf"

:)

---

