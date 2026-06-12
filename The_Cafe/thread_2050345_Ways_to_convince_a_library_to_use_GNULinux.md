---
title: "Ways to convince a library to use GNU/Linux?"
date: 2012-08-30
forum: The Cafe
---

### Post by Gogeden on 2012-08-30
Does anyone have any good ideas (Both ethical and practical) to convince a library to (At least) let users choose which operating system they can use?

---

### Post by Jakin on 2012-08-30
Im sure it would be much harder than just asking any ol' library, to sit down and listen to what you have to say. Start at the Main Branch if you are serious :)

Of course the first thing they will likely say, is bring your own computer, and run whatever you like.

---

### Post by KiwiNZ on 2012-08-30
What would their incentive to change be?

---

### Post by forrestcupp on 2012-08-30
What do you need to do on a library computer that you can't do with Windows?

---

### Post by Jakin on 2012-08-30
Certainly though, being a public place, it would be nice to see use of open-sourced means. Can't hurt to ask, if you can manage an audience.

---

### Post by KiwiNZ on 2012-08-30
> **Jakin said:**
> Certainly though, being a public place, it would be nice to see use of open-sourced means. Can't hurt to ask, if you can manage an audience.

It is not a simple process.

---

### Post by Primefalcon on 2012-08-30
if its just dumb systems accessing the Internet might not be too hard to change.... but to change the core infrastructure over.... well.... the techs might not know linux, they'd certainly have to re-train the staff...... and of course the down time....

I can't really see you having much luck, sorry

---

### Post by QIII on 2012-08-30
Offer to pay the municipality or county for the cost of infrastructure, integration with the city or county systems, training of administrators...

---

### Post by wojox on 2012-08-30
> **QIII said:**
> training of administrators...

or charge them and support it.

---

### Post by mevun on 2012-08-30
At my library, the PCs run special software to limit users to 2 hours per day which is tied to your library card.  This is 2 hours which can be split up, so you can get a 30 minute reservation, use it for 25 minutes and quit.  Then sign back into another computer later, do an hour, etc.  In between users, the computer "forgets" everything you've done as far as browser history and any files saved on the computer.

The computers are also integrated with their printing system, where the  print jobs are saved on some server.  Then you go to the printer station and provide your library card number to release your print job (and pay the  per-page fee).

Even if the same functionality was developed for Linux, I don't think they would want to run it as long as the "customers" want Windows.  Many people use the library for job searches and use MS Word for their resume.  I'm aware it's possible to use other software, but the people without PCs are probably less computer-savvy.

---

### Post by QIII on 2012-08-31
> **wojox said:**
> or charge them and support it.

