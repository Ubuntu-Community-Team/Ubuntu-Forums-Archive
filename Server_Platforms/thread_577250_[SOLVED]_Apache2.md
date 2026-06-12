---
title: "[SOLVED] Apache2"
date: 2007-10-16
forum: Server Platforms
---

### Post by will12 on 2007-10-16
I am very new to the world of web servers, or servers in general. I am trying to set up my apache2 server, and learn php at the same time. I need to know how to save php files in the /var/www file. Every time that I try to save the file in that folder I get a message that says that I don't have permission to save things here.

Anything that you can tell me to help me save my files in that file would be greatly appriciated.

Cheers

---

### Post by conjur3r on 2007-10-16
You will need to allow yourself permissions to write to files within that folder.  Open up a terminal and issue the following command replacing YOUR_USERNAME:

# sudo chown -R YOUR_USERNAME /var/www

---

