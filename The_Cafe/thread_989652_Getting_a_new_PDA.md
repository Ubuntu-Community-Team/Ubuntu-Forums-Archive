---
title: "Getting a new PDA"
date: 2008-11-21
forum: The Cafe
---

### Post by RealG187 on 2008-11-21
I had my HP iPAQ h4100 series and loved it to death. It was the best MP3 player I ever had, probably cuz I used WinmpAQ and when I got tired of that, I used Pocket Music, and with the same device I could use different media players!

I hate iPods since you have to use iTunes and can't just put the files on the flash device (I like devices where I can use a file manager to put stuff om, that way I can put songs on from any OS, or even use my [NSLU2]("http://bestwikiever.wikidot.com/NSLU2")).

My Sony PSP is good because I can put songs on from any OS/Filemanager/App/Device, but it only plays songs one sub-directory deep and it's kinda big. The iPAQ was small and powerful. On my PSP I could go on the internet over Wifi and listen to music, but not at the same time, on my iPAQ I was surfing and jamming.

Sadly my iPAQ broke and I want a new one. I am considering a smartphone, but with wireless ISPs (not Wifi routers) you hear about people getting bills for thousands of dollars a month. There are tons of videos on Youtube of people with iPhone bills in the thousands, and I seen on TV someone with an "unlimited" plan for portable internet in the country was tagged and "excessive user" and had very high bills.

I want a new PDA. It has to be Windows Mobile, because my iPAQ ran Windows Mobile (Pocket PC) 2003. I want to be able to run all my old programs I got when I had my 4410.

Can I buy a smartphone and later on get a plan, or do I have to decide when I buy it?

Does the iPAQ read SDHC cards? I heard it doesn't...

What is a good PDA that can read SDHC (Maybe Micro SD Cards, or Mirco SD Cards in an SD Adaptor) that can run all the programs my iPAQ did. I need a touchscreen since the apps my iPAQ had one.

---

### Post by toupeiro on 2008-11-21
You might have to check into the windows mobile part, but the Nokia N810 is an absolutely awesome PDA and can take the Hi Density SD cards.  A co-worker of mine has one, and I think he said he was able to replace the OS on it, so as long as Windows Mobile (CE) or whever they are calling it these days can recognize the hardware you should be in business.

[http://www.nokiausa.com/link?cid=PLAIN_TEXT_970297](http://www.nokiausa.com/link?cid=PLAIN_TEXT_970297)

Thats the WiMAX version..  there is a non-WiMAX version as well.

Its OS is called OS2008, which is some sort of linux (pretty sure its debian) derivative.  Point being, you can probably emulate your applications, plus get things like Skype and lots of other stuff that a standard PDA can't get.

---

### Post by RealG187 on 2008-11-21
Is it easy to replace the OS? Will Nokia support it? Or do you have to "hack" it (like use an exploit that can be patched to not work, so only certain ones can be done).

What is the WiMAX version? Does it have Wifi too?

---

### Post by toupeiro on 2008-11-21
> **RealG187 said:**
> Is it easy to replace the OS? Will Nokia support it? Or do you have to "hack" it (like use an exploit that can be patched to not work, so only certain ones can be done).

What is the WiMAX version? Does it have Wifi too?

It does have Wifi, WiMAX is a new WAN broadband access they are putting in cities nowadays.  As far as Nokia supporting it, I'll ask my co-worker next week, and post back here.

---

### Post by Mr. Picklesworth on 2008-11-21
I hesitate to call the N810 a PDA. Don't get me wrong, I love the thing, but it's more a pocket computer, sharing all the same flaws and virtues of a good desktop PC (or, more accurately, a netbook).

The OS is quite detachable. That's one of my favourite things about the N810, actually, is that I don't feel like I'm locked in to any one platform. I think part of that is thanks to the open source nature. This device is perfect for tinkering. It's more like a normal computer in that sense, because Nokia hasn't really put any blocks between me and the hardware. (Although they do quite frequently remind me when I am doing something that could break the device. Its software setup is pretty fragile).

There is a bootloader available for it, and a project called Deblet is creating a fully functional Debian install that runs on the tablet. It works fairly well, although I personally am happy with a Debian chroot within the official Maemo environment for anything complex.
Most other Linux environments are done just within chroots attached to the Maemo environment. It's a perfectly fine Linux kernel already, so no reason not to. Another group has Android working like that, and there .
I am fairly confident that if / when Nokia drops the N810, someone will get a full Android install working. I believe some bits of hardware are using proprietary drivers, but that issue is getting smaller all the time.

It *is* worth noting that there are rumblings of a new tablet with super fancy new processor coming some time in the next while (probably), so if you are looking long term, it may be worth waiting a bit for everything to be clear.

To give you an idea of what it is best suited to... here's what I use my N810 for:[LIST]
[*]Reading stuff. PDFs are readable without conversion. Abiword and Gnumeric can open Excel and MS Word files with reasonable accuracy. (Same as in Ubuntu, naturally). Gnumeric is pretty cool on here.

[*]Watching videos. For the most part one must run them through a converter (the Linux version of which is literally 5 times faster for me than the Windows version, even with relatively weak hardware video decoding). However, from time to time I can just dump a video on and go in one step! It's Linux, and most stuff uses mplayer (the exception being Nokia's media player that comes with it) so every format worth supporting works.

