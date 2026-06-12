---
title: "Apache2 second website issue"
date: 2017-04-05
forum: Server Platforms
---

### Post by whizperz on 2017-04-05
Hello everyone!

I got a problem with my Apache2 server and i am hoping that you can help me out and fix this issue of mine!

My os is Ubuntu 16.04 with Apache2 installed, and the problem i am having is that when i add a new website to my /var/www/ folder i cannot access it, it just gives me a 404 error saying that it does not exist

My first website is running great without any problems and that one is installed to /var/www/html.

Basicly i want it to be as the following, when someone enters my domain [www.mydomain.com]("http://www.mydomain.com") i want them to see the site i have in /var/www/html wich they are currently doing.
But! When they enter [www.mydomain.com/phpbb]("http://www.mydomain.com/phpbb") for example i want them to be directed to the second folder i created in the /var/www/ wich is called phpbb for the moment.

I did try to fix this on my own but i cant find any good explainations that i truly understand so is there anyone who can help me out with this?


This is how my virtualhost file is looking at the moment
```
<VirtualHost *:80>    
    ServerAdmin kristofferforsberg@hotmail.com
    ServerName myfirstsite.zapto.org
    ServerAlias www.myfirstsite.zapto.org
    DocumentRoot /var/www/html
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```


And this is how i want my structure to be, and the message i am getting, let me know if there is anything else i need to show you guys.

[IMG]http://i.imgur.com/dSIwRan.png[/IMG]
[IMG]http://i.imgur.com/G1GSPkb.png[/IMG]

---

### Post by darkod on 2017-04-05
If you want to use the same domain with /phpbb at the end, why didnt you put the folder directly into /html? That way it should open without declaring second site because this actually is not a second site.
Also after creating the folder and copying data you have to make sure the permissions are correct.

---

### Post by whizperz on 2017-04-05
Hi! And thanks for the response!

I should have been more clear, i am going to use multiple domains for each site thats why i want to get this to work. and i kinda did get it sorted but now i got another problem..

if i use a proxy i can actually see the second site i created now. but if i try to enter it through my ip "192.168.5.58/phpbb" it just tells me the site still is not to be found? Why is that? so i can enter it thorugh my external dns, but i cannot enter it thorugh my internal IP ?

---

### Post by pqwoerituytrueiwoq on 2017-04-05
1st look in these 2 folders
/etc/apache2/sites-enabled/
/etc/apache2/sites-available/
make a copy of the default named phpbb in the sites-available folder
2ed make a symlink to that in the other folder (../sites-available/phpbb)

change the port number to 82 in this file
and in the default change the port number to 81
modify /etc/apache2/ports.conf to listen on ports 81 and 82 but NOT 80

now install pound
[https://help.ubuntu.com/community/Pound](https://help.ubuntu.com/community/Pound)
you will want a config like this
```

ListenHTTP
    Address 10.0.0.25 # your systems local IP address
    Port    80

    ## allow PUT and DELETE also (by default only GET, POST and HEAD)?:
    xHTTP        0

    # web share
    Service
        HeadRequire "Host: .*domainA.com.*"
        BackEnd
            Address    127.0.0.1
            Port    81
        End
    End
    
    # Desktop Share
    Service
        HeadRequire "Host: .*domainB.com.*"
        BackEnd
            Address    127.0.0.1
            Port    82
        End
    End

    Service #this is what happens when someone connects using your IP address
        BackEnd
            Address    127.0.0.1
            Port    81
        End
    End
End

```

[COLOR=#ff0000]SECURITY NOTE:
Apache will not be able to see the original ip address, all request will appear to be form 127.0.0.1, so don't rely on IP based filters and be sure to disable any 127.0.0.1 only admin tools[/COLOR]

---

### Post by darkod on 2017-04-05
Don't get your point... Even if you use different domains the [www.domain.com](www.domain.com) part is different, right? That is the definition of different domains...

You can have /phpbb folder in each domain root, which will be accessible by [www.domain1.com/phpbb](www.domain1.com/phpbb), [www.domain2.com/phpbb](www.domain2.com/phpbb), etc...

As for your question why it doesn't work by using the IP, I think because the IP is pointing to the default site document root which is /var/www/html. By adding /phpbb on the end you are asking it to look for a folder named phpbb inside that root, which is not there.

---

### Post by SeijiSensei on 2017-04-05
Use an [**Alias**]("https://httpd.apache.org/docs/current/mod/mod_alias.html") directive:
```
Alias /phpbb /var/www/phpbb
```
or just put the directory under /var/www/html.

Alias specifications are useful if you want to point a URI at some location outside the normal web tree.

---

