---
title: "I share a connection with a hacked computer"
date: 2011-06-09
forum: Security
---

### Post by Libertydude on 2011-06-09
Hi, let me explain my situation. I am 17 and still living with my parents and we share a wireless router, anyway my mom's laptop running windows is obviously infected (but nothing is ever detected, rootkit maybe?). And my mom doesn't understand computer security and won't let me touch her laptop. So fixing it is out.

Anyway my laptop is running windows and keeps showing signs of being infected even after I do a clean install. I think the virus spreads through the router, to my clean laptop.

So if I install Ubuntu on my laptop which shares a connection with her infected laptop what can the hacker do to me?

---

### Post by Kinstonian on 2011-06-09
What leads you to believe of all the explanations for computer problems that her computer is "obviously infected?"  I'm not saying you're wrong, I'm just asking what evidence you have because I have none from what you've said so far.

If your mom does any kind of online banking or shopping you should explain to her that her financial information could be at serious risk if her computer is in fact compromised.  Try showing her this [youtube video](http://www.youtube.com/watch?v=CzdBCDPETxk).  With over 55,000 variants of malware released every day, AV software is falling behind and isn't able to detect a lot of malware these days.  AV companies just can't create signatures for all of it.  So just because AV software doesn't detect anything, should definitely not be interpreted as there is no problem.

If you use Ubuntu and follow the best practices, you will probably be fine.

---

### Post by Libertydude on 2011-06-09
> **Kinstonian said:**
> What leads you to believe of all the explanations for computer problems that her computer is "obviously infected?"  I'm not saying you're wrong, I'm just asking what evidence you have because I have none from what you've said so far.

If your mom does any kind of online banking or shopping you should explain to her that her financial information could be at serious risk if her computer is in fact compromised.  Try showing her this [youtube video]("http://www.youtube.com/watch?v=CzdBCDPETxk").  With over 55,000 variants of malware released every day, AV software is falling behind and isn't able to detect a lot of malware these days.  AV companies just can't create signatures for all of it.  So just because AV software doesn't detect anything, should definitely not be interpreted as there is no problem.

If you use Ubuntu and follow the best practices, you will probably be fine.
No point in even trying to explain it to her, and she just checks her email no online banking or anything.

But let's assume this hacker has *total* control over her laptop, could the hacker access my laptop?

---

### Post by Kinstonian on 2011-06-09
> **Libertydude said:**
> No point in even trying to explain it to her, and she just checks her email no online banking or anything.


Still not a valid reason not to care about your own security.  _If it's compromised_ there are other things her computer could be used for.  Things ranging from sending spam to compromising other computers to distributing child porn.

When your connected to the Internet, other people's security often depends on your own security.  For example, her computer could be hacked and email addresses harvested from her address book and used to send her friends malware which seems like it came from her.

> But let's assume this hacker has *total* control over her laptop, could the hacker access my laptop?

Right now, sure.  Malware is often capable of spreading through a network, and has been for years.  Gone are the days when malware spread mostly through floppy disks.  Now they mostly use the network to infect more people around the world.

Assuming her computer is infected, you could reconfigure your firewall to block all traffic from her computer.  You should also unplug her computer from the network until you can install all your patches after reinstalling.  However, first I'd try a Windows security forum like [BleepingComputer](http://www.bleepingcomputer.com/forums/forum103.html) to see if anyone there can determine whether your computer, or your moms is infected.  Not sure on how thorough forums like those are, but they seem to manage.

Good luck!

---

### Post by Libertydude on 2011-06-09
Is there a linux firewall with a GUI?

---

### Post by Libertydude on 2011-06-09
Also, if I never connect my ubuntu laptop to the internet when she is connected am I safe?

Can the hacker sort of *lurk* in the modem or wireless router?

---

### Post by dFlyer on 2011-06-09
Before even proceeding I would explain to her that if she is compromised and her computer is used to distribute child porn, she could get in a lot of trouble. You also have not answered what make you think she is compromised or infected. That information is important to know. Linux is not windows and to get hacked is rare but not unheard of. A virus I wouldn't worry too much about.

---

### Post by Libertydude on 2011-06-09
> **dFlyer said:**
> Before even proceeding I would explain to her that if she is compromised and her computer is used to distribute child porn, she could get in a lot of trouble. You also have not answered what make you think she is compromised or infected. That information is important to know. Linux is not windows and to get hacked is rare but not unheard of. A virus I wouldn't worry too much about.
Sorry, I am pretty sure it is infected because it is EXTREMELY slow, EXTREMELY buggy, always crashing, and shows some pretty weird behavior.

If I install ubuntu over her windows and mine, would this totally make us safe from our current problem?

---

### Post by sammiev on 2011-06-09
> **dFlyer said:**
> Before even proceeding I would explain to her that if she is compromised and her computer is used to distribute child porn, she could get in a lot of trouble. You also have not answered what make you think she is compromised or infected. That information is important to know. Linux is not windows and to get hacked is rare but not unheard of. A virus I wouldn't worry too much about.

+1 on this post. Need more answers to say the least. Great post dFlyer! :)

