---
title: "Anouncing A New Ubuntu Variant?"
date: 2010-07-20
forum: The Cafe
---

### Post by Intel91 on 2010-07-20
Hey,

     I have been working on my own variant of ubuntu for quite some time, and it is getting close to being sufficiently polished to introduce to the community. This variant specifies in giving windows converts an easier time transition to linux. 

The core features include: 
1. Pre-installation of wine
2. Option for a more windows like interface (defaults to standard gnome if not specified).
3. Standard Wubi installation (in order to unlock all features, wubi install is a must).
4. Software (I wrote) that automatically searches your computer for windows applications, then sorts them and places them in familiar directories in your new ubuntu installation. (meaning your windows desktop icons appear on your ubuntu desktop, and are fully functional links to the windows application that will run in wine, icons are all copied as well. Your windows start menu is copied to Applications>Windows Applications, are once again fully functional as supported by wine.
5. Obvious ability to swap between ubuntu and Windows from grub, courtesy of wubi.
6. Option to constantly update windows applications to ubuntu, meaning if you install a new game on windows, it will automatically show up in ubuntu.
7. Space conservation, no double application installations courtesy of my software + wubi.
8. Pre-installation of all widely used, and some not so widely used, codecs and interface software (flash, moonlight, avi, java, etc...)
9. Everything else you're used to seeing on ubuntu, no features or applications are removed.

So, what do you guys think, do you like where I'm going? I know many nixers are purists, and my install is a purist's install, but I feel this is a great way to get more people to use ubuntu, and switch from windows. I first called this transition ubuntu (trubuntu) when I started it, but come to find out the domain name trubuntu (available at the time) was registered just a few months ago. 

Anyways, among announcing it and the features, I would like to know how I can go about introducing this to the community. I have no idea how I can introduce it and hopefully turn it into what edubuntu, xubuntu, etc. are.

Thanks for Reading,
Intel91

EDIT:
I decided to provide some screen shots of the optional Windows-like interface (once again, defaults to gnome). These are a bit old, and blotched out due to personal information, so I apologize for that. The lower left-hand T is just a temporary logo, in case anyone wonders why its so ugly.
Also to simply answer one very important question, there are no double installations of your windows apps, they take up only one installation on one partition and are shared between the two, for more information check post #10.

[IMG]http://i25.tinypic.com/mwe6wy.png[/IMG]
[IMG]http://i25.tinypic.com/5f18ci.png[/IMG]

---

### Post by Iowan on 2010-07-20
Moved to Community Cafe.
Not really a support request. ;)

---

### Post by jroa on 2010-07-20
Sounds interesting.  I would love to give it a spin around the block for you.  I am not sure of the best way to get people to use it, though.

---

### Post by Timmer1240 on 2010-07-20
> **Intel91 said:**
> Hey,

     I have been working on my own variant of ubuntu for quite some time, and it is getting close to being sufficiently polished to introduce to the community. This variant specifies in giving windows converts an easier time transition to linux. 

