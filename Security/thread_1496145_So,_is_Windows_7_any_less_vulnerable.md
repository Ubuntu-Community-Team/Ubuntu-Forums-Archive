---
title: "So, is Windows 7 any less vulnerable?"
date: 2010-05-28
forum: Security
---

### Post by donsy on 2010-05-28
My laptop is beginning to show its age so it may be time for a new PC soon, and most likely it'll come with Windows 7 preloaded. I currently run a dual boot with Lucid and Windows XP, and although I hardly use XP anymore I would repeat this configuration on the new PC. So now I'm wondering if Windows 7 is any less vulnerable to viruses and malware than its earlier predecessors because I don't plan to renew any virus checking software that may come with it.

---

### Post by aysiu on 2010-05-28
> **donsy said:**
> My laptop is beginning to show its age so it may be time for a new PC soon, and most likely it'll come with Windows 7 preloaded. I currently run a dual boot with Lucid and Windows XP, and although I hardly use XP anymore I would repeat this configuration on the new PC. So now I'm wondering if Windows 7 is any less vulnerable to viruses and malware than its earlier predecessors because I don't plan to renew any virus checking software that may come with it.
With Windows 7, you can set up something like *sudo* so that you're prompted for a password if you are doing anything that will modify system files.

Set it up that way.

Also, install NoScript for Firefox and make sure Windows updates are set to install regularly, and turn off all the autorun stuff.

The likelihood you'll then get a virus or malware of any kind is pretty low, assuming you aren't downloading random shady .exes.

---

### Post by ssulaco on 2010-05-29
> **donsy said:**
> So now I'm wondering if Windows 7 is any less vulnerable to viruses and malware than its earlier predecessors because I don't plan to renew any virus checking software that may come with it.
There are alot of good freeware AV programs (just run one)
[http://majorgeeks.com/downloads29.html](http://majorgeeks.com/downloads29.html)
I like AVG,research it,I wouldnt pay for AV protection,I agree with aysiu,be careful where you go and what you download

---

### Post by JustYakov on 2010-05-29
It should be alright, and believe me when I said as I used Win7 when it was still in RC stage! :P But yeah, have an anti-virus handy or else bad things will happen, like I had to learn the hard way.

---

### Post by wilee-nilee on 2010-05-29
> **aysiu said:**
> With Windows 7, you can set up something like *sudo* so that you're prompted for a password if you are doing anything that will modify system files.

Set it up that way.

Also, install NoScript for Firefox and make sure Windows updates are set to install regularly, and turn off all the autorun stuff.

The likelihood you'll then get a virus or malware of any kind is pretty low, assuming you aren't downloading random shady .exes.

Yes, I know with both XP and W7 you can from a limited account right click and run as a administrator for program installs and modifications. W7 it is automatic from a limited, for a gui to popup for the admin password, never used vista probably basically similar.

For AV avast, malwarebytes, and superantispyware, are very good. Superantispyware is especially good. ccleaner to keep things cleaned up and a optimizer defragger like auslogics is very good and very fast.

---

### Post by UberStudent on 2010-05-29
You don't need to get a machine with Windows. Places like TigerDirect sell remarkably powerful NoOS machines for under $500. I'm using [this one]("http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=5279778&SRCCODE=GOOGLEBASE&cm_mmc_o=VRqCjC7BBTkwCjCECjCE") right now.

---

### Post by wilee-nilee on 2010-05-29
> **UberStudent said:**
> You don't need to get a machine with Windows. Places like TigerDirect sell remarkably powerful NoOS machines for under $500. I'm using [this one]("http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=5279778&SRCCODE=GOOGLEBASE&cm_mmc_o=VRqCjC7BBTkwCjCECjCE") right now.

Kind of a heavy device to carry around compared to a laptop eh.;) and THIS ITEM IS CURRENTLY UNAVAILABLE

---

### Post by CharlesA on 2010-05-29
@ wilee-nilee: Vista was the same, it would prompt for the user/password of someone with admin/power user rights if a limited user tried to install something or modify the system.

There have been arguments if UAC does anything for security, since many users are "click happy" and just click yes to any prompt. If you set it up after folllowing what aysiu suggested, you should be fine.

I've been running Win7 on my home desktop as well as my netbook without any problems (minus the BSOD on my desktop from failing memory, which wasn't a software problem :p)

---

