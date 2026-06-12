---
title: "Immunity's DR Rootkit"
date: 2008-09-05
forum: Security
---

### Post by doas777 on 2008-09-05
I just saw this article on the reg about a new Open source rootkit pack called DR: 
[http://www.theregister.co.uk/2008/09/04/linux_rootkit_released/](http://www.theregister.co.uk/2008/09/04/linux_rootkit_released/)

I wanted to know what everyone thinks about this one. Any good remediation techniques, or incoming vectors to harden?

Have fun,
Franklin

---

### Post by insane_alien on 2008-09-05
as always on linux, its not going to infect you unless you actually install it yourself.

The most likely attack vectors will be social engineering to convince you to install it, your system being hacked (in which case any number of rootkits could be installed) and if the repos are compromised and you update from them.

pretty much the same as with most rootkit infections.

as long as you are careful about who gets access to your system and are sure you haven't been hacked then you will be fine.

---

### Post by doas777 on 2008-09-05
Fair enough. thanks!

---

### Post by insane_alien on 2008-09-06
Yeah, just keep applying normal rootkit prevention and detection measures. thedetection kits will soon gain the ability to detect them.

---

### Post by brian_p on 2008-09-06
> **insane_alien said:**
> Yeah, just keep applying normal rootkit prevention and detection measures. thedetection kits will soon gain the ability to detect them.

It would be sufficient to do only essential tasks with root privileges.

---

### Post by insane_alien on 2008-09-07
> **brian_p said:**
> It would be sufficient to do only essential tasks with root privileges.

thats how they get in though, by piggybacking on or disguising themselves as essential tasks that require root priviledges.

say, for instance, one of the repos gets compromised and a package gets replaced with a rootkit(could be sudo, could be ssh could be the kernel itself) and advertises itself as a critical security update. chances are someone will download and install it.

bam they've just got themselves a rooted box.

thats only one vector for attack. but they all come down to manipulating you into installing the rootkit yourself. which is why you need detection measures in place if you can't afford your server to be compromised. afterall even the most experienced sysadmin is only human and will make a mistake eventually, and it only takes one for a rootkit to be inserted.

---

### Post by brian_p on 2008-09-07
> **insane_alien said:**
> 

say, for instance, one of the repos gets compromised and a package gets replaced with a rootkit(could be sudo, could be ssh could be the kernel itself) and advertises itself as a critical security update. chances are someone will download and install it.

That 'someone' would be ignoring the warning about the packages not being authenticated and presumably relying on his outdated and more than likely compromised detector to rescue him.

> thats only one vector for attack. but they all come down to manipulating you into installing the rootkit yourself. . . . . 

A vulnerable service is another route but keeping software up-to-date effectively closes it off.

> . . . . which is why you need detection measures in place if you can't afford your server to be compromised. afterall even the most experienced sysadmin is only human and will make a mistake eventually, and it only takes one for a rootkit to be inserted.

I wonder how many people run rkhunter from their hard disk. 99%?

---

### Post by jerome1232 on 2008-09-07
I was under the impression running a rootkit detector from the hard drive of a compromised machine is pretty futile, as they tend to disguise themselves, you should run it while the compromised system isn't running. (ie via live cd)

---

