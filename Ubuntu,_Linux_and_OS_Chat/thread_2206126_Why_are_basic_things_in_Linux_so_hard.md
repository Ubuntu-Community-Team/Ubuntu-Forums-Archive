---
title: "Why are basic things in Linux so hard?"
date: 2014-02-17
forum: Ubuntu, Linux and OS Chat
---

### Post by pixelblip on 2014-02-17
Hello there.
Nothing in life comes easy.......and neither does Linux. Ok here goes a mini rant!
Firstly I'm not a linux novice but no means an expert..... So far I've set Ubuntu up with an XP skin on a few pcs for people( sorry but it's the only way for people to feel comfortable with it coming from windows).....my experience is - if it looks a bit different they can't get use to it.

Anyway tonight I spent an hour trying to install a printer - a wireless printer for my friend........it's already set up and I wanted to connect to it on his Ubuntu pc.

I did it.........but so many things happen along the way.......if you are new to Linux it just throws you. I downloaded a driver from Samsung's site but when I clicked on the 'Autorun' it said I wasn't administrator. Huh?  I was an admin to my knowledge...anyway I thought why can't you just run a setup program easily like you do in windows? It's this sort of thing that really puts people off. Or why can't you right click over that setup file as 'Run as Administrator?'. 
 
Then I thought , I know I'll browse to it via terminal. Instinctively you want to right click over the file and 'Open Terminal here' - but you can't! So I tried to install that and got nowhere. Why isn't this included with Ubuntu automatically? You want to right click in an area and 'Open with Terminal'. Alright I know you might tell me how to do it but the fact it's not there in the first place is pretty bad.

Eventually I managed to do a sudo ./autorun ..........and it set up. 

But it made me think............how can we get people onto Linux when there's this much faffing around?

The PC he has got is now running fast and he's really impressed.........but he was totally out of his depth without my help.

Just food for thought here..........let's have some more 'Setup.exes' in Linux if you know what I mean! The Ubuntu software centre is really good........but for installing a Samsung printer it's not so handy!

Mike :D

---

### Post by deadflowr on 2014-02-17
Shouldn't this complaint be pointed toward Samsung?

---

### Post by pixelblip on 2014-02-17
I don't think it's just a Samsung thing.........I've come across  these issues myself in the past which is why I've taken the effort to write! Sorry if I sound like I'm complaining.........Ubuntu is really great.........but basic things are hard to do which shouldn't be......or is it just me?

---

### Post by deadflowr on 2014-02-17
> **pixelblip said:**
> I don't think it's just a Samsung thing.........I've come across  these issues myself in the past which is why I've taken the effort to write! Sorry if I sound like I'm complaining.........Ubuntu is really great.........but basic things are hard to do which shouldn't be......or is it just me?

You ranted about a problem that linux and Ubuntu have no control over.

---

### Post by pixelblip on 2014-02-17
I see...........so it's a Samsung issue then.......I apologise.

---

### Post by howefield on 2014-02-17
To be honest, this isn't really ranting about Samsung, but more about your own lack of knowledge.

---

### Post by pixelblip on 2014-02-17
I admit I have a lack of knowledge.........yes.........but isn't it about making software easier for everyone? My friend John wouldn't have had a clue how to install this. He can run a simple setup program in windows though.  I am not saying installing printers is always easy on windows by any means........why can't they ( whoever that is - Ubuntu - Samsung ) - make life a little easier for people less experienced? It is food for thought. I'll end my post now as it will just end in frustration.......like trying to get that printer working tonight. Sorry everyone!

---

### Post by monkeybrain20122 on 2014-02-17
Not really that hard. I am not a Linux expert but when confronted by a situation like that my first instinct would be to go to the terminal and run the installer with sudo (since it is for installing a hardware driver, if it is third party application then I would install it without sudo in /home and only make a symlink to /usr or /usr/local if needed)

---

### Post by Don_Stahl on 2014-02-17
Yes, I think the difficulty with "run as administrator" versus "sudo" is a conceptual difficulty, with some things -- like the Samsung driver mentioned -- being more problematic than others. 

Of course, system security is best served by requiring root (administrator) privileges for installing and removing software. We all know that, I think, including the OP. In Windows, when an install program is not run as admin, windows usually pops up a prompt window -- the one with the warning "You should only install software from publishers you trust" at the bottom. It's very convenient, since all you have to do is click the "Install" button and proceed. A child can do it, which is one reason trojans and other malware often show up on the PCs of people with children.

On the other hand, when I launch GParted in Ubuntu I get an authentication window, and I have to supply the root password. Very user-friendly, but somewhat more secure than the Windows method. But Samsung hasn't created a GUI authentication feature in their installation program. And *so far *Ubuntu hasn't implemented a universal authentication reminder. At least not to my knowledge. 

I think perhaps what the OP is wishing for is that whenever an installer of any kind was run (and the request was initiated without root privileges) that Ubuntu would launch an authentication window.

---

### Post by EnglishElectricAndy on 2014-02-17
As a newbie (less than 6 months use) to Linux I've found that 'basic things' are not hard, just different.

I certainly have got out of the habit of looking for "Setup.exe"s, indeed I've been pleasantly surprised at the number of peripheral devices (USB or wireless) that just seem to work with my Xubuntu 13.10 installation. Any issues that emerge now bring me to this forum or one of the other active and lively support resources.

Probably straying off topic and at risk of generating my own rant, I feel more empowered by Linux in my role as a consumer, to the extent that if a hardware/firmware manufacturer doesn't respect or support my choice of OS then they can wave goodbye to my custom. That Ralph Nader guy might have made some sense after all.

---

### Post by kurt18947 on 2014-02-17
> **EnglishElectricAndy said:**
> 
<snip>
Probably straying off topic and at risk of generating my own rant, I feel more empowered by Linux in my role as a consumer, to the extent that if a hardware/firmware manufacturer doesn't respect or support my choice of OS then they can wave goodbye to my custom. That Ralph Nader guy might have made some sense after all.

I feel in good company:D.  That is my position as well.

---

### Post by buzzingrobot on 2014-02-17
> **pixelblip said:**
> .

...when I clicked on the 'Autorun' it said I wasn't administrator. 

You weren't an adminstrator.  You were running as an ordinary user, as intended in Unix/Linux/OS X. The fact that Samsung was dumbheaded enough to deliver a driver install package that needed to run as root without bothering to tell the user is their mistake.  HP pushed a similar driver install package for a long time that would simply not work unless excuted as root.

If a similar package can run transparently on Windows, then it is a potential security threat.

> Instinctively you want to right click over the file and 'Open Terminal here'...

It's not instinctive. It's because you trained yourself that way.  Plenty of other ways to open a terminal.

> Eventually I managed to do a sudo ./autorun 

That's how it's done.  Linux is not Windows.  It's built to allow multiple users to work simultaneously on one machine.  That's why ordinary users can't muck about with making fundamental changes to the OS. That's why users get a home directory all to themselves.

> ...but he was totally out of his depth without my help.

Anyone with only Windows experience, with no other experience, will think everything works like Windows.

> Just food for thought here..........let's have some more 'Setup.exes' in Linux if you know what I mean! The Ubuntu software centre is really good........but for installing a Samsung printer it's not so handy!

Vendors like Samsung, and HP, Nvidia, AMD, etc., do not release the source for their drivers.  As such, they are at odds with the licenses that govern Linux development.  You will notice that Ubuntu and most other distributions do not include them in their installs. Some distros include some closed source in the repos, but let users deal with installing them.  Others wash their hands of it all.

The way to make this easier is to convince vendors to release open source products. Including, even, buying them.

---

### Post by lykwydchykyn on 2014-02-18
In modern Linux systems, hardware is automatically detected, installed, and configured for use without any intervention from the user --- ideally.  This can only be done when the hardware drivers are licensed in a way that's compatible with the rest of the system.  

Rather than asking why Ubuntu doesn't make it easier for you to run arbitray binaries as root (that should be obvious when you think about it that way), we should wonder why Samsung expects you to jump through hoops to make their printer (which you've bought and paid them for) work in Linux.  Why not contribute driver code to any of the existing print driver projects for CUPS, or provide sources that distros can package?  They put the burden on you the user to download the file and install it in a very non-standard (and very Windowsy) way.

