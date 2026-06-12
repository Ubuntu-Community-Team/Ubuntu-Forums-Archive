---
title: "SSH Access"
date: 2010-11-16
forum: Server Platforms
---

### Post by cbarron on 2010-11-16
Hey All,
I have a small SSH problem. I have 3 servers (2 of which are "new"). I have my ip linked to a domain name that I use for outside access to my servers, ftp, ect............I can access server1 on an outside connection but can not access the other 2 (yes ssh is setup and yes I did change the port numbers) I can use putty to access any of the 3 using their internal ip and port but cant access the 2 "new" ones using the domain and port # It says Connection Refused. Did I miss a setting or is there something else wrong?

The versions in Question are 10.04 lts server and 10.10 lts server

---

### Post by littlegreiger on 2010-11-17
You said you changed the ports, but did you forward those ports on your router? Seems simple, but you may have overlooked it, I know I have overlooked it a few times.

---

### Post by v1ad on 2010-11-17
yes i was about to say that, did you forward the ports? also check iptables maybe those ports are blocked.

---

### Post by cbarron on 2010-11-17
Shortly after posting as I was digging around I realized that the ports were set wrong in the router I had them flipped (set to the wrong ip ) So you both were right. THANKS for the replies.  Hopefully someone else can learn from my absent mindedness........:P

---

### Post by jpl888 on 2010-11-17
And it's worth noting even if you can't setup any more port forwardings for some reason that you could SSH into the machine that is accessible and then SSH from there into the other machines.

---

### Post by cbarron on 2010-11-17
> **jpl888 said:**
> And it's worth noting even if you can't setup any more port forwardings for some reason that you could SSH into the machine that is accessible and then SSH from there into the other machines.
Well do share...I would like to know how to do that!!!

---

### Post by jpl888 on 2010-11-18
Sorry I thought it was self explanatory.

Log into the machine that is available externally via SSH

e.g. ssh 86.86.86.86

Then once in there log into one of the other machines from the SSH session you just created.

e.g. ssh 192.168.0.1

It's like "chaining" SSH sessions or using the externally available machine as an SSH gateway that doesn't need any setup.

---

### Post by trundlenut on 2010-11-18
> **jpl888 said:**
> Sorry I thought it was self explanatory.

Log into the machine that is available externally via SSH

e.g. ssh 86.86.86.86

Then once in there log into one of the other machines from the SSH session you just created.

e.g. ssh 192.168.0.1

It's like "chaining" SSH sessions or using the externally available machine as an SSH gateway that doesn't need any setup.

This is particularly useful if you want to copy stuff from one server to another, it's a lot quicker than SSHing into the two servers separately and copying the data via your machine especially if that is connected by wireless.

---

### Post by jpl888 on 2010-11-18
Sorry for the off topic but is that avatar from "Charlton and the Wheelies" Trundlenut?

---

### Post by trundlenut on 2010-11-18
> **jpl888 said:**
> Sorry for the off topic but is that avatar from "Charlton and the Wheelies" Trundlenut?

Oh yes!

---

### Post by jpl888 on 2010-11-18
"Little old lady old" .... Nice! Takes me back. Have just gone foetal!

---

