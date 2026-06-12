---
title: "12,04 MySQL PHP LOAD DATA LOCAL INFILE problem"
date: 2012-05-01
forum: Server Platforms
---

### Post by Gohtar on 2012-05-01
I have spent the last 2+ hours trying to figure this out...

I am testing my current PHP website that is running fine on an 9.04 server on the new 12.04 server.

I have hit a problem where my data import scripts no longer work. 
I get the error: 1148 Error Message: The used command is not allowed with this MySQL version

I am trying to execute a LOAD DATA LOCAL INFILE query from a PHP CLI script, using a MySQLi connection.

I have done the following:
- Added local-infile=1 to the my.cnf
- Added --local-infile=1 to /etc/init/mysql.conf on the exec line
- Added local-infile=1 in the php.ini under the [MySQLi] in both the apache2 and cli folders
- Rebooted the server

I am able to run the command just fine using the mysql command line client on the server.

My files that I try to import are located in a CIFS mount on the server with 777 permissions.

I have tried to drop the LOCAL keyword and I get a File not found error. Error Number 29 Errcode: 13

So if anyone could please help me clear up one of the 2 issues I would appreciate it.

Thanks,

---

### Post by Franxois on 2012-05-04
Hi,

I'm not any help but I have the same issue here.

I would like to use LOAD DATA LOCAL INFILE with php & apache. I already had the option "mysql.allow_local_infile = On" in the php.ini file. I have the "The used command is not allowed with this MySQL version" error.

Does anyone have an answer ?

Thx

---

### Post by hcch on 2012-05-14
I've found out that the mysql package is compiled without the " enable-local-infile " option. Even enabling in the my.cnf the functionality is not present on the binaries.
So I think we should re-compile it or waiting for a package with tath option enabled.

---

### Post by garsax on 2012-05-24
I think I found a solution. Try this:

$link = mysqli_init();
mysqli_options($link, MYSQLI_OPT_LOCAL_INFILE, true);
mysqli_real_connect($link, DB_HOST, DB_USER, DB_PASS, DB_NAME);

Now you're allowed to use LOAD DATA LOCAL... :-)))

---

