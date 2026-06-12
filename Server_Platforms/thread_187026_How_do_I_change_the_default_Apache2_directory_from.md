---
title: "How do I change the default Apache2 directory from /var/www?"
date: 2006-06-02
forum: Server Platforms
---

### Post by brickbat on 2006-06-02
Hi, In the book I have it says to modify httpd.conf but this file is a dummy.

Also, if I want to develop multiple websites at the same time, how do I tell Apache2 to associate different addresses with different directories?  Or do I just do that on the remote server via the DNS entry and manually go to the different sites locally?

Finally, which version control system would you recommend for a newbie?  I only have heard of CVS.

---

### Post by Endwin on 2006-06-02
As for apache2 which I think you are using you want to look in endy:/etc/apache2/sites-available

edit default and you can change the document root there. I also think this is where you add in new virtual hosts. However for sub domains or other domains the DNS enteries need to point to your server and then this file handles where those requests go.

Take a look at the documentation for apache 2 here [http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/)

As for version control I am not sure which is the easiest, though I know subversion is popular with some people I know.

---

### Post by brickbat on 2006-06-02
ok. thanks

---

### Post by brickbat on 2006-06-03
So I did it and it works perfectly.  Now I need to learn about virtualhosts.  Thanks.

---

