---
title: "Suggesting a P2P mobile communications protocol"
date: 2012-07-09
forum: The Cafe
---

### Post by ki4jgt on 2012-07-09
Hi guys,

First things first, this is a brainstorm ONLY. You are free to make suggestions (good or bad). I have not made any plans to impliment this at all so have fun with it. The idea just popped into my head and I though, hey who better to work on something FREE for everyone than the open source community? You will also notice that there is no monitary gain for anyone in this protocol (except manufacturers who choose to use it). It's merely an idea. If you find vulnerabilities please try and help come up with a way to fix them (if you enjoy the idea that is). What is life without a little creative thinking? This is all in the spirit of furthering technology.

In the USA we have what is called the ISM band or now it's bands. Basically it's a frequency range between 902Mhz and 928Mhz. Which is open for everyone to use and expiriment as long as the transmition is below 1 watt (except for ham radio operators which isn't relavent to this post). I've found modems which can go up to 40 miles using this 1 watt limit at pretty good speeds.

Now that we have the introduction out of the way let's get down to protocol. In the amateur radio community we have digital modes which can scan an entire frequency spectrum at once looking for data. Using a USB dongle which is capable of both scanning 902-928 and transmitting on a select frequency within that range, the Internet, and gpg encryption, I believe it may be possible to impliment an entire P2P messaging system capable of handling voice or at least text. Again, just an idea. If you have problems with it make suggestions :)

Each node is continually scanning the entire frequency spectrum for the initial phrase "[P900]". Each node has a gpg key pair. The public key is hashed of which the first 14 characters will be the individual's Personal Access Sequence (PAS). EVERY transmition the node makes will be stamped with the ititial phrase and this PAS. This is how messages get around within the network.

When a node wishes to join the network, it sends out a request for other nodes which are receiving it at a certain signal strength. So calling all nodes hearing me at 90%. If nothing is heard it will call for nodes hearing at 80. The node will keep going down until it get's three other access nodes. Network strength will be a mean value of all three other nodes. Each node will routinely send out a signed statement of what nodes connect it to the network IE. node_PAS@connection1_PAS, node_PAS@connection2_PAS, node_PAS@connection3_PAS. Nodes connected to the Internet (known as Tunnels) send out node_PAS@nodes_IP-ADDRESS to all other clients it's connected to online.

Each node will have a software application which is capable of being in 2 states (Relay and Tunnel).

Relays are normal nodes. They simply receive and pass trafic within the 900Mhz band. Relays attempt to get all network communications (which are connected to them) to a Tunnel. Each Relay (including tunnels) keeps a 36 kb database (in RAM) of all @ messages it sees across the spectrum (including ones which it is not connected to).

Tunnels however (along with acting as a relay) connect to and form a P2P distributed database of locations for all of the PAS in the network through the Internet. Once it receives a message for PAS XYZ, it forms a path to send the message along by saying XYZ is @ PAL, PAL is @ MAT, MAT is @ 148.24.23.1 any @ the tunnel cant find, it will request through the P2P database.

Finally to the good stuff. Each sent message is signed and possibly encrypted (haven't checked the laws on that yet. Amateur radio ops aren't allowed to encrypt anything so I don't know if unlicensed individuals may or not). When a node receives a message from an individaul, it requests the gpg key associated with the PAS from the network. I guess a database of GPG keys will need to be maintained by the tunnels as well.

---

