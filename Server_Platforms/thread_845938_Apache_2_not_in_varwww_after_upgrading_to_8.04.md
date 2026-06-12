---
title: "Apache 2 not in var/www after upgrading to 8.04"
date: 2008-07-01
forum: Server Platforms
---

### Post by danosaka on 2008-07-01
After the Upgrade, Apache 2 is  **not in var/www** anymore... seams to work, but it does not list PhpMyAdmin, Drupal or MediaWiki. I can run them through [http://localhost/Drupal](http://localhost/Drupal) for example when I am online. But off line nothing works properly. How can I get apache back to var/www? Sorry for the newbie question.

---

### Post by windependence on 2008-07-01
I don't quite understand what you are asking here. Do you mean you can access the site from outside your network but not within it? Check your document root settings in Apache. The new installation may have overwritten your config files.


-Tim

---

### Post by danosaka on 2008-07-02
What do I have to check for in document root settings in Apache? And how can I do it?

Before the upgrade, when I accessed apache2 through Firefox ([http://localhost](http://localhost)) It listed drupal, mediawiki and phpmyadmin.
Now it does not list these, all it shows is the default message "it works".
Before, there was an apache2 file in the /var/www, now it isn't there anymore.

When I do the same thing off line nothing works, I get this message from Firefox: "Firefox is currently in off line mode and can't browse the Web." but this is the server!!! This is the machine where everything is running.

---

### Post by windependence on 2008-07-02
I'm sorry to tell you this but this is the way it's SUPPOSED to work. If you just want to see a directory listing, go into /var/www and remove index.html.

-Tim

---

### Post by danosaka on 2008-07-02
Tim, thank you. I all worked perfectly now. I went into /var/www and removed index.html. Then put the settings on Firefox to "work off line", and it worked. Sorry... I am a real newbie!!!

Thank you :)

---