---

### Post by dFlyer on 2011-06-09
> **Libertydude said:**
> Sorry, I am pretty sure it is infected because it is EXTREMELY slow, EXTREMELY buggy, always crashing, and shows some pretty weird behavior.

If I install ubuntu over her windows and mine, would this totally make us safe from our current problem?

What you have listed could be many other problems, buggy software, failing hardware, slow memory just to name a few. If you can't get your mothers system check you should have your system check to determine if it has been infected or compromised, and if it has let your mother know, so she could get her system fixed. I would say if you run linux, you will have a less chance of being hacked and almost 0 chance of being infected with a virus since most virus are windows related. From my own experience I've never been hacked or have had a virus in the past 15+ years running linux.

---

### Post by dFlyer on 2011-06-09
Oh yes, one other thing I can say is that if it's faulty hardware, installing linux will not fix the problem but only make them worst. Windows is more tolerant of hd and memory errors, where linux just will not run and if it does you will hate it, because of all the problems faulty hardware causes. My advise is to burn a live desktop cd and check both your memory and use disk utility to check your hd.

---

### Post by Libertydude on 2011-06-09
> **dFlyer said:**
> What you have listed could be many other problems, buggy software, failing hardware, slow memory just to name a few. If you can't get your mothers system check you should have your system check to determine if it has been infected or compromised, and if it has let your mother know, so she could get her system fixed. I would say if you run linux, you will have a less chance of being hacked and almost 0 chance of being infected with a virus since most virus are windows related. From my own experience I've never been hacked or have had a virus in the past 15+ years running linux.
What about just not connecting while she is? 

And is there a linux tutorial about blocking her IP address? And could a hacker crack the firewall?

---

### Post by dFlyer on 2011-06-09
Nothing is impossible. If you want to run linux, run linux. An OS is a personal choice. I can't guarantee someone will not try to hack you. I can assure you that I've never been hacked or have had a virus running linux. My daughter who runs windows has had virus in the past and she is using my wifi. I do not run a virus scanner because it's a waste of resources. My firewall is ufw which is standard. According to my testing on the web the firewall is stealth. Again the choice is yours. Do as you wish, but I would rule out having been hack or virus before doing anything so your mother can get her system fixed regardless of what you choose to do.

---

### Post by Thewhistlingwind on 2011-06-09
> **Libertydude said:**
> What about just not connecting while she is? 

And is there a linux tutorial about blocking her IP address? And could a hacker crack the firewall?

In that order:

Quit being stupid, if she's that damn resistant you really should just tell her that the dark recesses of the internet are probably lurking on her computer and that she should fix it. (DDos, Spam, things much worse,etc.)

Not that I know of, i'll write one for you.

Use arp -a to get the local Ip's on your network.
Block that IP using some kind of firewall utility.

