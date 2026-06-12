---
title: "Storm botnet"
date: 2008-08-22
forum: The Cafe
---

### Post by billgoldberg on 2008-08-22
I just read a comment on an article that a lot of the computers in that botnet were ubuntu boxes.

I don't believe it for a second.

Has anyone heard this before?

Just FUD?

---

### Post by Icehuck on 2008-08-22
> **billgoldberg said:**
> I just read a comment on an article that a lot of the computers in that botnet were ubuntu boxes.

I don't believe it for a second.

Has anyone heard this before?

Just FUD?

Storm worm was designed for windows only.

---

### Post by billgoldberg on 2008-08-22
> **Icehuck said:**
> Storm worm was designed for windows only.

That's what I was thinking.

I don't know why that guy said that then.

Just trying to scare new users?

It could be because the article was praising Ubuntu. Could be a gentoo user trying to scare the "noobs" or frustrated osx or windows user.

:p

---

### Post by kpatz on 2008-08-22
It's possible that those who control the botnet could be running Ubuntu, but the bots themselves are all Windows boxes.

I wonder if Storm will run in WINE? ;)

---

### Post by 159874 on 2008-08-22
Running viruses is a "windows-only-feature"

Besides, linux users dont need viruses anyway: "sudo rm -Rf /" (<-- NO, dont, dont ever do that... there is another solution! *G*)

I also dont think that Storm effects Linux machines

-----------
$Number

---

### Post by billgoldberg on 2008-08-22
> **159874 said:**
> Running viruses is a "windows-only-feature"

Besides, linux users dont need viruses anyway: "sudo rm -Rf /" (<-- NO, dont, dont ever do that... there is another solution! *G*)

I also dont think that Storm effects Linux machines

-----------
$Number

It is possible to write linux viruses.

Don't just assume you are untouchable on the web because you run Ubuntu (or another linux distro).

The same logic still applies as in windows (try avoiding dodgy pron, warez, ... sites).

---

### Post by Oldsoldier2003 on 2008-08-22
> **billgoldberg said:**
> It is possible to write linux viruses.

Don't just assume you are untouchable on the web because you run Ubuntu (or another linux distro).

The same logic still applies as in windows (try avoiding dodgy pron, warez, ... sites).

+1

Safe practicing safe computing habits regardless of platform is a good habit. I can honestly say that in all the years I have run windows as an OS at home or at work I have only had ONE incident and that was caused by not paying attention. 

Although the Linux security model is a major factor in the reason we don't have "in the wild" virii, it can be written.

---

### Post by Mr. Picklesworth on 2008-08-22
> **159874 said:**
> Running viruses is a "windows-only-feature"

Besides, linux users dont need viruses anyway: "sudo rm -Rf /" (<-- NO, dont, dont ever do that... there is another solution! *G*)

I also dont think that Storm effects Linux machines

-----------
$Number

That is a misconception. The purpose of a virus is rarely to damage your computer, more often to 'steal' it. The idea of a botnet is that your computer's power can then be utilized by the owner of the botnet. Think Folding@Home gone evil.
In fact, a virus usually aims to be unobtrusive and quiet in the background, particularly when the user is running his computer. (Although they tend to employ bizarre work-arounds to gain access, giving those funky symptoms). The trouble for them, though, is that virus writers tend to be incompetent baboons -- much like the people at Symantec who "work on" the Norton products. (Coincidence???)

While I doubt this is true, I would not be surprised if someone got a widespread virus in the Ubuntu community. There are a great deal of naïve users out there who download untrustable binaries, run strange commands involving wget from unusual sources, etc. The community here is very much about sharing scripts to achieve tasks, which involves a great deal of trust. Trust, regrettably, can be rather quickly infiltrated.
I would also not be surprised for a moment if Storm ran in Wine.


As for Windows, I recently acquired free copies of PCTools Spyware Doctor and Registry Mechanic. To my amazement, I had registry errors numbered in the hundreds and about 30 bits of spyware. The registry size was 50 MB. (GConf, by contrast, is 4.3 MB in my case and very useful). Keep in mind that I use Windows Vista very rarely, strictly for games. ClamAV has kept it virus free.
With that one, I am surprised when I *don't* find a problem.