### Post by wilee-nilee on 2010-05-29
> **CharlesA said:**
> @ wilee-nilee: Vista was the same, it would prompt for the user/password of someone with admin/power user rights if a limited user tried to install something or modify the system.

There have been arguments if UAC does anything for security, since many users are "click happy" and just click yes to any prompt. If you set it up after folllowing what aysiu suggested, you should be fine.

I've been running Win7 on my home desktop as well as my netbook without any problems (minus the BSOD on my desktop from failing memory, which wasn't a software problem :p)

Thanks, no problems with W7, hardly ever use it but it runs fast with a 1.6 atom chip with 2 gigs memory, 32 bit, lucid runs a little faster but it is a netbook.

---

### Post by CharlesA on 2010-05-29
Same deal when I've run Lucid on my netbook. I've got the same (or very similar) specs.

---

### Post by EarlGrey167 on 2010-05-29
You definitely need a good anti virus! My wife didn't have her Compaq laptop very long until I had to wipe the drive and start all over again. Since I've put AVG on it she hasn't had any problems with the OS.

---

### Post by OpSecShellshock on 2010-05-29
Yeah, the only thing I'd really caution against is that a lot of the newer devices with pre-installed OS don't come with a physical recovery disk. Evidently there's a way to reinstall (which I suggest as the standard response to any confirmed malware at this stage in its development), but I'm not sure how it's supposed to be done.

As for the "less vulnerable" question, well, the OS itself probably has more native protection measures than its predecessors, but application vulnerabilities and exploits make that pretty irrelevant. There's arguably a greater degree of protection against the low-rent malware that works well enough against XP, but it's not hard for a more talented malicious developer to whip up the necessary tools. Also, a lot depends on the user. Separating levels of access is a decent approach in many cases. By default the first user to log in, even in Win7, will be the admin. After that users should be setting up a regular user account with fewer privileges, but most won't because it complicates things and all the TV commercials pound the "simple" drum.

And I cannot stress enough how, no matter how frustrating it can be, auto-update should be enabled. Yes, it will result in having to wait while things load and the system restarts a few times, but by now it's easy enough to be conscious of the 2nd Tuesday of every month, and to do backups on the 2nd Monday. As for AV protection, something with a bit of heuristic detection would be good, but for stuff that's already known, Microsoft's Security Essentials is darn good. Better than a lot of third party stuff, since they know their own proprietary components better (well, you'd think anyway).

I guess fundamentally there's no such thing as a safe computer for impatient users, but for everyone else it's pretty much a great time to be a tech lover.

---

### Post by HermanAB on 2010-05-29
Win 7 is pretty good and I like using it, but security wise it is still Windows...

---

### Post by teh_drizzle on 2010-05-29
This suggestion is a bit over the top, not recommended if you're not semi-paranoid. :P

If you're willing to go through the trouble of teaching your firewall what applications you trust then I would suggest something like Comodo Internet Security ([http://www.comodo.com/home/internet-security/free-internet-security.php](http://www.comodo.com/home/internet-security/free-internet-security.php)). It can be a bit frustrating at first when you use exotic applications but if you'd like a heightened sense of security it helps. 

I use my laptop on a college campus (think large lan, full of unprotected student laptops) and depending on where I'm connected I have different network profiles for file sharing and etc. It will also sandbox new applications such that if you happen to download a bad file it wont cause much trouble. The down side to this is you'll have to un-sandbox new-trusted applications.

Other than that, the suggestions others made are great! Just make sure to have a sufficient password if you plan on using remote-desktop applications.

---

### Post by Chayak on 2010-05-31
Coming from penetration testing and incident response Win 7 machines are pretty solid.  It's normally the third party software that's installed that provides access.  Adobe Reader being the number one reason from opening malicious PDFs.

On the linux front the number one reason is SSH with weak passwords followed by FTP.

There are always exploits that are not public but the people who have that kind of thing don't bother with home users.

The best practical security measure is to have a linux desktop with no external services running and iptables blocking everything by default and then run windows or another instance of linux in a VM.  That way you can always revert to a known clean state and update on trusted networks.

---

### Post by donsy on 2010-05-31
> **Chayak said:**
> 
<snip>
On the linux front the number one reason is SSH with weak passwords followed by FTP.
There are always exploits that are not public but the people who have that kind of thing don't bother with home users.
</snip>

