---
title: "Rkhunter log"
date: 2010-03-04
forum: Security
---

### Post by Silvertones on 2010-03-04
Couls someone please give me an analysis of this log and let me know what's up? There are some warnings and don't know what they are. I googled and some appear to be normal.
Thanks!

---

### Post by doas777 on 2010-03-04
you are fine. most of the warnings are common. the only one that worried me is the message that sudo did not match it's checksum, but since they updated sudo due to a vulnerability earlier this week it makes sense that the hash does not match that of the previous scans. you may want to reenable the extra tests in rkhunter though. not sure why they aren't turned on.

---

### Post by Silvertones on 2010-03-04
Thankyou very much!

The sudo issue MAY be that at one time, and I think the previous scan was during this period, I had enabled a password for the ROOT account. I have since gone back to no password.

How do I reenable the extra testa?

---

### Post by cariboo on 2010-03-05
FYI, the last two root-kits I played with did not show up in rkhunter or chkrootkit.

---

### Post by Sir Jasper on 2010-03-05
Hi cariboo907 and all,

> **cariboo907 said:**
> FYI, the last two root-kits I played with did not show up in rkhunter or chkrootkit.

I did not entirely understand ¨played¨ [as in found by other means, or deliberately tested], but I would like some indication of how strongly the use of either or both packages is recommended?

My regards

---

### Post by Silvertones on 2010-03-05
This is the one thing that would make me go back to Windows. At least I can run all the tools I have and be assured that there are no issues & if something should get by the real time scanners I can fix them. All I have with Ubuntu is the assurance from users. I think we all have to agree that Linux is not 100% immune from attacks.  I need to at least be able to verify with certainty that I'm clean and if not I need to be able to fix things without having a degree in computer science.

---

### Post by doas777 on 2010-03-05
> **Silvertones said:**
> This is the one thing that would make me go back to Windows. At least I can run all the tools I have and be assured that there are no issues & if something should get by the real time scanners I can fix them. 

I understand your feeling, but i can't agree with your assertion. for instance, only 23% of fully patched AV systems can detect the ZeuS trojan. as of last year, close to 40% of distributed malware could not be detected via static signature scan. the only way to catch some of them is with behavioral analysis, and most AV/IS systems run in an non-interactive mode, to keep the user from being swamped with messages every time a process loads a new dll, or establishes a relationship with another process. of course malware employing a rootkit would not cause behavioral warnings, and most rootkits can't really be detected by conventional AV systems. 

