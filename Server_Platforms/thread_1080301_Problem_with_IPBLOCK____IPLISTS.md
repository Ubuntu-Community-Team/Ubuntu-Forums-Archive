---
title: "Problem with IPBLOCK  /  IPLISTS"
date: 2009-02-25
forum: Server Platforms
---

### Post by mistypotato on 2009-02-25
Hi,

whenever I run IPBLOCK, it maxes out my cpu and it remains maxed out at 100% until I shut down IPBLOCK.

I completely removed IPBLOCK and reinstalled and got the same result.

any ideas on what to do?


thx

---

### Post by uljanow on 2009-02-25
How do you run IPblock ? Do you see the complete the GUI ?

Normally it takes few seconds on recent hardware to load the lists.

---

### Post by mistypotato on 2009-02-25
Hello,

Yes, the GUI loads but the cpu load shoots to 100% and I haven't seen it come down.

It was running ok on the same machine for the last few days then yesterday I tried to update the defs and that's when it started.

So I deleted the files (gz) and then completely removed iplist from my system.

Then I started over, running the entire install process from the beginning.

Ultimately, the cpu load problem returned.

Odd thing is that it ran fine on the same machine for about 3 days before this problem.

---

### Post by windependence on 2009-02-25
I'm gonna get flamed for this but IMHO you don't need this crap. I know it looks scary when all those Chinese and Russian spoofed IPs are trying to bust in your box but the fact is they have entire IP blocks and will just eat up your processing power just to drop the traffic.

Get yourself a good hardware firewall, or build yourself a gateway box using pfsense and block the traffic BEFORE it get to the server.

-Tim

---

### Post by mistypotato on 2009-02-26
Still having the same issue :confused:

No matter how many times I COMPLETELY remove IPBLOCK from my system, then start all over.... it always goes back to the same problem of totally maxing out the cpu.

It does this even WITHOUT loading the blocklists....while it's still DISABLED.

Does anyone know why this particular program would be doing this?

It's working perfectly fine on my two other ubuntu 8.10 PC's.

---

### Post by uljanow on 2009-02-26
Hm, have you tried using **sun-java6-jre** as default java vm ?

```

sudo aptitude install sun-java6-jre
sudo update-alternatives --config java
```

---

### Post by mistypotato on 2009-02-26
Hi,

I "think" I do have that installed but with all these ubuntu machines sprouting up around here I may have missed that one.  :p

I will check it and thanks  ):P




Follow-up...upon checking...I have cacao jre installed...not sun-java jre.
So Im installing Sun Java jre as I write this.
Do I need to uninstall cacao jre or can they BOTH be installed?

---

### Post by mistypotato on 2009-02-26
Well,

I installed Sun Java jre and the problem persists.

I wonder what if any files might be leftover when you UN-install ipblock that could be causing this problem.

Otherwise, I'm in a bit of a pickle here as I don't know what else to try:confused:

---

### Post by R.Bucky on 2009-02-26
I used to run iplist on my gui server as well. Now that I have the Server edition installed, I simply place the block lists that I had before in my .htaccess. If you want an entire country blocked, try [http://www.blockacountry.com/]("http://www.blockacountry.com/"). Otherwise, I would agree that you need only to have a solid hardware firewall with UFW configured only to allow the bare minimums.

---

### Post by uljanow on 2009-02-27
cacoa doesn't need to be deinstalled. But it would require to set sun's java vm as the default one:
```

sudo update-alternatives --config java
```

Alternatively you could test it directly:

```
sudo /usr/lib/jvm/java-6-sun/jre/bin/java -jar /usr/share/java/ipblockUI.jar
```

---

### Post by mistypotato on 2009-02-27
> **R.Bucky said:**
> I used to run iplist on my gui server as well. Now that I have the Server edition installed, I simply place the block lists that I had before in my .htaccess. If you want an entire country blocked, try [http://www.blockacountry.com/]("http://www.blockacountry.com/"). Otherwise, I would agree that you need only to have a solid hardware firewall with UFW configured only to allow the bare minimums.

I use a Watchguard x500 core on my server and a Watchguard x15e on my desktop.

Still, I like the fact that ipblock adds an additional "layer" of protection and often I see blocks (new ones) that would have slipped through otherwise because they were added by a third party (BISS).

This way, I can continue building my personal block list from the blocks that show up.

But I DO have a comprehensive block list set up in my hardware firewalls.:p

---

### Post by mistypotato on 2009-02-27
I am wondering if this problem could be related to iplist ?

---

### Post by mistypotato on 2009-02-27
[SIZE="4"]When I try to update a couple of odd things happen....

1). I get a warning message saying that the package cannot be authenticated.


2). It takes me to a site called [COLOR="Red"]TU-Berlin.NET[/COLOR]
IP Address 82.100.220.38...........which when I look at it, looks like a bogus website?


Maybe my system has been compromised?

I ran rkhunter and everything c[/SIZE]ame back ok?

---

### Post by mistypotato on 2009-02-27
Results of rkhunter scan...latest updates

System checks summary
=====================

File properties checks...
    Files checked: 129
    Suspect files: 0

Rootkit checks...
    Rootkits checked : 109
    Possible rootkits: 0

Applications checks...
    Applications checked: 3
    Suspect applications: 0

The system checks took: 2 minutes and 39 seconds

All results have been written to the logfile (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.

---

