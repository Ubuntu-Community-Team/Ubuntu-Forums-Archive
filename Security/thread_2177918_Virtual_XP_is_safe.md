---
title: "Virtual XP is safe?"
date: 2013-09-30
forum: Security
---

### Post by jeehyun on 2013-09-30
I heard xp will be dropped next year.
I am using vmware player for xp in ubuntu.
Is it still safe to use virual xp(NAT mode) after 2014?
Will linux system guard my computer?

---

### Post by monkeybrain20122 on 2013-10-01
Why do you want virtual xp to go on the internet anyway? If it doesn't go on the internet then of course it is safe.

---

### Post by 1clue on 2013-10-01
No.  The VM is the same thing as running the computer on real hardware.  It has no magical protection of XP from the big bad world.  It's the same thing as running it behind your wireless router.  You can't be attacked from outside, but you can visit a website that has malware on it, or you can get email with malware on it, or any of the other ways XP would be vulnerable.

---

### Post by DuckHook on 2013-10-01
Just posted on another thread about this very topic. I run XP in a VM. I will disable the VM NIC come April 2014 and thereby sandbox XP within the VM. It won't have any further communication with the big bad outside world and will be stuck with whatever I've now got installed on it and nothing more. If you can *religiously* isolate XP this way, it should be as safe as anything else on your box. If you reconnect the NIC and decide to surf with it, all bets are off.

---

### Post by jeehyun on 2013-10-01
> **monkeybrain20122 said:**
> Why do you want virtual xp to go on the internet anyway? If it doesn't go on the internet then of course it is safe.

Oh. Internet is the reason to use xp for active-X based service.
If it's dangerous, I should think about windows 8 license.
Sad

---

### Post by DuckHook on 2013-10-01
> **jeehyun said:**
> ...If it's dangerous, I should think about windows 8 license.

ActiveX is one of the primary reasons why the Internet is infested with botnets. It is one of the worst scripting languages in existence and is like letting a ten-year-old juggle with hand grenades. Java and Flash are scary enough, but I dropped IE years ago and converted to FireFox (with NoScript installed to also restrict both Java and Flash) precisely to get rid of ActiveX. If you simply have to use it (for, say, a work site), then you have no other real choice but IE, as no other Linux browser that I'm aware of provides native support for ActiveX. FireFox has a plugin, but all it does is invoke IE in a tab, which obviously won't work on Linux. This means that, come April of next year when XP reaches end of life, you will have to move on to either Win 7 or 8.

If someone has another solution, I would love to know about it.

---

### Post by 1clue on 2013-10-01
If you're working inside a corporate firewall, then the site admins can prevent access to the outside world and you can use XP and ActiveX.

I agree with DuckHook's assessment of ActiveX and its relation to malware.

The good news is that there is a lot of new, good tech out there and techniques to minimize risk on other things.

XP was the workhorse Windows of its day, but now if I had to switch it up I'd probably go to Windows 7, it's the best desktop license of the recent ones.

---

### Post by SeijiSensei on 2013-10-01
One thing you can do is take a snapshot of the XP VM and store it away safely.  Then if the running version is borked, you can delete the VM and replace it with the clean snapshot.  I usually do this right after I have installed Windows and any other software like Office into the VM so I know I'm starting with a clean copy.

---

### Post by jeehyun on 2013-10-01
Thank you everybody

---

### Post by CharlesA on 2013-10-03
> **SeijiSensei said:**
> One thing you can do is take a snapshot of the XP VM and store it away safely.  Then if the running version is borked, you can delete the VM and replace it with the clean snapshot.  I usually do this right after I have installed Windows and any other software like Office into the VM so I know I'm starting with a clean copy.

I do that after I run updates. Quite handy.

---

### Post by dusanyu on 2013-10-05
Beauty of Virtual machines after you set it up back up the disk image. if the macchine gets infected or hacked delete and restore image from backup.

---

### Post by 1clue on 2013-10-05
Actually since XP is no longer going to receive updates, that's a really good plan.

In other words, every time you boot you boot from the latest snapshot.  You do what you do, (certainly you don't want to do anything with a credit card or bank account) and whether you get infected or not, it doesn't really matter.  You shut it down, and when you boot it comes back to the snapshot.

You don't get to save changes this way, but you can always start with a clean box.

---

### Post by knarf2 on 2014-03-05
> **DuckHook said:**
> Just posted on another thread about this very topic. I run XP in a VM. I will disable the VM NIC come April 2014 and thereby sandbox XP within the VM. It won't have any further communication with the big bad outside world and will be stuck with whatever I've now got installed on it and nothing more. If you can *religiously* isolate XP this way, it should be as safe as anything else on your box. If you reconnect the NIC and decide to surf with it, all bets are off.

If the writer of the above post (or anyone else on the forum) can answer my question, I'd be grateful. 
This sounds like an interesting idea, however forgive my ignorance, but how does one 'sandbox' a virtual XP and disable the 'NIC' (I assume that stands for network card?). Note I use only a single machine for use at home (not on any network). Thanks.

---

### Post by CharlesA on 2014-03-05
> **knarf2 said:**
> If the writer of the above post (or anyone else on the forum) can answer my question, I'd be grateful. 
This sounds like an interesting idea, however forgive my ignorance, but how does one 'sandbox' a virtual XP and disable the 'NIC' (I assume that stands for network card?). Note I use only a single machine for use at home (not on any network). Thanks.

Run it in a virtual machine and disable the network card in the virtual machine configuration.

How you accomplish that depends on what virtualization sofware you use (VirtualBox/KVM/VMWare/etc).

---

