---
title: "Very Slow Initial Response of Web Page"
date: 2013-06-12
forum: Server Platforms
---

### Post by greatlakes on 2013-06-12
Hi folks,

LAMP (Ubuntu, Apache2, MySQL and PHP) is used for my web server. Initially every thing worked perfectly. But at a point of time, initial request to index.php is shown in 2 to 3 minutes, even request to index.html is shown in seconds. Request to other pages from the initial page index.php is shown normally and quickly in seconds. Even weirder is the ip address of that Aqua Data Studio connected to the MySQL database is changed to an ip other than the one entered in the setting when you try to connect to the database. I thought that the point of time the change happened could be of unsuccessfully installing sendmail, but not sure.

What is the problem of the very slow initial request? How to solve the problem? I try to uninstall sendmail but do not help. I check the server which is not busy at all: most time is idle.

Thanks in advance,

---

### Post by tgalati4 on 2013-06-13
Look in /var/log and /var/log/apache for clues.  Are you using fastCGI?  PHP code requires some interpretation before it is served as a page.  Also, queries to mysql can take some time to populate fields in the page.  There are tutorials on the web for improving PHP and mysql speed.  Have you set enough RAM in php.ini?

---

### Post by greatlakes on 2013-06-13
From the following, you can see memory is not an issue. Before install sendmail, initial request was fine. Even now pages after index.php are fine with more intensive SQLs. FastCGI is not used, I guess. Check both /var/log and /var/log/Apache2, nothing is suspected.

procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free    buff      cache   si   so    bi    bo   in   cs us sy id wa
 1  0      0 1267192 152428 463768    0    0    14    21   19   49  1  0 98  1
 0  0      0 1267432 152444 463764    0    0     0    18   24   58  0  0 97  2
 0  0      0 1267432 152452 463764    0    0     0    22   18   44  0  0 99  1
 0  0      0 1267432 152452 463764    0    0     0     0   15   42  0  0 100  0

Thanks,

---

### Post by elnur on 2013-11-15
Sendmail has problems with one-part domains like localhost. Change your localhost to localhost.localdomain and it should fix it.

---

### Post by SeijiSensei on 2013-11-15
I've never seen any interaction between sendmail and Apache/PHP/SQL.  I'm more concerned about that IP address that somehow changed without your knowledge.  Installing sendmail alone would not do that.

Have you tried connecting to the MySQL database from the command prompt with the mysql client?  If the web server and MySQL are on the same machine, they should be communicating either via sockets or through the localhost (127.0.0.1) interface.  If they are running on separate machines, I'd take a look at network connectivity. 

Another possibility is a DNS failure.  Are the PHP applications using hostnames in the mysql_connect() request or IP addresses?  If you are using hostnames, create corresponding entries in /etc/hosts so that a DNS lookup is not required to connect.

---

### Post by SeijiSensei on 2013-11-15
I just realized this thread is five months old.

---

