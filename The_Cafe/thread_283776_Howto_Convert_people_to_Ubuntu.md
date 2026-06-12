---
title: "Howto: Convert people to Ubuntu"
date: 2006-10-24
forum: The Cafe
---

### Post by alecjw on 2006-10-24
Ok, I'm going to try and make a howto of all of the ways of converting people to ubuntu. Please post your own.

Here are a few of mine:

 * If you can get access to their computer, load it up with programs which will start up when they log on and slow their computer down a lot. I can only think of 2 right now: winzip and picozip.

 * Don't give them a choice! If it's their first computer, odn't give them the choice of Windows. Pretend it doesn't exist. Install Ubuntu on their computer when they get it. I bet your relatives ask you to set up their computer for them. When you do, just install Ubuntu. Then, the most important step: THROW AWAY THE WINDOZE RESTORE CD.

 * Show off XGL/Compiz/Beryl to them. They'll be dead jealous and will ask if you can make their computer do it, so you say, "Yes, but you'll need Ubuntu." So you install it for them.

---

### Post by DoctorMO on 2006-10-24
* Stick them in an ironmaiden, set fire to their village and torture their families until their surrender to the path of light.

---

### Post by jpkotta on 2006-10-24
> 
 * If you can get access to their computer, load it up with programs which will start up when they log on and slow their computer down a lot. I can only think of 2 right now: winzip and picozip.


This seems a bit malicious and unethical, eh?  Don't actively sabotage Windows, it will do fine on it's own.  Besides, I can easily write a simple shell script to bring a Unix machine to it's knees.  

The other two are OK, but you should be up front about things ("I'm going to replace Windows with Linux.  It's better, you'll thank me later.")

---

