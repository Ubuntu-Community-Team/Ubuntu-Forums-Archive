---
title: "My WinXP got infected after 23 minutes of being conected."
date: 2006-07-22
forum: The Cafe
---

### Post by Cyraxzz on 2006-07-22
There is this one game i like that does not run well under Wine. I decided to install WinXp on my old Machine. Shortly after the installation i activated the Windoze firewall and visited ATI to download the video driver, also visited microsoft.com to get some required driver for it. shortly after that I saw some unusual programs in task manager, i installed an anti-virus program from one of my USB memory chips, updated it and performed a scan and it found 2 threats. The firewall in my router was also active.

talk about insecurity...

---

### Post by BigDave708 on 2006-07-22
I'm actually speechless. I'm amazed it happened that quickly . . . 

You sure there's no other way a threat could have creaped in? Maybe from your USB drive?

---

### Post by scxtt on 2006-07-22
could you be a bit more vague? 

. . . "unusual programs" . . . "2 threats" . . . this sounds like FUD to me ...

:p

---

### Post by Engnome on 2006-07-22
Tip: pull the ethernet plug when you start your windows machine and download drivers from linux and transfer with usb thumb drive. I try to connect my wintendo box to internet as little as possible.

---

### Post by mips on 2006-07-22
Hmm, the way to do this is to download your drivers, anti-virus, firewall etc before you install windows to a clean flash stick, make sure you have the latest versions.

Disconnect the computer from any network, now install windows followed by the above extras. You will not have problems doing it this way. Afterwards you can connect to the net and get your updates.

I'm amazed at the amount of fud spread by people simply because they ignore to do the obvious. I have a windows partition on both my machines and have NOT had a virus in years and I don't attribute this to luck.

---

### Post by TravisNewman on 2006-07-22
*"I'm amazed at the amount of fud spread by people simply because they ignore to do the obvious. I have a windows partition on both my machines and have NOT had a virus in years and I don't attribute this to luck."*

Do you think that's obvious to most people? I certaily don't personally. Most people don't have flash drives, and while CD burners are more prevalent, many people don't know how to use them. It's not a case of ignoring to do the obvious, it's a case of doing what you SHOULD be able to do and not have to worry about this kind of threat.

---

### Post by mips on 2006-07-22
The threat is real and it's not going to go away any time soon, so best people take precautions. You would be a fool not to (not referring to you but the general populous).

---

### Post by scxtt on 2006-07-22
you ARE NOT going to get a "virus" (or anything negative) by visiting ATI.com / microsoft.com to download drivers &/or updates ...

based off the initial *vague* post - it's total BS to think just by running windows and having an active internet connection that BAM! you'll have a virus ...

---

### Post by Johnsie on 2006-07-22
all I know is it's pretty easy to end upith a load of junk on windows even if you are an advanced user.

---

### Post by Ubunted on 2006-07-22
I got the Sasser worm once less than 5 minutes after finishing a clean install behind my router.

It's not impossible, especially on unpatched XP.

---

### Post by sagarhshah on 2006-07-22
windows is going to be around for a while so people better start learning how to keep their computer safe!!

Or actually don't bother learning. Just pay the techie to do it. That way i can pay my way through uni by fixing messed up windows systems for money!!

---

### Post by richbarna on 2006-07-22
> **scxtt said:**
> you ARE NOT going to get a "virus" (or anything negative) by visiting ATI.com / microsoft.com to download drivers &/or updates ...

based off the initial *vague* post - it's total BS to think just by running windows and having an active internet connection that BAM! you'll have a virus ...

Actually it has happened to me a couple of years ago as well, and I am no windows newbie.
No vague descriptions here. I installed a fresh windows xp, the first thing as always was to install avg antivirus, I installed the drivers and setup files for my usb modem that connects via Telefonica Spain. Everything went according to plan. I started the connection, hit avg to update. In the middle of the update I got infected after approximately 25 seconds. The message "RPC has unexpectedly shutdown, windows will reboot in 30 seconds, and the countdown starts.
By the way ALL of my software was always virus checked before being saved on cd. So yes, you CAN get infected only by being connected to the internet, it doesn't matter what sites you visit.

