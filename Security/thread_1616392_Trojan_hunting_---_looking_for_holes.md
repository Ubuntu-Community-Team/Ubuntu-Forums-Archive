---
title: "Trojan hunting --- looking for holes"
date: 2010-11-08
forum: Security
---

### Post by Fictitious1 on 2010-11-08
Hi,

Loving Ubuntu, upgraded to 10.10 /wishing I could get back to 10.04 but that's another post.  Anyway,  here's my setup --- I'm in Windows 7 running Ubuntu Guest with Virtualbox 3.2.10  -- Came home and found Comodo had found a trojan 

TrojWare.Win32.Trojan.Test.A@132245252

at Location 

/sys32/ ... VBoxSVC.exe-#.log

Ubunutu is my main VBclient - have XP but rarely use - So I decided to check into if somehow I had been compromised/because I leave it up and running all the time...

Ran rkhunter - ok 
ClamAV - ok
chkrootkit -- and came up with 

chkutmp  --  **stack smashing detected*** /chktump terminated

backtrace:
/lib/lib.so.6(~)
etc
./chkutmp{0x8048bb5
(and a few other things #s etc)



So my question is -- One is it possible to infect a windows Host from a guest OS?
2 am I compromised? 
What are next steps..

Thanks

---

### Post by P4man on 2010-11-08
First of all, I strongly suspect its a false positive. Try turning heuristics off and see if it still complains.

> One is it possible to infect a windows Host from a guest OS?

If the guest OS has rw access to shared folder on the host, then yes, in theory, in so far the guest OS is vulnerable. But ubuntu is your guest right? It would be rather rare for ubuntu to get infected, this seems rather extremely unlikely to have infected your host. If your host  really is infected (I still don think so), the ubuntu VM will have nothing to do with it, and it just happened to be a virtualbox file that got infected.

> 2 am I compromised?

Probably not.

> What are next steps..

Install ubuntu and run windows as a guest VM and stop worrying :)

---

### Post by brian_p on 2010-11-08
> **Fictitious1 said:**
> Hi,

chkutmp  --  **stack smashing detected*** /chktump terminated

A chkrootkit bug.

[https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/623144](https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/623144)

> What are next steps..

Purge rkhunter and chkrootkit from your system. Neither has a sparkling record for detecting trojans.

---

### Post by cariboo on 2010-11-08
According to the Commodo forums, that is a false positive, that was supposed to be fixed 2 years ago.

---

### Post by Fictitious1 on 2010-11-08
Thanks for all the info.  Loving Ubuntu -- Probably gonna do full install soon.. The only,, I mean seriously only reason I have not full installed it is because on the rare occasion the wife and kids are all sleeping at the same time and I get like 15 minutes of free time, I boot up Steam and play a game in windows -- However, as it is I would probably be better off dual booting and just boot to windows if/when needed.

Anyway thanks for the help.

---

