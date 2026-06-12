---
title: "I feel unsafe using network facing app without Firejail .... What about you ?"
date: 2020-11-07
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2020-11-07
I never use any network facing app namely Firefox & Qbittorrent without Firejail. I just dont feel safe using them without a sandbox. What about you ?

---

### Post by crip720 on 2020-11-07
Don't use Firejail and have not had anything bad happen yet.  More concern about companies with our data that have weak security.  Every week or two read about someone leaving all our data out on a non-secured data base for anyone to read/copy.  Sometimes it does not make much sense that we are supposed to secure our machines to prevent data leaks, but all our data is on the web for the taking.

---

### Post by SeijiSensei on 2020-11-08
Used Firefox by itself for decades; never had an issue.

---

### Post by poorguy on 2020-11-09
I've used Firefox since my first days of using Linux without knowing what Firejail Sandbox was and never had a problems.

Nowadays I know about Firejail Sandbox and what it does so I  use it just for the extra level of protection it supposedly gives me.

---

### Post by linuxyogi on 2020-11-10
I must mention a fact & that is I am really grateful to the devs of Firejail for creating it. In the old days when there was no Firejail creating a custom Apparmor profile was (and still is) a nightmare. 
In other words the default protection that Firejail provides is more than enough in my personal opinion so no need to bother with creating a custom profile.

---

### Post by DuckHook on 2020-11-10
The old-timers on these forums will always encourage users to practice defence in depth. Firejail is an excellent tool as a *part* of that strategy. Those who like using AppArmor are also on the right track. I jail by running browsers within both VMs and LXD containers. All are valid measures.

crip720 does raise an excellent point: even the most hardened browser practices are pointless if the highest exposure risks are completely outside of our own control. These days, our greatest attention needs to be focused on giving out as little info as possible on things like social media and commercial Internet sites.

---

### Post by crip720 on 2020-11-22
Would also recommend the use of ad blocker on any browser.  Sites do not have control of what ads are placed on them and quite a few of trusted sites have ad malware.

---

### Post by Qassis on 2020-11-22
I'm WITH YOU!   I use Firetools (GUI for Firejail) with all APPs that don't need to have access to my drive or other (for some apps I use firejail to keep them off the network). For example, I use Firefox within Firejail MOST of the time when surfing (facebook, email, etc.) and blogging, but Firefox without firejail if I want to (i.e.) save a page or file to my hard drive. Currently I use Lynis, Firetools/Firejail, ClamAV/ClamTK, GUFW/UFW and Ubuntu LivePatch (auto-updates), all good HOME USER Level programs with System Admin Level increased security (IMHO). The programs I list are fairly self explanatory and many run well just by downloading them without configuring them. NOTE:  Anyone who gets hold of your computer can change your password, then log in if your BIOS is not password protected; here's HOW, (or How to change your password if YOU get locked out (or for someone who steals a Linux box)): [https://www.osradar.com/access-single-user-mode-ubuntu-20-04/](https://www.osradar.com/access-single-user-mode-ubuntu-20-04/)   Note, to my knowledge there is NO danger of this over the internet; but good for you to know if ever locked out of your own box due to password issue/error. HOW MUCH SECURITY DO I NEED WITH UBUNTU?   That's a personal and different answer for each of us.   If a game box only (no banking, purchasing etc.) perhaps very little additional security required. I look forward to hearing from others who use additional security (beyond defaults that come with Ubuntu 20.04), what you are using, and 'why'. Thank you.

---

