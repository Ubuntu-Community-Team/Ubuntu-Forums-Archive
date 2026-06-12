---
title: "Tor Help"
date: 2009-06-10
forum: Security
---

### Post by ki4jgt on 2009-06-10
Okay just setup tor repositories, then did Sudo apt-get install tor. Now when I use my wifi, firestarter recognizes tor as a running connection to the internet. I installed tor button, but when I go to Firefox and try to check my ip address on a site, it tells me the same ip address as when I have torbutton turned off!
Further question about the security of Tor, is it a good encryption service to use at a public wifi terminal, or am I missing the point all together?
Thanks in advanced.

---

### Post by cdenley on 2009-06-10
> **ki4jgt said:**
> Okay just setup tor repositories, then did Sudo apt-get install tor. Now when I use my wifi, firestarter recognizes tor as a running connection to the internet. I installed tor button, but when I go to Firefox and try to check my ip address on a site, it tells me the same ip address as when I have torbutton turned off!
Further question about the security of Tor, is it a good encryption service to use at a public wifi terminal, or am I missing the point all together?
Thanks in advanced.

I believe torbutton uses privoxy, which it assumes is configured to then use tor.

I think tor just gives you a false sense of security. It prevents somebody near your wifi terminal from intercepting your traffic, but whoever happens to be running your tor exit node can intercept it much more easily. The only real benefit of tor is that the servers you are connecting to cannot determine your IP address, since it receives all traffic from the tor exit node. You still have to protect any data you are sending in the usual ways.

What are the "tor repositories"?

---

### Post by rookcifer on 2009-06-10
> **ki4jgt said:**
> Okay just setup tor repositories, then did Sudo apt-get install tor. Now when I use my wifi, firestarter recognizes tor as a running connection to the internet. I installed tor button, but when I go to Firefox and try to check my ip address on a site, it tells me the same ip address as when I have torbutton turned off!
Further question about the security of Tor, is it a good encryption service to use at a public wifi terminal, or am I missing the point all together?
Thanks in advanced.

Follow [this tutorial]("http://www.torproject.org/docs/tor-doc-unix.html.en") on the tor website for getting it running in Linux.  It has always worked for me.  As the guy above said, you need Privoxy installed and you also need to tweak the tor config files, as outlined in the above link.

Tor encrypts your data through each node.  The default number of nodes used is 3, I believe.  So, in order for your IP address to be compromised it would take 3 malicious nodes working together to achieve it, but this is unlikely because Tor constantly randomizes which nodes you connect to.  As was said above, the only node which can see your data is the exit node, but the exit node cannot see your IP.  So, basically, Tor will guarantee anonymity but your privacy is broken at the last node in the chain.  The exit node can see what you're doing but it can't see who you are.

---

### Post by Agent ME on 2009-06-10
If you're using Tor, try to use HTTPS websites, just as if you were using an insecure wifi.

I don't really recommend using the tor package that comes in the repositories. It is set to run at all times, which may be good for some systems, but for laptops that have wireless that may change networks at times this isn't so great as Tor doesn't seem to always reconnect on its own.

Instead try following step one from the [mentioned page](http://www.torproject.org/docs/tor-doc-unix.html.en) to install Tor from source. (Privoxy in step 2 isn't really required, but you can still choose to use it.) Also, install [vidalia](http://www.torproject.org/vidalia/index.html.en) - it's the GUI for launching and controlling Tor, and having quick access to its settings. After you do that, it will show up in Applications -> Internet.

---

### Post by ki4jgt on 2009-06-11
Tor repositories are the download repositories listed on the tor website. you just add them to your software sources, and the key. and then you have the latest version of tor without have to wait for someone to write it into Ubuntu's repositories. All this can be found here: [https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian]("https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian") as to the effectiveness of this, b/c it was written as a debian tutorial, I don't know if it would cover Ubuntu w/o some major configuration or not, that's why I posted here b/c I don't know much about it. [for the guy who ask about the repositories]

and 

[To the rest of you]
Sorry, but tor is just too complicated for a newbie like me, maybe in a couple of years, who knows, that's how I figured out windows, I had several crash and burns, then I got tired of having 100-300 viruses every time I wanted to attempt something new that it just got old. I've bought a VPN service. My only problem is, the openvpn package isn't reading the config file they gave me, so I have to go with the less secure PPTP connection. I've tried setting up the VPN based on how the settings were written in the config file, but no luck. Anyone that knows how to convert a .ovpn file to one the works with Ubuntu's openvpn connections, please pm me or add a response either one, please and thank you!

---