Have aread up on Nachi :-
[http://www.fortinet.com/VirusEncyclopedia/search/encyclopediaSearch.do?method=viewVirusDetailsInfoDirectly&fid=437](http://www.fortinet.com/VirusEncyclopedia/search/encyclopediaSearch.do?method=viewVirusDetailsInfoDirectly&fid=437)

---

### Post by scxtt on 2006-07-22
i'm sorry, but i refuse to believe that a box, even just sitting there (and at least on a router), will be attacked by "viruses" like hungry fat kids @ a twinkie factory ... yes, windows has security holes, but there are no immediate "oh look its a windows box!!" viruses floating around wringing their hands in evil anticipation ...

---

### Post by DoktorSeven on 2006-07-22
Believe it or not, yes, it is possible to infect an unpatched WinXP  machine.  XP runs a service that can be attacked from the outside in such a way that it will be infected without you having to do anything at all. 

Service Pack 2 will keep this from happening, so the trick is to have SP2 at the ready, install XP then SP2 disconnected from the Internet, turn on XP's builtin firewall (at the very least, hardware FW is better), then allow XP access to the Internet.

Trust me, Windows is just that bad.

---

### Post by scxtt on 2006-07-22
i don't doubt it's vulnerable - but i fail to see (and please explain if necessary) how anything can even get past a router ...

case in point - i only had port 5900 forwarded to my box (well, SSH too), i shut down my :0 connection so i can't x11vnc into my box - fine, i thought, i'll use vncserver & port 5901 - well it's not forwarded (i disabled it, intentionally ... if i can't even get onto my box, i fail to see how others can ...

keep in mind i'm talking about being behind a router only (i never paid much attn to firewalls in my XP-only days) ...

i'm also going to blame a lot of problems on the fact that most people run XP as an administrator ...

---

### Post by Stew2 on 2006-07-22
Actually there are. I got busted by sasser while doing my xp updates. Check this out [http://en.wikipedia.org/wiki/Sasser_worm](http://en.wikipedia.org/wiki/Sasser_worm), it mentions that it can spread without the help of the user. Although I should also mention that I had it connected directly to my ADSL modem. Now that I have multiple computers I have a router set up with a Nat firewall and I havent had a problem since. It is possible to get something just by being connected to the internet. Might be a worm instead of a virus though :) . Have to remember that not everyone is running a router... although they should.

Regards,
Stew2

Edit: Note, mine was a fresh install of XP Home and as soon as I got connected to the internet I went to microsoft.com and started the updates and service pack 2. I never even made it through all of the updates before sasser started rebooting my newly built PC.

---

### Post by whiteguysamurai on 2006-07-22
You must have been either,
1) looking somewhere you shouldn't be,

2) A target from someone who hates you.

Believe it or not, my xp partition has never been attacked because i use some very prudent, yet basic steps.

*Always use a virus scan

*Never log in as admin

*Use a better firewall(several free ones)

*Use an alternative browser, like firefox or opera.

While i might seem trivial and tedious to most users, it's much easier and faster then the alternative.

Good luck.

---

### Post by LINUXBEN on 2006-07-22
My machine got infected only when members of the family got curious of opening emails with funny/weird attachments. Just educated them about the safe use of emails and internet. So far no virus/trojan horses has penetrated the system. 
I am using free zonealarm and avast.

---

### Post by Janux on 2006-07-22
Wow, how nice, Windows and Linux zealots.

While It's a reality that your Windows box can be pwn3d... ahem, infected even if you don't touch it, it's also easy to prevent that if you download the security patches from Windows Update and you have a properly configured firewall.

---

### Post by Stew2 on 2006-07-22
> **Janux said:**
> Wow, how nice, Windows and Linux zealots.

While It's a reality that your Windows box can be pwn3d... ahem, infected even if you don't touch it, it's also easy to prevent that if you download the security patches from Windows Update and you have a properly configured firewall.

Ummm... not really zealots on either side. Just folks stating their opinions. I personally run both OS's and dont really consider myself a zealot of either:D 

Regards,
Stew2

---

