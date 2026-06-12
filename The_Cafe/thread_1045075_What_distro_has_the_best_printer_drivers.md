---
title: "What distro has the best printer drivers?"
date: 2009-01-20
forum: The Cafe
---

### Post by NintendoTogepi on 2009-01-20
Ubuntu? SUSE? Arch?

My aunt wants me to set up a computer with Linux on it for my 14 cousin (Her daughter). She's in High School now and has to do a lot of essays, and it's quite a hassle for them having to share the one computer in the house. (a MacBook that they got last year)

Anyway, I showed my aunt a cool demonstration of Linux a few months back and how customizable it was, so now she wants me to set up a computer with just this on it:

Word Processor
Calculator

So that my cousin can write the essays and such for her school projects. (my aunt specified that she did NOT want any internet to be on the computer to distract her)

Should be very easy to get an old computer and hook it up with those programs, but what should I do in regards to the printer? What distro has the best printer support? What's the best printer company in terms of Linux support?

---

### Post by jrusso2 on 2009-01-20
I am not sure which one has the best printer support most use CUPS.  Find out the make and model of printer she uses.

---

### Post by steeleyuk on 2009-01-20
You'd be better off telling us which printer model they have, most HP printers have open source drivers. Epson also usually have drivers available but they can be incomplete on some models.

---

### Post by Bölvaður on 2009-01-20
HP makes Linux drivers which all are in the kernel by default, I think...

And the kernel version is the thing that determinates the driver support, but not the distro in it self.... I think...

why am I posting my lack of knowledge? because I must keep my ignorance spreading. The more of me in the world to go around the better :)

---

### Post by SunnyRabbiera on 2009-01-20
Its not the distro, its the printer model.
While most modern linux distros will probably be more compatible with cedrtain hardware its the hardware itself that matters.
Ubuntu, Mandriva, Debian, Fedora will probably work along with their variants, but again its the make and model that matters not the distro.

---

### Post by NintendoTogepi on 2009-01-20
> **steeleyuk said:**
> You'd be better off telling us which printer model they have, most HP printers have open source drivers. Epson also usually have drivers available but they can be incomplete on some models.

They want me to buy a printer, something under 100 dollars.

HP is a good one to buy?

So how exactly should I do this? Install Ubuntu minimal and then just add on AbiWord, Galculator, download the drivers...etc?

---

### Post by Sef on 2009-01-20
> They want me to buy a printer, something under 100 dollars.

HP is a good one to buy?

If you want to check that the printer is supported, then check the [HPLIP site]("http://hplipopensource.com/hplip-web/index.html").  Almost all are, but there are few exceptions.

---

### Post by vishzilla on 2009-01-20
the *gutenprint* package has many drivers while if you will buy hp, the *hplip* package will satisfy and for a samsung printer *splix* package has the drivers.

I guess most of the popular distros should have all these packages

---

### Post by Bölvaður on 2009-01-20
> **NintendoTogepi said:**
> So how exactly should I do this? Install Ubuntu minimal and then just add on AbiWord, Galculator, download the drivers...etc?

Could do, or go Debian or Arch.
But for a user that may need to work with other's it may be better to use OpenOffice3 as it has decent docx capabilities now, where for an instance GNUmetics may even lack in ods files and AbiWord in odf.


About web browser. You said there shouldn't be any, but she might need to send her files to other people, or to her self, so having some minimal browser with no flash would be something to consider

---

### Post by mips on 2009-01-20
> **NintendoTogepi said:**
> 
HP is a good one to buy?

So how exactly should I do this? Install Ubuntu minimal and then just add on AbiWord, Galculator, download the drivers...etc?

Yeah go with HP but first check the link Sef provided.

Just install the diver from the repos.

---

### Post by jespdj on 2009-01-20
Look at this: [OpenPrinting database](http://openprinting.org/printer_list.cgi) - contains a lot of info on printer models and whether or not they work on Linux, including information on how to access your particular model on Linux

---

### Post by ssam on 2009-01-20
[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)
has a huge database of printers and details how well they are supported. i have found it to be accurate.

there are a few HP printers that do not work (i am pretty sure that i have read that some of the cheapest HP printers are made by other companies and then re-branded as HP, these are the ones with poor support).

as people have said, there is not much difference between distros, however if you are using an old distro, you may get older printer drivers which may not work so well.

---

### Post by mips on 2009-01-20
A nice printer to have is the HP Officejet 6313 All-in-One. It does print, scan, copy & fax. Has Ethernet LAN & USB ports. They are really nice and it's like a mini office.

I see Newegg sells the 6310 (does not have LAN) for $89. The 6310 is an older model and I have found the 6313 to cost about the same.

Have a look at, [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010270038%2050001186%201094919007&bop=And&Order=PRICE](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010270038%2050001186%201094919007&bop=And&Order=PRICE)

---

