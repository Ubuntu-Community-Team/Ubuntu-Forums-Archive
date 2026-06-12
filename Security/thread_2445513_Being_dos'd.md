---
title: "Being dos'd"
date: 2020-06-15
forum: Security
---

### Post by youmustnot on 2020-06-15
Hello 

i hope someone can help us.
I rent a hertz server running ubunutu 18.04 and we run a number of Rust game servers on this. 
A few ban's here and there and we get a chap saying if we dont unblock him he'll dos the server, figured it was just a joke!

However, our server keeps getting pounded with all the game servers running extremely slow and i cant log into putty.

We've emailed hertz who have said they have detected an attack on our server and that they have email the attacker to ask them to stop?!
and if it continues they'll block the IP.
Thats all well and good I guess, but I'd rather get the tools i need to do it myself right away!
bringing the server to its knee's like this is killing our game servers and we've only just started to get good numbers :/

Very thankful for any advice.

---

### Post by CelticWarrior on 2020-06-15
No experience with such servers and even less with that hosting service but I think you're looking for Fail2Ban.

---

### Post by QIII on 2020-06-15
[This]("https://www.digitalocean.com/community/tutorials/how-to-protect-ssh-with-fail2ban-on-ubuntu-14-04") article about Fail2Ban is a bit old, but Digital Ocean has some really good tutorials and instructions.

I don't think there will be substantial changes between 14.04 and 18.04, but it might be worthwhile to do some further research.

---

### Post by youmustnot on 2020-06-15
hertz have just messaged us to say our server has been used to attack someone.

They want us to tell them, 

1) how this happened
2) how we are going to prevent it 

or they will block the server's IP

my god, totally stitched up here. 

I dont know what log to point fail2ban at we dont have apache on this server, its just 3 game servers and sftp.

---

### Post by QIII on 2020-06-15
Are you running nginx?

---

### Post by youmustnot on 2020-06-15
nope, no webservers

---

### Post by QIII on 2020-06-15
So you are exposing your naked game servers unprotected?  Your attacker is taking advantage of that.  Your OS is an open door with a sign that says "Compromise me".

---

### Post by youmustnot on 2020-06-15
how would you protect them?

I'll be honest I just followed a guide from LGSM 
[https://linuxgsm.com/](https://linuxgsm.com/)

what sort of protection should i get?
I'm more than willing to do the work!
I just dont know what to do

---

### Post by QIII on 2020-06-15
I would not expose a server (the machine) to the web without a well-protected web server.  Then, I'd put the game server behind that.

If LGSM does not operate under that environment, I'd bag the whole thing and find something else to do with my spare time.  You have exposed your OS and machine to just the sort of thing you have encountered.  The DoS might be the least of the things the attacker might have done.  You've basically been walking through a public park without a stitch of clothing on.

Both Apache and nginx can be hardened to reduce the threat of DoS.

---

### Post by TheFu on 2020-06-15
> **QIII said:**
> So you are exposing your naked game servers unprotected?  Your attacker is taking advantage of that.  Your OS is an open door with a sign that says "Compromise me".

+1000!!!

A) Don't allow connections from anywhere connections cannot be trusted.  i currently block about 10K subnets around the world from my web servers and about 4K from email SMTP.  i use **ipset** for this.

B) Always use a reverse proxy to ensure only valid URLs and requests even get to the the real server running any programs.  Nginx can look at the URLs, use regex patterns to allow validated requests and block all others. Nginx is just 1 option. There are others.

C) there are many levels of DDOS attacks.  if they are targeted just at a server process then after you setup A and B, look at fail2ban.  if they are attacking from only 1 ip or 20 ips, why haven't you blocked those already?

D) if your administrative access is using passwords, you've already failed as an admin. if anywhere in the world can access your sftp or ssh connection, just shut down the system and move to a different service already. Only use key-based connections for admin use. Don't use passwords.

