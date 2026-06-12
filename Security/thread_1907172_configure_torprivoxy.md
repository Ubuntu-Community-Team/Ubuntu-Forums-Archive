---
title: "configure tor/privoxy"
date: 2012-01-10
forum: Security
---

### Post by nethero on 2012-01-10
I guess this belongs on the security discussion forum.

I'm trying to configure Privoxy and Tor to work with Chrome.  Here is what I've done so far...

I've installed Privoxy using synpatic and edited the /etc/privoxy/config file to uncomment the line  "forward-socks5             /     127.0.0.1:9050 ." and restarted privoxy by typing sudo /etc/init.d/privoxy restart

I added the Tor repository to apt and installed tor, torsocks, and tor-geoipdb

I added the extension SwitchySharp to Chrome.

My question is how do I configure SwichySharp to work with Tor/Privoxy?

Here is a screenshot of how I've filled it out so far....

[IMG]http://img707.imageshack.us/img707/6972/screenshotcma.png[/IMG]


I don't have anything filled in for the Socks proxy.  Should I also enter 127.0.0.1 port 9050 (tor port)?  Please forgive the noob question, but what does my browser use a socks proxy for?  Do I need to use tor as my socks proxy for my browser?  Thanks.

---

### Post by hackertarget on 2012-01-11
You would not need to use the socks proxy option in the browser for privoxy.


A Socks server will proxy a lower level TCP or UDP connection, while a HTTP server will proxy only the HTTP protocol.

A HTTP server can because it understands the HTTP connection perform content blocking and content caching.

You would possibly use the Socks proxy if you were using other protocols over the Tor network.

