---
title: "Ubuntu - Grandma approved?"
date: 2009-12-06
forum: The Cafe
---

### Post by cartisdm on 2009-12-06
My Grandma, who has never used a computer before in her life, wants to be able to send a few emails to family members and get on facebook to see pictures of her Grandkids.

I am going to get her a very basic desktop computer for Christmas and would like to put the ABSOLUTE EASIEST operating system on it.  I know ubuntu is easy but I have a few concerns:

1. I live three states away so I will have to trust someone else to hook it up for her (I am thinking I will install the OS and get it all configured at my house then ship it to her).

2. If there every is even the slightest problem, I have to way to troubleshoot and my family members down there won't know a thing about navigating the linux GUI

3. Getting the nerve to throw someone balls deep in linux and not being there to monitor them

---

### Post by SunnyRabbiera on 2009-12-07
Actually something like Linux Mint, PcLinux or Mepis Linux might all be good options
All have codecs she might need

---

### Post by phrostbyte on 2009-12-07
I think the biggest issue is hardware. Just make sure all her hardware works, and that a web browser is easily accessible. Also apt-get some cool apps like Celestia. :)

---

### Post by chickengirl on 2009-12-07
Her not having used a computer before is actually a good thing IMO because you don't have to re-train her away from using Windows. And she's probably got a much better chance to NOT mess up a linux box the way she would with a Windows box since she probably doesn't understand about viruses and why you shouldn't click on banner ads that say you just won the lottery or whatever stupid thing.

Maybe you can set up a remote desktop or SSH access so you can troubleshoot it if she has problems?

---

### Post by staf0048 on 2009-12-07
I've been thinking of doing the same thing for my mother who has never owned a computer, but we're 2,000 miles away and I don't think the family that lives near her have enough technical knowledge to even diagnose a Window's error, so I've been battling the same concerns.

As for trouble shooting you could try OpenSSH.  Or if you want a GUI instead, go with either Remote Desktop Viewer (under Applications/Internet) or you could try XDMCP, but in either case you'd have to get access through her IP Address, which may be easier said than done.  

Apart from those options, I'm not sure what else you could do except to get her a webcam so you can watch what she's doing while you're instructing her.

---

### Post by cartisdm on 2009-12-07
> **chickengirl said:**
> Maybe you can set up a remote desktop or SSH access so you can troubleshoot it if she has problems?

I would LOVE to do that but that actually brings me to my next concern. She will be using dial-up internet.  I know this sounds pathetic, but I literally have ZERO experience with dial-up (and less than zero when it comes to using dial-up in linux).

1. If I get a USB or PCI card phone modem is it likely to be just as plug and play as other hardware?

2. Um.....how does one connect to the internet in ubuntu/linux using a phone line and internet provider?

Please be very blunt because I haven't had to connect online since I used that free AOL stuff when I was like 10 years old...

---

### Post by user1397 on 2009-12-07
I would definitely recommend something like linux mint or mepis, but you could also just use ubuntu and configure it slightly (to have necessary codecs, etc) before you ship it to her.  Like said before, make sure all hardware is compatible and maybe add simple icons to her desktop like "Internet" or "Email" stuff like that.

---

### Post by MaxIBoy on 2009-12-07
Most linux distros will do for this. It looks like all she needs is an email client, web browser, and maybe a media player. If this is all she needs then Mint will be fine (but put her on a limited account just in case.)


If you want to be able to administer it remotely, set it up with a dyndns domain name and SSH into it. That's what I do. You can also forward SSH over X. I find that a great arrangement is to have XFCE4-panel running over SSH, and put some launchers on it.


EDIT: Here is how you use dial-up with Linux: Don't. Just, don't. You can make it work and all, but only by disabling automatic updates and so on. In fact, I would suggest convincing her to get a cheap broadband connection. Dialup is just woefully insufficient for even something like Facebook (and a good 80% of spam messages these days would totally lock up everything.)

---

### Post by phrostbyte on 2009-12-07
> **cartisdm said:**
> I would LOVE to do that but that actually brings me to my next concern. She will be using dial-up internet.  I know this sounds pathetic, but I literally have ZERO experience with dial-up (and less than zero when it comes to using dial-up in linux).

1. If I get a USB or PCI card phone modem is it likely to be just as plug and play as other hardware?

