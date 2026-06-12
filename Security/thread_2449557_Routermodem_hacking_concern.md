---
title: "Router/modem hacking concern?"
date: 2020-08-29
forum: Security
---

### Post by atoota on 2020-08-29
Hello

I recently decided to try Linux for the first time. I had an old-ish desktop that ran Win8, but I wasnt using it anymore. I deleted everything from it using dban, and decided to put on Lubuntu 18.04 (I think it was .04) to try out Linux. I'm quite liking it, but after connecting it to the internet and trying a few things such as an online game, playing a dvd etc, I began to wonder about security. Is it possible for someone to hack through my computer to gain access to my router and modem, and therefore gain access to the other computers (Windows machines) I have connected to the router and modem and gain entry to them? None of the computers are networked to one another, but they all share the same internet connection through the same router and modem.

Thanks for any help.

---

### Post by Tadaen_Sylvermane on 2020-08-29
You need to look at the progression. Modem > Router > Lan. They can't get to your computer until they have already hacked your Modem / Router. That being said while I haven't got the time at the moment to find some, do some Googling for Linux security in comparison to Windows security. While not immune, Linux is generally far more secure with the exception of physical access. To be fair though, if someone has physical access then you are screwed no matter what OS you run.

TLDR: Your Linux computer is far safer to use than any of your Windows computers.

---

### Post by T6&amp;sfpER35% on 2020-08-29
that being said , 1st step is to change your router's default password.
plus make sure your firewall on linux is** on** .
you should be good to go ...

linux is** secure enough,** by far

---

### Post by Impavidus on 2020-08-29
Don't worry about a hacker gaining access to your Windows computer by first hacking your Linux computer. A hacker is more likely to gain access to your Windows computer directly. Your Linux computer is probably the most secure computer in your home.

That is, assuming it was indeed 18.04, not 18.10, which is no longer supported. Lubuntu 18.04 has another 8 months of support left, so that's not very long. Before it reaches end of life, you have to fresh install 20.04.

---

### Post by wildmanne39 on 2020-08-29
Moved to Security Sub-Forum.

---

### Post by atoota on 2020-08-29
Righto, thanks for all the replies. That makes me feel safer.

Yeah, I changed my default router password to something rather long and complicated when I set it up. How do I tell if the firewall on Linux is on though? Cant seem to find what it is located under.

Yep, checked and it's 18.04.5, so I guess it's got another few months left. When I upgrade to 20.04, can I use the upgrade function thingy 'Software Updater', or should I burn an .iso and install it that way, like I did with 18.04?

Not allowing any incoming traffic that I'm aware of - dont have any of those things going, not running a web server or the like.

Sounds good then.

Incidentally, if I wanted to check my router for hacks, is it something fairly simple to do? I'm wondering how to go about checking something like that. Purely out of interest.

Thanks again

---

### Post by EuclideanCoffee on 2020-08-29
The short answer is that yes, you can be hacked and have your computer infect other computers in your LAN.

Are you safer using Ubuntu?

The answer is neither yes or no. Any computer is vulnerable. But you can improve your computer's security by using it safely on any computer, regardless of operating system.

As long as you're using someone else's server, whether that is gaming or surfing the web, you trust that the person serving you the data will not be malicious. So if your concern is what happens if someone tries to hack your computer while playing video games, you need to consider what behavior puts you at risk. Whenever you use a gaming server, first you will likely download files from the game server. Make sure you either trust or accept the risk of the server you download from. It can be compromised and send you bad files. These bad files would be used to run software over your computer (or try to). It is possible for people to write software that runs malware on Linux software. The most powerful bot networks are Linux computers running software for someone else. These bot networks are Linux computers running this malware.

Now what should you do? How do you trust anyone?

Well, first put sometime into learning what security features are enabled and how to use them.

Ubuntu uses a whole set of security features. For video games it's incredibly limited. So if you use games, maybe stick to official or safe servers when possible.

But for browsing, you can rely on the security of Firefox or Chrome, which is pretty strong. To improve security you can use ufw to run default blocking settings. What would this do? Well, it can block scripts from accessing your LAN in case your computer is ever compromised, protecting your network from your device.

As you can see, this topic is an incredibly exhaustive. Here's a little list of things you can do today, but obviously there is much more we could talk about. :)

