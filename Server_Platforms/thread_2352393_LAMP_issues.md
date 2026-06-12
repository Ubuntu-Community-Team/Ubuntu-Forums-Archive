---
title: "LAMP issues?"
date: 2017-02-12
forum: Server Platforms
---

### Post by sacmo on 2017-02-12
Hello guys,

I am a new ubuntu server user, I decided to move to ubuntu at the suggestions of some friends, and I am trying to set up a web-server, now past the initial configuration and all the bla bla bla I managed to go without too much problems, but now I am encountering something rather strange and I would need some ideas as to where the problem might be coming from.

Basically i have the file index.php (which is my main page file) (this file is located into /var/www/html/sitename) and then I have the file fsts.php (which basically is another page of the website) this is also located in /var/www/html/sitename), now when I localhost/sitename/index.php it opens it without a problem, if I go to localhoste/sitename/fsts.php it doesn't open it at all. Also if I navigate from the website to the page fsts.php it sends me to the same blank page.

Before we continue allow me to explain that I checked the code of the file fsts.php multiple times to make sure there isn't a mistake, and there isn't.

Further more the same file works perfectly on a windows wamp installation, any ideas what might it be ? Where should I look or what should I do>

Thank you for your time

Kind regards,
A newbie user

---

### Post by cariboo on 2017-02-12
Check the log files both /var/log/apache2/access.log and /var/log/apache2/error.log

---

### Post by sacmo on 2017-02-12
> **cariboo said:**
> Check the log files both /var/log/apache2/access.log and /var/log/apache2/error.log

Cheers, helping me find out where the error logs are and being able to see them helped me troubleshoot and discover that there was a small path issue in the php (apparently for LAMP the php path connection must be entered a tad differently than how the automated DW does it.

Thanks again for the quick response.

---

