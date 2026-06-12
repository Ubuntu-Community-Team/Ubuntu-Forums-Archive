---
title: "Multiple apache2"
date: 2009-03-15
forum: Server Platforms
---

### Post by artheus on 2009-03-15
Hey!

Is it possible to have multiple apache2... or to have apache2 listen to multiple ports.. and assigning different '/var/www' directories for the different ports?

Cheers,
Artheus

---

### Post by Vegan on 2009-03-15
You can have apache listed on several ports using the Listen directive. Check you hpptd.conf file for a Listen directive, you should see one for port 80 which is the default for HTTP.

:guitar:

---

### Post by volkswagner on 2009-03-15
Yes add the port to ports.conf.

Then in the vhost file use your ip.add.ress:# to start the file.

You can use your default ip plus the port. like
<VirtualHost *:83> or you can specify your internal ip address like, <VirtualHost 192.168.1.1:83>.

Do not use the same port for more than one host or apache will throw an overlap error.

You will also want to add an entry to /etc/apache2/httpd.conf to tell apache you are using name based virtual hosts.

```
NameVirtualHost *

```

Not sure if you are aware, you can multiple sites using virtual hosts all on port 80.  Also note, the non default port, ie: anything other than port 80 will need to be specified in the url address.

You can find more info on setting up NameVirtualHosts [here]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html"), link provide in the sticky on this forum.

---

### Post by artheus on 2009-03-15
Thanks alot! :D

---

