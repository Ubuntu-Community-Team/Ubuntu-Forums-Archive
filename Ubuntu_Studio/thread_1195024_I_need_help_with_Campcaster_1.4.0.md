---
title: "I need help with Campcaster 1.4.0"
date: 2009-06-23
forum: Ubuntu Studio
---

### Post by moe19790 on 2009-06-23
hi,

every time i try to install the campcaster i`m getting this Msg Please help

Code

 p, li { white-space: pre-wrap; }  [FONT=Monospace]Checking for required tools...[/FONT]
 [FONT=Monospace]Executable su found...[/FONT]
 [FONT=Monospace]Executable psql found...[/FONT]
 [FONT=Monospace]Creating database and database user...[/FONT]
 [FONT=Monospace]ERROR:  role "campcaster" already exists[/FONT]
 [FONT=Monospace]ERROR:  database "Campcaster" already exists[/FONT]
 [FONT=Monospace]Done.[/FONT]
 [FONT=Monospace]Creating ODBC data source for Campcaster scheduler.[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]Using the following installation parameters:[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]  database server:        localhost[/FONT]
 [FONT=Monospace]  database:               Campcaster[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]Checking for required tools...[/FONT]
 [FONT=Monospace]Executable sed found...[/FONT]
 [FONT=Monospace]Executable grep found...[/FONT]
 [FONT=Monospace]Executable odbcinst found...[/FONT]
 [FONT=Monospace]Registering ODBC PostgreSQL driver...[/FONT]
 [FONT=Monospace]odbcinst: Driver installed. Usage count increased to 1. [/FONT]
 [FONT=Monospace]    Target directory is /etc[/FONT]
 [FONT=Monospace]Registering Campcaster ODBC data source...[/FONT]
 [FONT=Monospace]Done.[/FONT]
 [FONT=Monospace]Setting up directory permissions...[/FONT]
 [FONT=Monospace]Configuring apache ...[/FONT]
 [FONT=Monospace]/etc/apache/conf.d N[/FONT]
 [FONT=Monospace]/etc/apache2/conf.d Y[/FONT]
 [FONT=Monospace]done[/FONT]
 [FONT=Monospace]Restarting apache...[/FONT]
 [FONT=Monospace]apache N[/FONT]
 [FONT=Monospace]apache2 Y[/FONT]
 [FONT=Monospace] * Restarting web server apache2[/FONT]
 [FONT=Monospace]apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName[/FONT]
 [FONT=Monospace] ... waiting ...apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName[/FONT]
 [FONT=Monospace]   ...done.[/FONT]
 [FONT=Monospace]done[/FONT]
 [FONT=Monospace]Creating symlinks...[/FONT]
 [FONT=Monospace]Initializing database...[/FONT]
 [FONT=Monospace]*************************[/FONT]
 [FONT=Monospace]* StorageServer Install *[/FONT]
 [FONT=Monospace]*************************[/FONT]
 [FONT=Monospace]DB Error: connect failed[/FONT]
 [FONT=Monospace] [nativecode=pg_pconnect(): Unable to connect to PostgreSQL server: FATAL:  no pg_hba.conf entry for host "::1", user "campcaster", database "Campcaster", SSL off] ** pgsql(pgsql)://campcaster:PASSWORD@localhost/Campcaster[/FONT]
 [FONT=Monospace]Database connection problem.[/FONT]
 [FONT=Monospace]Check if database 'Campcaster' exists with corresponding permissions.[/FONT]
 [FONT=Monospace]/opt/campcaster/bin/postInstallStation.sh: line 402: 15425 Segmentation fault      php -q install.php[/FONT]
 [FONT=Monospace]dpkg: error processing campcaster-station (--install):[/FONT]
 [FONT=Monospace] subprocess post-installation script returned error exit status 1[/FONT]
 [FONT=Monospace]Errors were encountered while processing:[/FONT]
 [FONT=Monospace] campcaster-station[/FONT]

---

### Post by linux newbie2 on 2009-06-28
[SIZE=3]im getting the same problem
help!
linux newbie2:KS
[/SIZE]

---

### Post by peeyush2005 on 2009-09-18
[SIZE=3]Same problem here... please help us asap.[/SIZE] :(

---

### Post by maskurniawan on 2010-02-19
thank God I managed to overcome the problem. The solution to first check what port postgres is not true. reply anyone would ask please can send an email to me. thanks.[IMG]http://www.google.com/images/cleardot.gif[/IMG]

---

### Post by fedepier on 2010-03-26
I have the same error. I don't understand what I have to. Pls Help!

---

