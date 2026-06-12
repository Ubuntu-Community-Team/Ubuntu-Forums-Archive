---
title: "Tor / Privoxy Questions"
date: 2008-03-09
forum: Security Discussions
---

### Post by cegpope on 2008-03-09
Security questions regarding privoxy and tor:

1. Why is it that despite the moratorium on running programs under root, it is common for how-to's to include commands along the lines of "sudo privoxy" to launch from a terminal, or instructions to run it with a init.d script (which from my understanding runs it as root)?

I realize that if one opens a terminal and types privoxy, it returns the error " Fatal error: can't check configuration file '/home/username/config':  No such file or directory" but simply copying the config file from /etc/privoxy/ to /home/username/ allows privoxy to load without requiring root privileges, so am I missing something or is this actually the safer and undiscussed way of running privoxy?



2. I read recently that it has been revealed that Tor network users are susceptible to security risks since the exit node is capable of reading/logging information transmitted/received, such as login names and passwords used to during non-encrypted log ins (ie. signing into this site). Has anyone found a means of preventing this other than simply not using Tor when security/anonymity is desired?

---

### Post by euler_fan on 2008-03-09
> **cegpope said:**
> Security questions regarding privoxy and tor:
I realize that if one opens a terminal and types privoxy, it returns the error " Fatal error: can't check configuration file '/home/username/config':  No such file or directory" but simply copying the config file from /etc/privoxy/ to /home/username/ allows privoxy to load without requiring root privileges, so am I missing something or is this actually the safer and undiscussed way of running privoxy?


It's been my impression reading these forums it's usually better to run something as an unprivileged user than as root, so this may be something to ask the packagers to change. On the other hand, if you set up a new user I don't know how much more work it would be to get Privoxy set up for them. Maybe little or none?

> 
2. I read recently that it has been revealed that Tor network users are susceptible to security risks since the exit node is capable of reading/logging information transmitted/received, such as login names and passwords used to during non-encrypted log ins (ie. signing into this site). Has anyone found a means of preventing this other than simply not using Tor when security/anonymity is desired?

https:// or using a vpn are the suggestions I've seen. There are also [some VPN services]("http://blacklogic.com/") out there which offer to make you anonymous as well as provide vpn access. So I suppose (if you trust them) you might try to vpn though tor to them then access a website. I don't use or endorse the one I linked, but it's an example of what's out there.

---

### Post by cdenley on 2008-03-10
1. It does not run as root. Tor runs as debian-tor. Privoxy runs as privoxy.

2. No matter how you access a website, the connection to the destination server will always be unprotected unless you use SSL encryption. The web server you are connecting to won't belong to the tor network, so any encrpytion used by the exit node would have to be supported by the web server.

---

### Post by Neovos on 2008-03-10
isn't this the point of joining tor with privoxy? I just installed both and *think* I got them up and running and setup completely (with tor running as a relay as well). I know that privoxy basically runs dns requests through tor, therefore making the request anonymous and encrypting them (before sending it out to the tor network). If I understand this correctly, does this mean that you could configure privoxy to encrypt ALL data being sent out to tor not just dns requests? Which could therefore allow one to make insecure logins (this site) secure when routed through the tor network?

Also isn't the only real security threat with tor that people assume that anonymous = secure (as in encryption)?

Could I say that safe non-tor browsing practices (only using sensitive information on encrypted and trusted sites) stays safe when doing the same things on the tor network?

In other words, does a secure connection to my bank (which before was from my computer, through my ISP, and then to my bank) get compromised in any way by the fact that its now being routed through x amount of other tor servers in addition to the parties I know about? It's still encrypted by my SSL connection to the bank right?

It feels to me like what someone had to look hard for before (i.e. people connecting to their banks) is made easier by targeting tor exit nodes.

Just exploring some thoughts, any comments are appreciated, thanks.

---

### Post by Neovos on 2008-03-10
Oh and another thought. Does using an ipfliter program like moblock or ipblock affect all the tor node traffic as well? I'm not sure how it acts with the proxy chain setup (tor and privoxy). And if this does block malicious IP's, shouldn't some type of ipfliter be standard practice for tor nodes along with privoxy? If all nodes used that wouldn't it do much to strengthen the security of the tor network?

---

### Post by cegpope on 2008-03-10
> **cdenley said:**
> 1. It does not run as root. Tor runs as debian-tor. Privoxy runs as privoxy.

maybe running as root was the wrong terminology, but when following the common directions it appears that privoxy runs with root privileges (as seen under the user column in a process list) which leads me to believe that it is at least possible for an exploit to be designed to use privoxy against the host computer as long as privoxy users continue following the current directions instead of putting a config file into the home directory which allows privoxy to run under the "user's name" as seen in the process list, instead of "root".

If I am misunderstanding that processes running as user "root" have root privileges and that this is a "potential" threat to security, please explain why I am mistaken.

> **cdenley said:**
> 2. No matter how you access a website, the connection to the destination server will always be unprotected unless you use SSL encryption. The web server you are connecting to won't belong to the tor network, so any encrpytion used by the exit node would have to be supported by the web server.

I know that if I connect to this website for example without tor the simplified view of the connection is essentially Computer -> ISP -> Site Server and that any of these points in the connections could monitor the content that I am sending unless my browser and the destination are using SSL. 