E) Sounds like the system has been compromised.  Time to wipe and restore from a backup you made PRiOR, secure it, run some hacking attempts yourself, get 100 friends to hack it, secure against all the found issues, then bring up that new system for your users. Don't allow the world access until you are positive it is secure enough and won't be cracked  again in 5 min..  in short, nuke it for orbit since nothing on that system can be trusted anymore.  This time setup a secure system, on a different ip, patch it at least weekly and have daily, automatic, versioned, backups.  These aren't optional.

F) for $20 someone can pay a DDOS group to DDOS systems for 24 hrs sufficiently to really cost your provider $$$$$.  Many would just fire you and take the system down.  Some people would use this as a way to switch to a service like cloudflare who can handle huge amounts of bandwidth that most cheap DDOS attempts wouldn't impact  For $100, a much heavier DDOS can be ordered.  For $2000, pretty much everyone but FB and Google would be hurt.

There are anti-DDOS services, but those aren't cheap.  They are mostly used by online gambling sites the week before huge sporting events to prevent any betting by competitors.  They basically have huge pipes, analyze all inbound traffic before forwarding it off to the real servers unless it contains malicious content that abuses server resources. 
Around 2010, a south central Asian country was knocked offline through a DDOS of only 45Mbps.  At the time, the entire country only had a T3 connection to the internet - DS-3 is 35Mbps.  Basically, a single home computer in South Korea could have effectively DDOS'd that entire country. [https://en.wikipedia.org/wiki/2010_cyberattacks_on_Myanmar](https://en.wikipedia.org/wiki/2010_cyberattacks_on_Myanmar)

To block a small subnet from any Ubuntu system, something like this:
```
$ sudo ufw deny from 185.234.216.135/24
```

When you get over 50 rules like that, you'll probably want to switch to ipset which is much more efficient. it is also more complex to use. i block subnets, not single ips. My thought process is that any provider who doesn't proactively handle bad people needs all their subnets blocked.  MSFT corporate subnets were DDOS'ng one of my sites about 8 yrs ago, so i blocked  MSFT.  Those rules stand today.  
```
sudo /sbin/iptables -I INPUT -s  168.61.0.0/16  -j DROP
sudo /sbin/iptables -I INPUT -s  168.62.0.0/15   -j DROP

```

For servers, there is not type a, b, c answer.  There are guides that talk big picture ideas for you to fill in with 20-50 commands for each idea based on YOUR system and requirements.

---

### Post by youmustnot on 2020-06-15
I've shutdown all the game servers and installed apache2

the machine is still almost unreachable and it's saturating our 1gigbit connection

---

### Post by Skaperen on 2020-06-15
in a day or 2 or 4 the attacker might notice the  servers are down and end the attacks.  in the mean time, have you noticed what IP address they come from?  all the same or many "random" ones?

anything you do on your side of the link will still have the attack packets flooding your link.  maybe it is the whole machine that has been compromised.  does the problem still persist when you unplug the machine?

---

### Post by TheFu on 2020-06-15
> **youmustnot said:**
> I've shutdown all the game servers and installed apache2

the machine is still almost unreachable and it's saturating our 1gigbit connection
Why add apache?
Find the source ips and block those. if it is over 100 different ips, you'll be playing whack-a-mole until they get bored or hertz fires you.

