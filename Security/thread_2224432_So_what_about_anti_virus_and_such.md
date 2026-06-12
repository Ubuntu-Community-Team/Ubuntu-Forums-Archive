---
title: "So what about anti virus and such?"
date: 2014-05-16
forum: Security
---

### Post by nknwn on 2014-05-16
New Lubuntu users: "So what about anti virus and such?"

Me: "Well, allegedly Linux is safe from viruses and such."

 The new Linux user looked at me doubtfully. I went on: "You can install anti virus if you want but it doesn't run in the background you have to select a file to scan" My new Lubuntu user held up their hand: "I don't want to know about that, it sounds too complicated"

Of course I could have said to my new Lubuntu user: "Well, Linux is safe from viruses and such" but that is not strictly true is it. Linux viruses and malware exists, it's just quite hard to get 'infected', but it must be possible and that begs the question: Why would one not install anti virus and why should it not run in the background? That would certainly make new users happy.

I'm going to send my new Lubuntu user this: [http://www.howtogeek.com/135392/htg-explains-why-you-dont-need-an-antivirus-on-linux-and-when-you-do/](http://www.howtogeek.com/135392/htg-explains-why-you-dont-need-an-antivirus-on-linux-and-when-you-do/)

They will read the first paragraph and be happy most likely.

---

### Post by TheFu on 2014-05-16
"... and such" is vague. I'd drop that.

The most common end-user virus happens when they run WINE with Windows programs and do dumb things. If end-users continue to do dumb things, they will eventually get screwed regardless of the OS. Running flash, java, javascript is dangerous regardless of platform. Don't do it on untrusted websites.

You should also point out that the AV for Windows is known to be less than 50% effective. This has been known for many years.

Most of the real security in Linux is addressed through file permissions. Devices use file permissions and control access that way too.  A better understanding of directory/file permissions couldn't hurt them.

The only real reason for a Linux system to run AV is to be nice to any neighboring Windows machines.

If they run servers (or services), things are completely different. It is a very dangerous world out there and being hacked is a real concern.

---

### Post by jon43 on 2014-05-16
You need to understand what AV software does and how it works.

