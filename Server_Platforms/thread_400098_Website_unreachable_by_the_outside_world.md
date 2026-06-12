---
title: "Website unreachable by the outside world"
date: 2007-04-03
forum: Server Platforms
---

### Post by moreon on 2007-04-03
Hello Community,

I'm completely new to the webserving world and I'm trying to set-up an apache2 webserver. The problem is that while I can access my website from my pc everyone else can't.

What I've already done is the following:
1. Successfully set up an apache2 webserver
2. Obtained a dns from dyndns.com and successfully use ezipupdate since I have a dynamic ip (I can ping my hostname)
3. Tried the default port 80 but others couldn't access my website and then forwarded a XXXXX port in my router as well as changed the apache2 configuration through webmin to listen to that port but others still couldn't reach my website (with ":XXXXX" appended in the end of my url)
4. Changed the permissions of both /var/www and index.html to read-write for the www-data group

Any ideas?
Thanx in advance

---

### Post by huygens on 2007-04-03
Usually you should tell your router to forward any incoming connection on port 80, to the IP address (or the hostname) of your server on most probably the same port. (this is usually call port forwarding or dnat)
I am not sure if your point 3. covers exactly this.

In addition when you said that you can ping your hostname, from where do you ping it? Can your friends (so connected on the internet) can ping the hostname you have defined in DynDNS?

