---
title: "Server often unreachable in LAN - strange behaviour"
date: 2010-07-13
forum: Server Platforms
---

### Post by Chani.xy on 2010-07-13
Hello,

I am trying to set up a virtualized ubuntu server in a local lan.

In short : 
The server does not always answer to ping/ssh/whatever, but sometimes does, it seems completely random and dependant on the clients, it drives me crazy, what can I do to track down the problem ?

In long : 
I will give the exact environment further down, but first the symptoms :

A very strange network behaviour : the server does not always answer to ping/ssh/whatever from another computer in the LAN. 
It *seem*s completely random if it does or not, however I have identified some facts :

- it is able to ping any computer in the LAN, or even outside (using IP or hostname) so it's connection seems ok.

- it is able to ping itself using "ping localhost"

- the hyperviser is always able to ping it, however the *first* ping always fails (ie 3/4 first round then it works fine).

now for the strange/random facts :

- from my linux client, I can usually ping the server for about 10 minutes after I restart networking (in the ubuntu server), then it does not answer to ping/ssh/whatever anymore (though it happened that it suddenly came back for a while)

- from my colleague windows client, we can ping the ubuntu server (same as the hyperviser, 3/4 first round), even when the linux client can't anymore

- from my virtualized windows client, it is equal to my linux client (does not work fine)

- from another linux client, same (does not work fine)

- from 2 another windows machines, it does NOT work either !


Now for the environment :

- Hyper-V is the hyperviser on a DELL computer (not my fault, didn't have the choice)

- Ubuntu server 10.04 standard install, with the synthetic network drivers activated in the kernel and defined in Hyper-V.

- A static IP

- All computers in a LAN with mostly windows servers (such as DNS, AD and exchange servers)

- there is another virtualized server (windows) on the same hyper-v global virtual network, with its own IP, and this one pings perfectly fine from any client.

- the hyper-V also answers to ping


I'm lost, any hints on how I could try to narrow down the problem would be really appreciated.

Thank you,
Chani

---

### Post by leopardsanderson on 2010-11-22
Similar behavior but on a physical Ubuntu 10.04 Server, not virtual. After some time it is unreachable but it can ping the network computers. Resetting the eth0 interface (ifconfig eth0 down, ifconfig eth0 up) helps sometimes.
The LAN is made of wireless + Powerline ethernet, but I believe this is not important. The other machines are windox, with FTP or Cygwin clients used to ping/ftp/http the server.

How could I do more diagnostic from the server terminal?

Edit: 
LAN is a SOHO, with a DSL/wi-fi router. The IP of the server is static 192.168.1.2

Thanks
Leo

---

