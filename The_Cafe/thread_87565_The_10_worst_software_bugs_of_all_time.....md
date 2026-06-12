---
title: "The 10 worst software bugs of all time...."
date: 2005-11-08
forum: The Cafe
---

### Post by KingBahamut on 2005-11-08
July 28, 1962 -- Mariner I space probe. A bug in the flight software for the Mariner 1 causes the rocket to divert from its intended path on launch. 

1982 -- Soviet gas pipeline. Operatives working for the U.S. Central Intelligence Agency allegedly plant a bug in a Canadian computer system purchased to control the trans-Siberian gas pipeline.

1985-1987 -- Therac-25 medical accelerator. A radiation therapy device malfunctions and delivers lethal radiation doses at several medical facilities. 

1988 -- Buffer overflow in Berkeley Unix finger daemon. The first internet worm (the so-called Morris Worm) infects between 2,000 and 6,000 computers in less than a day by taking advantage of a buffer overflow. 

1988-1996 -- Kerberos Random Number Generator. The authors of the Kerberos security system neglect to properly "seed" the program's random number generator with a truly random seed. As a result, for eight years it is possible to trivially break into any computer that relies on Kerberos for authentication. It is unknown if this bug was ever actually exploited.

January 15, 1990 -- AT&T Network Outage. A bug in a new release of the software that controls AT&T's #4ESS long distance switches causes these mammoth computers to crash when they receive a specific message from one of their neighboring machines -- a message that the neighbors send out when they recover from a crash.

1993 -- Intel Pentium floating point divide. A silicon error causes Intel's highly-promoted Pentium chip to make mistakes when dividing floating-point numbers that occur within a specific range. For example, dividing 4195835.0/3145727.0 yields 1.33374 instead of 1.33382, an error of 0.006 percent. Although the bug affects few users, it becomes a public relations nightmare. With an estimated 3 to 5 million defective chips in circulation, at first Intel only offers to replace Pentium chips for consumers who can prove that they need high accuracy; eventually the company relents and agrees to replace the chips for anyone who complains. The bug ultimately costs Intel $475 million.

1995/1996 -- The Ping of Death. A lack of sanity checks and error handling in the IP fragmentation reassembly code makes it possible to crash a wide variety of operating systems by sending a malformed "ping" packet from anywhere on the internet. Most obviously affected are computers running Windows, which lock up and display the so-called "blue screen of death" when they receive these packets. But the attack also affects many Macintosh and Unix systems as well.

June 4, 1996 -- Ariane 5 Flight 501. Working code for the Ariane 4 rocket is reused in the Ariane 5, but the Ariane 5's faster engines trigger a bug in an arithmetic routine inside the rocket's flight computer. The error is in the code that converts a 64-bit floating-point number to a 16-bit signed integer. The faster engines cause the 64-bit numbers to be larger in the Ariane 5 than in the Ariane 4, triggering an overflow condition that results in the flight computer crashing.

November 2000 -- National Cancer Institute, Panama City. In a series of accidents, therapy planning software created by Multidata Systems International, a U.S. firm, miscalculates the proper dosage of radiation for patients undergoing radiation therapy.


My personal favorite is the Therac-25. What bonehead let that go without knowning that would happen?

---

### Post by az on 2005-11-08
[QUOTE=KingBahamut]What bonehead let that go without knowning that would happen?[/QUOTE]

Doctor Bruce Banner, of course!  It was part of his quest to harness the medicinal effects of gamma radiation.

But seriously, it would be great if we could come up with our favorite bug reports and submit them to lugradio or something....

---

### Post by welsh_spud on 2005-11-08
I suppose I was too young at the time to pay much attention, but did the Y2K bug acutally do any damage?

---

### Post by 23meg on 2005-11-08
I think the worst ever bug was the Award BIOS's "Keyboard not found - Press F1 to continue".

---

### Post by earobinson on 2005-11-08
lol i posted this to my blog yesterday, was going to post here but i passed out instead

---

### Post by earobinson on 2005-11-08
[QUOTE=welsh_spud]I suppose I was too young at the time to pay much attention, but did the Y2K bug acutally do any damage?[/QUOTE]
lots of code had to be changed but nothing blew up or anything cool like that

ahhh double post

