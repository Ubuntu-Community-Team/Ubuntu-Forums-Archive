---
title: "Who says only Microsoft gathers 'anonymous' user data"
date: 2010-08-10
forum: The Cafe
---

### Post by Madspyman on 2010-08-10
[http://www.phoronix.com/scan.php?page=news_item&px=ODQ5MA]("http://www.phoronix.com/scan.php?page=news_item&px=ODQ5MA")

> Just uploaded to the Ubuntu Lucid repository for Ubuntu 10.04 LTS (and we imagine it will appear shortly in Maverick too for Ubuntu 10.10) is a new package called canonical-census, which marks its initial release. Curious about what this package provides, we did some digging and found it's for tracking Ubuntu installations by sending an "I am alive" ping to Canonical on a daily basis...The program is to be added to the daily Cron jobs to be executed so that each day it will report to Canonical over HTTP the number of times this system previously sent to Canonical (this counter is stored locally and with it running on a daily basis it's thereby indicating how many days the Ubuntu installation has been active), the Ubuntu distributor channel, the product name as acquired by the system's DMI information, and which Ubuntu release is being used. That's all that canonical-census does, at least for now. Previously there haven't been such Ubuntu tracking measures attempted by Canonical. 

Does this rub anyone the wrong way? Being a avid Google user it's something I've learned to live with, but is it really necessary for Canonicle to include a data tracking package by default?

Edit:

Probably should have mentioned this.

> The good news for those concerned about privacy is that it appears for now Canonical is just interested in tracking the users of OEM installations -- those PCs that ship with Ubuntu by default such as from ZaReason, System76, and Dell. This information will obviously be valuable to both companies to see whether customers are keeping around their Ubuntu installations or just wiping them and just how often Ubuntu is being used on these systems (judging by the number of times that system reported to Canonical's server previously).

My thoughts are,

What if someone uninstalled canonical-census, no way to be sure so they'd be fudging the numbers regardless. Also uninstalling Ubuntu doesn't mean your installing Windows, it just might mean starting over from a fresh Ubuntu install which probably won't include canonical-census. This is a stupid idea. 

Also are they keeping track of IP addresses? What if someone installs a bunch of Ubuntu partitions on one machine all with canonical-census installed? You could easily fool Canonical into thinking that market-share is rising rapidly. It's seems like a flawed idea to me.

---

### Post by samalex on 2010-08-10
As long as they're up front about it and give the user the option to enable or disable it, I'm fine with it.  I'd probably disable it on my system, but any software that calls home should have permission from the user before doing so -- else it's considered malware in my book.  And if Canonical makes a habit of including such software without telling users, it'll turn users away.

Sam

---

### Post by zekopeko on 2010-08-10
> **Madspyman said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=ODQ5MA]("http://www.phoronix.com/scan.php?page=news_item&px=ODQ5MA")



Does this rub anyone the wrong way? Being a avid Google user it's something I've learned to live with, but is it really necessary for Canonicle to include a data tracking package by default?

It would be really nice if you mentioned that it's only for OEM installs and not vanilla Ubuntu.

---

### Post by FuturePilot on 2010-08-10
Oh boy here we go. :rolleyes:

First all it really says is PING $VERSION.
Second, this is targeted at OEM installs meaning it won't be included on the ISO image you download.
Third, with no way to accurately count the number of Ubuntu users and with all the "Linux marketshare at 1%" "Linux marketshare at 2%!!!!111" "Linux marketshare < 1%" discussion I would think that this might be welcome since it may be able to give an actual somewhat accurate number.

---

### Post by zekopeko on 2010-08-10
> **samalex said:**
> As long as they're up front about it and give the user the option to enable or disable it, I'm fine with it.  I'd probably disable it on my system, but any software that calls home should have permission from the user before doing so -- else it's considered malware in my book.  And if Canonical makes a habit of including such software without telling users, it'll turn users away.

Sam

You give more info by visiting a webpage then that OEM-install-only package sends to Canonical.

---

### Post by Bachstelze on 2010-08-10
> **FuturePilot said:**
> 
Second, this is targeted at OEM installs meaning it won't be included on the ISO image you download.

The problem remains. I doubt many OEMs would care about it, let alone mention it to their customers.

---

### Post by Elfy on 2010-08-10
> **zekopeko said:**
> It would be really nice if you mentioned that it's only for OEM installs and not vanilla Ubuntu.

I would agree with that sentiment.

> The good news for those concerned about privacy is that it appears for now Canonical is just interested in tracking the users of OEM installations -- those PCs that ship with Ubuntu by default such as from ZaReason, System76, and Dell. This information will obviously be valuable to both companies to see whether customers are keeping around their Ubuntu installations or just wiping them and just how often Ubuntu is being used on these systems (judging by the number of times that system reported to Canonical's server previously). For those not wanting to participate in this anonymous data gathering process, they could always sudo apt-get remove canonical-census. 

---

### Post by Madspyman on 2010-08-10
> **samalex said:**
> As long as they're up front about it and give the user the option to enable or disable it, I'm fine with it.  I'd probably disable it on my system, but any software that calls home should have permission from the user before doing so -- else it's considered malware in my book.  And if Canonical makes a habit of including such software without telling users, it'll turn users away.

Sam

Yeah sudo apt-get remove canonical-census. Being able to remove it kind of defeats it's purpose, it's supposed to tell Canonical how long an install has been alive on a daily basis, if the package is removed, Canonical won't be able to tell if it was because Ubuntu was uninstalled or just canonical-census.

---

### Post by Madspyman on 2010-08-10
> **zekopeko said:**
> It would be really nice if you mentioned that it's only for OEM installs and not vanilla Ubuntu.

I must have missed that part. Still don't see how this is going to help Canonical at all.

---

### Post by LowSky on 2010-08-10
just disable the cron job

---

### Post by NCLI on 2010-08-10
Guys, seriously, this in no way reduces your privacy. It doesn't identify you or your system, it just informs the server that there is a Model A computer distributed by company B which has had Ubuntu installed for X number of days. 

It **_doesn't_** say anything like: "Computername Dans Computer at IP-address xxx.xxx.xxx.xxx with MAC-address 00-00-00-00-00-00-00-00 has been active for X days, often browses porn sites and prefers Google over Bing."

It's simply:
```
Model name
Company name
Days Active
```

Anyone who gets scared by that should get cancel their internet subscription straight away, because just opening Firefox sends out more information than that.

I hope this will be installed by default(Though you should be able to deselect it during installation.) It would help us find out how many users Ubuntu really has.

---

### Post by Vincentlaborant on 2010-08-10
> **samalex said:**
> As long as they're up front about it and give the user the option to enable or disable it, I'm fine with it.  I'd probably disable it on my system, but any software that calls home should have permission from the user before doing so -- else it's considered malware in my book.  And if Canonical makes a habit of including such software without telling users, it'll turn users away.

Sam

It is located in the partner repro, and it is possible to remove it. I just tested it with my machine. As long as the partner source is not active, you will probably don't get the software in the first place.

But as I said, the package can be removed. Please note that both Windows and MAC OS have the same type of feature in it, but then we do not know what it does.

---

### Post by forrestcupp on 2010-08-10
> **zekopeko said:**
> It would be really nice if you mentioned that it's only for OEM installs and not vanilla Ubuntu.
Or they could just request a sales statement from the companies they partner with. ;)

---

### Post by StuartN on 2010-08-10
> **NCLI said:**
> Guys, seriously, this in no way reduces your privacy. It doesn't identify you or your system, it just informs the server that there is a Model A computer distributed by company B which has had Ubuntu installed for X number of days.

I still don't intend on allowing some privileged, behind-the-scenes application to update a private company's database about any aspect of my behaviour - whether that is uname -a, or any additional data that they might choose to add in a future update.