No. Also, Cracker, Not Hacker.

All that aside, let me be clear here, if you do install Linux, and the box gets infected, please send me a copy of the binary, such a novelty would look great in a museum.

---

### Post by Libertydude on 2011-06-09
> **dFlyer said:**
> Nothing is impossible. If you want to run linux, run linux. An OS is a personal choice. I can't guarantee someone will not try to hack you. I can assure you that I've never been hacked or have had a virus running linux. My daughter who runs windows has had virus in the past and she is using my wifi. I do not run a virus scanner because it's a waste of resources. My firewall is ufw which is standard. According to my testing on the web the firewall is stealth. Again the choice is yours. Do as you wish, but I would rule out having been hack or virus before doing anything so your mother can get her system fixed regardless of what you choose to do.
True, but back when I was 13 I tried to upgrade her old laptop from Widows 98 to Windows XP, anyway everything went well until I ran into a driver problem and rendered it unusable, not my fault tho.

So now I am basically forbidden from using her new laptop, she would never let me touch it. Her infection is her problem now. And she is also sort of paranoid, so if I said "hay mom, your infected" she would probably cancel the internet and I can't let that happen.

So, like I asked before am I safe if I just don't connect when she does?

---

### Post by lisati on 2011-06-09
> **Libertydude said:**
> If I install ubuntu over her windows and mine, would this totally make us safe from our current problem?

Unfortunately, no operating system can protect us completely from being human, with the many opportunities it brings for things to go wrong.

Try not to pressure your mum too much: having a good relationship with her is something valuable.

---

### Post by dFlyer on 2011-06-09
No answer to that question. What's to prevent her from connecting while your connected. Nothing. Again run linux if you wish or stay with windows if that's what you want. But no one on earth can guarantee what you want to know. The odds are very low for a hack and 0 for virus on linux. As posted by someone earlier, if it happens send me a copy, as it would be very rare indeed.

---

### Post by Libertydude on 2011-06-09
> **dFlyer said:**
> No answer to that question. What's to prevent her from connecting while your connected. Nothing. Again run linux if you wish or stay with windows if that's what you want. But no one on earth can guarantee what you want to know. The odds are very low for a hack and 0 for virus on linux. As posted by someone earlier, if it happens send me a copy, as it would be very rare indeed.
Cool, let me ask you something else, if I connect to a public wifi, could my ubuntu laptop get hacked by someone else connected? If so, how long would it take? Just a hypothetical question.

---

### Post by Thewhistlingwind on 2011-06-09
> **Libertydude said:**
> Cool, let me ask you something else, if I connect to a public wifi, could my ubuntu laptop get hacked by someone else connected? If so, how long would it take? Just a hypothetical question.

Sure, if your ports are open with services listening. Time taken to crack would depend upon the strength of your password, and what service and authentication scheme your using.

I'd be more worried about them doing a man in the middle or sniffing your traffic though to be honest.

EDIT: Ports open is the default, but no services are listening, until they are it's white noise and wasted bandwidth.
EDIT2: Also, understand that in many cases time taken to crack means "Eleventy gazillion years11!1!11!". It could also mean "About three weeks", "A day or two", and "Five seconds, lol."

---

### Post by dFlyer on 2011-06-09
My advice is you worry too much for any OS. I travel a lot because I'm retired and use wifi where every I go. Once again, I've never been hacked or have had a virus. My advice is to let it go. I can't guarantee you will never get hacked with linux and I can't guarantee you will never have a virus or malware. I can only share my experience, and that is [COLOR="Red"]IT'S NEVER HAPPENED TO ME IN 15+ YEARS[/COLOR], sorry about the shouting

---

### Post by Libertydude on 2011-06-10
> **dFlyer said:**
> My advice is you worry too much for any OS. I travel a lot because I'm retired and use wifi where every I go. Once again, I've never been hacked or have had a virus. My advice is to let it go. I can't guarantee you will never get hacked with linux and I can't guarantee you will never have a virus or malware. I can only share my experience, and that is [COLOR=Red]IT'S NEVER HAPPENED TO ME IN 15+ YEARS[/COLOR], sorry about the shouting
No problem, it is just that in a couple months I am going to be transmitting my social security number and I don't want it to get stolen.

