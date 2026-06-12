---
title: "Configure Apt-Cacher with building proxy already in place"
date: 2008-07-25
forum: Server Platforms
---

### Post by nbotticelli on 2008-07-25
Ok, I'm running a summer tech camp up here in Vermont teaching kids how to rebuild (frankenstein) old computers and also to build brand new barebones kits and loading them up with Edubuntu.

This means many computers all needing updates and various software etc.

During the first camp I was in a building where we also had a cable modem connection that was completely separate from our normal heavily proxied/filtered connection (required by feds) so it was very simple to set up a small apt-cacher server that the client machines could connect to to download updates etc...

Now I'm doing another camp here in my other school but we only have the heavily filtered/proxy network here and no other separate fast connection to the outside world...

Now, I thought this wouldn't be much of a problem since the past two weeks of the old camp we downloaded so many updates and various programs that I thought the apt-cacher server would already have pretty much everything we'd need and that even if we couldn't get synaptic to pull files from the outside world repositories that it wouldn't be a problem.

Here's what I'm running into though:

I can set the clients to pull updates from the apt-cacher but when I try to pull anything it just fails after a long while....can't connect to anything.....When I go into the synaptic package manager I can set the school proxy settings there and then when I go to update it'll just pull them straight down from the internet and override the apt-cacher server....Unfortunately our school filtering software is a bear and I don't have any control over it plus the actual server is located in a different building several miles from here and the downloads are way way way slow....worse than dial up for some reason on the ubuntu repositories....

Now, is there anyway to get the clients to still be able to pull updates/files from the apt-cacher server? Seems like if I don't have the school proxy put in it just won't do anything....

Also, I took a network cable from my classroom wall and hooked in a small router connected to a switch so that I would have my own little lan/network/server separate from the school network....


Any ideas?

This is really putting a huge hamper on everything that I'm trying to do in my camp here...

Thanks in advance!

---

### Post by songshu on 2008-07-26
hard to give any advice when not knowing exactly how the gestapo network you are on is configured.

but i think it would be solved when using the apt-cacher on your local LAN.

why can't you access the remote apt-cacher?
apt-cacher listens on port 3142 by default and i guess that that port is being blocked by the network firewall somewhere, probably forcing you to use the on site proxy. If you can access the apt-cacher config and set it up to listen on port 80 you should be fine to reach it through the proxy.

but above is just an assumption.

what do you have in your /etc/apt/sources.list  ?

---

