---
title: "Wordpress links (to internal pages) not working, only home page and wp-admin work"
date: 2013-06-20
forum: Server Platforms
---

### Post by arxix on 2013-06-20
Hello everyone and thanks in advance,
I was tasked with building a duplicate webserver to an existing wordpress site build on Ubuntu 12.04 LTS. I spun it up, installed wordpress, copied over the files and restored the DB from new backup. I was very happy when the home page popped up and almost decided it was time to call the ticket solved when I went to the admin portal and that worked just fine as well. All pages and links under the admin portal work, I wasn't until I clicked on a link on that home page and got a "The requested URL /solutions/ was not found on this server." that I realized that something was wrong. I worked on it for hours yesterday to no avail. I took another hour today to troll through google and a few forums and couldn't find anything that worked.

I apologize in advance if there is a thread which explains this exactly and I just couldn't find it. Any help will be appreciated.

-ArXiX

---

### Post by arxix on 2013-06-20
Figured it out!!! I started narrowing it down when I found that everything worked if I used default permalinks, but it failed when I selected anything else. I did some more googleing and found many things that didn't work for me. I had already fixed my .htaccess file. Then I found a page that said to try running the below code and it worked.

had to run:
```
sudo a2enmod rewrite
```

All is now well with the world just in time for lunch!!!!!

---

