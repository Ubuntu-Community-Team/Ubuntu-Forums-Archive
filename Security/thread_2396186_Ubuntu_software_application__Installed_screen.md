---
title: "Ubuntu software application | Installed screen"
date: 2018-07-12
forum: Security
---

### Post by phuongubuubun on 2018-07-12
Dear All,

I installed Ubuntu 16.04, encrypted all Home folder.
Recently I installed to use Brave browser and also Bitwarden.
I realized that the Ubuntu software application does not look like it was before.
In the All page, it did not show all available software.
While in Installed page it did not show all installed software, just new installed software.

I attached image here for you to see. This is the first time I see this problem.
Please kindly advise if I was hacked.
Thank you very much.
[IMG]https://ubuntuforums.org/asset.php?fid=275032&uid=2101911&d=1531393372[/IMG]

---

### Post by TheFu on 2018-07-12
Depending on how you installed those programs, they may not show up. I've never heard of either of those packages/tools before.

"Software Center" doesn't show all 60,000+ packages which are available to prevent overwhelming relatively new users. I don't know how the things shown by software center are selected for display.

If you want to see app packages that APT can see, use one of these tools:
apt-get / apt
aptitude
synaptic

Those will show all core packages and any PPA repository packages you may have added.  If you install software by using .deb file, it usually will not show up in APT.

APT is the database which knows about all the software repositories configured on the machine. The programs I listed are just different interfaces into that database to support software management on the machine.

Clear as mud?

---

### Post by phuongubuubun on 2018-07-12
I do not understand your answer, TheFu.

---

### Post by TheFu on 2018-07-12
> **phuongubuubun said:**
> I do not understand your answer, TheFu.

Sorry.  We may not have vocabulary that can work.

Take anything you don't understand and use google. [https://wiki.debian.org/Apt](https://wiki.debian.org/Apt) should begin to explain APT, if that is confusing.

Or perhaps I'm the one not understanding the question.
I've asked a few questions.  Can you answer those?

---

### Post by phuongubuubun on 2018-07-12
OMG, thank you so much TheFu.
I installed synaptic and i can see all installed software.
So as you explained that to prevent overwhelming, software center does not show all installed software.
So then, my laptop is not hacked, right?

---

