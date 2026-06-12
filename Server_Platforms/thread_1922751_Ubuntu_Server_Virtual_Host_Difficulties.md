---
title: "Ubuntu Server Virtual Host Difficulties"
date: 2012-02-09
forum: Server Platforms
---

### Post by Jstall on 2012-02-09
Hello all,

I am running Ubuntu Server as a virtual machine. I have a LAMP environment set up but am having difficulties configuring virtual hosts. Note I can navigate to my server's ip address like so : [http://10.11.1.117/](http://10.11.1.117/) and the proper document root will be show, it's just when I try to add my own that I get a problem. 

I created a site file in /etc/apache2/sites-available called "test.jay", this is what it looks like:
```

NameVirtualHost *:80

<VirtualHost *:80>
        ServerName test.jay
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/test/html
</VirtualHost>

```I then altered my hosts file etc/hosts adding a line for test.jay. It looks like this:

```

127.0.0.1 localhost
127.0.1.1 lamp
127.0.0.1 test.jay

#Required for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```I added my test.jay site using
```

a2ensite test.jay

```and restarted apache, however when I navigate to my server's ip like this : [http://10.11.1.117/test.jay](http://10.11.1.117/test.jay) I get a 404.  Could anyone tell me what I am doing wrong here? Any advice is appreciated. Thanks much!

---

### Post by volkswagner on 2012-02-09
What machine are you trying to access the site from?

Likely you need to alter the /etc/hosts file on the machine you are browsing from.


Client machine /etc/hosts
```
10.11.1.117  test.jay
```


Also check the permissions

```
ls -alt /var/www/test/html
```

---

### Post by Jstall on 2012-02-09
Hi,

Thank you for the reply. 

When I modify my client's host file it does indeed point to the ip address of my server but it only displays the document root in my default virtual host file. The permissions are ok on the var/www/test/html directory, if I change the default virtual host's document root to that I get the expected page. 

Here is the default virtual host file:
```

NameVirtualHost *:80
NameVirtualHost *:443


<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/
</VirtualHost>

<VirtualHost *:443>
        SSLEngine on
        SSLCertificateFile /etc/ssl/certs/cert.pem
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/
</VirtualHost>

ScriptAlias /cgi-bin/ /var/www/cgi-bin/

<Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        Order allow,deny
        allow from all
</Directory>

```
As an experiment I did try to add another virtual host using a different port that would use my test directory as it's document root but that didn't work either. Here is what I added to the default file:
```

NameVirtualHost *:81

<VirtualHost *:81>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/test/html/
</VirtualHost>

```