(Incidentally, this data collection does not comply with the data protection act where I live, which requires explicit opt-in consent).

---

### Post by NCLI on 2010-08-10
> **StuartN said:**
> I still don't intend on allowing some privileged, behind-the-scenes application to update a private company's database about any aspect of my behaviour - whether that is uname -a, or any additional data that they might choose to add in a future update.
IT DOESN'T. YOU ARE NOT PERSONALLY IDENTIFIED, SIMPLY COUNTED. This is not about you or your behavior, Canonical just wants to know how many people use Ubuntu.
> (Incidentally, this data collection does not comply with the data protection act where I live, which requires explicit opt-in consent).
Since it has just been uploaded and isn't used for anything yet, we don't know whether it'll be opt-in or opt-out.

---

### Post by *g!t5^_)*(H on 2010-08-10
I like it as long as the service doesn't provide personal data to Canonical. I fact, I think it is very necessary in order to know the real users of the system, and to get financial and investment sources. I would like to see it on every installed Ubuntu without care if it is from an OEM or a live CD. I'm sure Apple and Microsoft are doing it in worst ways, don't you think Google is working in this way? Please, Canonical really needs a census!

In fact, I'm going to install it:

sudo apt-get install canonical-census

---

### Post by mickie.kext on 2010-08-10
They probably want to check how much Ubuntu preinstalled computers continue runing Ubuntu after purchase, and how much get Windows installed.

---

### Post by juancarlospaco on 2010-08-10
If you dont like canonical-census just Fork it!!
its Open Source!
:)

---

### Post by kleskjr on 2010-08-10
Actually i think that its good for Linux and Ubuntu particularly. Installing the service will be a kind of support for the community.

---

### Post by Simian Man on 2010-08-10
> **mickie.kext said:**
> They probably want to check how much Ubuntu preinstalled computers continue runing Ubuntu after purchase, and how much get <snip>.

It wouldn't even tell them that much because if you install ANY OS on top it will stop calling home.

I really can't see why anyone would care about this one way or the other.  Either for Canonical for caring about this info or anybody reacting strongly.

---

### Post by juancarlospaco on 2010-08-10
There are something like that on Debian/Ubuntu since years, 
the APT package census, i allwayss activate it, 
its originally from Debian, but Ubuntu use it too.
:)

---

### Post by mickie.kext on 2010-08-10
> **Simian Man said:**
> It wouldn't even tell them that much because if you install ANY OS on top it will stop calling home.


Exactly. When it stops calling home, that means Ubuntu got dumped. That is enough info.

---

### Post by NCLI on 2010-08-10
> **Simian Man said:**
> It wouldn't even tell them that much because if you install ANY OS on top it will stop calling home.

I really can't see why anyone would care about this one way or the other.  Either for Canonical for caring about this info or anybody reacting strongly.

It tells them how many keep Ubuntu. That's what they're interested in.

---

### Post by Simian Man on 2010-08-10
> **mickie.kext said:**
> Exactly. When it stops calling home, that means Ubuntu got dumped. That is enough info.

> **NCLI said:**
> It tells them how many keep Ubuntu. That's what they're interested in.

If the OEM version gets replaced with a newer version it will also stop calling home.  As new versions come out fairly often, it's pretty likely to be replaced.

Also if I bought a Linux pre-installed computer, I'd probably fresh install anyway to get the partitioning scheme and possibly desktop I want.

---

### Post by Madspyman on 2010-08-10
> **mickie.kext said:**
> Exactly. When it stops calling home, that means Ubuntu got dumped. That is enough info.

Or someone uninstalled canonical-census, no way to be sure so they'd be fudging the numbers regardless. Also uninstalling Ubuntu doesn't mean your installing windows, it just might mean starting over from a fresh Ubuntu install which probably won't have canonical-census. This is a stupid idea. 

Are they keeping track of IP addresses? What if someone installs a bunch of Ubuntu partitions on one machine all with canonical-census installed? You could easily fool Canonical into thinking that market-share is rising rapidly. It's just a flawed idea.

---

### Post by fatality_uk on 2010-08-10
- unrolls tin foil onto table top
- shapes into fashionable trilby
- places on head
- feels relieved that **THEY** can't hear me anymore

---

### Post by NCLI on 2010-08-10
> **Simian Man said:**
> If the OEM version gets replaced with a newer version it will also stop calling home.  As new versions come out fairly often, it's pretty likely to be replaced.
An upgrade keeps the installed packages, so there's no reason why it should be removed after upgrading to a new version.
> Also if I bought a Linux pre-installed computer, I'd probably fresh install anyway to get the partitioning scheme and possibly desktop I want.
MMost people don't know how to install Ubun tu themselves. At least that's probably the group Canonical is aiming for with their OEM partners, not powerusers like you and me.
> **Madspyman said:**
> Or someone uninstalled canonical-census, no way to be sure so they'd be fudging the numbers regardless. Also uninstalling Ubuntu doesn't mean your installing windows, it just might mean starting over from a fresh Ubuntu install which probably won't have canonical-census. This is a stupid idea.
Again, the market Canonical is aiming for with the OEM computers isn't powerusers. The average user won't even know what canonical-census is, so why should he remove it? He's also unlikely to install reinstall Ubuntu himself.
> Are they keeping track of IP addresses? What if someone installs a bunch of Ubuntu partitions on one machine all with canonical-census installed? You could easily fool Canonical into thinking that market-share is rising rapidly. It's just a flawed idea.
No, they're not keeping track of the IP-adresses. And for the third time, **the OEM program isn't aimed at powerusers.** The main type of people who buy these machines will not have more than one operating system on them.

---

### Post by juancarlospaco on 2010-08-10
Im poweruser, and want to install it,
just because i can. :)

---

### Post by Simian Man on 2010-08-10
> **NCLI said:**
> An upgrade keeps the installed packages, so there's no reason why it should be removed after upgrading to a new version.
I meant a fresh install of a new version, with an in place upgrade you're right.

> **NCLI said:**
> MMost people don't know how to install Ubun tu themselves. At least that's probably the group Canonical is aiming for with their OEM partners, not powerusers like you and me.

While that is presumably their eventual goal, the fact of the matter is that, right now, practically nobody is going to buy Linux pre-installed who is not already a Linux enthusiast.

---

### Post by KiwiNZ on 2010-08-10
This thread demonstrates one thing .

