---
title: "The hidden price of free software?"
date: 2007-09-16
forum: Server Platforms
---

### Post by viking777 on 2007-09-16
I am away from home at the moment and of necessity I am using a different ISP, modem and firewall. The main difference with the present setup is that the firewall is considerably more verbose than the one I use at home, ie. it gives out a lot more information.

One thing I have noticed over the past couple of weeks using it is that on many occasions when I connect to the Ubuntu update server  ([http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy in my case) I very often get a port scan on my machine. The addresses from which the port scan originate have one thing in common, they are all owned by Canonical Ltd. and if you connect to the addresses appear to be genuine repositories. The other thing of note is that although I am using a GB server, the scans rarely if ever occur when I connect in the mornings (ie. when America is asleep) but always occur if I connect in the evenings. I have been on many other sites during the past two weeks and have never seen a port scan from any other source other than the Ubuntu server. 

Now my firewall is doing its job in blocking these scans, so I am not overly worried about them, but it does leave several questions in my mind.

Firstly what is the intent or purpose of Canonical scanning my machine, have I inadvertantly agreed to this behaviour in some hitherto unread user agreement?

Is anyone else getting these port scans from this address?

Supposing my system was not secure, what information would they take from these scans, and what would they do with it?

Do they know that this is happening, or could it be that somebody has hijacked their server addresses to carry out port scans for themselves?

Or is this just the hidden price of free software??

Let me know.

---

### Post by loell on 2007-09-16
oh, this is interesting :) , can anybody confirm this?

---

### Post by steve.horsley on 2007-09-16
I am curious to see what is going on. I'll try to configure my router to allow portscans through, but can you post some logs from your firewall we can look at?

---

### Post by viking777 on 2007-09-16
Well unfortunately at the moment I can't send you any logs to look at because I didn't save them and as far as I know Firestarter doesn't save them by default so unless there is some log file somewhere that I don't know about (there is nothing in /var/log) I don't have any record at the moment. The situation is further complicated by the quality of the signal I am receiving, at the moment I am getting a gprs signal at about 5KB/s which is not suitable for downloading anything except email. I will have to wait until I can get another 3G signal before I can start downloading again and generate some logs for you to see. It may be several days or even weeks before this happens, but I will get a log to you as soon as I can.

---

### Post by viking777 on 2007-09-17
You know how it is when you get the toothache and it hurts like hell until the day before you get an appointment with the dentist?

Well that is almost exactly what has happened here. I found my 3G connection and I have just spent about 25 minutes on the ubuntu update server and I didn't get a single peep out of the firewall.

Oh well, I will continue to monitor the situation and if I have a recurrence of it I will save the log and post it.

Sorry about that.

---

### Post by steve.horsley on 2007-09-18
No Probs.

I tried a couple of times and couldn't see anything interesting happening. It never hurts to be careful though.

---

### Post by viking777 on 2007-09-20
Well, here you go then, what is all this about?
This is the contents of the saved log after one synaptic update. By this I mean a package update ie. reload package information. I didn't actually download any packages, only the headers.

I have no expertise in decoding firewall logs so perhaps what I am seeing is normal?

