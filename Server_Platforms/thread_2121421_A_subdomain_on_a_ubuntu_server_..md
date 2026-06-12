---
title: "A subdomain on a ubuntu server ."
date: 2013-03-01
forum: Server Platforms
---

### Post by Raafat1991 on 2013-03-01
Hi...assuming i have a domain (say raafat.org) on a ubntu server with apache how can i get email.raafat.org or math.raafat.org or networking.raafat.org etc...

thank you guys .

---

### Post by lisati on 2013-03-02
Having a subdomain is usually fairly straightforward. On the Ubuntu end, you can use *virtual hosts*, and on your DNS host you add an entry to point the subdomain to your server's public IP address.

Hope this helps get you started, and that this will bump your thread so that someone who knows of a good tutorial can provide it.

---

### Post by Raafat1991 on 2013-03-02
> **lisati said:**
> Having a subdomain is usually fairly straightforward. On the Ubuntu end, you can use *virtual hosts*, and on your DNS host you add an entry to point the subdomain to your server's public IP address.

Hope this helps get you started, and that this will bump your thread so that someone who knows of a good tutorial can provide it.

Hi...more explanation will be better .but as you said .

---

### Post by GordThompson on 2013-03-02
Perhaps more information might be forthcoming if you were a bit more specific about what you want to *do *with those subdomains. As lisati mentioned, the *definition *of those subdomains is controlled by the DNS entries for your domain. If they are all going to reside on the same public IP address then the entries would look something like

raafat.org  A  123.456.78.90
email.raafat.org  CNAME  raafat.org
math.raafat.org  CNAME  raafat.org
...

Once that is done (and has propagated to the other DNS servers around the world) then any traffic sent to the subdomains will be directed to your public IP address. What happens next is up to you.

---

### Post by Raafat1991 on 2013-03-02
> **GordThompson said:**
> Perhaps more information might be forthcoming if you were a bit more specific about what you want to *do *with those subdomains. As lisati mentioned, the *definition *of those subdomains is controlled by the DNS entries for your domain. If they are all going to reside on the same public IP address then the entries would look something like

raafat.org  A  123.456.78.90
email.raafat.org  CNAME  raafat.org
math.raafat.org  CNAME  raafat.org
...

Once that is done (and has propagated to the other DNS servers around the world) then any traffic sent to the subdomains will be directed to your public IP address. What happens next is up to you.

Must i reserver email.raafat.org with all DNS servers around the world so i could use it ? Also with th rest of my entries ?

Look i have (a assumation) raafat.org reserved around the world so that any traffic to raafat.org will be sent to my public ip,i want to create a email server (with IRedMail...someone@raafat.org) and (for that) i will create email.raafat.org .My question is: what are steps for doing that ?


thank you .

---

### Post by GordThompson on 2013-03-03
> **Raafat1991 said:**
> Must i reserver email.raafat.org with all DNS servers around the world so i could use it ? Also with th rest of my entries ?
If you want the name 'email.raafat.org' to be accessible by other machines out on the Internet then a DNS entry must exist for it. You don't have to explicitly "reserve" it with every DNS server in the world; the DNS system will take care of that for you once the entry has been added to the authoritative DNS server for your domain (see below).

> **Raafat1991 said:**
>  Look i have (a assumation) raafat.org reserved around the world so that any traffic to raafat.org will be sent to my public ip,i want to create a email server (with IRedMail...someone@raafat.org) and (for that) i will create email.raafat.org .My question is: what are steps for doing that ?
Your domain, 'raafat.org', has to be registered with an organization that is an accredited [Domain Name Registrar]("http://en.wikipedia.org/wiki/Domain_name_registrar"). That organization will offer some kind of mechanism for updating your DNS entries. Check with them to see how you could get 'email.raafat.org' added to your DNS. (Many organizations like Go Daddy, Dyn Inc., etc. have "self-serve" options that let you log in to their website and change some of your DNS values yourself.)

---

### Post by Raafat1991 on 2013-03-04
> **GordThompson said:**
> 
Your domain, 'raafat.org', has to be registered with an organization that is an accredited [Domain Name Registrar]("http://en.wikipedia.org/wiki/Domain_name_registrar"). That organization will offer some kind of mechanism for updating your DNS entries. Check with them to see how you could get 'email.raafat.org' added to your DNS. (Many organizations like Go Daddy, Dyn Inc., etc. have "self-serve" options that let you log in to their website and change some of your DNS values yourself.)


What about a static IP need i that or a domain name is't enough ?



thank you .

---

### Post by GordThompson on 2013-03-04
> **Raafat1991 said:**
> What about a static IP need i that or a domain name is't enough ?
A static IP address is not absolutely necessary, but it does make things simpler. Running a server on a dynamic IP address requires the use of a Dynamic DNS (DDNS) service to keep your DNS records updated with your current IP address. 

