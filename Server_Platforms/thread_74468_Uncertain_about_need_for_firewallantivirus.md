---
title: "Uncertain about need for firewall/antivirus"
date: 2005-10-11
forum: Server Platforms
---

### Post by tmtjjhnsn on 2005-10-11
I am a Linux newbie.  I recently installed Ubuntu 5.04.  I have read a couple of posts indicating that Ubuntu has no open ports, and therefore has no need for a firewall.  I have read other posts discussing the merits of different firewalls in Ubuntu.  I noticed that Mepis includes the Guarddog firewall in its distro.  Is there a definitive answer as to whether a firewall is necessary?

I understand that Linux is not susceptible to Windows viruses, but could we not be unknowingly passing viruses along by email to our poor Windows friends if we are not scanning our incoming and forwarded messages?

Thanks for any help you can give me in solving these issues.  

t

---

### Post by Zelut on 2005-10-11
Well if you've got your computer(s) behind a router than you're probably fine without a firewall.  I have firestarter (apt-get install firestarter) installed on my home server but that is only because I have a few ports forwarded to that box.  I do notice hack attempts from time to time, but firestarter helps me out with that.  If you are directly connected to the outside, ie; direct connection to a modem I would suggest installing a firewall.

As far as virus/spyware go I wouldn't worry about it.  I've had Ubuntu installed on three of my computers since April and they're all still running just as well as they were on day 1.  NOT something you'd find with windows without antivirus :)

---

### Post by drogoh on 2005-10-12
[QUOTE=kuyaedz]
As far as virus/spyware go I wouldn't worry about it.  I've had Ubuntu installed on three of my computers since April and they're all still running just as well as they were on day 1.  NOT something you'd find with windows without antivirus :)[/QUOTE]

I would worry about security exploits.  I still see people trying to exploit outdated versions of software on ALL of my Linux and Unix machines to run little IRC bots and rootkit me.

On a different note, I have three computers running Windows without antivirus or firewalling and there has been not one piece of adware/spyware and I can tout not having a single virus infection in my time of owning computers.  Two of these Windows installs are over a year old.

---

### Post by wargames on 2005-10-12
[QUOTE=drogoh]On a different note, I have three computers running Windows without antivirus or firewalling and there has been not one piece of adware/spyware and I can tout not having a single virus infection in my time of owning computers.  Two of these Windows installs are over a year old.[/QUOTE]


Hi Billy G.!
Sorry couldn't resist.
Are your Windows systems even connected to the internet? Could you explain how you check your Windows systems for viruses and spyware/malware when you don't have any software to scan and detect for these types of intrusions? Also, there has been numerous studies conducted to clearly show that a Windows system connected to the internet without a firewall is a setting duck and will be compromised in little time. So if your Windows systems are connected to the internet without firewall protection then how are they not able to get attacked or intruded on?

---

### Post by xequence on 2005-10-12
[QUOTE=drogoh]

On a different note, I have three computers running Windows without antivirus or firewalling and there has been not one piece of adware/spyware and I can tout not having a single virus infection in my time of owning computers.  Two of these Windows installs are over a year old.[/QUOTE]

Well, that is quite amazing, since it took 12 minutes to get a fresh XP installation loaded up with spyware. I tried NOT to get it infected...

---

### Post by Samuel on 2005-10-12
its usually about 5 mins after i reinstall XP that my machine is hit with a messenger spam, easy to fix but still a security exploit on a windows box.

but back to the original subject, how important really is anti virus software on a normal home PC running Ubuntu? i have never had any problems and as i understand it no significant damage can be done by a virus on a linux box unless your logged in as root.

 just how popular are linux virii and spyware exactley? anyone know?

---

### Post by drogoh on 2005-10-12
[QUOTE=wargames]Hi Billy G.!
Sorry couldn't resist.
Are your Windows systems even connected to the internet? Could you explain how you check your Windows systems for viruses and spyware/malware when you don't have any software to scan and detect for these types of intrusions? Also, there has been numerous studies conducted to clearly show that a Windows system connected to the internet without a firewall is a setting duck and will be compromised in little time. So if your Windows systems are connected to the internet without firewall protection then how are they not able to get attacked or intruded on?[/QUOTE]