Let me know what you think.
```
Time:Sep 20 18:09:35 Direction: Unknown In:ppp0 Out: Port:52844 Source:ubuntu.datahop.it Destination:host167.msm.che.vodafone Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:09:59 Direction: Unknown In:ppp0 Out: Port:52843 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:10:06 Direction: Unknown In:ppp0 Out: Port:52844 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:10:55 Direction: Unknown In:ppp0 Out: Port:52843 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:11:06 Direction: Unknown In:ppp0 Out: Port:52844 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:11:54 Direction: Unknown In:ppp0 Out: Port:52843 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:12:05 Direction: Unknown In:ppp0 Out: Port:52844 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:12:54 Direction: Unknown In:ppp0 Out: Port:52843 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:13:06 Direction: Unknown In:ppp0 Out: Port:52844 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:13:54 Direction: Unknown In:ppp0 Out: Port:52843 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:14:06 Direction: Unknown In:ppp0 Out: Port:52844 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:14:54 Direction: Unknown In:ppp0 Out: Port:52843 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:15:06 Direction: Unknown In:ppp0 Out: Port:52844 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:15:54 Direction: Unknown In:ppp0 Out: Port:52843 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:16:06 Direction: Unknown In:ppp0 Out: Port:52844 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:26:27 Direction: Unknown In:ppp0 Out: Port:38200 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:26:29 Direction: Unknown In:ppp0 Out: Port:38194 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:26:32 Direction: Unknown In:ppp0 Out: Port:38195 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:26:34 Direction: Unknown In:ppp0 Out: Port:38196 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:26:43 Direction: Unknown In:ppp0 Out: Port:38200 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:26:47 Direction: Unknown In:ppp0 Out: Port:38201 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:26:48 Direction: Unknown In:ppp0 Out: Port:38202 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:26:53 Direction: Unknown In:ppp0 Out: Port:38203 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:26:55 Direction: Unknown In:ppp0 Out: Port:38190 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:26:56 Direction: Unknown In:ppp0 Out: Port:38204 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:26:56 Direction: Unknown In:ppp0 Out: Port:38192 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:26:57 Direction: Unknown In:ppp0 Out: Port:38193 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:26:58 Direction: Unknown In:ppp0 Out: Port:38205 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:27:00 Direction: Unknown In:ppp0 Out: Port:38194 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:27:02 Direction: Unknown In:ppp0 Out: Port:38195 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:27:04 Direction: Unknown In:ppp0 Out: Port:38196 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:27:13 Direction: Unknown In:ppp0 Out: Port:38200 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:27:15 Direction: Unknown In:ppp0 Out: Port:38201 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:27:16 Direction: Unknown In:ppp0 Out: Port:38202 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:27:25 Direction: Unknown In:ppp0 Out: Port:38203 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:27:26 Direction: Unknown In:ppp0 Out: Port:38204 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:27:29 Direction: Unknown In:ppp0 Out: Port:38205 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:27:54 Direction: Unknown In:ppp0 Out: Port:38190 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:27:55 Direction: Unknown In:ppp0 Out: Port:38193 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:27:57 Direction: Unknown In:ppp0 Out: Port:38192 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:28:01 Direction: Unknown In:ppp0 Out: Port:38194 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:28:04 Direction: Unknown In:ppp0 Out: Port:38195 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:28:06 Direction: Unknown In:ppp0 Out: Port:38196 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:28:13 Direction: Unknown In:ppp0 Out: Port:38201 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:28:14 Direction: Unknown In:ppp0 Out: Port:38200 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:28:14 Direction: Unknown In:ppp0 Out: Port:38202 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:28:55 Direction: Unknown In:ppp0 Out: Port:38193 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:28:56 Direction: Unknown In:ppp0 Out: Port:38192 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:29:12 Direction: Unknown In:ppp0 Out: Port:38201 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:29:13 Direction: Unknown In:ppp0 Out: Port:38200 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:29:14 Direction: Unknown In:ppp0 Out: Port:38202 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:30:12 Direction: Unknown In:ppp0 Out: Port:38201 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:30:13 Direction: Unknown In:ppp0 Out: Port:38200 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:30:14 Direction: Unknown In:ppp0 Out: Port:38202 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:30:25 Direction: Unknown In:ppp0 Out: Port:38203 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:30:26 Direction: Unknown In:ppp0 Out: Port:38204 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:31:13 Direction: Unknown In:ppp0 Out: Port:38201 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:31:14 Direction: Unknown In:ppp0 Out: Port:38200 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:31:14 Direction: Unknown In:ppp0 Out: Port:38202 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:31:38 Direction: Unknown In:ppp0 Out: Port:46914 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:32:01 Direction: Unknown In:ppp0 Out: Port:38194 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:32:04 Direction: Unknown In:ppp0 Out: Port:38195 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:32:05 Direction: Unknown In:ppp0 Out: Port:38196 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:32:12 Direction: Unknown In:ppp0 Out: Port:38201 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:32:13 Direction: Unknown In:ppp0 Out: Port:38200 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:32:13 Direction: Unknown In:ppp0 Out: Port:38202 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:32:27 Direction: Unknown In:ppp0 Out: Port:38205 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:32:37 Direction: Unknown In:ppp0 Out: Port:46914 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:32:53 Direction: Unknown In:ppp0 Out: Port:38190 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:32:54 Direction: Unknown In:ppp0 Out: Port:38193 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:32:55 Direction: Unknown In:ppp0 Out: Port:38192 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:33:03 Direction: Unknown In:ppp0 Out: Port:38195 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:33:06 Direction: Unknown In:ppp0 Out: Port:38196 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:33:11 Direction: Unknown In:ppp0 Out: Port:38201 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:33:11 Direction: Unknown In:ppp0 Out: Port:38200 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:33:12 Direction: Unknown In:ppp0 Out: Port:38202 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:33:27 Direction: Unknown In:ppp0 Out: Port:38205 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:33:37 Direction: Unknown In:ppp0 Out: Port:46914 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:33:55 Direction: Unknown In:ppp0 Out: Port:38190 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:33:55 Direction: Unknown In:ppp0 Out: Port:38193 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:33:57 Direction: Unknown In:ppp0 Out: Port:38192 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:34:02 Direction: Unknown In:ppp0 Out: Port:38195 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:34:04 Direction: Unknown In:ppp0 Out: Port:38196 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:34:12 Direction: Unknown In:ppp0 Out: Port:38201 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:34:12 Direction: Unknown In:ppp0 Out: Port:38200 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:34:13 Direction: Unknown In:ppp0 Out: Port:38202 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:34:24 Direction: Unknown In:ppp0 Out: Port:38203 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:34:24 Direction: Unknown In:ppp0 Out: Port:38204 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:34:26 Direction: Unknown In:ppp0 Out: Port:38205 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown
Time:Sep 20 18:34:37 Direction: Unknown In:ppp0 Out: Port:46914 Source:194.169.254.10 Destination:10.167.87.12 Length:1500 TOS:0x00 Protocol:TCP Service:Unknown

```