To be honest I think I will only connect when she is offline, yeah I know I am paranoid. ;)

---

### Post by dFlyer on 2011-06-10
If your going to be transmitting your ssn, I would guess it would be in email. Guess what bad move. Unencrypted email is not secure.

---

### Post by Thewhistlingwind on 2011-06-10
> **Libertydude said:**
> No problem, it is just that in a couple months I am going to be transmitting my social security number and I don't want it to get stolen.

To be honest I think I will only connect when she is offline, yeah I know I am paranoid. ;)

That's a different game entirely. Like I said earlier, you want to be aware of man-in-the-middle attacks, make sure your using SSH, etc.

EDIT: If your transmitting your SSN over email without openPGP/etc, I pity the fool.

---

### Post by Libertydude on 2011-06-10
> **dFlyer said:**
> If your going to be transmitting your ssn, I would guess it would be in email. Guess what bad move. Unencrypted email is not secure.
No, it is on Best Buy's website for their job application.

---

### Post by dFlyer on 2011-06-10
Hopefully it's a secured web site. My guess is that if it's best buy it will be.

---

### Post by Libertydude on 2011-06-10
> **dFlyer said:**
> Hopefully it's a secured web site. My guess is that if it's best buy it will be.
Yep, it is.

But without trying to sound OCDish, do you think my plan is 99% safe?

1) Install Ubuntu on my laptop
2) Only connect when she is offline

---

### Post by Thewhistlingwind on 2011-06-10
> **Libertydude said:**
> No, it is on Best Buy's website for their job application.

Well, when I say this changes the game entirely, I mean it.

The problem here is that if your router firmware IS indeed infected no amount of firewalling will save you, cause that router has to touch your packets.

If you want to get an idea of where your packets are going, on Linux use the command:

traceroute <Name of website>

Replace name of website, without the brackets, with a domain name or IP address of your choice, and it will show all the hops to get there. You should notice that your router is always on the list.

SSH can help somewhat, by tunneling your connection, but I'm not sure if your packets are secure even against your router when using it.

---

### Post by Libertydude on 2011-06-10
> **Thewhistlingwind said:**
> Well, when I say this changes the game entirely, I mean it.

The problem here is that if your router firmware IS indeed infected no amount of firewalling will save you, cause that router has to touch your packets.

If you want to get an idea of where your packets are going, on Linux use the command:

traceroute <Name of website>

Replace name of website, without the brackets, with a domain name or IP address of your choice, and it will show all the hops to get there. You should notice that your router is always on the list.

SSH can help somewhat, by tunneling your connection, but I'm not sure if your packets are secure even against your router when using it.
What is the odds of my router being infected?

---

### Post by Thewhistlingwind on 2011-06-10
> **Libertydude said:**
> What is the odds of my router being infected?

I don't know. Really.

If I had to guess though, a proper infection would require a vulnerability in your router firmware.

So, if your willing to install Linux over this, you may be served well by googling for outstanding vulnerabilities in your router. 

You could also flash it with one of the open implementations, but that's probably SERIOUS overkill. (Not to mention the hell your mom will raise if you "Break the internet".) 

My estimate of the chances could be summed up as: Low, But possible.

EDIT: A second opinion would be nice of course.
EDIT2: > **emiller12345 said:**
> Hopefully you have not been using a default  password on your router's control panel.  If so then your odds are  probably quite high I would think.  Usually they like to change settings  on the router like the IP of your dns servers.

*Facepalm* I didn't even THINK of that. No offense to your mom, but if she's the sysadmin, you probably got cracked like a starred window(s).

---

