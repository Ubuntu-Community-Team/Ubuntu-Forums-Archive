---
title: "Making Ubuntu 6.06 net-banking safe?"
date: 2006-08-28
forum: Server Platforms
---

### Post by Dar on 2006-08-28
Hi there,

I'm a new Linux user (as in days), but this seems to be the more relevant section to make a post than the new-user area. I have modified my installation using Ubuntu Demon's customisation guide so that I have multimedia support (it ran a highly-compressed movie file much better than Windows XP did, possibly because my Windows has to run an AV + firewall). I also installed RealPlayer and Skype from the commercial repositories, as well as flash and vlc plugins for Mozilla Firefox. I do not have a firewall or anti-virus in Ubuntu, but my update manager tells me my system is fully updated. 
I have 3 questions:
* Can I safely use net-banking on this multimedia-enabled Ubuntu installation? 
* Is this significantly safer than using net-banking on a Windows XP machine that is kept up-to-date with Windows Updates, the free Zonealarm firewall, commercial anti-virus software and free ad-aware (for removing spyware)?

Part of the reason I want to do this is I want to install Ubuntu 6.06 on my dad's and sister's PCs, but still give them all the multimedia functionality they want as well as OpenOffice programs. So my third question is: how do I make it easy for a non-computer person to keep an Ubuntu 6.06 installation secure enough for net-banking? (If I get tired keeping Windows safe (?) then I'm sure they skip safety-procedures far more often than I do). 

Thanks for any help, I'd greatly appreciate it :)

---

### Post by funchords on 2006-08-29
> **Dar said:**
> 
I have 3 questions:
*1* Can I safely use net-banking on this multimedia-enabled Ubuntu installation? 
*2* Is this significantly safer than using net-banking on a Windows XP machine that is kept up-to-date with Windows Updates, the free Zonealarm firewall, commercial anti-virus software and free ad-aware (for removing spyware)?
*3* How do I make it easy for a non-computer person to keep an Ubuntu 6.06 installation secure enough for net-banking? (If I get tired keeping Windows safe (?) then I'm sure they skip safety-procedures far more often than I do).

*1* Yes.

*2* For net banking, it's about the same level of protection.  Both platforms provide for a secure sockets connection from your browser to the bank's server, which provides both encryption (no evesdropping) and authentication (no impersonating).

Anti-virus and Anti-Adware software is designed to prohibit malicious software from being stored or executed on your system.  You are not going to get this kind of malicious software from your bank.  Furthermore, because of the safe privilege levels that user accounts have, any malicious programs that somehow do get executed have very limited access.  Linux is a inhospitible place for viruses, they don't do much, they can't spread far, and this is why there are so few Linux viruses.

*3* Continue to update Ubuntu when prompted.  Tell your dad and sister to beware of e-mail messages pretending to be from a bank, the government, or anyplace else official.  Never click on their links.  These usually are attempts by scammers to con them into inputting personal information into a fake, unsecure site.  Always log on to these important sites directly.

---

