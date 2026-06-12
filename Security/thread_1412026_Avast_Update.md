---
title: "Avast Update"
date: 2010-02-20
forum: Security
---

### Post by mattysegstro on 2010-02-20
I guess I have two questions here, the first one is that if I install Avast for Linux, it has the option to automatically update and all that, but what is it updating?  I notice that it's not in my list of Installed Software in the Ubuntu Software Center under the main Applications menu.  So if it's not there then I assume it doesn't automatically update when I run the Ubuntu Updater for all system updates.  I'm just wondering how to keep both aspects of it up to date, the signatures and the program itself.

Secondly, do you guys have any suggestions for what other programs I can run to keep my system more secure?  I've had nothing but bad luck with Clam and Klam antivirus programs, AVG Antivirus for Linux, and so I started using Avast.  If I go into Synaptic and install the 2 rootkit programs it offers (rootkit hunter and one other one), they install just fine but are no where to be found in the menu's.  Maybe there's a way to get them to show up, maybe Avast scans for rootkits anyway, etc.  So what other programs are out there for things like Antivirus, Antispyware, Antirootkit... just Antimalware in general?

Thanks a lot, I know that many people are going to say that I don't need these programs but that's what people have said about MacOSX for years and look at the malware that's out for it now and how people still refuse to run antimalware programs.  I just do my online banking and everything in Ubuntu and so I'd rather be safe than sorry.

Matt

---

### Post by Enigmapond on 2010-02-20
Well I hate being the first one to say this but you are spending way too much energy on this problem. You don't need these programmes...there is little to no way Linux can contract a virus and malware CAN'T install on your system. Trust what you read in the forum regarding this.

Cheers!

---

### Post by 73ckn797 on 2010-02-20
Avast works fine in Ubuntu. I only use it to scan my Windows drive and that is very rarely since I only use Windows rarely. Every time I have scanned Ubuntu there are no problems found.

---

### Post by mkvnmtr on 2010-02-20
The two root kit apps you mentioned are command line apps. They will noot be in a menu. If you have to have something with a gui try Tiger. It will do a pretty good security scan of your system using the command line apps.I kind of like running stuff like that but the truth is like the other poster said it is not necessary. The thing is if you run some of the security apps you might learn something about your system.

---

### Post by mikewhatever on 2010-02-20
> **mattysegstro said:**
> ...........

Thanks a lot, I know that many people are going to say that I don't need these programs but that's what people have said about MacOSX for years and look at the malware that's out for it now and how people still refuse to run antimalware programs.  I just do my online banking and everything in Ubuntu and so I'd rather be safe than sorry.

Matt

The problem is, the approach of barricading yourself behind animalware programs doesn't work. Just think of all those botnets of infected Windows PCs, likely running some kind of AV. All you really get by installing AVs is a false sense of security.

Anyway, to answer about Avast, as it is a manually installed program, it should be updated manually. There is probably an update button in its own interface.

---

### Post by mattysegstro on 2010-02-20
Thanks for the advice on the rootkit programs, and Avast does have the updater, I just wasn't sure if it was for the signatures only or the program as well, but I'll assume it's for both.

As for botnet infected PC's and stuff like that, like I said in my original post, I just worry because everyone thought that OSX was so secure that nothing could affect it, and now there are tons of infections out there for it.  Not as much as for Windows, I agree, but I just think that people have to be cautious in Linux even if we think we can't be affected by malware.  In today's age where there is so much private information being transmitted across the Internet, we have to do what we can to reduce the chances of us being infected and our data compromised.

Just my 2 cents worth, but I'll stick with Avast I guess and try that other rootkit program just to be on the safe side.  It doesn't take much time to scan stuff anyway, what can it hurt?

Matt

---

### Post by 73ckn797 on 2010-02-20
Avast updates signatures and program as needed. It does not run automatically unless you open it and set it to update when opened. It otherwise just sits there unless you start it.

---

### Post by jrusso2 on 2010-02-20
There is two malwares for Macs and both you have to install.

---

### Post by mikewhatever on 2010-02-21
> **mattysegstro said:**
> ..........

Just my 2 cents worth, but I'll stick with Avast I guess and try that other rootkit program just to be on the safe side.  It doesn't take much time to scan stuff anyway, what can it hurt?

Matt

Whatever gives you the peace of mind. :) To be honest, I used Avast on Ubuntu back in 2007 or something like that. Somehow, the idea of not having an AV seemed odd, after switching from Windows.

---

### Post by Sir Jasper on 2010-02-21
Hi,

I use Wine and  I also use avast! to check my Home directory.

I would say, set the updater to automatic. You can always cancel the download.

My regards

PS as a general note:  avast! (debian version) is best for ´buntu users on broadband (since the daily updates are full, not incremental).

---

### Post by rookcifer on 2010-02-21
You are wasting precious time and resources with AV software, which is completely and utterly worthless for a desktop machine.  You should focus more on learning about the DAC file permissions mechanism, ACL's, and Mandatory Access Control systems like AppArmor.  

Really, all you need is to just be sure to do updates when prompted and always install software from trusted sources (the Ubuntu repos).  Nothing else is needed.  If you want more, read up on the things I mentioned above.  See the security sticky at the top of this forum.

I have never seen a single person infected with a genuine Linux virus and I have been on various Linux security forums for years.  I have seen people damage their systems accidentally (by installing something from an untrusted source) but never have I seen a virus or a drive-by download, etc.

---

