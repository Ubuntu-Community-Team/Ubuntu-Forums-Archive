---
title: "New user, in need of hardening, privacy and security enhance guidance"
date: 2023-01-29
forum: Security
---

### Post by hallp2022 on 2023-01-29
Hi all,

New to Ubuntu and loving the experience so far. I am planning on beefing up my Ubuntu Desktop 22.04.1 LTS (64-bit) in terms of its security and privacy. For privacy, I have played around VPNs, macchanger, and am now exploring Next DNS to see what packages/apps are calling home and what kind of connections my machine is making with other servers. This has been an interesting journey and made me realize how Ubuntu in general is far more privacy-invasive compared to Windows who calls back home and Microsoft servers with almost every click you do in the OS.

Either way, as a newbie Linux and Ubuntu user who's got limited to medium level tech skills, is there a newbie-friendly guide you would recommend me to follow in order to enhance and tweak the privacy and security of my Ubuntu machine?

I am already using LUKS encryption and a Yubikey which is required to deploy sudo commands and to login to my machine, so this is good. I have also read the Linux overview section of privacyguides website and they recommended something about SWAP (which I don't fully understand the concept yet) which says: "Consider using ZRAM or encrypted swap instead of unencrypted swap to avoid potential security issues with sensitive data being pushed to swap space. ".

Now, how do I know if I am already using ZRAM or encrypted swap instead of unencrypted swap? Would this be enabled in my machine by default by running the latest and updated version of Ubuntu desktop or is this something I need to enable? If so, how can I implement it in my machine? I am running Ubuntu in a Macbook Pro 2015 model.

Another question I had was in relation to Secure Boot. I have done some reading about it and I think it is advantageous to use it. How do I know if this is already ON in my setup and how can I activate it if not?

Thanks everyone!

The other question I had was about secure boot,

---

### Post by TheFu on 2023-01-29
> **hallp2022 said:**
>  
Either way, as a newbie Linux and Ubuntu user who's got limited to medium level tech skills, is there a newbie-friendly guide you would recommend me to follow in order to enhance and tweak the privacy and security of my Ubuntu machine? 

No.  You should be concentrating on raising your Linux-fu for the next 2-5 yrs before jumping into this.  There are lots of lists for how to harden Linux, but many of those things will break your working system, so a deeper understand of what's really happening is required.  Prior tech knowledge that isn't Unix-based isn't useful.    Start here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Work through at least the first 250 pgs.  You'll still be a beginner.

I know you won't listen.  So, some keywords you can google to find more:   "STIG", "Practical Linux Security", Bob Toxen's _Real World Linux Security_  [https://linuxsecurity.com/features/real-world-linux-security-bob-toxens-perspective](https://linuxsecurity.com/features/real-world-linux-security-bob-toxens-perspective)
Beware that STIGs are distro and release specific.  Things done in 1 release don't apply to others.

There's little need to harden any Linux desktop, provided you always stay on a supported,  LTS from one of the top 5 Linux distro companies.  If you choose to run a different distro, all bets are off.  Many distros are created will little regard to security.

Unfortunately, security isn't a yes/no question or answer.  The same applies to privacy.  Using a VPN doesn't necessarily provide security or privacy.  It is how the tool is used which does that.
The level of security to handle a curious neighbor with access to your wifi network is very different than if a spy agency for a capable govt are out to get you ... or everyone.

There is a sticky threat at the top of this sub-forum which makes suggestions and has links to Ubuntu resources.  Start there, as you work through TLCL book.  In all Unix systems, basic knowledge is required as the first step to accomplishing the next tasks.  Say there are 100 steps.  Until you've fully mastered users, groups, file and directory permissions, you are still below step 5.  Nearly all Unix security begins with file and directory permissions.  Heck, directories are just files anyway.

Moving on to the next paragraphs in the questions ... 
If your system is using LUKS whole disk encryption - you checked that box during installation - then the swap is storage on encrypted storage, so your is encrypted.  Recognize that no disk encryption matters if the encrypted container is unlocked.  It only protects data at rest - i.e. a 100% powered down system.
BTW, if you use encrypted storage, you need to have fantastic backups.  If the wrong byte becomes corrupted, you could lose access to everything in that encrypted container.  Daily, automatic, versioned, "pulled", backups are my #2 security tool.  Much more important that almost anything else, except being on a currently maintained, LTS, from a trusted source.

I don't use secure boot and a few weeks ago, it was learned that many motherboard makers don't actually enforce it.  [https://arstechnica.com/information-technology/2023/01/300-models-of-msi-motherboards-have-secure-boot-turned-off-is-yours-affected/](https://arstechnica.com/information-technology/2023/01/300-models-of-msi-motherboards-have-secure-boot-turned-off-is-yours-affected/)   More research has found that it isn't just MSI.

This is a lesson.  Don't believe marketing claims until you validate them and for things you really care about, you'll want to periodically re-validate it is still working as you believe.

---

### Post by hallp2022 on 2023-01-29
Thanks for the tips, really appreciate the constructive and learning angle. I downloaded the books and it looks amazing. Something for me to use for my continuous learning about this wonderful OS!

---

