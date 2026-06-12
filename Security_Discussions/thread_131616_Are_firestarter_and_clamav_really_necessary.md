---
title: "Are firestarter and clamav really necessary ??"
date: 2006-02-16
forum: Security Discussions
---

### Post by kudu on 2006-02-16
Especially since I connect through a router, do I really need firestarter and clamav ?

---

### Post by rfruth on 2006-02-16
The price is right & they don't cause any problems, on a more serious note I think its  good to send a strong signal that the Linux community is prepared for a attack - long story short I use both clamAV & firestarter ...

;)

---

### Post by nanotube on 2006-02-19
my take on that would be a "no". although if you had to choose just one of the two, i would go with firestarter. :) a firewall is always a good thing... but there are no known virs in the wild for linux, so your clamav would just be sitting there doing nothing and eating your resources.

---

### Post by Leo_01 on 2006-02-20
i guess you might want firestarter if you want a a safe feeling when using ubuntu...(Maybe monitor traffic too?)

You might need clamAV if you are trading files with alot of Windows system often in your OWN network.
it really reduce the chance of all your Windows systems being infected with a crappy virus at one time.
other than that clamAV is just useless...

---

### Post by az on 2006-02-20
[QUOTE=rfruth]The price is right & they don't cause any problems, on a more serious note I think its  good to send a strong signal that the Linux community is prepared for a attack - long story short I use both clamAV & firestarter ...

;)[/QUOTE]

There is no reason to install them now.  If there is ever the need, to install them would take about thirty seconds.  Right now, I have better things to do with my bandwidth and cpu power.

And viruses are only a small fraction of security vulnerabilities.  Windows is particularly vulnerable to them because of the way it is built.  Unix is not particularly vulnerable to them for the same reason.

It is important to keep updated with all the security updates that are available to you, though.  Just keep installing the updates and you will be fine.

---

### Post by nocturn on 2006-02-20
Recently, people are starting to find out that virusscanners just don't work (on windows).

The first outbreak wave of the fast moving virusses came hours before AV signatures where out, so relying on it for defense is a big mistake.

Firestarter is a good precaution though (I have it).  The base install of Ubuntu is pretty secure, so you can do without.

---

### Post by bagel on 2006-02-20
I'm having installed both ClamAV and firestarter.

ClamAV is only used to check a certain file not an then(seldom at the moment)

firestarter is always running, the only "attack" so far was some guy doing a Nessus scan on me :) 

Ciao, bagel

---

### Post by psusi on 2006-02-20
Aside from the placeblo effect, installing them generally gets you nothing.  There are no open ports in an out of the box install of ubuntu, so there's nothing for firestarter to protect.  There's also no known linux virii in the wild.

---

### Post by Almighty on 2006-02-20
I dont understand why this topic is being brought up so much. How I look at things, having a Firewall is just like having a keyboard. When it comes to AV, I believe it should be a common practice to have one. Even if we arent capable of  having one of these bugs, we can still transmit them. 

Bottom line... if you have a computer connected to the internet, you should have at a bare minimum a firewall (hardware perferably) and antivirus.

---

### Post by psusi on 2006-02-20
[QUOTE=Almighty]I dont understand why this topic is being brought up so much. How I look at things, having a Firewall is just like having a keyboard. When it comes to AV, I believe it should be a common practice to have one. Even if we arent capable of  having one of these bugs, we can still transmit them. 

Bottom line... if you have a computer connected to the internet, you should have at a bare minimum a firewall (hardware perferably) and antivirus.[/QUOTE]

This is a false perception as a result of limited knowledge and exposure to windows for too long.  A firewall is only needed to deny access to services running on your PC to certain people.  When you don't have stupid services installed by default, there is nothing for the firewall to deny access to.  The only way you are going to spread a windows virus is if you get a windows executable in an email say, and forward it to other people.  Why would you do such a thing?  Just don't do that.

---

### Post by Almighty on 2006-02-20
I understand what you are saying. Personally I NEVER open emails with executables. I just feel as though its good general practice to have these things. 

I do agree, that I have been into the whole Micro$oft thing for too long, but its my job I kinda have to put up with its BS.

---

### Post by az on 2006-02-20
[QUOTE=Almighty]I dont understand why this topic is being brought up so much. How I look at things, having a Firewall is just like having a keyboard. When it comes to AV, I believe it should be a common practice to have one. Even if we arent capable of  having one of these bugs, we can still transmit them. 

Bottom line... if you have a computer connected to the internet, you should have at a bare minimum a firewall (hardware perferably) and antivirus.[/QUOTE]

With a sane security policy (nothing listening by default) a firewall will add nothing.

Unless you are running a mail server, you do not need a virus scanner.  So by default, and Ubuntu desktop does not need these things.

---

### Post by Almighty on 2006-02-20
Very true.

---

### Post by habrys on 2006-02-24
I'm pretty new to the Linux world, so please explain me a few things. I used to pay attention to have a firewall (ZoneAlarm) and antivirus (Avast!) always installed and running on my XP boxes.

Now I'm trying to switch to Linux (SuSE 9.3, 10.0 previously, now Ubuntu 5.10, which I am very impressed with), but I'm a little concerned about security.

1. No antivirus seems mostly ok for me with the way the sensitive parts of the system are protected from access of a normal user (only root or sudo can do everything). But, what if I start something infected during performing some administrative tasks as a root? I know it's not very likely, there are very few viruses for Linux etc., but still... it seems to present a small security gap. Correct me if I'm wrong.

2. What I'm way more concerned about is no controlling which applications are calling home, like for example ZoneAlarm does. Even if I'm behined a router with hardware firewall and behind the Linux software firewall (firestarter or whatever), I have only inbound protection, right? If there is a keylogger on my system, which wants to transmit my keystrokes to somebody over the internet - I get no warning from firewall. Am I right or is this somehow addressed? It is the most important and criticizied weakness of the in-built Windows XP firewall. Is the Linux firewall not better?

Should I be concerned?

---

### Post by ollyshaw on 2006-02-24
Personally I found there to be a couple of problems with firestarter,

I dont use anything at home, where i have a hardware firewall. At work, there is LOADS of network traffic, so i use guarddog, which once you get your head round it is great.

Olly

---

### Post by az on 2006-02-24
[QUOTE=habrys]
1. No antivirus seems mostly ok for me with the way the sensitive parts of the system are protected from access of a normal user (only root or sudo can do everything). But, what if I start something infected during performing some administrative tasks as a root? I know it's not very likely, there are very few viruses for Linux etc., but still... it seems to present a small security gap. Correct me if I'm wrong.[/QUOTE]

Viruses attack windows because there are holes that cannot be closed, as far as I understand it.  In linux, this is not the case.  That's why viruses are not a type of vulnerability to which linux is prone.  The user/root priviledge seperation has nothing to do with it.

Windows now uses such a priviledge structure.

And exploiting a vulnerability like a buffer overflow can result in arbitrary code being run as root.  This is know as priviledge escalation and is something that is constantly found and patched in linux.  Keep up with your security updates!
 


[QUOTE=habrys]
2. What I'm way more concerned about is no controlling which applications are calling home, like for example ZoneAlarm does. Even if I'm behined a router with hardware firewall and behind the Linux software firewall (firestarter or whatever), I have only inbound protection, right? If there is a keylogger on my system, which wants to transmit my keystrokes to somebody over the internet - I get no warning from firewall. Am I right or is this somehow addressed? It is the most important and criticizied weakness of the in-built Windows XP firewall. Is the Linux firewall not better?
[/QUOTE]


There are tons of such applications, as mentioned.  Also, the fact that we use centralised repositories, it is more unlikely that you will be running such an application.  You install stuff from outside repositories at your own risk, you know.

---

### Post by habrys on 2006-02-24
[QUOTE=azz]Viruses attack windows because there are holes that cannot be closed, as far as I understand it.  In linux, this is not the case.  That's why viruses are not a type of vulnerability to which linux is prone.  The user/root priviledge seperation has nothing to do with it.[/QUOTE]
Err... I always thought, that viruses are pieces of executeable code "glued" to normal programms, which execute themselves on startup of the given programm. After the malicious code did it's thing, the normal programm is executed, so the user can't notice any difference. And the virus (in the "doing it's thing" phase) can for example modify another programms from say /usr/bin in case of Linux (like sudo for example) - spread itself. Or wipe the whole partition. This can be prevented when you work as a normal user, without root privilages. You cannot modify sudo or wipe the partition, because you don't have the rights. But I really cannot see how exactly Linux should be less prone that Windows to the above scenario if you work as root.

[QUOTE=azz]Windows now uses such a priviledge structure.[/QUOTE]
Well... of course. The subtle difference is, under Linux your **default** user has no root privileges and under Windows your default user has adminstrator rights. You can limit your rights in Windows of course, but you have to be aware of security risks and actually do something to achieve it. Most of users don't know that. I think that's a huge difference. But that's a topic for another discussion actually... :) 

[QUOTE=azz]And exploiting a vulnerability like a buffer overflow can result in arbitrary code being run as root.  This is know as priviledge escalation and is something that is constantly found and patched in linux.  Keep up with your security updates![/QUOTE]
That's another story and the situation in Windows is just the same. There are also Online Updates in Windows world. The only difference is that maybe the Linux community reacts faster to close security holes. And of course the sources are mostly open, so no hidden backdoors for FBI etc.
 
[QUOTE=azz]There are tons of such applications, as mentioned.[/QUOTE]
Could you recommend something?

[QUOTE=azz]Also, the fact that we use centralised repositories, it is more unlikely that you will be running such an application.  You install stuff from outside repositories at your own risk, you know.[/QUOTE]
Centralised repositories are great and very complete for Ubuntu. But there are still many applications, which cannot be found there. And it will always be this way. I installed Ubuntu like a week ago and already had to install 4 applications, which are not available over apt/synaptic:
Firefox 1.5
Thunderbird 1.5
Skype
Azureus
I don't think you really can limit yourself only to the software from repositories. And even repositories cannot guarantee 100% security, I think...

---

### Post by earobinson on 2006-02-24
[QUOTE=nocturn]Recently, people are starting to find out that virusscanners just don't work (on windows).

The first outbreak wave of the fast moving virusses came hours before AV signatures where out, so relying on it for defense is a big mistake.

Firestarter is a good precaution though (I have it).  The base install of Ubuntu is pretty secure, so you can do without.[/QUOTE]
exactly anti-viruse are actualy virus docters all they can do is fix problems they know about.

And I think this is the 10th security thread i have read ... stickey one of them?

---

### Post by xequence on 2006-02-24
> Are firestarter and clamav really necessary ?? 

Nope, not at all.

---

### Post by Perfect Storm on 2006-02-24
[QUOTE=earobinson]exactly anti-viruse are actualy virus docters all they can do is fix problems they know about.

And I think this is the 10th security thread i have read ... stickey one of them?[/QUOTE]

Done.

---

### Post by lean on 2006-02-25
Habriz:

You are completely right. There is no outbound protection in Ubuntu. There are many reasons for this:
1. People do not think they can get spyware because they use central repository.
2. The architectual problems are a little advanced. The programs needs to be monitored when they start, and be recognised if they have been started before. This will propably need a kernel module, and nobody has done it.
3. A virus could propably use a certified process to send messages. So the virus could just start firefox [http://somehomepage.com/yourpersonalinfo](http://somehomepage.com/yourpersonalinfo), or wget [http://somehomepage.com/yourpersonalinfo](http://somehomepage.com/yourpersonalinfo). The OS would not be able to distinguish if it was a user who made the request, or a malicious piece of software.

So it is a case of plugging 90% of the holes in the ship, but it won't stop the ship from sinking, since all the water come in the last 10%.
At the moment people are just fixing 0%, to be 'in the honest'.

So outbound connection limiting in a simple form, will help you twart programs made by people who do not think you are using it. Programmers who know that you are running it, are just using another way fo sending your data.

---

### Post by nanotube on 2006-02-25
yes, the lack of outbound protection i think is one big piece that is lacking currently in iptables (and thus firestarter, which is just a gui for iptables). iptables can filter by the "name" of the process, (see man page for iptables, get to the matching by owner section. or just search for "--cmd-owner".) but it is still pretty primitive.

however, if you do want a robust per-process privilege setup, you should look into systrace ([http://www.citi.umich.edu/u/provos/systrace/)](http://www.citi.umich.edu/u/provos/systrace/)). that can let you configure so many things you wont know where to start! :) unfortunately, it seems that installing it would require recompiling your kernel with a systrace patch. not too friendly at the moment.

unless some kind ubuntu dev/packager would consider making a kernel version with systrace in it (or maybe a loadable module... i am not sure exactly what would work for systrace since i have not actually used it)? (wink wink hint hint) :)

---

### Post by Matchless on 2006-02-26
[QUOTE=azz]Viruses attack windows because there are holes that cannot be closed, as far as I understand it.  In linux, this is not the case.  That's why viruses are not a type of vulnerability to which linux is prone.  The user/root priviledge seperation has nothing to do with it.

Windows now uses such a priviledge structure.

And exploiting a vulnerability like a buffer overflow can result in arbitrary code being run as root.  This is know as priviledge escalation and is something that is constantly found and patched in linux.  Keep up with your security updates!
There are tons of such applications, as mentioned.  Also, the fact that we use centralised repositories, it is more unlikely that you will be running such an application.  You install stuff from outside repositories at your own risk, you know.[/QUOTE]

But imho we must remember that we live in the real world, where other OS's are used by the majority of people and even by linux users themselves. Files are sent and received continuously via email, down and uploads, transfers etc between linux and Windows PC's. Just think of image files, music files, Office files etc. For example if an Ubuntu user receives a nice image as an attachment with an email or downloads it from the internet and it contains a virus, it would be a very good idea to scan these files on receipt and remove the virus before passing on to friends and family! Yes, linux itself may not be affected by the virus, but do we really want to unwittingly help distributing any virii? I feel so strongly about this, that I feel Dapper should include a good anti-virus as standard.

---

### Post by habrys on 2006-02-26
[QUOTE=lean]
You are completely right. There is no outbound protection in Ubuntu.
[/QUOTE]
So no outbound protection in Linux? That's pretty bad news for me. I use my computer for internet banking among others and am pretty focused on security because of that. You may think I'm a little paranoid, but I actually have had a windows keylogger, which transmitted something over internet. No financial losses so far, but ... when you type in your bank account username and password a few times a day, keyloggers are no more a distant and theroetical threat - outbound protection becomes pretty basic and necessary feature.

[QUOTE=lean]
There are many reasons for this:
1. People do not think they can get spyware because they use central repository.
[/QUOTE]
As I said before: not everything can be found in repositories, even if they are pretty complete as it is in case of Debian/Ubuntu.

[QUOTE=lean]
2. The architectual problems are a little advanced. The programs needs to be monitored when they start, and be recognised if they have been started before. This will propably need a kernel module, and nobody has done it.[/QUOTE]
I have no doubts it's technically challenging, but I'm sure it can be done. I have no idea how exactly ZoneAlarm handles these things internally, but I can tell you how it looks from the user perspective.
Per default no applications have rights to transmit anything. If some application (like Firefox) tries to access internet, you get a popup question if it should be allowed or denied once or persistently. No matter what your answer is, the application's hash (MD5 or something) is stored with the appropriate right (allow, deny etc.) assigned. It is done not only on the application level, but also on library level (dll), so not so called "library injection attack" is possible. Similiar procedure is used when some application tries to actively open some port(s) for listening - act as a server (like eMule or some online game). Moreover ZoneAlarm opens the port(s) for listening only when the application, which has "server rights" granted, requests that (usually simply when it starts) and closes the given ports(s) when it stops. Actually even more than closes, they are stealthed, so not visible from internet zone at all. So the eMule server ports for instance are only opened when eMule works. This is all for free - I mean the free version of ZoneAlarm can do that (it's not GPL, just freeware for home users).

[QUOTE=lean]
3. A virus could propably use a certified process to send messages. So the virus could just start firefox [http://somehomepage.com/yourpersonalinfo](http://somehomepage.com/yourpersonalinfo), or wget [http://somehomepage.com/yourpersonalinfo](http://somehomepage.com/yourpersonalinfo). The OS would not be able to distinguish if it was a user who made the request, or a malicious piece of software.
[/QUOTE]
This is addressed in the Pro version of ZoneAlarm, which is no more free, sadly. If some application tries to start some other application or service, it needs also rights to do so. So if you click on a link in mail, Thunderbird needs rights to start Firefox - which are also as easy assigned as above described: you get a popup question and can answer "allow", "deny", "allow always", "deny always". Very nice and simple indeed.

Additionaly you have a list of all applications and dlls with its assigned rights stored in the ZoneAlarm database, which you can manage at will. I tend to check the list every week or so and delete all things I don't know by name. This way if it was something I don't really use - no problem, if it was regurarly used, but I don't recognize it by name, it has to ask ZoneAlarm for rights again.

[QUOTE=lean]
So it is a case of plugging 90% of the holes in the ship, but it won't stop the ship from sinking, since all the water come in the last 10%.
At the moment people are just fixing 0%, to be 'in the honest'.

So outbound connection limiting in a simple form, will help you twart programs made by people who do not think you are using it. Programmers who know that you are running it, are just using another way fo sending your data.[/QUOTE]
See above - this 10% can be handled as well.

I think Linux needs something like that. Or maybe something like that already exists?

And lean, thank you for clarifying this to me. No internet banking under Linux then I suppose, as long as I won't find acceptable sollution. Another reason, besides games to keep XP in a dual-boot configuration...

---

### Post by habrys on 2006-02-26
[QUOTE=nanotube]
however, if you do want a robust per-process privilege setup, you should look into systrace ([http://www.citi.umich.edu/u/provos/systrace/)](http://www.citi.umich.edu/u/provos/systrace/)). that can let you configure so many things you wont know where to start! :) unfortunately, it seems that installing it would require recompiling your kernel with a systrace patch. not too friendly at the moment.
[/QUOTE]

Thank you for the hint. The screenshots look very promising indeed. Compiling of a kernel module does not, but I think I'll give it a shot nevertheless.

Actually your link didn't work, but I've found it here:
[http://www.systrace.org/](http://www.systrace.org/)

Just one more thought: it seems pretty complicated - I mean installing and then defining of the rules too. I bet no average user will bother. Something like that, but with simple and pretty interface and preinstalled should be definitely part of most of the linux distributions. Maybe keyloggers are not a big problem now, when Linux has just 2-3% of desktop market share, but in a few years...

---

### Post by psusi on 2006-02-27
> **habrys]So no outbound protection in Linux? That's pretty bad news for me. I use my computer for internet banking among others and am pretty focused on security because of that. You may think I'm a little paranoid, but I actually have had a windows keylogger, which transmitted something over internet. No financial losses so far, but ... when you type in your bank account username and password a few times a day, keyloggers are no more a distant and theroetical threat - outbound protection becomes pretty basic and necessary feature.[/QUOTE]

You place too much trust in outbound protection, elevating it meerly to placeblo.  The only function outbound protection serves is to ( weakly ) attempt to detect when you have already been infected.  It is far better to prevent infection in the first place.  This is the general attitude of the linux community, and this is why ubuntu makes sure that you can't get infected in the first place.  

If you can't get infected in the first place, "outbound protection" does nothing for you, which is why nobody has bothered to implement it.  

[QUOTE=habrys]
I have no doubts it's technically challenging, but I'm sure it can be done. I have no idea how exactly ZoneAlarm handles these things internally, but I can tell you how it looks from the user perspective.
Per default no applications have rights to transmit anything. If some application (like Firefox) tries to access internet, you get a popup question if it should be allowed or denied once or persistently. No matter what your answer is, the application's hash (MD5 or something) is stored with the appropriate right (allow, deny etc.) assigned. It is done not only on the application level, but also on library level (dll), so not so called "library injection attack" is possible. Similiar procedure is used when some application tries to actively open some port(s) for listening - act as a server (like eMule or some online game). 
[/QUOTE]

Give me a few hours and a pot of coffee and I'll show you a program that bypasses all that.  It sounds fancy on paper, but it's really just another layer of tissue paper protecting you when you already have an Abram's A1 tank at your door.  

[QUOTE=habrys]
Moreover ZoneAlarm opens the port(s) for listening only when the application, which has "server rights" granted, requests that (usually simply when it starts) and closes the given ports(s) when it stops.
[/QUOTE]

That isn't anything that ZoneAlarm does said:**
> 
 Actually even more than closes, they are stealthed, so not visible from internet zone at all.

Stealthing ports violates the TCP protocol and doesn't add any protection.  It just means that if the port is closed, rather than inform someone trying to connect to it "this port is closed, go away" stealthing just ignores the request.  Either way the remote does not get a connection so it doesn't make any difference to security, it just annoys the hell out of people who wonder why the connection is just sitting there rather than either working or being rejected.

---

### Post by habrys on 2006-02-27
> **psusi]It is far better to prevent infection in the first place.  This is the general attitude of the linux community, and this is why ubuntu makes sure that you can't get infected in the first place.[/QUOTE]
I can only agree with that: better prevent an infection, than cure it. But I really cannot see how Ubuntu "makes sure that you can't get infected in the first place". Explain, please and remember I'm a Linux newbie.

[QUOTE=psusi]If you can't get infected in the first place, "outbound protection" does nothing for you, which is why nobody has bothered to implement it.[/QUOTE]
I cannot agree, that outbound protection "does nothing for you". Treat it just as another layer of protection. If the first layer fails (for example antivirus lacking a signature of a fast spreading virus), there is always the second layer: outbound protection. Of course it can be bypassed too given time, effort and enough of coffee, but... it can very well help as well. It's just question of odds. Without outbound protection chances it catches a keylogger transmitting something are 0%, right? With it sitting in place they are significantly bigger I'd say.

And now an example. I got something called "Blazing Tools Perfect Keylogger" under Windows XP a few months ago. It was hidden in a trojan horse, installed itself silently in the system and tried to transmit my keystrokes somewhere. The antivirus programm didn't detect it. But ZoneAlarm gave me a warning "bpk.exe tries to access the internet: allow, deny etc." The first layer of defense (antivirus) didn't work (probably lacking the signature), but the second layer actually did it's work excellently.

And now an example from the Linux world. I tried to find out if there are keyloggers available for Linux too. That's true, they are much more difficult to find, than in Windows world. But I found one: lkl. It can be installed to start silently, listen to keyboard port (0x60 if I remember correctly), log the keystrokes to a file and even send mails with reports to a given address. I did it all and Ubuntu did nothing to give me a warning. lkl even protocolled nicely my linux user and password, which I type in when logging into Ubuntu. Not to mention passwords and other things I typed in web forms (bank accounts!). Little explanation: I started lkl with a script in /etc/init.d, so it was already runnning before Ubuntu login screen shows up :)

Now I'm really a Linux newbie, who just knows how to google to find useful information. I don't want to think what a person with much more knowledge could do.

lkl is still pretty primitive (version 0.1) as it starts in userspace and not as a kernel module. And of course it cannot install itself without root privileges. But still... I can imagine a trojan horse with lkl attached, which can install itself in one of those rare moments, when you work as a root. All right, all right you have to sudo and there is no root account in Ubuntu. But I know people, who do "sudo konqueror" to do their root tasks. And you can always activate the root account, even in Ubuntu.

What I'm trying to say is, I think lack of outbound protection is still a security gap in my opinion. Not as huge as in case of Windows, but it should be closed some day, especially if Linux gains much more popularity...

[QUOTE=psusi]That isn't anything that ZoneAlarm does said:**
> 
Of course. I only mean the firewall for this port is closed as well, not only the port itself. When another application, which is not authorised tries to listen on the same port, it won't get a permission.

[QUOTE=psusi]Stealthing ports violates the TCP protocol and doesn't add any protection.  It just means that if the port is closed, rather than inform someone trying to connect to it "this port is closed, go away" stealthing just ignores the request.  Either way the remote does not get a connection so it doesn't make any difference to security, it just annoys the hell out of people who wonder why the connection is just sitting there rather than either working or being rejected.
If stealthing ports violates TCP protocol, then I violate TCP protocol anytime I switch my PC off or disconnect from the net any other way. I stealth all my ports then :) And another thought: I have nothing against annoying someone trying to scan my ports :) 

But seriously, don't you think, it's safer, when all your ports are stealthed, as opposed to just closed? If all the ports are stealthed, then you are practically invisible from outside. I think invisible is better, than closed. After port scanning no other tries to compromise your system are made - the hacker or rather script kiddie thinks your machine doesn't exist and moves on, right?

One more thought: my router (Netgear WGR614) running a hardware firewall also prefers to stealth ports per default instead of just closing them. It cannot be a coincidence, right? :)

