---
title: "Best ways to beat a IP filter"
date: 2007-07-07
forum: The Cafe
---

### Post by technomaniac on 2007-07-07
Hi...my college runs Squid proxy server and has IP filters on so that we cant even visit sites like youtube and orkut. What are the best ways to beat the IP filters? We generally use web based proxies but soon the sysadmin gets to know about it and blocks that site too. I want a cool and long term solution. I read somewhere that I could install apache on my PC and connect to our college gateway using that and encrypt all the packets from my PC itself...How do I do it?  Also other suggestions are welcome

---

### Post by FoolsGold_MKII on 2007-07-07
One very simple technique is to run the site through something like Google Translate, choosing  as the conversion languages "Chinese to English" or something similar. It will appear mostly identical, however the success of said technique is directly related to the complexity of the site you want to visit. Youtube probably won't work, as well as any site which uses forms, but it's still something to know.

The alternative is to simply not bother cracking the proxy. If the admins find you bypassing their protection mechanisms, they're likely to block net access entirely in response (been there, done that).

---

### Post by darkog on 2007-07-07
> **technomaniac said:**
> .. I want a cool and long term solution. 

move to another college.

---

### Post by kamaboko on 2007-07-08
Get a head shot of the computer admin at the college.  Send it to the FBI indicating that he is an undercover Taliban agent.  That will at least get him off campus for a while.

---

### Post by argie on 2007-07-08
Tor, perhaps?

---

### Post by technomaniac on 2007-07-08
Very thoughtful suggestions....But I think I will rather break into his server and modify the filters....I am preparing for it....

---

### Post by Warpnow on 2007-07-08
Don't do anything too intrusive...a permanent black mark to colleges...

Just use a proxy. Most browsers support them built-in or use a php one you host on some webspace.

---

### Post by init1 on 2007-07-08
> **technomaniac said:**
> Hi...my college runs Squid proxy server and has IP filters on so that we cant even visit sites like youtube and orkut. What are the best ways to beat the IP filters? We generally use web based proxies but soon the sysadmin gets to know about it and blocks that site too. I want a cool and long term solution. I read somewhere that I could install apache on my PC and connect to our college gateway using that and encrypt all the packets from my PC itself...How do I do it?  Also other suggestions are welcome
[https://desktopondemand.com/]("https://desktopondemand.com/")
[http://www.cosmopod.com/]("http://www.cosmopod.com/")
With this, you not only bypass the filters, but also get own Linux desktop you can use almost anywhere.

---

### Post by LookTJ on 2007-07-08
VPN connection to your router if it can run a vpn server(like dd-wrt firmware on WRT54G*)

---

### Post by sloggerkhan on 2007-07-08
Just for informational purposes, I'd like to know what college you go to.

---

### Post by DBO on 2007-07-08
Having been on the other side of this issue (i am really sorry, wasn't my idea) I know how the craftier students get around this.  The quickest and easiest long term solution is to get a box on the outside so to speak.  I assume you have some loving parents at home that would let you drop a linux machine on their internet for some proxied surfing. If so read on =)

This method will circumvent the following protections:
--Packet Filtering
--IP Filtering
--DNS Redirection
--If you are tricky you can do P2P this way
--Just about anything else

The cost of this method:
--Severe speed reduction (max speed == your home upload speed)

Procedure:
1) Drop off your PC at home with Ubuntu Server + SSH installed
2) Ensure port 22 is forwarded to your server from your home router
3) Install and configure squid proxy server (ask if you need help here)
4) Add the following entry to your ~/.ssh/config
> Host home
        HostName HOME_IP_ADDRESS
        User USERNAME
        LocalForward 3128 localhost:3128


5) Open a terminal, type "ssh home", and enter password.  Leave this open
6) Configure your web browser to use 127.0.0.1 port 3128 as its proxy server
7) Enjoy

---

### Post by Dr. C on 2007-07-08
> **DBO said:**
> Having been on the other side of this issue (i am really sorry, wasn't my idea) I know how the craftier students get around this.  The quickest and easiest long term solution is to get a box on the outside so to speak.  I assume you have some loving parents at home that would let you drop a linux machine on their internet for some proxied surfing. If so read on =)

This method will circumvent the following protections:
--Packet Filtering
--IP Filtering
--DNS Redirection
--If you are tricky you can do P2P this way
--Just about anything else

The cost of this method:
--Severe speed reduction (max speed == your home upload speed)

Procedure:
1) Drop off your PC at home with Ubuntu Server + SSH installed
2) Ensure port 22 is forwarded to your server from your home router
3) Install and configure squid proxy server (ask if you need help here)
4) Add the following entry to your ~/.ssh/config


5) Open a terminal, type "ssh home", and enter password.  Leave this open
6) Configure your web browser to use 127.0.0.1 port 3128 as its proxy server
7) Enjoy

This assumes of course that port 22 incoming is not blocked by the parent's ISP. Many do since they do not want their users  running servers on residential accounts. The trick is to use an obscure  non standard port to connect to the proxy server.

---

### Post by bapoumba on 2007-07-08
Closing the thread.
The official stance in these forums is to comply with local rules. The owner of the school internet access has set up a proxy, please see with the sys admin or your school officials.

---