[*]Audio is perfect, at least in my opinion. Pixel counters probably disagree, but using the Canola 2 media player it's amazing. (And the album art view is awesome). It does over the air podcast downloads, including video podcasts... and they "just work". No complaints about file size, either.

[*]Light web browsing. Web sites all tend to work, but they aren't exactly blazing fast. Flash works well, including YouTube.

[*]Tinkering with weird Linux stuff. For me, running a basic hardware simulator under Java in the Debian chroot.

[*]ScummVM. Specifically Curse of Monkey Island (that's #3), which I never got to play before. A great thing about these kinds of devices is they let you replay old games; I can never bring myself to it on modern computers because the screens are so huge. Either it hurts my eyes or I feel guilty about using all that technology (and such a huge screen) for something so simple and little. Now, if only Riven worked... I never played that game right either.

[*]My calendar. I mentioned earlier that this is not a great PDA. The reason is because Nokia themselves do not make any PDA-ish software. There are a few calendar / task management apps available, though. The one I use is Pimlico, which you'll also find in Ubuntu's repository as "dates", "tasks" and "contacts". Super simple, quick little app. Uses the Evolution data server to store its information (which, by the way, the tablet is running out of the box), so *in theory* it should be able to synchronize pretty well with a Linux desktop. It doesn't, though. The day when it will is getting closer, for example as Multisync gets closer to being good, if Pimlico Sync ever happens, or if Conduit on the tablet starts supporting Evolution Tasks. It works for me right now because I just do my calendar on my N810 alone instead of trying to sync with my big PC, however fun that would be.
Another possibility is a neat application known as GarmetVM. It, as the name states, is a virtual machine for the Garmin environment on Palm's PDAs. Indeed, you get a fully functional calendar, tasks and contacts system on there. Ubuntu supports wireless sync with that straight out of the box.
There are probably a million PIM apps for Android now.

[*]I mentioned contacts. I should clarify... it is more like a basic cell phone address book. I like it for my infatuation with the Telepathy framework and desktop integrated instant messaging. Each contact can be associated with an IM contact for any account you have set up. From the contact view, a click on his phone number will initate a call (with Skype or, I believe, a tethered cell phone), an email or an instant messaging session. No location stuff exists, regrettably.

[*]Email. The included email client happily downloads, via imap, from my gmail account. In my case I get tons of email traffic so I had to set up some extensive email filters so that only personal email stayed in my inbox. Otherwise, the poor device is nearly melted by all the traffic :o
Having a real keyboard helps a great deal. I use the email function routinely, which is unusual for a small device like this.

[*]GPS. Although getting better, the lock-on time isn't great and the available applications don't do a great job with it so I don't do a huge amount with the feature. For example, the included Wayfinder maps app won't do routing -- at all -- unless you fork over for an expensive subscription. (Why you need a subscription to calculate routes on the device is beyond me). Maemo Mapper is available, but doesn't do vector maps so also doesn't do routing. The built in map is fairly detailed for my area, so I can easily find destinations if I get lost... so it isn't entirely hopeless. In fact, it's kind of handy sometimes!
Maemo Mapper also has its moments; it can generate GPS traces, for example, and download a Google satellite map.
I just started playing with an app called ecoach, which is one of the first things for the N810 which uses the GPS for its task and *isn't* a map. Seems to work fairly well, and I look forward to more developers doing the same.

[*]Note taking! Maemopad+ is quite cool, and just recently Mono was ported to the tablet along with a proper repository for the things. Thus, I now have Tomboy running on there.

[*]Remote control. I can easily SSH from my tablet to my home computer. It feels nice because I didn't have to hack it to get there; it's all completely allowed.
[/LIST]

The development community for this thing is not great, largely because the development kit is a project in itself to set up and is unavailable to crazy 64-bit people like myself. That is a shame, but hopefully one day it will be sorted out.

As for the WiMax edition, yes it also does WiFi. The WiMax radio is added on, extra, to the back. (There is a slight bulge as a result).

To spare you any more mystery, here is a post I made on it when I got the thing:
[http://dylanmccall.blogspot.com/2008/04/got-my-n810-today.html](http://dylanmccall.blogspot.com/2008/04/got-my-n810-today.html)

---

### Post by RealG187 on 2008-11-21
Youtube works on it? On my PSP I can watch, but I don't use the browser, I run a program called PSP tube.

I used to use TCPMP (The Core Pocket Media Player) for Vidoes and it was cool how I could watch a video full screen and turn it sideways.

I had a few games on it like Sim City and Age of Empires, will the Nokia run those? Maybe I am better off sticking with HP? I contacted them and asked them what they reccomend.

As for wireless I don't know what to get, the 4100 used Wifi so I didn't have to worry about a bill/contracts or being taggged as an excessive user and getting a huge bill, but I only had internet access on it when I was at home (or by somewhere with an access point). Is there a device that has both Wifi and WAP?

> ScummVM. Specifically Curse of Monkey Island (that's #3), which I never got to play before. A great thing about these kinds of devices is they let you replay old games; I can never bring myself to it on modern computers because the screens are so huge. Either it hurts my eyes or I feel guilty about using all that technology (and such a huge screen) for something so simple and little. Now, if only Riven worked... I never played that game right either.
Are you saying you can run a VM on that thing? I never would have dreamed of running real Windows on a PDA/Portable Device (Windows 95 runs on PSP, but it takes 10 minutes to boot and it's impossible to use the mouse and keyboard). I too don't play games on a computer. only on portable devices.

---

### Post by Mr. Picklesworth on 2008-11-22
Oh no, the only VMs it runs are specific to particular things. ScummVM is strictly an implementation of the Scumm engine used for the awesome old LucasArts adventure games like Monkey Island, Sam & Max and Day of the Tentacle.

Having said that, there is Dosbox, and apparently someone got Windows 95 *booting* via that, but I doubt that it's a very satisfying experience based on how saddeningly slow Commander Keen 4 ran on there. (I think I did something wrong, though).

As a gaming device the 810 is a bit limited; there is no graphics acceleration and the processor is still a 400 mHz ARM, so it all has that slightly sluggish feel. AOE would be a no go. FreeCiv works, though :/
I think someone got the little MacOS emulators working, but again, don't expect too much.

The upcoming (still shady and secretive) device should be a lot more powerful as it has the newer omap 3 chip, hopefully with proper graphics acceleration and the like.

---

### Post by RealG187 on 2008-11-22
I know for a fact AOE and Sim City worked on my iPaq because they were the pocket versions (not vm)

---

### Post by Mr. Picklesworth on 2008-11-23
Oops, quick update on my own situation!
I just rediscovered GPE, the Maemo port of which has been nicely improved lately. I originally didn't give it much attention for some reason, but I was reminded that its name (G Palmtop Environment) is in fact a recursive acronym... which automatically makes it lovable free software!

Got it synchronizing with Evolution in Ubuntu somewhat painlessly using multisync0.90. I had to disable Contacts, but calendars, tasks and I think Memos (though there's no GUI for them) work.

So it now feels just like a proper PDA, except with more pixels.

Here is Garnet VM that I was mentioning, too:
[http://www.access-company.com/products/gvm/](http://www.access-company.com/products/gvm/)

---

