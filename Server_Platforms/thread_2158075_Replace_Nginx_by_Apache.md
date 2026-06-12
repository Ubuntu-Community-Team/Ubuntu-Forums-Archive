---
title: "Replace Nginx by Apache"
date: 2013-06-27
forum: Server Platforms
---

### Post by tiagoev on 2013-06-27
[COLOR=#000000][FONT=verdana]Hello to all.[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]I have a VPS with Ubuntu 04.12 LTS and ISPConfig web server nginx. I would like to change the nginx by apache. I can only uninstall and install nginx apache and everything will be working? Directories of my websites will continue in the same place? Or do I have to do some manual configuration?[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]I appreciate the help.[/FONT][/COLOR]

---

### Post by CharlesA on 2013-06-27
You will have to configure Apache to serve the files from wherever they were being served by Nginx.

---

### Post by tiagoev on 2013-06-27
Then it will be only the configuration files location is this? Not have to change anything in ISPConfig?


thanks

---

### Post by CharlesA on 2013-06-27
I have no idea. ISPConfig might allow Apache be to configured, but I haven't used it.

---

### Post by tiagoev on 2013-06-27
I'm looking for it but can not find anything about this exchange. I'm almost configuring my VPS from scratch to put apache.

---

### Post by CharlesA on 2013-06-27
In that case, the config files for Apache would be in /etc/apache2/sites-available/

Is there a reason you are switching to Apache from Nginx ?

---

### Post by tiagoev on 2013-06-27
I have a shop on opencart and always giving this error URL friendly because nginx does not accept. Htaccess, even converting. Htaccess to nginx, is always giving error paginão of searches.

---

### Post by CharlesA on 2013-06-27
I see. In that case, you should be able to port things over to Apache, but I would do it on a test machine before even touching the production server.

---

### Post by tiagoev on 2013-06-27
I'm installing Ubuntu server on a VM, and will configure the server and do the procedure in the VM first, let's see if it will be fine.

---

