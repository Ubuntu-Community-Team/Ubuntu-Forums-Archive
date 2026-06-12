---
title: "Blocking hackers trying to get in by IP address"
date: 2009-08-01
forum: Security
---

### Post by wxman on 2009-08-01
Does anybody know of a way to block script kiddies from trying to access my sites using IP addresses, not domain names?

In my logs I'm seeing people from the same block of IP's trying to access pages that aren't there using addresses like http://XXX.XXX.XX.XXX/store-admin for example. I know they're just fishing around to find a weakness, but I'd like to stop any access using an IP in the address instead of the proper domain name.

---

### Post by wirelessmonkey on 2009-08-01
In your apache configs, you can set the Allow/Deny rules....  

Order Deny/Allow
Deny from xxx.xxx.xxx.xxx

Allow from Any

---

### Post by wxman on 2009-08-01
> **wirelessmonkey said:**
> In your apache configs, you can set the Allow/Deny rules....  
Order Deny/Allow
Deny from xxx.xxx.xxx.xxx
Allow from Any
I knew that one, but could there be a similar function that will block anyone using an IP without specifically singling out one IP?

---

### Post by wojox on 2009-08-01
Order Deny,Allow
Deny from all
Allow from 127.0.0.1

You can use that and then only you will have access.

---

### Post by gombadi on 2009-08-01
> 
Does anybody know of a way to block script kiddies from trying to access my sites using IP addresses, not domain names?

and

I knew that one, but could there be a similar function that will block anyone using an IP without specifically singling out one IP?


wxman - From what I see you want to stop people connecting to your system unless they are requesting a url with a domain name. That is tricky as the only way to see if they are asking for a domain name instead of an ip address is to see what url they ask for AFTER they connect.

That means they will always be able to connect and will fill your logs but there is a way to ignore them.

On your system you configure apache with a vhost for each domain you want people to connect to. If they connect to your system and do not request a configured domain then apache will use the default vhost. This is the first that is configured.

What I do is configure the default vhost(the first that apache reads) to have a DocumentRoot of a directory that only has an index.html file in it and nothing else. The index.html file I use is -

```

<html><head><title>Nothing to see here...</title></head>
<body>
<h1>Nothing to see here.</h1>
<h3>Move along please...</h3>
</body>
</html>

```

When someone connects to my systems and does not request a configured domain then they end up in an empty directory. They can search for as long as they want to find any exploits but they will have trouble finding them in an empty directory.

Another thing to do is to set a custom log for the default vhost so apache sends the logs to a file such as /var/log/apache2/sillypeoplelookingforthingsthatdonotexist.log and then get log rotate to rotate the file and just ignore it.

As you say if you put a firewall or apache ip restrictions in place then you will be blocking anyone from that ip range from connecting to your system.

---

### Post by wxman on 2009-08-01
> **gombadi said:**
> On your system you configure apache with a vhost for each domain you want people to connect to. If they connect to your system and do not request a configured domain then apache will use the default vhost. This is the first that is configured.

What I do is configure the default vhost(the first that apache reads) to have a DocumentRoot of a directory that only has an index.html file in it and nothing else. The index.html file I use is -

```

<html><head><title>Nothing to see here...</title></head>
<body>
<h1>Nothing to see here.</h1>
<h3>Move along please...</h3>
</body>
</html>

```

When someone connects to my systems and does not request a configured domain then they end up in an empty directory. They can search for as long as they want to find any exploits but they will have trouble finding them in an empty directory.
That's what I thought. I have a file that says something like that in place now. I've messed around with my Apache setup enough to know that I've never seen a way to do this. I was just hoping someone had a great trick I had missed.

> 
Another thing to do is to set a custom log for the default vhost so apache sends the logs to a file such as /var/log/apache2/sillypeoplelookingforthingsthatdonotexist.log and then get log rotate to rotate the file and just ignore it.

As you say if you put a firewall or Apache ip restrictions in place then you will be blocking anyone from that ip range from connecting to your system.
These show up easily in my logs, including my Drupal log, where I find them the most. Most of the time they are coming from some dinky no name ISP that won't even list it's information in whois. A couple of times they've come from big ISP's and I actually reported them. It probably did nothing, but they didn't come back. I still like to stop them from trying.

---