[https://www.tecmint.com/linux-iptables-firewall-rules-examples-commands/](https://www.tecmint.com/linux-iptables-firewall-rules-examples-commands/) has commonly used firewall rules.  Note the drop and flood prevention and too many connections per ip rules.  There are lots of different full firewall scripts too.

---

### Post by youmustnot on 2020-06-15
thanks for your input/help guys. 

I just wanted to play a game with friends! turns into a massive ballache, all be it by my own lack of opsec :(
Ive installed a firewall and blocked all ports other than one, the server is responsive again. just downloading some config files and i'll have to wipe and do a hell of a lot of reading!

Thanks again guys, sorry I'm not on my game with this stuff, the information provided will help me for game server rev2!

---

### Post by youmustnot on 2020-06-15
i dont know how to find there IP's 

apache: QIII said to put the game server behind it?!
[COLOR=#990303]
[/COLOR]

---

### Post by TheFu on 2020-06-15
> **youmustnot said:**
> i dont know how to find there IP's 

apache: QIII said to put the game server behind it?!
 

The log files should have all connected ips.  "game server" doesn't tell us much.  There are hundreds of those and how to secure each is different.  System logs are usually in /var/log/ somewhere.  i use egrep to search them all at once.

Whether any web server can help protect any game server depends on the sort of traffic.  Nothing will be install and it magically will work.  You'll need to become very familiar with all the valid incoming requests and block anything that doesn't match those patterns.  That is in addition to all the firewall stuff above.

if your Linux-fu is weak, this can take weeks of effort.

---

### Post by youmustnot on 2020-06-15
the game server is a rust server.

the attack has started again..... they must be buying more bandwidth or something :(
the firewall doesnt seem to be helping

---

### Post by TheFu on 2020-06-15
> **youmustnot said:**
> thanks for your input/help guys. 

I just wanted to play a game with friends! turns into a massive ballache, all be it by my own lack of opsec :(
Ive installed a firewall and blocked all ports other than one, the server is responsive again. just downloading some config files and i'll have to wipe and do a hell of a lot of reading!

Thanks again guys, sorry I'm not on my game with this stuff, the information provided will help me for game server rev2!

If you just want to play some games with friends, then only allow those specific subnets any access. Go with a default deny rule, then have your friends provide their IP addresses so you can allow them in. That's the safest way to start, while you are still learning.

BTW, when I was starting out with Unix, I got hacked too. This was decades ago when there weren't even 1% of the bad people on the internet that we have today.  There's a bunch to know and different knowledge is needed if you run servers at home vs at some VPS provider.  Regardless, perhaps this outline will help?  [https://blog.jdpfu.com/2016/10/04/lamp-server-security](https://blog.jdpfu.com/2016/10/04/lamp-server-security) It is a general list of things with a few outside links. No commands, just ideas.

---

### Post by EuclideanCoffee on 2020-06-15
I'm sorry you're being DDOS'd.

You do not need a web server to protect your data.

Fail2ban is good, but it won't protect you from ddos unless you understand how it works.

Can you shut down your servers now, so you can spend the time you need to address the issue?

Once you shut down, we'll go over a diagram on how to setup your server.

---

### Post by youmustnot on 2020-06-15
thanks I will have a read. 

after the first attack and after i installed the firewall i fired up a game server.
the attack is happening again so ive closed all but one port again.
But i still have people playing on the server? 
i thought the firewall would have stopped the attack with only one port open and kicked the players on the game server? 

ufw default deny incoming
ufw allow 22
ufw enable
"Firewall is active and enabled on system startup"

---

### Post by youmustnot on 2020-06-15
> **EuclideanCoffee said:**
> I'm sorry you're being DDOS'd.

You do not need a web server to protect your data.

Fail2ban is good, but it won't protect you from ddos unless you understand how it works.

Can you shut down your servers now, so you can spend the time you need to address the issue?

Once you shut down, we'll go over a diagram on how to setup your server.

Yes!

---

### Post by QIII on 2020-06-15
> **EuclideanCoffee said:**
> You do not need a web server to protect your data.


Strictly speaking, you don't.  But you can add defense in depth.  As I said, that's what *I* would do.

---

### Post by TheFu on 2020-06-15
> **youmustnot said:**
>  
the attack is happening again so ive closed all but one port again. 

They attack is always happening if you allow the source IPs from anywhere in the world.  Only allow source IPs from places you specifically know to be friends.  Right now, that is your house/work subnets and nowhere else.

If you allow 22/tcp to the entire world, then the entire world will attack that.  Secure ssh first by not running on the default port. Moving it to something else ... pretty much anything else ... will probably stop those attempts. My blog has a "secure ssh connections" article that DOES have commands and settings.

And you still haven't said what a "game server" is. If you don't provide specifics, nobody can provide specific answers.

---

### Post by youmustnot on 2020-06-15
> **TheFu said:**
> They attack is always happening if you allow the source IPs from anywhere in the world.  Only allow source IPs from places you specifically know to be friends.  Right now, that is your house/work subnets and nowhere else.

If you allow 22/tcp to the entire world, then the entire world will attack that.  Secure ssh first by not running on the default port. Moving it to something else ... pretty much anything else ... will probably stop those attempts. My blog has a "secure ssh connections" article that DOES have commands and settings.

And you still haven't said what a "game server" is. If you don't provide specifics, nobody can provide specific answers.

ok i'll get that port changed over, 

the game server is a facepunch RUST game server. I'm using LGSM to manage it, i did mention it previously you must of missed it :)

---

### Post by TheFu on 2020-06-15
I caught the "rust" part, but that's like saying i'm running a C++ program. Very generic.  

Regardless, I&#8217;ve never heard of that game or the management software.  Often, the failure is with the management stuff, so don't open that to any ip except yours - better would be to only allow localhost connections to the management interface. Use an ssh-tunnel for that. This is admin 101.

---

### Post by youmustnot on 2020-06-15
LGSM only runs in terminal i dont believe there is any outward looking interface, it just seems to be alot of bash scripts :)[URL="https://linuxgsm.com/lgsm/rustserver/"]


https://linuxgsm.com/lgsm/rustserver/[/URL]

the PC survival game "rust" by facepunch, not rust the programing language :)

---

### Post by TheFu on 2020-06-15
Ah - thanks for the education.  

Many years ago i ran a TF server on the internet for friends.  Only brought it up when we all played. it was off otherwise. On weekends, they'd come over and we'd play on the LAN. We got tired and switched to a LAN-only game before we all got married and headed off to different parts of the world for other jobs.

Seems there is an entire group of people who prefer to hack game servers. There's a twitter tag just for announcing who is doing what and their steamids. Guess that helps ban them more places?

---

### Post by EuclideanCoffee on 2020-06-16
Sorry, I was away.

Did things improve since installing ufw and changing your port?

The next thing I would do is block all ports besides the game ports except incoming for port 22 (or whatever is ssh) from a trusted server.

You can create your trusted server from anything, but have in mind a "plan b" in case your trusted server is compromised.

Let me know if you need illustrations, and I'll provide them. From the general tone of your posts, it sounds like you're doing better.

Concerning a web server, you won't need one. Fail2ban does a good job protecting web servers in my experience, but when you want to adapt it for a special service like a video game server, you'd need to tweak it. Since users are connecting without a browser, you'd need to be sure you have some sort of fail2ban configuration setup after the initial attack waves have died down.

What is likely happening is that the banned user purchased a DDOS service. You can read more about this sort of thing from Krebs on Security's blog. He talks in depth about Minecraft DDOSing as it is more common and easy to explain.

---

### Post by youmustnot on 2020-06-16
the dos'ing is continuing, it stopped for a short while when i installed the firewall, but i think that was coincidence as its just as strong now.

how do i see these IP's hitting the server? i dont see all that much in auth.log the odd failed login attempt from africa. 

I've enabled the 'robot' firewall within hertzner, and the spamming has stopped again. 

with the remaining ports that are open i can rate limit them:
iptables -A INPUT -p udp -m udp --dport 27015 -m state --state NEW -m recent --set --name DEFAULT --rsource
iptables -A INPUT -p udp -m udp --dport 27015 -m state --state NEW -m recent --update --seconds 60 --hitcount 10 --name DEFAULT --rsource -j DROP

---