People will believe what they want and  not the facts. :(

---

### Post by NCLI on 2010-08-10
> **Simian Man said:**
> I meant a fresh install of a new version, with an in place upgrade you're right.
I don't really have to reply to this again, do I? :-p


> While that is presumably their eventual goal, the fact of the matter is that, right now, practically nobody is going to buy Linux pre-installed who is not already a Linux enthusiast.
Canonicals goal is clearly to make Ubuntu more widely used, and it has definitely succeeded to some degree. Most powerusers won't buy their desktops from OEMS, and only a few will bother to buy DELLs ubuntu laptops, since the range is limited.

To me, the shows that Canonical is trying to sell these computers to those who are new to our world, and want to try something different. From the incredibly many newbies who post questions here every day, many of them about incompatible hardware, it seems the right way to go.

Although its use may be limited right now, just the fact that it's there means that we can now get numbers one how many people actually purchase these things. I'm hoping for a positive surprise.

Finally, I doubt this will stay out of the default release for long. It's too useful.

[size=1]Going to bed now. Don't expect any replies for the next ten hours or so :-p[/size]

---

### Post by MCVenom on 2010-08-10
Hopefully canonical-census will be added as a default for all installs in Maverick+1; it'll give us better hard numbers for Ubuntu usage. :D

---

### Post by Madspyman on 2010-08-10
> **KiwiNZ said:**
> This thread demonstrates one thing .

People will believe what they want and  not the facts. :(

Is this aimed at anyone in particular? The people who should feel insulted have a right to know that they are the ones being insulted.

Also providing an hypothetical about a matter doesn't mean people don't understand the facts, it just means they don't agree with them, the truth behind an idea doesn't always make it a good one.

---

### Post by juancarlospaco on 2010-08-10
**[COLOR="Red"]<--------------------------The Flame starts here--------------------------->[/COLOR]**

---

### Post by RussellGee on 2010-08-10
This doesnt even work on non-OEM installs as it calls "/var/lib/ubuntu_dist_channel" which doesn't exist on default non-OEM installs of both lucid and maverick.

Silly FUD spreading.

---

### Post by acreech on 2010-08-10
> **RussellGee said:**
> This doesnt even work on non-OEM installs as it calls "/var/lib/ubuntu_dist_channel" which doesn't exist on default non-OEM installs of both lucid and maverick.

Silly FUD spreading.

This is quite a thread. I installed the package but found that I did not have that path and it did not add anything to my crontab either. How do you make it work on a fresh install.

---

### Post by handy on 2010-08-11
I haven't used Ubuntu for years, but I think that this is a good idea. In fact it would be really cool if there was another innocuous tool created that did a similar thing, which protected the users privacy totally just like the Ubuntu one, & counted the Linux install base to a centralised counter held at say [The Linux Counter]("http://counter.li.org/"). It would be opt in only & available on all distros. This would give us a far more accurate approximation of the number of machines running Linux.

The code is open, so how on earth can anyone be tricking us with this tool?

---

### Post by Drenriza on 2010-08-11
Taken from danish [http://newz.dk/canonical-begynder-at-spore-ubuntu-installationer#new](http://newz.dk/canonical-begynder-at-spore-ubuntu-installationer#new) IT news.

> Canonical begynder at spore Ubuntu-installationer
Canonical Limited, som er firmaet bag Ubuntu, har tilføjet en ny pakke til kodebasen for Ubuntu 10.04 LTS (Lucid Lynx), og der spekuleres i, om pakken ikke også snart vil kunne ses i Ubuntu 10.10 (Maverick Meerkat). Pakken hedder canonical-census og sender i al sin enkelthed et ping til Canonical en gang om dagen, som fortæller at systemet lever.
Pakken planlægges tilføjet til de daglige cronjob og vil derefter sende det samlede antal pings, som det har foretaget til Canonical over HTTP. Ved at programmet kører en gang om dagen, kan Canonical dermed se, hvor mange dage Ubuntu har været installeret. Herudover sendes nogle få systeminformationer, såsom hvilken udgivelse af Ubuntu der bruges.
Indtil videre ser det kun ud til, at Canonical vil spore OEM-installationer af Ubuntu, som følger med computere fra blandt andet Dell. Denne information kan være brugbar for begge firmaer, som kan se, om brugerne beholder styresystemet, efter computeren er købt.

In short it says that.
Canonical has started to track Ubuntu installations, by adding a new code to the Ubuntu 10.04 LTS (Lucid Lynx) system. And maybe in the up coming 10.10 (Maverick Meerkat). The package _**canonical-census**_ simply sends one ping everyday to Canonical telling that the ubuntu installation lives. Besides telling Canonical that the ubuntu installation is alive, it also sends limited system information, like what ubuntu version you use. DELL can also use this information to see how meny keeps ubuntu on their laptop after buying it.

So i'm wondering what do you think about this? I personally don't mind. 

Kind Regards

EDIT:
You can also read about it here
[http://linux.slashdot.org/story/10/08/10/0319243/Canonical-Begins-Tracking-Ubuntu-Installations](http://linux.slashdot.org/story/10/08/10/0319243/Canonical-Begins-Tracking-Ubuntu-Installations)

---

### Post by TheNerdAL on 2010-08-11
I like it. :D It can help track how many Ubuntu users there are. :D

---

### Post by kpkeerthi on 2010-08-11
I don't mind as long as it is Linux that is calling home :)

---

### Post by fluteflute on 2010-08-11
> **KiwiNZ said:**
> This thread demonstrates one thing .

People will believe what they want and  not the facts. :(
It's sad.

---

### Post by Elfy on 2010-08-11
Threads merged

---

### Post by Perfect Storm on 2010-08-11
> **TheNerdAL said:**
> I like it. :D It can help track how many Ubuntu users there are. :D

Same here. I don't mind if such things will be implemented. 
In overall it will help the spread of Linux in general. We'll have some facts on ~X% users. It will be easier to convince software companies to make software for Linux if you can throw them some cold facts.

I want more Games for Linux :D

---

### Post by Drenriza on 2010-08-11
What is it that people has against this? What are you afraid of would happen if you had this code on you'r machine?

The code is open, and you can see that you aren't in any danger, performance loss, critical space loss so what is the big deal?

E.T can phone home but Ubuntu can't. Pfff

---

### Post by Madspyman on 2010-08-11
> **Drenriza said:**
> What is it that people has against this? What are you afraid of would happen if you had this code on you'r machine?

The code is open, and you can see that you aren't in any danger, performance loss, critical space loss so what is the big deal?

E.T can phone home but Ubuntu can't. Pfff

I could really care less just expressing how I feel this is a bad idea. Not necessarily because of privacy issue (which apparently there aren't), also because it's not necessarily proof of anything. 

The numbers could be easily fudged, so why bother going to the effort to create something that could only work by taking into account more information than it actually does. For something like this to work properly it'd have to be included in every Ubuntu iso, be uninstallable and log IP addresses of users to get an accurate reading. 

IMO it's silly to create a program to collect information that can't work right because it can't collect information. I don't think this program can have a future, unless it's a shady one.

But hey I've said stupid things before.

---

### Post by handy on 2010-08-11
I have played music that I loved so much, but no one in the audience could relate to.

That's life. :)

---

### Post by KiwiNZ on 2010-08-11
I am compelled to repeat ....

This thread demonstrates one thing .

People will believe what they want and not the facts

---

### Post by Madspyman on 2010-08-11
> **KiwiNZ said:**
> I am compelled to repeat ....

This thread demonstrates one thing .

People will believe what they want and not the facts


"There are no facts, only interpretations." 

Also what true today might not be tomorrow, it's difficult to argue things are so black and white, when no one can be completely accurate about another's intentions. 

FUD or not no one can say for sure because nobody can predict the future. However everyone is entitled to their opinion.

---

### Post by KiwiNZ on 2010-08-11
Some people would not believe the facts if they were stamped on their foreheads. Why?  they prefer to run around like demented reef fish believing self generated or self serving rumor.

I guess it justifies the bulk purchase of tinfoil. :rolleyes:

---

### Post by handy on 2010-08-11
:lolflag:

I love it, well done Mike. :D

---

### Post by Madspyman on 2010-08-11
> **KiwiNZ said:**
> Some people would not believe the facts if they were stamped on their foreheads. Why?  they prefer to run around like demented reef fish believing self generated or self serving rumor.

I guess it justifies the bulk purchase of tinfoil. :rolleyes:

Hmm.. it would seem easier to dismiss such concerns as rumors, and calling people names, as is accustom to some sorts of a particular unix tribe. Not the same could be said for all of those members however because that would be generalizing, calling the observed facts of one particular situation, the ones that hold true of every situation.

True or not it's good to be careful, wouldn't want to offend anyone by disagreeing with what they consider the facts. God forbid someone tries to express an opinion another might consider wrong. There's a really good discount on bulk tinfoil, and it sure lasts long enough to get your moneys worth. Perhaps even by wrapping up some demented reef fish for leftovers.

---

### Post by Khakilang on 2010-08-11
I thought they already have software source to do that. Which I didn't activate by the way. Maybe I should so that they can improve the software packages.

[ATTACH]166155[/ATTACH]

---

### Post by NCLI on 2010-08-11
> **Madspyman said:**
> Is this aimed at anyone in particular? The people who should feel insulted have a right to know that they are the ones being insulted.

Also providing an hypothetical about a matter doesn't mean people don't understand the facts, it just means they don't agree with them, the truth behind an idea doesn't always make it a good one.
If you disagree with a fact, you're stupid. Seriously. A fact is defined as:
> fact [fækt]
n
1. an event or thing known to have happened or existed
2. a truth verifiable from experience or observation
3. a piece of information get me all the facts of this case
4. (Law) Law (often plural) an actual event, happening, etc., as distinguished from its legal consequences. Questions of fact are decided by the jury, questions of law by the court or judge
Disagreeing with "an event or thing known to have happened or existed" is just plain denial and spreads FUD. The facts of exactly what this application does is summed up in the first post, and you can check the source code yourself if you think the article is incorrect. What you cannot disagree with is what's actually in the source, that is fact, undeniable truth. 

**_YOU CANNOT DISAGREE ABOUT WHAT LINES OF CODE DO_**

Now, we can disagree on the effectiveness of this, and on how many people will keep the package installed, as that's a totally different discussion. My take on it is that this will only be limited to OEMs temporarily, that it will soon be part of the default installation as an opt-out feature(Opt-in would mean that many users wouldn't even know about it, and thus not activate it), and that most people won't give a damn. The few who do will probably remove it as surely as they'll put their tinfoil hats on in the morning before leaving the faraday cage they've erected around their bed.

This is such a small minority it really won't have any sort of noticeable impact on the census.

---

### Post by handy on 2010-08-11
Unfortunately this thread has become one of those threads that presents itself perfectly for *those* others who think that they need to show links to distro users who are showing their absolute  stupidity & just so happen to be Ubuntu users.

Hopefully we will stop talking all this crap soon?

---

### Post by fatality_uk on 2010-08-11
Has anyone created a "THIS IS AN OUTRAGE - LETS TELL CANONICAL WHAT WE THINK" FaceBook page yet?? :) Only a matter of time! :D

---

### Post by zekopeko on 2010-08-11
> **fatality_uk said:**
> Has anyone created a "THIS IS AN OUTRAGE - LETS TELL CANONICAL WHAT WE THINK" FaceBook page yet?? :) Only a matter of time! :D

Oh, what irony would that be!

---

### Post by Simian Man on 2010-08-11
In this thread I only see *one post*, StuartN's, that expresses any real concern over this.  Why are you guys all up in arms?  Defensive much?

---

### Post by forrestcupp on 2010-08-11
> **NCLI said:**
> IT DOESN'T. YOU ARE NOT PERSONALLY IDENTIFIED, SIMPLY COUNTED. This is not about you or your behavior, Canonical just wants to know how many people use Ubuntu.Yeah, we know what it is right now.  How hard would it be for them to slip a little more in later without publicizing it after we have all accepted it as harmless?  Sure, powerusers can look at the code and notice changes, but like you said below, this isn't aimed at powerusers.  It's aimed at OEM users who aren't going to put a whole lot of effort into looking into these things.

> **NCLI said:**
> Again, the market Canonical is aiming for with the OEM computers isn't powerusers. The average user won't even know what canonical-census is, so why should he remove it? He's also unlikely to install reinstall Ubuntu himself.

No, they're not keeping track of the IP-adresses. And for the third time, **the OEM program isn't aimed at powerusers.** The main type of people who buy these machines will not have more than one operating system on them.

> **KiwiNZ said:**
> I am compelled to repeat ....

This thread demonstrates one thing .

People will believe what they want and not the facts
That goes both ways.  Some people will just stubbornly believe that Canonical will never do anything wrong.  If Microsoft or Google put a simple, non-intrusive "call home" operation in any of their software, some of the proponents in this thread would be all up in arms about it, and I'm sure they already have.

But I personally don't care because I don't have anything to hide.  MS, Google, Canonical, or anyone can know about my computer if they want, as long as they aren't getting info that will allow them to steal my identity.

---

### Post by Noz3001 on 2010-08-11
I'd quite like something like this in all installations if the information was public. Statistics like this interest me.

---

### Post by mickie.kext on 2010-08-11
> **KiwiNZ said:**
> Some people would not believe the facts if they were stamped on their foreheads. Why?  they prefer to run around like demented reef fish believing self generated or self serving rumor.

I guess it justifies the bulk purchase of tinfoil. :rolleyes:

Which people? Which facts? I don't see any facts, and I see a lots of people. Would you care to tell me those facts?

Or maybe you just want to feel superior and insult everybody?

---

### Post by ibuclaw on 2010-08-11
I fail to see why there would be any negativity around this.

It's not like it's any different (or worse) to the popularity contest (popcon) package, in which thousands of people usually enable at their own will.
For those that don't know what popcon is. In a nutshell, it sets up a cron job that will periodically anonymously submit to the developers statistics about the most used packages on your system.

The result? It lets us maintainers know how many people actually use our software. :)

[http://qa.debian.org/popcon.php?package=gdc-4.3](http://qa.debian.org/popcon.php?package=gdc-4.3)

---

### Post by RiceMonster on 2010-08-11
When you install Fedora, it gives you the option to send them information about what kind of hardware you're installing it on. This is so they can get a better idea of what kind of hardware Fedora users are using. I don't mind, so I send the information. It's not like it looks up my credit card number, what kind of music I listen to, etc.

I don't have any problem with Canonical doing this. I don't use Ubuntu, but it wouldn't stop me from installing it (given that it comes with the ISO in the future) or buying an OEM machines with Ubuntu on it. As usual, I think this is overblown.

---

### Post by handy on 2010-08-11
> **forrestcupp said:**
> Yeah, we know what it is right now.  How hard would it be for them to slip a little more in later without publicizing it after we have all accepted it as harmless?  Sure, powerusers can look at the code and notice changes, but like you said below, this isn't aimed at powerusers.  It's aimed at OEM users who aren't going to put a whole lot of effort into looking into these things.




That goes both ways.  Some people will just stubbornly believe that Canonical will never do anything wrong.  If Microsoft or Google put a simple, non-intrusive "call home" operation in any of their software, some of the proponents in this thread would be all up in arms about it, and I'm sure they already have.

But I personally don't care because I don't have anything to hide.  MS, Google, Canonical, or anyone can know about my computer if they want, as long as they aren't getting info that will allow them to steal my identity.

Open source, remember?

Evil code becomes public very quickly...

---

### Post by Mr. Picklesworth on 2010-08-11
You know, it would be cool if this *was* a uniquely identifiable kind of thing, maybe tied to your Ubuntu Single Sign-On. You could use it to get the IP address for your computer at home and do some impromptu peer-to-peer stuff :b

---

### Post by 23meg on 2010-08-11
> **forrestcupp]Yeah, we know what it is right now. How hard would it be for them to slip a little more in later without publicizing it after we have all accepted it as harmless? Sure, powerusers can look at the code and notice changes, but like you said below, this isn't aimed at powerusers. It's aimed at OEM users who aren't going to put a whole lot of effort into looking into these things.[/QUOTE]

Technically, as long as it is to live in the Ubuntu archive, it would be next to impossible, since for it to get uploaded to the main component of the package archive, it would have to undergo code review and general scrutiny, not only by Canonical employees whom you assume to be malicious for the sake of argument, but independent developers as well. It's a good thing that this is free software, and part of the package archive. There is already at least [one]("http://skitterman.wordpress.com/2010/08/10/just-say-no/") long time Ubuntu core developer declaring reservations with the software even in its current form.

Technically, can a hypothetical malicious OEM tweak the source to make it nasty and ship it? Not as a direct derivative of canonical-census, since it's under the GPL, and the vendor would have to ship the derivative under the same license, effectively revealing the nasty bits to the whole world.

It's not as if Canonical is giving OEMs a substantial new technology that they could use for snooping on users, though said:**
> calls home[/URL] with no less than your GPS location data. Is anyone bugging Canonical or other component providers about that? Of course not; people who use the Palm Pre willfully agree with Palm's privacy policy, and have to live with the consequences of doing so.

But trust and mutual interests come before technicalities, and Canonical has no vested interest in violating the privacy of its users with software that uniquely identifies them with a call home scheme, so the question of *why* they would precedes that of whether they technically could.

[QUOTE=forrestcupp]That goes both ways. Some people will just stubbornly believe that Canonical will never do anything wrong. If Microsoft or Google put a simple, non-intrusive "call home" operation in any of their software, some of the proponents in this thread would be all up in arms about it, and I'm sure they already have.

A notable difference you omit is that unlike how it usually is with software coming from Microsoft or Google, in this case there is actually a way of being 100% sure that a piece of "call home" software is doing nothing malicious. People don't have to *believe* that Canonical is not doing wrong; they can go and check whether they're doing wrong themselves.

[QUOTE=forrestcupp]But I personally don't care because I don't have anything to hide.[/QUOTE]

That's an ultimately [fallacious]("http://papers.ssrn.com/sol3/papers.cfm?abstract_id=998565") line of thinking, but:

[QUOTE=forrestcupp]MS, Google, Canonical, or anyone can know about my computer if they want, as long as they aren't getting info that will allow them to steal my identity.[/QUOTE]

It's all about whom you trust. 

If you have read the relevant licensing and privacy agreements and trust that a piece of non-free, potentially privacy breaching software whose source cannot be audited by any other party than its vendor will not be getting information that will allow your vendor or another party to steal your identity now or in the future, you have accepted their terms and have to live with the consequences. And if you haven't, or don't trust the vendor of your OS or communication software, it's likely that you have bigger problems on your hands than the potential of a violation of privacy.

---

### Post by handy on 2010-08-11
> **23meg said:**
> ...
It's all about whom you trust. 

If you have read the relevant licensing and privacy agreements and trust that a piece of non-free, potentially privacy breaching software whose source cannot be audited by any other party than its vendor will not be getting information that will allow your vendor or another party to steal your identity now or in the future, you have accepted their terms and have to live with the consequences. ...

23meg, that is one very powerful sentence. #-o

---

### Post by Madspyman on 2010-08-11
> **NCLI said:**
> If you disagree with a fact, you're stupid. Seriously. A fact is defined as:

Disagreeing with "an event or thing known to have happened or existed" is just plain denial and spreads FUD. The facts of exactly what this application does is summed up in the first post, and you can check the source code yourself if you think the article is incorrect. What you cannot disagree with is what's actually in the source, that is fact, undeniable truth. 

**_YOU CANNOT DISAGREE ABOUT WHAT LINES OF CODE DO_**

Now, we can disagree on the effectiveness of this, and on how many people will keep the package installed, as that's a totally different discussion. My take on it is that this will only be limited to OEMs temporarily, that it will soon be part of the default installation as an opt-out feature(Opt-in would mean that many users wouldn't even know about it, and thus not activate it), and that most people won't give a damn. The few who do will probably remove it as surely as they'll put their tinfoil hats on in the morning before leaving the faraday cage they've erected around their bed.

This is such a small minority it really won't have any sort of noticeable impact on the census.

[Knowledge]("http://www.thefreedictionary.com/knowledge") is defined as the "state or fact of knowing." The second and third definitions of knowledge state that "knowledge is based on perception and experience." To dig deeper, the meanings of perception and experience should also be defined. 

[Perception]("http://dictionary.reference.com/browse/perception") is defined as the act or faculty of apprehending by means of the senses or the mind, cognition and understanding. [Experience]("http://dictionary.reference.com/browse/experience") is defined as a particular instance of "personally encountering or undergoing something." It could be argued based on the subsequent definitions of perception and experience that knowledge is gained through personal encounters using the senses.

Since no one experiences an event in the same way another person does, every person's acquisition of knowledge is different. Building off of this, one can conclude that knowledge is subjective, it is based on the individual's experience. 

[Truth]("http://dictionary.reference.com/browse/truth") is defined as conformity to fact or actuality. The second definition adds that it can also be a statement proven or accepted as true. Thus, truth is based on knowledge, and accepted as truth only if it conforms to a standard of general acceptance or general knowledge. 

However, since it is impossible to experience an event in the exact same way another person does, all knowledge is different, and therefore, all truth is different. In this case, truth is a logical fallacy.

To sum it up my argument is simply, regardless of the facts, there is really no way to be sure of anything. 

Also just because there are facts available doesn't mean that those are all the facts. Again things change, Google used to be for an open mobile web that was a fact, but now they seem to agree (profitably) with Verizon's take on things. 
  
Also it's not very sporting to use name calling as an argument.

---

### Post by espen77 on 2010-08-11
I dont mind it being in the rpo or even on the vanilla ISO if you can choose to activate and deactivate this function easily both in the installer and later, and that it is not active by default (like the apt package popularity info).

It could be a good tool if combined with the bugs filed in launchpad. It can provide people with a good sugestion of what computer to get if they want to run ubuntu (many users and few bugs), and the bug squishers with an idea about what bugs to fix to have a big impact for the most people.

---

### Post by KiwiNZ on 2010-08-11
@ madsyman there simply is no smoking gun. 

Remember Ubuntu is not compulsory. Don't like it, don't use it.

---

### Post by RiceMonster on 2010-08-11
> **Madspyman said:**
> However, since it is impossible to experience an event in the exact same way another person does, all knowledge is different, and therefore, all truth is different. In this case, truth is a logical fallacy.

No, it's a logical fallacy to arrive at the conclusion that truth is a logical fallacy. This is where relativism goes wrong. It has good intentions, but it in it's purest form, it's simply incorrect. Tell me, how is it possible for two conflicting things to be true? Also, maybe you can prove to me that whether 1+1=2 or not is relative? No, 1+1 does not = 2 because we agreed so, they are terms used to discribe a specific concept.

---

### Post by jrothwell97 on 2010-08-11
*sigh* how has this descended into a conversation bordering on philosophical semantics?

> **Madspyman said:**
> (metaphysical blah)

**To sum it up my argument is simply, regardless of the facts, there is really no way to be sure of anything. **

Nonsense.

This is nothing to do with "perception", "truth" or "knowledge." It's a few bloody lines of code that ping the Canonical servers with the model of the computer, if and only if it's an OEM installation where the OEM's opted to enable this feature and the user hasn't disabled it (either via wiping the OS or just tin-foil-hat package removal.)

**You can not disagree about what these lines of code do**, because what they do is absolute.

> **Madspyman said:**
> Also just because there are facts available doesn't mean that those are all the facts. Again things change, Google used to be for an open mobile web that was a fact, but now they seem to agree (profitably) with Verizon's take on things.

I don't see how this is relevant. If you mean there could be a stealth update (and how this is related to Google's possibly-undertable-deal-possibly-technical-compromise with Verizon, I have no idea) which enables Canonical to take your credit card number, purchasing habits and children, of course, *theoretically* that's possible. It's also *theoretically* possible that I'm not Jonathan Rothwell at all, but in fact the espionage author John le Carré.