The core features include: 
1. Pre-installation of wine
2. Option for a more windows like interface (defaults to standard gnome if not specified).
3. Standard Wubi installation (in order to unlock all features, wubi install is a must).
4. Software (I wrote) that automatically searches your computer for windows applications, then sorts them and places them in familiar directories in your new ubuntu installation. (meaning your windows desktop icons appear on your ubuntu desktop, and are fully functional links to the windows application that will run in wine, icons are all copied as well. Your windows start menu is copied to Applications>Windows Applications, are once again fully functional as supported by wine.
5. Obvious ability to swap between ubuntu and Windows from grub, courtesy of wubi.
6. Option to constantly update windows applications to ubuntu, meaning if you install a new game on windows, it will automatically show up in ubuntu.
7. Space conservation, no double application installations courtesy of my software + wubi.
8. Pre-installation of all widely used, and some not so widely used, codecs and interface software (flash, moonlight, avi, java, etc...)
9. Everything else you're used to seeing on ubuntu, no features or applications are removed.

So, what do you guys think, do you like where I'm going? I know many nixers are purists, and my install is a purist's install, but I feel this is a great way to get more people to use ubuntu, and switch from windows. I first called this transition ubuntu (trubuntu) when I started it, but come to find out the domain name trubuntu (available at the time) was registered just a few months ago. 

Anyways, among announcing it and the features, I would like to know how I can go about introducing this to the community. I have no idea how I can introduce it and hopefully turn it into what edubuntu, xubuntu, etc. are.

Thanks for Reading,
Intel91
sounds like a good idea!

---

### Post by forrestcupp on 2010-07-20
This is really kind of interesting.  Most variants are just someone's favorite themes and apps installed.  You're actually putting effort into this to give it functionality that you can't just get from a vanilla install and the repos.

I hope this works out how you want it to.

---

### Post by Madspyman on 2010-07-20
Think this is cool, not a windows user though, but I'm sure it'd help me get a few of my Win using friends interested in Ubuntu. The less tech support I'll have to do the better. 

I wonder when (or if) virtualization will be (or is) far enough along to allow booting from a Windows partition in Ubuntu w/o screwing up the partition from booting normally. That way virtualization could be integrated in so that Ubuntu could run everything from a Windows install, without having to restart the computer, but if you wanted to you could. That'd be an awesome migration tool.

---

### Post by pinguy on 2010-07-20
> **Intel91 said:**
> 4. Software (I wrote) that automatically searches your computer for windows applications, then sorts them and places them in familiar directories in your new ubuntu installation. (meaning your windows desktop icons appear on your ubuntu desktop, and are fully functional links to the windows application that will run in wine, icons are all copied as well. Your windows start menu is copied to Applications>Windows Applications, are once again fully functional as supported by wine.

Wine is a great tool but it's no were near ready to run all the programs that can run on XP let alone Windows 7 or a 64-Bit Windows. Wine is fine for the odd program where you can't find a [alternative]("http://alternativeto.net/") but not for every program a user has installed on there Windows computer. If you are trying to make a Opensource Windows OS have you had a look at [Arwinss]("http://www.reactos.org/wiki/Arwinss").

Wouldn't it make more sense to detect what programs the user had installed on Windows then download the native version and installed that eg. firefox, thunderbird, songbird ect. and used [alternatives]("http://alternativeto.net/") for programs that didn't have a native version eg. MS Office, MSN messager,Nero ect. 

Running all the users windows program though wine and also coping them to the Ubuntu drive so they are taking up more space just seems pointless to me as they are never going to run as well as they do in Windows and will probably put the user off using Ubuntu.

You have a great idea here. I just think the way you going about it is wrong.

---

### Post by Primefalcon on 2010-07-20
I dont use windows anymore, but this sounds like something that I haven't really heard of anyone else offering, and with wine itself getting better and better at supporting windows aps now... Well I'd be very interested in seeing your finish product tbh....

You'd probably be better of setting up your own site for it, my advice would be to started with shared hosting and move from there as your requirements gets heavier.

---

### Post by chris200x9 on 2010-07-20
yes you are.

---

### Post by Intel91 on 2010-07-21
> **pinguy said:**
> Wine is a great tool but it's no were near ready to run all the programs that can run on XP, it's ok for the odd program if you can't find a [alternative]("http://alternativeto.net/"). If you are trying to make a Opensource Windows OS have you had a look at [Arwinss]("http://www.reactos.org/wiki/Arwinss").

Wouldn't it be better if it could detect what programs was installed on windows then downloads the native version and installed that eg. firefox, thunderbird, songbird ect. and used [alternatives]("http://alternativeto.net/") for programs that didn't have a native version eg. MS Office, MSN messager,Nero ect. 

Running all the users windows program though wine and also coping them to the Ubuntu drive so they are using twice as much space just seems pointless as they are never going to run as well as they do in Windows.

You have a great idea here. I just think the way you going about it is wrong.

To address some of the questions and concerns, I will elaborate just a bit what my software does. All ubuntu alternatives will be used: if you have office, you can use open office, if you have IE or Firefox, you can use ubuntu firefox, this won't take away from that. 

Now, onto what you said about copying over the installs (actual entire files), that's not what my software does. My software utilizes the wubi install to easily mount your windows drive, and share it. All applications will be run from the windows drive with a symbolic link back to that drive, in a form wine understand and can launch. My software, called Momentum, searches and analyzes all windows application links, then creates a linux launcher based on information found in the windows .lnk (shortcuts) in an intuitive and automatic manner, allowing your applications to appear on your ubuntu install, without taking up any extra space. The registry is the only thing, if I decided to implement it, that would be "copied" or become double data. For everything else, it is run off the single install on the windows partition.

Thanks for the positive responses everyone, this gives me a bit more motivation to finish this thing up, and I think that getting a domain and hosting an install might be the best way to start. Getting people to know about it, that is a different story;).

---

### Post by cogar66 on 2010-07-21
Sounds pretty cool, I'll be sure to check it out.

---

### Post by Dustin2128 on 2010-07-21
Looks interesting, but I'd highly recommend against an interface strongly resembling windows. Sure, have the single panel and same basic arrangement (window buttons on the right), but if it looks like windows, ***people will expect it to behave like windows. ***Just a tip.

---

### Post by earthpigg on 2010-07-21
this concept is pretty amazing.

i have a question: would there be any possibility of running native software and syncing the config files between windows and ubuntu?

ie: run native FF in ubuntu, bookmark something, and have that bookmark sync with Windows FF's bookmarks.

---

### Post by Intel91 on 2010-07-21
> **earthpigg said:**
> this concept is pretty amazing.

i have a question: would there be any possibility of running native software and syncing the config files between windows and ubuntu?

ie: run native FF in ubuntu, bookmark something, and have that bookmark sync with Windows FF's bookmarks.

Ahh. You know, I didn't think about that, there's a lot of syncing of other "things". But, that would be extremely easy to implement, thanks for the suggestion.

---

### Post by BenAshton24 on 2010-07-21
This sounds like a fantastic idea! I can't wait to see how it turns out.

> **Intel91 said:**
> The registry is the only thing, if I decided to implement it, that would be "copied" or become double data.

Registry copying is a must have, especially for programs that rely on registry data for licensing reasons such as photoshop. Perhaps also you could add a feature that checks to see if software will function and if it has any special requirements. This could be done by connecting to your distro's (future) server and checking a database. Your program could download scripts, as required, for getting different programs to function correctly. The community could submit scripts for different pieces of software and updates. Software functionality could be determined by checking appdb (I don't know if it has an API for this).

