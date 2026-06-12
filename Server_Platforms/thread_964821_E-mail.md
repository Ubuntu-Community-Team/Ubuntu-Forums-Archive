---
title: "E-mail"
date: 2008-10-31
forum: Server Platforms
---

### Post by cjwallace on 2008-10-31
Guys.

I am using Zabbix on my Ubuntu server. I need to have it send emails , can someone please let me know which package to install

apt-get install ??

Cheers

Craig

PS , Sorry still learning Linux at the moment

---

### Post by narnian99 on 2008-10-31
run "apt-cache search zabbix"

on hardy i get the following :-


zabbix-agent - software for monitoring of your networks -- agent
zabbix-frontend-php - software for monitoring of your servers -- php frontend
zabbix-server-mysql - software for monitoring of your networks -- server
zabbix-server-pgsql - software for monitoring of your networks -- server

---

### Post by cjwallace on 2008-10-31
Thanks for the reply mate.

I already have Zabbix up and running and working ok at the moment.

I just need to get the email part working and i dont think by default on Ubuntu server any email stuff like postfix is it:confused: gets installed

---

### Post by cjwallace on 2008-11-02
Hi guys.

Any ideas on installing an smtp agent \ program so Zabbix can send out email alerts?

Cheers

Craig

---

### Post by cjwallace on 2008-11-02
Hi guys.

Not to worry i used apt-get install postfix

I have now configured the system and emails are being sent from Zabbix

Cheers

Craig

---

