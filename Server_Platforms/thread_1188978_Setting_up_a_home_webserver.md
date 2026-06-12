---
title: "Setting up a home webserver"
date: 2009-06-16
forum: Server Platforms
---

### Post by Hospadar on 2009-06-16
I'm going to be hosting my personal webpage at home off a little machine I have kicking around and I'm wondering what (if anything) I should be doing to secure it.

The machine that will host my site (which will be public) will be totally separate from my home server, so if it were to become compromised, I'd just wipe it, no biggie.  The only thing it's going to do is host this site (it's a little mini-itx mobo).  The only data to be stored on the webserver will be the webpage itself.

The server is going to be behind a router, and only port 80 will be forwarded to the webserver (there are other port forwards on my router, but they go to my personal data/mythtv server).

Is there anything else I need to be doing to lock down this server?
I'll probably have a cron job running clam av scans at least weekly (it'll have a very small hdd so no issue scanning often).

---

### Post by Vegan on 2009-06-16
You should be fine. When you install the server, choose the LAMP option and all the needed software will be ready to use.

the default /var/www is fine for a personal web page. The default document "it works" simply is a diagnostic page.

If course you can do much more, but this simple approach minimizes complexity.

---

