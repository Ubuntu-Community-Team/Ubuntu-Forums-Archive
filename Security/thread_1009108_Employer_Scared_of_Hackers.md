---
title: "Employer Scared of Hackers"
date: 2008-12-12
forum: Security
---

### Post by american.swan on 2008-12-12
My employer is terrified that someone will hack into my always updated Ubuntu box, leave some small changes, and proceed to attack other computers around the LAN or world from my computer.

How likely is this?  I suspect it's rather rare.  It's so bad they have ruled that file sharing must stop.  

Anyways, is there a program or way to regularly check for likely changes to various folders that would be "unusual" and result i a detection of mischief.  

My employer is rather foolish if you ask me.  They insist on using the most hacked os in history as their basis for operations costing them lots of time and energy in the virus department.

Also, are there any websites that store a mass of viruses if I wanted to screw over a computer on purpose. :) 

Is there any website full of Linux/Ubuntu hacking history?  Showing how incredibly insecure it is? Don't you love sarcasm?

---

### Post by Kinstonian on 2008-12-12
As far as security goes, I feel a lot safer using Linux than I do using Windows.  If you offer services to other computers you could be compromised by some server-side vulnerability, or you could be compromised by a client-side vulnerability such as one that exploits a hole in your web browser. It's certainly not impossible to compromise Ubuntu.  Linux is vulnerable to most of the same types of threats as Windows, just not as much.  For example you have malware for both Windows and Linux, but there is far more malware for Windows.

If it makes your boss feel better, you could install a host-based IDS like [OSSEC](http://www.ossec.net/), to help protect your Ubuntu desktop by detecting intrusions, but I think that would be a mistake.  Your employer doesn't seem to understand risk management.  An IDS is fairly cheap in deployment, what makes it expensive is the management-- investigating alerts and keeping signatures updated.  So what would your boss rather spend that time and money on, keeping your Ubuntu desktop secure, or keeping their mission critical server secure?

---

### Post by melojo on 2008-12-12
You could give your employer some facts.  Below is a link to one!!

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

---

### Post by Bucky Ball on 2008-12-12
> **american.swan said:**
> They insist on using the most hacked os in history as their basis for operations costing them lots of time and energy in the virus department.


You fogot money, which is surely a business concern? You are using the most secure operating system going, and you could tweak it to be even more so. Remember, networks are a unix specialty and any sys admin using unix will tell you the most unstable and insecure thing about their network are any windoze machines that happen to be hanging off it.

As the post above said, show him some facts and if there is a brain in there, it might see sense, agree with you and swap sides. There is one very important point that your boss doesn't make, but you should be aware of. There is absolutely no reason your machine can not get a *windoze* disease. This is not going to effect your breezy linux day to day ... but ... if you are on a network with windoze machines ... go figure. Therefore, in this situation, you would be wise to run a virus checker or firewall to prevent bringing down the network (and there are open source versions for linux/ubuntu designed for exactly this kind of scenario).

Having done that, there is no reason whatever for you not to be part of the network. The fact is, your machine is immune to what could make the rest of the network ill, so you don't want to naively pass anything on. Think of it like that. They could be firewalled against intrusion from the network but not from inside it (your computer). The fact you are running linux probably negates any windoze firewall or security they have set up for the network (it don't apply to you). Maybe not; something to look into.

It would be great to organise a meeting with him, give him the facts and show him the setup, then give him time to set some clear company policy on Office Network Security and the Use of Open Source Operating Systems! (lol). Hopefully you can all come to an arrangement.

Good luck.

