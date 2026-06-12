---
title: "Ubuntu Server as PDC and WINS?"
date: 2012-08-11
forum: Server Platforms
---

### Post by nickaceph on 2012-08-11
Hi to All,
Sorry to Posting this there is a lot of post probably pertaining to this issue, but those got me walking in circle so, I finally decide to post this to clarify the situation.

Situation:
[LIST=1]
[*]We have a small LAN roughly upto 30 computer's this PC's is running some of them windowXP/7 and some are Linux Ubuntu/Mint.
[*] Currently We have Windows XP as a Proxy Server and Gateway. then I installed Ubuntu 10.04 which is meant to be used as the PDC server.
[*]We are now trying to implement a PDC by using ubuntu server. reading and testing through the available resources we need to first fix the local name resolution in our LAN meaning PC's Window and Linux need to be able to reolved each other by hostname. this is now ok (linux-linux, linux-win, win-win, win-linux) but now, I dont know which is resolving the hostname the WindowsXP or the Ubuntu?
[*] I have configure Ubuntu 10.04 as a domain controller using Resara for now (because resara is closing I will be re installing it manually or somehow stick with it.
[*] with the above situation Window OS is able to join the Domain but a bit slow in logging in. but it was ok.
[*] Linux box however cannot connect to the Domain. with the following error : 
DNS_ERROR_BAD_PACKET A bad packet was received from a DNS server. Potentially the requested address does not exist.
[/LIST]

Goal which I need help (Please)
[LIST=1]
[*]Ubuntu Server to be the one to resolve the hostname of PC in the LAN dynamically (not from host file as would in windows network)
[*]how can I check from the client if my ubuntu is now resolving the LAN hostname?
[*]Ubuntu Server to be the PDC in My LAN
[*]Ubuntu will also be my File Server later on.
[/LIST]

Please help thanks.

---

### Post by bakegoodz on 2012-08-11
I have seen problems until WINS was set right. What you need to do is have the DHCP server give out the IP of the PDC as the WINS server. Then you need to make sure the WINS line in /etc/samba/smb.conf is set to the PDC's IP. Then all the LAN computers will use the PDC to give computer names out. WINS instead of DNS will be used for computers to find each other on the LAN.

---

