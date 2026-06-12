---
title: "Device security"
date: 2024-09-01
forum: Security
---

### Post by vmelnikv on 2024-09-01
After updating to version 24.04.1, a section appeared in the settings that informed me of the danger in my laptop.
In particular:
Linux Kernel Lockdown:  ! Fail
and
UEFI Secure Boot ! Fail

I went into UEFI and enabled Secure Boot. Then I entered Ubuntu and again the same error about the unlocked bootloader.
Why is this happening?

I started with the address specified in the report [https://fwupd.github.io/hsi.html](https://fwupd.github.io/hsi.html), then followed the links to their own VC where it is proposed to change the attribute file /sys/kernel/security/lockdown, namely: 
    Linux Kernel Lockdown: Not locked down
    The running Linux kernel supports lockdown but it is disabled. To modify lockdown either modify the sysfs attribute /sys/kernel/security/lockdown or set it on the kernel command line.

But my /sys/kernel/security/lockdown attribute has the following content 
[none] integrity confidentiality
and that's it 
How and whether to lock down the kernel?
Also, the report contains the following errors:
2024-08-30 09:00:11 Linux Kernel Verification Pass (Corrupted &#8594; Not Corrupted)
2024-08-14 18:44:16 Linux Kernel Verification ! Failed (Not corrupted &#8594; Corrupted)
Why are there different dates? Are the checks running all the time?
Should I be worried about the 14.08.2024 kernel being corrupted, given that the update to version 24.04 was on 08/30/2024?

---

### Post by TheFu on 2024-09-02
Don't know if this is related, but in the last month, a few boot security issues have been found across a large number of hardware vendors - large and small.  One of the issue was that a BIOS maker included "test" signatures in their release that each vendor was supposed to remove before using, but didn't.  

Boot security has always been an issue with all computers. There are a few mitigation strategies, like preventing boot from any external devices and having a sufficiently complex, long, BIOS password.  Another mitigation is to not allow a computer to be touched by anyone untrusted.  And another is to use normal methods to mitigate the "evil maid" attack.  [https://en.wikipedia.org/wiki/Evil_maid_attack](https://en.wikipedia.org/wiki/Evil_maid_attack)

Until good fixes are widely available and deployed, these are what we can do today.  Which is best for you is determined by the risks for your specific situation.  

If you represent either a govt or corporate security team, I'd suggest contacting both your hardware vendors and OS vendors where you have paid support to get specific advice on mitigation and when each will provide their part of the solution to these problems.  Don't trust what random people post on the internet.

---

### Post by vmelnikv on 2024-09-02
> **TheFu said:**
> Don't know if this is related, but in the last month, a few boot security issues have been found across a large number of hardware vendors - large and small.  One of the issue was that a BIOS maker included "test" signatures in their release that each vendor was supposed to remove before using, but didn't.  

This is also possible, since I bought my Asus laptop without an OS at  all, and it was possible to install Ubuntu only after installing Windows  and downloading the appropriate drivers specifically for Windows.

> **TheFu said:**
> 
Boot security has always been an issue with all computers. There are a few mitigation strategies, like preventing boot from any external devices and having a sufficiently complex, long, BIOS password.  Another mitigation is to not allow a computer to be touched by anyone untrusted.  And another is to use normal methods to mitigate the "evil maid" attack.  [https://en.wikipedia.org/wiki/Evil_maid_attack](https://en.wikipedia.org/wiki/Evil_maid_attack)

Until good fixes are widely available and deployed, these are what we can do today.  Which is best for you is determined by the risks for your specific situation.

BIOS password is set. But I'm more concerned not with direct influence through physical access, but external, without physical access.
Also, I'm new to Ubuntu and after seeing a few reports about security issues, I'm starting to get worried.
  

> **TheFu said:**
> If you represent either a govt or corporate security team, I'd suggest contacting both your hardware vendors and OS vendors where you have paid support to get specific advice on mitigation and when each will provide their part of the solution to these problems.  Don't trust what random people post on the internet.
I do not represent the state or a commercial organization. Ubuntu is installed on my own laptop for personal use.

---

### Post by TheFu on 2024-09-02
> **vmelnikv said:**
>  
BIOS password is set. But I'm more concerned not with direct influence through physical access, but external, without physical access.
Also, I'm new to Ubuntu and after seeing a few reports about security issues, I'm starting to get worried.
  

All OSes have security issues.  At least with Linux-based OSes, the issues aren't hidden for months or 3+ yrs, so we can't take mitigation steps, like with commercial OSes that often seem more interested in legal action to prevent responsible disclosure than actually fixing issues.  If you need a more secure OS, get a chromebook and give up privacy, but have great security.  RHEL has some better security, but many people disable the entire framework to avoid the added complexities and hassles.  Ubuntu is more middle of the road - enough security, but not too many hassles.  You should pick the level of security you need. 100% your choice.

---

### Post by vmelnikv on 2024-09-02
> **TheFu said:**
> 100% your choice.
I am well aware that the choice is entirely mine.
However, the theme is not created for choosing or comparing OSes.
I am interested in what can be done directly in my situation.

---

### Post by TheFu on 2024-09-02
In the Security Subforum here, there are sticky threads [https://ubuntuforums.org/forumdisplay.php?f=338](https://ubuntuforums.org/forumdisplay.php?f=338) that provide the answer for "Basic Ubuntu Security", but those measures apply to every Linux flavor.

Years ago, I wrote an article about normal maintenance for Debian/Ubuntu systems.  It is still relevant.  [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) .  It was written from the MS-Windows perspective at the time.

Basically, 
[LIST]
[*]Run only LTS releases
[*]Run only supported releases
[*]Stay Patched - that means 2-4 times a month
[*]Have automatic, daily, versioned, backups.
[*]Install software only from trusted sources. For people new to Linux, that means staying withing Canonical Repos.  Don't looks for setup.exe or other separate installation methods. 
[*]If you must use a PPA, only use the PPA directly from the project team - for example, I use Firefox-ESR and use the Mozilla PPA to stay current.
[/LIST]

If you stay patched, don't install software from untrusted sources and have at least weekly backups, you'll handle 99.9% of all issues.  Obviously, if you make a habit of visiting the more dangerous parts of the internet, you can be tricked into hacking your own system.

Remote access into Ubuntu really doesn't happen unless YOU set up some method for that to happen.  If you do, be certain to setup the firewall to limit the access to clients you expect.  **gufw** is a nice, simple, firewall that allows multiple profiles - like Home, Work, Public ... so different subnets can be allowed or blocked or just block everything (when on a public network).  To be clear, the Linux kernel has the firewall included.  All the "firewalls" you see recommended are just tools for us users to control the firewall in the kernel. Some have more features than others, but the cost is more complexity.  

If you want more security, there are lots of options to enable/disable in your browsers and fat email program.  Browsers are likely to be THE most dangerous software you use daily.  The same is true on all OSes.

---

### Post by vmelnikv on 2024-09-03
Thanks, very interesting article about general Linux handling.
However, what to do in the case I described, directly?

---

### Post by TheFu on 2024-09-03
> **vmelnikv said:**
> Thanks, very interesting article about general Linux handling.
However, what to do in the case I described, directly?

Generally, just waiting a few weeks will cause an update to address the issues. I don't worry about things I can't so something about.  I patch weekly, usually on Saturday mornings.

I don't use secure boot.  I don't see how it helps with system security for my specific situations.  That doesn't mean it isn't useful for others, but for me, it just gets in the way of running OSes that don't have MSFT approval. 

I don't have 24.04 anywhere besides toy installs.  Maybe in 2025.  Perhaps.

---