Now you're thinking!  :) Municipalities don't usually pay much.  :(

---

### Post by Roasted on 2012-08-31
Dropping Ubuntu systems in place of Windows wouldn't be difficult, assuming the software needed for their OPAC systems is not proprietary to Windows (most are web based anyway). The difficult part would be future maintenance, as the average I.T. Joe Technician knows Windows and nothing else.

---

### Post by lykwydchykyn on 2012-08-31
(I do tech support/systems admin for a municipal govt.)

Our library system uses an Ubuntu LTSP system for OPAC terminals, and debian for some kiosk-type terminals at the branches.  Mostly, because they have access to a Linux nutter who tinkers with this kind of stuff.  It did save a lot of money and has been successful for many years.

However, when it comes to the actual workstations available for public use, there are numerious things preventing the use of Linux.

- They use a time management/pc reservation/print costing system like the one mevun described, which doesn't support Linux (and from the response I got from the vendor, probably never will).

- They often get computers via grant, which come with requirements (such as "must run MS Publisher 2007").  Most notably, computers they've received from the Gates foundation (yes, *that* Gates).

- Staff (and I mean librarians, not IT people) are often required to help patrons use the computers.  It's all they can do to support people on one OS.

- Sadly, even in 2012, there are web pages that only work in IE, documents that only work in MSO, and peripherals that only work with Windows.  

Honestly, I think for a smaller library just starting out with computers (and thus, patrons having no particular expectations of the library's computers), a friendly, locked-down Linux solution could work great.  

Making a change at in an established setup requires buy-in from the whole staff, or else the project gets chucked at the first sign of a problem.  It's hard enough to find IT people who are into Linux, never mind administrators and library staff.

---

### Post by Lucradia on 2012-08-31
> **Gogeden said:**
> Does anyone have any good ideas (Both ethical and practical) to convince a library to (At least) let users choose which operating system they can use?

All our libraries still run Windows XP.

---

### Post by mips on 2012-08-31
> **lykwydchykyn said:**
> (I do tech support/systems admin for a municipal govt.)

Our library system uses an Ubuntu LTSP system for OPAC terminals, and debian for some kiosk-type terminals at the branches.  Mostly, because they have access to a Linux nutter who tinkers with this kind of stuff.  It did save a lot of money and has been successful for many years.

However, when it comes to the actual workstations available for public use, there are numerious things preventing the use of Linux.

- They use a time management/pc reservation/print costing system like the one mevun described, which doesn't support Linux (and from the response I got from the vendor, probably never will).

- They often get computers via grant, which come with requirements (such as "must run MS Publisher 2007").  Most notably, computers they've received from the Gates foundation (yes, *that* Gates).

- Staff (and I mean librarians, not IT people) are often required to help patrons use the computers.  It's all they can do to support people on one OS.

- Sadly, even in 2012, there are web pages that only work in IE, documents that only work in MSO, and peripherals that only work with Windows.  

Honestly, I think for a smaller library just starting out with computers (and thus, patrons having no particular expectations of the library's computers), a friendly, locked-down Linux solution could work great.  

Making a change at in an established setup requires buy-in from the whole staff, or else the project gets chucked at the first sign of a problem.  It's hard enough to find IT people who are into Linux, never mind administrators and library staff.

Support really is an issue. I could setup the most amazing system for a company etc but the general IT support crowd out there are microsoft based and when they encounter anything they they are not familiar with it's immediately **** according to them. Our government IT agency (SITA) does however have an open source policy and things are moving slowly but surely.

Locally all our public libraries have switched over to [Brocade]("http://www.nasa.gov/images/content/679610main_pia16092-673.jpg") from the PALS Library Systems or are in the process of switching over. As far as I'm aware Brocade uses a lot of open source components but it's not a 'free' system as far as I'm aware.

We don't have free to use PCs & Internet access in our libraries from what I have seen but something like LTSP could work I reckon.

---

### Post by Roasted on 2012-08-31
For what it's worth, LTSP is absolutely friggen sweet. It's a beautiful way to mass-manage multiple systems in one shot, not to mention it really breathes live into old hardware to serve as clients (assuming your server isn't exactly a Pentium 4). I've set up a few labs in school districts utilizing LTSP with great success and extremely minimal maintenance.

---

### Post by lykwydchykyn on 2012-08-31
> **Roasted said:**
> For what it's worth, LTSP is absolutely friggen sweet. It's a beautiful way to mass-manage multiple systems in one shot, not to mention it really breathes live into old hardware to serve as clients (assuming your server isn't exactly a Pentium 4). I've set up a few labs in school districts utilizing LTSP with great success and extremely minimal maintenance.

It is awesome.  Though I should mention that my original LTSP server for our library *was* a P4 :), and served up about 13 clients running firefox 2.

Nowadays I got some 8-core beast running it; we're approaching 20 clients and barely breaking a sweat.

---

### Post by Gogeden on 2012-09-03
Thanks for the replies folks! I might try to show the head officials of the library system some examples and advantages to using GNU/Linux over Windows.

---

### Post by overcast on 2012-09-03
If it has windows, surely they are likely to be experiencing the virus or malware issue. Show them how you are avoiding that by using the linux.

---

### Post by mamamia88 on 2012-09-03
My local library has actually moved over to some kind of Ubuntu variant that they setup to look like windows.  Guess it's just easier or cheaper to maintain.

---

