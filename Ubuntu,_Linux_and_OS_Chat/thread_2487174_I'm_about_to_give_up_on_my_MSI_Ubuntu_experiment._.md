---
title: "I'm about to give up on my MSI Ubuntu experiment. Too mnay issues."
date: 2023-05-26
forum: Ubuntu, Linux and OS Chat
---

### Post by dj1776 on 2023-05-26
_The machine:_
MSI Stealth 15M (Aussie model I believe)- 12th Gen Intel® Core™ i7-1280P × 20-- Fast and current machine with standalone GPU
Bought it for experiementing on CAD (I'm in the building industry looking to get into design)
Seems like a great machine- sleek, fast, etc, etc. many cores/threads etc.

For personal Ideological reasons I don't want an Apple or MS product (and certainly not Google) and I'm designing my life to be as free of big tech as possible (Lineage OS phone for example). Pay cash for 90% of stuff. Very, very reluctant to give out data- even my tenancy landlord doesn't have an email address for me- I make them put stamps on envelopes. 

_The main problems with the MSI_
It seems to be anti LINUX distros. Zorin ompletely failed to launch. Ubuntu boots after a timeconsuming rigmarole of going into safe mode and cleaning then resuming.

Cant' fix the brightness issue despite tryingevery single piece of advice i can find.
The battery lasts about 45mins with low intensity use.
it seems to be runing hot-using the active cooling system all the time.
No commercial CAD makers will support Linux (freeCAD is OK i suppose but mastering this won't get me a job with an architect or engineering firm.)

Anyone willing to offer words to persuade me NOT to sell my $2000 machine for a used market rate of likely $1000?
Even then what else can I get?

Do I swallow my Red Pill existance and go back to the evil round fruit? 
The idea makes me want to go Ted Kazinski and head for a cabin in the hills.

---

### Post by Frogs Hair on 2023-05-26
Moved to UL&OS Chat. Please start support threads for each problem separately if needed.

---

### Post by aljames2 on 2023-05-26
Well, most folks around here do have success running ubuntu on laptops, old & new(er).  Since this is not a support thread, how about starting a specific thread, maybe in “installations”, and start by providing some info on the Ubuntu flavor & version, and what OS was previously running on it, and what steps you took to prepare you SSD & bios to install Ubuntu.  Way too early to throw in the towel.

---

### Post by oldfred on 2023-05-26
I am running Kubuntu 22.04 on my MSI z690 desktop system.
You will not find commercial CADD software on Linux except perhaps some very high end system.
Also better to use a desktop with larger monitor as laptops are too small.

```

System:
  Kernel: 5.15.0-41-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: KDE Plasma 5.24.4 Distro: Ubuntu 22.04 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop Mobo: Micro-Star model: PRO Z690-A DDR4(MS-7D25) v: 1.0
    serial: <superuser required> UEFI: American Megatrends LLC. v: 1.70
    date: 06/23/2022
CPU:
  Info: 6-core model: 12th Gen Intel Core i5-12400 bits: 64 type: MT MCP
    arch: Alder Lake rev: 5 cache: L1: 480 KiB L2: 7.5 MiB L3: 18 MiB



```

---

### Post by TheFu on 2023-05-27
There's a point where the reality of life and making a living intersects with our ideals.

If you want to work in architecture, you'll need to be expert at the software used by the architects in the firm where you work.  I have some experience with CAD software. Every company picks the CAD stuff they will use depending on their industry.  AutoCAD is common for building designers. I know a company that doesn't use the 3D version of autoCAD.  For their needs, the cost was just too great. When I was consulting there (helping them move from 22 serves to 3 through virtualization), they were in the process of laying off 50% of their architects.  Mentor Graphics and ProE are common for aerospace. There are others.

I have an MSI system - a motherboard only, since I built the machine using parts.  It has been a workhorse for 13 yrs and is about ready for retirement. It is pre-USB3 and the bus bandwidth cannot support modern throughput needs.  Anyway, MSI didn't have any more issues than other systems.  When I come across a problem with Linux, I assume I'm missing something, not that the devs are idiots.  Almost always, the fault is mine. I don't know/understand how to accomplish what is desired and need to learn.  

Learning takes years.  After all, you didn't learn the OS you used previously in 1 day. It was many years to gain the knowledge.  Expecting Linux to be easier isn't realistic.  It is a completely different language .... like someone who speaks English trying to learn Mandarin.  Many things seem similar, but they really aren't.  That's a problem for all humans. We are pattern-matching biological machines.  When we see a pattern that looks like a pattern we believe we already understand, our brains assume the two different systems actually work the same, regardless of reality.

So, hold your nose and learn the tool used for your industry on the OS used by your industry.  There will be enough other tools, like a design library, and image catalog that are different and new that you'll need to learn at the job.

You can still use Linux outside of work and when online for enhanced privacy control.  Start with a pihole setup at home.  Block all the big-tech companies you like. Block trackers.  Don't allow javascript in your web browser without a conscious decision allowing it.  Wipe all cookies and HTML5 local objects daily.  Lie on all online forms.  Refuse to give data out to anyone, as your default stance.  If you use android, change the "advertising ID" daily.  Don't join social networks. If you do, don't connect to your friends or family, which provides so much extra data that is unbelievable. 
Learn to use new and different user accounts.  Linux is multi-user, so we don't have to use the same account for everything.  Some sandbox tools can make everything running under them appear to be a freshly installed instance without any access to the disk or many fingerprinting techniques. Learn to use those.  Block bad subnets around the internet.  Don't let inbound requests into your system.  Google and other big tech has techniques to trick your browser into making a request which allows their tracking tools direct access to your system, even if you didn't intend for that to happen.  This tricks your router/firewall, but if you also run a stateful firewall on the computer too, it definitely knows that you didn't ask for those packets and will block them.

I'm so fortunate that I work for myself and get to choose what software will be used.  Even then, sometimes, the client won't/cannot work with the tools I've selected, so I get to convert the data to whatever they require.  That's life.  Until there is a govt mandate that data forums be compatible, proprietary data formats will continue making it next to impossible NOT to run the same software - including version - as the "client" does.

Think about this.  MSFT has been selling new versions of MS-Office for decades with very few actual improvements to their proprietary file formats. When they switched to ZIPped XML, that was a huge step in the right direction, but even different OSes running the same MS-Office software had issues with compatibility.  If the company that has the source code can't make 100% compatible files between their MS-Windows and OSX versions, how can any other Office-clone software hope to do better?

Get ready to hold your nose, if you want to make a living.

---

### Post by ian-weisser on 2023-05-27
> **dj1776 said:**
> The idea makes me want to go Ted Kazinski and head for a cabin in the hills.

Many good people, and their families, suffered grievously from that person. Many others lived in fear for decades.

To treat their suffering so lightly is deeply offensive.

It's also an unnecessary distraction from your main point.

---

### Post by dj1776 on 2023-05-28
Point noted. It was a silly and thoughtless throwaway remark.
The cabin in the hills still appeals however.
The anti-industrial terrorism certainly doesnt.

---

### Post by dj1776 on 2023-05-28
How wonderfully generous to give at least ten minutes of your time writing this. Thank You.

Essentially I now understand that if I'm so upset by the obnoxious big tech (Apple/MSFT etc) then the only answer is to dive into a multi year (decade even) approach to mastering Linux based OS. I'm already a year or so in.

A plan beginning to gel is to revert the MSI Laptop back to Windows with which it runs extremely well and use this as a machine solely for my (again multi-year) CAD adventure and ringfence it from all other personal data sharing (if possible).

Step B is to get a Samsung Tab S5e tablet (a device they made so well its still beats its own products on almost every metric four years later) and to use this with the deGoogled Lineage OS which I'm already familiar with from my daily cell phone. The tablet can run my business and do the usual personal web surfing, self learning type behaviour we all engage in.

My journey in privacy and data hoarding is well advanced. Just today a store assitant enrolled me in their program over the counter when I went to make a purchase and I got a 50% discount. All the info given was bogus!!

My living is as a building contractor and I come from a family of architects and so my CAD journey is also well along. Circa 2005 at the University of Reading (UK) in the Computer lab we ran Pentium 4 machines and we were trying to design houses- you could have a cup of coffee in between renderings!

Thanks again for your appealingly philosophical comments.

---

### Post by QIII on 2023-05-28
How about this:

Start a new thread in the Installation & Upgrades section of the Forums and keep the discussion to installation issues without digression into commentary that is not directly to the point.  You have your reasons and opinions, they are yours to have, and they are really none of our business.  Except, that is, for the fact that you will find in the Linux ecosystem a paucity of the sort of professional tools you may be interested in using. -- which is a legitimate matter for others to be interested in pointing out.

If you have other issues, start separate threads for those.

There may very well be conditions that might make it difficult for you to install Linux on your particular hardware.  Unfortunately, that is not so terribly uncommon.  We don't control the OEMs.  How you choose to resolve that is your decision to make.  We aren't in the business of spending your money.

---

### Post by jayjayseal on 2023-05-29
I can run Linux fine on my MSI GF75 10SCXR-205. But CAD for Linux is another thing. As a work around you can run CAD on a Virtual Machine. As CAD relies on other Windows applications to run correctly. This is not really a Linux issue.. This is more a software programming issue for the dev's of CAD programs. You should not blame Ubuntu/Linux for this. You should blame the author :)

You might just been out of luck with your model/device. As said before everything works on my laptop. Including changing brightness of the LCD and the changing keyboard backlight. The only thing that does not work out of the box are a few of the the Fn keys as they seem to be mapped different on the keyboard itself. But i rarely use them. One of them being the disable the trackpad. But you can remap it to the P1 key which is a user programmable key and is next to the key it's replacing. So no big deal :)

Switching between the Intel GPU and the Nvidia chipset for (eg.) playing games etc.. is also working nicely.

---

### Post by agentl074 on 2023-05-30
I had an Asus M712 Vivobook with AMD Ryzen 5500U laptop -- but it came with Windows 10 and a custom string... it never liked Mint, but Ubuntu 22.04 worked. As for CAD, you'll want a good monitor -- or monitors -- and their may be some proprietary apps available for a price -- just have to add their repository (easiest on a DVD).  

This is a Linux compatible proprietary CAD program: 

[https://www.varicad.com/en/home/online-store/](https://www.varicad.com/en/home/online-store/)

---

### Post by kingshah001 on 2023-08-27
Same here i recently updated the version and having too many issues[[COLOR=#ffffff].[/COLOR]]("https://apkcroc.com")

---

