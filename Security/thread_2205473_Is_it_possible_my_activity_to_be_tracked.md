---
title: "Is it possible my activity to be tracked"
date: 2014-02-14
forum: Security
---

### Post by danbuz on 2014-02-14
Hi,

I work in IT company, and there is a rumor that high level managers track the activity of the servants. So we use firm's wi-fi connection, and work on WIN, but to synchronize my documents I use my own laptop connected to the same wifi. I'm with ubuntu and I just wonder is there a way managers to watch what I search for,  what I'm doing at all..
 
And is there a way to check if the connection is monitored.

Thanks in advance!

---

### Post by open2reason on 2014-02-14
danbuz,
You may attract attention by your efforts to see if others are tracking you.
Tracking of employees may be permissible depending upon the local laws and may well be deemed acceptable and form part of your contract of employment.
May well be best to assume that you are being tracked and monitored by your employer and act accordingly.

---

### Post by TheFu on 2014-02-14
I've worked at places where monitored everything. They had to - it was a legal liability thing.
If you are on someone elses network, they know all about your traffic. If they have enough resources, they can even see inside HTTPS traffic.

[CENTER]**Don't use work networks for non-work things.**[/CENTER]

Use your cell phone data connection if you can't just stop.  Wifi is easier to track than wired. Doesn't matter if they use WPA2 or RADIUS authentication. It is their network. They can see all the traffic.

The only way that I'd do anything the bosses might not like is by:
* using my non-Windows systems - never theirs.
* using an ssh/OpenVPN connection that uses IP addresses only. Most smart companies block all VPN stuff.
That's it.

TOR is **not** easy to use in a secure manner, though it may be good enough for smaller company networks, if you use your own equipment.

Assume your screen is being captured every 20 seconds and that security can watch live if you use a company-provided box on their network. I've seen this. A security guy watched suspects as they spent 10 hrs at work day trading stocks. He wondered when they actually did their jobs.

For your personal box, they can see all the network traffic, which means that websites you visit will be known if you do not take extra steps. There is good news. If you didn't have to setup a company Certificate to get on their network ( shame on IT for that ), then your HTTPS traffic content is probably safe enough, but they probably have a transparent proxy looking at all other unencrypted traffic. 

In very large enterprises, HTTPS traffic can be spoofed with a combined DNS/proxy setup.  Use HTTPS-everywhere and Certificate Patrol from your home internet connection to store "known good" HTTPS connection before going into work to see if the company gets in the middle or not. Certificate Patrol will tell you if a different Cert than expected is encountered.

---

### Post by raja.genupula on 2014-02-14
If your company not having a good network sys admin who dont know about tor browser , then No Body can watch your web-activity AFAIK.

---

### Post by CharlesA on 2014-02-14
> **TheFu said:**
> 
[CENTER]**Don't use work networks for non-work things.**[/CENTER]
This.
> **raja.genupula said:**
> If your company not having a good network sys admin who dont know about tor browser , then No Body can watch your web-activity AFAIK.

A better solution is not to do personal stuff at work.

---

### Post by Habitual on 2014-02-14
Honesty is doing the right thing when someone is looking.
Integrity is doing the right thing when no one is.

---

### Post by lisati on 2014-02-14
If you're worried about being watched while you're doing your personal stuff at work, you need to ask yourself if you should be doing it. Either get talking with your workplace's admin to find out what's acceptable, or don't do it at all.

---

### Post by CharlesA on 2014-02-14
Most of the places I have worked where you need to use the computers make you sign an acceptable use agreement as far as of the hiring process.

When in doubt ask either IT or HR.

---

### Post by tgalati4 on 2014-02-14
I won't mention any company but I have heard reports that simply plugging in your iphone or Android phone into a work computer to charge it will cause that phone to be completely imaged (copied) onto a company's security server for forensic analysis.  Some employees have lost their job for what was found, that was unrelated to direct job performance.  So, based on this, I would think that anything that is done on a company computer or anything plugged into a company computer is subject to such scrutiny.

---

### Post by Habitual on 2014-02-14
The long and the short of it is, Yes, your activity can be tracked.
If you have to ask yourself "should I be doing this at work?" then you probably shouldn't be doing it.

---

### Post by fugu2 on 2014-02-14
> **tgalati4 said:**
> I won't mention any company but I have heard reports that simply plugging in your iphone or Android phone into a work computer to charge it will cause that phone to be completely imaged (copied) onto a company's security server for forensic analysis.  Some employees have lost their job for what was found, that was unrelated to direct job performance.  So, based on this, I would think that anything that is done on a company computer or anything plugged into a company computer is subject to such scrutiny.