---

### Post by Bucky Ball on 2014-02-18
It depends so much on what manufacturers are willing to do with and for the Linux community. Pays to do some research. My Brother printer takes about five minutes to install. Some other brands and models won't install. Ever. That is down to their creators, not the volunteers and devs in Linuxland.

I always encourage people to contact manufacturers about this stuff as, while I understand people's frustrations, pointing the bone at Ubuntu and the community is misguided. I always contact manufacturers about their hardware, and mostly it is about things 'just working' in Ubuntu, although on the devices packaging there are logos for Win and Mac, but no Linux logo! I've plugged in heaps of devices and they've worked with no mention from the manufacturers that they do or should with Linux.

---

### Post by mastablasta on 2014-02-18
> **pixelblip said:**
>  My friend John wouldn't have had a clue how to install this. 

ha, ha.. i know the type. they also know to run malware infected files. it's so simple you just double click them and you data is stolen or locked...

otherwsie i agree with others - Samsung fault. HP drivers are already built in because HP open sourced them and works with Linux community to make them. my printer wasn't even on and was recognised via USB and system told me it's all ready for printing.

side note: there is a PPA for samsung that fixes soem issues in their drivers. this illustrates their idiotic behaviour. they included a CD with linux drivers but they were nto working well. a linux enthusiast and programer created a pacth that makes them work perfeclty, contacted Samsung to tell them about the fix, yet Samsung chose to ignore them and instead continue to ship faulty drivers. so i use unofficial PPA for my newer Samsung printer. we are not impressed... :-k

---

### Post by hoffman2 on 2014-02-18
Yes Ubuntu never been easy for me as well. I always in situation where I should spend a lot of time for something that is so easy on Windows. 
Here are some of my experiences: 

