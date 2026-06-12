---
title: "Make sense of piwik error on 14.04 with Apache2"
date: 2017-06-03
forum: Server Platforms
---

### Post by Drone4four on 2017-06-03
I reconfigured my Apache web server and vhosts last night and piwik is no longer working.  I started fresh with piwik by re-downloading the source into my public_html directory on my remotehost and extracting the zip file.  When I navigate to my piwik landing page in my browser, instead of getting the piwik landing page, I get [this]("https://gist.github.com/Angeles4four/219577b19c9c88c1f66da3a74ad4e8f0") output. Since I don&#8217;t understand php, does anyone know what is piwik could be trying to tell me here?

I tried Googling some of the strings in that traceback, such as: 
> require_once PIWIK_INCLUDE_PATH . /core/dispatch.php
but I couldn&#8217;t makes sense of most of the search results.

I also tried asking in #piwik on FreeNode last night, but that channel is kinda inactive.

Thanks for your attention.

---

### Post by Drone4four on 2017-06-13
I discovered the problem was a misconfigured php.  Turns out instead of executing the php script, Apache was serving piwik to the browser in plain text.  The MySQL password was inadvertently exposed in one of my configuration files. =/ Good thing the Apache web server was stopped for most of the past few weeks. I promptly changed the MySQL password and then uninstalled it.  I will start fresh with piwik soon.  But first I need resolve some issues surrounding my vhosts.

---

