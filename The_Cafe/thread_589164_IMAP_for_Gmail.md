---
title: "IMAP for Gmail"
date: 2007-10-23
forum: The Cafe
---

### Post by p_quarles on 2007-10-23
Gmail just added IMAP support for e-mail clients. Anyone using a gmail account on multiple devices should definitely appreciate this.
[http://mail.google.com/support/bin/answer.py?ctx=gmail&hl=en&answer=75725](http://mail.google.com/support/bin/answer.py?ctx=gmail&hl=en&answer=75725)

---

### Post by southernman on 2007-10-24
That should make a few people happy! 

:)

---

### Post by Macintosh Sauce on 2007-10-24
[COLOR="Sienna"]Thanks for the info. My wife and I use Gmail a lot, so having IMAP access is really nice.[/COLOR]

---

### Post by Dybber on 2007-10-24
Can anyone get it to work in Evolution? I can't.

EDIT: Restarting Evolution made it show up.

---

### Post by Phil Airtime on 2007-10-24
It hasn't been activated on the "Google Apps for My Domain" (not *my* domain!) that I use. It seems that upgrades don't get sent to that service for some reason; I still have 2048MB of space.

---

### Post by kanem on 2007-10-24
I have a general question about IMAP and google has only helped a little so far. 

The first advantage I see quoted is the ability to use multiple clients. So does anyone know how it would handle the following situation: 

One night I check my email. Later, the net goes down. I go back and read some more email and make some changes (delete some, move some to other folders etc). Then I turn off the computer. The next day at work I check my email. Obviously, the changes I made at home (after the net went down) are not going to show up here. I do some more changes to my inbox at work. When I get home and turn on my computer and fire up my email client what happens? Do the changes I made when the net was down get overwritten? Does the server try to reconcile the two?

---

### Post by MemoryDump on 2007-10-24
I just tried to get it going with Thunderbird and no luck so far even though I've enable the IMAP function in my Gmail account :(

says cannot connect to imap.google.com

---

### Post by p_quarles on 2007-10-24
> **MemoryDump said:**
> I just tried to get it going with Thunderbird and no luck so far even though I've enable the IMAP function in my Gmail account :(

says cannot connect to imap.google.com
You'll need to create new IMAP account, since TB doesn't allow you to change the connection protocol on existing accounts. Once you do that, restart, check e-mail, and it will sync with the server.

---

### Post by MemoryDump on 2007-10-24
> **p_quarles said:**
> You'll need to create new IMAP account, since TB doesn't allow you to change the connection protocol on existing accounts. Once you do that, restart, check e-mail, and it will sync with the server.

hmm.. that is what I did.. I removed the old account I had and created a new account using the setting provided by the Gmail help files.

