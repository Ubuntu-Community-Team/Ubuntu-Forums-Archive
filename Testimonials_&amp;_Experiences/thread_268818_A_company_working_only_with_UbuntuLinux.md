---
title: "A company working only with Ubuntu/Linux?"
date: 2006-09-30
forum: Testimonials &amp; Experiences
---

### Post by dnccnd on 2006-09-30
I am thinking of starting a business, something inbetween a normal business and a non-profit organisation. The idea is to place the business somewhere in Africa and contribute to some development programmes.

Because of the concept and the limited budget, I was thinking of using Ubuntu/Linux on all computers and servers and totally avoid using Windows. I am not too much into networking and Unix, but the main question is:

Would it be possible to create an IT-system for a small/medium company that only works with Ubuntu/Linux? What could the challanges be?

I guess the system should allow about 50 computers to work together through a network.

Do you have any experience with this kind of projects?

Thank you for any suggestions.

---

### Post by cunawarit on 2006-10-01
I am new to Linux too, so I can't tell you about any technical issues. But of course you can do anything you want to, Ubuntu is a fully featured OS and you could run a whole business using solely Ubuntu.

However, ruling out all use of Windows/MacOS and other commercial software entirely go might not be wise, it could possibly be the best/cheapest solution. Software price is only one thing to consider. Also as a non-profit/charitable organization you could get the software donated so you might not even have to pay for it. 

Where I work they have a "Microsoft where possible" policy. They uphold this  very tightly. Yet, they haven't been able to avoid having a few Macs, one Linux machine (possibly two soon), and several Unix servers.

---

### Post by geekchic9 on 2006-10-01
Just wanted to let you all know that I'm interested in this post as well, as my organization is a non-profit, although it's US-only for now.

---

### Post by DoctorMO on 2006-10-01
I'm on the other side of cunawarit, I avoide Windows and Mac like the plauges. because they're just not future proof enough.

Getting a business started with Linux is the cheepest solution. because ultimatly all the studies I've seen where Linux comes out even close to the cost of windows or Apple apear to factor in large retraining and retooling costs. I don't think this would be a factor with a linux company.

All the tools are there, the server versions contain all the services needed for enterprise business; the most important part of setting it all up though is having someone who is good at it or who is willing to put the time in to becoming good at it.

---

### Post by izalac on 2006-10-01
First of all, it depends whether Linux suits your needs as a user. If you have a need of some piece of software that is not available on Linux, then use Windows or whatever else you need. You might get a more definite and precise answer if you answer what do you intend to use your computers for.

First and foremost, in business world, computer is a tool to get your job done. If your business needs are covered by accessing Internet, surfing web, reading mail, sharing some files in network, using office suite, and eventually using some kind of intranet web server, then yes, Linux can suit your needs, and Ubuntu will even do it with the default install. Only problems you might encounter can come if you need to set up a wireless network, however, this can be solved by careful hardware selection.

If you really need MS Office capabilities, such as working with some extremely complex third-party Excel spreadsheet or Access database with tons of embedded Visual Basic code then CrossOver Office might be a cheaper solution than getting a full MS Office suite.

Getting a full Ubuntu network up and running is a fairly easy process, and it works very well. Linux, and generally pretty much every *nix system is basically built for networking purposes. Most complex part about its networking is getting it to work on Windows network if you want comfortable file and printer sharing services between two platforms.

The hardest part about company deciding to use Linux is switching the old Windows data to new Linux data, and teaching people to do their jobs in another, perhaps only slightly different way. Starting out immidiately with Linux is remarkably easier and cheaper, and Ubuntu is so far quite stable and safe.

About the challenge, if you're not too deep in Unix systems... find someone who is, or learn enough yourself to be able to solve situation if some difficulty happens to arise. No system is fully flawless and stupid-user-proof, and you will need someone to maintain the Linux network, and Linux techies are in much shorter supply than Windows techies.

---

### Post by geekchic9 on 2006-10-02
izalac,

Do you have or know any resources for people to educate themselves on Linux networking?

---

### Post by DoctorMO on 2006-10-02
[http://tldp.org/HOWTO/NET3-4-HOWTO.html](http://tldp.org/HOWTO/NET3-4-HOWTO.html)

the tutorials are all over the place and O'Reilly has some great books.

---

### Post by izalac on 2006-10-02
Nice one, DoctorMO :)
I've also noticed a lot of Linux training courses over the past few years, though I have no clue how deep they are. Some offer Red Hat certifications, and they tend to be more expensive.

Can't say much about books as I don't have much experience with them. However, I got a copy of "Red Hat Linux 7 Server" by Mohammed J. Kabir, by IDG books which I found a very valuable networking source several years ago, even though it's completely outdated now. Some config files remained pretty much the same.

Most Linux users however, as far as I noticed, are mostly self-taught. Reading guides on Net and trial-and-error have always been the primary methods of people who decided to teach themselves of inner workings of Linux and accompanying software.

I cannot guarantee about any books. I never read any O'Reilly books about Linux, but other books from them that I read generally proved to be very well written and quite nice to read.
There's also The Official Ubuntu Book from Prentice Hall, advertised on [www.ubuntu.com](www.ubuntu.com) that, according to description, covers mostly desktop, but Ubuntu server as well.

