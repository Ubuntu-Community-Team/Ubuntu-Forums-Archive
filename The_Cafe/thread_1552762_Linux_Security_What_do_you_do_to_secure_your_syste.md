---
title: "Linux Security: What do you do to secure your system?"
date: 2010-08-14
forum: The Cafe
---

### Post by Rubi1200 on 2010-08-14
Having read a fair amount about AppArmor, SELinux, grsecurity, Bastille Linux, as well as many general articles on the subject of Linux security, I am curious as to what security practices users implement on their systems.

As an average desktop user who does not use any server applications, I do not know whether the majority of these "hardening" tools are actually necessary or practical.

I look forward to reading the ideas, security features, and other comments from the community about what you do for security and how secure you feel with your setup.

To get the ball rolling, this is my current setup:

1. Router with firewall

2. No additional firewall enabled

3. No antivirus program installed

4. Firefox with NoScript and BetterPrivacy addons

5. Only download software from the official repositories

6. Keep the system updated with official security updates

7. Frequent checking of the logs, especially auth.log and messages

8. Strong passwords (usually 12-16 in length)

So, how do you secure your system?

---

### Post by JBAlaska on 2010-08-14
NAT Router
iptables

That's it for me.

---

### Post by TheNerdAL on 2010-08-14
I think my router has a firewall but I do nothing at all to secure my system. :P

Is that bad? :O

---

### Post by Rubi1200 on 2010-08-14
> **TheNerdAL said:**
> I think my router has a firewall but I do nothing at all to secure my system. :P

Is that bad? :O
That is the whole point of this thread. I am trying to understand what people do to protect their system and whether you feel secure or not.

---

### Post by handy on 2010-08-14
I use [**_IPCop_**]("http://www.ipcop.org/") & the [**_Copfilter_**]("http://www.copfilter.org/") add-on installed on an old Dell Optiplex PIII, as a headless firewall, router. 

It is quiet, effective, reliable, speeds up my internet access a bit & costs me a little over $50-/year in electricity.

I also use some Firefox add-ons to make me harder to track, block all cookies only accepting those that I must to access sites like this, & search using Scroogle.

Yet I know that I'm far from invisible on the net, but it isn't hard to do what I do & it does help.

[I]**[Edit:]** I'll list the add-ons I run on Firefox these days, they aren't all for security:

Adblock Plus
Download Status Bar
English Australian Dictionary
Faviconize Tab
Flashblock
Ghostery
GoogleSharing
RefControl
Stylish
User Agent Switcher
Xmarks
Youtube Comment Snob

[/I]

---

### Post by user1397 on 2010-08-14
I have a router, but apart from that I don't have any active security, more of the preventive type, aka I only download from the repos, I update my system frequently, I have a strong(ish) password, etc.

---

### Post by lisati on 2010-08-14
My $0.02: Only let in what you want to let in.

---

### Post by Rubi1200 on 2010-08-14
> **lisati said:**
> My $0.02: Only let in what you want to let in.
I totally agree. 

The question is what measures do you implement in order to achieve this stated goal?

Common sense? Yes, of course.

But what other approaches do you apply?

---

### Post by BigSilly on 2010-08-14
I have the router firewall enabled, and also the Ubuntu firewall via GUFW too. After that I run both rkhunter and chkrootkit every so often. I don't generally bother with the anti-virus tools in Linux though, unless you think I should...

---

### Post by Naiki Muliaina on 2010-08-14
I install anything :redface:

---

### Post by Khakilang on 2010-08-14
Just ClamAV and so far my computer hasn't been infected.

---

### Post by ssam on 2010-08-14
noscript firefox plugin - i think browsers are the most vunerable bit of a system. noscript stops a site's javascript until i white list it.

dont install flash - i have flash in a separate firefox profile, which i only use when i need it.

denyhost - i have ssh open. this blacklists the IP adddress of anyone who tries to brute force a password.

nat router.

strong passwords.

---

### Post by lovinglinux on 2010-08-14
[LIST]
[*]Router with firewall

[*]Ubuntu firewall enabled sometimes via Moblock

[*]No antivirus program installed

