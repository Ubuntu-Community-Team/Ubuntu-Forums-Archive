---
title: "Get compouters to boot onto Ubuntu through another computer"
date: 2008-12-27
forum: Server Platforms
---

### Post by inxygnuu on 2008-12-27
Hello, i just installed Ubuntu server 8.10 onto an old gateway, and I was wondering If I could make it so other computers on my network would boot onto this computer through the network. I know it is possible, I just need to know how to do this for a little fun.

---

### Post by pytheas22 on 2008-12-27
I think you're thinking of thin client stuff.  Check out [this page]("https://help.ubuntu.com/community/ThinClientHowto").

---

### Post by inxygnuu on 2008-12-27
Can this simply be done by selecting the boot from LAN/network option in the BIOS?

ADD ON: I found "INT18 Device (Network)" (exact wording) on one computer, will this work?

---

### Post by pytheas22 on 2008-12-28
> Can this simply be done by selecting the boot from LAN/network option in the BIOS?

Yes, that should work, provided your Ubuntu server is properly configured to allow remote clients to boot to it.

---

### Post by inxygnuu on 2008-12-28
how can I do this?

---

### Post by HermanAB on 2008-12-28
You need DHCP and tftp servers.

See this:
[http://brokestream.com/netboot.html](http://brokestream.com/netboot.html)

Cheers,

Herman

---

### Post by inxygnuu on 2008-12-28
> **HermanAB said:**
> You need DHCP and tftp servers.

See this:
[http://brokestream.com/netboot.html](http://brokestream.com/netboot.html)

Cheers,

Herman

ok, first I need to get gcc, but apot-get won't let me get gcc! When I try to run gcc, it tells me that gcc is a package, but when i run it, it says otherwise! wth?

---

### Post by pytheas22 on 2008-12-28
You can install gcc by typing:
```

sudo apt-get install build-essential
```

---

### Post by inxygnuu on 2008-12-28
OK, I know I am going to sound extremely stupid here#-o#-o:oops: but how do I connect to the Internet? I have used arch, but I have not used ubuntu like this.

---

### Post by HermanAB on 2008-12-28
You should not need GCC, since the DHCP and TFTP servers should be in Synaptic already.

To get network issues resolved, check the Network forum.

Cheers,

Herman

---

### Post by inxygnuu on 2008-12-28
Ok, I am FINALLY connected to internet. but it still wont find the packages.
is there some kind of updater available?

---

### Post by cariboo on 2008-12-28
If you are running a gui on your server open System-->Administration-->Synaptic Package Manager-->Edit-->Mark Packages by Task and select the Edubuntu Server.

If you are running on the command line, at the prompt type:

```
sudo tasksel
```

and select Edubuntu server. For more info on the Edubuntu server have a look [here.]("http://edubuntu.org/")

Jim

---

### Post by inxygnuu on 2008-12-28
> **cariboo907 said:**
> If you are running a gui on your server open System-->Administration-->Synaptic Package Manager-->Edit-->Mark Packages by Task and select the Edubuntu Server.

If you are running on the command line, at the prompt type:

```
sudo tasksel
```

and select Edubuntu server. For more info on the Edubuntu server have a look [here.]("http://edubuntu.org/")

Jim

Sorry, i don't have a GUI on it. Don't know how, this is for some fun and to learn.
and on the command line, it opens up the screen, but I can't move the selection, it only says 'Basic ubuntu Server'

---

### Post by inxygnuu on 2008-12-28
Wait, why edubuntu?

---

### Post by cariboo on 2008-12-28
Have tried the arrow and tab keys?

Jim

---

### Post by inxygnuu on 2008-12-28
Oh, tab works! thanks! now, to select ok...

---

