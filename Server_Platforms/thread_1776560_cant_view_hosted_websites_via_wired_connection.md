---
title: "cant view hosted websites via wired connection"
date: 2011-06-06
forum: Server Platforms
---

### Post by cbarron on 2011-06-06
I have an issue viewing my hosted webpages via wired connection on the same network as the server. I can view them via wireless without a problem but wired times out. I am at a complete loss as to why....any ideas?

---

### Post by arrrghhh on 2011-06-06
> **cbarron said:**
> I have an issue viewing my hosted webpages via wired connection on the same network as the server. I can view them via wireless without a problem but wired times out. I am at a complete loss as to why....any ideas?

Are you trying to hit these sites via their DNS address to your WAN IP?  Or are you trying to hit them via the local IP.

Keep in mind, if your router doesn't support it, you have to use the local IP vs the WAN IP.  My router does support it, it seems most Linksys ones do...

---

### Post by cbarron on 2011-06-06
I am trying to hit it via its url......I have a dlink dir615 with dd wrt on it.......Im still confused as to why I can hit it when im on wireless but not wired

---

### Post by arrrghhh on 2011-06-06
> **cbarron said:**
> I am trying to hit it via its url......I have a dlink dir615 with dd wrt on it.......Im still confused as to why I can hit it when im on wireless but not wired

D-Link... I think that's one of the ones that doesn't support it.

However, I have no clue why wireless it works and wired it doesn't - unless you have them in different subnets?

Either way, you didn't really answer my question - can you hit it via the LAN IP?  If that works, I'd say the WAN redirection isn't working on your router, as I stated previously.

---

### Post by cbarron on 2011-06-06
when typing the local IP I get the default "IT WORKS" page....but I do not get my index page.  Hope that answers the question. I will look into the redirection . any other ideas?

---

### Post by arrrghhh on 2011-06-06
> **cbarron said:**
> when typing the local IP I get the default "IT WORKS" page....but I do not get my index page.  Hope that answers the question. I will look into the redirection . any other ideas?

Are you typing in the full URL, or just typing in the IP?

If you don't have an index.html, you'll need more than just the IP.

---

### Post by cbarron on 2011-06-06
If I type the URL it times out after a very long time. If I type just the ip I get the default  "it works" page. I do have a index.php page but I think that Im not getting my page via ip because I am hosting more than one url on that ip.  if I type [http://192.168.2.98](http://192.168.2.98)  I get the default "it works" page. If I type [http://www.cjcomputers.net](http://www.cjcomputers.net) it times out

---

### Post by arrrghhh on 2011-06-06
> **cbarron said:**
> If I type the URL it times out after a very long time. If I type just the ip I get the default  "it works" page. I do have a index.php page but I think that Im not getting my page via ip because I am hosting more than one url on that ip.  if I type [http://192.168.2.98](http://192.168.2.98)  I get the default "it works" page. If I type [http://www.cjcomputers.net](http://www.cjcomputers.net) it times out

Are you using vhosts to redirect...?  I'm not an expert on this matter, I only have one site on my server.

If you can hit it from the outside, I'm not sure what the problem is to be honest.  It's definitely an issue with your router, no matter how you slice it.

---

### Post by cbarron on 2011-06-07
ok well the problem is solved. Thanks to some help from a friend, he figured out it was a firewall issue with my dd-wrt setup. Here is the link to the resolution:  [http://www.dd-wrt.com/phpBB2/viewtopic.php?p=529370](http://www.dd-wrt.com/phpBB2/viewtopic.php?p=529370)

Thanks for all the help

---