I did say they are running without firewalling.  I did not say, however, my network was not secure.  Unless you're inside my network you can't even see my Windows computers.  They're used for very specific purposes, but all have the capability of connecting out.  One is for work, so only work applications run on it, all of the network capable applications meeting or exceeding HIPAA requirements.  One is my high end monster I use for games.  Only commercial games, no "free download" things, and certainly nothing that is "free" (as in manure).  The other is too slow to do anything major, so it just sits there and is off about as much as it is on.

How am I not blowing smoke out my ass?

1) I watch what I install and don't install random things "just because it's neat".
2) I avoid IE for everything except one thing, and that is Windows updates.
3) I don't run anything that accepts connections and is therefore prone to exploitation.

---

### Post by wylfing on 2005-10-12
I am not sure drogoh is giving good advice. If you have Windows machines on your internal network, you need to be running protective utilities. Malicious software can hide out on your Linux system and infect your Windows machines again and again.

If, on the other hand, you are running only Linux (and if you have, say, a Linksys WRT54G to hide behind you are running Linux on that as well -- hint: get a copy of HyperWRT and install it on the router) you are more or less not susceptible to viruses or malware. Nevertheless, it is still a good idea to run a firewall on anything that has "server" features installed, for example apache, postfix, sshd, etc., you really should install some firewalling software to prevent anything untoward from happening. Do as kuyaedz says and install firestarter.

---

### Post by drogoh on 2005-10-12
[QUOTE=wylfing]I am not sure drogoh is giving good advice. If you have Windows machines on your internal network, you need to be running protective utilities. Malicious software can hide out on your Linux system and infect your Windows machines again and again.
[/QUOTE]

What I said is not advice; I did not in any way say "run without antivirus/firewalling".  I also highly doubt malicious software is "hiding out" on any of my machines.  What works for me may not work for the next user.  I run my ship the way I do because of one thing: experience.

My Unix security is masochistic to say the least.  However, I don't give Windows the opportunity to pick up crap like honey on velcro, so I feel I don't need to pay Symantec or McAfee to sit there and look pretty while nothing happens.  **IF** I had any open services on any Windows machine they sure as hell would be locked down tighter than Fort Knox.

---

### Post by wylfing on 2005-10-12
[QUOTE=drogoh]I don't give Windows the opportunity to pick up crap like honey on velcro, so I feel I don't need to pay Symantec or McAfee to sit there and look pretty while nothing happens.  **IF** I had any open services on any Windows machine they sure as hell would be locked down tighter than Fort Knox.[/QUOTE]

I'm the same. I wasn't criticizing you, only couching what you said so that a newbie doesn't take a wrong turn. (Stand back, I work in marketing :) ). Better that appropriate expectations take the front seat and technical accuracy takes the back.

---

### Post by bionnaki on 2005-10-13
> and if you have, say, a Linksys WRT54G to hide behind you are running Linux on that as well -- hint: get a copy of HyperWRT and install it on the router

is hyperWRT really worth it, security-wise?
I have all my proper ports forwarded & my static IPs set...
and I dont want to fiddle much (not very network-saavy).

---

### Post by wylfing on 2005-10-13
For my money, replacing the stock firmware of your WRT54G is very worthwhile. 99.5% of all attacks against that device are going to be based on exploiting a weakness in the stock firmware.

But even if security is not your bag, the extra features HyperWRT adds is well worth the 30-second effort of installing it.

---

### Post by tmtjjhnsn on 2005-10-13
Thanks for the interesting information and discussion.  I have decided to install a firewall.  I use a dial-up connection with no router.  I am still wondering, though, about antivirus software.  Should we be scanning our Linux machines to prevent the spread of Windows viruses to Windows users?

t

---

### Post by wylfing on 2005-10-13
Unless you are running a server for Windows clients, there's next to zero chance you're going to be infecting them. One common exception is forwarded email. Even though you can't catch a Windows virus travelling with an email, it's still possible to pass it on. But still, that is Windows users' problem. Let them handle it.

---

### Post by ~J~ on 2005-10-13
So would you say that my Netgear 834G router/firewall would pretty much secure my PC?

---

### Post by wylfing on 2005-10-14
That depends on two things: (1) do you run any server stuff? (2) do you forward ports from the router to your computer? If the answer to either of those questions is "yes" then I'd recommend running firestarter to keep out the script kiddies. Viruses I don't worry about.

You might think you don't run any server stuff, but Postfix, aMule, SSH, CUPS, and Samba all fall into this category.

---