I restarted apache and navigated to [http://10.11.1.117:81](http://10.11.1.117:81) but got a 404. 

Do you have any other suggestions as to what could be causing this? Thanks again for your response, I appreciate it.

---

### Post by Lars Noodén on 2012-02-09
In addition to editing /etc/hosts, you need to modify the URL.  Since 10.11.1.117 will be substituted for test.jay, your URI needs to look like this:

[http://test.jay/](http://test.jay/)

---

### Post by Jstall on 2012-02-09
Hi,

Thanks for the response. [http://test.jay/](http://test.jay/) is the URI I was using. It takes me  to the document root of the default virtual hosts file, /var/www.

---

### Post by SeijiSensei on 2012-02-09
> **Jstall said:**
> Thanks for the response. [http://test.jay/](http://test.jay/) is the URI I was using. It takes me  to the document root of the default virtual hosts file, /var/www.

You need to specify test.jay in a [ServerName directive]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html").

You might have additional problems trying to specify a name-based HTTPS virtual host.  Usually the simplest rule is one HTTPS host per IP address.

---

### Post by volkswagner on 2012-02-09
A few things to clean up.

Add a ServerName directive to your default.  You can make it the same as the hostname.

Run hostname on server to get your hostname
```
hostname
```

Also get rid of the NameVirtual host directive inside of all your vhost files and add that to ports.conf.

```
sudo nano /etc/apache2/ports.conf
```

You should have the following two lines:

```
NameVirtualHost *:80
Listen 80
```

As mentioned make sure you have the ServerName directive in all your vhost files.

Then restart apache2.

---

### Post by Jstall on 2012-02-09
Hello and thanks again for the response.

I have done as you suggested, volkswagner, but I still have the same issue. 

I have removed the NameVirtualHost from my virtual host files and put them into my ports.conf file. I also added the servername directive to my default virtual host file. 

This is what my test.jay virtual host file looks like now:
```

<VirtualHost *:80>
        ServerName test.jay
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/test/html
</VirtualHost>

```

Could it be that I am not navigating to the server properly? I am simply going to ip/test.jay

---

### Post by SeijiSensei on 2012-02-09
> **Jstall said:**
> Could it be that I am not navigating to the server properly? I am simply going to ip/test.jay

That serves the directory /var/www/test.jay.  If you want to name the virtual host test.jay, you either need to create an entry in /etc/hosts that points that name to the server's IP address, or set up a DNS server with something like bind9 to resolve the "test.jay" domain.

The /etc/hosts alternative is the [easiest to implement]("http://ubuntuforums.org/showpost.php?p=11675551&postcount=2") if you only have a couple of clients.  If you do that, you should be able to access [http://test.jay/](http://test.jay/).

---

### Post by Jstall on 2012-02-09
Hi,

Thanks for the reply. I already have the entry in my hosts file on the server:
```

127.0.0.1 test.jay

```

On my client machine my hosts file directs test.jay to the ip of the server, like so :
```

10.11.1.117  test.jay

```

So when on my client machine when I navigate to [http://test.jay](http://test.jay) it takes me to the document root of my default virtual host. I'm thinking that I am missing something though, how would I navigate to somewhere that map to my test.jay virtual host?

---

### Post by volkswagner on 2012-02-09
> **Jstall said:**
> 

Could it be that I am not navigating to the server properly? I am simply going to ip/test.jay

To navigate to your site the address would be

[http://test.jay](http://test.jay)

This should work because it is the serverName and you have an entry on your client /etc/hosts to take care of the lack of DNS.

/etc/hosts on client will resolve the address for you.

```
10.11.1.117  test.jay
```


If you want to navigate to the site using your ip, you would use the information in the default site.

since the document root is "/var/www/"

You should be able to navigate to test.jay with the following url.

[http://10.11.1.117/test/html/](http://10.11.1.117/test/html/)

---

### Post by Jstall on 2012-02-09
Hi, thanks again for the reply, you have been very helpful. 

I realize I can navigate to my test site by going to [http://10.11.1.117/test/html/](http://10.11.1.117/test/html/) , but that is just because of the directory structure is it not? That URI would work even if I didn't have a virtual host set up wouldn't it?

---

### Post by volkswagner on 2012-02-09
> **Jstall said:**
> Hi, thanks again for the reply, you have been very helpful. 

I realize I can navigate to my test site by going to [http://10.11.1.117/test/html/](http://10.11.1.117/test/html/) , but that is just because of the directory structure is it not? That URI would work even if I didn't have a virtual host set up wouldn't it?


Exactly correct.  Well there does have to be some config for Apache to point to a directory.  In this case it is your /etc/apache2/sites-enabled/000-default

The only reason I wrote that is because you wrote:

> Originally Posted by Jstall  

Could it be that I am not navigating to the server properly? I am simply going to [COLOR="Blue"]ip/test.jay[/COLOR]

Which will not work because test.jay is not a folder name under the the default vhost document root.

does [http://test.jay](http://test.jay) work yet?

---

### Post by Jstall on 2012-02-09
Yes! Success! Navigating to [http://test.jay](http://test.jay) does indeed direct me to the proper place! Thanks very much to everyone that posted in this thread. I've learned a bit more about webserver configuration and I got working what I needed to work. Thanks again!

---

