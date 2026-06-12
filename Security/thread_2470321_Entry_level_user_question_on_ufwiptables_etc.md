---
title: "Entry level user question on ufw/iptables etc"
date: 2021-12-25
forum: Security
---

### Post by westernswing70 on 2021-12-25
Hello!

This question is similar to a few others posted here before, but I feel the previous ones got some conflicting answers.

Background: I'm new to Ubuntu (20.04) and wanted to try it on my X240 for a simple portable alternative for surfing, banking and text editing. I've been very happy with it thus far, but recently I discovered that I've unknowingly been surfing without being behind a router firewall (I was an idiot in trusting the previous home owners connection). Also, I had not activated ufw (thinking it'd be activated by default). 

So the question is: Could my machine have been compromised as a result of my ignorance? I have only ever used it for email and banking on firefox, nothing extra installed except for gufw and no settings changed since install.

And on to my follow up question: Is ubuntu safe "out of the box"? Some forum users (on here and elsewhere) say "no ports are open" by default (whatever that means), others say that since ufw is just the frontend iptables are still active. Yet others second this, but add that since there are no rules set up all ports will accept all traffic by default. Am I to understand that this means going online on ubuntu vanilla with no router firewall is to expose one's internet traffic?

Thank you for reading, and feel free to call me a total n00b for making these easily avoidable mistakes.

---

### Post by DuckHook on 2021-12-26
Welcome to the forums, westernswing70

There's a lot to unpack in your queries:

Ubuntu does not have any open ports in its default configuration. So, if you installed Ubuntu from Canonical's ISO and didn't change anything, then you will not have been exposed through open ports. Open ports are the reason that we old&#8209;timers recommend UFW. An explanation of ports and their uses would be too much for this thread, but in a nutshell: ports are the "openings" in your operating system that allow unrequested packets from the outside to reach your computer. For example, if you were running a web server, you would need to open ports 80 and 443 to allow web queries from outside to reach you. Otherwise, your web server would remain isolated within your computer and never receive requests from the outside world, thus negating its purpose as a web server.

Almost all servers must open up ports in your OS in order to work. E-mail servers use a bunch of ports. File servers like NFS servers open up their own unique ports. SSH opens up the well&#8209;known port 22. On it goes.

A default Ubuntu desktop environment installs no servers. This is why we say that no ports are open by default. However, this state of affairs is not exactly secure. Since no specific rule is in place *prohibiting* the opening of a port, it is possible for a rogue script (say, on a bad website) to request such a port opening. The installation of UFW will specifically prohibit all port openings, changing the all&#8209;ports&#8209;closed feature of Ubuntu from a default behaviour into an enforced behaviour (a subtle but vital difference). With UFW active and properly configured, even a rogue script could not force a port open. Thus, it acts as another layer of protection for you.

Although you have restricted your usage to your browser, it does represent the single biggest attack surface to the bad guys prowling the Internet.

Your banking site is unlikely to be a threat.

But your e-mail provider is another significant threat vector. Just how much of a threat depends on your e-mail hygiene. I don't use my browser for e-mail; I use a dedicated e-mail client. Most good, modern e-mail clients are sufficiently robust that they filter spam, flag malware and won't autorun scripts or attachments. But accessing email through your web browser requires *you* to do most of that work (unless your email provider already has such algorithms in place).

Your question: "Is ubuntu safe 'out of the box'?"

Let's just go to the plain unvarnished answer: No OS is safe out of the box. Some OSes are better than others at having safer initial default configurations, but these can be quickly compromised through user error, ignorance or laziness. Perhaps a quantization would better illustrate this: Some OSes are an outright zero when it comes to security. But the OS is only 10% of overall security. The other 90% is the user.

So, in the hands of a highly skilled and security conscious user, even an awful OS (0 rating) can achieve high security because the user practices excellent (1) security hygiene. (0 * 10%) + (1 * 90%) = 90% security.

On the other hand the best OS in the world (1) in the hands of a lousy user (0) cannot be secure: (1 * 10%) + (0 * 90%) = 10% security.

I'm contrasting the two most extreme cases to emphasize my point, but you probably get my drift.

> Am I to understand that this means going online on ubuntu vanilla with no router firewall is to expose one's internet traffic?
Exposing your internet traffic has little to do with your firewall. Your firewall prevents bad guys from penetrating your internal LAN and seeing that is going on within your internal network. It does nothing to stop your traffic being snooped once your packets are being shuffled around out in the big wide world of the Internet. The only way to stop that sort of snooping is to encrypt your traffic. This is what the "s" in *https* does and why you must never visit that banking site, for example, without seeing the lock symbol on your browser. It means that SSL encryption is active.

BTW, this is why it is important to have a proper router firewall in place even if Ubuntu has no open ports by default. Without a firewall, an outsider can read what you send to your network printer, your network file server, etc. Your closed ports won't stop that sort of traffic which can be read in the clear. IMO, the only people who should compute without a router (or similar) firewall are über power users who know *exactly* what they are doing (running a honey pot for example).

