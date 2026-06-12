---
title: "howto create subdomains on apache?"
date: 2006-03-28
forum: Server Platforms
---

### Post by lunatic on 2006-03-28
hi,
    We wish to create a subdomain on [http://nitham.ac.in](http://nitham.ac.in) which is "http://glug.nitham.ac.in" under the same ip. So what changes are to be made on apache server so that we will be having /var/www/glug as root folder for glug.nitham.ac.in 
Regards,
Vijay

---

### Post by endersshadow on 2006-03-28
In the bottom of your httpd.conf file (or in your vhosts.conf file, for some servers), insert this:

```
<VirtualHost your.ip.goes.here>
DocumentRoot /var/www/glug
ServerName glug.nitham.ac.in
ServerAdmin administrator@nitham.ac.in
ScriptAlias "/cgi-bin/" "/var/www/glug/cgi-bin/"
ServerAlias glug.nitham.ac.in
</VirtualHost>
```

Restart Apache, and you'll be all set!

---

### Post by Mr. Picklesworth on 2006-06-24
Is it possible to set up subdomains like this with a local test server?
I have the server accessible only to computers on my network (its IP is 192.168.1.102) and it is not associated with any domain name servers.
Just trying to save some typing, and to get the transition from my server to the web server nice and clean I may as well mimic what it's doing.

For some reason, I can't get EmberShadow's suggestion to work with this setup...
(Error 404 when I try to access dhs.192.168.1.102, but 192.168.1.102/DHS/public_html works fine).

As you may have guessed, I'm new to servers.

Here is httpd.conf:
```
<VirtualHost 192.168.1.102>
DocumentRoot /var/www/DHS/public_html
ServerName dhs.192.168.1.102
ScriptAlias "/cgi-bin/" "/var/www/DHS/cgi-bin"
ServerAlias dhs.192.168.1.102
</VirtualHost>
```

Also:
Since it's 2006, I'm assuming we are discussing Apache2 here, right?
(All sorts of conflicting information out there because of untold version numbers).


Thanks!

---

### Post by Kurt` on 2006-06-24
[QUOTE=Mr. Picklesworth]Is it possible to set up subdomains like this with a local test server?[/QUOTE]
Yes.

I am currently waiting for my DNS to resolve to my new IP address, but I didn't want to pause development either. :)

Simply add entries to your hosts file for each subdomain.

On windows, c:\windows\system32\drivers\etc\hosts
on linux, /etc/hosts

Just add a few lines like these: (replacing the IP I put with the IP of the machine Apache is running on)

```
192.168.1.102    whatever.com
192.168.1.102    subdomain.whatever.com
192.168.1.102    anotherone.whatever.com
192.168.1.102    blahblah.whatever.com
```
(if your apache installation is on the same machine, just use 127.0.0.1 or localhost)

Then just add all the VirtualHosts in your Apache conf and you're good to go. :)

The HTTP 1.1 spec requires that the requested domain be sent along with any HTTP request. By adding a few entries to your hosts file, you can redirect ANY domain (locally) to your server. You could even redirect google.com to your server. ;) (but then you can't access it normally through your browser until removing the entries)

Edit: Yeah you can't do subdomain.<some ip here>, DNS doesn't work like that. ;)

---

### Post by Mr. Picklesworth on 2006-06-24
YAY!
Cool :)

I guess I can just use .local instead of .com to avoid any problems...

---

### Post by Kurt` on 2006-06-25
[QUOTE=Mr. Picklesworth]YAY!
Cool :)

I guess I can just use .local instead of .com to avoid any problems...[/QUOTE]
It only affects your local machine, feel free to make up anything you'd like. You're not going to get in trouble for it.

(Although, if other people use said computer, and you redirect google.com to msn.com and myspace.com to facebook.com, you might have some angry relatives. ^^)

---