1. After installing Ubuntu on my Lenovo e420 laptop, I have to figure out to install driver for my card reader. It took me almost 2 hours to browse around internet and trying to figure what to do until the car reader works. At first I have a bit proud of my self that I can do it. Because I am really new to this OS. 

2. Installing  brother all in one printer, it took almost two days ( yes two days no typo ). And still my wireless printer mode is not working. I need to use USB cable to print. 

3. Another couple of days to figure how to install and make the brother scanner works. 

4. I tried libre office and it works great even though everytime I send my work to co worker using windows office. And they all complained cause all the page setting is awful.... 

5, Now I am woking with my excel. The excel file that I got from microsoft excel is only 108kb. I use libre office  and save it to .xls or .xlsx booom the file is getting bigger to 4 MB. I tried freeoffice and it got worse the file that I am saving is now become 32MB....I don't even add any picture or any big size data on that file....only changing number....I tried to work it on microsoft office and no problem with the file...after edit the file and save it the size is still 108kb

6. I just bought a new HP all in one printer for my house. And again installing the driver on ubuntu is never a breeze. Need to browse around google to find out how to install it. It took me couple of days to make everything works....

  I don't know what will be next....it seems that I spend my productive time just to figure something that should only take couple of minutes on windows.... Well I am still keeping ubuntu on my laptop....hoping it will getting better and easied to use, hopefully soon..

---

### Post by mastablasta on 2014-02-18
> **hoffman2 said:**
> Yes Ubuntu never been easy for me as well. I always in situation where I should spend a lot of time for something that is so easy on Windows. 
Here are some of my experiences: 

1. After installing Ubuntu on my Lenovo e420 laptop, I have to figure out to install driver for my card reader. It took me almost 2 hours to browse around internet and trying to figure what to do until the car reader works. At first I have a bit proud of my self that I can do it. Because I am really new to this OS. 

this is not an issue if you bought laptop with linux preinstaleld or at least one that is certified to work with linux. 

> 
2. Installing brother all in one printer, it took almost two days ( yes two days no typo ). And still my wireless printer mode is not working. I need to use USB cable to print. 
3. Another couple of days to figure how to install and make the brother scanner works. 

I am not familiar with that brand. is the model certified to work with linux? do they provide linux drivers?

> 

4. I tried libre office and it works great even though everytime I send my work to co worker using windows office. And they all complained cause all the page setting is awful.... 

5, Now I am woking with my excel. The excel file that I got from microsoft excel is only 108kb. I use libre office and save it to .xls or .xlsx booom the file is getting bigger to 4 MB. I tried freeoffice and it got worse the file that I am saving is now become 32MB....I don't even add any picture or any big size data on that file....only changing number....I tried to work it on microsoft office and no problem with the file...after edit the file and save it the size is still 108kb

Separate issue. MS doesn't release it's document format eventhough they claim they do. if they did the libre office would have no issue exporting to that format. MS is still in legal battle over this issue. sicne they effectively ruined a company by doing that.

anyway who says you need to use libre office? there is kingsoft office, and a few others (mostly others are forks of open office) and there is also wine that can run MS office 2007 well. 

formating got better over the years and each verison improves it a bit. but then MS throws out another version of it's own format. sometimes i think it's just so people can't use substitutes. anyway a good solution is to use PDF for document exchanges. eventhough i use word and excel at work i would often print the files to PDF.

regarding size - i had an e-book over 300 pages with pics and all and size was smaller in libre office. PDF document was better created in libre office than in ms word.

did you know you can import and then edit PDF document into libre office (draw) ?

..
> 
6. I just bought a new HP all in one printer for my house. And again installing the driver on ubuntu is never a breeze. Need to browse around google to find out how to install it. It took me couple of days to make everything works....



assuming printer is certified for linux - you open software center and search for HP drivers & click install (hplip).: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)


no, the only thing difficult in linux is finding hardware that has good linux support & drivers from manufactures.:P

---

### Post by Bucky Ball on 2014-02-18
@hoffman2: Please post support threads in appropriate areas of the forum. There are a lot of knowledgable and experienced folk here happy to help with your issues.You have put your questions on a thread in a non-support area with a title that has nothing to do with your issues.

From your other posts on this forum it seems like you've solved plenty. If you're having issues, just ask. Make each thread specific rather than a whole bunch of unrelated questions. Good luck. ;)

---

### Post by hoffman2 on 2014-02-18
Guys I am just explaining how Ubuntu is never been an easy for me. Not looking for a solution here. I would ask on the appropriate forum if I would like to have a solution from other member.
Anyway, I still haven't given up on Ubuntu. I am still want to learn more about operating this Linux base OS.
I wish I could have left windows and moving all to Ubuntu but it's not gonna happen pretty soon for me.

---

### Post by varunendra on 2014-02-18
> **mastablasta said:**
> ..they also know to run malware infected files..

A BIG +1.

The fact that third party software that is not provided from the official repositories is a *little* difficult to install is what makes Linux a *little* more secure and not as easy to break as it is for Windows.

---

