---
title: "problems in getting server setup again"
date: 2013-10-30
forum: Server Platforms
---

### Post by micahpage on 2013-10-30
**problem:**
website not responding/displaying

**question:**
Is there anything i missed in the process of seting up apache/ubuntu server?

**history:**
I had my server all setup for the past year+. Then today, i decided to upgrade my server to a newer tower. In doing this i used a freshly downloaded ubuntu server 12.04.3. This is the process i did:
1) setup SSH (in which works fine)
2) updated/installed repos/libs
3) copied over my old /var/www to my new server
4) copied over my old defualt config file to /etc/apache2/sites-available/default
5) copied over my error pages to /etc/apache2/conf.d/localized-error-pages
6) changed owner of www
```
  107  sudo chown -R www-data:www-data /var/www
  108  sudo adduser micahpage www-data
  109  sudo chmod -R g+rw /var/www

```

Looking through the setup install, i dont see anything i forgot, but obviously i must of missed something as my website does not pop up
[www.metulburr.com]("http://www.metulburr.com")
Now coming up with this problem i wished i just used clonezilla and copied over everything from the old hard drive. I would, except i am prolly really close to one config line wrong or something. I have been coming up now on 24 hours with my site down, working on this trying to troubleshoot it. 

the error log:
```
micahpage@server:~$ tail -f /var/log/apache2/error.log
[Wed Oct 30 20:45:00 2013] [error] [client 5.10.83.36] (13)Permission denied: access to /forum/awards.php denied
[Wed Oct 30 20:45:30 2013] [error] [client 5.10.83.94] (13)Permission denied: access to /forum/search.php denied
[Wed Oct 30 20:46:47 2013] [error] [client 66.249.74.171] (13)Permission denied: access to /forum/awards.php denied
[Wed Oct 30 20:47:18 2013] [error] [client 5.10.83.17] (13)Permission denied: access to /forum/member.php denied
[Wed Oct 30 20:48:44 2013] [error] [client 69.205.234.41] script not found or unable to stat: /usr/lib/cgi-bin/client_ip.py, referer: http://www.metulburr.com/
[Wed Oct 30 20:49:01 2013] [error] [client 69.205.234.41] script not found or unable to stat: /usr/lib/cgi-bin/wedding_rsvp.py, referer: http://www.metulburr.com/wedding.html
[Wed Oct 30 20:49:03 2013] [error] [client 69.205.234.41] script not found or unable to stat: /usr/lib/cgi-bin/weddingpics.py, referer: http://www.metulburr.com/wedding.html
[Wed Oct 30 20:49:05 2013] [error] [client 69.205.234.41] script not found or unable to stat: /usr/lib/cgi-bin/wedding_rsvp_signup.py, referer: http://www.metulburr.com/wedding.html
[Wed Oct 30 20:54:02 2013] [error] [client 69.205.234.41] script not found or unable to stat: /usr/lib/cgi-bin/client_ip.py, referer: http://www.metulburr.com/
[Wed Oct 30 20:55:52 2013] [notice] caught SIGTERM, shutting down


```
I think the errors are unrelated as its just my cgi scripts and someone trying to jump on my forum. At one point i thought i had it working, but the cgi scripts were not working, but i think i was looking at localhost at that point. I dont really remember the day just blurred together after dealiong with it all day. 

Thanks in advance for any help at all,
greatly appreciated


EDIT:
OK i am stupid. i forgot to restart apache after modifying the config file
```
sudo /etc/init.d/apache2 restart
```

However i am stilll not sure why my cgi scripts are causing internal server errors

---

### Post by SeijiSensei on 2013-11-01
Have you considered using [mod_python](http://modpython.org/) to run those scripts rather than CGI?

---