### Post by scxtt on 2006-07-22
[quote=Janux]
[indent]Wow, how nice, Windows and Linux zealots.[/indent][/quote]i've yet to see anyone be overly zealous about anything - especially windows ...

---

### Post by Polygon on 2006-07-22
even with firefox, norton anti virus, and a fully patched windows sp 2 system, i still get these like 10 pieces of spyware (tracking cookies mostly) that appear on my  windows system every time i do a scan with them with adware 6 and spybot search and destroy.

but using internet explorer will get you spyware, and eventually viruses very easily. even with a firewall and anti virus program.  Its a real shame that that piece of crap is the default browser and one of the most used for windows....

---

### Post by K.Mandla on 2006-07-22
I am overly zealous about apathy and indifference. ;)

---

### Post by Stew2 on 2006-07-22
> **K.Mandla said:**
> I am overly zealous about apathy and indifference. ;)

:D No fair! Big words! :D

---

### Post by Ptero-4 on 2006-07-22
I'm Overly Zealous About Linux.

---

### Post by T700 on 2006-07-23
> **scxtt said:**
> i'm sorry, but i refuse to believe that a box, even just sitting there (and at least on a router), will be attacked by "viruses" like hungry fat kids @ a twinkie factory ... yes, windows has security holes, but there are no immediate "oh look its a windows box!!" viruses floating around wringing their hands in evil anticipation ...

I've worked on networks where we put out "honey pots" (unprotected Windows servers and workstations) and saw them infected within 30-60 minutes.  Not doing anything with them; just sitting wide open on the net.

Paul

---

### Post by scxtt on 2006-07-23
then i must be really lucky or my router is just smart ...

---

### Post by richbarna on 2006-07-23
> **Janux said:**
> Wow, how nice, Windows and Linux zealots.

While It's a reality that your Windows box can be pwn3d... ahem, infected even if you don't touch it, it's also easy to prevent that if you download the security patches from Windows Update and you have a properly configured firewall.

I run Linux and Windows, and I complain about and praise both OS's. If you read all of the thread, you will realise that the infections happened BEFORE there was even a chance to get updates.On 3 occasions the infections happened DURING updates. 

Properly configured firewall means nothing my friend, software firewalls are pretty but not much use.

By the way, I now have a 5 computer Linux network with IPCOP hardware firewall connecting through a router. NOTHING gets through.
Me and my friends regularly try to hack eachother's system to check the security. (We say compromised instead of pwn3d :))

---

### Post by Mathiasdm on 2006-07-23
> **scxtt said:**
> you ARE NOT going to get a "virus" (or anything negative) by visiting ATI.com / microsoft.com to download drivers &/or updates ...

based off the initial *vague* post - it's total BS to think just by running windows and having an active internet connection that BAM! you'll have a virus ...
Incorrect.
If you leave a Windows box connected to the intenet without protection (use those condoms!), it'll be infected in minutes.

