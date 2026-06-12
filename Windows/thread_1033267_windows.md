---
title: "windows"
date: 2009-01-07
forum: Windows
---

### Post by uberdonkey5 on 2009-01-07
ok, this isn't a windows forum, but I thought you might know more about this than windows people, and I am trying to convince a friend to change to ubuntu. Put it here, cos its not something desperate that I need to know.

They have a computer and it is slowing down with windows on it. I know the file system is rubbish and thats why defrag is needed, and also that virus software slows down windows, but why, even after defrag, is it still much slower than originally (windows XP)??

Also, as the geek I am, I remember in Babylon 5 people used to say 'frag-off'. Don't know what they were really meaning ;) but I am sure there are lots of inappropriate jokes that can be made regarding fragmentation.

t'anks
ud5

---

### Post by automaton26 on 2009-01-07
A slightly inappropriate post, but I'll reply anyway :)

Try closing as many of the systray apps (bottom-right taskbar) as you can.
If they don't provide an option to disable whether they "Run at startup", then use "Start...Run..." and enter "msconfig" application. You can turn them off under the "Startup" tab.

It's all the constant maintenance (virus/defrag) and slow bloated software that finally drove me to kubuntu...

---

### Post by Joeb454 on 2009-01-07
Moved to Windows Discussions

---

### Post by Giant Speck on 2009-01-07
Wait.  Does your friend even have problems with Windows? And I mean problems that make use of Windows unbearable?  Or do you just not like the fact he or she uses it? I mean, if he or she isn't experiencing any problems with Windows, then I don't see the point in trying to convert him or her to Ubuntu.

---

### Post by jrusso2 on 2009-01-07
Never try to convince a Windows user to change unless, he expresses and interest in Linux or shows some technical aptitude.

Otherwise you risk a frustrated user who will dish Linux to everyone.  And Linux is not for everyone.

---

### Post by cardinals_fan on 2009-01-07
Don't try to sell him.  If he's interested, show him my personal Windows setup:

1. Clean install Windows.
2. Set up a limited user account.
3. Install [suRun]("http://translate.google.com/translate?hl=en&sl=de&u=http://kay-bruns.de/wp/software/surun/&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3Dsurun%26hl%3Den%26client%3Dfirefox-a%26rls%3Dslitaz:en-US:official%26hs%3DpC6")
4. Install either Firefox or Opera.
5. Add either [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722") (FF) or [BlockIt]("http://my.opera.com/community/forums/topic.dml?id=241208") (Opera)
6. Install [ThreatFire]("http://www.threatfire.com/") (if it's an old machine, this isn't required)
7. Make sure he knows not to click suspicious links or fall for obvious scams

---

### Post by cabbiinc on 2009-01-07
My wifes XP machine was slowing more every day. I had the antivirus installed, the Spybot going, the regular updates from M$, and ZoneAlarm for a firewall. I did some digging and found that one of the semi-recent updates had turned the Windows Firewall back on. Once I turned that off and rebooted life was much better.

Win Key + R, type services.msc
Look for Windows Search, turn it off. It indexes your drive while your trying to use it. A complete waste of resources.

---

