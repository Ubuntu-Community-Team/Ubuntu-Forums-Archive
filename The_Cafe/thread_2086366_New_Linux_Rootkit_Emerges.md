---
title: "New Linux Rootkit Emerges"
date: 2012-11-20
forum: The Cafe
---

### Post by Linuxratty on 2012-11-20
It had to eventually happen.:( So, how do we stay safe?

> 
A new Linux rootkit has emerged and researchers who have analyzed its code and operation say that the malware appears to be a custom-written tool designed to inject iframes into Web sites and drive traffic to malicious sites for drive-by download attacks. The rootkit is designed specifically for 64-bit Linux systems, and while it has some interesting features, it does not appear to be the work of high-level programmer or be meant for use in targeted attacks. 

[http://threatpost.com/en_us/blogs/new-linux-rootkit-emerges-112012](http://threatpost.com/en_us/blogs/new-linux-rootkit-emerges-112012)

---

### Post by cwsnyder on 2012-11-20
First, don't browse using sudo or root account.

Second, edit your /etc/rc.local and add a line: **exit 0** to the end of the file if it does not already exist.

---

### Post by monkeybrain2012 on 2012-11-20
> **cwsnyder said:**
> First, don't browse using sudo or root account.

Second, edit your /etc/rc.local and add a line: **exit 0** to the end of the file if it does not already exist.

It already exists, what does it do?

---

### Post by Jakin on 2012-11-20
> **cwsnyder said:**
> 
Second, edit your /etc/rc.local and add a line: **exit 0** to the end of the file if it does not already exist.

Which should already be there in Ubuntu by default :)

---

### Post by KiwiNZ on 2012-11-20
I have made this a Sticky for a time so it does not get buried by the sands of time.

---

### Post by Paddy Landau on 2012-11-20
Fascinating. Perhaps it is time to start developing a Linux anti malware application.

> **monkeybrain2012 said:**
> It already exists, what does it do?
It tells the script to end immediately without error. The root kit adds its commands at the end of the script, *after* the [FONT="Lucida Console"]exit 0[/FONT], so it simply will not be executed.

However, it will not be long before malware becomes more intelligent than that.

---

### Post by lykwydchykyn on 2012-11-20
It should be pointed out:

 - This is targetted, as I understand it, at WEB SERVERS running 64-bit Linux.  It inserts iframes into the pages being served pointing to malicious code.
 - We do have anti-rootkit software already available.  See rkhunter and chkrootkit (though at this point they probably do not detect this rootkit since it's new).
 - AFAICT there's no new method of propegation/infection or privilege escalation here, so normal precautions apply (strong ssh security, apparmor, etc).
 - This does not really represent a new trend in "Linux Malware".  We've had rootkits around for a long time.  This one is notable because it's a new code base, rather than a variation on an old rootkit.

---

### Post by rai4shu2 on 2012-11-21
So:

1. No way to detect it.
2. No way to fix if you do detect it.

Nice. Way to not solve anything. I guess this isn't big concern, really. Except that this does poke a hole in the myth that Linux isn't a big target.

---

### Post by mamamia88 on 2012-11-21
would be nice to know what site to avoid that the outbreak started at so i could avoid it.

---

### Post by sffvba[e0rt on 2012-11-21
So someone wrote some code to compromise a computer system...


404

---

### Post by Linuxisfast on 2012-11-21
> **rai4shu2 said:**
> So:

1. No way to detect it.
2. No way to fix if you do detect it.

Nice. Way to not solve anything. I guess this isn't big concern, really. Except that this does poke a hole in the myth that Linux isn't a big target.

No myth, its the proven fact and do read up on the impact of this so called rootkit which is a work in progress and doesn't affect Ubuntu as pointed out by previous posters.

---

### Post by lykwydchykyn on 2012-11-21
> **rai4shu2 said:**
> So:

1. No way to detect it.
2. No way to fix if you do detect it.

Nice. Way to not solve anything. I guess this isn't big concern, really. Except that this does poke a hole in the myth that Linux isn't a big target.

If you've bothered to read [the actual analysis](http://blog.crowdstrike.com/2012/11/http-iframe-injecting-linux-rootkit.html) of the rootkit, you'll note:

- It's pretty simple to detect using ps, since the author botched process hiding.
- It's pretty simple to fix, since it's a discrete set of files that is started off at every boot with a line in /etc/rc.local
- It is nothing more or less than a rootkit.  It's not a virus, a trojan, or a worm.  It has no propagation method, exploits no security flaw, has no inherent means of elevating privilege.  It is software that has to be placed on a compromised system by an intruder with root.
- The execution of this rootkit is described in the analysis as amateur and mediocre.

Anyone whose ever put an SSH server on a public IP and bothered to browse their auth logs can tell you that Linux *Servers* are constantly being targetted for intrusion.  Mostly what these intruders want to do is install rootkits and use what they presume is a web server to distribute malware and spam.

So please, before everyone goes spreading FUD about how the Malware apocalpyse has finally hit your Ubuntu desktop, educate yourself and stick with the facts.

---

### Post by Hungry Man on 2012-11-21
There is no myth about Linux being too little to attack. Linux dominates the server market - this is an attack against servers (hence why it's designed to inject iframes into websites to steer traffic). Linux users, however, are rarely attacked, due to tiny market share.

---

### Post by CharlesA on 2012-11-21
> **lykwydchykyn said:**
> If you've bothered to read [the actual analysis](http://blog.crowdstrike.com/2012/11/http-iframe-injecting-linux-rootkit.html) of the rootkit, you'll note:

- It's pretty simple to detect using ps, since the author botched process hiding.
- It's pretty simple to fix, since it's a discrete set of files that is started off at every boot with a line in /etc/rc.local
- It is nothing more or less than a rootkit.  It's not a virus, a trojan, or a worm.  It has no propagation method, exploits no security flaw, has no inherent means of elevating privilege.  It is software that has to be placed on a compromised system by an intruder with root.
- The execution of this rootkit is described in the analysis as amateur and mediocre.

This x 9000. It sounds like a poor attempt to write malware for a *nix web server.

> Anyone whose ever put an SSH server on a public IP and bothered to browse their auth logs can tell you that Linux *Servers* are constantly being targetted for intrusion.  Mostly what these intruders want to do is install rootkits and use what they presume is a web server to distribute malware and spam.

So please, before everyone goes spreading FUD about how the Malware apocalpyse has finally hit your Ubuntu desktop, educate yourself and stick with the facts.

Indeed. It also looks like the machine needs to be compromised first for this thing to be installed, and if that is the case, you are already owned.

> **Hungry Man said:**
> There is no myth about Linux being too little to attack. Linux dominates the server market - this is an attack against servers (hence why it's designed to inject iframes into websites to steer traffic). Linux users, however, are rarely attacked, due to tiny market share.

Yep. Servers are a huge market for *nix, which makes them a target.

---

### Post by koenn on 2012-11-21
> **lykwydchykyn said:**
> 
- It is nothing more or less than a rootkit.  It's not a virus, a trojan, or a worm.  It has no propagation method, exploits no security flaw, has no inherent means of elevating privilege.  It is software that has to be placed on a compromised system by an intruder with root.

Well, at least the author adheres to the unix philosophy of small tools that do one thing only. Maybe he's also hoping for some bazaar style distributed development where other people write the propagation system or extensions such as a delivery system of pluggable privilege elevation mechanisms. 

If you're writing malware, might as well do it in line with the established practices of the target system.

---

### Post by rai4shu2 on 2012-11-21
> **lykwydchykyn said:**
> If you've bothered to read [the actual analysis](http://blog.crowdstrike.com/2012/11/http-iframe-injecting-linux-rootkit.html) of the rootkit, you'll note:

- It's pretty simple to detect using ps, since the author botched process hiding.
- It's pretty simple to fix, since it's a discrete set of files that is started off at every boot with a line in /etc/rc.local
- It is nothing more or less than a rootkit.  It's not a virus, a trojan, or a worm.  It has no propagation method, exploits no security flaw, has no inherent means of elevating privilege.  It is software that has to be placed on a compromised system by an intruder with root.
- The execution of this rootkit is described in the analysis as amateur and mediocre.

Anyone whose ever put an SSH server on a public IP and bothered to browse their auth logs can tell you that Linux *Servers* are constantly being targetted for intrusion.  Mostly what these intruders want to do is install rootkits and use what they presume is a web server to distribute malware and spam.

So please, before everyone goes spreading FUD about how the Malware apocalpyse has finally hit your Ubuntu desktop, educate yourself and stick with the facts.

Thanks for the information.

Okay, what we need is better communication from these hacker guys. Sheesh. Those of us who aren't security pros don't know how to read between the lines and really need things like the above spelled out to us more plainly (preferably within the first three paragraphs of the article pointing out the threat).

---

### Post by lykwydchykyn on 2012-11-21
> **rai4shu2 said:**
> Thanks for the information.

Okay, what we need is better communication from these hacker guys. Sheesh. Those of us who aren't security pros don't know how to read between the lines and really need things like the above spelled out to us more plainly (preferably within the first three paragraphs of the article pointing out the threat).

Unfortunately, you can count on the tech press to blow everything out of proportion, especially when it comes to security issues.  Take everything with a grain of salt.

[https://www.eviscerati.org/comics/comic/hd/2012/07/secret-history-technology-journalism](https://www.eviscerati.org/comics/comic/hd/2012/07/secret-history-technology-journalism)

---

### Post by CharlesA on 2012-11-21
> **lykwydchykyn said:**
> Unfortunately, you can count on the tech press to blow everything out of proportion, especially when it comes to security issues.  Take everything with a grain of salt.

[https://www.eviscerati.org/comics/comic/hd/2012/07/secret-history-technology-journalism](https://www.eviscerati.org/comics/comic/hd/2012/07/secret-history-technology-journalism)
That is a fact. They will do anything to get people's attention. Attention = hits.

The same thing happens on other news sites too.

---

### Post by sffvba[e0rt on 2012-11-21
> **koenn said:**
> well, at least the author adheres to the unix philosophy of small tools that do one thing only. Maybe he's also hoping for some bazaar style distributed development where other people write the propagation system or extensions such as a delivery system of pluggable privilege elevation mechanisms. 

If you're writing malware, might as well do it in line with the established practices of the target system.

:d


404

---

### Post by jerome1232 on 2012-11-21
I heard it's easy to install a rootkit on a well secured server.

Oh wait... 

Nothing that new here, rootkits have existed for how long?

---

### Post by Tibuda on 2012-11-21
> **Paddy Landau said:**
> Fascinating. Perhaps it is time to start developing a Linux anti malware application.

You mean, like Avast and ClamAV?

---

### Post by Aaron Christianson on 2012-11-22
> **CharlesA said:**
> This x 9000.
[IMG]http://media.tumblr.com/tumblr_mdhry6i8fh1r1e6ee.gif[/IMG]

---

### Post by Paddy Landau on 2012-11-22
> **Tibuda said:**
> You mean, like Avast and ClamAV?
As I understand, they protect against Windows viruses, e.g. if you are running a mail server. I believe that they do not protect against Linux malware. I may be incorrect.

---

### Post by Frogs Hair on 2012-11-22
```
sudo apt-get install rkhunter
```

```
sudo rkhunter --check
```

This application does show unhide.rb as a false positive.

---

