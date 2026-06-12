---
title: "Sort of a survey..."
date: 2005-08-21
forum: Server Platforms
---

### Post by jchristian on 2005-08-21
I've posted this on several forums, looking for a consensus.

I've been doing recreational/academic portscanning ( nmap )and pen/vuln testing (SATAN NESSUS ) for awhile now. It's instructive as hell, and mucho fun...
I keep hearing this vague 'net rumor that your ISP will drop and/or report you for this if their tech people "pick up the signs" on their logs.( whatever that means) I guess I could imagine HOW they could detect it, but I'm still skeptical given the amount of traffic on a given network.

The question is : Has anyone ever actually heard of this happening? Of an ISP ever ratting someone out based on such evidence?

Thanks for your response.

---

### Post by adwait on 2005-08-21
I haven't heeard of anyone being prosecuted, or otherwise chastised for running a port scan. I don't see, what could be illegal in portscanning.........unless you hack the computer, or do something malicious, I don't see, on what grounds your ISP could take action against you.

---

### Post by LordHunter317 on 2005-08-22
Your ISP can do whatever they want if you break their rules, pretty much.  And yes, they can detect and will detect you if you are doing agressive port scanning.

They don't have much legal recourse beyond cutting off your account, but that would still suck, so don't do it.

---

### Post by skoal on 2005-08-22
Well, sure.  In fact, I normally report port scans on my system (from remote clients) all the time to their ISP(s).  I've had several ISP admins tell me they've "fixed" the problem and instruct me to notify them again if those port scans, syn floods, etc continue.

All you have to do is read and ISPs EULA to see what you can and cannot do while using their network.  You'd be surprised how easy it is for anyone (including RIAA associates for that matter) to query an ISP admin about your activity, illegal or otherwise.  If your activity breaches their agreement with you, then they're all too happy to disconnect you or provide 3rd parties with that information to excuse themself of any related liability.

\\//_

---

### Post by cmh_ubuntu on 2005-08-25
I think most people see port scans as an attempt to get information to do some malicious activity, even if you just have an "academic" curiosity.  It's probably safest if you just set up some test machines on your own LAN (but perhaps less fun).

---

### Post by xequence on 2005-08-25
[QUOTE=skoal]Well, sure.  In fact, I normally report port scans on my system (from remote clients) all the time to their ISP(s).  I've had several ISP admins tell me they've "fixed" the problem and instruct me to notify them again if those port scans, syn floods, etc continue.

All you have to do is read and ISPs EULA to see what you can and cannot do while using their network.  You'd be surprised how easy it is for anyone (including RIAA associates for that matter) to query an ISP admin about your activity, illegal or otherwise.  If your activity breaches their agreement with you, then they're all too happy to disconnect you or provide 3rd parties with that information to excuse themself of any related liability.

\\//_[/QUOTE]


The dreaded long arm opf the ever so evil RIAA... I dont know but I always thought they got people by searching P2P networks for people uploading music and see if its real then supoenas their info from the ISP.

---

### Post by gravestone on 2005-08-29
For me, it's in the agreement I accepted when I signed up with the ISP.

If you want to do stuff like this, set up a test network with some old 486s. I did, it's great fun.

---

### Post by primeaudio on 2005-09-11
"I keep hearing this vague 'net rumor that your ISP will drop and/or report you for this if their tech people "pick up the signs" on their logs.( whatever that means) I guess I could imagine HOW they could detect it, but I'm still skeptical given the amount of traffic on a given network."


Remote scanning is considered malicious activity unless you are pointing it at yourself and ask your ISP's permission first if your just testing your firewall 
security they would wonder why aren't you using a scanner like sygates or say steve gibsons port scanner?

---

### Post by fishfork on 2005-09-12
ISPs definitely can detect this sort of this. My last one had a policy to disconnect you automatically if they noticed you portscanning, no questions asked. It might sound a bit draconian but if all ISPs did this, it would really cut down on the spread of worms and the amount of zombies spewing forth spam everywhere.

---

