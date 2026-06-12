---
title: "Best pactice examples for designing new Ubuntu infrastructure"
date: 2016-01-18
forum: Server Platforms
---

### Post by Zerrax on 2016-01-18
Best practice examples for designing new Ubuntu infrastructure
 

 Hi, I would like to now, is there besides the “Ubuntu Server Guide” other  
 “Best practices” documentation available?
 So we can learn from each-other experiences, and that the best solutions are documented?
 

 For example I would like to know what is best way implement a complete Ubuntu 14.04 server and desktop (So Ho) infrastructure with the following basic functionalities:
 

 - Local Mail Server (Postfix, Dovecot)
 - LDAP authentication
 - File sharing
 - Backup
 

 I think such a document could help promoting Ubuntu as a total solution for
 small and medium enterprises

---

### Post by TheFu on 2016-01-18
There aren't any specific best practices because Linux is extremely flexible and things that are important in my environment are not important to others.  For example, we will never allow php or java web-apps to face the internet, so that will alter which tools we will allow to be deployed.  Every setup has different items/dependencies like that.  For most Soho people, just using an all-in-one distro that includes these things is probably the "best practice" until they learn enough to be thoroughly scared away from using those distros.  It is all about compromise much of the time. If you don't need to compromise, then the setups will be very different.

Why have a local email server at all? I find that confusing. If setting up email, I'd spend the time to make it an internet email solution and always, always, always have a front-end email gateway to block 95% of the inbound crap-ola.  I'm positive others won't want that email gateway for some reason(s).

Make sense?  Flexibility. "Have it your way." is a core value for Linux admins.  This isn't a one-size-fits-all solution.

File sharing - use NFSv4 with Kerberos - avoid Samba.

Backups - er ... the tools which meet the "best practices" for backups are newer and still have critical bugs if you look through these forums for people asking for recovery help.  OTOH, the tool I like doesn't meet all those "best practices for backups" - rdiff-backup.  I'm shocked that people still bother with tar or dump or pure-rsync for backups. There are better, more efficient, answers today.  Sure, tar can be handy for tiny directory backups that need to be moved via sneaker-net, but certainly folks have moved to better tools for nominal, daily, automatic, backups. I hope so.  Backups that don't provide versioning are a waste - cannot be considered.  If the tool requires the operator to restore more than one backup "set", I consider that a failure too.  The idea of a "weekly full" and a daily incremental is so, so, so, 1980s. Sure, it is PROVEN, but so are the modern tools that are always current with older versions being differentials.  IMHO.

LDAP - how much security do you want?  Is a GUI mandatory for management?  There really isn't a GUI for Ubuntu on any current LTS server.  Do you need 2FA or not?  Certainly, a best practice would include 2FA with hardware tokens, right?  Some people might be willing to use Google Authenticator, but I'm not allowed to use any external services like that without high-level signatures from multiple S-VPs.  Public cloud computing is against our corporate policies, so we block access to most online storage providers, much of google, yahoo, any place where end-users might be tempted to upload photos or other files - BLOCKED.  Is this a best practice for everyone? Doubtful.  Where is the line?

Always run LTS releases, never non-LTS releases.  I'm about to install a 15.10 server because the hardware is too new for 14.04 and has trouble booting.  Attempted 8 installations with 14.04 today - none of them would boot after I was finished.  Just trying to use GPT disks with dm-crypt and LVM ... in a custom configuration.  Ran into a GRUB bug first reported in 2011 that seems nobody has/will ever fix.  Strangely, pulled a HDD from another, different box, and used that - worked. Booted without issues, but the partitioning isn't what we need today, so that isn't really an option.

There is much more to following "Best Practices" that what any document can cover, IMHO.  For example, I disagree with many of Redhat's teachings.  I would NEVER deploy either VNC or plain FTP on any of my networks. Anyone who does should just go back to using telnet. VNC and plain FTP have the exact same issues as telnet and we'd NEVER use telnet, so why are those other protocols ok to deploy? IMHO.

Of course, if you want to find walk-thrus for each of those elements listed above, and begin building a "Best Practices" (using a Wiki would be smart so there is a record of every modification), perhaps folks will contribute?  WikiBooks is where I'd start. [https://en.wikibooks.org/wiki/OpenSSH](https://en.wikibooks.org/wiki/OpenSSH) for example.

I think you'd want a few other items in your "infrastructure list" like 
* remote access - text methods / GUI methods
* VPN - openvpn (that is a project all by itself!)
* DNS - doesn't every home have a DNS server?
* Disaster Recovery! If you can't afford DR, then you can't afford the primary system. PERIOD.
* key management - certainly people have centrally maintained ssh-keys, right?
* DevOps tools and techniques
* Plus every section needs a security discussion.

Today, I'm inclined to deploy a CentOS server to LDAP and either Debian stable or Ubuntu LTS for the others.

