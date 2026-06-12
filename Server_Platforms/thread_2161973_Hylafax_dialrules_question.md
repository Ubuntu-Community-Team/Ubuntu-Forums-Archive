---
title: "Hylafax dialrules question"
date: 2013-07-12
forum: Server Platforms
---

### Post by 2WheelPenguin on 2013-07-12
Searched all over, amazed this one hasn't already been answered on the Hylafax mailing lists at some point, but there's just nothing out there.
How do you configure Hylafax dialrules to strip the 1 for a second area code?
In other words, you have a modem, its area code is 123, but say the phone line treats phone calls to area code 321 as a local call, won't work with 1 in front of the number.
How do I tell the dialrules NOT to add the 1 in front of anything that starts with 321 for an area code?
All the info currently out there is about how to add the 1 prefix, not remove the 1 prefix.

TIA

---

### Post by volkswagner on 2013-07-13
I'm not a programmer, but I feel your pain.  I have worked in Connecticut, which has the worst carrier dialing rules I've ever encountered.

Have you seen the [man pages for dial rules]("http://www.hylafax.org/content/Man_Pages_6.0.5")?

Again, as a non programmer it seems all the info is there.  I just don't know the specific answer.
I believe you should be able to create some of your own variables which include your local numbers not allowing a 1, then in the dial
rules replace those with the digits you want.  You would need to be able to create the regular expressions to match potential dialed numbers
which need to have the 1 or 1+areaCode stripped.

Just FYI, I don't believe there are any valid US area codes starting with 1.

---

### Post by 2WheelPenguin on 2013-07-17
yeah, all the dial rules involve adding something based on prefixes, or removing an area code.  I want to leave the area code, just get rid of the unnecessary '1' long distance digit in front of it.  I'm still really surprised this hasn't been covered before with all the HylaFax information that's out there.  Sometimes the simplest things become the most difficult.

---

### Post by vancejo on 2013-09-08
I don't mean to dig up old posts, but did you find your answser? If I am reading you correctly your answser is here... [http://netcodger.wordpress.com/2012/03/28/hylafax-dialrules-and-the-north-american-phone-system/](http://netcodger.wordpress.com/2012/03/28/hylafax-dialrules-and-the-north-american-phone-system/)

---

