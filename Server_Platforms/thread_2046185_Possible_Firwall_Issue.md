---
title: "Possible Firwall Issue?"
date: 2012-08-22
forum: Server Platforms
---

### Post by soundguyfyi on 2012-08-22
I am installing a password manager on an internet server within my office. I have gone through hoops to get it even installed.

Now I am facing an issue that looks like either a port, firewall or secure http issue.

Does this error message look familiar to anyone? I got it when trying to visit my site via Firefox on both the host computer and remote computer

"The connection to 10.10.0.248:80 was interrupted while the page was loading."

Her is the URL: [https://10.10.0.248:80/mrp/login/](https://10.10.0.248:80/mrp/login/) (obviously I know the link wont work for you. Its just for example)

I'm not sure what other info would be helpful so here is some random stuff.

MrP Password Manager by DaleGroup

I have tested the site with the firewall (shorewall) both on and off and had same failure.

Tried to turn off secure http in phpmyadmin within config with same results.

---

### Post by soundguyfyi on 2012-08-22
I was having an issue with my .htaccess files. Change Permissions to execute and that fixed it. Thanks [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195")

---

