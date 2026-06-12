---
title: "Keeping Your Privacy Private"
date: 2005-04-24
forum: The Cafe
---

### Post by beeldings on 2005-04-24
One of the main reasons why I switched from Windows to Linux was due to a growing number of concerns about my privacy and malicious software. I have always been very cautious about who I give my personal information out to and what accounts I have opened with on-line merchants. While I strive to do whatever it takes to properly secure my PC and change my passwords every few months, I decided to make a new thread so the Ubuntu Community can share their tips and tricks for protecting their Linux machines and their privacy. I would now like to share with you what I've done to protect my PC and my privacy.

I have my Internet connection wired through a Linksys router which then connects to a hub, and from there the correct connection is made. On the software side of things, I have Firestarter installed with ICMP filtering enabled along with a number of outgoing ports blocked. I use Firefox with Adblock and the latest version of filters, as well as a hefty 1MB hosts file. Javascript is almost entirely blocked, I do need it to access my free web-based e-mail accounts. I only accept cookies from the web sites I shop at, everything else is blocked.

For e-mail my family and I use Thunderbird with HTML and remote images disabled. I am considering setting up PGP for the family e-mail account, but my main concern with using PGP on the family account is that most of the people we contact don't have PGP or don't know what PGP is (besides the fact that they use Windows), and it would be a lot of time and effort to convince them to use PGP.