2. Um.....how does one connect to the internet in ubuntu/linux using a phone line and internet provider?

Please be very blunt because I haven't had to connect online since I used that free AOL stuff when I was like 10 years old...

NetworkManager (same thing that manages wifi) supports dial-up. Not that I have ever need to use it.

Note: Modem support on Linux has (historically) been flaky, due to modems being designed specifically to work on Windows and putting all the logic in software. You have to be careful which modem you get, and make sure it has Linux support.

---

### Post by earthpigg on 2009-12-07
make sure you [set up ssh]("http://wiki.archlinux.org/index.php/SSH") so you can administer the computer from your house.

free service provided by [dyndns]("http://www.dyndns.com/") and ddclient installed on the computer will make it so the dynamic IP address isn't an issue with ssh.

put giant icons on the desktop for the stuff she wants to do.

maybe consider an alternative UI such as [lxlauncher]("http://lxde.org/lxlauncher") or UNR.

set 'em up with two accounts -- one that is able to sudo, and one that isn't.


edit: whoa. dial up. haven't touched it since before i was a linux user. i cannot offer advice there, i am sorry.

edit2: if you can get dial up working, consider using Debian... they offer a 5 dvd collection you can burn yourself or purchase that can be used as a local repo, since downloading from repositories will not really be practical.

---

### Post by cartisdm on 2009-12-07
Crap...I was worried about the responses I would get after mentioning dial-up.  I don't really know what options are available, she lives in a very small town in Alabama (ie middle of nowhere) and I don't know if high speed internet access is even available.

---

### Post by phrostbyte on 2009-12-07
> **cartisdm said:**
> Crap...I was worried about the responses I would get after mentioning dial-up.  I don't really know what options are available, she lives in a very small town in Alabama (ie middle of nowhere) and I don't know if high speed internet access is even available.

Dial-up works. :) You just have to be careful with modem you get that's all.

---

### Post by cartisdm on 2009-12-07
If I do end up going the dial-up internet route, is there any hope of being able to use remote desktop so I can access her computer from my house?

---

### Post by Exodist on 2009-12-07
> **chickengirl said:**
> Her not having used a computer before is actually a good thing IMO because you don't have to re-train her away from using Windows. And she's probably got a much better chance to NOT mess up a linux box the way she would with a Windows box since she probably doesn't understand about viruses and why you shouldn't click on banner ads that say you just won the lottery or whatever stupid thing.

Maybe you can set up a remote desktop or SSH access so you can troubleshoot it if she has problems?
QFT..

She prob will not have any issues what so ever after you get her setup. Since she has never used a PC. She will not get frustrated over a re-learning curve that most get.

---

### Post by Exodist on 2009-12-07
> **cartisdm said:**
> If I do end up going the dial-up internet route, is there any hope of being able to use remote desktop so I can access her computer from my house?
If she is on the internet yes. Jsut get her IP.

---

### Post by cartisdm on 2009-12-07
> **Exodist said:**
> If she is on the internet yes. Jsut get her IP.

I'm more worried about speeds.  Would I be able to have a fast enough connection where it would be worth while to work on her computer remotely?

---

### Post by AllRadioisDead on 2009-12-07
To be honest, this sounds like way too much of a hassle just for the sake of getting linux on her box. If I were you, I'd set her up with a nice clean xp box, a decent but out of the way antivirus program, an internet browser, and a webcam. Just my 0.02, I know I'll get flamed for this.

---

### Post by earthpigg on 2009-12-07
> **cartisdm said:**
> I'm more worried about speeds.  Would I be able to have a fast enough connection where it would be worth while to work on her computer remotely?

via remote desktop? nah

via ssh? yes. comfy with the command line?

edit: got my 'yes' and 'no' backwards...

---

### Post by Exodist on 2009-12-07
> **cartisdm said:**
> I'm more worried about speeds.  Would I be able to have a fast enough connection where it would be worth while to work on her computer remotely?
Most everything should be done console wise. But yea dail up is fine. Used to be how I would access the server at a ISP I used to work for. If that failed I had to drive 20miles to work.. LOL luckly it normally worked.

---