It would also be good if you could add an extra step to ubiquity which asks the user which programs they want to transfer from windows to their Linux installation. If not then a welcome program with the same features could be easily implemented. A similar interface could also be used for asking the user if they want to transfer newly installed programs as they are detected by your software. Transferring wine programs that the user installs on their Linux installation, back to windows would be great as well. You could have the two OSs perfectly in sync.

Sorry for rambling but I really like your idea :)

Good luck,
Ben.

---

### Post by earthpigg on 2010-07-21
> Registry copying is a must have, especially for programs that rely on registry data for licensing reasons such as photoshop. Perhaps also you could add a feature that checks to see if software will function and if it has any special requirements.

or, he could ***not*** assume the user is a thief until proven otherwise, and simply remove the registry malware by default in each and every case where it is encountered.


suggesting that he import digital restrictions management garbage from windows is a horrid idea.

in my humble opinion.

not that i would violate Intel91's zeroth freedom by proposing to impose my opinion on his activities.

---

### Post by Madspyman on 2010-07-21
> **Intel91 said:**
> My software utilizes the wubi install to easily mount your windows drive, and share it. All applications will be run from the windows drive with a symbolic link back to that drive, in a form wine understand and can launch. My software, called Momentum, searches and analyzes all windows application links, then creates a linux launcher based on information found in the windows .lnk (shortcuts) in an intuitive and automatic manner, allowing your applications to appear on your ubuntu install, without taking up any extra space. The registry is the only thing, if I decided to implement it, that would be "copied" or become double data. For everything else, it is run off the single install on the windows partition.

