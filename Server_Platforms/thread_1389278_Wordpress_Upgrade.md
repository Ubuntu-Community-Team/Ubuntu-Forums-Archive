---
title: "Wordpress Upgrade"
date: 2010-01-24
forum: Server Platforms
---

### Post by ravingmad on 2010-01-24
How can I fix security so that a user can upgrade his Wordpress install from his Wordpress Admin interface? If I click "Upgrade automatically" all I get is "Installation Failed" yet this worked perfectly under Windows when I was running all my Wordpress sites there. I've read so many forum posts all over the Internet but nobody can seem to explain where the installation fails and I have no clue where to look in Ubuntu's log to find out what error is being generated so that I can work around it. Manual upgrades on 100+ wordpress sites is simply not an option. It is also nothing to do with the FTP password as I have that hardcoded in the config file and users are able to install plugins and themes perfectly but they cannot upgrade.

Hope someone can give a simple answer and fix to this problem.

Thanks in advance.
:D

[B]UPDATE:

Finally I have solved this, a new addition to a forum topic on Wordpress support forums helped me solve this. The solution is to download the new class-wp-upgrader.php from this link - [http://core.trac.wordpress.org/raw-attachment/ticket/10541/class-wp-upgrader.php]("http://core.trac.wordpress.org/raw-attachment/ticket/10541/class-wp-upgrader.php") and then replace your existing one which is in /wp-admin/includes/ and voila, automatic upgrade works once again. Hope this helps others who are experiencing this problem, this one has been keeping me going for months looking for a solution and after all that it was a bug in the wp-upgrader.  - The entire forum post relating to this can be found [here]("http://wordpress.org/support/topic/296758/page/2?replies=42") [/B]

---

### Post by ICEB3AR on 2010-01-24
I had the issue that it did nothing. It told that it will download the new files and nothing happens. I've read on a blog (only in german: [http://www.buildblog.de/2009/04/07/wordpress-auto-update-wenn-es-mal-nicht-funktioniert/]("http://www.buildblog.de/2009/04/07/wordpress-auto-update-wenn-es-mal-nicht-funktioniert/")) that it should work if your directory where the wordpress is located (and the subdirectories) have your web-user as owner.
**I've not tested this !** I made a fresh install for my one.

Hope this can help you.

---

### Post by ravingmad on 2010-01-24
> **ICEB3AR said:**
> I had the issue that it did nothing. It told that it will download the new files and nothing happens. I've read on a blog (only in german: [http://www.buildblog.de/2009/04/07/wordpress-auto-update-wenn-es-mal-nicht-funktioniert/]("http://www.buildblog.de/2009/04/07/wordpress-auto-update-wenn-es-mal-nicht-funktioniert/")) that it should work if your directory where the wordpress is located (and the subdirectories) have your web-user as owner.
**I've not tested this !** I made a fresh install for my one.

Hope this can help you.

Hi ICEBAR see my update above, I finally got this working !!! YAY !!!:D

---

### Post by etorvinen on 2010-02-18
I just got it to work it seems to be a permission.

you need to chown all his wordpress directory to www-data.

sudo chown -hR www-data /home/username/public_html

when i did this it started working with out patching wordpress.

---

