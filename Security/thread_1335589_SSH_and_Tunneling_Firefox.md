---
title: "SSH and Tunneling Firefox"
date: 2009-11-23
forum: Security
---

### Post by Rayve on 2009-11-23
I finally got my SSH set up so I can use keys (have to turn off the PasswordAuth now to make sure it truly works), but my question now is how to tunnel Firefox through that connection, so my browsing is secured?

I've followed the instructions here: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=723025](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=723025) but when I set up the proxy and start Firefox, I get a proxy error and nothing loads.  Do I need to somehow open Firefox from the command line once I'm SSH'd in, or can I open it as normal on my netbook?

I'll be leaving on vacation in a week or so and would love to keep my netbook secure as I travel.  Thanks, all!

---

### Post by fargle on 2009-11-23
I'm not sure about the built-in SSH forwarding, but what I do is run TinyProxy on my home server, then tunnel to the box and forward port 8888, like so:

```
ssh <ip> -l <user> -L8888:localhost:8888
```

Then just tell the local Firefox to use localhost port 8888 as a proxy.

the [[COLOR="Blue"]Multiproxy Switch[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/7330") addon for Firefox is your friend with this to allow for convenient switching to the proxy and a nice visual indication of what you're using.

I'm pretty sure tinyproxy can be installed via a simple apt-get, and I would turn down the logging level on it so it doesn't log every URL retrieved.

---

### Post by cb951303 on 2009-11-23
you need to connect to the SSH server like this

```

ssh -D 33333 server.address

```

and then you need to set your firefox proxy to 127.0.0.1 with socks v5 on port 33333 (or any port you like)

note that the SSH server you're connected needs to have tunneling enabled or it won't work.

cheers

---

