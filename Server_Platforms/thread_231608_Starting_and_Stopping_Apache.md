---
title: "Starting and Stopping Apache"
date: 2006-08-07
forum: Server Platforms
---

### Post by millerk123 on 2006-08-07
My Apache webserver is serving up pages ok, but httpd-stop, httpd-start yields "command not found" errors. Is there some other command I should be using? Should I be prefacing the comand with some path or something?

The boot-up process seems to start the webserver somehow. I started out with the desktop installation and added mysql and apache with the apt-get install command.

My "Hello World" page is served up across my LAN, no problem so it's running.

Kevin

---

### Post by mithras86 on 2006-08-07
it's running by init, so you have to go into terminal and type to stop:```
sudo /etc/init.d/apache2 stop
```The final word could be stop, start, restart, reload and force-reload.

---

### Post by millerk123 on 2006-08-07
ah- thanks that was it.

Is there a file I can edit to change the init? Reason is I have both Apache and Apache2 now and I would prefer it start Apache2.

Kevin

---

### Post by Glut on 2006-08-07
update-rc.d will change the scripts that are loaded at boot.
To load apache2: update-rc.d apache2 defaults
To stop apache1.3: update-rc.d apache remove

---