[*]Firefox with NoScript, AdblockPlus and SelectiveCookieDelete (BetterPrivacy and Ghostery are in the fridge for now)

[*]Most of my software are from the official repositories and PPAs, but I have a couple of deb files from other sources too

[*]Keep the system updated with official security updates

[*]No frequent checking of the logs. Sometimes I scan the system with rkhunter.

[*]An exclusive strong password (usually 12-16 in length) for each site, one password for Ubuntu login and another for Kwallet/encryption.
[/LIST]

---

### Post by CharlesA on 2010-08-14
[LIST]
[*]Router with NAT.
[*]iptables that blocks connections to ssh from all but a couple IP addresses.
[*]ssh using keys.
[*]BitDefender scanning Samba shares.
[*]15+ char passwords that are pretty much randomized letters/numbers for websites (gogo keepassx).
[/LIST]

---

### Post by handy on 2010-08-14
> **ssam said:**
> ...
dont install flash - i have flash in a separate firefox profile, which i only use when i need it. 

I'm using the 64bit Flash which apparently has security issues, though I'm using Flashblock so only Flash files that I want to see are allowed to run. So far so good. :)

---

### Post by Bachstelze on 2010-08-14
Obviously depends on whether we're talking about a desktop, laptop, router, switch/bridge, firewall...

---

### Post by Rubi1200 on 2010-08-14
> **Bachstelze said:**
> Obviously depends on whether we're talking about a desktop, laptop, router, switch/bridge, firewall...
Well, I am interested in the average user's setup (which I assume is either a desktop PC or a laptop).

In my case, it is a laptop with default Ubuntu installation. The security "measures" I employ are mentioned in my original post.

I am really interested to know if people consider tools like AppArmor, grsecurity, and so on to be necessary in terms of enhancing security for an average computer user.

---

### Post by FuturePilot on 2010-08-14
> **Bachstelze said:**
> Obviously depends on whether we're talking about a desktop, laptop, router, switch/bridge, firewall...

Indeed.

---

### Post by Rubi1200 on 2010-08-14
@FuturePilot

Our posts seem to have crossed paths. I would appreciate any insights you have on this subject.

Thanks.

@Bachstelze ditto

---

### Post by flukeairwalker on 2010-08-14
The router firewall with WPA2 encryption, Ubuntu firewall through Firestarter, encrypted home drive, strong passwords, only install through repos, ad block and flash block on Chromium. I'm not a power user by any means, mostly just use UNE 10.04 on my netbook.

But I'll happily download torrents every day of the week ;)

---

### Post by lovinglinux on 2010-08-14
> **handy said:**
> I'm using the 64bit Flash which apparently has security issues, though I'm using Flashblock so only Flash files that I want to see are allowed to run. So far so good. :)

Adobe finds a critical vulnerability on the Flash plugin every month now, so anyone using flash should use Flashblock or Noscript.

---

### Post by Frogs Hair on 2010-08-14
Firewall  configuration , No Script , Ad Block, and Better Privacy . I retired Clam AV due to a possible memory leak in Ubuntu 10.04 . The most important is , " Engage Brain Before Clicking or Installing."

---

### Post by bunburya on 2010-08-14
I do very little to protect my laptop. No AV software or firewall. My main way of keeping my laptop safe is only installing things from sources I trust. Having read this thread I'll probably install a few of the Firefox addons when I get home.

---

### Post by Rubi1200 on 2010-08-15
@lovinglinux 
> BetterPrivacy and Ghostery are in the fridge for now

Are you saying that BetterPrivacy is not effective?

I have used it for some time now and have been happy with it, but I am open to suggestions.

---

### Post by Fludizz on 2010-08-15
Two things: 
- A router with firewall, I filter both ipv4 and ipv6 so nothing can connect to systems within my home network without my explicit permissions. (No policy on outgoing traffic)
- Keep the system up to date with all security updates. This avoids being vulnerable to well known issues.

And a third thing: Be very aware what I view/download on the internet. I only install from the ubuntu repo's, unless I am familiar with the program and trust it's source (Like Opera).

---