Also you should take care with ezipupdate. If you run it from your server (instead of from your router), it will probably (I'm guessing) give your local and not your IP address to DynDNS. Usually, you should run the DynDNS (or other dynamic DNS services) update from the router (which has the public - meaning accessible for other - IP address). Most routers have this option in their configuration pages.

If you happen to know the model of your router, I could look for the user manual on internet and tell you more about how to configure the port forwarding and the dyndns update.

Perhaps, you already know/did what I just told. But it was unclear to me from your message...

---

### Post by moreon on 2007-04-03
First of all thank you for the reply. My router's model is Microcom AD2636. What I have done is used the port I have already opened for my bittorrent and DC client. I don't know how to tell my router to forward incoming connections on port 80 to my hostname. Neither do I know how to get ezipupdate running from my router. By the way I'm not using DHCP in Ubuntu but rather I have configured a Static IP address and I'm running ezipupdate from my pc. My friends haven't tried to ping my hostname so I don't know if it works from the "outside". I would very much appreciate if you told me how to do the above configuration on my router.

---

### Post by MJN on 2007-04-03
If you tell us your domain name we'd be able to help you a lot more.
 
Mathew

---

### Post by moreon on 2007-04-03
> **MJN said:**
> If you tell us your domain name we'd be able to help you a lot more.
 
Mathew

pantofla.homelinux.net

I told a friend to ping my hostname and he got a connection timeout although the output showed my static IP (10.0.0.50) so I guess that ezipupdate is working (or am I wrong?).

---

### Post by MJN on 2007-04-03
That's the problem - 10.0.0.50 is part of a so-called private address range (see [http://www.ietf.org/rfc/rfc1918.txt](http://www.ietf.org/rfc/rfc1918.txt) for details) wihch whilst fine (and common) for your internal LAN is not routable on the Internet. Hence when we look it up we can't connect, when you look it up you can - but only because you're on the same LAN.
 
You need to publish your *public* IP address - got to [http://www.whatsmyip.org/](http://www.whatsmyip.org/) and it'll tell you what this is. I'm not familiar with ezipupdate but there will be a way of configuring it such that it detects your public, not private, address and modifies the DNS accordingly.
 
Mathew

---

### Post by huygens on 2007-04-03
I perhaps have found a resource for your router (was pretty difficult...) [http://portforward.com/english/routers/port_forwarding/Microcom/2636/HTTP.htm](http://portforward.com/english/routers/port_forwarding/Microcom/2636/HTTP.htm)

Port forwarding is called "virtual server". What you have to do is to go to your configuration interface for your router (a web based configuration interface usually, see also above link).
You should see an entry "Virtual server" and select it.
For public port start and public port end type 80 for both. So the public ports range from 80 to 80. Private port should be set to 80 and IP to your local IP address (so it seems: 10.0.0.50)
Click on Add settings, and then on Save Settings/reboot.

As for dyndns, it does not seem to support it (from the resources I was able to gather on internet). A solution (not really helpful though) would be to buy an affordable router from D-Link, Linksys or Netgear :( . Even old ones can do such things, so you might find some second hand ones if budget is a constraint. However, I understand that you might not be willing to buy one...

But by the way, you only need to have a script updating dyndns in case your router get a dynamic IP address from your internet provider. In case your provider attributes you with a static IP address, you can set it using the web interface of dyndns and you do not have to bother to update it.

---

### Post by moreon on 2007-04-04
> **MJN said:**
> 
 
You need to publish your *public* IP address - got to [http://www.whatsmyip.org/](http://www.whatsmyip.org/) and it'll tell you what this is. I'm not familiar with ezipupdate but there will be a way of configuring it such that it detects your public, not private, address and modifies the DNS accordingly.
 
Mathew

My public IP address at this moment is 88.218.171.17 but it changes dynamically that's why I use ezipupdate to make my dynamic IP address point to my local static IP address (10.0.0.50). I don't know any other way to make my server accessible by the public so please tell me what else I can do. Do you think that I should change the local IP address I've set to some other that would be routable on the Internet? Excuse me if I talk nonsense:)

---

### Post by MJN on 2007-04-04
You're almost heading on the right track but getting a little confused along the way... ;-)
 
You're correct in acknowledging that your public dynamic IP address is a 'problem' and that ezipupdate is used to get round this. However, it is ezipupdate's job to point your pantofla.homelinux.net domain at your current *public* address. Hence whenever you get a new address from your ISP ezipupdate should detect this and update the DNS accordingly so the rest of us are none the wiser.
 
The only place your private (10.) address comes into play is when telling your router where you want port 80 forwarding to, i.e. which machine on your LAN. This obviously never changes and hence merely requires a router configuration rather than anything to do with ezipupdate.
 
Does that make any sense?
 
I haven't used ezipupdate so cannot tell you how to configure it such that it keeps an eye on your public address and populates the DNS with that. If you show me the output of **ezipudate --help** then hopefully things will become clearer. (I'm not at my machine right now so cannot install it myself to take a look).
 
Mathew

---

### Post by moreon on 2007-04-04
> **huygens said:**
> 

Port forwarding is called "virtual server". What you have to do is to go to your configuration interface for your router (a web based configuration interface usually, see also above link).
You should see an entry "Virtual server" and select it.
For public port start and public port end type 80 for both. So the public ports range from 80 to 80. Private port should be set to 80 and IP to your local IP address (so it seems: 10.0.0.50)
Click on Add settings, and then on Save Settings/reboot. 

Should port 80 be forwarded as both TCP and UDP?

> **huygens said:**
>  As for dyndns, it does not seem to support it (from the resources I was able to gather on internet). A solution (not really helpful though) would be to buy an affordable router from D-Link, Linksys or Netgear :( . Even old ones can do such things, so you might find some second hand ones if budget is a constraint. However, I understand that you might not be willing to buy one...

Since I'm not willing to buy a new router at the time being I'm attaching a few screenshots of the DNS configuration pages from my router's manual so that perhaps you can tell me if I can do anything through it.

> **huygens said:**
> But by the way, you only need to have a script updating dyndns in case your router get a dynamic IP address from your internet provider. In case your provider attributes you with a static IP address, you can set it using the web interface of dyndns and you do not have to bother to update it.

That's why I'm using ezipupdate.

I forgot to attach the screenshots. Here they are

---

### Post by moreon on 2007-04-04
> **MJN said:**
> You're almost heading on the right track but getting a little confused along the way... ;-)
 
You're correct in acknowledging that your public dynamic IP address is a 'problem' and that ezipupdate is used to get round this. However, it is ezipupdate's job to point your pantofla.homelinux.net domain at your current *public* address. Hence whenever you get a new address from your ISP ezipupdate should detect this and update the DNS accordingly so the rest of us are none the wiser.
 
The only place your private (10.) address comes into play is when telling your router where you want port 80 forwarding to, i.e. which machine on your LAN. This obviously never changes and hence merely requires a router configuration rather than anything to do with ezipupdate.
 
Does that make any sense?
 
I haven't used ezipupdate so cannot tell you how to configure it such that it keeps an eye on your public address and populates the DNS with that. If you show me the output of **ezipudate --help** then hopefully things will become clearer. (I'm not at my machine right now so cannot install it myself to take a look).
 
Mathew

I think get it. 
This is the output of 'ez-ipupdate --help':

```
usage: ez-ipupdate [options] 

 Options are:
  -a, --address <ip address>    string to send as your ip address
  -b, --cache-file <file>       file to use for caching the ipaddress
  -c, --config-file <file>      configuration file, almost all arguments can be
                                given with: <name>[=<value>]
                                to see a list of possible config commands
                                try "echo help | ez-ipupdate -c -"
  -d, --daemon                  run as a daemon periodicly updating if 
                                necessary
  -e, --execute <command>       shell command to execute after a successful
                                update
  -f, --foreground              when running as a daemon run in the foreground
  -F, --pidfile <file>          use <file> as a pid file
  -g, --request-uri <uri>       URI to send updates to
  -h, --host <host>             string to send as host parameter
  -i, --interface <iface>       which interface to use
  -L, --cloak_title <host>      some stupid thing for DHS only
  -m, --mx <mail exchange>      string to send as your mail exchange
  -M, --max-interval <# of sec> max time in between updates
  -N, --notify-email <email>    address to send mail to if bad things happen
  -o, --offline                 set to off line mode
  -p, --resolv-period <sec>     period to check IP if it can't be resolved
  -P, --period <# of sec>       period to check IP in daemon 
                                mode (default: 1800 seconds)
  -q, --quiet                   be quiet
  -r, --retrys <num>            number of trys (default: 1)
  -R, --run-as-user <user>      change to <user> for running, be ware
                                that this can cause problems with handeling
                                SIGHUP properly if that user can't read the
                                config file. also it can't write it's pid file 
                                to a root directory
  -Q, --run-as-euser <user>     change to effective <user> for running, 
                                this is NOT secure but it does solve the 
                                problems with run-as-user and config files and 
                                pid files
  -s, --server <server[:port]>  the server to connect to
  -S, --service-type <server>   the type of service that you are using
                                try one of: null ezip pgpow dhs 
                                dyndns dyndns-static dyndns-custom 
                                ods tzo easydns easydns-partner 
                                gnudip justlinux dyns hn zoneedit 
                                heipv6tb 
  -t, --timeout <sec.millisec>  the amount of time to wait on I/O
  -T, --connection-type <num>   number sent to TZO as your connection 
                                type (default: 1)
  -U, --url <url>               string to send as the url parameter
  -u, --user <user[:passwd]>    user ID and password, if either is left blank 
                                they will be prompted for
  -w, --wildcard                set your domain to have a wildcard alias
  -z, --partner <partner>       specify easyDNS partner (for easydns-partner 
                                services)
      --help                    display this help and exit
      --version                 output version information and exit
      --credits                 print the credits and exit
      --signalhelp              print help about signals
```

---

### Post by MJN on 2007-04-04
It looks like ezipupdate doesn't support the sensing of IP addresses that are not bound to a local interface.
 
Take a look at ddclient isntead. (I personally use zoneclient with DNS provided by ZoneEdit, but you should be fine with ddclient and dynDNS)
 
Mathew

---

### Post by huygens on 2007-04-04
Thanks MJN. I did not know ddclient and was already thinking of creating a small script to get the IP address!!

It seems that your router is not supported by ddclient, but it does not matter because you can use the option (which is available by default if not overriden) '-use=web' which will request ddclient to query a web site for your public IP address.

Best of all, ddclient is installable via your package manager (Synaptic, apt-get, aptitude, etc.) :-)

Some help about how to configure it: [http://ddclient.sourceforge.net/](http://ddclient.sourceforge.net/) :-)

As for your question moreon, port 80 should only be frowarded on TCP. HTTP is based on TCP and does not use UDP (AFAIK).
And about your screenshot. They are about DNS Proxy. A DNS is a server that just convert address from the IP form to the host name form and vice versa. Usually your provider *provides* a DNS for you to access internet so when you type [www.ubuntu.com]("http://www.ubuntu.com") your browser can find the IP address and connects to it.
Now, you are using a router which blocks the DNS connections. So the router are usually configured as a proxy, they will act as a local DNS server but will actually forward the request to the DNS server and give you back the answer. But this is something different than dynamic DNS. :-(
I have been looking on the menu on the left of the first screen shot. But none of the entries made me think that they could handle dynamic DNS.

---

### Post by moreon on 2007-04-11
Back from vacation now and back to problems too:) 

Thank you both for your help so far. I believe I've got ddclient working right (whenever I ping my hostname I get my current dynamic IP address). So I tried to visit my website in firefox from my machine as I used to and now I have firefox asking me for authentication although I was able to view it fine before:confused: It's asking me for username and password for "Home Gateway" at pantofla.homelinux.net 

What is happening now?

---

### Post by huygens on 2007-04-11
I just went on your page and I am not asked for a username/password.
A small page is displayed with the following HTML content:
[html]<HTML>
 <HEAD>
  <TITLE> &#927; &#915;&#961;&#951;&#947;&#972;&#961;&#951;&#962; &#949;&#943;&#957;&#945;&#953; &#922;&#945;&#961;&#945;&#947;&#954;&#953;&#972;&#950;&#951;&#962; </TITLE>
 </HEAD>

<BODY
  BGCOLOR="#FFFFFF"
  TEXT="#000000"
  LINK="#0000FF"
  VLINK="#000080"
  ALINK="#FF0000"
 >

<P ALIGN="CENTER"> &#915;&#961;&#951;&#947;&#972;&#961;&#951; &#949;&#943;&#963;&#945;&#953; &#922;&#945;&#961;&#945;&#947;&#954;&#953;&#972;&#950;&#951;&#962; <P><HR WIDTH="50%" SIZE="8">

</HTML>[/html]

So it seems to work... Did you solve it already?

---

### Post by moreon on 2007-04-11
> **huygens said:**
> I just went on your page and I am not asked for a username/password.
A small page is displayed with the following HTML content:

So it seems to work... Did you solve it already?

That's the page! I'm happy that others are able to see it but I haven't done anything and I still can't view it:(  I guess I'll have to change the topic to "Website unreachable by the inside world" ;)

I think I'm going insane](*,) 

Anyone any ideas?

---

### Post by huygens on 2007-04-11
> **moreon said:**
> I think I'm going insane](*,) 

Anyone any ideas?

OK, I think I understand why now. :-)
So your router has two interfaces one for the outside world that is now accessible via the dynamic dns thingy, and one for your local network.
Both interfaces can answer to HTTP services. the outside one for your web site, and the inside one for configuring your router (most probably).
The problem that is maybe causing you the pain is that if you use the outside connection, your router seems to stumble upon it because you are from the "inside" and just reply with the inside interface, so your router configuration HTTP service :-(

However, I do not have a solution to that yet :(
Just a try (but I think you will have the same problem...) If you go again to [http://www.whatsmyip.org/](http://www.whatsmyip.org/) and check your IP address. Then now, if you type in your browser the address [http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/) where xxx.xxx.xxx.xxx is your IP address, do you also have the problem?

---

### Post by moreon on 2007-04-11
> **huygens said:**
> OK, I think I understand why now. :-)
However, I do not have a solution to that yet :(
Just a try (but I think you will have the same problem...) If you go again to [http://www.whatsmyip.org/](http://www.whatsmyip.org/) and check your IP address. Then now, if you type in your browser the address [http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/) where xxx.xxx.xxx.xxx is your IP address, do you also have the problem?

Unfortunately I get the same problem. Also, if I click Cancel in the username/password window I get the attached screenshot in firefox.

> **huygens said:**
> So your router has two interfaces one for the outside world that is now accessible via the dynamic dns thingy, and one for your local network.
Both interfaces can answer to HTTP services. the outside one for your web site, and the inside one for configuring your router (most probably).

You're absolutely right! When I entered the username/password that is given in the router's manual for accessing the router's interface it directed me right to that. I'll search the manual in case I find anything relevant but I have to leave now. If you come up with anything in the meantime, let me know ;)

---

### Post by MJN on 2007-04-11
Try changing the port that your router's web interface is listening e.g. to 8080. That should get it out of the way and not mess with your other port 80 traffic. (Remember though that future connections to manage your router will need to be suffixed with :8080 e.g. [http://192.168.0.1:8080/](http://192.168.0.1:8080/))

Mathew

P.S. I like your Firefox 'Bookmarks Toolbar Folder' entries... the amount I see that seem to have a 'Torrents' folder in there!! :-D

---

### Post by moreon on 2007-04-12
> **MJN said:**
> Try changing the port that your router's web interface is listening e.g. to 8080. That should get it out of the way and not mess with your other port 80 traffic. (Remember though that future connections to manage your router will need to be suffixed with :8080 e.g. [http://192.168.0.1:8080/](http://192.168.0.1:8080/))

Good idea. But I did it and while I  can access now the router's web interface through a different port I still can't view my web page:( Firefox tells me "Firefox can't establish a connection to the server at 88.218.86.43(my current IP address). What else can I do?

---

### Post by MJN on 2007-04-12
Given we, on the outside, can see your site fine it would appear then that your router doesn't support so-called NAT loopback. Specifically, from the inside (LAN) you are unable to connect to internal machines via your router's external IP address. Further info can be found at [http://www.dyndns.com/support/kb/loopback_connections.html](http://www.dyndns.com/support/kb/loopback_connections.html).

A workaround for you would be to add pantofla.homelinux.net to the 127.0.0.1 entry in your /etc/hosts file. Hence when you query the DNS for the IP for pantoflora.homelinux.net you will get your local address back in response and connect directly without going via your router. The rest of us, using your public DNS, will continue to connect on your public IP address.

If you have any other machines internally you would need to add entries to their hosts files too but using your 10. address mapped to pantoflora.homelinux.net.

Mathew

---

### Post by moreon on 2007-04-13
Thanx for the info MJN.

I found another way to view my website from my machine by entering [http://localhost/](http://localhost/) in firefox.
Now I can proceed to the construction of it ;)

You were both very helpful.

---

### Post by MJN on 2007-04-13
You're most welcome.
 
Do be aware however that whilst [http://localhost/](http://localhost/) (or [http://127.0.0.1/](http://127.0.0.1/) etc) will work fine now you will come a cropper if you start to host multiple sites on your machine as there will be no way for Apache to determine which site you're after (as it goes off the name the client supplies to it).
 
Mathew

---