**Just because something is theoretically possible, it does not mean it will happen.** And if it did happen, you'd damn well hear about it.
  
> **Madspyman said:**
> Also it's not very sporting to use name calling as an argument.

It wasn't an argument, it was an opinion: and, after reading your post, one I unfortunately happen to share.

(Don't worry. Practically everyone's stupid, myself included.)

---

### Post by Madspyman on 2010-08-11
> **jrothwell97 said:**
> *sigh* how has this descended into a conversation bordering on philosophical semantics?



Nonsense.

This is nothing to do with "perception", "truth" or "knowledge." It's a few bloody lines of code that ping the Canonical servers with the model of the computer, if and only if it's an OEM installation where the OEM's opted to enable this feature and the user hasn't disabled it (either via wiping the OS or just tin-foil-hat package removal.)

**You can not disagree about what these lines of code do**, because what they do is absolute.



I don't see how this is relevant. If you mean there could be a stealth update (and how this is related to Google's possibly-undertable-deal-possibly-technical-compromise with Verizon, I have no idea) which enables Canonical to take your credit card number, purchasing habits and children, of course, *theoretically* that's possible. It's also *theoretically* possible that I'm not Jonathan Rothwell at all, but in fact the espionage author John le Carré.

**Just because something is theoretically possible, it does not mean it will happen.** And if it did happen, you'd damn well hear about it.

