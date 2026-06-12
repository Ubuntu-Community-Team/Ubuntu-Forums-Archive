---
title: "Problem running BIND9"
date: 2013-09-29
forum: Server Platforms
---

### Post by Jacob_Tennant on 2013-09-29
I have followed the instruction fro this webpage to install SAMBA4 as an AD:

[http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04](http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04)

However, when I add the following lines to the named.conf file BIND9 fails to start:
[COLOR=#000000][FONT=Consolas]
/var/lib/samba/private/named.conf
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]tkey-gssapi-keytab "/var/lib/samba/private/dns.keytab";
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]allow-query { any; };
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]allow-recursion { any; };
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]forwarders { 172.16.182.1; };
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]dnssec-validation no;

I am running this instance of Ubuntu Server 12.04 LTS on VMWare Fusion.[/FONT][/COLOR]

---

### Post by Habitual on 2013-09-29
What's the exact error message when starting it?
You have a [COLOR=#000000][FONT=Consolas]/var/lib/samba/private/dns.keytab file in that location?[/FONT][/COLOR]
and you are on a 172.16.0.0/12 network?

---

