---
title: "Blank php in firefox"
date: 2011-10-20
forum: Server Platforms
---

### Post by aiyori87 on 2011-10-20
Hi Guys,

I am new to ubuntu and i have set- up apache2 and php package according. I created a test.php and put it in the /var/www with the content of <?php phpinfo(); ?/>.

When i type in the link into the my firefox browser "http://192.168.1.XX/test.php", it gives me a blank page.

Can anyone help me with this?

I can view index.html in the browser.

Thanks

---

### Post by Ryan Dwyer on 2011-10-20
Make sure libapache2-mod-php5 is installed. You might need to restart Apache afterwards.

Also, the PHP closing tag should be ?> but this is not relevant to your problem.

---

### Post by shubham1 on 2011-10-20
> **Ryan Dwyer said:**
> Make sure libapache2-mod-php5 is installed. You might need to restart Apache afterwards.

Also, the PHP closing tag should be ?> but this is not relevant to your problem.
it might be rellvent to his problem try corecting the tag
try using any other browser

---

