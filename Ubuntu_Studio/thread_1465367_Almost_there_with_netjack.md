---
title: "Almost there with netjack"
date: 2010-04-29
forum: Ubuntu Studio
---

### Post by Chipp on 2010-04-29
Hey all, 

I feel I am very close to successfully using Netjack to pipe audio back and forth between a Windows 7 x64 Virtualbox guest and it's Ubuntu 10.04 amd64 host. 

Jack is installed and configured on both operating systems, bridged networking is setup and working between the hose and guest, and netjack is (mostly) working. 

I am using JackNone 0.5 on Windows, Jack 0.3.4 on Ubuntu. 

The issue I'm having is that very soon after connection between the client and server, the server gets "zombified" and dies (thus the client goes into freerun mode and dies). Here is the procedure I am following: 

Start the JACK GUI on Ubuntu, then start the JACK server from there. 

Open the Jack command prompt in Windows, and run the command:
```
jackd -R -d netone
``` 

I receive the message that Jack is starting in realtime mode, netone driver started, etc, and we wait for the server connection. 

The net connection is launched in Ubuntu with the command:

```
jack_netsource -H 169.254.xxx.xxx
```

Immediatly upon executing this, the client reports several autoconfig overrides that correspond to my server's ALSA settings, the MTU is set to 1400 bytes, and there is a netxrun for 23ms. This is all that happens before the server goes into zombie mode and the client reports the disconnect.  

I have tried taking redundancy up from the default of 1 all the way to 16, with no effect. I have tried taking the network latency   parameter from 100 to 10000 with no effect. 

Any ideas? I feel like I'm most of the way to having this work out, but there must be something funny going on with the network settings causing all the netxruns and eventual disconnect.

---

