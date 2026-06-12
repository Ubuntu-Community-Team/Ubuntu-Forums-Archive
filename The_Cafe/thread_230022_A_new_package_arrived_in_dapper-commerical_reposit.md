---
title: "A new package arrived in dapper-commerical repository"
date: 2006-08-05
forum: The Cafe
---

### Post by ubuntu_demon on 2006-08-05
A new package arrived in dapper-commerical repository
[http://ubuntudemon.wordpress.com/2006/08/05/new-package-for-dapper-commerical-repository/](http://ubuntudemon.wordpress.com/2006/08/05/new-package-for-dapper-commerical-repository/)

[Panda DesktopSecure](http://www.pandasoftware.com/products/DesktopSecure_part.htm?sitepanda=particulares) is added to the dapper-commercial repository.

If you enabled the dapper-commercial-repository then this will give you some more information :

$sudo apt-get update
$apt-cache show desktopsecure

Personally I don&#8217;t need a program like this. Ubuntu is quite secure and the developers are constantly improving Ubuntu&#8217;s security.
But in my humble opinion offering choice and making it easy to buy and install commercial software is a good thing.

This is a 90 days trial. It isn&#8217;t needed to install this software but if you insist here&#8217;s how to install it :

$sudo apt-get install desktopsecure

---

### Post by lazyd2 on 2006-08-05
*edit*

---

### Post by ubuntu_demon on 2006-08-05
$apt-cache show desktopsecure
> 
 Panda DesktopSecure for Linux is a security suite including:
 .
 Firewall protection. Protection against network attacks, not only at
 the network layer but also at the application layer. It detects which
 application is using the network and asks the user whether to grant or
 deny the access to it.
 .
 Antivirus protection. Protects the computer against all types of viruses,
 worms and Trojans, in both Linux and Windows (if the computer is used
 as a Windows file server for example).
 .
 Protection against unknown malware. This system includes detection of
 unknown malware using heuristic technology.
 .
 Permanent and on-demand mail protection. Protects your mail accounts
 from different types of malware that can reach your computer or protect
 the end-users from malicious messages sent from your system.
 .
 XWindow console to easily configure the settings of the product.


When I started DekstopSecure it showed me a lot of popups. It instantly reminded me of norton antivirus :-s. 

Some people want software like this. In my humble opinion offering choice is a good thing.

---

### Post by lazyd2 on 2006-08-05
> In my humble opinion offering choice is a good thing. I agree. 
I like Panda, used it on Win.

---

### Post by slimdog360 on 2006-08-05
I feel like installing it to see how it goes. I remember I used to use norton on windows but after a virus got on there and killed norton I was unable to delete the horrible antivirus. I found a free copy of panda with a magazine and it fixed up the virus right away (the actual virus not norton). After that I never used norton again but was always a fan of panda.
However I think in linux I'll stick with no antivirus and guarddog as my firewall thanks.

edit: when I told everyone about this panda software a few months ago I got insulted by about 1000 people (okay maybe not that many). I wish I was a forum staff member.
[my other thread where I was put down:(]("http://www.ubuntuforums.org/showthread.php?t=176753://")

---

### Post by ubuntu_demon on 2006-08-05
antivirus and a desktop firewall is not needed in Ubuntu at this point in time. There are multiple threads in the  Security Issues section about this :

[http://www.ubuntuforums.org/forumdisplay.php?f=7](http://www.ubuntuforums.org/forumdisplay.php?f=7)

But some people insist on using software like this. Choice is a good thing as I said before :).

---

### Post by Terracotta on 2006-08-05
Why does installing it installs libgksu in KDE? I thought we hade kdesu for that? I'm gonna check if it's worth it, love Opera, so perhaps closed source can be fine after all :idea: .
(KIDDING)

---

### Post by OffHand on 2006-08-05
This app reminds me of my XP time hehe
Anyways, I don't mind commercial sofware... whatever floats your boat :-P

---

### Post by Terracotta on 2006-08-05
> **subsonic_shadow said:**
> This app reminds me of my XP time hehe
Anyways, I don't mind commercial sofware... whatever floats your boat :-P

Ugh, just tried it, euh well, didn't get to try it, after installation it didn't appear in kicker, tried from the terminal:
desktopsecure
didn't work, restarted kicker nothing
restarted X and KDM
couldn't log in anymore, after typing my password it always returned to the KDM login screen. I'm veeeery positive that I dind't change anything that could breake my system (though I was running kde 3.5.4 but everything worked, it was a fresh startup...). Huh well this is the second time I have problems with these firewall things, guarddog made my internet connection breake and desktopsecure made my desktop breake. Huh well the most secure desktop is no desktop I guess...:-( )

---

### Post by lazyd2 on 2006-08-05
Installed it and so far its running great...

---

### Post by mitjab on 2006-08-05
i must pay for this?
Isn't free?

---

### Post by lazyd2 on 2006-08-05
> **mitjab said:**
> i must pay for this?
Isn't free?
Its free for 90 days.

---

### Post by lazyd2 on 2006-08-05
...

---

### Post by Anduu on 2006-08-05
A lot of people seem to be missing the point....

No there isn't a real need for Firewall/Antivirus.....right now.There is no incentive for hackers to go after Linux systems as they represent only a meager fraction of the OSes out there right now.Their goal is to cause the most damage possible on a large scale.

Now you can bet dollars to doughnuts that as Linux becomes more and more mainstream viruses/trojans/malware ***WILL*** start popping up and if we continue with this attitude that the "Mighty Linux" is impervious to such attacks a lot of people are going to get caught with their pants down.

We need to start protecting ourselves now.As they say an ounce of prevention is worth a pound of cure.

---

### Post by richbarna on 2006-08-05
> **Anduu said:**
> A lot of people seem to be missing the point....

No there isn't a real need for Firewall/Antivirus.....right now.There is no incentive for hackers to go after Linux systems as they represent only a meager fraction of the OSes out there right now.Their goal is to cause the most damage possible on a large scale.

Now you can bet dollars to doughnuts that as Linux becomes more and more mainstream viruses/trojans/malware ***WILL*** start popping up and if we continue with this attitude that the "Mighty Linux" is impervious to such attacks a lot of people are going to get caught with their pants down.

We need to start protecting ourselves now.As they say an ounce of prevention is worth a pound of cure.

If you aren't running as root, how can any piece of software, or even a script, install and run?

Take a standard attack, first there is a scan for vulnerable computers, then a dropper with a trojan is installed and a virus/worm is downloaded and installs itself. If you are behind a router, logged in as a user, that is practically impossible.

Remember that most infections are caused by people opening attachments they shouldn't, dubious infected downloads or by visiting websites specifically designed to exploit an unpatched windows box.

"Never underestimate the predictability of stupidity" The vius writer's motto.

---

### Post by Anduu on 2006-08-05
> Remember that most infections are caused by people opening attachments they shouldn't, dubious infected downloads or by visiting websites specifically designed to exploit an unpatched windows box.

Excactly...

And to reiterate...

> Now you can bet dollars to doughnuts that as Linux becomes more and more mainstream viruses/trojans/malware WILL start popping up and if we continue with this attitude that the "Mighty Linux" is impervious to such attacks a lot of people are going to get caught with their pants down.

---

### Post by jc87 on 2006-08-05
I know choice is a good thing , but in my modest opinion there are many other commercial packages that are way more important than an AV for Gnu/Linux.

Just for curiosity , does Panda actually protect from "Gnu/Linux virus" or is just an placebo?

---

### Post by OffHand on 2006-08-05
> **Anduu said:**
> A lot of people seem to be missing the point....

No there isn't a real need for Firewall/Antivirus.....right now.There is no incentive for hackers to go after Linux systems as they represent only a meager fraction of the OSes out there right now.Their goal is to cause the most damage possible on a large scale.

Now you can bet dollars to doughnuts that as Linux becomes more and more mainstream viruses/trojans/malware ***WILL*** start popping up and if we continue with this attitude that the "Mighty Linux" is impervious to such attacks a lot of people are going to get caught with their pants down.

We need to start protecting ourselves now.As they say an ounce of prevention is worth a pound of cure.

How about no? Linux isn't safer because of obscurity. It is safer because users and permissions are set up differently.

---

### Post by Perfect Storm on 2006-08-05
Seems quiet nice. Going to test it.

---

### Post by Anduu on 2006-08-05
> **subsonic_shadow said:**
> How about no? Linux isn't safer because of obscurity. It is safer because users and permissions are set up differently.

Think what you will but Linux day *is* coming...

---

### Post by jc87 on 2006-08-05
> **Anduu said:**
> Think what you will but Linux day *is* coming...

Why windows is soo vulnerable to virus :

A) You run as root for default , so when you execute something it has got automatically admin privileges to do what it wants.

B) IE is part of the OS and not just an browser , which is the security disaster we all know

C) You dont have repositories , so you need to download software from several different mirrors that may give you spyware instead of what you want.

