---
title: "Apache Virtual Host Warning"
date: 2007-09-27
forum: Server Platforms
---

### Post by samona on 2007-09-27
Can someone please help me with this error i'm getting.  I am trying to run three websites on my computer.  Website A, Website B, and Website apache2-default.  When I had only 2 websites running it worked ok.  Now that I added the third one (B) I get the following error:

```
VirtualHost A:0 overlaps with VirtualHost B:0, the first has precedence, perhaps you need a NameVirtualHost directive
  
```

In my hosts file I have
```

127.0.0.1	localhost
127.0.1.1	A
127.0.1.1	B
```

The problem is that when I type B in the browser it takes me to website A.  I don't want that.  I think it might be because the IP (127.0.1.1) is used for both websites.  Could that be the issue?  any help will be greatly appreciated.  Thanks!

---

### Post by wirelessmonkey on 2007-09-27
The problem is that your machine Cannot tell the difference between A and B, as they both resolve to the exact same address, the first in the list has priority.

In order to use B, you should give it a unique address.

Edit your hosts file to look like:
127.0.0.1     localhost
127.0.1.1     A
127.0.1.2     B


or instead of 127.0.1.2, you could use:

::1

Those are colons before the 1.

Best of Luck

---

### Post by samona on 2007-09-27
thank you very much, that worked.  That leads me to ask another question if you don't mind.

I thought for Virtual Hosts, you can use one ip address and the server will be able to differentiate based on the domain name.  In my case, I am using 3 different IP addresses.  Why is that the case?

---

### Post by wirelessmonkey on 2007-09-28
Virtual Hosts are, in your case, designated by domain name or port number. Creating an item in etc/hosts allows your system to lookup actual network host names.

So... Doing what you did made your **system** look for a network alias to B on your machine.  
Creating a virtual host would make **apache** look for a /B virtual host name.

I hope that makes sense, it's late here and I make no guarantees ;)

---

### Post by samona on 2007-09-28
i'm not sure what you mean.  In my configuration file for each host domain it is like the following:

```
<VirtualHost a>
....
</VirtualHost>
```

The next configuration file

```
<VirtualHost b>
....
</VirtualHost>
```
The last is :
```
<VirtualHost *>
...
</VirtualHost>
```

These 3 files are in the sites-enabled and sites-available.  I put them in my /etc/hosts file so that the computer doesn't look on the internet for them.  But I figured I can use one ip address (127.0.0.1) and it wouldn't matter because I will be able to access each site by just using the name.  In my case we set 3 different IP addresses for each site and I don't know why we had to do that since im doing virtual hosting.  I hope i make sense.  And thanks for taking the time for me, I appreciate it.

---

### Post by fatbastard spice on 2007-09-30
Resolving to the same ip address doesn't matter for apache if you're using named virtual hosts. Apache looks for the dns name in the browser header and then serves up the appropriate virtual host. Can't tell from your samples, but is there at least one NameVirtualHost * directive in your config files? I generally chuck it in the first site config that is enabled, but it could be anywhere in the config file chain before apache hits the VirtualHost directives.

---

### Post by samona on 2007-09-30
oh ok, i got you. Thanks!!!!!!

---

