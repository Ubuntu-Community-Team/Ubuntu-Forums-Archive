---
title: "VMware Server 2 is out for those waiting for it."
date: 2008-09-26
forum: Virtualisation
---

### Post by Coombabah on 2008-09-26
I didn't see any posts about it so here's a heads up for those that want to check it out.

VMware Server 2.
Version 2.0.0 | 116503 - 09/23/08
Note: It's over 500MB

Vmware Player 2.5 was also release on the same day

---

### Post by ewanchic on 2008-09-26
Is this only a 90 trail?

---

### Post by -Rick- on 2008-09-26
> **Coombabah said:**
> I didn't see any posts about it so here's a heads up for those that want to check it out.

VMware Server 2.
Version 2.0.0 | 116503 - 09/23/08
Note: It's over 500MB

Vmware Player 2.5 was also release on the same day
Did you try it? I've read some less positive comments about a new web interface (slow), though those were from some time ago.

---

### Post by cacharreo on 2008-09-26
No it isn't a 90 days trial version

---

### Post by trmentry on 2008-09-26
> **-Rick- said:**
> Did you try it? I've read some less positive comments about a new web interface (slow), though those were from some time ago.

The interface is very much like the interface from virtual infrastructure client just web based.

when you go to open up a console, it will download a 15mb firefox addon to actually get the console to open up.  that was somewhat annoying but on a lan, wasn't much of an issue... doing it remotely via an ssh tunnel over the internet was slow but worked and was tolerable.

i like that there isn't a client per-se that you install on your admin machine.  just go to the web page.  much nicer imo.  although i think i'll stick with my esxi install for now.


installing vmware 2.0 was a snap on 8.04.1 (hardy) 64 bit.  Not even sure I needed build-essential as it had pre-made modules already, so it never compiled anything.

Took about 10 min to get it installed and that was just hitting enter enter enter for defaults. :)

and no.. not 90 day restriction... just sign up and get your key...similar to getting a esxi key.

---

### Post by ewanchic on 2008-10-08
Dido. I was able to get server installed in the 64-bit Ubuntu environment, still utilized my existing virt-machines from 1.6.0. However, still had the keyboarding problem with Windows 2000 Professional, which I posted previously  [[ubuntu] VMware: Bad/wrong keys in Windows 2000 Profesional]("http://ubuntuforums.org/showthread.php?t=928008")

I'm split on the web interface. It's seems like I always need to pull up a console and type "vmware" in order to get a newly/active interface. And it's slow. Takes a good 5-10 minutes to get up my 2 windows virtual machine (2000 Server, 2003 Enterprise), but once they are up, they're fine.

I'm not sure how well the para-virtualiztion (harware) part of it works yet, I can only do software on mine :(

---