I've used to think that the only way to hack a linux system would be to obtain the root password. Now I realize that there may be more sophisticated methods used by criminal organizations and rogue nations, but I honestly don't see how a linux system could pick up a virus or other malware simply by surfing the Internet.

---

### Post by CharlesA on 2010-05-31
> **donsy said:**
> I've used to think that the only way to hack a linux system would be to obtain the root password. Now I realize that there may be more sophisticated methods used by criminal organizations and rogue nations, but I honestly don't see how a linux system could pick up a virus or other malware simply by surfing the Internet.

Only if you are stupid and download a package from a random website and install it without checking to make sure it is legit.

---

### Post by rookcifer on 2010-05-31
Windows 7 is essentially the same security-wise as is Vista.  The main improvement that Vista/7 have over XP is UAC and smarter defaults.  

If you run a 64 bit version of Vista/7, you also get the benefits of what M$ calls DEP (which is what we call NX here in Linux land) as well as ASLR (which Linux has had longer).  These both help make certain exploits much more difficult.  Also IE runs in a sandbox (though who uses IE?).  Seven also introduced AppLocker, which is an improved version of the old SRP, but you only get it if you buy the Enterprise or Ultimate versions.  Ditto for BitLocker.

Really, I see no reason to use Windows at all, even if it's not *quite* the security disaster it was in times past.

---

### Post by n1ght5t4lk3r on 2010-05-31
> **UberStudent said:**
> You don't need to get a machine with Windows. Places like TigerDirect sell remarkably powerful NoOS machines for under $500. I'm using [this one]("http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=5279778&SRCCODE=GOOGLEBASE&cm_mmc_o=VRqCjC7BBTkwCjCECjCE") right now.

Dell now ship Desktop and laptop computers with Ubuntu pre-installed, and I'm sure there are other companies doing this as well, the machies cost a bit less due to not paying M$ licence and you got the peace of mind of out of the box security

---

### Post by mikewhatever on 2010-05-31
> **n1ght5t4lk3r said:**
> Dell now ship Desktop and laptop computers with Ubuntu pre-installed, and I'm sure there are other companies doing this as well, the machies cost a bit less due to not paying M$ licence and you got the peace of mind of out of the box security

I suspect it's been a while since you visited dell.co.uk/ubuntu. The page is still there, but there are no products. Apparently, also no computers with Ubuntu on the French, German and Spanish pages.

---

### Post by Rubi1200 on 2010-06-01
> **rookcifer said:**
> 
Really, I see no reason to use Windows at all, even if it's not *quite* the security disaster it was in times past.

Totally agree!

I am forced to use Windows at work, even though I tried to persuade/convince them that Ubuntu was better/cheaper (free)/more stable/more secure etc.

The computers at work are unstable, constantly crashing, virus alerts abound (mostly false positives), and so on.

The reaction I received was that the IT people are not willing to deal with the learning curve involved with Linux networking; apparently this was the only reason against such a move.

---

### Post by cprofitt on 2010-06-01
Windows 7, when installed and setup properly is more secure than Windows XP.

Windows 7, when installed per defaults is less secure than Windows Vista.

I recommend creating a non-administrative user and running as that under either Vista or 7 as it adds an additional step to the parade for malware getting through. (it will require name and password vs. just click yes).

If I were to evaluate the technical aspect of security I would rater Windows 7 / Vista ahead of Linux in security capabilities. OS X would be behind Linux.

In reality given human influence, actual risk, and other factors I would rank the order Linux, Windows 7 / Vista, OS X in order of security.

In the end -- right now it is the ability of the OS to survive an exploited application more than the OS itself. The targets are applications right now.

---

### Post by rookcifer on 2010-06-01
> **cprofitt said:**
> 
If I were to evaluate the technical aspect of security I would rater Windows 7 / Vista ahead of Linux in security capabilities. 

Tell me you didn't just say that on a Linux forum!  But since you did, I must ask what "technical aspects" does Windows Vista/7 offer in terms of security that Linux does not.  I contend there aren't any, but I would like to see what you say.

> In the end -- right now it is the ability of the OS to survive an exploited application more than the OS itself. The targets are applications right now.

A lot of people say that, but they always fail to consider that the OS has a lot to do with what damage exploited apps can do in the first place.  After all, that's the entire purpose of frameworks like AppArmor -- to stop exploited apps from doing any damage outside of the scope of the app itself.

---

