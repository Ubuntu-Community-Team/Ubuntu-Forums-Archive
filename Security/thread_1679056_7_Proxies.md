---
title: "7 Proxies?"
date: 2011-01-31
forum: Security
---

### Post by cgb223 on 2011-01-31
Hey all, I was having an interesting conversation with a friend of mine involving some jesting remarks about "hacking." he made a joke about how he was safe no matter what he did because he was behind seven proxies.

That got me thinking:

A) is being behind seven proxies when doing illegal things or things involving privacy actually safe?

B) how would one go about routing all their Network traffic through seven proxies anyway?


Free oxygen for the person with the best answer,
Cheers!

---

### Post by CharlesA on 2011-01-31
Activities can be recorded whether you use proxies or not.

There will always be a record of your ip address *somewhere*.

In any case, it's only as "safe" as the proxies, as your traffic is going thru them. Would you trust them with your data?

---

### Post by bodhi.zazen on 2011-01-31
This is a fairly complex question, see:

[http://bodhizazen.net/Tutorials/Privacy](http://bodhizazen.net/Tutorials/Privacy)

In a nutshell, if you can send and receive data over "the internet" you can be tracked, it is simply a matter of difficulty and using the appropriate tool to track.

My link has additional links to "white papers" that discuss passive fingerprinting. The thing is, the more you try to block passive fingerprinting, the more you tend to stand out.

---

### Post by HermanAB on 2011-02-01
...and if he doesn't configure his browser and firewall to block DNS requests on the local net, then those will still be sent to his ISP in plain text, so his DNS provider more likely than not can still see which sites he is visiting.

---

### Post by SeijiSensei on 2011-02-01
If he's using [Tor]("http://www.torproject.org/"), tell him to stop so that the people who need it, like Egyptian activists, won't have to compete with his torrent traffic.

---

### Post by asdfghjkl67 on 2011-02-01
This is my current set up- I have a wireless router that uses the dns of my ISP and i connect to this router using ubuntu over the wireless. I then connect to a vpn service that uses open dns as its dns. 

Who can see my dns searches in plain text then?

---

### Post by nevius on 2011-02-01
7 proxies only help if you're in a hacking duel with Crash Override or Acid Burn. Then you'll have to be careful because those hackers can make your computer explode.

---

### Post by spynappels on 2011-02-02
Lol that made me.laugh, esp as when I saw that film first, those specs were still pretty good. Now they just make me smile.

---

### Post by asdfghjkl67 on 2011-02-02
> **asdfghjkl67 said:**
> This is my current set up- I have a wireless router that uses the dns of my ISP and i connect to this router using ubuntu over the wireless. I then connect to a vpn service that uses open dns as its dns. 

Who can see my dns searches in plain text then?

Bump lol

---

### Post by rookcifer on 2011-02-03
> **cgb223 said:**
> Hey all, I was having an interesting conversation with a friend of mine involving some jesting remarks about "hacking." he made a joke about how he was safe no matter what he did because he was behind seven proxies.

That got me thinking:

A) is being behind seven proxies when doing illegal things or things involving privacy actually safe?

No.  The reason is that the data sent over these proxies is all in plaintext, therefore all one has to do is backtrack through each proxy to find the originating IP.  This is trivial for any LEA to achieve.

If you want anonymity, something like TOR would be much better.  With TOR each hop along the chain is randomized and encrypted over three proxies.  The nodes are selected at random and no node knows what the other node is doing or who made the original request to send data.  Tor is not perfect, but it would take a highly sophisticated attack to track someone through it.

> B) how would one go about routing all their Network traffic through seven proxies anyway?

Daisy chaining them.  There's software you can use that accomplishes this.

---

### Post by HermanAB on 2011-02-03
if you really want to see what your system is divulging in plain text, while it is supposed to be using a VPN, run Wireshark or tcpdump.  You'll be amazed.

---

### Post by StaticIp on 2011-02-03
Its a meme from another forum.. He got trolled... Big time..

---

### Post by cariboo on 2011-02-03
You mean this one?
[IMG]http://i.imgur.com/3K30p.jpg[/IMG]

---