---

### Post by YourSurrogateGod on 2005-11-08
[QUOTE=23meg]I think the worst ever bug was the Award BIOS's "Keyboard not found - Press F1 to continue".[/QUOTE]
*lol*

---

### Post by YourSurrogateGod on 2005-11-08
[QUOTE=KingBahamut]June 4, 1996 -- Ariane 5 Flight 501. Working code for the Ariane 4 rocket is reused in the Ariane 5, but the Ariane 5's faster engines trigger a bug in an arithmetic routine inside the rocket's flight computer. The error is in the code that converts a 64-bit floating-point number to a 16-bit signed integer. The faster engines cause the 64-bit numbers to be larger in the Ariane 5 than in the Ariane 4, triggering an overflow condition that results in the flight computer crashing.[/QUOTE]
This one is my favorite, but then again I remember it well.

---

### Post by YourSurrogateGod on 2005-11-08
When I was still a n00b to C++ programming, I wrote "0++". Boy did I have fun trying to figure out what was wrong. The lesson that I learned was never use the letter "o" as an iterator in for-loops, stick to i, x, y and z.

---

### Post by earobinson on 2005-11-08
lol, oh memory leaks are so much more fun

---

### Post by Lovechild on 2005-11-08
[QUOTE=23meg]I think the worst ever bug was the Award BIOS's "Keyboard not found - Press F1 to continue".[/QUOTE]

I believe the text is "Keyboard error - press F1 to continue", and it's not a bug, it's a strange error message but it's correctly handled, abide a bit unfortunate.

---

### Post by 23meg on 2005-11-08
A code reuse nightmare: an American company developed an air combat training simulator for the Australian Air Force. After a period of testing, the air force demanded the presence of kangaroos in forests to increase realism, since typically they roam the forests in daytime in flocks of hundreds. The company upgraded the software, reusing the code they had created to simulate a certain kind of ground troop for another client, replacing the 3D model with that of a kangaroo. But they had forgotten to take something out: when the Aussie pilots started flying over forests in the upgraded version, they immediately got shot down by hundreds of ground to air missiles fired at them by kangaroos carrying missile launchers.

---

### Post by earobinson on 2005-11-08
lol OO programing at its worst :) If only the company was smart and had made the ai an extention of the simple class.

---

### Post by Omnios on 2005-11-08
A friend told me about winME when it came out. Aperently everytime you tryed to install something you literaly had to go to the MS download site to get a patch including stuff pertaining to some modems and ethernet cards. 
 
 Edit: I ment windows ME. 
         I must refrain from writing for at least an hour when I get up or at least wait till the coffee cuts in.

---

### Post by YourSurrogateGod on 2005-11-08
Worst software bug? Windows 95/98/ME.

---

### Post by Qrk on 2005-11-08
There was an airbus A330 prototype that took off and was going to buzz an airshow, but they kept the landing gear down for saftey. Unfortunatly the plane's onboard computers assumed that it was trying to land again. So the plane initiated an automatic landing sequence right into a forest. Fortunatly it was filled with test equipment, not passengers.

---

### Post by xequence on 2005-11-08
[QUOTE=YourSurrogateGod]Worst software bug? Windows 95/98/ME.[/QUOTE]

I knew someone would say that.

---

### Post by YourSurrogateGod on 2005-11-08
[QUOTE=xequence]I knew someone would say that.[/QUOTE]
It's true.

---

### Post by oddabe19 on 2005-11-09
damn, you beat me to it.

no, the WORSE bug ever....

Microsoft BOB.

*insert drum cue here*

Anyone else actually old enough to remember that besides me?

---

### Post by YourSurrogateGod on 2005-11-09
[QUOTE=oddabe19]damn, you beat me to it.

no, the WORSE bug ever....

Microsoft BOB.

*insert drum cue here*

Anyone else actually old enough to remember that besides me?[/QUOTE]
?

---

### Post by 23meg on 2005-11-09
[QUOTE=YourSurrogateGod]?[/QUOTE]
[http://toastytech.com/guis/bob2.html](http://toastytech.com/guis/bob2.html)

---

### Post by KingBahamut on 2005-11-09
Bob was the last thing that Melinda French, Now Melinda Gates, ever developed for MS.

---