### Post by deadflowr on 2018-07-12
My understanding is that Ubuntu Software (also known as gnome-software) uses appstream metadata.
And any software which does not meet the standards of appstream will get excluded.
More (or little more) here: [https://wiki.debian.org/AppStream/Guidelines]("https://wiki.debian.org/AppStream/Guidelines")

---

### Post by TheFu on 2018-07-12
> **phuongubuubun said:**
> OMG, thank you so much TheFu.
I installed synaptic and i can see all installed software.
So as you explained that to prevent overwhelming, software center does not show all installed software.
So then, my laptop is not hacked, right?

It is unlikely your laptop is hacked, provided you follow these steps 
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

If you have high-risk computing behavior, then your computer might get hacked.

It is impossible for anyone to day that any computer is not hacked.  Heck, I can't say with 100% certainty that my laptop, being used to type this now hasn't been hacked.  I can say it is very unlikely.
Why not?  The system has been connected to a network and it is routinely connected to networks I don't control, around the world.  I could have gotten hacked in South America, Asia, Europe, or at the local cafe just 10 minutes walk from my home.  I do take proactive steps to make hacking it harder, but that might not be enough.  Who can say?

---

### Post by TheFu on 2018-07-12
> **deadflowr said:**
> My understanding is that Ubuntu Software (also known as gnome-software) uses appstream metadata.
And any software which does not meet the standards of appstream will get excluded.
More (or little more) here: [https://wiki.debian.org/AppStream/Guidelines]("https://wiki.debian.org/AppStream/Guidelines")

Ah - appstream.  I've seen some package bugs in these forums related to appstream. Checked all my systems and that tool isn't even installed.  I suspect it is related to specific DEs?   And I just happen not to be using those.

Interesting, regardless.

---

### Post by phuongubuubun on 2018-07-12
I think I probably got hacked.
Btw, I followed this advice to reduce damages: [https://spreadprivacy.com/linux-privacy-tips/](https://spreadprivacy.com/linux-privacy-tips/)

---

### Post by TheFu on 2018-07-12
> **phuongubuubun said:**
> I think I probably got hacked.
Btw, I followed this advice to reduce damages: [https://spreadprivacy.com/linux-privacy-tips/](https://spreadprivacy.com/linux-privacy-tips/)

Why?

Nothing you've said here leads me to think that.

---

### Post by deadflowr on 2018-07-12
possible related bug reports:
[lpbug]1589970[/lpbug]
[lpbug]1553211[/lpbug]
[lpbug]1548933[/lpbug]

Doubtful it's a hack.

---

### Post by phuongubuubun on 2018-07-14
> **deadflowr said:**
> possible related bug reports:
[lpbug]1589970[/lpbug]
[lpbug]1553211[/lpbug]
[lpbug]1548933[/lpbug]

Doubtful it's a hack.
i hope you are right, but i had experience of being hacked both my Mac OS X and Ubuntu.
finally, i have to encrypted all my laptops and followed expert advice on security.

---

### Post by TheFu on 2018-07-14
> **phuongubuubun said:**
> i hope you are right, but i had experience of being hacked both my Mac OS X and Ubuntu.
finally, i have to encrypted all my laptops and followed expert advice on security.

If you are being hacked on Ubuntu, disable bluetooth, disable wifi, and always use a VPN when away from home/work. Also, never leave your machine unattended and booted. 15 seconds is all it takes for someone to insert a flash drive to drop a tiny script onto the machine which would capture credentials. This is in addition to using full disk encryption with an obscenely long passphrase.   I use 2FA to unlock FDE.  And if your passwords aren't totally random and 20+ characters, give it up. If you are using words, then 34+ characters is needed.

If they are still gaining access after you stay patched and do automatic, daily, backups, then you should be able to figure out how they are gaining access.

Of course, this assumes there aren't any bad behaviors happening while using the computer and that no govt is after you for illegal activities.

If this is about friends or family hacking in, that's a completely different issue.

---

### Post by phuongubuubun on 2018-07-14
> **TheFu said:**
> If you are being hacked on Ubuntu, disable bluetooth, disable wifi, and always use a VPN when away from home/work. Also, never leave your machine unattended and booted. 15 seconds is all it takes for someone to insert a flash drive to drop a tiny script onto the machine which would capture credentials. This is in addition to using full disk encryption with an obscenely long passphrase.   I use 2FA to unlock FDE.  And if your passwords aren't totally random and 20+ characters, give it up. If you are using words, then 34+ characters is needed.

If they are still gaining access after you stay patched and do automatic, daily, backups, then you should be able to figure out how they are gaining access.

Of course, this assumes there aren't any bad behaviors happening while using the computer and that no govt is after you for illegal activities.

If this is about friends or family hacking in, that's a completely different issue.
Thank you very much TheFu. 
Very nice advice. What do you mean FDE?
 I used 2FA for anything that is important. I also setup VPN too.
I will increase password to 34+.

Btw, comparing Brave browser and Firefox browser, what is more security, do you think?

---

### Post by TheFu on 2018-07-15
FDE = full disk encryption
Not all VPNs are secure. Never use PPTP. With others, try to use 256-bit encryption. 128-bit isn't considered secure.

For passwords, nobody should need to know more than 3 or 4 (unless you work for a govt on classified systems).  Store online passwords for each different login inside a password manager and use the longest passwords allowed. You'll never type them anyways, plus each login should have different credentials.   For banking and where ever money is involved, use a different login too.  I couldn't tell you my username to my bank. It is long and random. It is tied to a completely different email address than I use anywhere else.  But most logins shouldn't be tied to a password.  Passwords are security failures waiting to happen. Some sort of key or PKI should be used everywhere online at this point.

So that leaves 3-4 physical logins which still need strong passwords for most  people,
1) passphrase to unlock the FDE into your computer - you can use 2FA for this to make it 45+ characters with a USB key/yubikey
2) login to your desktop/laptop  (after FDE is unlocked)
3) login to a physical work computer
4) login to your password manager (use 2FA too).

If you work on classified systems, then you'll have multiple separate logins for each disconnected network.

I never mix login credentials. I will not let google/bookface/twwwwwwr be used to authenticate for some other online system.  Actually, I avoid using cloudy services due to privacy concerns.  Yes, I have accounts, but mostly to prevent shadow accounts by those services.  Most of the huge cloudy services are blocked at the network layer by my systems. To access them requires some effort because normally, all their domains resolved to 127.0.0.1.

