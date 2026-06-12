---
title: "Poll : Better Software and Hardware support"
date: 2007-02-08
forum: The Cafe
---

### Post by andytof47 on 2007-02-08
Hi I want to know what people think about Linux in general and the support that it receives from developers

I have noticed that most manufacturers Don't Support Us like they support other Operating systems and I continually need to go searching for things that waste time or don't work properly,  and don't have manufacturers drivers included.

E.G Canon CD Printer - No Drivers - Fix? Kind of Turboprint - However you have to pay for this....Pay to make my printer function the way that it is supposed to?..........No! thats not right, My money has already paid for their R&D on mac and windows - At the moment I will never use a mac, yet I have paid for them to include the driver support.

The point of the earlier example is to point out that these companies ought also to include Full functionality in their Linux Drivers 

So I would like to take a quick poll to see if this annoys others members of our Strong Linux Community....

Please give me insight and sites I May go to that advocate better support from these manufacturers

---

### Post by aysiu on 2007-02-08
This kind of discussion is probably better suited for the Cafe.

---

### Post by andytof47 on 2007-02-08
Cheers I wasn't sure where to put it, but if you want to move it you can - no probs:)

---

### Post by orthorim on 2007-02-08
The question is, why should they. I am going to post another thread on this - ubuntu is the first linux distro that I want to install, badly. 

However, it has a miniscule market share and hardware people often don't even provide proper drivers for Mac OS X - they have enough to cope with just to support Windows.

So I think the solution would be to make it very, very easy for HW manufacturers to support Linux - something like the NDIS wrappers for wireless cards except that it can't rely on an existing windows install but must work standalone.

I imagine it would work like this: 

A) Hardware vendor makes Windows driver, compiles .exe for Win
B) Ubuntu gives them a tool that allows them to create an executable for Linux in parallel. They don't have to do anything but run that tool on their existing code and release it.
C) Ubuntu, when running this binary, recognizes it as Windows driver and wraps it in binary that lets the driver think it's running on Windows and embeds it in Linux.

I bet that would work for most drivers out there. Of course driver vendors sometimes do something stupid thats unreasonable to support on Linux but I bet that for the most part it would not require much effort. 

Another alternative, though I am not sure of the legal ramifications would be that the driver vendor installs its own driver on its own Windows system, then uses an NDis wrapper like system to extract the drivers and provide them for download under Linux. As long as no Windows-proprietary DLLs need to be copied that should work fine as well.

The point is, NDISwrapper is the solution to Linux driver problems, you just have to find a way to make it independent of Windows installs - no one should have to install Windows to run Linux, obviously. 

Another options would be to establish a tried and trusted system whereby hardware vendors can provide developers with information they need to write drivers themselves. But in the end I imagine that would be even more work for the vendors than commissioning their own team to do it - they would spend less cash on developers but more on management and lawyers... maybe not so good. It's an illusion to think that HW vendors are happy to open source all their hardware secrets, that's not gonna happen.

---

### Post by cowlip on 2007-02-08
I say, HP and IBM.  I've had excellent luck with HP printers and my IBM Thinkpad.

---

### Post by aysiu on 2007-02-08
Another solution would be to support (i.e., buy products from) only manufacturers who support Linux (by either releasing Linux versions of their drivers or opening up their drivers so that Linux developers can incorporate those drivers into the kernel) and then write letters to the manufacturers who do **not** support Linux as well (or at all) and say something along the lines of: > I am interested in your products, but unfortunately you don't support Linux as well as your competitor _______, so I bought from them instead. I hope you will improve Linux compatibility in the future--I look forward to possibly being a future customer, should you do so.

---

### Post by cowlip on 2007-02-08
> **orthorim said:**
> 
Another options would be to establish a tried and trusted system whereby hardware vendors can provide developers with information they need to write drivers themselves. But in the end I imagine that would be even more work for the vendors than commissioning their own team to do it - they would spend less cash on developers but more on management and lawyers... maybe not so good. It's an illusion to think that HW vendors are happy to open source all their hardware secrets, that's not gonna happen.

