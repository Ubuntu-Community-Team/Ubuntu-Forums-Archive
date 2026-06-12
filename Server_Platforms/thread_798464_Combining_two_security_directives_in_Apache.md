---
title: "Combining two security directives in Apache"
date: 2008-05-18
forum: Server Platforms
---

### Post by woland on 2008-05-18
Hi!

I want to secure a directory in Apache in the following manner:
I want password and username to be required, except for users accessing from the company's IP address.

Is it possible to combine two security directives for a directory and if so, how do I do it?

Thanks in advance.

---

### Post by solcott on 2008-05-18
This is sort of a hackjob-ish way of accomplishing this, but this should work.

The paths here are examples, just to demonstrate the theory.

Put your content someplace like:
[FONT="Courier New"]/var/www/somehost/thecontent[/FONT]

Then, symlink something like
[FONT="Courier New"]/var/www/somehost/internalaccess/content[/FONT] to [FONT="Courier New"]/var/www/somehost/thecontent[/FONT]
and[FONT="Courier New"]
/var/www/somehost/externalaccess/content[/FONT] to [FONT="Courier New"]/var/www/somehost/thecontent[/FONT]

Set up virtual hosts to get their content from the external and internal symlinks [FONT="Courier New"]/var/www/somehost/internalaccess/[/FONT] and [FONT="Courier New"]/var/www/somehost/externalaccess/[/FONT] and then .htaccess the internal one to only allow from internal IP's, and the external vhost to require a password.

---