### Post by Irihapeti on 2009-12-07
For what it's worth, I ran Ubuntu for about 18 months with dialup only. Updates such as kernel upgrades could be a bit slow, so I often organised them to be done overnight or when I was out at a meeting. It's possible to write scripts to do that kind of thing and include them in the applications menu.

I used GnomePPP and wvdial. Network manager didn't seem to behave very well.

---

### Post by redrac on 2009-12-07
Set my mom up with ubuntu. And she loves it, asked me to put it on her old pc.  All she plays is solitaire and mahjong anyhow. She already used chrome for browser, so was no change there. No spyware no virus's this is on an old p3 866 with 512MB ram. Now granny won't let me touch her laptop, die hard winxp internet explorer user, paid to click programs and pretty much infested. She is stubborn, but does well for being 84

---

### Post by openuniverse on 2009-12-07
.

---

### Post by confused_user on 2009-12-07
dude are you out of your mind :)

your thinking about installing Linux on your gran's computer lol

man your i hope you have as lot of spare time on your hands.

save yourself the pain and just give her windows,at least she'll be able to get help from other people as well as you

---

### Post by openuniverse on 2009-12-07
.

---

### Post by AllRadioisDead on 2009-12-07
> **openuniverse said:**
> you don't think there's a very large percentage of people that can help with ubuntu, among the people that are more inclined to help with computer trouble? (among the people that can actually fix her windows machine when she gets a virus or opens a trojan horse in her email?)
OP states that she lives in the middle of nowhere, and his family wouldn't be able to help. Sorry, but that seems like a valid statement to me. At least if she did find someone to help her if she got a virus, they'd at least be familiar with the OS.

---

