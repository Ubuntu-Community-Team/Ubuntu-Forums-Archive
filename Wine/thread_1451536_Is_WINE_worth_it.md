---
title: "Is WINE worth it?"
date: 2010-04-10
forum: Wine
---

### Post by Arryc on 2010-04-10
I'm a pretty new user for Linux, so excuse my lack of knowledge.

It seems that there are a good number of programs that won't run on Ubuntu, but we can use Wine (or VirtualBox or similar applications) to get them to work.  That's really cool, but how is it that different from just using Windows instead of Ubuntu?  It sort of seems like using Wine or a VirtualBox or whatever defeats the purpose of having Linux, or at least takes away the "feel" of Ubuntu.

Can someone explain to me why that is not true (assuming it's not)?

Also, give me some pros and cons of using Wine, VirtualBox, or anything else that you might recommend.

Thanks!

---

### Post by AlanR8 on 2010-04-10
Feel your confusion!

When I first started with Linux three and a half years ago, Wine seemed important to me if only to get Word working.

Not used Wine for three years now and apart from what comes down with the Google Picasa download, it's not actively installed!

I do install VB because one of my clients uses some complex Word templates that get confused in Open Office. Other than that, Doze free for a few years now!

---

### Post by SecretCode on 2010-04-10
Virtualbox is like having a whole extra computer (or several) in your computer. Virtual machines (ie what virtualbox runs) are separate operating system installations, so they can be different from your main host system - I have various versions of Ubuntu in vms, Linux Mint, etc, plus Windows XP. 

When you run a vm it takes up a certain amount of RAM to run the separate OS. And it doesn't share data with your host OS - unless you set up shared folders and 'guest additions' for clipboard sharing. So it's quite a lot of work. The main advantage is getting complete isolation from what's on your host OS.

Wine is much closer to your host. Wine apps run on the same disk drive as your host, share the display, mouse, printers etc. There are one or two applications I run in wine, and apart from the different formatting of the widgets and fonts you wouldn't know they were from a different OS.

So yes, Wine is worth it. 

As to "defeating the purpose of using Linux", that depends what your purpose is! If it's to save the cost of a windows licence, then it's a good thing - supports the purpose. Wine has no Microsoft code in it. The difference from using real Windows is ... the price!

If it's to have every application look the same, then yes it's not going to help - the look and feel will vary. 

My purpose is using Linux is to get flexibility and control over my computing tools.  Wine helps.

---

### Post by V for Vincent on 2010-04-11
What "purpose of linux"? I can run a wine program while my system remains stable and without having to install all my day-to-day apps in two environments. And there's no one-to-two-minute wait between two OSes. Of course it's worth it.

---

### Post by Funnnny on 2010-04-11
>  That's really cool, but how is it that different from just using Windows instead of Ubuntu?
Wine is a layer to run Windows App, most windows app doesn't have the ability to recompile and run on other OS, so we need a special layer for it.
Note that Wine is not an emulator, Virtualbox almost IS, with VirtualBox you have to install extra OS on top of it.
> It sort of seems like using Wine or a VirtualBox or whatever defeats the purpose of having Linux, or at least takes away the "feel" of Ubuntu.
Wine & Virtual Box is free, yes as in free speech, freedom is our "feel" of Linux, nothing in Windows can beat it.
If you don't understand or "feel" much about our freedom, just think using Ubuntu doesn't cost you any money ;)

---

### Post by trig on 2010-04-11
I make small cheap computers from parts i get for free, and give them away. I could not put a OS on a computer because of the price of windows, and osx is a bit of a resource hog. Not to mention i feel as dirty using this a windows compy box. Wine does allow you top play windows software and even the elusive Cs brand....

---

### Post by Arryc on 2010-04-12
Sorry I was unclear about the "purpose" of Linux.  Basically, I like the freedom to change, customize, etc.  What I really meant was that if you want to use Wine, why not just get Windows.

Initially, I assumed Wine was similar to VirtualBox, but my current understanding is although Wine allows you to install and run Windows applications, it does not change your OS or interface to be Windows-like.  Is that correct?

So apart from installing various programs, do you even notice that Wine is there?

---

### Post by ronnielsen1 on 2010-04-12
> Initially, I assumed Wine was similar to VirtualBox, but my current understanding is although Wine allows you to install and run Windows applications, it does not change your OS or interface to be Windows-like. Is that correct?

So apart from installing various programs, do you even notice that Wine is there?

No
No
No

You have it configured right, you don't know it's there. It won't run all the exe's but it will run some of them. It's alot better than it used to be.

---

