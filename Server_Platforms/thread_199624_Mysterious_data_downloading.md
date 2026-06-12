---
title: "Mysterious data downloading"
date: 2006-06-19
forum: Server Platforms
---

### Post by akudewan on 2006-06-19
The other day, at night, I was doing nothing, just staring at gkrellm. Now, I noticed that some data is being downloaded at a steady 4kBps. At first I just thought it must be a cron job, like apt-get update or something. But I have a 128kbps connection, and whenever something is downloaded, I get a full speed of around 13-14kBps, even during apt-get update

Next, I decided to see whats up, and I ran the command "sudo lsof -Pni" to see all connections. I expected to see an external IP address, but I just saw the usual processes, no external IP was listed, and nothing out of the ordinary was established on the daemons listening on ports. I started to get more suspicious. I started killing daemons that I thought might be causing this: smbd, nmbd, vsftpd, ircd, and some others. But the download didn't stop.

Even though I have a cable connection, my IP address is dynamic. So I simply logged off the internet and then logged in again. The download now stopped, and I had a new IP address.

After this experience, I have decided to install firestarter. It seems to be very easy to use.

But I wonder what that mysterious download was! And why was it downloading at a lower speed? ps -A also showed nothing out of the ordinary and gkrellm showed "1 user".

Strange, isn't it ?

---

### Post by rbalfour on 2006-06-19
Someone pinging you...trying ssh brute force....there are a number of things.
The best way is protect your systems. Firewall and check the logs for attempts.

---

### Post by Azrael on 2006-06-20
Next time... use Ethereal. It's a 'sniffer' that will see all network packets reaching and leaving your network card.

---

### Post by akudewan on 2006-06-20
Thanks for the replies :)

---

### Post by MJN on 2006-06-22
A nice alternative to Ethereal is **IPTraf** (it's in the repositories). Nowhere near as powerful but a nice simple console-based sniffer which is great for keeping track of connections - doesn't show the actual packets like Ethereal but rather the actual connections in place and various stats-per-connection to boot.

Well worth having on your 'tool belt'.

Mathew

---

### Post by akudewan on 2006-06-23
Thanks Matthew. Actually I found ethereal very complicated to use. IPtraf is much easier.

---