It wasn't an argument, it was an opinion: and, after reading your post, one I unfortunately happen to share.

(Don't worry. Practically everyone's stupid, myself included.)

I mostly agree with you, I'm mostly just sick of people arguing they can know another's intentions, based on only the information made available to them. 

Yes if Canonical changed things we'd damn well hear about it, but whose to say they won't (they probably won't)? 

The Google example was about expressing how the facts changed, and it really doesn't matter what they were in the first place because they're not facts anymore. Facts are only relevant until proven false. 

Pluto isn't a planet anymore, and apparently the triceratops never existed. If I tried to tell someone those new facts 20 years ago they'd call me crazy.

But apparently I've said crazier things.

Edit:
I will however agree I started this this thread before I really took note of all the facts available, I'm just the kind who sticks to his guns. I just speak, and words come out, if they form sentences I consider myself lucky.

---

### Post by forrestcupp on 2010-08-11
> **handy said:**
> Open source, remember?

Evil code becomes public very quickly...

> **23meg said:**
> Technically, can a hypothetical malicious OEM tweak the source to make it nasty and ship it? Not as a direct derivative of canonical-census, since it's under the GPL, and the vendor would have to ship the derivative under the same license, effectively revealing the nasty bits to the whole world.I addressed that when I said what I said below.  Only OEM people are going to be affected, so power users won't care because it won't affect them.  Do you think the average OEM user is going to sift through the code of something they probably don't even know exists to make sure they haven't changed anything?

> **forrestcupp said:**
> Sure, powerusers can look at the code and notice changes, but like you said below, this isn't aimed at powerusers.  It's aimed at OEM users who aren't going to put a whole lot of effort into looking into these things.

> **23meg said:**
> not only by Canonical employees whom you assume to be malicious for the sake of argument,I don't assume Canonical employees are malicious at all.  You shouldn't assume that I assume that.

> **23meg said:**
> That's an ultimately [fallacious]("http://papers.ssrn.com/sol3/papers.cfm?abstract_id=998565") line of thinking, but:

It's all about whom you trust. 
How is my statement fallacious?  I was specifically speaking of Microsoft, Canonical, and Google.  I trust each of those to not steal my identity.  They all have too much at stake to do something so stupid.

I don't think Canonical is going to do something malicious.  But I do think that it's possible that they could slip something in that isn't malicious, but it's not necessarily something that someone is comfortable with.

They just need to be up front about things like this, even with people who don't read code and keep up on all the mailing lists.  It would be good if they made it optional, too, even with the OEMs.  At least let people know what they're doing the first time they turn on their new computer.

---

### Post by ssam on 2010-08-11
i enable popcon on my system. (system->admin->software sources->statistics) which sends a list of which packages are installed.

means we have nice stats [http://popcon.ubuntu.com/](http://popcon.ubuntu.com/)

---

### Post by KiwiNZ on 2010-08-11
> **hotrodder said:**
> I installed it because I'm not a paranoid user.

I want my PC to be counted to show Ubuntu how many are out here.

Got ya

Now we are watching you ......:evil:

---

### Post by zekopeko on 2010-08-11
> **KiwiNZ said:**
> Got ya

Now we are watching you ......:evil:

The economic downturn must have hit the Empire pretty hard considering you are actually making the population do the spying of themselves by themselves. Not that is some evil *sith* right there. ;)

---

### Post by KiwiNZ on 2010-08-11
> **zekopeko said:**
> The economic downturn must have hit the Empire pretty hard considering you are actually making the population do the spying of themselves by themselves. Not that is some evil *sith* right there. ;)

