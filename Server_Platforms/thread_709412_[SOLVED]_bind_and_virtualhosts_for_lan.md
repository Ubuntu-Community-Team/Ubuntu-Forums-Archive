---
title: "[SOLVED] bind and virtualhosts for lan"
date: 2008-02-27
forum: Server Platforms
---

### Post by xyrer on 2008-02-27
Hi, I have read all kind of posts about how to use bind, and how to create apache virtualhosts, but all of them seem to refer to only localhost, or stick too much to examples so changing anything crashes the whole process.

My problem is:
I have created a virtualhost in apache, named local.surftrackr.com, I don't know if this name is right, I have no domain or anything, no way I will buy one anyway.
I have this on my /etc/hosts file: ```
127.0.0.1       localhost proxy2
127.0.0.1       local.surftrackr.com


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

but I assume that it will only work on that machine, how can I configure bind to route local.surftrackr.com or whatever I have to put, to the apache virtualhost I created?

Please, if someone answers me, don't put example.com, it's very confusing, is that local only access website? is it public? what happened to the www? what if the local website I want is myshop.myweb.whatever?

I will make a tutorial out of this, the one I found didn't work at all.

this is the virtualhost file in sites-available: ```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName local.surftrackr.com
        DocumentRoot /var/www/surftrackr
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /var/www/surftrackr>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/surftrackr_error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```
I did a2ensite and it's on sites-enabled, restarted apache, this came out when I restarted it: ```
* Restarting web server apache2
[Wed Feb 27 19:00:40 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Wed Feb 27 19:00:50 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[ OK ]

```

Please, I searched a lot and tried many things, none worked, so no RTFM because I already did.

Thank you very much.

---

### Post by k_grdn on 2008-02-27
Hi,

Are you actually using bind?

Or are you refering to /etc/hosts?

Best practice is to use the ip address of your local interface. i.e

192.168.10.2 local.surftrackr.com

127.0.0.1 is used for the loopback interface.

It's also better practice to leave the default VH copy it and rename as your VH, don't forget to symlink it to sites-enabled then restart apache.

Regards,

k_grdn

---

### Post by Mr. C. on 2008-02-27
You have some confusion.  Here are some points to consider:

[LIST]
[*]You appear to be using the hosts table (/etc/hosts), and not bind (aka: named).
[*]Your **NameVirtualHost** parameter is incorrect.  Try **NameVirtualHost *:80**, since you are likely listening on port 80 and not others.
[*]Don't use a domain name that you do not own.  Create a local private name, something like myserver.local, and add a myserver.local entry in your /etc/hosts file.  You do not want the resolver to return a remote public IP address for your local server; avoid misconfiguration and unexpected problems by not stomping on existing domain names.
[*]You have a good VirtualHost container; just change the name to match the myserver.local phony domain name I gave above.
[*]The hosts entries you add on the apache server machine will be usable only by that machine.  So, the virtual host addresses will be 127.0.0.1.  To reach your virtual hosts from other machines on your lan, you need to add appropriate entries in *their* hosts table, or use a DNS server on your LAN.
[*]Get the local hosts file method working first, and then move to setting up a DNS server for your LAN when that is complete..
[/LIST]

MrC

---

### Post by xyrer on 2008-02-27
Hi, thank you for your help, I looked up all the points you wrote.
* I'm using bind, but many tutorials have the /etc/hosts thingy, so i edited it.
* I changed the file of the virtualhost to surftrackr.local in sites-available, then did a2ensite and the link is in sites-enabled, changed it to NameVirtualHost *:80 ( I don't know if I have to change any other file to reflect this, the default virtualhost has no :80)
* I changed the name inside the file as well, as you said.
* I want to use a dns server on my lan, it's precisely where I got stuck.
* I don't have graphic interface in that server so I just did a ping to surftrackr.local and this came out: ```
ping surftrackr.local
PING surftrackr.local (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.104 ms

```

I assume the apache config is fine, the bind part, so my entire lan is aware of the surftrackr.local virtualhost, is my problem, and is where I need the most help.
Thanks.

---

### Post by Mr. C. on 2008-02-27
> **xyrer said:**
> Hi, thank you for your help, I looked up all the points you wrote.
* I'm using bind, but many tutorials have the /etc/hosts thingy, so i edited it.

Right, it is simpler to remove additional factors such as bind, and move onto that when the system is working.  You may have installed a name server, but it also needs to be configured for any new zones that you add.  Otherwise, it is just a local caching name server, and is not authoritative for zones other than a local-only domain.

> **xyrer said:**
> 
* I changed the file of the virtualhost to surftrackr.local in sites-available, then did a2ensite and the link is in sites-enabled, changed it to NameVirtualHost *:80 ( I don't know if I have to change any other file to reflect this, the default virtualhost has no :80)

The important point is the elimination of the error that apache was generating.  Is that now resolved ?

> **xyrer said:**
> * I changed the name inside the file as well, as you said.

Good.
> **xyrer said:**
> * I want to use a dns server on my lan, it's precisely where I got stuck.
Ok, then I presume you have created the zone files for your bind server.  Have you added the zones for this phony domain ?

> **xyrer said:**
> * I don't have graphic interface in that server so I just did a ping to surftrackr.local and this came out: ```
ping surftrackr.local
PING surftrackr.local (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.104 ms

```

But you do have another system on the LAN, right?  If so, configure its host file to the phony virtual domain name you created, open its browser, and enter the URL.  That will get you paste the virtual domain part.  Then, move onto configuration of bind.
> **xyrer said:**
> 
I assume the apache config is fine, the bind part, so my entire lan is aware of the surftrackr.local virtualhost, is my problem, and is where I need the most help.
Thanks.

Give some feedback on the above questions regarding bind.  Do you want to learn about bind, or just configure it in a howto fashion and move on?

MrC

---

### Post by xyrer on 2008-02-27
I configured the machine I use (windows because of some issues), and it worked perfect, I pointed the browser to surftrackr.local and it worked, i put the local ip of my apache server on the hosts file and that did it, now I want all the rest of the machines to work the same way, obviously without this modification to the hosts file, so, as you said, I'll move onto the configuration of bind, althought the apache server complained about the same problem, I don't know where to solve it anyway, but it worked.

I want to learn about bind, but I'm the kind that learns following a howto, combined with the default documentation I make my own concept, when I see things working I realize what has to be done for any similar case.

By the way, I haven't added the zones in bind, that part got me confused in every howto and tutorial I found.

Thanks.

PD: I changed a little bit the file /etc/apache2/sites-available/surftrackr.local and the apache doesn't complain anymore.

---

### Post by Mr. C. on 2008-02-27
Not knowing which tutorials/howtos have failed you, nor why they are insufficient for you, I cannot make a recommendation for others.

I'll give you some lecture notes and lab work that may help you to understand a bit more so that the tutorials will help:

[http://cis68c2.mikecappella.com](http://cis68c2.mikecappella.com)

See week 8 Notes, lab work, and homework.

Go through the basics, and ask specific questions when you are stuck.

MrC

---

### Post by xyrer on 2008-02-27
Well, Right now I would like to know, how to make the surftrackr.local work in the entire lan, I assume I have to put the bind server as the dns of all machines.
And how should I make more virtualhosts, I tried to create another one and Apache complained again about no virtualhosts at :80, if i put it as :81 it works fine, I don't know if that's ok thou

---

### Post by Mr. C. on 2008-02-27
Yes, you configure the LAN systems to use your DNS server.  You can likely configure your router to provide this information via DHCP.

You can configure as many virtual hosts as you like.  The format is:

<VirtualHost address:port>

where address is the IP address of the server, and port is the port number that apache is listening on, typically 80 or 443 for SSL.  * is a value that means "all interfaces" (eg. all IP addresses that apache is listening on).

Create as many virtual host containers as you'd like:
```

<VirtualHost *:80>
   ...
   ServerName host1.surftrackr.local
   ...
</VirtualHost>

<VirtualHost *:80>
    ...
   ServerName host2.surftrackr.local
   ...
</VirtualHost>
```

Just create the DNS (A record) entries for host1.surftrackr.local, host2.surftrackr.local, etc.

MrC

---

### Post by xyrer on 2008-02-28
Well, then maybe is the dns part the one not working, could you help me a little on the bind config? I was following [this]("http://www.zaphu.com/2007/09/14/ubuntu-dns-server-guide-bind-master-server-setup/") tutorial, but I didn't understand why there is a bunch of hostnames, is not clearly explained what are they for (or I'm not understanding).

About the virtualhosts, I had to disable one to get the other one working, I will check further on that, but please help me with bind, the website you gave me is like reading chinese to me.

---

### Post by Mr. C. on 2008-02-28
I'm happy to help you, but to help, you really have to follow my suggestions and guidance.  I've suggested that you work on *one* area at a time.  Either pick virtual hosts or BIND.  Either way, you need to learn about them, and how to effectively test your configuration.  Both can work together, but both are independent and can be independently verified as operational.

DNS, in concept, is simple, but  is very complicated in practice.   You have to know some basics before you should setup a DNS server, or all sorts of trouble will arise.   If nothing makes sense on the notes and labs I provided, nor on the tutorial, its time to pick up a book on DNS and what it is all about.  Alternatively, don't configure a DNS server if you're not up for the challenge.

Multiple VirtualHosts works fine - I have dozens, other's have hundreds or thousands.  But we'll go nowhere with "it doesn't work" strategies.  Show your configuration, and the access_log and error_log messages that result.  Nobody here can magically sense your configuration files!

MrC

---

### Post by xyrer on 2008-03-01
Well, I was working on virtualhosts, but I thought I needed bind so the virtualhosts would work, I assume they work without bind when you test it on the same machine, but I can't do that in my case, the pc where I can experiment has ubuntu server, so no graphics, either way it has no monitor.

I tried to add the virtualhosts definitions to the hosts file on the windows machine I use (flash designer, so...) but it only worked with the first one, when I re-did the process to add another virtualhost, everything got messed up, but I don't know how to diagnose the problem, otherwise I would have posted everything relative to it, as I did at the beginning

In my country, getting access to technical books tends to be very expensive, I make  US$350 a month, a book as the ones you suggested costs around US$50.
I have tried to read and learn all by myself and learn the concepts of configuring bind, but it doesn't make any difference, the tutorials aren't complicated to understand, the complicated part is what they do not explain, like the hostnames I mentioned before, nowhere in the tutorial it says what are they for.

I would like to work on virtualhosts first then, as I think it's the easiest part, what files exactly should I look to troubleshoot what's going wrong? what files should I post so anyone can guide me?

Thanks for your patience, as I said before, I have problems getting the concept of things by reading tons of theory, I got into linux and programming without reading theory first and what I have learned I have done it well, all because I got into action, learning the concepts along the way and then reading theory, that way I could understand it, reading the theory after having learned the way to use a tool makes it a lot more comprehensive for me.

---

### Post by Mr. C. on 2008-03-08
Sorry for the delay - do you still need help with this ? 

I an appreciate your situation, but, let's focus on getting your tasks solved.

---

### Post by xyrer on 2008-03-08
Gee, later is way better than never, I stoped working on all this because of the frustration and some work in the office, althought I'm very interested, I was reading about dns and bind, got bind running but only as a forwarder, I don't know wich subject to study first, but as I can't work directly on my server, I assumed I had to make bind work first to work on virtualhosts then, but (correct me if I'm wrong) one doesn't work as I want without the other one.
I have failed to find a way to delete the virtualhosts, I deleted the files but somewhere they are still defined, I would need 2 virtualhosts working and the bind server to point to them; that way I would know everything that is necessary to work the rest on my own.
I guess I should post something, but I don't know what. Thanks.

---

### Post by Mr. C. on 2008-03-08
Xyer,

DNS and Apache are separate - you do not need to configure a DNS server in order to configure, test, and deploy your virtual hosts.

You can use a simple /etc/hosts -based name lookup to simplify your setup.  Or you can get DNS working correctly first, and then work on your virtual hosts later.

Regardless of which you want to do first, it is important to know how to test your configuration properly.  Once you have the service working, then you can go onto the next step.

You pick the one you want to work on, and let us know.

---

### Post by xyrer on 2008-03-17
All right, I didn't receive the e-mail notification so I didn't know you had answered, sorry.

I think virtualhosts are my priority now, the DNS is working but only as a slave, forwarding everything to my isp so I know it's working and I only have to learn how to add zones, but the virtualhosts are far more important right now to me.
I created one and tried to delete it but everything got messed up, so I created it again copying the default config, so I could still use the websites I have there.

Any help regarding creating more than one virtualhost is very welcome, as well as deleting them, I used a2ensite by the way.

Thanks.

---

### Post by Mr. C. on 2008-03-17
You'll have to show the contents of your httpd.conf and its accompanying vhosts.  Let's work from data, not story.

---

