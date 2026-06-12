---
title: "Tails Linux version 0.16 - Firewall Disabling Script Waits For Exploitation"
date: 2013-01-21
forum: Security
---

### Post by purplepotion on 2013-01-21
Tails Linux version 0.16 - Firewall Disabling Script Waits For Exploitation 

If you’re running Tails version 0.15 or 0.16, please locate and delete the following file each session: 

/usr/local/sbin/do_not_ever_run_me 

The file, if ran with correct permissions, will completely disable your firewall! So much for the idea that Tails always routes everything through Tor! Where this news has been posted and comments allowed, mysterious “anonymous” users have expressed their low brow intelligence leaving comments such as, “Well you need to be root to run it so it doesn’t matter, if you have root you can do anything!” 

First of all, a file called “do_not_ever_run_me” shouldn’t be on a Linux system. If it should NEVER BE RUN, and that means by anyone, root or user, local or remote, it SHOULD NOT BE INCLUDED IN THE DISTRIBUTION! 

Any current or future exploit which targets this file will “drop the shields” for the Tails user. 

Perhaps Tails itself in its next version, 0.17, should be nicknamed, “do_not_ever_run_me”. 

Another questionable decision by the Tails developers is to place the following line within the torrc file (located at /etc/tor/torrc): 

## We don’t care if applications do their own DNS lookups since our Tor ## enforcement will handle it safely. WarnUnsafeSocks 0 

Oh, really? We don’t care? Who is we? It’s not me! As the man page for Tor states, this is set to 1 by default, yet Tails sets it for 0! So if something “leaks”, you will never know it? Each session, delete this line or comment it out so the default is 1 like it should be for a Tor session. 

What else can we find in this anonymously developed distribution? I’m glad I’m not driving a car with software made by this group of developers.

---

### Post by purplepotion on 2013-01-21
[http://cryptome.org/2013/01/tails-exploit.htm](http://cryptome.org/2013/01/tails-exploit.htm) 

slammin'!

---

