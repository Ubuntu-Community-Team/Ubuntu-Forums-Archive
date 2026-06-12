---
title: "Web server with public IP address  not reachable via domain name in the web browser"
date: 2013-01-18
forum: Server Platforms
---

### Post by floorripper on 2013-01-18
Hello,

Recently I have setup a public web server on the internet. I have tested it in the lab with the simulated public IP addresses. Server is behind the cisco  firewall and I have allowed ports 22 and 80. In the lab it worked. I was able to reach my server at the *mydomain.com*
with the local connection to the FW and than to the server. I have entered an entry to the /etc/hosts for a simulated dns lookup for *mydomain.com*.


I am having running an Wordpress instance on the apache server. Since I have moved it to the public internet segment. My wordpress instance does no work eighter, I can only see the white screen without my theme. There is also an issue to log in into the wp-admin.

When I make **nslookup *mydomain.com***, I can get the right IP address.
ssh and port 80 also works.

from the server itself I can also do nslookups. I have seted up it with public dns server.

I have conntaced company where I have bought the domainname.com and inserted my IP address into the A records.

How can I make it reachable via mydomain.com and why wordpress stopped to work?
Thanks,


floorripper

---

### Post by darkod on 2013-01-18
Does the internet on the server work OK? You have the routing set up correctly according to how the server is connected?

I don't know if it can create problems, but in your place I would undo the DNS server configuration on your server. For simple set ups, use the control panel at your registrar where you registered the domain. Just set an A record pointing to the public IP and that's it. In that case the registrar servers are doing DNS.
Having it set up on your server might confuse things.

Also, in the registrar control panel create also the www CNAME so that it works with and without the www.

If you ping mydomain.com does it also display the correct public IP?

Do you have any FW in front of the server or on the server itself?

---

### Post by floorripper on 2013-01-18
Hello Darkod,

I have not install any DNS packadge. I have only in /etc/resolv.conf entry of the public dns server in order to resolve domain names.

I can ping the server with correct ip address, I can SSH into it.
Yes it is behind  cisco firewall.

 I did not anything in apache configuration. it is the default.

---

### Post by floatingworld on 2013-01-18
Can you see the site in the browser by typing in the IP address, in the same way that [http://127.0.0.1](http://127.0.0.1) and [http://localhost](http://localhost) are equivalent?

---

### Post by darkod on 2013-01-18
It might be a stupid question, but are you sure the cisco is allowing port 80?

---

### Post by imadovitsky on 2013-01-18
Hi [floatingworld]("http://ubuntuforums.org/member.php?u=903075")

Can you post ur network architecture and ur /etc/resolv.conf

---

### Post by volkswagner on 2013-01-18
Wordpress is configured to respond to the name you setup durning installation.

Did you change the name?  I'm not sure if your test case used the current domain name.  If you change the name look [here]("http://codex.wordpress.org/Changing_The_Site_URL").

---

### Post by floorripper on 2013-01-18
> **floatingworld said:**
> Can you see the site in the browser by typing in the IP address, in the same way that [http://127.0.0.1](http://127.0.0.1) and [http://localhost](http://localhost) are equivalent? 
- no I cannot

Firewall is open for port 22 and 80. and performs nat to the inside of the network.

Yes, server is on the internet with public ip.

**nslookup [www.domainname.com](www.domainname.com)** works
**Ping** **IP/domainname.com ** works
**ssh** works
**telnet** at port 80 works

I can see my wordpress webpage by using an IP address. But is broken and I cannot navigate to the wp-admin. But that is another problem. Main problem is that i cannot 

I believe that it is an issue  with the apache2 configuration or virtual host  settings.

---

### Post by floorripper on 2013-01-18
> **imadovitsky said:**
> Hi [floatingworld]("http://ubuntuforums.org/member.php?u=903075")

Can you post ur network architecture and ur /etc/resolv.conf


Yes there is picture!
[IMG]http://80.240.229.169/downloads/web-server-diagram.png[/IMG]

---

### Post by floorripper on 2013-01-18
> **volkswagner said:**
> Wordpress is configured to respond to the name you setup durning installation.

Did you change the name?  I'm not sure if your test case used the current domain name.  If you change the name look [here]("http://codex.wordpress.org/Changing_The_Site_URL").


I think  that the name has not changed. I have checked the SQL database entires, and there is correct website name.
This is the secondary issue. 

Primary is that the apache itself does not respond when you type **[www.mydomain.com](www.mydomain.com)**

we have to insert IP address.

---

### Post by volkswagner on 2013-01-18
> **floorripper said:**
> ..snip..


I believe that it is an issue  with the apache2 configuration or virtual host  settings.

Please post contents of /etc/apache2/ports.conf and your vhost file.

What sites are enabled?

```
ls /etc/apache2/sites-enabled
```

---

### Post by sandyd on 2013-01-18
> **floorripper said:**
> I think  that the name has not changed. I have checked the SQL database entires, and there is correct website name.
This is the secondary issue. 

Primary is that the apache itself does not respond when you type **[www.mydomain.com](www.mydomain.com)**

we have to insert IP address.

You have to create a CNAME record for [www.mydomain.com](www.mydomain.com) as well.
something like
```

www        3600        IN      CNAME  mydomain.com
```
NOTE: don't copy/paste the above - the spacing is a bit whacky

---

### Post by imadovitsky on 2013-01-18
try to ping the external DNS server from your web server, and verify that your Cisco ASA permet the web server to send DNS request to the external DNS. verify the cisco ASA log

---

### Post by anonymouschief on 2013-01-18
Try putting the server in DMZ for a short while and remove any /etc/hosts entries for the domain name and see if you can access the site via the domain name.

---