---

### Post by westernswing70 on 2021-12-26
DuckHook,

Thank you for your thorough answer! This was exactly the kind of information I have been looking for, and I am ever so grateful that you took the time to write it out in "layman's terms". I have only just recently awakened to the more security-focused approach to the digital life, and man is there a lot to learn. Your post above cleared up a whole bunch of questions I've been hoping to find the answer to though, and I feel like I now have a somewhat deeper understanding of the basics.

Since discovering my mistake described above I always keep ufw activated with the basic "block all incoming" setting. I trust my email provider (one of the more security conscious alternatives), although using a dedicated client sounds like a good idea for the future. I have had "https only" mode in firefox activated since day one, and obviously I have since then set up my own network with a basic router firewall. Also, I have never been running any servers, if that wasn't obvious from my cluelessness. :)

After-the-fact, is there any other precautions that I should take before I keep using the laptop? I re-installed Ubuntu after realizing my mistake, but are there any known malwares, bios hacks etc that targets linux users that I hypothetically might've been exposed to during my period of careless surfing?

Again, thank you for taking the time, during the holidays and all!

---

### Post by DuckHook on 2021-12-26
You are already well on your way to being a savvy user who practices good security hygiene. Most users pay too little attention to security whereas you are clearly concerned enough about it to take it seriously and learn more. You are far from clueless.

You mention a "period of careless surfing", but you don't seem to me to be the sort who visits questionable sites or indulges in stupid behaviour (i.e. downloading unvetted third party apps from i.pwn.you.com), but this is bald conjecture on my part—you will have to be the judge of your own behaviour. What I'm trying to say is that, if your definition of "careless surfing" was surfing without UFW activated, then this isn't really a big deal. However, if "careless surfing" means going into questionable sites, then this is a worry, but it would be a problem irrespective of UFW being activated or not.
> **westernswing70 said:**
> …are there any known malwares, bios hacks etc that targets linux users that I hypothetically might've been exposed to during my period of careless surfing?
There are always new threats arising practically daily. However, they take various forms and are not just browser based attacks. If you can address the "careless surfing" question with a high degree of confidence, then you shouldn't be overly worried about exposure to malware during your UFW lapse.

The way to protect yourself from malware, bios hacks, etc is to always keep your system updated. The update process installs the patches needed to close off known holes in both the OS and supported apps. It's people who run End of Life software and OSes who really need to worry. Believe it or not, there are still people running Windows XP in our day and age(!) We periodically get visitors to these forums asking for advice to fix Ubuntu versions that are well past their EoL date and then get defensive when we tell them that they are being foolish.

It's a good habit to periodically check your logs and briefly scan what processes are running on your machine. Granted, these are practices that require a bit of expertise, but the learning curve is not oppressively hard and may even be educational. A bit like appreciating what is going on under the hood of your car.

Last but not least, you need to guard against expecting impossible levels of security. To compute—especially in our modern computing world—is to interact with all that there is out there, an ecosystem that unavoidably contains both good and bad. We cannot fence ourselves off from every possible threat in the computing world any more than we can in real life. We take prudent measures to safeguard ourselves, but thereafter, we have to just get on with it.

I am a strong proponent in taking as many prudent measures as is reasonably possible. The important concept here is "reasonably". We all have different tolerances for how much convenience we are prepared to sacrifice for security, but I know of no one who has limitless tolerance.

There is no end to the security strategies available to harden ones installation. Once you are comfortable with Ubuntu and especially the command line, you may wish to explore these options. One of our resident forum security gurus, TheFu, is a proponent of *firejail*, a sandboxing platform that very effectively confines the browser to an isolated environment. I prefer the containment strategy of LXD (see the link in my sig: *Sandboxing Apps with LXD*). Others use Virtual Machines. There are native Linux processes like AppArmor. All of these tend to be more advanced features and require familiarity with the guts of Linux. There's no hurry in exploring these options and I would recommend that you gain a better understanding of Linux before tackling them.

A good introduction to Linux can be found in the following: [https://linuxjourney.com/](https://linuxjourney.com/)

There is also a wealth of educational info in the link in my sig: *Resources for Newcomers*

If you are feeling really adventurous check out the link in my sig: *A Great CLI Guide*

Good Luck and Happy Ubuntu-ing!

---

### Post by westernswing70 on 2021-12-27
Again, thank you DuckHook.

You are right, I don&#8217;t visit any dubious sites or engage in &#8220;careless surfing&#8221; in any other way. I should have phrased that differently as I was referring to the no ufw/no router situation. I guess I&#8217;ve been pretty conscious about the potential risks one may be exposed to online for quite some time, but the learning curve on how to harden one&#8217;s system has always seemed a bit too steep for me. Since you broke it down to more easily digestible pieces however, I feel like there might be some hope for me after all!

I&#8217;ll take a look at your links.
All the best!

---

