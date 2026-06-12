---
title: "Installing php 4"
date: 2005-03-05
forum: Server Platforms
---

### Post by rozbloke on 2005-03-05
Hi all, very new to Ubuntu.
I have a machine with just ubuntu installed and want to set it up as a server.
Following the Ubuntu guide i got to here
 $ sudo apt-get install php4
$ sudo apt-get install libapache2-mod-php4
$ sudo /etc/init.d/apache2 force-reload
$ sudo gedit /var/www/testphp.php

when i tested i get this message

(gedit:13096): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
/dev/dsp: No such file or directory
looking for type: got text/plain

How do i fix this?
Regards
Rod

---

### Post by alastair on 2005-03-05
Fix what?

/dev/dsp - not relevant to PHP or Apache (I guess a system sound wants to play on open a window?)

looking for type: got text/plain - from gedit?

Did gedit open and let you edit the file "/var/www/testphp.php"?

---

### Post by rozbloke on 2005-03-05
after i sent the last message, had a power cut.
When i got things back all was well.
Sorry for the noise.
Rod

---

### Post by az on 2005-03-05
"had a power cut."

...and now I am bald.


I like bald people.






Just being funny.  No offense.

---