---

### Post by nanotube on 2006-02-28
habrys, your arguments seem valid to me.

psusi, i will try to point out how good outbound protection works, and then i think you will see that it is not as easy as you say to bypass it.

first, it checks to see what process is starting a connection to the outside, and runs a checksum verification on the executable to make sure it has not changed. if it has - it warns you. so if some trojan has modified firefox or any other executable that "normally" would be allowed to access without challenge, that will be detected, and prevented.

second, all programs are also by default prevented from spawning other processes - so your keylogger/trojan cannot just spawn firefox or wget and access the net that way.

so while its always better to prevent infection rather than contain it afterwards, containment does serve as one of the valuable layers of protection, and is not quite as trivial to bypass as you make it out to be.

---

### Post by nocturn on 2006-02-28
I have seen the issue of outbound filtering raised here.  And Ubuntu does support it, even natively if you want (iptables).

It is just not activated by default because it would break connections for most newbie users (Windows SP2 firewall also doesn't do outbound filtering, I suspect mainly for the same reason).

Install Firestarter and set the outbound policy to restrictive (deny by default).  It can be set up to ask to open a port on each request.

---

### Post by nocturn on 2006-02-28
[QUOTE=Matchless]But imho we must remember that we live in the real world, where other OS's are used by the majority of people and even by linux users themselves. Files are sent and received continuously via email, down and uploads, transfers etc between linux and Windows PC's. Just think of image files, music files, Office files etc. For example if an Ubuntu user receives a nice image as an attachment with an email or downloads it from the internet and it contains a virus, it would be a very good idea to scan these files on receipt and remove the virus before passing on to friends and family! Yes, linux itself may not be affected by the virus, but do we really want to unwittingly help distributing any virii? I feel so strongly about this, that I feel Dapper should include a good anti-virus as standard.[/QUOTE]

I would not object per se to Dapper having a virusscanner in main (not on the install disc mind you), but if they enable stuff like on-access scanning, I'm out.

I don't want my box slowed to a crawl just because of a flawed security dogma.

And again, virus scanners are a remedy security measure, not a real prevention.  If you receive a virus (via mail or others) it may not be detected at all until your signatures are prepared for it.

I would rather have the devs focus on SELinux in Dapper and PaX, which are both generic security measures that help protect you against both human attackers and virusses.  

Regarding forwarding virusses to windows users.  It is in part their problem and their responsibility to buy those expensive commercial scanners as well as not running with admin privileges (despite this being the default).
And they are better served with a virus scanner on an SMTP server checking both incoming and outgoing mails of all users (preferably running more then one AV).

---

### Post by nocturn on 2006-02-28
[QUOTE=habrys]So no outbound protection in Linux? That's pretty bad news for me. I use my computer for internet banking among others and am pretty focused on security because of that. You may think I'm a little paranoid, but I actually have had a windows keylogger, which transmitted something over internet. No financial losses so far, but ... when you type in your bank account username and password a few times a day, keyloggers are no more a distant and theroetical threat - outbound protection becomes pretty basic and necessary feature.[/quote]

To be quite frank, this is simply untrue, both in facts and reasoning.
Linux does have outbound protection and it alsways had.  You can even turn it on without a GUI frontend, just set the default outbound policy to DENY.

Firestarter can do this from the GUI.

But don't expect this to be an all-in protection measure.  A trojan typicly comes via an allowed channel (like mail) and if it gets as far as being run, it can just as well disable both the firewall and AV software, there have been virusses that do this on windows.

You can buy yourself much more security at a lower cost by other measures, like not using things like ActiveX, by not having a mailclient that can execute code in messages and by not blindly executing stuff you don't know (mail attachments).

I care a great deal about security, but I have always hold the belief that you should plug the biggest holes first.  It makes no sense to put your pink in a small hole in your boat when half of the hull has been ripped off. 

Even if you have to download packages of the net that are not in the safe repositories, take a few precautions.  Use either alternative repositories that are well known or download packages from the main site of a project.  Verify MD5 sums and PGP sigs if they are provided etc.

If your a rather advanced user, do activate the outbound protection of firestarter or at least log and monitor outgoing connections.

---

### Post by nocturn on 2006-02-28
[QUOTE=habrys]I can only agree with that: better prevent an infection, than cure it. But I really cannot see how Ubuntu "makes sure that you can't get infected in the first place". Explain, please and remember I'm a Linux newbie.
[/quote]

Linux protects you by blocking of the infection paths.  Having things like ActiveX or macros in mails and documents that are automaticly run on opening is just a plain bad idea.

How would you get a Linux E-mail virus?  The steps would be:
1. Receive mail
2. Save attachment to disk
3. Give attachment on disk an executable flag (+x)
4. Run the attachment 
5. Because step 4 didn't infect the system as a whole, rerun attachment with sudo before it
6. Enter your password to make it work.

In the same way, I would rather have the Ubuntu team work on PaX and SELinux as a default which are real security measures (PaX prevents buffer overflows and SELinux is a security policy framework that is more advanced then application level firewalling).

> 
I cannot agree, that outbound protection "does nothing for you". Treat it just as another layer of protection. If the first layer fails (for example antivirus lacking a signature of a fast spreading virus), there is always the second layer: outbound protection. Of course it can be bypassed too given time, effort and enough of coffee, but... it can very well help as well. It's just question of odds. Without outbound protection chances it catches a keylogger transmitting something are 0%, right? With it sitting in place they are significantly bigger I'd say.


On Windows XP, your defense layers are already weak if you use Outlook and IE and almost non-existing if you run with admin privileges (which is still more difficult to avoid then on Linux).  If you do not add something like ZoneAlarm or Anti-virus, there would be little defenses left.

I don't know how you got the keylogger on XP, but it didn't appear on your system by magic.  It must have had an entry path, being an E-mail or a malicious website.  It probably was executed with admin rights?

Instead of protecting what it could do once it had access to your system, it should have been preventing from entering it.  You do know that the only secure way to recover from any infection (also on *nix) is to do a full reinstall?  That is why preventing a compromise is so important, but you need an additional defense once you do get infected.  It is just that AV and outbound filtering may not be that defense (I believe stack protection, non-executable memory and a policy such as SELinux are that defense).


> 
And now an example from the Linux world. I tried to find out if there are keyloggers available for Linux too. That's true, they are much more difficult to find, than in Windows world. But I found one: lkl. It can be installed to start silently, listen to keyboard port (0x60 if I remember correctly), log the keystrokes to a file and even send mails with reports to a given address. I did it all and Ubuntu did nothing to give me a warning. lkl even protocolled nicely my linux user and password, which I type in when logging into Ubuntu. Not to mention passwords and other things I typed in web forms (bank accounts!). Little explanation: I started lkl with a script in /etc/init.d, so it was already runnning before Ubuntu login screen shows up :)


Off course they exist, most programmers can write one in about an hour.  But the key remains how to get them installed with ROOT access without the users consent on a system (I presume you installed it nicely with sudo).

How would this keystroke logger have entered your Ubuntu system without your knowledge, much the same as happened to your XP system despite the presence of AV and a firewall?

---

### Post by doclivingston on 2006-02-28
[QUOTE=nanotube]second, all programs are also by default prevented from spawning other processes - so your keylogger/trojan cannot just spawn firefox or wget and access the net that way.[/quote]

"Program <mumble> is attempting to launch the program wget, do you wish to allow it?"   "Program <mumble> is trying to open a listening port, do you wish to allow it?"


How many people do you think can answer those correctly? (excluding people who know a fair bit about network security).

Outbound connection filtering requires the user to know what should be allowed to access the network. In general, users don't know that. Similarly, if your system doesn't have any ports open by default, inbound filtering requires the same knowledge.

Inbound filtering is useful on Windows because it has ports open by default.

---

### Post by habrys on 2006-02-28
First of all thank you for comprehensive answers to my questions, nocturn.

[QUOTE=nocturn]Install Firestarter and set the outbound policy to restrictive (deny by default).  It can be set up to ask to open a port on each request.[/QUOTE]

Can it be configured per application? I don't want to be asked to open a port after every click on a weblink in Firefox. I want to have a possibility for example to give only Firefox permissions to access internet over port 80. Based on checksum, so I will be asked again when I update Firefox from version 1.5 to 1.5.0.1. Or when something malicious manipulates binaries of Firefox. But no more often. 

Is it possible with iptables/Firestarter?

It's rather obvious, that nobody using Linix for desktop purposes turns on an outbound protection, which asks for permission on each http request.

---

### Post by habrys on 2006-02-28
[QUOTE=nocturn]
How would you get a Linux E-mail virus?  The steps would be:
1. Receive mail
2. Save attachment to disk
3. Give attachment on disk an executable flag (+x)
4. Run the attachment 
5. Because step 4 didn't infect the system as a whole, rerun attachment with sudo before it
6. Enter your password to make it work.
[/QUOTE]
Yes, this is one of possiblities to get a trojan.
Another would be:

1. You installed Ubuntu being a total newbie.
2. You discover, you cannot play mp3, most of movies, DVDs etc.
3. You search forums for simple solutions and read about something called Automatix, which installs all of it for you in one step.
4. You download, install and run Automatix.
5. You get asked for password. It's normal during installation, so no worries.
6. Automatix adds a bunch of 3rd party repositories to your your sources list. You won't read everything listed in this small terminal, typically, so you have no clue. Or even don't know what repositories and sources list are.
7. Quite a lot of new packages, most of them from 3rd party repositories get installed. You have no real overview what exactly, but you are happy, because mp3, movies and DVDs playback works now.

Now let's say some small application from 3rd party repositories is a trojan horse with a keylogger. You have no outbound protection. Bad luck...

Is the above scenario so impossible?

[QUOTE=nocturn]
I don't know how you got the keylogger on XP, but it didn't appear on your system by magic.  It must have had an entry path, being an E-mail or a malicious website.  It probably was executed with admin rights?
[/QUOTE]
It was a test. I wanted to see how secure my machine is. I prepared the trojan myself, sent myself a mail with attachement, yes opened and run the attachement, a pretty and funny screensaver with trojan attached and observed what happenes.

[QUOTE=nocturn]
Instead of protecting what it could do once it had access to your system, it should have been preventing from entering it.
[/QUOTE]
Why instead? Why not have both? You really think AV and outbound filtering are so useless, it's not worth effort to implement them?

[QUOTE=nocturn]
Off course they exist, most programmers can write one in about an hour.  But the key remains how to get them installed with ROOT access without the users consent on a system (I presume you installed it nicely with sudo).

How would this keystroke logger have entered your Ubuntu system without your knowledge, much the same as happened to your XP system despite the presence of AV and a firewall?[/QUOTE]
Using Automatix with 3rd party repositories for example. Or downloading and installing per hand some application, which is not available in repositories. Just don't tell me, that everything can be found in repositories. It cannot and it never will be this way - even if Ubuntu's repositories are in fact very complete.

---

### Post by nocturn on 2006-02-28
[QUOTE=habrys]
Can it be configured per application? I don't want to be asked to open a port after every click on a weblink in Firefox. I want to have a possibility for example to give only Firefox permissions to access internet over port 80. Based on checksum, so I will be asked again when I update Firefox from version 1.5 to 1.5.0.1. Or when something malicious manipulates binaries of Firefox. But no more often. 
[/quote]

You have several options here.  You can either allow connections based on ports (so, outbound policy is deny), each time an app wants access, the firewall prompts you to open that port outbound (for all, not one app).

This is possible with Firestarter.

There is also an option to use the --cmd-owner options in iptables to allow connections based on the launching process.  Firestarter does not provide this (maybe other GUI's do, but I don't know).

But I maintain that filtering based on application checksums (or names) provides no extra security.  If a malicious application already has root rights (to overwrite binaries) it will not have any trouble disabling the firewall entirely.

It provides a false sense of security if you think this will make your system secure and that is more dangerous then any problem it solves.

---

### Post by habrys on 2006-02-28
[QUOTE=doclivingston]"Program <mumble> is attempting to launch the program wget, do you wish to allow it?"   "Program <mumble> is trying to open a listening port, do you wish to allow it?"


How many people do you think can answer those correctly? (excluding people who know a fair bit about network security).

Outbound connection filtering requires the user to know what should be allowed to access the network. In general, users don't know that. Similarly, if your system doesn't have any ports open by default, inbound filtering requires the same knowledge.

Inbound filtering is useful on Windows because it has ports open by default.[/QUOTE]

I don't agree. It doesn't require much knowledge, just some common sense.

Example:
You just upgraded Firefox to a new version. You start it and try to access some webpages. You get a warning:
"Updated programm: firefox.exe tries to access internet; allow, deny, etc.."
It's obvoius you should allow.
But, if you did nothing, no new installation or upgrade, it's also pretty obvious you should deny, right?

If there is a situation, when you really don't know what to do, you just deny once and observe if some functionality you need doesn't work. In this case you just allow persistently. If everything seems to work and something bothers you to get internet access, you deny persistently. That's all - really simple.

Example: 
Microsoft Word want to access internet during installation. Deny. Try out if you can use Word normally. Deny persistently. Who knows, maybe Microsoft wants to run world statistics about documents written in Word. But I don't want to provide any data. So deny. As simple as that.

---

### Post by doclivingston on 2006-02-28
[QUOTE=habrys]5. You get asked for password. It's normal during installation, so no worries.[/QUOTE]

At this point, outbound filtering, anti-virus software et al, doesn't matter. The instant you have malicious code running unchecked (which it is, as root) it can do anything - including disabling or modfying your protection software.


The solutions are:

a) don't install things as root. This is hard because most binary packaging systems don't support user-installs, and some things need to be run at priveleged levels to work (not neccarily root, but things your user doesn't have).

b) Have the packaging system not do install stuff as root. SELinux can help here, by limiting dpkg/rpm to lesser priveleged levels, however it would still need full root access at certain times (installing a new kernel, or other root-priveleged things).

