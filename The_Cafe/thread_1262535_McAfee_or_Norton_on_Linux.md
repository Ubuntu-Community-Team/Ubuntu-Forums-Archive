---
title: "McAfee or Norton on Linux?"
date: 2009-09-10
forum: The Cafe
---

### Post by MaxIBoy on 2009-09-10
OK, I'd like to start with saying that this post is NOT what it seems. I am merely trying to fulfill a bull**** school policy. I am VERY confident in the security of my Debian laptop... (*If anyone wants to skip the backstory and get to the actual technical question, just scroll down past the line of equals signs. However, it's worth a good laugh to read it through, so as to appreciate the bitter humor of my situation.*)

...However, the county office (which oversees my school district, which oversees my school) isn't quite so sure. The school district's IT department (all one person of it) is absolutely clueless. Probably some idiot who actually needed to cheat in order to get an MSCE.

Also, last year, some equally clueless student (I can think of a few suspects) brought an unsecured Windows laptop to school, infecting the content filtering servers (which run Windows for some reason) and turning the whole LAN into an actually-pretty-hilarious-if-you-think-about-it maelstrom of worm infections, driving up the school's bandwidth usage to something like 100 times normal amounts. 

Now, an intelligent person would put FreeBSD on the servers and potentially rig it up to cut off any connected computers which broadcast huge bursts of packets. Their solution was to turn all the school WinXP machines into thin clients, take down the school WiFi networks, and issue an edict from on high against any personal laptops being connected by personal cat5 cables to the many extra sockets in the building. 

According to the school principal, there are in fact plans to allow people back onto the WiFi, but only by getting your MAC address white-listed. In my opinion that makes perfect security sense. However, they are also potentially planning to require EVERYONE to run an antivirus. I told the principal, "OK, I could put clamAV on it if it makes you feel better, but that only scans for Windows viruses." He said, "Actually we were planning on requiring either MCafee or Norton, we haven't decided which yet." 

Now, I'm pretty sure I can talk my way out of this one, as one of the student technical advisors is a very smart Macintosh user who also plays with Linux from time to time. He was the one who suggested the MAC address idea. Beats the hell out of the previous plan, which is "if one kid screws up, everyone else gets their WiFi privs taken away too." I pointed out that in freshman year I got my chair privileges taken away in Algebra, for leaning back too much (OK, so that teacher was also kind of a nut.) 

However, I might wind up being stuck running MCafee or Norton. SO:

=====================================================


Is it possible to run these under WINE? I plan on getting a copy of it, and never touching it unless I need to prove that I have it installed. Updating is not an issue. Whether it runs to a functional extent is also not an issue. 

An acceptable substitute is a dummy icon in the systray which shows a screenshot when I click on it, although it might be a bit too risky to bluff through it with only that.

Searching for Norton and Mcafee on WineHQ's appDB brings up only the original Norton Commander, plus Mcafee Visual Trace, whatever that is. I think I may be in uncharted territory.

---

### Post by lisati on 2009-09-10
To cut a possibly long and boring answer short: stand by for the people who would wonder why.

My own personal preference is, where possible, to use something that comes in a Linux-friendly version, and otherwise use Windows, complete with its own protection.

---

### Post by staf0048 on 2009-09-10
Well I'm not sure about McAfee, but I know Norton supports Linux, at least for businesses. See below.

As for pirated copies or faking it - can't help you there.

 [http://www.symantec.com/business/security_response/definitions/download/detail.jsp?gid=savce](http://www.symantec.com/business/security_response/definitions/download/detail.jsp?gid=savce)

I should note that the "Linux" section is posted under the "Unix" heading about 3/4 down the page.

---

### Post by MaxIBoy on 2009-09-10
Thanks, that's helpful!

Any other input?

(BTW I'm currently learning enough Gtk to make the systray applet, just in case I need to use that as a fallback.)

---

### Post by Chrus on 2009-09-10
Could you install windows and mcafee/norton in a virtual machine. When they want to check, open the virtual machine and run it from there.

---

### Post by Exershio on 2009-09-10
It is so ridiculously easy to spoof a MAC address that's almost worse than no security at all. What kind of IT administrator DOESN'T know that?

---

### Post by MaxIBoy on 2009-09-10
Good luck guessing a MAC address which happens to be on the whitelist. Do the math, 240 kids at the school, between 40 and 80 of them have laptops, that gives you AT BEST 80 good MAC addresses out of several trillion possibilities. And if some kid handed out his MAC address to everyone, guess what? You can remove that MAC address from the list. (In fact I might spoof that MAC address and blatantly play flash games with it, just because.)

In point of fact, the administrator DIDN'T know this until me and the Apple-using PFY I mentioned explained this to him.



The VM idea is possible, however I've never successfully gotten seamless mode to work in Vbox so that could be something of a stretch. Still, I could see a situation where I change the VM's desktop background to match mine and maybe put BBlean or something on it to make it look "non-Windows." That could fool the Principal.

More suggestions?

---

### Post by KiwiNZ on 2009-09-10
This should be discussed with those responsible for the network concerned not here

---

