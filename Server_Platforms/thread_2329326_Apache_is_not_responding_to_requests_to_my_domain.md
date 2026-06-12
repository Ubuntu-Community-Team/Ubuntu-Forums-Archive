---
title: "Apache is not responding to requests to my domain"
date: 2016-06-30
forum: Server Platforms
---

### Post by mohammadbagheri2010 on 2016-06-30
Hi.
I installed LAMP on my laptop using this command:
```
sudo apt-get install lamp-server^
```
It's perfectly installed.
I set the basic configurations using this link
 [https://www.digitalocean.com/community/tutorials/how-to-configure-the-apache-web-server-on-an-ubuntu-or-debian-vps](https://www.digitalocean.com/community/tutorials/how-to-configure-the-apache-web-server-on-an-ubuntu-or-debian-vps)
For those who don't have enough time to check it out I did the following :
1. added example.com.conf to /etc/apache2/sites-available/
2. in example.com.conf i have  :  

                                              <VirtualHost *:80>
   ServerAdmin [EMAIL="admin@example.com"]admin@example.com[/EMAIL]
   ServerName example.com
   ServerAlias [www.example.com]("http://www.example.com")
   DocumentRoot /var/www/example.com/public_html
</VirtualHost>

3.I have an index.html in /var/www/example.com/public_html/

So i have this example.com domain and when i try browsing it from my own browser it takes forever and displays nothing but an error finally.
I'm really frustrated now reading all these articles about apache and stuff.
Please please please help me out.

---

### Post by howefield on 2016-06-30
Thread moved to "*Server Platforms*" forum.

---

### Post by spjackson on 2016-06-30
Welcome to the forums.
> **mohammadbagheri2010 said:**
> Hi.
I installed LAMP on my laptop using this command:
```
sudo apt-get install lamp-server^
```
It's perfectly installed.
I set the basic configurations using this link
 [https://www.digitalocean.com/community/tutorials/how-to-configure-the-apache-web-server-on-an-ubuntu-or-debian-vps](https://www.digitalocean.com/community/tutorials/how-to-configure-the-apache-web-server-on-an-ubuntu-or-debian-vps)
For those who don't have enough time to check it out I did the following :
1. added example.com.conf to /etc/apache2/sites-available/

Is it also linked in sites-enabled?
> 
So i have this example.com domain and when i try browsing it from my own browser it takes forever and displays nothing but an error finally.

And what is the error? It sounds more like a DNS issue than Apache configuration, but without the error message, that is just a guess.

---

### Post by Graham_Willis on 2016-07-01
mohammadbagheri2010, please try to do the following: on the machine on which LAMP is installed open the file /etc/hosts in the editor of your choice and add the following lines:

```

127.0.0.1 example.com
127.0.0.1 www.example.com

```

Then: 

```

apt-get install lynx

```

lynx 127.0.0.1

Then exit it (I believe it is possible with Ctrl-C, I don't remember because I don't use it much) and

```

lynx example.com

```

And then tell us about the results, chances are that we'll be able to help. It seems that the domain you're trying to load in your browser is just not delegated to your server.

---

### Post by Habitual on 2016-07-02
> **mohammadbagheri2010 said:**
> 
1. added example.com.conf to /etc/apache2/sites-available/

You didn't say, so I'll bet you forgot to
```
sudo a2ensite example && sudo service apache2 reload

```

Please let us know,
Have a Great Day!

---

### Post by mohammadbagheri2010 on 2016-07-02
[**[COLOR=#000000]@Graham_Willis[/COLOR]**]("http://ubuntuforums.org/member.php?u=2026579")
Well I thought it's working till I realized that it's only working on my own laptop and not on any other device.

Is it possible that my hostname(domain) is not properly connected to my IP ?
I haven't set any configuration on apache2.conf file.Do i need to?

> **spjackson said:**
>   Welcome to the forums.

Is it also linked in sites-enabled? 

I actually don't know what you mean by "link" but i used ```
a2ensite example.com.conf & service apache2 restart
``` and there is this example.com.conf in sites-enabled directory.

> **spjackson said:**
>  And what is the error? It sounds more like a DNS issue than Apache configuration, but without the error message, that is just a guess.

The connection to the server was reset while the page was loading.

    The site could be temporarily unavailable or too busy. Try again in a few moments.
    If you are unable to load any pages, check your computer's network connection.
    If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the Web.




@[**[COLOR=#000000]Habitual[/COLOR]**]("http://ubuntuforums.org/member.php?u=504341")
Yes i did so but no results ! :(


Thanks for your help.

---

### Post by Graham_Willis on 2016-07-02
[QUOTE="mohammadbagheri2010"]Well I thought it's working till I realized that it's only working on my own laptop and not on any other device.[/QUOTE]

Do I understand it correctly that you put in your hosts file the line that I wrote earlier and you were able to load the page from the laptop? Please also tell us if LAMP is installed on the same machine on which you opened the domain example.com .

---

### Post by mohammadbagheri2010 on 2016-07-04
> **Graham_Willis said:**
> Do I understand it correctly that you put in your hosts file the line that I wrote earlier and you were able to load the page from the laptop? Please also tell us if LAMP is installed on the same machine on which you opened the domain example.com .
Yes I added what you wrote earlier and replaced example.com with own domain name and I could browse it with only the same laptop that LAMP is installed on but not from the outside world.
FYI, I want to have my server on my own laptop! There is no VPS and stuff...

Thanks for your help buddy.

---

### Post by darkod on 2016-07-04
Setting up web server at home is not so simple, especially if you don't have static public IP. And many internet providers block certain ports on your connection to prevent people running servers at home.

Also, which steps did you take to make sure the site can be browsed from outside world? Do you have A record set in the DNS for your domain? Pointing to your router public IP?

And set up port forwarding on your router to pass the traffic to your laptop?

---

### Post by Graham_Willis on 2016-07-05
[QUOTE="mohammadbagheri2010"]Yes I added what you wrote earlier and replaced example.com with own  domain name and I could browse it with only the same laptop that LAMP is  installed on but not from the outside world.
FYI, I want to have my server on my own laptop! There is no VPS and stuff...[/QUOTE]

By editing /etc/hosts file you told your computer (but only it) that if you make requests for this domain it should be loaded from the IP that you specified. **127.0.0.1 **is by no means your public IP address, but just a sort of notational convention which means "this local computer". So when you loaded the page from 127.0.0.1 the traffic didn't even go through the Internet. You'd be able to load this page with this configuration even with the Internet cut off.

Now, setting up a server at home is indeed a bit complicated, but if your provider allows to do that it should be feasible.

You should:

1. unblock (perhaps redirect) port 80 on your router. You will have to ask your internet provider for the details. If your provider doesn't make it possible, you won't be able to set up a public server, at least not easy.
2. establish what is public IP of your laptop (a lot of services to do that on the Internet) and if it is static. If it isn't, there is an additional difficulty. You will then probably have to think about DynDNS and redirection.
3. Go to the DNS zone of your domain (ask your registrar for details), delete the records like:

domain.com. A aa.bb.cc.dd
www A aa.bb.cc.dd

and add 

domain.com. A ip_of_your_laptop
www A ip_of_your_laptop
 
But be careful not to miss the trailing dot in **domain.com.  **. Otherwise it won't work
4. You will have wait a bit for these changes to propagate worldwide, but if everything is done correctly after some hours you should see the results. Well, you can check if your delegated your domain properly even earlier (but results still don't have to take effect immediately) by issuing the following command in  command line:

dig @registar_nameserver domain.com
dig @registar_nameserver [www.domain.com]("http://www.domain.com")

If you don't know what registar_nameserver is (in fact are as they should be at least two) just ask the registrar of your domain (or search in his docs).
The first command should show, among other lines, the line  **domain.com. A ip_of_your_laptop **. The second should show the line **[www.domain.com]("http://www.domain.com"). A ip_of_your_laptop **.

---

### Post by mohammadbagheri2010 on 2016-07-05
> **darkod said:**
> Setting up web server at home is not so simple, especially if you don't have static public IP. And many internet providers block certain ports on your connection to prevent people running servers at home.

Also, which steps did you take to make sure the site can be browsed from outside world?

I asked my friend to browse to my domain name.

> **darkod said:**
> 
Do you have A record set in the DNS for your domain? Pointing to your router public IP? 
I don't understand what does that mean :confused:

> **darkod said:**
> 
And set up port forwarding on your router to pass the traffic to your laptop?
[/QUOTE]
I'm not sure if I did that!
Does that mean that I needed to configure my router(modem actually) settings?

---