Ya do what ya got to do :p

Spying, of the people , for the people, by the people

---

### Post by handy on 2010-08-11
I always like knowing that someone is watching over me. :)

---

### Post by PryGuy on 2010-08-12
Ubuntu will 'phone home' too. Nice... :|

---

### Post by murderslastcrow on 2010-08-12
I assume that the source for this package is available, so we can see if anything shady is going on. In that case, I think this package should be included by default in 10.10 so we finally have an accurate count of how many Ubuntu users there are.

There is no risk involved if we can investigate what the code is doing and ensure there is no private data communicated. Don't be anal when this could be an opportunity to increase the viability of the platform we use with solid numbers. Please, please don't go overboard with this.

Think calmly about the possibilities, both for good, and the possibilities for checking the code. Canonical isn't going to do anything naughty if their source code has firm evidence of that wrong-doing. It's just a stupid move.

But yeah, doesn't rub me the wrong way. I've been waiting forever for some way to accurately count the number of Ubuntu users. I think Canonical ought to at least have THAT privilege.

---

### Post by 23meg on 2010-08-12
> **forrestcupp said:**
> Do you think the average OEM user is going to sift through the code of something they probably don't even know exists to make sure they haven't changed anything?

Non-technical users of free software don't sift through code for *any* kind of change. That doesn't mean they don't benefit from code disclosure, permissive licenses and distributed development; they benefit indirectly through the scrutiny of those who do, through implicit networks of trust, and through the trust they place in their development communities or vendors.

The people you implied to be hypocritical in going up in arms when Microsoft or Google call home, but not doing so when Canonical does, are not non-technical users, though; being Ubuntu forum members, they're mostly technically adept, somewhat experienced Ubuntu users who can be assumed to be able to distinguish between a 30-line GPL'd shell script that sends an unencrypted, standard HTTP request, and a proprietary, closed source call-home mechanism of unknown specification. They can hold Canonical accountable, since they can see, modify and refuse to use the source. In your example, they could not hold Microsoft accountable, since they would have agreed to an EULA that explicitly allows privacy-breaching home calling, and they wouldn't have source code to look at.

> **forrestcupp]I don't assume Canonical employees are malicious at all.  You shouldn't assume that I assume that.[/QUOTE]

I said that you were assuming that *for the sake of argument*, in questioning whether it would be easy / possible for Canonical to "slip a little more in later" said:**
> How is my statement fallacious?  I was specifically speaking of Microsoft, Canonical, and Google.  I trust each of those to not steal my identity.  They all have too much at stake to do something so stupid.

The "I have nothing to hide, so I have the high ground in all discussions of privacy" position is fallacious in that there's no casual connection between having or not having something to hide, and the need for privacy. If you have time and energy to read the article I linked to, you'll see that connection successfully refuted.  

> **forrestcupp said:**
> I don't think Canonical is going to do something malicious.  But I do think that it's possible that they could slip something in that isn't malicious, but it's not necessarily something that someone is comfortable with.

For reasons I outlined before, I disagree. Not only they *couldn't* technically, but the chances that they *would* attempt that are extremely slim.

