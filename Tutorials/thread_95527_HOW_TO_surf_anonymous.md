---
title: "HOW TO surf anonymous"
date: 2005-11-26
forum: Tutorials
---

### Post by Dutch on 2005-11-26
Hi after 5 months using Ubuntu the first HOW TO
Be gentle with me !  :-)

=====================================
Go to [www.watismijnip.nl](www.watismijnip.nl)  and write down youre IP ( you need it later)
```

$ sudo apt-get install tor privoxy

```


```

sudo gedit /etc/privoxy/config

```
and ad this line: "  forward-socks4a / localhost:9050 .  " (with the dot at the end)

then go to 
```

https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&id=125

```

click on "Install now" (62 KB file)

then Firefox askes you to install now ? > Click on Install now

After the instalation you have to restart Fire Fox again.
Then go to Extra > Switch Proxy > manage proxies > add > standard > next.

Then fill in:
Next enter the following information into both the HTTP Proxy and SSL Proxy fields. Hostname: 127.0.0.1 Port: 8118. Set up any proxy exceptions you may need and then click on OK.(Do this also for the proxy label)

Then choose in Firefox > extra > switch Proxy > Preferences > and apply "show toolbar"

Now the toolbar wil be shown in FF.
Choose  proxy, your proxy server you just filed in: 127.0.0.1

for other proxys go to:
```

http://proxy.org/tor.shtml

```

Then go to [www.watismijnip.nl](www.watismijnip.nl) and look if youre IP is different from above !
Then it worked, else not you can put you're questions here below.

=====================================

Hope it did work !

Cheers, 

Dutch.

With thanks to:
- ubuntu_demon
- ```

http://www.jgmnet.org/torfaq.html

```
- lindt

---

### Post by manicka on 2005-11-26
Nice How-To

I've added it the Ubuntu Document Storage Facility :)

---

### Post by Dr. Nick on 2005-11-26
Nice, Ive been using this for awhile now, never saw the list of ips though, thanks for the link. 

You might add that it has other uses aswell, Tor can be used with gaim as a socks proxy which will also encrypt your IM's which is nice for using at public wireless hotspots.

---

### Post by Canuckelhead on 2005-11-27
this is not working for me... my IP stays the same when I check it...
running tor from the command line I get...

Nov 27 02:54:03.704 [warn] /var/lib/tor is not owned by this UID (0). You must fix this to proceed.
Nov 27 02:54:03.704 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Nov 27 02:54:03.704 [err] init_from_config(): Acting on config options left us in a broken state. Dying.

what am I messing up?

---

### Post by Dutch on 2005-11-27
[QUOTE=Canuckelhead]this is not working for me... my IP stays the same when I check it...
running tor from the command line I get...

Nov 27 02:54:03.704 [warn] /var/lib/tor is not owned by this UID (0). You must fix this to proceed.
Nov 27 02:54:03.704 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Nov 27 02:54:03.704 [err] init_from_config(): Acting on config options left us in a broken state. Dying.

what am I messing up?[/QUOTE]


If u go to : Fire fox > extra > do u see there SwitchProxy ?
go to preferences and choose : "Show Toolbar" > ok .
Ctr Alt Backsp, restart and then try again.

After choosing the Proxy in the Fire Fox Toolbar from Switch Proxy click on apply.

If that does not work try:
```

sudo /etc/init.d/tor start

```
(with thanks to : AndEat)

Let me know if that works.

---

### Post by lindt on 2005-11-27
My IP didn't change, but I solved in few steps:

```
sudo gedit /etc/privoxy/config
```

and I've added this line:

```
forward-socks4a / localhost:9050 .
``` 
(remember the dot at the end)

I've also commented this two lines to unable privoxy logging:

```
#logfile logfile
#jarfile jarfile
```
I saved the file and restarted privoxy:
```
sudo /etc/init.d/privoxy restart 
```

and finally it's working

---

### Post by Dutch on 2005-11-27
Thanks lindt, I've aded your comments.

---

### Post by Dr. Nick on 2005-11-27
[QUOTE=Canuckelhead]this is not working for me... my IP stays the same when I check it...
running tor from the command line I get...

Nov 27 02:54:03.704 [warn] /var/lib/tor is not owned by this UID (0). You must fix this to proceed.
Nov 27 02:54:03.704 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Nov 27 02:54:03.704 [err] init_from_config(): Acting on config options left us in a broken state. Dying.

what am I messing up?[/QUOTE]

Are you using sudo infront of tor? I think all that means is that the owner of the file is not you.
You do not need to use sudo, If your not using sudo and it still doesnt work then try this command from a terminal  ```
sudo chown *yourusername */var/lib/tor
``` and then try to rereun ```
tor
``` without using sudo

---

### Post by ubuntu27 on 2005-11-27
Hmm? It does work for yo guys? I mean, I used to use Tor + Privoxy for a long time. But now it seem it is dead now. 

Maybe my ISP banned those proxy's IPs...

---

### Post by Dr. Nick on 2005-11-27
It has worked for me recently. Run ```
killall tor
``` then wait a few seconds and run tor, this may help if you get connected to a real slow tor node.
Also do you get the 404s from privoxy in your browser or do you get the web browser ones?

---

### Post by souled on 2005-11-27
How does tor work? I can get my browser to be anonymous, but I'm confused on how it does it. When I use the proxy, pages take a long time to load. Is this because of the proxy? Also, where do you change the proxy with the proxies from the site that Dutch provided?

---

### Post by Dr. Nick on 2005-11-27
> Basically Tor provides a distributed network of servers ("onion routers"). Users bounce their tcp streams (web traffic, ftp, ssh, etc) around the routers, and recipients, observers, and even the routers themselves have difficulty tracking the source of the stream

The proxy can slow you down some, depends on its user load at the time, killing and then restarting tor may connect you to a better proxy. You really dont have to change the proxies, it does it for you, just set your browser to use 127.0.0.1:8118 and the tor application will handle connections out.

I think it also encrypts it for you aswell which can cause it to be a little slower.

