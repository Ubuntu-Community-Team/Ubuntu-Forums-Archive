---
title: "Ngninx + Flask + server blocks?"
date: 2017-05-04
forum: Server Platforms
---

### Post by mastahbrood on 2017-05-04
Greetings to all,

Hope I will make myself clear since my knowledge is slim when it comes to Linux and terminology in general.
I have successfully configured Ubuntu 16.04 that is running NGINX, Flask and uwsgi with help from a kind person.
Problem is now that I will be running around 10 sites all on flask on same server meaning multiple nginx server blocks.

However, to configure another block I need to create a new user and set up everything again for each site.
Can I use something else? Like Gunicorn or Emperor to create new sockets on the fly?

I have followed this tutorial [https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-uwsgi-and-nginx-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-uwsgi-and-nginx-on-ubuntu-16-04) and it works. BUT I scratch my head how to achive multiple server blocks with at least pain as possible.

Cheers to all and long live open source and  kind people!!!

---

### Post by TheFu on 2017-05-04
Put each nginx "server" into a different file in the sites-available/ directory.  Create symbolic links to those files in the sites-enabled/ directory when/if you want them on and reload nginx.

Stay patched. Keep all the libraries updated used by your webapps and watch for problems in the news and logs related to all the tools used.  Proper maintenance for custom code isn't just apt update/upgrade. Wish it was, but it isn't.  

I do perl WSGI webapps and constantly need to update the underlying modules to stay secure. Every language has the same issues.

---

