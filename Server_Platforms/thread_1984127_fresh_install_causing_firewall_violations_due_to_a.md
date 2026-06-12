---
title: "fresh install causing firewall violations due to active FTP outbound attempts"
date: 2012-05-21
forum: Server Platforms
---

### Post by kevpatts on 2012-05-21
Hey guys,

I pretty much a fresh install of Ubuntu server 10.04 with a few services installed. I'm getting reports from my firewall that this box is trying to start an active FTP session. The report is daily and it lists 10 violations every day from this box. Every day there is a different port, e.g. 46425/tcp, 46404/tcp, etc.

The address that it's trying to connect to seems to be the Ubuntu repositories.

What is causing these and can I change this process to use passive mode? I suspect it's the update process but during installation I set the box up not to process updates automatically.

Kevin

---

### Post by darkod on 2012-05-21
Any particular reason you have such strict rules for outbound traffic? Usually you would allow all outbound from your LAN to the outside.

The source port might be random but the destination port should be 21 if it's standard FTP. In that case you can consider allowing an outbound rule for destination port 21.

I'm not sure what actually happens if you say not to process updates automatically. I guess maybe it just doesn't install them, but it still needs to check in the repositories whether there are any updates.

Also, you selected not to install even the security updates? And in any case, even if you try to do manual updates, that firewall will block you as it is. You don't plan to install any updates ever?

---

### Post by kevpatts on 2012-05-21
Sorry, I should have been clearer. These are inbound connections from the reporitory server being blocked, not outbound. I believe they are the reverse connections associated with an active FTP connection.

We do plan to install updates, and standard aptitude commands work fine, that is why I am confused that something is causing this active FTP connection to be kicked off between 6 and 7am every morning.

Kevin

---

### Post by darkod on 2012-05-21
I'm not really an expert and can't help much. I guess someone else will jump in soon.

As far as inbound traffic is concerned, you would usually have inbound rules allowing RELATED and ESTABLISHED traffic from your outbound connections. So everything originating from your server will be allowed back.

But if you want to understand this better before allowing it, you'll have to wait for someone else. :)

---

### Post by kevpatts on 2012-05-21
Thanks for that. That is how I have it set up on my hardware firewall but the traffic is getting blocked by the software firewall (ufw (i.e. iptables)). The have set it up to default deny incoming and allow outgoing.

---

### Post by darkod on 2012-05-21
Double check ufw rules in /etc/ufw/before.rules. I think there are default rules to allow back established and related traffic.

So if you are using ufw it should allow the related incoming traffic.

---

### Post by kevpatts on 2012-05-21
Thanks darkod, my main question though is why is it doing this? I don't want to allow any inbound traffic for security reasons apart from what I specifically allow, even if it's related. I don't think it should require this as other distributions don't.

---

### Post by darkod on 2012-05-21
Well, here is where we go apart. Related traffic is related and that's good enough for me.

Especially if we are talking about incoming traffic related to updates, I can't see it as security risk. I don't know why you see it as such.

---

### Post by kevpatts on 2012-05-23
> **kevpatts said:**
> Thanks darkod, my main question though is why is it doing this? I don't want to allow any inbound traffic for security reasons apart from what I specifically allow, even if it's related. I don't think it should require this as other distributions don't.

Anyone else have any idea on this by any chance?

---

### Post by kevpatts on 2012-05-23
Thanks kellyone,

Why does it require incoming connections though?

---

### Post by roelforg on 2012-05-23
> **kevpatts said:**
> Thanks kellyone,
 
Why does it require incoming connections though?
 
A better question would be: Why is it using ftp anyhow?
Because the default settings only use http connections (as far as i know).

---

### Post by kevpatts on 2012-05-24
I'm only making the assumpton that this is active FTP becaus I don't know of any other protocol that would require inbound connections and it must be triggered by an outbaound connection because otherwise our firewall would not allow any traffic to this box. Smells very much like active FTP to me.

---

### Post by darkod on 2012-05-24
Why making assumptions? Wouldn't the log of the firewall show you details about the blocked traffic and the source/destination ports?

One of them might be a random high port but the other should be the port of the service doing the connection.

---

### Post by kevpatts on 2012-05-24
> **darkod said:**
> Why making assumptions? Wouldn't the log of the firewall show you details about the blocked traffic and the source/destination ports?

One of them might be a random high port but the other should be the port of the service doing the connection.

