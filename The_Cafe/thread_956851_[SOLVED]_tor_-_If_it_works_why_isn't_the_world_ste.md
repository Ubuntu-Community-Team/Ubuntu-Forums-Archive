---
title: "[SOLVED] tor - If it works why isn't the world stealing music freely?"
date: 2008-10-23
forum: The Cafe
---

### Post by methodmarvel on 2008-10-23
**Sorry for putting this in the wrong place - please move me?**

I've found videos on youtube about a program called tor which hides your IP address.

I was just wondering, if tor works, why people don't use it when they torrent music? Surely it would mean they couldn't be identified or caught?

Basically I'm interested in whether it's lack of "thief education" or whether it's full of flaws.

---

### Post by mikewhatever on 2008-10-23
Absolute beginners section,:confused: have you noticed?

---

### Post by DGortze380 on 2008-10-23
I need to look more into how this actually works, but regaurdless ultimately the thing that convicts most of the copyright infringement cases is forensic evidence. 

Take a step back and think about it logically for a minute, it's impossible to totally hide your IP address 100% of the time. If your IP was not used, and stored, at some point, by some device (realistically, at a number of points, by a number of devices), TCP would not function.

---

### Post by Simplicius on 2008-10-23
> **methodmarvel said:**
> I was just wondering, if tor works, why people don't use it when they torrent music? Surely it would mean they couldn't be identified or caught?

Actually, I understand that a lot of people do use it for that. But I think it is considered to be bad manners. Tor was created for a different purpose AFAIK. For instance, think about a news reporter in a hostile place trying to get information out without being caught.

---

### Post by Sub101 on 2008-10-23
Looks like an interesting project and agree with your view based on my quick research. Perhaps the reason is that no-one knows about it? Or their conscience prevents them?

---

### Post by methodmarvel on 2008-10-23
> **mikewhatever said:**
> Absolute beginners section,:confused: have you noticed?
**Sorry for putting this in the wrong place - please move me?**

Well it's kind of a beginners question - I mean I don't know anything about this.

---

### Post by aeiah on 2008-10-23
tor is slow, that's why. its main use is (mostly)anonymous communication.

---

### Post by Sef on 2008-10-23
> **Sorry for putting this in the wrong place - please move me?**

Well it's kind of a beginners question - I mean I don't know anything about this. 	

Moved.   No worries.  You learn by asking.   We all started off where you are.

---

### Post by LaRoza on 2008-10-23
The world is, for a large part...

Tor and other proxies are good for hiding IP's, but they are slow. Torrents are P2P, and are much faster and would be harder to track.

---

### Post by myusername on 2008-10-23
how is tor slow? i have never used it but i am interested

---

### Post by Dr Small on 2008-10-23
> **myusername said:**
> how is tor slow? i have never used it but i am interested
Tor connects through multiple nodes, each with a different upload ratio (along with other users passing through the node) and ultimately when you pass your connection through a series of different connection (each sometimes slower) your connection is drastically hampered.

The node with the least upload speeds will cause your uploads speeds to be the that node's lowest, or less. Tor is slow, but it helps sometimes when you want to be anonymous.

---

### Post by init1 on 2008-10-23
> **methodmarvel said:**
> **Sorry for putting this in the wrong place - please move me?**

I've found videos on youtube about a program called tor which hides your IP address.

I was just wondering, if tor works, why people don't use it when they torrent music? Surely it would mean they couldn't be identified or caught?

Basically I'm interested in whether it's lack of "thief education" or whether it's full of flaws.
Why? Because it's extremely slow. Pages take forever to load.

---

### Post by bwhite82 on 2008-10-23
> **methodmarvel said:**
> **Sorry for putting this in the wrong place - please move me?**

I've found videos on youtube about a program called tor which hides your IP address.

I was just wondering, if tor works, why people don't use it when they torrent music? Surely it would mean they couldn't be identified or caught?

Basically I'm interested in whether it's lack of "thief education" or whether it's full of flaws.

As was already mentioned, it is bad manners to use it for any downloading purpose (excess bandwidth) because you're using up other people's bandwidth as well. Random people volunteer to be nodes. As far as flaws, some have been found which is why it is recommended that you utilize Privoxy or other such proxy in conjunction with Tor.