Wine's getting there, but it's still got some issues. I've tried to set Wine to use a Windows partition as its drive C: way back. It overwrites key Windows system files and makes the partition unbootable. 

Sounds like your creating links to boot the files from the Windows partition, keeping the Wine default C: in tact. When the Windows programs boot in Ubuntu won't they be looking in .wine/drive_c (or dosdevices/c: ) for the system files they need to boot? I'd imagine you'd also need to copy over system files (system32 etc..) that get installed during the original programs installation.

Maybe I'm just not following. I've never used wubi before either, so I'm not sure I can say.

---

### Post by BenAshton24 on 2010-07-21
> **earthpigg said:**
> or, he could ***not*** assume the user is a thief until proven otherwise, and simply remove the registry malware by default in each and every case where it is encountered.


suggesting that he import digital restrictions management garbage from windows is a horrid idea.

in my humble opinion.

not that i would violate Intel91's zeroth freedom by proposing to impose my opinion on his activities.

If you delete the registry data used by a photoshop installation then it will lock you out, regardless of whether your copy is legal or not. This is the case for many other programs as well.

If you are referring to software that is somehow inserted into the registry, then there is no such thing as "registry malware". If you are talking about a piece of malware designed to manipulate the registry, then the chances of such software being transferred to the Linux installation and functioning within wine are almost non-existent.

Not all data stored in the registry is "digital restrictions management garbage". Some programs store basic settings in there, which they require to function.

I dislike proprietary software as much as anyone, but Intel91 is attempting to bridge the gap between windows and Linux and allow windows users to see the numerous benefits of open source without such a steep learning curve. Preventing popular programs from functioning by not transferring necessary data does not make this goal any easier to reach.

Ben.

---

### Post by Stancel on 2010-07-21
> **Dustin2128 said:**
> Looks interesting, but I'd highly recommend against an interface strongly resembling windows. Sure, have the single panel and same basic arrangement (window buttons on the right), but if it looks like windows, ***people will expect it to behave like windows. ***Just a tip.

A Windows-style GNOME is much better than the ugly and tacky looking design of KDE. I am pretty sure a lot of people are put off by GNOME's two panels, it seems pointless, it is good to see a GNOME design that makes more sense. It might look like Windows but in my opinion that is a good thing.

---

### Post by Johnsie on 2010-07-21
I ignored this thread because it said 'ubuntu variant' and there are already alot of Ubuntu variants. However this project does seem interesting and original so I'm looking forward to giving it a shot.

To the guy who was talking about syncing firefox bookmarks, there are already firefox addons that can do that.

---

### Post by forrestcupp on 2010-07-21
> **earthpigg said:**
> or, he could ***not*** assume the user is a thief until proven otherwise, and simply remove the registry malware by default in each and every case where it is encountered.
It's not a matter of what he wants to do; it's a matter of what the software requires.  If software can't see its registry keys, it won't run.  That is something that can't really be changed with this project because he can't write a patch to reprogram every possible piece of software ever installed.

---

### Post by gemmakaru on 2010-07-21
Sounds like Winebuntu to me.  Is that name taken?

---

### Post by Madspyman on 2010-07-21
> **gemmakaru said:**
> Sounds like Winebuntu to me.  Is that name taken?

Maybe, Wubuntine.

---