If it isn't clear already, never use smartphones or tablets for anything sensitive/financial. Those platforms have too many security issues to be trusted.

No browser's security should be trusted 100%.  We can only attempt to mitigate the risks as much as possible.  All browsers allow remote servers to run code locally on your computing device.  That should be enough warning.  Every tab is another opportunity to be hacked. Every saved state from a prior run is a way to retain dangerous code. 

If you want a secure browser experience, create a new userid, start the browser, visit the 1 site you need, no others, and do what you require. Shut down the browser and remove the account and all files under that userid when you are done.  If you want a little more security, put that new userid into a restricted container with read-only access to the system.  NEVER visit more than 1 website, which you can't always trust anyways.

I have a browser and about 10 trusted sites that I'll use only from my home network and only for low-risk activities.
I use a different userid and a different browser for online banking running inside a firejail container.  If I need to do other financial stuff elsewhere, I'll shutdown and restart a new userid and new firejail instance for the next site.  
I was a CFO at a small company. In my country, business banking accounts don't have the same protections against fraud as personal account do.  Basically, if someone hacked my computer, they could steal our entire payroll and the bank wouldn't be liable for any of the money.  So, maybe I'm a little paranoid, but how could I explain to all the workers that they weren't being paid because our bank account was hacked through my negligence. I couldn't.  BTW, we were an IT Infrastructure and Security Consulting firm.

IMHO.

---

### Post by phuongubuubun on 2018-07-15
> **TheFu said:**
> FDE = full disk encryption
Not all VPNs are secure. Never use PPTP. With others, try to use 256-bit encryption. 128-bit isn't considered secure.

For passwords, nobody should need to know more than 3 or 4 (unless you work for a govt on classified systems).  Store online passwords for each different login inside a password manager and use the longest passwords allowed. You'll never type them anyways, plus each login should have different credentials.   For banking and where ever money is involved, use a different login too.  I couldn't tell you my username to my bank. It is long and random. It is tied to a completely different email address than I use anywhere else.  But most logins shouldn't be tied to a password.  Passwords are security failures waiting to happen. Some sort of key or PKI should be used everywhere online at this point.

So that leaves 3-4 physical logins which still need strong passwords for most  people,
1) passphrase to unlock the FDE into your computer - you can use 2FA for this to make it 45+ characters with a USB key/yubikey
2) login to your desktop/laptop  (after FDE is unlocked)
3) login to a physical work computer
4) login to your password manager (use 2FA too).

If you work on classified systems, then you'll have multiple separate logins for each disconnected network.

I never mix login credentials. I will not let google/bookface/twwwwwwr be used to authenticate for some other online system.  Actually, I avoid using cloudy services due to privacy concerns.  Yes, I have accounts, but mostly to prevent shadow accounts by those services.  Most of the huge cloudy services are blocked at the network layer by my systems. To access them requires some effort because normally, all their domains resolved to 127.0.0.1.

If it isn't clear already, never use smartphones or tablets for anything sensitive/financial. Those platforms have too many security issues to be trusted.

No browser's security should be trusted 100%.  We can only attempt to mitigate the risks as much as possible.  All browsers allow remote servers to run code locally on your computing device.  That should be enough warning.  Every tab is another opportunity to be hacked. Every saved state from a prior run is a way to retain dangerous code. 

If you want a secure browser experience, create a new userid, start the browser, visit the 1 site you need, no others, and do what you require. Shut down the browser and remove the account and all files under that userid when you are done.  If you want a little more security, put that new userid into a restricted container with read-only access to the system.  NEVER visit more than 1 website, which you can't always trust anyways.

I have a browser and about 10 trusted sites that I'll use only from my home network and only for low-risk activities.
I use a different userid and a different browser for online banking running inside a firejail container.  If I need to do other financial stuff elsewhere, I'll shutdown and restart a new userid and new firejail instance for the next site.  
I was a CFO at a small company. In my country, business banking accounts don't have the same protections against fraud as personal account do.  Basically, if someone hacked my computer, they could steal our entire payroll and the bank wouldn't be liable for any of the money.  So, maybe I'm a little paranoid, but how could I explain to all the workers that they weren't being paid because our bank account was hacked through my negligence. I couldn't.  BTW, we were an IT Infrastructure and Security Consulting firm.

IMHO.

OMG, thank you so much.
I think I was lucky because I am not CFO.
Thank you very much for your advice with a long message.

---