I've also read stories about the exit nodes intercepting traffic. Use it with caution and do not believe it is "foolproof".

---

### Post by HittingSmoke on 2008-10-23
> **Soldierboy said:**
> As was already mentioned, it is bad manners to use it for any downloading purpose (excess bandwidth) because you're using up other people's bandwidth as well. Random people volunteer to be nodes. As far as flaws, some have been found which is why it is recommended that you utilize Privoxy or other such proxy in conjunction with Tor.

I've also ready stories about the exit nodes intercepting traffic. Use it with caution and do not believe it is "foolproof".

Yea, as has been said, Tor just relays your traffic through multiple other "nodes" which are really other people who use Tor and decide to donate some of their bandwidth to the network.

As for the downloading thing. I use Tor with Deluge for my torrents but I only use it for tracker requests not actual traffic. Thats completely useless and cripples the network. I don't download music or movies so I don't really have anything to worry about but I just don't trust bittorrent anymore the way fake trackers and ISP filtering has become such a problem.

---

### Post by handy on 2008-10-23
I run vidalia on all my OS's & distro's.  Vidalia is a GUI front end that handles Tor & Privoxy really nicely.

I don't find any noticeable difference in speed between using Tor & not using Tor these days.

I really like the fact that it adds another layer of anonymity to my surfing, though it is not perfect, if an organization was out to get you they could throw resources at the problem & track you down.

For most of us using Tor & Privoxy is a great privacy buffer, & with Vidalia, it makes it so easy, now you can just do a few clicks to set it up, no editing config files.

I recommend that everyone should try Vidalia, if you don't like it, it is easy to remove.

---

### Post by Dr Small on 2008-10-23
> **handy said:**
> I don't find any noticeable difference in speed between using Tor & not using Tor these days.


And you won't if you only get 56KBps download. But for those that get 1500KBps, it drastically slows things down.

---

### Post by mkvnmtr on 2008-10-23
On a couple of the better known bit torrent sites you can find some well written tutorials about why tor won't help you with downloading from torrents. They are easy to find and easy to understand.

---

### Post by billgoldberg on 2008-10-23
For one simple reason, it's waaaaaaay to slow.

---

### Post by handy on 2008-10-23
> **Dr Small said:**
> And you won't if you only get 56KBps download. But for those that get 1500KBps, it drastically slows things down.

I'm on 1500/256 & I don't have any problem using the Vidalia package.

On or off, the speed difference is not noticeable.

---

### Post by Dr Small on 2008-10-23
> **handy said:**
> I'm on 1500/256 & I don't have any problem using the Vidalia package.

On or off, the speed difference is not noticeable.
You must be going through some uber fast nodes then, is all I can say.

---

### Post by handy on 2008-10-23
> **Dr Small said:**
> You must be going through some uber fast nodes then, is all I can say.

I am using the what is regarded as the best ISP in the country, perhaps that is making a difference?

The ISP connects to the world via Japan & the U.S.  I know no more. :-)

---

### Post by sefs on 2008-10-23
Tor can be rather good at what it does for being anonymous (not secure) on the internet.  But you have some things going against you...

1) Lack of bandwidth ... the downloading of large files thru the system will bring it to its needs as most of the bandwidth is donated and its just not there to support applications that eat up bandwidth.

2) Anyone can run tor servers ... i.e  the cia, the fbi, the nsa, the foreign agencies, the russian mafia, your next door neighbour... so the question is are you really anonymous on the tor network.

p.s. just make sure you use end to end encryption (ssl, ect.) if using services like email over it (really you should not be)

---

### Post by sloggerkhan on 2008-10-23
I've used tor in the past. It raises your ping to really high levels (unimportant for **normal** web browsing and email) and also tends to reduce your bandwidth tremendously. Via tor, I've tended to get connections in the 30 to 120 kilobytes a second range on connections that without it run at about 1 megabyte a second.

Further, a lot of websites try to watch for Tor exit nodes and block them from doing things such as sight registration for various reasons.

---

### Post by Kingsley on 2008-10-23
Tor is way too slow for illegal downloading. I occasionally use it for other reasons.

Check out the Torbutton extension for Firefox.

---

