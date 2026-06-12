---
title: "Questions about DNS surver"
date: 2013-01-10
forum: Server Platforms
---

### Post by c4sh3w on 2013-01-10
I have looked around and found somethings about it, but none of them really helped.
 
Do I need to set up a DNS server to host a mail, ssh, proxy, or irc server? if so:
     what is the NS or? like is it the name of the hostmachine? or something else?
 
     About the IP Address, do I use the IP address of the machine I'm setting the DNS on or do I use a different one that I have to buy?
 
     FQDN= Fully Qualified Domain Name, where do I go to get a domain named fully qualified?
 
Any questions about what I'm trying to do I will answer if it is needed.
Any help will be greatly appreciated!

---

### Post by darkod on 2013-01-11
For ssh you don't need to set up any specific DNS if you are accessing by public IP. If you want to access by host, like computer1.mydomain.com then you have to set up DNS so that the computer1.mydomain.com can be translated correctly to the public IP. The full name of a host, like the mentioned is called the FQDN. It's not a "special" type of domain. If's just your ordinary domain, and in front of it usually the computer name as specified in the DNS of that domain.

For mail server you will need a domain first. Usually the registrar where you buy the domain will have some sort of control panel that lets you manage hosts (doing DNS for you). So you don't specifically need to set up your own DNS server. In fact, you can do most operations in the registrar's control panel.

A proxy is usually installed inside a private LAN to limit internet access.

I don't know anything about irc servers.

Do you plan to have all these roles on one machine?

---

### Post by c4sh3w on 2013-01-11
Yes I would like to have all of these services all on one machine.


To set up a DNS server (for the purpose of having a personal mail server, proxy, ssh, and irc) do I need a Caching Nameserver? (dose it just cach websites that I visit?).
Do I only need a Primary Master? (Secondary Master optional?)


    NS = nameserver
        Where is that found? is it the hostname of the machine?
            EX: hostname is linuxbox, so would linuxbox be the nameserver?

    FQDN
        Fully Qualified Domain Name, Do I need to buy one, or do I just make it up?
            EX: hostname.websitename.extenshion or is one given to me?
                  I would like to have all non-standard domain names. (excluding the mail)


    IP Addresses 
        When changing the ip address of 127.0.0.1, what do i change it to?
            EX: 198.168.1.10 <-- IP Address given in most examples OR
            to something else like the computers IP Address
                EX: google "what's my ip address" and it comes up with
                    50.973.114.83 OR is it the ip address of the modems



Any help with these questions will be greatly appreciated


PS thanks darkod. I posted that in a little hurry, hope this trys to clear what I'm trying to say up some.

---

### Post by darkod on 2013-01-11
Sorry, but I already answered most of that. Please reread carefully the previous post, and this one too.

You don't buy an FQDN but you do need to buy a domain name. If you want people to send you email to that domain, you can't make it up yourself. So, you buy a domain name (for example mydomain.com) and in the registrar control panel configure one A record which you can name what ever you like, and it has to point to the public IP of the server (or the router/modem if the server is on a private LAN). So, lets say you decide to call the A record 'ns'. In that case the full FQDN of that A host will be:
ns.mydomain.com pointing to IP x.x.x.x

If you do set up your nameserver, it can't be only caching nameserver. Caching nameservers do nothing except caching the visited websites. If you do install your DNS server it needs to be authority for the domain, but you don't need to install one at all. You can use the DNS service in the control panel of the registrar.

For the main server to work you will also need to set up MX record pointing to the FQDN of the server, in the example above ns.mydomain.com.

The IP of the server depends where is it located. If it's in a private (or home) network, you can't simply put a public IP on it. It needs to be private IP but in that case the A record in the DNS will need to be pointed to the public IP of your router/modem.
And you don't "change" the 127.0.0.1 address on the server, you simply configure the network interface with the correct IP. The loopback interface still exists and it continues to have the 127.0.0.1 address.

If you are doing this at home, have you tried to check if the needed ports are open? Lots of internet providers will block certain ports so you can't install servers running services on your home internet connection. If the ports you need are blocked, it might be impossible to make this work, depending...

---