with windows you can just never tell if it is clean.
[http://www.darkreading.com/security/antivirus/showArticle.jhtml?articleID=220000718](http://www.darkreading.com/security/antivirus/showArticle.jhtml?articleID=220000718)
[http://www.darkreading.com/security/antivirus/showArticle.jhtml?articleID=215600282](http://www.darkreading.com/security/antivirus/showArticle.jhtml?articleID=215600282)

---

### Post by Silvertones on 2010-03-05
I'm not sure what your conclusion is though.
On my Windows boot I run:
1. PC Tools Firewall+  because I don't have a router I'm on dialup
2. Avast v5 that is an  excellent virus tool both real time and scan with behavior guards and also detects other malware other  malware. Very light on resources.
3. PC Tools Spyware Dr. excellent  anti malware real time & scan with ThreatFire Behavior shield.
4.  Malware Bytes scan only.

All this crap does bog the computer down. That's why I came to Ubuntu but I've got to be safe.

Uncertainty is what will bring me back to Windows. I'm still playing  with Linux though. I have a friend,MIT guy, who's been the IT Director for a major University and his comments were that security for the average home user was about 50/50 between Linux and Widows. He said that the big difference is with Linux you may not know you have an issue because the majority of attacks is in the form of rootkits. Very difficult to detect and per other users the tools we have available,RKHUNTER & CHKROOTKIT, are not very good.

I want to use UBUNTU because I like the way it's setup. I'm new at this please convince me.

---

### Post by OpSecShellshock on 2010-03-05
Rootkits happen on Windows all the time, too. And for the most part they load up prior to the Windows API, which means that any diagnostic tools will start up after the rootkit itself. Rootkits work because the OS doesn't know that they're there. It's an OS agnostic thing for the most part, but the risk can be mitigated in many cases by permission restrictions and user awareness that it's a potential issue.

Consequently, tools for finding rootkits mostly compare expected states to actual states to look for discrepancies. But you have to keep updating the expectation of the tool in order for it to know what to look for. Even then, there are so many things other than rootkits that can cause the same thing to happen that the detection tools can't make a definitive conclusion one way or the other. The best they can do is point you to things that you should look into further. At that point you can monitor the outgoing connections that your computer initiates and try to see what it's doing.

The issue here (as I understand it) is not so much that Linux has too few protective applications, but more that the Windows platform has so many tools that claim to be protective, but aren't--at least not in the way that users think they are.

---

### Post by Silvertones on 2010-03-06
Please forgive me for looking like I'm pro Windows. I'm not. I'm just taking this side of the debate so that I can further educate my self.
Avast has the ability to to a boot scan which happens before the OS loads. It also has real time protection based of a definitions file and it also has real time protection based on behavior.
Spyware Dr. has these same things.
I have Wireshark configured so that it runs under a normal user. If I monitor this while my dialup connection is online with no browser loaded I should see outgoing traffic right?

With the Firewall I use on Windows It prevents outgoing traffic unless I allow it. Can the GUFW be set to prevent outgoing traffic?

---

### Post by OpSecShellshock on 2010-03-06
I think you can set outgoing traffic according to what you specifically want to allow, though I'm not sure that the gufw interface has the option to. You can configure iptables manually otherwise. But on Ubuntu it's not really worth it, because it causes usability frustrations that are out of proportion to the actual risk of allowing every connection that you initiate to go out. For example, when I first started using Ubuntu a few years back and Firestarter was the recommended front end, I set it up to deny everything except what was on a list of exceptions--but I didn't have the necessary experience to know what to make exceptions for, so my clock was constantly becoming more and more divergent from the actual time due to my not allowing ntp, and my dhcp lease renewals kept failing. It was a mess, and didn't actually provide any protection from real-world risks.

Windows (which I deal with most of the time, though I don't use it at home) is just structured differently. Lots of things run with system privileges, or with a combination of user and system privileges, or as services that don't really explain what they do. There's essentially more stuff that needs to run, but is out of the user's control. In that sense, it's worth putting more time into the configuration of the software firewall. In all fairness, a lot of things are out of the user's control precisely because it's a lot to have to know about, and sometimes you just want to get on with your work and not deal with it.

Really, the important thing with any system is to know the risks. I think that when new Linux users are told that the biggest risk comes from rootkits, they think it's a common occurrence. It's not. Nor is it some kind of automated attack you can get via drive-by download (at the moment). When there is a rootkit, it's usually "personal," by which I mean the parties responsible for installing and running it have specifically targeted the victims. A lot of times the malicious actors also have some kind of physical access. Really though, as much knowledge as it seems like a user has to have to defend against them, it takes so much more knowledge to actually pull it off that unless someone really wants something on that particular machine, they won't bother. So while it might (arguably) be that the biggest risk comes from rootkits, it's still not particularly big. It's just big by comparison to other risks. It's also not exactly true, since most folks leave social engineering out of their assessments, but there's neither software nor hardware that can protect against that.

---

### Post by Silvertones on 2010-03-06
Nice post [OpSecShellshock]("http://ubuntuforums.org/member.php?u=946893"). I've only been using Ubuntu for maybe six weeks so it's hard dropping the Windows mentality. I've made a lot of mistakes.
1. installed WUBI
2. Activated the root password
3. Logged as root and probably did things I shouldn't have
4. Broke the new update yesterday
5. Didn't do a baseline scan while the install was still virgin

I nuked the whole darn thing. I've just completed a new side by side install. Now I've got to go to the library so I can do the updates and install the rest of the necessary programs. It's iritating that wvdial is not part of the install as I need it for my dialup connection. Oh well it's quicker using the WiFi at the library.

---

### Post by doas777 on 2010-03-08
> **Silvertones said:**
> I'm not sure what your conclusion is though.
On my Windows boot I run:
1. PC Tools Firewall+  because I don't have a router I'm on dialup
2. Avast v5 that is an  excellent virus tool both real time and scan with behavior guards and also detects other malware other  malware. Very light on resources.
3. PC Tools Spyware Dr. excellent  anti malware real time & scan with ThreatFire Behavior shield.
4.  Malware Bytes scan only.

All this crap does bog the computer down. That's why I came to Ubuntu but I've got to be safe.

Uncertainty is what will bring me back to Windows. I'm still playing  with Linux though. I have a friend,MIT guy, who's been the IT Director for a major University and his comments were that security for the average home user was about 50/50 between Linux and Widows. He said that the big difference is with Linux you may not know you have an issue because the majority of attacks is in the form of rootkits. Very difficult to detect and per other users the tools we have available,RKHUNTER & CHKROOTKIT, are not very good.

I want to use UBUNTU because I like the way it's setup. I'm new at this please convince me.

I think your freind at MIT is mixing servers and desktops. linux servers are good target, so a attacker will try to break in via a PHP or other application server, and once they are in, install a rootkit, to ensure that they can maintain access. however, the attacker had to take the time to get in in the first place, manually. very few attackers would take that much time to break into some ones linux desktop, especially since the desktop shoudl never be internet facing.

with windows desktop, you still get rootkits, but they get installed automatically on thousands or millions of systems at at time, by automated trojans, worms, and viri. 

also, there are ways to tell if you are infected in linux. they are very very technical, but at least it is possible. how you would find a ring-0 rootkit on a windows system if your scanner could not point it out to you (as is the case with 77% of current ZueS infections)?

scanners make you THINK that your machine is clean, but all they are really telling you is that they couldn't find anything. a negative result can never be affirmative. thats like me asking you a yes/no question, and when you say "I don't know", I take it as "yes".

---

### Post by Silvertones on 2010-03-09
I'm done with the updates etc. Virgin install. Ran RKHUNTER to establish a base line. I have the same 2 warnings as before. At least now I can use this as a base.
I've also got a proper install.
Thanks for all the help

---

