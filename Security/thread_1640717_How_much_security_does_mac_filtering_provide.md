---
title: "How much security does mac filtering provide?"
date: 2010-12-08
forum: Security
---

### Post by mehmeh12 on 2010-12-08
On the wireless router i have it has something called mac filtering-if i enable this will my wireless connection be more secure?

To test it out how do i change the mac address of my ubuntu computer?

---

### Post by Joe of loath on 2010-12-08
It's incredibly easy to spoof a mac address, you can download a program called macchanger which will do it in a couple of seconds.

---

### Post by TheFr00n on 2010-12-08
I agree with Joe. It will increase your security in that it will stop the old lady next door accidentally auto-connecting to your network when she turns on her laptop, but it will in no way hinder a determined individual intent on gatecrashing.

So it's not like its pointless. But it's pretty much like saying No Entry Without A Green Hat. All one has to do is get a hat that looks Green, and you're in.

---

### Post by Dave_L on 2010-12-08
So someone monitoring the network traffic can easily determine the MAC addresses in use, even if the network is encrypted?

---

### Post by TheFr00n on 2010-12-08
In a matter of moments, and without any particular skill.

---

### Post by HermanAB on 2010-12-08
Howdy,

The MAC is in every packet header.  Read the IEEE 802 spec.

You can change the MAC with ifconfig. So MAC filtering is probably a good defence against your little kid sister.

---

### Post by TheFr00n on 2010-12-08
I don't know, man. My sister is kinda hardcore.

---

### Post by HermanAB on 2010-12-08
Well, once your sister turned 12 and dropped her Geek Barbie, all bets are off - then you better encrypt everything with AES256.

---

### Post by bodhi.zazen on 2010-12-08
Your question is easy to answer, but security is a broad issue.

Personally there is only so much you can do with securing wireless, as your packets are transmitted over the air, and thus your network is open.

If you want to increase security, you need to use encryption.

ssl - https, ssh, kerberos, etc

If you really  want a secure network, you need to use a wired connection and restrict access to the router.

---

### Post by FuturePilot on 2010-12-08
It will probably stop a scriptkiddy but for anyone that actually knows what they're doing it's extremely easy to get around.

---

### Post by anomie on 2010-12-08
[QUOTE=mehmeh12]On the wireless router i have it has something called mac filtering-if i enable this will my wireless connection be more secure?[/QUOTE]

No. 

Use WPA2-PSK with a *strong* key. That's about the best you'll be able to do with minimal effort + a typical home router/access point.

---

### Post by CharlesA on 2010-12-08
> **anomie said:**
> No. 

Use WPA2-PSK with a *strong* key. That's about the best you'll be able to do with minimal effort + a typical home router/access point.

Use AES, instead of TKIP as well.

MAC filtering is trivial to get around.

---

### Post by mehmeh12 on 2010-12-09
> **Joe of loath said:**
> It's incredibly easy to spoof a mac address, you can download a program called macchanger which will do it in a couple of seconds.

i downloaded this from the repos but i cant find the gui anywhere-i take it that it has be be run from the terminal? where might i find these commands?

---

### Post by Joe of loath on 2010-12-09
```
man macchanger
``` same as for any other program.

---

### Post by azwar on 2010-12-10
> **mehmeh12 said:**
> i downloaded this from the repos but i cant find the gui anywhere-i take it that it has be be run from the terminal? where might i find these commands?

Run it as ```
gksu macchanger-gtk
```

---

### Post by mehmeh12 on 2010-12-10
> **Joe of loath said:**
> ```
man macchanger
``` same as for any other program.
 
would this work with the commands on this page [http://linux.die.net/man/1/macchanger](http://linux.die.net/man/1/macchanger)  ?

---

### Post by mehmeh12 on 2010-12-10
> **azwar said:**
> Run it as ```
gksu macchanger-gtk
```

Thanks thats really a easy to use tool!!!

if i change my mac to something else different to the default will anything critical change-will i find myself being hacked or say will system settings be all changed or my home folder become corrupted? 

How do i confirm that the mac has changed as well? is there a website i can visit that tells my current mac address?

---

### Post by HermanAB on 2010-12-10
Howdy,

You don't need special programs to change or verify the MAC.  It can all be done with ifconfig.
$ man ifconfig

---

### Post by bodhi.zazen on 2010-12-10
> **hermanab said:**
> howdy,

you don't need special programs to change or verify the mac.  It can all be done with ifconfig.
$ man ifconfig

+1

---