[https://nakedsecurity.sophos.com/2015/05/27/5-tips-to-improve-your-linux-desktop-security/](https://nakedsecurity.sophos.com/2015/05/27/5-tips-to-improve-your-linux-desktop-security/)

---

### Post by atoota on 2020-08-29
Ok, thanks. That's helpful information. Actually I do those things on my Windows machines already but nice to get a refresher. I followed the instructions to set up the firewall on 18.04 too, thanks. Kinda scared to play games now lol; no loss though, usually way too busy to game much anyway!

Is there some easy way to test my router etc now? I use an antivirus for my Windows machines, as well as MalwareBytes and Spyware Blaster. Can one of the first two be used to check my network and router?

---

### Post by EuclideanCoffee on 2020-08-30
Good question. Network security is better understood from the router. Your router sends your data through its gateway to other routers outside your LAN. To see what these routers are, using the traceroute command inside Ubuntu’s terminal you can see what router address comes outside of your immediate IP and so on.

You may wonder how to access your router. Use one of these commands in this help forum as a way to find your router address.

[https://askubuntu.com/questions/605424/how-to-show-just-the-ip-address-of-my-router](https://askubuntu.com/questions/605424/how-to-show-just-the-ip-address-of-my-router)

Once found, type in the IP address of your router and enter its console. From here you will need some help from your IPS. But what we intend to do here is make sure you how port forwarding disabled. Check that all devices connected you can recognize. And also check the logs for anything weird. If you find something funny, just google it until it makes sense.

Now that your network is secured, you should feel pretty safe. But your end points will still be at risk.

For Ubuntu, since this is an Ubuntu support forum, you can rely on the built in security model for most things unless you use WINE or run anything in sudo or root. Doing so bypasses Linux security. This means you need to run your programs as your user without elevated privileges. You shouldn’t need to enter your password.

For anti-virus, there are far and few vendors. ClamAV and RKhunter are popular, but they are not feature rich nor contemporary enough to see advanced threats. I this case you need to realize that anti-virus will likely catch nothing.

---

### Post by guiverc on 2020-08-30
> **atoota said:**
> 
Yep, checked and it's 18.04.5, so I guess it's got another few months left. When I upgrade to 20.04, can I use the upgrade function thingy 'Software Updater', or should I burn an .iso and install it that way, like I did with 18.04?


Lubuntu 18.04 was the last Lubuntu using the LXDE desktop.

The Lubuntu 20.04.1 release notes are [https://lubuntu.me/focal-1-released/](https://lubuntu.me/focal-1-released/) and which state

> ***Note***, due to the extensive changes required  for the shift in desktop environments, the Lubuntu team does not support  upgrading from 18.04 or below to any greater release. Doing so will  result in a broken system. If you are on 18.04 or below and would like  to upgrade, please do a fresh install.

Yes the Lubuntu team wrote notes on upgrading from 18.04 to 18.10 (*the first release using LXQt*), however those notes were never publicly posted so you'll have to hunt to find them, and even following those, you'll likely have issues.  Upgraded systems are not supported (*due to problems that are encountered*).  Yes it's possible; the system I'm using now was a LXDE system upgraded... but expect problems if you don't re-install (at least for a time, I  did on this box).

You can re-install without format like other releases, which is what I'd do (having done it many many times). Depending on changes made to your older system, minor glitches maybe encountered (due to outdated system configs that remain), but it's still what I'd do, and those minor glitches were quick to fix (*taking minutes instead of days-weeks*). Regardless backup first as with anything.

---

### Post by atoota on 2020-08-30
Ok, thanks EC. I did all that, port forwarding is disabled. Seems to have been already. Went through the log and nothing seems suspicious. Guess it's as good as it's going to get.

One game I tried required me to run a command through WINE to get it to play. I guess that is not so great, in terms of security?

Guiverc, thanks for the info. I'll do a fresh .iso install then.

Cheers

---

### Post by EuclideanCoffee on 2020-08-30
> 
[COLOR=#000000]One game I tried required me to run a command through WINE to get it to play. I guess that is not so great, in terms of security?


Not completely bad. Do you trust the vendor? If so, it should be fine. Are you playing online? If so, are there official servers or servers maintained by the game's vendor? If so, you're likely safer than running on a community server.
[/COLOR]

---

### Post by atoota on 2020-08-30
> **EuclideanCoffee said:**
> Not completely bad. Do you trust the vendor? If so, it should be fine. Are you playing online? If so, are there official servers or servers maintained by the game's vendor? If so, you're likely safer than running on a community server.
[/COLOR]

Hmm unfortunately I think it's more of a community server? I'm not sure exactly though. The game in question I've linked below. It's a game I played nearly a couple of decades back for a year or two. It went through various iterations and eventually got completely cancelled around 2011, I believe. In the last few years there have been a few of these emulator servers bringing it back to life. I noticed the linked one below a couple of weeks back and decided to give it a try on the Linux machine I set up. (The original was simply Star Wars Galaxies) I havent played it since posting here lol.

[https://swglegends.com/](https://swglegends.com/)

---

### Post by TheFu on 2020-08-30
For all computing devices, stay patched, create backups, don't visit dangerous parts of the internet.  Routers are just computers with extra networking hardware.

Almost all consumer routers are poorly maintained. Some small biz routers do a good job of making patches available, but those tend to be a little harder to configure than what a home user would have.  Pay attention to all router bugs in the news and take action.
[https://arstechnica.com/information-technology/2018/06/vpnfilter-malware-infecting-50000-devices-is-worse-than-we-thought/](https://arstechnica.com/information-technology/2018/06/vpnfilter-malware-infecting-50000-devices-is-worse-than-we-thought/)
[https://www.zdnet.com/article/fbi-recommends-that-you-keep-your-iot-devices-on-a-separate-network/](https://www.zdnet.com/article/fbi-recommends-that-you-keep-your-iot-devices-on-a-separate-network/)
[https://securityledger.com/2019/08/huge-survey-of-firmware-finds-no-security-gains-in-15-years/](https://securityledger.com/2019/08/huge-survey-of-firmware-finds-no-security-gains-in-15-years/)
All those extra features on home routers tend to have security flaws and should not be used.  Don't connect storage to the router. Don't setup FTP access externally, and don't use the DLNA server that some routers have.  There is a long history of router vendors adding "features" that should never exist or be used on any router.  Routers need to do 2 things. Route and firewall. Anything else is adding complex software and asking to be hacked.  If your router firmware hasn't been patched in the last 30 days, assume it is out of date and go get the newest version. All routers should have been patched a few times this year. If that hasn't happened, then your router is out of support and needs to be replaced.
Or you can move to a type of router that is maintained and patched more like Ubuntu is, nearly weekly, there are updates/fixes available for some router distros.  Many well-known "brands" of consumer routers have terrible security records.  A few have been so bad, they are mandated by the govt to be monitored for 20 yrs to ensure they maintain the hardware they sell with fixes to the firmware.

For Ubuntu, the Basic security guide should be sufficient for most home users:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

There are security guides for almost any need,  Do online banking? There are techniques to reduce risk over on Brian Krebs' website. Best to be paranoid even when "they" aren't out to get you, since "they" are out to get anyone they can. All of us.  

Stay patched, have daily, automatic, versioned, backups.  Know how to restore the backups from yesterday or 33 days ago.  That's the summary.

---

### Post by EuclideanCoffee on 2020-08-31
Regardless of which operating system you use, you'd need to trust that service. I'm actually familiar with Star Wars Galaxy. I didn't pick it up because I felt uncertain about the service. It's not that I distrust people and think they would do intentional harm while hosting a game, I suspect their infrastructure could be taken over easily. The same for any continuation of a video game online. I have to wonder if some of these computers are XP machines running software 2 decades old. Having done some online game development maintenance has made me wary of them. :)

If you look at the wiki on basic security, do a control + f find function for WINE. In it, you'll see many warnings on how malware can run from WINE. Though this is true, malware is common to Linux as well, but malware for Linux is commonly transmitted different methods and not through web browser hacking and the like. Since Android is a commonly used Linux device that uses a commonly used security feature called SELinux, it's not true that you are also absolutely safe with vanilla Linux anything, even following basic security.

What can you realistically do?

As I said earlier, it comes down to trust. Think of every web site you visit, every game you play, and every program you run as a thing of trust. Ask if you trust whatever you are about to do. You can come up with a pretty strong answer by asking yourself if you know what the source code is, if it has been vetted by security experts (see updates for security fixes, CVEs), if the program has direct access to your root (do you need to run sudo or su), and if the service sends data back to a web server.

Based on how many yeses and noes you decide on, then you know what is a gap. After you determine the gaps, see if you can willing to accept the gaps in order to use the software. Sometimes you just can't say no to playing a fun game with friends online. But maybe only do it on an old dedicated desktop that has limited access to the rest of your LAN. :) Good luck.

---

### Post by atoota on 2020-08-31
Righto, thanks. Yeah, I dont think the people running the server would be out for doing malicious harm either. Just, as you say, others who might take advantage of such a server. I guess one saving grace for these SWG emulator servers is that the populations are pretty small, and likely wouldnt attract too much attention.

Yeah, the desktop I put Linux on, was pretty much as you describe. It was an old Windows machine that I was no longer using. I deleted everything using dban, then put Lubuntu 18.04 on it. I used the browser a couple times, played a DVD, and the rest has simply been Star Wars Galaxies. All my work, and everything else, is done on a couple of other machines (Windows based).  I dont have any kind of home network setup between any of the machines - they cant access one another. Nonetheless, would I be correct in thinking that as they all still use the same router, that makes the whole setup vulnerable?

This thread has scared the proverbial outta me lol! I disconnected the Linux desktop from the internet, and will probably run dban on it again. Then maybe just dismantle it and throw away the various pieces. It really is long in the tooth, and not good for much these days, so I wanted to experiment putting SWG on it to see if it would work. I guess I proved that it could do that, at least.

---

### Post by TheFu on 2020-08-31
> **atoota said:**
>  
This thread has scared the proverbial outta me lol! I disconnected the Linux desktop from the internet, and will probably run dban on it again. Then maybe just dismantle it and throw away the various pieces. It really is long in the tooth, and not good for much these days, so I wanted to experiment putting SWG on it to see if it would work. I guess I proved that it could do that, at least.

I would be 10x more concerned about Windows than Linux behind a patched router.

PATCH YOUR ROUTER.

---

### Post by EuclideanCoffee on 2020-08-31
```

This thread has scared the proverbial outta me lol! I disconnected the  Linux desktop from the internet, and will probably run dban on it again.  Then maybe just dismantle it and throw away the various pieces. It  really is long in the tooth, and not good for much these days, so I  wanted to experiment putting SWG on it to see if it would work. I guess I  proved that it could do that, at least.                 

```

lol. I've been there. I'm still using Linux, but I guess I use it very differently today. :)

I seriously encourage you to at least try running the software from your old desktop. If data privacy is a concern (I notice you used dban), replace your disk with SSD (big upgrade). Encrypt your disk when installing. Lubuntu okay, but I recommend Xubuntu or MATE. Then enable UFW.

After that, start learning your other computer's security settings, learn which firewall you want to have, and monitor your router.

It seems scary, but knowing this stuff will really protect your privacy and personal security. You can also find a job doing this if that ever strikes your fancy. Best of luck.

Edit. If you have issues with UFW, I expect a new topic posted here. ;)

---

### Post by atoota on 2020-08-31
Righto, cheers. I did have the game running for nearly two weeks before it occurred to post here. So it works okay. That said, two weeks was enough lol. The game, back years ago, was pretty broken. Not much has changed, and the in-game economy...well I dont want to even use the word 'economy'...it's a mess. Suffice to say, I've had my fill.

All that said, I might dban (I dont really have that much stuff that is private. I suppose if someone wanted to steal my picture for voyeuristic purposes I'd be more concerned with their mental state than my pic being 'out there' lol ) it all again, and set up Xubuntu, just to have a look (at Xubuntu, not SWG).

TheFu, I'll look into getting a new router then. Mine is pretty old, and hasnt had a firmware update for a long time. I had no idea about all the things you mention about patching routers. That said, I dont use vpns, iots, or the like, so maybe that helps?

---

### Post by kevdog on 2020-09-11
What kind of router do you have?

---

### Post by ipv on 2020-09-11
> **atoota said:**
> How do I tell if the firewall on Linux is on though?

```
sudo ufw enable
```

```
sudo ufw status
```


> **atoota said:**
> Cant seem to find what it is located under.

the firewall gui might be more helpful :

```
sudo apt install gufw
```


> **atoota said:**
> I use an antivirus for my Windows machines, as well as MalwareBytes and Spyware Blaster.

anti-virus + mbam + spyblast = overkill

> **atoota said:**
> Can  one of the first two be used to check my network and router?

no.

---

