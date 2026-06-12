---
title: "Is Ubuntu naturally a low resource demanding OS?"
date: 2009-09-02
forum: The Cafe
---

### Post by techno-atom on 2009-09-02
I'm just curious because I am using a Netbook and my upgrades are very limited. I can run Ubuntu 9.04 perfectly fine and it runs smoothly. Has Ubuntu always been pretty reasonable with the specs it requires? I'm not sure how frequently new versions of this OS are released but should I be fine as far as future releases go? I have the latest version of the Acer Aspire One Netbook that launched earlier this year.

---

### Post by steeleyuk on 2009-09-02
Ubuntu releases every 6 months in April and October. There are LTS releases which are made every two years (8.04 being the latest).

Ubuntu is relatively low specification compared to today's hardware standards but GNOME (the desktop environment it uses) is certainly not lightweight compared to others out there. XFCE, for example is popular and requires fewer resources than GNOME. You can go even lighter than that and use something like LXDE or IceWM.

All in all, you should be fine with Ubuntu but there are many other choices out there. I've been using Ubuntu for close to three years and the resource usage hasn't changed that much.

---

### Post by Cato2 on 2009-09-02
I've run Ubuntu quite happily in 512 MB RAM on an old Pentium III, so a modern netbook is just fine.  It runs really fast in 1 GB, I set up a PC like this recently.

If you want a super-low resource using variant of Ubuntu, try Crunchbang or Lubuntu (just released so perhaps a bit bleeding edge) - can work in 200 MB or less.  These are for more experienced users so maybe just use Ubuntu for a while first.

The LTS releases are supported for 3 years on the desktop/laptop - so Ubuntu 8.04 aka Hardy will work until 2011. However, netbooks/laptops often need a more recent Ubuntu release, so you might want to use 9.04 which will be supported until about Oct 2010 (18 months from release in Apr 09).

Future releases will be fine - Ubuntu is actually getting faster to boot in most recent releases, and generally it's incredibly customisable so you can always strip out things that you don't want.

---

### Post by aysiu on 2009-09-02
"Reasonable" is kind of a vague term in this context.

*I* think Ubuntu is reasonable... but someone with only 128 MB of RAM may think it sluggish... or someone with a really tweaked out Arch Linux or Slackware installation may also find Ubuntu sluggish.

I use it on a 1.6 GHz Intel Atom processor with 2 GB of RAM on my HP Mini, and it works just fine, even with Compiz running. Very smooth.

---

### Post by snowpine on 2009-09-02
Hi Techno-Atom, here are the system requirements for Ubuntu:

> Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution
    * Sound card
    * A network or Internet connection 

Note: All 64-bit (x86-64) PCs should be able to run Ubuntu. Use the 64-bit installation CD for a 64-bit-optimised installation.

Recommended for visual effects

Visual effects provide various special graphical effects for your desktop to make it look and feel more fun and easier to use. If your computer is not powerful enough to run visual effects, you can turn them off and will still have a usable Ubuntu desktop.

Visual effects are turned on by default if you have a graphics card which is supported. For information on supported graphics cards, see DesktopEffects.

    * 1.2 GHz x86 processor
    * 384 MB of system memory (RAM)
    * Supported graphics card (see DesktopEffects) 

The requirements have not changed much in the 2 years I've been using Ubuntu.

Ubuntu is generally regarded as one of the "heavier" Linux distributions, however in my (limited) experience, it is fairly efficient compared with, for example, Microsoft Windows Vista.

To answer your specific question, I believe that Ubuntu will continue to support netbooks like your Acer for quite some time (at least 3 more years, probably more).

---

### Post by blueturtl on 2009-09-02
> Is Ubuntu naturally a low resource demanding OS?

Consider that Ubuntu and other open Linux based operating systems are generally forged to meet the needs of consumers or users. It is in the interest of some users to be able to run modern day software on hardware that is not necessarily the most up-to-date. When this is possible to achieve, it generally is.

Ubuntu is packaged to run on systems that are fairly robust to offer a rich end-user experience, but due to it's modular nature can be customized to run on a fraction of it's official system requirements.

Certain commercial *ahem* software products on the other hand are specifically made to sell hardware. Bigger software requires bigger hardware, catch my drift? :) Might explain why so few of the big hardware vendors push Linux for desktop end-users. With Linux, a user might hold on to what they've got up to ten years, if not more! Right now it seems, people want new hardware every two or three years which is very lucrative if you're in the hardware business.

---

### Post by Viva on 2009-09-02
I've run ubuntu on 256mb ram without any noticeable slowness before/

---

