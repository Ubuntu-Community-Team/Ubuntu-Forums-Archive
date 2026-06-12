---
title: "Ubuntu Hardy Server. Shares read-only on terminal, write possible on dolphin"
date: 2009-01-16
forum: Server Platforms
---

### Post by awe on 2009-01-16
Hello,

I have migrated my business to Ubuntu recently. I am facing a problem with samba shares. I have created a number of shares on the Ubuntu Server 8.04 setup. I can see all the shares and their files from the clients. Clients are Kubuntu 8.04. However, I am able to write on the shares only when I am in Dolphin, but from the terminal I cannot. Also, I have a wine application and it cannot write.

I have tried what I think is every possible option. I have many shares, but I will talk about only one of them in order to keep this post simple. It is mounted on startup via the fstab file:
```
# Samba shares
//servidor/planningtour /servidor/planningtour cifs iocharset=utf8,credentials=/servidor/.smbcredentials,file_mode=0777,dir_mode=0777 0 0
```

I have tried with and without file_mode and dir_mode. The entry on the server for this share is like this:

```
[planningtour]
        comment = Dades del programa PlanningTour
        path = /opt/planningtour
        printable = no
        hide dot files = yes
        read only = no
        guest ok = yes
        public = yes
        writable = yes
        browseable = yes
        force directory mode = 0777
        force user = administrador
        admin users = root, administrador, recepcio, comptabilidad, nobody
```

Samba uses an LDAP backend. It is configured so in the server as well as the clients:

server:
*passdb backend = ldapsam:ldap://localhost/*

clients:
*passdb backend = ldapsam:ldap://192.168.10.1/*
192.168.10.1 being of course the server's IP where LDAP runs.
The pre-LDAP setting in smb.conf was passdb backend = tdbsam, producing the same (bad) results that I have now.

When working on the client, I am logged in as user "administrador" that exists locally on the client as well as in the server's LDAP tree.

What am I doing wrong? 

This setup is a small business, every machine is a production machine, I cannot afford to keep playing around, the network in my business will remain stopped until I can solve this problem. I suppose you understand that I am under stress.

Regards.

---

