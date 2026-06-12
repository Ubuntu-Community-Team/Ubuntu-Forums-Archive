---
title: "Help With Hacker, Wanna Buy New Ubuntu"
date: 2008-04-03
forum: Security Discussions
---

### Post by OrcaWave on 2008-04-03
This is a VERY long story.

I'll try to keep it short though.

I've had a hacker stalk me for a long time here on the net.

Short story.....I got him fired for putting some of my private medical information on the net.

He worked as the main CT (computer tech) for the hospital where I was a patient.

When the hospital looked, they found that he was not only hacking patient records, but was running a pornography spamming ring with THEIR COMPUTERS!

Our ISP (Mediacom High Speed Internet) even admits that we're hacked (he's using THEIR computers) but refuses to act "because we don't get involved in personal vendetta's".

I've been to the FBI, who surprisingly, knew all about this socio-path, but does not got involved in personal cases (only unless one has a BUSINESS and has been hacked for over $10,000.00 in damages),

After being astounded that the FBI already knew all about him here's what else has happened to us.

After going through six Windows computers, and all of them falling like weeds under a lawnmower, we bought a Mac....it took him NINE MONTHS to learn his way around a Mac, and then he found a back door in our I-Mac G-5, through I-Chat, and Dashboard.

We were using OS X Tiger when this happened. I've heard it all about "Macs CAN'T be hacked", so please don't tell me THAT. It's JUST NOT TRUE.

I'm thinking of switching to a System 76 Ubuntu machine.

But I have questions.

After talking with Tom at System 76 this morning, and telling him our story he said (basically) "I don't know if Ubuntu can do anymore for you than a Mac could do, Mac use's a Linux kernal (I THINK that's what he called it)".

We are using an 'Alpha Shield' external firewall  ( [www.alphashield.com](www.alphashield.com) ) and I had ALL of our Mac locked down tight, and NO sharing applications were turned on.

But the Mac firewall WAS ON! And this guy is so "good", he still managed to find some 'backdoor' into I-Chat and Dashboard.

HOW do I go about super securing a brand new System 76 Ubuntu computer?

I'm thinking of trying THIS wireless router, it's got a double firewall in it:



[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3570079&CatId=373](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3570079&CatId=373)




But there MUST be MORE that I can do yet.

I've heard from reliable sources that Ubuntu is coming out with a firewall in their next update on April 24th, 2008.

Will this be a GOOD and strong firewall, do you think?

A Mac comes with reformat disc, what if you need to wipe the hard drive clean on a Ubuntu machine, can you burn a Ubuntu disc, and use it in the same way that you can in a MacIntosh?

That is, to wipe the hard drive, and to reformat the computer?

Can you please tell me that there is some way to really LOCK DOWN a Ubuntu machine, to where NO ONE can get through it, or is Tom right, and eventually this guy will be able to get through no matter WHAT I DO for security?

