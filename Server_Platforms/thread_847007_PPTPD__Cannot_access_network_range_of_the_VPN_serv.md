---
title: "PPTPD : Cannot access network range of the VPN server"
date: 2008-07-02
forum: Server Platforms
---

### Post by Knightwise on 2008-07-02
Hey everyone,

I'm using pptp to act as a vpn endpoint on my hardy heron box. I have configured pptpd so i can "call in" using my windows machine and have a vpn connection to my server. Here is my setup.


Gateway to www (router 192.168.123.253)**Dads machine(192.168.123.20)**Ubuntu server(192.168.123.11)

                                                    Vpn Interface server
                                                    10.0.0.1
                                                             *
                                                             *
                                                    Vpn client
                                                    10.0.0.2

I can connect to my server over VPN and access the 10.0.0.1 interface. I have also installed GUIDEDOG and enabled NAT, that way my VPN client can also surf the net when connecting to the VPN. However I would like to access files and services on my dads machine (in the 192.168.123.0 range) What setting do I need to change to make this happen ?

---

