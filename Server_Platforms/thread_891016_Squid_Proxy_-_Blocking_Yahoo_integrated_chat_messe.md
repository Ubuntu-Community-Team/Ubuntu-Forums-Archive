---
title: "Squid Proxy - Blocking Yahoo integrated chat messenger"
date: 2008-08-15
forum: Server Platforms
---

### Post by whitegourd on 2008-08-15
I'm trying to block the use of the integrated chat client within Yahoo mail (webmessenger).  The client systems at my work place are accessing the Internet through the proxy server (Squid) where squidGuard utilizes the Shallalist blacklists.

I enabled the chat category in the blacklists, and tested this with Googles integrated chat client.  This was pretty easy to block because the url "http://chatenabled.mail.google.com" is denied.

I have yet to find a way to keep users from accessing Yahoo's web client (even when webmessenger.yahoo.com is being blocked).  I've done quite a bit of searching on the Internet and they suggested to also block "httpcs.msg.yahoo.com".  This still doesn't prevent users from accessing yahoo web chat.

I also tried adding the acl's in squid.conf to deny the ports 5100, etc. but that didn't seem to help.  Is there a url that I can add to my blacklist that will prevent access to Yahoo's web messenger?  Preferably through the blacklisting the sites that the web messenger tries to connect to?  I'd like to avoid having to add it to the iptables if at all possible.

---

### Post by promodus on 2008-08-15
add the hostname of that server to your hosts file with the localhost address.

Example:

/etc/hosts
```

127.0.0.1	chatenabled.mail.google.com
```
Is one way to do it.

You can also null route the IP.
```
route add -host 209.85.201.189/32 gw 127.0.0.1 metric 0 dev lo
```
That will guarantee nothing goes to that IP address. You will need to save that within your firewall rules...

Just keep in mind that if you use the hosts file, that when people access the said webpage, they'll get the default webserver on that machine... This can be convenient to say "this page has been blocked" or what ever you decide.

---

### Post by whitegourd on 2008-08-16
Well, I currently have outgoing port 5050 blocked on the firewall which stop any attempts to log into Yahoo's chat messenger.

The Google chat isn't the one I'm having trouble blocking, it is the Yahoo Messenger one that is giving me some trouble.

I have yet to find the correct url or IP to block Yahoo's Messenger since there are many multiple ones, and the ones that they do mention, doesn't seem to work.

webcs###.msg.yahoo.com
httpcs.msg.yahoo.com
webcs.msg.yahoo.com
msg.yahoo.com

So far it doesn't seem that Squid/SquidGuard is able to stop/redirect these connections.  Has anyone been successful in blocking Yahoo Webchat Messenger in Yahoo Mail?  I'd sure like to know how you got it to work if you did.

---

