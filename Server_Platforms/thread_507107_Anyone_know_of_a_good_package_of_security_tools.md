---
title: "Anyone know of a good package of security tools?"
date: 2007-07-22
forum: Server Platforms
---

### Post by sent17inel on 2007-07-22
In Backtrack and nubuntu the security tools come pre-installed... I want all of those on my ubuntu computer.. does anyone know if there is a way that i can get those all installed quickly and efficiently? I read the sticky on free security tools and someone gave a link to a collection of security tools but the link is broken... Can anyone help me? If you are uncomfortable posting here plz p.m.

---

### Post by Catsworth on 2007-07-22
Your best bet really is going to be to decide which tools you want and then install them individually.

Any package you find will contain tools that you don't want, and will invariably be missing more than a few tools that you *do* want.

You won't necessarily save any time by installing a 'package', but you will certainly learn a whole load by installing the components yourself.

On a slightly different note.....there are perils associated with what you're doing that you have probably thought about, but which are certainly worth me mentioning just in case:

The types of tools that are contained within BackTrack, and therefore almost certainly the sort of tools you're talking about installing, can very easily be used to compromise a system.  Normally that system will be a target of your choice.  If a malicious attacker happens to gain a foothold into *your* system, having those tools installed will certainly make life a lot easier for them

---

### Post by sent17inel on 2007-07-22
Alright. I'll stop my search for the lazy easy way....... :)

---

### Post by sent17inel on 2007-07-22
Umm... Just in case anyone stops by and reads this thread and umm ya iunno im just gonna say this.. ideally i would like to have all of these tools on my ubuntu system [http://backtrack.offensive-security.com/index.php?title=Tools](http://backtrack.offensive-security.com/index.php?title=Tools) there is alot there like two hunderered and i just wish i didnt have to install them all one by one... but oh well... ill go get started...

---

### Post by Catsworth on 2007-07-23
Seriously dude, you should ask yourself if:

a) you really need *all* those tools
b) you really can't work from either 1) a LiveCD, or 2) a B|T install on a seperate partition
c) you really want those tools installed on your machine at all, where they can be used against you.

---

### Post by odiseo77 on 2007-07-23
I'm not a security guru myself, but as Catsworth said, these tools can be used against you; they're like counter-attack tools; thus, they obviously mean exposure. Take for instance, you're getting continuous pings from a certain IP address and you use nmap against this address; you're basically saying to the other side "hey I'm here", and if the other side happens to be a real blackhat and not a stupid scriptkiddie, *you don't wanna mess with him* (know of a guy who tried something similar and got his system totally cracked, including his MSN account).

So, my advice is to remain as stealthed as possible (an easy way would be to install firestarter and configure it to block ping responses and other type attacks... not that they won't realize you're there, but at least it will make it harder for them). You can also install chkrootkit and rkhunter and make regular scans for rootkits on your system.

---

### Post by sent17inel on 2007-07-23
> **odiseo77 said:**
> I'm not a security guru myself, but as Catsworth said, these tools can be used against you; they're like counter-attack tools; thus, they obviously mean exposure. Take for instance, you're getting continuous pings from a certain IP address and you use nmap against this address; you're basically saying to the other side "hey I'm here", and if the other side happens to be a real blackhat and not a stupid scriptkiddie, *you don't wanna mess with him* (know of a guy who tried something similar and got his system totally cracked, including his MSN account).

So, my advice is to remain as stealthed as possible (an easy way would be to install firestarter and configure it to block ping responses and other type attacks... not that they won't realize you're there, but at least it will make it harder for them). You can also install chkrootkit and rkhunter and make regular scans for rootkits on your system.

Ya i guess your right.... Im so impulsive sometimes..... ill probably just get a few of the basic security auditing tools and read up on how they work and how to use them... can anyone list me the basics? so i will know what i should invest my time in?

---

### Post by Catsworth on 2007-07-23
I would suggest that you learn nmap back to front and inside out.  Know and understand the command line options/switches, and make sure you understand the results that you are getting.

Once you've got that the world is your oyster :)

---

### Post by astralsin on 2007-07-24
For penetration testers, these tools are essential.  You HAVE to conduct vulnerability assessments against your own networks.  In such case, the tester should acquire a cheap old laptop and install backtrack to the hard drive (just do it as a live installation, I can't get the real install to work).  this laptop is a minimal security risk if its kept in a safe place.  

as it has been said, learn the crap out of nmap.  learn how to read wireshark logs.  learn how to do some of the more devious things (dns poisoning, MITM) and try to execute them against your own network.

---

### Post by sent17inel on 2007-07-25
Okay i have begun following your advice and i read a tutorial so to speak on nmap and learned a great deal. As for backtrack.. I tried to install Backtrack 2.0 final and when ever i would click install it would never work... so i gave up on that... do u know why it would not work?

---

### Post by astralsin on 2007-07-25
make sure you install it as a livecd, NOT as a real distro, it gives you the option.  its based on Slax and is built as a livecd.  it doesn't have an installer like ubuntu and wont install as a normal OS. just choose the livecd install option

---