---

### Post by Sef on 2008-08-22
> I also dont think that Storm effects Linux machines

But there are Linux botnets running.

---

### Post by gorilla on 2008-08-22
An article I read somewhere (can't find it anymore) claimed there actually are quite some Linux boxes slave-working for Storm. Those would however got infected by custom hacking, ie a human hacking into the box or using stolen passwords.
Allegedly the hacked Linux slaves are not used for the grunt work but rather at a higher level in the command hierarchy. Which makes sense; After all the controller component has to be extra stable :p

---

### Post by billgoldberg on 2008-08-22
> **gorilla said:**
> An article I read somewhere (can't find it anymore) claimed there actually are quite some Linux boxes slave-working for Storm. Those would however got infected by custom hacking, ie a human hacking into the box or using stolen passwords.
Allegedly the hacked Linux slaves are not used for the grunt work but rather at a higher level in the command hierarchy. Which makes sense; After all the controller component has to be extra stable :p

Just a quick question for some of the network guru's here.

How could you catch such unwanted traffic?

---

### Post by Dremora on 2008-08-22
Comcast blocks port 25 to prevent zombie Windows boxes from flooding the network with spam. :lolflag:

---

### Post by zmjjmz on 2008-08-22
> **billgoldberg said:**
> Just a quick question for some of the network guru's here.

How could you catch such unwanted traffic?

traceroute?

---

### Post by Ender305 on 2008-08-22
nmap and/or wireshark

---

### Post by Yuki_Nagato on 2008-08-29
> **billgoldberg said:**
> It is possible to write linux viruses.

Don't just assume you are untouchable on the web because you run Ubuntu (or another linux distro).

The same logic still applies as in windows (try avoiding dodgy pron, warez, ... sites).

I REALLY do not like unpacking compressed files that are packed in a format that is not ".zip" if I found the package on an extraneous website.  It just seems that if there was something malicious in there, it would be a tailored Linux Trojan.

@Dremora - As does every other American ISP I have tried.  So much for "sendmail."

---

### Post by zmjjmz on 2008-08-29
Viruses for Linux are far harder to make, and must take advantage of an exploit that allows it to run.
Trojans, on the other hand, can infect any operating system.

---

### Post by happysmileman on 2008-08-29
> **Yuki_Nagato said:**
> I REALLY do not like unpacking compressed files that are packed in a format that is not ".zip" if I found the package on an extraneous website.

Why does it matter if it's a ".zip" archive? It's just as easy for someone to put a virus in a ".zip" file as it is to put it in any other format, and generally they'd want it to be in ".zip" because more people know how to extract it, so more people will run it. Or course anti-virus software might know how to look in ".zip" files so I suppose that's a reason.

Also I don't know who told me this or where I read it, but apparently botnet owners target Windows users with exploits and viruses (obviously, far more targets and generally easier to infect), but will try and manually hack Linux boxes which they find to have high bandwidth and/or uptime and install rootkits, these boxes are where the bots get their orders from.

---

### Post by evymetal on 2008-09-03
Also, many botnets are designed to spend a significant amount of time automatically trying to log into easy hosts.

For example, on the servers I work on we get roughly 200 ssh attempts a day from what appear to be windows bots - all trying usernames like "guest", "test", "apache" etc - and passwords like "password". Luckly the boxes are locked fairly tight, but there are definately pleanty of people out there trying.

Besides that, think of all the possible sql injections etc possible on a developer's test box, or a badly written home server - there are pleanty of ways that you could just try and hope that 1 in a thousand unix ip addresses you try will have a root password of "password".

Especially with the sshd vulnerabilities that were found a few months ago in debian (and thus ubuntu), I wouldn't be surprised if there are quite a lot of ubuntu bots still around (it's patched now, but once they're in they're in unless you really know what you're doing).

---

