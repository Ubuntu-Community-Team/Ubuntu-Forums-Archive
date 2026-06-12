---
title: "Blocked outgoing ICMP packet (ICMP type 3)"
date: 2009-12-05
forum: Security
---

### Post by issya on 2009-12-05
I have an Ubuntu server in my house that is set up as a DMZ on my router. It is a Web and e-mail server. I own a marketing company that sends out bulk e-mail from that server for various clients. I noticed the red hard drive light is almost constantly on now. I looked over my router logs and it looks like that server is flooding the router with outgoing ICMP packets. The message I see is the below. It may even happen multiple times a second. I can clear the logs and in 10 minutes it may have 1,000 of them.

Blocked outgoing ICMP packet (ICMP type 3) from server_ip to 10.10.7.208

I tried looking at a bunch of things and it doesn't seem like any abnormal processes are running or even tying of the network. I do get mail servers connecting to it though. Isn't this a ping back? I tried adding a rule to drop all ICMP to iptables and it didn't do anything. I also ran chkrootkit and nothing was found. There was regular ssh with password login setup. I did see various Chinese IP addresses trying to login to SHH. I changed some of the settings and made it so you have to have a certificate to login.

I also saw a few getty processes running last night but haven't seen them again. Any help on this would be greatly appreciated.

---

### Post by OpSecShellshock on 2009-12-05
Have you tried going to an realtime block list sites and putting in the IP address of your mail server to see if it's been flagged? It may also be sending out ICMP packets when messages get read in order to check the validity of the recipients' addresses. Some bulk mailing programs do that for whatever reason. ICMP type 3 means "destination unreachable." It's possible that an outbound packet of this type could indicate that your server is trying to respond to incoming pings with the message that you can't be pinged (which would make sense if you've got it configured to drop incoming pings).

---

### Post by issya on 2009-12-05
Thanks for the fast reply. The ip has not been flagged by spam databases.

I do know that the bulk e-mail program tracks opens and clicks. Could this be something to do with it? I don't see why it would need to ping though. I am going to check with the software provider to see if this is possible.

I just added the rule to iptables yesterday and it was not dropping them before then. Yet this problem has been happening before then. Is it bad to not answer ping requests? Could this be some type of DoS?

---

### Post by Hackuin on 2009-12-06
Hello.
Its seems to be some variant of SYN FLOOD to me.
As, shock figured, the server is replying to the ping requests, for the clients which doesn't exist/ which cannot be reached.

As far as your question is concern:
> 
 Is it bad to not answer ping requests?
No. Not really, it actually depends up on your Network scenario.

I could say, and pretty sure, you need to block the inbound "echo requests" so, that your server shouldn't reply to the echo requests of the fake/spoofed/non existing machines, which is filling up your logs.

---

### Post by koenn on 2009-12-06
> **Hackuin said:**
> Hello.
Its seems to be some variant of SYN FLOOD to me.
As, shock figured, the server is replying to the ping requests, for the clients which doesn't exist/ which cannot be reached.

As far as your question is concern:
No. Not really, it actually depends up on your Network scenario.

I could say, and pretty sure, you need to block the inbound "echo requests" so, that your server shouldn't reply to the echo requests of the fake/spoofed/non existing machines, which is filling up your logs.
yes, dropping the incoming echo requests would fix this, if the replies are triggered by an external source.
It's strange, though, that echo requests should arrive at this server while their destination is elsewhere, unless there's some weird routing going on  somewhere, or the echo requests are meant to trigger replies to flood a given address (a so-called 'reflected' DDoS)


edit:
[http://www.networksorcery.com/enp/protocol/icmp/msg3.htm](http://www.networksorcery.com/enp/protocol/icmp/msg3.htm)
some background on what reasons hosts may have to (legally) send "destination unreachable"

---

### Post by Hackuin on 2009-12-07
> **koenn said:**
> yes, dropping the incoming echo requests would fix this, if the replies are triggered by an external source.
It's strange, though, that echo requests should arrive at this server while their destination is elsewhere, unless there's some weird routing going on  somewhere, or the echo requests are meant to trigger replies to flood a given address (a so-called 'reflected' DDoS)


edit:
[http://www.networksorcery.com/enp/protocol/icmp/msg3.htm](http://www.networksorcery.com/enp/protocol/icmp/msg3.htm)
some background on what reasons hosts may have to (legally) send "destination unreachable"

Well,
Might be a case of someone blindly running weird, DDoS tools?

> 
It's strange, though, that echo requests should arrive at this server while their destination is elsewhere
If the firewall is correctly configured, the attack cannot be possible, the idea is that, the attacker will initiate a connection (SYN) with a spoofed IP which does not exist, if the spoofed IP exist it will obviously send RST to the SYN/ACK send by the server, so, when the attackers spoofs the IP of non-existent address, the server will send the SYN/ACK to spoofed address and wait for the three-way handshake but, as the address doesn't exist, it is going to wait for its timeout value, soo, the attacker will again send the ACK to server and establish the connection. The restriction is it requires, the IP ID which can be easily guess, becasue, the attackers it self is initiating/sending a SYN request to server with spoofed address. The only problem is Seqence number, which I guess the attack is getting failed and he is playing around with the server.

-Hackuin

---

