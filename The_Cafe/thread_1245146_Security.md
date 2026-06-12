---
title: "Security?"
date: 2009-08-20
forum: The Cafe
---

### Post by oxf on 2009-08-20
I'm posting this as a result of a long discussion that I had with someone yesterday. 

To cut a long story short most (but not all) of my on line connecting is via extended wireless link. I have, like all the rest of the faculty/students, wifi access into the campus system, i.e. I can sit with my laptop anywhere in range, library, cafe, plaza etc etc and log in and be online to my hearts content. 

About 1KM from me is a small extension unit and some residences associated with the main campus. This has Wifi access into the main system as well. My residence is line of site the other side of a small deep valley. I reasoned that with enough antenna gain I could connect into it. I have some basic experience in RF design and construction and set about the task. After some initial teething problems I achieved my goal with a high gain helical antenna. Ironically its better in winter when theres no leaves on the trees. However, it pretty reliable now I removed some branches of a tree next to my house. Only when its wet and windy does the signal strengh get reduced slightly. 

To return to the main point. When I talked about this with my friend over coffee he said I was taking a huge security risk. I explained that the beam width of this antenna is --extremely-- narrow (like I have to have it rigidly clamped so the wind does not vibrate it off alignment). Still he was unconvinced. I view this essentially as a large WiFi router, just that its a ways off. The security in place on the campus system is from what I understand pretty tight. Then theres the security on my system. 

But I would be interested to hear any perpectives or thoughts any of you may have on this. All of this of course refers connecting in using Linux.

Thanks

---

### Post by gn2 on 2009-08-20
If the long range communication to the access point is adequately protected by encryption, the range and width of the beam is completely irrelevant.

---

### Post by mcduck on 2009-08-20
It's not any different from normal wireless connection. The security problem, if any, would be in the University's end. Definitely not on your machine. :)

---

### Post by stwschool on 2009-08-20
Wi-fi is wi-fi, however it's done. Odds are it's still susceptible to the typical problems of wi-fi (ie WPA and WEP are both crackable with tools like aircrack such that someone could then packet-sniff and engage in man-in-the-middle attacks). I'd suggest the main security risk lies thus not in your computer, or at the campus, but rather in the transfer of data over wi-fi.

---

### Post by 3rdalbum on 2009-08-20
I agree with the earlier posters - you are not creating a security problem by erecting this antenna. The distance you are using the connection over does not help an attacker in any way, because you've already proven that it's possible to access the network across a long distance anyway. Any interested hacker will have a Pringles can or a Woktenna already pointed in that direction.

---

### Post by oxf on 2009-08-21
> **3rdalbum said:**
> I agree with the earlier posters - you are not creating a security problem by erecting this antenna. The distance you are using the connection over does not help an attacker in any way, because you've already proven that it's possible to access the network across a long distance anyway. Any interested hacker will have a Pringles can or a Woktenna already pointed in that direction.

Thanks all. Thats reasuring and pretty much what I thought before I had this conversation.
BTW way the helical I constructed has (in theory) considerably more gain than a cantenna

---

### Post by Johnsie on 2009-08-21
Anything you do on the Internet is hackable. It's better just to assume that your computer is vulnerable before you even use the Internet.

Obviously there are ways to be more careful and using a log range wi-fi connection is less secure than fixed line or a short distance wifi, simply because it makes the catchment area for possible hacker higher. 

The biggest risk isn't the wifi though, it's the software you use and what you do online that most people wlll target.

---

### Post by running_rabbit07 on 2009-08-21
Manufacturers of equipment underthe 802.16 Wireless standard are claiming a range of up to 30 miles.

Just thought I'd throw that out there. 

As long as WPA2 is implemented with a good 128-bit key then all should be fine.

---