---

### Post by habrys on 2006-02-28
[QUOTE=nocturn]You have several options here.  You can either allow connections based on ports (so, outbound policy is deny), each time an app wants access, the firewall prompts you to open that port outbound (for all, not one app).

This is possible with Firestarter.

There is also an option to use the --cmd-owner options in iptables to allow connections based on the launching process.  Firestarter does not provide this (maybe other GUI's do, but I don't know).
[/QUOTE]
Thank for information. I'll try this out.

[QUOTE=nocturn]
But I maintain that filtering based on application checksums (or names) provides no extra security.  If a malicious application already has root rights (to overwrite binaries) it will not have any trouble disabling the firewall entirely.

It provides a false sense of security if you think this will make your system secure and that is more dangerous then any problem it solves.[/QUOTE]
I don't agree here. You can for example install some malicious application from 3rd party repository with sudo apt-get and then start it under your regular user. In this case the application cannot disable firewall, but can try to transmit some data, right?

And even if it runs with root privileges it is possible, it cannot disable the firewall, simply because the hacker didn't thought about implementing it. Or it looks for iptables and you have some uncommon firewall solution.

What I'm trying to say, firewall with outbound protection is obviously not 100% waterproof, but it increases security in my opinion. Like any other security measure.

And yes, you shouldn't get false sense of security having outbound protection, you should still check the logs from time to time, that's all true. Manual browsing of logs is just another layer of security, also not 100% waterproof, as you can overlook something.

---

### Post by doclivingston on 2006-02-28
> **habrys]You just upgraded Firefox to a new version. You start it and try to access some webpages. You get a warning:
"Updated programm: firefox.exe tries to access internet said:**
> 

Okay, so you trust firefox. Do you trust *every* extension you have installed? the flash plugin? the movie-playing plugin? They are all running inside the application "firefox.exe", which you have authorised full access to the internet.

As mentioned above, you also need to limit which programs can launch firefox - otherwise malicious code will take advantage of the fact that Firefox is in the "trusted" list.


[quote]Microsoft Word want to access internet during installation. Deny. Try out if you can use Word normally. Deny persistently. Who knows, maybe Microsoft wants to run world statistics about documents written in Word. But I don't want to provide any data. So deny. As simple as that.

How do you know which application is really "Word"? Any application could call itself that, you could have several things calling themselves "Word".

If you want to go by paths, would you trust "/usr/bin/firefox" or "/usr/lib/firefox/firefox-bin"? the second one is the actual program.

---

### Post by habrys on 2006-02-28
[QUOTE=nocturn]
There is also an option to use the --cmd-owner options in iptables to allow connections based on the launching process.[/QUOTE]
This is only process name based, right? No checksums?

---

### Post by doclivingston on 2006-02-28
[QUOTE=habrys]I don't agree here. You can for example install some malicious application from 3rd party repository with sudo apt-get and then start it under your regular user. In this case the application cannot disable firewall, but can try to transmit some data, right?[/quote]

The application running as your user can't. But the install-script could (which is run as root).


> And yes, you shouldn't get false sense of security having otbound protection, you should still check the logs from time to time, that's all true. Manual browsing of logs is just another layer of security, also not 100% waterproof, as you can overlook something.

I agree here. However, how do you know that the malicious code has installed something that tampers with the logs?

---

### Post by habrys on 2006-02-28
[QUOTE=doclivingston]Okay, so you trust firefox. Do you trust *every* extension you have installed? the flash plugin? the movie-playing plugin? They are all running inside the application "firefox.exe", which you have authorised full access to the internet.[/QUOTE]
You're right, there is no control over plugins and extensions. That's a gap. 

[QUOTE=doclivingston]As mentioned above, you also need to limit which programs can launch firefox - otherwise malicious code will take advantage of the fact that Firefox is in the "trusted" list.[/QUOTE]
This is solved in ZoneAlarm Pro nicely. You get a warning when some application tries to start another one. So you for example get a warning, when you click on link in mail: "thunderbird tries to start firefox". And you can for example say, that you trust thunderbird to start firefox.

[QUOTE=doclivingston]
How do you know which application is really "Word"? Any application could call itself that, you could have several things calling themselves "Word".[/QUOTE]
It's pretty obvoius. When I double click Word icon, see Word window and see a warning from ZoneAlarm "word.exe is trying to access internet", I can assume with high probability, that it's the real Word calling home. If I only see the warning and did nothing before (no Word running), then I suspect something could be wrong.

[QUOTE=doclivingston]
If you want to go by paths, would you trust "/usr/bin/firefox" or "/usr/lib/firefox/firefox-bin"? the second one is the actual program.[/QUOTE]
As above.

---

### Post by habrys on 2006-02-28
[QUOTE=doclivingston]The application running as your user can't. But the install-script could (which is run as root).[/QUOTE]
That's right. I overlooked that.
Another example then. I download some malicious software and installed it manually as a root. With mkdir, cp etc. And then run it as a normal user. It tries to transmit data over internet, but can't disable the outbound protection, right? Caught!

[QUOTE=doclivingston]I agree here. However, how do you know that the malicious code has installed something that tampers with the logs?[/QUOTE]
You don't know of course. That's another reason it's also not 100% waterproof.

But hackers are also only people, which can overlook something. For example to disable your outbound protection, even from a trojan horse running under root. Or to install something tampering with your logs.

Nearly nothing is 100% waterproof. It's just a question how hard and time consuming breaking of your machine's security is. If it's too hard, the bad guys just won't bother and move along to easier targets (Windows perhaps...). And this is exactly what should be achieved with multiple layers of security. And outbound protection is just one of them in my opinion.

---

### Post by nocturn on 2006-02-28
[QUOTE=habrys]This is only process name based, right? No checksums?[/QUOTE]

No checksums.  They would be useless.  If an app already entered your machine and gained root access (needed to overwrite the binaries), it can run iptables -F before launching or even recalculate and overwrite the valid checksum list (If you switch from DAC to MAC based access controls, this would not be so).

Checksum checking in Linux is usefull at install time though and enables you to verify the integrity of already installed packages.

---

### Post by nocturn on 2006-02-28
[QUOTE=habrys]
It's pretty obvoius. When I double click Word icon, see Word window and see a warning from ZoneAlarm "word.exe is trying to access internet", I can assume with high probability, that it's the real Word calling home. If I only see the warning and did nothing before (no Word running), then I suspect something could be wrong.
[/QUOTE]

So ZoneAlarm pops up that warning.  Maybe a virus already modified the icon link to c:\hacked\word.exe, which first launches the payload and then starts word in the background (which isn't accessing the net).

The only way that checksums would be usable in this manner is if they were provided by ZoneAlarm itself (not calculated locally).

---

### Post by nocturn on 2006-02-28
[QUOTE=habrys]That's right. I overlooked that.
Another example then. I download some malicious software and installed it manually as a root. With mkdir, cp etc. And then run it as a normal user. It tries to transmit data over internet, but can't disable the outbound protection, right? Caught!
[/QUOTE]

So, outbound protection might be able to protect this remote scenario (I say might, because chances are that if you didn't download a package you have to compile for yourself and the malicious code could be in the make install routine, which is run as root).

Security is always a tradeoff.  You buy additional security at a cost, be it money, time or convience.  Using protections such as making /tmp noexec,nosuid and sticky costs very little yet the gains are big.  The same goes for PaX (once it is tested and integrated).  SELinux offers big gains, but at a rather high cost.

Outbound protection is both complex and fragile, the costs are high but the gains are very low (specially on Linux), which makes it a bad tradeoff to make.

---

### Post by habrys on 2006-02-28
[QUOTE=nocturn]Outbound protection is both complex and fragile, the costs are high but the gains are very low (specially on Linux), which makes it a bad tradeoff to make.[/QUOTE]
All right, you convinced me. I am far too ignorant when it comes to Linux to judge myself if the costs are worth the gain, so I'll just have to believe your judgement in this matter.

If someone has another views on the usability of outbound protection in Linux, please post here. I will keep an eye on this thread :)

---

### Post by nocturn on 2006-02-28
[QUOTE=habrys]All right, you convinced me. I am far too ignorant when it comes to Linux to judge myself if the costs are worth the gain, so I'll just have to believe your judgement in this matter[/QUOTE]

Please don't believe me on this.  The more you know, the safer you will be.  

It's just that Linux is quite different from Windows, what is a good idea there my not work here.

For example the signed repositories are something that Windows will not have (except for MS' own products).

---

### Post by habrys on 2006-02-28
[QUOTE=nocturn]Please don't believe me on this.  The more you know, the safer you will be.[/QUOTE]

Of course, but learning needs time and in the meantime I need some opinions. Thank you for yours.

---

### Post by LKRaider on 2006-03-08
> Another example then. I download some malicious software and installed it manually as a root. With mkdir, cp etc. And then run it as a normal user. It tries to transmit data over internet, but can't disable the outbound protection, right? Caught!

You are jumping a crucial step, which is the selection of software you will be installing.

You have to take into account that linux programs (often) are open-source, and that means they are usually the work of more than one person, viewable by anyone and utilized by a comunity of users.

I don't say that there couldn't be an open-source project that was attacked and altered maliciously without anyone taking notice, but the chances of such going unnoticed is so small and may last for such a small time (of people noticing and fixing it), that the tradeoff of actively running an reactive security scheme for that event is just unexcusable.

The process of how software is developed for the linux platform is what sets it apart from the windows-way.

Your judgement and research also comes into place here when selecting your software sources (just ask yourself: have it been implemented elsewhere? what kind of security holes it offers, if any? Is it being actively developed? Does it offer support or has a community? etcetera...)

---

### Post by psusi on 2006-03-09
> **habrys]I can only agree with that: better prevent an infection, than cure it. But I really cannot see how Ubuntu "makes sure that you can't get infected in the first place". Explain, please and remember I'm a Linux newbie.[/QUOTE]

With a default windows install, there are several services that are listening for remote connections.  Several of these services have known bugs that can be exploited to take over your computer.  This is why installing a fresh copy of windows on a PC connected to the Internet without a hardware firewall will result it it being compromised within moments.  

With a default ubuntu install, there are no listening services, and if you choose to install some, they are rapidly kept up to date to fix any bugs found that could possibly be used to exploit your system.  


[QUOTE=habrys]I cannot agree, that outbound protection "does nothing for you". Treat it just as another layer of protection. If the first layer fails (for example antivirus lacking a signature of a fast spreading virus), there is always the second layer: outbound protection. Of course it can be bypassed too given time, effort and enough of coffee, but... it can very well help as well. It's just question of odds. Without outbound protection chances it catches a keylogger transmitting something are 0%, right? With it sitting in place they are significantly bigger I'd say.[/QUOTE]

The problem is that neither of these are protection at all said:**
> And now an example. I got something called "Blazing Tools Perfect Keylogger" under Windows XP a few months ago. It was hidden in a trojan horse, installed itself silently in the system and tried to transmit my keystrokes somewhere. The antivirus programm didn't detect it. But ZoneAlarm gave me a warning "bpk.exe tries to access the internet: allow, deny etc." The first layer of defense (antivirus) didn't work (probably lacking the signature), but the second layer actually did it's work excellently.

The real problem is that you were infected in the first place.  How did this happen?  Because you use outlook and got an email message with a self executing virtus attachment?  Email clients in Ubuntu aren't stupid enough to automatically execute code that could possibly do maliscious things.  

Which is better?  Never to execute code that COULD harm you, or to run a program that looks at the code and decides if it thinks that it IS harmful?

[QUOTE=habrys]And now an example from the Linux world. I tried to find out if there are keyloggers available for Linux too. That's true, they are much more difficult to find, than in Windows world. But I found one: lkl. It can be installed to start silently, listen to keyboard port (0x60 if I remember correctly), log the keystrokes to a file and even send mails with reports to a given address. I did it all and Ubuntu did nothing to give me a warning. lkl even protocolled nicely my linux user and password, which I type in when logging into Ubuntu. Not to mention passwords and other things I typed in web forms (bank accounts!). Little explanation: I started lkl with a script in /etc/init.d, so it was already runnning before Ubuntu login screen shows up :)
[/QUOTE]

Obviously you can make your PC do whatever you want, since you own it.  The question is, can someone else do that without your permission?
[QUOTE=habrys]
Now I'm really a Linux newbie, who just knows how to google to find useful information. I don't want to think what a person with much more knowledge could do.

lkl is still pretty primitive (version 0.1) as it starts in userspace and not as a kernel module. And of course it cannot install itself without root privileges. But still... I can imagine a trojan horse with lkl attached, which can install itself in one of those rare moments, when you work as a root. All right, all right you have to sudo and there is no root account in Ubuntu. But I know people, who do "sudo konqueror" to do their root tasks. And you can always activate the root account, even in Ubuntu.[/QUOTE]

Never forget the old axiom "There is no limit to the depth of human stupidity".  If you download a program from Joe Cool Hacker and run it as root, you get what you asked for.  Stick to running only verified software from the Ubuntu repositories ( let alone as root ) and you will be fine.  

Whatever kind of detection you have in place, once you run a program as root, it can do anything it wants, including disable your detection software.  That makes detection somewhat of a moot point.  

[QUOTE=habrys]
But seriously, don't you think, it's safer, when all your ports are stealthed, as opposed to just closed? If all the ports are stealthed, then you are practically invisible from outside. I think invisible is better, than closed. After port scanning no other tries to compromise your system are made - the hacker or rather script kiddie thinks your machine doesn't exist and moves on, right?[/QUOTE]

No, because that is security through obscurity, which isn't security at all.  It is like generating a very long and complex password that you can't remember, so you write it down on a note stuck under your desk, then claiming you are safe because you have a very complex password.  Well, no, you aren't because all someone has to do is look under your desk. 

[QUOTE=habrys]
One more thought: my router (Netgear WGR614) running a hardware firewall also prefers to stealth ports per default instead of just closing them. It cannot be a coincidence, right? :)[/QUOTE]

Yes, it is a widely held believe that it is a good thing, but that doesn't make it correct.  If someone is probing to see what ports you have open, they won't care if you don't refuse the connections, they will just try them all and see if any work.  

Originally stealthing ports slowed down probes because they only tried to connect to one port at a time, and waited several seconds before timing out.  It didn't take long ( hours?  days? ) before people figured out you can just send all the connection requests without waiting for any of them to be rejected.

[QUOTE=nanotube]
psusi, i will try to point out how good outbound protection works, and then i think you will see that it is not as easy as you say to bypass it.[/QUOTE]

It does not matter what it does because once my virus has infected your computer, it can simply shut zone alarm off.  

[QUOTE=nanotube]first, it checks to see what process is starting a connection to the outside, and runs a checksum verification on the executable to make sure it has not changed. if it has - it warns you. so if some trojan has modified firefox or any other executable that "normally" would be allowed to access without challenge, that will be detected, and prevented.[/QUOTE]

I don't need to modify the executable image on disk, I can have another process force the firefox.exe process to perform the IO on my behalf using the debug apis.  

[QUOTE=nanotube]second, all programs are also by default prevented from spawning other processes - so your keylogger/trojan cannot just spawn firefox or wget and access the net that way.[/QUOTE]

I do not believe this to be the case.  ZoneAlarm does not hook the kernel NtCreateProcess call AFAIK.  It may hook some of the higher level apis that nice applications use, but a virus can bypass those, and again, once the virus is running with root privleges, it can break whatever hooks ZoneAlarm has in place.

---

### Post by CameronCalver on 2006-03-10
where do i get "firestarter" from

---

### Post by Sef on 2006-03-10
> where do i get "firestarter" from

Applications ----->Add Applications ----> System Tools ------> Click on more programs -----> click on Firestarter -----> Apply ------>Apply again -----> just follow any other instructions.

---

### Post by fuzzygenius on 2006-03-13
[QUOTE=Sef]Applications ----->Add Applications ----> System Tools ------> Click on more programs -----> click on Firestarter -----> Apply ------>Apply again -----> just follow any other instructions.[/QUOTE]

Or, in a terminal:

sudo apt-get install firestarter

---

### Post by handy on 2006-03-13
My wife & I run ZoneAlarm Suite, on our xp boxes, I have installed it on the machines of a couple of business LANs that I maintain, so I am fairly familiar with it from the user level, & I have had the opportunity to watch a variety of users come to grips with it...

ZAS, is a problem for the average user, they don't understand anything about the OS, they are usually scared of it.  They are scared to make a choice when a ZAS request is popped up.  The first week of use (when the rules are being established by ZA) is quite traumatic for some users.  Putting extra strain on anyone in the office who does have an understanding!  Or the admin'!

ZAS slows all machines down quite noticeably.  I would never run such software on Ubuntu.  Being free of such software is one of the many joys of using Linux, in my opinion.

I use web based email, with a reasonable anti-virus & spam protection supplied by that ISP.  

Any email that I don't recognise, I delete.

I back up my important files regularly.

My preference is that I would rather reinstall my system in the event of infection, than cripple it with paranoia!

**[EDIT:**] & yes I use Ubuntu for internet banking most days, & any other financial transactions on the web, NO worries! :-D

***This link is a good one re: windoze / linux & security:***

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

---

### Post by vayu on 2006-03-14
[QUOTE=nocturn]
But I maintain that filtering based on application checksums (or names) provides no extra security.  If a malicious application already has root rights (to overwrite binaries) it will not have any trouble disabling the firewall entirely.
[/QUOTE]

It will have the possibility, but just like the variety of legit applications we run they all have different amounts of features behind their design and  implementation.  Many of the arguments here have been of the variety if the program got in it could just do this or that.  Yes it could disable the firewall, yes it could find the hash table of checksums maintained by an outbound security scheme, but that does not mean it's easy or it will.

Just getting a keylogger in there and working would be a pretty good task for an aspiring identity thief.

I'm positive that many scripts (and programs) are installed as root by Ubuntu users alone that the user doesn't read or know what's in it.

I think habrys brings up valid points.  My needs don't dictate the same needs as his, and I don't like to slow my system down with things I don't need, but that doesn't mean that's what's right for everybody.

---

### Post by handy on 2006-03-14
[QUOTE=vayu]It will have the possibility, but just like the variety of legit applications we run they all have different amounts of features behind their design and  implementation.  Many of the arguments here have been of the variety if the program got in it could just do this or that.  Yes it could disable the firewall, yes it could find the hash table of checksums maintained by an outbound security scheme, but that does not mean it's easy or it will.

Just getting a keylogger in there and working would be a pretty good task for an aspiring identity thief.