### Post by jms1989 on 2006-10-22
> **Kurt` said:**
> Yes.

I am currently waiting for my DNS to resolve to my new IP address, but I didn't want to pause development either. :)

Simply add entries to your hosts file for each subdomain.

On windows, c:\windows\system32\drivers\etc\hosts
on linux, /etc/hosts

Just add a few lines like these: (replacing the IP I put with the IP of the machine Apache is running on)

```
192.168.1.102    whatever.com
192.168.1.102    subdomain.whatever.com
192.168.1.102    anotherone.whatever.com
192.168.1.102    blahblah.whatever.com
```
(if your apache installation is on the same machine, just use 127.0.0.1 or localhost)

Then just add all the VirtualHosts in your Apache conf and you're good to go. :)

The HTTP 1.1 spec requires that the requested domain be sent along with any HTTP request. By adding a few entries to your hosts file, you can redirect ANY domain (locally) to your server. You could even redirect google.com to your server. ;) (but then you can't access it normally through your browser until removing the entries)

Edit: Yeah you can't do subdomain.<some ip here>, DNS doesn't work like that. ;)

Are you refering to /etc/host.conf on Ubuntu Linux? I have Apache2 installed and it's contents contain;
```
multi off
```
so I'm not sure what to do to it.

---

### Post by Mr. Picklesworth on 2006-10-22
Quite a multi-purpose thread... It's had 3 owners so far :b

Nope, not /etc/host.conf; you're looking for /etc/hosts.
You probably have it there unless something *really* weird has happened :)

The Hosts file is part of something sort of like (in my simple mind... not sure how right I am) a local DNS server.
When you ask for an address like localhost (127.0.0.1, in this case), it is turned into an IP address in the same way that [www.google.com](www.google.com) is turned into Google's IP.

Of course, the IP address for localhost isn't stored on a DNS server; it's stored on your computer!

That is where the Hosts file comes in.

When a check for what IP address belongs to the URL you've entered is carried out, it will first check the hosts file to see if an IP for that URL is there.
If it is, it will use that. If it isn't, it will ask a DNS server.

So, if you want to add a subdomain but you aren't set up with a domain name host, you have to register subdomain.domain in your hosts file, leading to your IP address.


Err... I'm not sure if I made sense...

---

### Post by jms1989 on 2006-10-22
> **Mr. Picklesworth said:**
> Quite a multi-purpose thread... It's had 3 owners so far :b

Nope, not /etc/host.conf; you're looking for /etc/hosts.
You probably have it there unless something *really* weird has happened :)

The Hosts file is sort of like (in my simple mind... not sure how right I am) a local DNS server.
When you ask for an address like localhost (127.0.0.1, in this case), it is turned into an IP address in the same way that [www.google.com](www.google.com) is turned into Google's IP.

Of course, the IP address for localhost isn't stored on a DNS server; it's stored on your computer!

That is where the Hosts file comes in.

When a check for what IP address belongs to the URL you've entered is carried out, it will first check the hosts file to see if an IP for that URL is there.
If it is, it will use that. If it isn't, it will ask a DNS server.

So, if you want to add a subdomain but you aren't set up with a domain name host, you have to register subdomain.domain in your hosts file, leading to your IP address.


Err... I'm not sure if I made sense...

I think I did this right...
```
127.0.0.1 michaels-web.net www.michaels-web.net
127.0.0.1 pokemon.michaels-web.net
127.0.0.1 linux-gazette.michaels-web.net
127.0.0.1 hula.linux-gazette.net

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Update: I got it working. Although, you can't access it over the internet, I'm going to disclose the domain and subdomains. [http://michaels-web.net](http://michaels-web.net)  [http://linux-gazette.michaels-web.com](http://linux-gazette.michaels-web.com)  [http://graffiti.michaels-web.com](http://graffiti.michaels-web.com)  (WARNING: Ages 18 and up!!)  [http://hula.michaels-web.com](http://hula.michaels-web.com)

---

