---
title: "Can Kolab be Installed with Apt-get instead of obmtool?"
date: 2006-12-15
forum: Server Platforms
---

### Post by brianwhi on 2006-12-15
I am running 32 bit kubuntu 6.10 as a vm with vmware.  I want to experiment with kolab server.  When I did an apt-cache search for kolab I got a long list of available packages:

root@kubuntu610-templ:~# apt-cache search kolab
kdepim-wizards - KDE server configuration wizards
kolab-cyrus-admin - Cyrus mail system (administration tool)
kolab-cyrus-clients - Cyrus mail system (test clients)
kolab-cyrus-common - Cyrus mail system (common files)
kolab-cyrus-imapd - Cyrus mail system (IMAP support)
kolab-cyrus-pop3d - Cyrus mail system (POP3 support)
kolab-libcyrus-imap-perl - Interface to Cyrus imap client imclient library
kolab-resource-handlers - Scripts for the Kolab groupware server
kolab-webadmin - web-interface for kolab administration
kolabd - Kolab groupware server
ldap-account-manager - webfrontend for managing accounts in an LDAP directory
libkolab-perl - Perl extensions for the Kolab Groupware Suite
root@kubuntu610-templ:~

I took a snapshot and did apt-get install kolabd.  It installed most of the packages listed then launched into a setup routine asking configuration questions.  After I answered them it said apache was also installed and running.  

Does anyone know if this is the correct method to install kolab now with ubuntu 6.10?  I don't know how to download all the packages into the directory to use with the installation tool that's in the kolab documentation.

---

### Post by joan.mercadal on 2006-12-29
Hello,
Have you finally install the kolab server in this way?

Then, could you advise me how to configure.. access to kolab-webadmin?

Regard

Joan

---

### Post by TurboSockeGT on 2007-01-10
Yes, kolab2 can be installed this way, but you still have to "bootstrap" it with /usr/share/kolabd/kolab_bootstrap -b 
Which doen't create a valid ldap configuration, at least on my system.

At the moment I'm torn apart between the OpenPKG original which doesn't create the apache configuration and the Ubuntu package,

Either way I have to find the time to get my hands dirty and either fix the ubuntu package templates or create an apache.conf of my own for the original.

The third alternative is sticking to with eGroupware which is fine for my needs.

---