Also, if you are planning on running a mail server then it won't be able to send mail from your dynamic IP address directly to other mail servers because many of them will see that the mail is coming from a dynamic IP block and reject it (they'll assume that it's spam). In addition, you won't have a matching reverse DNS entry and that will further diminish the reputation of your mail server. So instead of sending messages directly you would have to set up your mail server to send all messages through another "legitimate" mail server (acting as a "smarthost" for you).

---

### Post by brent1975 on 2013-03-04
Here is how to set up sub-domains. DNS does play a roll and as the information that has been given to you is real specially with email. You want to know how to setup sub-domains.  Here is a little walk through that I use when I create a subdomain.

Here we go:
sub-domains is a good way to organize your website.  example.com is  what is called the parent domain. You could have many different parts to   your website. For example you could have forums, books, music, really  anything. so instead of having all your components to your website lay  in the same directory /var/www  you could go a step further and organize  it. Here is an example of how you could structure /var/www using  sub-domains
  
 /var/www/example.com   { Main domain }
 /var/www/forums              { forums }
 /var/www/music                {if you have a music site or streaming}
 /var/www/books                { digital books site}
  
  
  
 By using this type of structure to set up sub-domains all your  website components eg: forums, music, books wont have to all be in the  root directory of the website. Do you like [www.example.com/forums?]("http://www.example.com/forums?") or  would you rather see forums.example.com? 
  
 Here is how we accomplish this.
  
 [COLOR=#000000] We need to navigate to [/COLOR]
```
cd /etc/apache2/sites-available/
```

Now we are going to create our sub-domain file.


```
sudo nano forums.example.com
```
We will use a virtual host. Here is what it will look like.
```

<VirtualHost *:80> 
ServerName forums.example.com
 ServerAlias www.forums.example.com
 DocumentRoot /var/www/forums/
     </VirtualHost> 
<Directory /var/www/forums/>
                 Options -Indexes FollowSymLinks MultiViews                 
                AllowOverride All                 
                Order allow,deny                 
                allow from all 
</Directory>

```
Next we will need to enable the site with apache2.
```
sudo a2ensite forums.example.com
```
Now we need to reload apache for the changes to take place.
```
sudo /etc/init.d/apache2 reload
```
Now all you need to do is create a folder in /var/www called forums eg; /var/www/forums
  
 In order for you to be able to access the forums.example.com you will  need to modify DNS and add an A record. You Can go to the registar  where you got the domain and register the sub-domain and point it to  your server, you could use a third party dns such as zoneedit to handle  all your dns needs for your domain 




[COLOR=#000000]
[/COLOR]

---

### Post by Raafat1991 on 2013-03-04
> **brent1975 said:**
> Here is how to set up sub-domains. DNS does play a roll and as the information that has been given to you is real specially with email. You want to know how to setup sub-domains.  Here is a little walk through that I use when I create a subdomain.

Here we go:
sub-domains is a good way to organize your website.  example.com is  what is called the parent domain. You could have many different parts to   your website. For example you could have forums, books, music, really  anything. so instead of having all your components to your website lay  in the same directory /var/www  you could go a step further and organize  it. Here is an example of how you could structure /var/www using  sub-domains
  
 /var/www/example.com   { Main domain }
 /var/www/forums              { forums }
 /var/www/music                {if you have a music site or streaming}
 /var/www/books                { digital books site}
  
  
  
 By using this type of structure to set up sub-domains all your  website components eg: forums, music, books wont have to all be in the  root directory of the website. Do you like [www.example.com/forums?]("http://www.example.com/forums?") or  would you rather see forums.example.com? 
  
 Here is how we accomplish this.
  
 [COLOR=#000000] We need to navigate to [/COLOR]
```
cd /etc/apache2/sites-available/
```

Now we are going to create our sub-domain file.


```
sudo nano forums.example.com
```
We will use a virtual host. Here is what it will look like.
```

<VirtualHost *:80> 
ServerName forums.example.com
 ServerAlias www.forums.example.com
 DocumentRoot /var/www/forums/
     </VirtualHost> 
<Directory /var/www/forums/>
                 Options -Indexes FollowSymLinks MultiViews                 
                AllowOverride All                 
                Order allow,deny                 
                allow from all 
</Directory>

```
Next we will need to enable the site with apache2.
```
sudo a2ensite forums.example.com
```
Now we need to reload apache for the changes to take place.
```
sudo /etc/init.d/apache2 reload
```
Now all you need to do is create a folder in /var/www called forums eg; /var/www/forums
  
 In order for you to be able to access the forums.example.com you will  need to modify DNS and add an A record. You Can go to the registar  where you got the domain and register the sub-domain and point it to  your server, you could use a third party dns such as zoneedit to handle  all your dns needs for your domain 




[COLOR=#000000]
[/COLOR]


Thank you man i have no an idea how can i thank you and every one posted something here...

i think that idea become clear but is there any one have registered with a DNS server (just i want to know those steps) ?


thank you .

---

### Post by Raafat1991 on 2013-03-04
Also i'm planning to do that:one public ip for these:a email server,a web server,a vpn network. i will create a filter so that any a request with 1 port will be redirected to 192.168.1.2 (a web server) and 2 port will be redirectd to 192.168.1.3 (a email server) and 3 port to a vpn server.  (1,2,3 ports just an example hhhh)


Can i get that running ?

---

### Post by GordThompson on 2013-03-04
> **Raafat1991 said:**
> is there any one have registered with a DNS server (just i want to know those steps) ?
Yes, I have my domain registered with Dyn. I went to [http://dyn.com/](http://dyn.com/) and subscribed to their "Domain Registration" and "Dyn Standard DNS" services. I chose Dyn because I knew that I could get Dynamic DNS (DDNS) and just use my dynamic IP address; it was cheaper than paying my ISP for a static IP.

Once I had signed up I could log in to their website and edit my DNS records (see screenshot). I created CNAME aliases for 'www' and 'webmail', and added a TXT record for SPF email validation.

[ATTACH=CONFIG]239769[/ATTACH]

---

### Post by GordThompson on 2013-03-04
> **Raafat1991 said:**
> Also i'm planning to do that:one public ip for these:a email server,a web server,a vpn network. i will create a filter so that any a request with 1 port will be redirected to 192.168.1.2 (a web server) and 2 port will be redirectd to 192.168.1.3 (a email server) and 3 port to a vpn server.  (1,2,3 ports just an example hhhh)


Can i get that running ?
Yes, if you are behind a router that does Port Forwarding (and nowadays even the most inexpensive home WiFi routers do).

---

### Post by Raafat1991 on 2013-03-05
Hi...i saw your image but was small...what about updating your ip how did you do that ? also can you set a port with your ip so that any request to email.raafat.org will be with 1 port automatically ?

---

### Post by GordThompson on 2013-03-05
> **Raafat1991 said:**
> Hi...i saw your image but was small...
Did you try clicking on the thumbnail? That should display a larger image.

> **Raafat1991 said:**
> what about updating your ip how did you do that?
Because I'm using Dynamic DNS (DDNS) I have to run a [DDNS updater]("http://dyn.com/support/clients/") on one of my machines. It checks my current (dynamic) IP address every few minutes and updates my DNS "A" record automatically if necessary.

> **Raafat1991 said:**
> also can you set a port with your ip so that any request to email.raafat.org will be with 1 port automatically ?
No, DNS doesn't work that way. However, if traffic arrives at your public IP address on port 25 then your router will know that it's mail and forward it accordingly (once you have Port Forwarding set up).

---

### Post by Raafat1991 on 2013-03-06
> **GordThompson said:**
> Did you try clicking on the thumbnail?

Yes i did...

So (as mentioned befor) a static ip is better for a email server ,Also with a webserver ?

in general,when must i take a static ip ?


thank you

---

### Post by Raafat1991 on 2013-03-07
Hi....

---

### Post by lisati on 2013-03-07
> **Raafat1991 said:**
> Yes i did...

So (as mentioned befor) a static ip is better for a email server ,Also with a webserver ?

in general,when must i take a static ip ?


thank you

Having a static IP address possibly matters more when you're running an email server, because some email providers block incoming mail from dynamic IP addresses.

---

### Post by Raafat1991 on 2013-03-07
> **lisati said:**
> Having a static IP address possibly matters more when you're running an email server, because some email providers block incoming mail from dynamic IP addresses.

Hi...only with email servsers ?


thank you .

---

### Post by lisati on 2013-03-07
> **Raafat1991 said:**
> Hi...only with email servsers ?


thank you .
As long as your DNS records are pointing to the correct IP address, it shouldn't really matter for people connecting to your server from the outside. The important thing is that your website or email server can be found by those who you might want to connect to your server. Keeping unwanted visitors out is another story......

For email, there is a nuisance factor introduced by malware on infected computers, which commonly connect via dynamic (i.e. *not* static) IP addresses, and some email providers prefer to play it safe.

---

### Post by Raafat1991 on 2013-03-07
> **lisati said:**
> As long as your DNS records are pointing to the correct IP address, it shouldn't really matter for people connecting to your server from the outside. The important thing is that your website or email server can be found by those who you might want to connect to your server. Keeping unwanted visitors out is another story......

For email, there is a nuisance factor introduced by malware on infected computers, which commonly connect via dynamic (i.e. *not* static) IP addresses, and some email providers prefer to play it safe.

thank you man .

---

### Post by Raafat1991 on 2013-03-07
Hi...i think this thread has been solved.....thank you everyone .

---

### Post by Raafat1991 on 2013-03-07
But where is : mark this thread as solved ?

---