### Post by Intel91 on 2010-07-21
Well, my reservation in copying over registry was not DRM or Malware, as previously mentioned, the likelihood of them being destructive to the linux environment through wine is a bit small. My reservation was more the legality, I'm not a lawyer. This may seem like a silly reservation, but I figured there might be a possibility key registry data in wine could be attacked by Microsoft. If that isn't the case, a registry copy will be immediately implemented.

Wine keeps its own c: on the linux partition, that is basically ignored by the new user. The links remain on the linux partition once copied as well and the links then tell linux what to do to open the file: open it in wine from the directory in the mounted windows partition. This prevents any break in either system. 

As mentioned earlier, this is my effort at a "perfect sync" (though not perfect) to make a bridge between linux and windows, so it isn't such a shock: "I downloaded -insert windows program here- from the internet, why doesn't it work?.... Linux doesn't work!!".

---

### Post by eriktheblu on 2010-07-21
I really like the idea even though I would never use it. The name should be considered carefully since I think Canonical may object to anything that looks like "Ubuntu".

---

### Post by JustinR on 2010-07-22
> **eriktheblu said:**
> I really like the idea even though I would never use it. The name should be considered carefully since I think Canonical may object to anything that looks like "Ubuntu".


[http://www.ubuntu.com/aboutus/trademarkpolicy](http://www.ubuntu.com/aboutus/trademarkpolicy)

Well you could make sure it aligns with this article and he's set! Hope the project will turn out well. It looks very nice.

---

### Post by Intel91 on 2010-07-22
> **JustinR said:**
> [http://www.ubuntu.com/aboutus/trademarkpolicy](http://www.ubuntu.com/aboutus/trademarkpolicy)

Well you could make sure it aligns with this article and he's set! Hope the project will turn out well. It looks very nice.

Wow, I'm glad you pointed that out. I read it, but I'm a bit worried about what is considered commercial. I'd like to possibly do a bit of ad hosting (on my website) to recover operating costs/time, but I don't plan on selling the variant to people or corporations. Does anyone have any experience with that? It seems that creating the variant will end up easier than hosting it, naming it, and promoting it.

---

### Post by earthpigg on 2010-07-22
the website being commercial and the distribution being commercial, i believe, are not the same thing.

it's not like you can/would prevent anyone from hosting it from their own website.

unless you plan on integrating the website into the distribution in some way, i'm pretty sure you will be fine.

and remember that the link above is only about **trademark**, not copyright. if it really comes down to it, remove the visible ubuntu logos and the word 'ubuntu' from the help menus and whatnot... look at what Linux Mint does to accomplish this.

Linux Mint is based on Ubuntu, and is clearly a commercial product hosted on a commercial website. They don't seem to have any problems :D

---

### Post by Lucifer The Dark on 2010-07-22
I hope you like honest opinions? Personally I don't see the need for another entire variant of Ubuntu, but parts of this are more than a little interesting.
> **Intel91 said:**
> The core features include:
1. Pre-installation of winePractically everyone installs this at some point so having it from first install would save time for lazy people like me. ;)
> **Intel91 said:**
> 2. Option for a more windows like interface (defaults to standard gnome if not specified).I prefer Gnome, I would imagine a lot of Nixer's would rather not have their OS looking like Windows, at least you're giving a choice & not just forcing it.
> **Intel91 said:**
> 3. Standard Wubi installation (in order to unlock all features, wubi install is a must).If this could work without wubi as well it would get a wider audience.
> **Intel91 said:**
> 4. Software (I wrote) that automatically searches your computer for windows applications, then sorts them and places them in familiar directories in your new ubuntu installation. (meaning your windows desktop icons appear on your ubuntu desktop, and are fully functional links to the windows application that will run in wine, icons are all copied as well. Your windows start menu is copied to Applications>Windows Applications, are once again fully functional as supported by wine.THIS sounds like a BRILLIANT idea, if you can get this to work without wubi you'd make a lot more people happy than you will already.
> **Intel91 said:**
> 5. Obvious ability to swap between ubuntu and Windows from grub, courtesy of wubi.See above.
> **Intel91 said:**
> 6. Option to constantly update windows applications to ubuntu, meaning if you install a new game on windows, it will automatically show up in ubuntu.See above again.
> **Intel91 said:**
> 7. Space conservation, no double application installations courtesy of my software + wubi.Ability to work with or without wubi is a must (in my opinion).
> **Intel91 said:**
> 8. Pre-installation of all widely used, and some not so widely used, codecs and interface software (flash, moonlight, avi, java, etc...)Time saver for lazy people like me again. BUT would be appreciated all the same.
> **Intel91 said:**
> 9. Everything else you're used to seeing on ubuntu, no features or applications are removed.
Again would be appreciated by lazy people like me. :D

Now I did say I was going to be honest & while I'm not personally interested in a new variant I think you're doing a cracking job & should carry on at full speed.

---

### Post by HappinessNow on 2010-07-22
Will it also have Google Chrome? Chromium?

as far a name you should just use a variation of the word Ubuntu scrambled:

unbutu

utnubu

bunutu

---

### Post by Excedio on 2010-07-22
> **earthpigg said:**
> this concept is pretty amazing.
 
i have a question: would there be any possibility of running native software and syncing the config files between windows and ubuntu?
 
ie: run native FF in ubuntu, bookmark something, and have that bookmark sync with Windows FF's bookmarks.
 
> **Intel91 said:**
> Ahh. You know, I didn't think about that, there's a lot of syncing of other "things". But, that would be extremely easy to implement, thanks for the suggestion.
 
> **Johnsie said:**
> To the guy who was talking about syncing firefox bookmarks, there are already firefox addons that can do that.
 
[Xmarks]("http://www.xmarks.com/").

---

### Post by neoargon on 2010-07-22
That's a really good idea to be able to use windoms application without duplication . What about using  native windows dlls ?That would make more applications working . Not all dlls should be replaced though. The list is in wine's site .
 
In my opinion, it is better not looking exactly like windows . An identity is a must . Many of my friends who switched to Ubuntu switched because it looks cool . They say that the integration of socializing apps and ayatana notifications are cool 

One might think : If it is exactly like windows and if it doesn't run many of my applications , why should I switch to it?

---

### Post by neoargon on 2010-07-22
Did you theme the look of windows applications? That would be cool

---

### Post by neoargon on 2010-07-22
Is your software, momentum, open source?is it available for downloading ?

---

### Post by Intel91 on 2010-07-22
> **neoargon said:**
> Is your software, momentum, open source? Is it available for downloading ?

Currently not open source. You could imagine why I wouldn't make it open source until the OS is actually released, or a bit after. 

As far as the windows-like interface goes, users will once again have the option. I changed my basic installer principle in giving people text options, I started replacing text with pictures that have explanations, so people can see gnome-standard with my windows-like gnome and visually decide on the spot.

This principle is possible without wubi, it just presents some installation issues that are easily circumvented with wubi. The first versions will be wubi only, but if people like it I will make a non-wubi version or the nixers. I don't see average windows converts gaining an advantage from a non-wubi install.

EDIT: 
I forgot to mention one nice aspect about this. If you are installing this variant, chances are you've got windows, otherwise you would just install ubuntu. That being said, if I assume your version of windows is legitimate, I can use your cd key (license) to give you all kinds of goodies that wine might not otherwise afford someone without a key. For example, certain key .dlls, runtime environments, wga software, etc... 
Some of these require a license for legal download and usage, and I believe it is still legal if used in linux. But that legal analysis is based on my entirely non-existent law degree from Yale.

---

### Post by neoargon on 2010-07-22
If one has  legitimate copy of windows, it wouldn't be illegal to copy windows dlls to wine folder or using without copying , .

---

### Post by neoargon on 2010-07-22
> **Intel91 said:**
> Currently not open source. You could imagine why I wouldn't make it open source until the OS is actually released, or a bit after. 

As far as the windows-like interface goes, users will once again have the option. I changed my basic installer principle in giving people text options, I started replacing text with pictures that have explanations, so people can see gnome-standard with my windows-like gnome and visually decide on the spot.
.
That would be cool

---

### Post by neoargon on 2010-07-22
What about the possibility of using dlls without copying ? Just like what your software does on exe's

---

### Post by pinguy on 2010-07-22
So when are you going to release it?? I would like to try it but very well doubt it will work that well. As I said Wine is great but it's no where near as good as it needs to be for this too work.

Why is *(momentum)* not going to be open source?? Have you got millions of £/$ to do this yourself? Because what you are trying to archive is no small feat and will need a lot of man hours and money to pull off.

As I said before what you seem like you are trying to pull off is a open-source Windows, where you can run all of your windows programs in a open-source OS, and [ReactOS]("http://www.reactos.org") have been trying to do this for years and they are still not there yet.

Release trubuntu *(or what ever you are going to call it)* as a nightly build and let us test it and give you feedback. At the moment you are promising a lot without showing us anything except a screenshot.

The way it sounds at the moment is all you are doing is copying the windows drive into wine and hoping it will work. 

Please prove me wrong because I really want this to work because hopefully it will get Photoshop to work under wine.

---

### Post by Intel91 on 2010-07-22
> **pinguy said:**
> So when are you going to release it?? I would like to try it but very well doubt it will work that well. As I said Wine is great but it's no where near as good as it needs to be for this too work.

Why is *(momentum)* not going to be open source?? Have you got millions of £/$ to do this yourself? Because what you are trying to archive is no small feat and will need a lot of man hours and money to pull off.

As I said before what you seem like you are trying to pull off is a open-source Windows, where you can run all of you windows programs in a open-source OS, and [ReactOS]("http://www.reactos.org") have been trying to do this for years and they are still not there yet.

Release trubuntu *(or what ever you are going to call it)* as a nightly build and let us test it and give you feedback. At the moment you are promising a lot without showing us anything except a sceenshot.

The way it sounds at the moment is all you are doing is copying the windows drive into wine and hoping it will work. 

Please prove me wrong because I really want this to work because hopefully it will get Photoshop to work under wine.

I know wine needs to be better, and I'm not attempting an "open source windows" like reactos. I am attempting a stopgap between the windows-linux transition. My wine doesn't work any better than yours, or anyone else's. The main concentration of the operating system is my momentum software, and I said it won't be open source at first. Eventually I will make momentum open source.

What I have announced isn't something I'm attempting to pull of, its what I have already pulled off. I have a working version, but when I say it isn't sufficiently polished, its the installation software that interacts with wubi + momentum +squashfs that isn't done, without that I've got software that requires a lot of user interaction, which isn't my goal. My goal is ease. Once I've got the installation worked out, I'll release it. I wanted to know if people liked it and get a bit of motivation to finish up, which is why I posted. I also knew I was going to get suggestions, which I would like to implement before release. This isn't a willy-nilly copy of the windows drive to wine, and as I have tried to point out in numerous posts, it isn't a copy of the drive in the least, as that would create double data.

My initial launch won't be perfect, thats not what I'm going for, I just want it to be something I'm proud of, so I'm not going to launch it before it is ready. One thing I would like to setup on a later version after I launch is a patched version of wine to be included. This would be setup on the premise of "top 25", in that I will set Transition OS (confirmed, thats what I'm calling it, already bough the domain, don't want to deal with trademarks and copyrights, etc...) to be able to out-of-the-box run the 25 most popular windows games and the 25 most popular windows apps. I feel this Top 25 will encompass most users, as I'm confident most game/app usage will lie in that top 25. That will eventually take care of vast concerns with wine.

---

### Post by RevengeOfTheToxicRodent on 2010-07-22
What's the point? It is just another lost fragment.

---

