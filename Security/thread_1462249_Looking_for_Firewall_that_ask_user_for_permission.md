---
title: "Looking for: Firewall that ask user for permission"
date: 2010-04-25
forum: Security
---

### Post by ubutu on 2010-04-25
Does Linux have a firewall that ask my permission before granting access to outbound/inbound traffic?

For instance, I installed a program then it goes on the internet and does whatever it please. I know Antivirus in Linux is not needed, but anyone can write a program that collects user data and connect to whatever server.

I'm looking for something like what COMODO in Windows has. It ask the user's permission for ANYTHING to run, move or breathe and has the ability to remember/learn the user's action.

Ubuntu has iptables and Firestarter to configure it, is that all I have to work with? I just need a simply method to ensure ALL applications ask my permission before accessing the web.

Thank you

---

### Post by Kalma on 2010-04-25
Well, that is my case as well: I remember COMODO and ZoneAlarm with some nostalgy... They were so easy to use.

I'm affraid Linux doesn't work in the same way. What you need to control outbound requests is a proxy. I would recommend you use Squid + User Authentication.

You may find how I managed to get it working (it was really hard for me because I am not a Linux expert, just migrated from Windows as well). I also use Dansguardian as parental control, but you can omit this part.

[http://ubuntuforums.org/showthread.php?t=843510&highlight=parental+control&page=16]("http://ubuntuforums.org/showthread.php?t=843510&highlight=parental+control&page=16")

Good luck.

---

### Post by cariboo on 2010-04-25
If seems you didn't understand the info you were given in the other thread you posted in. Firestarter is not recommend as a firewall frontend, as it hasn't been updated since 2005.

There is no interactive firewall needed. Any knowledge you gained running Windows does not transfer to a Linux variant. I would suggest you run a portscan against your Ubuntu system from another computer, to see what ports are actually open. You can use nmap to check for open ports, if you are uncomfortable using a terminal, there is a gui for nmap called zenmap, both are available in the repositories.

If you don't understand the results you get, post them here, and you'll get an explanation of what is going on.

---

### Post by ubutu on 2010-04-25
I like how everyone knows exactly what I need and ignore what I'm asking for......I'll try and ask specific questions, either you know or you dont. Please no debates. Thank you.

Once an application is run, how to monitor and limit everything it does and make it ask my permission to go or do anything?

A member suggested AppArmor as closest, currently reviewing..............
.
.
.
.
.
.
.............................................................................................
:"No, I don't care how it work, just as long as it does"

---

### Post by cariboo on 2010-04-25
Appamour won't do what you want. Could please give us an example, what program do you want to control?

---

### Post by JayRobert on 2010-04-25
The [Security page]("https://help.ubuntu.com/community/Security") might also be a good place to start.  I'm also coming from Windows, and learning about how different the security issues in the Linux world are.

Looks like there might not be the exact thing you're accustomed to in Windows, but I think there are tools available that will help you control your ports.

---

### Post by cariboo on 2010-04-26
In Linux we don't worry about outbound connections, because the user initiates them, there is nothing in the background running that needs an outbound connection unless you start the program/service yourself. 

If you really aren't sure run wireshark, when you have nothing running to see what your network connection is doing, then start running the programs/services you are worried about one at a time, and watch the output. Wireshark is in the repositories.

---

### Post by Soul-Sing on 2010-04-26
> 
Once an application is run, how to monitor and limit everything it does and make it ask my permission to go or do anything?

For limiting out bound connections: 

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

A firewall has to be "constructed" in Linux, it is not building up itself via asking or denying permissions as in Windows.

---

### Post by iponeverything on 2010-04-26
ntop can also give you a very fine grain view of network traffic on your system. 

There is not a ZoneAlarm type of application that I know of for Linux, the simple reason for this is that it is not needed. 

Much of the software for Linux was written "to scratch an itch." Certain genres of software exist for windows and not for Linux. In the case of Ad-aware, Zone-Alarm, and host of others meant to addresses persistent and annoying abuses by windows software vendors and blackhats -- frankly just don't apply under Linux. If at some point it does start to become an issue, I am sure Linux will evolve in such a way as to make it very difficult for software like this to function.

---

### Post by ubutu on 2010-04-27
> **cariboo907 said:**
> In Linux we don't worry about outbound connections, because the user initiates them, there is nothing in the background running that needs an outbound connection unless you start the program/service yourself.   I'm not worried Ubuntu the OS, I'm concerned about anonymous malicious Linux coders.  "We"?...... as in experienced Linux user who knows what to look for and the time to comb through codes. Or TRUST the reputation of the coder  Windows users coming over to try Ubuntu don't know or have the time. Apparently, In Linux, once an app is run and password provided its free to do whatever it wants. So since I'm new to Linux, some helpful coder says I should run his script and trust him, because why? I trust Ubuntu, I just don't trust anonymous coders, and your solution is don't run certain apps or comb through codes?.....   As an individually, my needs are different from yours, one does not fit all. I'm looking for a way to know in real time what a particular app is doing, what file is it accessing and all I'm told is to block ports. Sure, I'll go ahead and block port 80 because some malicious coder wrote a script to use port 80.   Are you seriously telling me Linux doesn't have a comprehensively way to control what an app does after you give it permission?  It's either someone is saying I don't need it and trust what the app is doing to my system or answer my questions with another question.  I've always thought Ubuntu was better then Windows, cept my search told me otherwise  By default Ubuntu is more secure than Windows but like myself and other experienced Windows user, we've managed to to make our version of Windows more secure than Ubuntu. And for some reason everything always seems to be a debate with Linux. What's that all about?  Thanx for confirming Windows market share.

---

### Post by Irihapeti on 2010-04-27
If you restrict yourself to installing programs from the Canonical repositories, there should be no possibility of malicious scripts ending up on your system.

If you don't trust what's in the official repositories, then that's a much bigger problem.

FYI, it initially bothered me that there wasn't this kind of firewall available. However, after 2-1/2 years and no trace of any problems of this kind, I'm comfortable with the way things are.

---

### Post by Agent ME on 2010-04-27
> **ubutu said:**
> So since I'm new to Linux, some helpful coder says I should run his script and trust him, because why? I trust Ubuntu, I just don't trust anonymous coders, and your solution is don't run certain apps or comb through codes?.....
That is actually the standard advice, on any system. Don't run code you don't trust.

There may be firewalls available on windows that allow you to interactively control in realtime what gets through, but that's kinda of a hacky protection. The program could still do other bad things to your computer, and possibly find a way around the firewall by using an already trusted program to help.

A better solution if you want to run an untrusted program would be to run it under its own user account that doesn't have access to your personal data, or use AppArmor to lock it away from anything it doesn't need.

---

### Post by OpSecShellshock on 2010-04-27
I understand those concerns. The only way to protect yourself against code from a source you don't trust is to not run it. Not all people's needs are going to be met by software available in the repositories, of course (though most will). In those cases, it's best to only install or run applications that you've obtained from the developer's official site. If you have a question about the reputation of a specific third party project or decent sources, or even if you have doubts about something that's available, you can ask for help on these boards. If one of the members here finds something suspicious, they'll let you know. A good application's official site will tell you exactly what it does and everything that it does, and will show you what it looks like when it's working. As such, anything that accesses the web should tell you that it's accessing the web, along with what exactly it's accessing. If you run it and discover that it's doing something other than that, you can stop it and uninstall it.

---

### Post by Soul-Sing on 2010-04-28
>  ....but like myself and other experienced Windows user, we've managed to to make our version of Windows more secure than Ubuntu.....

Great keep up your good work, and spread it around to less experienced Windows users.

---

### Post by scottuss on 2010-04-28
Short(ish) Answer:

I know what you're looking for, and rather than telling you that it isn't needed,I'll just quickly say here that there isn't really a tool to do this at the moment. 

Why(ish!):

Because it isn't needed, and there are clearly no developers that *want* this feature, thus it hasn't been implemented. On Linux, there's a different way of doing things and some adjustment is required. One major thing I would say that I personally have realised is that you should not run code unless you trust it, therefore my policy is generally: if it ain't Open Source (so I, or others can check it) then I don't use it.

You should be wary of things, but in the Linux world, tools from the Windows world such as the firewalls you describe are overkill and not used.

---

### Post by ubutu on 2010-04-28
Thanx for the clarification. Ubuntu relies on community trust and user's feed-back for continuity in return the OS is open and free to use.

Maybe I was asking the wrong questions initially but it seems AppArmor is exactly what I'm looking for. 

```
http://en.wikipedia.org/wiki/AppArmor
```".......[B][I]AppArmor allows the system administrator to associate with each program a security profile that restricts the capabilities of that program.

It supplements the traditional Unix discretionary access control (DAC) model by providing mandatory access control (MAC).

In addition to manually specifying profiles, AppArmor includes a learning mode, in which violations of the profile are logged, but not prevented. This log can then be turned into a profile, based on the program's typical behavior.[/I][/B] "

Unless someone suggest I don't actually need AppArmour....\\:D/

---

### Post by cariboo on 2010-04-28
I think mostly it depends on your level of paranoia. I've been using a Linux variant for over 10 years, and I haven't felt the need to try and secure my setup the same way i would a Windows system. I'm behind a router, with no ports forwarded. I've been running this way since I got high speed access 8 years ago, and never had any problems. I don't even bother looking at the logs anymore, as there are so many blocked attempts to break into the system every day, it's just a waste of time.

---

### Post by Irihapeti on 2010-04-28
I would suggest that the OP read bodhi.zazen's stickies on security and AppArmor, and then make a decision. If you are running a server that's accessible from the internet, that will influence the decision.

---