I'm positive that many scripts (and programs) are installed as root by Ubuntu users alone that the user doesn't read or know what's in it.

I think habrys brings up valid points.  My needs don't dictate the same needs as his, and I don't like to slow my system down with things I don't need, but that doesn't mean that's what's right for everybody.[/QUOTE]

This a valid point that Vayu makes: The bottom line is that you have to do what you think you have to...

Research well before making your decision, which is of course what this thread is about.  Then do what you are comfortable with.

What suits one user, another will be agitated about, another anxious, I guess there is a difference between those two emotions?  I don't know, I don't suffer from those emotions, I have different emotions, no more or less important, just different!! :KS

---

### Post by nocturn on 2006-03-14
[QUOTE=vayu]Yes it could disable the firewall, yes it could find the hash table of checksums maintained by an outbound security scheme, but that does not mean it's easy or it will.[/quote]


It's very easy to disable the firewall, just run 'iptables -F' as root to clear it.

> 
I'm positive that many scripts (and programs) are installed as root by Ubuntu users alone that the user doesn't read or know what's in it.



That's part of my point.  If a users insist on going outside of the trusted repositories without being able to check the safety of the code they download, there is very little we can do to protect them.  
If they blindly install code from untrusted sites, chances are they are going to tell the firewall to let it through (if the code din't bypass it already which would be trivial).

That is why I think we should concentrate on getting stuff like PaX, SELinux or AppArmor installed and enabled by default.  It can help protect users regardless of the threat, regardless of their level of skills and even in the case that they run untrusted code as root.

> 
I think habrys brings up valid points.  My needs don't dictate the same needs as his, and I don't like to slow my system down with things I don't need, but that doesn't mean that's what's right for everybody.

I'm certainly not saying the no-firewall setup is good for everybody.  I intall firestarter on each of my systems myself for several reasons.  Even enabling the outbound blocking is a good idea in some situations (although I don't do that).

It's just that checksums add very little to the current filtering mechanism while being a lot more complex and slower.   
And setting outbound blocking (in any form) by default will break the installation for most novice users.

---

### Post by justask on 2006-03-14
The trouble with ZoneAlarm and other Windows closed source firewalls is that you first have to trust them.

---

### Post by Dml on 2006-03-14
re: if you run as root you get what you deserve.

