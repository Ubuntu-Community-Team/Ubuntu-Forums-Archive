---
title: "ssh servers"
date: 2010-11-05
forum: Server Platforms
---

### Post by bouncingwilf on 2010-11-05
Apologies in advance for the very basic questions I have but I'd rather get this right before I start opening up ports through my router's firewall!

Basically, as I stated in a general post last week, I hope to be able to do some remote maintenance on a boat computer and to that end I've been reading the various posts and guides on the subject of ssh and ssh security.  I've set up 2 PCs , one as a server, one as a client (both behind my router firewall) ; modified the sshd_config files as recommended and generated the appropriate public and private keys. Now here's the bit I've not quite got right - I can't test the system because neither machine can "see" the other. One has a local address of 192.168.1.65 and the other 192.168.1.69 but I can't even ping one from the other although both have Internet access through the router. I'm sure the answer is embarrassingly simple as to how I can ssh between these two machines but for the life of me. I can't see it. As I said before, I'd sooner ask than to expose PC ports to the big bad world. Once I get over this hurdle, I should be able to "test" the system and work the rest of it out.

Bouncingwilf

---

### Post by HermanAB on 2010-11-05
Howdy, 

You need to forward port 22/TCP in the router to the machine behind it.  If it is a dinky little home router, then you can easily do it in the router control panel.

---

### Post by bouncingwilf on 2010-11-05
This what I suspected i.e. allow port forwarding on my dinky router (know how to do that) and then open port 22 (or whatever I specified in sshd_config) on the server. But is there no way that two IP devices, both the same side of the router can see each other or does all traffic have to go through the "internet" side of the router? I realise I'm being thick here but I was hoping to test everything before opening up port 22 to the outside world.


Bouncingwilf

---

### Post by tgm4883 on 2010-11-05
If they are on the same local network you don't need to open ports in the firewall. Can you ping the other machine? I've seen on some routers a wireless privacy mode (or something to that effect), basically what it does is not allow each wireless device to see anyone else on the network. You may want to check that.

---

### Post by bouncingwilf on 2010-11-05
Ah! now that makes sense - Instinctively I felt that as they're all on the same local net inside the router/firewall boundary they should be able to ping each other ( that's how it used to happen 25 years ago when my brain hadn't atrophied) I'll check the wireless privacy mode thing out as both machine are using wlan connections. - Many thanks.

Bouncingwilf

---

### Post by HermanAB on 2010-11-05
Howdy,

You can debug LAN network trouble using telnet:
$ telnet other.host.ip.address 22

You should get a prompt from the other machine SSH server.

Once you get a prompt, run ssh with debug messages enabled:
$ ssh -vvv [email]username@other.host.ip.addres[/email]s

---