### Post by howefield on 2010-04-12
> **Arryc said:**
> It sort of seems like using Wine or a VirtualBox or whatever defeats the purpose of having Linux, or at least takes away the "feel" of Ubuntu.

99 times out of a hundred there will be an excellent native Linux application that fits the bill, but for various reasons there will be the exception to that rule.

That's when Wine comes into it's own.

I don't see it as a way to run Windows programs per se., it is a way to get work done when there is no other way.

Most people have a specific reason for running applications in Wine, eg, specialisation, quality, and compatability, cost, comfort, ect, ect. The reasons are many and varied, but see it as a tool to extend your desktop if required, and if you don't need it, even better :)

---

### Post by Arryc on 2010-04-13
So, is there any downside whatsoever to using Wine?

---

### Post by Mark Phelps on 2010-04-13
> **Arryc said:**
> So, is there any downside whatsoever to using Wine?

Having used Wine -- and since weaned myself away from using it -- I would say the answer depends on WHY you're using Wine in the first place.

If you have a few MS Windows apps that you simply can't replace with Linux apps, and they work fine in Wine, then Wine serves a valuable purpose in letting you do some useful stuff.

But if (as one person claimed) you have over 100+ apps installed in Wine and do nearly everything using them -- then I would say the downside is that you're robbing yourself of the opportunity for learning and using the enormous variety of free Linux apps.  You're basically using Linux as a free, function-limited, version of MS Windows. So, in that case, you're not learning anything useful by using Ubuntu.

---

### Post by trig on 2010-04-13
I have a lap top that is dual boot win 7 and ubuntu 9.10. i use wind on the TV for my wife's comfort and netflicks. I use to play wow on it, but i havent had the desire to play my char.

---

### Post by howefield on 2010-04-14
> **Mark Phelps said:**
> But if (as one person claimed) you have over 100+ apps installed in Wine and do nearly everything using them...

Which person claimed this, I do not see it ?

---

### Post by CheAmr on 2010-04-14
for me ? 

not at all

---

### Post by Naegling23 on 2010-04-14
Ah wine...

Is it worth it.  Well, its free.  If it runs the program you want/need, then yes its worth it.

Whats the downside?  Well, its twofold.

1)  Wine runs windows programs, which means windows like behavior.  So, the programs, although they run right alongside others in linux, they feel like they dont belong...its sort of like running kde apps in gnome, but since windows file structure is different, there is more to it than just looks.

2)  This one is a philosophical one.  If you use wine to run an application, say World of Warcraft, then where is the incentive for that company or programer to release a linux version?  Many people dislike using wine because they feel there should be a native linux application that does what they want, or the game should be released natively on linux before they offer their support (ie money) to buy and use it.

So, like everything there is a large grey area.  Companies like blizzard actively work with wine to ensure that their games (world of warcraft) work well.  So, good for them.  But, because wine is ultimately responsible for the code, they have zero incentive to offer a linux version of world of warcraft.  So, wine lets you play the game, but also prevents a native version.  Everyone has an opinion on whether or not this is a good or a bad thing.

---

### Post by alex.rayu on 2010-04-16
Wine is free. It definitely worth it. Hopefully even more.

---

### Post by Zintha on 2010-04-16
Downside to having Wine?
Isn't that like asking whats the downside to installing something?

I guess it uses some space up, end of the day there are a few things that are just easier to use with Wine rather than mess about with compatibility issues. Those few things that just don't have an equivalent in Linux.

Its like asking whats the downside of having a NES Emulator, unless you're asking what the downside is compaired to buying a NES. With Wine and Windows there are differences, some stuff still doesn't work and what does (with games at least) there will be a step-down in graphics.

In World of Warcraft instead of 60 fps i'm hovering around 30 fps on the same graphics (Ultra all the way).

My suggestions, get Wine. Worst that'll happen is that you don't like it and have to weigh up using Windows or staying with Linux. In which case you can duel boot but thats a whole other issue.

---

### Post by Xeneth on 2010-04-17
I can imagine it opens you to a windows flaw here or there because it allows something to run that would not otherwise be able to. (spyware or the such)

---

### Post by cogadh on 2010-04-18
That would really only matter if you made the mistake of running Wine with root or sudo permissions, which is not how it is designed to be used anyway. As long as Wine is only run with normal user permissions (and it is configured properly), the only thing malware can do is possibly damage the .wine directory, which is very easily remedied.

---

### Post by hikaricore on 2010-04-18
You can also run questionable software in "bottles" using WINEPREFIX and even safeguard your .wine directory. ;)

---