[http://mail.google.com/support/bin/answer.py?answer=77662](http://mail.google.com/support/bin/answer.py?answer=77662)

---

### Post by hanzomon4 on 2007-10-24
what does imap do?

---

### Post by p_quarles on 2007-10-24
> **hanzomon4 said:**
> what does imap do?
It synchronizes the server with the e-mail client. POP servers by default only allow you to download a message to one e-mail client. IMAP allows you to keep the same folders, with the same contents, on multiple machines.

---

### Post by Zdravko on 2007-10-24
DOES IT DOWNLOAD THE SENT ITEMS??? This is VERY important for me!

---

### Post by Inxsible on 2007-10-24
Not having IMAP was one of the reasons, why I stopped using clients for my GMail accounts.

The other reason was the threading of related emails. I am so used to this feature that i just find it odd otherwise. Hopefully some client will be able to thread emails like GMail does.

I know Thunderbird has threading...but it threads on subject line...which bunches unrelated mails together and makes it even harder to find especially when I get un-related emails without a subject line in both of them.

---

### Post by MemoryDump on 2007-10-26
I still can't get Thunderbird to read my Gmail messages using IMAP! Just says can't connect to imap.google.com :(

---

### Post by Zdravko on 2007-10-26
> **Zdravko said:**
> DOES IT DOWNLOAD THE SENT ITEMS??? This is VERY important for me!
Bump!

---

### Post by samir85 on 2007-10-26
> **Zdravko said:**
> 
DOES IT DOWNLOAD THE SENT ITEMS??? This is VERY important for me! 

Bump! 

It does.

---

### Post by Zdravko on 2007-10-26
> **samir85 said:**
> It does.
Thank you very much for the concrete answer. I had been waiting for years for this option! May God bless Google!
:guitar::guitar::guitar:

---

### Post by MemoryDump on 2007-10-26
I still can't get this to work with Thunderbird.. has anybody been able too under Gutsy?

I can ping the address:
ping imap.gmail.com
PING gmail-imap.l.google.com (72.14.205.109) 56(84) bytes of data.
64 bytes from qb-in-f109.google.com (72.14.205.109): icmp_seq=1 ttl=247 time=101 ms
64 bytes from qb-in-f109.google.com (72.14.205.109): icmp_seq=2 ttl=247 time=20.6 ms
64 bytes from qb-in-f109.google.com (72.14.205.109): icmp_seq=3 ttl=247 time=117 ms


however I can't connect to it... just keeps on spitting:
"failed to connect to server imap.google.com"

I removed my .mozilla-thunderbird and redid everything and still no go... this is frustrating!! :(

---

### Post by p_quarles on 2007-10-26
> **MemoryDump said:**
> I still can't get this to work with Thunderbird.. has anybody been able too under Gutsy?

I can ping the address:
ping imap.gmail.com
PING gmail-imap.l.google.com (72.14.205.109) 56(84) bytes of data.
64 bytes from qb-in-f109.google.com (72.14.205.109): icmp_seq=1 ttl=247 time=101 ms
64 bytes from qb-in-f109.google.com (72.14.205.109): icmp_seq=2 ttl=247 time=20.6 ms
64 bytes from qb-in-f109.google.com (72.14.205.109): icmp_seq=3 ttl=247 time=117 ms


however I can't connect to it... just keeps on spitting:
"failed to connect to server imap.google.com"

I removed my .mozilla-thunderbird and redid everything and still no go... this is frustrating!! :(
Have you changed the settings on your gmail account? You need to use the web interface to do that before you'll be able to connect. 

Also, they're rolling it out slowly, because initial imap connections can eat huge amounts of bandwdth. You may not have the option of switching yet.

---

### Post by MemoryDump on 2007-10-26
> **p_quarles said:**
> Have you changed the settings on your gmail account? You need to use the web interface to do that before you'll be able to connect. 

Also, they're rolling it out slowly, because initial imap connections can eat huge amounts of bandwdth. You may not have the option of switching yet.

yeah.. I checked that and doubled checked..

I've attached a few screenshots... I'm no I'm not going nuts.. or am I.. :lolflag:

---

### Post by p_quarles on 2007-10-26
Change the servername in thunderbird to:
```
imap.gmail.com
```

---

### Post by MemoryDump on 2007-10-26
> **p_quarles said:**
> Change the servername in thunderbird to:
```
imap.gmail.com
```

wow.. I truly am an idiot... DOH!!! :(

thanks a bunch.. I'll go bury my head in the ground for a while.. ):P

---

### Post by element on 2007-10-26
I cant connect to imap.gmail.com either.

---

### Post by p_quarles on 2007-10-26
> **MemoryDump said:**
> wow.. I truly am an idiot... DOH!!! :(

thanks a bunch.. I'll go bury my head in the ground for a while.. ):P
Nah, it's easy to miss stuff like that. I stared at your screenshots for several minutes, trying to figure out why the heck it wasn't connecting. Only noticed that as I was about to close them and give up. :)

---

### Post by ThinkBuntu on 2007-10-26
POP for me. I need my email fetched all at once (for when I don't have internet), not just the headers.

---

### Post by Zdravko on 2007-10-26
What do you mean with the headers?
BTW, I don't have the IMAP option yet :(

---

### Post by p_quarles on 2007-10-26
> **ThinkBuntu said:**
> POP for me. I need my email fetched all at once (for when I don't have internet), not just the headers.
That's ideal if you're just checking e-mail on one computer. You do know, though, that Thunderbird can be set to automatically download imap folders for offline use?

---

### Post by chronusdark on 2007-10-26
evolution keeps giving me permission errors does thunderbird run any better?

---

### Post by Joeb454 on 2007-10-26
The only reason I don't use the IMAP function is because I delete all the sent emails from my client unless I've sent them to myself (created a rule, much easier :p)

Unless anybody knows how I can keep this in IMAP without actually deleting them on the server then I'll have to stick with POP :(

---

### Post by ben::zen on 2007-10-26
Is anyone else trying this/succeeding with KMail? I'm wondering because it works just fine with POP, but when I go to try IMAP, it doesn't work. I *do* have the option, it is enabled.

---

### Post by p_quarles on 2007-10-27
Yeah, I've got kmail working with it fine on my laptop. I will say, though, that Thunderbird (on my desktop) took quite a bit less time to sync than kmail did. Not sure why.

Anyway, if you want to post the config details from kmail, I'll be happy to compare them with mine.

---

### Post by Spr0k3t on 2007-10-27
This is one of the features I've been waiting for on gmail.  I'll have to get this set up when I get home.

---

### Post by blom on 2007-10-27
I'm not sure if anyone else has seen this problem, but I've configured evolution to use IMAP against my gmail account and it doesn't seem to play very nicely.  While I'm able to read my emails, they don't get marked as read when I do, they don't get deleted when I delete them, and when I try to exit Evolution is just hangs.

So not really what I'm after really ;)

---

### Post by Sasank on 2007-10-27
I am having the same problem as described by MemoryDump.

My thunderbird says, Connection to server imap.gmail.com timed out.

Anybody else solved this? Thunderbird is not even prompting me for a password, so I am guessing that it might be problems with gmail servers. But I am able to ping them. 

Please post if you solved this.

---

### Post by tduermeier on 2007-10-27
I'm having the same problems as those described above with all the settings in correctly for Thunderbird 2.0.0.6 (20071022) on Gutsy (imap.**gmail**.com, SSL, port 993, IMAP enabled via web browser).  Has anyone had any luck getting around this?  I can't seem to find any error on my end, could it be problems on google's end?

---

### Post by Bou on 2007-10-30
I haven't still gotten the option to use IMAP. How long is this supposed to take? Why are they activating some accounts, but not others?

---

### Post by Zdravko on 2007-10-30
> **Bou said:**
> I haven't still gotten the option to use IMAP. How long is this supposed to take? Why are they activating some accounts, but not others?
The same here! :mad:

---

### Post by kentl on 2007-10-30
They always roll out every new feature gradually. In a sense the ones getting the option early act as beta-testers. Maybe you should be glad that you haven't gotten it yet? So you don't have to fight any quirks they still need to solve.

Personally I've gotten it. But I'll bide my time and use it one week or more from now. In that time I'll also try to grow into the mental state needed to try and install Mutt. ;)

---

### Post by ButteBlues on 2007-10-30
> **Zdravko said:**
> The same here! :mad:
Same. "Over a week" my ****.

---

### Post by Zdravko on 2007-10-30
Why don't we write a complaint against gmail? We are discriminated!

---

### Post by happysmileman on 2007-10-30
One of my accounts is able to use IMAP now, however it happens to be the account I never use (as opposed to the account I almost never use) and don't even have SMTP set up for it. I'll wait until both are able to use IMAP before bothering to switch

---

### Post by whatrucrazy on 2007-10-30
I'm having the same issues with imap on gmail using thunderbird 1.5, it attempts to connect for a minute or so then just times out without having connected to imap.gmail.com.

Using Fiesty
Have enabled imap in the gmail settings
Have configured thunderbird properly, right ports and servers
Using a new thunderbird account not an existing one
Reinstalled thunderbird just in case.
No luck.

I thought for a week that I must have typed something wrong when configuring it, but so glad to see its not just me after reading it over and over and over... it's restored my faith in myself!

Google, do no evil eh... ha!

I was thinking of emailing someone at google but couldn't find any clear contacts, if anyone can, or knows whats going please post here.

thanks

---

### Post by Dragonbite on 2007-10-30
This is soo cool of news!  Now if only they would connect their Calendar too so Outlook / Evolution could run as much like a full Exchange Server as possible!!

Btw.. I copy-pasted the Configuration settings for "other clients", which I found at [[COLOR="Blue"]http://mail.google.com/support/bin/answer.py?answer=78799[/COLOR]]("http://mail.google.com/support/bin/answer.py?answer=78799")
> Configuring other mail clients 

You can use the following information to configure IMAP with many mail clients. If you encounter difficulties, we suggest contacting your mail client's customer support department for further instructions -- we're unable to provide assistance with configuring mail clients not listed [[COLOR="Blue"]here[/COLOR]]("http://mail.google.com/support/bin/answer.py?answer=75726"). Incoming 

**Mail (IMAP) Server - requires SSL:**	imap.gmail.com
**Use SSL:** Yes
**Port:** 993 
**Outgoing Mail (SMTP) Server - requires TLS:**	smtp.gmail.com (use authentication)
**Use Authentication:** Yes
**Use STARTTLS:** Yes (some clients call this SSL)
**Port:** 465 or 587 
**Account Name:** 	your Gmail username (including @gmail.com) 
**Email Address:** 	your full Gmail email address (username@gmail.com) 
**Password:** 	your Gmail password 


Please note that if your client does not support SMTP authentication, you won't be able to send mail through your client using your Gmail address.

I look forward to seeing if I can get Evolution to run it. :)  Wonder if KMail can connect to it?

COOOOOLLL....
Just got it working, using the above settings, in Opera.
One thing to remember is that after you set up the account initially, you usually have to go into the account settings to modify the Port# and other settings.  While the outgoing port was correct, the incoming port number is different than the default was.

---

### Post by hkgonra on 2007-10-30
> **Zdravko said:**
> Thank you very much for the concrete answer. I had been waiting for years for this option! May God bless Google!
:guitar::guitar::guitar:

BTW, Pop access on gmail downloads sent items as well, most pop e-mail does not work that way but gmail does.

---

### Post by Zdravko on 2007-10-30
[hkgonra]("http://ubuntuforums.org/member.php?u=152740"), I am not sure about this. But IMAP must be much better. I wish I had it now.

---

### Post by hkgonra on 2007-10-30
> **Zdravko said:**
> [hkgonra]("http://ubuntuforums.org/member.php?u=152740"), I am not sure about this. But IMAP must be much better. I wish I had it now.

I am sure about it, been using if for over a year now. 
You are right though IMAP is better. 
The google POP is I guess a hybrid of normal POP and IMAP.

---

### Post by Dimitriid on 2007-10-30
Well my account still has no "imap" to enable. What is this "select accounts" #(!(@(%& anyway? Either have an opt in beta or wait until you can offer to all, this is just pathetic.

---

### Post by Zdravko on 2007-10-30
Well, as I said - I feel discriminated! Why do other people deserve IMAP and I don't?

---

### Post by Dimitriid on 2007-10-30
Right on. They obviously like to play favorites. Im dumping my gmail account altogether, I had enough of greedy ******* corporations like google or microsoft, I wont touch anything they do.

---

### Post by p_quarles on 2007-10-30
Umm, guys, I *seriously* doubt that the basis for rolling out IMAP availability is anything other than random. As someone pointed out, Google typically releases things in increments. 

As I pointed out earlier, too, synchronizing an IMAP account for the first time is a pretty large job -- it eats up bandwidth and server resources. Given the amount of space gmail allots to each user (~4 GB), I'm kind of guessing they *couldn't* make this option available to everyone all at once.

---

### Post by samir85 on 2007-10-30
> **Dimitriid said:**
> Well my account still has no "imap" to enable. What is this "select accounts" #(!(@(%& anyway? Either have an opt in beta or wait until you can offer to all, this is just pathetic.

My account doesn't have the IMAP enable option too, but IMAP is working anyway :D

---

### Post by Dimitriid on 2007-10-30
> **p_quarles said:**
> Umm, guys, I *seriously* doubt that the basis for rolling out IMAP availability is anything other than random. As someone pointed out, Google typically releases things in increments. 

As I pointed out earlier, too, synchronizing an IMAP account for the first time is a pretty large job -- it eats up bandwidth and server resources. Given the amount of space gmail allots to each user (~4 GB), I'm kind of guessing they *couldn't* make this option available to everyone all at once.

Excuse me but do you work for google? Otherwise why are you making excuses for them? If they cant handle IMAP they don't have to offer IMAP instead of just let the users feel cheated. If they want to test it out guess what? There is such a thing as an **opt in beta test** when you know there will be a set amount of people allowed, not random ******** like this.

So why should I keep my email with them? So they can keep scanning my emails for adds? So that they can keep compromising my personal information? So that I have to wait for functionality? I rather have another account even if it gives me 5mb of space but at I know what I get.

---

### Post by p_quarles on 2007-10-30
> **Dimitriid said:**
> Excuse me but do you work for google? Otherwise why are you making excuses for them? If they cant handle IMAP they don't have to offer IMAP instead of just let the users feel cheated. If they want to test it out guess what? There is such a thing as an **opt in beta test** when you know there will be a set amount of people allowed, not random ******** like this.

So why should I keep my email with them? So they can keep scanning my emails for adds? So that they can keep compromising my personal information? So that I have to wait for functionality? I rather have another account even if it gives me 5mb of space but at I know what I get.
What's your problem? You accused Google of "playing favorites," and I pointed out that there are other, more logical reasons for why they would roll out IMAP in waves. So now you say I'm "making excuses for them." Seriously: chill out. Gmail is not something to get upset about. 

In re: "handling IMAP," though, I'll repeat my point: daily IMAP use takes up no more or less server resources than POP. It's the initial connection to the client that uses a great deal more.

---

### Post by AaronMiller on 2007-10-30
I've been waiting for this for so long. I get to sync my work, windows, linux, and laptop all together! Hooray!

Too bad I can't enable it yet.:(:(:(:(:(:(

---

### Post by Dimitriid on 2007-10-30
> **p_quarles said:**
> What's your problem? You accused Google of "playing favorites," and I pointed out that there are other, more logical reasons for why they would roll out IMAP in waves. 

They are not logical. They are excuses. If they cant handle the extra load don't release it, period. Now stop talking to me.

---

### Post by misfitpierce on 2007-10-30
Im good with POP lol :)

---

### Post by Phil Airtime on 2007-10-30
> **Dimitriid said:**
> They are not logical. They are excuses. If they cant handle the extra load don't release it, period. Now stop talking to me.

Handbags at dawn...! Seriously, if it's upsetting you that much, go and pay for an IMAP email inbox at a hosting company.

---

### Post by p_quarles on 2007-10-30
> **Dimitriid said:**
> They are not logical. They are excuses. If they cant handle the extra load don't release it, period. Now stop talking to me.
I'm sure their servers could handle it (they do have some pretty impressive data centers, after all), but it would slow everything down. To me, it seems much more reasonable to release it incrementally than either to release it all at once or not offer it all. 

Again, I'm not making excuses for Google. I'm speaking simply as someone who knows a thing or two about servers.

---

### Post by psusi on 2007-10-30
IMAP so rocks POP.

---

### Post by Buffalo Soldier on 2007-11-05
Reporting Gmail's IMAP working perfectly with Evolution :)

---

### Post by balthamaisteri on 2007-11-05
I can't see that IMAP option unless i turn my language to English (US), but it still works.

Only thing that makes me cry is that i cannot see Ä and Ö letters on my gmail messages :D i can see them on other accounts that are usin IMAP. 

I am usin Thunderbird 2.0, please help me :)

---

### Post by p_quarles on 2007-11-05
@balthamaisteri: That really sounds like a bug with gmail, rather than anything with Thunderbird. They must have a bug report system somewhere. You could file a report with them, and there might even be a workaround if someone else already has.

---

### Post by mpiktas on 2007-11-06
I can confirm that it works perfectly with Thunderbird 2.0 on Feisty (no Gutsy for me, because of ATI). Evolution works, but does have some problems. I have a lot of emails in Gmail, and Evolution does not cope easily with it. It always archives the folders, which takes ages, and the only way to close it is to use killall evolution. And yes there is a bug with encodings in gmail. Some emails do not display correctly in imap, but correctly in browser.

---

### Post by Zdravko on 2007-11-06
I still have this option not enabled. :cry:

---

### Post by hkgonra on 2007-11-06
> **balthamaisteri said:**
> I can't see that IMAP option unless i turn my language to English (US), but it still works.

Only thing that makes me cry is that i cannot see Ä and Ö letters on my gmail messages :D i can see them on other accounts that are usin IMAP. 

I am usin Thunderbird 2.0, please help me :)

They said on the gmail website somewhere that right now the IMAP option is only available in English but is coming soon to other languages.

---

### Post by Phil Airtime on 2007-11-06
Brilliant; it's been added to the Google Apps domain I use as my main mailbox. No more convoluted forwarding to use Evolution!

---

### Post by Bou on 2007-11-07
> **hkgonra said:**
> They said on the gmail website somewhere that right now the IMAP option is only available in English but is coming soon to other languages.

Yup, I set my gmail account to US English and the option appeared. It seemed to be already activated, anyway.

The thing is, it doesn't seem to play very nicely with Evolution does it?

[IMG]http://img453.imageshack.us/img453/9669/pantallazo1sh8.png[/IMG]

You see how the inbox (green-coloured) appears twice, as do the trash (red-coloured) and spam (blue). There are also folders for drafts and sent items, which already appear elsewhere. And these folders cannot be deleted.

Is there a chance to get rid of them and just use Evolution's settings for drafts, trash and so on?

---

### Post by Zdravko on 2007-11-07
My language is set to UK currently. I don't want to change it!

---

### Post by Bou on 2007-11-07
> **Zdravko said:**
> My language is set to UK currently. I don't want to change it!

You just have to change to US for a minute so that the option appears and you can turn it on. If you then change back, it'll stay on.

---

### Post by Zdravko on 2007-11-07
I will wait until I get it officially.

---

### Post by steve k on 2007-11-07
> **mpiktas said:**
> I can confirm that it works perfectly with Thunderbird 2.0 on Feisty (no Gutsy for me, because of ATI). Evolution works, but does have some problems. I have a lot of emails in Gmail, and Evolution does not cope easily with it. It always archives the folders, which takes ages, and the only way to close it is to use killall evolution. And yes there is a bug with encodings in gmail. Some emails do not display correctly in imap, but correctly in browser.

This is working out the same way for me too: it's taking forever to just USE it with Evolution.  Is there a work around or some way we can get evo. to stop archiving everything every time?  Can we turn something off?  Anyone know?

---

### Post by Lostincyberspace on 2007-11-07
> **Joeb454 said:**
> The only reason I don't use the IMAP function is because I delete all the sent emails from my client unless I've sent them to myself (created a rule, much easier :p)

Unless anybody knows how I can keep this in IMAP without actually deleting them on the server then I'll have to stick with POP :(

Yes creat a folder to in your account and set up a filter with the clients name or address and a week or something that auto moves the mail. you can edit so you only have one filter also. and if you ever need to find an email just go to the folder and it will be there

---

### Post by Dragonbite on 2007-11-08
At home I set up the IMAP with Opera on my laptop and over dial-up.  

It was slow but I knew that it would be (for downloading at least) the thing that got me was that as I was typing, there was close to 0.5-1 per keystroke.  The only thing that sped it up was moving my cursur around the screen.

Now I don't know if it was the dial-up, or the low powered laptop (TinyMe (PCLOS) P MMX 233MHz 128Ram).  Has anybody encountered anything like this?  Especially, has anybody encountered anything like this over dial-up?

---

### Post by gasparov on 2007-11-15
Hi,
   it is supposed to work like this, this is made in order to keep gmail functionalities:
if you move an email message to a GMAIL folder you apply a label on it!!!

---

### Post by whatrucrazy on 2007-11-28
Solution!!

So I couldn't access gmail through thunderbird (see my earlier post in this thread) and it turns out that's because I had moblock installed: its a p2p filesharing tool to stop downloads from dodgy sites, like RIAA run sabotaging and IP address collecting peers. The problem is that it doesn't play nice with other firewall type programs like iptables and such.
 
uninstall it - via synaptic if you like - and hey presto its all good in gmail town.

good luck if that's your problem. the only reason I found it was because after a while I couldn't even access google, gmail or a whole load of web pages (not just mail servers) through my system - it was in the process of solving that problem that I realised it was probably what cause the gmail issues.

happy now.

---

### Post by jpc2769 on 2008-03-28
> **whatrucrazy said:**
> Solution!!

So I couldn't access gmail through thunderbird (see my earlier post in this thread) and it turns out that's because I had moblock installed: its a p2p filesharing tool to stop downloads from dodgy sites, like RIAA run sabotaging and IP address collecting peers. The problem is that it doesn't play nice with other firewall type programs like iptables and such.
 
uninstall it - via synaptic if you like - and hey presto its all good in gmail town.

good luck if that's your problem. the only reason I found it was because after a while I couldn't even access google, gmail or a whole load of web pages (not just mail servers) through my system - it was in the process of solving that problem that I realised it was probably what cause the gmail issues.

happy now.

I am having the same problem, but I do not have any firewall installed, nor do I have moblock. Can anyone help me out?

---

### Post by aaaantoine on 2008-03-28
I had been using it for a couple of weeks, but for the past few days I've been unable to connect to smtp.gmail.com.  In other words, I can receive mail in Evolution, but can't send any.

It could be because of a location change.  At any rate, I'll be tying up a Firefox tab for a few days and try Evolution again afterwards to see if the problem goes away.

---