If you decide to write back could you please not use 'computerese' and please just say it in plain English (if that's possible, I mean)? Thanks.

I REALLY want to try Ubuntu, and one more thing.

This hacker cuts through Mozilla Firefox like hot butter, so is there another browser to use with Ubuntu that's SAFE do you think?

I'm VERY discouraged from what I heard from System 76 this AM, can you guys help me PLEASE?

Here's the computer that we plan on buying:


Graphics: Intel 950 Graphics Media Accelerator

Sound: Realtek ALC 662 4 Channel Audio

Processor: Core 2 Duo E6420 2.13 GHz FSB 1066 MHz L2 4 MB

Memory: 2 GB - 2 x 1 GB DDR2 667 MHz

Hard Drive: 250 GB SATA 300 Mbps - 7200 RPM 8 MB Buffer

Ottical Drive: First CD - RW / DVD 

Second Optical Drive: CD - RW / DVD

Wireless: 802. 11 bg

Thank you so very much!  Orca Wave

---

### Post by KhaaL on 2008-04-03
Its late here and I just skimmed through your post, but you need to consider this:

if you want a maximum security OS, then FreeBSD is what you want. But it dosen't matter how secure system you get unless you're knowlegable about computer security and am aware of social engineering that can be used to compromise your data.

You maybe should start in that end - raising your own security awareness and knowlege about how computer systems can be compromised.

---

### Post by Sef on 2008-04-03
> f you want a maximum security OS, then FreeBSD

OpenBSD if u want the maximum.

As for security, don't download, flash or java.

---

### Post by |2A|N on 2008-04-03
Get yourself a good hardware firewall and you will never be tampered with on the net again..!

---

### Post by netlogic on 2008-04-03
pfsense if you want a simple installation.

---

### Post by LeChacal on 2008-04-03
The New Firewall that you are speaking of in 8.04 is just a GUI (graphic user interface) for the standard Linux firewall Iptables ( here is a guide for them [http://ubuntuforums.org/showthread.php?t=159661&highlight=shut+down]("http://ubuntuforums.org/showthread.php?t=159661&highlight=shut+down")). You may want to look at them and see if the default setting suit you. I can't speak for the new firewall but there is one called firestarter that has logs that you can look at for questionable  activity. That can help catch things early. Yes a hardware filewall can normally be better if set up right.

I agree with KhaaL that you need to educate your self on security more and you will begin to see holes and things that you can do to protect yourself. I don't agree that FreeBSD is the safest but I don't want to start a flamewar I just have to say that learn your OS inside and out and if you build your own OS like you can basically do with Gentoo or you truly do with LFS (Linux From Scratch) you can make your OS more secure (if you know what you are doing) and to your liking. 

My help to you if you want to learn security set up a machine (it sound like you have several available ) and only do thing with security don't do anything else on because your gone to learn best by playing and reading. Through playing you can trash your machine and going to some website that do security (hacker) info can trash your PC.

And if all that doesn't work you can alway pay a hit man to do your dirty or flee the country.:lolflag:

---

### Post by hyper_ch on 2008-04-04
if you want an unhackable computer then unplug it from the net and put it into your bank's treasure vault...

As soon as you hook up a computer to the net it can be hacked... question is only how difficult you make it for others.

Another thing that you may consider is to have two sets of computers.... ones without sensitive data on it which can access the internet and a complete seperate network for your actual work that is totally cut off the net (those two lans must not be connected in any way other than carrying around files on usb pen drives).

---

### Post by tamoneya on 2008-04-04
why dont you just get a restraining order.

---

### Post by Hallvor on 2008-04-04
> After talking with Tom at System 76 this morning, and telling him our story he said (basically) "I don't know if Ubuntu can do anymore for you than a Mac could do, Mac use's a Linux kernal (I THINK that's what he called it)".

I don`t think Macs use a linux kernel, but a hybrid XNU kernel. Mac is not Linux.

Anyway, you should get some legal advice. Talk to a lawyer (or the local motorcycle gang).

---

### Post by hyper_ch on 2008-04-04
I thought Macs use a Unix kernel...

---

### Post by netlogic on 2008-04-04
It is based around Steve Job's other company, NextStep when he got canned for few years.... Which is mach kernel based around BSD.

---

### Post by The Cog on 2008-04-04
Linux with a firewall will keep an outsider from hacking in. Ubuntu actually installs with no listening services so can't accept incoming connections even without a firewall.

But it will not protect you from downloading and running malware that does things once it gets there. In this category are things like email attachments, trojans that look like free downloads, even flash, javascript and java. Your best protection against these is to use a live CD so that when you finish at the end of the day, any hacking gets undone every day. 

A more complicated way would be to run one Linux in a VM inside another Linux. Use the "host" linux just to run the VM and never connect to the internet. Use the "guest" linux to do all your internet access, but set the VM up to restore the guest disk to a known good image when it restarts, which should give you the security of a live CD without the slowness.

---

### Post by Cannaregio on 2008-04-04
> **OrcaWave said:**
> This hacker cuts through Mozilla Firefox like hot butter, so is there another browser to use with Ubuntu that's SAFE do you think?

Yes, use [opera]("http://www.opera.com/products/desktop/"). Whatever OS you use, use opera.
It's imo the safest and quickest browser around. Try it.

Ubuntu + Opera is a fairly good combination for web browsing impunity, as you will see.

For the rest I agree with what others said: learn your security stuff, understand web-protocols, try various tools by yourself. 
Just to make one example: nmap has more than 30 different parameters: play with it until you learn them all.

After some months, if you do, you will be much more confident and you'll understand the dos and do nots.

Yes it takes months, maybe years, not weeks and not days, whatever OS you'll use.

---

### Post by ameba on 2008-04-04
Make sure your wireless router has a strong password and make sure you use the strongest WiFi protected Access.

He/she might want to come around your house and get you that way.

How certain are you that he/she got into your system via i-chat & or dashboard?

Whats your proof or reasoning? Or, how did you come up with that conclusion?

Your situation, to me at least, sounds exaggerated.

---

### Post by OrcaWave on 2008-04-04
> **ameba said:**
> Make sure your wireless router has a strong password and make sure you use the strongest WiFi protected Access.

He/she might want to come around your house and get you that way.

How certain are you that he/she got into your system via i-chat & or dashboard?

Whats your proof or reasoning? Or, how did you come up with that conclusion?

Your situation, to me at least, sounds exagerated _except_ the medical records part and the pornography.



Ameba,

   Funny. If I posted the whole FIVE YEAR STORY, you'd think that it was some kind of thriller (or spy) movie.

He's in Little Rock, Arkansas (maybe the tornado kicked his a_ _ last night! Here's to HOPING!  lol).

We are in Northern Iowa, very near Minnesota. But I USED to live in Arkansas.

This all started five years ago, when I threw him off a Yahoo e-list that I ran.

Look, he's had our HOME PHONE SERVICE turned off, literally, by using my Social Security number (which he got from my medical records). It took a note from our Family Physician (I have some medical problems) and THREE DAYS for Qwest to turn our phone service back on.

He's gone to my high school website and had me listed as "dead", along with a photograph from our year book (from 1970....he knew where I went to High School).

He's had our home town Police Dept. come to our front door at 1:30 AM in the morning, because (supposedly) I'd been killed in some horrible car crash, all while I was safely sleeping in our bed.

I could go on and on and on, but if you don't believe me ALREADY, what's the point?

And do you wanna KNOW what's double bad about THAT?

Because socio-paths like him THRIVE on doing such outlandish things that they simply WON'T BE BELIEVED.

Right?  You DON'T BELIEVE.

I finally had decide "You know it doesn't make a shi_  load of difference who believes me, or NOT".

My wife KNOWS cause she's been with me through 3 and a half years of this 5 year WAR.

The I-Chat literally turned itself ON, and the ONLY way to shut it off, was to pull the electricity plug from the wall.

I called our Mac tech, who knows our story and believes (he worked on an HP/Windows that we have that this maniac destroyed) us.

He said to put I-Chat in the garbage can and empty it, which I DID.

End of I-Chat problem.

Later on, he found a way into (a back door) Dashboard, so I trashed it too.

No more Dashboard problems.

I know that it's hard to believe, but that's really YOUR problem, which as I said, simply feeds his maniacal behavior.

I could publish the whole story here, but's what's the point?

But frankly, it's a lot BETTER story than 'The Net', Sandra Bullock's old movie!   :-)

Orca Wave

---

### Post by kevross_33 on 2008-04-04
Hey once you have ubuntu have a look at ossec and snort to provide host and network intrusion detection and prevention. If he gets close you can look at the logs and see and ossec can read the logs from snort for network attacks as well as attack patterns on the system and create a firewall block.Also you have agents that you can install on other Linux and Windows devices to watch for attack patterns on them too and feed them to the server (which also acts as a normal agent to protect its itself)

Also have a look at ipcop. It is a dedicated device so is on its own, and old pc with 2 networks cards is fine.

It provides intrusion detection though snort, firewall, VPNs etc. Also you have addons, such as search for mhaddons on google as it provides addons and get guardian and you can select individual snort rules as well as it provides intrusion prevention through created firewall blocks for a period of time. Other features include web proxy, content filtering addons, update caching addons, network antivirus and so on (I don't use the proxy because proxies can become annoying).

Anyhoo with that layer of active response without affecting your connection and usability he will be detected, blocked etc. He will have a particularly hard time compromising your network. 

To get started with ipcop search for "the perfect linux firewall" on google to get up and running and learn how to install addons to improve the default install significantly.

---

### Post by nrcooled on 2008-04-04
That is one hell of a story!  I would agree that if you are serious about this whole thing then you should educate yourself.  Just buying new computers or OSs will just slow him down but not stop him.  

Arm yourself with some knowledge and then start configuring your network to be secure.  Layered defense is the best methodology and since you don't need to provide any remote services or configure a DMZ then it should make it easier.

Don't throw away that G5 quite yet...just build it properly.

---

### Post by FastZ on 2008-04-04
So do you work for the hospital or something?  If wherever you are working has any kind of medical records or sensitive date like that on the network, using wireless should probably be stopped.  It is just way too simple to hack into a wireless network.  Get yourself wired if that's the case.

I saw someone mention ipcop, its worth looking into Smoothwall as well if you are interested in building a dedicated hardware firewall out of one of those computers that you claim he trashed.  Just change out some parts and install the firewall OS and you're on your way to being a lot more secure.  

Like someone else said earlier, just replacing machines isn't going to stop this guy from hacking in and causing you headaches.  You need to actually learn what it means to be secure and learn what it takes to stay on top of security and make it a 24/7 thing that you are thinking about.  Another person said that the only secure machine is one that's turned off...that's absolutely true.

---

### Post by OrcaWave on 2008-04-05
Matt,

  I was A PATIENT in the hospital (in Little Rock, AR.) where I USED to live.

I now live in Iowa.

The hacker lives in Little Rock, Arkansas.

But he continues knowing my social security number (as well as my wife's personal information too), and other personal information about me.

He KNOWS what "lines" not to step over, more or less. Banking or debit cards being our only two kinds of accounts. He knows all about BOTH of them.

But if he DID THAT, THE BANK would MAKE the Feds get involved. And he KNOWS THIS.

Consequently, he doesn't (so far) bother our bank account.

For a total sleeze scumbag, he's pretty smart.

He tried to hack my Pay Pal account, but they caught someone trying to get into it, and closed it.

There's another thread that tells this whole story over in The General section of this Forum.

[http://ubuntuforums.org/showthread.php?p=4646752#post4646752](http://ubuntuforums.org/showthread.php?p=4646752#post4646752)

I hope that I answered your questions here.

Orca Wave

---

### Post by Cannaregio on 2008-04-05
Back to your original questions.
Maybe you should just stop posting kilometers about "your" hacker. 
Your questions are relevant on these forums only insomuch as they apply to [COLOR="Blue"]every[/COLOR] hacking attempt, not just one private case.
And, frankly, you shouldn't use all those uppercase crap either: no need to shout.

> **OrcaWave said:**
> But there MUST be MORE that I can do yet.

There's: read, study and in a couple of months you'll hopefully begin to understand some basic security.

> **OrcaWave said:**
> I've heard from reliable sources that Ubuntu is coming out with a firewall in their next update on April 24th, 2008.

Will this be a GOOD and strong firewall, do you think?

Not particularly "GOOD" nor particularly "strong" (nor your sources seem particularly "reliable"). A firewall is no automatic guarantee anyway. 
Much more important is, for instance, your knowledge in how to manipulate the host file or the [iptables]("https://help.ubuntu.com/community/IptablesHowTo"), duh.

> **OrcaWave said:**
> A Mac comes with reformat disc, what if you need to wipe the hard drive clean on a Ubuntu machine, can you burn a Ubuntu disc, and use it in the same way that you can in a MacIntosh?
That is, to wipe the hard drive, and to reformat the computer?

Macs and GNU/Linux are different beasts, and reformatting isn't necessary, unless you are using toy systems like windows and are at the same time a complete newbee (which you wont do/be either, if you read and study long enough, see above most of the answers to your extremely long postings). "Can you buy an Ubuntu disk?". Your need to study is immense.

> **OrcaWave said:**
> Can you please tell me that there is some way to really LOCK DOWN a Ubuntu machine, to where NO ONE can get through it, or is Tom right, and eventually this guy will be able to get through no matter WHAT I DO for security?

It depends. Short answer is no. In fact I would say he will surely be able to get through, no matter behin which OS you'll hyde, since, as stated,  knowledge and hence defence capacities are inversely proportional to paranoia, yet you do seem to enjoy the latter most.

> **OrcaWave said:**
> I REALLY want to try Ubuntu

Be REALLY our guest, and go ahead if this is true. But my impression is that you just want to speak loudly about your hacker.

---

### Post by steveneddy on 2008-04-05
This is a multiple thread.

Someone merge this with the [other thread of the same name.]("http://ubuntuforums.org/showthread.php?t=744563")

[COLOR="Red"]**Please don't double post!**[/COLOR]

---

### Post by 3rdalbum on 2008-04-05
1. Having the Mac OS firewall turned on doesn't mean diddly-squat. It still lets incoming connections through on multiple ports, even when it's turned onto its most restrictive settings.

2. There's not really any such thing as a "good and strong" firewall. A firewall's job is to drop incoming connections. Either it drops the connections, or it doesn't. If it drops the connections, it's a firewall. If it doesn't drop the connections, it's not anything. Check that your firewalls are configured to block incoming connections.

3. If your story of the attacker is as you say, then he is intercepting internet traffic before it reaches you. ("man in the middle attack"). There's probably not a lot you can do, as all internet traffic coming into your computer would be untrusted. The best thing to do would be to gather evidence that he is causing your problems, and put him behind bars.

4. Ubuntu would probably hold out longer than the Mac. Apple aren't very good at security.

5. I don't believe your story anyway.

---

### Post by OrcaWave on 2008-04-05
Thanks for your reply, and your help.

But your an Aussie.

This America, I wouldn't expect you to understand, nor believe, unless you've actually lived here.

OW

---

### Post by OrcaWave on 2008-04-05
Ok, let me tell you what I have learned.

I'm responsible for the security of whatever OS that I use.

Ubuntu, Mac...whatever.

After all of these posts, I've finally figured that out.

Yes, all that I've had as "a weapon" is free speech.

David can't stop me from posting about his nefarious activities.

Do I "enjoy" this? Not really. But I *can see* how it might look that way.

Do I think that there is "a spiritual side" to this......"Why do I need this in my life" I think the quote was.

Yes, I'm a firm believer that there's way more than we see with just our physical eyes.

Did I "draw" this to me somehow.........Richard Bach, in his great book 'Illusions', might have 'Donald Shimoda' ask me.

Yes, maybe I did.

I've not totally finished processing just *why* yet.

Have I gone to a good counselor about this?

Yes. Several times. And yes, I was believed as to this being true.

Look, here's the bottom line. 

I know a sure proof way to put this man into prison, but it involves my wife's work computer which she has at home.

Until she will allow me to go to the hospital who she works for, all I can change is *my own computer*.

She's *my wife* and unless she says "Yes, go and talk to them", I can't act on my own.

So, you've all helped me alot, and now it's time for me to help *myself*.

I always thought:

"Well, this piece of hardware will fix it." Or, "If I have this kind of computer it will fix the problem".

But that's not the solution at all, the solution is get up off my butt, and really learn computer security, from the ground up.

Is that scary? Yeah, kind of.

Might it be worth it in the end?

Absolutely!

To those who have not believed. Someday it could happen to *you*.

To the rest of you, thank you so much for being strong with me. I *really* appreciate it!

I needed it, and I didn't even know that I needed it!

That's kind of sad isn't it?

I've been so involved in this for so long, that I actually never really understood what I really needed to do. The main thing (learning computer security from the ground, up), I mean.

Thanks for showing me that.

And I will rent "The Secret', movie tonight. thanks.

Bless you all, Orca Wave

---

### Post by jba6511 on 2008-04-07
simple: hire a penetration tester to do an assessment and tell you where you are vulnerable. Than plug these holes. Also, they can provide you with appropriate settings and help set up an IPS. You should also be keeping detailed logs on another server that are backed up and written to a write once media. Instead of spending all this money on new equipment, why not just get an assessment and secure what you have and are comfortable working with. Than use applications such as Nessus to scan when changes are made to the network and remember to keep up with your patches. If you want to learn more about security yourself, take a look at some of the courses offered by SANS, the Security+ from CompTIA and the courses offered by Offensive Security (makers of BackTrack).

---

### Post by ameba on 2008-04-11
OrcaWave  OrcaWave is offline
5 Cups of Ubuntu
	  	
Join Date: Mar 2008
Beans: 25
Thanks: 0
Thanked 0 Times in 0 Posts
Re: Help With Hacker, Wanna Buy New Ubuntu
Thanks for your reply, and your help.

But your an Aussie.

This America, I wouldn't expect you to understand, nor believe, unless you've actually lived here.

OW



_Thats an ad homien attack.... Your very illogical thinking that he wouldn't understand because he's Austrailan._

Why would you go to a counselor over something soo small. BRAIN-WASHED

What if ubuntu fails you? What are you going to do then?

Are you going to live in a padded room with a straight jacket on???

---

### Post by OrcaWave on 2008-04-11
Your absurd.

Try going through people telling YOU that your nuts over and over again.

Counseling is a *good thing*. Snipe at counseling if you like. Whatever.

What will I do if Ubuntu FAILS TOO?

Just what I''m doing right here.

I'll work on an old Panther machine. Which he HASN'T been able to kill off yet.

But the SEVENTH TIME, *WILL BE* the charm.

Ubuntu WILL work!

I got him FIRED from his job.

I got him FIRED from being a "Minister" in the Arkansas Dept. of Corrections.

I sicked the IRS on him.

And to be quite HONEST. I'm NOT finished YET!

I DO keep a loaded gun within easy reach.

And I don't "Live in a padded room" now.

Why should I THEN (If "then" even comes!), Bozo?

---

### Post by The Tronyx on 2008-04-12
> **jba6511 said:**
> simple: hire a penetration tester to do an assessment and tell you where you are vulnerable. Than plug these holes. Also, they can provide you with appropriate settings and help set up an IPS. 

That is a relatively absurd suggestion.  Do you know how much it costs to hire a pen tester?

---

### Post by Siph0n on 2008-04-12
No, how much DOES it cost??? :)

---

### Post by netlogic on 2008-04-12
You can't really price these things out like this. Sometimes, you need to hire third party developers to modify open source apps. Also, many engineers might be needed to complete the project. It also affects who is your client. 

The range can be anywhere from $750 to $175,000 (one hr to entire week). Most large companies only test once every two years, so it isn't a high cost for them.

---

### Post by The Tronyx on 2008-04-12
> **Siph0n said:**
> No, how much DOES it cost??? :)

A skilled pen tester, if working hourly can command anywhere from $200-$300 an hour.

---

### Post by Mindless Automata on 2008-04-12
Something is strange here.

1)  Why would you go to the FBI, and apparently not sue?
2)  The hacker caused you thousands of dollars in computer damage?  How did a hacker destroy your hardware without physical access to the box?  Last I checked this isn't really possible.
3)  How is this guy getting your IP address?  HOW IS HE FINDING YOU?
4)  Then you talk about watching a new-age claptrap movie... ("The Secret")?

Either you're a troll, or you're so inept at computers that you think you're being hacked and you're not.  There's no magic with computers.

If you're being sincere, my guess is you're a middle-aged woman with a poor understanding of computers and technology.  We can't help you here; the best remedy is reading up on computers and using them, and learning about them.  If this is true you're probably being phished or you have an unsecured wireless connection.  Security depends not just on computer and its programs but the person behind the computer, too.

---

### Post by netlogic on 2008-04-12
> **OrcaWave said:**
> Your absurd.
Try going through people telling YOU that your nuts over and over again.
Counseling is a *good thing*. Snipe at counseling if you like. Whatever.
What will I do if Ubuntu FAILS TOO?
Just what I''m doing right here.
I'll work on an old Panther machine. Which he HASN'T been able to kill off yet.
But the SEVENTH TIME, *WILL BE* the charm.
Ubuntu WILL work!
I got him FIRED from his job.
I got him FIRED from being a "Minister" in the Arkansas Dept. of Corrections.
I sicked the IRS on him.
And to be quite HONEST. I'm NOT finished YET!
I DO keep a loaded gun within easy reach.
And I don't "Live in a padded room" now.
Why should I THEN (If "then" even comes!), Bozo?

I finally got around and reading  the whole thread. The certain aspect of your story really doesn't fit in a real life scenario.  I can't really accuse you, but the tone of your structure isn't convincing. However, the unusual aspects of human life does occur in the most unpredictable way. Also, it is hard to judge or read off someone only through a set of text a person has written.

I am sure you heard it before and others have said it. Many security flaws can be prevented from a basic understanding.

1. knowledge
2. protection of network service 
3. protecting your flaws in the application
4. physical protection
5. encrypting important data

The simple aspect of knowledge is to be very suspicious.  Don't reply or click on any items received from people you don't know.  You should try to understand how phishing attacks can occur. Also, understand the limited security protection that browser can offer. For an average person, number two is out of their area of focus. They can only protect themselves with a simple firewall configuration. Programmers make mistakes just like anyone. Many applications go through many stage of security flaws. The complex layers of libraries in many systems can cause many issues. It is notable that Windows and OSX have many great areas of plug and play concept, in return they provide automations that can create a security concerns. Automations mean attackers can predict the result of an Operating System by feeding the information that automate the attackers outcome. Having various unpatched applications can unpredictable behaviors  to phising attacks. The issue with this area is not every applications are discovered for the areas of suspicions. In the past few years, both white and black hat hackers gain financial rewards by not notifying their discoveries. White hat might need some bags of trick to gain notable accomplishment for their client. Black hats might not notify to increase in their payoffs. The good rule to follow is don't click or use anything from people you don't know. If you feel something isn't right, don't proceed. It is really important to understand, if others have the physical access and the machine isn't properly set for encrypting important volumes such as var, home, etc, and tmp, it almost certain all your security is comprised.

---