So - there are many opinions for almost everything, which makes having a definitive "Best Practice" hard or impossible.  BTW, about 10 yrs ago, I tried to write a book about infrastructure best practices for enterprises. It is hard. Very hard.  IBM has a book and the LISA guys have a whitepaper you can still find for how to setup enterprise infrastructure. Found this from BMC: [https://docs.bmc.com/docs/display/public/tsim10/Best+practices+for+Infrastructure+Management](https://docs.bmc.com/docs/display/public/tsim10/Best+practices+for+Infrastructure+Management) - imagine that, they suggest deploying BMC solutions. ;)

Anyway - some thoughts.

---

### Post by MAFoElffen on 2016-01-18
> **TheFu said:**
> ***[COLOR=#b22222]So - there are many opinions for almost everything, which makes having a definitive "Best Practice" hard or impossible.[/COLOR]***  BTW, about 10 yrs ago, I tried to write a book about infrastructure best practices for enterprises. It is hard. Very hard.  IBM has a book and the LISA guys have a whitepaper you can still find for how to setup enterprise infrastructure. Found this from BMC: [https://docs.bmc.com/docs/display/public/tsim10/Best+practices+for+Infrastructure+Management](https://docs.bmc.com/docs/display/public/tsim10/Best+practices+for+Infrastructure+Management) - imagine that, they suggest deploying BMC solutions. ;)

I think you hit about everything in that post... Well written. Great summary that hit what I was thinking, as I read your post, right on the head of the nail! Funny about your link there in that summary, as I was just reading another vendor's recommendations, and their sub-topic was on "What you need to create your affordable Enterprise Infrastructure." I had to chuckle. I'll leave it at that for now...

---

### Post by Zerrax on 2016-01-19
Thank you very much TheFu for your very extensive answer! it's appreciated very much. your answer was the "best practice" information were I was looking for ;-)

I know that it's difficult to give a simple, short answer on a matter that is so big as designing a complete new server infrastructure, it's almost impossible. 
I agree with you that there are to many decisions have to be made, and that to create a document that claims to be "one size fits all" is almost impossible

But what I was thinking about, those handy, clearly written pdf, mobi, documents like those VMware Guides about installing, configuring their products, to help the customer on his way...
They don't cover everything, they are not perfect, but they give the user a first start, and keep the basic server running, that I was looking for 
but then for installing Ubuntu server with basic tasks.

"Best Practice" for me is making decisions and concessions! based on practical experience from experts (like you) decisions that work in the field, they don't have to be "the way to go" for everybody
but at least they work, they are stable. that was were I was looking for

If such a compact document is not yet available for Ubuntu server, maybe I have to make it myself, and of course share it with everybody
Thanks again for you very informative answer!

---

### Post by TheFu on 2016-01-19
Debian Administration Guides?
Plus there are lots of individual "best practices" out there. However, whenever I read most, I see huge, terrible, issues.  There are some reputable websites with how-to guides, but they only say what to type, not WHY.  The WHY likely is intuitively obvious for someone with a firm, long, detailed, grasp of the OS, but for someone with less than 2-5 yrs experience, it is unlikely to be obvious.  

In short, find a mentor. Work together on things that interest both of you.  In manyshops, the system admins simply know what to type because someone else has created policies and standards to be followed. Sometimes those are brilliant things and sometimes they are not. Comes down to judgment.  For example, where I used to work, we were required to have 5 NICs on every server and to dual-home the primary and backup networks.  The management LAN connection didn't have to be dual-homed.  In all my years running servers, only once has a NIC failed, but for the 1,000 or so servers I spec'd and deployed, all of them had these redundant connections.  In one set of servers, we bought both 100base-tx and FIDI NICs because the data center infrastructure was being switched out and it wasn't certain which NIC type would be used ... then it came back from S-VPs that our project would have to purchase all the switches (at $130K/ea) to make the change to 100-base-tx networking.  I had to ask the client for $3M more and they weren't happy, but they did it. It was a fairly large project, so that amount was about 4% of the project. We always claim +/- 10% is as accurate as our estimates can be.

If you are really just starting out with Linux, crawl, stand, walk, jog, run, sprint .... [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)
If you are beginning level with the shell/CLI, get some automation going. Be consistent in your deployments: [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)
Consistency and reproducibility is important for an admin. You'll probably like the 2nd link more.  Lots of other people have written similar articles - mostly from a web-app deployment standpoint. I cringe at all the things they don't do. They would never know when the system was being hacked, for example, because nobody adds performance monitoring to their cloud servers. Seems pretty basic to me, but only professional admins do performance monitoring. Devs don't.  I've been both. Each has something to learn from the other.

Oh, and I'm hardly an expert. I've just been around a long time.  I know very little about setting up LDAP, though I've done it a few times and use it daily. I don't like **any** of the tools for it. DR and backups were an important part at my prior job. It was corporate policy to have DR for every system, period. If a project couldn't fund the DR requirements, then they didn't get to do the primary systems either.  DR had to be at least 500 miles away and not have similar risk factors as the other location.  Both couldn't be in earthquake or hurricane zones, for example. It isn't hard to avoid both of those things - I'm shocked at the places people build data centers. It is like they don't believe something bad could ever happen when there is a history of something bad happening every decade. Darwin at work, IMHO.

Anyway, that's enough from me. Hopefully you'll start/find a wikibook on this.

---

