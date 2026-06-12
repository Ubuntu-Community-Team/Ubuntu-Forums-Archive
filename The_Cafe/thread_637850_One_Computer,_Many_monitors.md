---
title: "One Computer, Many monitors"
date: 2007-12-11
forum: The Cafe
---

### Post by Black Mage on 2007-12-11
What is called to have many monitors and keyboard on computer to run different user sessions?

I'm not talking about a dual monitor. I'm saying like there is a server in my house, and my dads in one room with just a mouse and keyboard accessing his account on the server, and my mom is in another room, doing the same thing.

---

### Post by bonzodog on 2007-12-11
I believe the term you are looking for is 'Thin Client' or possibly, 'Terminal Server'.

---

### Post by Black Mage on 2007-12-11
Ahh, ok. Does this exist in Ubuntu or Linux yet?

---

### Post by rabi.fettig on 2007-12-11
I think [this]("http://www.ndiyo.org/systems") might be what you're looking for. I remember reading about it a while ago. I'm not sure how or where you can find these things, though.

---

### Post by Black Mage on 2007-12-11
Than you. This is a very interesting read.

---

### Post by Lostincyberspace on 2007-12-11
This originated in Unix and is pretty well supported in Linux I am pretty sure there are some distros specific for this.

---

### Post by Whiffle on 2007-12-11
Yes it can be done, and its been possible for a while:

