---
title: "Directory Permissions/Security Question . . ."
date: 2014-01-10
forum: Security
---

### Post by BuntuSeriously on 2014-01-10
Greetings!

Just a simple question for the community today ;o)

Being moderately concerned with security on my trusty laptop, I was wondering what a 'net-side attack would look like to get at files on a common-access directory such as Documents or Desktop (unencrypted drive; typical install with a good PW).

In short, apart from someone rambling through the relevant folders while physically sitting at the system itself, is it much of a trick for some clown (or worse) to rummage about on a properly firewalled and updated 'buntu from the net these days?  What's the latest thinking here???

Thanks again, and Cheers!

---

### Post by TheFu on 2014-01-11
There are thousands of different attack vectors, so it is impossible to explain them here, even if I knew them all.
If you block all inbound requestes with a software firewall AND a hardware firewall and don't have any servers listening (like sshd or apache or ... ), then your risks become like a typical desktop user of any other OS.  Email and web-based attacks.

From javascript, it is amazing what can be accomplished inside a LAN.

If you use IM, skype, remote desktop services (even commercial ones), that opens a different method of attack. Basically, every networked program running on your system is a possible attack vector.

There are almost always kernel attacks too. Fortunately, most are uncovered and get patched, but there is always a small window where the attack could be effective. Bad guys are constantly looking for ways to get around existing protections. A tiny programming error in any of the OS firewall or networked apps is all that is needed.

With physical access, everything is available on any computer, unless it is powered off AND uses strong encryption PROPERLY setup.  There are successful attacks against encrypted disks if they are improperly configured. Hard to believe, but true.

There are always new attacks. Just a few weeks ago, the ad network used by Yahoo! was putting out cross-platform viruses.

---

### Post by BuntuSeriously on 2014-01-11
@TheFu:

Thanks for the input.

You got me a'wonderin' when you mentioned this:

> Basically, every networked program running on your system is a possible attack vector.

So, how might this relate to OpenVPN? We don't seem to be able to get hold of the latest version in the repos: Heard much concern via this route???

Lovin' 12.04 ;o)

---

### Post by TheFu on 2014-01-11
Out of every program running on my systems ... ubuntu, ssh, nginx, firefox, thunderbird, and others, the one that I have the absolute least concern about is openvpn. I'm more worried that the NSA was able to get ssh modified and that Ubuntu itself has issues.

OpenVPN is written by security professionals for 1 purpose.  They aren't likely to make bonehead mistakes like the Firefox, Pidgin, Growl, Debian and Ubuntu teams might.  I'm not saying anyone is incompetent, just that the more complex any code, program, library is, then it requires an extra level a discipline to ensure there aren't any mistakes.  I KNOW about writing nearly bug-free code. Wrote man-rated GN&C software for space vehicles. Our project had very few bugs - fewer than 1 every 2 years were uncovered when I left that position and there were over 20 full-time people coding at the time. Quality and meeting requirements were the most important things.  Every decision, every day was about making the code follow the requirements. I've never seen or heard of any other software shop like that ever since.

Still - the openvpn guys have my trust.

---

### Post by BuntuSeriously on 2014-01-12
@TheFu:

> I'm more worried that the NSA was able to get ssh modified and that Ubuntu itself has issues.

Oh, you had to bring up the "N" word...

{shiver}

With so much current criticism of emergency unemployment and its costs to the American taxpayer, has anyone ever stopped to consider where an entity such as this finds the breathtaking level of funding necessary to support its "[mission?]("http://www.nytimes.com/1983/03/27/magazine/the-silent-power-of-the-nsa.html")"   Does the term "wholesale printing" ring any bells in this context???

But I digress...

In any event, OpenVPN is quite a blessing for many of us out here in an age of strange adversaries.  And, let's all hope the Ubuntu projects continue to draw upon a generally-safe organizational core for those of us who seek to keep some of our everyday affairs truly our own ;o)


Thanks again & have a great week --

---

