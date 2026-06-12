---
title: "Will Ubuntu save my now unsupported android tablet?"
date: 2024-04-11
forum: The Cafe
---

### Post by hyperlinxe on 2024-04-11
Hi guys, I was wondering what the status is for ubuntu working with android tablets/phones, I have an old tablet, that I got several years ago, and it was a very nice system for a long time. But when I starting playing around with it again recently I discovered that android stops producing updates for older systems. It's an older tablet, but it's really strange that in the time I stopped using it, there are no updates whatsoever... maybe 6 years? So they basically stopped updating it, soon after they put it on the market because I got it brand new, used it for a couple years, had it updated, then have left it off for a long time after that, so I am totally unable to get any more updates for it from that time period.

It's really strange to me, firefox which has darkmode and support for security extensions is totally broken, even though the system hasn't changed since I last used it several years ago, google products all work fine, and I can't get any system updates now whatsoever. I've never even turned on the system since it was working perfectly years ago, and all of the sudden firefox is broken? And chrome is just fine? Anyways I searched around android forums, and other forums for answers, and discovered they simply stop supplying updates, so I am unable to fix my android tablet at this point, unless I can get a custom linux operating system for it.

( I even managed to update firefox, from the google play store, and it was still broken!)

I *could* technically fix it as well by installing a new android version with unsupported methods, but why the hell would anyone do something that stupid, when we have linux!

---

### Post by TheFu on 2024-04-12
Linux moves forward every day.  Devices that use non-standard hardware, which nearly all Android devices do, lose any desire for anyone to ensure they continue working. The GPU drivers are usually proprietary and nobody makes any others.  When those cannot link to the newest kernels, which happens quicker with proprietary driver "blobs" and when a new libc is created based on the newest kernels, things start to break.

If you remove the GUI, you'll find other, newer things, can work.  When I put xubuntu onto my 2010 tablet, the method used was to use the Android kernel at the time and run xubuntu inside a chroot and access it using VNC.  As you can imaging, in 2010, the tablets only had 1GB of RAM, so it was a tight fit to have RAM and CPU capable of running 
[LIST]
[*]Android
[*]chroot - xubuntu
[*]VNC-server
[*]VNC client
[/LIST]
In the end, I wasn't able to get the keyboard mapping correct and gave up.  My solution at the time was to get the cheapest chromebook I could ($200) and use that instead.  After a few months running LUbuntu inside a chroot under ChromeOS with a "guest" login, I wiped the system, broke the hardware protection to prevent loading other OSes and loaded Lubuntu into the Chromebook.  With only 16GB of SSD storage, it wasn't exactly tight, but it wasn't clear fields of empty storage either.  

I haven't touched that old tablet in years. It must be around somewhere.  I need to wipe the storage and see about getting some "recycle" credits from the local office products store.  It is recycling season here.  I've been saving all my old electronics in a few boxes for that specific use.  Same for old, dead, batteries.  Too bad old paint cans don't get any credits. ;)

---

### Post by hyperlinxe on 2024-04-12
Maybe I can fix it if I can use something besides google play store to manage my apps.... I ran that old tablet just like any other computer, but now certain apps I like such as firefox are totally broken! The support we get from android and the manufacturer is summed up in, buy something new, or update. I want to get the system I already have working basically. I'm not concerned about having the newest kernel or gpu driver. I just want to use basic apps like firefox instead of chrome...maybe download a video or a pdf file and use a pdf viewer or vlc. In other words I just want to restore it's basic functionality, which is now mysteriously broken.

---

### Post by him610 on 2024-04-12
@TheFu
> Too bad old paint cans don't get any credits. 
Loved that comment; it made me chuckle.

---

### Post by Irihapeti on 2024-04-12
There are other varieties of Linux that will run on old phones and tablets. You could try looking at postmarketOS and see if your tablet is one that it will run on. I have it running on an old Motorola phone from 2016, which originally used Android 6.

---

### Post by hyperlinxe on 2024-04-12
I thought Ubuntu was making a "mobile" OS? Isn't that what I'm talking about? Is ubuntu making an OS to replace android and google OS's on phones and tablets?

---

### Post by QIII on 2024-04-12
That project was abandoned years ago.

---

