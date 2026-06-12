---
title: "Using Ubuntu server need howto for sharing internet to some, not all computers on L"
date: 2012-05-05
forum: Server Platforms
---

### Post by CongoJim on 2012-05-05
I've been asked to setup a LAN where access to internet only allowed to certain computers yet allow access to all computers to the local network. I'd also like to add the ability to download all users pop3 mail for them and send their mail out whether they are allowed accessed to internet or not. The problems are: Electricity not 24/7 (I'm in the DR Congo) so the server can't be on 24/7 to receive email, internet connection slow, very slow which is why we need to limit access to the net, yet I have installed ejabberd for communication in the building and want all computers to be able to access that for messaging and file transfers. My hope is that when the server is turned on it downloads everyone's emails so they can access theirs via an email client (sadly a few holdouts still using windows). The mail server would also allow anyone to send emails as well, just no surfing. Is all of this possible? I got the part of connect internet to server and server to routers and switches :p but how to get UFW and postfix and whatever other doohickies to play together is just a mystery to me.

---

### Post by darkod on 2012-05-05
So, what kind of setup do you plan to use?

The server is connected to the internet directly with one network card, and with the LAN with another network card, right?

---

### Post by CongoJim on 2012-05-05
> **darkod said:**
> So, what kind of setup do you plan to use?

The server is connected to the internet directly with one network card, and with the LAN with another network card, right?

Yes. Currently using apache2 and ejabberd for local network activities.

---

### Post by darkod on 2012-05-05
So, your server will be your internet gateway.

Maybe some experts will have other ideas, but in my opinion the easiest way to control the internet connection, is to set your server as a gateway on the machines you want to have internet, and don't set any gateway on the machines that you don't want to have internet access. Without gateway, they can't get out.

The internal LAN traffic should work fine with only IP and subnet mask.

Also, if the server will be a router, you need to uncomment the routing command in /etc/sysctl.conf. Have you done this? Can you get out to the internet from one machine that has the server as gateway?

PS. The setting in /etc/sysctl.conf you need to enable is net.ip4.ip_forward=1. Make sure there is no # in front of it. After you do that the server should forward packets from one interface to the other which you need so it can be a router for the other machines.

---

### Post by SeijiSensei on 2012-05-05
Use [fetchmail]("https://help.ubuntu.com/community/GmailPostfixFetchmail") to get the mail from the remote POP3 server.  If you set up user accounts on the server, fetchmail can download a message addressed to user@domain and deliver it to that user's mailbox. In fact you can tell it that remote user william has local account bill and deliver it accordingly.

The easiest solution to segregate users is to use separate networks.  If your wiring supports it, add a third network card to the server and connect the Internet-enabled machines to one card and the blocked machines to the other.  Put each group of machines in a separate IP subnet and write an iptables rule that only masquerades traffic originating on the Internet-enabled interface.

If you must have a single physical network, you can have your server run dhcpd.  In dhcpd.conf, define two subnets, one for permitted and one for blocked hosts.  In the definition for permitted hosts, you'll need to use the "host" directive and the permitted machines' MAC addresses to place those machines in the permitted subnet.

However since you say browsing won't be allowed, I'm not sure you even need to implement any of the above.  If the only external service you're using is email, then leaving net.ipv4.ip_forward=0 in /etc/sysctl.conf is a simple solution.  Then the box can't forward traffic between interfaces and no one will be able to get to the Internet.

For a simple web-based email client solution, I recommend [Squirrelmail]("https://help.ubuntu.com/community/Squirrelmail").  Then your users can use a browser for mail services making it entirely cross-platform.  It's also an easier solution to administer since you don't need to worry about configuring the users' individual client mail software.  Use [dovecot]("https://help.ubuntu.com/community/Dovecot") with IMAP on the server box so the users can have mail folders.

Let's talk for a second about how the Internet connection is set up.  Do you have some type of dialup connection using PPP, or a full-time connection over DSL or some similar technology?  If you're using PPP, you can set up the box to run pppd on demand and dialout to the provider at fixed intervals.  (See the section on "demand dialing" in [this document](http://www.faqs.org/docs/linux_network/x7297.html).)  During this period your box would download the mail using fetchmail and send out any queued messages using sendmail or Postfix.  If PPP with demand dialing is configured, you could put a script in /etc/cron.hourly that would run fetchmail and despool the outbound mail queue.  When fetchmail starts, it would cause the pppd daemon to dial out to your provider.

Another option you might explore is whether anyone still supports UUCP for email in the DRC.  UUCP was designed specifically for the type of problem you have where you want asynchronous mail traffic and nothing else.  It's a dialup service.  I used to be a UUCP provider back in the mid 1990's, and setting it up on Linux wasn't that hard.  On-demand PPP is a better long-term solution, though, since it does give you true Internet connectivity.

---

### Post by CongoJim on 2012-05-05
> **darkod said:**
> So, your server will be your internet gateway.

Maybe some experts will have other ideas, but in my opinion the easiest way to control the internet connection, is to set your server as a gateway on the machines you want to have internet, and don't set any gateway on the machines that you don't want to have internet access. Without gateway, they can't get out.

The internal LAN traffic should work fine with only IP and subnet mask.

Also, if the server will be a router, you need to uncomment the routing command in /etc/sysctl.conf. Have you done this? Can you get out to the internet from one machine that has the server as gateway?

PS. The setting in /etc/sysctl.conf you need to enable is net.ip4.ip_forward=1. Make sure there is no # in front of it. After you do that the server should forward packets from one interface to the other which you need so it can be a router for the other machines.

Wouldn't they be able to insert the gateway after? It's not like I can mask it on the other computers.

---

### Post by darkod on 2012-05-05
> **CongoJim said:**
> Wouldn't they be able to insert the gateway after? It's not like I can mask it on the other computers.

Not unless they all have administrator permissions. In both linux and windows, they can't touch the network settings without admin rights. From this aspect I said I like this solution. But if all users have local admin rights, you will need other options. Some of them are suggested above.

---

### Post by SeijiSensei on 2012-05-05
> **CongoJim said:**
> Wouldn't they be able to insert the gateway after? It's not like I can mask it on the other computers.

As I said in my rather longish reply:

> **SeijiSensei said:**
> If the only external service you're using is email, then **leaving net.ipv4.ip_forward=0 in /etc/sysctl.conf is a simple solution**.  Then the box can't forward traffic between interfaces and no one will be able to get to the Internet.

---

### Post by sj1410 on 2012-05-05
making it more simple
```

net.ipv4.ip_forward=1 in /etc/sysctl.conf 

```
and
```

iptables -t nat -A POSTROUTING -s 192.168.1.2/32 -o eth0 -j MASQUERADE

```
where 192.168.1.2 is the ip of PC where u want to allow internet and eth0 is the interface where internet is connected.

add as many rules as you want

---

### Post by SeijiSensei on 2012-05-05
I think you missed this point in the original post:

> The mail server would also allow anyone to send emails as well, *just no surfing*.

As far as I can tell, the only external service they wish to provide is email, and even that may be limited to specific users.  

On the other hand we have this:

> I'd also like to add the ability to download all users pop3 mail for them and send their mail out *whether they are allowed accessed to internet or not*.

So perhaps some users will be allow to connect directly to the Internet.  All this is speculation until Jim returns.

---

### Post by darkod on 2012-05-05
> **SeijiSensei said:**
> I think you missed this point in the original post:



As far as I can tell, the only external service they wish to provide is email, and even that may be limited to specific users.  

On the other hand we have this:



So perhaps some users will be allow to connect directly to the Internet.  All this is speculation until Jim returns.

I think it's a bit more complicated than that. The very first sentence of the first post says "access to internet only allowed to certain computers", so it sounds to me they really want two groups of computers, with and without internet, and on top of that the email for everyone will be downloaded locally and distributed.

---

### Post by elico on 2012-05-05
you can use squid as proxy server and user authentication to allow the internet access.

---

### Post by SeijiSensei on 2012-05-05
> **darkod said:**
> I think it's a bit more complicated than that. The very first sentence of the first post says "access to internet only allowed to certain computers", so it sounds to me they really want two groups of computers, with and without internet, and on top of that the email for everyone will be downloaded locally and distributed.

That's what I thought originally as well; my first post was premised on creating two subnets, either physically or via DHCP host reservations, and granting one access and blocking the other.  I wouldn't trust using Squid with authentication because it would be too easy for an unauthorized person to get the credentials of an authorized user.  

Creating two physical subnets is probably the most secure, though you'd need need to keep the unauthorized users from sitting down at an authorized machine.  If each client workstation has a unique username and password that belongs only to the person authorized to use that machine, that's probably a step in the right direction.  If there's some form of network authentication with NIS or LDAP you have the problem of someone logging in from an authorized workstation.  (I don't think NIS enables you to tie a user account to a specific IP address; maybe LDAP supports that?  Or maybe some method based on Kerberos?)

If authorized people use the system at a different time of day from unauthorized users, say during working hours vs other times, you can use cron to change the value of /proc/sys/net/ipv4/ip_forward, setting it to zero during the unauthorized periods, and setting it back to one during working hours.

---

### Post by CongoJim on 2012-05-07
Sorry for the delay, like I said, electricity not a permanent thing.

I'll try and explain better. I have an ISP that gives us "blazing" 30kb/s download speeds at best of times. My current setup is the isp modem is connected to the router with dhcp distribution. A fixed addy is on the server that is used for an accounting program I wrote in PHP and ejabberd communications. The problem is there are 40 computers connected to the network which was fine because I disabled auto updating on the Windoz users and download the updates manually once for distribution around the building. Unfortunately, some jerk from the capital city (the LAN is in a provincial governor's office building) showed people Youtube, Facebook, Skype and Yahoo. The other day the governor couldn't get into his yahoo mail and was calling the ISP bad names. I told him the problem is our system is overloaded. The order came down, block the internet to all but certain authorized users but allow LAN activities. Since we have a domain I can issue pop3 addresses to everyone and at least allow them that privilege otherwise they're going to be in my office every 5 minutes wanting to check their e-mail. The building is 150 meters long and I've wired it with mostly wireless routers as all walls and ceilings are thick concrete that I have no means, nor desire, to drill through for cables.
So now I wish to pass the internet through the server and yes I have two but not three cards. 

So the setup I need is via the server, allow 10 computers unlimited access to the internet and limit the other 30 to the LAN. I would also like to download the emails for all 40, leaving the mail on the host server for the domain so that access can be gained when out of the building and letting all 40 access their email from the local server which would send and receive all their mail. The local server is not on all the time so as I understand it the email has to have an offsite connection that can receive 24/7.   

So, my guess is that I need to use the router to assign addresses to specific macs then set up on the local server an IP table that determines who gets out and who doesn't. Then I have to use Fetchmail to download and send all the emails and configure everyone's email client to get mail from the local server. How to do all that is the $60 question as I am not a network guru by any means. Of course I don't have $60 to pay...:)

---