### Post by gnomeuser on 2010-08-15
I use the standard means offered by Ubuntu (AppArmor, Glibc and GCC proactive security features, gnome-keyring), outside of that I use GRC.com to generate randomized passwords for everything (was it not for the keyring this would be a terrible approach). 

On machines that leave my house I have homedir encryption enabled.

I really want to figure out the best way to add more encryption to what I do online, also I have been looking at setting up a Tor exit node using an old Zonbo machine.

Finally I have a pretty much deny all firewall in my router, though with upnp enabled (yeah comfort does win out occasionally, since I control all the software since my network I can't really see a serious downside, just make sure upnp connections are limited to a few applications and that connections are torn down after use).

---

### Post by Paqman on 2010-08-15
I'm a bit concerned to see people using Firestarter and ClamAV. The former is no longer maintained, and the latter is a very poor performer. I wouldn't trust either of them to make my system much more secure.

---

### Post by Rubi1200 on 2010-08-15
> **Paqman said:**
> I'm a bit concerned to see people using Firestarter and ClamAV. The former is no longer maintained, and the latter is a very poor performer. I wouldn't trust either of them to make my system much more secure.

I totally agree.

But, why then are these 2 programs still being given focus and linked to on the official Ubuntu Community Documentation pages?

And why is Firestarter, in particular, available through the official repositories if it is no longer maintained?

---

### Post by CharlesA on 2010-08-15
> **Rubi1200 said:**
> 
And why is Firestarter, in particular, available through the official repositories if it is no longer maintained?

I seem to recall one of the mods mentioning that firestarter will no longer by supported under 10.10.

---

### Post by malspa on 2010-08-15
> **Rubi1200 said:**
> I totally agree.

But, why then are these 2 programs still being given focus and linked to on the official Ubuntu Community Documentation pages?

And why is Firestarter, in particular, available through the official repositories if it is no longer maintained?

Firestarter is probably still fine to use, although I use guarddog instead.  But if you have a NAT router, I don't think you need either one.

I don't bother with ClamAV anymore.

---

### Post by Paqman on 2010-08-15
> **Rubi1200 said:**
> 
And why is Firestarter, in particular, available through the official repositories if it is no longer maintained?

It's in Universe, not the core repos. If you got rid of all the unloved packages in Universe, there's be nothing left. That's why we have MOTUs. 

The [documentation]("https://help.ubuntu.com/community/Firewall") does seem to state that Firestarter is obsolete, but people still use it for some reason.

---

### Post by mr-woof on 2010-08-15
I've got a nat router and a ipcop firewall running on an old p2-300 laptop at the moment, with copfilter installed. no ports being forwarded, no ssh open etc
Gufw/clamav/rkhunter/Chkrootkit installed
all systems updates
install from the repos
Firefox with no script. adblock and flashblock installed.

---

### Post by Pogeymanz on 2010-08-15
> **lovinglinux said:**
> [LIST]
[*]Firefox with NoScript, AdblockPlus and SelectiveCookieDelete (BetterPrivacy and Ghostery are in the fridge for now)
[/LIST]

Isn't betterprivacy kind of useless anyway? You can disable Flash's LSOs by going to adobe's site.

---

### Post by khelben1979 on 2010-08-15
My system is behind a hardware firewall. Feels pretty good!

---

### Post by BigCityCat on 2010-08-15
I have OSSEC Hids installed
iptables
Router firewall with wpa2
strong passwords
keepassx for important passwords
lastpass firefox addon for unimportant passwords
adblock
noscript
I also block third party cookies and clear all browsing history everytime I close my browser.

I do not feel secure. I am not a Linux expert so I feel I could be missing something. I do install things from gnome look but after that I pretty much stick to the repos. I do have Bitdefender installed but I use that to scan windows if windows were to get infected. I have clamav as well but I have never used it. I just installed it for the hell of it.

I do feel much safer using Linux and I have Win7 that I hardly ever use.The reason I hardly use it is because I don't feel safe using it.

Oh yeh I have the basic apparmour profile for Firefox enabled.

---

### Post by Windows Nerd on 2010-08-15
A router...with Open NAT (I know, how unsecure, but it helps when playing Xbox online); several ports forwarded, UPnP enabled.

Hosts.Allow set to only allow connections on the local network (so I can SSH around the house). Hosts.Deny set to deny everyone.

ClamAV, just so I don't have any windows viruses that could spread to my Windows computers.

Flashblock, noscript, and strongish passwords. That is all I think (I know, I really need to tighten up my router security!).

---

### Post by Rubi1200 on 2010-08-15
Just want to say a big thanks to everyone who has participated thus far. 

I find the approaches and combinations of security tools that people are using very interesting; this was what I was hoping to learn.

For my part, I think that I need to keep reading, reading, reading; which I do whenever I find the time.

I have recently been following this thread ([http://ubuntuforums.org/showthread.php?t=1550295](http://ubuntuforums.org/showthread.php?t=1550295)), which makes for fascinating reading (though many of the concepts and technical aspects are well beyond my limited knowledge).

Please feel free to continue sharing your thoughts about how to secure your system.

:)

---

### Post by MooPi on 2010-08-16
I built a firewall from the least expensive computer parts i could find. It runs 24/7 with the occasional reload due to power failure disruption. Uses Smoothwall and I consider it sufficient.

---

### Post by tjktyler on 2010-08-16
I use Ubuntu's GUFW and my router's hardware firewall. I constantly use secure connections when available (Email, IM, web browsing). I regularly check my running processes. Otherwise, I take precautions to make sure I don't do anything terribly stupid.

---

### Post by KingYaba on 2010-08-16
OpenDNS
Firefox + noscript
And just some common sense when it comes to installing software and how I store sensitive files on this computer (Truecrypt).
Router is wpa2 with a very strong password. It blocks things, too.

---

### Post by Cant on 2010-08-17
I don't really need internet protection because I only ever go to the sites in my bookmarks, but I completely lock down the computer when I leave it.

---

### Post by julio_cortez on 2010-08-17
Browser addons + Antivirus (just because I have a shared data partition between W7 and Kubuntu).
I might aswell consider adding a router with firewall anyway (the one I currently have either doesn't have it or has it locked down as it's still an old router I got from my ISP).

---

### Post by Penguin Guy on 2010-08-17
I have a router with firewall. I have nothing else protecting my system: No IPTables, no antivirus, no log-checking, no browser extensions, no passwords, nothing.

Unless you do something stupid like setup SSH with a short password (which is what firewalls prevent) or download and run a file from a dodgy website, there is no way anyone can do anything to your system (unless you are misfortunate enough to be the victim of an unpatched security exploit).

---

### Post by julio_cortez on 2010-08-17
> **Penguin Guy said:**
> no passwords
> **Penguin Guy said:**
> there is no way anyone can do anything to your  system.
Let someone untrusted enter your room when you're away and you'll see :lolflag:

---

### Post by Penguin Guy on 2010-08-17
> **julio_cortez said:**
> 
[QUOTE=Penguin Guy;9729484]no passwords
> **Penguin Guy said:**
> there is no way anyone can do anything to your system.
Let someone untrusted enter your room when you're away and you'll see :lolflag:[/QUOTE]
A password won't help if someone has access to the physical computer. I would recommend a password for laptops though.

---

### Post by julio_cortez on 2010-08-17
I know what you mean, I was joking..
This happened to my cousin's laptop once my uncle got hold of it, that's why I posted it :D

At least passwords leave my relatives away from administrative accounts (*and yes, most of my relatives **ARE** untrusted when it comes to using a PC*) :P

---

### Post by regala on 2010-08-17
> **Rubi1200 said:**
> interesting stuff

There misses a choice: I install Debian :)

---

### Post by Penguin Guy on 2010-08-17
> **julio_cortez said:**
> I know what you mean, I was joking..
This happened to my cousin's laptop once my uncle got hold of it, that's why I posted it :D
Depends what kind of *content* is on the computer :P

---

### Post by julio_cortez on 2010-08-17
No compromising content, really.
But giving them administrative accounts is like telling them "come on, this PC is yours to destroy" :D

---

