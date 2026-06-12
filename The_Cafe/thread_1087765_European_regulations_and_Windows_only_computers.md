---
title: "European regulations and Windows only computers"
date: 2009-03-05
forum: The Cafe
---

### Post by anthonie on 2009-03-05
Hi all,

I have no clue whether I'm posting in the right forum. 

Today I received an email from ASUS regarding a complaint I have about my laptop. It does not have a decent acpi functionality and therefor I asked for a solution. 

I'll copy and paste the email right under the reply I got. 

Dear Customer:
This Laptop its designed and tested to work under Windows Vista.
Asus Iberica

---------- Original Message ----------
From : [email]anthonie@********.com[/email]
Sent : 03/03/2009 19:02:35
To : "tsd@asus.com.tw"
Subject : <TSD> Notebook X50Gl 

[CASEID=WTM200903031826354578]

Apply date : 3/3/2009 6:26:35 PM

[Contact Information]
*Name : Anthonie 

[Product Information]
*Product Type : Notebook
*Product Model : X50Gl
*Date of Purchase : 2008/11/1

*Operating System : Linux 

[Problem Description]
I run a dualboot Vista/Linux and I have described the problem I have on the forum for the X50GL model.

[http://vip.asus.com/forum/view.aspx?](http://vip.asus.com/forum/view.aspx?)
id=20090302200731206&board_id=3&model=X50Gl&page=1&SLanguage=en-us

I'll simply cut and paste the message here, as I learned only today that tech staff is not likely to read the forums and should rather be contacted through this enquiryform. 

It seems that the programmers at Asus did not manage to get the instructionset DSDT and/or ECDT correct. As a result my laptop has lots of flaws.

The most important of them is that when I use any linux distro I will be stuck with a machine that has not battery icon (which kind of reduces the usability of a laptop-machine).

Less annoying, but pretty silly too, is the fact that the power-down function does not work. So, when I turn off my machine from the desktop it will power down to tty1, but after that it comes to a halt and the machine needs to have it's power-button pressed for a couple of seconds in order to really shut down.

I suffer frequent lags in functionality that at first I thought were due to the operating system of choice, but after fiddling around for a couple of weeks that turns out not to be the case.

At the contrary: When I look at the directories under /proc/acpi/, it turns out that hardware states are not reported at all. The files are there, but the're empty (zero bytes, that is).

I know about the acpi4asus project, but that is pretty much out of date, resulting in a machine with lots of flaws as briefly described above.

I guess the question to the experts at Asus should be: Can we expect an updated DSDT-set somewhere in the near future or are we left alone in the dark to sort it out ourselves?

If you search the internet you'll find lots of users that have no clue about the nature of the problem. All they know is the machine they paid good money for works partly only.

Anthonie

------------------------------


So what it boils down to is that I would like to know whether this is legal in Europe or not. Are vendors allowed to sell general purpose computers that can only be expected to run a Microsoft Operating System?

I searched the net but had trouble just deciding what search terms to use. Needless to say I did not find any usefull information whatsoever.

If anyone else has experience in the legal field or has dealt with these kind of problems before, I'd like to hear.

Anthonie

---

### Post by sydbat on 2009-03-05
I suggest looking in your local phone book under 'Lawyers' and find one that deals with technology law...then call them and ask if you can ask one or two questions about this. It should be free, as most lawyers allow a 5 - 10 minute consultation call to determine if there is a case.

---

### Post by SuperSonic4 on 2009-03-05
As far as I know it is not legal but I'm not a lawyer or know very much at all. However, I suspect this kind of vendor lock in would violate antitrust/competition laws and microsoft was already found guilty of stifling competition by bundling WMP with windows.

More likely is the tech people can't be bothered to deal with it

---

### Post by anthonie on 2009-03-05
> **sydbat said:**
> I suggest looking in your local phone book under 'Lawyers' and find one that deals with technology law...then call them and ask if you can ask one or two questions about this. It should be free, as most lawyers allow a 5 - 10 minute consultation call to determine if there is a case.

Thnx for the reply. I kind of waited to do that as the local language here is one I do not speak very well, being a foreigner and all that. Hence the post to see if others have dealt with it. 

Personally I had the same thought as SuperSonic4, but maybe someone else here can shed some light on the matter.

Anthonie

---

### Post by mihai.ile on 2009-03-05
Excuse me but are you telling me that I could get in trouble if I start a Laptop brand only with Ubuntu on them because:
vendors are not allowed to sell general purpose computers that can only be expected to run a SPECIFIC Operating System?
Since when?
I sell with what I can support, don't buy if you don't want, and what do you mean by "general purpose"? It has ASUS on it. By this logic Mac would be even worse!

I could understand it if ASUS would be the market leander close to 100% market share but even so...

You can't force someone to support Microsoft Windows or Mac OS instead of their Ubuntu offering just because you like it more...

P.S: I switched the OS's, it makes more sense to me this way.

---

### Post by MikeTheC on 2009-03-05
@ mihai007:

No, it really wouldn't work that way. An OS which is "Linux-centric" or at least "Linux friendly" would be one in which there was complete documentation on all of its functionality, more or less by definition. At that point, Microsoft or anyone else who wanted to support the hardware with their OS would have a practically zero-effort experience in doing so.

Supporting Linux is not the same thing as supporting any proprietary, commercial OS, since by definition everything has to be exposed and "in the open". Everyone -- including commercial OS vendors -- would benefit. You cannot correctly or accurately turn this argument around the other way and come to the same conclusion.

---

### Post by mihai.ile on 2009-03-05
Ok, that's correct, but even so they make ASUS laptops. They can decide what to support don't you think? You can't force them to hire developpers/support staff just to offer another OS option. It's the way they donne it, don't buy their products if you don't like what they are doing. I still think that the only way to force the company would be if they are close to full market share in that area.

People have a choise, don't buy their products. I know there are better and worse choises (usually we get worse hardware if we want to choose linux based systems) but that's just the way it is right now, I hope will improve.

This is one of the reasons that I got an Dell xps as my second laptop.

---

### Post by MikeTheC on 2009-03-05
> **mihai007 said:**
> Ok, that's correct, but even so they make ASUS laptops. They can decide what to support don't you think? You can't force them to hire developpers/support staff just to offer another OS option. It's the way they donne it, don't buy their products if you don't like what they are doing. I still think that the only way to force the company would be if they are close to full market share in that area.

People have a choise, don't buy their products. I know there are better and worse choises (usually we get worse hardware if we want to choose linux based systems) but that's just the way it is right now, I hope will improve.

This is one of the reasons that I got an Dell xps as my second laptop.

You're combining two different things and assuming I said something I didn't.

Asus is perfectly free to do whatever they want with the products they make.

Linux-friendly or Linux-centric hardware, as I described above, is well documented and everything is accessible to any OS developer who comes along.

I didn't say that Asus either *does* make or *should* make (or, to pick up on what you said, *should **be forced** to make*) such hardware. That being said, just like people probably wouldn't choose to buy a car that had only three wheels, the market should respond appropriately to whatever Asus puts out.

Personally, I am always fully conscious of the fact that whenever I buy something, I am voting with my wallet. The onus is on my fellow human beings to "get it" and act accordingly. Until or unless that happens, don't go expecting any real improvements.

For my part, I don't (normally) buy name-brand PCs, the exception being Macs from Apple (for clearly obvious reasons). My current PC is an eMachines system, but only because it was decent enough and price-pointed low enough that I couldn't justify building a system since I couldn't have built one as well-spec'd as this one for the same price.

---

