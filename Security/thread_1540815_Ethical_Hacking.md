---
title: "Ethical Hacking"
date: 2010-07-28
forum: Security
---

### Post by liquidfunk on 2010-07-28
In September I'll be starting my third year of my degree, and I'm planning on doing a project on Network penetration and Ethical hacking for my final dissertation. 

Other than nmap, netcat, hydra and msf3 can anyone suggest some security testing tools, or techniques that I could use? 

I'm planning on (over my summer break) trying to gain entry into a friends computer, secured behind a firewall and a router. Just for some practice.

Perhaps someone could give me some pointers?

Thanks

---

### Post by bodhi.zazen on 2010-07-28
1. Read the security sticky. There are several tools listed in the NIDS and HIDS threads.

2. Use google.

3. Try any of the available security distros. 

[http://spins.fedoraproject.org/security/](http://spins.fedoraproject.org/security/)

[http://www.backtrack-linux.org/](http://www.backtrack-linux.org/)

DVL : [http://www.damnvulnerablelinux.org/](http://www.damnvulnerablelinux.org/)

There are many others, they are moderately uniform in the tools they include.

---

### Post by wacky_sung on 2010-07-28
Backtrack is good beside that you add it into Ubuntu.

[http://hakblog.co.uk/2009/11/26/add-backtrack-4-tools-to-ubuntu-tutorial/](http://hakblog.co.uk/2009/11/26/add-backtrack-4-tools-to-ubuntu-tutorial/)

You can use the list of tools here below.
[http://sectools.org/](http://sectools.org/)

---

### Post by Bachstelze on 2010-07-28
> **liquidfunk said:**
> 
I'm planning on (over my summer break) trying to gain entry into a friends computer, secured behind a firewall and a router. Just for some practice.

Perhaps someone could give me some pointers?

Unless your friend is very negligent or runs a very complex system, you probably don't have a chance.  It's not "If I try hard enough, I'll get in", you have to have a public exploitable security flaw (or find one, good luck with that).

---

### Post by stlsaint on 2010-07-28
> **Bachstelze said:**
> Unless your friend is very negligent or runs a very complex system, you probably don't have a chance.  It's not "If I try hard enough, I'll get in", you have to have a public exploitable security flaw (or find one, good luck with that).

I second that post. If you friend is running a *nix system behind a properly setup router firewall and a OS firewall than you are probably going to have to basically *ask* him to open up some ports or download some type of code that will give you root, which defeats your purpose!

---

### Post by earthpigg on 2010-07-28
> **stlsaint said:**
> I second that post. If you friend is running a *nix system behind a properly setup router firewall and a OS firewall than you are probably going to have to basically *ask* him to open up some ports or download some type of code that will give you root, which defeats your purpose!

he could socially engineer his target into downloading/installing some software with an undisclosed payload.

it shouldn't be hard, as they are friends.

there was a thread some time ago regarding a non-root script that would modify the synaptic menu entry (as an example) from this:

```
gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
```

to this:

```
gksu --description ~/.config/obfuscated/file/rawr
```

user enters password. the initial script hid the obfuscated script somewhere in a dotfolder at the same time that it modified the synaptic menu entry.

the 'rawr' script (that now has root) does whatever it wishes, then runs synaptic as normal. no reason to suspect anything.

how often do people check their gnome menu entries?

---