### Post by aysiu on 2006-10-24
You may want to check out this thread, too: [How To: Convert Windows Users to Ubuntu](http://ubuntuforums.org/showthread.php?t=58862)

---

### Post by Lord Illidan on 2006-10-24
>   * If you can get access to their computer, load it up with programs which will start up when they log on and slow their computer down a lot. I can only think of 2 right now: winzip and picozip.

Lame, man, lame.. just go and trawl the web, download as much malware and adware as you can, let it stew for a couple of days and wait for the cursing to begin.. then step in and offer them a linux cd.

>   Don't give them a choice! If it's their first computer, odn't give them the choice of Windows. Pretend it doesn't exist. Install Ubuntu on their computer when they get it. I bet your relatives ask you to set up their computer for them. When you do, just install Ubuntu. Then, the most important step: THROW AWAY THE WINDOZE RESTORE CD.

Good idea.

> Show off XGL/Compiz/Beryl to them. They'll be dead jealous and will ask if you can make their computer do it, so you say, "Yes, but you'll need Ubuntu." So you install it for them.
Just be prepared to wade in when it stops working/crashes/games wont' work etc..

---

### Post by alecjw on 2006-10-24
> **jpkotta said:**
> This seems a bit malicious and unethical, eh?  Don't actively sabotage Windows, it will do fine on it's own.  Besides, I can easily write a simple shell script to bring a Unix machine to it's knees.  

The other two are OK, but you should be up front about things ("I'm going to replace Windows with Linux.  It's better, you'll thank me later.")

"Oh, those 100 new icons in the taskbar? They're just useful programs which I installed for you."

Besides, as you said, they'll thank you later.

I'm planning to use this tactic on my parents' computer when they get it. They currently have an AMD XP 2000+ with 1/4GB RAM. It's running really slowly because all of the programs are fighting to run at startup. I bet it would run at the speed of light with Ubuntu, but it takes about 5 minutes to log on right now. When thay get their new Pentium D, dual core, it will work fast for a couple of days then slow down again. (Helped along by me). Thy'll say to me, "Why's this new computer running so slowly?" I'd check what programs are running and find, amongst others, norton insternat security and tell them, "It's your firewall." they'd reply, "But we need a firewall with all of these viruses and hackers." So I'd say, "Not if you used ubuntu."

Here's another idea. If you have Windows, type in the command:
```
shutdown -n <ip address of the person you want to convert> -r
```
And it will give them 30 seconds of warning before it restarts their computer. (provided that they don't have a firewall running) Then, just claim that, "It must have been a hacker. Windows is a security risk becuase it grants anyone access to your computer." Which is half true. There will be 2 possible outcomes: he/she gets a firewall, in whihc case you go throug the "Your computer's slow becuase you have a friewall" thing or he/she gets ubuntu.

---

### Post by Lord Illidan on 2006-10-24
Actually, firewalls are a need for Ubuntu too.. ip-tables is Ubuntu's firewall. What Ubuntu doesn't have is spyware and malware.

---

### Post by alecjw on 2006-10-24
> **Lord Illidan said:**
> Actually, firewalls are a need for Ubuntu too.. ip-tables is Ubuntu's firewall. What Ubuntu doesn't have is spyware and malware.

Which doesn't use up my entire processor :)

---

### Post by Lord Illidan on 2006-10-24
> **alecjw said:**
> Which doesn't use up my entire processor :)
point taken ;)

---

### Post by alecjw on 2006-10-24
Another one: This one is VERY evil though. Install VNC server on their computer and.... I expect that you know whaere this is going. In fact, I'll do it now. Then, If you're feeling daring, tell them their credit card number whihc you intercepted as they typed it in.

No. That's *too* evil. But I'll give it a go.

---

### Post by skymt on 2006-10-24
> **Lord Illidan said:**
> Actually, firewalls are a need for Ubuntu too.. ip-tables is Ubuntu's firewall. What Ubuntu doesn't have is spyware and malware.

No. Ubuntu has no open ports by default. Setting up an iptables firewall with a frontend like Firestarter does no harm, but no good either. There are very few cases where a software firewall is useful.

---

### Post by alecjw on 2006-10-24
> **skymt said:**
> No. Ubuntu has no open ports by default. Setting up an iptables firewall with a frontend like Firestarter does no harm, but no good either. There are very few cases where a software firewall is useful.

I thought iptables was the software which actaully kept those ports closed.

---

### Post by skymt on 2006-10-24
> **alecjw said:**
> I thought iptables was the software which actaully kept those ports closed.

A "closed" port is just a port that no programs are listening to. iptables is mainly useful (on a desktop, anyway) for limiting access to services (web, email, SSH, etc) to certain networks and computers. If you don't run services, your ports are closed.

---

### Post by raul_ on 2006-10-24
Or just let windows do it's job....

---

### Post by DoctorMO on 2006-10-24
alecjw, not quite iptables is a rule set for organising incomming connections. you hardly need a firewall if you have no ports to connect to. there is nothing to manage.

the ports are opened and managed by other parts of linux such as /etc/services.

---

### Post by Tux Aubrey on 2006-10-24
If someone asks me to help them set up or fix their machine I just say "Sorry, I don't do windows".  

After years of being the family geek, it usually starts a conversation in which the subject of Linux and Ubuntu comes up immediately.  A demo clinches it.

Mind you, I'm also very much in favour of burning their villages too.

---

### Post by DoctorMO on 2006-10-24
I think that will help, I see more and more family geeks moving towards ubuntu and thus in time they will adobt a no windows foobar rule too.

---

### Post by TheWizzard on 2006-10-24
> **skymt said:**
> No. Ubuntu has no open ports by default. Setting up an iptables firewall with a frontend like Firestarter does no harm, but no good either. There are very few cases where a software firewall is useful.

dude, that's ubuntu's default of iptables. you can *change* it with firestarter ot guarddog (my favourite).

---

### Post by skymt on 2006-10-24
> **TheWizzard said:**
> dude, that's ubuntu's default of iptables. you can *change* it with firestarter ot guarddog (my favourite).

Actually, iptables in Ubuntu defaults to letting everything through. It's secure because there are no services listening. Picture a big room. On one side of the room is a bunch of people (the Internet). The other side is empty (your computer with no services running). You don't want anyone on your side of the room to listen to the mindless jabber of the Internet side. Sure, you could put up a sound barrier (configure iptables), but why bother? There's nobody on your side to be bothered by the yak-yak-yak on the Internet side.

---

### Post by TheWizzard on 2006-10-25
> **skymt said:**
> Actually, iptables in Ubuntu defaults to letting everything through. It's secure because there are no services listening. 

ok, then i misunderstood :???:

---

