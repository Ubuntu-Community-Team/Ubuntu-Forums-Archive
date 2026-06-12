---
title: "Ubuntu in an office environment"
date: 2006-02-26
forum: The Cafe
---

### Post by saads on 2006-02-26
Anyone have a guide on how to setup/administer ubuntu in an office environment?  I think this would be a major step in cutting into Microsoft's main revenue generator.  Thoughts that I have on this:

1) Setting up an email/calendar mechanism to compete with Microsoft Exchange.  Hula and Zimbra are two projects that I think would be useful in this regard.

2) Setting up an office productivity suite - I think OpenOffice has this well covered.

3) Administering updates to each computer - not sure here.

4) Giving users a mechanism to install software in such a way that they do not require root priveleges to do so.  The sysadmins would not want to give each user root priveleges on their machine, and at the same time they don't want to have to approve every single software install.  What's a good way to set up this balance?

5) What would the system architecture be - the employees would all be running Ubuntu desktop and then we'd have a few ubuntu servers.  Which software would be running where?

There's clearly a lot more to this, but i'm hoping to get this discussion started.  If people could address the above issues too that would be great.

---

### Post by briancurtin on 2006-02-26
while i think you have some good questions for linux as a whole running in the office, i think another that you need to look into is support. i have heard that canonical can provide corporate-type support, but i havent looked at any numbers or what they do, so you should definitely look into that if you are dead-set on ubuntu. RedHat and Novell/SuSE are highly regarded in the office, and provide pretty solid support from what i do know. not saying that ubuntu/canonical doesnt, its a topic that you do need to look into when using this in an office environment.

---

### Post by DigitalDuality on 2006-02-26
From a system's admin perspective... i'd prefer users not being able to install software.  I wouldn't even tell them about synaptic or educate them on apt-get or anything of the sort.

90% of PC problems in my last 2 jobs stem from people who need basic office functionality (office suite, template, internet connection, e-mail) who decide to install stupid crap without knowing what it is or what it does.

Luckily my last job (not current) blocked them downloading any exe's from both e-mail and internet.  

Linux in my current office environment would get rid of more than half the problems we have.  And everyone "applications" are just insurance apps that are online apps hosted on carriers websites.  

Yet, they'd rather pirate... yes.. pirate.. Windows, Office 2003, McAfee, anti-spyware apps, Act, and various other applications.  

Needless to say i'm job hunting...

While i love "freedom" of Linux, freedom is not a suitable option in an office in terms of computer usage.  It creates more headaches than its worth.  And training people is time consuming and not too fiscally conservative.  They need the tools and the know how to perform their task.. and that's it IMO.

Controlling what's on a system upon deployment of that box... and down the road, i think is pretty imperative for maintaining a smooth running network.  And i try to, to the nth degree.  I work with alot of really old machines b/c the company i'm at won't pay for upgrades or new systems.  So  i deal with alot of XP pentium 2 and 3 systems with 256M of Ram at the max.  A user so much as changing the theme on their desktop destroys the speed and efficency of the machine.  So.. it gets locked down pretty tightly.

---

### Post by nalmeth on 2006-02-26
I think the whole training problem is overblown. For fun, I'm using KDE to create an environment that looks and feels exactly like windowsXP. How much employee training would be required to click an "Internet Browser" icon, especially when the new browser looks almost identical to the old one? The difficulty is in making sure that the apps and the environment are easy to use and recognizable, not in finding out how to simplify teaching the users how to use the apps. Ubuntu is probably not ready for this yet, of course there would have to be introduction and training, because on first sight, it looks worlds different. Even KDE. I just point out that with the versatility of linux comes the ability to make it look and operate however you like. A company would make good money providing an OS that mimicked the outgoing one, but was more stable, and cost-effective.

---

