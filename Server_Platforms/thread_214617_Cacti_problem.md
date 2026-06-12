---
title: "Cacti problem"
date: 2006-07-12
forum: Server Platforms
---

### Post by Linus Torvalds on 2006-07-12
Well Thanks to the help here I got Cacti installed :D  and I'm trying to add my Linksys router to "Devices" but when I click "go" in the web ui after entering my device it complains:
Undefined index: host_status in /usr/share/cacti/site/host.php on line 730:confused: 

I checked that line of code it reads: if ($_SESSION["sess_host_status"] != $_REQUEST["host_status"]) {

What am I doing wrong?

---

