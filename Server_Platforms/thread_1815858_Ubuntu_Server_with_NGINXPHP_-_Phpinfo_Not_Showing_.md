---
title: "Ubuntu Server with NGINX/PHP - Phpinfo Not Showing Info.."
date: 2011-08-01
forum: Server Platforms
---

### Post by Farrawr on 2011-08-01
I've tried everything suggested to me by other people. I'm running NGINX with Php5/php5-fpm, both are started processes. I've edited the NGINX server configuration file to allow php to be used, and I've updated my php5-cgi as well. 

My server configuration file can be found here: [http://pastebin.com/xPQDtfkQ](http://pastebin.com/xPQDtfkQ)
And the blank page can be found here: [www.fagclan.com](www.fagclan.com)

While it SHOULD be showing phpinfo via <?php phpinfo(); ?>, it's just showing a blank page. I've chown'd the correct folders, and all other errors (Originally it was just showing the php code, but I uncommented something I left commented and it's now just showing a blank page), and I have no idea what to do. I'm completely lost as to what I could be doing wrong.

---

### Post by Farrawr on 2011-08-01
Bump, I still need help with this.

---

### Post by Wim Sturkenboom on 2011-08-02
Not at all familiar with nginx, but the first thing I would check is the log files (of the webserver?)

---

### Post by Farrawr on 2011-08-02
> **Wim Sturkenboom said:**
> Not at all familiar with nginx, but the first thing I would check is the log files (of the webserver?)

Already checked errors.log in the nginx dir, fixed two problems but they were not related to PHP.

---

### Post by Farrawr on 2011-08-02
Apparently I'm the first person to ever have a PHP problem?

---