link to tor site
[http://tor.eff.org/](http://tor.eff.org/)

---

### Post by souled on 2005-11-27
I just installed InitNG, and I told it to run privoxy and tor, but when I switch my proxy in Firefox, I get an error about not being able to connect to the proxy because of a bad configuration. Any suggestions?

Edit: I discovered that the directories in the tor.i file are wrong. For the daemon, it points to /usr/bin/tor, but that file is not there, only tor-resolve. Where is tor?

---

### Post by Dr. Nick on 2005-11-27
[QUOTE=souled]I just installed InitNG, and I told it to run privoxy and tor, but when I switch my proxy in Firefox, I get an error about not being able to connect to the proxy because of a bad configuration. Any suggestions?[/QUOTE]

Switch proxy to what? The only proxy you need to define in FF for tor+privoxy is 127.0.0.1 and port 8118. I dont use switchproxy but instead just go to Edit-Prefrences-General-Connection Settings and set it to manual and 127.0.0.1 port 8118 to use tor, then automatic to not use tor

---

### Post by souled on 2005-11-27
When I change it to 127.0.0.1, I get "couldn't connect to proxy server, check your configurations." I'm looking at tor.i and privocy.i (for InitNG), and the tor.i paths are correct ```

service daemon/tor {
        need = system/mountfs net/lo virtual/networking daemon/privoxy
        daemon = /usr/sbin/tor
        daemon_args = --chuid tor
        pid_file = /var/run/tor/tor.pid
        HOME=/var/lib/tor
} 

```

But the privoxy.i paths aren't right.

```


service daemon/privoxy {
        need = system/initial system/localmount net/lo
        use = net/eth0
        daemon = /usr/sbin/privoxy
        daemon_args = "/etc/privoxy/config"
        pid_file = /var/run/privoxy.pid
}

```

There is not /var/run/privoxy.pid. Does that make a difference?

Edit: I know it has something to do with InitNG because when I boot with the init.d stuff, everything works

---

### Post by Dr. Nick on 2005-11-27
Oh, I have never used InitNG so I am not sure how to set it up that way.
I have a privoxy.pid file under /var/run so I am not sure why you dont Mine is owned by root for some reason. If I remember when I set mine up way back when I had a problem with my config privoxy file not being in my home directory, you have any similar problems? That may be part of the problem Im not sure. Hope you can figure it out.

---

### Post by Nano on 2005-12-01
Looks pretty cool.
I'm just wondering, is there a way to use tor also with Nicotine (soulseek client)?

---

### Post by Danielle on 2005-12-01
[QUOTE=souled]How does tor work? I can get my browser to be anonymous, but I'm confused on how it does it. When I use the proxy, pages take a long time to load. Is this because of the proxy? Also, where do you change the proxy with the proxies from the site that Dutch provided?[/QUOTE]
hi, the way it works is your packets enter TOR's servers at the first server all packets are encrypted they then go on to the next server then the next, that's what slows you down traveling through those extra servers, and the more people using them the less bandwidth they have, but the more anonymous you are.

your ISP can see you going into the first server but not after that, it's then possible to see all the  packets leaving the last server, but at that point no one will know whos packets are whos from the out-side. TOR will know but i don't think they keep records.

---

### Post by Dr. Nick on 2005-12-01
[quote=Nano]Looks pretty cool.
I'm just wondering, is there a way to use tor also with Nicotine (soulseek client)?[/quote]

If the program supports socks proxy connections you can use tor. Just set it to 127.0.0.1:5190 I believe.

_***However***_ At one time they asked that tor not be used with any p2p apps due to the amount of traffic that it creates would cause heavy load on the servers and hinder the other users. I am not sure when the statements were made (Date) so this may or may not be applicable if they have since had alot of new servers. Also the operators of serves can filter which ports can be used to cut down on using it as a proxy to send spam, so they could in-effect block popular p2p ports hindering its usage aswell.

If its supported and you choose to use it I would just try to be respectable and not transfer gigs of data per day :) Also realize that your transfer speeds will not be what they used to be, so download and upload speeds will take a hit.

---

### Post by thewanderer on 2005-12-01
> Originally Posted by souled
How does tor work? I can get my browser to be anonymous, but I'm confused on how it does it. When I use the proxy, pages take a long time to load. Is this because of the proxy? 

Each hop in the proxy chain adds another layer of encryption (known as onion routing) - so that the proxies in the middle of the chain have no idea about the source, destination or contents of the traffic. They only know of the previous hop and the next hop.

As far as i know the only known attack against this (apart from brute forcing multiple layers of encryption) is for a hostile entity to control both the entry point proxy and the exit proxy. If you control entry and exits points of the network then you could sniff the exit traffic / destination ip and determine the source IP from time matching the sessions.

Not easy to do - this would require significant resources (government agencies), i believe there are ways to configure tor for the ultra paranoid types to restrict the entry and exit proxies to systems outside of USA and Germany. Apparently two of the world leaders in surveillance.  :cool:

---

### Post by ubuntu27 on 2005-12-01
I think that there are way TOO much Tor Client. 
We need more people who provide Tor Server. :D 

TOr: [http://tor.eff.org/](http://tor.eff.org/)

---

### Post by bionnaki on 2005-12-02
does this make bittorrent use anonymous?

---

### Post by skeezer65134 on 2005-12-02
I've used this before, and it's pretty awesome. However, I'm having problems getting it running now....

When I start it via 'sudo /etc/init.d/tor start' and 'sudo /etc/init.d/privoxy start' it says all is well. However, trying to connect to the proxy with Firefox fails. On top of that, running an nmap on my machine shows ports 9050 and 8118 are both closed.

I have tried killing it via the init scripts and running 'sudo killall -9 tor' and 'sudo killall -9 privoxy' and confirming that they both stopped.

Any ideas?

---

### Post by ubuntu_demon on 2005-12-02
duch : thnx for the howto. Please also put the links I gave you in there.

---

### Post by Dr. Nick on 2005-12-02
[quote=skeezer65134]I've used this before, and it's pretty awesome. However, I'm having problems getting it running now....

When I start it via 'sudo /etc/init.d/tor start' and 'sudo /etc/init.d/privoxy start' it says all is well. However, trying to connect to the proxy with Firefox fails. On top of that, running an nmap on my machine shows ports 9050 and 8118 are both closed.

I have tried killing it via the init scripts and running 'sudo killall -9 tor' and 'sudo killall -9 privoxy' and confirming that they both stopped.

Any ideas?[/quote]

Make sure you put the line for foward socks in your privoxy config, the line with the dot(.) at the end. Running nmap from a different IP on your machine should show them closed, when privoxy starts it say "listening on port 8118 for** local** connections only" so I think it is supposed to look like that. just try and start tor and privoxy without the /etc/init.d, Just run "tor" and "privoxy" from a terminal and see what happens

---

### Post by skeezer65134 on 2005-12-02
[QUOTE=Dr. Nick]just try and start tor and privoxy without the /etc/init.d, Just run "tor" and "privoxy" from a terminal and see what happens[/QUOTE]
Yes, I added that line, and yes I was running nmap from the same machine that I installed Tor and Privoxy on (this one).
```
#        Sample Configuration File for Privoxy
#
#  Copyright (C) 2001-2004 Privoxy Developers http://privoxy.org
#
#  $Id: config,v $
#
# Added for Tor support
forward-socks4a / localhost:9050 .
```


Running on their own I get this:
```
$ sudo tor
Dec 02 08:58:49.920 [notice] Tor v0.1.0.15. This is experimental software. Do not rely on it for strong anonymity.
Dec 02 08:58:49.977 [warn] /var/lib/tor is not owned by this UID (0). You must fix this to proceed.
Dec 02 08:58:49.977 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Dec 02 08:58:49.978 [err] init_from_config(): Acting on config options left us in a broken state. Dying.
$ sudo privoxy
Dec 02 08:59:03 Privoxy(b7d606c0) Fatal error: can't check configuration file '/{$PWD}/config':  No such file or directory
Dec 02 08:59:03 Privoxy(b7d606c0) Fatal error: can't check configuration file '/{$PWD}/config':  No such file or directory
$
```
I filled in {$PWD}, but basically it would just look for the config file anywhere that I tried to run it from.

Running 'ps aux' I see that they run as the following:
Tor - /usr/sbin/tor
Privoxy - /usr/sbin/privoxy --pidfile /var/run/privoxy.pid --user privoxy /etc/privoxy/config

So, this is how I ran the both of them (this time, as root, and not just with sudo):
```
# /usr/sbin/tor
Dec 02 09:09:24.772 [notice] Tor v0.1.0.15. This is experimental software. Do not rely on it for strong anonymity.
Dec 02 09:09:24.833 [warn] /var/lib/tor is not owned by this UID (0). You must fix this to proceed.
Dec 02 09:09:24.834 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Dec 02 09:09:24.834 [err] init_from_config(): Acting on config options left us in a broken state. Dying.
# /usr/sbin/privoxy --pidfile /var/run/privoxy.pid --user privoxy /etc/privoxy/config
Dec 02 09:09:39 Privoxy(b7d786c0) Info: loading configuration file '/etc/privoxy/config':
Dec 02 09:09:39 Privoxy(b7d786c0) Info: Privoxy version 3.0.3
Dec 02 09:09:39 Privoxy(b7d786c0) Info: Program name: /usr/sbin/privoxy
Dec 02 09:09:39 Privoxy(b7d786c0) Info: Listening on port 8118 for local connections only
#
```

OK, so Privoxy starts, but not Tor (which is odd because Tor was working last night). Despite it saying it's working and listenning on port 8118, nmap still shows nothing. Odd indeed. Maybe not..... when I do 'telnet localhost 8118' it logs in. Typeing "help" results in it exiting saying "HTTP/1.0 400 Invalid header received from browser". Maybe it really is running after all.

Starting Tor from the init script (because it still fails from the command line) gives me:
```
# /etc/init.d/tor start
 * Starting tor daemon (tor)...                                                                                                                                          Dec 02 09:12:39.343 [notice] Tor v0.1.0.15. This is experimental software. Do not rely on it for strong anonymity.
                                                                                                                                                                  [ ok ]
#
```

This leads me to believe that it's running. Again, using telnet to connect works, but it exits on any command (as I guess I'd expect since I don't know what commands to use).

So, time to fire up Firefox. Setting it to use 127.0.0.1:8118 results in it connecting to Privoxy now, but Tor is still MIA. Instead Privoxy results in a 404 error regardless of what page I try to load. 

```
No such domain

Your request for http://www.google.com/ could not be fulfilled, because the domain name www.google.com could not be resolved.

This is often a temporary failure, so you might just try again. 
```

So, I'm half way there.... kinda. Still seems odd that the init script doesn't want to load it right. I'm missing something, what is it?! The [Official Doc]("http://tor.eff.org/cvs/tor/doc/tor-doc-unix.html") only says to add that one line to the Privoxy config and leave the rest alone, which I have done before. This was so easy to set up on Gentoo, and it should be just as easy here. Any more ideas?!

---

### Post by skeezer65134 on 2005-12-02
Gah! Now it magically workswhen running from the init scripts! What is this, Windows with it's "I work sometime, other times I don't" attitude?!

The only extra thing I did was telnet to localhost:9050 and type 'HTTP-REQUEST' (sans the ') and I got this....
```
# telnet localhost 9050
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
HTTP-REQUEST
HTTP/1.0 501 Tor is not an HTTP Proxy
Content-Type: text/html; charset=iso-8859-1

<html>
<head>
<title>Tor is not an HTTP Proxy</title>
</head>
<body>
<h1>Tor is not an HTTP Proxy</h1>
<p>
It appears you have configured your web browser to use Tor as an HTTP Proxy.
This is not correct: Tor provides a SOCKS proxy. Please configure your
client accordingly.
</p>
<p>
See <a href="http://tor.eff.org/documentation.html">http://tor.eff.org/documentation.html</a> for more information.
<!-- Plus this comment, to make the body response more than 512 bytes, so IE will be willing to display it. Comment comment comment comment comment comment comment comment comment comment comment comment.-->
</p>
</body>
</html>
Connection closed by foreign host.
```
This told me Tor was actually running. Fired up Firefox, and it works fine now. Sigh...... Thanks for the help I guess.

---

### Post by Dr. Nick on 2005-12-02
I see an error when tor started up about not being owned by this uid, If you go back to page one I showed how to fix that, Ive had it aswell. I will run nmap on my self and edit this post with  its results

EDIT
Nmap didnt show either tor or privoxy open on mine yet it works
To fix the tor uid error run 
sudo chown *yourusername */var/lib/tor
then killall tor and rerun tor

---

### Post by Nimefurahi on 2005-12-04
Very nice how-to, Dutch, and thank you.
Were you once of the Gentoo community?
Cheers!

---

### Post by Knomefan on 2005-12-07
Just wanted to say thanks for the great howto.
Works like a charm here, well done.

---

### Post by ace2005 on 2005-12-10
> Privoxy Configuration access denied

The feature you are trying to access has either been disabled by the Privoxy administrator, or you came here by following an unsafe external link.

All enabled features are accessible from the main menu.

I just get this when i try to edit stuff, what do i have to do to allow myself to edit it using a browser?

---

### Post by Twizz on 2005-12-10
Hello, is there a way to get this to also hide what browser I'm useing?

---

### Post by souled on 2005-12-11
I think there's an extension called AgentSwitcher. It allows your to mask your browser as another browser. Google it.

---

### Post by Twizz on 2005-12-11
[QUOTE=souled]I think there's an extension called AgentSwitcher. It allows your to mask your browser as another browser. Google it.[/QUOTE]

I found the extension.  Thanks for your help

---

### Post by bierpullen on 2005-12-12
Thanks
Just wanted to say thanks for the great howto.
Works like a charm here, well done.
This is great !!!
=D> 
------------------------------------------


Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.
[http://www.antarctica-rbak.nl/ubuntu](http://www.antarctica-rbak.nl/ubuntu)

---

### Post by royg1234 on 2005-12-16
3 questions:

[LIST=1]
[*]Privoxy gives me a foreign IP, so when I go to [www.google.com](www.google.com) it speaks to me in a different language.  Can I set a preference for USA IPs?
[*]Is there *any* way to make it faster?  It's unusably slow.
[*]How do I get this to work with Gaim?
[/LIST]

Thanks

---

### Post by Dr. Nick on 2005-12-16
[quote=royg1234]3 questions:[LIST=1]
[*]Privoxy gives me a foreign IP, so when I go to [www.google.com]("http://www.google.com") it speaks to me in a different language.  Can I set a preference for USA IPs?
[*]Is there *any* way to make it faster?  It's unusably slow.
[*]How do I get this to work with Gaim?[/LIST]Thanks[/quote] 
1. You can hit google.com in englsih link, their is a way to make certain sites use certain ip's but its not real easy, I had a link but never used it. I will dig it out and post here if I can find it.
----------
EDIT Counldnt find the link but its a known problem. Wiki entry [here. ]("http://wiki.noreply.org/noreply/TheOnionRouter/TorFAQ#GoogleLanguage")
One solution would be to tell your browser to not use a proxy for google but then you wouldnt be anonymous on the site. Google customizes results to your ip so using tor can give some neat results :)
-----------
2. Thats a tough one, It is luck really. If it is unbearanbly slow open a terminal and run** killall tor **then relaunch tor and you may get connected to a faster route.

3. To work with gaim or any other application supporting proxy, Open up the prefrences and tell it to use a socks server and set it to ip 127.0.0.1 and port 9050. If possible use socks4a for better security but either socks4 or 5 should work fne aswell. Ive heard that some socks versions other than 4a leak dns info but have never tested it. When you are using a socks server privoxy is not involved just tor

---

### Post by Stambo00 on 2005-12-18
I just wanted a small detail cleared for me about the internet slowing down using this how-to. Will this will slow down my internet connection in firefox? or my internet as a whole?

---

### Post by Dr. Nick on 2005-12-18
It will slow down whatever program you use it with, If you dont set up the program to use a proxy you will have your regular speed just not be anonyomus, So if you connect with it in firefox you will be slowed down in firefox, But if you are download a torrent or chatting at the same time those wont be slowed down

---

### Post by Stambo00 on 2005-12-18
Cheers, I'd just like to express my thanks for a great how-to. Works beautifully.

---

### Post by poptones on 2005-12-18
There's still some holes here. The simplest exploit with the config given is just to get your ISP server logs: if you don't use dns caching they'll still know every site you visit. If you set privoxy to forward dns requests all you're doing is sending the packets out to tor, which encrypts the traffic and sends it hop to hop *only to send the dns request right back to your isp*. It would be trivially easy to correlate these "alien" dns requests with your outgoing traffic.

If you want to be *anonymous* make sure you don't use your isp's dns configuration; set your dns resolution to the public dns hosts scattered across the globe.

Oh, and don't forget this doesn't "protect" you on gaim or usenet or email unless you also set those clients to use the socks proxy provided by tor.

---

### Post by Knomefan on 2005-12-18
> **poptones]There's still some holes here. The simplest exploit with the config given is just to get your ISP server logs: if you don't use dns caching they'll still know every site you visit. If you set privoxy to forward dns requests all you're doing is sending the packets out to tor, which encrypts the traffic and sends it hop to hop *only to send the dns request right back to your isp*. It would be trivially easy to correlate these "alien" dns requests with your outgoing traffic.

If you want to be *anonymous* make sure you don't use your isp's dns configuration said:**
> 
I think privoxy should take care of the dns problem:

[QUOTE]The Problem. When your applications connect to servers on the Internet, they need to resolve hostnames that you can read (like tor.eff.org) into IP addresses that the Internet can use (like 209.237.230.66). To do this, your application sends a request to a DNS server, telling it the hostname it wants to resolve. The DNS server replies by telling your application the IP address.
...
So what can I do? 
For HTTP (web browsing), use a socks4a-capable HTTP proxy, such as Privoxy. See the Tor documentation for more information.

[http://wiki.noreply.org/noreply/TheOnionRouter/TorFAQ#SOCKSAndDNS](http://wiki.noreply.org/noreply/TheOnionRouter/TorFAQ#SOCKSAndDNS)

---

### Post by poptones on 2005-12-18
Uhhh... no, that isn't "taking care of it" at all. if your internet configuration involves DHCP then when you connect to your ISP it sets your DNS servers to its domain. When you "proxy" these requests through privoxy and tor all you are doing is encrypting the request at tor, sending it through multiple hops along that network only to have it exit the last machine in the chain right back to your ISP. That remotely proxied request is getting sent, in cleartext, right back to your ISP. Now your ISP has a record in their logs of both your entry point into the network and your exit point - completely **not** anonymous to anyone able to impound those records.

> We need a way to intercept DNS requests so they don't "leak" while we're trying to be anonymous. (This happens because the application does the DNS resolve before going to the SOCKS proxy.) One option is to use Tor's built-in support for doing DNS resolves; but you need to ask via our new socks extension for that, and **no applications do this yet**. A nicer option is to use Tor's controller interface: you intercept the DNS resolve, tell Tor about the resolve, and Tor replies with a dummy IP address. Then the application makes a connection through Tor to that dummy IP address, and Tor automatically maps it back to the original query.

---

### Post by Knomefan on 2005-12-18
[QUOTE=poptones]Uhhh... no, that isn't "taking care of it" at all. if your internet configuration involves DHCP then when you connect to your ISP it sets your DNS servers to its domain.
[/quote]
I'm probably just confused (as is so often the case with me) but could you explain what using your ISP's DNS has to do with using DHCP?

[QUOTE=poptones]
 When you "proxy" these requests through privoxy and tor all you are doing is encrypting the request at tor, sending it through multiple hops along that network only to have it exit the last machine in the chain right back to your ISP. That remotely proxied request is getting sent, in cleartext, right back to your ISP. Now your ISP has a record in their logs of both your entry point into the network and your exit point - completely **not** anonymous to anyone able to impound those records.[/QUOTE]
Again, I'm confused. Doesn't it boil down to your ISP having the record of you connection to a tor server and the record of another tor server looking up the DNS on the ISP's nameserver?

---

### Post by poptones on 2005-12-18
OK, where I am on dialup my ISP is a relatively small provider that provides service only in this state. In that regard the odds of me entering and exiting via this ISP are damn slim.

BUT, let's consider someone on... pacbell, or at&t, or even aol or netscape.

Those services have millions of customers and the odds of going through the tor net and ultimately exiting within the same /8 are not insignificant.

When forwarding DNS requsts through privoxy you get a LOT of timeouts which end up in 404s. Tor "servers" that provide dns service back to their connections generate a significant amount of dns traffic. This alone is enough to draw attention and it's a safe bet any automated sniffing equipment will be logging machines fitting these traffic patterns. 

DNS is one of the weakest links in all this. If you *really* want to have some amount of privacy you need to configure a local dns host and have it peer to some of the public dns servers. You can even use tor to do it; the thing is, once you have a local DNS cache you minimize that outgoing traffic - most of your requests now go directly to their resolved destination, which makes it significantly harder to correlate your traffic patterns.

---

### Post by Knomefan on 2005-12-18
[QUOTE=poptones]
DNS is one of the weakest links in all this. If you *really* want to have some amount of privacy you need to configure a local dns host and have it peer to some of the public dns servers. You can even use tor to do it; the thing is, once you have a local DNS cache you minimize that outgoing traffic - most of your requests now go directly to their resolved destination, which makes it significantly harder to correlate your traffic patterns.[/QUOTE]
Now this is something I can agree with.

---

### Post by Dr. Nick on 2005-12-18
How would you go about something like this?

---

### Post by Danielle on 2005-12-23
hi, i had a quick look in synaptic and i think proxychains, chained together with TOR and Privoxy should stop the DNS requests being leaked. however, i think you shouldn't rely on me especially as i have only thought about it for a minute or so. get an experts opinion.

OK, i found this, this will work.
[http://www.imperialviolet.org/deerpark.html](http://www.imperialviolet.org/deerpark.html)

---

### Post by jing10 on 2005-12-25
there is no need to install any program, you can use webbased phproxy like this.

[http://radiofarda.be]("http://http://radiofarda.be")

they are fast , free and need nothing to install on your pc. just go to that site and put the site adress in

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-25
You must be a spammer - three posts here and every one of them points to a proxy server in belgium.

FYI Belgium explicitly outlaws telecommunications anonymity and anonymizing services. If you're going to use a proxy server make sure it isn't just a honeypot set up by someone phishing for passwords and credit card info.. and make sure it's in a country that actually offers meaningful protection for telecom users.

---

### Post by ace2005 on 2005-12-25
But what he said goes along with the title of the threads and he didn't start any of them

HOWTO: Surf and IM anonymously using tor and privoxy
General - HOW TO surf anonymous
how to surf anonymously ?

I wouldn't have thought of that as spam, but the posts are identical, but interesting info about Belguim

Link points to: [http://http//radiofarda.be](http://http//radiofarda.be)

lol

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-25
And that's relevant to whether or not his posts (all phrased identically, all concerning a single issue) are spam?

were you not here last week when everyone on the board got spammed by a service offering bots to post to these boards? This is exactly what they do.

---

### Post by ace2005 on 2005-12-25
Cleaver bots, i was here but i guess i never say any of that

That proxy is broken, i went to google, clicked on images and it said "Error: Please supply a valid URL"

None of the links above the google search box work

anyway lets get back on topic

---

### Post by j-strap on 2005-12-28
NOTE
====

What poptones states above is false: there are no DNS requests to your own DNS server. 

TOR does not send DNS requests to your system's DNS server. If your browser uses SOCKS4a or SOCKS5 correctly to connect to the TOR network, there are no local DNS leaks and the browser sends only unresolved hostnames to the TOR network. The TOR exit node resolves the hostname using its own DNS services however they may be configured. This is the way SOCKS works - the browser sends only the hostname (it does not send any details of your systems DNS configuration - why should it?).

Just use privoxy or configure firefox according to the link posted by Danielle above. There is no need to install a local DNS server or any of that stuff.

j-

---

### Post by Zerocool10482 on 2005-12-31
Where on the page do I put this code?

forward-socks4a / localhost:9050 .

Please put the lines that are before and after so I can look for that. Thanks.

---

### Post by Dr. Nick on 2006-01-01
[quote=Zerocool10482]Where on the page do I put this code?

forward-socks4a / localhost:9050 .

Please put the lines that are before and after so I can look for that. Thanks.[/quote]

You can put it anywhere in the privoxy config file, I think it is in alphabetical, but you can put it wherever you want in the file and it should work

---

### Post by atlas95 on 2006-01-01
Thanks you very well for this how to!
Works directly...
But I have the same question of *** how to surf anonymous? it is possible?
Best regards

---

### Post by Sandpainting on 2006-01-01
sand@nux-12:~$ sudo apt-get install tor privoxy
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package tor

What's wrong? I'm very new for linux and I want to test this...

---

### Post by Dr. Nick on 2006-01-01
[quote=Sandpainting]sand@nux-12:~$ sudo apt-get install tor privoxy
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package tor

What's wrong? I'm very new for linux and I want to test this...[/quote]

Have you enabled the universe reposiroty? You can do it through synaptic or by editing the /etc/apt/sources.list file. If you need help doing this the forums are full of info, or if you still need help after you can post back here

---

### Post by majikstreet on 2006-01-01
I didn't use your instructions, but they look nice.. another tip: most apps can be "torified" by doing "torify appname".. I've only tested it with irssi, though.

---

### Post by Sandpainting on 2006-01-02
[QUOTE=Dr. Nick]Have you enabled the universe reposiroty? You can do it through synaptic or by editing the /etc/apt/sources.list file. If you need help doing this the forums are full of info, or if you still need help after you can post back here[/QUOTE]
Thanks a lot Nick, now tor is working fine. :razz:

---

### Post by ubuntumaneh on 2006-01-02
SwitchProxy doesn't work on firefox 1.5, as is noticed in the page for download. Also I gave it a try. It doesn't work.
So, does anyone know a work around of this? Maybe, some other extension.
Thanks

---

### Post by ubuntumaneh on 2006-01-02
Solved. For firefox 1.5, download have to be done from:
[http://www.roundtwo.com/product/switchproxy](http://www.roundtwo.com/product/switchproxy)

Thanks

---

### Post by christmasisland on 2006-04-07
I'm using Firefox 1.5.0.1 and got the extension here:

[https://addons.mozilla.org/firefox/125/](https://addons.mozilla.org/firefox/125/)

It worked, also.

---

### Post by BabyBoy on 2006-06-18
Hey, very nice tutorial!! done what you said works fine! thank you ;) 


Is it possible to go through proxy through terminal apps? 

Im sure there was a app to force all your applications to use the proxy :S 

i aint too sure good tutorial anyhow :) :)

---

### Post by Iesos on 2006-06-22
Thanks for the How To. Got some question though:
1. Is it realy running? I get the different IP-address, but trying to run tor:
```
$ tor
Jun 23 01:42:33.981 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
Jun 23 01:42:33.982 [notice] options_validate(): Your ContactInfo config option is not set. Please consider setting it, so we can contact you if your server is misconfigured or something else goes wrong.
Jun 23 01:42:33.983 [warn] resolve_my_address(): Address 'totoro' resolves to private IP '127.0.0.1'. Tor servers that use the default DirServers must have public IP addresses.
Jun 23 01:42:33.983 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.
```
whats that about? Ant if I get that error, is it realy working as it should?

2. This is about torify, I get the error above. But no errors when I run:  $torify app-name . Does this mean its running correctly or not? Can I check it in some way?

---

### Post by matko on 2006-07-07
hello. nice howto. how should i manage to work privoxy with squid?
is here anybody that could help me to set up squid and privoxy working together?

thanx

---

### Post by Albi on 2006-07-07
[http://www.safehazard.com](http://www.safehazard.com)

You can do it without TOR, and this is very secure too.

---

### Post by wirelessman on 2006-07-17
What if you are behind a router?  Will not your traffic still noted as moving through your router (the ip it has**from your isp** as well as its MAC address)?:confused:

---

### Post by equilibrium on 2006-07-27
I installed this but I noticed loads of random connections being made when my machine was idle?

I have conky setup to display active(ESTABLISHED) connections using netstat and every now and then I get about 5 different connecetions :confused: 

So I removed them from startup and made some scripts to start and stop both tor and privoxy, so it can be used as and when I need it.

Anyone know why there were random connections? :( very strange, not sure if it's worth worrying about or not tho. Better to be safe than sorry tho :D

---

### Post by GStubbs43 on 2006-07-30
Thanks, works great, except for one part. When I'm using Chatzilla, it shows my ip as my real ip and not the fake one. When I do a Whois of myself in chatzilla, it shows <xx-xxx-xxx-xx.ptldme.east.verizon.net> Which is completly correct. Can I use this trick in Chatzilla? Thanks!

---

### Post by j-strap2 on 2006-07-31
I'd edit your post and remove the IP address you posted - it makes you a bit of a target for idiots.

I haven't used chatzilla for a long time but I recall that it can't be configured to work with a proxy. You could run it use torify or similar. Better, you can use another client - Gaim works well with Tor and supports most IM protocols. Gaim also has a plugin for the OTR encryption package.

---

### Post by cyclister on 2006-07-31
First all my java flash etc are gone now :( 

My ff will not let the thing install by itself :( when Im trying to do that 
[https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&id=125](https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&id=125)
Have tried to tar and install that one with no luck?
Have a chrome folder in my /home sounds pretty wrong.

Do not really get this how exact where do you input 
forward-socks4a / localhost:9050 . 

Where do I switch proxy?

Then Firefox > extra > switch Proxy > Preferences > and apply "show toolbar"
This Im not getting at all Im looking in my ff like every where but cant really find this one?

What do you sugget me to do?

This sounds to me like Im should start all over again and get my mozilla add this plugin for starter but how?
Like remove package or?

Would be nice to hear what you should have done plz

---

### Post by stoft on 2006-07-31
Aside from switchproxy there's also the torbutton addon for mozilla/firefox:
[https://addons.mozilla.org/firefox/2275/]("https://addons.mozilla.org/firefox/2275/") 
Simpler to configure and less obtrusive in the browser window.

---

### Post by mcman42 on 2006-07-31
Nice job, works very well for me. What should I do if I dont want tor and privoxy to start with boot? I want to turn them on by hand when I need and them to be off all the rest time. How do I do that?

---

### Post by lonetree on 2006-07-31
Is there any step-by-step guide for 6.06? if seems that I have hard time making it work

---

### Post by stoft on 2006-08-01
> **mcman42 said:**
> Nice job, works very well for me. What should I do if I dont want tor and privoxy to start with boot? I want to turn them on by hand when I need and them to be off all the rest time. How do I do that?

Do you mean the daemon(s) or just in the browser? If it's just in the browser (firefox) it's enough to have the torbutton or switchproxy addon to switch it on/off when you need to.

> **lonetree said:**
> Is there any step-by-step guide for 6.06? if seems that I have hard time making it work

Be more specific, what is the problem?

---

### Post by mcman42 on 2006-08-01
I meant the daemons. I got them not to load on boot through System->Administration->Boot-up manager and it works nice so I got it to work on my own.

But I am still wondering what would I have to do if I wanted to change this through terminal instead of graphic interface. What commands would I have to use?

---

### Post by doomsday on 2006-08-01
this isn't "anonymous".  in fact, you are just spreading your ip all over the world now.  so that other's can use it, for their dirty deeds.  can you make your house invisible?  can you erase your face? no and you can't erase your internet traces either.

---

### Post by j-strap2 on 2006-08-01
> **doomsday said:**
> this isn't "anonymous".  in fact, you are just spreading your ip all over the world now.  so that other's can use it, for their dirty deeds.  can you make your house invisible?  can you erase your face? no and you can't erase your internet traces either.

^^This is nonsensical.

There is no such thing as true anonymity, but there are degrees of anonymity. Tor is not perfect but it does 2 things:

1. Encrypts traffic between you and your ISP so that your ISP cannot see where you are browsing and what you are browsing.

2. Disguises the connection to the remote server by multiple encrypted hops through intermediate nodes so that the remote server cannot determine your IP.

mcman42

You could disable tor in the system services and then run it manually from the command line - just use the 'tor' command. You might have to kill it with a 'killall tor'.

---

### Post by stoft on 2006-08-01
> **j-strap2 said:**
> 
1. Encrypts traffic between you and your ISP so that your ISP cannot see where you are browsing and what you are browsing.

Which is good enough for me, it allows me to connect with jabber on the standard port AND avoid my employer's websense filter. ;)

---

### Post by Metroid48 on 2006-08-03
Yah, it worked!

A few things though. Firstly, internet is MUCH slower now. Also, I'm not sure exactly where to put the info. It has the following fields: HTTP Proxy, SSL Proxy, FTP Proxy, Gopher Proxy, SOCKS Proxy, and No Proxy for. each (aside from the last) also have a port field. I just filled in the data for every one. Is that right?

-Metroid48

---

### Post by stoft on 2006-08-03
> **Metroid48 said:**
> internet is MUCH slower now

Copied from [the wikipedia entry on tor]("http://en.wikipedia.org/wiki/Tor_(anonymity_network)"):

> It is considered impolite to transfer massive amounts of data across the Tor network - [COLOR="Red"]the onion routers are run by volunteers using their own bandwidth at their own cost[/COLOR].

In other words, your connection is as good as your fellow users make it. If you want to speed things up, and save bandwidth, don't load massive things using Tor and use it only for the sites where you really want/need to be anonymous.

---

### Post by cyclister on 2006-08-03
Im running tor besides this one.
Do not know what Im doing wrong but hey this privproxy do not works for me, did something wrong in that privproxy configuration file.


Some socks4 forward lines are wrong :(

---

### Post by j-strap2 on 2006-08-04
cyclister, to configure privoxy, you need to edit its config file and insert the single line

```
forward-socks4a / localhost:9050 .
```

Remember to include the fullstop at the end of the line.

---

### Post by bluntu on 2006-08-05
It is very important that you off the TIMESTAMPS because if that thing is on you're dead.

[Tracking PCs anywhere on the Net](http://www.zdnet.com.au/news/security/0,2000061744,39183346,00.htm)

Luckily there is a way to off this and this is what I like about LINUX. It allows you to control how it works! 

Visit: [http://www.linuxguru.co.uk/sblog/index.php?cat=2](http://www.linuxguru.co.uk/sblog/index.php?cat=2)   and just follow that instruction. You can copy his whole sysctl.conf and replace it with yours (yours is empty by default I believe).

Now visit: [www.speedguide.net:8080](www.speedguide.net:8080)

To varify.     

NOTE: Before you do any of this I recommend that you visit speedguide (link above) and see if your: Timestamps (RFC1323) is "ON"

Then visit it again AFTER you off the timestamps and you will see that it will be OFF. This is important so get it done before you surf with TOR.

Also if you want to check your IP try this site: [samair](http://www.samair.ru/proxy/proxychecker/results.htm) Which reports more than just IP! If your setting is incorrect this site will reveal your true IP and last, use "User Agent Switcher" (Firefox) to not report your browser because with it people can detect your OS.

Good luck.

---

### Post by Christopher on 2006-08-05
> **bluntu said:**
> It is very important that you off the TIMESTAMPS because if that thing is on you're dead.

[Tracking PCs anywhere on the Net](http://www.zdnet.com.au/news/security/0,2000061744,39183346,00.htm)

Luckily there is a way to off this and this is what I like about LINUX. It allows you to control how it works! 

Visit: [http://www.linuxguru.co.uk/sblog/index.php?cat=2](http://www.linuxguru.co.uk/sblog/index.php?cat=2)   and just follow that instruction. You can copy his whole sysctl.conf and replace it with yours (yours is empty by default I believe).

Now visit: [www.speedguide.net:8080](www.speedguide.net:8080)

To varify.     

NOTE: Before you do any of this I recommend that you visit speedguide (link above) and see if your: Timestamps (RFC1323) is "ON"

Then visit it again AFTER you off the timestamps and you will see that it will be OFF. This is important so get it done before you surf with TOR.

Also if you want to check your IP try this site: [samair](http://www.samair.ru/proxy/proxychecker/results.htm) Which reports more than just IP! If your setting is incorrect this site will reveal your true IP and last, use "User Agent Switcher" (Firefox) to not report your browser because with it people can detect your OS.

Good luck.

The last link you posted(samair) i went to it and im not using anything except the default Firefox and its telling me this:  Resume: You are using  hight anonymous (elite) proxy (if you are using proxy). But it does tell my correct Ip addy. Would surfing annoymously hide my IP addy? Oh and my Timestamp is off by default. Thank you in advance.

---

### Post by bluntu on 2006-08-05
I visit samair regularly to check my IP but I do find that it's a bit strange in that it assumes you use a PROXY by default each time you visit it (or maybe I'm missing something). I tend to ignore the "Resume:" part and fixed my eyes on the first two (IP and Country), that should be enough.

Just today I did something wrong and it detected my real IP and when it does it will be in "RED" so you won't missed. Sometimes I forget to void my Agent (Browser header stuff) so by visiting there I tells me about it.

---

### Post by GuitarHero on 2006-08-06
Why not just use a proxy site?  I set my own one up to bypass my schools web filters.

---

### Post by Razer(x) on 2006-08-06
Does it slow down my internet connection??...(my english is not so good)

---

### Post by cyclister on 2006-08-06
But it wont work :( and my java flash wont work either while it are up. 

Did read on priv's homesite that you should somehow configurate it a little more I guess :( 

But I have somelines wrong in my file think in the midle somewhere, did put that line in their and did some wrong.

Might be me always something that wont work

[HTML]
#  Examples:
#
#      From the company example.com, direct connections are made to all
#      "internal" domains, but everything outbound goes through their
#      ISP's proxy by way of example.com's corporate SOCKS 4A gateway
#      to the Internet.
#
#        forward-socks4a   /              socks-gw.example.com:1080   www-cache.example-isp.net:8080
#        forward-socks4a / 
#
#      A rule that uses a SOCKS 4 gateway for all destinations but no
#      HTTP parent looks like this:
#
#        forward-socks4   /               socks-gw.example.com:1080  .
[/HTML]

---

### Post by bluntu on 2006-08-06
```

forward-socks4a / 127.0.0.1:9050 .

forward-socks4a :443 127.0.0.1:9050 .

forward-socks4a :53 127.0.0.1:9050 .

listen-address  127.0.0.1:8118

```

I have that at the beginning of my privoxy's 'config' file and I use this:

[img]http://tor.eff.org/img/screenshot-switchproxy-proxyconfig.jpg[/img]

Privoxy doesn't support FTP but by forwarding it to Privoxy is like stopping it. This way people can't find out my real IP by putting an ftp image or link. You can read more on this at TOR.eff.org

@GuitarHero:
Using a web proxy (proxy sites) is like walking in the tunnel with a Ninja suit.
Using TOR+Privoxy is like walking in the tunnel with a Stealth suit.

> **Razer(x) said:**
> Does it slow down my internet connection??
Yes, Proxies tend to slow down your connection.

On Windows you have Vidalia that allows you to get new IP (location) and if you're lucky you will find one that is on HIGHSPEED and so speed wouldn't be a problem.

---

### Post by cyclister on 2006-08-08
That was little strange dosent Tor work on port 9050 also?

---

### Post by j-strap2 on 2006-08-08
> **cyclister said:**
> That was little strange dosent Tor work on port 9050 also?

I'm not sure what you mean. Tor listens for SOCKS5 connections on 9050. Many client applications don't use the SOCKS5 protocol correctly (and leak DNS queries), hence Privoxy is used to safely route HTTP connections to the Tor SOCKS5 listener. So, after you configure Privoxy to route to Tor on 9050, you tell your client applications to connect to Privoxy's listening port on 8118.

---

### Post by Steve S. on 2006-10-02
Just to interject: wanted to say thanks for this Howto.  Worked like a charm.

---

### Post by Mark_in_Hollywood on 2006-10-14
Does this work in SwiftFox? Does this work in Dapper 6.06LTS?

---

### Post by benjaminzsj on 2006-10-25
Thanks for the how to, my problem is can I use HTTP proxy for my IM? It gives me error saying "proxy forbids tunneling".
> **Mark_in_Hollywood said:**
> Does this work in SwiftFox? Does this work in Dapper 6.06LTS?
It works very well in Edgy, it should work in Dapper, no idea about SwiftFox.

---

### Post by Malakia on 2006-10-26
Which IM program are you using? I would check the website for the program and see if they have anything about setting it up under a proxy server or check the tor website.

---

### Post by benjaminzsj on 2006-10-26
> **Malakia said:**
> Which IM program are you using? I would check the website for the program and see if they have anything about setting it up under a proxy server or check the tor website.
I'm using Gaim, I go through its FAQ but no luck with proxy settings.

---

### Post by stonymouse on 2006-11-20
I tried this out and apart from it slowing down FF somewhat (like Torpark?), it works. I am however, showing an IP adress of 66.199.184.254, which it seems, has been banned from editing Wikipedia articles due to the possibility of it being a zombie computer... or a Tor open proxy address! Poo!

Thanks for the hour or so's worth of interesting reading to.

Jenny

---

### Post by stonymouse on 2006-11-20
I tried this out and apart from it slowing down FF somewhat (like Torpark?), it works. I am however, showing an IP adress of 66.199.184.254, which it seems, has been banned from editing Wikipedia articles due to the possibility of it being a zombie computer... or a Tor open proxy address! Poo!

Thanks for the hour or so's worth of interesting reading to.

Jenny

---

### Post by pkjm17 on 2006-11-25
Where in the /etc/privoxy/config file do you add "localhost:9050 ."?

---

### Post by pkjm17 on 2006-11-25
In the /etc/privoxy/config/ file, where do u add "localhost:9050 ."?

---

### Post by Stambo00 on 2006-11-29
At the end

---

### Post by squidward_tentacels on 2006-12-02
Awesome tutorial, However how exactly would you edit the configuration files to disallow certain exit points by IP address? Ive searched around the tor site and hidden wiki, for an answer but havent found one. My understanding of Tor is that you connect to a random tor node with each restart, but about half of the time I get the same exit node!

149.9.0.59 (or something else in the 149.9.*.* range) 

OrgName:    PSI
OrgID:      PSI-1
Address:    1015 31st St NW
City:       Washington
StateProv:  DC
PostalCode: 20007
Country:    US

NetRange:   149.9.0.0 - 149.9.255.255
CIDR:       149.9.0.0/16
NetName:    PSINET-B-9
NetHandle:  NET-149-9-0-0-1
Parent:     NET-149-0-0-0-0
NetType:    Direct Assignment
NameServer: NS.PSI.NET
NameServer: NS2.PSI.NET
Comment:
RegDate:    1992-01-28
Updated:    1992-02-03


Frequently using the same exit node out of Washington, DC really seems a bit....well,lacking....The only PSI out of DC I could locate ([http://www.psi.org/](http://www.psi.org/)) smacks of Government funding. Excuse me while I put on my Tinfoil Hat here for a moment, but are these really the people you trust as the endpoint to your "private" communications;

PSI Board of Directors

Frank Loy, Chair
Former Under Secretary of State for Global Affairs
U.S. Department of State
Washington, DC

Rehana Ahmed
Physican
Nairobi, Kenya

Rita I. Bass
Chief Executive Officer
MEDIBANC, Inc.
Denver, Colorado

Frank Carlucci
Chairman Emeritus
The Carlyle Group
Washington, DC

Sarah G. Epstein
Population Consultant
Washington, DC

Gail McGreevy Harmon
Partner
Harmon, Curran, Spielberg & Eisenberg, LLP
Washington, DC

William C. Harrop
Former U.S. Ambassador to Guinea, Israel, Kenya and Zaire and Inspector General of the U.S. Department of State and the Foreign Service
Washington, DC

Adriaan Jacobovits de Szeged
Former Netherlands Ambassador to the United States
The Hague, The Netherlands

Ashley Judd
Actor/Activist
Franklin, Tennessee

M. Peter McPherson
Founding Co-Chair, Partnership to Cut Hunger and Poverty in Africa and President Emeritus, Michigan State University
Washington, DC

Gilbert Omenn, M.D.
Professor of Internal Medicine, Human Genetics and Public Health
University of Michigan
Ann Arbor, Michigan

Malcolm Potts, M.D.
Bixby Professor, School of Public Health
University of California, Berkeley
Berkeley, California

Mechai Viravaidya
Chairman
Population and Community Development Association
Bangkok, Thailand
	  	

So anyway, If anyone knows how to restrict exit nodes, that would be awesome[-(

---

### Post by squidward_tentacels on 2006-12-02
Ok, Ive got it now:smile: Its really not to bad to set this up.
The easiest way Ive found is to begin here; [http://proxy.org/tor.shtml](http://proxy.org/tor.shtml) and copy & paste a list of servers (by nickname) that are exit nodes, and in locals you wish to use into a text file. In my case I choose servers outside of the US, Germany, China, & Belguim.

For example "ExitNodes fioyaZ3iuthaihiera,molly,ChlenNigeraTor,Aioe........" and so on, I would also recommened going all the way down the list and choosing as many exit nodes as possible, as some may be unroutable/offline.

OK, once you have your list of prefered exit nodes , we need to edit the torrc file. When I tried to open this with "sudo gedit etc/Tor/torrc" all I got was a blank file, and an error when attempting to save, additionaly I crashed Tor, and had to "sudo apt-get remove --purge tor", and then reinstall it to get it working again, so you DONT want to attempt to edit the configuration file that way.;) 

Rather "sudo nautilus" ,and then browse your way to /etc/Tor/torrc. The file will open and you will see many commented out configuration options for various aspects of Tor. What you want to do is add "ExitNodes YOUR,LIST,OF,PREFERED,SERVERS,HERE....." as in the example above, using the list you made. Then beneath that, make sure and add;
"StrictExitNodes 1" as this specifies only to use the exit nodes you have listed above. You may also wish to add the following to a new line "SafeLogging 1" If 1, Tor replaces potentially sensitive strings in the logs (e.g. addresses) with the string [scrubbed]. This way logs can still be useful, but they don't leave behind personally identifying information about what sites a user might have visited. Or I believe there was an earlier post that would effectively disable logging altogether.  Make sure to save the file, and restart Tor for the changes to take effect. 

I added those lines to the bottom of the file. You can also specify entry nodes in the same manner, or even servers that you never want to use as any part of the circut, and host of other cool commands, available here;
[http://tor.eff.org/tor-manual.html](http://tor.eff.org/tor-manual.html)
Under the client options heading. Please bear in mind, there is no such thing as complete anomnity on the web, only degrees. However I think I like this a little better than exiting in Washington half the time:p

---

### Post by ice60 on 2006-12-02
> **pkjm17 said:**
> In the /etc/privoxy/config/ file, where do u add "localhost:9050 ."?

sudo gedit /etc/privoxy/config

i've always added it here -
```
#
#
forward-socks4a / localhost:9050 .
#  
#  6. WINDOWS GUI OPTIONS
#  ======================
```

then use these settings in firefox -

then i suppose you can use ethereal to see where your port 53 (DNS) is requesting from - it shouldn't be your ISP :)

---

### Post by frodon on 2007-01-10
I updated this guide with more detailled explanations and screenshots on the UDSF for those who are interested.

[http://doc.gwos.org/index.php/Surf_anon](http://doc.gwos.org/index.php/Surf_anon)

---

### Post by elysium444 on 2007-03-22
It worked, And I wanted to use this for rapid share but couldnt achive it I dont know what they r using. any idea how to download from rapidshare without limitations...

---

### Post by sefs on 2007-05-04
How does one set up a US Proxy from the list given in the how to. It does not mention port numbers and such. just ip addy.

Thanks.

---

### Post by duds888 on 2007-07-05
I'm so un-tech literate I hope someone can explain this to me in baby langauge!

I want to use Pandora music service, which has recently stopped anyone outside of the US using it. It does this based on IP address...

I have a Apple G4 ibook, running OSX 10.4 and Firefox. How can I make it look like I'm residing in the US?

Any help will be gratefully received!

Duds888

---

### Post by stoft on 2007-07-05
> **duds888 said:**
> I'm so un-tech literate I hope someone can explain this to me in baby langauge!

I want to use Pandora music service, which has recently stopped anyone outside of the US using it. It does this based on IP address...

I have a Apple G4 ibook, running OSX 10.4 and Firefox. How can I make it look like I'm residing in the US?

Any help will be gratefully received!

Duds888

Use a US-based proxy service?

---

### Post by fnx.lv on 2007-07-30
First of all I would like to thank you for this tutorial.  I'll admit it took me a couple hours to get it working properly.  Had to do a bit of reading but thats all good.  Now I have a couple of questions... :)

One:  When i run "top" in a terminal i show two new users I've never seen before:  'privoxy' and 'debian -t'
 --privoxy makes sense obviously but what about debian -t? Is this normal?  Also when i run the command "tor" to initiate the program i get this message saying something similar about user 'debian -t' and it sounds like a warning to me:

Jul 30 04:42:12.267 [notice] Tor v0.1.1.26. This is experimental software. Do not rely on it for strong anonymity.
Jul 30 04:42:12.268 [notice] Initialized libevent version 1.1a using method epoll. Good.
Jul 30 04:42:12.268 [warn] /var/lib/tor is not owned by this user (fnx, 1000) but by debian-tor (112). Perhaps you are running Tor as the wrong user?
Jul 30 04:42:12.268 [warn] Failed to parse/validate config: Couldn't access/create private data directory "/var/lib/tor"
Jul 30 04:42:12.268 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.

--perhaps I am running "tor" as the wrong user? hmm...

Question Two:  Well as it worked my IP did in fact change after successfully configuring tor and privoxy but is there another way to check anonymity?  Another website that will display my provider and other pertinent potentially identifiable information?

Three:  Running Firestarter shows me connected to a few IP's that are totally random, much how a user described earlier in this post.  They are on ports 9001 and 9030 and 443, 'Program' says "tor".  Again is this normal?  Maybe I'm missing the whole point of proxy servers...  (newb)

Last question:  I'm also behind a router and I'm currently using my ISP's DNS servers.  I was reading previous posts about achieving "true" anonymity only by using public DNS servers.  Is this tor/privoxy trick rendered useless if I'm still on Comcast's DNS?

Sorry for the long post.  I'm relatively new to Linux and networking in general so any tips/help would be more than much appreciated.  Again my humble apologies for the long post.  

-fnx

---

### Post by i M@N on 2007-07-30
Hello.

fnx.lv : you should have a look @ [http://ubuntuforums.org/showthread.php?p=2859870](http://ubuntuforums.org/showthread.php?p=2859870)

@+...

---

### Post by fnx.lv on 2007-07-30
> **i M@N said:**
> Hello.

fnx.lv : you should have a look @ [http://ubuntuforums.org/showthread.php?p=2859870](http://ubuntuforums.org/showthread.php?p=2859870)

@+...

Thanks for the link.

---

### Post by Clark_Bent on 2007-08-23
I have ran tor and privoxy for a while with firefox and they have worked well until recently it suddenly quit working. I have no idea why. Tor appears to work. I think privoxy is the problem. When I attempt to enable tor in firefox, privoxy complains it can't find the domain. 

At the bottom of my privoxy.conf

forward-socks4a / localhost:9050 .

I have firefox with the following under edit/preferences/connection settings

http proxy = localhost port 8118
ssl proxy = localhost port 8118
socks host = localhost port 9050
socks v5 is checked

Any insight would be greatly appreciated.

---

### Post by ssc351 on 2007-09-02
Hey Great howto!

So I read through the thread a one person brought up multiple exit nodes.  I can't seem to get this to work.  I insert them all in the tor file however I can't get the internet to run.  Is there a way to do it through SwitchProxy?  That seems like a more userfriendly interface.  In switchproxy, I tried clicking on Add, then Anonymous, then adding all the exit node address from the tor site but still nothing.  FYI, I am a newb.

---

### Post by TheIrishGuy on 2007-11-16
This howto will show you how you can surf (or IM, or irc, or whatever) anonymously using the [tor](http://tor.eff.org) network. I'm using hoary, so I don't know if this will work on warty. Please give me some feedback on this.

**BEFORE YOU START**
Make sure you have enabled the universe repository.

**INSTALL TOR AND PRIVOXY**
```
$ sudo apt-get install tor privoxy
```

**CONFIGURE PRIVOXY**
Add the following line to */etc/privoxy/config*. You can put it at the top of the file if you want (Don't forget the last dot.)

then it's time to start tor and privoxy
```

$ sudo /etc/init.d/tor start
$ sudo /etc/init.d/privoxy start
```

To Torify an application that supports http (ie Firefox), just point it at Privoxy (that is, localhost:8118 ). To use SOCKS directly (for example, for instant messaging, Jabber, IRC, etc), point your application directly at Tor (localhost:9050). 

To see if everything is working, go to [this site.](http://peertech.org/privacy-knoppix/)




[COLOR="Red"][size="4"]install squid + add zapper[/size]t[/COLOR]


you might want to also add squid, for caching and pre-fetching, also addzapper to remove unwanted adds
this works with the previous privoxy and tor guide

```

sudo apt-get install squid addzapper

```

```

sudo gedit /etc/squid/squid.conf

```

```

http_port 127.0.0.1:3128
icp_port 3130
htcp_port 4827
visible_hostname localhost 

cache_mem 32 MB
refresh_pattern . 0 20% 8640
hierarchy_stoplist cgi-bin ?

ftp_user Squid@domain1.com
ftp_passive off

acl QUERY urlpath_regex cgi-bin \?
acl www_ports src 80 443
acl ftp_ports src 21
acl localhost src 127.0.0.1/32
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl CONNECT method CONNECT
acl PURGE method PURGE
acl wwwusers src 0.0.0.0/0.0.0.0
acl ftpusers src 0.0.0.0/0.0.0.0

http_access allow localhost 
cache_peer localhost parent 8118 7 no-query default  
never_direct allow all  

access_log /var/log/squid/access.log
cache_log /var/log/squid/cache.log
no_cache deny QUERY
cache_dir ufs /var/spool/squid 10000 16 256 
request_body_max_size 500 MB
redirect_program /usr/local/bin/squid_redirect
useragent_log /var/log/squid/useragent.log
log_fqdn on




```

add zapper

```

sudo gedit  /usr/local/bin/squid_redirect

```

paste in the following
```

#!/usr/bin/perl -w
#
# Freshmeat release version 3.5.
#
# See the home page at:
#	http://adzapper.sourceforge.net/
# and the freshmeat record at:
#	http://freshmeat.net/projects/squid_redirect/
#
# Recode of the ad-zapper in perl.
# Only necessary because the shell seems to be failing big case statements.
# However, things are neater this way anyway because perl will build
# big optimised pattern matches.
#	- Cameron Simpson <cs@zip.com.au> 09apr1999
#
# Tunable policy by setting $STUBURL_xx to PASS.
#	- Cameron Simpson <cs@zip.com.au> 28jul1999
#
# Tunable CLEAR/VISIBLE mode by setting ZAP_MODE.
#	- Cameron Simpson <cs@zip.com.au> 26feb2000
#
# Personal zap pattern support.
#	- Cameron Simpson <cs@zip.com.au> 05mar2000
#
# Standalone proxy mode.
#	- Cameron Simpson <cs@zip.com.au> 02may2004
#

use strict qw(vars);
use bytes;

use POSIX ":sys_wait_h";
use Socket;
require 'flush.pl';

$::IOSIZE=1024;

sub mkzapcode($);
sub mkredirectfn($);
sub proxy_forkchild($$$);
sub proxy_getheaders($);
sub proxy_lookup($);
sub proxy_main($$;$);
sub proxy_munge($$);
sub proxy_rigsocket($);
sub proxy_copybody($$$$$);

$::cmd=$0;

# restart hook
$SIG{HUP}=sub { exec($0,@ARGV) };

# what to do if we don't change anything - Johannes Berg <johannes@sipsolutions.net>
$::NoChangeValue=( defined $ENV{ZAP_NO_CHANGE} ? $ENV{ZAP_NO_CHANGE} : '' );

# where to find the replacement URLs
$::StubBase=( defined $ENV{ZAP_BASE} && length $ENV{ZAP_BASE}
	    ? $ENV{ZAP_BASE}
	    : 'http://adzapper.sourceforge.net/zaps'
	    );
# not actually useful, because SSL doesn't go via the proxy
$::SSLStubBase=( defined $ENV{ZAP_BASE_SSL} && length $ENV{ZAP_BASE_SSL}
	       ? $ENV{ZAP_BASE_SSL}
	       : 'https://adzapper.sourceforge.net/zaps'
	       );
$::SSLStubBase =~ s/^http:/https:/;	# in case

# we always zap ads, web bugs and counters so set default placeholders
$::StubURLs{NOZAP}=1;		# http://noads/ bypasses the zapper
$::StubURLs{AD}="$::StubBase/ad.gif";
$::StubURLs{ADSSL}="$::SSLStubBase/ad.gif";
$::StubURLs{ADBG}="$::StubBase/adbg.gif";
$::StubURLs{ADPOPUP}="$::StubBase/closepopup.html";
$::StubURLs{ADJS}="$::StubBase/no-op.js";
$::StubURLs{ADHTML}="$::StubBase/no-op.html";
$::StubURLs{COUNTER}="$::StubBase/counter.gif";
$::StubURLs{COUNTERJS}="$::StubBase/no-op-counter.js";
$::StubURLs{COUNTERHTML}="$::StubBase/no-op-counter.html";
$::StubURLs{WEBBUG}="$::StubBase/webbug.gif";
$::StubURLs{WEBBUGJS}="$::StubBase/webbug.js";
$::StubURLs{WEBBUGHTML}="$::StubBase/webbug.html";
$::StubURLs{ADMP3}="$::StubBase/ad.mp3";
$::StubURLs{ADSWF}="$::StubBase/ad.swf";
$::StubURLs{PRINT}=IGNORE;	# PRINT rules disabled by default
$::StubURLs{REWRITE}=1;		# typeless rewrite
$::StubURLs{ANTICRACK}=$::StubURLs{AD};	# vehicles for crackers
$::StubURLs{ADHTMLTEXT}=$::StubURLs{ADHTML};
$::StubURLs{ADJSTEXT}=$::StubURLs{ADJS};

# make use of the qr() syntax to precompile pattern REs?
# I'd do this based on perl version if I could find out when it came in...
$::UseQR=0;
if (defined $ENV{ZAP_USE_QR} && length($ENV{ZAP_USE_QR}))
{ $::UseQR=1;
}
@::ZapRE=();

# backwards compatible
if (defined $ENV{STUBURL} && length $ENV{STUBURL}
 && ! defined $ENV{STUBURL_AD})
{ $ENV{STUBURL_AD}=$ENV{STUBURL};
}

# arrange paths for the active zap classes
{ my @classes = grep(/^STUBURL_/, keys %ENV);
  for (@classes)
  { $_ =~ s/^STUBURL_//;
  }

  for my $class (@classes)
  { $::StubURLs{$class}=$ENV{"STUBURL_$class"}
	if defined $ENV{"STUBURL_$class"}
	&& length  $ENV{"STUBURL_$class"}
	;
  }
}

# use the "clear" versions if ZAP_MODE is "CLEAR"
if (defined $ENV{ZAP_MODE} && $ENV{ZAP_MODE} eq CLEAR)
{ for my $type (keys %::StubURLs)
  { $::StubURLs{$type} =~ s/\.[^.]+$/-clear$&/;
  }
}

# "generate perl" mode
if (@ARGV == 2 && $ARGV[0] eq '--generate')
{ my $ptnfile=$ARGV[1];
  if ($ptnfile eq '-')
  {}
  elsif (! open(STDIN,"< $ptnfile\0"))
  { die "$::cmd: can't open $ptnfile: $!\n";
  }

  print mkzapcode(STDIN);
  exit 0;
}

$::Verbose=0;
$::DoProxy='';
undef $::LogFile;
if (exists $ENV{ZAP_LOGFILE} && length($ENV{ZAP_LOGFILE}))
{ $::LogFile=$ENV{ZAP_LOGFILE};
}

GETOPT:
while (@ARGV)
{ if ($ARGV[0] eq '-v')
  { $::Verbose=1;
    shift(@ARGV);
  }
  elsif ($ARGV[0] eq '-P')
  { shift(@ARGV);
    $::DoProxy=shift(@ARGV);
  }
  elsif ($ARGV[0] eq '-l')
  { shift(@ARGV);
    $::LogFile=shift(@ARGV);
  }
  elsif ($ARGV[0] =~ /^-./)
  { die "$::cmd: unsupported command like option: $ARGV[0]\n";
  }
  else
  { last GETOPT;
  }
}

if (defined $::LogFile)
{ open(LOGFILE,">> $::LogFile\0")
    || die "$::cmd: can't append to $::LogFile: $!\n";
}

# Note: the $ZAP_CHAINING variable is obsolete.
#       It was originally intented for piping redirectors
#	together, but that simply doesn't work right because
#	of the protocol specification.
#	Instead, use the wrapzap script.
$::Chaining = ( exists $ENV{ZAP_CHAINING} && length $ENV{ZAP_CHAINING}
	      ? $ENV{ZAP_CHAINING} eq 'FULL'
		? 2
		: 1
	      : 0
	      );

undef $::PreMatch;
if (defined $ENV{ZAP_PREMATCH} && -s $ENV{ZAP_PREMATCH})
{ if (open(PTNS,"< $ENV{ZAP_PREMATCH}\0"))
  { $::PreMatch=mkredirectfn(PTNS);
    close(PTNS);
  }
  else
  { warn "$::cmd: can't open \$ZAP_PREMATCH ($ENV{ZAP_PREMATCH}: $!";
  }
}

if (defined $ENV{ZAP_MATCH} && -s $ENV{ZAP_MATCH})
{ if (open(PTNS,"< $ENV{ZAP_MATCH}\0"))
  { $::Redirect=mkredirectfn(PTNS);
    close(PTNS);
  }
  else
  { warn "$::cmd: can't open \$ZAP_MATCH ($ENV{ZAP_MATCH}: $!";
  }
}
else
{ $::Redirect=mkredirectfn(DATA);
}

undef $::PostMatch;
if (defined $ENV{ZAP_POSTMATCH} && -s $ENV{ZAP_POSTMATCH})
{ if (open(PTNS,"< $ENV{ZAP_POSTMATCH}\0"))
  { $::PostMatch=mkredirectfn(PTNS);
    close(PTNS);
  }
  else
  { warn "$::cmd: can't open \$ZAP_POSTMATCH ($ENV{ZAP_POSTMATCH}: $!";
  }
}

# -P lport:rproxy:rport
if (length $::DoProxy)
{ if ($::DoProxy =~ /^((\d+):)?([^:]+):([^:]+)$/)
  { my($lport,$rproxy,$rport)=($2,$3,$4);
    $lport=8080 if ! length $lport;
    warn "proxy_main($lport,\"$rproxy:$rport\",5) ...";
    proxy_main($lport,"$rproxy:$rport",5);
  }

  exit 0;
}

while (defined ($_=<STDIN>))
{
  if (defined $::LogFile)
  { print LOGFILE $_;
    flush(LOGFILE);
  }
  chomp;
  
  my @words = split;

  my $ourl = $words[0];
  my $nurl = '';	# gets set on a redirection

  if (@words == 1 || $words[3] eq GET)
  { $nurl=redirect(@words);
  }

  if (! $::Chaining)
  { print "$nurl\n";
  }
  else
  { $nurl=$ourl if ! length $nurl;

    if ($::Chaining == 1)
    { print "$nurl\n";
    }
    else
    { print "$nurl @words[1..$#words]\n";
    }
  }

  flush(STDOUT);
}

exit 0;

# We need to deal correctly with whitespace and %xx stuff.
# Report from Rod Savard 29mar2004.
sub unpcnt($)
{ my($txt)=@_;
  $txt =~ s/%([0-9a-f][0-9a-f])/eval "chr(0x$1)"/eg;
  return $txt;
}

sub pcnt($)
{ my($txt)=@_;
  ##my $otxt = $txt;
  $txt =~ s/[\s'"\000-\031\177-\377]/sprintf("%%%02x",ord($&))/eg;
  ##warn "<= $otxt\n=> $txt\n";
  return $txt;
}

sub redirect
{ my(@words)=@_;

  my $nurl='';

  if (defined $::PreMatch)
  { $nurl=&$::PreMatch(@words);
  }
  if (! length $nurl)
  { $nurl=&$::Redirect(@words);
  }
  if ( ! length $nurl && defined $::PostMatch)
  { $nurl=&$::PostMatch(@words);
  }
  if ( ! length $nurl )
  { $nurl=$::NoChangeValue;
  }


  return pcnt($nurl);
}

# Read pattern specs from a stream and turn into perl code.
# Patterns are shell-style patterns, except that:
#	** matches strings including /
#	? is not a meta character
#	. isn't either
#	\ doesn't work
# - Cameron Simpson <cs@zip.com.au> 09apr1999
#

sub mkzapcode($)
{ my($STREAM)=@_;

  my $code = "y|/||s;
	      if (0) {}\n";
  my $ncode;

  my $lastclass;
  my @ptns;

  local($_);

  RULE:
  while (defined($_=<$STREAM>))
  { chomp;

    s/^\s+//;
    s/^#.*//;
    next if ! length;

    my(@F)=split;
    if (@F < 2 || @F > 3)
    { warn "$::cmd: $STREAM, line $.: wrong number of arguments\n\tneed CLASS pattern\n\tor   CLASS pattern subst\n";
      next RULE;
    }

    my($class)=shift(@F);
    $class=uc($class);

    # avert our eyes from some classes
    if ($class ne PASS
     && ( ! exists($::StubURLs{$class})
       || $::StubURLs{$class} eq IGNORE
	))
    { ##warn "skip (class=$class) $_\n";
      next RULE;
    }

    if (@F == 1)
    # plain match
    {
      my $ptn = shift(@F);

      $lastclass=$class if ! defined $lastclass;
      if ($class ne $lastclass)
      { if (@ptns)
	{ $code.=process($lastclass,@ptns);
	  @ptns=();
	}

	$lastclass=$class;
      }

      push(@ptns,$ptn);
    }
    elsif (@F == 2)
    # rewrite
    { my($ptn,$subst)=@F;

      # flush pending patterns
      if (@ptns)
      { $code.=process($lastclass,@ptns);
	@ptns=();
      }

      undef $lastclass;

      # for debugging
      my $ptndesc = "$class $ptn $subst";
      $ptndesc =~ s/['\\]/\\$&/g;

      $ptn='^'.ptn2re($ptn).'$';
      my $ptnexpr = re2expr($ptn);

      $code.="  elsif($ptnexpr)\n"
	    ."  { \$nurl=\"$subst\";\n"
	    ."    if (\$::Verbose)\n"
	    ."    { warn \"$class \$_\\non:\\n\".'$ptndesc'.\"\\n\";\n"
	    ."    }\n"
	    ."  }\n";
    }
    else
    { warn "$::cmd: $STREAM, line $.: unhandled number of fields [@F]\n\t";
    }
  }

  # flush pending patterns
  $code.=process($lastclass,@ptns) if @ptns;

  $code.="  elsif (\$::Verbose)\n"
	."  { warn \"PASS \$_ on no match\\n\";\n"
	."  }\n";

  $code;
}


sub subptn2re($)
{ local($_)=@_;
  return "[^/]*" if $_ eq '*';	# * -> [^/]*
  return ".*" if /^\*+$/;	# ** -> .*
  return $_;			# leave everything else alone
}

sub ptn2re($)
{ local($_)=@_;
  y|/||s;				# turn slashes into "/+"
  s|[.\@\%\$?+]|\\$&|g;			# quote specials
  s:(\\.|[^*\\]|\*+):subptn2re($&):eg;
  return $_;
}

sub re2expr
{ my($re)=@_;

  # old style compile-on-first-use
  return "m($re)o" if ! $::UseQR;

  # new style - force compilation now
  my $qr = eval 'qr($re)o';
  if ($@)
  { warn "$::cmd: qr fails: qr($re): $@";
    $::UseQR=0;
    return "m($re)o";
  }

  push(@::ZapRE,$qr);
  my $expr = "/\$::ZapRE[$#::ZapRE]/";
  warn "re=[ $re ]\nexpr=[ $expr ]";
  return $expr;
}

sub process
{ my($class)=shift;
  my(@ptns)=@_;

  my $nurl;

  if ($class eq PASS)
  { $nurl=PASS;
  }
  else
  # we trimmed unknown classes and IGNORE classes in mkzapcode()
  # so we can believe this without further checks
  { $nurl = $::StubURLs{$class};
  }

  my $code = '';

  # for debugging
  my $ptndesc = join("\n\t\t\t", map("$class $_", @ptns));
  $ptndesc =~ s/['\\]/\\$&/g;

  local($_);

  # transmute patterns into regexps
  @ptns=map(ptn2re($_),@ptns);

  # was joined with \n\t| but older perls don't like that
  my $bigptn = '^('.join('|', @ptns).')$';
  my $ptnexpr = re2expr($bigptn);

  $code.="  elsif ($ptnexpr)\n";
  if ($nurl eq PASS)
	{ $code.="  { \$nurl=\$url;\n"
		."    warn \"PASS \$_\\non:\\t\\t\\t\".\n\t\t\t'$ptndesc'.\"\\n\" if \$::Verbose;\n"
		."  }\n";
	}
  else	{ $code.="  { \$nurl=\$::StubURLs{$class};\n"
		."    if (\$::Verbose)\n"
		."    { warn \"$class \$_\\non:\\t\\t\\t\"\n\t\t\t.'$ptndesc'.\"\\n\";\n"
		."    }\n"
		."  }\n";
	}

  return $code;
}

sub mkredirectfn($)
{ my($STREAM)=@_;

  my $fn = 'sub { my($url,$client,$ident,$method)=@_;
		  local($_)=unpcnt($url);

		  my $nurl = "";
	   '
	 . mkzapcode($STREAM)
	 . '
		  return $nurl;
	    }';

  my $fnref;
  eval "\$fnref=$fn";
  if ($@)
  { warn "$::cmd: error compiling function: $@\n\tcode is:\n$fn\n";
    undef $fnref;
  }

  return $fnref;
}

sub proxy_term($)
{ my($sig)=@_;
  if ($$ == $::ProxyMainPid)
  {
    for my $pid (@::ProxyChildren)
    { kill($pid,15);
    }
  }
  exit 1;
}

sub proxy_main($$;$)
{ my($listen_port,$upstream,$nforks)=@_;
  $nforks=5 if ! defined $nforks;

  # nail children on abort
  @::ProxyChildren=();
  $::ProxyMainPid=$$;
  $SIG{__DIE__}=\&proxy_term;
  $SIG{HUP}=\&proxy_term;
  $SIG{INT}=\&proxy_term;
  $SIG{TERM}=\&proxy_term;

  local($::TCP_Proto)=scalar(getprotobyname('tcp'));
  ##warn "[$$]: TCP_Proto=[$::TCP_Proto]";

  my($proxy_name,$proxy_port,$proxy_addr,$proxy_paddr)
   = proxy_lookup($upstream);

  # set up token stream
  pipe(FROMCHILD, TOPARENT) || die "$::cmd: pipe: $!";

  proxy_rigsocket($listen_port);

  warn "[$$]: listening on port $listen_port ...\n";

  for my $i (1..$nforks)
  { push(@::ProxyChildren,proxy_forkchild($proxy_paddr,$proxy_name,$proxy_port));
  }

  # spawn new children as the old children die
  while (<FROMCHILD>)
  {
    # grab any dead children
    my $pid;
    while (($pid=waitpid(-1,WNOHANG)) > 0)
    { ##warn "[$$]: waitpid got something\n";
      @::ProxyChildren=grep($_ != $pid, @::ProxyChildren);
    }

    # spawn fresh child
    push(@::ProxyChildren,proxy_forkchild($proxy_paddr,$proxy_name,$proxy_port));
  }

  die "[$$]: exit from supposed main (parent is ".getppid().")";
}

sub proxy_lookup($)
{ my($upstream)=@_;

  my $proxy_name = 'proxy';
  my $proxy_port = 8080;
  my $proxy_addr;
  my $proxy_paddr;

  if ($upstream =~ /^(\S+):(\S+)$/)
  { $proxy_name=$1;
    $proxy_port=$2;
  }
  elsif (length $upstream)
  { $proxy_name=$upstream;
  }

  if ($proxy_port =~ /^\D/)
  { $proxy_port=getservbyname($proxy_port, 'tcp');
    die "$::cmd: No proxy port" unless $proxy_port;
  }

  $proxy_addr = inet_aton($proxy_name) || die "$::cmd: can't look up \"$proxy_name\"";
  $proxy_paddr = sockaddr_in($proxy_port, $proxy_addr);

  return ($proxy_name,$proxy_port,$proxy_addr,$proxy_paddr);
}

sub proxy_rigsocket($)
{ my($listen_port)=@_;
  die "$::cmd: socket: $!" if ! socket(SOCK, PF_INET, SOCK_STREAM, $::TCP_Proto);

  die "$::cmd: setsockopt: $!" if ! setsockopt(SOCK,
					SOL_SOCKET,
					SO_REUSEADDR,
					pack("l", 1));

  ##warn "[$$]: bind to port $listen_port ...";
  die "$::cmd: bind: $!" if ! bind(SOCK, sockaddr_in($listen_port, INADDR_ANY));

  die "$::cmd: listen: $!" if ! listen(SOCK,SOMAXCONN);
  ##system("netstat -an | grep $listen_port");
}

sub proxy_forkchild($$$)
{ my($proxy_paddr,$proxy_name,$proxy_port)=@_;

  my $pid;
  if (! defined ($pid=fork))
  { die "$::cmd: fork fails: $!";
  }

  # parent returns, child proceeds
  return $pid if $pid != 0;

  ##warn "[$$]: new child forked...";

  # we don't need this
  close(FROMCHILD);

  my $ok = accept(CONN,SOCK);
  die "$::cmd: accept: $!" if !$ok;
  # tell parent we need a new child
  print TOPARENT "\n";
  close(TOPARENT);
  ##warn "[$$]: new child: accepted";
  close(SOCK);	# let go of socket

  my $persist=1;
  my @hdrs;
  my $gotproxy=0;
  my($method,$uri,$v1,$v2);
  local($_);
  my $pass=0;
  my $orq;
  my $grandchild;

  REQUEST:
  while ($persist)
  {
    ++$pass;

    warn "[$$]: pass $pass: waiting for request ...\n";
    if ($pass > 1)
    { ##warn "[$$]:      last rq was $orq\n";
    }

    # read request
    if (! defined($_=<CONN>))
    { ##warn "[$$]: EOF from client, quitting\n";
      if ($gotproxy)
      { ##warn "[$$]: killing grandchild $grandchild\n";
	kill(15,$grandchild)
		|| warn "$::cmd: [$$]: kill(TERM,$grandchild): $!";
      }
      exit 0;
    }

    chomp;
    s/\r$//;
    s/\s+$//;

    if (! m:^(\S+)\s+(.*\S)\s+HTTP/0*(\d)\.0*(\d+)\s*\r?$:)
    { warn "$::cmd: bad syntax from client: $_";
      print CONN "400 Invalid HTTP request: $_\r\n";
      exit 0;
    }

    ($method,$uri,$v1,$v2)=($1,$2,$3+0,$4+0);
    $orq="$method $uri HTTP/$v1.$v2";
    warn "[$$]: pass $pass: $orq\n";

    # or depend on keep-alive? check >= 1.1
    $persist = ($v1 > 1 || ($v1 == 1 && $v2 >= 1));
    ##warn "[$$]: persist from request = [$persist]";

    # gather up the request
    @hdrs=proxy_getheaders(CONN);

    ## see if "Connection: close" supplied
    if (grep(uc($_->[0]) eq CONNECTION && $_->[1] =~ /\bclose\b/i, @hdrs))
    { $persist=0;
      ##warn "[$$]: disable persist by Connection: close";
    }

    ## munge URL here and adjust Host: if changed
    { my $muri = $uri;	# URI to munge

      # turn into absolute URL if necessary
      if ($muri !~ m|^[a-z][-a-z\d+.]*:|i)
      # no scheme - add http:// and Host
      { my @hosts = map($_->[1], grep(uc($_->[0]) eq HOST, @hdrs));
	if (@hosts)
	# yes, there is a Host: header
	{ @hosts = grep(length,split(/\s+/,$hosts[0]));
	  if (@hosts)
	  # yes, there's a host in the first Host: header
	  { $muri = "/$muri" unless $muri =~ m:^/:;
	    $muri="http://".lc($hosts[0])."$muri";
	  }
	}
      }

      my $nuri=proxy_munge($muri,$method);

      if ($nuri ne $muri)
      {
	warn "[$$]: ouri: $muri\n";
	warn "[$$]: nuri: $nuri\n";

	$uri=$nuri;

	# see if we need to change the Host: header
	if ($muri =~ m|^https?://([^@/]*@)?([^/:]+)(:[^/]*)?/|i)
	{ my $ohost=lc($2);
	  if ($nuri =~ m|^https?://([^@/]*@)?([^/]+)/|i)
	  { my $nhost=lc($2);
	    if ($nhost ne $ohost)
	    { for my $H (@hdrs)
	      { if (uc($H->[0]) eq HOST)
		{ ##warn "[$$]: $H->[0]: $H->[1] -> $nhost\n";
		  $H->[1]=" $nhost\r\n";
		}
	      }
	    }
	  }
	}
      }
    } ## end of munge

    my $proxyagain=1;

    PROXYLOOP:
    while($proxyagain)
    {
      # we general run this loop only once
      $proxyagain=0;

      # ready to go - connect to upstream server if necessary
      if (! $gotproxy)
      {
	# channel to report persistence
	# \n - persist
	# EOF - close upstream connection and refork, reconnect on next rq
	pipe(FROMGRANDCHILD, TOCHILD) || die "$::cmd: [$$]: pipe: $!";
	pipe(GCHILD_READ, GCHILD_WRITE) || die "$::cmd: [$$]: pipe: $!";

	# connection to upstream
	socket(PROXY, PF_INET, SOCK_STREAM, $::TCP_Proto)
	  || die "$::cmd: proxy socket: $!";
	connect(PROXY, $proxy_paddr)
	  || die "$::cmd: connect($proxy_name:$proxy_port): $!";

	$gotproxy=1;
	##warn "[$$]: connected to proxy\n";

	# fork child to stream proxy responses
	my $child=$$;
	$grandchild = fork();
	if ($grandchild < 0)
	{ my $err = "$!";
	  warn "$::cmd: fork: $err";
	  print CONN "503 fork: $err\r\n";
	  exit 0;
	}

	if ($grandchild == 0)
	# child - copy proxy output
	# this used to be a straight copy
	# but we must parse and honour "Connection: close"
	# from upstream
	{ proxy_grandchild($child);
	  exit 0;
	}

	# parent - fall through and handle connection
	close(TOCHILD);
	close(GCHILD_READ);
      }

      # dispatch request and headers
      printflush(GCHILD_WRITE,"$method $uri $v1 $v2\n")
	|| die "tell grandchild the request: $!";

      print PROXY "$method $uri HTTP/$v1.$v2\r\n";
      for my $H (@hdrs)
      { print PROXY $H->[0], ":", $H->[1], "\r\n";
      }
      printflush(PROXY,"\r\n");
      ##warn "[$$]: sent rq to proxy\n";

      proxy_copybody(CONN,PROXY,$method,$persist,\@hdrs)
	|| die "copybody up to PROXY failed: $!";

      ##warn "[$$]: end request for $uri\n";

      # read [persist response] from child
      if (!defined($_=<FROMGRANDCHILD>))
      { $gotproxy=0;
	close(FROMGRANDCHILD);
	warn "[$$]: abort from grandchild, retrying with new grandchild";
	$proxyagain=1;
	next PROXYLOOP;
      }
      chomp; s/\r$//; s/\s+$//;
      warn "[$$]: grandchild said [$_]\n";
      if (!/^([A-Z]+)\s+(\d\d\d)\s*/)
      { warn "[$$]: bad grandchild return, bailing out";
	exit 0;
      }
      my($gchoice,$gresponse,$getc)=($1,$2,$3);
      if ($gchoice eq PERSIST)
      { $persist=1;
      }
      elsif ($gchoice eq CLOSE)
      { $persist=0;
      }
      else
      { die "[$$]: unsupported choice \"$gchoice\", aborting";
      }

      warn "[$$]: loop bottom: persist=$persist";
    }	# end of PROXYLOOP
  }	# end of REQUEST $persist loop

  ##warn "[$$]: child exits";

  exit 0;
}

sub proxy_getheaders($)
{ my($conn)=@_;

  # list of [field,body] pairs
  my @hdrs=();

  local($_);

  my($f,$b);

  HEADER:
  while (defined($_=<$conn>))
  {
    # trim end of line
    chomp;
    s/\r$//;

    last HEADER if ! length;

    if (/^[ \t]/)
    # continuation
    { $b.="\r\n$_";
    }
    else
    # end of current header, start new
    {
      # stash pending header, if any
      if (defined $f)
      { ##warn "[$$]: [$f: $b]";
	push(@hdrs,[$f,$b]);
	undef $f;
	undef $b;
      }

      if (/^([^:\s]+):/)
      # new header
      { $f=$1; $b=$';
      }
      else
      { s/\s+$//;
	warn "$::cmd: bad header line: $_\n\tending header read";
	last HEADER;
      }
    }
  }

  # stash pending header, if any
  if (defined $f)
  { ##warn "[$$]: [$f: $b]";
    push(@hdrs,[$f,$b]);
    undef $f;
    undef $b;
  }

  ##warn "[$$]: got headers";
  return @hdrs;
}

sub proxy_grandchild($)
{ my($child)=@_;

  close(FROMGRANDCHILD);
  close(GCHILD_WRITE);

  select(CONN);
  $|=1;

  ##warn "[$child:$$]: grandchild, copying from proxy ...\n";

  local($_);
  my $rq;

  RESPONSE:
  while (defined($rq=<GCHILD_READ>) && defined($_=<PROXY>))
  {
    my($rq_method, $rq_uri, $rq_v1, $rq_v2)=split(/\s+/,$rq);

    # collect response line
    if (! m:^HTTP/(\d+)\.0*(\d+)\s+(\d\d\d)\s*([^\r\n]*):)
    { warn "$::cmd: [$child:$$]: bad response from proxy: $_\n";
      close(TOCHILD);
      last RESPONSE;
    }

    my($v1,$v2,$code,$info)=($1,$2,$3,$4);
    warn "[$$:$child]: [HTTP/$v1.$v2 $code $info]\n";

    # collect response headers
    my @hdrs = proxy_getheaders(PROXY);
    for my $H (@hdrs)
    { warn "  $H->[0]:$H->[1]\n";
    }

    # adjust persistence based on response code and headers

    # disable persistence for HTTP/1.0 and below by default,
    # then permit it if "Proxy-Connection: keep-alive"
    my $persist = 1;
    if ($v1 < 1 || ($v1 == 1 && $v2 < 1))
    { $persist=0; warn "[$child:$$]: disable persist - HTTP < 1.1\n";

      if (0&&grep( uc($_->[0]) eq 'PROXY-CONNECTION'
	     && $_->[1] =~ /\bkeep-alive\b/i,
		@hdrs
	      )
	 )
      { $persist=1;
	warn "[$child:$$]: enable persist by proxy's Proxy-Connection: keep-alive";
      }
    }
    else
    { warn "disable persist for HTTP/$v1.$v2 response anyway\n";
      $persist=0;
    }

    # see if "Connection: close" supplied
    # or "Proxy-Connection: close" (from Netscape-Enterprise/3.6 SP3)
    if (grep( ( uc($_->[0]) eq CONNECTION
	     || uc($_->[0]) eq "PROXY-CONNECTION"
	      ) && $_->[1] =~ /\bclose\b/i,
	     @hdrs)
       )
    { $persist=0;
      warn "[$child:$$]: disable persist by proxy's Connection: close";
    }

    warn "[$child:$$]: pass response to parent\n";
    printflush(TOCHILD,($persist ? PERSIST : CLOSE)." $code $info")
	|| die "[$child:$$]: print(TOCHILD) fails: $!";
    warn "[$child:$$]: told parent, passing response to client\n";

    # copy to child
    print CONN "HTTP/$v1.$v2 $code $info\r\n";
    for my $H (@hdrs)
    { print CONN $H->[0], ":", $H->[1], "\r\n";
    }
    printflush(CONN,"\r\n");

    # see RFC2616 section 10
    if (
	$rq_method ne HEAD
     && (
	  $code == 200 && grep($rq_method eq $_,GET,POST,TRACE)
       || grep($code == $_, 201,202,203,206,
			    300,301,302,303,307,
			    401,403,404,406,409)
       || $code =~ /^5/
	)
       )
    { 
      proxy_copybody(PROXY,CONN,'',$persist,\@hdrs)
	|| die "copybody from PROXY to CLIENT fails: $!";
    }

    last RESPONSE if !$persist;
    warn "[$child:$$]: getting next PROXY response...\n";
  }

  warn "[$child:$$]: exiting\n";
  exit 0;
}

sub proxy_copybody($$$$$)
{ my($from,$to,$method,$persist,$H)=@_;

  my $ok=1;
  my $err;

  warn "[$$]: copybody($from,$to,...)\n";
  ## copy the body, if any
  ## deduce length according to RFC2616 part 4.4
  my @te = grep(uc($_->[0]) eq 'TRANSFER-ENCODING', @$H);
  if (@te && uc($te[0]->[1]) ne IDENTITY)
  # expect chunked data transfer
  { my($ok,$err)=proxy_copychunked($from,$to);
  }
  else
  # expect ordinary body, possibly with Content-Length
  {
    my $cl = undef;
    my @cl = grep(uc($_->[0]) eq 'CONTENT-LENGTH', @$H);
    if (@cl)
    { $cl=$cl[0]->[1]+0;
      warn "  content-length=$cl\n";
    }
    elsif ($persist)
    { $cl=0;	# assume no body
    }

    if ($persist ? 1 : ($method ne GET && $method ne HEAD))
    # copy body using Content-Length
    { ($ok,$err)=proxy_copycl($from,$to,$cl);
    }
  }
  warn "[$$]: copybody done\n";

  return $ok;
}

sub proxy_copycl($$$)
{ my($from,$to,$cl)=@_;

  my $ok=1;

  warn "[$$]: reading unchunked body from $from";
  local($_)='';
  COPY:
  while ((!defined($cl) || $cl > 0)
      && read($from,$_,(defined $cl && $cl < $::IOSIZE ? $cl : $::IOSIZE)) > 0
	)
  {
    ##warn "[$$]: read ".length($_)." bytes of request body\n";
    if (! printflush($to,$_))
    { warn "$::cmd: [$$]: printflush($to,..): $!";
      $ok=0;
      last COPY;
    }
    $cl-=length if defined $cl;
  }
  warn "[$$]: finished unchunked body, ok=$ok";

  return ($ok,"");
}
sub proxy_copychunked($$)
{ my($from,$to)=@_;

  local($_);
  my $chunksize;

  CHUNK:
  while (defined($_=<$from>))
  {
    if (! /^([\da-f]+)/)
    { return (0,"bad chunk size: $_");
    }
    $chunksize=eval("0x$1");
    print $to $_;

    last CHUNK if $chunksize == 0;
    
    $_='';
    while ($chunksize > 0 && read($from,$_,($chunksize < $::IOSIZE ? $chunksize : $::IOSIZE)) > 0)
    { print $to $_;
      $chunksize-=length;
    }
    flush($to);
  }

  flush($to);

  # pass trailer headers
  while (defined($_=<$from>) && !/^\r?\n/)
  { print $to $_;
  }
  if (defined)
  { ##warn "[$$]: final trailer: $_";
    print $to $_;
  }
  flush($to);

  return (1,"");
}

sub proxy_munge($$)
{ my($uri,$method)=@_;

  my $nuri = redirect($uri,'-','-',$method);
  $uri=$nuri if length $nuri;

  return $uri;
}

__DATA__
##
## Last updated Tue Oct 23 12:21:34 EST 2007.
##
NOZAP (*://**)?NOZAP $1
PRINT http://((www*.|)washingtonpost.com)/wp-dyn/articles/(A[0-9]*).html http://$1/ac2/wp-dyn/$3?language=printer
PRINT http://((www*.|)news.utoronto.ca)/bin6/(*).asp http://$1/bin6/print/$3.htm
PRINT http://(www*.|)gamegirladvance.com/(archives/20[0-9][0-9]/[0-9][0-9]/[0-9][0-9]/*).html http://www.gamegirladvance.com/$2-print.html
PRINT http://(www*.|)internetnews.com/(*)/article.php/([0-9]*) http://www.internetnews.com/$2/print.php/$3
PRINT (http://(www*.|)enterpriseitplanet.com/**)/article.php/([0-9]*) $1/print.php/$3
PRINT http://(www*.|)wi-fiplanet.com/news/article.php/([0-9]*) http://www.wi-fiplanet.com/news/print.php/$2
PRINT http://(www*.|)smh.com.au(/articles/**.html) http://www.smh.com.au/cgi-bin/common/popupPrintArticle.pl?path=$2
PRINT http://(www*.|)zdnet.com.au/newstech/**/0,([0-9]*),([0-9]*),00.htm http://www.zdnet.com.au/printfriendly?AT=$2-$3
PRINT https://freeinternetpress.com/modules.php?name=News&file=article&sid=(*) 302:http://freeinternetpress.com/modules.php?name=News&file=print&sid=$1
PRINT http://*.zdnet.com/*/stories/*/0,14179,(*),00.html http://www.zdnet.com/filters/printerfriendly/0,6061,$1-92,00.html
PRINT http://news.zdnet.co.uk/story/0,,t([0-9]*)-s([0-9]*),00.html http://news.zdnet.co.uk/cgi-bin/uk/printerfriendly.cgi?id=$2&tid=$1
PRINT http://(*.zdnet.co.uk)/**/0,([0-9]*[0-9]),([0-9]*[0-9]),00.htm http://www.zdnet.co.uk/print/?TYPE=story&AT=$3-$2t-10000018c
PRINT http://www.zdnet.com.au/news/(*)/0,(*),(*),00.htm http://www.zdnet.com.au/news/$1/print.htm?TYPE=story&AT=$3-$2-10000004c
##PRINT http://(news.|)zdnet.com(|.com)/[0-9][0-9][0-9][0-9]-(*).html* http://$1zdnet.com$2/2102-$3.html?tag=printthis
PRINT http://zdnet.com.com/m/2100-([0-9]*_[0-9]-*).html* http://zdnet.com.com/2102-$1.html?tag=printthis
PRINT http://((www*.|)fool.com)/N(ews/mft/20[0-9][0-9]/mft*.htm) http://$1/Server/FoolPrint.asp?File=/n$3
PRINT http://(*.silicon.com)/(**)/0,([0-9]*[0-9]),([0-9]*[0-9]),00.htm http://$1/$2/print.htm?TYPE=story&AT=$4-$3t-40000019c
PRINT http://(www*.|)timesonline.co.uk/article/0,,(*),00.html http://www.timesonline.co.uk/printFriendly/0,,$2-2,00.html
PRINT http://((*.|)reuters.(com|co.uk))/**(newsArticle|newsPackageArticle).jhtml*(storyID=[0-9]*[0-9])* 302:http://$1/printerFriendlyPopup.jhtml?$5
PRINT http://((*.|)reuters.(com|co.uk))/**(newsArticle|newsPackageArticle).aspx*storyID=(*.xml) 302:http://$1/printerFriendlyPopup.aspx?storyID=uri:$5
PRINT http://(www*.|)technologyreview.com/articles/(*).asp** http://www.technologyreview.com/articles/print_version/$2.asp
PRINT (http://(www*.|)technologyreview.com/articles/*/**.asp?p=)2 ${1}0
PRINT http://(www*.|)techcentralstation.com/(*)/techwrapper.jsp?**&CID=(*) http://www.techcentralstation.com/$2/printer.jsp?CID=$3
PRINT http://(www*.|)pcworld.com/news/article/0,aid,([0-9]*[0-9]),00.asp http://www.pcworld.com/resource/printable/article/0,aid,$2,00.asp
PRINT http://(www*.|)kobtv.com/index.cfm?viewer=storyviewer&id=([0-9][^&]*)** http://www.kobtv.com/process/printstory.cfm?id=$2
PRINT (http://(www*.|)popularmechanics.com/**/20[0-9][0-9]/**/)index.phtml $1/print.phtml
PRINT http://abcnews.go.com/(**)/(story|wireStory)?(id=**) http://abcnews.go.com/$1/print?$3
PRINT http://www.technologyreview.com/read_article.aspx?(id=[1-9]**) http://www.technologyreview.com/printer_friendly_article.aspx?$1
PRINT (http://(www*.|)wkrn.com/*/story.asp?S=[0-9]*) $&&ClientType=Printable
PRINT http://cnews.canoe.ca/CNEWS/(*/20[0-9][0-9]/[01][0-9]/[0123][0-9])/([0-9]*[0-9])-ap.html http://cnews.canoe.ca/CNEWS/$1/pf-$2.html
PRINT http://((ww*.|)ctv.ca/servlet/ArticleNews)/story/(CTVNews/[0-9]**) http://$1/print/$3&subhub=PrintStory
PRINT (http://(www*.|)canoe.ca/**/News/20[0-9][0-9]/[01][0-9]/[0123][0-9])/([0-9]*.html) $1/pf-$3
PRINT (http://(www*.|)post-gazette.com/pg)/([0-9]**[0-9].stm) $1/pp/$3
PRINT http://((www*.|)spectrum.ieee.org.nyud.net:8090)/[a-z]*[0-9]/([0-9]*[0-9]) http://$1/print/$3
PRINT http://((www*.|)smartmoney.com)/(*/index.cfm?story=**) http://www.smartmoney.com/print/index.cfm?printcontent=/$3
PRINT http://distrocenter.linux.com/distrocenter/([0-9]**[0-9]).shtml** http://distrocenter.linux.com/print.pl?sid=$1
##PRINT http://((*.|)news.com.au)/common/story_page/0,[0-9][0-9][0-9][0-9],([0-9]*[0-9]),00.html http://$1/common/printpage/0,6093,$3,00.html
PRINT http://(www*.|)redherring.com/article.aspx?a=([0-9]*[0-9]) http://www.redherring.com/PrintArticle.aspx?a=$2
PRINT http://(www*.|)astrobio.net/news/modules.php?**&(sid=[0-9][0-9]*)** http://www.astrobio.net/news/print.php?$2
PRINT (http://(www*.|)tomahjournal.com/articles/**).txt $1.prt
PRINT http://(www*.|)azcentral.com/community/tempe/articles/*.html http://www.azcentral.com/php-bin/clicktrack/print.php?referer=$&
PRINT http://(www*.|)csoonline.com/read/**.html $&?action=print
PRINT http://((www*.|)wwwcoder.com)/main/parentid/*/site/([[0-9]*[0-9])/*/default.aspx http://$1/main/DesktopModules/ResDirMgr/ASPSearch_Options.aspx?action=print&article=$3
PRINT http://(www*.|)scoop.co.nz/stories/**.htm $&?mode=print
PRINT http://(www*.|)wkyt.com/Global/story.asp?[Ss]=([0-9]*[0-9]) $&&ClientType=Printable
PRINT http://www.dailystar.com.lb/article.asp?edition_id=*&categ_id=([0-9])&article_id=([0-9]*[0-9]) http://www.dailystar.com.lb/printable.asp?art_ID=$2&cat_ID=$1
PRINT http://(www*.|)japancorp.net/Article.Asp?Art_ID=(*) http://$1japancorp.net/printarticle.asp?Art_ID=$2
PRINT http://(www*.|)japantoday.com/e/?content=comment&id=(*) http://www.japantoday.com/e/tools/print.asp?content=comment&id=$2
PRINT (http://(www*.|)democratandchronicle.com/biznews)/([0-9]*.shtml) $1/forprint/$3
PRINT http://(www*.|)physorg.com/news([0-9]*).html http://www.physorg.com/printnews.php?newsid=$2
PRINT http://((www*.|)(tdn|missoulian).com/articles/**).txt http://$1.prt
PRINT http://(www*.|)iol.co.za/index.php?*&art_id=([a-z][a-z][0-9]*[0-9]) http://www.iol.co.za/general/news/newsprint.php?art_id=$2&sf=
PRINT http://(www*.|)onlamp.com/pub/wlg/([0-9]**) http://www.onlamp.com/lpt/wlg/$2
PRINT http://((www*.|)rednova.com)/news/display/?(id=116562) http://$1/modules/news/tools.php?tool=print&$3
PRINT http://((www*.|)rednova.com)/news/*/([0-9]*[0-9])/**.html http://$1/modules/news/tools.php?tool=print&id=$3
PRINT (http://(www*.|)csmonitor.com/20[0-9][0-9]/*/p*.htm)l $1
PRINT http://judiciary.senate.gov/testimony.cfm?(id=**) http://judiciary.senate.gov/print_testimony.cfm?$1
PRINT http://(www*.|)enr.com/features/*/archives/[0-9]*[0-9]-[0-9].asp http://www.enr.com/print.asp?REF=$&
##PRINT http://news.com.com**/2*-(*-*).html** http://news.com.com/2102-$1.html?tag=ni_print
PRINT http://((www*.|)capitolhillblue.com/artman/publish)/article_([0-9]*).shtml http://$1/printer_$3.shtml
PRINT http://(www*.|)lcsun-news.com/artman/publish/article_(*).shtml http://www.lcsun-news.com/artman/publish/printer_$2.shtml
PRINT (http://(www*.|)digitimes.com)/news/(a2*.html) $1/print/$3
PRINT http://((www*.|)news-medical.net)/?id=([0-9]*[0-9]) http://$1/print_article.asp?id=$3
PRINT http://(www*.|)sltrib.com/2[0-9][0-9][0-9]/*/**.asp $&?display=print
PRINT (http://(www*.|)avnonline.com/index.php?*)&Action=View_Article&Content_ID=([0-9]*[0-9]) $1&Action=Print_Article&Content_ID=$3
PRINT http://(www*.|)economist.com/(**)/displayStory.cfm?[Ss]tory_[Ii][Dd]=(*) http://www.economist.com/$2/PrinterFriendly.cfm?Story_ID=$3
PRINT http://www.pawtuckettimes.com/site/news.cfm?(newsid=**) http://www.pawtuckettimes.com/site/printerFriendly.cfm?$1
PRINT http://(www*.|)xml.com/pub/(a/20[0-9][0-9]/[0-9][0-9]/[0-9][0-9]/*.html) http://www.xml.com/lpt/$2
PRINT http://allafrica.com/stories/([0-9]*).html http://allafrica.com/stories/printable/$1.html
PRINT http://(www*.|)acmqueue.com/modules.php?name=Content&pa=showpage&pid=([0-9]*[0-9]) http://www.acmqueue.com/modules.php?name=Content&pa=printer_friendly&pid=$2&page=1
PRINT http://((www*.|)dailyreviewonline.com)/Stories/0,[0-9][0-9][0-9][0-9],([0-9]*[0-9]),00.html http://$1/cda/article/print/0,1674,$3,00.html
PRINT http://newsforge.com/newsforge/([0-9][0-9]/*/*/*).shtml** http://newsforge.com/print.pl?sid=$1
PRINT http://((*.|)newsforge.com)/*/([0-9]**).shtml** http://$1/print.pl?sid=$3
PRINT http://(www*.|)advancedippipeline.com/news/([0-9]*[0-9]);jsessionid=** http://www.advancedippipeline.com/shared/article/printablePipelineArticle.jhtml?articleId=$2
PRINT http://(www*.|)wfmynews2.com/2wk/2wk.asp?ID=(**) http://www.wfmynews2.com/2wk/print2wk.asp?ID=$2
PRINT http://(www*.|)bizreport.com/article.php?art_id=(*) http://www.bizreport.com/print.php?art_id=$2
PRINT http://(www*.|)bizreport.com/news/([0-9]*[0-9])/ http://$1bizreport.com/print/$2/
PRINT http://(www*.|)upi.com/view.cfm?StoryID=(*) http://www.upi.com/print.cfm?StoryID=$2
PRINT http://(*.indiatimes.com)/articleshow/([0-9]*[0-9]).cms http://$1/articleshow/msid-$2,prtpage-1.cms
PASS http://news.independent.co.uk/low_res/story.jsp?story=**
PRINT http://news.independent.co.uk/**/story.jsp?story=(*) 302:http://news.independent.co.uk/low_res/story.jsp?story=$1&host=3&dir=505
## OLD RULE
##PRINT http://news.independent.co.uk/**/story.jsp?story=(*) http://news.independent.co.uk/low_res/story.jsp?story=$1&host=3&dir=60
PRINT http://(www*.|)thisislondon.com/news/articles/([0-9]*[0-9])?** http://www.thisislondon.com/til/jsp/modules/Article/print.jsp?itemId=$2
PRINT http://(www*.|)scidev.net/news/index.cfm?fuseaction=readnews&(itemid=**) http://www.scidev.net/News/index.cfm?fuseaction=printarticle&$2
PRINT http://(www*.|)sciam.com/article.cfm?*&articleID=(*) http://www.sciam.com/print_version.cfm?articleID=$2
PRINT http://((www*.|)(news4jax.com|thechamplainchannel.com))/*/([0-9]*[0-9])/detail.html http://$1/print/$4/detail.html?use=print
PRINT http://news.ninemsn.com.au/article.aspx?id=* $&&print=true
PRINT http://(www*.|)wired.com/wired/archive/(**).html** http://www.wired.com/wired/archive/${2}_pr.html
PRINT http://(www*.|)dailymail.co.uk/pages/live/articles/**.html?(in_article_id=*&in_page_id=*) http://www.dailymail.co.uk/pages/text/print.html?$2
PRINT http://(www*.|)medicalnewstoday.com/index.php?newsid=(*) http://www.medicalnewstoday.com/printerfriendlynews.php?newsid=$2
PASS http://(www*.|)techworld.com/**&printerfriendly=1
PRINT http://((www*.|)techworld.com)/**/index.cfm?FeatureID=([1-9]*[0-9]) http://$1/features/index.cfm?featureID=$3&printerfriendly=1
PRINT http://((www*.|)anandtech.com)/*/showdoc.(html|aspx)?i=(*) http://$1/printarticle.$3?i=$4
## number change?
PRINT http://(www*.|)wired.com/news/*/0,*,(*),00.html** http://www.wired.com/news/print/0,1294,$2,00.html
## need to turn $yyyymmdd into date of article, not today:-(
##PRINT http://seattletimes.nwsource.com/html/*/([0-9]*)_(*[0-9]).html http://seattletimes.nwsource.com/cgi-bin/PrintStory.pl?document_id=$1&slug=$2&date=$yyyymmdd
PRINT http://seattlepi.nwsource.com/*/[0-9]*_*.html http://seattlepi.nwsource.com/printer2/index.asp?ploc=t&refer=$&
PRINT http://(www*.|)computerworld.com/**/story/0,*,([0-9]*[0-9]),00.html http://www.computerworld.com/printthis/2004/0,4814,$2,00.html
PRINT http://(www*.|)computerworld.com/action/article.do?command=viewArticle*&articleId=([[0-9]*[0-9])* http://www.computerworld.com/action/article.do?command=printArticleBasic&articleId=$2
PRINT http://(news.bbc.co.uk/[0-9]/**.stm) http://newsvote.bbc.co.uk/mpapps/pagetools/print/$1
PRINT http://(www*.|)wweek.com/story.php?story=(*) http://www.wweek.com/print.php?story=$2
PRINT http://(*.itworld.com/**)/page_1.html http://$1/pfindex.html
PRINT http://((*.|)enterprisestorageforum.com/**)/article.php/([0-9]*[0-9]) http://$1/print.php/$3
PRINT http://iccheshireonline.icnetwork.co.uk/**/tm_objectid=([0-9]{1,8})*&siteid=([0-9]{1,6})** http://iccheshireonline.icnetwork.co.uk/printable_version.cfm?objectid=$1&siteid=$2
PRINT http://(www*.|)washingtonpost.com/wp-dyn/articles/(A*-*).html http://www.washingtonpost.com/ac2/wp-dyn/$2?language=printer
PRINT http://(www*.|)washingtonpost.com/ac2/wp-dyn?*&contentId=(A*-*)&notFound=true http://www.washingtonpost.com/ac2/wp-dyn/$2?language=printer
PRINT http://weekly.ahram.org.eg/(20[0-9][0-9]/**.htm) http://weekly.ahram.org.eg/print/$1
PRINT http://(www*.)minebox.com/australian-mining-news.asp?NID=(*) http://www.minebox.com/print-article.asp?article=$2
PRINT (http://(www*.|)thenation.com/)doc.mhtml?(*) $1/docprint.mhtml?$3
PRINT http://(www*.|)streathamguardian.co.uk/news/*/display.var.([0-9]*[0-9]).0.*.php http://www.streathamguardian.co.uk/misc/print.php?artid=$2
PRINT http://(www*.|)cancerresearchuk.org/news/pressreleases/(*) http://www.cancerresearchuk.org/news/pressreleases/$2?view=Printable
PRINT http://my.webmd.com/(content/article/**.htm)** http://my.webmd.com/$1?printing=true
## disabled - the 302 trick doesn't cut it - annoying
##PRINT http://(www*.|)cbsnews.com/(stories/2**)/main([0-9]*).shtml 302:http://www.cbsnews.com/$2/printable$3.shtml
PRINT http://(www*.|)hardwareanalysis.com/content/article/(*)/ http://www.hardwareanalysis.com/action/printarticle/$2/
PRINT http://(www*.|)nydailynews.com/(**)/story/([0-9]*).html http://www.nydailynews.com/$2/v-pfriendly/story/$3.html
PRINT http://(www*.|)adn.com/front/(story/[0-9]*-*.html) http://www.adn.com/front/v-printer/$2
PRINT http://dsc.discovery.com/news/(**).html http://dsc.discovery.com/news/${1}_print.html
PRINT http://www.newscientist.com/article.ns?id=** $&&print=true
PRINT http://(www*.|)newscientist.com/news/news.jsp?id=(*) http://www.newscientist.com/news/print.jsp?id=$2
PRINT http://(www*.|)sundayherald.com/([0-9]*[0-9]) http://www.sundayherald.com/print$2
PRINT http://(www*.|)greenpeace.org/press/release?item_id=** $&&print=1
PRINT http://(www*.|)nytimes.com/(aponline|20[0-9][0-9]/[01][0-9]/[0-3][0-9])/**.html?** $&&pagewanted=print
PRINT http://writ.news.findlaw.com/(*/20[0-9]*.html) http://writ.news.findlaw.com/scripts/printer_friendly.pl?page=/$1
PRINT http://(www*.|)oreillynet.com/pub/(wlg/[0-9]*) http://www.oreillynet.com/lpt/$2
PRINT http://(www*.|)siliconvalley.com/mld/siliconvalley/news/[0-9]*[0-9].htm $&?template=contentModules/printstory.jsp
PRINT http://(www*.|)grandforks.com/mld/grandforks/([0-9]*[0-9]).htm $&?template=contentModules/printstory.jsp
PRINT http://(www*.|)centredaily.com/mld/centredaily/*.htm $&?template=contentModules/printstory.jsp
PRINT http://rss.com.com/[0-9][0-9][0-9][0-9]-(*.html)?*tag=feed* http://rss.com.com/2102-$1?tag=ni_print
PRINT http://(www*.|)securityfocus.com/(*/[0-9]*) http://www.securityfocus.com/printable/$2
PRINT http://(www*.|)perl.com/pub/a/(20*/*/*/*.html) http://www.perl.com/lpt/a/$2
PRINT http://(www*.|)newmediazero.com/news/story.asp?id=(*) http://www.newmediazero.com/output/print.asp?id=$2
PRINT http://(www*.|)tribnet.com/news/story/([0-9]*).html http://www.tribnet.com/news/v-printer/story/$2.html
PRINT http://straitstimes.asia1.com.sg/singapore/story/0,*,(*),00.html* http://straitstimes.asia1.com.sg/storyprintfriendly/0,1887,$1,00.html
PRINT http://(www*.|)nettavisen.no/servlets/page?*(item=[0-9]*) http://www.nettavisen.no/servlets/page?section=99&$2
PRINT http://(www*.|)cbronline.com/latestnews/* http://www.cbronline.com/print_friendly/$2
PRINT http://(www*.|)cbronline.com/article_news.asp?guid=(**) http://www.cbronline.com/article_news_print.asp?guid=($2)
PRINT http://(www*.|)thestar.com/NASApp/cs/ContentServer?pagename=thestar/Layout/Article_Type1(&c=Article&cid=**) http://www.thestar.com/NASApp/cs/ContentServer?pagename=thestar/Layout/Article_PrintFriendly$2
PRINT http://www.thestar.com.my/news/story.asp?(file=**) http://www.thestar.com.my/services/printerfriendly.asp?$1
PRINT http://(www*.|)local6.com/*/*/detail.html $&?use=print
PRINT http://(www*.|)washingtonpost.com/wp-dyn/articles/(*-*).html http://www.washingtonpost.com/ac2/wp-dyn/$2?language=printer
PRINT http://www.indystar.com/articles/0/([0-9]*[0-9]-[0-9]*)-*.html http://www.indystar.com/articles/0/$1-P.html
PRINT http://wnd.com/news/article.asp?ARTICLE_ID=(*) http://wnd.com/news/printer-friendly.asp?ARTICLE_ID=$1
PRINT http://(www*.|)timesleader.com/mld/timesleader**/([0-9]*).htm $&?template=contentModules/printstory.jsp
PRINT http://(www*.|)voanews.com/article.cfm?objectID=(*) http://www.voanews.com/PrintArticle.cfm?objectID=$2
PRINT http://(www*.|)voanews.com/*/20[0-9][0-9]-[0-9][0-9]-[0-9][0-9]-*.cfm $&?renderforprint=1
PRINT http://(www*.|)(dmeurope.com|europemedia.net)/*.asp?ArticleID=([0-9]*) $&&Print=true
PRINT http://fpeng.peopledaily.com.cn/(20[0-9][0-9][0-9][0-9]/*)/eng(*_*).shtml http://fpeng.peopledaily.com.cn/$1/print$2.html
PRINT http://(www*.|)newsfactor.com/perl/story/(*).html http://www.newsfactor.com/perl/printer/$2/
PRINT http://(www*.|)rockymountainnews.com/drmn/*/article/0,*,(*),00.html http://www.rockymountainnews.com/drmn/cda/article_print/1,1983,${2}_ARTICLE-DETAIL-PRINT,00.html
PRINT http://(www*.|)nzherald.co.nz/storydisplay.cfm?storyID=([0-9]*[0-9])&** http://www.nzherald.co.nz/storyprint.cfm?storyID=$2
PRINT http://(www*.|)nzherald.co.nz/index.cfm?*ObjectID=([0-9]*[0-9]) http://www.nzherald.co.nz/print.cfm?objectid=$2
PRINT http://(www*.|)enterpriseitplanet.com/networking/features/article.phpr/(*) http://www.enterpriseitplanet.com/networking/features/print.php/$2
PRINT http://(www*.|)planetark.(org|com)/dailynewsstory.cfm/newsid/([0-9]*[0-9])/story.htm http://www.planetark.com/avantgo/dailynewsstory.cfm?newsid=$3
PRINT http://(www*.|)popularmechanics.com/*/*/20[0-9][0-9]/*/*/ $&print.phtml
PRINT http://(www*.|)docguide.com/news/content.nsf/news/(*) http://www.docguide.com/news/content.nsf/NewsPrint/$2
PRINT http://(www*.|)newsmax.com/archives/articles/20[0-9][0-9]/**.shtml http://www.newsmax.com/cgi-bin/printer_friendly.pl?page=$&
##PRINT http://(www*.|)eweek.com/article2/(0,*.asp) http://www.eweek.com/print_article/$2
PRINT http://(www*.|)scienceblog.com/community/modules.php?name=News&file=article&sid=(*) http://www.scienceblog.com/community/modules.php?name=News&file=print&sid=$2
PRINT http://(www*.|)scienceblog.com/community/article([0-9]*[0-9]).html http://www.scienceblog.com/community/article-print-$2.html
PRINT http://(www*.|)scienceblog.com/cms/*_([1-9]*[0-9]) http://www.scienceblog.com/cms/node/$2/print
##PRINT http://(www*.|)sciencedaily.com/(releases/20[0-9][0-9]/*/[0-9]*[0-9].htm) http://www.sciencedaily.com/print.php?url=$2
PRINT http://(www*.|)aftenposten.no/*/local/article.jhtml?articleID=(*) http://www.aftenposten.no/template/droplets/utskriftsvennlig.jhtml?articleID=$2
PRINT http://(www*.|)aftenposten.no/**/article*.ece $&?service=print
PRINT http://(www*.|)dailytimes.com.pk/default.asp?(page=story_*) http://www.dailytimes.com.pk/print.asp?$2
PRINT http://(www*.|)vnunet.com/News/(*) http://www.vnunet.com/Print/$2
PRINT http://(www*.|)vnunet.com/news/(*) http://www.vnunet.com/print/it/$2
PRINT (http://*.boston.com/**/articles/[0-9][0-9][0-9][0-9]/[0-9][0-9]/[0-9][0-9]/*/)(?|)** $1?mode=PF
PRINT http://(www*.|)worldnetdaily.com/news/article.asp?ARTICLE_ID=(*) http://www.worldnetdaily.com/news/printer-friendly.asp?ARTICLE_ID=$2
PRINT http://(www*.|)eet.com/sys/news/(*) http://www.eet.com/printableArticle?doc_id=$2
PRINT http://(www*.|)informationweek.com/story/showArticle.jhtml**?articleID=(*) http://www.informationweek.com/shared/printableArticle.jhtml?articleID=$2
PRINT http://(www*.|)edinburghnews.com/index.cfm?id=(*) http://www.edinburghnews.com/print.cfm?id=$2
PRINT http://www.fredericksburg.com/News/FLS/20[0-9][0-9]/**[0-9] $&/printer_friendly
PRINT http://(www*.|)nj.com/newsflash/*/index.ssf?/cgi-free/getstory_ssf.cgi%3f* http://www.nj.com/enter/index.ssf?/printer/printer.ssf%3f/newsflash/get_story.ssf%3f/cgi-free/getstory_ssf.cgi%3f$2%3faponline
PRINT http://(www*.|)nj.com/newsflash/*/index.ssf?(/**-0/[0-9]*[0-9]).xml http://www.nj.com/printer/printer.ssf?$2.xml?aponline
## ABC BUSTED THIS ## PRINT http://(www*.|)abc.net.au/(*/news/stories/s*[0-9].htm) http://www.abc.net.au/cgi-bin/common/printfriendly.pl?/$2
## ABC BUSTED THIS ##PRINT (http://(www*.|)abc.net.au/news/newsitems/**.htm) http://www.abc.net.au/cgi-bin/common/printfriendly.pl?$1
## ABC BUSTED THIS ##PRINT http://(www*.|)abc.net.au/(ra/newstories/*.htm) http://www.abc.net.au/cgi-bin/common/printfriendly.pl?/$2
## ABC BUSTED THIS ##PRINT http://(www*.|)abc.net.au/am/content/20[0-9][0-9]/s[0-9]*[0-9].htm http://www.abc.net.au/cgi-bin/common/printfriendly.pl?$&
PRINT http://(www*.|)betterhumans.com/(News/news|Features/**).aspx?articleID=(*) http://www.betterhumans.com/Print/index.aspx?articleID=$3
PRINT http://(www*.|)gulfnews.com/Articles/*.asp?ArticleID=(*) http://www.gulfnews.com/Articles/print.asp?ArticleID=$2
PASS http://(*.|)news.yahoo.com/**&printer=1
PRINT http://(*.|)news.yahoo.com/news?tmpl=story**&u=** $&&printer=1
PRINT http://(*.|)news.yahoo.com/s/ap/20[0-9][0-9]** $&&printer=1
PRINT http://(www*.|)globeandmail.com/servlet/ArticleNews/TPStory/(**)/Idx http://www.theglobeandmail.com/servlet/ArticleNews/TPPrint/$2/
PRINT http://(www*.|)(the|)globeandmail.com/servlet/story/(*)/BNStory/(**) http://www.theglobeandmail.com/servlet/story/$3/BNPrint/$4
PRINT http://(www*.|)boston.com/dailyglobe2/203/(**)+.shtml http://www.boston.com/dailyglobe2/203/$2P.shtml
PRINT http://slate.msn.com/id/(*)/** http://slate.msn.com/toolbar.aspx?action=print&id=$1
PRINT http://eetimes.com/sys/news/(*) http://eetimes.com/printableArticle?doc_id=$1
PRINT http://(www*.|)eetimes.com/**/showArticle.jhtml?articleID=([0-9]*[0-9]) http://www.eetimes.com/article/printableArticle.jhtml?articleID=$2
##PRINT http://(www*.|)msnbc.com/news/(*).asp http://www.msnbc.com/m/pt/printthis.asp?storyID=$2
PRINT http://(www*.|)msnbc.msn.com/id/[0-9]*[0-9]/ $&print/1/displaymode/1098/
PRINT http://(www*.|)af.mil/stories/story.asp?storyID=(*) http://www.af.mil/stories/story_print.asp?storyID=$2
PRINT http://(www*.|)fortune.com/fortune/technology/articles/0,*,(*),00.html http://www.fortune.com/fortune/print/0,15935,$2,00.html
PRINT http://(www*.|)salon.com/tech/wire/(20**)/index.html http://www.salon.com/tech/wire/$2/print.html
PRINT http://(www*.|)newsday.com/(news/**)/(*),0,*.story?coll=* http://www.newsday.com/templates/misc/printstory.jsp?slug=$3&section=/$2
PRINT http://(www*.|)dfw.com/mld/*/news/*/[0-9]*.htm $&?template=contentModules/printstory.jsp
PRINT http://orlando.bizjournals.com/orlando/stories/20[0-9][0-9]/[0-9][0-9]/[0-9][0-9]/story*.html?t=printable $&?t=printable
## osnews uses the Referrer header
PRINT http://(www*.|)osnews.com/story.php?news_id=(*) 302:http://www.osnews.com/printer.php?news_id=$2
##PRINT http://(www*.|)forbes.com/(20[0-9][0-9]/[0-9][0-9]/[0-9][0-9]/*).html** http://www.forbes.com/$2_print.html
##PRINT http://(www*.|)forbes.com/(**/20[0-9][0-9]/[0-9][0-9]/[0-9][0-9]/*).html** http://www.forbes.com/$2_print.html
PRINT http://((www*.|)forbes.com)/**/(20[0-9][0-9]/[0-9][0-9]/[0-9][0-9]/*).html http://$1/$3_print.html
PRINT http://sci.newsfactor.com/perl/story/(*).html http://sci.newsfactor.com/perl/printer/$1/
PASS http://(www*.|)sfgate.com/cgi-bin/article.cgi?**&type=printable
PRINT http://((www*.|)sfgate.com/cgi-bin/article.cgi?**)&type=* http://$1
PRINT http://(www*.|)sfgate.com/cgi-bin/article.cgi?f=(**) http://sfgate.com/cgi-bin/article.cgi?file=$2&type=printable
PRINT http://(www*.|)sfgate.com/cgi-bin/article.cgi?(f|file)=(**.DTL) http://sfgate.com/cgi-bin/article.cgi?file=$3&type=printable
PRINT http://(www*.|)iht.com/articles/(*).html http://www.iht.com/cgi-bin/generic.cgi?template=articleprint.tmplh&ArticleId=$2
PRINT http://(www*.|)stuff.co.nz/stuff/0,*,(*),00.html http://www.stuff.co.nz/stuff/print/0,1478,$2,00.html
PRINT http://(www*.|)smalltimes.com/document_display.cfm?document_id=(*) http://www.smalltimes.com/print_doc.cfm?doc_id=$2
PRINT http://(www*.|)canada.com/*/story.asp?id=(*) http://www.canada.com/components/print.aspx?id=$2
PRINT http://(www*.|)nature.com/nsu/(*/*.html) http://www.nature.com/nsu/nsu_pf/$2
PRINT (http://(www*.|)nature.com/news/20[0-9][0-9]/*)/full/([0-9]*).html $1/pf/$3_pf.html
PRINT http://(www*.|)javaworld.com/javaworld/(*/*).html http://www.javaworld.com/javaworld/${2}_p.html
PRINT (http://(www*.|)linuxworld.com/story/[0-9]*[0-9]).htm $1_p.htm
PRINT http://(www*.|)businessweek.com/(*/content/*/*.htm) http://www.businessweek.com/print/$2
PRINT http://(www*.|)theage.com.au(/articles/20**.html)** http://www.theage.com.au/cgi-bin/common/popupPrintArticle.pl?path=$2
PRINT http://(www*.|)kansascity.com/(mld/kansascity/news/**.htm) http://www.kansascity.com/($2)?template=contentModules/printstory.jsp
PRINT http://(www*.|)miami.com/mld/miamiherald**/[0-9]*.htm $&?template=contentModules/printstory.jsp
PRINT http://breakingnews.iol.ie/news/story.asp?(j=**) http://breakingnews.iol.ie/email/printer.asp?$1
PRINT http://(www*.|)enn.com/news/enn-stories/*/*/*/s_([0-9]*[0-9]).asp http://www.enn.com/extras/printer-friendly.asp?storyid=$2
PRINT http://(www*.|)chron.com/cs/CDA/ssistory.mpl/(*/[0-9]*[0-9]) http://www.chron.com/cs/CDA/printstory.hts/$2
PRINT http://(www*.|)scotlandonsunday.com/index.cfm?id=(*) http://www.scotlandonsunday.com/print.cfm?id=$2
PASS http://news.scotsman.com/print.cfm?**
PRINT http://news.scotsman.com/*.cfm?id=(*) http://news.scotsman.com/print.cfm?id=$1
##PRINT http://home.kyodo.co.jp/all/display.jsp?an=* http://home.kyodo.co.jp/all/printer_friendly.jsp?an=$1
PRINT http://(www*.|)foxnews.com/story/0,*,(*),00.html http://www.foxnews.com/printer_friendly_story/0,3566,$2,00.html
PRINT http://(www*.|)taipeitimes.com/News/edit/archives/20[0-9][0-9]/[0-9][0-9]/[0-9][0-9]/* $&/print
PRINT http://(www*.|)techtv.com/news/*/story/0,*,(*),00.html http://www.techtv.com/news/print/0,23102,$2,00.html
PRINT http://(www*.|)theregister.(com|co.uk)/20[01][0-9]/[0-9][0-9]/[0-9][0-9]/*/ $&print.html
PRINT http://osdir.com/Article([0-9]*).phtml http://osdir.com/PrintArticle$1.phtml
PRINT http://(www*.|)linux.com/article.pl?(sid=**) http://www.linux.com/print.pl?sid=$2
PASS ftp://**
PASS http://*.ac.uk/**
PASS http://webmail.aol.com/**
PASS http://images.google.com/images?**
PASS http://ads.nana.co.il/**
PASS http://ads.sms.at/**
PASS http://ads.x10.com/misc/*.gif
PASS http://(www*.|)infopark.de/images/**.gif
PASS http://(www*.|)bund.de/**
PASS http://*.sears.com/**
PASS http://(*.|)aliantlink.com/**
PASS http://(*.|)sysco.com/**
PASS http://(*.|)esysco.net/**
PASS http://(*.|)lead-pursuit.com/**
PASS http://(*.|)cervelo.com/**
PASS http://(*.|)alternate.de/**
PASS http://*.ereader.com/**
PASS http://*.atlasf1.com/**
PASS http://*.mediasupply.com/**
AD http://(www*.|)solariscentral.org/images/ads/**
AD http://(www*.|)superguadagni.net/public/banner/**.gif
AD http://(www*.|)girlsnavi.net/bn/*.gif
AD http://tremulous.bricosoft.com/images/banniere/b.php
AD http://(www*.|).net-security.org/images/ads/**
PASS http://*.(edu|gov|org)(|.au)/**.(gif|jpg)
# two exceptions from Putinas Piliponis
PASS http://*.bov.com/**
PASS http://*.exler.ru/**
PASS http://(www*.|)cbc.ca/mycbc/images/banner/banner*.gif
PRINT http://(www*.|)cbc.ca/story/**.html $&?print
PRINT http://(www*.|)cbc.ca/stories/(**) http://www.cbc.ca/cgi-bin/templates/print.cgi?/$2
PASS http://(www*.|)universetoday.com/am/publish/printer_*.html
PRINT http://(www*.|)universetoday.com/am/publish/(*).html* http://www.universetoday.com/am/publish/printer_$2.html
ADPOPUP http://ads.x10.com/traffic/*.htm
ADPOPUP http://ads.x10.com/advertisement/*.htm
ADPOPUP http://ads.x10.com/weather/**.htm
ADPOPUP http://ads.x10.com/yahoo/*.html
ADJS http://ads.x10.com/720x300/*/1/DSC
AD http://ads.x10.com/?**
PASS http://ads.x10.com/**
ADJS http://ads.**.js
## AD http://ads.x10.com/?**
AD http://ads.x10.com/**.gif
AD http://images.x10.com/traffic/*.jpg
AD http://ad.**.gif
AD http://ad.*/bb.cgi?cmd=ad**
AD http://ads.**.gif
AD http://ads.**.gif**
AD http://ads[0-9]*.**.gif**
ADPOPUP http://businessfactory.delphi.com/redir/**
##AD http://promo.*/**/*468*.gif
PASS http://banners.wunderground.com/banner/**.gif
AD http://businessfactory.delphi.com/delphi/exciting2.gif?**
AD http://businessfactory.delphi.com/returnfeed.asp?**
AD http://(www*.|)internetnews.com/icom_includes/special/**.(gif|jpg)
AD http://ads*.realcities.com/ads*/**.gif
AD http://banner*/**.gif
AD http://*/[0-9]*_banner_*.gif
AD http://*/*_ban/*.gif
AD http://*/adsdisplay?**
AD http://(www*.|)computers.us.fujitsu.com/internal/comps/**.gif
AD http://tools.epersonals.com/farm/epersonals_160x600_*.jpg
AD http://banners.advancewebhosting.com/rt.phtml?**
AD http://banners.advancewebhosting.com/test_image.phtml?**
AD http://banners.nextcard.com/affiliates/AffiliateImages?**
AD http://banners.pennyweb.com/**.(gif|jpg)***
AD http://(www*.|)jandraffiliates.com/Images/**.gif
AD http://(www*.|)officemax.com/images/affArt/**.gif
AD http://(www*.|)banneranswers.com/bin/bimg.cgi?**
AD http://bannerpower.com/cgi-bin/bannerpic.cgi?**
AD http://media.interadnet.com/**.gif
AD http://tr.adinterax.com/**.(gif|jpg)**
PASS http://(www*.|)commbank.com.au/**.gif
PASS http://(www*.|)bluemountain.com/homegifs/*_ad.gif
PASS http://images.delphi.com/dir-html/partner/delphi/home_images/*_ad.gif
PASS http://(www*.|)techiwarehouse.com/images/*_ad.gif
PASS http://*.hp.com/ghp/banners/*.gif
PASS http://*.hp.com/RealMedia/ads/Creatives/HP_emarketing/**
PASS http://img*.outblaze.com/graffiti.net/ads/login_ad.gif
PASS http://*.epicurious.com/**
PASS http://www.splenda.com/**
PASS http://(www*.|)zoomerang.com/images/recipient/**
AD http://**_ad.(gif|jpg)
AD http://**/affiliate-*.gif
AD http://ad.openfind.com.tw/cgi-bin/AD/advimage.exe?**
AD http://**/recip*/*.(gif|jpg)
AD http://ad.adware.hu/adware.big?**
AD http://ad.adware.hu/richfile.big?**
AD http://pagead*.googlesyndication.com/pagead/imgad?**
ADJSTEXT http://pagead*.googlesyndication.com/pagead/*.js
ADHTMLTEXT http://pagead*.googlesyndication.com/pagead/ads?**
ADHTMLTEXT http://groups.google.com/groups/adfetch?**
WEBBUG http://www.google.com/ig/images/tick.gif?**
WEBBUG http://www.google-analytics.com/__utm.gif?**
WEBBUG http://pagead*.googlesyndication.com/pagead/imp.gif**
WEBBUG http://ad.adware.hu/files/default
WEBBUG http://audit.median.hu/cgi-bin/track.cgi?**
WEBBUG http://pestiest.hu/cgi-bin/matesz/CP/est?MIME=image/gif**
WEBBUG http://m1.nedstatbasic.net/n?id=**
WEBBUG http://cme*.americangreetings.com/images/blankpixel.gif**
WEBBUG http://*.sky.com/x/x.gif
WEBBUG http://didtheyreadit.com/index.php/worker?code=**
WEBBUG http://*/RealMedia/ads/adstream_lx.cgi/intm/it/*.*.*/**?_RM_EMPTY_
ADJS http://*/RealMedia/ads/adstream_mjx.cgi/**
WEBBUGHTML http://a.boom.ro/ads.php?**
WEBBUGHTML http://a.boom.ro/track.php?**
COUNTER http://log.trafic.ro/cgi-bin/pl.dll?**
COUNTER http://m1.webstats4u.com/n?**
COUNTERJS http://m1.webstats4u.com/m.js
COUNTERJS http://storage.trafic.ro/js/trafic.js
ADJS http://a.boom.ro/boom.php?**
AD http://adverts.lrfairplay.com/adredir.imgw?**
AD http://adverts.lrfairplay.com/getadvert.imgw?**
AD http://**/RealMedia/ads/adstream_nx.(ads|cgi)/**
AD http://**/RealMedia/ads/adstream_lx.(ads|cgi)/**
AD http://**/RealMedia/ads/**.gif**
AD http://static.sky.com/images/pictures/[0-9]*[0-9].gif
AD http://escati.linkopp.net/cgi-bin/date.cgi?**
AD http://escati.linkopp.net/cgi-bin/countdown.cgi?**
AD http://escati.linkopp.net/cgi-bin/clock.cgi?**
AD http://(www*.|)journalregister.com/circads/*.jpg
AD http://(www*.|)sfbg.com/images/tiles/*_*.gif
AD http://*.instacontent.net/adserver/**
AD http://(www*.|)fhm.ro/nou/*.(gif|jpg)
AD http://ad2.ip.ro/please/showit/11/1/1/1/?typkodu=img&**
AD http://ads*.quarterserver.de/**.gif
AD http://ad*.haynet.com:8080*/[1-9]*x[1-9]*/**.gif
AD http://image.adition.net/**.gif
AD http://ads*.revenue.net/load/**.(gif|jpg)
AD http://(www*.|)engadget.com/common/media/bnr_*.gif
AD http://ad.spieletipps.de/cgi-bin/avp/bimg.pl?**
AD http://ad.spieletipps.de/avp/banners/**.gif
ADHTML http://ad.spieletipps.de/cgi-bin/avp/banners.pl?**
ADHTML http://(www*.|)jittery.com/bp/?user=**
ADHTML http://(www*|.)jittery.com/ads/*.cfm?**
ADHTML http://ads*.revenue.net/**/page.html**
ADHTML http://ads.betanews.com/adserve.iframe/**
ADHTML http://ads*.quarterserver.de/adserver/servlet/view/html/zone?**
ADPOPUP http://ads*.quarterserver.de/adserver/servlet/view/window/internal;**
ADPOPUP http://ads*.revenue.net/**pop.html**
ADPOPUP http://*.smartadserver.com/*/show*.asp?**
ADJS http://*.liberation.fr/inc/smartad.js
ADSWF http://*.smartadserver.com/**.swf**
ADSWF http://ads*.quarterserver.de/kelkoo/*.swf**
ADSWF http://(www*.|)scoop.co.nz/adserver/creative/**.swf**
ADSWF http://(www*.|)fhm.ro/nou/**.swf
ADSWF http://(www*.|)komplett.no/mlf/produkt/bilder/**.swf**
ADSWF http://(www*.|)engadget.com/common/media/*.swf
ADSWF http://ad2.ip.ro/logos/*.swf?**
ADSWF http://194.145.249.110/images/logoAnim*.swf
ADSWF http://img-catgeo.paginegialle.it/clienti/**/A/*.swf**
ADSWF http://*.tiser.com.au/images/**.swf**
ADJS http://*.tiser.com.au/jserver/**
ADJS http://ad-uk.tiscali.com/jserver/**
AD http://*.tiser.com.au/nserver/**
AD http://*.tiser.com.au/images/**
ADHTML http://ad2.ip.ro/please/code?**
ADHTML http://ads.specificpop.com/code?**
ADHTML http://ads.specificclick.com/code?**
ADHTML http://www.imdb.com/google/box?**
ADHTML http://**/RealMedia/ads/adstream_sx.ads/**
ADHTML http://ad.aboutwebservices.com/cgi-bin/ad/**
ADHTML http://adserver.**/ads/adstream_nx.cgi/**.html*
ADHTML http://adserve.viaarena.com/admin/frmServeBanner.aspx?**&IFrame=1**
ADHTML http://ads.***/ads/adstream_sx.ads/**
ADHTML http://nztv.untd.com/webads/**.htm**
ADHTML http://www.penny-arcade.com/ads/advert/index.php
ADHTML http://exchange.adbanners.com/serve-banner.php?**
ADHTML http://www*.bannerspace.com/asp/getad_fc.asp?**
ADHTML http://(www*.|)rednova.com/_include/banners/**.html
ADHTML http://ad[0-9]*.neodatagroup.com/ad/seatb.jsp?**
ADJS http://ad1.neodatagroup.com/uploads/js/*.js
AD http://*.adserver.com/w/cp.x;**;tid=[78];**
AD http://cdn.specificmedia.com/contents/**.jpg
AD http://adserver*-images.backbeatmedia.com/**.gif
ADJS http://nztv.untd.com/webads/js/adtags.js
# oh the irony!
PASS http://(www*.|)nytimes.com/2004/01/19/technology/19popup.html**
ADPOPUP http://*.adserver.com/w/cp.x;**
ADPOPUP http://*.adserver.yahoo.com/a?**
ADPOPUP http://*.infinityads.com/loading.php?**
ADPOPUP http://bannerads.zwire.com/bannerads/AdWindow.asp?**
ADPOPUP http://simplemp3s.com/exit.htm
ADPOPUP http://(www*.|)adexit.de/page.phtml?**
ADPOPUP http://sweepstakes.yahoo.com/popups/*.html
ADPOPUP http://squaregallery.com/cgi-bin/ad/popup?**
ADPOPUP http://adserv.internetfuel.com/cgi-bin/newredirect.cgi?**
ADPOPUP http://adserv.internetfuel.com/cgi-bin/omnidirect.cgi?**
ADPOPUP http://nitrous.exitfuel.com/?**
ADPOPUP http://(www*.|)nightscapecreations.com/newsite/contest_pop.cfm
ADPOPUP http://adv.surinter.net/popuprich.cfm?**
ADPOPUP http://adserver.tribuneinteractive.com/event.ng/**
ADPOPUP http://*.targetnet.com/ad/id=*&opt=hkj**
ADPOPUP http://*.casalemedia.com/V2/**.html**
ADPOPUP http://*.casalemedia.com/c?**
ADPOPUP http://64.156.188.97/**.htm
AD http://64.156.188.97/fclick/*.gif
AD http://65.119.30.151/UploadFilesFor*/*125x125ad.gif
AD http://isg*.casalemedia.com/V2/**.(gif|jpg)
AD http://(www*.|)nightscapecreations.com/newsite/imgs/contest*.jpg
AD http://*.clicrevenus.com/cgi-bin/affc0?*.gif**
AD http://s*.xperformance.net/sys/ads?**
ADHTML http://*/ads/[0-9]*.htm
ADHTML http://sfads.osdn.com/*.html
ADHTML http://ads.osdn.com/?ad_id=**
ADHTML http://focusin.ads.targetnet.com/ad/id=*opt=hhj*
ADTHTML http://adsfac.net/ffp.asp?loc=*&js=no
ADJS http://adsfac.net/ad.asp?loc=**
ADSWF http://adsfac.net/ag.asp?**
AD http://adsfac.net/getCreative.asp?**
AD http://focusin.ads.targetnet.com/ad/id=*opt=hij*
AD http://fmads.osdn.com/banner/**
AD http://ads.osdn.com/?ad_id=**
AD http://ads.addynamix.com/**
AD http://(www*.|)zanox-affiliate.de/bin/z_ct_ppc.dll?*
AD http://ar.atwola.com/image/**
AD http://ar.atwola.com/content/**
ADJS http://ar.atwola.com/html/**;ctype=application/x-javascript**
ADJS http://ar.atwola.com/file/adsWrapper.js
ADJS http://ar.atwola.com/file/adsEnd.js
ADJS http://**/ads/adstream_(m|)jx.ads/**
ADJS http://*.flycast.com/FlycastUniversal/
ADJS http://*.flycast.com/**/js/**
ADJS http://*.adbureau.net/jserver/**
ADJS http://ad.adverticum.net/js.prm?**
ADJS http://amch.questionmarket.com/adsc/**/randm.js
ADJS http://amch.questionmarket.com/adsc/**/decide.php?**
ADJS http://ads.gamespy.com/jserver/**?unique
ADJS http://*.adbrite.com/mb/text_group.php?**
ADSWF http://adcontent.gamespy.com/**.swf**
ADSWF http://(www*.|)minebox.com/images/*.swf
ADSWF http://(www*.|)independent.co.uk/img/commercial/skyscrapers/*.swf
ADSWF http://creative.apn.co.nz/*.swf?**
ADHTML http://ad.yieldmanager.com/iframe**
ADHTML http://ad.yieldmanager.com/st?ad_type=iframe&**
ADHTML http://ad.yieldmanager.com/imp?**
ADJS http://ad.yieldmanager.com/rmtag2.js
AD http://content.yieldmanager.com/**.gif
AD http://(www*.|)independent.co.uk/images/*CARDSKYSCRAPER*.(gif|jpg)
AD http://adcontent.gamespy.com/**.(gif|jpg)
AD http://sher.index.hu/ad?**
AD http://creative.apn.co.nz/**.gif**
AD http://index.hu/res/hirdetes/img/**
AD http://(www*.|)ebcvg.com/img/**x600*.gif
AD http://(www*.|)smallcapcenter.com/baimg/img/**.gif
ADHTML http://ad.adverticum.net/html.prm?**
ADHTML http://ad2.netforum.hu/view.php?**
ADHTML http://ad.adware.hu/html.big?**
ADHTML http://ad.adware.hu/richadware.big?**
ADHTML http://view.atdmt.com**/iview/**
WEBBUG http://view.atdmt.com**/view/**
AD http://view.atdmt.com/avenuea/view/**
AD http://sp*.atdmt.com/b/**.(gif|jpg)
AD http://sp*.atdmt.com/ds/**.(gif|jpg)
AD http://*/img.atdmt.com/**.(gif|jpg)
AD https://*/img.atdmt.com/**.(gif|jpg)
ADJS http:/view.atdmt.com/*/jview/**
PASS http://(www&.|)bankrate.com/**
PASS http://(www*.|)comcast.net/**nav.swf**
PASS http://adsrv.bankrate.com/cgi-bin/accipiter/adserver.exe/site=brm/parent=brm/**
PASS http://www.americanexpress.com/*/images/banners/**.swf
PASS http://(www*.|)uniden.com.au/AUSTRALIA/resources_oz/images/flash/banner_*.swf
PASS http://images.motogp.com/flash/banner/**.swf**
PASS http://www.optimumnutrition.com/swf/**.swf
ADSWF http://**banner**.swf**
ADSWF http://cdn.atdmt.com/**/banners/**.swf**
ADSWF http://spd.atdmt.com/ds/**.swf?**
ADSWF http://(www*.|)ananova.com/assets/*banner.swf
ADSWF http://**/(ad|ads|banner*)/**.swf**
ADSWF http://*.infosync.*/adsync/**.swf**
ADSWF http://(www*.|)blargoc.co.uk/tekheads*.swf
ADSWF http://**/BD_flashlogo.swf
ADSWF http://fstrk.net/ag.asp?**
ADSWF http://**468x60*.swf**
ADSWF http://(www*.|)ad-blazer.com/**.swf
ADSWF http://(www*.|)bejba.com/banner/*/[Bb]anner*.swf
ADPOPUP http://(www*.|)bejba.com/banner/*/[Bb]anner*.html
ADPOPUP http://context*.kanoodle.com/cgi-bin/context.cgi?**&cgroup=finpop**
ADPOPUP http://*.coolsavings.com/scripts/PopUpWindow.asp?**
ADPOPUP http://205.180.85.40/novus/*.html
ADPOPUP http://media*.fastclick.net/novus/*.html
ADPOPUP http://media*.fastclick.net/w/pop.cgi?**
ADPOPUP http://media*.fastclick.net/w/pc.cgi?**
REWRITE http://media*.fastclick.net/w/get.media?*url=(http**) $1
ADHTML http://mbe.ru/adrevolver/banner?**
ADHTML http://media.adrevolver.com/adrevolver/banner?**
ADHTML http://media*.fastclick.net/w/get.media?t=[sn]**
ADSWF http://*.fastclick.net/fastclick.net/**.swf**
AD http://media*.fastclick.net/w/get.media?(**&|)sid=**
AD http://media*.fastclick.net/cid*/media*.gif
AD http://images.fastclick.net/ref*.gif
AD http://*.fastclick.net/fastclick.net/**.gif
AD http://cserver.mii.instacontent.net/fastclick/**.gif
AD http://*.infosync.*/adsync/**.(gif|jpg)
AD http://(www*.|)macinstein.com/adSQL/banners/*.JPG
AD http://**/adserver/image?ID=**
AD http://**/accipiter/adserver.exe**
AD http://accipiter.speedera.net/*-images.adbureau.net/**
AD http://**/accipiter/nserver/**
AD http://**-images.adbureau.net/**.gif
AD http://inl.adbureau.net/adserver/**/AAMSZ=**
AD http://*.flycast.com/**
AD http://*.linkexchange.ru/cgi-bin/**
AD http://(*.|)(advernet.ru|m2k.ru:8080)/(img|images)/([0-9]*).(gif|jpg|jpeg)
AD http://ad*.aaddzz.com/image/**
AD http://az.yandex.ru/bshow?banner=**
AD http://pics.rbc.ru/rbcmill/img/**.gif
AD http://content.ad-flow.com/**.gif
AD http://(www*.|)cbx*.com/images/button*.gif
AD http://(www*.|)cbx2.net/images/banbtn.gif
AD http://(www*.|)cbx*.com/*-*x*.gif
AD http://(www*.|)cbx*.com/cgi-bin/showbanner.cgi?**
AD http://(www*.|)looksmart.com/plainads/**
AD http://advertising.quote.com/**
AD http://(www*.|)advertisingbay.com/banner/**.GIF
AD http://gfx.tv2.dk/images/**banner*.gif
AD http://tourgfx.tv2.dk/spons/*.gif
AD http://(www*.|)makestuff.com/images/*_banner.gif
AD http://imp.partner2profit.com/bt/p2p.gif?**
AD http://images.about.com/partners/vpn/partnerbox/**.gif
AD http://images.about.com/specials/aboutads/**.gif
AD http://**/partners/*banner.gif
AD http://**/partners/**/468*.gif
AD http://**/partnertiles/*.gif
AD http://partner.xerox.com/asknancy/images/*banner.gif
AD http://images.villagevoice.com/tiles/*.gif
AD http://**/ad_graphics/**
AD http://(www*.|)quotestream.com/images/webbanners/**
AD http://rewards.macandbumble.com/rectangle_banners/*.(jpg|gif)
AD http://(www*.|)skins.be/banners/**
AD http://(www*.|)skins.be/*_60x468_*.gif
AD http://(www*.|)skins.be/ss/*.gif
AD http://citi.bridgetrack.com/ads/image/_raw.htm?**
AD http://adpush.dreamscape.com/adpush/bin2/adserve.cgi?**
AD http://*/DA/**.(gif|jpg)
AD http://spinbox*.filez.com/?*
AD http://*.spinbox.net/?SIT=**
AD http://*.spinbox.net/?AI=**
AD http://spinbox.*/DA/**
AD http://*.dvlabs.com/klipmart/**.(gif|jpg)
WEBBUG http://*.kliptracker.com/klipinsert*.gif**
ADHTML http://klipads.dvlabs.com/klipmart/**.htm
ADSWF http://*.dvlabs.com/klipmart/**.swf**
ADSWF http://images.tvnz.co.nz/spinbox/**.swf
ADJS http://*.spinbox.net/?DC=**&JS=Y**
ADJS http://klipads.dvlabs.com/klipmart/**.js
ADHTML http://*.spinbox.net/?DC=**
ADHTML http://servedby.advertising.com/site=**
ADJS http://*servedby.advertising.com/pops=**
AD http://*servedby.advertising.com/**
AD http://babs*.dk/pro-banner.php*?**
AD http://babs.dk/uimg/**.gif
AD http://ad.borsen.dk/uimg/**
AD http://ad.admediaserver.com/host/jserv_imp.php/**
AD http://ad.admediaserver.com/host/reg_imp.php/**
AD http://(www*.|)alphatradefn.com/l.php?**
AD http://(www*.|)aip.org/aserver/**.gif
AD http://*.adoptimizer.eu/adi.php**
ADHTML http://*.adoptimizer.eu/adi-i.php**
##ADPOPUP http://*.doubleclick.net/adi/**;sz=**
ADHTML http://*.doubleclick.net/adi/**
ADHTML http://babs*.dk/pro-html.php*?**
ADHTML http://ad.borsen.dk/html.php*?**
ADHTML http://ad.borsen.dk/html?**
ADHTML http://(www*.|)wkrn.com/global/ad.asp?type=core&**
ADHTML http://(www*.|)securityfocus.com/frames/ad.html?**
ADHTML http://bannervip.webjump.com/webjump/valet/b1.asp?**
ADHTML http://(www*.|)nettaxi.com/cit_frames/ae-frame.html
ADHTML http://fs.dai.net/htm/nettaxi/leader.html
ADHTML http://204.246.215.162/~banners/frame.html
ADPOPUP http://**popover.cfm?**
ADPOPUP http://**popunder;**
ADPOPUP http://**popunder.asp**
ADPOPUP http://**popunder.htm**
ADPOPUP http://**-popback-*.htm*
REWRITE http://ad.doubleclick.net/clk;*?(http:**) $1
PASS http://ad.doubleclick.net/crossdomain.xml
PASS http://*.doubleclick.net/clk;**
PASS http://fastbuy.doubleclick.net/WebSteps?**
ADJS http://*.doubleclick.net/adj/**
PASS http://(www*.|)doubleclick.net/**
PASS http://ad.doubleclick.net/cgi-bin/**
ADHTML http://ad.doubleclick.net/adl/**
AD http://*.doubleclick.net/**
AD http://(www*.|)doubleclick.net/optoutbanner/movies-ny.gif
AD **.doubleclick.net/viewad/**.gif
ADJS http://*.valueclick.com/cycle?**&t=js**
ADJS http://*.valueclick.com/jsmaster
ADPOPUP http://images.ad-flow.com/**/bnr_*x*/bnr.html
AD http://ads*.ad-flow.com/?DC=**
AD http://ads*.ad-flow.com/?SIT=**
AD http://(www*.|)bepaid.com/images/*.gif
AD http://stats.adage.com/sponsors/*/banners/**
AD http://*.img.pheedo.com/img.phdo?**
AD http://*.valueclick.com/**cycle?**
AD http://*.valueclick.com/ad.s/*.gif
AD http://image.click2net.com/?**
AD http://pub.nomade.fr/media/*.gif
AD http://*.pointroll.com/**Media/**.(gif|jpg)
AD http://*.pointroll.com/DefaultAd/?**
AD http://(www*.|)click-fr.com/print.cgi?a=**
AD http://(www*.|)click-fr.com/printj.cgi?a=**
ADHTML http://(www*|).click-fr.com/printk.cgi?a=**
##AD http://(www*.|)theregister.co.uk/media/*.gif
AD http://(www*.|)theregister.co.uk/media/1098.gif
ADHTML http://a.tribalfusion.com/f.ad?**
ADPOPUP http://a.tribalfusion.com/p.media/**.html
ADJS http://a.tribalfusion.com/j.ad?**
AD http://*tribalfusion.*/media/**.(gif|jpg)
AD http://a.tribalfusion.com/i.ad?**
ADSWF http://*tribalfusion.*/**.swf?**
ADSWF http://*.pointroll.com/**/Media/**.swf**
ADSWF http://(www*.|)europemedia.net/art/*_(button|banner).swf
ADSWF http://(www*.|)der-schacht.com/**/banner*.swf
ADSWF http://(www*.|)2cpu.com/Images/zzqbanner*.swf
ADSWF http://java.yahoo.com/a/1-/flash/datek/datekgan46860.swf
ADSWF http://**java*.yahoo.com/**.swf**
ADSWF http://(www*.|)theregister.co.uk/media/*.swf
ADSWF http://movies.go.com/img/movie_search.swf
ADSWF http://(www*.|)beijing-olympic.org.cn/eolympic/image/title_*.swf
ADSWF http://(www*.|)nrl.com.au/s200[0-9]/images/flash/intro.swf
AD    http://(www*.|)nrl.com.au/s200[0-9]/images/frontpage/*banner*.gif
AD    http://(www*.|)nrl.com.au/s200[0-9]/images/stateoforigin/*banner*.gif
AD    http://(www*.|)nrl.com.au/s200[0-9]/images/frontpage/telstra_button_bigevent.gif
AD    http://(www*.|)nrl.com.au/s200[0-9]/images/frontpage/buttons/*.gif
AD    http://(www*.|)wallpaper-desktop.net/gifs/buttons/*.gif
PASS http://(www*.|)cjr.org/images/**
PASS http://212.113.5.84/media/53.gif
PASS http://(www*.|)conrad.fr/images/banner/banner_*.gif
PASS http://(www*.|)monitorbusiness.com.au/media/banner[0-9].gif
PASS http://**/toolbar/**
PASS http://(www*.|)cisco.com/images**banner**
PASS http://(www*.|)hp.cz/**/banner*.gif
PASS http://europa.eu.int/**
PASS http://*.westpac.com.au/images/banner_*.gif
PASS http://*.uni-essen.de/Library/images/**
PASS http://*.panasonic.de/common/images/banner/**gif
AD http://**/banner[_0-9]*.gif
AD http://**/banr/*.gif
AD http://**/hostban*.gif
AD http://212.113.5.84/media/*.gif
AD http://199.172.144.25/**.gif
AD http://**/*banner/*banner*.gif
AD http://**/linkpic*.gif
AD http://banner.topping.com.ua/cgi-bin/pbn_click.cgi?**
AD http://4click.com.ua/cgi-bin/pc100.cgi?**
AD http://b.abn.com.ua/abnl.php?**
PASS http://(www*.|)oilnet.ru/**
ADHTML http://ad.adriver.ru/cgi-bin/erle.cgi?**bt=1?**
ADHTML http://ad[0-9].lbn.ru/bb.cgi?cmd=ad&**
ADJS http://ad.adriver.ru/cgi-bin/erle.cgi?**bt=16?**
ADJS http://tx3.design.ru/cgi-bin/banner/**
ADJS http://bs.yandex.ru/show/**
AD http://ad[0-9].lbn.ru/bb.cgi?cmd=ad&pubid=**
AD http://(www*.|)bizlink.ru/cgi-bin/irads.cgi?**
AD http://1000stars.ru/cgi-bin/d1000.pl?**
AD http://1000stars.ru/cgi-bin/1000s.cgi?**
AD http://(www*.|)ranker.ru/scripts/sqltmex.dll?**
AD http://reklama.netskate.ru/banner.pl?action=Show**
AD http://*.reklama.ru/cgi-bin/banner/**
AD http://*rb[0-9].design.ru/cgi-bin/banner/**
AD http://(www*.|)banners.ru/cgi-bin/banner/**
AD http://sj[0-9].lenta.ru/cgi-bin/banner/**
AD http://banner.netskate.ru:82/*.gif
AD http://rotabanner.**/cgi-bin/**
AD http://*.totemcash.com/free/rotative_banner.php?**&size=**
AD http://ad[0-9].bb.ru/bb.cgi?cmd=ad**
AD http://gazetaru[0-9].express.ru**/?action=show&magic=**
AD http://**:8080/?action=show&magic=**
ADSWF http://**netoscope.ru/i/**.swf
ADHTML http://ad[0-9].bannerbank.ru/bb.cgi?cmd=ad&**
AD http://ad[0-9].bannerbank.ru/bb.cgi?cmd=ad**
AD http://engine.awaps.net/**.gif?**
AD http://468.smi.ru/cgi-bin/banner/**
AD http://195.54.209.142/cgi-bin/img?user=**
AD http://*.rambler.ru*/ban.ban?**
AD http://*.rambler.ru/top100/*.gif
AD http://bannervip.web1000.com/images/**.gif
AD http://212.24.32.74/cgi-bin/banner/**
AD http://ad.kimo.com.tw/**.gif
AD http://ad.linksynergy.com/fs-bin/show?**
AD http://banner.linksynergy.com/fs/banners/*.gif
AD http://**/bannerprogram/**.gif
AD http://(www*.|)nh.com/cgi/adgenie/loadimage.cgi?**
AD http://(www*.|)nh.com/adgenie/images/*.gif
AD http://(www*.|)hubbe.net/gfx/*banner*.gif
AD http://(www*.|)stomped.com/counter-bin/images/*_banner.gif
ADSWF http://(www*.|)ad.tomshardware.com/**.swf
ADSWF http://g.fool.com/**.swf
AD http://216.92.21.16/images/banner/**.swf
AD http://(www*.|)buffalo.com/images/banner*/**.gif
AD http://(www*.|)ad.tomshardware.com/cgi-bin/bd.m?**
AD http://(www*.|)ad.tomshardware.com/images/banner/**
AD http://(www*.|)ad.tomshardware.com/cgi-bin/bannerdisplay.m?**
AD http://(www*.|)tomshardware.com/images/new/pair.gif
AD http://(www*.|)tomshardware.com/images/new/100hot_logo.gif
AD http://(www*.|)bluesnews.com/images/*-ad.gif
AD http://(www*.|)bluesnews.com/images/sub_skyscr*.gif
AD http://(www*.|)sysopt.com/i/resellerratings2.jpg
AD http://(www*.|)sysopt.com/i/dicejobs.gif
AD http://(www*.|)sysopt.com/i/ss2000trial4.gif
AD http://(www*.|)sysopt.com/pcmech2.gif
AD http://(www*.|)sysopt.com/charles.gif
AD http://adopt.hbmediapro.com/contents/([0-9]*[0-9])/([0-9]*[0-9]).gif
AD http://(www*.|)voodooextreme.com/affiliate_search_120x90_bottom.gif
AD http://(www*.|)pcoutfitters.com/stores/ve/pco_anim.gif
AD http://(www*.|)dimension3d.com/images/jpabutton.gif
AD http://(www*.|)macintouch.com/images/acius08.gif
AD http://216.87.208.127/images/fb_button_105X30.gif
AD http://(www*.|)bcentral.com/images/bc/ie-static.gif
AD http://(www*.|)bcentral.com/images/meta/logo/msnlogo.gif
AD http://(www*.|)expedia.com/daily/home/images/amex.gif
AD http://(www*.|)expedia.com/daily/home/images/worldspan.gif
AD http://gs.cdnow.com/RP/CDN/graphics/home/home_visa.gif
AD http://cdn*.adsdk.com/CDN/**.gif
AD http://gs.cdnow.com/graphics/CMS/65/7865.gif
AD http://(www*.|)reel.com/content/reelimages/gbl/visa_logo.gif
AD http://(www*.|)reel.com/content/reelimages/gbl/nav_wingspan.gif
AD http://(www*.|)qrz.com/pix/[0-9]*.gif
AD http://(www*.|)hollywoodvideo.com/pix/gc_logo_blk.jpg
AD http://(www*.|)whatisthematrix.com/234x60_v5.gif
AD http://images.resellerratings.com/images/prices/*.(gif|jpg)
ADHTML http://(www*.|)resellerratings.com/price-direct-theinquirer.pl
ADHTML http://www.gizmag.com/ads/**.htm
ADPOPUP http://**ads/**popups/**.html
ADPOPUP http://**popups/**promo**.html
ADPOPUP http://32.96.232.10/teleweb/autopop/pop.asp?**
ADPOPUP http://(www*.|)novuslink.net/mk/get/fc2
ADPOPUP http://(www*.|)barnesandnoble.com/promo/coupon/popups/**.asp?**
ADPOPUP http://(www*.|)barnesandnoble.com/popup_cds*.asp?**
ADPOPUP http://adserver.trb.com/html.ng/**adtype=popwindow**
ADPOPUP http://images.weeklyworldnews.com/ad_server/**.html
ADPOPUP http://216.40.195.26/Reliaquote/**.html
ADPOPUP http://(www*.|)zdmcirc.com/zdmcirc/popups/*.html
AD http://(www*.|)zdmcirc.com/graphics/*pop*.gif
AD http://app-05.www.ibm.com/images/**.gif
AD https://ssl-images.amazon.com/images/**
## Now much too general. Yanking and making a new one.
##AD http://g-images.amazon.com/images/G/***.gif
ADHTML http://bwp.zdnet.com.au/search
ADHTML http://(www*.|)zdnet.com/fcgi-bin/becky/**
ADHTML http://rcm**.amazon.**/e/cm?**f=ifr**
ADHTML http://(www*.|)burstnet.com/cgi-bin/ads/**.cgi/**/RETURN-CODE
ADHTML http://*/cgi-bin/ad/inline?**
ADJS http://rcm.amazon.com/e/cm?**
ADJS http://ads[0-9].gamecity.net/modperl/jsformat.pl?**
ADJS http://(www*.|)burstnet.com/cgi-bin/ads/**.cgi/**/JS**
AD http://(www*.|)burstnet.com/cgi-bin/ads/ad*.cgi/ns
AD http://(www*.|)burstnet.com/cgi-bin/ads/**.cgi**
AD http://(www*.|)burstnet.com/gifs/*.gif
AD http://ds.serving-sys.com/BurstingRes/**.(gif|jpg)
AD http://ads[0-9].gamecity.net/images/*.gif
AD http://(www*.|)mp3.com/images/MP3Com/bigwords_120x25.gif
AD http://216.200.201.200/img/template/va-logo.gif
AD http://webcenters.netscape.com/shopping/gr/shoplogo.gif
AD http://(www*.|)video-now.com/research/salesBanner*.gif
AD http://*/cgi-bin/webconnect.dll?*
AD http://secure.webconnect.net/cgi-bin/webconnecthome.dll?**
AD http://209.90.128.55/click2/ad_bin/**.gif
AD http://usa.nedstatbasic.net/cgi-bin/referstat.gif?**
AD http://ad[0-9]*.yourmedia.com/datas/**/img/*.gif
AD http://ad[0-9].pamedia.com.au/images/*.gif
AD http://(*.|)linkbuddies.com/image.go?*
ADHTML http://mm.chitika.net/minimall?**
ADHTML http://*.linkbuddies.com/image.php?**
ADHTML http://*.desktopia.ru/index/iframe*.htm
ADHTML http://*.lbe.ru/cgi-bin/iframe/**
AD http://*.lbe.ru/bb.cgi?**
AD http://*.lbe.ru/cgi-bin/banner/**
AD http://(*.|)websponsors.com/**.gif
AD http://(www*.|)websponsors.com/**.gif
AD http://images.thisislondon.co.uk/**/sponsorship**.gif
AD http://ad.linkexchange.com/**
AD http://media.exchange-it.com/image.go?**
AD http://banner.freeservers.com/*.gif
AD http://banner.linkexchange.com/**
AD http://leader.linkexchange.com/**
AD http://**/*468[x_]60*.(gif|jpg)
AD http://gif.hitexchange.net/**
AD http://ad2.jwtt3.com/**
AD http://ads*.zdnet.com/**
AD http://adserv.net/but/*.gif
AD http://**/adserver/**.gif
AD http://**/adserver/**.jpg
AD http://**/adserver/banner_request/**
AD http://**/adserver.phtml**
AD http://**/adserver.exe/**
AD http://**/AdServer.exe/**
AD http://*/bm/*.gif
AD http://**/oasisi.php?**
AD http://assets.bravenet.com/bravenet/images/c/**
ADBG http://**/ad_bkgd.gif
ADBG http://ads.cmpnet.com/cmpnet/bgimage?**
ADBG http://(www*.|)bigcharts.com/images/ads/compaq.gif
ADBG http://cbs.marketwatch.com/images/ads/*_paper.gif
ADPOPUP http://cbs.marketwatch.com/membership/promo/memberB_access_promo.asp?**
ADHTML http://adserv.ads-tracker.com:8080/server/iframe-ad/client/realgn.com/banner/**
ADJS http://adserv.ads-tracker.com:8080/server/js-ad/client/realgn.com/banner/**
ADJS http://adserv.bravenet.com/cpceng.php?*type=sponsorbar*
ADJS http://mercury.bravenet.com/rover/**
ADJS http://au.java.yahoo.com/java/js_template/468_*.js
ADJS http://**/adjs.php?**
ADJS http://www.timesonline.co.uk/genads/**.js
ADJS http://news.ninemsn.com.au/9msnshared/spac.js
PASS http://adserver.yahoo.com/a?*p=broadcast*
WEBBUG http://geo.yahoo.com/f?**
WEBBUG http://*.adserver.yahoo.com/l?**
WEBBUG http://www.bravenet.com/setcookie.php
ADHTML http://*.yahoo.com/java/js_template/728_reg_061501_loop_true.js
ADHTML http://ypn-js.overture.com/d/search/p/ypn/jsads/?**
ADHTML http://**/phpads.php**
PASS http://(www*.|)ad.nl/ad/**.gif
PASS http://(www*.|)mamut.com/images/ads/**
PASS http://(www*.|)retravision.com.au/**
PASS http://*.adobe.com/ads/**
PASS http://(www*.|)internettg.org/newsletter/dec00/images/ad_gif.gif
PASS http://((www*.|)skins.be)/framepic.php?(*) http://$1/kijk_onder.php?$3
PASS http://(*.|)skins.be/kijk_onder.php?**
PASS http://(www*.|)molendatabase.nl/nederland/kijk.php?**
PASS http://(www*.|)bikepoint.com.au/bikecontent/**
ADHTML http://adserver.news.com.au/html.ng/**
ADHTML http://**/(kijk*|adframe).php**
ADSWF http://adimages.go.com/ad/**.swf**
ADSWF http://**/(onlineads|[Aa]ds)/**.swf**
ADSWF http://assets.bravenet.com/bravenet/images/**.swf*
ADSWF http://ads.adx.nu/dn/html/**.swf**
ADSWF http://img-cdn.mediaplex.com/**.swf
ADJS http://web.unltd.info/adx.js
ADJS http://adserv*.adtech.de/?addyn**
ADTEXT http://ads.addynamix.com/**
AD http://*.media.addynamix.com/**.gif**
AD http://adserv*.adtech.de/?adserv**
AD http://*/iserver/**/AAMSZ=**
AD http://(*.|)nytimes.com/adx/**.(jpg|gif)
AD http://graphics*.nytimes.com/marketing/**.(gif|jpg)
AD http://**/adcycle.cgi?**
AD http://*/adimages/**
AD http://adserver.*/**
AD http://adserv.*.de/images/**.(gif|jpg)
AD http://(www*.|)worknwoman.com/adserve/ads_2.cgi?page=*
AD http://(www*.|)worknwoman.com/adserve/images/**.gif
AD http://ads*.hyperbanner.net/gif.cfm?**
AD http://(www*.|)contentserver.com.au/ads/ad_loader.cfm?**
AD http://adimages.criticalmass.com/**
AD http://*/adserv/**.gif
AD http://*/ad_images/**.gif
AD http://*/nsadimages/**
AD http://**/ad/*.gif
AD http://*/ad?**
AD http://*/topcash/*.gif
AD http://*/*flashclick*.gif
AD http://205.153.208.93/?**
AD http://208.178.186.243/**.gif
AD http://image1.narrative.com/news/*.gif
AD http://**?adserv**
AD http://service.bfast.com/bfast/serve/**
AD http://service.bfast.com/bfast/serve?**
AD http://*/AdSwap.dll?**
AD http://*/images_ads/*.gif
AD http://*/button_ads/**.gif
AD http://*/images/*_ads/**.gif
AD http://*/adjuggler/images/*.gif
AD http://(www*.|)thenation.com/images/aj/*.gif
AD http://*/clickthrough/*.gif
AD http://**/adimg/**
AD http://**/ad_imgs/**
AD http://**/ad_*.gif
AD http://adimg.egroups.com/img/**
AD http://adimgpj.voila.fr/bandeaux/**
AD http://(www*.|)jememarre.dpn.ch/publicite/**
AD http://(www*.|)clicmoi.com/cgi-bin/pub.exe?*
AD http://**/publicidad/**.gif
AD http://**/fwiadimages/**.gif
AD http://**/ban[0-9].gif
AD http://**/ban[0-9][0-9].gif
AD http://*/cobanner*.gif
AD http://*/cobanner*.jpg
AD http://**/ABS/**.GIF
AD http://**/ABS/**.JPG
AD http://*/annons/**.gif
AD http://*/servfu.pl?**
AD http://sunserver1.songline.com:1971/*?
AD http://ad.blm.net/image?**
AD http://*/ad/**.gif
AD http://*/onlinead/**.gif
AD http://*.mtree.com/xbs/**
AD http://*/ad/igc.cgi/**
AD http://cgi3.fxweb.com/v2-trackrun.cgi?**
AD http://(www*.|)fxweb.holowww.com/Assets/*.gif
AD http://yoda.cybereps.com:8000/**.gif
AD http://images.cybereps.com/traffic/images/**
AD http://my.netscape.com/publish/images/addchannel_anim.gif
AD http://**/showad.cgi?**
AD http://ads.hbv.de/**
AD http://*/viewbanner.php*?bannerID*
AD http://images*.iac-online.de/**.gif
AD http://service.bol.de/partner/*.gif
AD http://(www*.|)manager-magazin.de/mmo_banner/*.gif
AD http://**servant.guj.de/**
AD http://(www*.|)linux-magazin.de/banner*
AD http://banner.websitesponsor.de/nt-bin/show**
AD http://(www*.|)websitesponsors.com/cgi-bin/system/image?**
AD http://(www*.|)websitesponsors.com/cgi-bin/system/eimage?**
AD http://(www*.|)websitesponsors.com/referrals/*.gif
AD http://(www*.|)websitestop.com/clicktrade/**.gif
AD http://**/linkshare/**.(gif|jpg)
AD http://(*.|)iwin.com/ad/**
AD http://ad.*/cgi-bin/rotate.php*?*
AD http://**/468x60**.gif
AD http://**/(adview|adimage|viewbanner).php?**
AD http://admech.*.com/AdCall.asp?**
AD http://images.trafficmp.com/tmpad/**.gif
ADHTML http://*.trafficmp.com/tmpad/banner/itrack*.asp?**
ADHTML http://banners.webmasterplan.com/view.asp?**
ADHTML http://(www*.|)sponsorads.de/click.php?**
ADHTML http://info-ad.de/oben.php?**
PASS http://load.weatheronline.co.uk/**popup.html
PASS http://pages.ebay.com**popup.htm**
PASS http://*.ergophizmiz.com/**
PASS http://*.mini-itx.com/**
PASS http://www.saunalahti.fi/~ojn/photos/popup.html?**
PASS http://(*.|)pbs.org/includes/tvschedules/**popup.htm**
ADPOPUP **popup.htm**
ADPOPUP http://ad.iwin.com/tmpad/**.htm
ADPOPUP http://ad.iwin.com/tmpad/content/netflix/rollover.html
ADPOPUP http://ad.iwin.com/tmpad/banner/itrack.asp?**
ADPOPUP http://*.focalex.com/pops/popup(_general.emp|.mpl)?**
ADPOPUP http://*.focalex.com/offers.mpl?**
ADPOPUP http://*.puretec.de/werbung**
ADPOPUP http://popup.zmedia.com/popups/**
ADPOPUP http://popup.found404.com/*.*html?**
ADPOPUP http://popup.msn.com/*popupad.asp?**
ADPOPUP http://popup.msn.com/*PopupAd.asp?**
ADPOPUP http://(www*.|)gopopup.com/redir.php**
ADPOPUP http://(www*.|)deluxelink.de/script/gopopup.php?**
ADPOPUP http://(www*.|)sitepoint.com/popup/popup.php?**
ADPOPUP http://(www*.|)7host.com/**/pop.asp?**
ADPOPUP http://*.popupmoney.com/**.php?**
ADPOPUP http://**/popup_exit/**.*html**
ADPOPUP http://**/aoexit.shtml?**
ADPOPUP http://nitrous.*fuel.com/**/exitpop*.html**
ADPOPUP http://nitrous.*fuel.com/framer.html**
ADPOPUP http://nitrous.*fuel.com/sites/hp4group2.html
ADPOPUP http://nitrous.*fuel.com/sites/aboutcom.html
ADPOPUP http://(www*.|)found404.com/affiliate*/pc404.html?**
ADPOPUP http://affiliate.cfdebt.com/banners/popupwin.asp?**
ADPOPUP http://**/hidden_popup.htm
ADPOPUP http://direct.ninemsn.com.au/**[Mm][Ee][Tt][Hh][Oo][Dd]=[Pp][Oo][Pp][Uu][Pp]**
# German for "ad"
COUNTER http://**/werbung/ziAdCount?**
PASS http://(www*.|)kodi.de/werbung/**
# ad: de:werbung,anzeige da:reklame no:annonser es:reklaam
AD http://**/(anzeige|werbung|WERBUNG|annonser|reklame|reklaam)/**.(gif|jpg)
AD http://*.de/images/wrb/**
# several patterns from Sergey Smirnov
AD http://www.hotlog.ru/buttons/*.gif
AD http://217.73.192.65/top100/banner*.gif
AD http://reklama.utro.ru/images/**
AD http://reklama.utro.ru/bb.cgi?*
AD http://images.directtrack.com/**.gif
AD http://(www*.|)keralanext.com/image/**.gif
AD http://adv.aport.ru/scripts/adv.dll?*
ADHTML http://(www*.|)netzagent.com/freetv/ad.htm
ADHTML http://*/hserver/**
ADHTML http://bannervip.web1000.com/web1000/[ab].asp
ADHTML http://**.adbutler.*/view.php?**inv=if**
ADHTML http://imgserv.adbutler.*/ieservad?**
ADHTML http://imgserv.adbutler.*/adserve/**type=iframe**
ADHTML http://channels.real.com/getlatest.glh?**
WEBBUG http://tracking.starmedia.com/track.gif**
WEBBUG http://c.ninemsn.com.au/c.gif?**
ADJS http://ds.starmedia.com/jserver/**
ADJS http://(www*.|)real.com/scripts/popunder2_.js
PASS http://(www*.|)smh.com.au/animations/bn.gif
PASS http://(www*.|)3dpulpit.com/animations/*.gif
PASS http://(www*.|)smh.com.au/animations/*.gif
AD http://*/animations/*.gif
AD http://imgserv.adbutler.com/imgserve.ibs?**
AD http://**/ani.gif
AD http://**/anim.gif
AD http://**/gifanim*.gif
AD http://adfarm.mediaplex.com/ad/bn/**
AD http://(www*.|)date.com/GetImage.do?**
AD http://img*.mediaplex.com/**.gif
AD https://img*.mediaplex.com/**.gif
AD http://www.104.ch/bn/*.jpg
AD http://*/img/clients/bn*.gif
AD http://*/client/button**.gif
AD http://*.mediaplex.com/ads/**
AD http://*.mediaplex.com/ad/bn/**
AD http://**/ban/ani[0-9]*.gif
AD http://(www*.|)nmnews.net/images/ani**.gif
AD http://(www*.|)fxsound.com/grfx/dfx_animated.gif
AD http://*/animeu/*.gif
ADJS http://imgserv.adbutler.com/jad?**
ADJS http://*.cybereps.com:8880/jserver**
ADJS http://216.148.128.89/jserver/**
ADJS http://home.netscape.com/h.js
ADJS http://*.usercash.com/**.js
ADHTML http://*.usercash.com/*.php**
ADHTML http://www.megaupload.com/adbrite.php?**
ADPOPUP http://**/ads/popup.shtml
ADPOPUP http://*.billiger-telefonieren.de/popup/*
ADPOPUP http://businessfactory.delphi.com/click.asp?**
ADPOPUP http://(www*.|)avault.com/ads/**
ADPOPUP http://*.doubleclick.net/ad**popup**
ADPOPUP http://ads.freecity.de/popup**
ADPOPUP http://ads.i2as.ulimit.com/oasisi-i.php?**
ADPOPUP http://(www*.|)fortunecity.com/marketplace/
ADPOPUP http://**/**/reclama/disp_banner.php**
ADPOPUP http://**.tvmovie.de/static/popup/**
ADPOPUP http://**.tvtoday.de/**popup**
ADPOPUP http://**.2xt.de/**popup**
ADPOPUP http://click4cash.de/popup/**
ADPOPUP http://**.aax.de/weblet/Banner**
ADPOPUP http://adserv.spiegel.de/**/ads/**.html
ADPOPUP http://(www*.|)babylon-x.com/servlet/click**
ADPOPUP http://(www*.|)t50.com/extra2.html
ADPOPUP http://(www*.|)t50.com/cgi-bin/download2.cgi
ADPOPUP http://(www*.|)altrawarez.com/**
ADPOPUP http://(www*.|)icewarez.net/popup*.htm*
ADPOPUP http://(www*.|)mywarez.net/my_files/exit.php
ADPOPUP http://(www*.|)easywarez.com/newsecrets.html
ADPOPUP http://(www*.|)spaceports.com/cgi-bin/ad.cgi?*
ADPOPUP http://(home.|www.|)netscape.com/misc/snf/popup_*.html
ADPOPUP http://(home.|www.|)netscape.com/misc/popup.html?**
ADPOPUP http://bannervip.webjump.com/ads/web1000/pop-up.html
ADPOPUP http://*go2net.com/adpopup?**
ADPOPUP http://server*.hypermart.net/adpopup?**
ADPOPUP http://*.to/pop.asp?**
ADPOPUP http://*tantofaz.net/local/misc/points/popup.asp
ADPOPUP http://cvo.tsx.org/window.mml
ADPOPUP http://(|www).space.com/php/popup/promo/**.php
ADPOPUP http://**/popupad.php
ADPOPUP http://(www*.|)nwfusion.com/auddev/pop/*.html
ADPOPUP http://img-snv.mediaplex.com/ads/**/pop_under_source.htm
ADPOPUP http://**/ads/popups/**.html
ADPOPUP http://(www*.|)popupad.net/ats/switch.php
ADPOPUP http://**/Ads/Media/Rich/**.html
ADPOPUP http://*.freeze.com/**.asp?**
AD http://(www*.|)tutopia.com/images/model/**.(gif|jpg)
AD http://(www*.|)tutopia.com/images/arControl/*.jpg
AD http://(|www).space.com/promo/images_cj/**.jpg
AD http://(www*.|)smh.com.au/images/**promo*.(gif|jpg)
ADJS http://www.space.com/js/site_pops.js
PASS http://*.cnet.com/Ads/Media/Images/Buttons/*sas*
PASS http://*.cnet.com/Ads/Media/Images/Buttons/*pfc*
AD http://(www*.|)msnbc.com/site_elements/msn_shopping_nbc_snap.gif
PASS http://(www*.|)msnbc.com/ads/i/corners.gif
PASS http://(www*.|)msnbc.com/ads/i/grey.gif
PASS http://(www*.|)topjobs.com.au/ads/**.gif
PASS http://(www*.|)eonline.com/Ads/Includes/Images/search.back.gif
PASS http://(www*.|)zdnet.com/include/**
PASS http://(www*.|)norml.org/about/ads/NORML_*
PASS http://(www*.|)adobe.com/ads/**.gif
PASS http://(www*.|)apple.com/hardware/ads/**
PASS http://(www*.|)buyersport.com/**/ads/**.html*
PASS http://images.salon.com/src/ads/**_flashme*.html?**
PASS http://cache.ultramercial.com/ads/**.gif
ADSWF http://**/Ads/Media/Flash/**.swf**
PASS http://**apple.com/switch/ads/**
PASS http://tanopah.jo.free.fr/ADS/bloc**
ADJS http://c*.zedo.com/**jsc/**.js
ADHTML http://xads.zedo.com/ads*/a?**
ADHTML http://ccas.clearchannel.com/CCAS_tag.html?**
ADPOPUP http://c*.zedo.com/jsc/c1/ff2.html?**
WEBBUG http://c[0-9].zedo.com/*/0/0/0/blank.gif
ADSWF http://**/bannerfarm/**.swf
ADSWF http://adsys.townnews.com/*/creative/**.swf**
PASS http://ads.vnuemedia.com/ads/amusementbusiness/**
PASS http://(www*.|)acmehorses.com/media/ads/**
PASS http://(www*.|)emagen.com.au/Ads/**
PASS http://www.yamaha-motor.com.au/images/**
AD http://*ads.zedo.com/ads2/x?**
AD http://**/([Aa][Dd][Ss]|_ads|ad.s|ads2|adsart|ars-ads|bfarm|bannerfarm|liveads|adlinks|[Bb]anner*[Aa]ds)/**.([Gg][Ii][Ff]|[Jj][Pp][Gg])**
AD http://**/ads.(pl|cgi)?**
AD http://images.salon.com/src/bizwidget/travelocity/bali.gif
AD http://(www*.|)salon.com/Creatives/**.(jpg|gif)
AD http://(www*.|)realcastmedia.com/creatives/ml/*_[1-9]*x[1-9]*.gif
AD http://adsys.townnews.com/*/creative/**.jpg
AD http://ccas.clearchannel.com/cc-common/CCAS_media/**.(gif|jpg)
AD   http://view.iballs.*.avenuea.com/iballs/view/**/direct/**
AD   http://view.avenuea.com/view/**
AD   http://view.avenuea.com/avenuea/view/**
AD   http://image.*.avenuea.com/**/image.*.avenuea.com/Banners/**.gif
AD   http://a[0-9]*.akamai*.net/**/(promo|promos)/**.(gif|jpg)
AD   http://a[0-9]*.akamai*.net/**/www.dealtime.com/**affiliate/**.gif
AD   http://a[0-9]*.akamai*.net/**/imgsrc.*.avenuea.com/Banners/**.gif
AD   http://a[0-9]*.akamai*.net/**/image.*.avenuea.com/Banners/**.gif
AD   http://a[0-9]*.akamai*.net/**/www.salon.com/Creatives/**.gif
AD   http://a[0-9]*.akamai*.net/**/www.space.com/images/space_shop_badge.gif
AD   http://a[0-9]*.akamai*.net/**/www.space.com/**/sponsors/**.gif
AD   http://a[0-9]*.akamai*.net/**/www.namezero.com/images/*.gif
AD   http://a[0-9]*.akamai*.net/**/ad.caramail.com/pub/**
AD   http://a[0-9]*.akamai*.net/**/ad.adtraq.com/**
AD   http://a[0-9]*.akamai*.net/**/(ad(|image)(|s)|[Bb]anner(|ad)(|s))/**.gif
ADSWF http://a*.akamai*.net/**/*.shoshkeles.com/**.swf
ADPOPUP http://(www*.|)zeropaid.com/images/ads/**pop*.html
ADPOPUP http://adv*.eblocs.com/spyblocs/adv/**.html
PASS http://www.pers.mq.edu.au/ads/**
PASS http://nx1.salon.com/RealMedia/ads/click_lx.ads/www.salonmagazine.com/**.html/**
PASS http://cache.ultramercial.com/ads/**.html
ADHTML http://**/ads/**.html**
ADSWF http://**/ads/**.swf
WEBBUGJS http://a[0-9]*.g.akamai*.net/**/stats.hitbox.com/js/**.js
WEBBUG http://*.hitbox.com/HG**
WEBBUG http://hits.gureport.co.uk/HG**
ADJS http://*.akamai*.net/**/www.msnbc.com/m/js/flash.js
ADJS http://*.akamai*.net/**/www.msnbc.com/m/js/flash.vbs
PASS http://a[0-9]*.g.akamai*.net/arttoday.token/sites/clip-art/**.gif
PASS http://a[0-9]*.g.akamai*.net/**/bg*.gif
PASS http://a[0-9]*.g.akamai*.net/**/*.*.*/**.gif
PASS http://a[0-9]*.g.akamai*.net/**/*.com/**.gif
PASS http://a[0-9]*.g.akamai*.net/**/background*.gif
PASS http://a[0-9]*.g.akamai*.net/**/backtile*.gif
PASS http://a[0-9]*.g.akamai*.net/**/bg_*.gif
PASS http://a[0-9]*.g.akamai*.net/**/icon**.gif
PASS http://a[0-9]*.g.akamai*.net/**/logos/**.gif
PASS http://a[0-9]*.g.akamai*.net/**/header**.gif
PASS http://a[0-9]*.g.akamai*.net/**/nav**.gif
PASS http://a[0-9]*.g.akamai*.net/**/spacer*.gif
PASS http://a[0-9]*.g.akamai*.net/**/rules/*.gif
PASS http://a[0-9]*.g.akamai*.net/**/dotclear*.gif
PASS http://a[0-9]*.g.akamai*.net/**/bg*.gif
AD   http://a[0-9]*.g.akamai*.net/**.gif
PASS http://(www*.|)csiro.au/promos/**.gif
PASS http://(www*.|)smh.com.au/media/promo/iconsm.gif
PASS http://(www*.|)afl.com.au/lib/images/promos/*.gif
PASS http://pics.ebay.com/aw/pics/**/buyItNow_*x*.gif
PASS http://(www*.|)redhat.com/img/*promo*.gif
PASS http://(www*.|)*sony.com/**promo**.gif
PASS http://*.dell.com/images/**
##AD http://**/*promo[0-9]*.(gif|jpg)
##AD http://**/[Pp]romo(s|)/**.(gif|jpg)
AD http://images.getrelevant.com/**
AD http://icache.getrelevant.com/**
AD http://*.getrelevant.com/**.gif**
AD http://(www*.|)airgunstore.com/AGS*.GIF
AD http://adgraphics.theonion.com/**.(gif|jpg)
AD http://203.147.223.47/retro_au/**.gif
AD http://images.yahoo.com/promotions/*/*.gif
AD http://rd.yahoo.com/**http://store.yahoo.com/cgi-bin/clink?ydomains+merchant-ad**
AD http://au.java.yahoo.com/java/*/abn*
ADHTML http://red.namezero.com/strip2/strip.jhtml?**
PASS http://(www*.|)direct.bigpond.com/images/banner/*.gif
PASS http://(www*.|)cai.com/banner/*.gif
PASS http://(www*.|)google.com/adv/*.html
PASS http://images.google.(co.*|com|com.*)/images?**
PASS http://(www*.|)advantedgeonline.com.au/adv/**
PASS http://(www*.|)fuzzyfur.net/DSOS/adv/**
PASS http://**/banner/site/menu/**.jpg
PASS http://*cyberjaya-msc.com/images/banner/**
PASS http://(www*.|)stgeorge.com.au/resources/stg/images/banner/**.gif
PASS http://(www*.|)indoorclimbing.com.au/images/banner/**
PASS http://(www*.|)ap.dell.com/ap/images/banner/*.(jpg|gif)
PASS http://(www*.|)info.gov.hk/banner/**
PASS http://(www*.|)saintcorporation.com/images/banner/**
PASS http://(www*.|)sueddeutsche.de/imperia/md/images/banner/**
PASS http://nosoftwarepatents.com/**
PASS http://(www*.|)tmanime.com/tmanime/wallpapers/banner**
PASS http://(www*.|)axiossystems.com/images/banner/**
PASS http://zzz.com.ru/banners/**
PASS http://*.openoffice.org/banners/**
PASS http://newsimg.bbc.co.uk/**.(gif|jpg)
PASS http://(www*.|)supergo.com/images/banners/**
PASS http://(www*.|)sabregen.co.za/[Pp]ict_banner/**
PASS http://(www*.|)bridgestone.com.au/common/commonimages/banners/**
PASS http://(www*.|)gamesmarket.com.au/images/banners/**
PASS http://mckague.com/photographs/special/banners/**
PASS http://(www*.|)pulitzer.org/**
PASS http://(www*.|)pch.net/images/sponsors/*.gif
PASS http://www.ati.com/banners/images/**
PASS http://(www*.|)epson.*/banners/**.(gif|jpg)
PASS http://discussion.ottawabusinessjournal.com/pubfiles/obj/banners/**.jpg
PASS http://(www*.|)racv.com.au/images/augbanners/hmpage_top_*_top_*.jpg
PASS http://(www*.|)wasabisystems.com/images/banner*/**
PASS http://(www*.|)ow.com.au/images/Left_banners/**
PASS http://(www*.|)palmone.com/asia/images/entry/banner/**
PASS http://partner.scribona.no/upload/banner/**
PASS http://(www*.|)abc.net.au/news/img/*banner*.gif
PASS http://advocacy.daemonnews.org/**
PASS http://dvdstation.com.au/images/adverts/**
PASS http://shop.private.com/shop/media/**
PASS http://(www.|)seek.com.au/**
PASS http://(www*.|)bunnings.com.au/layouts/cust_bunnings/adverts/**
PASS http://www.sigpet.com.au/assets/**
PASS http://www.fredart.com/fredart/banners/**
PASS http://www.stuff.co.nz/stuff/masthead/banner/**
PASS http://ez.no/var/ezno/storage/images/images/**
PASS http://(www.|)epa.ie/**
PASS http://(www*.|)alternate.nl/pix/misc/bgtreebanner.gif
PASS http://(www*.|)genright.com/images/**
PASS http://cisco.netacad.net/**
PASS http://www.edubase.com.my/**
PASS http://upload.wikimedia.org/wikipedia/**
PASS http://www.avico.com.au/_lib/images/**
PASS http://www.insuremyride.com.au/images/**
PASS http://(www*.|)trading*post.com.au/ContentManagement/**
AD http://(www*.|)planet3dnow.de/images/zusatz/*.gif
AD http://(www*.|)sueddeutsche.de/sz/misc/marktplatz/**.gif
AD http://**/([Aa]dvert|ADVERT|advbn|adgifs|blipverts|showsell|*[Bb]anner|bann|bannerlink|linkbacks|liveads|adproof|SiteSponsor|spon)**.([Gg][Ii][Ff]|[Jj][Pp][Gg]|[Pp][Nn][Gg])*
AD http://*/advert/bin/image?**
AD http://*/Ad=*/**
AD http://**/sponsorad.gif
AD http://**/bin/statdeploy?*
AD http://**/images/ads_new/*.gif
AD http://**/images/ads-side*/ad-*.gif
AD http://**/images/sponsor.gif
AD http://*.the-park.com/images/*banner*.gif
AD http://*/*/ba_ad/*.gif
AD http://*/cgi-bin**/banner.cgi**
PASS http://(www*.|)uq.edu.au/**banner**.gif
PASS http://(www*.|)mpce.mq.edu.au/images/**
PASS http://msdn.microsoft.com/msdn-online/shared/graphics/banners/*-banner.gif
PASS http://(www*.|)mozilla.org/**-banner.gif
AD http://**-banner.gif
PASS http://(www*.|)amazon.com/g/v9/icons/*-banner-*.gif
AD http://**/*-banner-*.gif
## PASS http://(www*.|)ztree.com/assets/images/**
## PASS http://(www*.|)doschdesign.de/assets/images/**
## PASS http://(www*.|)stallion.com.au/assets/images/**
## PASS http://209.1.197.35/assets/images/**
## AD http://*/assets/images/*.jpg
ADJAVA http://(www*.|)ntexplorer.com/DynamicBanner.class
AD http://(www*.|)matrox.com/mga/media/int_banners/*.gif
PASS http://(www*.|)matrox.com/*/banners/**
PASS http://(www*.|)research.att.com/banners/*.gif
PASS http://(www*.|)javasoft.com/images/banners/*.gif
PASS http://(www*.|)lancrypto.com/images/banners/*.gif
PASS http://(www*.|)agcrc.csiro.au/img/banners/*.gif
PASS http://(www*.|)Europe.DataFellows.com/images/banners/*.gif
PASS http://*/images/banners/anonline.jpg
PASS http://(www*.|)corel.com/graphics/banners/**
PASS http://(www*.|)verifone.com/images/banners/*.gif
PASS http://java.sun.com/images/banners/*.gif
PASS http://(www*.|)tandberg.com/images/banners/*.gif
PASS http://virtuallythere.com/cgi-bin/mqcustomconnect?**
PASS http://(www*.|)parentingplace.com/images/banners/*.gif
PASS http://**/banners/**spacer.gif
PASS http://image.weather.com/pics/banners/banner_general.jpg
AD http://image.weather.com/creatives/**.gif
AD http://**/webbanners/*.gif
PASS http://**/banners/back.gif
PASS http://**/banners/bgpic.gif
PASS http://(www*.|)energy.gov/images/banners/*.gif
PASS http://(www*.|)blackwell-science.com/**/banners/**
WEBBUG http://*.yimg.com/**/i/**.jpg?**sig=**
PASS http://*.yimg.com/**/(bin|auc)/**.gif
PASS http://*.yimg.com**/(i|xp|cx)/**.(gif|jpg)
ADSWF http://*.yimg.com/**/*[0-9]x[1-9]*.swf**
AD http://*.yimg.com**/(a|adv|ba2)/**.(gif|jpg)
AD http://**/banners/*.banner
AD http://**/Banners/Images/**
AD http://**/bnrs*/*.gif
AD http://**/bn/**.gif
AD http://**/bnr-*.gif
AD http://**/(bann|banrgifs|ad-(banner|images|bin)|sponsor|((pr|s|other|)banner(s|sp|))|baners|Banner(s|)|BANNER(S|)|banniere|baneri)*/**.(gif|GIF|jpg|JPG)**
AD http://**/adserve?*;image;**
AD http://(www*.|)eads.com/adserve/adserve.dll/banner?**
AD http://images.blogads.com/**/thumb?**
AD http://ads*.intelliads.com/html-bin/adselect-**
AD http://ads*.intelliads.com/images/**.gif
AD http://ads*.intelliads.com/html-bin/adselect300.asp?obnum=*
ADSWF http://**/ad-bin/*.swf
ADSWF http://**/bannieres/**.swf**
ADSWF http://reiter.typepad.com/*/banniere.swf
PASS http://**/SmartBanner/**single_pixel.gif
PASS http://**/SmartBanner/**1ptrans.gif
PASS http://**/SmartBanner/chtml/*/page/*.html/**
ADJS http://**/SmartBanner/jsad**
ADJS http://icc.intellisrv.net/adopt.jsp?**
ADJS http://**/DynamicJSAd?**
ADJS http://(www*.|)budsinc.com/pubcodes/banner.js
ADJS http://show.budsinc.com/jserver/**
ADHTML http://(www*.|)advertwizard.com/plugin/plugin.phtml?**
ADHTML http://**/SmartBanner/htmlad?**
PASS http://wyse.com.au/graphics/ban/**
AD http://(www*.|)advertwizard.com/banner_display/show_banner.phtml?**
AD http://**/SmartBanner/**.gif
AD http://**/SmartBanner/nph-graphic**
AD http://**/SmartBanner/nph-defgraphic**
AD http://**/maxcash/*.jpg
AD http://**/cgi-bin/cash4views.pl?banner=**
AD http://**/adstream.cgi/**
AD http://**/*adbans*.gif
AD http://**/roto/rotoad*.jpg
AD http://**/roto/**ban*.jpg
AD http://**/sponsor/banner*.jpg
AD http://**/sponsor/*.gif
AD http://**/(banners|banniere)/**.jpg
AD http://**/ban/*.gif
AD http://**/ban/*.jpg
ADHTML http://ad.preferences.com/iframe;**
ADHTML http://ad.preferences.com/oframe;**
ADJS http://ad.preferences.com/oscript;**
ADJS http://ad.preferences.com/jscript**
AD http://gm.preferences.com/image;**
AD http://ad.preferences.com/image;**
AD http://ad.preferences.com/**.gif
AD http://media.preferences.com/**.gif
AD http://privacyproxy.nytimes.com/RealMedia/PP/IMP/**
AD http://(www*.|)reftracker.de/buttons/button*.gif
AD http://tracker.advancewebhosting.com/images/*.gif
AD http://tracker.advancewebhosting.com/image.phtml?**
AD http://199.172.144.25/*.gif
AD http://207.168.8.47/*.gif
AD http://207.178.253.240/banners/**.gif
AD http://ad.blm.net/image?**
AD http://(www*.|)sun.com/sunworldonline/swol-ad/**
AD http://207.87.27.37/news/an_*.gif
AD http://*/graphics/ad-banner/*.gif
AD http://*times*/*.*x*.gif?**
AD http://*times*/TT*.*x*.gif?**
AD http://199.78.52.10/*web_ani/*.gif
AD http://199.78.52.10/web_gif/*.gif
AD http://199.78.52.10/~web_ani/*.gif
AD http://**/*_ad_*x*.gif
AD http://**/[Aa]d[Bb]anner**.(gif|jpg)
AD http://**/image.avenuea.com/Banners/**
AD http://**/Ads/Media/Images/**.gif**
AD http://**/Ads/Media/Images/**.jpg**
AD http://*/bfast/serve?**
PASS http://ads.vnuemedia.com/image.ng/Site=amusementbusiness&**
AD http://*/image.ng;**
AD http://*/image.ng/**
AD http://ak.maxserving.com/images/**.gif
ADPOPUP http://*.maxserving.com/adclick/**
ADPOPUP http://**/phpAdsNew/adclick.php?**
ADJS http://*.maxserving.com/gen.js?**
PASS http://*.djnr.com/**/buttons/*blink.gif
PASS http://(www*.|)dpreview.com/reviews/*/Images/Captures/*blink.gif
PASS http://**/emoticons/blink.gif
AD http://**blink.gif
AD http://**/baner*.gif
AD http://register.ero.ru/pc/*.gif
AD http://xb.xoom.com/images/*.gif
AD http://(www*.|)addfreestats.com/cgi-bin/connect.cgi?**
AD http://admedia.xoom.com/Banners/**.gif
AD http://members.xoom.com/**/anixoom.gif
AD http://a*.interclick.com/**.gif
PASS http://ads.bmais.net/*.ng**
PASS http://ads.adsag.com/*.ng**
ADHTML http://a*.interclick.com/getJs.aspx**
ADHTML http://ilinks.industrybrains.com/showct?**
ADHTML http://**/advertpro/banners.pl?**
ADHTML http://**/advertpro/servlet/file?**
ADHTML http://**/advertpro/servlet/view/banner/html/**
ADHTML http://(www*.|).sys-con.com/(banner|ads)/**.cfm
ADHTML http://banners.sys-con.com/IFrames/*.php
ADHTML http://xb.xoom.*/xb*.odt
ADHTML http://adforce*/?adiframe**
ADHTML http://www2.efront.com/adserve.iframe/**
ADHTML http://(www*.|)macaddict.com/ad_frame/
ADHTML http://(www*.|)itworld.com/ad_*.htm**
ADHTML http://**/html.ng/**
ADJS http://banners.sys-con.com/phpAds**.js
WEBBUG http://(www*.|)powerweb.net/*/tracker.cfm/**.gif
WEBBUG http://*.2o7.net/b/ss/**?**
WEBBUG http://dw.com.com/clear/**.gif?**
WEBBUG http://**/AdsManager/adlog.php?**
WEBBUG http://log.go.com/log?**
WEBBUG http://*netshelter.*/serve.cgi?**
WEBBUG http://195.25.89.17/**_v?**
WEBBUG http://195.25.89.18/**_p?**
WEBBUG http://stat.cybermonitor.com/**_p?**
WEBBUG http://**/audit/track.cgi?**
WEBBUG http://*.netscape.com/c.cgi?**
WEBBUG http://*.sextracker.com/clit?**
WEBBUG http://register.ero.ru/g/ch.gif?**
WEBBUG http://register.ero.ru/g/cw.gif?**
WEBBUG http://*/0.gif?tag=**
WEBBUG http://*.microsoft.com/trans_pixel.asp?**
WEBBUG http://(www*.|)planet3dnow.de/cgi-bin/picount/count.pl
WEBBUG http://refcounter.sexhound.com/?id=**
WEBBUG http://images.sexhound.com/NewSite/spacer.gif
WEBBUG http://y1.extreme-dm.com/z/?tag=**
WEBBUG http://counter*.hitslink.com/stats-ns.asp?**
WEBBUG http://*.burstnet.com/*/blank.gif?**
PASS http://(www*.|)info.gov.hk/cgi-bin/forms/count.cgi?**
PASS http://s1.thecounter.com/**
COUNTERJS http://(www*.|)addfreestats.com/cgi-bin/countnow.cgi?**
COUNTERHTML http://count0r.customize.org/count0r.php?**
COUNTERHTML http://okcounter.com/okcounter.html?id=**
AD http://counter.yadro.ru/logo?**
COUNTER http://counter.yadro.ru/hit?**
COUNTER http://e.ofuda.cc/disp/[0-9]**.gif
COUNTER http://mom.freelogs.com/counter/index.php?**
COUNTER http://top.novgorod.ru:81/**
COUNTER http://bar.hit-counter.udub.com/counter/index.php?**
COUNTER http://okcounter.com/okcounter.html?id=**
COUNTER http://a.xcounters.com/?*
COUNTER http://count.2ch.net/ct.php/*
COUNTER http://counters.freewebs.com/Members/Counters/counter.jsp?**
COUNTER http://counter.animehost.de/showhits.php?*&st=img*
COUNTER http://c*.gostats.com/gogi/count.pl?**
COUNTER http://webcounter.goweb.de/**
COUNTER http://webcounter.goweb.de:90/**
COUNTER http://sys.bool.co.il/cgi-bin/bu_counter.cgi?**
COUNTER http://(www*.|)counter4u.de/cgi-bin/counter4u/img_counter_fast.pl?**
COUNTER http://counter.mycomputer.com/c.count?**
COUNTER http://**/count?ID=**
COUNTER http://**/cgi/count?**
COUNTER http://(www*.|)geocities.com/cgi-bin/counter**
COUNTER http://tools.geocities.**/@geocounter
COUNTER http://**/counter.cgi?**
COUNTER http://**/cgi-bin/counter/odometer.pl?**
COUNTER http://*/hit.counter?**
COUNTER http://*/nfcounter?**
COUNTER http://*.thecounter.com/id=**
COUNTER http://**/fpcount.exe**
COUNTER http://**/Count.exe?**
COUNTER http://*/cgi-bin/counter?**
COUNTER http://*/cgi-bin/count?**
COUNTER http://**/tb2count.fcgi**
COUNTER http://**/pqcount.fcgi**
COUNTER http://**/count.cgi?**
COUNTER http://**/Count.cgi**
COUNTER http://*/cgi-bin/SmartCounter?**
COUNTER http://*.xoom.*/*/counter.gif**
COUNTER http://*/counter?**
COUNTER http://counter.*/?**
COUNTER http://www[0-9].pagecount.com/*/counter.gif?**
COUNTER http://work.goen.ne.jp/counter*/fs/count?**
COUNTER http://top.list.ru/counter?**
COUNTER http://counter.rambler.ru/top100.cnt?**
COUNTER http://**/top100/nph-top100?A=**
COUNTER http://www[0-9].pagecount.com/images/xoom_counter_logo_basic.gif
COUNTER http://counter[0-9]*.com/c*/id/**
COUNTER http://c[0-9].*counter.com/c*/id/**
COUNTER http://hardware.pagecount.com/hardware/counter.gif?**
COUNTER http://fastcounter.linkexchange.com/digits?**
COUNTER http://fastcounter.bcentral.com/digits?**
COUNTER http://fastcounter.linkexchange.com/fastcounter?**
COUNTER http://fastcounter.bcentral.com/fastcounter?**
COUNTER http://**/counter.gif?**
COUNTER http://*.digits.com/wc/**
COUNTER http://*/cgi-bin/wc?**
COUNTER http://*/cgi-bin/wc/**
COUNTER http://counter[0-9].*/c**
COUNTER http://*/counters/*.gif
COUNTER http://*counter.com/counter/**
COUNTER http://fakecounter.com/[0-9]*.gif
COUNTER http://fakecounter.com/home.page?**
COUNTER http://*/cgi-bin/newcount?**
COUNTER http://*/cgi-bin/c2countit/c2countit.cgi?*
COUNTER http://*/cgi-bin/imagecounter?**
COUNTER http://**/counter.exe?**
COUNTER http://**/counter.gif
COUNTER http://*/cgi-bin/hits/hitmat.cgi?**
COUNTER http://**/Geo-counter.gif?**
COUNTER http://book.pagecount.com/book/counter.gif?*
COUNTER http://**/wwwcount.cgi?**
COUNTER http://(www*.|)mirc.to/public/counter?*
COUNTER http://(www*.|)whatsis.com/whatsis-bin/swc?**
COUNTER http://bilbo.counted.com/[0-9]**
COUNTER http://(www*.|)yandex.ru/cycounter?**
COUNTER http://u[0-9]*.spylog.com/cnt?**
COUNTER http://(www*.|)compteur.com/cgi-bin/compteur.cpt?**
COUNTER http://(www*.|)imingo.com/services/compteur/icptgr.php?**
COUNTER http://(www*.|)perl-gratuit.com/cgi-bin/count/compteur?**
COUNTER http://(www*.|)addfreecounter.com/cgi-bin/cptconnect.cgi?**
COUNTER http://**/HitCounter.dll?**
COUNTER http://210.239.47.44/~inosuke/count/dream.cgi?id=*
COUNTER http://(www*.|)deadline.demon.co.uk/cgi-bin/count
COUNTER http://(www*.|)webd.org/fr/services/compteur/counter.asp?id=**
COUNTER http://**/nph-count(|.cgi)?**
COUNTER http://*.hypercount.com*/**/?**
COUNTER http://loga.hit-parade.com/logo*.gif**
COUNTER http://log*.xiti.com/hit.xiti?**
AD http://img.hypercount.com/*.jpg
AD http://escati.linkopp.net/logos/counter2000.gif
WEBBUG http://cs.sexcounter.com/cs/?**
COUNTERJS http://*.sitemeter.com/js/counter.js?**
COUNTER http://*.sitemeter.com/meter.asp?**
COUNTER http://escati.linkopp.net/cgi-bin/counter2000.cgi?**
COUNTER http://(www*.|)peakpeak.com/cgi-bin/counter/counter.pl?**
COUNTER http://portal.plocman.pl/top100/cgi-bin/stat.cgi?**
COUNTER http://**/hitometer.cgi
COUNTER http://gratiscounter.de/hit.cgi?**
COUNTER http://statse.webtrendslive.com/**button*.asp**
COUNTER http://counter*.sextracker.com/**
COUNTER http://*.sextracker.com/stx/send/**
COUNTER http://count.paycounter.com/?fn=0**
COUNTER http://web.ukonline.co.uk/public-cgi/wcount/**
COUNTER http://counter.hitslink.com/counter.asp?**
COUNTER http://counter.hitslink.com/counterupdate.asp?**
COUNTER http://*/cgi-bin/cnt.cgi?**
COUNTER http://counters.honesty.com/cgi-bin/honesty-counter.cgi?**
COUNTER http://**/counter.img?**
COUNTER http://*/counter.php?**
COUNTER http://*/counter.php3?**
COUNTER http://(www*.|)apcupsd.org/cgi-bin/apcupsdCount.cgi?**
COUNTER http://c.sexcounter.com/counter.html?**
COUNTER http://c.sexcounter.com/cnt.html?**
COUNTER http://(www*.|)topwebmaster.de/modul-center.html?modul=counter&**
COUNTER http://(www*.|)alphalink.com.au/cgi-bin/Count2.cgi?**
COUNTER http://(www*.|)btinternet.com/cgi-bin/counter/**
COUNTER http://(www*.|)stomped.com/counter-bin/images/icompz-banner.gif?**
COUNTER http://((www*.|)web-chart.de|151.189.43.51)/cgi-bin/chart/webchart.cgi?**
COUNTER http://hit*.hotlog.ru/cgi-bin/hotlog/count?**
COUNTER http://(www*.|)top-chart.de/cgi/topchart2.cgi?**
COUNTER http://(www*.|)hitlogger.com/cgi-bin/nstats-bin/do/stats.cgi?**
AD http://(www*.|)hitlogger.com/nstats-web/banner.gif
COUNTERJS http://(www*.|)top-chart.de/code/code_tc4.js
COUNTERJS http://((www*.|)web-chart.de|151.189.43.51)/counter.js
PASS http://ads.vnuemedia.com/js.ng/Site=amusementbusiness&**
ADJS http://adforce*/?addyn**
ADJS http://(www*.|)efront.com/adserve.jscript/**
ADJS http://(www*.|)geocities.com/js_source/pu5geo.js
ADJS http://(www*.|)geocities.com/js_source/ygNSLib9.js?*
ADJS http://**/js.ng/**
ADJS http://adproxy.whowhere.com/ad.cgi?*response_type=JS
ADJS http://(www*.|)teknosurf.com/text/*.js
ADJS http://layer-ads.de/**
ADJS http://*.intellitxt.com/intellitxt/front.asp?**
ADJS http://vpdc.ru4.com/aw.asp?**
# ADSWF http://vpdc.ru4.com/SWF/Window/AffiliateWindow/**.swf?**
ADSWF http://http.edge.vru4.com/smartserve/**.swf
AD http://*.ru4.com/content/images/**.(gif|jpg)
AD http://*.ru4.com/images/**.(gif|jpg)
ADHTML http://*.ru4.com/smartserve/ad?**
ADHTML http://(www*.|)danworld.net/cgi-pub/centralad/ssirand.cgi/**
ADHTML http://display.adhearus.com/display_ad.php?**
ADHTML http://*.pricegrabber.com/search_getprod_ad.php/**
ADHTML http://layer-ads.de/ad.php?**
ADHTML http://layer-ads.de/refer.php?**
ADHTML http://cp-co.kir.jp/banner/*/
AD http://dist.belnk.com/4/placement/**.jpg
ADJS http://webpdp.gator.com/4/placement/[0-9]*/
AD http://webpdp.gator.com/**.gif
AD http://**/centralad/**getimage**
AD http://(www*.|)edacafe.com/common/getimage.php?**
PASS http://home.netscape.com/affiliate/images/jump_*.gif
PASS http://(www*.|)ofoto.com/affiliates/**
PASS http://(www*.|)ebags-backpacks.com/affiliate/**
AD http://affiliate.plugnpay.com/*.gif
AD http://static.admaximize.com/gifs/**
AD http://adforce*.imgis.com/**
AD http://adforce*/?adserv**
AD http://(www*.|)efront.com/adserve.image/**
AD http://imageserv*.imgis.com/**
AD http://fp.cache.imgis.com/images/Ad*
AD http://(www*.|)sfgate.com/place-ads/**.gif
AD http://(www*.|)ad-up.com/cgi-bin/view.cgi/**
AD http://bizad.nikkeibp.co.jp/image/**.gif
AD http://(www*.|)nikkeibp.asiabiztech.com/image/Ad_*.gif
AD http://ads1.zdnet.com/adverts/**
AD http://*currents.net/ccigraph/vendors/*.gif
AD http://(www*.|)dgmaustralia.com/merchants/**.gif
AD http://headline.gamespot.com/rotations/graphics/*.gif
AD http://**/~web_ani/*.gif
AD http://static.wired.com/advertising/**
AD http://static.wired.com/advertising/*.gif
AD http://static.wired.com/news/images/button_ads_*.gif
AD http://(www*.|)motorcycle.com/mo/mcads/**.gif
AD http://(www*.|)motorcycle.com/mo/mcads/**.jpg
AD http://(www*.|)motorcyclenews.com/global_graphics/bikemart.gif
AD http://(www*.|)motorcyclenews.com/global_graphics/duke_video.gif
AD http://(www*.|)motorcyclenews.com/global_graphics/on_sale_arrows.gif
AD http://(www*.|)motorcyclenews.com/global_graphics/fantasy_road_race.gif
AD http://(www*.|)motorcyclenews.com/global_graphics/sidelinks/mandp_button.gif
AD http://(www*.|)csmonitor.com/advertising/*.gif
AD http://(www*.|)currents.net/ccigraph/vendors/*.gif
AD http://(www*.|)dvdresource.com/images/*banner*.gif
AD http://(www*.|)ednprodmag.com/images/prbanner/*.GIF
AD http://(www*.|)latimes.com/ADS/*.gif
AD http://(www*.|)mcafee.com/banners/*.gif
AD http://(www*.|)dvdtown.com/gfx/banners/*.gif
AD http://(www*.|)askdigitalman.com/gfx/*banner.gif
AD http://banner.orb.net/ORBitBanner/*/banner.gif?**.10.21.22.15.10
AD http://(www*.|)mediacity.com.sg/cgi-bin/adopt/place_ad_cookie?**
AD http://(www*.|)ohio.com/advertising/*.gif
AD http://image.pathfinder.com/shared/images/ad/*.gif
AD http://image.pathfinder.com/shared/images/marketing/*.gif
AD http://a.mktw.net/MarketWatch/**.gif
AD http://images.people2people.com/images/marketing/**.gif
AD http://marketing.nyi.net/**.gif
AD http://image.pathfinder.com/sponsors*/**.gif
AD http://(www*.|)smartclicks.com:81/**/smartimg
AD http://(www*.|)sofcom.com.au/cgi-bin/Banner/Show.cgi?function=pic**
AD http://(www*.|)submit-it.com/images/animbanner_*.gif
PASS http://(www*.|)storedj.com.au/images/anim*.gif
PASS http://sfx-images.mozilla.org/affiliates/**
AD http://**/anim[0-9].gif
AD http://**/anim[0-9][0-9].gif
AD http://**/animban*.gif
AD http://**/aniban*.gif
AD http://**/anim_btn*.gif
AD http://(www*.|)wallpapervault.com/btn*.gif
AD http://(www*.|)thestar.com/**/ad/**.gif
AD http://(www*.|)thestar.com/thestar/images7/*_ani.gif
AD http://(www*.|)tradingpost.com.au/gfx/advt/*.gif
AD http://(www*.|)uexpress.com/comics_channel/images/IE4_ANIMATED.gif
AD http://(www*.|)superstats.com/images/ss.gif
AD http://(www*.|)cashcount.com/cgi-bin/hits/log.cgi?**
AD http://(www*.|)geocities.com/MemberBanners/live/*.gif
AD http://pic.geocities.com/images/mbe/mbe*.gif
AD http://pagesthatpay.geocities.com/thumbnails/*.gif
AD http://(www*.|)geocities.com/sponsor/*.gif
AD http://(www*.|)geocities.com/cgi-bin-local/GeoAD?**
AD http://(www*.|)village.com.au:1971/*?**
AD http://(www*.|)upside.com:8001/*?**
AD http://(www*.|)phillynews.com/advts/images/*.gif
AD http://ad.gamespot.com/rotations/graphics/*.gif
AD http://ad.gamespot.com/rotations/graphics/*.gif
AD http://(www*.|)thewebsubmitter.com/wsbanner3
AD http://(www*.|)topcenter.com/*.gif
AD http://images.yahoo.com/a/eg/egghead/*.gif
AD http://(www*.|)sofcom.com.au/cgi-bin/banserv/s?**
AD http://(www*.|)excite.com/img/art4/home/promo/*.gif
AD http://**/getimage.cgi**
AD http://**/getimage.exe/*?**
AD http://*/banmat/*.jpg
AD http://**/[Aa]ffiliates/**.gif
AD http://**/(affiliate|affilies)/**.gif
AD http://images.ifriends.net/affiliate_programs/**.GIF
AD http://www5.zdnet.com/graphics/pcast.gif
AD http://(www*.|)zdnet.com/zdtv/graphics/library/*.gif
AD http://208.156.39.144:80/*?
AD http://img.getstats.com/?**
AD http://**/ads/ad.pl?**
AD http://(www*.|)LinkAustralia.com/cgi-localbin/ads.pl?**
AD http://bs7.gsanet.com/gsa_bs/gsa_bs.cmdl?**
AD http://(www*.|)sun.com/sunworldonline/swol-ad/**
AD http://(www*.|)digitaleyes.net/images/Banner*.gif
AD http://banner.rootsweb.com/cgi-bin/newbanner.cgi?**
AD http://bannerbrokers.com/cgi-bin/banner.cgi?**
AD http://bannermaster.geektech.com/**.gif
AD http://206.132.234.218/**.gif
AD http://(www*.|)activeie.com/images/ukchat2.jpg
AD http://(www*.|)chipcom.net/*ad.gif
AD http://(www*.|)elibrary.com/advertising/*/*.gif
AD http://www3.switchboard.com/home/disspbox.gif
AD http://www3.switchboard.com/images/disbar.gif
AD http://www3.switchboard.com/images/ebay54.gif
AD http://www3.switchboard.com/images/coupon.gif
AD http://(www*.|)gottsoftware.com/CGI/mln_nonssi.pl?**
AD http://(www*.|)speed-links.com/cgi-local/adssl.pl?**
AD http://(www*.|)hostamerica.com/images/ha_banner*.gif
AD http://echo.znet.de/banner/factumbanner.gif
AD http://(www*.|)bannerweb.com/click/**
AD http://(www*.|)vrserv.com/clicktrade/*.gif
AD http://(www*.|)ml.org/gfx/spon/*/*.gif
AD http://(www*.|)twice.com/rvanim.gif
AD http://(www*.|)twice.com/hbobanne.gif
AD http://(www*.|)abc.net.au/news/graphics/the_dial.gif
AD http://(www*.|)newscientist.com/houseads/*.gif
AD http://(www*.|)dvdresource.com/images/adventure1.gif
AD http://image1.narrative.com/internet/*.gif
AD http://(www*.|)slugburger.com/ThAlley/Graphics/banner*.gif
AD http://(www*.|)puretec.de/gifs/sieben1.gif
AD http://(www*.|)dansdata.com/images/*banner*.gif
AD http://(www*.|)dansdata.com/images/fo32.gif
AD http://www.dansdata.com/images/dotnet3.gif
AD http://dansdata.com/images/*banner.gif
AD http://(www*.|)dansdata.com/images/tsurf.GIF
AD http://(www*.|)dansdata.com/images/referral1.gif
AD http://(www*.|)dansdata.com/images/apple.gif
AD http://(www*.|)dansdata.com/images/sb1.gif
AD http://(www*.|)dansdata.com/images/cg_400.gif
AD http://(www*.|)mamma.com/feature*.gif
AD http://(www*.|)dvd.com/stories/splash_page/pic_*.gif
AD http://(www*.|)floridatoday.com/*/ad/*.gif
AD http://(www*.|)nypostonline.com/images/p6teaser/*.gif
AD http://(www*.|)eweek.com/dropdown/*.jpg
AD http://bs[0-9]*.gmx.net/[0-9]**
AD http://**/advertisers/*.gif
ADSWF http://**/advertise(|r(|s))/**.swf**
ADSWF http://temp.customize.org/*.swf
ADSWF http://(www*.|)gamespy.com/aspcommon/120x38/arcade_120x38.swf
ADSWF http://*.yimg.com**/(a|ads*)/**.swf**
ADSWF http://*.yimg.com**/a/**.swf**
ADSWF http://*extremetech.*/dropdown/**.swf?**
ADJS http://*extremetech.*/dropdown/**.js
ADJS http://www*.gmx.net/de/ad/*banner*.js
ADJS http://adimp.excite.co.jp/bservers/**
AD http://(www*.|)altavista.com/av/gifs/ie_horiz.gif
AD http://guide-p.infoseek.com/images/promo/*.gif
AD http://(www*.|)infoseek.com/rimage?**
AD http://infoseek.go.com/cimages?*Promo*
AD http://images.usatoday.com/shop/_images/**.gif
AD http://(www*.|)usatoday.com/marketpl/**.gif
AD http://(www*.|)usatoday.com/library/commerce/img/*.gif
AD http://(www*.|)usatoday.com/gen/wtg/img/*.gif
AD http://(www*.|)usatoday.com/20[0-9][0-9]/enterprise/*_468*.gif
WEBBUG http://images.usatoday.com/**/clear.gif**
WEBBUG http://images.clickability.com/**/spacer.gif**
WEBBUGJS http://www.usatoday.com/_common/_scripts/counter.js
ADPOPUP http://(www*.|)usatoday.com/advertising/orbitz/orbitz-window*.htm
ADPOPUP http://*actionsplash.com/PC1.asp?**
ADPOPUP http://*actionsplash.com/JR90.asp?**
ADPOPUP http://(www*.|)focalex.com/pops/popup_internet.emp?**
ADPOPUP http://jumpeu.altavista.com/popups/**
AD http://adaver1.altavista.yellowpages.com.au*/ad_image;**
AD http://(www*.|)yellowpages.com.au/yp/images/ll/*.gif
AD http://(www*.|)yellowpages.com.au/yp/images/yp_gettoit.gif
PASS http://linuxtoday.com/pics/lt.gif
PASS http://*.linuxtoday.com/pics/lt.gif
PASS http://linuxtoday.com/pics/lt.jpg
PASS http://linuxtoday.com/pics/new.jpg
PASS http://linuxtoday.com/pics/icom-linmicro.jpg
PASS http://linuxtoday.com/pics/logo-mini.gif
AD http://linuxtoday.com/pics/*.gif
AD http://linuxtoday.com/pics/*.jpg
AD http://linuxtoday.com/ltbs/pics/*.gif
AD http://linuxtoday.com/ltbs/pics/*.GIF
AD http://*.linuxtoday.com/pics/*.gif
AD http://(www*.|)linux-directory.com/button_88x31.gif
AD http://(www*.|)amasuperbike.com/image/ad_*.gif
AD http://(www*.|)amasuperbike.com/image/new/ad_*.gif
AD http://(www*.|)amasuperbike.com/r1.gif
AD http://(www*.|)amasuperbike.com/GSXR750.gif
AD http://(www*.|)amasuperbike.com/tbrc51.gif
AD http://(www*.|)amasuperbike.com/*banner*.gif
AD http://(www*.|)amasuperbike.com/dunlop.jpg
AD http://(www*.|)amasuperbike.com/parts.jpg
AD http://(www*.|)amasuperbike.com/agv2.gif
AD http://(www*.|)amasuperbike.com/muzzyanim.gif
AD http://(www*.|)amasuperbike.com/vr1000.gif
AD http://(www*.|)amasuperbike.com/hondaanim.gif
AD http://(www*.|)amasuperbike.com/image/vnh.gif
AD http://(www*.|)amasuperbike.com/super.gif
AD http://www*.burstnet.com/gifs/*X*.gif
AD http://(www*.|)flatoday.com/space/today/resume.gif
AD http://(www*.|)flatoday.com/**ad-*.gif
AD http://(www*.|)flatoday.com/space/today/pr-*.gif
AD http://(www*.|)flatoday.com/space/resume.gif
AD http://(www*.|)ohms.com/toolbar.gif
AD http://(www*.|)ohms.com/jmpbanner.gif
AD http://(www*.|)34u.com/images/34ubanner.gif
AD http://(www*.|)themez.com/mini-cg1.gif
AD http://(www*.|)independent.co.uk/-images/buttons/*_*x*.(gif|jpg)
AD http://(www*.|)independent.co.uk/img/commercial/**.(gif|jpg)
ADSWF http://(www*.|)independent.co.uk/images/flash/**.swf
ADSWF http://(www*.|)heise.de/RealMedia/ads/**.swf**
ADHTML http://(www*.|)hit-now.com/b*.php**
AD http://(www*.|)dslvalley.com/images/pub/*/*x*.gif
ADHTML http://(www*.|)dslvalley.com/pub/pub.php?mode=view**
ADHTML http://ads.tripod.lycos.co.uk/ad/*/frame.php?**
ADHTML http://ads.treehugger.com/iframe/th_rightcol.php
ADJS http://*.hitbox.com/js/hbf.js
ADJS http://*.hitbox.com/js?**
WEBBUG http://heise.ivwbox.de/cgi-bin/ivw/CP/newstick_mm;**
WEBBUG http://ehg-dig.hitbox.com/HG?**
COUNTER http://hg1.hitbox.com/HG?**
COUNTER http://aibg.hitbox.com/ace?**
COUNTER http://ias.hitbox.com/**
AD http://stats.hitbox.com/buttons/*.gif
AD http://w[0-9]*.hitbox.com/Hitbox?**
AD http://w[0-9]*.hitbox.com/*.gif
AD http://w[0-9]*.hitbox.com/wc/C*.cgi
AD http://w[0-9]*.hitbox.com/wa/W44103822.cgi
AD http://ias.hitbox.com/*.gif
AD http://ibg.hitbox.com/ace?id=*
AD http://(www*.|)downloadx.com/wallpaper/ad*.gif
AD http://(www*.|)12c4.com/a/*.gif
AD http://adcreatives.imaginemedia.com/MPCN/**.gif
PASS http://g.deja.com/gifs/20x20.gif
PASS http://g.deja.com/gifs/*_x*.gif
PASS http://g.deja.com/gifs/1x1_*.gif
PASS http://g.deja.com/gifs/nextart2.gif
PASS http://g.deja.com/gifs/next_*.gif
PASS http://g.deja.com/gifs/*arrow*.gif
AD http://g.deja.com/gifs/*x*.gif
AD http://w1.dejanews.com/gifs/*.gif
AD http://*.joboptions.com/jo_deja/img/ad_banners/*.gif
AD http://207.87.22.200/content/**.gif**
AD http://(www*.|)x.org/images/banner_*.gif
AD http://(www*.|)wholesaledirect.com.au/images/banner_*.gif
AD http://(www*.|)mcpmag.com/images/ban_*.gif
AD http://*lokau.com.br/images/ban_**
AD http://*banner.inside.com.br/Banner/**
AD http://(www*.|)inside.com/img/memberarea_anonymous2.gif
AD http://(www*.|)inside.com/img/button_*_140.gif
AD http://200.212.87.26/images_capa/**
AD http://(www*.|)wincvs.org/osbanner.gif
AD http://(www*.|)wincvs.org/lw1.gif
AD http://focus.de/GLOBPICS/**.gif
AD http://(www*.|)osopinion.com/art/maxpcn*.gif
AD http://(www*.|)maccentral.com/static/*.gif
AD http://(www*.|)dilbert.com/comics/dilbert/images/*_banner_*gif
AD http://(www*.|)dilbert.com/comics/dilbert/images/*_anim.gif
AD http://(www*.|)dilbert.com/comics/dilbert/images/*_ani.gif
AD http://(www*.|)perlmonth.com/images/barnesandnoble1.gif
AD http://(www*.|)perlmonth.com/images/hv1banner.gif
AD http://(www*.|)silicon.com/image/inform_*.gif
AD http://(www*.|)silicon.com/image/mind_exp_jd.gif
AD http://(www*.|)silicon.com/image/*_ban.gif
AD http://banner.ft.com/banner/*
AD http://explorezone.com/graphics/associates/*.gif
AD http://explorezone.com/graphics/buttons/*.gif
AD http://(www*.|)sol.dk/img/partner/*.gif
AD http://(www*.|)sol.dk/it/newgraphics/banner_ie5.gif
AD http://images.cnn.com/SHOP/partners/**/images/*,gif
AD http://(www*.|)cnn.com/images/9903/barnesstory.gif
AD http://banners.imfc.com/?**
AD http://(www*.|)projo.com/words/images/words.gif
AD http://(www*.|)qsound.com/trackes/*.gif
AD http://images.fogdog.com/toolkit/images/*_*x*.gif
AD http://(www*.|)egghead.com/media/bnr/*.gif
AD http://(www*.|)email-it.net.au/MS_AUS.gif
AD http://(www*.|)hostonfly.com/*/ban/*.gif
AD http://(www*.|)pixunlimited.co.uk/sys-images/Network/Front/Merchandising/**.gif
AD http://(www*.|)amazon.com/g/associates/**.gif
AD http://rcm-images.amazon.com/images/**/associates/**.gif
AD http://(www*.|)amazon.com/**/roto-ads/*.gif
AD http://(www*.|)washingtonpost.com/wp-adv/advertisers/style/images/*.gif
WEBBUG http://rsi.washingtonpost.com/F**.gif?**
ADPOPUP http://(www*.|)washingtonpost.com/wp-srv/popjs/**.htm
ADJS http://(www*.|)washingtonpost.com/wp-srv/javascript/common/promoad.js
ADJS http://(www*.|)canoe.ca/MoneyIncludesDesign/promo_money.js
PASS http://(www*.|)canoe.(com|ca)/(CanoeGlobalnav|CNEWS*Images|MoneyDesign)/*.gif
AD http://(www*.|)canoe.(com|ca)/AdsCanoe/**
AD http://*ads*.canoe.(com|ca)/**.(gif|jpg)
AD http://*ads*.canoe.(com|ca)/event.ng/**
AD http://*.arena.ne.jp/ba/*.gif
AD http://(www*.|)clickz.com/clickz.images/*/*[0-9]x[0-9]*.gif
AD http://8ball.federated.com/*_banner.gif
# AD http://invis*.free.anonymizer.com/http://**
AD http://(www*.|)altavista.com/av/content/images/*.gif
AD http://(www*.|)redhat.com/img/banner_*.gif
AD http://(www*.|)redhat.com/img/free_hat_offer3.gif
AD http://(www*.|)redhat.com/img/button_animation.gif
AD http://(www*.|)ht.com.au/images/bo.gif
AD http://(www*.|)javaworld.com/javaworld/icons-rd/h-store.gif
AD http://lwn.net/images/aspsys/*.gif
AD http://lwn.net/images/linuxtoday/lt_wow.gif
AD http://lwn.net/images/sonysweeps_header_2.gif
AD http://(www*.|)linuxnewbie.org/newbiead.gif
AD http://(www*.|)linux.org/graphic/(square|banner)/*.(gif|jpg)
AD http://(www*.|)provantage.com/AD_*.GIF
AD http://(www*.|)kbench.com/korean/index/*[0-9]_[0-9].gif
AD http://(www*.|)videoclips.freeserve.co.uk/amazon1.gif
AD http://(www*.|)videoclips.freeserve.co.uk/*banne*r*.(gif|jpg)
AD http://(www*.|)videoclips.freeserve.co.uk/*adban*.gif
AD http://www4.macnn.com/media/*.gif
AD http://(www*.|)dvdcity.com/graphics/dvdcity-2.gif
AD http://tsms-image.tsms.com/gifs/*
AD http://(www*.|)calendarexpress.com/CEBabes143x140.gif
AD http://(www*.|)brassmonkey.net/*.gif
AD http://*/sexswapicon.gif
AD http://(www*.|)sexclicks.org/*.gif
AD http://(www*.|)sexnation.net/graphics/*.gif
AD http://(www*.|)pcworld.com/shared/graphics/smartagebutton.gif
AD http://(www*.|)luckysurf.com/BeFree/pix/*.gif
AD http://(www*.|)smartage.com/cgi-bin/befreecookie.pl
AD http://(www*.|)smartage.com/cgi-bin/resell_cookie.pl
AD http://(www*.|)smartage.com/img/promote/media_buyer/*.gif
AD http://(www*.|)slaughterhouse.com/banner/*.gif
AD http://rc5.distributed.net/cgi-bin/banners.cgi
AD http://(www*.|)thefreesite.com/alabsss.gif
AD http://64.152.192.114/stuff_tc/mb_*x20.gif
AD http://(www*.|)snafu.de/~wehe/amzn-b2.gif
AD http://(www*.|)dav[0-9]*.vhm.de/wimages/*_banner_*.gif
AD http://(www*.|)newsweek.com/nw-srv/test/patek/ir_animation.gif
AD http://macintouch.com/images/*.gif
AD http://images.100free.com/*ban[0-9]*.jpg
AD http://add.buzina.com/*.gif
AD http://(www*.|)it-seek.com/cgi-scripts/ffsbantrack.pl?action=view
AD http://(www*.|)whowhere.lycos.com/images/ebay_bst.gif
AD http://(www*.|)whowhere.lycos.com/images/find_books.gif
AD http://(www*.|)whowhere.lycos.com/images/1800/w_letters2.gif
AD http://(www*.|)ms-links.com/cgi-bin/bi2.cgi?**
AD http://home.att.net/~swchoe/desktopani.gif
AD http://(www*.|)medhelp.org/images/differenceAB.gif
AD http://appwatch.com/images/geekbanner1.gif
AD http://appwatch.com/images/banner-*.gif
AD http://(www*.|)excite.com/img/wea/applet/shwpixls.gif
AD http://htmlwizards.com/button/*.gif
AD http://(www*.|)htmlwizards.com/button/*.gif
AD http://(www*.|)freestuffcenter.com/button.gif
AD http://(www*.|)freestuffcenter.com/thegovernmentban.gif
AD http://(www*.|)freestuffcenter.com/sub/buttons/*.gif
AD http://(www*.|)gifart.com/links/*.gif
AD http://(www*.|)gifart.com/buttons/*.gif
AD http://(www*.|)dnps.com/*/banner/*.gif
AD http://(www*.|)dnps.com/*_bans/*.gif
AD http://(www*.|)dnps.com/contests/*.gif
AD http://(www*.|)dnps.com/*banners/*.gif
AD http://(www*.|)dnps.com/edison/*.gif
AD http://(www*.|)dnps.com/netgravity/*.gif
AD http://(www*.|)dnps.com/hotcompanies/top.gif
AD http://(www*.|)dnps.com/classiccars/*.gif
AD http://(www*.|)dnps.com/emf/emf.gif
AD http://(www*.|)dnps.com/huntingtonbank/evenbetter[0-9]*.gif
AD http://(www*.|)dnps.com/internal/*468.gif
AD http://(www*.|)freep.com/grafix/dci_logo.gif
AD http://(www*.|)free-search.com/weeklycontests.gif
AD http://(www*.|)looroll.com/buttons/looroll_banner.gif
AD http://(www*.|)looroll.com/buttons/looroll_button.gif
AD http://(www*.|)looroll.com/buttons/telebutton.gif
AD http://(www*.|)looroll.com/buttons/skindepth_button.gif
AD http://209.58.17.9/workbanner.phtml?action=image**
AD http://(www*.|)indsoft.net/wallpapers/*.gif
AD http://(www*.|)autoworld.com/aig/newaiglogo.gif
AD http://(www*.|)tweak3d.net/images/partof.gif
AD http://z0.extreme-dm.com/i/**
AD http://206.161.225.50/digilogo/logo.cgi?**
AD http://216.27.61.205/dmimages/0441.gif
AD http://(www*.|)mplayer.com/graphics/ad_sales/**.gif
AD http://(www*.|)mplayer.com/graphics/home/defaultad.gif
AD http://(www*.|)quake3world.com/dfnbutton.gif
AD http://(www*.|)fastgraphics.com/logos/*.*
AD http://(www*.|)safe-audit.com/sites/*/*.gif
AD http://(www*.|)alpha-processor.com/images/nav/animtickerfw.gif
AD http://(www*.|)shades.com/v1_banner2a.gif
AD http://(www*.|)globeandmail.com/**_promo.gif
AD http://dev3.ny.thinkinc.com/*/*.sdpban/**.gif
AD http://(www*.|)register.com/images/usanetbanner.gif
AD http://208.178.169.7/nonstop/infinity-120x90.gif
AD http://(www*.|)luminanet.com/[a-z]*banner.gif
AD http://(www*.|)linuxstart.com/images/banner3.gif
AD http://(www*.|)hotthemes.com/images/top501.gif
AD http://(www*.|)hotthemes.com/images/*_affilliate_*.gif
AD http://(www*.|)hotthemes.com/wall/images/myshare_rd54.gif
AD http://(www*.|)hotthemes.com/wall/allbanners/*.gif
AD http://(www*.|)digitalblasphemy.com/graphics/webshots.gif
AD http://(www*.|)commission-junction.com/banners/tracker.exe?**
ADPOPUP http://(www*.|)commission-junction.com/track/track.dll?**
##ADPOPUP http://(www*.|)amazon.*/exec/obidos/tg/browse/**site-redirect**
ADPOPUP http://(www*.|)track4.com/*?**
AD http://(www*.|)icreditreport.com/graphics/2check32.gif
AD http://(www*.|)headhunter.net/images/Aff/*.gif**
AD http://(www*.|)theage.com.au/images/shoptoday.gif
AD http://(www*.|)blackdown.org/images/simplicity.gif
AD http://home.snap.com/main/images/contest/newyear/logos.gif
AD http://(www*.|)startribune.com/mcu/promotions/investorfactory/012000/ha1.gif
AD http://(www*.|)zserver.com/?SIT=**
AD http://banners.orbitcycle.com/router/**
AD http://(www*.|)esign.com.au/*_anim.gif
AD http://(www*.|)anthemrecords.com.au/Banner*.gif
AD http://(www*.|)unsound.com.au/webring/graphics/ozcdstoreslogo.gif
AD http://(www*.|)abe.com.au/cgi-bin/bi2.cgi?**
AD http://(www*.|)abe.com.au/banners/*.gif
AD http://(www*.|)sexplanets.com/banners/*.gif
AD http://technocrat.net/technocrat_net/Image/BannerAdvertising/**
AD http://(www*.|)tvguide.com/rbitmaps/*.gif
AD http://(www*.|)tvguide.com/images/*ad.gif
AD http://(www*.|)lendingtree.com/new/branch/images/2_home_banner.gif
AD http://(www*.|)estore.com.au/images/icons/*button*.gif
AD http://(www*.|)isyndicate.com/images/nav/bignight_468.gif
AD http://(www*.|)themeworld.com/images/*468.gif
AD http://(www*.|)isyndicate.com/images/nav2/anim_logos_new.gif
PASS http://www-*.cricket.org/logos/SUPPORT/HOSTS/components/**
PASS http://www-*.cricket.org/logos/spacer*.[Gg][Ii][Ff]
PASS http://www-*.cricket.org/logos/CI/cricinfo-news.gif
ADBG http://www-*.cricket.org/logos/**-background.gif
AD http://www-*.cricket.org/logos/**.[Gg][Ii][Ff]
AD http://www-*.cricket.org/adlib/server.cgi/**
AD http://**/apbanner*.gif
AD http://**/banner[0-9]*.gif
AD http://http.a.radix.intervu.net/smirror/alembke/rules/bannerimgs125/*.gif
AD http://*/htmlad/*.gif
AD http://(www*.|)adverline.com/cgi-bin/pvis?**
AD http://(www*.|)regieclick.com/pub.zarc?**
AD http://(www*.|)regieclick.com/pubs/[0-9]*.gif
AD http://(www*.|)cybergreetings.com/clipart/associat.gif
AD http://liquidad.narrowcastmedia.com/~wsapi/ncmapi/GIF**
AD http://wwjd.net/wwjd/php_lang.gif
AD http://(www*.|)wwjd.net/wwjd/phpAds/phpads.php*
AD http://(www*.|)paypal.com/images/paypalbanner.gif
AD http://(www*.|)leadinglight.net/banad-*.gif
AD http://privacy.net/_ads/*.gif
AD http://privacy.net/analyze/cool112.gif
AD http://privacy.net/images/eyes2.jpg
AD http://(www*.|)planetmirror.com/images/pmpromo.gif
AD http://(www*.|)planetmirror.com/images/playstation.gif
AD http://(www*.|)planetmirror.com/images/poweredge.gif
AD http://(www*.|)planetmirror.com/images/pmsearch.gif
AD http://comtrack.comclick.com/cgi-bin/aff_bandeau.cgi?**
AD http://bandeau.comclick.net/bandeaux/**
AD http://(www*.|)teletranslator.com:8080/images/pub.gif?**
AD http://mirror.qkimg.net/[0-9]*/[0-9]*.gif
AD http://comtrack.comclick.com/cgi-bin/aff_bandeau.cgi?**
AD http://logv9.xiti.com/hit.xiti?**
AD http://fx4.tgv.net/servlets/adjuggler?**ajtype=cgi_image**
AD http://(www*.|)techcentralstation.com/servlet/CMBinaryServer?cid=**
AD http://fl01.ct2.comclick.com/aff_url.ct2?*
ADJS http://fl01.ct2.comclick.com/aff_js_src.ct2?**
ADHTML http://fl01.ct2.comclick.com/aff_frame.ct2?**
ADHTML http://comtrack.comclick.com/cgi-bin/rq_frame_editeur.cgi?**
PASS http://shamanismweb.org/freak/images/glassblock.gif
PASS http://shamanismweb.org/freak/images/backmain.gif
PASS http://shamanismweb.org/freak/images/pd-*.gif
AD http://shamanismweb.org/freak/images/*.gif
AD http://shamanismweb.org/freak/pictures/webspace_small2.gif
BULLET http://*/anpnt.gif
BULLET http://**/pstmdrn/posbul1a.gif
NEW http://**/buttons/1new.gif
NEW http://*/news[0-9]*.gif
NEW http://*.yimg.com/images/new*.gif
NEW http://(www*.|)yanman.com/images/sign_sm_new.gif
NEW http://(www*.|)free-graphics.com/new.gif
PASS http://(www*.|)free-graphics.com/updated.gif
PASS http://(www*.|)free-graphics.com/arrow.gif
PASS http://(www*.|)free-graphics.com/navigation.gif
PASS http://*.aol.com/price_plans/**
PASS http://movies.channel.aol.com/**/trailer.adp
ADPOPUP http://*.aol.com/**.adp
ADPOPUP http://ads.admonitor.net/clicktrack.cgi?**
ADPOPUP http://(www*.|)aol.com/popups/*.html
ADPOPUP http://eshop.msn.com/categorypopup.aspx?**
ADPOPUP http://fdimages.fairfax.com.au/crtvs/*pop*.html
## stripping the ? seems to break their image cache service
##REWRITE (http://farm*.static.flickr.com/*/buddyicons/*.jpg)?[0-9]* 302:$1
ADHTML http://*xml.eshop.msn.com/xmlbuddy/eShopOffer.aspx?**
AD http://*image.eshop.msn.com/img/merch/**.(gif|jpg)
AD http://*image.eshop.msn.com/img/sinv/**.jpg
AD http://*xml.eshop.msn.com/trackofferimpression.aspx?**
AD http://affiliate.aol.com/static/aan/images/*.gif
AD http://fdimages.fairfax.com.au/*/pop_*.gif
AD http://(www*.|)aol.com/popups/gr/aol_31.gif
AD http://res.sys-con.com/**Pop_Up.gif
AD http://res.sys-con.com/portlet/**.jpg
AD http://(www*.|)newaol.com/aolcreative/images/250hours/88x31bold.gif
AD http://members.aol.com/tennmax/hs_guide.gif
AD http://(www*.|)dse.com.au/isroot/DSE/images/*_banner.gif
AD http://(www*.|)dse.com.au/isroot/DSE/images/banner_*.gif
AD http://(www*.|)wric.com/ic_aol.gif
AD http://(www*.|)wric.com/cocbannr.jpg
AD http://(www*.|)free-graphics.com/*.gif
AD http://adcontent.gamespy.com/**.gif
AD http://adimages.gamespy.com/**.gif
AD http://ad.caramail.com/pub/*.gif
AD http://(www*.|)adverline.com/cgi-bin/pvis?**
AD http://(www*.|)channelseven.com/images/*_promo_*.gif
AD http://(www*.|)cash-for-clicks.de/nt-bin/show.exe?**
AD http://(www*.|)cashforclicks.com/**.gif
AD http://(www*.|)free-banners.com/images/hitslogo.gif
AD http://(www*.|)free-banners.com/images/banner-button.gif
AD http://(www*.|)free-banners.com/images/banner-button2.gif
AD http://(www*.|)free-banners.com/images/applynowcompress.gif
AD http://(www*.|)free-banners.com/images/casino2.gif
AD http://(www*.|)free-banners.com/images/alladvantage-logo.gif
AD http://(www*.|)riva3d.com/allad.gif
AD http://(www*.|)alladvantage.com/images/*.gif
AD http://(www*.|)eads.com/images/refbutton.gif
AD http://(www*.|)jackpot.com/images/hb3.gif
AD http://(www*.|)dcypher.net/images/buttons/anibut.gif
AD http://(www*.|)netmonger.net/~chiptech/jc/pc/gfx/logobutton.jpg
AD http://(www*.|)bostonherald.com/**/images/*[0-9]x[0-9]*.gif
AD http://(www*.|)everythinglinux.com.au/images/ads/**
AD http://everythinglinux.com.au/images/ads/**
#PASS http://(www*.|)ibuypower.com/images/ibuypower-logo.gif
#PASS http://(www*.|)ibuypower.com/images/title-*.gif
AD http://(www*.|)ibuypower.com/images/ad-*.gif
AD http://(www*.|)ibuypower.com/images/logo*.gif
AD http://(www*.|)ibuypower.com/images/netscape.gif
AD http://(www*.|)ibuypower.com/images/ie.gif
AD http://(www*.|)ibuypower.com/images/dialpad_launch.gif
AD http://(www*.|)bonus.com/applets/ecards/mday/image/html/ani*.gif
AD http://(www*.|)linuxmall.com/Images/gotlx1.gif
AD http://bagel.openvista.com/images/cooltunes.gif
AD http://(www*.|)starbuzz.net/starbuzzsite.gif
AD http://(www*.|)pokertraffic.com/cgi-bin/hit.cgi?**
AD http://(www*.|)pokertraffic.com/images/*.gif**
AD http://(www*.|)guide2poker.com/images/*.gif
AD http://(www*.|)trafficoverdrive.com/bpwork2.pl?ID=*
AD http://(www*.|)trafficoverdrive.com/*.gif
AD http://*/TrafficCash/*.gif
AD http://*/TrafficCash/*.jpg
AD http://(www*.|)idirective.com/graphics/banner*.gif
ADHTML http://(www*.|)clickheretofind.com/parse.php3?**
AD http://(www*.|)clickheretofind.com/**.(gif|jpg)
AD http://(www*.|)jackpot.com/images/hb2.gif
AD http://(www*.|)ocworkbench.com/archives/mar2000/content/index.1.gif
AD http://lygo.com/ly/a/h/aff_hotbotlogo.gif
AD http://developer.netscape.com/images/apple.gif
AD http://(www*.|)penguincomputing.com/graphics/squarepc.gif
AD http://(www*.|)linuxquake.com/gif/buttons/lgdc-button.gif
AD http://(www*.|)lightningfree.com/**/buttons/*.gif
AD http://(www*.|)lightningfree.com/images/PhonePics/*.gif
AD http://(www*.|)lightningfree.com/**/*ban[0-9]*.gif
AD http://(www*.|)rdjd.net/banner1/banner1.jpg
AD http://slate.msn.com/articleimages/Drugstore_120x240cprtn_st53381.gif
AD http://slate.msn.com/animated_highlight_tm_free_.gif
AD http://(www*.|)spedia.net/imgs/spb.gif
AD http://(www*.|)uol.com.br/anuncio/goto/*.gif
AD http://*iconet.com.br/banners_front/**
AD http://*iconet.com.br/banners/**
AD http://*valevirtual.com.br/anuncio/**
AD http://*uol.com.br/anuncio/**
AD http://*bol.com.br/adlogbot**
AD http://(www*.|)christianet.com/*/btn_*.gif
AD http://(www*.|)penny-arcade.com/img/rspy.gif
AD http://allhw.com/images/netkills.gif
AD http://realbeer.com/rbi/images/banners/*.gif
AD http://(*.|)bluestreak.com/images/animated.gif
AD http://(*.|)bluestreak.com/ix.e?**
AD http://(*.|)bluestreak.com/adv/**.jpg
ADSWF http://ads.snowball.com/advertisers/**.swf**
ADSWF http://**/(adv|advertisements)/**.swf**
ADSWF http://realbeer.com/rbi/images/banners/*.swf
ADSWF http://(www*.|)tek-tips.com/images/tekattention.swf
ADSWF http://arstechnica.com/includes/tcmtile.swf
ADSWF http://images.anandtech.com/banners/**.swf
ADSWF http://(www*.|)porno-mania.net/a*.swf
ADSWF http://(www*.|)drinkinghard.com/*.swf?**
AD http://arstechnica.com/includes/ars-ad.gif
AD http://(www*.|)qksrv.net/image-**
PASS http://(www*.|)wist.uni-linz.ac.at/~didi/u2/images/jt_green1.gif
AD http://(www*.|)wist.uni-linz.ac.at/~didi/u2/images/*.gif
AD http://u2fanclub.org/cgi-bin/exchange/bpwork.cgi?**
AD http://(www*.|)megaspider.com/megaspider.gif
AD http://208.49.239.150/serv/**
AD http://216.65.106.2/*.gif
AD http://(www*.|)appleinsider.com/images/apple_design.gif
AD http://(www*.|)macosrumors.com/capitalism/*.gif
AD http://(www*.|)wfsdirect.com/graphics/winfreestuff*.gif
AD http://**/newban1.gif
AD http://(www*.|)tourbar.com/*.gif
AD http://**/ban.php?**
AD http://count.ru/cnt?id=**
AD http://(www*.|)one.ru/cgi-bin/cnt.cgi?id=**
AD http://bans.bride.ru/getb?*
AD http://**/pornotallica.gif
AD http://**/porntallica.gif
AD http://**/porntallicabutton.gif
AD http://**/uhohnet*.gif
AD http://**/rawlinks.gif
AD http://**/hioctane.gif
AD http://**/buttons/test08.gif
AD http://**/virtuagirl.gif
AD http://**/vgirl*.gif
AD http://(www*.|)freexlinks.com/images/freexlinksbutton.gif
AD http://networxxx.com/topnic.gif
AD http://static.stileproject.com/forum/link/link/l5.gif
AD http://graphics*.sextracker.com/**.gif
AD http://*.banners.sextracker.com/cids/**.gif
AD http://hestia.sextrail.trakkerd.net/**
PASS http://*.ads.**.html
PASS http://*.ads.**.js
ADPOPUP http://ads.world-free.net/adclick.cgi?**
ADPOPUP http://ads.inet1.com/html-bin/Popup-Auto.asp?**
ADHTML http://(www*.|)click4pic.com/f[0-9]*.html
ADHTML http://adserv.exxxit.com/cgi-bin/roidirect.cgi?**
ADHTML http://sbinternational.igallery.net/cgi-bin/bnd.cgi/**
ADJS http://*/jnserver/**
ADJS http://hit*.vioclicks.com/s3.asp?**
ADJS http://ad.erotik-click.de/myad_show.php*?**
ADJS http://(www*.|)porntrack.com/sexblocks/*.phtml?**
ADJS http://ads*.erotism.com/adults.js
ADJS http://(www*.|)cash2002.de/cgi-bin/cash_x.cgi?**
ADJS http://(www*.|)babebusters.com/clickzs.js
ADJS http://*.clickzs.com/**.js
ADJS http://adcontroller.unicast.com/java**/wrapper.js
ADJS http://adcontroller.unicast.com/java/HTMLad_utils/ad2applet.js
ADHTML http://adcontroller.unicast.com/upload/**.html
# this is actually a Java file - maybe I should leave it alone
AD http://adcontroller.unicast.com/java/classes/adcontroller.jar
ADSWF http://adcontroller.unicast.com/upload/**.swf
ADSWF http://generator.zdnet.com/dell/dellbanner*.swt**
ADSWF http://(www*.|)forcevideo.com.au/force.swf
ADSWF http://se.fs.mgon.com/flashmovies/mgochannel*.swf
ADSWF http://(www*.|)fileplanet.com/gauge_accurate.swf
ADSWF http://(www*.|)babebusters.com/logo.swf
AD http://b.porncity.net/pctop/*.gif
AD http://*.porntrack.com/**
AD http://(www*.|)(boobweb.net|kinghost.com)/ban/**
AD http://bancol.babenet.com/logo.gif?**
AD http://**/bantgp*/*.gif
AD http://(www*.|)freesexspace.com/max*.gif
AD http://(www*.|)sex-mission.com/users/**/buttons/*.(gif|jpg)
AD http://(www*.|)penispill.com/**.gif
AD http://(www*.|)sugarcandys.com/files/bans/**.(gif|jpg)
AD http://(www*.|)pioneerlocal.com/graphics/badges/*
ADJS http://a8-lib.a8ww.net/scripts/sac.js
ADPOPUP http://*.mail.com/**/common/us/(ad_behind|banner_*_logout).htm*
ADPOPUP http://**/AffiliateConsoles/**.(asp|htm)**
ADPOPUP http://sex.globalporn.net/cali/console*.htm
ADPOPUP http://**/exitconsole*.cfm
ADPOPUP http://**/enter_console.php?**
ADPOPUP http://*.telia.com/*/console.html
ADPOPUP http://(www.|)shorturl.com/console.html?**
ADPOPUP http://(www*.|)weeklywallpaper.com/console*.html
ADPOPUP http://(www*.|)glamours.com/console**exit*.html
ADPOPUP http://*.issexy.tv/**popup*.html
ADPOPUP http://(www*.|)boneprone.com/shhh.html
ADPOPUP http://spunkysheets.com/console*.htm
ADPOPUP http://(www*.|)superchicken.com/privacy.html
ADPOPUP http://**/banners/icadverts/directnic/adult_java.html
ADPOPUP http://(www*.|)pantyfantasies.com/verify-nopop.htm
ADPOPUP http://*.need4xxx.net/freepop.html
ADPOPUP http://www.welcometofree.com/ban/ncc.txt
ADPOPUP http://www.welcometofree.com/exit.php3
ADPOPUP http://cgi.gammae.com/go.cgi?**
ADPOPUP http://(www*.|)elitecities.com/free-paysite-access/free-xxx-passwords.html
ADPOPUP http://(www*.|)bigtitfantasy.com/*_pop.html
ADPOPUP http://(www*.|)popadult.com/*.htm
ADPOPUP http://(www*.|)pioneerlocal.com/house/nssubscribe/ns-subscribe-pop.html
ADPOPUP http://webpdp.gator.com/v3/webpdp_v3_detect.php?**
PASS http://(www*.|)help-site.com/gif/blank.gif
PASS http://(www*.|)help-site.com/gif/hs*.gif
PASS http://(www*.|)help-site.com/gif/l_*.gif
AD http://(www*.|)help-site.com/gif/*.gif
PASS http://(www*.|)usdefense.com/images/pgdvder.gif
AD http://(www*.|)usdefense.com/images/*.gif
PASS http://www71.pair.com/compsw/firesite/wd2856/wf110.gif
AD http://www71.pair.com/compsw/firesite/wd2856/wf[0-9][0-9][0-9].gif
PASS http://www71.pair.com/compsw/firesite/wd2856/wf*.gif
PASS http://www71.pair.com/compsw/firesite/wd2833/wf*.gif
AD http://www*.pair.com/compsw/firesite/wd*/wf*.gif
AD http://(www*.|)88888.com/images/oneandonly/rules.gif
AD http://www2.idg.com.au/cwsites/mycw/my_computerworld.gif
AD http://(www*.|)olympics.com/eng/images/*logo*.gif
AD http://(www*.|)olympics.com/eng/images/*promo*.gif
AD http://(www*.|)backupcentral.com/images/banner.gif
AD http://(www*.|)themestream.com/gspd_browse/browse/view_image.gif?com_id=*
AD http://static.gfx.streamate.com/thumb/**
AD http://(www*.|)cwcom.net/ntlworld/images/*.gif
AD http://(www*.|)ntlworld.com/images/promos/*.gif
AD http://www.sanity.com.au/promos/**.gif
AD http://graphic.recommend-it.com/bigbut5mint.gif
AD http://(www*.|)twistedhumor.com/buttons/addr1.gif
AD http://(www*.|)expressindia.com/newads/*.gif
AD http://(www*.|)internet.com/_housebanners/**.gif
AD http://worldwideadultdomains.org/**/mouse.gif
AD http://rstrip.namezero.com/navbar/strip.jsp?**
AD http://turbo.ovh.net/cgi-bin/affiche.pl?**
AD http://comm.ovh.fr/cgi-bin/banniere.cgi?**
AD http://affilies.ibazar.fr/image.phtml?**
AD http://(www*.|)macbidouille.com/ads/**
AD http://(www*.|)macplus.org/cgi-bin/echange/echange.cgi?**
AD http://www.blackorange.com/blackorange/assets/product_images/**
AD http://pub.macgeneration.com/**
AD http://tracker.affistats.com/dirtag.php?**
AD http://(www*.|)regieclick.com/pub.php*?**
AD http://(www*.|)plemx.com/px.exe?**
AD http://(www*.|)techextreme.com/images/*banner.gif
AD http://taggin.com/ad/view.php*?**
AD http://nbe.net-on.net/bserve.cgi?**
AD http://naturalismedicina.com/cgibin/linswap/dis1?**
AD http://adtracking.net-on.net/sys/banner?**
AD http://(www*.|)tech-report.com/i/kagear.gif
AD http://probe.prohosting.com/show/**
AD http://(www*.|)dingoblue.com.au/images/bluesquare.gif
AD http://(www*.|)onelook.com/count/onesuite1.gif
AD http://english.peopledaily.com.cn/pict/ads.gif
AD http://(www*.|)theworldnews.com.au/axafront.gif
AD http://(www*.|)eng-slo.com/Images/pcmax*.gif
AD http://media.quinstreet.com/images/adt/adt_full_0001.gif
AD http://(www*.|)booksonline.com/bookclubs/images/partners/**.gif
AD http://(www*.|)eu.mtnsms.com/images/wildlife1.gif
AD http://adimages.go.com/ad/sponsors/**.gif
AD http://officequest.net/fq-adds/fq-ads.php?**
AD http://shkbanner*.hk.ap.valuecommerce.com/**
ADSWF http://tech-report.com/ads/coolerguys.swf**
ADSWF http://**/(affiliates|affiliation|sponsors|sponsorlogo)/**.swf**
ADSWF http://g.fool.com/art/free/moneyadvisor/**[0-9]x[0-9]**.swf
ADSWF http://(www*.|)kongthumbz.com/uv-hor*.swf?**
ADSWF http://ad.keenspace.com/Skotos/BannerBar.swf
ADSWF http://*/adflash/**.swf
ADSWF http://(www*.|)ottawabusinessjournal.com/www/*.swf
ADSWF http://(*.|)hardocp.com/ads/**.swf
ADSWF http://(*.|)hardocp.com/DA/**.swf
ADJS http://(www*.|)hk.co.kr/adscript/kt_ad_main.js
ADJS http://*/adserve?*;jscript;**
ADJS http://abcnews.go.com/jscript/hbe-v65-no10.js
ADJS http://adimages.go.com/ad/sponsors/utilities/adinsert.js
ADJS http://(*.|)hardocp.com/?DC=**JS=Y**
ADJS http://ads.adservingcentral.com/?**JS=Y**
AD http://(*.|)hardocp.com/?SIT=**
AD http://(*.|)hardocp.com/ugossi/*.(gif|jpg)
ADHTML http://(*.|)hardocp.com/?DC=**DH=Y**
ADHTML http://(*.|)hardocp.com/ugossi/*.(html|php)
ADHTML http://ads.adsonar.com/adserving/getAds.jsp?**
ADHTML http://www.streamate.com/exports/tour/?**&otype=html**
ADHTML http://(www*.|)rapigator.f2s.com/topframe.html
ADHTML http://ebiz.xxx-access.com/topframe.php**
ADPOPUP http://(www*.|)rapigator.f2s.com/tell.html
PASS http://(www*.|)rapigator.f2s.com/images/logo.gif
PASS http://(www*.|)rapigator.f2s.com/images/screenshot.gif
PASS http://(www*.|)rapigator.f2s.com/images/rapsource.gif
PASS http://(www*.|)rapigator.f2s.com/images/wow.gif
PASS http://(www*.|)rapigator.f2s.com/images/subscribe.gif
AD http://(www*.|)rapigator.f2s.com/images/*.gif
AD http://(www*.|)goto.com/images-promoters/**.gif
AD http://a*.qz3.net/**/www.eyewonder.com/customerSpace/**.jpg
AD http://213.219.40.69/*-125x1251.gif
AD http://4.78.22.8/cc*.gif
AD http://(www*.|)theinquirer.net/*-125x1251.gif
AD http://oasis1.economy.com/oasisi.php?**
AD http://mds.centrport.net/mdsefc?**
AD http://iad.anm.co.uk/*/[1-9]*.gif
AD http://(www*.|)domainbuster.com/bizad.gif
AD http://(www*.|)novuslink.net/images/*[0-9]x[0-9]*.gif
AD http://(www*.|)dagbladet.no/*/gavetips/150x500.gif
AD http://(www*.|)dn.no/ads.dn.no/**.gif
AD http://e2.emediate.se/media/**
AD http://(www|gfx).dagbladet.no/an/**
AD http://(www*.|)libertyhaven.com/images/*banner.gif
AD http://(www*.|)itv-f1.com/images/partners/*.gif
AD http://*/@*?
AD http://(www*.|)jspinsider.com/images/*.gif
AD http://(www*.|)cera2.com/*1ogo.gif**
AD http://images*.blogads.com/**/c.gif?**
AD http://**/blogads/**/thumb?**
AD http://(www*.|)komotv.com/art/frontbadges/**
PRINT http://(www*.|)komotv.com/stories/([0-9]*[0-9]).htm http://www.komotv.com/news/printstory.asp?id=$2
ADJS http://*.blogads.com/**/feed.js
WEBBUGHTML http://hb.lycos.com/header?**
WEBBUGJS http://*.imrworldwide.com/v5.js
COUNTERJS http://*.imrworldwide.com/*.js
REWRITE http://switch.atdmt.com/action/msn_hm_*_signup_link?href=(**) $1
WEBBUG http://*.imrworldwide.com/cgi-bin/m?**
WEBBUG http://*.imrworldwide.com/cgi-bin/count**
WEBBUG http://images-aud.slashdot.org/pc.gif?**
WEBBUG http://switch.atdmt.com/action/**
WEBBUG http://**/sitestats.gif?**
WEBBUG http://webhit.aftenposten.no:8080/servlet/WebHit?**
WEBBUG http://cluster.chart.dk/chart.asp?**
WEBBUG http://*.chart.dk/chart.jsp?**
WEBBUG http://jmm.livestat.com/E
WEBBUG http://(www*.|)toplist.cz/count.asp?**
WEBBUG http://(www*.|)whispa.com/tracking/exposure.dll?**
WEBBUG http://*.clickzs.com/in.gif?**
WEBBUG http://(www*.|)click-safe.com/trk**.gif
WEBBUG http://gold.weborama.fr/fcgi-bin/comptage.fcgi?**
WEBBUG http://(www*.|)cnn.com/cookie.crumb
WEBBUG http://cbs.marketwatch.com/1.gif
WEBBUG http://images*.slashdot.org/Slashdot/pc.gif?**
WEBBUG http://dot.idot.cz/?**
WEBBUG http://(*.|)vibrantmedia.com/system/SetURLCookie.asp?**
WEBBUG http://(*.|)vibrantmedia.com/**/1x1.gif
AD http://itxt.vibrantmedia.com/al.asp?ipid=**
ADHTML http://itxt.vibrantmedia.com/al.asp?**
ADHTML http://*.bbmedia.cz/please/showit/**?typkodu=html**
ADJS http://*.bbmedia.cz/please/showit/**?typkodu=js**
ADSWF http://*.im.cz/reklama/**.swf**
ADSWF http://*.im.cz/r/**.swf**
ADSWF http://(www*.|)seznam.cz/rek/**.swf
ADSWF http://(www*.|)svethardware.cz/adv/adv.nsf/**.swf**
ADSWF http://mainos.*.fi/**.swf**
ADSWF http://*.bbmedia.cz/logos/*.swf**
ADSWF http://ad*.lupa.cz/**.swf**
PASS http://imgfarm.com/images/weather.com/**
## BEGIN Sami Sundell zaps rules
# www.lumitykki.net
WEBBUG http://www.lumitykki.net/mainostus/adlog.php?*
AD http://www.lumitykki.net/mainokset/*.gif
ADSWF http://www.lumitykki.net/mainokset/*.swf
ADJS http://track.adform.net/BPL/*
AD http://track.adform.net/Adf/*
# www.radiocity.fi
ADSWF http://www.kiss.fi/images/skabat/hitmedia_win.swf
# www.alypaa.com
ADHTML http://alypaa.com/voice
# www.msn.fi
WEBBUG http://c.msn.fi/c.gif?**
ADSWF http://track.adform.net/Flash/**
# www.iltalehti.fi
ADSWF http://www.iltalehti.fi/ilmkuvat/**.swf?**
AD http://www.iltalehti.fi/ilmkuvat/**.gif
WEBBUG http://stat.www.fi/**
WEBBUG http://stat.almamedia.fi/**
# www.fmi.fi
AD http://www.fmi.fi/img/fi/Talvi.gif
# www.digitoday.fi
WEBBUG http://www.digitoday.fi/services/adlog.php?*
AD http://www.digitoday.fi/services/images/*.gif
ADSWF http://www.digitoday.fi/services/images/*.swf?**
# mycroft.mozdev.org
WEBBUG http://stat.onestat.com/asp/stat.asp?*
# www.digicamera.net
AD http://www.digicamera.net/cgi*/showsell.pl?**
# www.shooshtime.com
AD http://www.shooshtime.com/uploaded/sl1.gif
ADHTML http://www.shooshtime.com/adserver/view.php?*
ADHTML http://www.shooshtime.com/affiframe.php
ADHTML http://shooshtime.com/afffp.php
ADHTML http://www.dumpanimage.com/aff/aff.html
AD http://graphics.adultfriendfinder.com/images/piclist/promo/**.jpg
ADJS http://adultfriendfinder.com/piclist?*
ADJS http://banners.adultfriendfinder.com/piclist?*
ADPOPUP http://www.adultactioncam.com/?*
ADPOPUP http://www.datecam.com/exits_dynamic/index.php?*
ADSWF http://player.videosz.com/win-style-dark.swf
# www.engadget.com
ADSWF http://*.engadget.com/common/media/griffin.swf
# www.ragnaranchorage.tk
ADPOPUP http://banners.dot.tk/bmcbanner?*
## END Sami Sundell zaps rules
AD http://imgfarm.com/images/**.gif
AD http://ad*.lupa.cz/cgi-bin/banredir.cgi?**
AD http://mainos*.fi/mainoskuvat/**.(gif|jpg)
AD http://(www*.|)mtv3.fi/ks/img/ttlogo.gif
AD http://(www*.|)mtv3.fi/uutiset/img/*_mainos.gif
AD http://(www*.|)veikkaus.fi/mtv3/i/*_mtv3.gif
AD http://*.im.cz/reklama/**
AD http://ad*.billboard.cz/**
AD http://ad*.atlas.cz/ban/**
AD http://dbbsrv.com/image/[0-9]**
AD http://i.m3.net/**.gif
AD http://*.bbmedia.cz/please/showit/**?typkodu=img**
AD http://*.bbmedia.cz/logos/*.gif**
AD http://(www*.|)bbmedia.cz/logos/*.gif?**
AD http://ad.*.cz/ad/*banner?**
AD http://ad.leadcrunch.com/show.html?**
AD http://ad*/AdRun.dll?**
AD http://ad*/adrun.dll?**
AD http://ad*/adimg*.asp?**
AD http://www.thaile.com/cgi-bin/f/start.pl?action=be&**
AD http://img.thaile.com:8080/images/**.gif
AD http://(www*.|)adbanner.cz/img/**
AD http://(www*.|)adbanner.cz/**/[Bb]an*.jpg
ADHTML http://(www*.|)banner.cz/showbanner2.php3?**
ADJS http://(www*.|)banner.cz/showbanner.php3?**
ADJS http://(www*.|)awin1.com/awshow.php?**
ADSWF http://channel.mobil.cz/flash/*.swf
AD http://*.billboard.cz/link/banner.cgi?**
AD http://*.idnes.cz/**.asp?baner=**
ADJS http://(www*.|)[Pp]ay[Pp]opup.com/popup.php?**
ADJS http://banner.0catch.com/cgi-bin/popup_mainsite.js
ADJS http://textlink.webmersion.com/cgi-bin/text_server.js
ADJS http://ad.idnes.cz/**.js?**
ADJS http://ad.iaa.cz/ad/**.js
ADJS http://asn.premium.cz/**.js
ADHTML http://ad*.atlas.cz/adhtml*.asp?**
AD http://ad.lupa.cz/cgi-bin/banredir.cgi?**
AD http://ad.adrenaline.cz/adrun.dll?**
AD http://arbo.bbmedia.cz/logos/**
WEBBUG http://www.toplist.cz/count.asp?**
WEBBUG http://*.falkag.de/dat/bgf/trpix.gif?**
WEBBUG http://1bg.cqcounter.com/cgi-bin/c?**
WEBBUG http://stats.clickability.com/t.gif**
WEBBUG http://f2nsmh.*.2o7.net/b/ss/f2nsmh/1/**
AD http://ad.linx.sk/adrun.dll?**
AD http://ad.linx.sk/AdRun.dll?**
AD http://(www*.|)yceml.net/[0-9]**.gif
AD http://(www*.|)dialerfactory.com/**banner*.gif
AD http://content.cpxinteractive.com/**.(gif|jpg)
ADSWF http://*/dat/bgf/**.swf?**
ADSWF http://(www*.|)dialerfactory.com/**.swf
ADSWF http://members.home.nl/**/sexmaxxscroll*.swf
ADSWF http://suburbancrackhouse.org/**.swf
ADSWF http://(*.|)imdb.com/flash/*.swf
##ADSWF http://*.imdb.com/media/imdb/**.swf**
ADSWF http://(www*.|)burnoutpc.com/images/banners/**.swf
ADSWF http://(www*.|)alinom.com/t/**.swf**
ADSWF http://**/ad*[0-9]x[0-9]*.swf**
ADSWF http://(www*.|)stickyhole.com/archivbanner/**.swf**
ADSWF http://*/xxxmovieforum/posttemplateflash*/imgs/*.swf
ADSWF http://*twinkys.com/flash/**.swf
ADSWF http://(www*.|)hankooki.com/adflash/*.swf**
ADSWF http://images.bigfoot.com/images/en/directory/dir_header_*.swf
AD http://images.bigfoot.com/images/en/directory/header_girls.jpg
ADJS http://*twinkys.com/js/*.js
AD http://*twinkys.com/if/*.gif
AD http://(www*.|)smutserver.com/**/120x60.gif
AD http://images.smutserver.com/*.gif
AD http://hose-hounds.com/df/df*.jpg
PASS http://(www*|.)businessweek.com/bwdaily/dnflash/*/nf*.htm
ADHTML http://(www*.|)businessweek.com/bwdaily/dnflash/**.htm
ADHTML http://*-dialer.com/autoload.cfm?**
ADHTML http://(www*.|)start.com.au/startx/system/tracking/tracking_countclicks.asp?**
ADHTML http://oldstats.gamers.com/banman.asp?**
ADHTML http://gamershell.com/ad/*.html
ADHTML http://web.icq.com/client/ate/ad-handler/0,,clrcv,00.htm
ADHTML http://ad.sales.olympics.com/adl/**
ADHTML http://(www*.|)heatsink-guide.com/ad.htm
ADHTML http://messenger.netscape.com/bookmark/*/messengerstart.html
ADHTML http://(www*.|)ppruneadvertising.com/cgi-bin/ads_nonssi.cgi?iframe
ADHTML http://tvdk.bannerstats.dk/adiframe.php?**
AD http://tvdk.bannerstats.dk/bannerdir/*.gif
AD http://(www*.|)olivant.fo/lysingar/**
AD http://(www*.|)portal.fo/lysingar/**
AD http://(www*.|)sportal.fo/lysingar/**
AD http://(www*.|)nitsoh.com/emp.gif
AD http://(www*.|)nummar.fo/graphics/lysingar/**
AD http://(www*.|)decroix.net/Button/but*.gif
AD http://(www*.|)uf.fo/images/lysingar/**
AD http://(www*.|)bil.fo/*.gif
AD http://(www*.|)tele.fo/lysingar/**
AD http://(www*.|)seoghoer.dk/pics/*.gif
PASS http://blog.koehntopp.de/exit.php?**
ADSWF http:/www*.betway.com/itat?action=asset_req**
ADSWF http://hingis.betway.com/tbm/IT/TBM_foot/*.swf**
ADHTML http://netshelter.adtrix.com/serve.cgi?**
ADHTML http://(www*.|)ecasinoads.com/*.htm
ADHTML http://(www*.|)zipzoomfly.com/jsp/AD_Banner/*.jsp
ADHTML http://network.boyis.com/traffic/topframe.asp?**
ADPOPUP http://network.boyis.com/traffic/maiocco.asp?ADV=**
ADPOPUP http://(www*.|)planetlucky.com/retail/offer.asp?**
ADPOPUP http://(www*.|)ig.com.br/paginas/pop_ups/**
ADPOPUP http://*uol.com.br/janelas_assinantes/**
ADPOPUP http://*uol.com.br/janelas_visitantes/**
ADPOPUP http://cancaonova.org.br/janela.html
ADPOPUP http://(www*.|)smartredirect.com/smartredirect_ad.html
ADPOPUP http://(www*.|)smartredirect.com/smartredirect_ad.php?**
ADPOPUP http://(ad.|ads.|www.|)multimania.*/**/perso.phtml?**
ADPOPUP http://pub.chez.com/cgi-bin/perl/popup.pl/**
ADPOPUP http://perso.club-internet.fr/html/Popup/popup_frame*.html
ADPOPUP http://(www*.|)club-internet.fr/pagespersos/popup.phtml
ADPOPUP http://(www*.|)freestuffcenter.com/pop-up/
ADPOPUP http://(www*.|)uol.com.br/janelas_visitantes/ilimitado_comvc.htm
ADPOPUP http://*.com.br/publicidade/publicidade_popup_body.php3?**
ADPOPUP http://(www*.|)brassmonkey.net/link.htm
ADPOPUP http://(www*.|)cash4xxx.de/php-bin/exitwin.php?**
ADPOPUP http://(www*.|)adbuyindex.com/exitwindow.asp?**
ADPOPUP http://66.40.21.115/pop.html
ADPOPUP http://63.215.140.157/xit/**/index.html
ADPOPUP http://213.132.197.200/pm/popup.php**
ADPOPUP http://*/pop.phtml?**
ADPOPUP http://add.buzina.com/*popup*.html
ADPOPUP http://add.buzina.com/*exit*.html
ADPOPUP http://popup.scambiositi.com/advcode.php?**
## ADPOPUP http://**/ctc.cgi?*
ADPOPUP http://(www*.|)geocities.com/toto?*
ADPOPUP http://geocities.yahoo.com/toto?*
ADPOPUP http://*.tripod.*/adm**/popup**.shtml**
ADPOPUP http://*.tripod.com/adm**/popunder/**
ADPOPUP http://(www*.|)hitstation.com/Adserve/banner.cfm?t=1
ADPOPUP http://(www*.|)angelfire.com/cgi-bin/admem?*
ADPOPUP http://(www*.|)angelfire.com/sys/popup_source.shtml*
ADPOPUP http://(www*.|)freewebsites.com/banner/console.html
ADPOPUP http://*lolita-free.com/?**
ADPOPUP http://(www*.|)multimania.fr/general/pub/perso.phtml?**
ADPOPUP http://pub.chez.com/cgi-bin/perl/popup.pl/**
ADPOPUP http://(www*.|)popuptraffic.com/assign.php?**
ADPOPUP http://php.offshoreclicks.com/imps.php?**
ADPOPUP http://php.offshoreclicks.com/dialup_files/install.php?**
ADPOPUP http://arsconsole.global-intermedia.com/*.php?**
ADPOPUP http://all.global-intermedia.com/index.php?**
ADPOPUP http://(www*.|)reliaquote.com/banner/AdBaner/**
ADPOPUP http://(www*.|)time.com/time/interstitials/inter_mt.html?**
ADPOPUP http://(www*.|)time.com/time/interstitials/td_popprem_pi.html?**
ADPOPUP http://search.sprinks.about.com/library/dist/sperch2.htm?siteid=awspop&**
ADPOPUP http://files.slutsandladies.com/**/out*.htm*
ADPOPUP http://(www*.|)business2.com/subs/b2_puord.html?**
ADPOPUP http://bidclix.net/PopUps/Popup*.jsp?**
ADPOPUP http://images.v3.com/pop*.htm
ADPOPUP http://(www*.|)hitboss.com/*/*.htm
ADPOPUP http://(www*.|)hightrafficads.com/conframe.html?**
ADPOPUP http://media.fastclick.net/w/click.here?**pop=**
ADPOPUP http://offers.mailpref.go.com/offers
ADPOPUP http://(www*.|)nextcard.com/pxweb/**.jhtml
ADPOPUP http://instant-access.sex-explorer.com/w_ncc/warning/index.php?**
ADPOPUP http://(www*.|)nakednews.com/exit*.html
ADPOPUP http://(www*.|)xxxsexyweb.com/newspop.htm
ADPOPUP http://(www*.|)premier-blind.com/hardcore/*.html
ADPOPUP http://205.180.85.40/*special/
ADPOPUP http://home.talkcity.com/homepopup.html?**
ADPOPUP http://**/subpopup*.html
ADPOPUP http://**/mainpopup*.html
ADPOPUP http://*.mytoday.de:8200/mytoday/popup.html?**
ADPOPUP http://(www*.|)insands.com/lspop*.htm
ADPOPUP http://(www*.|)insands.com/*popup*.htm
ADPOPUP http://(www*.|)nextcard.com/pxweb/**.*html;**
ADPOPUP http://(www*.|)karasxxx.com/potd/*.shtml**
ADPOPUP http://www.daily*.com/poptopdownloads.html
ADPOPUP http://storefront.linksynergy.com/fs-bin/store?**
ADPOPUP http://(www*.|)yourwebguide.com/interneteraser*.html
ADPOPUP http://www.pokerroom.com/
ADPOPUP http://(www*.|)technologyreview.com/2free_popup.asp?ad=**
ADPOPUP http://(www*.|)mtreexxx.net/cpd/freepass/indexLC.html?**
ADPOPUP http://(www*.|)free*pass.com/free_exit/**.(htm|php)**
ADPOPUP http://(www*.|)hentai-top100.com/cgi-bin/rankem.cgi?**
ADPOPUP http://64.239.23.77/Utils/timer_**.(asp|html)
ADPOPUP http://64.239.23.77/MiniNav/**.(asp|html)
ADPOPUP http://(www*.|)fucking24x7.com/aff.html
ADPOPUP http://(www*.|)smashingthumbs.com/eliminator.html
ADPOPUP http://pop.adultplatinum.com/console/*.htm**
ADPOPUP http://pop.mircx.com/pop/default/pop/**
ADPOPUP http://pop.mircx.com/pop/cjb/pop/**
ADPOPUP http://fr.wedoo.com/ranking/popup/*.*html**
ADPOPUP http://programs.wegcash.com/exits/?**
ADPOPUP http://exits.filthyclicks.com/**
ADPOPUP http://adultdreams.com/randommulti/**.shtml**
ADPOPUP http://(www*.|)prosolutionpills.com/popup/*.html
ADPOPUP http://shopping.webmarket.com/exitpage/*.html
ADPOPUP http://*/exit*.(html|php)**
ADPOPUP http://*/the-exit.php
ADPOPUP http://(www*.|)tier1network.com/poppage-exit.htm**
ADPOPUP http://(www*.|)johnefrem.com/javab/jpop/**.html
ADPOPUP http://console.popupsponsor.com/media/ads/spec_pop.phtml?**
ADPOPUP http://(www*.|)statster.com/server/?**
ADPOPUP http://ads.popupsponsor.com/media/ads/*.phtml
ADPOPUP http://62.146.220.26/*/
ADPOPUP http://(www*.|)crazypopups.com/server/index.php?**
ADPOPUP http://(www*.|)exchangepopups.com/epop.php?**
ADPOPUP http://ad.ilse.nl/popunder.dbl?**
ADPOPUP http://(www*.|)latinmail.com/popup_*.html
ADPOPUP http://(www*.|)datafull.com/**/popup*.(htm|php)
ADPOPUP http://pollserver.interpolls.com/cache/**.html
ADPOPUP http://www.military.com/Data/Popup/New_Education_Popunder.htm
ADPOPUP http://popups.crosswinds.net/popup*.php?**
ADPOPUP http://www.galttech.com/count*.shtml
AD http://(www*.|)datafull.com/popups/*.gif
AD http://bitzi.com/image/bitzipanel-*.gif
AD http://img.suprnova.org/template/sideads/*.(gif|jpg|png)
AD http://(www*.|)p2pnet.net/images/*.gif
AD http://(www*.|)labyrinth.net.au/~mdem/cgi-bin/Advertising/**.gif
AD http://(www*.|)ezydvd.com.au/g/i/b/46860/*.gif
AD http://jnova.cjt1.net/HTM/**JavaSiteReport.asp?**URL=**.gif
AD http://jcontent.bns1.net/bns/**.gif
AD http://www.mecha.ne.jp/~wtw/2CH-*.gif
AD http://flash.2ch.net/image/*bn.gif
AD http://www2.2ch.net/2ch.gif
AD http://2ch.sakuraplus.com/images/*.gif
AD http://teeshot.maido3.com/strap/strap.jpg
ADSWF http://(www*.|)zipzoomfly.com/images/bnr/*.swf**
ADSWF http://jcontent.bns1.net/bns/**.swf**
ADSWF http://www.ezydvd.com.au/g/i/b/46860/*.swf
ADSWF http://(www*.|)datafull.com/flash/*.swf
ADSWF http://(www*.|)madman.com.au/flash/random-*.swf
ADSWF http://www.cyber-traffic.net/cgi/rank3.php
ADSWF http://www.cyber-traffic.net/2ch/link.php
ADSWF http://ad.detik.com/images/**.swf
ADSWF http://media.baventures.com/*.swf**
ADSWF http://icons.ilse.nl/patch/c4sales/*.swf?id=**
ADJS http://view.popupsponsor.com/media/lx.js?**
ADJS http://tpl*.realtracker.com/netpoll/ifreev3ia.asp?**
ADHTML http://j.2004cms.com/HTM/**JavaSite(Report|Request).asp**
ADHTML http://tpl*.realtracker.com/netpoll/MHWAdLookup.asp?AdID=*
ADHTML http://jupiter.bravenet.com/rover/f?*ctype=0*
ADHTML http://www.wallpaperlove.com/bonus.htm
ADHTML http://(www.|)adtology*.com/**.htm
ADHTML http://ads.datinggold.com/iframe*.php?**
ADHTML http://*.falkag.(de|net)/server/rich.asp?cmd=ifr&**
ADJS http://*.falkag.(de|net)/dat/**.js
ADPOPUP http://*.falkag.(de|net)/server/rich.asp?**
AD http://*.falkag.(de|net)/server/?**
AD http://*.falkag.(de|net)/dat/bgf/**.gif
AD http://falk.speedera.net/dat/**.gif
AD http://*.afcyhf.com/**
AD http://stats.popupsponsor.com/pv-trck.php?**
AD http://destiny.autonomous.co.uk/destiny/servlet/autonomous.destiny.hit.AdHitServlet?**
AD http://(www*.|)astalavista.box.sk/*[0-9].(gif|jpg)
AD http://(www*.|)astalavista.box.sk/*-ani.gif
AD http://desktopsunlimited.com/images/virtual*.gif
AD http://**/virtuagirl*_[1-9]*[Xx][1-9]*.gif
AD http://(www*.|)animewallpapers.com/h/tcg/ban**.gif
AD http://ads.datinggold.com/(pic|show.banner)*.php?**
AD http://www.wallpaperlove.com/*messages.gif
AD http://icons.ilse.nl/icons/adverts/**.(gif|jpg)
AD http://*.tradedoubler.com/imp/img/**
ADJS http://*.tradedoubler.com/imp/pool/js/**
ADJS http://destiny.autonomous.co.uk/destiny/servlet/autonomous.destiny.hit.PosHitServlet?**
ADJS http://ad*.nakednews.com/rotatetag.html
ADJS http://bidclix.net/js/pop.jsp?**
ADJS http://addictivetechnologies.net/*/js/Confirm*.js
ADJS http://install.xxxtoolbar.com/ist/scripts/prompt.php?**
ADJS http://espacio.ya.com/js/mosca.js
ADJS http://espacio.ya.com/js/var_mosca.js
ADJS http://(www*.|)bravenet.com/jsbanner.php?**
ADJS http://(www*.|)adv-network.org/advpop/js.php?**
ADJS http://srs.targetpoint.com/resources/inc/banner.js
ADJS http://ads.adorigin.com/?**JS=Y**
ADJS http://ads.digitalacre.com/motor?**
AD http://admin.digitalacre.com/images/**.(GIF|gif)
AD http://cyber-knowledge.net/blog/images/hm.gif
AD http://sportsbybrooks.com/farkbutton.gif
AD http://huuto.net/fi/huutonet/bannerit/*
AD http://ads.**.(gif|jpe?g)
AD http://*.ads.**.(gif|jpe?g)
AD http://ad.erotik-click.de/banner/*.gif
AD http://(www*.|)joinfree.ro/adult20.jpg
AD http://(www*.|)gm.com/nonflash_homepage/images/story*.jpg
AD http://ads.adorigin.com/?SIT=**
AD http://*/kanoodle_img.php?**
AD http://exit.silvercash.com/exit/**.(jpg|gif)
ADHTML http://exit.silvercash.com/exit/**.html
ADHTML http://*.wecloseyoursales.com/**.asp
ADHTML http://fapomatic.com/aff*.html
ADHTML http://context*.kanoodle.com/cgi-bin/ctpub_adserv.cgi?id=**
ADHTML http://ads.adorigin.com/?**DH=Y**
ADHTML http://adzones.torrentspy.com/ad*.htm
REWRITE http://*/ct/*.php?**&ctg=(**)\*\*** 302:$1
REWRITE http://xit.sexlist.com:81/?TSLID=149199/(http://**) 302:$1
REWRITE http://xxxonice.com/ct/cx.php?action=frm&**&src=(http://**)\*\*3F\*\*ids=** 302:$1
REWRITE http://xxxonice.com/ct/cx.php?action=frm&**&src=(http://**) 302:$1
REWRITE http://eurothumb.com/ct/gal.php?**&ctg=(http://**) 302:$1
REWRITE http://(*).freecyberzone.com/cgi-bin/i/images/(**) http://$1.freecyberzone.com/images/$2
REWRITE http://((www*.|)belladonnarealm.com)/downloads/view.php?photo_id=(*)&screen=** http://$1/downloads/pics/$3.jpg
PASS http://(www*.|)ibm.com/common/stats/stats.js
COUNTERJS http://**/stats.js
COUNTERJS http://*.surfaid.ihost.com/**
COUNTERJS http://**/sacdcoc.js
COUNTERJS http://**/track.js?**
COUNTER http://*.legarde.com/cans.php?page=**
COUNTER http://xyz.freeweblogger.com/counter/index.php?**
COUNTER http://counter*.house*.ch/counter/live.php?**
COUNTER http://*.foxcounter.com/foxcounter.php?**
COUNTER http://**/uc.GIF?**
# Nimda defense from Boi
# See: http://(www*.|)incidents.org/react/nimda.php, "DETAILS OF WEB BROWSER-BASED PROPAGATION:"
ADPOPUP http://**/readme.eml
HR http://**/anmcolbar.gif
HR http://(www*.|)geocities.com/SunsetStrip/Hotel/4447/bar.gif
HR http://**/barflash.gif
HR http://**/movingrainbowbar.gif
HR http://(www*.|)crosswinds.net/~donaldhinds/gif/line09a.gif
HR http://home.beseen.com/hobbies/gammaray2/tiles11.GIF
# NEXT http://home.att.net/~swchoe/next.gif
# PREV http://home.att.net/~swchoe/previous.gif
### END AUTO __DATA__ AREA

```

```

sudo chmod a+x /usr/local/bin/squid_redirect

```

then install "Tor button" from apps.mozilla.org, this will allow you to turn on and off tor by a simple click in firefox

[COLOR="Red"][SIZE="4"]Recap / understanding[/SIZE][/COLOR]

so basically 

firefox netowrk proxy settings set to 3128 > squid
squid.conf point to 8118 (privoxy)
privoxy goes to tor (optional download torButton from mozzila addons, for a fast on and off for tor)

you request a page, squid requests it from privoxy and onto tor, the page is sent back to squid, 
addzapper removes any adds, and the page, images, videos, files whatever is cached 

so you can view the page quicker the next time :)

---

### Post by TheIrishGuy on 2007-11-16
you end up with something like this, addzapper is not perfect, but its gets enough of them!!

[IMG]http://www.feeditout.com/addzap/1.png[/IMG]

[IMG]http://www.feeditout.com/addzap/2.png[/IMG]

[IMG]http://www.feeditout.com/addzap/3.png[/IMG]

---

### Post by mfolnovic on 2007-11-17
but proxies slows internet down, right ?

---

### Post by coldstatue on 2007-11-17
> **mfolnovic said:**
> but proxies slows internet down, right ?

Definitely. And don't forget, this anonymizes you - it doesn't protect your data. If you log in to your (plain text, unencrypted) email through Tor, anyone running an end node can read it.  Please see:

[http://arstechnica.com/news.ars/post/20070910-security-expert-used-tor-to-collect-government-e-mail-passwords.html](http://arstechnica.com/news.ars/post/20070910-security-expert-used-tor-to-collect-government-e-mail-passwords.html)

please also see:

[http://digg.com/search?s=tor&submit=Search&section=all&type=both&area=all&sort=most](http://digg.com/search?s=tor&submit=Search&section=all&type=both&area=all&sort=most)

Using Tor may actually draw attention - especially if you run a node. People have been busted for the traffic of OTHERS running through their nodes.  It's an interesting fight if you are concerned about privacy and freedom of speech. But if you're just looking for a way to do illegal stuff, it's bad news. (Though I'm sure many-a-hacker hath found solace in Tor) If you just don't want your  small town ISP knowing that you look at totally legal T & A, well... more power to ya. I am no expert, but this is what I have picked up through this forum and articles on Digg.

---

### Post by Crypto77 on 2007-11-18
Ok. basically I followed everything in the tutorial, and when I visit the URL [www.watismijnip.nl]("www.watismijnip.nl") I get a different IP address than I did before installing privoxy and tor.  However, upon visiting this site [www.whatsmyip.org/]("www.whatsmyip.org/")  It gives me the same number it did before I installed and configured the software.  Whats up?  Does tor only fools some sites?

---

### Post by coldstatue on 2007-11-18
try this first

[http://torcheck.xenobite.eu/](http://torcheck.xenobite.eu/)

its a yes/no - tor is/isn't working site

also, make sure you use the official tutorial
[http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)

did you install the firefox pluigin (if using ff) the status of the text/icon it provides is a good indicator too.

---

### Post by rexmundy on 2007-12-06
Hi, I'm new to this and I have been trying to get it to work. I have the toolbar and a proxy set up, but when I check it at [http://www.watismijnip.nl/](http://www.watismijnip.nl/) it still gives me the same IP address. What am I not doing right here?

---

### Post by ice60 on 2007-12-07
> **rexmundy said:**
> Hi, I'm new to this and I have been trying to get it to work. I have the toolbar and a proxy set up, but when I check it at [http://www.watismijnip.nl/](http://www.watismijnip.nl/) it still gives me the same IP address. What am I not doing right here?
i haven't read through this thread so i don't know anything about a toolbar, but maybe you forgot to chain privoxy with TOR and your browser is just connecting straight to the site without going through privoxy.

if you want to be sure to be anonymous you have to be careful about your browser making direct connections through java applets and flash, you can either disable javascipt and java, or make them go through privoxy.

---

### Post by subs on 2007-12-07
this wont give me any problems with dhcp will it because of the dynamic ip jig

---

### Post by mozkill on 2007-12-12
An alternative method to secure browsing:

1. install  SQUID and "ssh" on home machine with Synaptic  ( for the time being, just enable "http allow all" in the squid.conf )
2. Setup a Secure tunnel from your machine  to your home machine using Putty.exe .
3.  Point webbrowser at the local port that Putty listens on.

all web traffic is piped from your browser through putty to your home sshd daemon (port 22) and forwarded to squid on your home machine.

thats it.

(here is someone who does it like I do:   [http://tech.burgessfam.com/2007/06/secure-tunnel-through-putty_30.html](http://tech.burgessfam.com/2007/06/secure-tunnel-through-putty_30.html) )

---

### Post by kevdog on 2007-12-25
mozkill

What does squid in this configuration do for you??  It might mask the clients IP address, however would it just allow the IP address of the server to be sent??

Also can you explain to me any other additional steps to setup squid?

---

### Post by loodjuret on 2007-12-26
As mentioned earlier, it's wise to know that Tor doesn't protect your data. Data traffic through exit nodes is easily monitored. Using accounts with a login/passwd without any encryption can be a bad idea with privoxy installed.

---

### Post by illumeo on 2008-01-07
Followed the HowTo and works according to the torcheck site.  It does slow things down a bit.  how do i turn it off if i don't need it?

cheers

---

### Post by illumeo on 2008-01-08
ok, installed the fire fox button for tor and works, (once you use it)

---

### Post by edgarinventor on 2008-01-11
Done what you say, but stopped at seeing the Proxy bar on Firefox.
I just use the Proxy you've wrote, and it goes along fine.

Is it ok to skip the remaining steps?

---

### Post by inzaghi89 on 2008-01-14
Fine, i've installed the tor and privoxy, but i've question. What is this process [[img]http://www.inzaghi89.is.net.pl/uploads/thumbs/200801141506281583356802zrzutekranu_Firestarter_inzaghi89.png[/img]](http://www.inzaghi89.is.net.pl/uploads/200801141506281583356802zrzutekranu_Firestarter_inzaghi89.png)

Are this dangeorus? Or sending sth info from my pc? I've another one question, is the tor safe?

---

### Post by x53x6ex69x67x67x65x72 on 2008-03-08
Hi
I've installed Tor & Privoxy (And They are starting properly.) 
But I've a problem like this post:
```
http://ubuntuforums.org/showpost.php?p=538485&postcount=26
```
When I try to open google (or any other site) browser says:> 
No such domain

Your request for [http://www.google.com/](http://www.google.com/) could not be fulfilled, because the domain name [www.google.com](www.google.com) could not be resolved.

This is often a temporary failure, so you might just try again. 
I checked tor's logfile, And it says :
> No Tor server exists that allows exit to [scrubbed]:80. Rejecting.

What's the problem??

---

### Post by Laughed on 2008-03-09
this in't working for me. when I use sites like ipchicken my addie is always the same. What gives???

---

### Post by Nerdriot on 2008-03-09
Went to install, got this:

```
Starting tor daemon: tor...
Mar 09 22:11:36.392 [notice] Tor v0.1.2.17. This is experimental software. Do not rely on it for strong anonymity.
Mar 09 22:11:36.394 [notice] Initialized libevent version 1.3b using method epoll. Good.
Mar 09 22:11:36.394 [notice] Opening Socks listener on 127.0.0.1:9050
invoke-rc.d: initscript tor, action "start" failed.
dpkg: error processing tor (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tor
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Didn't know what to think of it, but continued on through the rest of the tutorial.

Installed the FireFox plugin, and it doesn't allow me to add a proxy...

Sadface.

Any ideas?

---

### Post by Nerdriot on 2008-03-09
Well, now that I'm able to add a proxy, everything I go to gives me a nice, big ol' 503.

Heeeeeeeeeelp!

---

### Post by Nerdriot on 2008-03-09
Fixed, sorry.

</noobishness>

---

### Post by Laughed on 2008-03-10
This is still not working for me

---

### Post by frodon on 2008-03-10
> **Laughed said:**
> This is still not working for meThanks for sharing, hope someone will be able to guess what your problem is but since there's not a lot of mediums here, giving details on what steps you followed to install and configure TOR would be more useful if you want to solve your issue.

---

### Post by Lucho77 on 2008-04-14
Thanks Dutch, I did just set it up and it's working good.

---

### Post by Gnezis2001 on 2008-09-22
> **dutch said:**
> hi after 5 months using ubuntu the first how to
be gentle with me !  :-)

=====================================
go to [www.watismijnip.nl](www.watismijnip.nl)  and write down youre ip ( you need it later)
```

$ sudo apt-get install tor privoxy

```


```

sudo gedit /etc/privoxy/config

```
and ad this line: "  forward-socks4a / localhost:9050 .  " (with the dot at the end)

then go to 
```

https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&id=125

```

click on "install now" (62 kb file)

then firefox askes you to install now ? > click on install now

after the instalation you have to restart fire fox again.
Then go to extra > switch proxy > manage proxies > add > standard > next.

Then fill in:
Next enter the following information into both the http proxy and ssl proxy fields. Hostname: 127.0.0.1 port: 8118. Set up any proxy exceptions you may need and then click on ok.(do this also for the proxy label)

then choose in firefox > extra > switch proxy > preferences > and apply "show toolbar"

now the toolbar wil be shown in ff.
Choose  proxy, your proxy server you just filed in: 127.0.0.1

for other proxys go to:
```

http://proxy.org/tor.shtml

```

then go to [www.watismijnip.nl](www.watismijnip.nl) and look if youre ip is different from above !
Then it worked, else not you can put you're questions here below.

=====================================

hope it did work !

Cheers, 

dutch.

With thanks to:
- ubuntu_demon
- ```

http://www.jgmnet.org/torfaq.html

```
- lindt

hi nice tutorial !!! , i would like to know how to configure it to obtain a united states ip , thanks
EMAIL:   [email]gnezis@gmail.com[/email]    THANKS FOR THE HELP

---

### Post by claypole on 2008-10-13
Thanks Dutch, works great!

I wanted to use this to enable access to Pandora outside of the US also, so I added the following three lines to "/etc/tor/torrc"

[FONT=courier new]StrictExitNodes 1
exitnodes
desync,whistlersmother,lefkada,bettyboop,croeso,TorLuwakOrg,nixnix,inap1,redpineapple,cronic,sasquatch,slowturtle2

Then run "sudo /etc/init.d/tor restart"

This just forces TOR to make the last exit node in the US.

Dutch, can you add to the original HOWTO at the bottom so the info is all available in one place, I was going to post a separate HOWTO but this is the only change/addition so probably makes sense to keep it here and will save other people the time it took me to find and test.

:guitar:
[/FONT]

---

### Post by TheFuzz4 on 2009-03-03
I was wondering if anyone had a how to or knew how to setup a server for this.  i.e. I have a Kubuntu server here in my house that currently does not do much.  I would like to be able to have the rest of my client machines in the house connect to this server for the TOR client.  Currently when I try and do it, it tells me that they are not allowed to proxy through it.   Thanks for your help with this in advance by the way this HOW TO was great and the TOR client is running great.

---

### Post by sgissinger on 2009-03-06
great, thanks !

---

### Post by jaqrah on 2009-04-04
Thanks Dutch!

I spent a few hours last night trying to figure this out.  Glad I found this tutorial today before I punished myself further. ;)

Jaq

---

### Post by gakazzi on 2009-04-05
this is not working for me... my IP stays the same when I check it...
running tor from the command line I get...

Apr 05 22:30:42.336 [notice] Tor v0.2.0.31 (r16744). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Apr 05 22:30:42.339 [notice] Initialized libevent version 1.3e using method epoll. Good.
Apr 05 22:30:42.339 [notice] Opening Socks listener on 127.0.0.1:9050
Apr 05 22:30:42.339 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Apr 05 22:30:42.339 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Apr 05 22:30:42.339 [err] Reading config failed--see warnings above.

any help?

---

### Post by Tressica on 2009-04-24
The site, 
[https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&id=125](https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&id=125)
doesn't work.  Is there another one I can get?

---

### Post by xyepblra on 2009-04-27
I have upgraded my Intrepid Ibex to Jaunty Jackalope and now I cannot install tor under JJ. Can anybody tel me how to do that?

---

### Post by Tressica on 2009-04-29
How do you shut off Privoxy?  It's messing with my email and I need it off NOW.  Do I just run [killall tor] ?

---

### Post by nunki on 2009-04-29
> **Tressica said:**
> How do you shut off Privoxy?  It's messing with my email and I need it off NOW.  Do I just run [killall tor] ?

Run
```

sudo /etc/init.d/privoxy stop

```

---

### Post by xyepblra on 2009-04-29
> **Tressica said:**
> How do you shut off Privoxy?  It's messing with my email and I need it off NOW.  Do I just run [killall tor] ?In drop-down menu on the Privoxy toolbar choose "None", then click on "Apply" button next to the drop-down menu, and enjoy your connection as usual.

**My Privoxy doesn't want to get installed under Ubuntu 9.04. Reason is tor package, which is no longer available but was mentioned in the dependencies list for the other package. Can anyone help me installing it?**

---

### Post by Neheb on 2009-05-06
> **xyepblra said:**
> **My Privoxy doesn't want to get installed under Ubuntu 9.04. Reason is tor package, which is no longer available but was mentioned in the dependencies list for the other package. Can anyone help me installing it?**

Check out [http://www.avuc.nl/2009/05/04/tor-on-ubuntu-904/](http://www.avuc.nl/2009/05/04/tor-on-ubuntu-904/). seems like that works.

---

### Post by xyepblra on 2009-05-16
Great HOWTO, but
> **Dutch said:**
> ```

$ sudo apt-get install tor privoxy

```won't work for tor in Jaunty. Download [debian package for tor]("http://packages.debian.org/etch-backports/i386/tor/download") and install it manually. The rest will be as easy as described by Dutch.

---

### Post by tturrisi on 2009-05-17
FYI all,

Anon browsing via proxies and TOR, for the most part, is successful.  But know that there's no such thing as 100% of the time anonymous browsing.  Code can be used on a Web docs that detects proxies, as well as TOR exit nodes, and the script can then do other things, like make requests to multimedia or other plugins that will send back the real IP address assigned by your ISP.  And there are other methods of determining a visitor's real IP address.

I bring this up in case anyone thinks that their identity is secured by surfing anonymously.

---

### Post by kthxbai2u on 2009-05-18
Well,

nice writeup so far...

Anyone needing to surf anon just google "anonymizer" and it should come up with tonnes of results :)

---

### Post by Poadrim on 2009-07-29
Hi, have been reading this thread and I have some questions, (I have also read the [http://www.jgmnet.org/torfaq.html](http://www.jgmnet.org/torfaq.html) and that diden't help me much) I have added to proxys and "http://www.jgmnet.org/torfaq.html" says that you can use tor with a database, so how do I connect tor and the datebase?

---

### Post by jennakellogg on 2009-07-29
Thanks for the post Dutch, it worked for me. :)

---

### Post by KyonoRocks on 2009-08-03
OK this really doesn't seem to want to work for me. This is what I've done...

1. Followed all the steps in the HOWTO
2. Realized that Tor wasn't installed because this guide is really old and 9.04 doesn't have it
3. Installed Tor through looking at the torproject.com linux installation advice
4. Installed Tor Button

So now I've got Privoxy toolbar showing on my firefox, with my single proxy '127.0.0.1'. The settings are 127.0.0.1 with 8118 in all the port boxes except in the SOCKS box where I've stuck 9050 as the port number. On the bottom of my browser I have the Tor button text which toggles between Tor Disabled and Tor Enabled when I click it.

I go to the IP checker site and my IP hasn't changed. Since the IP hasn't changed, I'm not going to complain about it not working for blocked (in China) sites yet.. since I can't seem to get it to work for unblocked sites!

**Note:** I'm in China and I want to use this as a way to get around the bloody 'Great (fire)wall'. I usually use web based proxies but they often get shut down by the government within a couple of days. If I can get this to work, will it give me the same experience as a web-based proxy site without having to find a new one every 3 days?

I'm completely new to Ubuntu (and proxies in general!) so please bear with me

---

### Post by ArmenianLeader4 on 2009-08-03
Nice tutorial. Works fine for me. (but i don't NEED to be surfing anonymously :D)

---

### Post by KyonoRocks on 2009-08-14
Can anyone help me? 2 posts up. I need to watch videos on YouTube and for some reason web proxies don't let me! I hate China arghh!

---

### Post by plyn_ on 2009-08-16
> **KyonoRocks said:**
> Can anyone help me? 2 posts up. I need to watch videos on YouTube and for some reason web proxies don't let me! I hate China arghh!

gotomypc.com

If you can access a computer outside of the country, then you can open a browser and surf the net. Given that you know someone who would let you run this on their comp. Tried and tested from within China as of 7/09.

---

### Post by brianmc on 2009-10-12
This entire thread should be completely taken down and all links to it redirected to a well written tutorial on tor. The details may well have been correct several years ago, but not now, not in any clear and concise way, and not with notes of what tor should not be used for. :mad:

No, it is not for use with your precious p2p client. Look for another solution to that problem. There are people living under oppressive regimes need the bandwidth you'd suck up just to get the next episode of "Pets do The Funniest Things".

No it is not for hulu, spotify, youtube, or any damn ENTERTAINMENT site that your ISP or country blocks you from. First, for the same reasons as p2p is out. Second because these sites frequently use Flash and Java.

Flash has it's own in-built cookie mechanism. Changing your Firefox settings, or the Privoxy settings will not stop this. If you ever run flash from the same site both via tor, and direct, your identity is compromised.

Java, when run locally, can obtain sensitive information and pass it back to the web site you are looking at. ALWAYS disable Java when using Tor.

On Windows, there is the Vidalia package, this - in combination with Torbutton for Firefox - does things right. This is also the configuration best-tested by the Tor developers.

Torbutton for the standard version of Firefox shipped with 9.04 Jaunty is ... shite. It is unreliable in toggling between using and not using Tor, but at least it does deal with a lot of the important security issues like Flash, Java, and cookies. Yes, if cookie settings are wrong, or not stripped somewhere you're identity is revealed again.

The Vidalia 'manager' window would be nice to have - but does not work if you have tor set up as a service and launched fairly early on. With it you could easily manage the Tor setup, and at-will request a new circuit,

At the moment, if you want Tor you have to get it from the tor project's repository. Yet, EVERY SINGLE UBUNTU TUTORIAL HERE makes zero mention of actually checking the full fingerprint of the key used to sign packages. If you don't know why this is important, google for hash collisions before one has you as the bitch of some Chinese hacker.

Grumbling over, I'm off to see if I can put together a decent tutorial on this, one that's not "DO A,B,C,D" result: super-anonymous! Because that, quite simply, is not how these things work.

---

### Post by MelDJ on 2009-10-12
this tutorial is four years old. its better if you google a way to do it than read this

---

### Post by brianmc on 2009-10-12
> **MelDJ said:**
> this tutorial is four years old. its better if you google a way to do it than read this

Yes, but you're forgetting something. Virtually every other tutorial 'out there' is equally outdated. Google does take age into account in its algorithm, this is one of the first hits people will find - and get it disastrously wrong.

I at least have the advantage that I know who Peter Palfrader is, and have some background in the theory of secure communications over an insecure network. If I write a tutorial, I can at least get it sanity-checked before someone else who really needs Tor to work properly screws up and ends up consigned to an oubliette in some oppressive regime.

If you want to say, "move on, try somewhere else, pray you don't **** up", fine. It's the wrong attitude and reaction to this particular piece of incorrect (or, more charitably, outdated) information.

I'm going to do something about it, but in the meantime I would say that anyone who wants to access the web using strong anonymity (and doesn't have a fair to good understanding of cryptography, onion routing, and browser leakage) get the Vidalia bundle for Windows, yes, you heard, Windows. It has been extensively tested by people who know what they're doing, and what attacks using Tor can be subjected to. The sad fact is, their efforts are best invested there to provide the best protection to as many people as possible.

For those who still want to try and get Tor running with this - or any other tutorial - the following are important points.


[LIST]
[*]Tor will always mean access to the web - or any other service - is much slower. The encryption involved adds an overhead; but, more importantly, your traffic is probably going at least four times further between you and the sites you look at - versus the direct connection.
[*]Cookies, Flash, Java, and a variety of other helpful bits and pieces for your web browser can easily give away your identity and/or IP address.
[*]Many websites block Tor in some way or other; as do services like IRC servers. Anonymity turns people into ******** - and they've already spoiled things for a lot of people. Wikipedia is probably the prime example here. All Tor exit nodes are blocked from editing Wikipedia (with obscure ways for you to get an exception for a particular Wikipedia account).
[*]Never log on to a service like webmail or a bulletin board through Tor unless the service's web address starts https:// There are malicious Tor exit nodes out there; if your traffic via Tor isn't leaving the exit node encrypted (as it is with [https://)]("https://%29") then a malicious end node can get your username and password. They can also get absolutely any other personally identifying information you might send out.
[*]If you are having problems with search - such as Google.com redirecting you to the language site most appropriate for the location of the exit node, use a country-specific google address for the language you want. For example, [http://google.com.au](http://google.com.au)
[*]At all times keep your [AFDB]("http://zapatopi.net/afdb/") in place. ;-)
[/LIST]
Later....

---

### Post by Axess_Denied on 2010-01-18
Bump

So what solutions exist for users to communicate via the internet with anonymity? A Google search for 'anonymizing proxy, ubuntu' yields this post. 

I understand that a lot of undesirables (pedophiles, pirates and malicious users) use Tor. Is there a better solution?

I would like internet anonymity for several reasons other than pornography, piracy or hacking... keeping telecom companies out of my business is one.

---

### Post by brianmc on 2010-01-19
> **Axess_Denied said:**
> Bump

So what solutions exist for users to communicate via the internet with anonymity? A Google search for 'anonymizing proxy, ubuntu' yields this post. 

I understand that a lot of undesirables (pedophiles, pirates and malicious users) use Tor. Is there a better solution?

I would like internet anonymity for several reasons other than pornography, piracy or hacking... keeping telecom companies out of my business is one.

Tor is your best solution; and you are painting its users with a broad and particularly negative brush.

An anonymising prixy is a bad idea; you don't know who set it up and what data they're capturing when you use it.

It is worth the effort to set up Tor, but it will be slow, and it isn't just download and install a package - unless the Firefox plugin has been properly fixed.

---

### Post by manners2345 on 2010-03-22
Finally after much trying, I think I am closing in on getting tor to work

I am getting the following: 514 Authentication required, when tor button is enabled, trying to setup so censored users can reach Internet, not just as a relay


What does that mean in ENGLISH??

Thank you!!!!

---

### Post by manners2345 on 2010-03-22
Also trying to run thru wine, Windows Firefox

---

### Post by marklusty on 2010-11-08
Hi guys,I have just been to the tor website,grabbed the linux bundle and have it running fine on my desktop.I have had 2 different ip`s on running the software bundle.

---

### Post by WarrenSH on 2011-02-17
What about people that use Chrome over Firefox?

---

### Post by brianmc on 2012-07-16
This has been languishing, so I want to try and give some pointers on the question and broader issues with anonymity.

> **WarrenSH said:**
> What about people that use Chrome over Firefox?

I've no idea what your options are for Chrome. You **probably** could simply tell Chrome to use a localhost connection to the Tor process on your machine. But, as a non-Chrome user I don't know how to make those changes.

What I've done for Firefox is to install Tor, and configure as-per the instructions on the Tor site; those are always going to be the most-current. You, usually, then want some sort of filtering proxy. I've used Privoxy, which helps by cutting out most tracking cookies, making sure stuff is wrapped into a localhost SOCKS proxy.

The reason you want/need a localhost SOCKS proxy is that you do not want your DNS lookups leaking out to your ISP; DNS lookups have to go out via Tor.

Now, a prior poster has asked about Flash. Sorry, but you ***cannot*** trust Flash through Tor. Flash has the built-in functionality to query your local machine and find out your real IP address. The same goes for JavaScript and Java.

---