### Post by juancarlospaco on 2009-09-02
Yes, 
...and get faster and faster when possible

[IMG]http://ubuntulife.files.wordpress.com/2009/05/testsqlite.png[/IMG]

:)

---

### Post by Cato2 on 2009-09-02
> **aysiu said:**
> "Reasonable" is kind of a vague term in this context.

*I* think Ubuntu is reasonable... but someone with only 128 MB of RAM may think it sluggish... or someone with a really tweaked out Arch Linux or Slackware installation may also find Ubuntu sluggish.

I use it on a 1.6 GHz Intel Atom processor with 2 GB of RAM on my HP Mini, and it works just fine, even with Compiz running. Very smooth.

You can use Ubuntu fine in 128MB, but you must run something like LXDE or Openbox, not GNOME/KDE/XFCE (Xubuntu).  For a small server, 128 MB is also fine, just use the CLI only.

Also, google for 'distrowatch minimal xubuntu' for a great guide on a stripped down XFCE based Ubuntu - very easy to follow.

---

### Post by Tristam Green on 2009-09-02
Ubuntu 9.04 runs really well on my AspireOne D150, as does KDE 4.3.

Issues I've had:

- WEP Authentication fails in KDE (I don't know the nature of this issue, I haven't really begun to sort it out.  Nor do I really want to)
- Battery life is horrid out of the box.  I get 6-6.5 hours on a 6-cell batt in Windows 7 Professional, and I get around 3-4 hours on the same battery in *buntu.
- I haven't loaded the "cooked" kernel for the AspireOne, but really, I don't know that I want to lol.

---

### Post by hessiess on 2009-09-02
Linux is extremely modular, it can be as light or as heavy as you want depending on what modules (applications) are used.

> **Tristam Green said:**
> - WEP Authentication fails in KDE (I don't know the nature of this issue, I haven't really begun to sort it out.  Nor do I really want to)


DONT USE WEP! it is extremely easy to crack and is basically the same as having no encryption at all!.

---

### Post by aysiu on 2009-09-02
> **hessiess said:**
> Linux is extremely modular, it can be as light or as heavy as you want depending on what modules (applications) are used.



DONT USE WEP! it is extremely easy to crack and is basically the same as having no encryption at all!.
It is extremely easy to crack for those who have cracking software and know how to use it, but I wouldn't say it's "basically the same" as no encryption.

WEP at least keeps *most* freeloaders off your network. It is not secure, though, and you should not use it for sensitive online transactios.

---

### Post by t0p on 2009-09-02
I've got an EeePC 701, with 512MB of RAM.  I'm using Eeebuntu 9.04 on it at the moment, and it performs okay-ish.  A little sluggish.  But I intend to upgrade RAM to 2GB soon, and expect it to fly.

I also own a Pentium 4 desktop machine with 256MB RAM.  I use Hardy with XFCE on it, but I'm also using some Gnome apps like Firefox.  As a result it can be *very* slow.  Soon I shall replace Hardy with something newer (probably Karmic) and I may go for a truly lightweight desktop like LXDE.  I'm also going to upgrade this machine's RAM.  But Crucial.com says it can only take 512MB of RAM maximum, so I don't know what it'll be like.

Ubuntu is *not* a particularly lightweight Linux distro.  But it's far less bloated than Vista/XP/OSX.

---

### Post by t0p on 2009-09-02
> **aysiu said:**
> 
WEP at least keeps *most* freeloaders off your network..

I don't seewhy you think that.  If I was looking at my neighbourhood networks for something to piggyback on, and I saw no open networks  and 1 wep-"protected" network, I'd fire up Backtrack, crack the wep key and get me some free internet.  I mean, why not? Wep is so trivial to crack now, it may as well be open. Of course I'd go for an actual open network rather than a wep access point.  But open APs are very rare now.  In fact, wep's pretty rare too.  Wpa/wpa2 is most common now.  It seems the message has finally got through.

---

### Post by aysiu on 2009-09-02
> **t0p said:**
> I don't seewhy you think that.  If I was looking at my neighbourhood networks for something to piggyback on, and I saw no open networks  and 1 wep-"protected" network, I'd fire up Backtrack, crack the wep key and get me some free internet.  I mean, why not? Wep is so trivial to crack now, it may as well be open.
I said it keeps *most* freeloaders off your network.

Most freeloaders do not know how to fire up Backtrack to crack the WEP key. I'm not saying WEP crackers are rare. I'm just saying they do not constitute the majority of wireless network freeloaders.

