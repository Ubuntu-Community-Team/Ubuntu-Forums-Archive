---
title: "[SOLVED] Tor+Privoxy Showing Up But Not Working"
date: 2008-03-17
forum: Security Discussions
---

### Post by randy78 on 2008-03-17
Hello all

I have added the Tor repos, downloaded and installed both Tor and Privoxy, as well as set up Vidalia...

I had this setup before I re-installed and now I can't seem to get it working properly for the life of me.

I have followed several guides, added what needed to be added, commented out what needed commented out and have even set Vidalia to not start Tor when it starts.

Everything is running and the Tor and Privoxy processes even show up in System Manager, but when I try to route Opera or Firefox through them (ports 8118 and 9050, respectively), I end up with just my regular old internet connection, instead of a proxy!

I am assuming that it has something to do with group permissions and I have added myself to the debian-tor group and have tried also adding myself to the Tor group (Unsuccessfully).

Any info on how to get this running would be greatly appreciated!

Thanx ;)

---

### Post by p_quarles on 2008-03-17
Without knowing what specific steps you followed, it would be difficult to say why it's not working as intended. Links or a more thorough description would help people help you.

---

### Post by FakeOutdoorsman on 2008-03-17
Did you try these instrucitons?
[Running the Tor client on Linux/BSD/Unix]("http://www.torproject.org/docs/tor-doc-unix.html.en") [torproject.org]

---

### Post by randy78 on 2008-03-17
> **FakeOutdoorsman said:**
> Did you try these instrucitons?
[Running the Tor client on Linux/BSD/Unix]("http://www.torproject.org/docs/tor-doc-unix.html.en") [torproject.org]

I tried those instructions,  these: [http://ubuntu-tutorials.com/2006/11/02/how-to-install-tor-privoxy-kubuntu-606-610/](http://ubuntu-tutorials.com/2006/11/02/how-to-install-tor-privoxy-kubuntu-606-610/)

These:
[http://blog.mypapit.net/2007/06/how-to-setup-tor-and-privoxy-in-ubuntu-feisty-fawn.html](http://blog.mypapit.net/2007/06/how-to-setup-tor-and-privoxy-in-ubuntu-feisty-fawn.html)

These:
[http://blog.aizatto.com/2006/09/01/protecting-your-privacy-setting-up-tor-in-ubuntu-dapper-drake/](http://blog.aizatto.com/2006/09/01/protecting-your-privacy-setting-up-tor-in-ubuntu-dapper-drake/)

These:
[http://corvillus.com/2006/09/18/how-to-set-up-tor-and-privoxy-on-ubuntu-linux/](http://corvillus.com/2006/09/18/how-to-set-up-tor-and-privoxy-on-ubuntu-linux/)

and many more like those...

Everything works and the Network Map comes up in Vidalia with connections and whatnot, but nothing will work using the proxy.

When I enable Opera to use Proxy servers, it just uses my regular internet connection, as if I never configured it to use the proxy servers...

Firefox is the same, with and without TorButton.

I figured out why the processes weren't being displayed in System Monitor, and that was because I had to enable View All Processes...

Thanks all :)

---

### Post by randy78 on 2008-03-17
Okay!

I ended up just using the sample config file on the tor site located here:
[https://wiki.torproject.org/noreply/TheOnionRouter/PrivoxyConfig](https://wiki.torproject.org/noreply/TheOnionRouter/PrivoxyConfig)

Thanks to all!

---