AV software is only looking for files/programs that fit the known "definitions" of a virus. Since there is no known "virus" for Linux (yes, there are Trojans, Rootkits, and other Malware- but that isn't a "virus"), the only virus definitions it will look for are windows-based. In other words, even if it had a 100% chance of catching what it's looking for, it would make 0% difference for a linux-only user.

---

### Post by LastDino on 2014-05-16
> **TheFu said:**
>  AV for Windows is known to be less than 50% effective. 
.
Are you being generous? ;D

I've personally never found AV useful in live situation when I was using WIndows.  Especially, if your're acquiring  things by ''shady'' methods. Which is something Windows users  do it more often or not. 
However, It did came in handy when I was dealing with removable media.

---

### Post by jon43 on 2014-05-16
I've had it pick up a few things... but it was pretty obvious stuff. Like an attachment named Photo.jpg.exe

---

### Post by HermanAB on 2014-05-16
You can send new users this link: [https://www.gnu.org/fun/jokes/evilmalware.html](https://www.gnu.org/fun/jokes/evilmalware.html)

---

### Post by Chayak on 2014-05-19
I use to analyse malware for a living before being promoted to solutions engineering so I have a decent perspective on the question.

The truth about all Anti-Virus programs is they don't detect new threats. I'll lump them all into the term AV for brevity.
I have a few hundred out of 4TB of malware samples that are not detected by any vendor's AV. It's a fact of life. AV software signatures only detect samples that have been in circulation for a bit or are widespread enough to become a priority. The most dangerous malware is the ones you never know you have and it can be months if ever before a signature is produced.

As to not being an idiot on the web you can get malware from anywhere. A script inserted into an ad can exploit your browser and inject a malicious payload. Many people assume only porn and shady sites are a risk but your more likely to get malware from religious based sites. It's easy to get malware. There's a reason why malware analysts tend to work in virtual machines. There's a huge number of computers running AV software infected with malware and there's zero signs operationally until you forensically examine the system for it. The malware isn't detected because it doesn't draw attention to itself, hence no analysts have spared time to look at it and make signatures.

There's a reason most malware analysts become rather paranoid and end up using Linux, or Macs. Yes, I know malware isn't unknown on the platforms but compared to Windows the number of malware threats combined are far less than .01%

But as for Linux as long as you're not running an SSH server on a system with weak passwords so a bruteforce bot doesn't infect your system you're quite safe.  There's a reason most malware labs run on Linux and just use windows virtual machines for analysis.  The system I use to archive all the samples is running Ubuntu Server.

---

### Post by jon43 on 2014-05-19
Thanks Chayak for the information. That does make me feel somewhat safer than even before on the Ubuntu platform. 

Geez... 4tb? How many samples is that? Most malware is only a few hundred KB's up to maybe a few MB I thought?

---

### Post by Chayak on 2014-05-19
Quite a few and that includes 500GB or so of Android malware.  I don't have an exact count as much of it is in encrypted archives.  It's encrypted mostly to protect people from themselves should they ever happen to come across them.

---

### Post by Rob Sayer on 2014-05-19
Yep, that was a good post.

I've only had linux installed on my own machines for a couple of years but I have friends who have been using it at home for 20 years.  Not *one of* them uses an AV program that runs in the background constantly.

I use ClamTK to check dl'ed files on demand.  But that's only because it could end up on my one remaining windows partition.  Unlikely, because I rarely use windows anymore, but you never know.  Or I could give a bad file to a windows user.  I don't use Wine.  I'd use a VM instead myself.

Many linux users don't even use a firewall, and I don't think I need to teel you how stupid that'd be in windows.  You'd want a linux firewall if you were running a server definitely, and it's probably a good idea if you do a lot of torrenting.  

I'm not saying don't bother with a firewall.  It's a good idea.  But for regular desktop users it's really not that necessary.  Linux doesn't leave ports open like stupid windows does.

---

### Post by jon43 on 2014-05-19
> **Chayak said:**
> Quite a few and that includes 500GB or so of Android malware.  I don't have an exact count as much of it is in encrypted archives.  It's encrypted mostly to protect people from themselves should they ever happen to come across them.

I hear about Android malware all the time it seems like. There are three questions I have about this, if you don't mind. 

First, what is so different about Android compared to desktop Linux that makes it more vulnerable to malware? You never hear about Ubuntu having this stuff, but there is apparently that much on Android- why?

Second, what sort of malware is it, in general? Just trojans that get packaged with real apps, or are people actually pulling off script injections in the browser and such?

Third, if you had an Android, how would you secure it? Is it even possible?

---

### Post by Chayak on 2014-05-19
With Android it's an application that a user installs that has hidden functionality.  It can have hidden control features, bitcoin mining, information harvesting, etc.  Many of the ad engines are quite aggressive at collecting data as well and are a privacy threat.  Many times these trojan applications are copies of legitimate apps.

99.99% of Android malware I've seen is free.  If you stick to the official Google or respected third party like Amazon and stay away from free apps that are loaded with ad engines you'll be fine.  There are a lot of researchers constantly looking over apps in those stores and any malware is quick to be taken down.

---

### Post by LastDino on 2014-05-20
> **Rob Sayer said:**
> 

Many linux users don't even use a firewall, and I don't think I need to teel you how stupid that'd be in windows.  You'd want a linux firewall if you were running a server definitely, and it's probably a good idea if you do a lot of torrenting.  

I'm not saying don't bother with a firewall.  It's a good idea.  But for regular desktop users it's really not that necessary.  Linux doesn't leave ports open like stupid windows does.

Even if you're a regular desktop user, it's highly recommended to install and enabling firewall is the first thing you do. While Virus threat may not be that effective against Linux atm, hacking is.

---

### Post by spynappels on 2014-05-20
If you are a regular desktop user, you are unlikely to have vulnerable services listening on ports and are likely to be behind a router which should not have any ports forwarded to your desktop.

Caveat is torrenting, as stated before.

---

### Post by bashiergui on 2014-05-20
Anyone asking about AV on linux doesn't understand what AV does. It's just The Thing they need for their computer to stay safe.

There is no Thing to keep you safe. Maybe it's the best advice to tell them to do nothing so there is no security blanket, no protection between them and Bad. Then maybe users would be more cautious because they can't rely on some Thing to protect them.

---

### Post by TheFu on 2014-05-21
> **bashiergui said:**
> Anyone asking about AV on linux doesn't understand what AV does. It's just The Thing they need for their computer to stay safe.

There is no Thing to keep you safe. Maybe it's the best advice to tell them to do nothing so there is no security blanket, no protection between them and Bad. Then maybe users would be more cautious because they can't rely on some Thing to protect them.

For average computer users concerned with security, I send them to KrebsOnSecurity.com - he has a way of simplifying understanding.

I only run AV on Linux when required - it is mandated by our E&O insurance policy, for example. I don't think it does any good, but a contracts is a contract.

Over the years, I've been hacked twice. The first happened when I was on a US government network in 1994 and was very new to UNIX/Linux.  The internet was relatively safe back then.   The other time was around 2002, I was running redhat (not really important) with a version of BIND that was 2 months behind on patches.  Thanks to versioned backups, I was able to determine everything the attackers had done.  Didn't even reboot the box, though I did take it off the network for a few hours as this was determined.  These days, I'd pull the HDD to perform analysis from a trusted system. Back then, we didn't do that on Linux.

There is something about getting hacked that teaches humility. Anyone can be hacked these days. A-N-Y O-N-E.

---

### Post by bashiergui on 2014-05-21
> I only run AV on Linux when required - it is mandated by our E&O insurance policy, for example.Holy WTF. The stupid hurts physically sometimes. Sharp pain right here. Ow. 

An even more painful thought- I wonder if the insurance company have the same rigorous (LOL) requirements for their own network. :\

---

### Post by TheFu on 2014-05-22
I've worked in 7 different companies.  At 3, we didn't run Windows in my job and I don't recall any AV running.
At the others, we had Windows and AV was mandatory, controlled by IT, and we didn't have admin rights to stop it. I suspect big insurance companies are like that (but do not know).  More over, I worked in 1 company to deploy AV+patching for 20K sometimes-connected laptops.  The reporting of patches being installed was more important than actually getting them installed, it seemed.  The goal was 95% installation since the laptops might not be connected to their network more than 1 hr every few weeks over a DSL VPN.  These laptops were connected to customer networks constantly, so being patched and current was just a good idea.

I think they really just want people performing "industry standard" system maintenance and to uninformed people, AV **is** industry standard. After all, if Microsoft does it, then everyone else must too.

---

### Post by Cbhihe on 2014-05-23
Very interesting posts, folks. I am learning quite a bit...

I'm a Lx learner, actually a recent returnee from a distant but dedicated Unix past, when the web was all command line and surfing meant gopher'ing...

I am migrating from Win XP to Ubuntu's Trusty Tahr. I have set up a dual boot on my laptop, where I share all my files on an ext3 volume (/home == D:\) between Lx and Win XP.
As suggested earlier in this thread, what could happen is that an infected file acquired under Lx could perfectly go undetected and have no adverse effect while running Lx, but make its way on a shared volume that would then be a ticking bomb waiting for the Win XP OS to trigger it on its next boot.
So I want to protect my system under Lx as if it were a Win XP boot (I mean with at least the same "efficacy") hoping that overall I will be saving myself time and aggravation.

What would you recommend for a free client firewall and free client AV under Desktop-Lx ? ( I do do some torrenting after hours when connected to my ISP).
The requirement for the AV is that should actually carry *malware*  libraries with at least daily updates and website black lists equivalent to products running under a Win OS.
- Lx Firewall: ufw ? anything else that's good, light weight and reasonably configurable ?
- Free Lx AV: Clam (Free) ? Comodo (Free) ?
Anything else that will block not only relatively rare (for now) Lx exploits but also Win exploits under Lx ?

Thanks ahead.

---

### Post by bashiergui on 2014-05-23
> What would you recommend for a free client firewall and free client AV under Desktop-Lx ? ( I do do some torrenting after hours when connected to my ISP).
The requirement for the AV is that should actually carry *malware* libraries with at least daily updates and website black lists equivalent to products running under a Win OS.You sure you read the thread? I'm thinking you skimmed a bunch of posts. [QUOTE=Chayak]With Android it's an application that a user installs that has hidden functionality. It can have hidden control features, bitcoin mining, information harvesting, etc. Many of the ad engines are quite aggressive at collecting data as well and are a privacy threat. Many times these trojan applications are copies of legitimate apps.


99.99% of Android malware I've seen is free. If you stick to the official Google or respected third party like Amazon and stay away from free apps that are loaded with ad engines you'll be fine. There are a lot of researchers constantly looking over apps in those stores and any malware is quick to be taken down.[/QUOTE]A lot of the dubious and outright malicious apps ask for way too many permissions on the phone. There's no reason a puzzle game needs access to my photos, contacts, gps, etc. Hell, a lot of "legit" apps overstep their needs. 


You can use Permission Monitor or Permission Explorer to see and control exactly what each app is accessing.

---

### Post by Chayak on 2014-05-23
> **Cbhihe said:**
> 
What would you recommend for a free client firewall and free client AV under Desktop-Lx ? ( I do do some torrenting after hours when connected to my ISP).
The requirement for the AV is that should actually carry *malware*  libraries with at least daily updates and website black lists equivalent to products running under a Win OS.
- Lx Firewall: ufw ? anything else that's good, light weight and reasonably configurable ?
- Free Lx AV: Clam (Free) ? Comodo (Free) ?
Anything else that will block not only relatively rare (for now) Lx exploits but also Win exploits under Lx ?

Thanks ahead.

Ubuntu has UFW built in
Don't bother with AV under linux.  The AV you can get in windows is much superior for obvious reasons.  If the windows AV is worth anything it will prevent anything it knows about from being executed at runtime anyway.

---

### Post by Cbhihe on 2014-05-24
@bashiergui
I did read every one of the 18 posts preceding mine. Some more than once actually.

My question has almost nothing to do with Android. The "almost" is there as a concession 
to the fact that Android is a (not so distant) relative of Lx.  Instead my post focuses on 
Desktop Lx's that share physical and logical space with Windows in dual boot configs. The 
rub lies in sharing partitions and alternatively allowing one system or another to boot. It is 
likely that Lx will fare well under the circumstances. I am concerned about viral infections 
gotten under Lx and only activated under Windows, when it boots.

The posts by Chayak [viz. #12] are truly interesting, because he describes the type of 
experience that one rarely encounters out there. But I am not referring to _that_ type of 
malware, that I already had a "chance" to experience on my own Android cell.  Rather I 
wanted to deepen on something TheFu said:

> **TheFu said:**
> 
The only real reason for a Linux system to run AV is to be nice to any neighboring Windows 
machines.

**It is exactly my case !** Hence my query... What would be a recommendation for a Free 
AV running under Lx and bent on recognizing malware active under Lx (not my priority) AND/or 
under Windoze (my utmost priority!) ?

@Chayak
Thanks for the input. Yes ufw is part of Ubuntu TT, but should I be content with that package ? 
I was hacked once too, running Sun Solaris and, boy, _it is_ a lecture on humility. Actually the
person who did it was quite correct and just left an easter-egg with a message behind. No real harm 
done. 
As I said I run Trusty Tahr as a Desktop Linux. However my near future will be an Ubuntu LAMP Server 
on a physically separate machine (no Windoze there) and Web Services with a database as backoffice. 
Should I still rely on ufw for that - I mean as far as a firewall is concerned ?
Again I quote TheFu:
> **TheFu said:**
> 
If they run servers (or services), things are completely different. It is a very dangerous 
world out there and being hacked is a real concern.

Cheers,
- ced.

---

### Post by maglin2 on 2014-05-24
I don't believe there currently is a free out of the box on-access AV/antimalware programme for Trusty. Comodo supported only up to Ubuntu 12.04.2 (kernel 3.5). There are plenty of on-demand scanners.

if your concern is browser related malware, then there are probably DNS (eg Open DNS, Comodo DNS), add-on (eg bitdefender trafficlight, adblock plus) and perhaps hosts file approaches to restricting access to sites hosting malware.

(and of course there is noscript)

---

### Post by TheFu on 2014-05-24
For the last 10 yrs, there is only 1 firewall for Linux - iptables.  EVERYTHING ELSE is just a front-end to iptables. ufw is a simple interface to iptables. Feel free to use something more complex, if you like. 

I run clamAV with daily/weekly (sorry - don't recall) updates on a file server that gets office-productivity data files. This is just to be a nice neighbor for Windows - my windows machines don't see any of those files (or get on the internet directly).

When running servers on the internet, being paranoid is your friend. Restrict access as much as possible. Requiring a VPN is the best security, but restricting which parts of the world might be desired and running something like mod_security (apache) and/or using a reverse proxy like nginx to filter dangerous requests is smart too.  Depending on the sort of programs you make available, it would be a good idea to seek out "security best practices" for the tool, language, webserver ... and hit the OWASP checklists for additional security measures.

I like to deny everything, then only allow the specific things required to normal users. For example, my blog has an admin set of pages - those are NOT available from the internet.  If there is a DB involved, lock it down so that only the specific IPs required to have access do ... - never the internet.  There are too many things to remember/list them all here.  Build a checklist, add to it, use DevOps tools to be consistent and be ready with excellent, versioned backups for WHEN (not if), the machines are hacked.  Hopefully, you'll only need those backups to migrate to a bigger, faster server or cluster of servers, but if not, you'll be ready.

---

### Post by Chayak on 2014-05-24
> **Cbhihe said:**
> 

@Chayak
Thanks for the input. Yes ufw is part of Ubuntu TT, but should I be content with that package ? 
I was hacked once too, running Sun Solaris and, boy, _it is_ a lecture on humility. Actually the
person who did it was quite correct and just left an easter-egg with a message behind. No real harm 
done. 
As I said I run Trusty Tahr as a Desktop Linux. However my near future will be an Ubuntu LAMP Server 
on a physically separate machine (no Windoze there) and Web Services with a database as backoffice. 
Should I still rely on ufw for that - I mean as far as a firewall is concerned ?

Cheers,
- ced.

UFW is perfectly fine as it's just a user friendly frontend for IPtables which is the standard Linux firewall even on high security systems and firewall specific distros.  Keep in mind that a firewall just blocks connections.  If you open a port for SSH or Apache to the internet then it doesn't provide any protection on those open ports.

AppArmor is something you should research for protecting exposed server processes.  If you're running SSH put it on a high nonstandard port to avoid most of the bots and configure it to use keys only.

---

### Post by Cbhihe on 2014-05-24
Thanks a bunch, Chayak, Maglin2 and TheFu... 
It does it for me. I think you have given me enough pointers to last me dense weeks of late study followed by trial and error. 
AppArmor was already on my plate and I 'll keep it there. I will give ClamAV a try (should be the easy bit) if I manage to run it on U.14.04. I will also look at grsecurity, RSBAC and nginx, when I have half a leg to stand on. Again thanks.
-ced.

---

### Post by waltsullivan on 2014-05-25
First, one needs to understand that a virus subverts code running on the target system, and gets the code (running as the user it was running as pre-attack) to DO SOMETHING. In Linux/UNIX, that means running as a regular user, unable to modify the system without further privilege escalation. In Windows, it's not so clear - some subvertable programs run with Administrative rights, privilege escalation is easier, etc. Other attack possibilites are services accepting requests from the network. Most Linux/Unix services run as root. If subverted, it's a win for the Bad Guy. However, the open-source nature of the Linux services, plus the ability to NOT RUN unneeded services helps. Windows has a different security model, different system calls, and different resources available to programs. A WindowsVirus.exe has no chance of running under Linux, unless one uses the WINE Windows environment simulator. Well, duh!

---

