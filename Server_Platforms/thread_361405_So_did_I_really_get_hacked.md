---
title: "So did I really get hacked?"
date: 2007-02-14
forum: Server Platforms
---

### Post by Troubled on 2007-02-14
I was browsing on the  web the other day and stumbled on to Netrek, an old POSIX multiplayer shooter game. I wanted to try it out, so I downloaded it and eventually got it to work. The program connected me to a server, and gave me a game interface, so I played it for a while, until I saw the following message appear on the screen:

Player K0 to ALL: Damn llamas, I hate llamas.

This was kind of baffling, as there was of course nothing referencing llamas in the game, so I typed in:

Player K2 to ALL: What llamas?

Then I got the reply that I was hoping not to get:

Player K0 to ALL: It's K2's login name.
Player K0 to ALL: Hey, that's you!

So I had to ask:

Player K2 to ALL: How the ---- do you know that?

Player K5 to ALL: He hacked your box, lolxorz.

So I'm wondering, has this guy really hacked into my computer? My game login name is something very generic -- Player, actually -- and I never chatted into the box before. I see that the server broadcasts each player's ISP openly, but surely not their login names!

My hostname isn't the same as my username, either. How could this person have gotten this information? Admittedly, I don't have a firewall installed, after reading all of the posts on this forum that dictated, "Linux is totally secure; iptables takes care of everything; you don't need a firewall or an antivirus."

Could this person have actually hacked into my system, and what harm could he have done? And if he did do something, what can I do to prevent this from happening again?

---

### Post by Troubled on 2007-02-14
bump!

---

### Post by Perfect Storm on 2007-02-14
Moved it here, though it might not fit 100% I guess there's a bigger chance to get an answer here.

---

### Post by Sqwishy on 2007-02-14
I really doubt you were hacked, sometimes i do stuff like that to noobs and tell them i hacked them or something. It's probobly soemthing in the game that you don't understand, if someone was actually hacking you he probobly wouldn't be 0mfg i h4x0rd joo l0Lz

---

### Post by ComplexNumber on 2007-02-14
personally, i don't think you've been hacked, but i don't have an intimate knowedge of security. when you install ubuntu, your login name is the same as your computer name with "-desktop" appended to it. well, thats if you didnt change that to something different, that is. it may have something to do with that, but can't be sure.


> 
Admittedly, I don't have a firewall installed
i bet you do ;). iptables is the actual firewall.  i think its installed by default, but  not 100% certain. there is a firewall frontend called firestarter which allows you to configure iptables via a GUI.
you still need a firewall whatever the OS.

---

### Post by moma on 2007-02-14
No, your machine has not been hacked or cracked.

[iptables...]("http://www.netfilter.org/projects/iptables/index.html") firewall is activated by default and would protect you against hacking attempts.

if you run Ubuntu/GNOME then [Firestarter...]("http://www.fs-security.com/") is a good (firewall) **front-end** that work upon the iptables' rule set.

$ [COLOR="SeaGreen"]sudo apt-get install firestarter[/COLOR]
And look in the System menu.   Note: You are safe without Firestarter too but it makes easier to change the iptables rules (open and close ports etc). 

Install "Guarddog" firewall if you run Kubuntu/KDE.  Guarddog is also in the repository.
----

The two log entries
[SIZE="6"]> 02/14/2007 11:07:55 AM computer kernel [17183847.572000] ISO 9660 Extensions: Microsoft Joliet Level 3
02/14/2007 11:07:55 AM computer kernel [17183847.648000] ISO 9660 Extensions: RRIP_1991A[/SIZE]
Nothing to worry about. You have put a bootable CD (with ISO filesystem image) on to the cdrom.

---

### Post by lamego on 2007-02-14
I don't know Netrek but several clients report the unix/linux user id when connecting, this is the most probable scenario, you have been a joke target.

---