### Post by emiller12345 on 2011-06-10
> **Libertydude said:**
> What is the odds of my router being infected?
Hopefully you have not been using a default password on your router's control panel.  If so then your odds are probably quite high I would think.  Usually they like to change settings on the router like the IP of your dns servers.

---

### Post by dFlyer on 2011-06-10
I really believe your question has been answered. You need to review all post and decide what you want to do. No body can guarantee that bad thing will not happen. With linux the chances are very low. Should you decide to install linux, remember it's not windows and don't expect it to work like windows. First download a live desktop cd and decide if linux is what you want, and to be sure all your hardware works with linux. If so have fun and take it slow. You should first back up all important data that you want to keep. I would say clone your disk but if your worried it's been compromised a clone will only carry your problems over on a reinstall. Since virus infect executable files you should not have to worry about them with linux since they only run on windows. You should scan any file you want to transfer to linux so you don't infect other windows users should you decide to share file with other window users.

---

### Post by Libertydude on 2011-06-10
> **emiller12345 said:**
> Hopefully you have not been using a default password on your router's control panel.  If so then your odds are probably quite high I would think.  Usually they like to change settings on the router like the IP of your dns servers.
Oh snap, I forgot to change it. <blush>

I am the network admin, I am a failure. :(

I personally think flashing the firmware is over kill, but I will change the password tonight.

> (Not to mention the hell your mom will raise if you "Break the internet"
Dude, you soooooooo hit the nail on the head, this is what really frightens me from implementing any serious security on the network besides an anti-virus program and anti-spyware.

---

### Post by Libertydude on 2011-06-10
> **dFlyer said:**
> I really believe your question has been answered. You need to review all post and decide what you want to do. No body can guarantee that bad thing will not happen. With linux the chances are very low. Should you decide to install linux, remember it's not windows and don't expect it to work like windows. First download a live desktop cd and decide if linux is what you want, and to be sure all your hardware works with linux. If so have fun and take it slow. You should first back up all important data that you want to keep. I would say clone your disk but if your worried it's been compromised a clone will only carry your problems over on a reinstall. Since virus infect executable files you should not have to worry about them with linux since they only run on windows. You should scan any file you want to transfer to linux so you don't infect other windows users should you decide to share file with other window users.
Thanks for the info, but I have been using Linux since I was 13, but security has always sorta scared me. :D

But in conclusion, the consensus is I am 99% safe from being hacked, despite being connected to a compromised computer?

---

### Post by Thewhistlingwind on 2011-06-10
> **Libertydude said:**
> 

But in conclusion, the consensus is I am 99% safe from being hacked, despite being connected to a compromised computer?

In this case, it would appear so.

If your running Linux.

EDIT: Eh, block her packets anyway. Never too careful.....
EDIT2: And theres no running services connected to ports.
EDIT3: Well, that's my input into the consensus, second and third opinions please.

---

### Post by Libertydude on 2011-06-10
> In this case, it would appear so.

If your running Linux.
Great, this is a load off of my mind.

> EDIT: Eh, block her packets anyway. Never too careful.....
How do I do this?

> EDIT2: And theres no running services connected to ports.
When it comes to networking I am a total noob, please explain this to me. :)

---

### Post by Thewhistlingwind on 2011-06-10
> **Libertydude said:**
> 
How do I do this?


When it comes to networking I am a total noob, please explain this to me. :)

In that order:

Read the UFW manpage, it would take too long to explain the ufw/Iptables rules. To get local IP addresses use arp -a.

Imagine an electrical outlet. On your side, you plug into the socket, and you receive electricity from an external source on the other side.

Networking sockets work the same way. An application plugs into a socket, then receives packets from an external network connection on the port, what it does with them after that depends on the application.

In the case of things like Open SSH and VNC, these things will allow external logins into your computer over a network. Obviously if the authentication on these services are cracked, you'll have a break-in on your hands.

---

### Post by Libertydude on 2011-06-10
> **Thewhistlingwind said:**
> In that order:

Read the UFW manpage, it would take too long to explain the ufw/Iptables rules. To get local IP addresses use arp -a.

