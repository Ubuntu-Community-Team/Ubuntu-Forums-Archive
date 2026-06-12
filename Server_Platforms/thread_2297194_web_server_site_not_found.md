---
title: "web server site not found"
date: 2015-10-01
forum: Server Platforms
---

### Post by sublevel42 on 2015-10-01
I installed my DDNS system and it is updating my ip. On my ubuntu server if i type in sublevel4.dynu.com/phpinfo.php i get the info page. if I put that in from any other computer i get a 404. I can ftp using [ftp://sublevel4.dynu.com](ftp://sublevel4.dynu.com) but that hits a different server. so i am guessing that there is something wrong :)
What do i need to do to fix this?

---

### Post by SeijiSensei on 2015-10-01
Where is phpinfo.php located?  In /var/www/html or somewhere else?

If you're using 14.04 or later, the default website directory is /var/www/html.  In prior versions it was /var/www.

---

### Post by sublevel42 on 2015-10-02
Yes there is the index.html that apache created and the phpinfo.php. both are in the /var/www/html directory. I have tried to access the site from 3 different networks and 4 different computers and thus far on the computer the server is running on can access it. I even tried using the IP and when i do that i get the same page but the the IP in the address bar and a /UI after it.

---

### Post by SeijiSensei on 2015-10-02
There's more going on here.  Asking for the index.html page redirects to the /UI URI; the standard page doesn't do that.  Any Redirect or Rewrite directives? 

Are you sure your Internet service provider allows servers?  Perhaps they redirect traffic upstream from you.  You wouldn't see that if you try to connect from the local server itself, but you would when connecting from outside.

The Terms of Service for most residential accounts ban servers.  Have you read yours?  This could all be a result of your ISP's policies.

---

### Post by sublevel42 on 2015-10-02
I will double check but i have FTP that is working on the same dynamic domain systems that i have been using for over a week, it doesn't go to the ubuntu box though it goes to another server. however the ubuntu webserver stuff isn't working. Maybe i need to remove it all and start over, not that i want to. There is a breakdown somewhere i am going to have to do some hunting. I hope all the permissions changing and owner changing i did to see if i could fix this doesn't mess everything else up.

---

### Post by sublevel42 on 2015-10-02
i have some more to add...
when i go to the url the error page i get
[h=1]Not Found[/h][COLOR=#000000][FONT=Arial]The requested URL /UI was not found on this server.[/FONT][/COLOR]
[HR][/HR]Apache/2.4.7 (Ubuntu) Server at sublevel4.dynu.com Port 80

[COLOR=#222222][FONT=Verdana]I didn't put /UI at the end of the url and the signature is from my server. so it looks like its getting to the server its just not landing in the right place.

[/FONT][/COLOR]

---

### Post by sublevel42 on 2015-10-05
I was able to get to the webpages and the phpmyadmin on the site from my laptop on my network. But i could not get there from my phone or ipad. all on the same network. I also can't access the site at all from the same laptop on my work network. I have an ftp on another network device that works flawlessly using the same ddns service. I have to port forwards on my router one for web and one for ftp. both are identical settings.

---

