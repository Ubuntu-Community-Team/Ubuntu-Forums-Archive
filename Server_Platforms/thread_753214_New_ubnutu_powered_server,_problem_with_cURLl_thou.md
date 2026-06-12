---
title: "New ubnutu powered server, problem with cURLl though"
date: 2008-04-12
forum: Server Platforms
---

### Post by leewilson78 on 2008-04-12
I am running CubeCart on my Ubuntu powered dedicated server, I ran into problems because it seemed that cURL wasn't installed, I uploaded a php file containing the following:

<?php phpinfo(); ?>

... to my sites public_html directory, just to see if there was any reference to cURL, there wasn't. I then tried to install cURL using the following command:

apt-get install php5-curl

... but got the following message:

php5-curl is already the newest version.

Which sounds like it is already installed, however, I can't seem to see it when calling for server information (via <?php phpinfo(); ?>).

Can anyone help. Should I be seeing cURL in the list?

Appreciate any help.

Thanks
Lee

---

### Post by andguent on 2008-04-13
Try this and let us know how it goes:
[http://ubuntuforums.org/showthread.php?t=491149](http://ubuntuforums.org/showthread.php?t=491149)

---

### Post by leewilson78 on 2008-04-13
Hi andguent, 

Which bit do I need to try, the permissions on the file?

The following file: /etc/php5/cli/php.ini is set at 0664 with the owner set to root and the group set to root.

Thanks
Lee

---

