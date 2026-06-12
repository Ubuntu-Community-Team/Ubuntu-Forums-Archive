---
title: "Inaccurate Copyright Infringement Claims"
date: 2010-08-31
forum: Security
---

### Post by cj.surrusco on 2010-08-31
I am an active user in the bittorrent community. I have a server set up at home and one of it's main uses is acting as a torrent daemon.

Every once in a while I will get an e-mail from your ISP about downloading copyrighted material through bittorrent. Most people that use bittorrent know how it works. Your ISP will send you an e-mail notifying you that BayTSP (or a similar company) has reported that your IP was on the peer list for a torrent that may contain copyrighted material. These are normally accurate as far as the file contents, so I respond to BayTSP and notify them that I have deleted any files that may violate copyright infringement, and everything is OK. This normally happens 2-3 times a year.

However, in the last few weeks, I have received three e-mails from my ISP, Charter, saying that BayTSP has found my IP sharing files that have *never* come in contact with my network. All three of them are movies, and I have never even heard of any of them. In the evidence that BayTSP provides, my IP address is accurate. 

The evidence at the end of the e-mail looks like this:
```


Title:  Scorpion King, The
Infringement Source:  BitTorrent
Initial Infringement Timestamp:  15 Aug 2010 07:33:48 GMT
Recent Infringement Timestamp: 15 Aug 2010 07:33:48 GMT
Infringing Filename:  The Scorpion
King(2002)-720p.BluRay.Dual.Audio.Hindi-Eng_DjVikas
Infringing File size:  1903950895
Infringers IP Address:  xx.xxx.xx.xx
Infringers DNS Name: xx-xxx-xx-xx.dhcp.nwtn.ct.charter.com
Bay ID: 0352847fe1b162e9f9260ad39ba051e3653b055d|1903950895
Port ID: 40999

``` 

I have serious doubts that anyone connected to my network has used torrent service to download these movies. I nobody in my household has done it, and I have fairly strong protection on my wireless network (WPA2 with AES encryption). Plus, I live in a very suburban area, so I doubt that anyone would seriously try to crack my wireless key and use my network.

The only other answer that I could come up with was TOR. All three of the incidents occurred *after* I set up my server to be a TOR relay. From what I read, I didn't think anything like that could happen. Do you think that it's possible that somebody is downloading the copyrighted materials through that TOR service and the TOR service is using my IP to connect to bittorrent?

This problem is really confusing me. The first time, it didn't really bother me, but now that it has happened three times in such a short amount of time, I am starting to get a little worried.

Any input or advice would be greatly appreciated.

Thanks.

---

### Post by uRock on 2010-08-31
I find it funny that ISPs bother with notices, when they have the ability to stop torrenting in their network.

I only torrent Linux ISOs, so I have nothing to worry about.

---

### Post by v1ad on 2010-08-31
i don't think isp's should have the power to restrict torrents, because at times we still are using them to download legal software.

and cj, they probably are transferring files through your service, any way to encrypt it?

---

### Post by rookcifer on 2010-09-01
> **cj.surrusco said:**
> The only other answer that I could come up with was TOR. All three of the incidents occurred *after* I set up my server to be a TOR relay. From what I read, I didn't think anything like that could happen. Do you think that it's possible that somebody is downloading the copyrighted materials through that TOR service and the TOR service is using my IP to connect to bittorrent?

Yes, this is likely what happened.  You must be careful when setting up a Tor relay to not set yourself up as an exit node!  Are you an exit node?

---

### Post by cj.surrusco on 2010-09-01
> **v1ad said:**
> i don't think isp's should have the power to restrict torrents, because at times we still are using them to download legal software.

and cj, they probably are transferring files through your service, any way to encrypt it?
I didn't think that my IP address would be used to connect TOR users to the internet. I was under the belief that data was only pushed through my relay to another relay. I don't understand how I would encrypt the TOR data, though. I don't have any control over the data that goes through my relay.
> **rookcifer said:**
> Yes, this is likely what happened.  You must be careful when setting up a Tor relay to not set yourself up as an exit node!  Are you an exit node?

I never noticed any configuration for being an exit node or not. 

Thanks for the suggestion. I'm going to look into that now. Do you now how to be a relay without being an exit node? That would probably explain the e-mails, though.

EDIT: I found out how to prevent your relay from acting as an exit node. You just need to uncomment or add the following line to your torrc:
```
ExitPolicy reject *:*
```
I'll start my relay back up with this option and see if the problem stops.

---

### Post by Bachstelze on 2010-09-01
> **rookcifer said:**
> Yes, this is likely what happened.  You must be careful when setting up a Tor relay to not set yourself up as an exit node!  Are you an exit node?

Except that without exit nodes, TOR would be useless. Personally I am an exit node, but only on select ports (at the moment 22, 80, 110, 220, 443, 993, 995) that have a low-risk of abuse and are the most useful to legit TOR users. Never got a problem, in a little over a year.

---

### Post by cj.surrusco on 2010-09-01
> **Bachstelze said:**
> Except that without exit nodes, TOR would be useless. Personally I am an exit node, but only on select ports (at the moment 22, 80, 110, 220, 443, 993, 995) that have a low-risk of abuse and are the most useful to legit TOR users. Never got a problem, in a little over a year.

Ah, that definitely sounds like the way to go. I want to help the TOR network, but I don't want to risk getting in trouble with my ISP or anything like that. I even read a story about a guy that ran an exit node and was arrested because someone had used his exit node to download child pornography (Maybe he was trying to cover his own butt, can't say for sure, but he was found not guilty). That would obviously be very serious, and could even happen with just those select ports open. Is there an easy way that I could block anyone from using my port 80 to browse anything illegal like that?

---

### Post by Bachstelze on 2010-09-01
> **cj.surrusco said:**
> Ah, that definitely sounds like the way to go. I want to help the TOR network, but I don't want to risk getting in trouble with my ISP or anything like that. I even read a story about a guy that ran an exit node and was arrested because someone had used his exit node to download child pornography (Maybe he was trying to cover his own butt, can't say for sure, but he was found not guilty). That would obviously be very serious, and could even happen with just those select ports open. Is there an easy way that I could block anyone from using my port 80 to browse anything illegal like that?

You can block (or allow only) specific domains, but I don't think any kind of content filtering is easily possible. Even tools specifically designed for that purpose are not without flaws.

I don't think you need to worry about stuff like that. Child porn matters are taken seriously, and they do very thorough investigations so they don't convict innocent people. They probably seized the guy's computer, investigated it and found nothing. If he was really downloading child porn, they would have found it.

---

### Post by cj.surrusco on 2010-09-01
> **Bachstelze said:**
> You can block (or allow only) specific domains, but I don't think any kind of content filtering is easily possible. Even tools specifically designed for that purpose are not without flaws.

I don't think you need to worry about stuff like that. Child porn matters are taken seriously, and they do very thorough investigations so they don't convict innocent people. They probably seized the guy's computer, investigated it and found nothing. If he was really downloading child porn, they would have found it.
Yeah, but the idea of having a dawn raid on my house and the cops taking my computer isn't too thrilling, even if I am let go without charges ;)

I think I will stay as a middleman for the time being, and if the problem with my ISP stops, then I will add an exit node for those particular ports. Thanks for the advice :D

---

### Post by cj.surrusco on 2010-09-17
Okay, I disable the exit node and two weeks have gone by with no more copyright infringement claims. I think it's safe to assume that it was coming from torrent traffic on the TOR network.

---

