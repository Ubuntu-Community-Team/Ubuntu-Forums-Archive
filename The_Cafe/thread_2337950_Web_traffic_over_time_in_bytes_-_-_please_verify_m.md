---
title: "Web traffic over time in bytes - - please verify my arithmetic"
date: 2016-09-23
forum: The Cafe
---

### Post by Drone4four on 2016-09-23
I have endeavoured to calculate how many bytes circulate the internet in any given month every five years since 1985 .  I’m using a [white paper from Cisco]("http://blogs.cisco.com/sp/the-history-and-future-of-internet-traffic") for the stats. 
If you scroll down that page, you’ll see there is a chart with an estimated amount of Gigabytes transferred in any given month, year over year.  The key point to notice here is that measurements are in GBs.  I’ve attempted to re-calculate the GB format into bytes (bytes multiplied by ten to an exponent) in order to demonstrate how amazingly fast computers advance.  

To put the statistics in perspective, I’ve divided the GB figures by 8 to demonstrate how much the data would fill a modern Moto G smartphone.

Math was not one of my stronger subjects in high school and I majored in social sciences in university.  This is why I am reaching out here.  Would a kind soul please verify my arithmetic?

1985:  33 GB/mo (10 bytes ^7)
So 3 bytes with 10 zeros
4 Moto G (8 GB storage) smartphones

1990: 1,000 GB/mo (10^10)
So 1 byte with 12 zeros 
~ 125  Moto G smartphones
	
1995: 150,500 GB/mo (10^9)
~ 1.5 byte with 14 zeros
~ 18, 800 Moto G smartphones	

2000: 75,250,000 GB/mo (10^9)
So just shy of 1 byte with 17 zeros
~ 9,406,250 Moto G smartphones

2010: 13,751,003,569 GB/mo (10^10)
So just over 1 byte with 19 zeros
~ 1,718,875,446 Moto G Smartphones
	
2019 (projected): 108,102 PB/mo (10^15)
~ 1 byte with 20 zeros
~ 13,740,000,000 Moto G smartphones

---

### Post by SurfaceUnits on 2016-09-23
Byte Converter is here to help

