---
title: "i hate it when a web site assumes ..."
date: 2019-09-03
forum: The Cafe
---

### Post by Skaperen on 2019-09-03
i hate it when a web site assumes that the source IP address can be used to determine what country someone is in and blocks access on that basis.  all the IP address can readily show, if it is an ISP, is what country the ISP is in, not the users.

---

### Post by uRock on 2019-09-04
> **Skaperen said:**
> i hate it when a web site assumes that the source IP address can be used to determine what country someone is in and blocks access on that basis.  all the IP address can readily show, if it is an ISP, is what country the ISP is in, not the users.

If the ISPs are registering their subnets properly, then your IP should be very close to your physical location, unless using VPN, frame relay, or something of the like.

---

### Post by TheFu on 2019-09-05
> **Skaperen said:**
> i hate it when a web site assumes that the source IP address can be used to determine what country someone is in and blocks access on that basis.  all the IP address can readily show, if it is an ISP, is what country the ISP is in, not the users.

It is a legal requirement in some jurisdictions. Complain to the govt.  I hate that I have to accept terms when visiting sites located in the EU which have nothing to do with my legal location.

There are also contractual reasons, so the website has a contractual requirement to block users from certain countries using the best available method.  

There's something called "industry standard" which gets most companies making a mistake from being sued, provided they follow "industry standard practices." If they didn't and make a mistake, they will be sued.

---

### Post by Skaperen on 2019-09-05
not all ISPs are big enough to justify a separate IP allocation of the minimum required size in every country they serve, at least in IPv4.

---

### Post by SeijiSensei on 2019-09-06
I don't know of many multinational ISPs myself. Looking at a list of [ISPs serving Wheeling]("https://www.highspeedinternet.com/wv/wheeling"), only the satellite providers like Hughes might cross international borders.

[Geolocation]("https://www.whatismyip.com/my-ip-information/") for my Verizon Fios IP puts me in Cambridge, MA, rather than my actual location of Newton, but it's only off by a couple of miles.

---

### Post by Skaperen on 2019-09-06
try VPS services.  find the cheapest one that doesn't do any logging.  put your fixed proxy there.  now, where are you?

---

### Post by Skaperen on 2019-09-06
and that list doesn't even have any of the locally headquartered providers.

---

### Post by SeijiSensei on 2019-09-06
> **Skaperen said:**
> try VPS services.  find the cheapest one that doesn't do any logging.  put your fixed proxy there.  now, where are you?
Well, sure. If you use a virtual private network provider you're going to appear to be located at the provider's endpoint. Isn't that why people use VPNs in the first place?

[NordVPN]("https://nordvpn.com/blog/dedicated-ips-in-united-states-and-united-kingdom/") appears to let you designate the country you want your traffic to appear to be from.

---

### Post by Skaperen on 2019-09-06
i did set up a VPN through my VPS server to get IPv6.  IPv4 is also routed but i guess i can unroute it.  all this because web sites don't understand that an IP address only tells them where their ISP is.  one exception is Google.  they know where i am despite the IP address, whether IPv4 or IPv6.  that's one of the few i want to hide from.

---

### Post by TheFu on 2019-09-06
> **SeijiSensei said:**
> I don't know of many multinational ISPs myself. Looking at a list of [ISPs serving Wheeling]("https://www.highspeedinternet.com/wv/wheeling"), only the satellite providers like Hughes might cross international borders.

Perhaps Skaperen isn't in the USA and lives in a border city.

---

### Post by VMC on 2019-09-06
> **TheFu said:**
> Perhaps Skaperen isn't in the USA and lives in a border city.
[https://www.google.com/search?q=Wheeling+WV+USA&oq=Wheeling+WV+USA&aqs=chrome..69i57&sourceid=chrome&ie=UTF-8](https://www.google.com/search?q=Wheeling+WV+USA&oq=Wheeling+WV+USA&aqs=chrome..69i57&sourceid=chrome&ie=UTF-8)

---

### Post by sdsurfer on 2019-09-09
Worse yet is when you tell your marketing team their Big Idea to use geolocation to market to target areas by IP won't work, and why it won't work, they push you to code it that way anyway, then come back a week later complaining the store in Wazoo, Indiana is reporting that their web site says they're in Scottsdale, Arizona. I TRIED TO TELL YOU! LOL

---

### Post by TheFu on 2019-09-09
> **sdsurfer said:**
> Worse yet is when you tell your marketing team their Big Idea to use geolocation to market to target areas by IP won't work, and why it won't work, they push you to code it that way anyway, then come back a week later complaining the store in Wazoo, Indiana is reporting that their web site says they're in Scottsdale, Arizona. I TRIED TO TELL YOU! LOL

> 
Accuracy of geolocation database varies depending on which database you use. For IP-to-country database, some vendors claim to offer 98% to 99% accuracy although typical Ip2Country database accuracy is more like 95%. For IP-to-Region (or City), accracy range anywhere from 50% to 75% if neighboring cities are treated as correct. Considering that there is no official source of IP-to-Region information, 50+% accuracy is pretty good. 
That is a direct quote from 1 of the IP-geolocation sites, including the misspellings, BTW.
If I lived in Windsor, CA, I wouldn't be surprised if Detroit, USA showed up.

My IP at any time can be reported less than a mile off or thousands of miles off.  Google freaks out. If locations by geo-guessing change too quickly. Google will refuse to work - sending people like me into a recursive captcha that can't be solved.
Right now, using my real public, static, IP, whatsmyip is showing a town about 30 miles from reality with the wrong city.  Whatismyip is closer, but shows the wrong ISP.  How can you get the wrong ISP?  I don't live inside any city - up here in Squidbillyland, but if you know anything about Squidbillies, you can get pretty close - give us a holler.  ;)

---

### Post by Shibblet on 2019-09-09
This may not be the right thread to ask this in, but...

I constantly get emails from Linkedin, telling me that I have been highlighted in profiles, and resumes, and the like.  And I have NEVER logged into LinkedIn once in my life.  These emails are pretty specific with phone numbers, personal information, and, of course, they have my email address.

How is this even close to okay?  If I go onto Linkedin, and just start naming people, all of a sudden, they are Linkedin members?

---

### Post by uRock on 2019-09-09
> **Shibblet said:**
> This may not be the right thread to ask this in, but...

I constantly get emails from Linkedin, telling me that I have been highlighted in profiles, and resumes, and the like.  And I have NEVER logged into LinkedIn once in my life.  These emails are pretty specific with phone numbers, personal information, and, of course, they have my email address.

How is this even close to okay?  If I go onto Linkedin, and just start naming people, all of a sudden, they are Linkedin members?

That's madness!  I closed my account because I saw names of people I had removed from my life show up as visitors to my page. Funny enough, within 3 days at work my employer's HR called me in to ask why I closed my account. Apparently they have an algorithm that watches LinkedIn for employee's changes.

---

### Post by Shibblet on 2019-09-10
> **uRock said:**
> That's madness!  I closed my account because I saw names of people I had removed from my life show up as visitors to my page. Funny enough, within 3 days at work my employer's HR called me in to ask why I closed my account. Apparently they have an algorithm that watches LinkedIn for employee's changes.

Right?  Apparently, they take information from everyone's resume and friends.  If you are listed as a professional reference on someone's resume (which I am), they build a profile for you.

I've heard people say it before.  Privacy is an illusion.  It's absolutely impossible to keep your personal information private these days.

---