It does:
```
May 24 06:36:19 web1 kernel: [743887.599227] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=63386 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743887.648841] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=63584 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743887.734915] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=63892 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743887.894253] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=64633 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743887.949044] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=64892 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743888.038814] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=65254 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743888.062485] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=65339 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743888.092443] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=65442 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743888.141446] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=42 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743888.207648] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=232 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0
```

---

### Post by roelforg on 2012-05-24
> **kevpatts said:**
> It does:
```
May 24 06:36:19 web1 kernel: [743887.599227] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=63386 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743887.648841] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=63584 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743887.734915] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=63892 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743887.894253] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=64633 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743887.949044] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=64892 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743888.038814] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=65254 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743888.062485] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=65339 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743888.092443] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=65442 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743888.141446] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=42 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0 
May 24 06:36:19 web1 kernel: [743888.207648] [UFW BLOCK] IN=bond0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=193.1.193.69 DST=192.168.55.76 LEN=1500 TOS=0x00 PREC=0x00 TTL=58 ID=232 PROTO=TCP SPT=80 DPT=46655 WINDOW=86 RES=0x00 ACK URGP=0
```
 
Am i reading this log wrong, or is ufw blocking the http-response from ie.archive.ubuntu.com?
If i'm right, it's blocking you from updating the package list (or a package).

---

### Post by kevpatts on 2012-05-24
> **roelforg said:**
> Am i reading this log wrong, or is ufw blocking the http-response from ie.archive.ubuntu.com?
If i'm right, it's blocking you from updating the package list (or a package).

This is exactly what's happening (although I'm not sure that it's the http-response), but it ONLY happens during a job in /etc/cron.daily. Otherwise I can run apt-get update and I can use apt-get to install packages without an issue.

---

### Post by darkod on 2012-05-24
That's HTTP all right. SPT=80, source port 80.

---

### Post by kevpatts on 2012-05-24
Okay, we've really got nowhere here so far!

I'm still no closer to finding out why this traffic is trying to come in to my box...

---

### Post by roelforg on 2012-05-24
> **kevpatts said:**
> This is exactly what's happening (although I'm not sure that it's the http-response), but it ONLY happens during a job in /etc/cron.daily. Otherwise I can run apt-get update and I can use apt-get to install packages without an issue.
 
Wait... You didn't mention the cronjob.
Which one is causing problems?

---

### Post by kevpatts on 2012-05-24
Sorry, I only noticed that now. All I can see from the logs is that it kicks off the cron.daily tasks and then those errors appear. I don't know which task is causing them. There's an apt, an aptitude and a dpkg job in there. The atp job is the only thing that seems to do a significant amount of work.

---

### Post by SeijiSensei on 2012-05-24
/etc/cron.daily/apt appears to check for updates every night.  Why don't you run this from the command line with sudo and watch the firewall log?

Why in the world are you blocking related and established traffic?  How is anyone supposed to communicate with remote sites?  I have a rule that blocks traffic with source port 80, but only to defeat spoofed packets.  (Actually these packets would be blocked anyway but with this rule they don't fill up the logs.)  It sits well below the standard "ESTABLISHED,RELATED" rule, so legitimate replies to my requests are accepted but not spoofs of such replies.

"Stateful packet inspection," which iptables uses, is designed precisely to make sure reply traffic matches up with known requests.  Not allowing established and related traffic thwarts the whole point of SPI.

---

### Post by roelforg on 2012-05-24
> **kevpatts said:**
> Sorry, I only noticed that now. All I can see from the logs is that it kicks off the cron.daily tasks and then those errors appear. I don't know which task is causing them. There's an apt, an aptitude and a dpkg job in there. The atp job is the only thing that seems to do a significant amount of work.

/etc/cron.daily/apt seems to update the package list and repo keys.
This might've caused the firewall to think it's doing bad stuff.

---

### Post by kevpatts on 2012-06-27
Sorry for the delay on this everyone, I was on annual leave for a while.

Okay, I'm not intentionally blocking Established/Related traffic. I set up ufw with "default deny incoming" and "allow https" and this is what's being blocked.

This is for a production web server, not for an office type situation, so there should be minimal outbound requests.

The machine has been set up not to perform automatic updates.

---

### Post by kevpatts on 2012-06-27
This morning:
```
count source                  host    action     port/protocol
10    ubuntu.ftp.heanet.ie    web2    [BLOCK]    48221/tcp
1     zaurac.canonical.com    web1    [BLOCK]    53252/tcp
9     ubuntu.ftp.heanet.ie    web1    [BLOCK]    53342/tcp
```

there are two web boxes, web1 and web2.

---