[http://www.desktoplinux.com/articles/AT5785842995.html](http://www.desktoplinux.com/articles/AT5785842995.html)

---

### Post by Chayak on 2008-12-12
Well you can always point out that the Pwn 2 Own contest with a $20000 grand prize that the Mac fell first, Vista second, and the Ubuntu machine never fell.

Then there is the strange phenomenon where security researchers statistically are known to run linux on their own machines.  Security researcher researchers are still studying to find the cause of this but they suspect it's because the security researchers know something and care about security on their own machines.  An independent review (funded very generously by Microsoft) says their research shows no such thing and points out it's likely a spreadsheet error.

---

### Post by hyper_ch on 2008-12-12
Generally, every machine that is connected to the internet can be hacked. Practically linux is quite safe by default, however wrong configuration can the machine leave open.

Generally I'd also say a linux server is by default more secured than a windows one.

Just be sure you know what you're doing.

---

### Post by TreeFinger on 2008-12-12
for what your employer is scared of to happen, i believe the root password, or another account with the same privileges would need to be cracked. how many computers are there that you are monitoring and taking care of?

---

### Post by RJARRRPCGP on 2008-12-26
-Please delete, double posted, because I got a server error.-

*RJARRRPCGP: *A server on your end is unstable* ->I gotten a proxy server error.

---

### Post by RJARRRPCGP on 2008-12-26
> **american.swan said:**
> 

My employer is rather foolish if you ask me.  They insist on using the most hacked os in history as their basis for operations costing them lots of time and energy in the virus department.


LOL sounds just like in the USA, where Microsoft dominates. :rolleyes:

---

### Post by FrostDust on 2008-12-26
You should also realize, if someone's Windows machine gets compromised, it'd be assumed to be a normal occurrence, cause "Windows boxes get viruses all the time." They'd just reimage it, secure the network, and everyone would just move on. If something happened to your Ubuntu box, they'd be thinking it's your fault for trying something different, and it going wrong.

It's nice to use the OS or software you want, but unless you work in the IT department, decisions like that aren't yours to make.

---

### Post by Bucky Ball on 2008-12-27
The last post brings up a good point. Why not try getting one of the IT staff onside? You might find that most of the IT staff use linux on their boxes anyhow and can be very specific to your employer about the pros and cons of windoze and linux security issues.

---

### Post by iGama on 2008-12-27
> **Bucky Ball said:**
> The last post brings up a good point. Why not try getting one of the IT staff onside? You might find that most of the IT staff use linux on their boxes anyhow and can be very specific to your employer about the pros and cons of windoze and linux security issues.

You would be amazed of the number of IT Staff that don't use linux and say its a piece of crap... even security guys.... its a sad world out there lol

---

### Post by The Cog on 2008-12-27
I agree. For most IT staff, Linux is outside their familiar paths of thinking and is therefore an unknown to be feared and reviled. The last thing such people want is to reveal their lack of knowledge, so Linux has to be suppressed at any cost. Common sense or the good of the company don't enter into it.

---

### Post by Swerve1000 on 2008-12-27
You could always download a copy of [NESSUS]("http://www.nessus.org/nessus/") and run that against the box.

---

### Post by scorp123 on 2008-12-29
> **The Cog said:**
> I agree. For most IT staff, Linux is outside their familiar paths of thinking ... Depends on their background. What you say above is only true for people who have only had a Windows background so far. I am too "IT staff" but I flat out refuse to touch anything that has a "Microsoft" logo on it ... and that's because I have a UNIX-ish background. It really depends on the background and history that people have.

---

### Post by BatsotO on 2008-12-29
Some time IT staff will get bonus from the vendor when they make big purchase. :lolflag:
Correct me if i'm wrong but the guys where i work do file sharing with samba and gftp, that can do file transfer using ssh without problem. is there any more secure way than ssh?

---

### Post by dperfors on 2008-12-30
> **BatsotO said:**
> is there any more secure way than ssh?Tapes? or eh... flopy disks? o no, usb keys are used now a days :) They are more secure and _could_ be faster ;)

---

### Post by pdtpatrick on 2008-12-30
Dude just tripwire which will show you which files were recently changed and by who and what .. and then you can also use snort for intrusion detection. .. combine those two and if you want to be one step more secure then install nagios for system monitoring .. i think your boss will get off your back with all the hacking non sense.

---

### Post by k_aneda on 2009-01-02
> **american.swan said:**
> My employer is terrified that someone will hack into my always updated Ubuntu box, leave some small changes, and proceed to attack other computers around the LAN or world from my computer.

How likely is this?  I suspect it's rather rare.  It's so bad they have ruled that file sharing must stop.  

Anyways, is there a program or way to regularly check for likely changes to various folders that would be "unusual" and result i a detection of mischief.  

My employer is rather foolish if you ask me.  They insist on using the most hacked os in history as their basis for operations costing them lots of time and energy in the virus department.

Also, are there any websites that store a mass of viruses if I wanted to screw over a computer on purpose. :) 

Is there any website full of Linux/Ubuntu hacking history?  Showing how incredibly insecure it is? Don't you love sarcasm?


Assuming by your profile that you're in South Korea, you're in one of the *hardest* IT environments to crack.   For some reason unknown to me, probably because I don't live there and fully understand the business culture, the view of your IT Department/Managers liking Windows over Linux is pretty much standard for nearly every product conceivable in IT - for search, backup & recovery, system management, applications, *everything*.   

Once they have a product in-place, they will keep it for as long as possible, and this is one of the varied reasons Microsoft is so entrenched in South Korea.

Unless you can prove to a Manager that all is well and costs can be lowered, etc etc management speak here. - and have someone in I.T. with some degree of power to back you up, you will have to put up with whatever the SOE/standard corporate image is.   (Or you could consider changing careers and trying to invade the I.T. department :P)

[The other major caution is that by showing Linux is less susceptible to viruses (at time of writing), you could potentially make him look bad and start a game of office-politics warfare with your manager.. ;)   ]

---

### Post by Bucky Ball on 2009-01-02
Maybe just let him read through this thread! Lot of convincing points here.

---

### Post by melojo on 2009-01-02
> **Bucky Ball said:**
> The last post brings up a good point. Why not try getting one of the IT staff onside? You might find that most of the IT staff use linux on their boxes anyhow and can be very specific to your employer about the pros and cons of windoze and linux security issues.

I work at a school and some IT staff have never herd of it and others have never used it or even know what it is about.

---

