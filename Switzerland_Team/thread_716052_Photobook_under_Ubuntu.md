---
title: "Photobook under Ubuntu"
date: 2008-03-05
forum: Switzerland Team
---

### Post by frank.bommeli on 2008-03-05
Hi guys,

Since I decided to give Ubuntu a try, I have the same recurrent problem.
One of my main activity home is to play with photos. I make photobooks. I haven't found any Photobook provider in Switzerland with a software for linux. Ifolor (ex photocolor) has a .net framework application. I tried to install fuji's with wine, but could not install it (got an error)

So my question is how can I make a Photobook with Ubuntu in Switzerland?

Has someone an idea?

Thanks in advance.

Frank :confused:

---

### Post by popch on 2008-03-08
I have seen someone offer a web based photobook service which runs on flash. It was called Snapmania. Green.ch also appears to offer that service. I have, however, not been able to find any prices for the finished books. I have no personal experience with any of those.

Googling (in google.ch) for 'Photobook' yields a few hits. Have you tried running some of those downloads in Wine?

---

### Post by frank.bommeli on 2008-03-09
I don't want a web based solution. First, I don't have always a connection when I'm working on my photobooks and due to the size of the images, it can be painful to work online and / or over a slow connection.

I confess, I tried only fuji with Wine and nothing with ifolor.

I should  add that I'm a Ubuntu (Linux) beginner.

---

### Post by popch on 2008-03-09
There's myphotobook which runs in Wine, after a fashion. However, it is painfully slow and tends to drop mouse clicks ar something. Not very enjoyable for a real project.

There are, however, some services which accept pdf documents instead of some special formats. You can do pdf quite well with OpenOffice.

---

### Post by frank.bommeli on 2008-07-12
Well I tried the ifolor app. It is the one I use under windows.
Using wine and winetricks, I was able to start it but there are errors during installation and the application is not usable. The first error message is:


fixme:powrprof:DllMain (0x7e370000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:advapi:CheckTokenMembership ((nil) 0x13b9b8 0x32f97c) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x13b9b8 0x32f97c) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x13b9b8 0x32f97c) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x13b9b8 0x32f97c) stub!
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime Optimization Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000457,(nil),0x0001,0x00000000,0x7e5fd254,(nil)): stub
err:eventlog:ReportEventW L".NET Runtime Optimization Service (clr_optimization_v2.0.50727_32) - Service reached limit of transient errors. Will shut down. Last error returned from Service Manager: 0x80070005.\n"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime Optimization Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000454,(nil),0x0001,0x00000000,0x7e5fd2c8,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub


I have to say I don't know what to do with that.
If someone has an idea. If I make it one day, I will tell you.

---

### Post by frank.bommeli on 2009-01-29
Well I guess I have to give the last answer to that one.
I finally found a photobook software which runs under linux.
Ok it is under Wine, but It works fine.

I now use Bookfactory (bookfactory.ch). For what I saw it is the same software as for bookfactory.de. 
I see no difference under Windows or with Ubuntu.

Hope the next one will not have to look as long as I had to.

Cheers

fan

---

### Post by mdklnxtps on 2009-06-10
I too have looked around quite a bit.

Finally, in Switzerland I've found that CeWe albums can be ordered by Migros, Manor and onlinebilder24.ch; at the latter two one can already download the Linux client of the CeWe software.
Via the CeWe forums one can also get the unbranded software with which one can burn a CD that can be put into a fotobag at the Migros - which is what I did a week ago.

I unfortunately didn't select the right option, for "photo paper photo album" (fotoalbum auf fotopapier), but Migros doesn't even know they have that, no one could give me the price quote (instead they said they don't have it in their 'Sortiment')...

I have also talked to someone from fotomaxx.ch, who mentioned that they do accept a series of jpgs to make albums from.
I asked at [email]info@fotomaxx.ch[/email] and they sent me the information on how to do that (sRGB images, size in mm for cover and book pages, 300ppi, file naming, etc).

I then realised that this may be a regular option, so I also sent an email to the contact address of [www.expertfoto.ch](www.expertfoto.ch), where indeed they also sent me info on how to do things via a series of jpgs.

I'm mostly interested in the latter two, since they both offer photo albums on photo paper (fotoalbum auf fotopapier) instead of digital print quality (digitaldruck), and on top of that they offer leporello - pages open completely, not like a regular book, but like most children's books.
This last feature is not offered at CeWe as far as I know.

Hope this helps.

---

### Post by Catapa on 2009-09-09
[COLOR=#000000][FONT=Times New Roman][FONT=Verdana][B]Image layering and blend-in image masks in photo books with Linux

[/B]
Try [http://fotoinsight.com/book](http://fotoinsight.com/book) , the FotoInsight Designer photobook software exists in different languages, they are all over Europe.

FotoInsight offers photo books (200 gr paper, 300 dpi Indigo print) and [photo paper books]("http://www.sourcewire.com/releases/rel_display.php?relid=49733") (400 gr photo paper, processed photographic paper) in different sizes. 


[/FONT][/FONT][/COLOR]

---

### Post by mdklnxtps on 2009-09-10
Hi Catapa, thanks for your find.
This is actually the exact same producer/printer as I mentioned, they are called CeWe.

Another thing I really dislike is their terms, you have to agree that they can use your photoalbum on their promotional pages...

Otherwise, they indeed have a linux client as well. Which works fine.

---

### Post by Catapa on 2009-09-11
> **mdklnxtps said:**
> they are called CeWe.

Another thing I really dislike is their terms, you have to agree that they can use your photoalbum on their promotional pages...

Otherwise, they indeed have a linux client as well. Which works fine.

The terms you mention are if using the [photo book linux software]("http://fotoinsight.com/book") and service from the CEWE page. If you are using the FotoInsight Designer software from the FotoInsight page the terms are short and simple, at least *I could not find any clause comitting your art work*.

Cata

---

### Post by mdklnxtps on 2009-09-13
If you install the Linux photobook software - or just download it and read the EULA, you find this:
> 4.6  Authorized cewe-photo-provider and its suppliers claim no ownership of Your personal photos.*** You hereby grant us a non-exclusive, royalty-free, fully-paid perpetual licence to use, download, upload, copy, print, display, reproduce, post, transmit and distribute these photos in the normal course of our business.***

Then if you look at the example photobooks linked from the regular photobook page you posted, you'll quickly see that those are all real books made by customers of CeWe. Which implies what the normal course of their business is.
I don't like that, and I'll have my future photobooks printed elsewhere.
As I mentioned, plenty of photo houses are willing to print books based on jpgs. I asked 3 and got the positive response from 2.


Which fotoinsight designer software / software to make photobooks with are you referring to, that runs on Linux?
I couldn't find any other than the CeWe version.

---

### Post by aiser on 2009-12-01
:d

---

