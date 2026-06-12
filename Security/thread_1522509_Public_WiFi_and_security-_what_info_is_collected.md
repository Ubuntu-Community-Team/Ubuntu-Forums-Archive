---
title: "Public WiFi and security- what info is collected?"
date: 2010-07-02
forum: Security
---

### Post by PDA1 on 2010-07-02
When you connect to a free wifi hotspot what sort of information about my computer is gathered by the service?

I assume they collect some sort of identifying information which is specific to my machine and record everything I type.  Is it something like that?

Maybe hard drive serial number?

---

### Post by flick on 2010-07-02
Anything not encrypted can be seen/read by anyone who has a wireless card in promiscuous mode running something like wireshark.

Best advice is to limit public wifi browsing to casual stuff : news sites, blog reading, etc. Save online banking and such for at home on a wired connection.

---

### Post by PDA1 on 2010-07-02
I've read that some people use TOR in public.    Would that be much safer?

---

### Post by cdenley on 2010-07-02
With public wifi, any data you send or receive can be easily intercepted. However, anytime you use the internet, you should assume this is a possibility, since you never know how your traffic will reach its destination, or who may gain access to your data along the way. Never send any sensitive data across the internet unless it is encrypted. When browsing an encrypted page, make sure you don't get any warnings about the SSL certificate the server is using.

Nobody is going to be able to get any information from your system over the network (except maybe about your network interface) unless you run software which reveals that information. Your web browser will reveal what browser and version you are using, as well as your OS. Nothing should reveal your hard drive serial number, though, and certainly not your keystrokes.

Tor would prevent anyone who intercepts your wifi traffic from being able to read it, but that just shifts the threat somewhere else. When using tor, whoever has access to the exit node you happen to be using at the time has easy access to all your traffic unencrypted. Between the exit node and the server you are communicating with, it is still just as insecure as if you were not using tor. The only benefit is that anyone who can read your traffic shouldn't know your IP address.

---