[http://gentoo-wiki.com/HOWTO_Multiseat_X](http://gentoo-wiki.com/HOWTO_Multiseat_X)

I don't know of any ubuntu howtos on the subject, but its pretty much the same.

Edit: oh wait, not what you were asking, darn.

You could do thin clients, which would be a computer that boots off the network (booting off the server), and then runs an x session.   I personally think it'd just be easier to get multiple computers.

---

### Post by matthewcraig on 2007-12-11
This is just LTSP

---

### Post by Black Mage on 2007-12-11
> **Whiffle said:**
> Yes it can be done, and its been possible for a while:

[http://gentoo-wiki.com/HOWTO_Multiseat_X](http://gentoo-wiki.com/HOWTO_Multiseat_X)

I don't know of any ubuntu howtos on the subject, but its pretty much the same.

Edit: oh wait, not what you were asking, darn.

You could do thin clients, which would be a computer that boots off the network (booting off the server), and then runs an x session.   I personally think it'd just be easier to get multiple computers.

Easier yes, but cheaper? Thats the main goal, to save money.

---

### Post by rabi.fettig on 2007-12-11
I know [Koolu]("http://koolu.com/") makes a thin client that costs $200. Cheaper than that, you might want to look at [TigerDirect.com's recertified computers]("http://www.tigerdirect.com/applications/refurb/refurb_slc.asp?CatId=6&category=Desktop%20Computers"). They sometimes have systems for around $100 that you could get up and running as a thin client. My roommate recently got a few systems from his company's IT department that were headed for a landfill. They can't run much, but the beauty of a thin client architecture is that they don't have to.

---

### Post by koenn on 2007-12-11
There's rougly 3 ways of doing this :

1/ multi-seating; with multiple keyboards & monitors attached directly to the computer
eg like this : [http://www.multiseatcomputer.be/](http://www.multiseatcomputer.be/)  or what Whiffle posted
requires a computer with multiple video cards and lots of ports for keyboards and mice.


2/ remote sessions on 1 computer (think : multiple users having 'remote desktop' or vnc sessions on the same computer. 
requieres a network. 


3/ a thin client / terminal server solution. You can look at LTSP or Edubuntu, which is a somewhat specialized LTSP implementation. 
This also requires a network, and specific configuration.

---

### Post by hkgonra on 2007-12-11
If you plan to use old systems as thin-clients then you could probably get all you want out of people's trash.

---

### Post by mips on 2007-12-11
> **Black Mage said:**
>  I'm saying like there is a server in my house, and my dads in one room with just a mouse and keyboard accessing his account on the server, and my mom is in another room, doing the same thing.

As you describe it above it will NOT work. Cable length is a problem, especially with monitors, distance is limited. Unless there is some fancy box out there to extend the signal range.

Your best bet would be to go the thin client route as others have suggested here.

Instead of having a thin client box + monitor you could also get a thin client that has the thin client & connectors built into the monitor, like this:
[http://www.lucidatech.com/product/integrated.htm](http://www.lucidatech.com/product/integrated.htm)

---

### Post by Black Mage on 2007-12-11
With something like Ndiyo System, link is the 4th post, that different room think would be possible because its through ethernet. And long ethernet cables are relatively inexpensive and a ethernet connection should more than be able to support this type of video speed, with a good swtich or router.

So this brings possibly when not inhibited by a VGA cable.

---

### Post by Black Mage on 2007-12-12
On a 2.4 ghz quad core, 2 gig ram computer, does anyone have an idea of how many users that system could support?

---

### Post by koenn on 2007-12-12
> **Black Mage said:**
> On a 2.4 ghz quad core, 2 gig ram computer, does anyone have an idea of how many users that system could support?
Depends on what these users will be doing. 

These are Edubuntu's
Recommended specs

This mostly depends on the applications and usecases you decide upon.

Memory Because of the way shared memory works it will use less memory if everyone uses the same applications. Likewise some applications might eat more memory then others. In general you need around 256MB for the system and 128MB per user if they use office applications and a web browser. It's wise to have some extra memory capacity, since running out of memory could have major consequences. Extra memory will be used by the Linux kernel for caching, which speeds up overall performance.

Processors Processor speed depends highly upon the usecase. If you use CPU-hungry applications you might need a little more; Flash uses large amounts of CPU time, for example. Fortunately, the thinclients stay responsive even if a small group of users try to hog all of the CPU time (unless the load becomes extremely high).

Disks It's advisable to use some form of RAID in the terminal servers. Besides saving your data when a single disks fails, it improves the performance (especially read performance, which is the most important here). Since there will be considerable disk activity, the system might become slow if you don't use a RAID setup. 

[https://help.ubuntu.com/community/HowToCookEdubuntu/Chapters/HardwareRequirements](https://help.ubuntu.com/community/HowToCookEdubuntu/Chapters/HardwareRequirements)

---

### Post by Lostincyberspace on 2007-12-12
Safely 2 at the same time it would be able to run 4-5 with only lite use at the same time, and unlimited if they were all on at different times.

---

### Post by Black Mage on 2007-12-12
Only two?

If each user uses up around 128, a gig should be able support 8 users. But users are probably going to use more so lets say 5 users. And a quad-core only supporting 2 users? That sounds like under estimating the specs. Not to mention swap space could be used.

---

### Post by Lostincyberspace on 2007-12-12
> **Black Mage said:**
> Only two?

If each user uses up around 128, a gig should be able support 8 users. But users are probably going to use more so lets say 5 users. And a quad-core only supporting 2 users? That sounds like under estimating the specs. Not to mention swap space could be used.
Most users would only qualify as lite. Lite = music, web browsing (i was using firefox in my estimate), and a few other small apps. I guess I was a little conservative you should be able to run at about 400MB per user (for regular Ubuntu) with space so you should be able to have 5 perfectly fine (only if they don't do folding at home or things like that). If you used Xubuntu you could get much more, closer to 10-15

---

### Post by koenn on 2007-12-12
> **Black Mage said:**
> Only two?

If each user uses up around 128, a gig should be able support 8 users. But users are probably going to use more so lets say 5 users. And a quad-core only supporting 2 users? That sounds like under estimating the specs. Not to mention swap space could be used.
swap compensates for memory shortage, and uses up CPU (to process the swapping)

It's also quite relative : if 1 user manages to simultanously run a couple of memory hungry applications executing CPU-intensive operatians, you're going to support a lot less users than if they're all just running a  light web browser. 

given that, I'd guess 5-10 users would work. 

Have a look at the multiseat link I posted earlier - they're selling multi-user pc's. see how many concurrent users they support, and what the specs of those machines are. 
Or look at what Edubuntu says about number of users per server.

---

### Post by Lostincyberspace on 2007-12-12
Oh and its not the quad core that supports a few users its the memory.

---

### Post by aaaantoine on 2007-12-12
If you wanted to only allocate 128MB RAM to each user, you would have to choose your software carefully (ie, something other than Firefox, 32-bit instead of 64-bit OS, possibly ditch Gnome in favor of something more lightweight).

Then again, I don't know what the overhead is for having multiple users logged in vs a single user.

---

### Post by Black Mage on 2007-12-12
Alrite, so a 2.4 quad core, 2 gigabytes of ram, with raid could support around 5 users using intensive applications pretty.

Specs are looking good, and they should be similiar in Mac OS X.  Now how would these specs compare for Windows users?

---

### Post by Black Mage on 2007-12-13
Doing this for Vista would be really tight, wouldn't it. With Vista requirements, 2 gigs might only really give you two users....

---

### Post by koenn on 2007-12-13
I don't think you can do any of this with Windows, except if you set up (and get licenses per user for) Terminal Services ....

Unless you have a linux server and use Windows + X for windows or so ....

---

### Post by lespaul_rentals on 2007-12-13
You can use VNC.  It will open a seperate X session in the background for every user.  Obviously, it can get a bit slow, but it's pretty much remote desktop access.

---

### Post by andersja on 2008-05-13
See also the concept called "multi seat". There is much more information (and an opportunity to vote) here:

[[IMG]http://brainstorm.ubuntu.com/idea/3442/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/3442/)

---

