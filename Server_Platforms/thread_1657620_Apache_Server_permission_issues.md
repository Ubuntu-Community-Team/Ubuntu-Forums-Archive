---
title: "Apache Server permission issues"
date: 2011-01-01
forum: Server Platforms
---

### Post by vezinadj on 2011-01-01
Keep in mind, I am very new to apache2. I have a local server just so I am able to test my php files. I edited my apache server config so that instead of where I store my files in /var/www/ it is now in a separate location on my drive (Which is tested and working fine if I make a test.php that simply echo's a message). My issue is when i try to make a folder in that same folder location, and instead of using localhost/test.php I used localhost/folder/test.php I get a error 

Forbidden

You don't have permission to access /CE_project/current/caronlayout.php on this server.

Apache/2.2.16 (Ubuntu) Server at localhost Port 80

I have images that are in subfolders to my website, so for them to not be accessible when testing my site, is kind of a big issue. Im sorry if this is a newbi question but I have tried for a little while and am frustrated! Any help would be great!

---

### Post by Calimo on 2011-01-01
Hi,
Have a look to the apache error log (normally in /var/log/apache2/error.log). There will be some hint about the reason of the error: apache couldn't read the file? It was denied by an "order" policy?

Most probably apache can't read the file. You need to set the appropriate properties: it must be readable by user www-data. Either chown the files and folder, or chmod it to the appropriate permissions.

---

### Post by vezinadj on 2011-01-01
Thank you for the quick reply, I am not to sure how to chmod the whole folder? I would like access to the whole thing so I can view images linked in my html and php code within subfolders in my server folder. Confusing, I know. Any help with how to start doing this?

---

