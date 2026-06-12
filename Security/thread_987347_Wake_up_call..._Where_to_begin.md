---
title: "Wake up call... Where to begin?"
date: 2008-11-19
forum: Security
---

### Post by Xswitch on 2008-11-19
Ok, I've been running Ubuntu for a while now.  Everything has been cool, until a couple of nights ago... "echo you got owned"  ...  Not sure of the exact wording, but I realized that I had remote enabled...  I backed up my data and am reinstalling...  

Here's what I've done

1. I read the great threads by bodhi.zazen (Intrusion Detection and Ubuntu Security)

2. I downloaded and installed tiger and ran the scan.

Here are my ?'s...

1. tiger created a large report.  Should I start securing my system by going through this report line by line, and then plugging the holes?

2. bodhi.zazen gave an amazing tutorial on using snort and ossec.  Should I do that tutorial first?

I guess I'm looking for a what to do 1st, 2nd, 3rd, 4th, etc...

Thanks everyone...  was totally freaked out by the "echo you got owned"....  Needless to say, I felt TOTALLY VIOLATED.  I am now dedicating some serious time to reading and understanding how to secure, as best I can, my ubuntu machines.  

... Not a good feeling... :(

---

### Post by HermanAB on 2008-11-19
Problems are usually due to using bad quality passwords.  Bear in mind that by default, any user can log in via FTP or SSH if those services are enabled. Most brute force dictionaries are up to 8 characters in length.  Therefore all user passwords should be at least 9 characters in length - mine are 16 characters, semi-pronounceable.

Another common way that perps get into a server is via bad quality PHP applications running on Apache. For example a bulletin board (discussion forum).

Then of course, there are Trojan horses received via Email.  If you fall for those, then you need to surrender your Geek license.

Cheers,

Herman

---

### Post by HermanAB on 2008-11-19
BTW, if someone sends you a message that pops up on your terminal saying "You are owned", it doesn't necessarily mean that you really are.  There are various ways to pop a message onto a screen!

Check your logs.

H.

---

### Post by Xswitch on 2008-11-19
Ok... I'll check the logs and then start on bodhi.zazen's tutorial...  thanks a lot...

---

### Post by stmurray on 2008-11-19
I'm not sure what you mean by "remote enabled", but if you mean remote desktop (which is actually a version of vnc behind the scenes), then I wouldn't be doing that.  vnc was never really designed for security, although it has been beefed up a bit in recent years.  For remote access, I tunnel vnc over ssh.  Bodhi's article has a link for VNC that explains tunneling over ssh. I also run ssh on a random high port, rather than the default port of 22, to make it harder for an attacker to find it.  

(Before I get the expected replies of "that's security by obscurity and that never works", let me add that security by obscurity never works if that is your ONLY security.   My ssh server is not hidden from an attacker motivated enough to scan all 65,536 tcp ports to find it.  However, folks who are randomly finding ssh servers and trying to guess passwords generally don't do full scans, because they take too long.  My real security is that I trust ssh enough and have strong passwords.  My secondary security is the obscure port that it runs on.  I also run snort and prelude and have never seen a password guessing attack on my ssh) 

Anyway, I also run a firewall to ensure that the only internet traffic getting to my machine is ssh (over the obscure port).  That way, if I accidentally enable a service or install software that opens a port that I am not aware of, I am still protected.

---

### Post by mflint on 2008-11-19
> **Xswitch said:**
> echo you got owned
You don't explain how this message appeared, so it's hard to diagnose the level of risk...

It's quite odd to think that an attacker would announce his presence after a successful hack. If *I* were hacking someone's machine, I'd keep quiet... install a rootkit and cover my tracks. Ho hum...

Another observation: folks here are talking about strength of passwords... but I thought it was more usual for people to disable password authentication for sshd, and just use keys instead. Or maybe it's just me?

One final thought: I happily use ssh (with keys, not passwords) on port 22. I trust [DenyHosts](http://denyhosts.sourceforge.net/) to put a stop to brute-force attacks.

Matthew

---

### Post by mflint on 2008-11-19
Is your hack related to this one in this thread?

[http://ubuntuforums.org/showthread.php?t=980832](http://ubuntuforums.org/showthread.php?t=980832)

---

### Post by Xswitch on 2008-11-19
> **mflint said:**
> Is your hack related to this one in this thread?

[http://ubuntuforums.org/showthread.php?t=980832](http://ubuntuforums.org/showthread.php?t=980832)

Yes...  I saw that...  and yes to vnc as well...

---

### Post by bodhi.zazen on 2008-11-19
Thank you for your kind works and I am sorry to learn of your woes.

Starting with the security thread will go a long way.

Second step is to secure any server you install. Can you tell us if you are running VNC, ssh, etc ?

Third, do you have a router ? If not, they are not all that expensive and they offer a ton of security.

To be honest, I am quite happy with OSSEC + Snort, although they have a bit of a learning curve.

---

### Post by Xswitch on 2008-11-19
When the attack happened, I had one of my ubuntu machines connected directly to the cable modem.  I got a yellow box in the upper left corner that said "Someone is trying to control/access your desktop."  Gmail chat was open and browser was minimized.  Wasn't really doing anything.  Just had chat window open waiting for a reply from my friend.  When the yellow box appeared, I immediately tried to sign out of gmail, but could not.  I'm assuming the attacker kept scrolling the window to the bottom so that I could not click the "sign out" button.  I was eventually able to sign out.  

I do have a router, but it was not connected at the time.  It is now connected.  Do I need to configure the router in any special way?

Router is Linksys...

VNC was running at the time as well.  It was enabled via Remote Desktop.  I immediately disabled that.  Heard a lot about ssh, but my knowledge of ssh is, well, zero right now... (LOL)

Because of what happened to me, I will be spending just about all of my free time studying and reading and implementing security on my systems.  I now have absolutely no problem with the learning curve.  I will take it one step at a time.  Because I don't know just what was compromised, I'm going to reinstall.

Thanks a lot, bodhi.zazen.  I am very greatful for what you and so many others have done to help people like me.  I have an incredible amount of respect for this community.

I think I've given you all the details of this attack...

Thanks again and G-d bless...

---

### Post by bodhi.zazen on 2008-11-19
Well, this is the issue with VNC servers The only protection you have is a password, which can be cracked. You should look at VNC over ssh or FreeNX.

You should be fine once you start using your router ...

And keep reading ...

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

---

### Post by srt4play on 2008-11-19
This happened to me as well, the "echo you got owned" showed up in nautilus's quick search pop-up (when you just start typing with a nautilus window opened and in focus). I was VNC'd into the machine at the time and man it really is a feeling of total violation.

In my case the attack was due to a port forward rule for VNC that I set in my router to that machine so I could access it away from home. Stupidly I didn't put a password on VNC. The port forward was going to be a one day temporary thing but I forgot about it and it came back to bite me.

---

### Post by stmurray on 2008-11-20
It looks like this is most definitely a VNC worm, either guessing passwords or using a known VNC vulnerability to send keystrokes to the default (in focus) window.  The ones that I have seen have all been Windows, so you both may be OK (once you stop using VNC over the Internet without tunnelling over ssh).  

To verify that VNC was the culprit,  check the VNC logs (should be in .vnc directory under your home directory-- that is, ~/.vnc ) .  If the attack was done using VNC you will see entries with odd IP addresses (that is, IP addresses you never used to access the machine remotely) and they will have 0 bytes sent for copyRect, hextile, etc. 

My home firewall shows 645 different IP addresses that tried to connect to VNC (port 5900) in the last 6 months, so VNC attacks appear to be somewhat popular.

---

### Post by srt4play on 2008-11-20
> **stmurray said:**
> It looks like this is most definitely a VNC worm, either guessing passwords or using a known VNC vulnerability to send keystrokes to the default (in focus) window.  The ones that I have seen have all been Windows, so you both may be OK (once you stop using VNC over the Internet without tunnelling over ssh).  

To verify that VNC was the culprit,  check the VNC logs (should be in .vnc directory under your home directory-- that is, ~/.vnc ) .  If the attack was done using VNC you will see entries with odd IP addresses (that is, IP addresses you never used to access the machine remotely) and they will have 0 bytes sent for copyRect, hextile, etc. 

My home firewall shows 645 different IP addresses that tried to connect to VNC (port 5900) in the last 6 months, so VNC attacks appear to be somewhat popular.

Good information, thanks for sharing. I use the built-in VNC server (vino) that comes with Ubuntu and there is no vnc hidden directory. Does a log file exist for vino and if so where?

---

### Post by kevdog on 2008-11-20
Using VNC over ssh is what you want to do if you need remote access (for a quick dirty setup).  Again if you have no listening processes on your box, you will never be owned.  If you just figure out what your listening daemons were, that will tell you where you were vulnerable.

---

### Post by srt4play on 2008-11-20
> **kevdog said:**
> Using VNC over ssh is what you want to do if you need remote access (for a quick dirty setup).  Again if you have no listening processes on your box, you will never be owned.  If you just figure out what your listening daemons were, that will tell you where you were vulnerable.

Right.  Still would like to know if vino logs anywhere.

---

### Post by Xswitch on 2008-11-21
Samba was installed on my machine as well...

---