[https://trac.torproject.org/projects/tor/wiki/doc/TorifyHOWTO](https://trac.torproject.org/projects/tor/wiki/doc/TorifyHOWTO)


* I hope that makes sense, I have not had any coffee yet. :confused:

---

### Post by bodhi.zazen on 2012-01-11
See also : [http://bodhizazen.net/Tutorials/TOR](http://bodhizazen.net/Tutorials/TOR)

---

### Post by Ms. Daisy on 2012-01-12
> **bodhi.zazen said:**
> See also : [http://bodhizazen.net/Tutorials/TOR](http://bodhizazen.net/Tutorials/TOR)
bodhizazen, nice tutorial!  I'm following it but the Firefox add-on torbutton "has been removed by it's author." Will foxyproxy do the same thing?

Also, you recommend editing the repository to
```
deb http://deb.torproject.org/torproject.org lucid main
```I assume that I would change "lucid" to "oneiric" if that's what I've got installed, right?

---

### Post by bodhi.zazen on 2012-01-12
You are correct on the repository, change "lucid" to your version of Ubuntu.

Torbutton appears to be maintained

[https://www.torproject.org/dist/torbutton/torbutton-current.xpi](https://www.torproject.org/dist/torbutton/torbutton-current.xpi)

[https://blog.torproject.org/blog/torbutton-141-released](https://blog.torproject.org/blog/torbutton-141-released)

I have not tried it. Torbutton does more then switch proxies.

[img]http://www.pc-freak.net/images/torbutton-properties_dialog.png[/img]

---

### Post by nethero on 2012-01-13
> **hackertarget said:**
> You would not need to use the socks proxy option in the browser for privoxy.

Thanks for the explaination.  I was just wondering why ProxySwitch included a SOCKS option to begin with if all a browser uses is HTTP.  Based on your description it sounds like a web browser would not even need direct access to a SOCKS proxy at all, right?  Does  a browser use SOCKS for downloading or for some other function that I'm not aware of?

> **bodhi.zazen said:**
> See also : [http://bodhizazen.net/Tutorials/TOR](http://bodhizazen.net/Tutorials/TOR)

That is an excellent tutorial!  Should be a sticky somewhere :D.  I was aware of privoxy and polipo but your tutorial showed me some unique configs that will come in handy.  Also I never tried configuring my entire system to run through tor, I wasn't aware that it could be done without something like torsocks.  I'll try it using your tutorial at a later date.

Also, thanks for the screenshot of torbutton.  I've been using foxyproxy but then when I switched to chrome and ProxySwitch I saw the SOCKS option and was wondering why chrome needed it (hence my questions).  Anyway, I remember when all tor button did was change your browsers proxy settings.  It appears they've added lots of new features to it.  Now it disables javascript, form autofill, and disables browser plugins?   Oooooo  Foxyproxy does not do all that!  Although foxyproxy does have a great deal of flexibility so I'll probably keep it around.

---

### Post by 0011235813 on 2012-01-15
Mate, I don't know why you put tor as an HTTP proxy; tor is a SOCKS proxy. If you try to open a webpage with tor as an HTTP proxy, it will not load- you will simply get an error message saying that tor is not an HTTP proxy and that it is a SOCKS proxy and that you should configure it appropriately. You just type the IP and the port in the SOCKS part; you ignore the HTTP and the FTP. I would know; I configured Chromium to run with it using the same or similar add-on. It's slow though; for some reason Opera seems to be one of the few browsers that will allow me to browse reasonably fast with tor. 

As for the tor button business, FoxyProxy does the same thing; simply click on the big fox icon, in the window that it opens, rightclick- tor wizard.

---

### Post by nethero on 2012-01-15
> **0011235813 said:**
> Mate, I don't know why you put tor as an HTTP proxy; tor is a SOCKS proxy. If you try to open a webpage with tor as an HTTP proxy, it will not load- you will simply get an error message saying that tor is not an HTTP proxy and that it is a SOCKS proxy and that you should configure it appropriately. You just type the IP and the port in the SOCKS part; you ignore the HTTP and the FTP. I would know; I configured Chromium to run with it using the same or similar add-on. It's slow though; for some reason Opera seems to be one of the few browsers that will allow me to browse reasonably fast with tor. 

As for the tor button business, FoxyProxy does the same thing; simply click on the big fox icon, in the window that it opens, rightclick- tor wizard.

Yes, I know that Tor is a SOCKS proxy.  My question is broader than that.  I'm wondering why there is a SOCKS option in SwitchySharp.  Simply put, when does a browser need a SOCKS proxy?

---

### Post by hackertarget on 2012-01-15
You should be aware of the issue of DNS leakage when using Socks. 

Generally this is why browsing through Privoxy or another proxy is better than browsing straight through Socks 5.

DNS Leaks occur when you access a web page via Socks 5 the hostname is looked up by your computer with the dns request going over your regular Internet connection (to your ISP DNS server perhaps). The actual communication will go via Tor, but the DNS looup occurs locally.

Obviously this can have serious consequences if you are after a truly anonymous Tor prescence.

[https://trac.torproject.org/projects/tor/wiki/doc/TorFAQ](https://trac.torproject.org/projects/tor/wiki/doc/TorFAQ)

---

### Post by nethero on 2012-01-16
> **hackertarget said:**
> You should be aware of the issue of DNS leakage when using Socks. 

Generally this is why browsing through Privoxy or another proxy is better than browsing straight through Socks 5.

DNS Leaks occur when you access a web page via Socks 5 the hostname is looked up by your computer with the dns request going over your regular Internet connection (to your ISP DNS server perhaps). The actual communication will go via Tor, but the DNS looup occurs locally.

Obviously this can have serious consequences if you are after a truly anonymous Tor prescence.

[https://trac.torproject.org/projects/tor/wiki/doc/TorFAQ](https://trac.torproject.org/projects/tor/wiki/doc/TorFAQ)

Yup!  I was using Chrome and SwitchSharp to do my "anonymous" browsing.  Then I read that section about DNS leakage.  I reconfigured Privoxy to use socks4a.  Then I switched on Wireshark and used Chrome to connect to a website through my Privoxy/Tor setup.  Guess what?  Wireshark showed several DNS connections from my local computer to the DNS server.  Naturally this was a concern to me.  I thought I had Privoxy configured properly so I reread bodhi.zazen's tutorial on Privoxy to make sure I did not miss anything.  Then I tried using Firefox and tor button to connect to the same website through my Privoxy/Tor setup.  Wireshark showed NO DNS connections.  So either one of two things is happening....

#1  My Privoxy/Tor setup is not configured properly

#2 Chrome leaks DNS requests regardless of how it's configured.

I've yet to test Opera or Chromium.

---

### Post by 0011235813 on 2012-01-16
> **nethero said:**
> Yes, I know that Tor is a SOCKS proxy.  My question is broader than that.  I'm wondering why there is a SOCKS option in SwitchySharp.  Simply put, when does a browser need a SOCKS proxy?

Why does a browser need a SOCKS proxy? Hmmm... Let's see... Maybe so it can use a SOCKS-based proxy service like tor? I'm not trying to be funny here, but if a browser doesn't support SOCKS then you can't use tor. If you try and use a browser like Rekonq in Kubuntu, you will find that it does not support SOCKS. If you then try to input tor's IP address and port, into the HTTP or the FTP part, you will find that it does not work; you will simply get the error message I talked about in my last post.

PS: Chrome and Chromium are the **same thing**, Chromium is just a rebranded version of Chrome for Linux. Are you sure you're using Ubuntu?

---

### Post by emiller12345 on 2012-01-16
> **Ms. Daisy said:**
> Also, you recommend editing the repository to
```
deb http://deb.torproject.org/torproject.org lucid main
```I assume that I would change "lucid" to "oneiric" if that's what I've got installed, right?
If you don't know the name of your distribution, I believe you can use this...
```
echo "deb http://deb.torproject.org/torproject.org `grep "DISTRIB_CODENAME" /etc/lsb-release | cut -d= -f2` main" | sudo tee -a /etc/apt/sources.list
```

and it will automatically add it to the end of your sources.list file

---

### Post by nethero on 2012-01-16
> **0011235813 said:**
> Why does a browser need a SOCKS proxy? Hmmm... Let's see... Maybe so it can use a SOCKS-based proxy service like tor? I'm not trying to be funny here, but if a browser doesn't support SOCKS then you can't use tor. If you try and use a browser like Rekonq in Kubuntu, you will find that it does not support SOCKS. If you then try to input tor's IP address and port, into the HTTP or the FTP part, you will find that it does not work; you will simply get the error message I talked about in my last post.

PS: Chrome and Chromium are the **same thing**, Chromium is just a rebranded version of Chrome for Linux. Are you sure you're using Ubuntu?

Dude...   As I mentioned I have Privoxy (also playing around with Polipo) between my browser and tor.  So is specifying a SOCKS proxy necessary?  However, don't bother replying to any of my posts.  You're type of "help" I can do without.  In my original post I admited I was new to this an needed help and you go and respond like this?  Did you forget your meds or something?  Yes I know that Tor is a SOCKS proxy and yes I know Chromium is Chrome.  I only mentioned I would test Chromium because it is updated more regularly and I only asked if SwitchySharp needed a SOCKS proxy specified because it was working without one being specified.  Anyway I found the answer to my question. 

To anyone that is interested..  Chrome/SwitchySharp does not seem to require a entry in the SOCKS proxy field because in my setup I have either Privoxy or Polipo between Chrome and Tor.  All I had to do was make sure Privoxy or Poliop forwarded to TOR and then specify 127.0.0.1:8123 or 127.0.0.1:8118 in the HTTP Proxy fields and it worked.

However, this is contrary to what I experienced in Firefox.  In Firefox I had to explicitly enter 127.0.0.1:9050 in my SOCKS host fields AND enter either 127.0.0.1:8123 or 127.0.0.1:8118 in the HTTP Proxy fields (depending on which proxy I was using) or it WOULDN'T work.  Why Chrome/SwitchySharp work differently, I don't know.

---

### Post by Wayne776 on 2012-04-28
> **nethero said:**
> Yup!  I was using Chrome and SwitchSharp to do my "anonymous" browsing.  Then I read that section about DNS leakage.  I reconfigured Privoxy to use socks4a.  Then I switched on Wireshark and used Chrome to connect to a website through my Privoxy/Tor setup.  Guess what?  Wireshark showed several DNS connections from my local computer to the DNS server.  Naturally this was a concern to me.  I thought I had Privoxy configured properly so I reread bodhi.zazen's tutorial on Privoxy to make sure I did not miss anything.  Then I tried using Firefox and tor button to connect to the same website through my Privoxy/Tor setup.  Wireshark showed NO DNS connections.  So either one of two things is happening....

#1  My Privoxy/Tor setup is not configured properly

#2 Chrome leaks DNS requests regardless of how it's configured.

I've yet to test Opera or Chromium.

I am currently trying to set up TOR/Chrome/Switchysharp/privoxy and I think I found out why your DNS was leaking.....Google Chrome has DNS pre-fetching option, try disabling the DNS pre-fetching and see if that helps.:guitar:

---

### Post by ottosykora on 2012-04-29
@nethero

the best before use Tor wuld be to gather some infos from the torproject.org site.

Why? Because Tor is constantly developed and some things have changed recently.
If you install tor from the repositories of the distro, you will very likely get an outdated version of tor.

If you need tor for just surfing internet with the browser, then you will be advised by the dev of the tor not to use anything else but firefox and tor and torbutton.

Better more: use the firefox bundle, as in that all possible security measures have been installed by the tor team.

You do not need any polipo or privoxy with current version, though you may still use it if you want.

So far devs of tor were only succesful with firefox to be secure, all other browsers are not to be used with tor as too many mechanisms are present able to bypass tor.

So get the firefox-tor bundle, run the wireshark and see there.

It is possible to use tor systemwide, but the hwto in on the torproject website and it is not so simple (relative) , you will need ip tables to help divert all traffic via tor.

---