You need to strap the stump, braw!
[http://int3.cc/products/usbcondoms](http://int3.cc/products/usbcondoms)

---

### Post by tgalati4 on 2014-02-15
I remember riding a subway in Boston with a public service poster that looked like a Beneton Ad with three shirtless young men with the tagline:  "Don't forget your Jimmy Hat".  One of them was wearing a wool cap--because, you know,  it gets cold in Boston.  So the message is if it is cold outside and you are shirtless, don't forget your Jimmy Hat.

---

### Post by danbuz on 2014-02-15
The main reason Im concerned is because I kinda work on second place which is competition.. The truth is that both companies know that, I'm just doing my job, but I needed to do things as online banking, using some firm's software that are ok to use only in the first company I work ( and I used it in the second). I have personal data I would not like to expose, but the situation was like this that I should use my PC anyway...

So is there a way they to see personal files, folders or even what kind of software I'm using.. or it is just the browsing data. And is there a way to check if I'm tracked?

---

### Post by Iowan on 2014-02-15
I can see your concern - and exposure. I can see each company claiming to need to need to monitor your computer for malware/spyware from the "other" company. And, to a certain extent, they'd be right.

---

### Post by danbuz on 2014-02-15
> **Iowan said:**
> I can see your concern - and exposure. I can see each company claiming to need to need to monitor your computer for malware/spyware from the "other" company. And, to a certain extent, they'd be right.


I appreciate your thoughts but I need specific answers to the specific questions I asked! Thanks in advance!

---

### Post by Iowan on 2014-02-15
Is there a specific question that hasn't been answered?

---

### Post by danbuz on 2014-02-15
> **Iowan said:**
> Is there a specific question that hasn't been answered?


[COLOR=#000000]So is there a way they to see personal files, folders or even what kind of software I'm using.. or it is just the browsing data. And is there a way to check if I'm tracked?

And if once tracked, Could the continue to track me on my home wifi, or I should change the internet connection?[/COLOR]

---

### Post by bashiergui on 2014-02-15
> **danbuz said:**
> [COLOR=#000000]So is there a way they to see personal files, folders or even what kind of software I'm using.. or it is just the browsing data. And is there a way to check if I'm tracked?

And if once tracked, Could the continue to track me on my home wifi, or I should change the internet connection?[/COLOR]If the company owns the computer you use then assume they can see everything- network traffic, saved files, emails.

If you're using a personal computer to connect to them remotely then assume they can see all your network traffic & emails you send/receive. 

They could do keylogging & screenshot your screen every few seconds if they felt like it, but no company can do that for everyone all the time.

No, there isn't really a tool you can use to see what they see. Yes, they could easily check your OS, software, versions when you connect to their network. It depends on how you connect to their network whether they can see your personal files on your computer.

If you need to do something that you do not want them to see then get off their network. If it's a company-owned computer then yes they could see your history of stuff you did off their network. They are less likely to do that if you own the computer, but they could potentially acquire an image of your computer while you're connected if they were so inclined.

---

### Post by danbuz on 2014-02-16
> **bashiergui said:**
> If the company owns the computer you use then assume they can see everything- network traffic, saved files, emails.

If you're using a personal computer to connect to them remotely then assume they can see all your network traffic & emails you send/receive. 

They could do keylogging & screenshot your screen every few seconds if they felt like it, but no company can do that for everyone all the time.

No, there isn't really a tool you can use to see what they see. Yes, they could easily check your OS, software, versions when you connect to their network. It depends on how you connect to their network whether they can see your personal files on your computer.

If you need to do something that you do not want them to see then get off their network. If it's a company-owned computer then yes they could see your history of stuff you did off their network. They are less likely to do that if you own the computer, but they could potentially acquire an image of your computer while you're connected if they were so inclined.


Very big THANKS for this specific answer. So, now I know they stole something from me and used it for their own purpose. I'm continue investigating and than straight to the lawyers!

---

### Post by TheFu on 2014-02-16
> **danbuz said:**
> Very big THANKS for this specific answer. So, now I know they stole something from me and used it for their own purpose. I'm continue investigating and than straight to the lawyers!

Whoa there cowboy.  YOU put your PC on THEIR network.  THEY OWN the NETWORK and all DATA traveling over it - at least in the USA.  In many states, they also own any field-related work you may do even if on your own equipment and own time. That comes down to the employment contract and state laws, which vary widely by state.  

I my state, they own everything related to my work even if it isn't directly related to my position.  So if I wanted to "keep" my private work private, no way would I ever connect that machine to their network - even from my home over a VPN.  I'd have a different machine, never talk about the work, never show it to anyone from the job, no clients, no customers, and I'd quit my job a few weeks before trying to sell anything related to the new idea.  I've heard of companies signing agreements to let an employee  work on stuff outside of work when the company didn't believe it was interesting in my state.

Other states have very different laws. I think California is more friendly to people working-at-home creating stuff.

**A company has the right - and perhaps the legal mandate - to secure all the devices on their network. ** I think they haven't done anything wrong.

OTOH, you haven't named the company, the country, the province or the industry, so everything in every post above about legal stuff means absolutely NOTHING.  Only a lawyer will be able to provide advice - be certain to get one familiar with IP laws, not just any lawyer. I think you will be surprised, and unhappy, with their response.

---

### Post by bashiergui on 2014-02-16
> **danbuz said:**
> Very big THANKS for this specific answer. So, now I know they stole something from me and used it for their own purpose. I'm continue investigating and than straight to the lawyers!
+1 to TheFu

Also check your employee manual/agreement. It probably states that nothing you do on their network is private.

---

### Post by fugu2 on 2014-02-16
Also keep in mind that search engine results are not private, and can be linked from your private residence to your work place and should not be assumed to be completely seperate. This can lead to leaking corporate data.

---

### Post by open2reason on 2014-02-17
> **danbuz said:**
> Very big THANKS for this specific answer. So, now I know they stole something from me and used it for their own purpose. I'm continue investigating and than straight to the lawyers!

If engaging lawyers the very act of discovery may uncover actions that may not support you case, indeed some may be detrimental to your cause.

---

### Post by mimilovell on 2014-02-21
yes you can be tracked. In our company our managers monitor everything. It is best not to do personal stuff like this at work during work times

---

### Post by eightbits2010 on 2014-02-22
Well, doesn't his apply (tracking) to ALL newwork connections? Including your ISP ? I would be interested in knowing who and when I am being tracked. I know google and facebook seem to share your site's visited.

---

### Post by open2reason on 2014-02-22
In my country ISPs have to by law keep records of sites visited by customers. Telecommunication companies also have to keep records of calls and txts contacted by subscribers.

---

### Post by bashiergui on 2014-02-22
> **eightbits2010 said:**
> Well, doesn't his apply (tracking) to ALL newwork connections? Including your ISP ? I would be interested in knowing who and when I am being tracked. 
That's what Tor and VPNs are for. > **eightbits2010 said:**
> I know google and facebook seem to share your site's visited. Use private browsing and don't click on links when you're logged in to Facebook or Google to avoid that.

---

### Post by CharlesA on 2014-02-22
> **bashiergui said:**
> Use private browsing and don't click on links when you're logged in to Facebook or Google to avoid that.

Could just use Ghostery or the like too.

---

### Post by fugu2 on 2014-02-22
This can help too.
http://winhelp2002.mvps.org/hosts.htm

---

### Post by 1clue on 2014-02-23
Wow.

OK Some of this has already been said here, but for the sake of completeness.  In the USA last I checked:
[LIST=1]
[*]Your employer has the right to any information on any hardware they own.  In other words, keyloggers are legal and legitimate.
[*]Your employer has the right to any information that passes on their network.
[*]Cisco and pretty much every other business/enterprise switch can mirror a port to another port.  Generally this means that every packet entering or leaving their network can be recorded in full or in part, and generally speaking a lot of companies make use of that.  It's their equipment, their account and their data.  They're legally responsible for what goes through their router, so you can pretty much say that they own it.  Legally.
[*]Regarding your equipment on their network, if you send the data across their network then it's their data.  I don't think there's a legal recourse.
[*]The same goes for connecting to the company VPN from outside:  If it goes through their VPN then it's their data.
[*]I pretty much guarantee that the only company that's OK with you using Facebook on company time or with company equipment is Facebook.
[*]If you use search engine plugins on your browser, then probably they transmit data you don't think they transmit.  Any sort of quick search is going to send data as you type it, because they're sending results as you type it.
[*]With https you're still using their DNS which is not encrypted.  They know what site you went to.
[*]With ANYTHING, they know what IP address you went to and what protocol you tried.
[*]Try to think of anything at all that you would do -- legally -- for your company on their equipment that involves TOR.  I'm dying to hear what it might be.
[*]Rights to your work:
[LIST=1]
[*]Contracts vary, and state laws vary.
[*]Sometimes the company claims all intellectual works you created while in their employ.  That includes time you spent at home on your own equipment.  Sometimes this is legal.
[*]Sometimes companies restrict that to the type of business they're in.
[*]Sometimes they restrict it to time on their equipment or while in their building.  Or pretty much anything else.
[*]When you sign the contract for employment, there is a non-compete clause.  Sometimes they claim rights to anything you came up with for a long time after you quit.  These are sometimes shaky unless they can prove you worked on it while in their employ.
[/LIST]
[/LIST]

---

### Post by 1clue on 2014-02-23
Some companies forbid all non-business-related (THEIR business) use of company resources.

Some companies allow or even encourage music or similar.  Some allow news sites or similar when you're on break.

If you have to wonder if something is OK and are afraid to ask, then you already know the answer.

---

### Post by jimmyh1972 on 2014-02-25
[[COLOR=#000000]danbuz[/COLOR]]("http://ubuntuforums.org/member.php?u=1708442")[COLOR=#000000] [/COLOR]

[COLOR=#000000]In order to track you (or any other employs) the sys admin must implement a machine tracker app (or in its pro name a key logger + trojan to capture screen shots,[/COLOR]

[COLOR=#000000]network connections etc. in addition to that he must tap the server or the proxy of the organization.[/COLOR]

[COLOR=#000000]having a simple wifi router wont be enough for that.[/COLOR]

[COLOR=#000000]any way in order to evade any kind of surveillance you need to:
[/COLOR]
1. use your personal laptop - ubuntu OS is much more secured than windows

2. when you browse the web use any kind of VPN (like TOR witch is free or the paid ones like hid my ass etc...)

3. as long as you use VPN the chance to track you is flimsy

for any more information about tracking and tapping you can write to me in private

---