---

### Post by dendrobates on 2007-09-20
This does not look like a port scan.  

and 

194.169.254.10 is not a Canonical server, it is a mirror sponsored by datahop.it.

---

### Post by Brazen on 2007-09-20
yeah it looks more like the machine these logs are from is messed up, not handling packets correctly or something.  Is the 10.167.87.12 the ip address of your Ubuntu machine?

My guess is you are getting collisions and junk over your 3g signal (which would be expected) and this firewall or router or whatever is logging it.  Does this show up when you are downloading files from anywhere else?

---

### Post by steve.horsley on 2007-09-20
Looks very odd. But each port is addressed several times, and all packets are 1500 bytes. I suspect that some load-sharing gateway is getting its session info messed up and you are getting data packets (and retransmissions) intended for other downloaders. So other downloaders are probably cursing a flakey download service. A proper wireshark trace would provide more info, but you need to truncate the capture to say 60 bytes per packet.

---

### Post by viking777 on 2007-09-21
Thanks for the replies. Like I said before I am no expert in these matters so, as you say, it could just be messed up packets over my gprs/3g connection. I got an almost identical list again today. I know these are not Canonical servers, but the ones I had last week definitely were (although unfortunately I did not save the log of these). The ip address marked destination was indeed my ip at that time. I rarely if ever get results such as this when connected to other sites, only the Ubuntu update server.

Probably all quite innocent but it does make you wonder.

---