### Post by Swagman on 2009-12-07
Use Ubuntu Netbook Remix on it and turn off updates.  You can manually update it when you visit her. (Now you've got no excuse not to visit more often !!)

:D

You could, of course, buy her a 3G dongle for net access. Considering she will be on dial-up which is *painfully* slow and she's likely not to realise to break the connection so she doesn't get a humongous phone bill that **YOU** will undoubtedly have to pay !!

By NOT going 3G... ie: Staying on dial-up Rules OUT any windows Boxen.  How many rogue dialers does a windows box get when the user is unaware of what a dialer even is  ?

Answer = THOUSANDS

---

### Post by leandromartinez98 on 2009-12-07
> **Swagman said:**
> Use Ubuntu Netbook Remix on it and turn off updates.  You can manually update it when you visit her. (Now you've got no excuse not to visit more often !!)


Installing the netbook remix is good idea, even in a desktop. And I agree with disabling the automatic updates (just disable the update notifier on her account).

I don't agree with the suggestions of installing a XP box, unless the best alternative turn out to be buying a pre-configured box from a local (to her) reseller. With Ubuntu and no updates, she will have a very smooth and uniform experience. With a dial-up connection, it will be a pain to maintain automatic XP upgrades and Virus databases, she will be getting virus database update warnings all the time, it will be horrible.

---

### Post by openuniverse on 2009-12-07
.

---

### Post by alexfish on 2009-12-07
While  away home I called  in at my sisters , a hard nut fan of windows , and nearly a grandmother
 

       ask &#8220; could I use the computer &#8220;    of course she always says yes
 

      so I booted up, sat and waited and waited and waited , time for coffee  
 

       went down stairs to put the kettle on , then went back up stairs
 

       by which time it was just making the automatic connection to the router
 

     waited and waited for panel to show the web browser  
 

      heard  &#8220; coffee is ready &#8220;   
 

         Do you know  loading windows is good excuse for a coffee break  
 

           can't mention drink here cos I might get shot at
 

    well to cut a long story short 'ish  
 

      I ask why do you bother with windows . Her reply was &#8220;well normally when &#8220; '''''''''' &#8220; her son
   calls up from London , he sorts it out  ' ????????????????????????
 

      so doing what sensible people do , I carry a live CD of Ubuntu
 

             her only comment was &#8220; is it as easy as that &#8220;  , &#8220; yes &#8220; was the reply.
 

             Left a copy as Xmas Gift , because I 'm not mean
      
      all  GRANDMOTHERS  should try Linux for Christmas

---

### Post by wilee-nilee on 2009-12-07
> **ihermit said:**
> To be honest, this sounds like way too much of a hassle just for the sake of getting linux on her box. If I were you, I'd set her up with a nice clean xp box, a decent but out of the way antivirus program, an internet browser, and a webcam. Just my 0.02, I know I'll get flamed for this.

I would say that your probably correct but I would make sure she has W7 it is much faster. A dual boot might suit her we don't know she might have no problems.

---

### Post by t0p on 2009-12-07
Okay, first point: the only things wrong with dial-up is it's not "always-on" and it's slow.  There's no issue with Linux and dial-up, it's easy to use.  Check out **GnomePPP**.  If your grandmother knows nothing about computers, you'll have to set it up for her of course.  Just shipping the computer to her in a crate is not an option.

Also remember, the computer will be linked to the internet only when she chooses to connect it.  Not always-on like broadband.  So if you want to do online support, you'll have to liaise with her carefully by phone or something.

Are you absolutely sure you want to go the Linux route?  It has advantages, of course, but also one big disadvantage: hardly anyone knows anything about it.  If she wants her computer fixed and you're unavailable for some stupid reason like having a life of your own, she will probably not be able to find a local friend who knows Linux unless she's awfully lucky.  But finding someone who knows XP (or even 7) will be much motre likely.

Good luck.

---

### Post by Johnsie on 2009-12-07
Grandma approved? No. A recent update of Ubuntu made the system spam my log files. The log files filled my hard disk and gnome wouldn't start up. I had reboot into the terminal and delete those files manually.

Ubuntu could be granny friendly, but only when there are some decent quality assurance techniques used the update process. My machine is not a test machine, it should not be installing faulty software in the updates.

---

### Post by confused_user on 2009-12-07
> **openuniverse said:**
> you don't think there's a very large percentage of people that can help with ubuntu, among the people that are more inclined to help with computer trouble? (among the people that can actually fix her windows machine when she gets a virus or opens a trojan horse in her email?)

yes actually i do think there are more people that can help with windows, or course there is, it's got a huge userbase, much bigger than ours :)

i recommend windows for old people because they don't give a ****, they just want to look at websites and use email.  jebus h chirst can you imagine what would happen if she did an update.

Gran: it told me a i needed to do an update, i dont know what a kernel is so figured that it wouldn't tell me to upgrade unless it had been tested and would definitely be ok.  Now i just see this little white dot thing flashing in the corner.

Old people know how to live their lives without computers, they dont give a **** about compiling software and fixing stuff everytime they turn their computer on.

Come on, be reasonable, windows (if someone set's it up for her) has got to be a better option for the elderly).

the thing with trojans and all that other malware is that you can get this software call AntiVirus which detects and protects you from malware.  As long as you keep it updated your fine.  the people that get infected are the ones that dont keep their AV up to date.

---

### Post by Johnsie on 2009-12-07
To be fair must Ubuntu users don't need to compile anything... everything is distributed as binary.

Maybe a driver would need to be compiled though... Not all hardware sold in the high street has a Linux driver available, but they almost always have a windows driver. The way I see it is, if my hardware wont work easily in an operating system I wont use the operating system. I've paid good money for hardware and software and I expect to be able to use those things.

---

### Post by Swagman on 2009-12-07
> **confused_user said:**
> yes actually i do think there are more people that can help with windows, or course there is, it's got a huge userbase, much bigger than ours :)

i recommend windows for old people because they don't give a ****, they just want to look at websites and use email.  jebus h chirst can you imagine what would happen if she did an update.

Gran: it told me a i needed to do an update, i dont know what a kernel is so figured that it wouldn't tell me to upgrade unless it had been tested and would definitely be ok.  Now i just see this little white dot thing flashing in the corner.

Old people know how to live their lives without computers, they dont give a **** about compiling software and fixing stuff everytime they turn their computer on.

Come on, be reasonable, windows (if someone set's it up for her) has got to be a better option for the elderly).

the thing with trojans and all that other malware is that you can get this software call AntiVirus which detects and protects you from malware.  As long as you keep it updated your fine.  the people that get infected are the ones that dont keep their AV up to date.

You **DIDN'T** read my post ( or ignored it) which said keep updates switched **OFF** did you.

Because you skipped my post you didn't read the bit about Rogue Dialers and windows boxes. So. Baring that in mind **YOU** wont mind paying her phone bill When ( not if) she gets a rogue dialer will you.

If she doesn't update then **NOTHING** will go wrong with the linux install. So she wont need Windows people contaminating her thought process will she.

---

### Post by confused_user on 2009-12-07
> **Swagman said:**
> If she doesn't update then **NOTHING** will go wrong with the linux install. So she wont need Windows people contaminating her thought process will she.

I **did** read your post and there is no need to get shirty about this.  I'm offering you my opinion in response to your question.

to say **nothing will go wrong if she doesnt update** make me smile.  do you really believe that?

anyway, send me the bill if you feel that strongly about it, i'll pay it.

---

### Post by Swagman on 2009-12-07
Sorry if I came over offensive. didn't mean it to sound that way.

I actually **DO** believe that if the OP sets up her machine and turns off automatic updates then she wont b0rk it.

Windows on the other hand.. Clicky Clicky Clicky... oh dear [**I'm infected**](http://ubuntuforums.org/showpost.php?p=8449137&postcount=7)

---

### Post by cartisdm on 2009-12-07
I am confident that if I am able to set up the OS beforehand and completely, for lack of a better term, idiot-proof the setup, it will not give her any problems.  She won't ever need to mess with adding hardware because she'll never plug anything into it (except MAYBE a flash drive with pictures).

My biggest concern is the internet connection.  I want her to enjoy her first web browsing experience and facebook over dialup just seems like a disaster.  If I get her a 3G dongle, how much could she expect to pay for basic internet access?

In reference to the Remote Desktop and SSH, I will need a GUI envirement.  I am not comfortable enough with the terminal to make adjustments remotely so I will want to literally be able to see her desktop, mouse her mouse via my mouse, and make any small adjustments as needed (if needed).

---

### Post by mamamia88 on 2009-12-07
i would just buy my grandma a mac or something.  at least it has commercial support if something goes wrong.  maybe a mac mini or something

---

### Post by Simian Man on 2009-12-07
Honestly, just install Windows XP.  It sounds like she'll only run a few applications - web browser, a word processor, maybe Skype.  Using those applications on Windows will be no harder than running them on Linux (and possibly easier), so I don't see why you think Linux will somehoe be easier for her.

Dial-up is something of a hassle with Linux.  It's not hard, but it's not as easy as wireless.  If you lived down the street, then getting the it all setup and everything would be doable, but otherwise no.  If she has problems with XP in some way, she can likely find someone local to help her.  Not so with Linux.

Install a fresh XP, and then add an Antivirus like AVG, whatever applications she might use and make big links on the dekstop.

> **cartisdm said:**
> In reference to the Remote Desktop and SSH, I will need a GUI envirement.  I am not comfortable enough with the terminal to make adjustments remotely so I will want to literally be able to see her desktop, mouse her mouse via my mouse, and make any small adjustments as needed (if needed).

Running VNC or X11 over SSH over dial-up will be slow to the point of being completely useless.

---

### Post by cartisdm on 2009-12-07
> **mamamia88 said:**
> i would just buy my grandma a mac or something.  at least it has commercial support if something goes wrong.  maybe a mac mini or something

Um.....pass.  I don't have money falling out of my wallet that I can throw towards a computer that will just operate as a web browser.  I am planning on getting this whole setup, monitor and peripherals included, for less $200

---

### Post by mamamia88 on 2009-12-07
you gonna build it or get it second hand?  a monitor itself will set you back at least $100 good luck

---

### Post by cartisdm on 2009-12-07
> **mamamia88 said:**
> you gonna build it or get it second hand?  a monitor itself will set you back at least $100 good luck

A 15'' refurb LCD monitor on tiger direct is only $60.  I can get a small case (off-lease) desktop computer for cheap

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5311073&CatId=119](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5311073&CatId=119)

Anyone have any experience on installing linux to one of these ThinkCentres?

---

### Post by mamamia88 on 2009-12-07
well i stand corrected that will be more than enough for your grandma.  just use it for a month or so before you give it too her to make sure bugs are worked out so you don't have to troubleshoot over phone and you should be fine

---

### Post by speedwell68 on 2009-12-07
My suggestion for a decent distro and interface would be Mint 8.  I have just installed it on my Uncle's new machine.  It is perfect out of the box.  Why not install the Netbook-launcher as an interface, it is so easy to tailor to even the most novice user.

---