[http://www.zdnet.com.au/news/security/0,2000061744,39200021,00.htm](http://www.zdnet.com.au/news/security/0,2000061744,39200021,00.htm)
[http://www.usatoday.com/money/industries/technology/2004-11-29-honeypot_x.htm](http://www.usatoday.com/money/industries/technology/2004-11-29-honeypot_x.htm)
[http://www.techweb.com/wire/security/54201306](http://www.techweb.com/wire/security/54201306)

> **scxtt said:**
> then i must be really lucky or my router is just smart ...
A router is (amongst other things) a firewall. The chances of being infected while behind a router are much lower.

I've heard many stories of people getting infected while installing Windows.
That's why I always install antivirus software and a firewall before going online.

---

### Post by bonzodog on 2006-07-23
heh...Windows won't install on this box...doesn't like my hardware. 
I once did it after 3 hours of attempts, and massive amounts of reconfiguration after install, with the net disconnected.
I don't kniow what it is about my hardware config, but windows really doesn't like it. Linux Just Works. Windows doesn't. 'nuff said.

---

### Post by mips on 2006-07-23
> **scxtt said:**
> i'm sorry, but i refuse to believe that a box, even just sitting there (and at least on a router), will be attacked by "viruses" like hungry fat kids @ a twinkie factory ... yes, windows has security holes, but there are no immediate "oh look its a windows box!!" viruses floating around wringing their hands in evil anticipation ...

This has happened to me before at work, a place with high security, multiple firewalls, Antivirus and completely locked down desktops, users cannot even change the wallpaper.

I prepped a fresh PC by using the XP install cd instead of the company drive image. After my reboot the PC was infected. I found this out after I installed the the AV which was the first thing I installed. Cannot remember the virus/worm name though. In the company there were a few machines used for process control on the LAN that did not have the same setup as most desktops.

I recall a couple of the worms/virii were so bad (virus patches werent applied fast enough because the security team usually test in a lab env first to check stability etc and they took a bit to long) that we were tasked with implementing access lists on all the cisco routers (1000+) to block the worm traffic, it actually had a very bad performance impact on the network as well. job was very easily done with a few scripts.

So just because it has not happened to you does not mean it is not possible. It can be prevented though.

---

### Post by scxtt on 2006-07-23
i've never said it was 'impossible', i'm just stating that going to ATI.com/MS.com WILL NOT infect a windows box and that i've NEVER had that problem for 2 simple reasons:

1. i'm always on a router [w/ at most SSH/VNC port forwarded]
2. don't use windows as an administrator

and while i'm no windows 'fan', this "oh snap, my windows box got infected by trojanz/wormz/viruzez like *that*" talk is worthless (IMO) ...

not to mention that virus software is hardly perfect ...

---

### Post by bruce89 on 2006-07-23
I got this too, a while ago with XPSP1 (not firewall on by default), I was downloading Zonealarm thinking a few minutes wouldn't matter.  Apparently is does.

Please could people stop saying this can't happen, as it happened to me.

---

### Post by Omnios on 2006-07-23
I was a knoledgable winXP user and though time intensive I had no data loss and other than regular spyware removal things worked good I also used Ez Armor which worked like real armor. Anyways on the other hand my dad has had huge problems with his anti virus program and spy ware and  a few weeks ago he told me that he started XP and whent to the kitchen to get a glass of water, by the time he got back he had about three viruses. His anti virus is from his ISP and aperently sucks. 

 Well he currently has Ubuntu 6.06 which he is using more now as he learns how to use it.

---

### Post by confused57 on 2006-07-23
> **bruce89 said:**
> I got this too, a while ago with XPSP1 (not firewall on by default), I was downloading Zonealarm thinking a few minutes wouldn't matter.  Apparently is does.

Please could people stop saying this can't happen, as it happened to me.
I've installed Windows (XP) only once, but I had read your computer could be compromised in only a matter of minutes.  Therefore, I installed XP offline and installed the zonealarm.exe I had downloaded to USB drive...then configured my internet connection, went online, immediately went to Windows update...installed every free anti-spyware program I could think of, installed anti-virus...haven't had any problems in the 8 months since installing.

---

### Post by maagimies on 2006-07-23
Every time I have installed Windows with network cable plugged in, and without a router, in my first boot to Windows the desktop was filled with porn and gambling ads.
Well, I now have more then a 1 computer, so I got a router and that problem was solved :)

---

### Post by Zzooommm on 2006-07-23
When I installed XP (retail CD, no service packs) on a family PC (it had direct net access) it got infected with that blaster thingie under 5 minutes of use. It booted for the first time, I opened the browser to download security updates and before I could even finish the selection process - boom infected.

---

### Post by aktiwers on 2006-07-23
If you downloaded Xp, there is a good chance someone placed a virus in it. It has happend to me. I had a virus before even getting connected to the internet, or installing anything but my usual stuff, that never had any viruses before.

---

### Post by Ptero-4 on 2006-07-24
It's funny how you guys put up with that crap. If you want to secure Windoze. The trick is simple. Just remove Windoze from your PC, and put the Windoze install CD in it's box, sealed and shrinkwrapped. That's the only way Windoze is secure.

---

### Post by mips on 2006-07-24
> **Ptero-4 said:**
> It's funny how you guys put up with that crap. If you want to secure Windoze. The trick is simple. Just remove Windoze from your PC, and put the Windoze install CD in it's box, sealed and shrinkwrapped. That's the only way Windoze is secure.

Sorry to say but that is not the only way. You can install XP without any hassles if you do it right and never have any issues !!!

---

### Post by bailout on 2006-07-25
I always feel very sad and left out when reading these sort of threads as despite having run windows for many years now no one has ever thought me important enough to take over my pc, bombard me with viruses or spyware. Whenever I try running anti-virus scans or spyware catchers hoping I can join in the fun they always come up blank. I have reinstalled, downloaded updates from the net etc, etc but still nothing :(

What am I doing wrong?

---

### Post by Christmas on 2006-07-25
When I was using Windows XP I made the mistake to open Internet Explorer without SP2 and ZoneAlarm, which I used all the time. The default homepage is set to Microsoft Network I think or something related to Microsoft. I got infected immediately. With SP2 and ZoneAlarm I didn't had problems. Actually there was only one, which I couldn't get rid of with SpyBot Search and Destroy, Lavasoft Ad-aware and BitDefender 8. I was redirected to a google search each time when I tried to click some links.

Now on Kubuntu 6.06 I have no such issues.

---

### Post by Christmas on 2006-07-25
> **bailout said:**
> I always feel very sad and left out when reading these sort of threads as despite having run windows for many years now no one has ever thought me important enough to take over my pc, bombard me with viruses or spyware. Whenever I try running anti-virus scans or spyware catchers hoping I can join in the fun they always come up blank. I have reinstalled, downloaded updates from the net etc, etc but still nothing :(

What am I doing wrong?

You can switch definitely to Ubuntu :) Or, if you really need Windows, here's what I used to do. Always had SP1 and SP2 installed, and always made the proper updates through Windows Update. I didn't use the build-in firewall that came with SP2, I only used the free ZoneAlarm Firewall, which is the greatest of all IMO. Never had problems with it. Don't click on banners, "spy-removal" offers, warez, porn sites, crack sites. Use Firefox instead of Internet Explorer. Install BitDefender Free Edition and scan absolutely every single file you download from DC, web sites, IRC or whatever else. And, of course, even like this you have to make an anti-spyware and virus removal scan once a week. Use SpyBot Search & Destroy and Lavasoft Ad-Aware for spyware. There was also CWS Shredder (I think that is the correct name) which gets rid of Cool Web Search, a very common adware. This is a lot of work unfortunately.

---

### Post by confused57 on 2006-07-25
> **bailout said:**
> I always feel very sad and left out when reading these sort of threads as despite having run windows for many years now no one has ever thought me important enough to take over my pc, bombard me with viruses or spyware. Whenever I try running anti-virus scans or spyware catchers hoping I can join in the fun they always come up blank. I have reinstalled, downloaded updates from the net etc, etc but still nothing :(

What am I doing wrong?

If your dog loves you, you're important...I wouldn't take not getting viruses & spyware personally.

---

### Post by Redcard on 2006-07-25
Usually it's faster to infect.  In corporate enviroments, there are specialized versions of windows that include the bugfixes slipstreamed in.  Here at where I work, our record is an infect two minutes and eleven seconds after the network cable was plugged in to go download updates from MS.   Our average is around 4 minutes.  

This, of course, is not nearly enough time to download anything.. so all the AV programs and such must be carried in on a USB key and hand installed/updated.  Once that's done ,we hand install the latest microsoft "SuperPatch."  Then, and only then, do we go online.  

If we follow all the steps very, very carefully, we end up with a clean machine.  That is, of course, until some virus sneaks past NAV

---

### Post by gray-squirrel on 2006-07-25
> **scxtt said:**
> i've never said it was 'impossible', i'm just stating that going to ATI.com/MS.com WILL NOT infect a windows box and that i've NEVER had that problem for 2 simple reasons:


I think what some people have been trying to say (and if not, I will say it now) is that you don't even have to go to a Web site to have issues.  I mean, there are things like rootkits out there. . .

I remember one Windows XP computer at work that for some reason did not have SP2 installed.  One morning I was unfortunate enough to use it (and I thought it was patched!) and it was only minutes after reaching the desktop that I saw a sign of an attack: the message "The RPC has unexpectedly shutdown message" that another person on this thread talked about came up on the screen.  This happened even after I restarted the system three times or so.  And I had no browsers running.  But the network connection to the Internet made it all possible.

---

### Post by mips on 2006-07-25
> **Redcard said:**
> Usually it's faster to infect.  In corporate enviroments, there are specialized versions of windows that include the bugfixes slipstreamed in.  Here at where I work, our record is an infect two minutes and eleven seconds after the network cable was plugged in to go download updates from MS.   Our average is around 4 minutes.  

This, of course, is not nearly enough time to download anything.. so all the AV programs and such must be carried in on a USB key and hand installed/updated.  Once that's done ,we hand install the latest microsoft "SuperPatch."  Then, and only then, do we go online.  

If we follow all the steps very, very carefully, we end up with a clean machine.  That is, of course, until some virus sneaks past NAV

Should look into drive images.

---

### Post by Redcard on 2006-07-25
Drive images don't solve the problem of having to get the latest patch for the latest exploit.  In fact, drive images are a huge part of the problem, since it is often required to be online to do the imaging (or the updating required to bring the image to current once the old image is on the machine.)

Now, if there was a way to use automatically put ghost images into a sand box to update them and then image them off, that'd be different, but the problem is that images are often months to years old.

---

### Post by IYY on 2006-07-25
> i'm sorry, but i refuse to believe that a box, even just sitting there (and at least on a router), will be attacked by "viruses" like hungry fat kids @ a twinkie factory ... yes, windows has security holes, but there are no immediate "oh look its a windows box!!" viruses floating around wringing their hands in evil anticipation ...

I am sorry, but you are simply wrong. The submitter of this thread is not the first to tell this story, and it has been demonstrated and documented. If you turn on a fresh Windows box, with an old Windows XP CD, and Internet Explorer, on a network without a router, it will get compromised.

No expert will do this, of course, and Microsoft does suggest downloading the patches as soon as possible, but the problem is real and many novice users suffer from it.

---

### Post by scxtt on 2006-07-25
[quote=scxtt]i'm sorry, but i refuse to believe that a box, even just sitting there [color=red](and at least on a router)[/color], will be attacked by "viruses" like hungry fat kids @ a twinkie factory ... yes, windows has security holes, but there are no immediate "oh look its a windows box!!" viruses floating around wringing their hands in evil anticipation ...[/quote][QUOTE=IYY]I am sorry, but you are simply wrong. The submitter of this thread is not the first to tell this story, and it has been demonstrated and documented. If you turn on a fresh Windows box, with an old Windows XP CD, and Internet Explorer, on a network without a router, it will get compromised.

No expert will do this, of course, and Microsoft does suggest downloading the patches as soon as possible, but the problem is real and many novice users suffer from it.[/QUOTE]as you can easily see in what you quoted me as saying, i'm referring to being on a router ... so if i'm "simply wrong", you're "simply" guilty of not reading closely ... i'm not defending windows, i'm just tired of people whining about WELL documented problems w/ simple solutions ...

---

### Post by IYY on 2006-07-25
So, are you implying that the average home-user has/sgiykd get a router, even if she only has one machine? Why should an operating system need an extra piece of hardware to protect it from getting hacked while just sitting there?

---

### Post by scxtt on 2006-07-26
you'll have to take that up w/ microsoft ... and honestly, a wired/wireless router isn't all that expensive - comparable to buying A/V software {and can be used above and beyond just this purpose, let's say "she" gets a laptop - "she" can plug it into her shiny, new router} ...

---

### Post by Redcard on 2006-07-26
There is no well documented solution to the windows XP issue.  The fact is, Microsoft will not do for it what they do for Windows 2003.  They will not close all the connections until the updates are downloaded.  In Windows server 2003 R2, after the OS is installed, a screen is opened that basically controls a very strict firewall. The browser is set to the highest security and goes directly to update.  The patches are downloaded.  So long as that screen is up, the computer is literally shut tight.  

No such screen exists for the XP user.   No such methodology exists.   Microsoft basically leaves them out there in the open as they try to download patches.

Oh sure, you can buy XP with SP2 installed, but let me assure you, that doesn't protect you from any of the exploits listed after the SP2 release.  You're still very vulernable.

There's NOTHING a user can do about this, other than use another machine to get the cumulative updates since SP2 and slipstream them in or install them with the network connection disconnected.  The common every day Joe doesn't have the techology or the technical knowhow to do this.  THey'd rather pay someone at CompUSA a hundred or so bucks to do it.  This is IF they don't throw in the recovery CD.  If they use the recovery CD , they run into the same issue I described earlier that occurs with Ghost images.  They still have to update.. and that requires them to be online.. and that requires the system to be open until that update is done.

Make no mistake about this.  Your common user is HOSED when it comes to Microsoft installs.  The thing that amuses me even more is how the corporate customers can get all this stuff slipstreamed in through MSDN , but the common joe gets to play russian roulette.

Just for fun, I set up a new Windows box.  No updates.  XP, with the recovery disk that came with the HP.

Five and a half minutes until it got hit with an exploit.  The exploit installed a browser "add-on" to IE, and that was storing my passwords in plaintext on a file.   Supposedly there is a port open that could be "fished" for that file.  It was reported by NAV.

That's the reality of windows.  That's how it works if you don't have their server OS.

---

### Post by stchman on 2007-03-08
I have installed XP enough times to recommend the right way.  I recommend you be hooked up to a router or if not download Comodo firewall.  it is preferrable to have all software and drivers on CD.

1.  First dload AVG anti virus and anti spyware, hardware drivers, firewall, etc. 
2.  Do a fresh install of XP SP2 without ethernet or wifi hooked up.
3.  Install chipset drivers
4.  Install hardware drivers
5.  Install AVG anti virus
6.  Install AVG anti spyware
7.  Hook up your ethernet cable or enable wireless
8.  Let windows update to its thing
9.  Once all software (Office, web browser, etc.) has been installed make a new account called Admin
10.  Log off and then log into Admin
11.  Make the account you just logged off of a limited account
12.  Log off admin and log back into the limited account.
13.  Never surf internet on Admin EVER
14.  Never surf internet with Internet Explorer, use Firefox.  Firefox has an IE plugin.  IE has too many security holes.
15.  Follow these steps and your XP based PC is relatively secure.

The only thing I ever get are some tracking cookies under this configuration.  I tell my brother and nephew to do this or I won't fix their fu&^*)( up Windows anymore.  You may have to log on to admin periodically to let windows update itself.  If you do this you will spend <1% of your time on Admin.

There are some retarded programs that require Admin right (Quicken being one of them).  I still don't know why they do!!!!!!  Log onto Admin and Comodo has an option to disable internet access, DO IT!!!!!!

---

### Post by yaztromo on 2007-03-08
> **Cyraxzz said:**
> There is this one game i like that does not run well under Wine. I decided to install WinXp on my old Machine. Shortly after the installation i activated the Windoze firewall and visited ATI to download the video driver, also visited microsoft.com to get some required driver for it. shortly after that I saw some unusual programs in task manager, i installed an anti-virus program from one of my USB memory chips, updated it and performed a scan and it found 2 threats. The firewall in my router was also active.

talk about insecurity...

What a load of rubbish.

---

### Post by om3ganet on 2007-03-09
Aww. I've been intentionally trying to infect a Windows XP (SP1) machine (in a virtual PC) for a while. I've put the virtual PC in the DMZ zone so all incoming traffic goes to it, but I don't appear to have any viruses, worms, Trojans or pop ups!

Guess I'm just unlucky eh?

om3ganet

---

### Post by AlanRogers on 2007-03-09
This was potentially one of the most useful and actually one of the most destructive threads I've read on this otherwise superb forum. It is riddled with opinion and vicarious experience, many responses sadly lacking in any real research, complete analysis or factual information.

It is certainly true that computers running Windows can pick up viruses without user intervention; it was all over the news some years back, as viruses crippled businesses worldwide. At the time of their peak virility, such viruses were capable of infecting virgin install machines within 27 seconds of being first connected to the internet (Source: [BBC News]("http://news.bbc.co.uk/1/hi/technology/3147147.stm")).

The debate about who is at fault, to blame, too stupid, talking rubbish and so on is just playground chest-shoving. This is a Linux forum first and foremost, but a thread like this will be around for a long time because it contains a lot of the keywords that searchers will use, whether here or on a search engine. So far, all we've successfully achieved is to spread FUD ourselves, IMHO.

Those particular viruses are less prevalent now; not dead or gone but less effective because of patching. Therefore, it will be harder to replicate the failures of four years ago. All of the correct advice has already been given but so despersed through the thread that nobody will stick around long enough to read it.[LIST=1]
[*]Install anti-virus software first and update offline using files downloaded using another computer
[*]Make sure that your firewall is secure, and on!
[*]Apply as many patches as you can offline using downloaded executables
[*]Make sure all available appropriate updates are applied as soon as possible - do not rely on automatic notification[/LIST]This is my attempt to boil all of the preceding advice and vitriol down into a simple set of guidelines that others stumbling across this thread later will be able to follow.

---

### Post by nocturn on 2007-03-09
[http://isc2.sans.org/survivaltime.html](http://isc2.sans.org/survivaltime.html)

Basicly, the survival time is the average time from connecting a machine to the net until it is hit by probes.  If these probes find you to be vulnerable (unpatched), you're infected.

23 minutes seems to be consistent with that rule...

---

### Post by nocturn on 2007-03-09
> **scxtt said:**
> i'm sorry, but i refuse to believe that a box, even just sitting there (and at least on a router), will be attacked by "viruses" like hungry fat kids @ a twinkie factory ... yes, windows has security holes, but there are no immediate "oh look its a windows box!!" viruses floating around wringing their hands in evil anticipation ...

ISC reports seem to prove you wrong.  Which is part of the reason the internet survival time is such an important metric.  Generally, it is believed to be problematic when the survival time exceeds the amount of time needed to download MS patches, but infections can already occur in much less time (since it is an average).

---

### Post by nocturn on 2007-03-09
> **bruce89 said:**
> I got this too, a while ago with XPSP1 (not firewall on by default), I was downloading Zonealarm thinking a few minutes wouldn't matter.  Apparently is does.

Please could people stop saying this can't happen, as it happened to me.

Indeed.  This is very well documented by organisations such as SANS, so the people who did get infected need not to think it is only them or they are being alarmist.

I don't wish to take a stab at windows particulary now, but this one is so well known it is foolish to deny it (I don't think that even MS denies it).

---

### Post by nocturn on 2007-03-09
> **scxtt said:**
> as you can easily see in what you quoted me as saying, i'm referring to being on a router ... so if i'm "simply wrong", you're "simply" guilty of not reading closely ... i'm not defending windows, i'm just tired of people whining about WELL documented problems w/ simple solutions ...

Keep in mind that not all routers perform equally well as firewalls AND a lot of them have Upnp enabled by default, exposing services to the outside without the user explicitly telling them too.

---

### Post by Trebuchet on 2007-03-09
> **bailout said:**
> I always feel very sad and left out when reading these sort of threads as despite having run windows for many years now no one has ever thought me important enough to take over my pc, bombard me with viruses or spyware. Whenever I try running anti-virus scans or spyware catchers hoping I can join in the fun they always come up blank. I have reinstalled, downloaded updates from the net etc, etc but still nothing :(

What am I doing wrong?I'm with you. Despite ten years on the internet using Windows on multiple machines, I just can't seem to get infected. I had no idea common sense was such an effective barrier against malware.

---

### Post by karellen on 2007-03-09
I never had any real problems with windows xp...but I don't consider myself the average joe user :)

---

### Post by luca.b on 2007-03-09
> **stchman said:**
> 
periodically to let windows update itself.  If you do this you will spend <1% of your time on Admin.

If you use IE unfortunately it will mean little, as IE (AFAIK) runs with the SYSTEM account privileges, which means even higher than Administrator.

---