The .deb files contain or can contain script that can do anything. I suppose them is executed as root. If you install something from .deb you can easily get infected. And people very often download .deb 's of open source software compiled by somebody, and also love to build .deb's for anyone else. There's very real possibility of virus spreading around. Granted, there's not many linux computers, and not many virus writers, but it is certanly possible, and it can spread :( edit: i don't think i'm disclosing anything secret to potential virus writers as they probably know it already anyway.
edit: my point is, it is just as secure in this regard as windows, just less popular.
edit: trusted repositories: hmm, what if i don't want to too much trust the repositories? With all respect, there's lot of software, i don't believe all sources is read by maintainers to ensure that them is virus free.

---

### Post by handy on 2006-03-14
I think that the speed with which the linux community would respond to such a breech of security cannot possibly be compared to windoze!

& due to the open source nature of the software the response would be incredibly effective! :cool:

---

### Post by kencoe on 2006-04-04
Anti-virus software is a maybe. If you are storing docs (particularly downloading and uploading .doc, .pdf. ...) your should be running one. No matter how secure an OS is, you can still distribute it to alot of other people. Even if it doesn't affect you, it doesn;t look too good for the Linux community if we are the ones spreading those things around.

As far as a firewall, every extra step toward security is a plus. There is always a bug in any system. I direct you to the Ubuntu security updates section for a reminder. If a hacker can get a cobalt system or a GA-Bull, you can be cetain that they can find a weakness in your box, too. Every system has a fault, every step toward security is an improvement.

Two other suggestions, though. Stop running any broadcast, or listening services you do not need (i.e. ftp or http servers, port scanners, remote connection hosts OR clients). Also, invest in a NAT router, prefereably with hardware firewall. If you want an easy, basic, check of how secure your system is then go to [Steve Gibsons Site]("http://www.grc.com") and try out his sheilds up! page. It's free, and it is a good start. Besides, then you can read his take on true computer security, or the illusion of it...

---

### Post by derjames on 2006-04-05
Steve Gibson site ([http://www.grc.com](http://www.grc.com)) as Kencoe points out has several check tools (also free software for windows users) , I did use Shields Up! in both Ubuntu 5.10 and Windows XP with Norton Internet security 2005. While Ubuntu passed every single test, Windows XP with Norton failed (Norton firewall set at the recommended level of security i.e default.) I don't know if this is a true benchmark, however I can tell you I did pay 35 pounds sterling for this piece of software (Norton) that cannot even block a ping request at the RECOMMENDED level of security... well this was just a single test based on my own computer, this may not apply to your particular case, but you can perform the same test just to see happens...

---

### Post by peter07 on 2006-04-08
What do you think about that:

"Virus writers have crafted another example of malicious software that can infect computers running Windows or Linux."

[http://news.zdnet.com/2100-1009_22-6059140.html](http://news.zdnet.com/2100-1009_22-6059140.html)

:confused:

---

### Post by airtonix on 2006-04-21
windows is the virus, and when we stop being lazy and realise this things will get interesting. right now wolves vist the field of sheep like a shopping mall. easy pickings...... mmm bit ... like ...the matrix.

---

### Post by cssutto on 2006-04-21
I know you guys are tired of this thread, but I have to tell this because it is really a big joke on me.

I just installed Ubuntu three days or so ago.

And of course having used MS in one form or another from its very beginning, I am paranoid.  On W2K, i run a firewall, NOD32, and about seven or so anti-spywares, because as we know none of them get everything.

So the first thing I did is load firestarter and clamav.  I can't get clamav to run, so that is how I ended up here.

Firestarter astounded me.  It loaded with no effort at all and of course I immediately went to Steve Gibson's Shield's Up to test it.

I was absolutely amazed.  The very first firewall, and I have had five over the years, that on the very first try closed all of the ports.  Complete stealth on the first try.

Amazing.  In the past, I would muck around for days to get the right combination of closed ports and a system that would work.

So looking for a solution to my clamav problem, I read all of the posts here and was surprised to learn so much in so few minutes.

So I turned firestarter off and went back to Shield's up and guess what?  All of my ports are closed and gave the all green stealth results that Gibson is so proud of.

So I learned a big lesson today.

Thanks, guys.

Now if I could just get that darn network thing to save my dialup numbers, ISP addresses etc, so I do not have to fill that in every thime I dial up, I will have resolved all of my dial up problems.

By the way, the reason I am moving to linux is that I got so tired of MS's constant panic's over security.  All of that stuff is a pain.

You are right.  MS is the virus we all need to run from.

I have stuff over 20 years old on my W2K machine.  I am playing with Ubuntu on an older machine.  In a few days, I am going to set my main machine up with dual boot unless I learn of a way to read that old stuff without it.

I have PeachTree accounting for two companies on the W2K and old Lotus 1-2-3 spread sheets and Lotus Word Pro docs that are old old old, but I can't get along without them, at least until I find a replacement.

Anyone who has been that route and can give me some advice, will be appreciated.

But thanks for the big lesson on firewalls.

CSSJR

---

### Post by und3rtug4 on 2006-05-13
In my opinion, I would not use any of them......

.... it depends of the scenario!

ClamAV if it is on a mailserver or some system wich trade files with users with diferent OS, this will reduce the infection of Win systems!

I dont use firestarter cause my machines are in a secure LAN, wich is protected with firewall and nat!

But my laptop that is always with me, anywhere I go (yes, to the bathroom to :mrgreen: ), is protected by firestarter, but no AV soft!

Conclusion: You must analise the function and surrounding enviorament of the machine that you configuring, so that you can meet the security needs, without  lost of usefull resources and accessibility!

Props to all!

;)

---

### Post by kencoe on 2006-05-14
[QUOTE=und3rtug4]I dont use firestarter cause my machines are in a secure LAN, wich is protected with firewall and nat!

But my laptop that is always with me, anywhere I go (yes, to the bathroom to :mrgreen: ), is protected by firestarter, but no AV soft! [/QUOTE]

We must also remember that most security policies now recommend installing software firewalls on individual machines within a secure network to help prevent the possibility of internal attack. It would depend on how much your network users are really trustable, and how high tendency is to install questionable apps that aren't. There are many newer Admins checking these forums as well...

For all the new admins reading... Use Whitelist mode!!!

---

### Post by Raavea on 2006-06-14
In my opinion, we should always be kitted up ready.

I mean, yeah, in a few minutes you can install these things, but what if some nasty thing has blocked out those abilities?

So, in my own PC, I have firestarter, chkrootkit, rkhunter, and am thinking of installing avast! for linux. I was always very impressed with avast! as I installed it on a few friends' XP boxes, and it found, on one system, over forty trojans, viruses and worms, that norton had said weren't there. I installed avast! for linux a while back, on Breezy, but it was impossible to read because somehow the letter-spacing had been completely bummed...

I'm going to go find this shield up thingy, it sounds interesting...

---

### Post by eX0r on 2006-06-16
A default, updated install with no firewall is immune to every existing network attack e.g. ICMP based ?

---

### Post by kencoe on 2006-06-21
> ... but there are no known virs in the wild for linux, so your clamav would just be sitting there doing nothing and eating your resources.

There are at least three known viruses for Linux. Fortunately, none of them do anything unless run as root and ignored, and then do little damage. Still much better the Windows or Mac.

---

### Post by flamarro on 2006-07-28
Having read all these amazing pages and as a newbie ( not newbie for starting to use ubuntu, but really for jumping always between XP and linux. Use XP, but theres always a litle voice saying, "go to ubuntu, it's much better now", looks like a itching, :smile: and there i am again with another try) i'd like to ask something.
As mencioned by others, i too, used automatix for install a lot of stuff ( yes, that was a lazzy thing to do ).
Sometimes i use Amule and Azureus ( yes, sometimes i lose some episode of one particulary show i like :) ). Therefore, i use a ipfilter ( Moblock ) and like it seems, there is a trouble running it with firestarter, because the two of them can't work together. So, when i go and use this programs, i turn moblock on, therefore, shuting off firestarter.
So now i have a fresh installed ubuntu, tweaked with automatix, running a firestarter firewall that don't block anything, only shows what passing by on my PC, and a moblock ipfilter that is really working. All of this in a ADSL connection on a Dlink router with nat. Is this for instance, a well protected machine, running only moblock without a firewall?
Another question, on a fresh install, only using oficial repositories, is there any trouble only by using firefox, no matter the page i go to, and other programs, even if they are not the most updated ones?


Sorry to ask these question, but consider like a summary of all that has been said. I think like me, there is a lot of guys in my condition and don't now if they are really protected.

PS: Again, sorry for my english

---

### Post by ciscosurfer on 2006-08-11
> **nanotube said:**
> my take on that would be a "no". although if you had to choose just one of the two, i would go with firestarter. :) a firewall is always a good thing... but there are no known virs in the wild for linux, so your clamav would just be sitting there doing nothing and eating your resources.
If you're running SMB, NFS, etc. (sharing with Windows) on production machines, then a good AV solution to "nip it in the bud" is a good solution.  A good hardware firewall (or firewall/router) is the best, and should the first, line of defense.  Firestarter and clamav I suppose are okay to use on top of these defenses, but in this authors opinion, completely unnecessary (and use up cycles as well).

And I'm going to have to disagree slightly with you nanotube: while the spread is not very significant, there are indeed Linux viruses, worms, and trojans out in the wild.  Here [is short list]("http://www.viruslibrary.com/virusinfo/Linux.htm") (and these are only the ones with "linux" in there name....keep in mind also that there are a number of known vulnerabilities in server-type programs such as Apache, etc.)  Another point: the link above is not exhaustive by any means...simply do a search on the web for linux and virus and you'll be surprised!

---

### Post by byte69 on 2006-08-15
I use both firestarter and clamav.  I think its better to use the tools given then to hope a zero day does not come up and byte Linux.   *nix is better secured as an OS in general.  But things running on top of that OS can cause you problems.   Like OpenOffice scripting vulnerablities that were just pointed out.   
[http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9002430]("http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9002430")
In theory it would not effect the underlying system but may effect your data etc.   So why take the chance?   Its avalible and useful.   The argument that it waste clock ticks.   Come on ~80% of your cpu time is idle anyway.   

Using layered defenses is good.  I wish Ubuntu had SELinux built in also just for the extra security.  In its place I have installed>  [http://www.ossec.net/]("http://www.ossec.net/")  OSSEC HIDS - Open Source HIDS.  "OSSEC HIDS is an Open Source Host-based Intrusion Detection System. It performs log analysis, integrity checking, rootkit detection, time-based alerting and active response."  

BYte69

---

### Post by missmoondog on 2006-08-15
i use firestarter is all. mainly because of that error you always get saying clam is out of date and then won't update itself!

i think i use pretty good, basic, common sense about what i open and such.

---

### Post by ChadMMc on 2006-08-15
I use Firestarter and not the ClamAV (I had the same problem as missmoondog)

I have checked my ports and ping return status with the Shields UP! web site and I am in stealth mode on all my ports and in the ping handling. 

I would use the ClamAV eventually if it would work correctly. ](*,)

---

### Post by ice60 on 2006-08-16
hi, generally if you run something from an untrusted source there's a chance it could be malware and erase the most important and least protected directory, and also the one directory whcih can't be replaced in 15 minutes - your home directory.

there was the time the Mozilla repos had malware, so even trusted soruces can have malware.

alot of anti-virus scanners depend heavily on something called heuristics, which means they don't have to have sigs for the lastest malware. heuristics will pickup the code. you can read about F-Prots virtual Employee below
[http://www.wilderssecurity.com/showthread.php?t=136830](http://www.wilderssecurity.com/showthread.php?t=136830)

i'm not really sure but nmap can probably see 'stealthed' computers maybe with the new bad checksum option.

---

### Post by Pumm4 on 2006-08-18
> **kudu said:**
> Especially since I connect through a router, do I really need firestarter and clamav ?
No, unless you are runing a server.

> **habrys said:**
> I can only agree with that: better prevent an infection, than cure it. But I really cannot see how Ubuntu "makes sure that you can't get infected in the first place". Explain, please and remember I'm a Linux newbie.
iptables is Linux's firewall which has been a part of the kernel since version 2.4.

It is often referred to as a packet filter as it examines each packet transferred in every network connection to, from, and within your computer.

iptables replaced ipchains in the 2.4 kernel and added many new features including connection tracking also called as stateful packet filtering.

Rules, Targets, Chains, Tables, States, and all that stuff

iptables makes decisions on what to do with a packet based on rules that the system administrator creates.

Data is passed through the Internet in the form of packets of information; connecting from your computer to a website will cause many packets to be exchanged in both directions.

To understand the user concept of Linux... A user without root privileges cannot damage the entire system. Any damage caused is strictly limited to the user's own account and data. Any operation caused with root privileges may potentially harm the entire system. Anyone intending to harm a running Linux system must gain root privileges first. This is why it is much harder to create viruses for Linux systems. They must overcome the root barrier first.

> 
And now an example. I got something called "Blazing Tools Perfect Keylogger" under Windows XP a few months ago. It was hidden in a trojan horse, installed itself silently in the system and tried to transmit my keystrokes somewhere. The antivirus programm didn't detect it. But ZoneAlarm gave me a warning "bpk.exe tries to access the internet: allow, deny etc." The first layer of defense (antivirus) didn't work (probably lacking the signature), but the second layer actually did it's work excellently. 
If converting to a Linux system from a MS Win system, you probably experienced a fair share of trouble caused by multiple kinds of viruses and worms spreading over the Internet via e-mail. Now that you have made the switch to Linux, you can at least put that fear aside, because these cannot harm a Linux system as easly as Windows system.

> 
lkl is still pretty primitive (version 0.1) as it starts in userspace and not as a kernel module. And of course it cannot install itself without root privileges. But still... I can imagine a trojan horse with lkl attached, which can install itself in one of those rare moments, when you work as a root. All right, all right you have to sudo and there is no root account in Ubuntu. But I know people, who do "sudo konqueror" to do their root tasks. And you can always activate the root account, even in Ubuntu.

What I'm trying to say is, I think lack of outbound protection is still a security gap in my opinion. Not as huge as in case of Windows, but it should be closed some day, especially if Linux gains much more popularity... Switching from your normal user account to root for administrative tasks and switching back for your normal work sounds tedious and perhaps unnecessary because root has ultimate power over the system. Still, switching back to the normal user account after accomplishing the administrative jobs adds to security, because any mistake made as root can have severe consequences.
The whole system might be affected, not just the normal user account. Thus, preserve your system's integrity by clearly distinguishing between the different roles ("normal user" and "superuser").

Keeping your system up to date by always applying the software updates to add security to your system. These updates fix possible exploits contained in the application code.

> **habrys said:**
> 
After port scanning no other tries to compromise your system are made - the hacker or rather script kiddie thinks your machine doesn't exist and moves on, right?
Wrong. (BlackHat) Hackers do not use click-me programs like trojans or exploits to help them gain access. They do not attact home users unless there is a good reason for it. Not long ago there was an article on zdnet dot com "Mac OS X hacked under 30 minutes" well Windows can be done under a minute.
> 
But hackers are also only people, which can overlook something. For example to disable your outbound protection, even from a trojan horse running under root. Or to install something tampering with your logs. 
Hackers = skills above advanced user. They don't do mistakes, but Script Kiddies do.

> **nocturn said:**
> Please don't believe me on this. The more you know, the safer you will be.
It's just that Linux is quite different from Windows...
That's because Windows is not Linux. ;)

> **ciscosurfer said:**
> 
And I'm going to have to disagree slightly with you nanotube: while the spread is not very significant, there are indeed Linux viruses, worms, and trojans out in the wild. Here is short list (and these are only the ones with "linux" in there name....keep in mind also that there are a number of known vulnerabilities in server-type programs such as Apache, etc.) Another point: the link above is not exhaustive by any means...simply do a search on the web for linux and virus and you'll be surprised!
There are more nasty codes outside that are not listed in that link.

> **byte69 said:**
> I use both firestarter and clamav. I think its better to use the tools given then to hope a zero day does not come up and byte Linux. *nix is better secured as an OS in general. But things running on top of that OS can cause you problems. Like OpenOffice scripting vulnerablities that were just pointed out.
[http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9002430](http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9002430)
In theory it would not effect the underlying system but may effect your data etc. So why take the chance? Its avalible and useful. The argument that it waste clock ticks. Come on ~80% of your cpu time is idle anyway.

Don't believe everything you read. As you can see that site is closed source related. Article is trying to say "Hey buy MS Office and stay bug-free". 

Have Phun

---

### Post by ciscosurfer on 2006-08-18
@Penguinux Pumma
I couldn't agree more with (nearly ;)) everything you said. Excellent post!

> Another point: the link above is not exhaustive by any means...simply do a search on the web for linux and virus and you'll be surprised!                                  
> There are more nasty codes outside that are not listed in that link.Indeed!

---

### Post by clapper65 on 2006-08-25
I move my Ubuntu laptop from home to work quite a bit.  Corporate policy is to have anti-virus on every machine on the network.  So I installed clamav, just to play by the rules.  I've not heard of any good reason not to.

---

### Post by ciscosurfer on 2006-08-25
Just understand the limitations of anti-virus software for Linux:  Just like their Windows couterparts, they do nothing to stop a zero-day attack, among other limitations.  If you feel more secure knowing that you have an AV scanner running, then by all means, go ahead and use it.  But it is important to understand how Linux virii propogate, etc.  Some earlier posts in this thread address this issue.  I'm of the opinion that on a Linux box, it's more conducive to use a firewall than an AV program.  But do some research and then you decide. And in the end, it's all about smart user practices. :-D

---

### Post by frankie_d on 2006-08-26
I think a lot of new Ubuntu users and newbee linux users in general are asking the questions.
I just installed Ubuntu 6.06. Have been playing with differet Linux distros for a long while. I am a long time windows user and I do believe the Ubuntu 6 is the best yet. I too had the question in my head "what kind of security do I need. Duh- Linux is the security...Bye Bye Windows :) :)

---

### Post by gannic on 2006-08-27
I just dont get it....

Someone else pointed it out....lets say 50% of ubuntu users use automatix. Thats universe and multiverse stuff. One piece of malicious code and thats it...%50 of linux users infected.

'Its the same or worse on windows' seems to be the linux cry....well....yes, but what now for windows...a week later all the antivirus/spyware tools catch up and wipe it out - the damage may have been done but the users get a chance to change passwords etc when they are found. What about linux...... nothing.... that malicious code just sits there as far as I can tell. Linux has no user friendly protective measures or scanning at all.

I am new to Ubuntu, but I think there is an advantage to Windows over Linux not mentioned...saftey in numbers...there are a lot of machines to be infected before yours; many poorly protected - meaning hackers neednt bother writing complex scripts to disable zonealarm. You have a really good chance of escaping. On Linux there seems to be a big group who claim to only use trusted repositories, so dont play DVDs, use their computers for jukeboxes etc etc., and no way of detecting an infection of any type. Probably the hackers are more able too.

I just turned on outbound blocking on Firestarter and its terrifying. I am getting at least 5 to 10 outbound connections a second. Thats after I have opened the 2 ports I think I need. Allsorts of things are turning up, so many I am thinking I need to reinstall ubuntu.

As far as I can see the truth is you dont need AV or firewall packages on linux because they are not as functional as they are on windows. Someone already said, its about layers - but without the code from the universe and multiverse hardly anyone would be using Ubuntu or Linux for home computing, because there is too much functionality missing.

---

### Post by skymt on 2006-08-28
Universe and multiverse are screened. You can't just submit a package and get it in. You have (practically) no chance of getting burned by installing a package. If you do, you have to re-install from scratch to be sure the scumware is really gone, no matter what OS you run.

About your Firestarter worries: please run ps -e in a terminal and post the output. We can help you find out if you really have something.

---

### Post by saintj0n on 2006-10-04
Aren't script type "viruses" still possible? It would be crude and unable to hide under close scrutiny but someone could theoretically slip you a malicious script. Linux is sophisticated and slipping in a bash script in with a phony email would work right? It would be a cheesy thing to do but if someone has a grudge......:twisted:

---

### Post by Perfect Storm on 2006-10-04
But you have to make the script executable first and then run it with admin previledge.

---

### Post by airtonix on 2006-10-09
yep, sudo is king. long live the sudo...

Three cheers for sudo...

Hip hip...Horray
Hip hip...Horray
Hip hip...Horray

---

### Post by eeried on 2006-10-11
Hello,

I have no firewall yet because i'm running Xubutu and installing Firefstarer (which I used on ubuntu Breezy) would install loads of gnome stuff. I didn't close any ports myself.

This is the report I got from  [ShiedsUP]("http://www.grc.com/x/ne.dll?rh1dkyd2")

All ports closed and three stealthed

> Solicited TCP Packets: RECEIVED (FAILED) — As detailed in the port report below, one or more of your system's ports actively responded to our deliberate attempts to establish a connection. It is generally possible to increase your system's security by hiding it from the probes of potentially hostile hackers. Please see the details presented by the specific port links below, as well as the various resources on this site, and in our extremely helpful and active user community.

Unsolicited Packets: PASSED — No Internet packets of any sort were received from your system as a side-effect of our attempts to elicit some response from any of the ports listed above. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system remained wisely silent. (Except for the fact that not all of its ports are completely stealthed as shown below.)

Ping Reply: RECEIVED (FAILED) — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.

Conclusion: a firewall is necessary to pass the test.

In my mind ClamAv is necessary only to make sure you don't pass viruses from infected files you may have received to Windows users. At least this is the present situation. I guess we'll be informed if Linux viruses get really nasty for the common user on her desktop.

---

### Post by deepwave on 2006-10-19
I think Bastille is a better option to secure a Linux box then firestarter or clamav.

ClamAV is really only good for an email server with Windows clients.  It really doesn't make much sense to write a Linux virus.  Worms are more of a problem.

As for a firewall, unless you are worried about a lot of traffic (or fear a DDOS) I would not bother.  A better way is to uninstall unwanted services, and keep your system up-to-date.

---

### Post by Blutack on 2006-10-23
Another thing is that linux users tend to be more computer literate than most windows users (the ones that get upset because they can't find my start button or Windows Media Player on my laptop...).  We are more aware of basic security measures like not running files we don't know and not running as admin.
I am not downplaying the security of linux.  It is fantastic.  The total failure of relying on external programs for security has already been well proved by m$ already.  Any process can be terminated by malware with enough privilages.  Most of security is stopping it getting in first.
And to those who distrust them, I'd take apt-repositorys over shoving 'free windows painting program' into google any day.

---

### Post by airtonix on 2006-10-25
I find it hilarious that to "stop" a windows system you first have to click on the  "start" button.

lmao

No wonder new computing neophytes who are birthed on windows are confused about what a computer really is.....gee some think its a vending machine.

---

### Post by gerowen on 2006-10-29
I use firestarter to monitor and control traffic because I run a small personal web server, and am on a network with Windows machines which requires me to open certain ports at certain times, so I like to have a quick and easy way to manipulate my firewall policy.

I have a whole different philosphy about antiviruses though.  As I said in another thread, a virus is a program just like any other, it just does things that you don't want and that harm your system like delete necessary operating system files and such.  The fault with antiviruses comes due to the fact that they only detect "known" viruses.  I or anybody else who knows a programming/scripting language could write a malicious file to delete files, or create a really big file until the hard drive is full, whatever we wanted.  The funny thing is, not one antivirus in the world would pick it up.  An anti-virus is "helpful" if you're sharing files with a Windows system where the user has full read/write privilages to the entire disc, but other than that it's pretty useless.  True virus protection should come in the form of a well structured operating system, not in the form of another piece of software to eat up your system resources.

---

### Post by redwolf963 on 2006-10-30
As far as MS and viruses go,their OS is set to an unreal *trust* environment.

Even in the new version,Vista,the permissions that programs need to run,are at a level that are *unsafe* for average users.And that's a shame that a company that sells itself as "user-friendly"..ie.It just works!...can still turn out such low-security requirement code.
I was looking forward to the new file system they were coming out with,that never materialised.

OK,enough knocking MS.At the end of the day,they still have a big lock on the market.Consumer and business.

Luckily,for linux users anyway,the virus threat has not really developed as a viable playground for the malicious type's that use their skills to steal money,credit card #'s,bank acct's,and so on.

Never forget that the first virus,or rootkit,was written on a UNIX machine.
Therefore,you still need to be vigilant in ways most common users don't consider.
NEVER CONNECT TO THE INTERNET WITHOUT A FIREWALL!

IPtables may be too granular for some users,I mean too difficult for some to decypher,especially MS users.I believe the knocks of learning to configure your own system far outweigh any of the perceived difficulties.
My message?:Let's get the word out about what the average linux user already knows....Wannabe secure?Try Linux!

Sorry for the length of this rant,
Regards, Scott

---

### Post by dannyboy79 on 2006-10-31
i have a netgear router/switch/firewall between my internal network and the cable modem. I do have virus protection and a firewall running on winbloz xp so I figured I would install firestarter and add some rules. Besides adding the normal ports like ftp, ssh, telnet, and the ports I use for bittorrent, what else should I be adding in the rules of either outbound or inbound within Firestarter? Keeping in mind that I do need to share files thru Samba between my Xubuntu laptop, my 3 xbox's which run xbox media center, my winbloz xp machine, as well as my ubuntu server machine (which is were I have firestarter installed) any suggestions would be very appreciated. also, am i understanding clamav correctly, it doesn't run all the time does it, only when I open it and tell it what folders and files to scan? or can I have it running all the time? how does clamav's virus file or definitions get updated if it's not running all the time? thanks for anyones help.

---

### Post by Chxta on 2006-11-13
[http://www.pcw.co.uk/personal-computer-world/software/2151042/avg-free-linux](http://www.pcw.co.uk/personal-computer-world/software/2151042/avg-free-linux)

I'm giving it a try because I think we are getting a little over confident in the Linux world...

---

### Post by crouton on 2006-11-14
My two cents:

If it's available, and it works, and your machine can spare the resources (and most machines these days can), then there is no reason not to have a firewall and AV running.  You don't have to run everything locked down, but getting in the habit of using these programs is a good idea.

---

### Post by PilotJLR on 2006-11-19
Exactly! If you are not running any services, then an iptables firewall is pointless.
Behind a normal SPI NAT router, you're fine with no iptables firewall. Especially if you have no services... then you need no firewall at all.

---

### Post by Circus-Killer on 2006-11-20
i see a few people suggestion to install firestarter, stating that "having a firewall is good". when you first install ubuntu, a firewall is already up and running.

firestarter is merely a nice gui to make setting up the firewall easier for the end user. as for clamav, its not really necessary if you not connected to other windows machines on your local network.

so, basically, the answer is no, you dont need either. you might want firestarter if you wanna customize your already existing firewall,  but it is not necessary.

---

### Post by Cynical on 2006-11-20
[quote=marcusdean.adams]The fault with antiviruses comes due to the fact that they only detect "known" viruses.[/quote]

not true

[http://en.wikipedia.org/wiki/Antivirus#Approaches](http://en.wikipedia.org/wiki/Antivirus#Approaches)

---

### Post by ciscosurfer on 2006-11-20
> **Cynical said:**
> not true

[http://en.wikipedia.org/wiki/Antivirus#Approaches](http://en.wikipedia.org/wiki/Antivirus#Approaches)Heuristics are fine, but zero-day attacks really suck.

---

### Post by Jiawen on 2006-11-28
I am still kind of confused about whether or not I need Firestarter...

My machine has been running 6.10 since around the beginning of this month (November 2006), and before that I was running Mandriva, under which I used Firestarter. I currently have Democracy 0.9.1 installed and I occasionally use other Bittorrent clients. I installed Firestarter a couple days after I installed Ubuntu, ran it once then read a bit more here and elsewhere that said I didn't need any firewall other than iptables. 

But earlier today, I noticed that Democracy was connecting to the Internet even when I didn't have any active downloads, so I rebooted and started up Firestarter to check what was going on. Apparently, Democracy is a true Bittorrent-style client and uploads as well as downloading. That's cool with me -- that's the whole purpose of Bittorrent, after all -- but I have Democracy set to use ports between 8500 and 8600, and these connections are all over the place: 10044, 23245, 55785, etc. When I close Democracy, most of the connections go away, but one remains -- that connection to 10044, with a connection that resolves to tm.net.my, the program listed as Python 2.4.

Is this connection okay? How do I get Democracy to *actually* use only ports 8500-8600? Is Democracy unsafe to use? What about other torrent clients? Is Firestarter/iptables not doing its job?

Thanks!

---

### Post by koanhead on 2006-12-04
I have had problems with both firestarter and clamAV. Firestarter causes troubles with Azureus- sometimes it wants to block the port that Azureus uses and there seems not to be any easy way to explicitly instruct firestarter to leave that port alone. 
    The more serious difficulty was partly due to my own dumbassitude. I ran a clamTk scan and set it to automagically quarantine any matches. It decided that gdm was a virus (!) and 'quarantined' it. I would have caught this and changed it but I was playing around with a game that went fullscreen and bogged the system so badly that I had to kill the X server to get my machine back... and the X server was permanently dead after that.

---

### Post by Perfect Storm on 2006-12-04
heh, don't trust these so called anti-virus applications, the moral of the story. I've seen many thread about false detections and none about actual a virus.

---

### Post by drphilngood on 2006-12-04
> **koanhead said:**
> ...I ran a clamTk scan and set it to automagically quarantine any matches. It decided that gdm was a virus (!) and 'quarantined' it. I would have caught this and changed it but I was playing around with a game that went fullscreen and bogged the system so badly that I had to kill the X server to get my machine back... and the X server was permanently dead after that....

Yeah´, I´ve seen auto-quarantine hose linux and windows machines, alike.

---

### Post by cj100570 on 2006-12-30
> **kudu said:**
> Especially since I connect through a router, do I really need firestarter and clamav ?

If your computer is connected to the internet and you send and receive mail, "Yes", it's necessary! If nothing else it's simply insurance against something happening. The AV scanner will at least let you know that there's an infected file on your pc and prevent you from sending it on to someone else. As for the firewall, it can help you harden your system against attacks and monitor it to let you know when someone is probing your machine. I've been using Linux for 3 years now and I've noticed a complacency about viruses that's dangerous. Just because there aren't any known viruses "now" doesn't mean that it's going to stay that way. There is undoubtedly some malcontent sitting at his pc right now brewing up a payload just for us.

---

### Post by Mzee nyuki mpya on 2007-01-01
> **Artificial Intelligence said:**
> heh, don't trust these so called anti-virus applications, the moral of the story. I've seen many thread about false detections and none about actual a virus.
I run Edgy with Firestarter & Clamav. I use a router (Netgear DG834) with a built-in firewall. When I ran a Clamav recursive scan yesterday, it found 2 viruses, both called HTML.Phishing.Auction-270, which I quarantined and then deleted. The really scary thing for me was that the files consisted of gzip compressed data. Are these linux viruses? If they were Windows viruses, surely they would be .exe files? Obviously I didn't unzip them to find out any more.
I Googled the name and the only Antivirus company that came up with anything about it was Clamav, so well done to them. I've tightened my browser security further, not allowing any History, etc. I've upgraded Opera to version 9.10, which has the ability to enable Fraud Protection, which they have just developed to reduce the phishing threat, but I'm still worried about my online banking and my Gnucash data security.

---

### Post by malakhi on 2007-01-05
> **Mzee nyuki mpya said:**
> I run Edgy with Firestarter & Clamav. I use a router (Netgear DG834) with a built-in firewall. When I ran a Clamav recursive scan yesterday, it found 2 viruses, both called HTML.Phishing.Auction-270, which I quarantined and then deleted. The really scary thing for me was that the files consisted of gzip compressed data. Are these linux viruses? If they were Windows viruses, surely they would be .exe files? Obviously I didn't unzip them to find out any more.

That particular "virus" is not a virus in the traditional sense of the word. It's essentially an internet scam that ClamAV found in your history. While it is malicious, it does not pose a risk to the data stored on your computer. It is strictly confined to the browser (still not to be taken lightly).

That said, no, these are not "Linux viruses." Instead, they are referred to as [phishing]("http://en.wikipedia.org/wiki/Phishing") attacks. The fact that it was gzipped isn't all that unusual. Most modern web servers and browsers have the ability to use gzipped html to save bandwidth.

---

### Post by Mzee nyuki mpya on 2007-01-07
Thanks, Malakhi,
                       I feel less worried now; I've deleted all the History in Firefox and Opera, so I should have got rid of this security problem. I'm pleased that Clamav picked it up, although I understand now that it's not strictly a virus.
    The incident has made me determined to run scans more frequently. Unlike some of the contributors to the forum, I think it's a pity that there is no option to easily install Clamuko so that any security threats can be caught immediately rather than lurking until the next scan. This could be the default and those who don't like it should have the option to opt out if they are worried it will slow their browsing experience.

---

### Post by saphil on 2007-01-08
Firestarter is a gui front-end for the linux firewall built into the kernel. 

Whether you have or don't have the gui, you have a firewall.  
You have a firewall containing or using unknown iptable rules.  Even though firestarter is not exactly groundbreaking gui technology, it does give you a gui interface for looking at very simple general firewall settings.  

Why not keep it?

---

### Post by RobMBaker on 2007-01-18
This thread is so long! Sorry, but I'm gonna be a bit lazy and just ask my question; rather than reading through the other half of the thread (that I got tired of reading) ...

I (like habrys [i think that was the user]) use internet banking and other sensitive internet accounts; and would prefer my passwords to remain secret. I know that a system-wide virus cannot install itself in Ubuntu without sudo; but could a keylogger just install itself on my user account? Are all files downloaded automatically set with no executable property? If so, good (but could I have a source to read that from please); if not, is it possible to make sure a rogue website (unlikely, I know) doesn't covertly install a keylogger on my account (in my home folder, say). In theory, could that happen?

Also, if I was dumb enough (or someone who I was letting use my machine) to install a keylogger by mistake (not as root, that's too dumb - just as part of another 'rare' program from a little-known repository, installed in my home folder); could that keylogger then send out its logs via firefox etc., or even record my keystrokes to begin with?

The final issue is void if the above two are not problems: if a linux virus (I know they exist, even if there aren't many) managed to install itself in my home folder; could it possibly 'jump' into a root folder the next time I run Update Manager or some other task that requires my entering the supervisor password?

That's all a bit messy, but I hope my questions are clear. I've been using Ubuntu for a few months now, and haven't had a problem; but I just wanted to clear this issue up, just in case I've been riding 'beginners luck' thus far ...

---

### Post by RobMBaker on 2007-01-21
Sorry, but I really want an answer for at least one of my sub-questions; but no-one's even posting ... don't want this thread to get forgotten ...

---

### Post by SZF2001 on 2007-01-21
Yes, I have been wondering this myself. Any help anyone?

In fact I'm looking for a keylogger to install for my parents since, well, if they ever switch to Ubuntu they'd like to have one so they know what the kids were up to, ya know.

---

### Post by ssavelan on 2007-01-22
I just tried firestarter and it is working very gracefully it seems.

Yet, it gives me a red hits

Time: Jan 22 01:17:23 Source: 81.8.167.100 Destination: 66.56.19.178 In IF: eth0 Out IF:  Port: 21 Length: 60 ToS: 0x00 Protocol: TCP Service: FTP

Time: Jan 22 01:17:26 Source: 81.8.167.100 Destination: 66.56.19.178 In IF: eth0 Out IF:  Port: 21 Length: 60 ToS: 0x00 Protocol: TCP Service: FTP

These are in red within the 'events' tab in the firestarter gui.  I blocked them, assuming that my right-click user interface-input was well recieved (my computer runs so fast with ubuntu that without a notification that something has happened, I sometimes don't know if it has done anything).

The panel icon the goes to a red lighting bolt and says something like "hit recieved from ####."

Any ideas if I should worry or not?

---

### Post by Mzee nyuki mpya on 2007-01-22
In short, no, I don't think you should worry; actually it's proof that Firestarter is doing its job. When I went broadband I bought a router (Netgear DG834) with a built-in hardware firewall and I very rarely see any change to the nice reassuring blue panel icon.
However, when I was on dial-up Firestarter used to scare me. On _average_ it detected 2 "serious attacks" _every minute_! Sometimes Firestarter failed to detect my external hardware modem at all, although I could still connect to the Internet and send and receive e-mails. So presumably at these times all these attacks were getting through! I was so scared I  signed up for broadband, even though I could hardly afford it. (I am very glad I did, though - I can now install all available updates without having to look at the size and work out how much it was going to cost me, paying by the minute for the time I was connected.) 
Of course it's not for this thread for me to wonder why it's such a big deal for dial-up modem manufacturers to allow their products (which we have paid good money for) to work with Linux, when an ADSL router that doesn't cost that much more just works...

---

### Post by LKRaider on 2007-01-22
There are a few keyloggers for linux [[1]]("http://sourceforge.net/projects/lkl") [[2]]("http://distrojockey.com/2005/ultimate-linux-keylogger-uberkey.190.linux") [[3]]("http://www.securiteam.com/tools/6B00L0U95Q.html")

So, it IS possible someone to install a userspace keylogger on your home dir and try to send the logged data out.

The point is who do you trust to get your software from? If you are running software from possibly insecure locations there is not much you can do to protect the system.

If you *must* execute software that can't be trusted, your best bet, IMO, is to run it in throwaway virtualized environments.

---

### Post by RobMBaker on 2007-01-22
I know *I* could install some dodgy software on my userspace that could do some (limited) damage ... but could some dodgy software install itself on there? Hence my question about whether ALL incoming files are marked non-executable or not ... which I still haven't found a convincing answer to ...

---

### Post by LKRaider on 2007-01-22
Whether they are marked non-executable does not matter much, since you still have to tell them to execute manually.

What I mean is, if you are worried about downloading files off possibly insecure locations, it might be better running your browser/internet apps on a chroot jail or virtualized environment and also executing possibly malicious code inside throwaway virtualized setups.

---

### Post by RobMBaker on 2007-01-24
Thanks LKRaider; but I was just wondering whether any (rare) malware could get onto my system by itself; just from a dodgy web-page. It's because I'm thinking about installing Edgy for my parents; and I don't want them accidentally getting a virus/keylogger ... however rare they may be for Linux.

---

### Post by LKRaider on 2007-01-25
chroot the browser, setup an adblocker+noscript and they'll be fine :)

---

### Post by RobMBaker on 2007-01-28
Thanks LKRaider; could you possibly point me in the direction of a how-to for the chroot part? I take it there's a man page about it too, but how-tos are generally easier to follow ...

---

### Post by LKRaider on 2007-01-28
Unfortunatly I could not find a specific how-to for securing Firefox in a chroot jail.

You could try an follow the guides for running Firefox 32bit on 64bit systems, like the [32-bit Chroot How-To]("http://ubuntuforums.org/showthread.php?t=24575").
Notice however that these guides do not focus security, so don't just follow them blindly.

One thing you have to make sure is that the regular user can execute the chrooted program without the need to be root, since that would be even more dangerous than simply running it as the regular user outside of chroot.


If this chroot process turns out to be too much trouble, as an alternative you could create a limited user account and setup firefox to only be executable from there and with limited privileges. This would effectively secure the regular user folder and the root filesystem aswell, if correctly set.

Would be nice to have how-to's for all this, but sadly I found none :/

---

### Post by RobMBaker on 2007-01-28
Thanks very much for the info.
I think I'll try the 'limited user account' path - as that's probably adequate for my needs.
If I turn off scripts and only allow specified cookies; I reckon it'll be fine.

Thanks again.

---

### Post by Clint. on 2007-02-04
If you want to really get into the network security aspect of the system, check out   [http://www.netfilter.org/](http://www.netfilter.org/)   ,  also you can visit  [www.insecure.org](www.insecure.org)    as well.  There is Nothing wrong with making your system secure and understanding what your doing to the system.  It builds a good level of confidence.  Also, with installing vmware and hacking the vmware workstation to be optimized, its by far more secure than any stand alone windows platform. After I acquire 2 GB of ram, I am going to be isolating Windows Vista Ultimate, like I did with my Windows XP Professional VLK".  Its great working with debian, ubuntu, and Securing Windows Systems.  You always have more options. :- )

[http://i115.photobucket.com/albums/n312/clintsnet/debiangnulinux2007pic-01byZoo.png](http://i115.photobucket.com/albums/n312/clintsnet/debiangnulinux2007pic-01byZoo.png)

---

### Post by El Viejo Lobo on 2007-04-25
I am new with Linux - Ubuntu (less then a year) and went through Windows before internet came to life. I remember the floppy 5.25 diskettes moving virus on DOS and Windows 3.1. I divorced Windows XP months ago. Make it short, We arerom  traumatized and like old generals fight the last war battles in the present war.
From having 6 to 7 different protection software to none takes time to get used and build confidence. We the newbies have to hear what the old solders of Linux tell us and give them the credits for their knowledge.

---

### Post by mosaic2s on 2007-06-25
can i install a anti spyware on linux machine and clean up the non-ubuntu pc's networked with it?
is there a good anti spyware available on ubuntu?

sandeep

---

### Post by dannyboy79 on 2007-06-26
not sure if there is antispyware for Linux, there's a plugin for firefox which prevents javascripts from even running and installing spyware to begin with. most spyware comes from installing little apps for internet explorer and you don't even know they are being installed. most every app for linux will be spyware free as long as you use the repositories and when you don't use the repo, you'll be compiling from source and I am sure the code would have been scrubed by other coders so that the source code won't have any spyware either. So needless to say, I am not sure about spyware program for linux per say, I guess what you want it a spyware server that would check NON-Ubuntu machines and I don't know of any. Good luck. Did you Google?

---

### Post by mosaic2s on 2007-06-27
thanks for more info.

I agree that linux will have no spyware for now. but spyware in non-linux os is real threat - my networking slowed down enough for the dhcp router to be suspected. have disabled screen savers in non-linux os and have cleaned them up using free for some time anti -spywares like avg, counter spy with non-linux os.

network is stable and fast now. but this has made me think about switching to linux a lot more. am getting stuck because of printer driver and industry standard CAD prog. search is on.
also keeping linux alive on the system that i use.

Sandeep

---

### Post by Mzee nyuki mpya on 2007-07-02
Hi, Sandeep, 
                    I'm no expert, but I'll give a couple of pointers.
Does your router have a built-in hardware firewall? Have you changed the original router password to something more secure?
Have you seen qcad? (Find it with synaptic, also sagcad and the more specialised electric, kicad, sailcut and varkon.)
Printer drivers shouldn't be too much of a problem. Ubuntu recognises many printers and it may well have drivers for all of yours. If you have a problem with a particular printer,search this forum; someone will have the same printer and you'll find out how they managed to find a driver. I've been there and am now using my daughter's old Epson;  she had problems with getting it to work with Wndows XP, but it now works fine with Ubuntu!

---

### Post by gregor171 on 2007-07-13
I just have to mention, that I don't like **firestarter** to much.. Nice firewall's are also:
**Ipkungfu **- has a usefull** feature block** list & **safe list**
**Ubuntu-firewall **- easy to install, works as a router as well, a good feature is also that sometimes drops but sometimes rejects bad packets, to confuse attacker. se this page [http://rob.pectol.com/]("http://rob.pectol.com/")
Please comment on that
Greg

---

### Post by LKRaider on 2007-07-15
The Ubuntu-firewall seems really nice, specially the NAT internet sharing and the "set-it-and-forget-it " simple configuration!

Thanks for posting the link :)

---

### Post by misfitpierce on 2007-07-15
Honestly clamAV isnt really necessary but I would run a firewall regardless of router or not.

---

### Post by eentonig on 2007-07-15
I would say, being up to date with your soft will be more beneficial.

Virus and Firewall soft does use some ressources on your system. Not much, I agree, but I can't justify the expense for something I actually don't need. Especially since random attacks are blocked by your routers NAT.

Even when running a ssh server on your home system, I see no use in running a firewall. How are you going to configure it? Block all inbound that's not SSH? There's nothing listening anyway. so they can't connect to it. And ssh needs to be reachable, or you might as well uninstall it.

Small correction. A firewall can be justified for home use, if you have some services running AND you use some IDS software like snort. Becasue then, those can manage you firewall to block hacking attempts.

---

### Post by gregor171 on 2007-07-18
I'm not quite sure, that this is for this post, but as I recently found out it is good to have a list of bad ip-s blocked, or better, to limit access to ssh to only few ip-s. SSH  MUST be secured as much as possible!!! 

I set up a test server and I wasn't to cautious, after setting up some files up and down to server, rights to some files have changed, but also useraccount Nobody was not locked. Somebody has then deleted webadmin account from ftp users. Funny.

After securing it, everything seems fine.

A good, configurable Firewall is definitely necessary!!!!

---

### Post by symvolker on 2007-07-24
Gentleman - viruses, worms, trojan's, backdoors and downloader are existing for linux! Even if the number is much smaller than M$ viruses. AV is free so use it, especially if the computer is connected to a network.

---

### Post by aztec13 on 2007-07-25
With my system specs I can barely scrape up enough space to run Gnome right. Any program I can avoid I would prefer. However I use Firefox extensions to protect myself somewhat. At least I feel less guilty running around online w/o anything. Finjan ,Ad Block, No Script and many more.If you look around on concise freeware there is something called "SandBoxie" its possible it may work under UNIX systems.  It sets aside a seperate environment for each session.  Its hard to explain something you don't understand yourself. But SandBoxie Good Ug thing bad no get past. Ug. Thats my impression of a Layman.

---

### Post by lisati on 2007-07-25
> **Almighty said:**
> I understand what you are saying. Personally I NEVER open emails with executables. I just feel as though its good general practice to have these things. 

I do agree, that I have been into the whole Micro$oft thing for too long, but its my job I kinda have to put up with its BS.

It's not just the EXE files and DOC macros - I've recently been receving suspicious emails with what, at first sight, appears to be a PDF file. And the usual caution about "security" warnings supposedly from a bank or other such organization. There is no substitute for good sense.

---

### Post by phillipchandler on 2007-08-30
Ive just installed f-prot for ubuntu using a great guide. But I was puzzled, I opened the virus list and found quite a few thousand viruses listed.
Daft question alert. If I installed the deb version for linux, and linux viruses are supposed to be about 40(ish), then why does f-prot have all these virus defs ?? The list shows a lot of w32 **** which I think is windows viruses, and Im assuming they cant cross contaminate, ie a virus written for windows, cant jump over to linux, because of programming and partition types etc. So why is f-prot for linux released with such a large def database ?

---

### Post by Perfect Storm on 2007-08-30
Normally it used to scan after win viruses so you don't pass them along to win OS, like an E-mail server.

---

### Post by tzembi on 2007-09-01
Hi there,

I stumbled upon this Thread for the search of another question. 

Currently i am using wine to run windows apps in Ubuntu.

I recognized the ability of wine to connect to the internet and searched for a possibility to switch this off (no luck until now). I just dont want it to connect because i am testing windows freewaretools which are often not trustable.

I cant use firestarter because i dont know the port the win app will use in advance so it would be good if there was any possibility to deny wine  access to the internet.

So - any Idea on this ?

EDIT: Did post my findings in another Thread, if someones interested: [http://ubuntuforums.org/showthread.php?t=543419](http://ubuntuforums.org/showthread.php?t=543419)

---

### Post by nvteighen on 2007-09-04
For desktop PCs (i.e.: that you don't run any server app), IMO both aren't necessary, but it may be helpful, specially Firestarter. Yes, Ubuntu default is no-open-ports, but with Firestarter I can see if I'm being attacked or not and from where... and also prevents me in case of accidentaly opening a port...

---

### Post by rzrgenesys187 on 2007-09-18
does clamav use resources? i thought it only ran for me when i did a clamscan in the terminal?

---

### Post by euler_fan on 2007-09-20
> **rzrgenesys187 said:**
> does clamav use resources? i thought it only ran for me when i did a clamscan in the terminal?

Depends on the configuration. It will use resources whenever it is running. For instance, while running as a cron job.

Also, there is an on-access scanning option, for instance, which I presume means it is running in the background in order to let you do the scanning.

---

### Post by stmurray on 2007-09-26
All security is a trade off.  Firewalls and AV add processing overhead and admin overhead.   if you don't worry about the availabilty or data on your workstation, there is no reason to take the time to config a firewall or AV.  If you have sensitive (like financial) data or use the machine for money making activities (meaning if you're down, you are losing money) taking the time to add the security is cheap insurance.  

I run firestarter because:
1) my home network is wireless, even though it is wpa2 encrypted  
2) I poke an ssh thourgh my hardware router from the internet to a "DMZ" sever (which I finally upgraded from a 5 year old version of Red Hat to Ubuntu).  I run snort on the machine I have open to the internet.   
3) I run programs like vnc, vmware, that open up all kinds of ports as services and who knows if they have any vulnerabilities.  

If I had a laptop, that connected to public networks (in airports cyber cafes, etc) I would most definately run a firewall. 

If you are the type you is constantly downloading and installing all kinds of packages from all kinds of places, you ought to be running an AV (that would hopefully find known trojan horses, backdoors and other unwanted malware as well as viruses).  

All OSes (all software for that matter) will have bugs which means they will have security vulnerabilities.  If over 90% of the desktops around the world were to run linux,you can bet there would be a lot more linux malware.....

Sean T Murray

---

### Post by Travisher on 2007-09-27
To prevent a real biological virus from spreading you must deal with potential carriers as well as those who may become afflicted. While there is a time lag between an out break and a 'cure', this does not warrant an attitude of "what's the point in joining in with prevention measures". 

Whales have apparently evolved to cope with HIV over 100,000 years ago. Mankind, suddenly exposed to HIV, has not evolved to cope yet. The logical conclusion is that without a manufactured cure, the offspring of those infected who do evolve, will inherit the earth.

OS writers have an advantage over evolution, they can see how other OS software is evolving and emulate without the process of extinction. 
Just because infections haven't jumped species from Windows to Linux this does not mean you should be complacent. You wash your hands every time you go to the toilet, you don't not bother because you haven't got ill yet.

On the point of firewalls, if you don't run a firewall how do you know that last download of a cool ringtone or whatever didn't contain a trojan that is even now forwarding your online banking details to gangsters. Things like Java are cross platform after all!

It isn't about linux vs. Windows, its about basic hygiene, use a firewall, use a virus checker and keep it clean.

---

### Post by Perfect Storm on 2007-09-28
> It isn't about linux vs. Windows, its about basic hygiene, use a firewall, use a virus checker and keep it clean.

Funny, now I'd ran two diffrent anti-virus applications on my computer in 4 years just to counter-predict "the-sky-is-falling" crew. Guess what I have found;

Nada, zip, zero...

---

### Post by nooby on 2007-09-28
I'm totally new to linux and ubuntu. I downloaded the WUBI installer and am curious on if that change anything about ports being shut by default. 

How does one know if a poort is open? Maybe I should start Firestarter cause taht one maybe do show if tehre are traffic I would not know of without it? 

I also wonder if my linux will know when it could update to Gutsy? Do I have to undelete this wubi and then download a new wubi or is it possible to upgrade to Gutsy when it comes. 

I like the safety of not doing partition and changing windows. I write in win now cause I need to chack if it still works. :) 

I ahve firefox on windows. How do I migrate my bookmarks?

---

### Post by g2g591 on 2007-09-28
just figured i should mention that most of those firewalls are just front ends to iptables, the real firewall that is enabled by default (try portscanning a default install) the default configuration is having all (or at least most) of the ports stealthed by default

---

### Post by Adam590 on 2007-09-30
> **g2g591 said:**
> ...the default configuration is having all (or at least most) of the ports stealthed by default

Did you mean closed? 

I checked mine with the default config, and they seemed to be closed, but not stealthed. Is there a significant difference if nothing is listening on those ports? If so, is there a way to turn off stuff like ping response without using an iptables front end?

---

### Post by trak87 on 2007-10-05
> **g2g591 said:**
> just figured i should mention that most of those firewalls are just front ends to iptables, the real firewall that is enabled by default (try portscanning a default install) the default configuration is having all (or at least most) of the ports stealthed by default

Ubuntu's firewall is not enabled by default. This may not be the case with the server version. Would somebody please clarify this?

Found this article today on hacked Linux boxes:

[http://it.slashdot.org/it/07/10/05/1234217.shtml](http://it.slashdot.org/it/07/10/05/1234217.shtml)

---

### Post by nooby on 2007-10-05
Didn't someone give us a link to a site that could test if one are vulnerable or not? 

My HDD act as if it gets very buizzy when I am on Linux but less so when on windows. Does Linux do a lot of IO? I am new to Linux so don't know what to expect in behavior?

---

### Post by julian67 on 2007-10-13
> **nooby said:**
> Didn't someone give us a link to a site that could test if one are vulnerable or not? 

My HDD act as if it gets very buizzy when I am on Linux but less so when on windows. Does Linux do a lot of IO? I am new to Linux so don't know what to expect in behavior?

Maybe you have a desktop search tool installed that indexes your data. This would make extra activity on the hard disk sometimes.  Beagle and Tracker are maybe the best known.

---

### Post by Electric_Cowboy on 2007-10-15
After Installing Firefox, Thunderbird, Sun Java, and Azureus, I proceeded
to download my emails, Big Mistake!!!

Good thing I also installed Aegis virus scanner, which found
but did not remove Magister@aa and Netsky viruses.

Lesson learned: don't install the evil Java, it will make your 
Linux installation just as vulnerable as Micro$oft Windows. :(

Far better to use Ktorrent instead which does not use Java
and doesn't have all the security holes of Azureus.

So, yes I think antivirus software is absolutely necessary
even on a server, if nothing else but to let you know when
it's time to reinstall everything from scratch.

---

### Post by julian67 on 2007-10-15
But these are Windows viruses/worms. They can't harm your Ubuntu system. Netsky is 3 years old. If your email provider doesn't manage to deal with old and well known malware you should change your email provider. If they arrived on your system via bittorrent then that is more to do with your behaviour than with choice of client. If you installed Firefox, Thunderbird, Java and Azureus from Ubuntu repositories there is almost zero chance you acquired the files that way. There is certainly no need to re-install your system unless it's a Windows server. Think what would happen if you had not used AV and had left these malware undetected on your Ubuntu server......nothing.

---

### Post by switchover on 2007-10-22
it says i do not have permission to update avg. I only have one user account on ubuntu and i am using that obviously. How can i change this?

---

### Post by Perfect Storm on 2007-10-22
> **switchover said:**
> it says i do not have permission to update avg. I only have one user account on ubuntu and i am using that obviously. How can i change this?

Guide: [http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

It will make a launcher with right permission in System Tools.

---

### Post by justin whitaker on 2007-10-22
It seems to me, policy wise, that letting the "ubuntu is safe by default' message propagate is a bad thing. 

Yes, unless you are using WINE at the time of infection, there is no way a windows virus can harm your system.  

That's not the point. The point is is that Linux will get to a point where putting a virus out there to snag unwary Ubuntu users will be appealing to hackers...and do you really think proprietary vendors are above stooping that low to discredit their competition? 

It costs a few cpu cycles, and some ram to run ClamAV. I think most of us can afford that. Use them, submit bugs, keep the projects going. We are going to need them.

---

### Post by julian67 on 2007-10-22
> **justin whitaker said:**
> It seems to me, policy wise, that letting the "ubuntu is safe by default' message propagate is a bad thing. 

................................

That's not the point. The point is is that Linux will get to a point where putting a virus out there to snag unwary Ubuntu users will be appealing to hackers..................

A virus isn't going to work. I'm not sure how many times this has been explained on this forum, probably many hundreds. For a virus to have an effect it has to be executable and to be run as root. In Windows this is default for 98 through to XP SP2 and is probably how many people will run Vista. Basically a virus in Linux is never going to affect anyone but the user who is very foolish yet also decided to choose to run as root and is happy to make executable and run an unknown script. So you can see the only likely victims would be the forum mods and admins over at freespire/linspire. <--joke (kind of).

There are plenty of other ways to compromise a system but really viruses are not something any Linux desktop user needs to worry about. Unless you run a mailserver it is a complete waste of time to run AV on Linux, the only result is a waste of your time and resources.

---

### Post by mjwood0 on 2007-10-23
> **julian67 said:**
> A virus isn't going to work. I'm not sure how many times this has been explained on this forum, probably many hundreds. For a virus to have an effect it has to be executable and to be run as root. In Windows this is default for 98 through to XP SP2 and is probably how many people will run Vista. Basically a virus in Linux is never going to affect anyone but the user who is very foolish yet also decided to choose to run as root and is happy to make executable and run an unknown script. So you can see the only likely victims would be the forum mods and admins over at freespire/linspire. <--joke (kind of).

There are plenty of other ways to compromise a system but really viruses are not something any Linux desktop user needs to worry about. Unless you run a mailserver it is a complete waste of time to run AV on Linux, the only result is a waste of your time and resources.

The real problem here is wrapping one's head around the type of viruses that can be spread and the type that a virus scanner will protect a user from.

It is entirely correct that unless a user is running as root, or consciously runs a program that is infected the user cannot pick up a virus.  The worry is that for this to be practical, no one would ever run any programs as root.  

There comes a trust issue here.  If an infected program were to find its way into the repositories or the user installed something without first verifying the file contents somehow, that the user could actually install the virus themselves.  

Obviously, the repositories are going to be as safe as possible.  However, using third-party repos increases the chances of infection.  

On the flip side of this, security holes in the linux distribution can be exploited but a virus scanner isn't going to do any good in this case.  And in the case where the user downloads an infected file and runs it, will the virus definitions be up to date enough that running a scanner will do any good?  I'm guessing that the community would get the word out as fast, or not faster with regards to infected repos. 

Really, at this point in time, there is little merit to running a virus scanner.  

I do think that setting up a good firewall though is a smart idea.

---

### Post by julian67 on 2007-10-23
People coming from Windows are often very aware of viruses but  most have been happy to install warez/cracks and freeware/shareware from untrustable sources. This was my mindset for quite a long time when I used Windows and I know it was essentially the norm for many home users. Many don't know not to run as admin, or disbelieve the importance this because they have been relentlessly marketed to by the AV/Win security vendors who have convinced them that if they run the right AV and (software) firewall that they are secure. MS spent too many years being silent on this.  A lot of experienced users who consider themselves to be knowledgeable are actually sceptical when told that running an OS installed from a CD found on a ed2k or torrent indexing site is a bad idea. Why? Because they are going to run a set of cracked "security" products on it so it will be safe! It takes a while using Linux to really break away from this kind of thinking and see things rationally. I ran AV checks for the first couple of months of using Linux and *then* I actually believed what I already knew.

---

### Post by Daveski on 2007-11-10
> **julian67 said:**
> For a virus to have an effect it has to be executable and to be run as root. In Windows this is default for 98 through to XP SP2 and is probably how many people will run Vista. Basically a virus in Linux is never going to affect anyone but the user who is very foolish yet also decided to choose to run as root and is happy to make executable and run an unknown script.

It is worth noting that as Linux grows there are more and more users who do not have the basic knowledge to recognise something like a pop-up which dupes them into agreeing to allowing malicious code to run. The classic Windows scam at the moment is to pop up a window that warns of a virus detected, and asking the user if they would like to fix the problem. If the OS says ' Do you want to run this program?' the user will Click the YES button without thinking twice. Even if the code attempts to run as Admin / Root and then when the user is asked for confirmation or to type their password they will happily do so.

---

### Post by julian67 on 2007-11-10
I don't see why a virus/trojan writer would bother to advertise their product in this way, as in Windows these things don't need to ask anything, the users are already running as root and the malware installs silently and will probably never be detected. 

This kind of pop up seems more relevant to phishing/social engineering and inducing users to give away user/password combos for web based accounts as opposed to PC accounts. It's the kind of thing that gets offered if the user is tricked into visiting a malicious site, perhaps by following a link from another web page or from an email. 

It's also common for shareware to contain adware/spyware (and worse) and the shareware's installer might request permission to install.

But the general point is true that users are vulnerable due to their own behaviour whatever their OS.

---

### Post by Daveski on 2007-11-10
> **julian67 said:**
> But the general point is true that users are vulnerable due to their own behaviour whatever their OS.

Indeed. But right now the risk is low enough for Linux users to save the overhead of virus scanning by simply not bothering - however if you share files with other users (especially Windows users) then I think it is your responsibilty to have at least checked that file for viruses before willingly passing it on to someone else.

---

### Post by julian67 on 2007-11-10
> **Daveski said:**
> I think it is your responsibilty to have at least checked that file for viruses before willingly passing it on to someone else.

No it isn't and logically it doesn't make any sense.

You aren't vulnerable to virus so no AV used on Linux.

Windows users *are* vulnerable to viruses so* do* use AV and,  *because they do,*  there is no need for Linux users to do so. 

If there are Windows users who don't protect themselves somehow that is frankly nobody's problem but their own and they are going to suffer problems *caused by compromised Windows PCs*.

Using AV on Linux desktop offers no benefit (unless placebo effect on your mind is considered a benefit) but does negatively impact your system's performance.

---

### Post by Daveski on 2007-11-10
> **julian67 said:**
> If there are Windows users who don't protect themselves somehow that is frankly nobody's problem but their own and they are going to suffer problems *caused by compromised Windows PCs*.

Everyone who uses the Internet suffers - the armys of zombie PCs which can be used to spread spam and DoS attacks slows the effective speed of communication for all users, and may compromise services.

> **julian67 said:**
> Using AV on Linux desktop offers no benefit (unless placebo effect on your mind is considered a benefit) but does negatively impact your system's performance.

I was thinking not of running resource hogging real-time scans, simply that responsible users should scan files that they intend to make available to others. Yes, you might say that Linux users are unlikely to experience local problems from virus infections, but they can spread viruses just as much as the next man.

---

### Post by julian67 on 2007-11-10
> **Daveski said:**
> Everyone who uses the Internet suffers - the armys of zombie PC's which can be used to spread spam and DoS attacks slows the effective speed of communication for all users, and may compromise services.

Yes everybody suffers, and the impact on this situation of running AV on Linux desktop is exactly zero.  It doesn't help anybody. Think about it again:  if someone uses Windows and AV then you're not offering them any extra protection....zero impact. If someone uses Windows and no AV they are already part of the problem....the impact of running AV on your PC is again precisely zero.

---

### Post by Daveski on 2007-11-11
I am sorry you think that way - we'll just have to disagree on this point. Perhaps it is a placebo as you suggest, but I feel much happier knowing that I have used the tools available to me to reduce the spread of viruses.

If someone uses Windows and no AV, but is infected directly by a file that I made available to them, then I consider myself part of the problem. Sure the Windows user has a responsibility to protect their system and that of others by running security software, but if they now have a virus that I could have prevented, then we are both to blame.

> One of the great things about being a desktop Linux user is that you&#8217;re immune to Windows&#8211; based viruses and spyware. However, if you&#8217;re like me, you probably share files with people that use Windows, and just as it&#8217;s possible for you to carry a biological virus and not get sick, you can unwittingly be a carrier and transmitter of Windows&#8211;based viruses, by virtue of receiving files and relaying files that are infected. Even though you don&#8217;t get sick, it&#8217;s still embarrassing when you give someone else the equivalent of the &#8220;computer clap.&#8221;  - Jason Perlow (Linux Magazine)

---

### Post by julian67 on 2007-11-11
> **Daveski said:**
> 
If someone uses Windows and no AV, but is infected directly by a file that I made available to them....

OK so what is actually the threat to the Win user with no AV? Is it the 10% of users out there with Linux or BSD or Mac? Or is it the *tens of millions* of infected Windows machines? Please remember that on the infected Win PCs the malware is *active*, it's *using* the hosts system to attack other Win PCs. And on a unix like system what is being done by that same malicious win32 code? 
Nothing!  It's not stealing your passwords or connecting home via IRC or executing any payload. It's entirely useless. 

Windows botnets are like a parallel universe, we are not really relevant to them. 

> **Daveski said:**
> I am sorry you think that way - we'll just have to disagree on this point. Perhaps it is a placebo as you suggest, but I feel much happier knowing that I have used the tools available to me to reduce the spread of viruses.


If it makes you feel happier and that is enough reason then run AV but your actions will have no benefit for anyone else.

---

### Post by davidU on 2007-11-19
From a current Windows network users point of view.
I have been moving over to Ubuntu for a while now, a few years in fact. I run it on my laptop and a desktop machine as dual boots.
It takes a while to move over when you have three kids, and a network of windows boxes to look after - in your spare time.
Professionally trained on Windows boxes, I am well aware of the miriad ways that one of these can be exploited and the requirement to constantly chaperon them, especially when they are driven by teenagers who love file sharing but don't want to know about anything technical, like safe browsing habits.
So, I want to run Apache server on Ubuntu to host my own multimedia stuff on a web site, along with other aspiring artists. Some of whom use MACs incidently.
Having read the relevant documents regarding my wishes, I fear that running an Ubuntu server (LAMP) will inevitabley expose the Windows nodes on my network to a greater number of potential exploits, than when running Apache as a restricted user mode on a Windows 2000 Pro setup.
So if I want to ensure less work on the Windows nodes, I either run the firewall and AV on Ubuntu or don't even bother using Ubuntu for the web server.  
This feeling arises mainly 'cos I still don't have the requisite knowledge and skill to lock the Ubuntu thing down, or feel confident that it is locked down, then there's the time required to monitor the traffic passing through the Ubuntu node.
It would be nice if everything were simple.
However, folks run Internet Explorer on MACs, I don't know why, but they do.  They aren't IT techies, they are artists and just as likely to click OK, when they shouldn't, as any Windows user.
Firefox and Mozilla have revealed exploits in the way they fail to validate certain bits of code, (.jar) a java archive exploit being the latest.  
Someone please tell me that these potential data stealing vulnerabilities won't affect me if I am running Ubuntu OS.

Wasn't BIND in need of a security fix recently, and doesn't BIND run on UNIX boxes as well as Linux and Windows. 
Doesn't this pose any malicious capability scenario for the Ubuntu user ?
And when the banks gave up user accounts to curious passers by, they weren't all running Windows OSes, surely.  No, these were sometimes DNS or DHCP exploits, and Ubuntu won't be in the clear, I fear from poisoned IP Tables.
I would really love to believe that these security vulnerabilities have no implications for Ubuntu users, but I'm afraid, at this pint in time, I can't.

I value my security far too much, even though I have noting to hide, recovering from an infection isn't fun, it is time consuming for a start.

I fix folks Windows PCs all the time after malicious software has it's wicked way, though to date, I'm happy to say, my own PCs have never succumbed to anything serious.

I'm looking forward to the day when I can feel as confident about my Ubuntu machines.  

Perhaps someone here can put me straight and allay my fears, then I can get on with the job of hosting those music tracks, safely.

---

### Post by julian67 on 2007-11-19
Vulnerabilities in applications don't really have much relevance to firewalls or viruses/AV but they of course are often cross platform so users of any system are vulnerable. Applications can be locked down using AppArmor which is now shipped with Ubuntu 7.10. It's been part of Suse and openSuse for a long time. If you want a friendlier gui admin environment for administering a server perhaps you should investigate openSuse 10.3 or SLES. I don't use openSuse btw but I used to and its gui config tools (mostly accessed via Yast) are very slick, much more advanced than those in Ubuntu. You can do everything down to the finest detail in gui.

---

### Post by davidU on 2007-11-20
Hi julian67, 

Thanks, that's really good info.  Stuff I never knew about 'till now.

So I'll investigate OpenSuse as you suggest. 

Regards

David

---

### Post by zman58 on 2007-12-08
The firewall in the WAN router may be enough for your particular application. A firewall can prevent an improperly configured service from broadcasting on the Internet. For example, suppose you have a CUPS printer installed and the CUPS system is broadcasting availability of the printer to the internet (a common default). A firewall can be setup to prevent this. Ideally, of course, it is best to make sure that CUPS is setup to not broadcast.

Another good reason to use a firewall is so that outside port scanners can not easily "find" your system. If your firewall presents a stealthy interface to the outside world, then outside systems that attempt to access your host IP address won't see anything. The firewall would drop the incoming message because it was initiated from outside. This is a good thing because you do not want other undesired hosts to be able to easily find your system.

---

### Post by vmikalinis on 2008-01-25
I would say if you have the router/firewall, then you don't need another one on the local machine....but as a responsible computer user I would also say to run clamav because if you relay that virus even one time, even if it is not run or does any damage to your machine, it has that much more of a chance in making a step to another machine.  You can help cleanup in other words even if your machine is safe.

---

### Post by julian67 on 2008-01-25
> **vmikalinis said:**
> if you relay that virus even one time................

ok, putting logical thinking hat on again:

relay it to where?

A Windows PC with up to date AV? OK no harm done.

A Windows PC without up to date AV? It's already infected.  No further harm done.

A Mac or Linux computer? No harm done.

Conclusion: total waste of time and resources, only effect is placebo. 

There are botnets with hundreds of thousands of trojaned Win PCs spewing their  malware and it's actually ridiculous to think that there is any chance of your single Linux box actually being a threat to anyone at all in this way.  Any Win boxes out there with vulnerabilites are already infected by their Windows peers.  Your Linux box is not even *accumulating* malware let alone executing it.

---

### Post by CarrotRevelation on 2008-01-26
This is an opportunity to kick a horse while its down that I cant pass up. :razz: Firestarter is not a firewall and AV software is an afterthought.



Why did I switch to Linux? I wanted more control over my system in the long run and after the whole hardware hashing and WGA Windows is not an acceptable long-term option regardless of the availability of applications in Linux. Relying on Windows for HDCP and DRM playback and DX10 video gaming is unacceptable and I don't like being pigeon-holed. I need to be free man! :guitar:



I have amassed quite a large library of security tidbits (not OS specific) if you would like here's one. If you haven't read it yet find the pdf and related material by Googling: "The Death of Defense in Depth" and Nruns.com. If you don't understand the pdf presentation Google is your friend...I think. BTW, I don't like Steve Gibson, GRC, or Shields UP! I don't believe spoonfeeding people or inventing new terms like Microsoft does with protocols helps anybody understand what a machine does while you sleep. :twisted:



If you really want to know about your computer wade neck deep!

---

### Post by Chappy7777 on 2008-02-04
I was curious about this since I just got hispeed installed w/in the last couple months. My thought and what I read on here back when I 1st got into Ubuntu (and Xandros for awhile) was that AVs and Firewalls are not needed on Ubuntu. Partly/mostly because nothing can be done to the system w/o a password. Also, MS programs, good and evil, don't run on Ubuntu (out of the box). So how is an MS spyware program going to run on here (Feisty)? I figure it can't.

Today I came onto this thread and started reading it because it's a Sticky. I started on page 1, read 2 as well, then hopped to this page.
It seems, comparing the 2, that more folks are installing AVs and Firewalls. Tho there are still those saying these are a waste of CPU and of time.

I wonder if the difference is just due to another year of highly increased spread of malware in the MS world has made some Linux users nervous. 

Is "better safe than sorry" applicable here? 

I's be just asking, but would like an answer, some thoughts. 

Thnx!

---

### Post by julian67 on 2008-02-04
A firewall is essential in many circumstances, on any desktop/server OS. Anti virus generally has no use outside of Windows or computers that principally exist to serve Windows clients.  The post that I'd be interested to see is the one from someone running an up to date Linux or BSD kernel based OS that has suffered a virus infection that actually did something. I'm not sure there has ever been such a post anywhere, ever.  Can anyone point me to one?

---

### Post by p_quarles on 2008-02-05
> **julian67 said:**
> A firewall is essential in many circumstances, on any desktop/server OS. Anti virus generally has no use outside of Windows or computers that principally exist to serve Windows clients.  The post that I'd be interested to see is the one from someone running an up to date Linux or BSD kernel based OS that has suffered a virus infection that actually did something. I'm not sure there has ever been such a post anywhere, ever.  Can anyone point me to one?
No, there are no known *nix viruses in the wild, and if something like that were to happen we can be assured that it would be huge news here, not something buried in an old, unread post.

That said, you will find several posts from people who twiddled with settings, found their computer beginning to behave strangely, and then leaping to the conclusion that they got a virus. Those are false alarms. 

@Chappy: You don't really "install" a firewall with Linux, since the iptables packet filtering module is built-in to the kernel. Different distros use different default configurations, depending on their purpose. In Ubuntu, the default is that no daemons (server applications) are enabled, and therefore there is no need for any iptables rules. The premise here (which is sound) is that you can't attack something that doesn't exist. 

Once you begin to run a server -- any kind of software that listens for incoming connections -- you need to think about packet filtering. This includes games and torrents, as well the things we think of as servers, such as web and mail servers. Nearly any router worth the name will have likely be adequate for ordinary home security. Running an iptables rule generator such as Firestarter isn't usually necessary, but it's certainly a good idea if you have any doubts about your setup.

---

### Post by julian67 on 2008-02-05
> **p_quarles said:**
> No, there are no known *nix viruses in the wild, and if something like that were to happen we can be assured that it would be huge news here, not something buried in an old, unread post.


That's what I thought. I did some searching and there hasn't been an effective virus for *nix for several years and even those that were capable of doing something were basically not so effective and rapidly rendered useless by the speedy issue of patches.  Imo people (like me) who used Windows for years before switching to the free desktop became habituated to defragging, running AV, trying too many horrible freeware "optimizers", junk cleaners, malware detectors+removers etc etc etc ad infinitum. I switched away from Windows about 2 years ago and I remember clearly feeling this *nagging itch* impelling me to worry/tinker/optimize/scan to forestall impending disaster.... It kind of worried me that none of these types of tools were even available (mostly) for my new system it took a couple of months to really understand that there wasn't any impending disaster cos I was no longer walking in the shadows. I run iptables (configured with firestarter) as it's the easiest way imo to set up NAT (internet connection sharing) and I run some p2p apps, samba and ssh server but AV on the free desktop is entirely pointless. The biggest danger these days for Win users is from subverted websites and cross site scripting, putting your browser in touch with compromised servers which scan your OS for vulnerabilities and instantly exploit any found. Almost without exception they are looking for Windows vulnerabilities though I guess if you were running an unpatched/ old & unsupported distro you might end up get rooted. My point is that you can visit these malicious sites from a patched non-Win system and they don't even waste their time trying to upload their garbage to your machine; do the same from IE on Win and you'll find a few free(beer) additions to your hard drive. GNU/Linux generally doesn't even collect and host the windows malware let alone execute it :)

I'm not complacent though. Win users often seem to believe that if they can keep the viruses out they're safe but getting rooted is a much worse proposition (can be integral to virus infection I know, but also possible by using weak passwords, running as admin/root, using apps with vulnerabilities, being victim of social engineering/phishing etc).  I think it's worth running iptables just to see the logs of who is connecting/trying to connect on which ports and which packets are being rejected. I found it educational.

---

### Post by p_quarles on 2008-02-05
> **julian67 said:**
> Imo people (like me) who used Windows for years before switching to the free desktop became habituated to defragging, running AV, trying too many horrible freeware "optimizers", junk cleaners, malware detectors+removers etc etc etc ad infinitum. I switched away from Windows about 2 years ago and I remember clearly feeling this *nagging itch* impelling me to worry/tinker/optimize/scan to forestall impending disaster.... 
Yeah, I remember that feeling as well.

If you haven't read it already, the third sticky note in this sub-forum is an excellent discussion of how security in *nix works differently from Windows.

---

### Post by hyper_ch on 2008-02-05
> **Chappy7777 said:**
> It seems, comparing the 2, that more folks are installing AVs and Firewalls. Tho there are still those saying these are a waste of CPU and of time.
I tend to think those are users with still a windows mindset. A lot of noobs come here and ask what is the best AV/FW software... and quite often they get the advice it's ClamAV or something else... so they just keep installing without further inquiring.

Of course Linux can also be a target to malware but it's just very, very unlikely and I daresay most often it's social engineering..,

---

### Post by seanc7 on 2008-02-09
The bigger security issue to me about Unix/Linux systems are rootkits. Although installing only from the official repositories would minimize that risk.

The other only worry is phishing scams. But then using good common sense eliminates that risk. Never click links in emails that ask you to enter private information. Verify the important websites (ie: banking) you use are legit by taking a quick peek at the SSL cert every so often. Even better, book mark their SSL encrypted login page instead of going to the public non encrypted site.

---

### Post by euler_fan on 2008-02-10
> **seanc7 said:**
> The bigger security issue to me about Unix/Linux systems are rootkits. Although installing only from the official repositories would minimize that risk.

The other only worry is phishing scams. But then using good common sense eliminates that risk. Never click links in emails that ask you to enter private information. Verify the important websites (ie: banking) you use are legit by taking a quick peek at the SSL cert every so often. Even better, book mark their SSL encrypted login page instead of going to the public non encrypted site.

Speaking of phishing, there are [unofficial phishing filters]("http://www.sanesecurity.co.uk/clamav/usage.htm") for use with ClamAV. Perhaps I should say third party. No idea how well they work, but it does prove the premise ClamAV can can target non-viral threats (which like phishing may be much more relevant) too.

---

### Post by bloodniece on 2008-02-11
Ok, since this is a server forum too, has anyone setup Webmin to configure iptables?  I would prefer a web-based config tool as I do not have a window manager installed on my Edgy server.  I looked at the Webmin module for iptables but it seems like you need to know more about iptables to use it over Firestarter.   The only firewall I have experience with is Juniper Netscreen.

---

### Post by p_quarles on 2008-02-11
> **bloodniece said:**
> Ok, since this is a server forum too, has anyone setup Webmin to configure iptables?  I would prefer a web-based config tool as I do not have a window manager installed on my Edgy server.  I looked at the Webmin module for iptables but it seems like you need to know more about iptables to use it over Firestarter.   The only firewall I have experience with is Juniper Netscreen.
If you want to use an easy config tool, you should. Just create the rules on another machine (one that does have a window manager) using Firestarter, FWBuilder, Guarddog, etc. Then, save the rules:
```
sudo sh -c "iptables-save > iptables.up.rules"
```Transfer that file to the /etc directory on the server, then make it run on startup by adding the following to /etc/network/interfaces:
```
 pre-up iptables-restore < /etc/iptables.up.rules
```This should go directly below the entry for the primary interface, presumably eth0.

---

### Post by sandman94 on 2008-02-14
Antivirus scanners in general are not used on workstations. The only time a virus scanner is used on a Linux/UNIX Machine, is when they act as a server for, say Windows Clients.

---

### Post by julian67 on 2008-02-15
> **bloodniece said:**
> Ok, since this is a server forum too, has anyone setup Webmin to configure iptables?  I would prefer a web-based config tool as I do not have a window manager installed on my Edgy server.  I looked at the Webmin module for iptables but it seems like you need to know more about iptables to use it over Firestarter.   The only firewall I have experience with is Juniper Netscreen.

Have a look at [http://firehol.sourceforge.net/]("http://firehol.sourceforge.net/"), it's about the easiest way to set up iptables and ideal for a server running without X. There's a good article at linux.com [Three tools to help you configure iptables](http://www.linux.com/feature/44818) 

I spent maybe half an hour reading about firehol, then looked at the support forums and was surprised to find I could easily see the solutions to some of the questions people posed. The syntax is that easy (I am good at bash scripting in the same way that Wayne Rooney is good at quantum physics). Using the firehol tutorial linked on their home page I had my gateway set up with NAT (masquerading) and ports opened for various services in just a few minutes.  It's an amazing tool.

---

### Post by postie on 2008-02-17
Hi :lolflag:
I am fairly new to Ubuntu Linux, Being a Windows user for many years I still installed Firestarter and Clamtk Virus scanner as a precaution.

However after using Ubuntu for only two weeks Clam Tk virus scanner
picked up the following:

Inbox Non-ISO Extended-As 1.15MB Email.Phishing RB-2754.

Is this a windows or Linix Virus?

Ps. I am Using Thunderbird for my E-mail

---

### Post by julian67 on 2008-02-17
> **postie said:**
> Hi :lolflag:
I am fairly new to Ubuntu Linux, Being a Windows user for many years I still installed Firestarter and Clamtk Virus scanner as a precaution.

However after using Ubuntu for only two weeks Clam Tk virus scanner
picked up the following:

Inbox Non-ISO Extended-As 1.15MB Email.Phishing RB-2754.

Is this a windows or Linix Virus?

Ps. I am Using Thunderbird for my E-mail
It doesn't look like a virus of any kind, but a phishing email i.e. an email from a scammer which looks to the unwary like a real email from their bank/ebay/paypal or similar which is used to try to obtain confidential information from you, like tricking you into revealing your password or login for something. Chances are it encourages you to follow a link and log in to a spoofed site. Probably it's been highlighted by coming from an IP address know to be a source of these kinds of things.

---

### Post by stevet73 on 2008-02-19
I think those of us migrating from the Windows environment may not understand the Linux environment. Systems Internals has a free Windows task mamager replacement program that shows all running services, processes and applications. Seeing the number of processes running in Windows is amazing. Process Explorer has an "animated" icon detailing processor usage. Is there a similar product for Linux? 
Check out "Windows Sectrts" newsletter at
[http://windowssecrets.com/2007/09/13/01-Microsoft-updates-Windows-without-users-consent](http://windowssecrets.com/2007/09/13/01-Microsoft-updates-Windows-without-users-consent)
detailing how Windows procedes to update without permission bypassing all firewall and "security" measures.

---

### Post by hyper_ch on 2008-02-20
open the terminal and typ:

```

top

```

or install htop first
```

sudo apt-get install htop

```
and run it
```

htop

```

There's also a graphical task manager (somewhere) but I never bothered with it.

---

### Post by julian67 on 2008-02-20
> **stevet73 said:**
> I think those of us migrating from the Windows environment may not understand the Linux environment. Systems Internals has a free Windows task mamager replacement program that shows all running services, processes and applications. Seeing the number of processes running in Windows is amazing. Process Explorer has an "animated" icon detailing processor usage. Is there a similar product for Linux? 
Check out "Windows Sectrts" newsletter at
[http://windowssecrets.com/2007/09/13/01-Microsoft-updates-Windows-without-users-consent](http://windowssecrets.com/2007/09/13/01-Microsoft-updates-Windows-without-users-consent)
detailing how Windows procedes to update without permission bypassing all firewall and "security" measures.

There are numerous ways to monitor all kinds of system activity in Linux. A nice easy one is to use [htop](http://htop.sourceforge.net/). There are also simple panel plug ins that show cpu,ram,swap usage. You might want to have a look at conky which you can display all kinds of info on your desktop.

---

### Post by Sit3UserX on 2008-03-08
Ok, i got it!

iptables = firewall
firestarter = frontend (or GUI?) for configurating iptables and just it!

It does not matters if firestarter runs or not as a service, in fact you don't really need it because  of the very true firewall are the iptables and it is loaded everytime you login.

Right?

---

### Post by hyper_ch on 2008-03-09
> **Sit3UserX said:**
> Ok, i got it!

iptables = firewall
firestarter = frontend (or GUI?) for configurating iptables and just it!

It does not matters if firestarter runs or not as a service, in fact you don't really need it because  of the very true firewall are the iptables and it is loaded everytime you login.

Right?

It loads every time the kernel is booted... not only after you login

---

### Post by Sit3UserX on 2008-03-10
> **hyper_ch said:**
> It loads every time the kernel is booted... not only after you login

Oh, thanks, you are right!:)

---

### Post by nativehound on 2008-03-11
Well this is what i think,  I ran my Ubuntu 7.10 i386 install threw  grc.com with Firestarter and without and as you can clearly see in  the screen shot,  you should run a firewall or a well configured iptable .  just to be safe and stealthy...  :)

---

### Post by hyper_ch on 2008-03-11
> **nativehound said:**
> you should run a firewall or a well configured iptable .  just to be safe and stealthy...  :)

If there are no services listening you don't need to close ports... it's just useless...

---

### Post by nativehound on 2008-03-11
I agree, If there are no services listening you don't need to close ports. but  we have people who cut and paste code with no idea what it means or dose.  They  might enable  an ssh or samba service.  or maybe I'm just paranoid .  :)

---

### Post by hyper_ch on 2008-03-11
if they just copy''n'paste any code then it won't matter if firewall is enforced or not because sooner or later they'll wrack their system anyway...

---

### Post by iposner on 2008-03-12
If you're running a bolted down hardware firewall, then firestarter is useless as the hardware firewall is almost certainly using the same underlying iptables service -- if you can't configure your hardware firewall properly, then you're unlikely to be able to configure your computer either.

However, it has to be said that firestarter is technically not the same as, say, ZoneAlarm, for Windows (nor does it have to be):

ZoneAlarm takes digital signatures of every process accessing the internet and compares these against the previous signatures for these same processes. In this way, if the signature changes, ZoneAlarm prompts the user that a new process/changed process is trying to access the internet. This offers some protection against trojans.

Firestarter does not offer a similar feature, but since most users are only installing software from trusted repositories, this is far less of an issue.

Because I run a hardware firewall and because firestarter does not take signatures of processes accessing network resources, I uninstall it, as I do for iptables.

---

### Post by bhavi on 2008-03-22
> **kudu said:**
> Especially since I connect through a router, do I really need firestarter and clamav ?

Viruses arent easy to program in linux because of Ubuntu/Linux has very CLEAR defenitions of groups and users, file ownerships and permissions.. So In ubuntu/linux if at all a virus is there it can affect only the user who ran the program.. And because of the file ownerships and permissions the USER will have a control over the system unlike in windows where the OS has control over the machine.. This makes Virus development in linux difficult to say the least.. 

So I dont use an antivirus because I think there is no need to from the above reasons..

On the other hand, I will go for a firewall as It allows me to configure the traffic the way I want.. :)

---

### Post by sekinto on 2008-04-02
I use Avast! Antivirus to check files for other people who run Windows. But there really is no need for an AV in Linux at this time.

Firestarter gives you information about active connections which is nice to know, but Wireshark goes much more in depth I think. Firestarter still provides a simple interface and an easy way to set rules for your firewall though.

---

### Post by misfitpierce on 2008-04-04
I find Firestarter necessary as it allows you to edit the IPTables aka Firewall built directly into Ubuntu. You dont have to have tray icon on or leave Firestarter open just simply apply the rules you want and close Firestarter and the rules stay permanent until you change them. Great and useful tool. :)

---

### Post by anantshri on 2008-04-04
I would suggest you to keep firewall ready for all unforseen circumstances,

and for clamwin,

do you connect to windows network, if no then it can be safely left behind.

---

### Post by hyper_ch on 2008-04-04
> **misfitpierce said:**
> I find Firestarter necessary as it allows you to edit the IPTables aka Firewall built directly into Ubuntu.

There is however, first a required need that demands twinkering with it... if you are behind a hardware router you have a firewall on there and you should configure that... hence leave iptables the way it was delievered...

---

### Post by Duckyspetrie on 2008-04-14
It is somewhat irresponsible, methinks, to run Linux without an antivirus. Sure (theoretically) we are immune from viruses at the moment, but anyone who shares files with Windows users is putting them at risk unnecessarily (I'd rather not send my mom a virus in an email). As for this argument about resources, running a virus scan once a week is so minute, yet can prevent so many problems, that it only makes sense, at least to me, to do so. I use Avast! for Linux and Guarddog for a firewall. Ultimately, security relies mostly on the user.

---

### Post by hyper_ch on 2008-04-14
> **Duckyspetrie said:**
> It is somewhat irresponsible, methinks, to run Linux without an antivirus.
I think it unnecessary to run antivirus on linux...

> **Duckyspetrie said:**
> but anyone who shares files with Windows users is putting them at risk unnecessarily (I'd rather not send my mom a virus in an email).
You're not putting them at risk, they do it themselves by using such an OS.


> **Duckyspetrie said:**
> As for this argument about resources, running a virus scan once a week is so minute, yet can prevent so many problems, that it only makes sense, at least to me, to do so.
Now you go wrong, if you get the latest pps through email and forward it, you'll send it to your mom before the weekly scan... hence a weekly scan is utterly useless ;)

---

### Post by p_quarles on 2008-04-14
> **Duckyspetrie said:**
> It is somewhat irresponsible, methinks, to run Linux without an antivirus. Sure (theoretically) we are immune from viruses at the moment, but anyone who shares files with Windows users is putting them at risk unnecessarily (I'd rather not send my mom a virus in an email). As for this argument about resources, running a virus scan once a week is so minute, yet can prevent so many problems, that it only makes sense, at least to me, to do so. I use Avast! for Linux and Guarddog for a firewall. Ultimately, security relies mostly on the user.
Anti-virus programs can very easily be a security vulnerability. Think about the fact that this type of software is designed to interact directly with untrusted code -- it has to in order to determine whether or not it is dangerous. The fact is that AV software is among the most targeted type of application out there. 

Aside from that, there is relatively little evidence that virus scanners are actually all that effective in preventing the spread of malware. I've repaired a few virus-infested systems, and all were running updated anti-virus software. So much for that. 

You can consider me irresponsible for not running AV software if you want. I would suggest, on the other hand, that the anti-virus software you are using has the effect of making you feel that your computer is more secure than it actually is.

---

### Post by Perfect Storm on 2008-04-14
+1 p_quarles

I like to add to what p_quarles said about Anti-virus is a vulnerability itself.

I've seen people on this forum which have deleted false positives (false detection) and hosed their own system or application(s) by trusting Anti-virus. So if you don't know a thing about virus' or at least do a search on the subject and/or file structures, an anti-virus application can be dangerous for the user(s).

---

### Post by Malikius on 2008-04-14
firewall other then Guarddog that is easier to configure? I am used to Nortons firewall or similar. I am going to dump Windows, because I am tired of the nonsence. And fully switching over to Linux. But, I want to be able to easily configure a firewall and antivirus program to keep secure. What do you folks recommend for these two options?

---

### Post by p_quarles on 2008-04-14
> **Malikius said:**
> firewall other then Guarddog that is easier to configure? I am used to Nortons firewall or similar. I am going to dump Windows, because I am tired of the nonsence. And fully switching over to Linux. But, I want to be able to easily configure a firewall and antivirus program to keep secure. What do you folks recommend for these two options?
I would recommend that you read the [sticky thread on Linux security](http://ubuntuforums.org/showthread.php?t=694198), and then (and only then) decide whether or not you actually need those tools. There is a good reason that the majority of desktop UNIX/Linux users don't bother with configuring IPtables (the "firewall" built-in to most kernels) or installing an anti-virus application.

---

### Post by Daveski on 2008-04-15
> **hyper_ch said:**
> I think it unnecessary to run antivirus on linux...
You're not putting them at risk, they do it themselves by using such an OS.

OK, how about not putting them at ADDITIONAL risk by not actually sending them a virus.

> Now you go wrong, if you get the latest pps through email and forward it, you'll send it to your mom before the weekly scan... hence a weekly scan is utterly useless ;)

Agreed, but if you are running scanning software because you feel that it is your responsibility NOT to send infected files to other users, then I would hope that you would manually scan files before you forward them to others. People should run security software but should be aware of the security risks and have an understanding of how they work and how best utilise them. The automatic real-time scanners are there to protect those who sacrifice resources so that they don't have to think, and feel they can offload the responsibility to their computer. Those Linux users who run scanners because they feel a responsibility, should (I hope) have the necessary skills to use the software effectively.

---

### Post by hyper_ch on 2008-04-16
> **Daveski said:**
> OK, how about not putting them at ADDITIONAL risk by not actually sending them a virus.

Well, I think other people can decide on their own what they want to use... it is not my job to baby-sit and spoon-feed them.

---

### Post by Th3Professor on 2008-05-10
I've come across - online, not as an attack to my own computer - these Linux-based viruses (or "virii?" lol)...

"cuckoo's egg" (I think this is from the 1980s, in the unix-only days)

"bad bunny" (forgot where I found this)

"bliss" (supposedly Linux's "first virus"... supposedly)

There's a page somewhere in the ubuntu site that lists tons of viruses, including some cross-platform viruses, which seem to be the "new scare".

The #1 problem I've seen people face with *nix-based security has nothing to do with a virus or need for an anti-virus program but, rather, has involved rootkit.

---

