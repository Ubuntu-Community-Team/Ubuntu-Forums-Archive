---
title: "Sites-available ?"
date: 2013-03-01
forum: Server Platforms
---

### Post by MocroNL on 2013-03-01
Hello Ubuntu guru's.

Configuring a site to shorten the URL is not working as it should.
I'am trying to add smokeping to the sites available and then activate it with a2ensite Smokeping.
After that I reload Apache2 and try to reach the site(smokeping/) but it does not work.

Config:
<VirtualHost *:80>
        ServerAdmin [EMAIL="support@abc.nl"]support@abc.nl[/EMAIL]
        Servername smokeping.abc.nl
        ServerAlias smokeping smokeping.abc.local
        Documentroot /usr/share/smokeping/www
        Redirect [http://smokeping.abc.nl]("http://smokeping.tallgrass.nl") [http://smokeping.abc.nl/smokeping]("http://smokeping.tallgrass.nl/smokeping")
</VirtualHost>

Iam not sure about the Document root. Is there a specific file in the Document root so I can identify the folder as Document root?
And I have been looking for a index.php index.html etc... But couldn't find any.

Thanks in advance!

---

### Post by ranger12 on 2013-03-01
Try this tutorial and see if this doesn't work:

[https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts](https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts)

I did not try it myself so I have no idea if this will work or not.

---

### Post by Rakeshvijayan on 2013-03-02
> **ranger12 said:**
> Try this tutorial and see if this doesn't work:

[https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts](https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts)

I did not try it myself so I have no idea if this will work or not.

You pointing good answer to him I followed this one when i start to  learn virtual host  , But understand that I need to learn more about  this  , I have question to you  friend[**[COLOR=#000000] MocroNL[/COLOR]**]("http://ubuntuforums.org/member.php?u=1722238")  why the "redirect" is using on virtual host file

---

