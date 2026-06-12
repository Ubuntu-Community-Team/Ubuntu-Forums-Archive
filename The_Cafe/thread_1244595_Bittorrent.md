---
title: "Bittorrent"
date: 2009-08-19
forum: The Cafe
---

### Post by Messyhair42 on 2009-08-19
I've got questions regarding the Bittorrent protocol. first off I'm on a 1.5 Mbps connetion (average peak is 180Kbps, on rare occasions i can hit 230 Kbps), upload is restricted to 128Kbps, and in Ubuntu I use Ktorrent. when I'm running a bittorrent download i can't browse the web or even use IM, nothing goes through even if my DL rate is way below peak, this is true for all computers on my network. also i usually get higher DL rates if i'm running just one torrent at a time. I'm just confused as to why it can be so inefficient for me.

---

### Post by dumblebee100 on 2009-08-19
> **Messyhair42 said:**
> I've got questions regarding the Bittorrent protocol. first off I'm on a 1.5 Mbps connetion (average peak is 180Kbps, on rare occasions i can hit 230 Kbps), upload is restricted to 128Kbps, and in Ubuntu I use Ktorrent. when I'm running a bittorrent download i can't browse the web or even use IM, nothing goes through even if my DL rate is way below peak, this is true for all computers on my network. also i usually get higher DL rates if i'm running just one torrent at a time. I'm just confused as to why it can be so inefficient for me.

That is not just you ...me too suffering from the same problem ..but slight change ..I have 1 mbps connection ....but when I start a torrent I can browse the pages very slowly ..at least I get pages if I wait some time ..some time I have to refresh it constantly to repaint if some extra data has downloaded to present html page requested ...and when comming to IM ..I use pidgin with 3 accounts ..when using torrents I get frequent disconnection ....its just like I have to reconnect all the 3 accounts in line for every 20 seconds or so 


as far as I know the torrents will make connections with many IPs and use bandwidth to keep a connection alive so thats what restricting other apps 
to get bandwidth 

because we feel that if we pause download we could get bandwidth for other apps but in my case even pausing doesnt change much ..I have to stop it entirely

---

### Post by Pogeymanz on 2009-08-19
Yeah, me too. I think it's not the bandwidth, but the number of connections that it keeps trying to make/check/keep-alive. Because, for me at least, pages load just as quickly, but there is a huge pause before they start loading.

---

### Post by t0p on 2009-08-19
When you're up/downloading a fairly popular torrent or two, open a terminal and type in the command

```
netstat -tcp
```

All those connections are bound to compete with your web browsing and instant messaging traffic and slow it down.

---

### Post by mkvnmtr on 2009-08-19
Try lowering the number of connections per minute or second I forget which. That helped my browsing speed.

---

### Post by .Maleficus. on 2009-08-19
> **Messyhair42 said:**
> I've got questions regarding the Bittorrent protocol. first off I'm on a 1.5 Mbps connetion (average peak is 180Kbps, on rare occasions i can hit 230 Kbps), upload is restricted to 128Kbps, and in Ubuntu I use Ktorrent. when I'm running a bittorrent download i can't browse the web or even use IM, nothing goes through even if my DL rate is way below peak, this is true for all computers on my network. also i usually get higher DL rates if i'm running just one torrent at a time. I'm just confused as to why it can be so inefficient for me.
Let's take this one step at a time.  You're paying for 1.5Mbps from your ISP?  Mbps means "mega*bits* per second".  As you know, there are 8 bits in a byte, so your actual download rate (in MBps (megabytes per second)) will be 1/8th of that, or ~187.5KBps (kilobytes per second).  The same applies for your upload rate.  You can see why your connection is very slow - you're already using most of your bandwidth.  And because the computers on your network share the bandwidth, well, you get the idea.  As for one torrent at a time - the more that the protocol can allot to each torrent the faster they will be.  The less torrents, the less it has to share and the faster that one will go.  Does that answer things for the most part?

---

### Post by Messyhair42 on 2009-08-20
but even so, my total torrent DL/UL rate could be 10 Kbps and i can't browse the web at the same time. likewise, running one torrent at a time i may average 40-50 Kbps but as soon as i start a second or more the total DL rate usually drops to below 20. there is something with the BT protocol i think that causes these events.

---

### Post by Messyhair42 on 2009-08-27
saw this article [http://torrentfreak.com/isp-friendly-bittorrent-tracker-doubles-download-speeds-090823/]("http://torrentfreak.com/isp-friendly-bittorrent-tracker-doubles-download-speeds-090823/")
i won't deny that i think ISPs are part of the problem when it comes to torrents, they're remarkably efficient for distributing data and it's a legitimate protocol.

---

### Post by kpkeerthi on 2009-08-27
You are probably choking your router or modem with too many 'open' connections from your torrent client. Try to reduce it in your torrent client. With 1.5Mbps connection, I would not have more than 40 open connections.

---

### Post by drawkcab on 2009-08-27
You can also limit your max upload to 15kbps.

---