### Post by hyperlinxe on 2024-04-12
Alright guys thanks for the advice. I know there are a few projects out there in internet land that can fix it. I might try playing around with the old os, ..., i think it's android 7.1 or something, and see if I can get my mysteriously shouldn't be broken apps, not broken again. It's really strange that for an OS that undergoes literally no changes. 100% no changes whatsoever. All of the sudden apps start breaking. Ideally I'll find a linux OS to fix it? Maybe not? Same problems there?

---

### Post by QIII on 2024-04-12
Android is a 'nix.

---

### Post by hyperlinxe on 2024-04-12
google nix... not gnu nix right...

---

### Post by QIII on 2024-04-13
I have need to google neither 'nix nor GNU.

---

### Post by grahammechanical on 2024-04-13
I may be wrong about this but it is my understanding that the Android developers do not update devices with Android as the OS. The responsibility for upgrading a version of Android to a newer one rests on the manufacturer who made the device and install Android on it. Which does not happen or only happens rarely. It explains how it happens that devices are sold but are not supported in the sense that Linux users understand support.

The mobile OS that Ubuntu developers were working on was called Ubuntu Touch. When Ubuntu developers dropped the project a small group of developers took it upon themselves to continue the project and porting Ubuntu Touch to various devices. Success is varied.

[https://ubuntu-touch.io/en_GB/](https://ubuntu-touch.io/en_GB/)


[https://ubports.com/](https://ubports.com/)

[https://ubports.com/supported-products](https://ubports.com/supported-products)

[https://devices.ubuntu-touch.io/](https://devices.ubuntu-touch.io/)

Regards

---

### Post by hyperlinxe on 2024-04-13
Yes that is a good point, you are right, the manufacturer of my tablet is actually some weird company you've never heard of, but it's a verizon tablet, with android os. So it's a verizon tablet, with android 7.1 or something, and so I looked at verizons resources and androids resources to see if I could get any system updates when I discovered that my applications were suddenly broken, other than all of the google apps.

So consider that it's a device that cost several hundred dollars, received updates for I can't remember honestly, maybe 4 years, and with Verizon as the management of my operating system I am suddenly without recourse to fix it, other than to what's called jail break my tablet, and flash the rom with a new os, and could use android or some other system that's developed.

I just want to point out, that I am amazed personally, at how useful these devices actually are, just like smart phones, they do everything a computer can do, and between google play store and the internet I was watching movies, downloading movies, downloading books, reading books, browsing the internet, playing video games, and doing basically everything one could expect with that tablet, that we can do with computers...

What's really interesting isn't how with Verizon as my operating system manager, I stop receiving support, and am directed to buy entirely new systems, despite having brand new quality hardware still, but how for a system that 100% hasn't changed at all, is fully updated, the apps on it are suddenly broken, after simply so much time has passed.

---

### Post by phatton1 on 2024-04-13
@hyperlinxe

It may be worth looking at UserLAnd in the Google apps store, gets good reviews.

I'm going to try it on an old tablet (once it's charged &#128514;)

---

### Post by TheFu on 2024-04-13
> **hyperlinxe said:**
>  100% no changes whatsoever. All of the sudden apps start breaking. Ideally I'll find a linux OS to fix it? Maybe not? Same problems there?

Maybe the apps didn't change on your device, but the rest of the world did change.  Protocols used changed. Versions of java changed.  They aren't often backwards compatible indefinitely.

Will a program written for WinXP run on Windows11?  Nope. Most will not.  Android device official lifespans are measured in months.  If you do stuff 100% locally on the tablet, I bet all that would work with the factory shipped programs and OS.  When you need to touch the outside world, that's where changes impact you.  For example about 5 yrs ago, lots of CA Certs were updated to new, different, ciphers for security reasons.  Older devices weren't built with those newer ciphers in mind, so some devices stopped working and couldn't connect to web and email servers any more.  There was a long period where new and old ciphers were supported, but eventually the older ciphers were deprecated and a few years later, they were removed to protect everyone.

On low powered devices, often certain things are performed in hardware because the CPUs aren't strong enough to do the task without hardware ASIC support.  Most of the time, we see this in video playback.  Originally, all video codec decoding was done by the CPUs.  Then we got hardware decoding by the GPU for mpeg2 streams.  A few years later, mpeg2 and h.264/AVC/vp8 streams had hardware decoding.  The streaming world wants to ship us h.265/HEVC/vp9 streams now, but not all devices support decoding those video streams in hardware, so playback of them isn't possible.  

Where I live, our TV broadcasts are in mpeg2 still.  Our tuners support mpeg2, not h.264 and certainly not h.265 encodings.  A new standard has been pushed to allow h.265 and later video codecs to be supported, but the govt isn't mandating support, so only early adopters are bothering. These new tuners are 3x more expensive than the current mpeg2 tuners and many of the new channels broadcasting have DRM that doesn't work universally.  As long as the DRM doesn't "just work", and work without an internet connection mandated, nobody will switch.  When that switch does finally happen, perhaps in 10+ more years after multiple failures first, h.265 will be extremely out of date and our old tuners will become bricks with power supplies.

The world moves forward, not always at the pace we might like. Sometimes it is much too slow. Sometimes much too fast. Seldom is it just right for our individual desires.

---

### Post by hyperlinxe on 2024-04-13
No, I actually would like to understand the problem in depth. It's not simple browsing system files, like here with linux, where we have everything at our fingertips, but basically this is the situation as I understand it...

It's a Verizon tablet, with Android 7.1 OS.
Had it fully updated, until they stopped supplying updates.
Everything was working. 
Google play store, drivers, firefox, vlc, pdf viewers, everything I used it for.
Left it off, in it's original box even, never touched it, it was fully off,
and then turned it on one day to play around with it, remembering how much fun I had had with it,
and while thinking of all the fond memories of what was once a perfect system, I opened firefox
and found firefox couldn't get to webpages! I could change settings on firefox, but couldn't get to a
webpage, and every time I tried, firefox would completely freeze, and crash,  tried reverting it to default settings, 
same problem, tried using google chrome, (it's basically a google operating system) and google chrome
worked perfectly. Tried getting system updates, which ran in an infinite loop searching for updates , but
never accomplishing anything, looked on android forums, verizon forums, verizon customer support, searched
for a third-party android update tool, discovered it was for a different android system, and finally managed to update
firefox from the google play store, which didn't work earlier, and it had the exact same problem.

edit: I could do a factory reset, but then I don't even think I can update the system to it's newest possible state, I think the updates for that version are discontinued completely! So I really don't have good options...as far as I can tell to fix it.

---

### Post by phatton1 on 2024-04-13
So after trying UserLAnd on an ol' tablet and paying £1.99 for the privilege I can confirm it sucks. You get a desktop environment and open terminal, no apps installed and doesn't seem able to install any. 

I think someone has already suggested a factory reset, if that doesn't work then it looks like a new tablet &#128542;&#128542;

---

### Post by TheFu on 2024-04-13
Programs have versions.  Those versions have requirements - call them minimal environments.  The tablet you have doesn't meet the minimal requirements for the new versions of the programs.

I've had 3 tablets.  In 2010, an Acer 10inch tablet. It was high-end at the time.  I hadn't learned of a good use for tablets back then, so what I wanted were things that it didn't do well.  I used it to listen to music, read some websites and read some ebooks.  The screen resolution at the time wasn't great for any tablet and the battery life was less than 6 hrs. Also, not great.  Fortunately, work bought that tablet to help development of a special project for a client.  Everyone on the team had a slightly different tablet, so we could ensure compatibility of our work across a few different tablets.   I was writing the back-end video server which would feed tens of thousands of curated videos that our client was selling to movie studios.  They were switching to 4K resolution videos. At the time, no tablet could playback anywhere near 4K video. Heck, our tablets struggled with even 720p resolution videos.  My Acer tablet handled the highest resolution at the time - about 600p - without artifacts or stuttering.

I left that company, but they didn't want any personal use equipment back. I did return a few servers, since I was running the company infrastructure.

I remained friends with the others on the company board and we'd have lunch occasionally. One of them had an Amazon Fire 8 HD tablet.  He was addicted.  In 2017, I picked up the same tablet, just the 7th-generation. I came with android 4.x from Amazon.  As an Amazon device, it felt extremely limited to me for the first few days. Slowly, I removed all the Amazon-specific advertising and programs, then side-loaded some apps that would hook into my personal servers.  This made the tablet much more useful to me.  Example servers the tablet connected into were nextcloud, kodi, Plex, Firejail, wallabag, calibre, and all my internal network storage using sftp.  I loaded the openvpn client on it, so I had access to everything while traveling too.  I ran an openvpn server for about a decade, before switching to wireguard.  Around the fall of 2022, that fire8 tablet stopped working one day.  It just stopped. No boot. No factory reset. It was dead. The day before, it was working perfect like it had for years. The tablet was sitting on the nightstand - I read before going to sleep. It wasn't dropped or even out of the room between the day it worked and the day it didn't work again.  Over those 5 yrs of use, I became addicted to it.  Of course, it wasn't perfect but for $50, it was an impressive tool that I used daily.  Around 2019, I stopped taking a laptop when I traveled. The tablet was sufficient for my needs.

I lasted about 3 days before I ordered a replacement.  Found a less expensive, new, 8in Samsung tablet. It was around $120. Besides being newer - faster CPU, more RAM, newer Android version, I planned to use it nearly the same as the Fire8 Tablet.  There was 1 major difference which had always bothered me about the Fire8 tablet. The Samsung has a real GPS, so navigation tools work with it, unlike the Fire8.  Also, it has USBc for charging/power.  The Amazon tablet was the last actively used mini/micro-USB computing device I have.  I still have older devices with mini/micro-USB - my older cell phones, a rechargeable GPS receiver and a rechargeable screwdriver.  I keep the older phones working without SIMs by powering them on every 6 months and topping off the battery. They leak charge about 10% per month, it seems, even when powered down completely.

My desire for a GPS was the main driver to leave Amazon's Fire tablets, but getting a more current Android release was in my mind too.

The samsung tablet has never been connected to google, so there's no way to use the google app-store.  It connects to my servers and I use f-droid for applications.  This alternate "store" is something that normal end-users probably don't know.  Google likes to track us all.  Android does have google ties inside it, but I don't have to bridge the gap between the tablet and the real world.

Most people don't know this, but google created Android phones as a way to connect our fake, virtual, online personas to our real names and most importantly, our bank accounts.  That was their main goal. Before Android/iPhones, nobody used their real names online.

It isn't hard to find my real name, but I won't spoon feed it to Google and other tracking companies.

If it was me, I'd recycle the tablet, try to get some credit at an office-product store, perhaps $10 off per item recycled, and move on.  While there are very expensive tablets on the market today, there are also some excellent values for less than $130 from well-regarded companies, not just random companies from Shenzhen. There's a point when old hardware isn't useful anymore.  The more connected a device is to outside systems, the faster those devices will become less and less useful as the outside world keeps going.  GSM cell networks have all been turned off here.  2G networks at nearly all gone.  3G will be gone next year.  4G and 5G appear to be around, perhaps 5 more years, before they will be replaced too.  Progress keeps moving ... even when it isn't really progress.

We've gone far from the original purpose of this thread now. Sorry.  I'll go away. Sometimes I feel like a record saying the same things over and over and over, just to slightly different people.

---

### Post by hyperlinxe on 2024-04-13
Oh no, I'm going to hack it, in order to fix it. I love that tablet. I was playing morrowind on it with tablet touch screen controls, and downloading HD movies with torrenting software. I had that google tablet doing god mode level operations, like it was any other computer. Right now firefox is broken, but everything else as far as I can tell should be working. Updates are meaningless to the software/hardwares functionality, if I can fix them independently.

It just so happens, that I'm mad about the situation, because I understand firefox shouldn't be broken the way it is, crashing in an infinite loop opening websites. That is not a typical software bug, that is something along the lines of what many people call BS. Firefox is the browser that has dark mode, and the capability to add security extensions that actually protect my tablet unlike google, so the fact that it's broken and not google, is very frustrating to me.

I'm definitely going to fix it. They call it jail-breaking for a reason btw, it's not because of some great mystery, google, and google operating systems are extremely manipulative of their users. It's an open secret, except drowned in their advertising that consumes the entire internet.

---

### Post by him610 on 2024-04-13
I always wondered if there were some uncomplicated way to use the screen of a tablet as an auxiliary screen for one's phone. My somewhat dated tablet has a seven inch screen, probably four times what my phone has.

---