I also realize that when using tor, the connection becomes something along the lines of Computer -> tor tunnel entry -> ISP -> tor node -> tor node -> tor exit node -> Site Server. It has been revealed that while using Tor, one's ISP is inhibited in knowing what one is transmitting and where it is really going, the tor relay nodes are inhibited in seeing transmission data or destination, but that the exit node, being run by Anyone That Chooses To, can observe/record any data it is transmitting to/from the destination site's server.

My concern is that tor appears to pose a security risk to anyone using tor to connect to sites that do not use SSL encryption such as some email (which was used to demonstrate the existence of this threat by recording and publishing email account logins and passwords), websites such as this one, etc... 

So I am wondering, if anyone has found any way to prevent the exit node from recording the data it transmits/receives or if anyone has heard if the TOR developers are making any alterations to the system to prevent this from being a possibility?

---

### Post by Biggus on 2008-03-10
You can't stop the operators of exit nodes from examining the data that leaves from their box.

tor only provides anonymity, not security.

In short, if you're using my box as an exit node, I will be able to monitor your communications. I will not be able to trace them back to a point of origin, but I will be able to monitor the contents. If your communications are unencrypted, then I may be able to record whatever information you send. This is not a 'fault' of tor, but merely a reflection of the http protocol (or smtp, or whatever).

---

### Post by p_quarles on 2008-03-10
The best way to initiate privoxy is to run the startup script:
```
sudo /etc/init.d/privoxy start
```
This runs the startup script as root, but does not run the daemon as root.

---

### Post by A$h X on 2008-04-12
I run Tor and foxyproxy. Is this as secure as privoxy, or am i wasting my time? I tried privoxy and editing the config correctly, but for some reason it just did not want to work. So in the end I settled on foxyproxy instead.

---

### Post by Neovos on 2008-04-12
> **A$h X said:**
> I run Tor and foxyproxy. Is this as secure as privoxy, or am i wasting my time? I tried privoxy and editing the config correctly, but for some reason it just did not want to work. So in the end I settled on foxyproxy instead.

I don't know much bout foxyproxy, but you might have better luck with the "tor button." It is a toggle for:

1) routing dns traffic through privoxy
2) routing net traffic through tor

---

### Post by netlogic on 2008-04-12
> Is this as secure as privoxy, or am i wasting my time? I tried privoxy and editing the config correctly, but for some reason it just did not want to work.

I know others have said this few times throughout the thread. It doesn't provide security at all. It only provides an anonymity until you sign on to a site without SSL.   I find it totally pointless. It will protect your ISP from knowing what you are doing. That is about it.

---

### Post by mrsteveman1 on 2008-04-13
Privoxy is SUPPOSED to prevent certain identifying information from leaking out, such as scripts reporting your IP address back to the website in question, or requesting a cookie that may have been used previously while on a normal connection. It doesn't encrypt or protect anything really, and in many cases it isn't necessary. Especially if you are logging in to a website where you have already, in the past, logged in with the same account while on your real network with your real IP revealed. You aren't protecting anything in that case.

Also, Privoxy merely scrubs data before feeding it to TOR, it isn't listening on any outward facing ports, but then again TOR isn't either. It may be possible to exploit either of them to compromise a machine but it is unlikely.

Tor on the other hand, obscures where you are connecting from and encrypts your packets until they are well away from your own connection, preventing your ISP from spying on you and preventing the target servers from identifying where you are. Once those packets leave the TOR network though they are completely open, and at that point any personally identifying information in the packets is revealed to any node the packets pass through, including the target servers/websites. For instance, some people run AIM over TOR thinking it provides security, it doesn't. Anyone running a TOR exit node can read your AIM conversations if they want to.

---

### Post by netlogic on 2008-04-13
> **mrsteveman1 said:**
> Privoxy is SUPPOSED to prevent certain identifying information from leaking out, such as scripts reporting your IP address back to the website in question, or requesting a cookie that may have been used previously while on a normal connection. It doesn't encrypt or protect anything really, and in many cases it isn't necessary. Especially if you are logging in to a website where you have already, in the past, logged in with the same account while on your real network with your real IP revealed. You aren't protecting anything in that case.

Also, Privoxy merely scrubs data before feeding it to TOR, it isn't listening on any outward facing ports, but then again TOR isn't either. It may be possible to exploit either of them to compromise a machine but it is unlikely.

Tor on the other hand, obscures where you are connecting from and encrypts your packets until they are well away from your own connection, preventing your ISP from spying on you and preventing the target servers from identifying where you are. Once those packets leave the TOR network though they are completely open, and at that point any personally identifying information in the packets is revealed to any node the packets pass through, including the target servers/websites. For instance, some people run AIM over TOR thinking it provides security, it doesn't. Anyone running a TOR exit node can read your AIM conversations if they want to.

Very clear and concise and accurate. Simple way to say this, Tor is just a random proxy server. Most cases, it will blur the source and destination for people who are spying on you such as your ISP or people in your network.
If the security of contents are concern, try to only associate activities that offers public/private key and ssl method. Like use a public key for instant messenger and educate your friends how important for them to use it.  Since, AOL never released an information about how long they cache people's conversations, it is best to encrypt all of them. For sharing photos with your friends with your web server, just offer them convince of SSL connections. It is really hard to mask source and destination information, but you can mask your data.

---