True but there was just recently a framework put in place for that:   [http://www.kroah.com/log/2007/01/29/](http://www.kroah.com/log/2007/01/29/)

Also MS has started hating WINE with its "genuine advantage" stuff.  You apparently can't install WMP11 or IE7 because it doesn't pass validation if it finds a WINE registry key.

---

### Post by andytof47 on 2007-02-08
> The question is, why should they. I am going to post another thread on this - ubuntu is the first linux distro that I want to install, badly.

It may be the first distro you want to install badly, but there are plenty of others who already have a few distros up their sleeves already.

No considering that their is a huge potential for growth in the *nix market in general with friendlier *nix distros being developed nearly everyday, why wouldn't a company want to support their customers?

> However, it has a miniscule market share and hardware people often don't even provide proper drivers for Mac OS X - they have enough to cope with just to support Windows.


yes but those devices that do provide support get repeated business from mac users!

And take for example Cowlip 

> I say, HP and IBM. I've had excellent luck with HP printers and my IBM Thinkpad.

He/She would probably be willing to purchase IBM and HP again because of the ease of use, however if the driver support wasn't there like for example <enter the name ofsome unsupported piece of hardware here> you would look for an alternative next purchase!

I don't think the idea is to get us as the community to write wrappers and such just to get our  hardware up and running - as I said earlier, when I buy a Printer, I want the whole thing to work - yes! on Linux - otherwise I won't buy Canon next (I actually have this situation at the moment)

Remeber that for every $ you spend you are paying for "support" a couple of thousand spent in providing Native Linux support will pay for itself Long term


This is the point of this discussion - basically to gague the temperatureof peoples opinions and perhaps to do something about it.

---

### Post by andytof47 on 2007-02-08
Oh BTW


[HTML]Another solution would be to support (i.e., buy products from) only manufacturers who support Linux (by either releasing Linux versions of their drivers or opening up their drivers so that Linux developers can incorporate those drivers into the kernel) and then write letters to the manufacturers who do not support Linux as well (or at all) and say something along the lines of:[/HTML]

Ayisu - that is exactly what I am trying to do 

I am actually starting a site called linuxpetitions.org and bug these guys into supporting all of us in the *nix community

the site isn't up yet but I think we can get these big guys to see things our way - I hate having to run vmaware to run my N70 or print directly onto cd's

---

### Post by unbuntu on 2007-02-08
10. Others:  nVidia.

---

### Post by andytof47 on 2007-02-08
> unbuntu  	10. Others: nVidia.


Yeah! would you buy an Nvidia card again because it's easier to install?

I was an ATI fan on windows because of the macromedia built into the Nvidia driver, however I've had joy again with Nvidia on Ubuntu with twin view

The only problem is that I can't use twin view and Beryl--------some sort of glitch

but the point is I would buy an Nvidia card again under Linux:)

(I could only put 10 manufacturers sorry there were heaps more i wanted to put)

---

### Post by WalmartSniperLX on 2007-02-08
I would have to agree with HP being one of the best, but only because all my printers are HP and work fine. And as far as logitech, my pointer will randomly fly to all corners of the screen. Nvidia is also really good, hands down. Im hoping Ati will follow soon, and not repeat the mistake of letting nvidia take the complete lead in Linux/OpenS with their next cards.

EDIT: Does anyone know any new info about the AMD/Ati proposal for OpenS drivers?

---

### Post by steven8 on 2007-02-09
I thought about voting for Microsoft, since they'd made such greats strides partnering with Novell, one of the heaviest hitters in Linux.  Then I thought, naw!, and voted for HP instead.

:-)

---

### Post by Polygon on 2007-02-09
i voted hp, just because it seems that the HP printer protocol (jet direct or whatever) is open source or documented enough to work on the first try when setting up my printer in linux

