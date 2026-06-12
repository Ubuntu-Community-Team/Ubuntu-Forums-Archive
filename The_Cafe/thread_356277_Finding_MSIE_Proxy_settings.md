---
title: "Finding MSIE Proxy settings"
date: 2007-02-08
forum: The Cafe
---

### Post by v8YKxgHe on 2007-02-08
Hey,

At college, MSIE connects to a proxy server first which we can't get the details of (as Tools->Internet Options is restricted). A couple of my mates have laptops which they want to connect to the internet but can't because we don't know the proxy settings. 

Is there anyway of finding out what the proxy settings are, so we can configure them on the laptop? 

Regards,

---

### Post by doobit on 2007-02-08
> **AlexC_ said:**
> Hey,

At college, MSIE connects to a proxy server first which we can't get the details of (as Tools->Internet Options is restricted). A couple of my mates have laptops which they want to connect to the internet but can't because we don't know the proxy settings. 

Is there anyway of finding out what the proxy settings are, so we can configure them on the laptop? 

Regards,

1.Ask your network administrator.
2.Use a different browser, since you can probably bypass the proxy that way.

---

### Post by v8YKxgHe on 2007-02-08
> **doobit said:**
> 1.Ask your network administrator.
2.Use a different browser, since you can probably bypass the proxy that way.

We asked the network admin, but his reply was a very stuborn "In a word...NO!". Both of the laptops are using Firefox (one is a Macbook and the other has Ubuntu on it)

I've actually found in the log files ( C:\Document and Settings\Username\Application Data\Microsoft\Internet Explorer\brndlog.txt) that shows it adding the proxy server with all address and ports, but when we changed the settings in Firefox it was able to connect but was refused. Is this becuase they only allow a certain mac-address to connect?

---

### Post by koenn on 2007-02-08
They might be in the windows registry, maybe somewhere near
CurrentUser ... Software ... Microsoft ... Internet Exxplorer  or so

(can't check, no WIndows Machines in the vicinity)

---

### Post by koenn on 2007-02-08
> but when we changed the settings in Firefox it was able to connect but was refused. Is this becuase they only allow a certain mac-address to connect?
could also be an authentication problem : maybe the user accounts on your ubuntu /Mac are not allowed to use the proxy

---

### Post by v8YKxgHe on 2007-02-09
maybe if we make a user with our normal college username, and spoof the mac address it could work? I'm gonna try it today and see if it works, I will be the end of the year find a way how to get on the internet with them! :)

---