> **forrestcupp said:**
> They just need to be up front about things like this, even with people who don't read code and keep up on all the mailing lists. 

Rick Spencer, the desktop team manager, [blogged]("http://theravingrick.blogspot.com/2010/08/can-we-count-users-without-uniquely.html") about it, and Slashdot, Phoronix, dozens of blogs and news websites picked up on it within hours.

> **forrestcupp said:**
> It would be good if they made it optional, too, even with the OEMs.  At least let people know what they're doing the first time they turn on their new computer.

*Anything* they offer to OEMs to ship on their machines is optional, by definition, since Canonical can't force OEMs to ship or not ship a particular package. And currently, this particular package is to be used by **one** OEM; not forced on every future OEM who will ship Ubuntu preinstalled:

[QUOTE=Rick Spencer]Currently this system is only slated to be used by the specific OEM customer who requested it[/QUOTE]

---

### Post by murderslastcrow on 2010-08-12
I should just buy tons of computers from this OEM and do a lot of questionable things on them, just to spite the paranoid among you. Bwahahaha.

I totally would if I had the money.

---

### Post by rapha on 2010-08-12
> **optimisme said:**
> 
In fact, I'm going to install it:

sudo apt-get install canonical-census

Awesome idea, just did the same thing!

---

### Post by ssam on 2010-08-12
> **murderslastcrow said:**
> I assume that the source for this package is available, so we can see if anything shady is going on. In that case, I think this package should be included by default in 10.10 so we finally have an accurate count of how many Ubuntu users there are.


```

apt-get source canonical-census

```

```

sam@oberon:/tmp/canonical-census-0.1$ cat send-census 
#!/bin/bash
# Send an "I am alive" ping to Canonical. This is used for surveying how many
# original OEM installs are still existing on real machines. Note that this
# does not send any user specific data; it only transmits the operating system
# version (/var/lib/ubuntu_dist_channel), the machine product name, and a
# counter how many pings were sent.
#
# (C) 2010 Canonical Ltd.
# License: GPL v2 or later

set -e

COUNTFILE=/var/lib/send-install-count/counter
DCD=/var/lib/ubuntu_dist_channel
SCRIPT=http://census.canonical.com/submit

[ -e $DCD ] || exit 0

# read release info
. /etc/lsb-release || :

# get current count
if [ -e $COUNTFILE ]; then
    cur=$(< $COUNTFILE)
else
    cur=0
fi

# get DCD
channel=$(sed -n '/^[[:alnum:]]/ { p; q}' $DCD)

# get machine product name
product=$(< /sys/class/dmi/id/product_name) || product=''
product=${product/% *}


# report in
if ! wget -O /dev/null -q "$SCRIPT?count=$cur&dcd=$channel&product=$product&release=$DISTRIB_RELEASE"; then
    #echo "failed"
    exit 0
fi

# update counter
((cur=cur+1))
mkdir -p $(dirname $COUNTFILE)
echo $cur > $COUNTFILE

```

