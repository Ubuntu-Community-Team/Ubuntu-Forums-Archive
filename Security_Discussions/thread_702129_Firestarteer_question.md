---
title: "Firestarteer question"
date: 2008-02-20
forum: Security Discussions
---

### Post by cybergalvez on 2008-02-20
Hi all I've got a real firestarter newbie question.   Its my understanding that the firewall in ubuntu is iptables and that firestarter is a gui to edit the iptables, so my question is: once you install firestarter and get it configured do I need to keep it running? or can I just run it when I need to make a change?  or do I have it all wrong?
Thanks in advance for any and all help
Jose

---

### Post by freelinuxhelp on 2008-02-20
To answer your question, I could close it after I configured it, and it would keep the configuration, but I don't use it anymore.

Further...
As I understand it, the firewall in Linux is netfilter, iptables is the userland application for configuring it...
Iptables can be a royal PITA to configure, so firestarter (and a few others) were created to make it easier to use.
I don't know if I would use firestarter. I read somewhere that the project is dead, and the latest news on their website is from July of 2005. [http://www.fs-security.com/news.php](http://www.fs-security.com/news.php)

If you search synaptic for firewall, you'll get a few different GUI config tools.

On a side note, it's been my experience, that Ubuntu has automatically opened the port for any service I installed. What's the bigger picture? What port do you need to open? There may be another way.

---

### Post by Liet_Kynes on 2008-02-20
After configuring your firewall its not necessary to run firestarter except to change rules.

Although ... I seem to be experiencing trouble with that. After rebooting I check the status of the firewall with 
```
sudo iptables --list
```
and there appears to be no rules loaded.

Only if i manually start firestarter does the firewall rules get loaded. How does one get the ruleset to be loaded automatically? All the FAQs say that you don't need to run firestarter for the rules to be loaded.

---

### Post by ung/xunil on 2008-02-20
> **cybergalvez said:**
> Its my understanding that the firewall in ubuntu is iptables and that firestarter is a gui to edit the iptablesCorrect.> **cybergalvez said:**
>  so my question is: once you install firestarter and get it configured do I need to keep it running? 
No.
> **cybergalvez said:**
> or can I just run it when I need to make a change?Yes.
> **cybergalvez said:**
>  or do I have it all wrong?No you didn't. You got it right. Firestarter is to be used exactly that way: you run the "wizard" to configure it at least one time (not optional) and use it to change rules when needed. You can close it after setting the rules because every time you'll reboot, Firestarter will be executed and will apply the rules (it saves them in /etc/firestarter/).

The only problem in Firestarter is that it checks if the network interface you defined is active when it starts on boot, and many times it fails here if you are using a wireless interface, leaving the computer without a firewall. There are some workarounds for this problem in this forum. If it's not your case, forget it.

---

### Post by cybergalvez on 2008-02-20
thanks everyone for your help.  The big picture (why I installed it in the first place) is that I am getting an error connecting to my works breeze server, when I called tech support they said to make sure some ports were open, so I felt obligated to test that and tell them that it still doesn't work (not quite finished doing that but almost ready).  

So now my question is: once I've installed firestarter ad messed with it, if I remove it will that leave my computer with the default firewall that it had before, or now that its installed should I just let it be?
Jose

---

### Post by ung/xunil on 2008-02-20
> **cybergalvez said:**
> once I've installed firestarter ad messed with it, if I remove it will that leave my computer with the default firewall that it had before, or now that its installed should I just let it be?
Jose
If you remove/uninstall firestarter, then, when you reboot, iptables will not be set and [will have the default policies/rules]("https://help.ubuntu.com/community/IptablesHowTo"), i.e. none (ACCEPT ALL), just as when you first installed Ubuntu.

When you uninstall firestarter (or firehol, or shorewall, etc), iptables will have its rules setup and working until you shutdown. When you reboot, there will be no "tool" to set up iptables and iptables will have the[ default settings]("https://help.ubuntu.com/community/IptablesHowTo").

---

### Post by cybergalvez on 2008-02-20
> **ung/xunil said:**
> If you remove/uninstall firestarter, then, when you reboot, iptables will not be set and [will have the default policies/rules]("https://help.ubuntu.com/community/IptablesHowTo"), i.e. none (ACCEPT ALL), just as when you first installed Ubuntu.

When you uninstall firestarter (or firehol, or shorewall, etc), iptables will have its rules setup and working until you shutdown. When you reboot, there will be no "tool" to set up iptables and iptables will have the[ default settings]("https://help.ubuntu.com/community/IptablesHowTo").

Wow thanks did I have it backwards, I thought that with the standard iptables installed that essentially everything was closed except for what my programs opened (ie port 80 when you fire up a browser) but if I understand you correctly the default iptables desn't really close off any ports so I really should be running something like firestarter anyway right?
Jose

---

### Post by OrangeCrate on 2008-02-20
> **cybergalvez said:**
> ... so my question is: once you install firestarter and get it configured do I need to keep it running? or can I just run it when I need to make a change?
Jose

As said, you only need to run Firestarter when you need to make a change. To see if it's working, you need to check it from a remote source such as Shields Up!

See Firestarter's FAQs here:

> Q: How can I test if the firewall is working for sure?

The only way to know for sure if your firewall coverage is complete is for an outside party to test it. You can not run nmap or some other network tool to test the firewall from the firewall host itself.

There are many free sites on the Internet that will provide a remote scan of your system. Here are a few that we have found useful, as well as the expected result with the Firestarter default policy loaded:

    * Sygate Security Scan
      The scan will report Unable to detect any running services!
    [B]* Shields Up!
      The scan will report all ports as stealthed.[/B]

[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

Shields Up! is here:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by HermanAB on 2008-02-22
Note that the Linux network stack is pretty good, so even with NO rules in netfilter, you are still OK.

Probably the most important rule to add to a firewall these days, is a rate limiting filter, which will slow down any kind of repetitive attack (and they all are).  Most (all?) firewall scripts out there, add oodles of rules that don't really do anything useful anymore, since the problems that they guard against, have been fixed years ago.

Sooooo, it is my humble opinion that if you add a simple rate limiting rule then your system is likely safer than with any other overly complicated firewall system, Shorewall, Firestarter, whatever.

Add the following lines to the bottom of /etc/rc.d/rc.local, to limit new connection attempts to once per minute:

iptables -I INPUT -p tcp -m state --syn --state NEW --dport ssh \
-m limit --limit 1/minute --limit-burst 1 -j ACCEPT
iptables -I INPUT -p tcp -m state --syn --state NEW --dport ssh -j DROP

That will defeat even the most patient hacker...

---

