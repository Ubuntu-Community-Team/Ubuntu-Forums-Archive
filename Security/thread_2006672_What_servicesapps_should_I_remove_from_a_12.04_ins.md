---
title: "What services/apps should I remove from a 12.04 installation?"
date: 2012-06-19
forum: Security
---

### Post by nrundy on 2012-06-19
I just installed 12.04. What apps and services should I uninstall to claim more resources and improve overall system security?


[LIST]
[*]I do not have any local networks
[*]I do not do any file sharing
[*]I do not use VPN or do any remote connections
[*]I do not use UbuntuOne or any other file syncing backup service
[*]I do not use any "cloud" services
[*]I do not do any social networking like Facebook or Twitter or LinkedIn
[/LIST]
All I do is write text documents, use Firefox to surf web, and listen to music stored on my harddrive.


So what do you recommend that I uninstall from Ubuntu 12.04 Desktop install?

---

### Post by *^kyfds( on 2012-06-19
there isn't really much you can do if you're trying to speed up your machine or free memory.

however, I'd only suggest removing ubuntu one if you're not using it anyway.

---

### Post by *^kyfds( on 2012-06-19
there is transmission.

It's a bittorrent client.

if you're not torrenting anything, legally of course ;) then you may as well remove it too.

---

### Post by sudodus on 2012-06-19
The big improvement in speeding up would be to choose a desktop environment with smaller foot-print

Lubuntu with ultra-light LXDE or
Xubuntu with light XFCE

In order to increase security I suggest that you read and apply the information in this link
[[COLOR="Red"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

---

### Post by nrundy on 2012-06-19
> **sudodus said:**
> The big improvement in speeding up would be to choose a desktop environment with smaller foot-print

Lubuntu with ultra-light LXDE or
Xubuntu with light XFCE

In order to increase security I suggest that you read and apply the information in this link
[[COLOR=Red]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

I'm not looking to improve performance per se. I simply want to remove items that I never use. This can result in less things running in the background, but whether it improves performance or not doesn't matter. Security wise, if something provides a service that can be exploited (eg. file sharing), why not uninstall it if I NEVER use it?

This is what I am inquiring about.

---

### Post by nrundy on 2012-06-19
> **Thehumorouscheese said:**
> there isn't really much you can do if you're trying to speed up your machine or free memory.

however, I'd only suggest removing ubuntu one if you're not using it anyway.

There seems to be a lot of ubuntu one related packages installed. Is there one "installation" that basically comprises "Ubuntu One" that you know of? Or does uninstalling Ubuntu One entail uninstalling several different things?


> **Thehumorouscheese said:**
> there is transmission.

It's a bittorrent client.

if you're not torrenting anything, legally of course :wink: then you may as well remove it too.

Good one! Thanks.

---

### Post by *^kyfds( on 2012-06-19
i believe ubuntu one is one singular software.

and about transmission - i agree with you. if you never use it, uninstall it.

although it doesn't really pose any security risk to ubuntu.
linux is pretty much virus proof.

---

### Post by *^kyfds( on 2012-06-19
i think that's everything.

The only other things bundled with ubuntu is thunderbird, which i assume you'll be using.

As I said, relatively few things are actually bundled with ubuntu.

---

### Post by Soul-Sing on 2012-06-19
nrundy good question. (And a naise linkage to that brainstorm idea.)
- I disable avahi (server)
- cups(d) (server)
- ubuntu-one (via synaptic)
- dnsmasq
- I would like to remove geo-ip thing, but breaks the data server.
- Disable bluetooth

thats it...

---

### Post by nrundy on 2012-06-19
> **leoquant said:**
> nrundy good question. (And a naise linkage to that brainstorm idea.)
- I disable avahi (server)
- cups(d) (server)
- ubuntu-one (via synaptic)
- dnsmasq
- I would like to remove geo-ip thing, but breaks the data server.
- Disable bluetooth

thats it...

Yes. I have already removed some things but wanted to hear what others said. I have removed

Avahi
cups
music and video lenses 
dnsmasq I disabled by commenting out
geo-ip I am stuck with (can't uninstall without also removing time indicator)

How did you remove Ubuntu-One and dnsmasq? What are the exact names to remove?

---

### Post by Soul-Sing on 2012-06-19
> How did you remove Ubuntu-One and dnsmasq? What are the exact names to remove?

dnsmasq as you did. So I disabled it.(Not removed it, sorry bout that)
Ubuntu-one; I did some googling. But I was alarmed about my computer connecting to amazon. (The server where ubuntu-one is hosted.) I did go so far in disabling ubuntu-one services/client, that this behaviour stopped.

---

### Post by nrundy on 2012-07-12
VINO looks like another that can be uninstalled. This is an app that lets people see your desktop from a remote computer.

---

