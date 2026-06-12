---
title: "Trying to host my own WordPress Blog..."
date: 2011-05-16
forum: Server Platforms
---

### Post by Vanillalite on 2011-05-16
PREFACE: I'm new at this so bare with me everyone!

So I have a spare computer to which I installed Ubuntu Server 11.04 as well as the LAMP stack since it said I could do that during the install. Finished the install, and everything booted up fine and such.

Only other thing I've done is the 

```
sudo apt-get install wordpress
```

Outside of this I'm sort of at a loss on where to go. Do I need to buy a domain name from a host? How do I connect wordpress to the LAMP stack? I'm thinking I need to make this computer have a static IP on my network? Can I do that and keep the others DHCP? What else?

I'm partly doing this because I'd like to host my own blog, and partly as a learning experience on just how to go about setting something like this up. Thanks for any help in advance!

---

### Post by CharlesA on 2011-05-16
Wordpress is fairly easy to install.

I used the page [here]("http://codex.wordpress.org/Installing_WordPress") when I messed around with it on a test server.

If you want to have it accessible from the internet, you'd have to buy a domain name, and either get hosting somewhere, or see if your ISP allows servers to be run on your connection (most residential ISPs block ports and have it written into the TOU that you aren't allowed to run servers).

You don't need to do anything to "attach" Wordpress to the LAMP stack, if you follow the install instructions, you'll be able to access the blog with no problems.

---