---

### Post by Adamant1988 on 2007-02-09
I didn't vote, I've never had good luck with peripherals. 

On another note:  This information needs to be pooled together from the various distros in an easy to manage fashion so that there would be a one stop shop for finding out if a product is linux compatible or not.   I've seen linuxcompatible.org and the layout and design is horrible and confusing, and needs to be done better.  

I'm thinking user ratings and comments on hardware, and a "5 star" rating system to show how compatible each product is with different distributions.  You should be able to find your devices by Device type> brand> type> model number

For example  "Printer> HP> All-in-one> HP deskjet f335"
A pull down menu would work best here.

---

### Post by aysiu on 2007-02-09
I'm kind of sad that this thread died:
[ ubuntu / linux endorsed hardware](http://ubuntuforums.org/showthread.php?t=352137&highlight=hardware+compatibility)

---

### Post by towsonu2003 on 2007-02-09
none of the above... all go the whiny way of "oh sir / mam, we don't support your thingy, whatever it is called, we support wondovzzzz only! click [NO CARRIER]"

yep

cowon is good, but they don't manufacture computers :) just mp3 /audio / video players

---

### Post by SunnyRabbiera on 2007-02-09
I would say the best out of all of them is HP
But I have had great success with logitech as well
IBM is very good too.
I bought a HP computer just because they do support open software, and even though they dont officially support linux on thier desktop my warrenty is more for hardware then software and if I have problems I can just backup my data, wipe my drive and send it back to HP claiming MS killed my compy :D

---

### Post by andytof47 on 2007-02-09
Does it strike anyone as amazing that no obile phone manufacturers are actually willing to step up to the plate and support linux???

The Billions of $$$$$$$$ that are created in this industry should make phone manufacturers willing but there you again, another example of manufacturers trying to shut out the open source community and thereby maintaining their monopolistic strongholds (OOOOOO I like that word:popcorn: )


I can't wait till this comes out in Australia
[http://www.openmoko.com/pixels/FIC-neo1973.png](http://www.openmoko.com/pixels/FIC-neo1973.png)

Oh yeah - I'll be buying one - and i'm sure thousands of other linux users will too


I'm focusing on the phones because as you can see from the poll - NADA ZIP Zilch - none of the companies want to give us our bucks worth!!!!

Anyways, I just got an email back from Nokia and they have told me that my email has been forwarded onto the Asia Pacific product development manager - PM me if you want a read - It's not that interesting but when I get a reply fromt he right person I will be posting it on a my website make.

---

### Post by jclmusic on 2007-02-09
lol @ the person who chose microsoft - come on, that's gotta be a joke! :lolflag:

---

### Post by andytof47 on 2007-02-10
Yes It is amazing that 2 people would vote 4 microsoft, but in the end microsoft were forced to do what they probably didn't really want to do because of market pressure and the risk of alienating the Mac market completley.

Internet explorer for Mac

Media player for Mac

the same principle applies here 

We pressure the company's into playing fair, thats really what this is about. 

Not just from one distro, but we join together and utilize our skills, using the professionals amongst us.

I have created a domain that, although done before if done correctly will provide two important things

One voice for Linux users - however wether the voice is heard clearly depends on us, I mean how willing we are to unite and in many senses create a synergy from our combined talents that enables us to effectively communicate what we want.....

Read on (it's O.k. I'm not completley mad - maybe I am) but got [www.endorsedbylinux.org](www.endorsedbylinux.org)     - or if that doesn't work then just goto my home site on my internet providers

[http://www.adam.com.au/andytof47/linux/endorsed/](http://www.adam.com.au/andytof47/linux/endorsed/)


I am forwarding on that until I get the home server set up smoothly


anyway I am also doing a [www.linuxpetitions.org](www.linuxpetitions.org) ------should be fairly easy to setup, but it will provide us a place to rally our combined complaints and publicly air the responses we receive from company's such as canon, nokia, <add name of comapny here who isn't supporting us properly with driver development>, But I need code and profesional design


Hear that, Code please, and professional design. Don't worry about half hearted stuff, same as me, I'm actually a marketer by trade geek at heart who is sick of being fobbed off by bigger companys who don't really care but still take our money!!!!!

So who's in? who can contribute to this project especially linuxpetitions.org - should be a fairly straight forward from design - exactly like ipetitions.com and a database and some nice search tools? 


:)  waiting to hear from y'all:popcorn:

---

### Post by awakatanka on 2007-02-10
> **jclmusic said:**
> lol @ the person who chose microsoft - come on, that's gotta be a joke! :lolflag:I voted for microsoft because they bringing people to the linux side with there bad behavior.

How can you choose between this chooses when there much more and that are not on the list.

---

### Post by andytof47 on 2007-02-10
> How can you choose between this chooses when there much more and that are not on the list.

Yeah but we are focusing on multi-national billion daollar company's that ought to be doing much more....


Besides you could've not voted and just written who you wanted to vote for :)

You're only allowed 10 options anyways

---

### Post by Mathiasdm on 2007-02-10
> **andytof47 said:**
> Yes It is amazing that 2 people would vote 4 microsoft, but in the end microsoft were forced to do what they probably didn't really want to do because of market pressure and the risk of alienating the Mac market completley.


I voted for Microsoft, but purely as a joke ;)

---

### Post by andytof47 on 2007-02-10
> I voted for Microsoft, but purely as a joke 

I put thme up there for a joke aswell bwahahahhahaahahha:lolflag:

---

### Post by pmj on 2007-02-10
I have no idea which of these manufacturers have the best support, but on that list I only have products from Microsoft and Logitech, and only the Microsoft hardware (a keyboard) works perfectly without any messing around. Yes, it's just a keyboard, but can I do anything other than vote for Microsoft? :)

---

### Post by shining on 2007-02-10
> **towsonu2003 said:**
> none of the above... all go the whiny way of "oh sir / mam, we don't support your thingy, whatever it is called, we support wondovzzzz only! click [NO CARRIER]"


I've the same feeling.

---

### Post by Garyu on 2007-02-10
You've got a weird mix here... You should have narrowed the poll down to specific hardware. I.e. Canon mainly makes printers, scanners and cameras. Nokia only makes mobile phones. IBM... and Dell... makes mainly computers? Microsoft mostly provides keyboards, mice, joysticks... 

I would compare this poll to the one in the backyard: "Which is most important to keep in Feisty: Gnome, Gaim or IceWM" (or something similar). Reaks of sarcasm and irony and not very serious.

I have Microsoft keyboard and mouse. They use generic drivers and as such always works without any difficulties. In Hoary I had some problems with the multimedia buttons, but that has since been fixed.

I have a Logitech webcam. Took loads of work, but sometimes it actually works (at least to some extent).

I got a HP LaserJet printer and a HP scanner. The scanner has been really troublesome since it uses ppscsi, but the printer wasn't too difficult to set up.

I got a Nokia mobile phone with a 2 Mpix camera. It works out-of-the-box as a USB-storage unit, but without capabilities to synchronize the calendar and contacts.

So from the above, Microsoft has the best Linux support since I've never had any kind of problem with them, but this is only because they are really simple products that don't require drivers. None of these are connected in any way though. You would be better off to do a poll on "Which HP products work best, scanners, printers, cameras, etc" or "Which printer companies provides the best support, HP, Canon, Lexmark, etc"

---

### Post by hoagie on 2007-02-10
I voted for hp. My printer works fine and I never had a problem with it. On the other side logitech is the worst manufacture in terms of linux support. Their mice work fine with ubuntu, but it never goes further than that. I can't take advantage of the extra buttons ...

---

### Post by lyceum on 2007-02-10
I am surprised that HP go marked so high, when I called their support numbre, they did not know what Linux was. My laptop was made by them and it has a Broadcom WiFi chip in it, which does not work with Linux.

The easiest install I have even done was to an IBM think pad. IBM made it to the Ohio Linuxfest, the biggest name there I know of.

---

### Post by shining on 2007-02-10
> **lyceum said:**
> I am surprised that HP go marked so high, when I called their support numbre, they did not know what Linux was. My laptop was made by them and it has a Broadcom WiFi chip in it, which does not work with Linux.

The easiest install I have even done was to an IBM think pad. IBM made it to the Ohio Linuxfest, the biggest name there I know of.

Well, I don't think hp is the worst.
They have a linux section on their site :
[http://h71028.www7.hp.com/enterprise/cache/309906-0-0-0-121.html](http://h71028.www7.hp.com/enterprise/cache/309906-0-0-0-121.html)
And donated servers to [http://www.kernel.org/](http://www.kernel.org/)
I also have a perfectly working hp laser printer.

They just don't seem to know Linux is also just fine for a home / personal usage.
Though, the 2 hp laptops I have run perfectly with Linux (first has no wifi, second is the one I'm using right now, an intel centrino, with intel wireless)
Though, before buying the second one (nx7400), I searched a bit on the net, and found some had this crappy unsupported Broadcom. I was a bit scared, I called hp support, and it seemed like they didn't know any better, indeed.
It seemed there were more chances it had an intel chip though, so I took it. I was relieved when I saw it was the case :)

---

### Post by andytof47 on 2007-02-10
> You've got a weird mix here... 

Well, actually the diversity of the mix was deliberate.

1)TWhen you are trying to be productive these days, it takes a mix of all types of peripherals from a diverse range of manufacturers.

who made you printer?
Your mobile phone
Your mp3 player?
your Laptop?
Your Printer

If your answer contains three of the above then I am glad i put this mix together.

It captures the broadness of the base of the gadgets we use as a communty

> Reaks of sarcasm and irony and not very serious.  


2) easy misconception to draw, but this is a very serious poll
> It works out-of-the-box as a USB-storage unit, but without capabilities to synchronize the calendar and contacts.


POINT !!!!!!!!


I am sick of limping along with peripherals that only have have the functionality working out of the box or even with a driver disk that never or hardly ever has linux support built into it

So who else hates limping along with linux?

lots of us? well lets do something substantial together and get in the big boys faces with petitions ffrom lots of us on the same issues that have been affecting us for ages!!!


Please contribute             

[www.linuxpetitions.org](www.linuxpetitions.org)            (I need help with design, code functionality)

Personal message anyone who is interested

Cheers lets change thithaaang

---

### Post by %hMa@?b&lt;C on 2007-02-11
mock up of site diesign. Icons used were GPL'd that I found on KDE-look
[IMG]http://img178.imageshack.us/img178/5482/untitled1le3.jpg[/IMG]

---

### Post by andytof47 on 2007-02-11
I Like it:) 

> jeffc313  	mock up of site diesign. Icons used were GPL'd that I found on KDE-look


I'll PM you about the design

Sweet:popcorn:

---

### Post by andytof47 on 2007-02-12
O.k>

We have a concept and if you take the time to look at this site we are making progress.

[SIZE="6"]Who Can Contribute?[/SIZE]


Hey who can design a database with the type of fields that have been included on the website mockup?

Seriously - something that can have field and filters that limit by kerel version, distro, etc etc?


Are there any serious coders out there who can spare some time to further what will be a powerful tool for us as a community?


Please PM nah just pop it up here on the thread so we can keep the momentum

Serious coders anted to help - basically in th same way that linux wouldn't work without the input of it's community this wouldn't either - I appreciate the help that has already come to this site so far - keep it up and hopefull in the not to distant we will have a firm foundation to build a powerful database

[www.endorsedbylinux.org](www.endorsedbylinux.org)

It's up so have a squiz and if you can add anything feel free - actual code or sugestions:)

---

