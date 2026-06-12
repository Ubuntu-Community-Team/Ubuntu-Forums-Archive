---
title: "For new users..."
date: 2009-10-20
forum: Testimonials &amp; Experiences
---

### Post by Ub28 on 2009-10-20
[FONT="Arial"][SIZE="3"][COLOR="Blue"]Hi

I'm so far very pleased with Ubuntu and I'm using it more often than Vista (I have 2 hard disks, one with Vista and the other with Ubuntu).

I'm glad all my hardware works and there was no faff or tricky steps to get the devices up and running.

Bearing in mind I'm new to the Linux world and I've been using Windows for years (and I expect most home users reading this are in the same situation). I would like to suggest the following four features are made available "out of the box" for Ubuntu users, including those who bought Ubuntu pre-installed:

1. Firewall software that fully passes the Shields Up test on "Common Ports" ([https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")) - users of Windows XP SP2 and later versions already have a software firewall that passes the "Common Ports" test.  I don't connect through a router with a firewall, so the Shields Up test fails on me. :(

2. Choice of web browsers and an option to get Internet Explorer running.  For reasons unknown to me, some websites will **only** work in Internet Explorer.  After lots of searching the Internet, I discovered IEs4Linux and after lots of confusion, I followed some technical steps on their website and finally got Internet Explorer 6 working.  

3. A friend who has a Ubuntu netbook was unable to format USB pendrives, memory cards etc. until they got some 3rd party tool. As we're used to the Windows method of right-clicking a removable device and selecting the "Format" option (along with a warning about losing files!), I hope the same feature can be included with Ubuntu.

4. Sun Java and a flash player installed. Yes I know it means accepting a licence agreement, but who reads them?  Most users will accept the agreement so the software can just work.  I could not get flash player working as soon as I opened youtube, but eventually found flash player using the tools for installing programs in Ubuntu.

_
I know plenty of people who get frustrated with computers and get confused over the simplest things in Windows. If Ubuntu has most or all of the expected things available from day one, I can see a lot of happy Ubuntu users forever.

The only thing I did not mention is an option to choose an anti-virus program. I've just read that few viruses exist for Linux at the moment, but if this changes, then obviously an anti-virus program will be required in future.

Thanks for reading.  Does anyone else have a wish-list for NEW users of Ubuntu/Linux?[/COLOR][/SIZE][/FONT]

---

### Post by P4man on 2009-10-20
> 1. Firewall software that fully passes the Shields Up 

You dont need a firewall. Unlike with windows, ubuntu has no programs listening to any incoming ports by default, so blocking ports where nothing is listening anyway is pointless and makes things harder for the user for no reason. You only need a firewall if you have want to differentiate services between local network and internet (say allow an ftp server to be accessed from your home network, but not the internet). 

What that test reports is pretty irrelevant.
> 
2. Choice of web browsers and an option to get Internet Explorer running. 

You do have a choice. Go to add/remove programs and install any of a dozen browsers. But shipping just one on the cd helps keep the cd below 650 Mb :)

As for IE.. about the last thing I would want is IE included in ubuntu. Not just because I dont like or need it, but because of security vulnerabilities ported over to ubuntu then, and the fact it works rather poorly anyway. ies4linux is a good solution if you cant live without IE for a given site, but that should be the exceptionm not the rule. Contact the webmaster if his website doesnt comply with internet standards.. Besides, im pretty sure there are legal barriers to including IE,

> 3. A friend who has a Ubuntu netbook was unable to format USB pendrives, memory cards etc. until they got some 3rd party tool. As we're used to the Windows method of right-clicking a removable device and selecting the "Format" option (along with a warning about losing files!), I hope the same feature can be included with Ubuntu.

Formatting a USB stick is easy enough. Just use gparted. However some USB sticks have funny firmware that makes them behave like cdroms and they include u3 software ( google on it) You need a vendor tool to remove the software and reflash the firmware so it works like a normal usb stick that you bought it for. There is nothing ubuntu can do about that, complain at the vendor of the stick, ask u3 to make a linux tool (they do have an OS-X tool) or vote with your wallet and buy one that works as advertised and not one that works as an advertisement.
[http://en.wikipedia.org/wiki/U3](http://en.wikipedia.org/wiki/U3)

> 4. Sun Java and a flash player installed. Yes I know it means accepting a licence agreement,

I agree. But I think its legal issues here, Im not sure. However there are plenty of distributions that include those. have a look at Linux mint, its based on ubuntu and has flash and java as well as other restricted codecs out of the box. Its legality in some countries could be questionable though.

> Thanks for reading.  Does anyone else have a wish-list for NEW users of Ubuntu/Linux?

Oh yeah plenty. Id have them agree to an EULA where they have to state they understand ubuntu is not windows and doesnt want to become windows :p

---

### Post by mick222 on 2009-10-20
> 1. Firewall software that fully passes the Shields Up test on "Common Ports" ([https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)) - users of Windows XP SP2 and later versions already have a software firewall that passes the "Common Ports" test. I don't connect through a router with a firewall, so the Shields Up test fails on me. 
 Ubuntu firewall is installed but the gui it not should be in synaptic under gufw
2 internet explorer is proprietary windows software and also not as secure as firefox or Ubuntu

---

### Post by mick222 on 2009-10-20
> 4. Sun Java and a flash player installed. Yes I know it means accepting a licence agreement
 It takes about two minutes from installing Ubuntu to get these working synaptic-> ubuntu restricted extras .Remember if you installed windows youself you would have to go to sun javas site then adobes to get these as they arn't installed in windows either by default.

> The only thing I did not mention is an option to choose an anti-virus program. I've just read that few viruses exist for Linux at the moment, but if this changes, then obviously an anti-virus program will be required in future.
 You can install clam av but not much point as it really only detects windows viruses which have no effect in ubuntu . Viruses are not a problem as to affect the system they need root access and would have to ask for the password each time it changed something.

---

### Post by philinux on 2009-10-20
> 4. Sun Java and a flash player installed. Yes I know it means accepting a licence agreement, but who reads them? Most users will accept the agreement so the software can just work. I could not get flash player working as soon as I opened youtube, but eventually found flash player using the tools for installing programs in Ubuntu.

It's not just about accepting an agreement it is ubuntu's philosophy.
However simple to sort out.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by snakeman21 on 2009-10-20
There is an IE for linux.  It's kind of a pain to install, but it's useful for testing web pages you've made to see if they look right in IE.

---

### Post by MaxIBoy on 2009-10-20
This is an interesting read which might explain some of it:
[http://www.fsf.org/about/what-is-free-software](http://www.fsf.org/about/what-is-free-software)

Basically, a lot of people (myself included) woiuld object if Flash and Java were included out-of-the-box. It's like asking us to install a virus-- we can't look at the source code, we have no dea what these programs actually do. For all I know, Flash will periodically "phone home" to Adobe Inc. with a history of my browsing habits. (In fact, it *does* do this, and we only found this out by watching it carefully.) 

Full disclosure: I do in fact use Adobe's Flash plugin, because I trust Adobe not to look at personal details. But not everyone trusts Adobe and it's not fair to expect them to. That should be a personal choice.

Internet Explorer would be even worse. Not only is it proprietary, it's a huge security risk. The danger with including IE is that people might actually use it.



You can also install something like Linux Mint. Mint is the exact same as Ubuntu with a different theme, all the programs renamed (i.e. Gimp renamed to Mint Gimp or similar,) and things like flash working out-of-the-box.

---

### Post by philinux on 2009-10-20
> **snakeman21 said:**
> There is an IE for linux.  It's kind of a pain to install, but it's useful for testing web pages you've made to see if they look right in IE.

+1 However most times all you need for problem pages is the user agent switcher. [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by mick222 on 2009-10-20
> You can also install something like Linux Mint. Mint is the exact same as Ubuntu with a different theme, all the programs renamed (i.e. Gimp renamed to Mint Gimp or similar,) and things like flash working out-of-the-box.
 Whilst mint is based on Ubuntu if you look at it now it is quite different and a distro in it's own right. Mint install has sort of been copied by Ubuntu and mint tools ,mintupdate and the menus are all different from a standard Ubuntu install.

---

### Post by MaxIBoy on 2009-10-20
So if I take Ubuntu and install one or two other programs on it, it's not Ubuntu anymore? Wrong. 

You can easily install MintMenu and MintUpdate on Ubuntu by adding the proper repositiories and looking in the package manager. 


Not to say that Mint isn't a worthy project. It's just not a real distro, more of a remix.

---

### Post by P4man on 2009-10-20
> **MaxIBoy said:**
> 

Not to say that Mint isn't a worthy project. It's just not a real distro, more of a remix.

I guess one could call ubuntu a remix of debian too, instead of real distro :)
Anyway, thats kind of a pointless discussion, what matters is that we have the choice between debian, ubuntu, mint and over a 100 other distro's or remixes :)

---

### Post by MaxIBoy on 2009-10-20
> **P4man said:**
> I guess one could call ubuntu a remix of debian too, instead of real distro :)
Anyway, thats kind of a pointless discussion, what matters is that we have the choice between debian, ubuntu, mint and over a 100 other distro's or remixes :)
The difference is that Mint uses the Ubuntu repositories, whereas Ubuntu has its own repos separate from Debian.

But yes, remixes are just as valid and just as useful.

---

### Post by philinux on 2009-10-20
> **MaxIBoy said:**
> The difference is that Mint uses the Ubuntu repositories, whereas Ubuntu has its own repos separate from Debian.

But yes, remixes are just as valid and just as useful.

I dont run mint but.
I think you'll find mint is a Distro with it's own repos.
[http://en.wikipedia.org/wiki/Linux_Mint](http://en.wikipedia.org/wiki/Linux_Mint)

---

### Post by DeMus on 2009-10-20
Adding IE to Ubuntu? Come on. Most of us are trying to get away from Microsoft because it is unsafe, unstable, and you want to include it into Ubuntu? I say NEVER. But who am I?
If you can't see a webpage as it should be, then contact the webmaster and point out to him/her the website is not coded right. Or use any of the possibilities mentioned here in this thread. I know even that is crazy, we have to adjust to people who follow Microsoft's way of doing things. It's a world upside down.
Isn't there a website somewhere where we can blacklist those sites which do not confirm to the W3 standards? Maybe that'll teach them.

I still think it is shame that Adobe bought Macromedia and therefore Flash. I simply don't like Adobe. They build gigantic software packages which are so slow. Just see the Acrobat reader. A 70MB download file for a simple reader??? Who comes up with that? Other pdf readers need a few MB and do the same.

No, let's stick with those people who make software for Linux as it is intended: free, fast, secure. Real Linux software, not Windows software coded in a different way so it works on Linux.

When you want to make the move to Linux then go all the way. Forget you ever learned about Windows. The two OS's just aren't the same. As it is pointed out so often: Linux is not Windows.
Read as much as possible about it, there are plenty books and websites to learn all there is to know about this great OS.

---

### Post by bumanie on 2009-10-20
Essentially agree with the above sentiments - as with many new linux users, who have only used windows, the new user still thinks the way they did when using windows. But the two OSes are completely different, one needs to learn a new way of doing things. The issue is whether you are prepared to go on a learning curve and learn a new way of doing things. If you are, you will find that there is much you can do with your pc without the limitations and constraints on choice that is set by a proprietary system. By the way, I would not like any of those things you mentioned included natively in ubuntu, especially IE. 
To format a drive, as mentioned there is gparted, but it can also be done via command line (bar it being one of those horrible U3 things). Although anti-virus is not really needed for linux, there is the open-source program [clamav]("http://www.clamav.net/") and there are some others like avg free and avast free that have linux versions available. You are correct that there are very few linux viruses. For a virus to be executed and do system-wide damage in linux, you would have to be tricked into executing the virus in super user mode. For more, read [this]("http://linuxmafia.com/~rick/faq/index.php?page=virus").

---

### Post by Ub28 on 2009-10-20
Thank you so much for your replies, I'm really grateful.  :)

I find Ubuntu makes my PC go at "rocket speed" and it's so much nicer to use Ubuntu.  It feels like having a brand new computer, there are no delays when opening programs - I could go on forever about how Ubuntu is better on my computer!!!!

I have noticed another thing about Ubuntu: my computer runs a *LOT* cooler.  After I shut down Ubuntu and switch off the mains, I notice the back of my PC doesn't feel hot.  When running Vista, the hard drive is constantly clunking away and the power supply feels like a room heater!

Again many thanks and I will carefully read all the replies.

Cheers.):P

---

### Post by solwic on 2009-10-20
> **DeMus said:**
> Adding IE to Ubuntu? Come on. Most of us are trying to get away from Microsoft because it is unsafe, unstable, and you want to include it into Ubuntu? I say NEVER. But who am I?
If you can't see a webpage as it should be, then contact the webmaster and point out to him/her the website is not coded right. Or use any of the possibilities mentioned here in this thread. I know even that is crazy, we have to adjust to people who follow Microsoft's way of doing things. It's a world upside down.
Isn't there a website somewhere where we can blacklist those sites which do not confirm to the W3 standards? Maybe that'll teach them.

I still think it is shame that Adobe bought Macromedia and therefore Flash. I simply don't like Adobe. They build gigantic software packages which are so slow. Just see the Acrobat reader. A 70MB download file for a simple reader??? Who comes up with that? Other pdf readers need a few MB and do the same.

No, let's stick with those people who make software for Linux as it is intended: free, fast, secure. Real Linux software, not Windows software coded in a different way so it works on Linux.

When you want to make the move to Linux then go all the way. Forget you ever learned about Windows. The two OS's just aren't the same. As it is pointed out so often: Linux is not Windows.
Read as much as possible about it, there are plenty books and websites to learn all there is to know about this great OS.

+1.  I like the way you think. :cool:

---

### Post by snakeman21 on 2009-10-20
> **DeMus said:**
> Adding IE to Ubuntu? Come on. Most of us are trying to get away from Microsoft because it is unsafe, unstable, and you want to include it into Ubuntu? I say NEVER. But who am I?
If you can't see a webpage as it should be, then contact the webmaster and point out to him/her the website is not coded right. Or use any of the possibilities mentioned here in this thread. I know even that is crazy, we have to adjust to people who follow Microsoft's way of doing things. It's a world upside down.
Isn't there a website somewhere where we can blacklist those sites which do not confirm to the W3 standards? Maybe that'll teach them.

I still think it is shame that Adobe bought Macromedia and therefore Flash. I simply don't like Adobe. They build gigantic software packages which are so slow. Just see the Acrobat reader. A 70MB download file for a simple reader??? Who comes up with that? Other pdf readers need a few MB and do the same.

No, let's stick with those people who make software for Linux as it is intended: free, fast, secure. Real Linux software, not Windows software coded in a different way so it works on Linux.

When you want to make the move to Linux then go all the way. Forget you ever learned about Windows. The two OS's just aren't the same. As it is pointed out so often: Linux is not Windows.
Read as much as possible about it, there are plenty books and websites to learn all there is to know about this great OS.

+1.  So many people download Linux thinking that they're essentially getting a free version of Windows.  How could Linux be any better than Windows if it was the same as Windows?  It's the differences that make a system better than another one, not the similarities.  I stopped using Windows mainly because I was sick of having bloated antivirus programs, BSOD's, and stupid "Trial Versions" of software that are intended for nothing more than to entice me into shelling out hundreds of dollars for the full version.  Which would inevitably crash once I bought it.  

Sure, there were differences that were hard to get used to.  But after a few weeks, I came to appreciate them.  It confused me at first when I ran a command from the Terminal, and I didn't get a confirmation.  I thought that meant it failed.  But then a dear friend named Jason (who was helping me learn Ubuntu from halfway around the globe) told me that Linux only bothers to tell you if something *doesn't* work.  This was tricky for me at first.  But now, on the rare occasion that I do something on a Windows system, I absolutely *hate* all the pointless confirmations and having to click "Okay" for EVERY LITTLE THING I DO.  It's insufferable.  I love how Ubuntu doesn't ask me to confirm when I want to trash a file.  I find it so pointless on Windows that you have tell it to delete a file, then tell it that yes, you're sure you want to delete it, then follow the same two steps to delete it from the recycle bin.  I don't have to be sure that I want to put it in the trash, because I can easily recover it if I choose to.  It just seems that Windows assumes that you are an idiot.

---

### Post by trixman on 2009-10-21
> **Ub28 said:**
> [FONT="Arial"][SIZE="3"][COLOR="Blue"]Hi

I'm so far very pleased with Ubuntu and I'm using it more often than Vista (I have 2 hard disks, one with Vista and the other with Ubuntu).

I'm glad all my hardware works and there was no faff or tricky steps to get the devices up and running.

Bearing in mind I'm new to the Linux world and I've been using Windows for years (and I expect most home users reading this are in the same situation). I would like to suggest the following four features are made available "out of the box" for Ubuntu users, including those who bought Ubuntu pre-installed:

1. Firewall software that fully passes the Shields Up test on "Common Ports" ([https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")) - users of Windows XP SP2 and later versions already have a software firewall that passes the "Common Ports" test.  I don't connect through a router with a firewall, so the Shields Up test fails on me. :(

2. Choice of web browsers and an option to get Internet Explorer running.  For reasons unknown to me, some websites will **only** work in Internet Explorer.  After lots of searching the Internet, I discovered IEs4Linux and after lots of confusion, I followed some technical steps on their website and finally got Internet Explorer 6 working.  

3. A friend who has a Ubuntu netbook was unable to format USB pendrives, memory cards etc. until they got some 3rd party tool. As we're used to the Windows method of right-clicking a removable device and selecting the "Format" option (along with a warning about losing files!), I hope the same feature can be included with Ubuntu.

4. Sun Java and a flash player installed. Yes I know it means accepting a licence agreement, but who reads them?  Most users will accept the agreement so the software can just work.  I could not get flash player working as soon as I opened youtube, but eventually found flash player using the tools for installing programs in Ubuntu.

_
I know plenty of people who get frustrated with computers and get confused over the simplest things in Windows. If Ubuntu has most or all of the expected things available from day one, I can see a lot of happy Ubuntu users forever.

The only thing I did not mention is an option to choose an anti-virus program. I've just read that few viruses exist for Linux at the moment, but if this changes, then obviously an anti-virus program will be required in future.

Thanks for reading.  Does anyone else have a wish-list for NEW users of Ubuntu/Linux?[/COLOR][/SIZE][/FONT]

enjoy the linux !!!!:P

---

