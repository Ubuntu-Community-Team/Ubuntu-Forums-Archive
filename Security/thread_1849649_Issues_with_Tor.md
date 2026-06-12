---
title: "Issues with Tor"
date: 2011-09-24
forum: Security
---

### Post by DevinJCan on 2011-09-24
Hello everyone,
I am attempting to set up Tor with relaying on my PC and I am having some issues with the initial config. Ubuntu 10.04 natty. I have Vadalia associated. This is the message log from Tor: 
> 
Sep 24 22:07:39.458 [Notice] Tor v0.2.2.33 (git-56122e2e9be4c477). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
[LEFT]Sep 24 22:07:39.458 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Sep 24 22:07:39.458 [Notice] Opening Socks listener on 127.0.0.1:9050
Sep 24 22:07:39.458 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Sep 24 22:07:39.458 [Notice] Opening Control listener on 127.0.0.1:9051
Sep 24 22:07:39.458 [Notice] Closing partially-constructed listener Control listener on 127.0.0.1:9051
Sep 24 22:07:39.458 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Sep 24 22:07:39.458 [Error] Reading config failed--see warnings above.
Sep 24 22:08:27.834 [Notice] Tor v0.2.2.33 (git-56122e2e9be4c477). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Sep 24 22:08:27.835 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Sep 24 22:08:27.835 [Notice] Opening Socks listener on 127.0.0.1:9050
Sep 24 22:08:27.835 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Sep 24 22:08:27.835 [Notice] Opening Control listener on 127.0.0.1:9051
Sep 24 22:08:27.835 [Notice] Closing partially-constructed listener Control listener on 127.0.0.1:9051
Sep 24 22:08:27.836 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Sep 24 22:08:27.836 [Error] Reading config failed--see warnings above.
Sep 24 22:09:29.302 [Notice] Tor v0.2.2.33 (git-56122e2e9be4c477). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Sep 24 22:09:29.302 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Sep 24 22:09:29.302 [Notice] Opening Socks listener on 127.0.0.1:9050
Sep 24 22:09:29.302 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Sep 24 22:09:29.302 [Notice] Opening Control listener on 127.0.0.1:9051
Sep 24 22:09:29.302 [Notice] Closing partially-constructed listener Control listener on 127.0.0.1:9051
Sep 24 22:09:29.303 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Sep 24 22:09:29.303 [Error] Reading config failed--see warnings above.
Sep 24 22:11:36.144 [Notice] Tor v0.2.2.33 (git-56122e2e9be4c477). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Sep 24 22:11:36.144 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Sep 24 22:11:36.144 [Notice] Opening Socks listener on 127.0.0.1:9050
Sep 24 22:11:36.144 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Sep 24 22:11:36.144 [Notice] Opening Control listener on 127.0.0.1:9051
Sep 24 22:11:36.144 [Notice] Closing partially-constructed listener Control listener on 127.0.0.1:9051
Sep 24 22:11:36.144 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Sep 24 22:11:36.144 [Error] Reading config failed--see warnings above.
Sep 24 22:15:37.384 [Notice] Tor v0.2.2.33 (git-56122e2e9be4c477). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Sep 24 22:15:37.385 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Sep 24 22:15:37.385 [Notice] Opening Socks listener on 127.0.0.1:9050
Sep 24 22:15:37.385 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Sep 24 22:15:37.385 [Notice] Opening Control listener on 127.0.0.1:9051
Sep 24 22:15:37.385 [Notice] Closing partially-constructed listener Control listener on 127.0.0.1:9051
Sep 24 22:15:37.385 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Sep 24 22:15:37.385 [Error] Reading config failed--see warnings above.
[/LEFT]


---

### Post by Dangertux on 2011-09-24
It seems as if you have two verions of Tor running or something else running on port 9050, and 9051.

Can you post the results of 

```

sudo netstat -anlp | grep :9050

```

---

### Post by DevinJCan on 2011-09-24
Here it is:
> djc@djc-M4:~$ sudo netstat -anlp | grep :9050
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN      1320/tor The port number in the socket is red.

---

### Post by Dangertux on 2011-09-24
The port number is red because grep highlighted it.

Perhaps you have two upstart jobs for Tor? Did you try to install it multiple times? Also : is Tor functional regardless of the error?

The second error is about reading the config, is your Tor configuration file correct? If you're not sure you can post it.

---

### Post by DevinJCan on 2011-09-24
I may have installed twice. I've had the Vidalia say that tor was running only once but Firefox was not working with the tor-button extension (Firefox is configured to use a proxy server that is refusing connections.) and I restarted and Vidalia is not working.

Here is the tor-tsocks.conf:
> # This is the configuration for libtsocks (transparent socks) for use
# with tor, which is providing a socks server on port 9050 by default.
#
# See tsocks.conf(5) and torify(1) manpages.

server = 127.0.0.1
server_port = 9050

# We specify local as 127.0.0.0 - 127.191.255.255 because the
# Tor MAPADDRESS virtual IP range is the rest of net 127.
local = 127.0.0.0/255.128.0.0
local = 127.128.0.0/255.192.0.0


---

### Post by Dangertux on 2011-09-24
Well, at this point unless someone else has another idea, I would think the easiest way would be completely removing tor and reinstalling it. 

If you installed it from repos you can do the following

```

sudo apt-get remove --purge tor

```

Also : I am fairly sure Vidalia installs tor, so you may have doubled up because of that. I would try using only one or the other and see if that works.

---

### Post by DevinJCan on 2011-09-24
I purged and re-installed Tor. 
Unexpected error message reads:
> Vidalia detected that the Tor software exited unexpectedly. Please check the message log for recent warning or error message.Log:
> Sep 24 23:12:36.056 [Notice] Tor v0.2.2.33 (git-56122e2e9be4c477). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Sep 24 23:12:36.056 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Sep 24 23:12:36.056 [Notice] Opening Socks listener on 127.0.0.1:9050
Sep 24 23:12:36.056 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Sep 24 23:12:36.056 [Notice] Opening Control listener on 127.0.0.1:9051
Sep 24 23:12:36.056 [Notice] Closing partially-constructed listener Control listener on 127.0.0.1:9051
Sep 24 23:12:36.056 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Sep 24 23:12:36.056 [Error] Reading config failed--see warnings above.This "Failed to bind one of the listener ports." seems important. so I goggled it and came up with this: [http://ubuntuforums.org/archive/index.php/t-1255475.html](http://ubuntuforums.org/archive/index.php/t-1255475.html)

I installed  privoxy and Tor is now running with Vidalia. Its funny because this is the first place that has mentioned privoxy.

Making progress. I will mark this post solved once I am sure that Tor is configured and running properly. Thanks for your time.

**UPDATE:** I restarted Firefox. When I toggle the Torbutton I can now navigate to a website and upon testing settings under Torbutton preferences : "Tor proxy test FAILED! Check your proxy and Polipo settings." 

Also. I restarted my PC and was unable to get Tor to start until I ran "sudo killall tor" and restarted Vidalia. Now Vidalia is telling me that I am "Connected to the Tor network!" 

The Torbutton Test Settings is says "Tor proxy test: Local HTTP Proxy is unreachable. Is Polipo running properly?"

what is really going on here?

---

### Post by Dangertux on 2011-09-24
The tor project moved away from privoxy and to polipo. Update your torbutton settings manually to point them at the privoxy port instead of the polipo port which is what tor button is looking for. 

Glad it seems to have worked out

---

