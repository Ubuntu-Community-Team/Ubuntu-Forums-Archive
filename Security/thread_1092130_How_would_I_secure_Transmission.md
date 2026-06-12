---
title: "How would I secure Transmission?"
date: 2009-03-10
forum: Security
---

### Post by brandon88tube on 2009-03-10
I wanted to know any ways of securing Transmission so that I can use it to download some files as that seems to be the only way to get some subtitled stuff I've been looking for. This might be impossible as I have to open the port up to use it and that right there is a red-flag for me, but I wanted to know if there was any way to make it safe to use. I'm not all that knowledgeable about torrent programs and that so I hope what I am asking doesn't sound completely stupid. I would love to finally download stuff I was unable to before. If I can't secure it, then I will just have to give up and try to hope that it comes out in a different form and not as a torrent.

---

### Post by Tubes6al4v on 2009-03-10
If it is just that file, then you can open the port until it is done, then close it again. With torrents, you inherintly trust the people you are getting the file from, so you are vulnerable there anyhow. You have to asses whether it is worth the risk. For me, it is.

---

### Post by Sander79 on 2009-03-10
Currently I just forward the torrent port on my router and close it after a download session. Not very clean but I haven't got time to investigate a better way. When I do have time, I'll use this:
[http://azureus.sourceforge.net/doc/AnonBT/Tor/howto_0.5.htm](http://azureus.sourceforge.net/doc/AnonBT/Tor/howto_0.5.htm)

---

### Post by brandon88tube on 2009-03-10
So, things don't look to good then?

---

### Post by batharoy on 2009-03-10
If your worried about someone trying to sneak in through that open port you can use moblock.
It can be configured to allow out going but still block incoming.

---

### Post by lovinglinux on 2009-03-10
> **Sander79 said:**
> When I do have time, I'll use this:
[http://azureus.sourceforge.net/doc/AnonBT/Tor/howto_0.5.htm](http://azureus.sourceforge.net/doc/AnonBT/Tor/howto_0.5.htm)

Please, DON'T. Tor is not designed for torrent. Not that it doesn't work with this protocol, but the problem is that Tor nodes are computers from regular users like you and me who donate their bandwidth to Tor project. So it is considered abuse to use Tor for p2p.

> It is considered impolite to transfer massive amounts of data across the Tor network – the onion routers are run by volunteers using their own bandwidth at their own cost.

> Due to the high bandwidth usage caused by the use of this protocol, it is considered impolite and inappropriate to use the Tor network for BitTorrent transfers. By default, the Tor exit policy blocks the standard BitTorrent ports.

Besides, even if you can get your torrent application working with Tor, you won't get fast download speeds, since most experienced users will block connections from Tor ips.

> **Sander79 said:**
> Currently I just forward the torrent port on my router and close it after a download session. Not very clean but I haven't got time to investigate a better way. [/url]

I also do this. There is no reason to leave a port open if you are not using it, but this is not necessarily an improvement in security, because if the torrent application is not running then there is no process listening to the torrent port, which makes an attempt to hack into your computer useless.

In my opinion, the best way to protect BitTorrent activity is to use an IP block list application like [moblock]("http://moblock-deb.sourceforge.net/") or [iplist]("http://iplist.sourceforge.net/"), which will prevent a series of IPs on a list to connect to your machine. There are several [ip lists providers]("http://iblocklist.com"), which covers known hackers, p2p corrupt senders, bogus ips, pedophiles and other nasty groups you don't want to connect to.

---

### Post by Tubes6al4v on 2009-03-10
Tor doesn't make anything more secure, just more anonymous. Actually, I think it makes it less secure, as you trust the end node with your information. If you happen to be downloading something that is considered illegal in a country you might be visiting(i.e. music in the US), then you could save it to a hidden Truecypt volume.

I have no experience with it, but would sandboxing Transmission prevent any other files from being written beside what you are downloading?

---

### Post by brandon88tube on 2009-03-10
Not entirely sure what you mean by sandboxing it, but if the outcome is what I'm looking for then that would be nice.

---

### Post by lavinog on 2009-03-10
Afaik: The port is only open on your machine when transmission is running...also, using a non-standard port reduces your chances of being attacked, since most script-kiddies are scanning for known ports.

Like mentioned before: downloading a file from an untrusted source should be more of a concern.

---

### Post by Tubes6al4v on 2009-03-10
[http://en.wikipedia.org/wiki/Sandbox_(computer_security](http://en.wikipedia.org/wiki/Sandbox_(computer_security))

I suppose [AppArmor ]("http://ubuntuforums.org/showthread.php?t=1008906")from Novel or SELinux from DoD could do the same, but I don't have too much experience in them either.

Edit: ... or if you are more comfortable with it, you can make a simple virtual machine, and use that for torrent stuff. I don't think that anyone could gain access to your real machine. Maybe someone can confirm this.

---

### Post by brian_p on 2009-03-10
> **brandon88tube said:**
> Not entirely sure what you mean by sandboxing it, but if the outcome is what I'm looking for then that would be nice.

What outcome are you looking for? We know you have mentioned "securing Transmission" and making it "it safe to use" and having "to open the port up to use it and that right there is a red-flag for me". But could you be a little more precise in what you are concerned about?

For example, you might envisage transmission making all the contents contents of your hard drive available to download. Or maybe you think it is susceptible to a DoS attack?

---

### Post by brandon88tube on 2009-03-10
I don't want to get attacked while having the port open and I also would rather no one connect to me, but I don't think that is possible when using a P2P client.

---

### Post by lavinog on 2009-03-10
> **brandon88tube said:**
> I also would rather no one connect to me, but I don't think that is possible when using a P2P client.
That is how p2p works.
You may want to see if you can find the files available from a website.

Possibly using a virtual machine can reduce your risks, but might be a little excessive if you are not planning to do this on a regular basis.

---

### Post by Jimmynemo2 on 2009-03-10
Just cuase someone needs to say it... REALLY?

Isn't it worth a little inherit risk to get something you know you want?

you're on a Linux box, and going to not download something because you don't want to let down a port or two even just while you download?

By this same reasoning (your low tolerance for acceptable risk) do you drive to work? do you interact with people who without your knowing might be sick?

If your allowable risk is zero, you're likely to miss out on much worth doing and having. Really, give it a shot. Live a little.

---

### Post by brandon88tube on 2009-03-10
Well my real problem is my lack of knowledge with security matters that I try and read up on, but do not always understand or have time to spend. Also, I don't think its entirely worth the risk to just get some files that are just for personal use and not a necessity. Also, I've tried to find places that just have it for download and its very hard to find.

---

### Post by Jimmynemo2 on 2009-03-10
Thats what i mean though- you cant find the files elsewhere, and you obviously care enough to want to find the torrent file of it. 

Me personally, and I am sure many many more with me- its easily worth the risc to lower a port if its for a purpose you want. Having all your ports down all the time is easily a bad thing, but protection of your machine is only useful so long as you can still use it to do the things you want. Once you are protecting it so much that you no longer are getting to use it for what you want, then its time to rethink the thought process behind protection.

The safest car is the one never driven, but that car also becomes the worst investment.

Side note: while p2p does require others to connect to you, so does visiting a website, checking your email or anything at all you do on line. there's an inherit level of trust with a website, but they also can do ill to you, same as p2p. I'm not in favor of rampant p2p downloading, but if thats where the file you want it, I do hope you get it.

---

### Post by lavinog on 2009-03-10
on a similar note: I just finished working on a windows computer that was infected with viruses...It looks like the source was a mp3 file that was downloaded from a p2p site. Apparently the DRM code in the file was malacious.

---

### Post by lovinglinux on 2009-03-10
> **brandon88tube said:**
> I don't want to get attacked while having the port open and I also would rather no one connect to me, but I don't think that is possible when using a P2P client.

To download from p2p networks you need to let people connect to you. If you don't, you still will be able to download if the swarm is big enough, because your torrent client will initiate connections too. Basically it works like this:

- you download a torrent file which contains information about the file you actually want to download and at least a tracker

- the tracker is responsible for keeping lists of peers (IPs) sharing the file you want

- your torrent client gets the tracker information from the torrent file and connects to it to get a list of other peers, then it starts sending connections requests to several peers. Meanwhile, everyone in the swarm (i.e. bunch of peers sharing the same file) will also get the IP list from the tracker and eventually will try to connect to you. If you have the port closed, they won't be able to initiate a connection, but they will connect to you if your client requests the connection.

- once you connect to a peer, it doesn't really matters if your machine sent the connection request or if the peer machine sent to you. The connection is established, so the peer IP has a "free pass". Both your computers start to exchange pieces of the file you are downloading.

So if you never open the port for incoming connections, you will prevent people scanning open ports to reach you, but you are still vulnerable to attacks by those peers you connect to. The vulnerability I'm talking about is not that they will be able to do anything they want. You have to run a client listening to that port and this client must have a vulnerability that can be exploited, otherwise the attacker won't be able to do you harm.

BitTorrent is much safer than other p2p protocols (Limewire, Amule, Donkey etc) because the peer connected to you does not have access to any of your folders. He can only download and upload pieces of the file you are sharing. These pieces are checked by your torrent client and they are discarded if they are not valid.

I'm not saying that there isn't a risk. I'm not security expert (so please someone correct me if I'm wrong), but there also the same risk when browsing the web or chatting with IM applications. As long as you keep you OS updated and the client you are using too, you should be considerably safe. Besides, the torrent client does not run as root, so even if the attacker can use a vulnerability, it would be hard for him to gain access to your entire machine. I can't say the same about Windows users :D

---

### Post by Jimmynemo2 on 2009-03-10
plus one to lovinglinux's reply.

---

### Post by ranch hand on 2009-03-16
Having lived in the police state of ohio, I understand your paranoia.  What you need to concider, in the case of something that is rare on the net, is what kind of folks are interested in it.

Rare things are not likely to attract a lot of people trying to get into your box.  There is no reason for them to try that route.  It does not connect them to enough machines.

Try not being so scared of humanity.  Most of us are harmless.

---

### Post by ballajazzhus on 2011-07-18
there would have to be a vulnerability in transmission in the first place, no?

---

### Post by Perfect Storm on 2011-07-18
Thread closed. Please check the date of a thread before replying. Thanks.

---