Imagine an electrical outlet. On your side, you plug into the socket, and you receive electricity from an external source on the other side.

Networking sockets work the same way. An application plugs into a socket, then receives packets from an external network connection on the port, what it does with them after that depends on the application.

In the case of things like Open SSH and VNC, these things will allow external logins into your computer over a network. Obviously if the authentication on these services are cracked, you'll have a break-in on your hands.
I still don't understand. :(

---

### Post by Thewhistlingwind on 2011-06-10
> **Libertydude said:**
> I still don't understand. :(

Listening service <<<>>> | <<< External source

Brackets = traffic
| = port

Get the idea?

Now:

SSH/etc take commands from these external sources and execute them.

---

### Post by Libertydude on 2011-06-10
> Listening service <<<>>> | <<< External source

Brackets = traffic
| = port

Get the idea?

Now:

SSH/etc take commands from these external sources and execute them.
Yes, I get it now, but how do I close my laptop's ports?

---

### Post by Thewhistlingwind on 2011-06-10
> **Libertydude said:**
> Yes, I get it now, but how do I close my laptop's ports?

Enable UFW, but before that set some default rules and block your moms local IP.

Of course, if you don't have any listening services, then to quote myself from earlier "It's just white noise and wasted bandwidth." (The hack attempts, not the firewall.) However, it's good practice to turn it on anyway.

man ufw

ufw enable

---

### Post by Libertydude on 2011-06-10
> **Thewhistlingwind said:**
> Enable UFW, but before that set some default rules and block your moms local IP.

Of course, if you don't have any listening services, then to quote myself from earlier "It's just white noise and wasted bandwidth." (The hack attempts, not the firewall.) However, it's good practice to turn it on anyway.

man ufw

ufw enable
As of now, I do not have ubuntu installed, I will try it when it is. Thank you for the help. :)

---

### Post by Lars Noodén on 2011-06-10
> **Libertydude said:**
> Sorry, I am pretty sure it is infected because it is EXTREMELY slow, EXTREMELY buggy, always crashing, and shows some pretty weird behavior.

I'm not sure that's anything other than the usually MS Windows experience. It's what moved me to Linux at home, not just at work.
> **Libertydude said:**
> 
If I install ubuntu over her windows and mine, would this totally make us safe from our current problem?

Yes. That would make you totally save from the current problem, and a few others, too.  I would recommend taking a look at Kubuntu, Lubuntu or even Ubuntu Studio.  Find something that she likes.

---

### Post by u.rusty on 2011-06-10
> **emiller12345 said:**
> Hopefully you have not been using a default password on your router's control panel.  If so then your odds are probably quite high I would think.  Usually they like to change settings on the router like the IP of your dns servers.

Quite high that someone could easily access the settings in his router, probably not so high that it has been 'infected'.

---

### Post by emiller12345 on 2011-06-11
> **u.rusty said:**
> Quite high that someone could easily access the settings in his router, probably not so high that it has been 'infected'.
"Default Router Password Vulnerability (Belkin)" -- google it
This is how easy it is to mess with someones router with a default password, without even compromising a computer directly.
EVERYONE should change their default password. Regardless of the vendor.

---

### Post by sammiev on 2011-06-11
> **emiller12345 said:**
> "Default Router Password Vulnerability (Belkin)" -- google it
This is how easy it is to mess with someones router with a default password, without even compromising a computer directly.
EVERYONE should change their default password. Regardless of the vendor.

Isn't it the first thing one would do? :o

---

### Post by desertdog on 2011-06-14
If you want to learn more about computer security, I suggest you start listening to the Security Now podcast with Steve Gibson and Leo LaPort.

Also, your mother's computer slowness could be due to hard drive errors. Steve Gibson has a product called SpinRite, which you can purchase for about $70 or $80 at [www.grc.com](www.grc.com) and make a bootable CD or USB stick. It is expensive, but can fix a lot of hard drive problems.

---