there is some analysis at [http://techandsp.blogspot.com/2010/08/whats-all-fuzz-about-canonical-census.html](http://techandsp.blogspot.com/2010/08/whats-all-fuzz-about-canonical-census.html)

---

### Post by Johnsie on 2010-08-12
I think it's a great idea. Some people might be disappointed with he results though. Most people eventually give up using Ubuntu as their main OS except for the ones who have been using Ubuntu isnce the mid 0's. If you don't believe me just look at the dates most of the people in this thread signed up to the forum. There are alot of people who started using Ubuntu in the mid 0's but alot less seem to be recent users. I believe the reason is that Windows7, Windows XP and and OSX have better lookng GUI.

---

### Post by zer010 on 2010-08-12
Canonical Begins Tracking Ubuntu Installations

[http://www.phoronix.com/scan.php?page=news_item&px=ODQ5MA](http://www.phoronix.com/scan.php?page=news_item&px=ODQ5MA)

What's the thoughts about this?

---

### Post by howefield on 2010-08-12
> **zer010 said:**
> What's the thoughts about this?

Read the nine pages here and you'll find out.

[http://ubuntuforums.org/showthread.php?t=1550018](http://ubuntuforums.org/showthread.php?t=1550018)

---

### Post by alket on 2010-08-12
I will install it, this will help Canonical for better stats, and if there are good stats other software companies will start to port their apps to linux. This is the same as promoting Ubuntu to relatives.

---

### Post by Johnsie on 2010-08-12
duplicate thread.

---

### Post by Nick_Jinn on 2010-08-12
I think the nature of tracking installations is different from tracking the kind of data that MS sells to corporations for marketing or to the government for whatever privacy violating reasons.

---

### Post by Sam on 2010-08-12
> **ssam said:**
> ```

apt-get source canonical-census

```

<snip>

Hum this is only a HTTP request with a querystring. Is there any protection against forged requests on the server? Anyone can send false requests and boost the statistics...

---

### Post by t0p on 2010-08-12
I think this census is a generally good idea as it may improve our operating system and apps.  I joined in Popularity Contest for a while, but after a while I sort of forgot about it.  That's a problem of opt-in systems.

I gotta say, some of the comments earlier in the thread seemed a little patronising and a bit offensive.  All that talk that "facts are facts" and it's somehow stupid or even malicious to "ignore the facts".  Most people who really think about what's going on around them accept relativity and the inability to make truly precise measurements.   No doubt what I just wrote strikes many of you as ridiculously philosophical or pedantic considering (one of) the subject(s) of this thread - but if you want to make someone feel stupid, it's not a good idea to contradict him with even more stupid comment.

---

### Post by forrestcupp on 2010-08-12
> **23meg said:**
> 
For reasons I outlined before, I disagree. Not only they *couldn't* technically, but the chances that they *would* attempt that are extremely slim.You really don't think it's possible that Canonical would ever do anything that is not malicious, but still uncomfortable to some people?  That's what I said in my post.  Let me give you a couple of examples that have already made people uncomfortable, even if it's unjustified in some people's opinion: Ubuntu One, proprietary software or modules being included, Mono apps, and even Canonical-Census.  These are just a few things that aren't malicious or even wrong, but they have made people uncomfortable.  What is and isn't acceptable is extremely subjective.  True, we have a choice of what OS we use, but people who buy an OEM usually don't want to have to worry about installing another OS.

It's unrealistic to think that they couldn't or wouldn't add more stuff to Census that would make people more uncomfortable, even if it's not malicious.  I definitely don't think Canonical is ever going to do anything malicious.  But I'm not stubborn enough to think they won't ever do anything uncomfortable to the user.


> **23meg said:**
> Rick Spencer, the desktop team manager, [blogged]("http://theravingrick.blogspot.com/2010/08/can-we-count-users-without-uniquely.html") about it, and Slashdot, Phoronix, dozens of blogs and news websites picked up on it within hours.How many people who buy an Ubuntu netbook just to browse the web and read emails are really going to keep up on Phoronix or blogs about Ubuntu?

> **Johnsie said:**
> I believe the reason is that Windows7, Windows XP and and OSX have better lookng GUI.Lol.  I don't think that's the reason.  I'm way more impressed by the GUIs in Linux than anything else I've seen.  But I primarily use Windows 7 because of software compatibility.  That's pretty much the only reason.

---

### Post by betrunkenaffe on 2010-08-12
> **StuartN said:**
> I still don't intend on allowing some privileged, behind-the-scenes application to update a private company's database about any aspect of my behaviour - whether that is uname -a, or any additional data that they might choose to add in a future update.

(Incidentally, this data collection does not comply with the data protection act where I live, which requires explicit opt-in consent).

So Windows 7 isn't available where you live? That doesn't have explicit opt-in consent. You opt in by using it, there isn't another option.

The world is going to end, Canonical will know everything about us and use it to rule the world!!

On a more serious note: If I don't have my lappy on, does the cron job run when I boot it? Seems to me it should initialize the day you installed and then just report the diff in days between that and now because if I keep my laptop off for a week, really messes the numbers up. Might install this now since I have an OEM Ubuntu install.

---

### Post by BigSilly on 2010-08-12
I don't mind really. Is this not enabled in Lucid then? I'd be quite happy to do it if it was. At the end of the day, we put all sorts of crazy details about ourselves into the internet, and though of course I have concerns about privacy, and also about the direction Ubuntu and Canonical are taking with certain things, this sounds pretty innocuous to me. Maybe it'll help us get some more accurate stats too.

---

### Post by 23meg on 2010-08-12
> **forrestcupp said:**
> You really don't think it's possible that Canonical would ever do anything that is not malicious, but still uncomfortable to some people?  That's what I said in my post.  Let me give you a couple of examples that have already made people uncomfortable, even if it's unjustified in some people's opinion: Ubuntu One, proprietary software or modules being included, Mono apps, and even Canonical-Census.  These are just a few things that aren't malicious or even wrong, but they have made people uncomfortable.  What is and isn't acceptable is extremely subjective.  True, we have a choice of what OS we use, but people who buy an OEM usually don't want to have to worry about installing another OS.

It's unrealistic to think that they couldn't or wouldn't add more stuff to Census that would make people more uncomfortable, even if it's not malicious.  I definitely don't think Canonical is ever going to do anything malicious.  But I'm not stubborn enough to think they won't ever do anything uncomfortable to the user.

I agree, and to take it further, I actually find it unrealistic to think that *any* significant user-facing move taken by a company of Canonical's influence is not going to make a lot of people uncomfortable. The census script has already made plenty of people uncomfortable, even in its current state. That something makes some people uncomfortable doesn't mean it's inherently malicious, unethical or goes against basic rights such as privacy. To decide whether a particular move qualifies as such or not, I'd evaluate each specific case in context and in the light of facts, without going down [slippery slopes]("http://en.wikipedia.org/wiki/Slippery_slope"). 

> **forrestcupp said:**
> How many people who buy an Ubuntu netbook just to browse the web and read emails are really going to keep up on Phoronix or blogs about Ubuntu?

How many people who buy an Ubuntu netbook just to browse the web and read emails will go to canonical.com or oemwebsite.com and look for announcements? 

If there's a specific way you suggest in which Canonical can be *usefully* more up front about this, feel free to suggest it. I don't think Canonical announcing it any louder will have any effect in this regard; it's OEMs that have to make it clear, and ultimately, users who have to read usage agreements and the like to be aware of it.

---

### Post by Madspyman on 2010-08-12
> **Sam said:**
> Hum this is only a HTTP request with a querystring. Is there any protection against forged requests on the server? Anyone can send false requests and boost the statistics...


I tried to make a similar point to this earlier but was (at least it sounded that way) referred to as a stupid, paranoid, tin foil hat wearing, demented reef fish who wouldn't believe the facts if they were stamped to my forehead.

> Also are they keeping track of IP addresses? What if someone installs a bunch of Ubuntu partitions on one machine all with canonical-census installed? You could easily fool Canonical into thinking that market-share is rising rapidly. It's seems like a flawed idea to me.


> The numbers could be easily fudged, so why bother going to the effort to create something that could only work by taking into account more information than it actually does. For something like this to work properly it'd have to be included in every Ubuntu iso, be uninstallable and log IP addresses of users to get an accurate reading. 

> IMO it's silly to create a program to collect information that can't work right because it can't collect information. I don't think this program can have a future, unless it's a shady one.


I'm starting to believe expressing any concern around here is an unwelcome processes for some.

---

### Post by cariboo on 2010-08-12
Actually Canonical does keep track of unique ip addresses. That is how they come up with the 12 million users figure, although the figures aren't very accurate, as I have 6 unique installs and only one ip address, I'm sure there are more people in the same boat.

---

### Post by FuturePilot on 2010-08-12
> **cariboo907 said:**
> Actually Canonical does keep track of unique ip addresses. That is how they come up with the 12 million users figure, although the figures aren't very accurate, as I have 6 unique installs and only one ip address, I'm sure there are more people in the same boat.

***raises hand***

---

### Post by NCLI on 2010-08-12
> **mickie.kext said:**
> Which people? Which facts? I don't see any facts, and I see a lots of people. Would you care to tell me those facts?

Or maybe you just want to feel superior and insult everybody?

The facts are in the code. The open code. Anyone who bothers to have a look at it will quickly see that it's very simple, and not anything to worry about.

> **Madspyman said:**
> [Knowledge]("http://www.thefreedictionary.com/knowledge") is defined as the "state or fact of knowing." The second and third definitions of knowledge state that "knowledge is based on perception and experience." To dig deeper, the meanings of perception and experience should also be defined. 

[Perception]("http://dictionary.reference.com/browse/perception") is defined as the act or faculty of apprehending by means of the senses or the mind, cognition and understanding. [Experience]("http://dictionary.reference.com/browse/experience") is defined as a particular instance of "personally encountering or undergoing something." It could be argued based on the subsequent definitions of perception and experience that knowledge is gained through personal encounters using the senses.

Since no one experiences an event in the same way another person does, every person's acquisition of knowledge is different. Building off of this, one can conclude that knowledge is subjective, it is based on the individual's experience. 

[Truth]("http://dictionary.reference.com/browse/truth") is defined as conformity to fact or actuality. The second definition adds that it can also be a statement proven or accepted as true. Thus, truth is based on knowledge, and accepted as truth only if it conforms to a standard of general acceptance or general knowledge. 

However, since it is impossible to experience an event in the exact same way another person does, all knowledge is different, and therefore, all truth is different. In this case, truth is a logical fallacy.

To sum it up my argument is simply, regardless of the facts, there is really no way to be sure of anything. 

Also just because there are facts available doesn't mean that those are all the facts. Again things change, Google used to be for an open mobile web that was a fact, but now they seem to agree (profitably) with Verizon's take on things. 
  
Also it's not very sporting to use name calling as an argument.

Many people have replied to this port already, but as it was aimed at me, I feel that I have to address it anyway.

Madspyman, I'm not even going to respond to your attempt to make this discussion into a philosophical argument, because as much as I like debating philosophy, it's simply not relevant. Lines of code do what they do. You don't have to think about defining truth or knowledge, you can simply read the code to know what it does. It's not even very complicated; anyone with some Bash experience should easily be able to figure out what these particular lines of code do.

I am sorry about the name calling, but you are behaving like a paranoid idiot right now, and I call them as I see them. I hope you're able to see it yourself now.

---

### Post by Madspyman on 2010-08-12
> **NCLI said:**
> The facts are in the code. The open code. Anyone who bothers to have a look at it will quickly see that it's very simple, and not anything to worry about.



Many people have replied to this port already, but as it was aimed at me, I feel that I have to address it anyway.

Madspyman, I'm not even going to respond to your attempt to make this discussion into a philosophical argument, because as much as I like debating philosophy, it's simply not relevant. Lines of code do what they do. You don't have to think about defining truth or knowledge, you can simply read the code to know what it does. It's not even very complicated; anyone with some Bash experience should easily be able to figure out what these particular lines of code do.

I am sorry about the name calling, but you are behaving like a paranoid idiot right now, and I call them as I see them. I hope you're able to see it yourself now.

Agreed I went a bit left field with that post, It's actually from a philosophy paper I wrote good ways back. Got an A on it I might add. 

Anyway, no harm done no hard feelings.

---

### Post by KiwiNZ on 2010-08-12
This thread begs for closure and so be it.

---

