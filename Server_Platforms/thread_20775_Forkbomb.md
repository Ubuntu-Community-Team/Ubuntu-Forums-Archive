---
title: "Forkbomb"
date: 2005-03-18
forum: Server Platforms
---

### Post by kuleali on 2005-03-18
the ascii forkbomb done by a normal user stopped my system.

**** this...

---

### Post by jdodson on 2005-03-18
[QUOTE=kuleali]the ascii forkbomb done by a normal user stopped my system.

**** this...[/QUOTE]

i read somewhere that debian was immune?  strange....

can you post up the code here so i can try it out on my ubuntu systems?

---

### Post by Poyayan on 2005-03-18
I tested forkbombing Ubuntu as well.

Code (just remove the a's and type it into a bash terminal.  The a's we added since it was converting the characters into smilies) -
:a(a)a{a a:a|a:a&a a}a;a:

The simple code (13 characters) to basically stop Ubuntu as a user.  Type it into the terminal and your system is effectively frozen.
Apparently debian is not affected by a forkbomb.  This should probably be fixed before release.
-Poyayan

---

### Post by jdodson on 2005-03-18
[QUOTE=Poyayan]I tested forkbombing Ubuntu as well.

Code (just remove the a's and type it into a bash terminal.  The a's we added since it was converting the characters into smilies) -
:a(a)a{a a:a|a:a&a a}a;a:

The simple code (13 characters) to basically stop Ubuntu as a user.  Type it into the terminal and your system is effectively frozen.
Apparently debian is not affected by a forkbomb.  This should probably be fixed before release.
-Poyayan[/QUOTE]

thanks for the info, i will give it a go.

---

### Post by kuleali on 2005-03-18
hear is the code:
:(){ :|:& };:

---

### Post by Poyayan on 2005-03-18
if you want a simple program that can do this as well you can use the following C code:

int main(void) {
     while(1) {
          fork();
     }
}

By the way I'm using Hoary prerelease with all the latest updates.
-Poyayan

---

### Post by adun on 2005-03-18
its not only an Ubuntu prob. works in sarge as well.

---

### Post by beeldings on 2005-03-18
I tried this on my machine, and I had to reboot. It brought my system down in a matter of seconds. I am also running the Hoary preview release. I hope this problem is patched by the time Hoary is officially released.

---

### Post by bored2k on 2005-03-18
[QUOTE=beeldings]I tried this on my machine, and I had to reboot. It brought my system down in a matter of seconds. I am also running the Hoary preview release. I hope this problem is patched by the time Hoary is officially released.[/QUOTE]
 scary ..

---

### Post by diebels on 2005-03-18
Tried this over an ssh session on my gateway with grsecurity kernel patch.
Got a few hundred or so of these:
"-bash: fork: Resource temporarily unavailable"
It ran for a few minutes and the system started to feel a bit sluggish. But I was able to run top and ps aux. Did a kill -9 <process>, on one of the "-bash" processes, and everything was back to normal.

Think grsecurity fixes this. Maybe selinux too, but I've never tried.

There is also a [Hardened Debian Project](http://www.debian-hardened.org/)

---

### Post by kuleali on 2005-03-18
This is actually not a big problem, just ulimit the resources any user has.

---

### Post by diebels on 2005-03-18
[QUOTE=kuleali]This is actually not a big problem, just ulimit the resources any user has.[/QUOTE]
 So how do you limit the resources of root?

---

### Post by diebels on 2005-03-18
Guess limiting the resources of root is a bit harder.

Tried running the fork bomb as root on the gateway. All server processes locked up, nfsd, sshd, httpd. Network and NAT was still running though, could still talk to the Internet from the inside network. Hit the reset button after while.

Set limits for users in ```
/etc/security/limits.conf
```

---

### Post by jdong on 2005-03-18
You can:

a. Use ulimit.

b. Use grsecurity kernel patches.



I personally recommend that you look into grsec, especially if it's a multiuser/shared system. It stops a good 80% of discovered exploits dead in its tracks... Looking back in time, the 2.6.8 kernel local root exploit was stopped by grsec... a LOT of exploits.

---

### Post by Buffalo Soldier on 2005-03-19
[QUOTE=beeldings]I tried this on my machine, and I had to reboot. It brought my system down in a matter of seconds. I am also running the Hoary preview release. I hope this problem is patched by the time Hoary is officially released.[/QUOTE]

Runing Hoary and experienced the same thing.

---

### Post by Mike Douglas on 2005-03-19
[QUOTE=diebels]So how do you limit the resources of root?[/QUOTE]
If someone else has root, then a forkbomb isn't your only problem.

---

### Post by jdong on 2005-03-21
If someone had root access, "cat /dev/urandom > /dev/hda" is a much bigger problem.... ;)

---

### Post by jon_k on 2006-03-24
This is basic [LInux+](http://www.comptia.org/certification/linux/) material here. You can hard-limit the resources any user uses (except for uid 0) by editing the /etc/security/limits.conf file.

ulimit is virtually useless, because AFAIK you have to execute it via bash (e.g. through a users bashrc) which can be reset by the user after they're logged in.

---

### Post by agger on 2006-12-14
> **jon_k said:**
> This is basic [LInux+](http://www.comptia.org/certification/linux/) material here. You can hard-limit the resources any user uses (except for uid 0) by editing the /etc/security/limits.conf file.

ulimit is virtually useless, because AFAIK you have to execute it via bash (e.g. through a users bashrc) which can be reset by the user after they're logged in.

I just tried entering this fork bomb as a non-privileged user on my Xubuntu box (running Xubuntu Edgy) and it just died - I had to turn off the power to reboot it.

I think this is a serious security problem - this should NOT be possible to do just like that. I think the DEFAULT SETTINGS should reject this sort of attack.

This article 

[http://www.securityfocus.com/columnists/308](http://www.securityfocus.com/columnists/308)

explains that this is a Linux problem - the BSDs just shrug off this kind of attacks. Maybe Ubuntu should, too, by default?

---

### Post by TyphoonJoe on 2006-12-22
> **jon_k said:**
> This is basic [LInux+](http://www.comptia.org/certification/linux/) material here. You can hard-limit the resources any user uses (except for uid 0) by editing the /etc/security/limits.conf file.

ulimit is virtually useless, because AFAIK you have to execute it via bash (e.g. through a users bashrc) which can be reset by the user after they're logged in.

Not quite...  Just change the ownership of the users bashrc file (or .profile or whatever) to root.  The user can execute the script, but can't modify it.  If you want users to be able to run  custom commands on login just create $HOME/login.sh for them, and have a call in the bashrc to this script.  

This works because a user can lower their ulimit, but cannot raise it ^_^

I agree Ubuntu should work this way out of the box, at least the server install.  But you CAN harden your system against this quite easily.

---