D) Security patches take way too much time to come out.


Why Ubuntu is not:


A) If you execute a virus it cant screw your system over unless you give him root permissions.

B) If you use only thrust-worthy repositories what you select is what you get wyswyg

C) Security patches are very quick to appear after the flaw is detected , in the past i remember a few hours after i read the news about it i already have my system updated  , most times even before.



I personally think AV´s at Gnu/Linux are more an placebo than anything else , and the only utility i can see is if you have an win partition and you want to scan from within Gnu/Linux , because how do you expect to be more protected? do you want the av asking you if you really wanted to give root permissions to app X ? is going to scan your .debs and see if contains any package that will change the OS? is going to add another firewall to the one that already is in the kernel?

Keep your system updated , dont give root permissions to strange executables , and dont use weird repositories , do that and you will be safe.

---

### Post by Anduu on 2006-08-05
A few articles....no they are not all screaming "The sky is falling!!!"...

[http://infosecuritymag.techtarget.com/ss/0,295796,sid6_iss407_art817,00.html](http://infosecuritymag.techtarget.com/ss/0,295796,sid6_iss407_art817,00.html)
[http://lwn.net/Articles/179465/](http://lwn.net/Articles/179465/)
[http://www.claymania.com/unix-viruses.html](http://www.claymania.com/unix-viruses.html)
[http://www.desktoplinux.com/articles/AT3307459975.html](http://www.desktoplinux.com/articles/AT3307459975.html)

---

### Post by slimdog360 on 2006-08-06
I just installed it about an hour ago.
The install went fine, but then I had to reboot the computer after it installed, something I hate.
    
After the restart I was bombarded by popups saying that my antivirus was out of date. So when I tried to update it tells me I had to register with them, again something I hate.
    
So everything has updated and I think, "what the hell, I'll scan the hdd". That takes forever, during which my cpu is going full ball so I cant do anything else and but surprise, there is nothing wrong with my computer. Oh and during the scan I had about 5 popups saying that I had to scan my computer (a small glitch I suppose, but annoying).

 Now when I wanted to connect to the internet another pop up saying do I want to allow firefox to connect to the internet.
I think Im going to have to uninstall it, I cant have all these troubles.

However it is nice to see companies taking more interest in linux. Who knows maybe (woops sorry I just got another pop up, okay its delt with) Canon will start spending 10 minutes to make drivers available for linux.

Anyway I think for now I'll stick with guarddog as a firewall and nothing else, none of those dreaded popups.

---

### Post by Perfect Storm on 2006-08-06
Have the exactly same experience as Slimdog360. But I'll like to add that you can set it to auto-allowed for an application, so there aren't many pop-ups after it all are set.

But it seems a bit power hungry IMO :-({|= 
The good thing is it's very professional done and very easy to use, if you are a newbie. But I don't think a more experienced user can get anything from it.

Edit:

It found my eicar test file and deleted it automatically, so it's a good idea to set it to only report (to avoid it's messing something up).
Also 45 euro for a year is a bit to much IMO. If I have to pay for such application which a based on subscription, I think 29 euro is more realistic comparing to almost non-existing virus thread for linux.
I would say use F-prot instead. It can do more and it's free, and it's a whole lot more lightweighted.

---

### Post by LordMau on 2006-08-06
Does the panda firewall here interfere with firestarter if installed?

---

### Post by Adamant1988 on 2006-08-06
How good is the firewall as compared to FireStarter?

I would like to use this though... one of the main reasons I came to linux was for security reasons... even Linux isn't immune completely.

---

### Post by Anduu on 2006-08-06
Basically anything like firestarter,panda,guarddog etc are just "front ends" to iptables.

They just allow you to configure iptables to suit your needs.

---

### Post by Anduu on 2006-08-06
> **LordMau said:**
> Does the panda firewall here interfere with firestarter if installed?

I would assume that having more than one would cause problems...

---

### Post by OffHand on 2006-08-06
> **Anduu said:**
> A few articles....no they are not all screaming "The sky is falling!!!"...

[http://infosecuritymag.techtarget.com/ss/0,295796,sid6_iss407_art817,00.html](http://infosecuritymag.techtarget.com/ss/0,295796,sid6_iss407_art817,00.html)
[http://lwn.net/Articles/179465/](http://lwn.net/Articles/179465/)
[http://www.claymania.com/unix-viruses.html](http://www.claymania.com/unix-viruses.html)
[http://www.desktoplinux.com/articles/AT3307459975.html](http://www.desktoplinux.com/articles/AT3307459975.html)

Your links didn't convince me mate. I trust on common sense.
Virusses are not going to be installed by itself, unlike Windows.
If you stick with the repositories and trusted sources for your software, the chance of getting a virus is almost non-existent.

---

### Post by Mathiasdm on 2006-08-06
> **ubuntu_demon said:**
> antivirus and a desktop firewall is not needed in Ubuntu at this point in time. There are multiple threads in the  Security Issues section about this :

[http://www.ubuntuforums.org/forumdisplay.php?f=7](http://www.ubuntuforums.org/forumdisplay.php?f=7)

But some people insist on using software like this. Choice is a good thing as I said before :).
Err... A firewall is A Good Thing, be it for Windows, Linux, BSD or anything else.
And installing an Antivirus can be useful, if only to protect your Windows-using friends (you can't get infected yourself, but you can pass the virus along!).

Oh, and I'm not going to install is, seeing as it's a trial thingy (I don't like trial thingies :-P )

---

### Post by ubuntu_demon on 2006-08-06
> **bc87]
I personally think AV´s at Gnu/Linux are more an placebo than anything else 
[/quote]

I agree unless you want AV in order to scan for windows virusses.

But having a placebo is nice. I think some people will insist on running AV because they are used to windows and if they can't easily run AV on Ubuntu they will blame Ubuntu.

[QUOTE=slimdog360 said:**
> 
However it is nice to see companies taking more interest in linux. Who knows maybe (woops sorry I just got another pop up, okay its delt with) Canon will start spending 10 minutes to make drivers available for linux.


I agree. It's great that slowly companies are taking more interest in GNU/Linux.

I really like the dapper-commercial repository. Having commercial software easily available in Ubuntu is great.

---

### Post by ubuntu_demon on 2006-08-06
> **Adamant1988 said:**
> How good is the firewall as compared to FireStarter?


Firestarter is great. Ubuntu is secure by default(no open ports). If you don't run a server then you probably won't need a firewall at all.

IMHO the practical differences between firestarter and DesktopSecure's firewall :

- more hassle and popups with DesktopSecure
- non-geeks don't understand the concept of ports and therefor firestarter is a bit hard. (but most people don't need it anyway)
- DesktopSecure can restrict software from using the internet connection whereas firestarter can only restrict ports. This is only an issue when you download and install malicious software from the internet instead of using the recommended repositories.

---

### Post by Perfect Storm on 2006-08-06
I actually don't see how a newbie can use the popup allow/not-allow when they don't know the linux, the names of the diffrent stuff that want to access etc. etc., there's a bigger chance that they cut themself off the internet with an accident.

---

### Post by ubuntu_demon on 2006-08-06
> **Artificial Intelligence said:**
> I actually don't see how a newbie can use the popup allow/not-allow when they don't know the linux, the names of the diffrent stuff that want to access etc. etc., there's a bigger chance that they cut themself off the internet with an accident.

For people without computer experience DesktopSecure is a hassle. Let's hope people without computer experience trust the fact that Ubuntu is secure on default instead of trying to install stuff they don't understand.

I think DesktopSecure is mostly targeted towards ex-windows users who insist on buying AV and firewall.

Most people who have windows experience always click "yes/allow/okay" unless they are absolutely sure they want to click "no/don't allow". At least that's my experience with a lot of people who use windows. DesktopSecure will make them feel a bit safer. Although it's primary useful purpose is scanning for windows virusses.

---

### Post by ubuntu_demon on 2006-08-06
You can also find Panda DesktopSecure here :

Applications -> Add/Remove -> System Tools

---

### Post by arkangel on 2006-08-06
well i dont know ,  it seems to be consuming a lot of resources , and  i never  heard a virus attacking on Linux system,  and showed some pop ups  for buying :S the professional edition , for a minute  i thought i was in  windows , fortunately  it is not disturbing me any more ;) , well i would like to see the  private sector doing more useful than a popup launcher applicantion . On the other hand ,  it is good to we have more to choose

---

### Post by Perfect Storm on 2006-08-06
Just discovered that Panda have a gtkrc file in /opt/panda/DesktopSecure/share/pavdsk which means you customize it. Also noticed that it uses its own GTK engine 
```
  engine "/opt/panda/DesktopSecure/lib/gtk-2.0/engines/libpavengine.so"  {
  }
}

style "pav-clearlooks-wide" = "pav-clearlooks-default"
{
  xthickness = 2
  ythickness = 2
}
etc. etc. etc.
```
If it's possible to point it to the GTK2 engine on Gnome instead of its own (without breaking the application), there might be some resourceses to been saved.

---

### Post by Buffalo Soldier on 2006-08-06
> **subsonic_shadow said:**
> How about no? Linux isn't safer because of obscurity. It is safer because users and permissions are set up differently.True. GNU/Linux is a lot safer because of those reasons and many others.

But people who have been Windows for too long have had their mindset to "OS can not survive without Anti-Virus". Their experience with OS from Microsoft has been so terrible that they can't seem to fathom that an OS can be built tough.

It is for this people that we should provide options for Anti-Virus. Even though it's just for placebo effect, but at least it keeps things calm in here.

---

### Post by jamesford on 2006-08-06
Having converted from windows about a year ago I now see no need for this. Back then I would have installed it right away. It takes a while getting rid of all the Windows habits.

---

