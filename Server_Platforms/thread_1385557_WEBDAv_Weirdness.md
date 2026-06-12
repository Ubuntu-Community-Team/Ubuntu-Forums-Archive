---
title: "WEBDAv Weirdness"
date: 2010-01-19
forum: Server Platforms
---

### Post by furiousanger on 2010-01-19
Hi All, 

I have a running 8.04 server which, amongst many things, has a webserver running on it in the following location: 

/var/www/furious

Via no-ip, this then serves my external website quite happily. I wanted to have access to a calendar aswell from Sunbird, so enabled the WEBDav mod. 

In the /var/www folder, I created a test folder called davhome as per these instructions [http://www.ubuntugeek.com/howto-setup-a-remote-calendar-using-webdav-with-mozilla-sunbird.html](http://www.ubuntugeek.com/howto-setup-a-remote-calendar-using-webdav-with-mozilla-sunbird.html), and success ! This works quite happily on my internal network, publishing and reading quite happily.

When I tried to re-create this in the /var/www/furious folder however, whilst I can subscribe and read the calendar quite happily from the external website address, I cannot write to it :( To add insult to injury, the same happens when I subscribe to the calendar from my internal network - I get "Internal Server Error 500" :(

Any help would be gratefully received !

---

