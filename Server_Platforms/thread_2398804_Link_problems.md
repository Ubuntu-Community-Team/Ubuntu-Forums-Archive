---
title: "Link problems"
date: 2018-08-17
forum: Server Platforms
---

### Post by zapposhusse2 on 2018-08-17
[COLOR=#141414][FONT=Verdana]Recently I started up a new **Apache server** and migrated all web sites from my old NAS Server.
Everything works fine except one problem I can not find any solution for. I am sure many of you know exactly what is wrong. Please help. Last problem to get it up and running
1. Copied all files to new apache server. Wordpress. Have multiple web sites
2. Exported/imported database. OK
3. Changed the links in “Settings” General (Permalinks OK)
4. Changed all links inside Theme to correspond to new server. All correct
5. Links in database OK since the paths are the same as old server. Fixed IP
6. .htaccess have standard wordpress content[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]7. Chmod /var/www/html to 755[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]8. Configured and activated virtual .conf for all web sites[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]Everything works fine except internal links like “Menu” links. I delete a link and reinstall it – does not help, seems that links to other pages than “Home” do not resolve.
Now I am clueless.[/FONT][/COLOR]

---

### Post by cariboo on 2018-08-17
Moved here, help should be quicker.

---

### Post by LHammonds on 2018-08-17
> **zapposhusse2 said:**
> [COLOR=#141414][FONT=Verdana]Everything works fine except internal links like “Menu” links. I delete a link and reinstall it – does not help, seems that links to other pages than “Home” do not resolve.[/FONT][/COLOR]
This sounds like your DNS or site path does not match.  If it is the exact same DNS but different IP, should not be an issue.  It is a different story if you were switching domain names.

Look at the URL you are using to access the webpage.  Compare that to your "WordPress Address / Site Address (URL)" in settings.

When you hover over a link that is not working, right-click the link and select COPY.  Now paste it into a text document and look at where it is trying to go.

Did your old site expect to be running under a /wordpress-site1/* folder and your new site is configured to run in a different folder?

Examine your Apache configuration for the site definition for "DocumentRoot" and compare that with your old server.  Make sure the physical paths are relatively the same too by looking where the "wp-config.php" file is located on both.

Example:
```
Old server
/var/www/mysite1/wordpress/wp-config.php

New server
/var/www/mysite1/wp-config.php
```

I know this sounds elementary but these are the 1st things I would do to troubleshoot the bad links.

LHammonds

---