[http://www.whatsabyte.com/P1/byteconverter.htm](http://www.whatsabyte.com/P1/byteconverter.htm)

But if you ask harddrive manus, 33GB = ~10MB

---

### Post by steeldriver on 2016-09-23
As I understand it, the figures are already in bytes (B) not bits (b) per unit time - the division by 8 is to get them in units of "Moto G's per unit time"

Although I believe the conventional units are either "Libraries of Congress" or "station wagons full of floppies" ;P

---

### Post by yetimon_64 on 2016-09-23
> **steeldriver said:**
> ...Although I believe the conventional units are either "Libraries of Congress" or "station wagons full of floppies" ;P

:lol: ...=d>.

---

### Post by qyot27 on 2016-09-23
There is one foreseeable problem here: due to the perennial data prefix wars, you could be looking at two different sizes of -bytes.  The data transfer numbers are (per what I seem to remember is standard) standard SI prefixes (1000), since bandwidth data DL/UL figures are actually reported with standard SI units.  But the drive size reports as advertised are very likely still in binary units (1024).  The drift wouldn't be very big in 1985, but by even 1990 it would be noticeable (but likely not enough to really affect anything), and by 1995 the drift would actually start causing big problems in the accuracy of the storage size being compared.

And if you want to get *really* pedantic, subtract the size of the Android installation first and only count the storage size not taken up by the phone's OS.

---

### Post by SurfaceUnits on 2016-09-25
[h=1][SIZE=4][Files size units: &#8220;KiB&#8221; vs &#8220;KB&#8221; vs &#8220;kB&#8221;]("http://ux.stackexchange.com/questions/13815/files-size-units-kib-vs-kb-vs-kb")[/SIZE][/h]

[LIST]
[*]"1 KB" means 1024 bytes (as Windows would report it, traditional usage)
[*]"1 kB" means 1000 bytes (as Mac OS would report it, IEC usage)
[*]"1 KiB" means 1024 bytes (unambiguous, but perhaps unfamiliar terminology)
[/LIST]

[http://ux.stackexchange.com/questions/13815/files-size-units-kib-vs-kb-vs-kb#13850](http://ux.stackexchange.com/questions/13815/files-size-units-kib-vs-kb-vs-kb#13850)

---

### Post by Drone4four on 2016-09-26
According to the Cisco white paper I linked to in my initial post, Historical Global Internet Traffic Data, 1984 through 2014 goes like this:
> 
Year – Traffic (GB/mo)
1984 – 15
1985 – 33
1986 – 65
1987 – 128
1988 – 252
1989 – 498
1990 – 1,000
1991 – 2,002
1992 – 4,444
1993 – 8,715
1994 – 25,830
1995 – 150,500
1996 – 1,200,000
1997 – 5,000,000
1998 – 11,200,000
1999 – 25,500,000
2000 – 75,250,000
2001 – 175,000,000
2002 – 356,000,000
2003 – 681,050,000
2004 – 1,267,800,000
2005 – 1,802,745,619
2006 – 2,910,579,371
2007 – 4,477,367,718
2008 – 6,491,159,470
2009 – 9,301,984,735
2010 – 13,751,003,569
2011 – 19,974,008,812
2012 – 26,214,897,380
2013 – 32,798,830,927
2014 – 42,423,169,029

Do you see the notation next to traffic at the top? It says “GB”.  So I made my calculations confusing Gigabytes and Gigibytes.  In my first approach I took for example the 75,250,000 “GB” for the year 2000 and added 6 zeros to convert the number to bytes.  In so doing I conflated Gigabytes with Gigibytes which you are all saying are two different standards, one being for Windows the other for Mac. That’s not the greatest approach.  Instead this time I’m gonna use a converter, similar to the one **SurfaceUnits** shared.  Embedded in Google’s search results is a conversion calculator.  

So at this point I guess I have two question for you folks now:  

[LIST=1]
[*]With respect to the figures quoted in Cisco’s “Historical Global Internet Traffic Data, 1984 through 2014” in the white paper, are they Gigabits, Gibibits, Gigabytes, Gibibytes?  
[*]  Which of those four notations would Linux (an Android device like a Moto G) measure the data it stores?
[/LIST]

With answers to both those questions, the superior conversion tool embedded in the Google search will do all the heavy lifting and converting.

Thanks for your attention.

---

### Post by steeldriver on 2016-09-26
1. there is almost certainly no way of knowing - if telecom engineers wrote it, I'd put money on giGA i.e. units of 1000 x 1000 x 1000 bytes - given that it's almost certainly been passed through Cisco's marketing department - who knows?

2. you would need to look at the actual specs of the device, as others have mentioned you then need to decide whether to use the *total *capacity or the *available *capacity

In practice, does it really matter? You are basically doing a 'back of the envelope' calculation (aka a SWAG) - just divide the Cisco numbers by 8 and accept that you may be up "wrong" by a factor up to 1.024^3 either way (approximately +/- 7% if I've got **my **arithmetic right)

---

### Post by SurfaceUnits on 2016-09-27
A 16GB SD card in my LG Android has 14.88GB capacity

---

### Post by Drone4four on 2016-10-07
If I now wanted to [convert 33 giGA (1024 x 1024 x 1024 bytes) into bits, it would be 2.64e+11 or 2.64 x 10^11]("https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=convert+33+Gigabytes+to+bits"), right?  And 1 bit is either a 1 or 0? So it would be fair to say that 2.64e+11 ones or zeros moved or traveled across the global Internet in any given month (on average) in 1985?

---

### Post by steeldriver on 2016-10-07
Sorry - I had a brainfart above

giGA is powers of 10 (i.e. 1GB is 10^9 bytes = 8x10^9 bits)

giBI is powers of 2 (i.e. 1GiB is 2^30 bytes = 2^33 bits)

33GB is 33 x 8x10^9 bits, or 2.64x10^11 bits

---

