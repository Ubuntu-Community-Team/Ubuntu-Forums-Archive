---
title: "Does Apache Support Multiple hosting for SSL?"
date: 2009-05-21
forum: Security
---

### Post by uupreti on 2009-05-21
Hello Everybody!
I have quick question for you. I have setup an apache server to support virtual hosting ( name based hosting) to host more than one domain at the same ip. Everything is working good and fine when I am hosting single website but when I tried to host next domain in same server, it gave me error while restarting apache.

So my question is?
1. Does apache support multiple domain in same ip and port to have two certificates ( multiple SSL sites hosting in virtual hosting).
2. Do I have to do extra configuration for this?
3. If yes what is this and not then how hosting company will manage huge numbers of SSL websites hosting in same server??

I have heard about Shared-SSL but really dont' know about it.

Does it make sense??

Thanks

---

### Post by HermanAB on 2009-05-22
You need a unique static IP address for each SSL web site.

---

### Post by uupreti on 2009-05-22
Then what will be answer for my third question?? How hosting server will manage to do this?

---

### Post by cariboo on 2009-05-22
A shared ssl Server is just a ssl VituralHost. Here are the rules:
[list]
[*]Only one ssl VirtualHost per Internet IP address. Unlike apache's NameVirtualHost, ssl only responds to requests on a specific IP address.
[*]You need a ssl Cert. For testing you can create your own.
[/list]

---

### Post by uupreti on 2009-05-22
So that means I can't have two different domain right? Let me tell you as clear as I can (for eg. **[https://www.abc.com](https://www.abc.com)** and **[https://www.xyz.com](https://www.xyz.com)** in server which has only one IP **192.168.1.1** ) is not possible right??

---

### Post by cdenley on 2009-05-22
> **uupreti said:**
> So that means I can't have two different domain right? Let me tell you as clear as I can (for eg. **[https://www.abc.com](https://www.abc.com)** and **[https://www.xyz.com](https://www.xyz.com)** in server which has only one IP **192.168.1.1** ) is not possible right??

There is a way, if I remember correctly, but it isn't guaranteed to work on all browsers. The problem is that the hostname isn't sent by the browser to the web server until the SSL certificate has been accepted and the connection is encrypted. How would the server know which certificate to send if it doesn't know the hostname yet?

