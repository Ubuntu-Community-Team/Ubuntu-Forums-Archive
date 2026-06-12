---
title: "unknown web traffic?"
date: 2006-01-01
forum: Server Platforms
---

### Post by wargames on 2006-01-01
Ok, I wasn't for sure where to ask this so here it goes....

I'm on dial-up and after I connect, I start Firefox 1.5 and start to browse like usual. Then after the page loads, I noticed that my Network monitor (icon with 2 monitors) lights up and stays lighted up and my external modem lights also start blinking even though I'm not downloading, and Firefox has already rendered the page. So I close Firefox and noticed that there is still traffic on my connection even though I'm not doing anything anymore. So I disconnect and then reconnect and start Firefox again and load a different page, and again, this unknown traffic starts up again even though Firefox has rendered the whole page. So again I close out Firefox and the web traffic is still going. I opened up the Details to gnome-ppp and it appears as if my connection is receiveing data, even though I'm not doing anything.

How can I check to see what application is accessing the web? Have I been hacked? Is this a virus or worm or some spyware? It's done this in the past few days and now I'm worried that someone or something has hacked my system.

I ran chkrootkit from the terminal and everything checks out ok, but then again, if someone has hacked my system then they could make that output say anything.

Any ideas? Is my system screwed? :confused:

---

### Post by alinuxfan on 2006-01-01
try installing fiestarter...a GUI frontend for IPTABLES and see what it logs....you can set it up to be as restrictive as you want....i found it a lot easier than trying to type it all in myself (with help from the linux documentation project of course)

---

### Post by wargames on 2006-01-01
[QUOTE=alinuxfan]try installing fiestarter...a GUI frontend for IPTABLES and see what it logs....you can set it up to be as restrictive as you want....i found it a lot easier than trying to type it all in myself (with help from the linux documentation project of course)[/QUOTE]

I have firestarter already installed. I checked the Events tab and there was nothing listed there. I have not changed anything in Firestarter, just ran the wizard and chose ppp for my connection. As far as that, I don't know how to edit IPTABLES or even why I have this unknown traffic or what to do about it.

Right now, I'm posting from my Windows machine, until someone can help me with this, because I don't trust my Ubuntu system being connected to the internet right now.

Any suggestions as to what is going on and why this unknown traffic seemed to start a few days ago?

---

### Post by wargames on 2006-01-02
Could it be possilbe that the Updates checker in Firefox 1.5 is going out and checking for updates automatically and that this might explain the unknown web traffic. Does Firefox 1.5 call home on a regular basis to check for updates?

I decided to check this. I disconnected from the internet. Ran "sudo firefox" and under Preferences--->Advance tab--->Update tab and unchecked these:

Automatically check for updates to:
Firefox
Installed Extensions and Themes
Search Engines

Then I closed this window, and then closed Firefox. Now I reconnected and launched Firefox as I usually do as a user. So far, no unknown web traffic, but I'll have to test this the next few days to see if the unknown web traffic returns. Maybe this was just Firefox calling home, but that still makes me wonder why it didn't stop when I closed Firefox before?

Any suggestions or advice would be great.

---

### Post by lotusleaf on 2006-01-02
[QUOTE=wargames]Any suggestions as to what is going on and why this unknown traffic seemed to start a few days ago?[/QUOTE]

Since you're using Firestarter, go into the outgoing section and switch to restrictive, and before you add the ports to open, sit there and look at the connections being logged in outgoing and look them up if you're curious.

---

### Post by wargames on 2006-01-02
I believe I've found out what was accessing the internet.

It started up again today so I let it run for a couple of minutes and then my Update Manager icon popped up and stated that I had updates available. I didn't know that Update Manager was set to automattically check for updates. I thought that you had to do apt-get update or hit the Reload button in Update Manager to check for updates. I went and unchecked the option to automattically check for updates in the Update Manager so this should fix it. I don't like programs going out on their own to check for updates, because I usually handle that myself.

Thanks for the replies and help.

---

