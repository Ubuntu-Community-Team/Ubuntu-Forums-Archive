---
title: "using a port sniffer"
date: 2007-05-23
forum: The Cafe
---

### Post by maniacmusician on 2007-05-23
Hi,

I was a bit bored here in class so I thought I'd try to do something interesting; see what ports the school's network left open. For example, I know they close down AIM ports. So I decided to use Nast for this, which I found in the repos.

It has a "-S" flag, which is a port scanner. It asks me to point it to an IP to scan, and then asks for a port range. What IP address does it need to scan? The network gateway? It's a bit interesting, I never knew much about networking, so this is as good as a time as any to learn.

thanks.

---

### Post by ice60 on 2007-05-23
most people who know what they're doing use nmap i think. you could try a ping scan. maybe this :confused: -
nmap -sP 192.168.0.0/24

i found this in my bash history -
sudo nmap -n -sP -oA output_file 192.168.10.0/24

if you run that from your desktop you can then open the output_file.xml file in firefox. 

btw, they are local scans

---