> Of course I'd go for an actual open network rather than a wep access point. And in my neighborhood, there *are* plenty of totally unsecured networks. So if you are looking to freeload (and don't have the savvy to research how to crack WEP keys), the unsecured networks are far easier to freeload off of than the WEP-"secured" networks.

> But open APs are very rare now. In fact, wep's pretty rare too. Wpa/wpa2 is most common now. It seems the message has finally got through. Maybe where you live. Not where I live. Plenty of people in my neighborhood have totally unsecured or only WEP-"secured" networks.

---

### Post by t0p on 2009-09-02
> **aysiu said:**
>  Plenty of people in my neighborhood have totally unsecured or only WEP-"secured" networks.

My word.  That's.... ridiculous.

And of course you're right.  If I was in your neighbourhood and wanted to freeload, I'd use the open networks before the wep-"protected" ones.  My comments were based on what I see where I live - very few open APs, occasional wep-encrypted APs.

So my neighbours are more security-conscious than yours.  I'm surprised, as I don't live in an area full of IT "experts".  Then again, maybe I do.  Crazy.

Oh, I do hope no one's gotten the impression that I go around using other folks' internet connections.  It's something I *have* done, when I was learning about wireless "security".  I'd do it if I really needed to get online and had no legitimate access of my own.  But I've nearly always got my 3G modem or my cellphone with me nowadays.  No, I talk about it because it *is* pretty trivial to beat wep, and I know plenty of people who know how to do it.  It is easy to download Backtrack and to read the [Remote Exploit forums]("http://forums.remote-exploit.org").  But like you say, who needs to learn how to do that when there are completely unprotected APs out there?

I remember having a conversation with a guy who thought his wireless AP was secure because he filtered for mac addresses.  He was shocked when I told him just how easy it is to change your equipment's mac numbers to match his authorized numbers.  I really ought to remember that his ignorance isn't that unusual.

---

### Post by aysiu on 2009-09-02
> **t0p said:**
> 
I remember having a conversation with a guy who thought his wireless AP was secure because he filtered for mac addresses.  He was shocked when I told him just how easy it is to change your equipment's mac numbers to match his authorized numbers.  I really ought to remember that his ignorance isn't that unusual. A lot of people also thinking hiding your ESSID makes it secure. Lotta ignorance out there.

---

### Post by lykwydchykyn on 2009-09-02
> **t0p said:**
> 
I remember having a conversation with a guy who thought his wireless AP was secure because he filtered for mac addresses.  He was shocked when I told him just how easy it is to change your equipment's mac numbers to match his authorized numbers.  I really ought to remember that his ignorance isn't that unusual.

To be fair, you'd actually have to KNOW one of those numbers to make use of that, but I suppose a bit of sniffing might turn one up.

---

### Post by heyyy on 2009-09-02
> **t0p said:**
> My word.  That's.... ridiculous.

And of course you're right.  If I was in your neighbourhood and wanted to freeload, I'd use the open networks before the wep-"protected" ones.  My comments were based on what I see where I live - very few open APs, occasional wep-encrypted APs.

So my neighbours are more security-conscious than yours.  I'm surprised, as I don't live in an area full of IT "experts".  Then again, maybe I do.  Crazy.

Oh, I do hope no one's gotten the impression that I go around using other folks' internet connections.  It's something I *have* done, when I was learning about wireless "security".  I'd do it if I really needed to get online and had no legitimate access of my own.  But I've nearly always got my 3G modem or my cellphone with me nowadays.  No, I talk about it because it *is* pretty trivial to beat wep, and I know plenty of people who know how to do it.  It is easy to download Backtrack and to read the [Remote Exploit forums]("http://forums.remote-exploit.org").  But like you say, who needs to learn how to do that when there are completely unprotected APs out there?

I remember having a conversation with a guy who thought his wireless AP was secure because he filtered for mac addresses.  He was shocked when I told him just how easy it is to change your equipment's mac numbers to match his authorized numbers.  I really ought to remember that his ignorance isn't that unusual.

this might be a bit out of the topic but
speaking of wireless security if i "hide" my wifi would that be any good?
also could you recommend me a link or two to set up my wireless properly(securely)?

---

### Post by hessiess on 2009-09-02
> **heyyy said:**
> this might be a bit out of the topic but
speaking of wireless security if i "hide" my wifi would that be any good?
also could you recommend me a link or two to set up my wireless properly(securely)

Just use WPA with a super-random password like the ones generated by [https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm).

---

### Post by t0p on 2009-09-02
> **lykwydchykyn said:**
> To be fair, you'd actually have to KNOW one of those numbers to make use of that, but I suppose a bit of sniffing might turn one up.

