---
title: "How to Edit the file ports.conf"
date: 2011-07-08
forum: Server Platforms
---

### Post by varunaub on 2011-07-08
I want to edit the file ports.conf to make Apache to listen only to loopback interface as described [https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html) here ,The text extract follows

> The *Listen* directive specifies the port, and optionally the IP address,              Apache2 should listen on. If the IP address is not specified, Apache2              will listen on all IP addresses assigned to the machine it runs on.              The default value for the Listen directive is 80.  Change this to              127.0.0.1:80 to cause Apache2 to listen only on your loopback interface              so that it will not be available to the Internet, to (for example) 81              to change the port that it listens on, or leave it as is for normal              operation.  This directive can be found and changed in its own file,              /etc/apache2/ports.confBut by typing 
[CODE]sudo vi /etc/apache2/ports.conf [/CODE}

and opening the file I am not able to edit the file
   After going to the Listen Directive I am not able to type 127.0..0.1, Since what I type does not appear on the screen, **[COLOR=Black]the Keyboard is not working.[/COLOR]**

How will I be able to edit the ports.conf and other configuration files

---

### Post by An Sanct on 2011-07-08
How about using another editor? Lets say '[Nano]("https://help.ubuntu.com/community/Nano")' or gedit, if you use a visual interface?

PS. here is a short [vi - howto]("http://www.lagmonster.org/docs/vi.html")

---

### Post by doas777 on 2011-07-08
> **An Sanct said:**
> How about using another editor? Lets say '[Nano]("https://help.ubuntu.com/community/Nano")' or gedit, if you use a visual interface?

PS. here is a short [vi - howto]("http://www.lagmonster.org/docs/vi.html")
wow, you just reminded me why I will never ever use vi for anything but the simplest of tasks, and then only under threat of violence.

```
Esc + : h i <letter> 
``` is a ludicrous way to go back one car and add a letter.


@op, I recomend Nano.

---

### Post by An Sanct on 2011-07-08
I used vi on my flashed wifi router :) shortly I found out the bliss of nano ;) vi is hardcore ;)

---

