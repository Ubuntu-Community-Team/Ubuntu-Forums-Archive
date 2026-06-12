---
title: "BIND not resolving client requests"
date: 2008-12-15
forum: Server Platforms
---

### Post by NetworkGuy on 2008-12-15
I have brought up a DNS master and two slaves.   I am having issues with the servers performing lookups for URL's that are non-authorative for them.  

If the client requests www.<mycompany>.com then it will return the correct address, but the same client requesting [www.cnn.com](www.cnn.com) gets denied.   

This occurs with or without the UFW turned on.  

Any ideas?

---

### Post by cdenley on 2008-12-15
Did you configure a "forwarders" section?
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

---

### Post by NetworkGuy on 2008-12-16
Forwarders are not enabled.  Shouldn't need them with the root servers specified.

I found the answer I was looking for after a lot of experimentation.

While recursion is turned on by default, the only addresses allowed to use the function by default are machines within the same subnet of the DNS server.  If you have a client on a different subnet than the server, attempting a lookup for a public URL other than what it is authoritive for will fail.   The answer is to add the line in the options file

> allow-recursion {any;};

Since every install is different, you need to decide if this is a good thing or not.  You can adjust the option to only allow machines you are responsible for to use this or as above you can allow anybody that can see your server to use it for DNS resolution.

---