**Airodump-ng** (one of the **Aircrack-ng** suite of tools, included in Backtrack) shows the mac addresses of wireless access points and of clients associated with those access points.  So you can see the mac addresses of any clients connected to the access point in question.  Then you can use **macchanger** to make your wireless card spoof the mac of the client you wish to impersonate. Or **ifconfig** can do this too.

If you want to know more, go check out the [Remote Exploit Forums]("http://forums.remote-exploit.org").  Plenty of guides on how to use the various tools included in Backtrack.  Though of course you should only use these tools to test the security of your own system.  It is utterly wrong to crack someone's network without permission.

---

### Post by t0p on 2009-09-02
> **hessiess said:**
> Just use WPA with a super-random password like the ones generated by [https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm).

**WPA2** is better than WPA. A vulnerability has been discovered in WPA's security protocol, TKIP.  WPA2 uses CCMP, which is a more robust protocol.  Google "WPA2" for more info.

---

### Post by hessiess on 2009-09-02
> **t0p said:**
> **WPA2** is better than WPA. A vulnerability has been discovered in WPA's security protocol, TKIP.  WPA2 uses CCMP, which is a more robust protocol.  Google "WPA2" for more info.

I know, but a lot of older routers cannot support WPA2, as its based on AES instead of RC4 like WEP and WPA. AES is a more computationally intensive algorithm so needs stronger hardwere, whereas WPA is normally just a firmware update.

From my understanding the vonribility in WPA just alows someone to capture network traffic and then preform an off-line brute force attack on it, in which case using a maximum entropy password WPA is still secure, unless you have a few billion years to spare.

---

### Post by Tristam Green on 2009-09-03
Because I **totally** asked for a lecture on how to secure my wireless that I've been managing to keep people off of for....seven years?

---

### Post by Cato2 on 2009-09-04
> **Tristam Green said:**
> Because I **totally** asked for a lecture on how to secure my wireless that I've been managing to keep people off of for....seven years?

WPA plus TKIP has been cracked completely, quite recently - in 60 seconds, anyone with the right tools can walk up to your wireless network and break TKIP.  Basically WPA+TKIP is now like WEP, providing only trivial protection against the average WiFi freeloader, not against someone with suitable tools.

Just because nobody has broken into your network doesn't mean nobody will, though the risk is a bit lower using WPA+TKIP than using no encryption.

---

### Post by Martje_001 on 2009-09-04
> **juancarlospaco said:**
> Yes, 
...and get faster and faster when possible

[IMG]http://ubuntulife.files.wordpress.com/2009/05/testsqlite.png[/IMG]

:)
Also show the tests where it's getting slower! ;)

---

### Post by binbash on 2009-09-04
PcLinuxOS, debian, fedora,gentoo *place most distros here* use less resource then Ubuntu. I have never saw my cpu usage goes under %10, even with Openbox but on debian or pclinuxos i am using max %1.

---

### Post by hessiess on 2009-09-04
> **Cato2 said:**
> WPA plus TKIP has been cracked completely, quite recently - in 60 seconds, anyone with the right tools can walk up to your wireless network and break TKIP.  Basically WPA+TKIP is now like WEP, providing only trivial protection against the average WiFi freeloader, not against someone with suitable tools.

Just because nobody has broken into your network doesn't mean nobody will, though the risk is a bit lower using WPA+TKIP than using no encryption.

More info on the WPA/TKIP hack, the recent hack requires a man in the middle attack where the origonal user connecting to the network is actually OUT OF RANGE of the wireless router. more info in Sccurity now ep 212 [http://www.twit.tv/sn212](http://www.twit.tv/sn212). It is not a problem as it does not alow the encryption key to be obtained and is only possable on ARP packets, howeaver you should use AES encryption if possable.

---

### Post by Hallvor on 2009-09-04
Ubuntu is probably the heaviest there is, but I`d say both variants of PCLinuxOS (KDE and Gnome edition) are not only lighter, but also easier to use.

---

### Post by nothingspecial on 2009-09-04
> **Hallvor said:**
> Ubuntu is probably the heaviest there is, but I`d say both variants of PCLinuxOS (KDE and Gnome edition) are not only lighter, but also easier to use.

I`d say sabayon is heavier. But it`s all irrelevant really. You can make Arch as bloated as you like and Ubuntu as light as you want. 

You say in your title "naturally". Then yes Ubuntu, when the full version is first installed, is quite heavy. It includes alot of stuff you may not need preconfigured but that`s kind of the point.

But this is linux, do with it what you will. That really is the point.

---

