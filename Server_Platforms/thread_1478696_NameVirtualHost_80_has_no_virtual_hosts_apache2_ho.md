---
title: "NameVirtualHost *:80 has no virtual hosts apache2 hosting multiple sites without DNS"
date: 2010-05-10
forum: Server Platforms
---

### Post by tapas_mishra on 2010-05-10
Hi,
I have some problem in apache2 configuration.
 I have two websites on same IP on LAN.i.e. 192.168.1.5
 site1.abc.com
and abc.com
both have different document roots
for abc.com document root 
/var/www/abc
and for site1.abc.com document root
/var/www/site1

 the above sites are on a server which is accessible to me only via SSH.

Now on Lan if I do
    
       [http://192.168.1.5](http://192.168.1.5) 
I get abc.com 
and if I do 
    [http://192.168.1.5/abc](http://192.168.1.5/abc)
 or [http://192.168.1.5/site1](http://192.168.1.5/site1)


 then in both cases I am getting site abc which is alphabetically first vhost (that is also how apache2 serves)
What should I do to be able to access both the websites

following are vhosts in sites-enabled

 for abc /etc/apache2/sites-enabled/abc.com
 ```

  NameVirtualHost *:80
   <VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName abc.com
        ServerAlias www.abc.com
        DocumentRoot /var/www/abc
        <Directory /var/www/abc >
                Options FollowSymLinks
                AllowOverride None
        </Directory>
  
</VirtualHost>
~                 

 
```and for site1.abc.com a separate file in /etc/apache2/sites-enabled/site1.abc.com

 ```

  NameVirtualHost *:80
   <VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName site1.abc.com
        ServerAlias site1.abc.com
        DocumentRoot /var/www/site1
        <Directory /var/www/site1 >
                Options FollowSymLinks
                AllowOverride None
        </Directory>
  
</VirtualHost>
~                 

 
```What should I check in a few blogs I checked they said to mention in /etc/apache2/apache2.conf 
ServerName. 
But in this case what should I put I have two different websites or what other thing I have missed? I do not have access to DNS so that on LAN I can point site1.abc.com and abc.com to same IP 192.168.1.5 which to me seems could resolve the issue.

---

### Post by Ryan Dwyer on 2010-05-10
Yes, you need to access it via the hostname. You can do this without changing DNS settings by adding an entry to /etc/hosts on each client machine.

---

### Post by tapas_mishra on 2010-05-10
Even before you said I did try that and it did not worked.
[http://192.168.1.5](http://192.168.1.5) 
was giving me index page of abc.com how to access different domains in this case from client machine on network.


Ok here  I found some thing that may help this link [http://httpd.apache.org/docs/2.2/vhosts/examples.html](http://httpd.apache.org/docs/2.2/vhosts/examples.html) it says

```

In order to match the     correct virtual host a client must send the correct 
Host:     header. Old HTTP/1.0 clients do not send such a header and Apache  has    
 no clue what vhost the client tried to reach (and serves the request    
 from the primary vhost) 
```That is what is exactly happening.If I type in browser [http://192.168.1.5](http://192.168.1.5) I get abc.com which alphabetically is coming first. 


I used a Firefox plugin [Live HTTP headers ]("https://addons.mozilla.org/en-US/firefox/addon/3829")
to see which header is going to webserver and it came to be HTTP 1.0 to  which the above links says is a problem.I am surprised since I am using mozilla 3.6.3 if this has a problem then which brower does not have or sends correct HTTP :host header.

Or am I accessing the sites on LAN in a wrong way I mean I should do some thing like 
[http://192.168.1.5/abc.com](http://192.168.1.5/abc.com)
and [http://192.168.1.5/site1.abc.com](http://192.168.1.5/site1.abc.com)

If ServerPath is to be used how is this to be used in my case ?
What I am not clear is /etc/apache2/sites-enabled/abc.com
/etc/apache2/sites-enabled/site1.abc.com
in both  the files I should  use ServerName or I should create a separate default file for this.

---

### Post by Ryan Dwyer on 2010-05-10
> **tapas_mishra said:**
> Even before you said I did try that and it did not worked.
[http://192.168.1.5](http://192.168.1.5) 
was giving me index page of abc.com how to access different domains in this case from client machine on network.

You should make an entry in /etc/hosts and request it using the hostname. You do not browse to [http://192.168.1.5](http://192.168.1.5) - you browse to [http://www.abc.com](http://www.abc.com).

> **tapas_mishra said:**
> I used a Firefox plugin [Live HTTP headers ]("https://addons.mozilla.org/en-US/firefox/addon/3829")
to see which header is going to webserver and it came to be HTTP 1.0 to  which the above links says is a problem.I am surprised since I am using mozilla 3.6.3 if this has a problem then which brower does not have or sends correct HTTP :host header.

It's probably sending HTTP/1.0 because you're using the IP instead of the hostname. It doesn't need to use HTTP/1.1 in that case.

> **tapas_mishra said:**
> Or am I accessing the sites on LAN in a wrong way I mean I should do some thing like 
[http://192.168.1.5/abc.com](http://192.168.1.5/abc.com)
and [http://192.168.1.5/site1.abc.com](http://192.168.1.5/site1.abc.com)

If ServerPath is to be used how is this to be used in my case ?

Here's how ServerPath should be used: [http://apache.active-venture.com/vhosts/examples-additional.html#serverpath](http://apache.active-venture.com/vhosts/examples-additional.html#serverpath)

But it's easier to add an entry to /etc/hosts and request it via hostname.

> **tapas_mishra said:**
> What I am not clear is /etc/apache2/sites-enabled/abc.com
/etc/apache2/sites-enabled/site1.abc.com
in both  the files I should  use ServerName or I should create a separate default file for this.

Both virtual host files should have the ServerName directive. If you get a warning when starting Apache then you need to set a global ServerName outside of a virtualhost container.

---

### Post by tapas_mishra on 2010-05-10
> **Ryan Dwyer said:**
> You should make an entry in /etc/hosts and request it using the hostname. You do not browse to [http://192.168.1.5](http://192.168.1.5) - you browse to [http://www.abc.com](http://www.abc.com).
That is what exactly the problem is even after doing that it did not responded properly.
I am not sitting on 192.168.1.5 in fact there is no browser installed on it.Gnome Dispay Manager is not there it is a server with just a black screen.


> **Ryan Dwyer said:**
> 
It's probably sending HTTP/1.0 because you're using the IP instead of the hostname. It doesn't need to use HTTP/1.1 in that case.

Yes exactly that is what the problem is I am aware that I should not use IP and send host name./etc/hosts works if you are sitting and checking the websites from the Apache server itself.
I am using a Mac on Client machine but then there is a scenario where development team may not be using Linux for them I can not change /etc/hosts in their systems.
DNS I mentioned I do not have any access.


> **Ryan Dwyer said:**
> 
But it's easier to add an entry to /etc/hosts and request it via hostname.

Ya I understand but if you are now clear with above scenario then you can understand better.

> **Ryan Dwyer said:**
> 
Both virtual host files should have the ServerName directive. If you get a warning when starting Apache then you need to set a global ServerName outside of a virtualhost container.
Yes this is quite right.So you mean to say if I host multiple websites then in apache2.conf I should mention ServerName for each of them.




> **Ryan Dwyer said:**
> 
Here's how ServerPath should be used: [http://apache.active-venture.com/vhosts/examples-additional.html#serverpath](http://apache.active-venture.com/vhosts/examples-additional.html#serverpath)

Thanks for this one.I read it but it says if you have some thing like [www.abc.com/sub1]("http://www.abc.com/sub1") then ServerPath helps
I have to websites on same machine.
[http://site1.abc.com](http://site1.abc.com) and [http://www.abc.com](http://www.abc.com)

  If I use  box say  client side which does not have access to /etc/hosts
and then to access the above two domains what should I do ?
If I type on client browser 
[http://192.168.1.5](http://192.168.1.5) I have not specified which vhosts I want to access .
How do I configure my Apache2 to handle this situation?
for some time you assume /etc/hosts file is not there or you do not have access to this.
Also DNS you do not have access so that internal IPs can be redirected to that Apache server.
I do have access to Apache server as root but not the DNS so if any one suggests some thing I shall be able to try it. 
Then how do I access both websites?

---

### Post by Ryan Dwyer on 2010-05-10
When I said to edit /etc/hosts, I meant on the client machines, not the server.

I believe Mac has an /etc/hosts as well. Mac does a good job of hiding the system filestructure so you might have to use a terminal to edit it.

With Windows you can edit C:\WINDOWS\system32\drivers\etc\hosts.

So yeah, you need to edit the hosts file on each machine that needs to access it. Unless you have a local DNS server, in which case you can add one record and it's done.

---

### Post by tapas_mishra on 2010-05-10
> **Ryan Dwyer said:**
> When I said to edit /etc/hosts, I meant on the client machines, not the server.

I am also saying the same.I looked at [this]("http://wiki.centos.org/TipsAndTricks/ApacheVhostDefault") page and they say to create a generic host also.
So that default vhost does not gets served.
I am not clear with how to make a generic host.

---