### Post by K.Mandla on 2006-02-26
[QUOTE=DigitalDuality]From a system's admin perspective... i'd prefer users not being able to install software.  I wouldn't even tell them about synaptic or educate them on apt-get or anything of the sort.[/QUOTE]
I think that would be the way to go. And you're right, the bulk of problems in an office setting stem from folks who install Weatherbug or 20 other things like it because it looks cute. Then their computers don't run, and they complain to the IT gang.

We have one self-proclaimed "power user" in our office who spends most of his time surfing for warez and tying up the network with a torrent client. About a month ago he got into some serious spyware that locked up his machine. It took two techies the better part of the weekend to clean it out, but I was a proponent of running Killdisk. The poor guy looked real worried for a while.

Of course everyone has a story like that. Personally I'd almost prefer an environment where no one had administrator privileges ... except administrators.

---

### Post by GreyFox503 on 2006-02-26
[quote=saads]1) Setting up an email/calendar mechanism to compete with Microsoft Exchange.  Hula and Zimbra are two projects that I think would be useful in this regard.[/quote]

This is something that was brought to my attention recently.  I know at least one person at my school who uses some of the more interesting features of Exchange to send email, make notes, and schedule appointments... and sync it with his PDA.  As far as I can tell, Evolution does not have complete compatibility with this.  (That's what he told me after trying, anyways.)  That's all that is keeping him on Windows.

Because it's Microsoft's system, though, it might be harder than I think to make an app that works perfectly with it...

---

### Post by aysiu on 2006-02-26
[QUOTE=briancurtin]i have heard that canonical can provide corporate-type support, but i havent looked at any numbers or what they do, so you should definitely look into that if you are dead-set on ubuntu.[/QUOTE] If you want to look into it, look here:

[http://www.ubuntu.com/support/supportoptions/paidsupport](http://www.ubuntu.com/support/supportoptions/paidsupport)

---

### Post by Iandefor on 2006-02-26
[quote=K.Mandla]I think that would be the way to go. And you're right, the bulk of problems in an office setting stem from folks who install Weatherbug or 20 other things like it because it looks cute. Then their computers don't run, and they complain to the IT gang.

We have one self-proclaimed "power user" in our office who spends most of his time surfing for warez and tying up the network with a torrent client. About a month ago he got into some serious spyware that locked up his machine. It took two techies the better part of the weekend to clean it out, but I was a proponent of running Killdisk. The poor guy looked real worried for a while.

Of course everyone has a story like that. Personally I'd almost prefer an environment where no one had administrator privileges ... except administrators.[/quote] That's disgusting. One reason I'm glad my school runs Macs is that when somebody tries to download some piece of spyware, they wind up with an exe that they can't run.

---

### Post by DigitalDuality on 2006-02-26
Don't expect that to last too much longer.

---

### Post by Iandefor on 2006-02-26
[quote=DigitalDuality]Don't expect that to last too much longer.[/quote]I don't. Which is why I'm currently drafting a proposal to switch my school over to Ubuntu. I don't really expect it to work, though.

---

### Post by DigitalDuality on 2006-02-26
A proposal to have ClamX and possibly MacScan (it's a pay product..not quite sure if its worth it yet either) would probably be a more "sure thing" route.

Though, i'll never damn promotion of Ubuntu :)

---

### Post by poofyhairguy on 2006-02-26
[QUOTE=saads] The sysadmins would not want to give each user root priveleges on their machine, and at the same time they don't want to have to approve every single software install.  [/QUOTE]

Why not? It seems that preventing normal users from installing things might be one of the best parts of Ubuntu.

---

### Post by mstlyevil on 2006-02-26
[QUOTE=poofyhairguy]Why not? It seems that preventing normal users from installing things might be one of the best parts of Ubuntu.[/QUOTE]

A lot of companies that I know of do just that. They set up limited accounts for their users and must give approval before anything installs. This would not be a big change for those in the corporate world.

---

### Post by Iandefor on 2006-02-26
[quote=DigitalDuality]A proposal to have ClamX and possibly MacScan (it's a pay product..not quite sure if its worth it yet either) would probably be a more "sure thing" route.

Though, i'll never damn promotion of Ubuntu :)[/quote] Yeah. What really needs to happen is that they need to get a freaking administrator for their computers. It gets really bad. Like, so bad they have to reinstall OS X about once a year.

---

### Post by Stormy Eyes on 2006-02-26
[QUOTE=saads]What's a good way to set up this balance?[/quote]

Every time some user asks for an install, give them 30 seconds to justify it. If they fail, hit them with a sledgehammer. The users will learn before you kill -9 too many of them. :twisted:

You really don't want to be giving install privileges to people who don't know how to troubleshoot their machines if they screw things up.

---

### Post by GreyFox503 on 2006-02-26
Survival of the fittest, eh?  :)

---

### Post by Stormy Eyes on 2006-02-26
[QUOTE=GreyFox503]Survival of the fittest, eh?  :)[/QUOTE]

More like risk management and loss prevention.

---

### Post by saads on 2006-02-26
[QUOTE=poofyhairguy]Why not? It seems that preventing normal users from installing things might be one of the best parts of Ubuntu.[/QUOTE]

The reason is that as a sysadmin it would become a massive headache if every time someone wanted to install something they had to contact the sysadmins to get them to come and do it for them - but as mentioned this may be in fact already the case in most corporate environments that run windows so that wouldn't be much of a change.  I would like the user to be able to install software in a "sandbox" of sorts, so that no matter what they install, it won't affect the system detrimentally.  Since they don't have root priveleges, this should be possible.  But the easy and most user-friendly method of installing software is by using .debs and apt-get or synaptic, which by default requires root permissions since most software gets installed into protected sections of the filesystem.  

They could, theoretically, install from source in their home directories, but I'm thinking it would be ideal if users could install things without affecting the system as a whole.  Theoretically users can easily destroy their own login sessions and environment already, so why not let them install software if the worst they can do is affect their own logins?

---

### Post by DigitalDuality on 2006-02-26
Maybe all of my experience has been different from yours... but banning users from installing software is no where near the headache, that allowing them is.

Let them call you for 2-3 weeks and just say no to every silly, non-sensical thing they want.  They'll get the hint after a while.  What gets installed on a computer should be decision of a sys admin.  You're not there to be a repair guy.. but to prevent problems from happening in the first place.

---

### Post by Stormy Eyes on 2006-02-26
[QUOTE=saads]Theoretically users can easily destroy their own login sessions and environment already, so why not let them install software if the worst they can do is affect their own logins?[/QUOTE]

Why make the sysadmin's job unnecessarily difficult? Believe me: as an admin to the ignorant, I'm going to lock down every damn thing I can. You don't get to configure anything unless you're Linus f---ing Torvalds.

---

### Post by commodore on 2006-02-27
[QUOTE=nalmeth]I think the whole training problem is overblown. For fun, I'm using KDE to create an environment that looks and feels exactly like windowsXP. How much employee training would be required to click an "Internet Browser" icon, especially when the new browser looks almost identical to the old one? The difficulty is in making sure that the apps and the environment are easy to use and recognizable, not in finding out how to simplify teaching the users how to use the apps. Ubuntu is probably not ready for this yet, of course there would have to be introduction and training, because on first sight, it looks worlds different. Even KDE. I just point out that with the versatility of linux comes the ability to make it look and operate however you like. A company would make good money providing an OS that mimicked the outgoing one, but was more stable, and cost-effective.[/QUOTE]

That wouldn't be Linux anymore. I hate all the screenies and distros I see that look like Windows.

---

### Post by saads on 2006-02-27
[QUOTE=commodore]That wouldn't be Linux anymore. I hate all the screenies and distros I see that look like Windows.[/QUOTE]
I disagree.  I think the strength of Linux is that you can make it what you want it to be.  If you want it to be like Windoze, then you can make it so.  If you want it to be like OSX, then you can make it so.  And best of all, it stays free :)

---

### Post by saads on 2006-02-27
So to get this back on track - has anyone installed Ubuntu in an office environment who can offer specifics on how to go about setting it up?  My first post mentioned an email/calendar service that rivals MS Exchange.  What about other products for the office environment?  And the infrastructure setup in terms of software on the servers?  How would you go about managing updates to all of the individual clients, etc?

---

### Post by jc87 on 2006-02-27
[QUOTE=Stormy Eyes]Why make the sysadmin's job unnecessarily difficult? Believe me: as an admin to the ignorant, I'm going to lock down every damn thing I can. You don't get to configure anything unless you're Linus f---ing Torvalds.[/QUOTE]

But then you would have RMS hacking your passwrd , why won´t you join me and just  use enter for a passwrd?:twisted:

---

### Post by Stormy Eyes on 2006-02-27
[QUOTE=jc87]But then you would have RMS hacking your passwrd , why won´t you join me and just  use enter for a passwrd?:twisted:[/QUOTE]

RMS will be right under Linus in /etc/sudoers. I figure he knows what he's doing.

---

### Post by tekwarren on 2006-02-27
Just adding my 2 cents to the tangent about users and priveledges to install: I've only worked in windows environments as far as end user machines. I dare say as a Sys Tech/PC Tech/etc that if users had their install priviledes revoked I probably wouldn't have a job. I think this would eliminate a GREAT deal of problems user initiated. Although I don't know if I could enforce this personally as then you run into the unhappy employee situation...that and I want to keep my job :-#

---

### Post by DigitalDuality on 2006-02-27
See that's the thing.

I can't tell you the number of offices i've walked into that are purely "reactive" to situations, rather than preventive.  When you make that kind of change in policy (which you must explain why in full detail, and be convincing, and persistant to whoever's above you to approve this).. and you're workload decreases.. guess what?

You think you're out of a job?  Oh hell no.

Then you find and test ways to make tasks more efficient, more economically feasible, find ways to aid them expand their business.

How can you BUILD and be constructive..and actually Do something for a company.. if you spend all day doing nothing but being a repair guy? Once you flip the IT section over from being reactive, to being pro-active.. you look alot better in the eyes of your superiors. Believe me.  Especially if you can improve their current systems and save them headaches and money.

Sure users are going to be pissed.  So what? Politely explain to them that it's wasteful of company money to keep fixing problems that can be easily prevented and that you'd rather be a constructive employee than one who drags it down.

And while users may be angry at first (couple weeks/month or so), over the long haul, they'll get over it.  Not only that.. but they'll be amazed at how much smoother their system is.  it doesn't crash as much, there's not as many software conflicts.  It's one less day they don't have to go without a machine and interupt their work.

When systems continually and habitually crash..bc of spyware, people installing stupid crap, viruses, software conflicts,  ... who do you think looks bad?

The people downloading the crap? or the IT guy?  From my experience.. the general consensus gets blamed on IT.  "They can't keep the system up.. " is a very common complaint.  Don't allow their whining, guilt tripping, and complaining, make you look bad. This is your job, and  your reputation. Sure, you'll give their system back to them after they mess it up and they'll say "thank you so much.. you're so great".  But believe me, when you walk out of their presence..alot more gets said that always isn't so appreciative.  

Get a backbone and do what needs to be done..you'll thank yourself for it for a long time.

---

### Post by matthinckley on 2006-02-27
Awesome Post DigitalDuality.. Couln't agree more..

---

### Post by jc87 on 2006-02-27
[QUOTE=Stormy Eyes]RMS will be right under Linus in /etc/sudoers. I figure he knows what he's doing.[/QUOTE]

But passwords are a way to sysdmins to control and prevert users:twisted: , eventually someone would realize that with the login/pass RMS would have access to the whole system:rolleyes:  , or have you never read Free as in freedom the RMS history:-k .

---