About every two to three months, I use a [random password-generator](http://www.msdservices.com/apg/index.php) to create new passwords for my accounts. My primary focus is on my bank account password. While I don't conduct any actual banking (i.e transfer funds or pay bills), I use my bank's web access feature to check my account statements and make various service inquiries. When I do access my bank account on-line, I always make sure to clear out the cache and any existing cookes and log-on to the account in a new browser window. When I log out of my account, I clear everything, and then shut down the browser.

As a personal rule, I do not store any sensitive information on my computer. Any files containing private information are copied to CDs, which I store in a safe, and then I delete the file from the hard drive.

I would consider myself to have a secure setup in terms of hardware and software-based solutions for my PC. However, I do have some concerns that I would like to share with the Community:

My number one concern is general web browsing. While I have taken steps to protect the integrity of my privacy, I feel as though I should take an additional step and use a proxy for HTTP access, not HTTPS access. However, I cannot seem to locate information regarding a trustworthy, free HTTP web proxy. Does anyone know of a solution?

My next problem is that I would like to further lock-down my PC. I have Firerstarter and the firewall in my Linksys router, but I'm not confident that they are truly securing my PC. I have recently started to enter all entries from the "Events" section in Firestarter into my hosts.deny file, and I have ALL:ALL and ALL:PARANOID in that file as well. What else should I install or configure in order to properly secure my PC? I would like to be able to freely access the Internet while keeping intruders out. Scans of my PC at GRC.com reveal that my machine passes the stealth portion of the tests, but I don't want to be lured into a false sense of security.

Finally, I would like to know if it is possible to encrypt the contents of my hard drive, and if and when I get rid of my PC or decide to sell my hard drive, I would like to know if there are any programs for Linux that would allow me to securely wipe all data from the drive so that it could not be recovered.

People tell me I'm a little too paranoid when it comes to this sort of thing, but my I believe that it's better to be safe and paranoid than a victim of ID theft and sorry.

---

### Post by sas on 2005-04-24
Wrap your computer in tin foil....that'll stop them reading the magnetic field around your hard drive. 


I don't believe there is a trustworthy free http proxy....after all you don't know what they log and can't take their word for it.....

Uhm, have you checked out SELinux? or Ubuntu hardened?

---

### Post by beeldings on 2005-04-24
"Uhm, have you checked out SELinux? or Ubuntu hardened?"

I actually wasn't aware that such a version of Ubuntu existed. I heard of SELinux when I used Fedora Core 2, but back then I was new to Linux and didn't know what that was about. Thank you for bringing this to my attention, I'll check out Google for some more information.

---

### Post by TravisNewman on 2005-04-24
Well, I DO find that a bit paranoid, but I would like some info about some of the things you've spoken of. Especially HTTP proxies. I'd love to know the most reliable and trustworthy free HTTP proxy.

Other than that, it seems like you've got your computer pretty well locked down. You might look into hardened kernels and SE Linux, though neither are officially supported in Ubuntu.

Literally, the ONLY way to ensure that nothing will ever get hacked, is to first unplug the network cable from your pc, two, turn off the computer, and three, destroy the computer, and melt the platters of the hard drive. There's always going to be SOMEONE out there smarter than the people who made the security software.

But while I wouldn't go to the extent you have, I understand your concern, and would love to see your hosts file, if it isn't restrictive. Do you ever have trouble with legitimate content?

---

### Post by beeldings on 2005-04-24
> "But while I wouldn't go to the extent you have, I understand your concern, and would love to see your hosts file, if it isn't restrictive. Do you ever have trouble with legitimate content?"

The problem with my hosts file is that I've appended hosts files I've found through Google to my file, so that leads to the problem of double or even triple entries. I've been meaning to go through the file and clean it up, but doing so would take forever. I used a program called Hostess under Windows, but it doesn't work too well with Wine.

As for problems with legitimate content, if by that you mean "mainstream" web sites, then yes, some legitimate content is blocked. I know for a fact that if you were to use my hosts file, you would have problems with Yahoo or any site that uses Akamai Technologies to link images and the like. I also know that most, if not all Microsoft content is blocked, including Hotmail. A lot of the entries in my hosts file were posted in order to block malicious web content including cookies from data harvesters like DoubleClick and web bugs (those 1x1 transparent images). If you're a member of eBay and PayPal, all of their content has been blocked.

If you would like to see my file, I can send it to you. Be prepared to load it up in nano in case it blocks your favorite web sites. My filters for Adblock are almost identical to the ones referenced in a thread on the forums regarding tweaking Firefox, with the main exceptions being that I blocked all eBay, PayPal, and Akamai content.

---

### Post by TravisNewman on 2005-04-24
well, I'd rather not have to go through and edit it so that I can use hotmail, ebay, and paypal ;) I may try to find an established hosts file on the net later that doesn't block non-advertising/malicious websites. But I do admire your diligence!

---

### Post by AdamZ on 2005-04-25
For wiping your hard drive, there are a couple of [boot disks](http://dban.sourceforge.net/) you can use. There are others on the web.

There's an [interesting paper](http://www.cypherpunks.ca/otr/otr-wpes.pdf) on why you shouldn't use PGP for everyday communications. For IM, [OTR](http://www.cypherpunks.ca/otr/) gives better privacy properties (good luck getting anyone to use it though). There's nothing like it for email yet, unfortunately.

---

### Post by az on 2005-04-25
Are you asking for something like this?

[http://packages.ubuntu.com/hoary/web/anon-proxy](http://packages.ubuntu.com/hoary/web/anon-proxy)


Although I think that you are going to be a victim of a lot of bad jokes because of the extent to which you take security seriously, I commend you for your hard work in securing your computer system.

---

### Post by TravisNewman on 2005-04-25
"The encrypted messages are sent through a chain of intermediate servers (named Mixes) to the final destination on the Internet."

Is there any way to know where these Mixes are, who runs them, etc? Or is is just random?

That would be nice to know, though as the description put it, the mix chain would have to be totally corrupt in order to read your information, so one corrupt Mix can't compromise the process.

---

### Post by crmanski on 2005-04-25
For my own home system I use an old PC with two nics and run smoothwall on it ([www.smoothwall.org](www.smoothwall.org)).  This comes with an integrated squid proxy install which is easily to setup transparently.  For increasing privacy I run privoxy ([www.privoxy.org](www.privoxy.org)) in front of the squid proxy.  It does an excellent job of removing scripts, webbugs, etc. I use the switchproxy firefox extension to switch this off easily if needed (when shopping, etc).

---

### Post by beeldings on 2005-04-25
crmanski,

I have plans to turn my current PC into a firewall router once I purchase a new PC. The only problem is that while I take computer security and general privacy issues very seriously and know a great deal on these subjects, I have no real world experience in true computer networking. My current "network" is the Linksys router feeding my Internet connection to my PC and then again to my PS2 via port-forwarding. That's the extent of my networking experience.

On that note, can anyone recommend a good book or two on Linux networking for someone with limited experience?

---

### Post by philipacamaniac on 2005-04-25
Just a quick question, beeldings - do you forward any ports from your Linksys router to anywhere internally on your network?

Because if not, there is no need for any concern. Your router uses NAT (network address translation), and if you have not opened any ports for access, it is practically invisible from the Internet. If this was the case, there isn't even a need for using IPTables (firestarter) on the PC. A hacker has to have an in - and if you haven't provided any in, there is nothing more you can do to lock down the network. At that point, you should be more concerned with physical security.

If you do forward ports, then only those ports are accessible. For example, I have SSH (port 22) open on my router, and it is forwarded to my Linux box. The only possible in for a hacker is through that open SSH port. And since I require a specific certificate to connect to my machine, and I use a very long password with letters, numbers and symbols, I believe I am as safe as I need to be.

What is the reason for wanting to turn your current PC into a firewall/router? Unless maybe you are looking to somehow get more performance than the Linksys...

---

### Post by az on 2005-04-25
[QUOTE=beeldings]crmanski,

I have plans to turn my current PC into a firewall router once I purchase a new PC. The only problem is that while I take computer security and general privacy issues very seriously and know a great deal on these subjects, I have no real world experience in true computer networking. My current "network" is the Linksys router feeding my Internet connection to my PC and then again to my PS2 via port-forwarding. That's the extent of my networking experience.

On that note, can anyone recommend a good book or two on Linux networking for someone with limited experience?[/QUOTE]

[www.aboutdebian.com](www.aboutdebian.com)

Look in the networking page.

Install shorewall and shorewall-doc.  The firewall documentation is excellent.

I guess anon-proxy did not turn your crank?

---

### Post by beeldings on 2005-04-26
[QUOTE=philipacamaniac]Just a quick question, beeldings - do you forward any ports from your Linksys router to anywhere internally on your network?[/QUOTE]

I have TCP ports 10070-10080 and UDP port 10070 forwarded to my Playstation 2 for on-line gaming. I am pretty certain that I do not have anything being forwarded to my PC>

---

### Post by beeldings on 2005-04-27
[Security for the Paranoid](http://it.slashdot.org/article.pl?sid=05/04/27/1721238&from=rss)

And I thought I was paranoid...

---

### Post by TravisNewman on 2005-04-27
Ha-- well, he has more reason to be more and more paranoid than you. He still uses Windows.

---

### Post by beeldings on 2005-04-29
```
netstat -na
```
I just ran this command and it lists a lot of open ports and associated details. Most of the programs connected to the network or posted as "Listening" are in /tmp/orbit-username/ and /tmp/.X11-unix/. I'm sure that this is nothing to lose sleep over, but should I be concerned about this?

--------------------------------------------------

As I first posted in this thread, I would also like to share some tips and tricks to help one protect their privacy/identity. For those of you not familiar with [Junkbusters](http://www.junkbusters.com), I suggest that you give it a quick look. It's very informative and provides links to help one opt-out of pre-approved credit card or insurance offers, as well as information on removing your name from telemarketing lists and direct marketing lists.

Another recommended site is the [Privacy Rights Clearinghouse](http://www.privacyrights.org/). It deals with some of the same topics as Junkbusters, but it does offer additional advice on educational and medical privacy.

Both sites are worth a look, highly informative, and regularly updated. However, most of the content deals with privacy issues in the United States, so I really don't know how this information will hold up in the rest of the world.

On another note, has anyone here ever used one of those "free" credit report web sites? I've checked some of them out, but I'm not comfortable providing my sensitive information like my Social Security number over the Internet. If anyone has any experience with credit reports in general, please share it if you wouldn't mind.

---