It technically is possible if openssl is compiled with SNI support (I don't think it is by default), and if the user's web browser supports it.
[http://en.wikipedia.org/wiki/Server_Name_Indication](http://en.wikipedia.org/wiki/Server_Name_Indication)
[http://www.ietf.org/rfc/rfc3546.txt](http://www.ietf.org/rfc/rfc3546.txt)
[http://www.g-loaded.eu/2007/08/10/ssl-enabled-name-based-apache-virtual-hosts-with-mod_gnutls/](http://www.g-loaded.eu/2007/08/10/ssl-enabled-name-based-apache-virtual-hosts-with-mod_gnutls/)

---

### Post by bodhi.zazen on 2009-05-22
You can do this in one of several ways.

#1 is by using a "wild card" in your ssl certs. This works if your virtual hosting is all on one domain 

foo.com
domain1.foo.com
domain2.foo.com

[http://blog.bodhizazen.net/linux/ssl-certificate-with-virtual-hosts/](http://blog.bodhizazen.net/linux/ssl-certificate-with-virtual-hosts/)

#2 is to assign more then 1 ip address to your ethernet card.

example ;

```
root@ufbt:~#ifconfig eth0:0 192.168.1.11
root@ufbt:~#ifconfig
eth0      Link encap:Ethernet  HWaddr de:ad:be:ef:20:51
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::dcad:beff:feef:2051/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2755726 errors:0 dropped:378 overruns:0 frame:0
          TX packets:3155961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2435917177 (2.4 GB)  TX bytes:3088869992 (3.0 GB)
          Interrupt:10 Base address:0x8000

eth0:0    Link encap:Ethernet  HWaddr de:ad:be:ef:20:51
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6864886 (6.8 MB)  TX bytes:6864886 (6.8 MB)
```

Now, as you can see, I did not fully configure eth0:0, simply set it up in /etc/network/interfaces, with a static ip, same as you would eth0.

You then configure / bind your vitrualhosts (in apache) to each ip address and you make one ssl per virtualhost (you will get 'woring host" error messages mind you).

You may not be able to do this if you do not have sufficient ip addresses.

And #3, more complex, is to use virtualization or multiple servers. You then throw up an apache installation as a reverse proxy to proxy incoming requests to your virtual or physical servers.

With this you put the ssl cert on the proxy server (not on the virtual servers).

[http://www.apachetutor.org/admin/reverseproxies](http://www.apachetutor.org/admin/reverseproxies)

And here is an example using pound as a proxy :

[http://www.cyberciti.biz/faq/linux-http-https-reverse-proxy-load-balancer/](http://www.cyberciti.biz/faq/linux-http-https-reverse-proxy-load-balancer/)

---

### Post by uupreti on 2009-05-23
Yeah Wildcard is for domain and it's subdomain but I am talking about two different domain [www.abc.com](www.abc.com) and [www.xyz.com](www.xyz.com). Any insight on this??

---

### Post by bodhi.zazen on 2009-05-23
Well, did you look at either of the other two suggestions I gave you ?

The second is a way of assigning a unique ip address to each virtual host.

The third is to use a proxy server. You use https to connect to the proxy and traffic between the proxy and your virtual hosts is https.

run the proxy on port 80 and teh virtual hosts on 8080 bound to localhost (or firewall 8080).

---

### Post by oke on 2009-06-17
There is another option to serve multiple domains with one SSL certificate. Next to the wildcard for the support of

[INDENT]foo.com
domain1.foo.com
domain2.foo.com
[/INDENT]
you can also have domains like

[INDENT]abc.com
domain1.abc.com
domain2.abc.com[/INDENT]

on the same server SSL certificate. Information, background, and script to generate the private key and CSR for this purpose can be found on URL [http://wiki.cacert.org/wiki/VhostTaskForce](http://wiki.cacert.org/wiki/VhostTaskForce). In section "Interoperability Test" it is shown that one CommonName (CN) with multiple SubjectAltNames (SANs) and a few other details works best. However, the script that is most up to date, which I used myself, and worked :p is at URL [http://wiki.cacert.org/wiki/CSRGenerator](http://wiki.cacert.org/wiki/CSRGenerator).

For the above example use for instance CN=*.foo.com and SAN1=*.foo.com (repetition of the CN as first SAN is a must!); SAN2=foo.com; SAN3=*.abc.com; SAN4=abc.com (as input to the script).

My webserver currently serves a situation like the example with only one SSL certificate from CAcert. I can confirm from testing that both IE7 and Firefox 3.0.11 work well on all my (secure) domains.

---

### Post by bodhi.zazen on 2009-06-17
Thank you for the links oke ;)

---

### Post by noway2 on 2009-07-09
I would like to follow up on the first post in this thread by bodhi.zazen.

In item #2, the setup called for using an alias IP address and I am admittedly intrigued by the idea but I am having trouble grasping part of the concept.

In the example, private IP addresses were used for the two vhosts, and presumably they would be behind a router doing NAT.  The Apache setup portion is clear, but in my thought experiment on the concept I am having trouble with the NAT portion.

The router I use only allows you to forward a particular port, 443 in this case, to a single IP address.  I presume that you would set this to the non-alias IP and since both IPs are the same hardware, they would both see/receive the query.  Further, I am guessing that somehow, the protocol stack is implemented in the NIC card such that the alias IP address, or at least as seen by Apache, is able to be identified by the correct vhost.  Is this correct or do I have it all wrong and this is what was meant by "having enough IP addresses"?  If you had multiple public IP addresses you could use this technique to forward them to the same server, but I am assuming the whole idea is to use one public IP address for multiple virtual hosts by name.

On a similar note, I have read that the mod_gnutls supposedly allows this through SNI, but so far I haven't been able to get that work :(

---

### Post by malikp on 2009-07-17
I also looking for way to resolve same issue.
 
This may help. 
 
[http://ubuntuforums.org/showthread.php?t=1145086&highlight=sni](http://ubuntuforums.org/showthread.php?t=1145086&highlight=sni)
 
Look like only solution is SNI and for me browser support not an issue.

---

### Post by scientastic on 2009-08-10
There is a third option.  You can use just one IP address, have multiple certificates, and multiple hostnames over SSL.  Each hostname should have its own certificate, of course, which is specific to that hostname.

The catch: each of the hostnames has to run on a separate port.

If that's acceptable to you (using a non-standard port for HTTPS), then here is how it's done:

Your /etc/apache2/ports.conf should contain the following:
```
<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here

    # Actually, contrary to the comment above (which I think was a
    # stock comment that came with the installed config files), SSL
    # name-based virtual hosts are supported, but there are a few
    # issues.  Multiple name-based virtual hosts cannot work with
    # HTTPS if they each have their own certificate, because the SSL
    # connection wraps the HTTP and thus the server doesn't know what
    # the requested hostname is until after it has had to present its
    # certificate to the client.  The only workaround I've found is to
    # have each HTTPS site running on a separate port.  That way
    # Apache can distinguish them before it unwraps the SSL.

    # Domain [www.abc.com]("http://www.abc.com/") gets the standard port in this example
    NameVirtualHost *:443
    Listen 443

    # Domain [www.xyz.com]("http://www.xyz.com/") gets the non-standard port in this example
    NameVirtualHost *:8443
    Listen 8443
</IfModule>
```Next, each of your domains should typically have its own file under /etc/apache2/sites-available/.  For example:

/etc/apache2/sites-available/www.abc.com:
```

# domain: [www.abc.com:443]("http://www.abc.com:443")
# public: /path/to/www.abc.com/files/

<IfModule mod_ssl.c>

<VirtualHost *:443>

        # server name (domain name) and alias, and admin email
        ServerName [www.abc.com]("http://www.abc.com")

        # Index file and document root (where the public files are located)
        DirectoryIndex index.html index.php
        DocumentRoot /path/to/www.abc.com/files/

        # ... other settings ...

        # Custom directory options
        <Directory /path/to/www.abc.com/files/>
                # ... other settings ...
                SSLRequireSSL
        </Directory>

        # SSL options
        SSLEngine on
        SSLProtocol all
        SSLCipherSuite HIGH:MEDIUM  # or whatever
        SSLCertificateFile /etc/apache2/ssl/www.abc.com.crt
        SSLCertificateKeyFile /etc/apache2/ssl/www.abc.com-private-key.pem

        # The following is if you have made your own root certificate
        SSLCACertificateFile /etc/apache2/ssl/my-ca.crt

</VirtualHost>

```/etc/apache2/sites-available/www.xyz.com:
```

# domain: [www.xyz.com:8443]("http://www.xyz.com:8443")
# public: /path/to/www.xyz.com/files/

<IfModule mod_ssl.c>

<VirtualHost *:8443>

        # server name (domain name) and alias, and admin email
        ServerName [www.xyz.com]("http://www.xyz.com")

        # Index file and document root (where the public files are located)
        DirectoryIndex index.html index.php
        DocumentRoot /path/to/www.xyz.com/files/

        # ... other settings ...

        # Custom directory options
        <Directory /path/to/www.xyz.com/files/>
                # ... other settings ...
                SSLRequireSSL
        </Directory>

        # SSL options
        SSLEngine on
        SSLProtocol all
        SSLCipherSuite HIGH:MEDIUM  # or whatever
        SSLCertificateFile /etc/apache2/ssl/www.xyz.com.crt
        SSLCertificateKeyFile /etc/apache2/ssl/www.xyz.com-private-key.pem

        # The following is if you have made your own root certificate
        SSLCACertificateFile /etc/apache2/ssl/my-ca.crt

</VirtualHost>

```Now, you can access your two sites at the following two URLs:

[https://www.abc.com/](https://www.abc.com/)
[https://www.xyz.com:8443/](https://www.xyz.com:8443/)

---