I never read any of these books, and henceforth I cannot personally guarantee you'll find required knowledge in them, and you might also have to employ google tactics and asking questions on forums to be able to find exactly what you need, if books prove inadequate. However, to me, they seem like a good start and quality materials.

---

### Post by izalac on 2006-10-02
Oh, and of course... There's a ton of Ubuntu-specialized knowledge already summarized and easily available on [https://help.ubuntu.com/](https://help.ubuntu.com/)

For configuring your network, just look in Server Guide, Networking section. It might be enough for your needs on networking education :)

---

### Post by maniacmusician on 2006-10-02
If you really want to use a business starting ubuntu, you should consider using [Impi Linux]("http://www.impilinux.co.za/"). It uses a lot of ubuntu code (mark shuttleworth invests in it), has access to all the repositories for ubuntu, and it offers varying levels of commercial support along with their product. It's worth checking out. Not totally free, but the price is probably reasonable for the polish and support that you get.

---

### Post by cunawarit on 2006-10-03
> **DoctorMO said:**
> I'm on the other side of cunawarit, I avoide Windows and Mac like the plauges. because they're just not future proof enough.

What do you mean they are not future proof? I don't see the OS that is running on 90% of the world's desktops going away any time soon.  Similarly, I don't see the OS used by most graphics designers around the world suddenly dissapearing.

---

### Post by tribaal on 2006-10-03
If you plan to build a network in Africa, you'll need to consider the bandwidth problem they have. Most countries there have a national bandwidth more narrow than a DSL...

So you'll want to host as much as possible on your LAN (email etc...), and you'll have to work with apt-mirror and web caches (like squid) a lot. Hopefully, for this particular use, you can pretty much go with the default settings with tweaking the configs too much.

If you consider handing out Ubuntu CDs locally (in Africa), remaster a Desktop CD and a Xubuntu so that the sources.list point to your mirror instead of the international ones (bandwith saving again: intra country is more or less available, but International bandwidth is really slllooooow).

Oh, and make sure you get a good auxiliary power generator for your "server room"... You get brownouts and blackouts fairly often, even in major cities.

And don't forget to plug air conditionning to the generator, too ;)

Hope this gives you a few pointers :)

- trib'

---

### Post by izalac on 2006-10-03
> **cunawarit said:**
> What do you mean they are not future proof? I don't see the OS that is running on 90% of the world's desktops going away any time soon.

I do. It will have to be upgraded to Vista soon if you "wish to remain productive".

---

### Post by DoctorMO on 2006-10-03
> What do you mean they are not future proof? I don't see the OS that is running on 90% of the world's desktops going away any time soon. Similarly, I don't see the OS used by most graphics designers around the world suddenly dissapearing.

Disapearing, not being available to you and having a system wich becomes unusable over time is not something which looks to the future. this is reflected in the very way the two bits of software mentioned are built. Mac performs better but it's still looking at short term returns rather than long term technogical achievment.

Not future proof QED.

Anyway this is a side issue, lets keep thi on topic.

---

### Post by dca on 2006-10-04
This is actually an interesting thread.  I'd like to see more (as far as users trying to implement Linux or Ubuntu Server in an enterprise environment) posts like these.  Outside of my work as a consultant, I'm trying to help a friend re-open an old old hotel.  In my spare time, basically, still a long way to go.  The original idea was to go all open source to eliminate paying license/maintenance fees for OS(s) and PMS(s)...  I built an old server from spare parts and he has an old server that will be the basis.  One for the PMS, the other for everything else and take it from there.  I hope this post won't end up in 'The Backyard' but I think the clients (a bunch of old PIII systems w/ 256MB RAM) will run a hybrid SimplyMEPIS version.  We're toying around w/ the idea of having two workstations in the lobby for internet use.  The original problem was which browser would be most comfortable to an average Windows/IE user?  Oh, then there's the POS system for gift shops, snack bars, etc.  The PMS for room & reservations, the definite possability it won't offer any kind of high-speed (WiFi or wired) from the room.  Sorry to talk your eyes off, but I too, am interested in posts like these...

---

### Post by izalac on 2006-10-05
I'd go with Firefox, dca :) I had most positive experiences converting IE users to Firefox.

---

### Post by dca on 2006-10-05
> **izalac said:**
> I'd go with Firefox, dca :) I had most positive experiences converting IE users to Firefox.
 
Thanks for the input, I'm going to have to agree with you on that one...

---

### Post by dnccnd on 2006-10-06
Thanks to everyone for the very interesting inputs.

I am not too familiar with many of the technical information you provided, therefore I was wondering whether there are consultants specialised in implementing this kind of projects, and where they can be found.

As far as the challanges of working in Africa, I am aware of them. At least I guess Ubuntu/Linux can help these countries in developing their IT capabilities, more than the 100$ PCs developed and promoted by the UN! They are probably too basic, while Linux offers so much more!

---

### Post by DoctorMO on 2006-10-06
I think you can hire technical resources for linux/ubuntu to set up networks and do training etc.

I'm in London though which is quite easy to find the skills you need.

---

