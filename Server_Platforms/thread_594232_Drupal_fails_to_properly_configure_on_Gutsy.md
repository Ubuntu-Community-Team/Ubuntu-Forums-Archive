---
title: "Drupal fails to properly configure on Gutsy"
date: 2007-10-27
forum: Server Platforms
---

### Post by odubtaig on 2007-10-27
Having a problem with the Drupal install on Gutsy/7.10 Desktop.

It installs without any error messages, however there seems to be several things left undone:[LIST]
[*]Apache is not configured to point to [font=courier new][color=darkgreen]/usr/share/drupal5[/color][/font], I had to change the WebDocuments variable by editing [font=courier new][color=darkgreen]/etc/apache2/sites-available/default[/color][/font] manually despite making sure the 'configure apache2' box was ticked on install
[*]No tables are created in the MySQL 'drupal5' database, I've checked this with a [font=courier new][color=darkgreen]mysql -u root -p drupal5[/color][/font] and [font=courier new][color=darkgreen]show tables;[/color][/font]
[/LIST]A further error message implies that more is missing:

**Fatal error:** Call to undefined function block_list() in /usr/share/drupal5/includes/theme.inc on line 1018

So, I've got a load of missing tables errors (OK 'warnings'), the inevitable slew of complaints that cookies, headers modifications, etc can't be set because the header has already been sent (with the error messages) and a missing block_list()

All I did was load index.php

Unless I've done something drastically stupid/wrong, is there a good place to present this as a bug?

---

### Post by conjur3r on 2007-10-28
Hmm.  I think you've left a step or two.  Did you try the install.php file?  Point to it from your browser to see if that starts the installation process.  It should allow you to configure drupal as well as install the database tables and populate it with data.

I can't speak for what the package does as I haven't used it but I have installed drupal before.  It just seems like you haven't ran its installation process.

---

### Post by odubtaig on 2007-10-28
Good call!

I was under the impression the config settings set up by the .deb installation would have taken care of that bit it only seems to half configure it for whatever reason.

Thanks :KS

---

### Post by copilot on 2007-12-17
When I point my browser at the install.php file it only gives me the option to download the file to my local machine.

---

