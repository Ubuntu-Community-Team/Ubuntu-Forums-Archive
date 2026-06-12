---
title: "Successfully Implemented Ubuntu at home. My Office is Next!!!"
date: 2009-01-08
forum: Testimonials &amp; Experiences
---

### Post by subzero.amir on 2009-01-08
I am the facto unofficial IT guy in my office (15 users). I have been asked by management to check linux to use in office as windows seems to give them security headaches and worries.

So, without having ANY experience with Linux AT ALL, I dived in and wiped my windows laptop and installed ubuntu.

Played with it and LOVED it. found a few glitches but that is normal. Screwed something up, and i came to this forum for help. Within 20 minutes help arrived and solved the problem. So I used my wife's home desktop and my kids computer as lab rats to test.

Everything works smoothly!!!!! networking and other stuff go without a problem!!!!!!!!

Next....i will takeon my office computer. Hope it goes well............

---

### Post by steveneddy on 2009-01-08
Good Luck!

We're all counting on you.....

---

### Post by wolfen69 on 2009-01-08
i wish you all the luck in the world with that. although i would go with debian in an office environment. debian is not cutting edge, but is rock solid stable.

---

### Post by halovivek on 2009-01-09
Really happy to hear this. Like you people if you introduce in the office with proper security in linux. every one will follow and linux can gain the market share and monopoly will come to end one day.

---

### Post by hyper_ch on 2009-01-09
if you don't use any proprietary system that only works on windows then you should be fine. Good luck :)

---

### Post by subzero.amir on 2009-01-17
Just to update...
Pheeeww.... finally installed ibex on 2 office computers. Both users are happy, especially with the interface. Waited for about a week to gauge their happiness level and still up... Many questions asked, and a bit of confusions but everything sorted out. 

Both asked where is my firewall and where is the anti-virus.

I happily answered u don't need 'em no more....

The only thing upset them is Yahoo messenger. Up to now, still can't find any software that can match the power of YM.

Myself use pidgin and gyachi, but gyachi is so ugly, and pidgin doesnt do voice/video.

All in all, i would say that average users are quite ready for Ubuntu.

Cheers,

---

### Post by solwic on 2009-01-17
> **subzero.amir said:**
> Just to update...
Pheeeww.... finally installed ibex on 2 office computers. Both users are happy, especially with the interface. Waited for about a week to gauge their happiness level and still up... Many questions asked, and a bit of confusions but everything sorted out. 

Both asked where is my firewall and where is the anti-virus.

I happily answered u don't need 'em no more....

The only thing upset them is Yahoo messenger. Up to now, still can't find any software that can match the power of YM.

Myself use pidgin and gyachi, but gyachi is so ugly, and pidgin doesnt do voice/video.

All in all, i would say that average users are quite ready for Ubuntu.

Cheers,

Actually you do have a firewall.  It's called iptables, and you get get a GUI for it by typing, in terminal:

```
sudo apt-get install firestarter
```

It'll run a very simple set up, and then give you options for permissive or restrictive filtering, and even let you set up port mapping and ip recognition and filtering. 

It's pretty wild.  :)

But no...the AV thing is out, thankfully.  Frees up a bunch of system resources.  :)

---

### Post by hyper_ch on 2009-01-17
DO NOT INSTALL FIRESTARTER!

It will alter the default rules on iptables!

In most cases, as you are very likely behind a router, you don't need to mess at all with iptables!

---

### Post by billgoldberg on 2009-01-17
> **hyper_ch said:**
> DO NOT INSTALL FIRESTARTER!

It will alter the default rules on iptables!

In most cases, as you are very likely behind a router, you don't need to mess at all with iptables!


Indeed, there is no reason a normal user behind a modem should be messing with iptables.

There are set up just fine ootb.

-

If you do need to change them, use ufw (or gufw if you need a gui). Firestarter is obsolete.

---

### Post by solwic on 2009-01-17
> **hyper_ch said:**
> DO NOT INSTALL FIRESTARTER!

It will alter the default rules on iptables!

In most cases, as you are very likely behind a router, you don't need to mess at all with iptables!

Whatever you like.  I don't use it, personally.  Not anymore, anyway.  

Again, whatever you like.  :)

---

### Post by onero on 2009-01-17
> **jrock612 said:**
> Whatever you like.  I don't use it, personally.  Not anymore, anyway.  

Again, whatever you like.  :)


I use gufw. It's just a GUI for ufw (uncomplicated firewall), which is installed in Ubuntu by default.

---

### Post by glotz on 2009-01-17
> **subzero.amir said:**
> The only thing upset them is Yahoo messenger. Up to now, still can't find any software that can match the power of YM.

Myself use pidgin and gyachi, but gyachi is so ugly, and pidgin doesnt do voice/video.

All in all, i would say that average users are quite ready for Ubuntu.
Great hearing about your success!

Perhaps [Ekiga]("http://ekiga.org/") would serve?

I wholeheartedly agree with your view on GNU/Linux desktop readiness.

---

### Post by zero244 on 2009-01-18
As far as Yahoo Messenger I use Pidgin, which I like better than any of the Windows IM's
And it comes preinstalled on Hardy.

---

### Post by subzero.amir on 2009-01-18
> **zero244 said:**
> As far as Yahoo Messenger I use Pidgin, which I like better than any of the Windows IM's
And it comes preinstalled on Hardy.

True. I like pidgin's clean look. But I need vid and voice. I read somewhere in this forum that pidgin is very close to releasing a new version that support vid/voice. Keeping my fingers crossed.

Meanwhile, thanks to everybody in this thread for your support and advice. (I am not gonna mess with the iptable. I am happy with the way things go).

Cheers.

---

### Post by waspbr on 2009-01-18
have you tried amsn? it if I am not mistaken it does have video support, you might wanna check it out, I reckon it is in the repos but you can also try getdeb.net (though it is down atm  [to me])

---

### Post by russu52 on 2009-01-18
congrats on your turning to ubuntu. i have done the same step 2 wks ago - from vista on an acer aspire 5720, supposedly built for vista, but jams at everything and most of my peripherals - scanner, graphics tablet, mp3 player and pda were unrecognised by vista. With Ibex everything is running smoothly. cheers

---

### Post by phantom@atom-desk on 2009-01-18
I installed Ubuntu Hardy on My new Lenovo Ideacenter Desktop (LENOVO RECOMMENDS VISTA):( some four months ago. Later i Came to know that the graphics card provided was not supported (SIS 671). I tried Ibex but it was working with my graphics properly so sticking to 2D graphics in ubuntu Hardy work-around provided on this forum. I am loving Ubuntu every minut i Am using it more and more. Though it's a bit difficult for new user, But so is windows (for a new user). Now i am pursuading my friends towards Intrepid or Hardy

---

### Post by subzero.amir on 2009-01-18
> **waspbr said:**
> have you tried amsn? it if I am not mistaken it does have video support, you might wanna check it out, I reckon it is in the repos but you can also try getdeb.net (though it is down atm  [to me])

Yes I did and it is a great piece of software. But it doesn't do yahoo and gmail account.

---

### Post by loell on 2009-01-19
you can change gyache's default icon theme.

---

### Post by subzero.amir on 2009-01-20
*&#@, I accidentally and stupidly removed gnome-dekstop from my own laptop yesterday. I still can boot and go to its GUI, but there is nothing there. No panel, nothing. (Mouse and network still works)

So i ctrl+alt+2 to try to apt-get install gnome-dekstop, and the wlan is working, but I had a second thought.

I have been installing and uninstalling many many many apps, like gyachi, amsn, all the javas and flashes, etherape, grSync and many more.

I don't like to install apps that I don't use, and now that I have been using Ubuntu for a few months and I kind of know which apps I like and which apps suits me, again, I wiped everything and install Ibex.

I have install Ibex for abt 5-6 times, and everytime I am still amazed by the speed, robustness, and ease. All took less that 25 minutes. (Of course, to customize the desktop to the setting I like took longer). 

But the point is why does Microsoft with all the money and resources can't do what Ibex can?

Amazing.... 

BTW, no drivers installation needed, all provided by the mighty Ibex.

---

### Post by wolfen69 on 2009-01-20
> **subzero.amir said:**
> But I need vid and voice. I read somewhere in this forum that pidgin is very close to releasing a new version that support vid/voice.

i have heard that kopete has support for vid/voice.

---

### Post by ugm6hr on 2009-01-20
> **subzero.amir said:**
> Amazing.... 

Glad it's going so well :)  Hopefully your work colleagues agree.

PS: Why do you need Yahoo IM for an office installation?

---

### Post by forkandles on 2009-01-20
subzero.amir,

How refreshing to get some really positive news (from a former Windows user) about Linux instead of people whingeing about some problem or another that Windows doesn't have and therefore Linux needs redesigning.
Good for you.
I am sure that your co-workers will appreciate your efforts in giving them Ubuntu 8.10, especially when YET ANOTHER virus/bug/worm has recently bitten millions of Windows users.
Carry on the good work and introduce as many people as possible to the merits of Linux/Ubuntu.

---

### Post by subzero.amir on 2009-01-20
Thanks, and now the 2 coworkers are a regular browser of this forum. Mostly thay are looking at customization page.

---

### Post by subzero.amir on 2009-01-20
> **wolfen69 said:**
> i have heard that kopete has support for vid/voice.

I did install Kopete. Never been able to get it to work and I gave up...

---

### Post by subzero.amir on 2009-01-20
> **ugm6hr said:**
> 

PS: Why do you need Yahoo IM for an office installation?

We sometimes use it to call overseas and long distance. The rates in my country is very expensive.

---

### Post by trixman on 2009-01-20
> **subzero.amir said:**
> I am the facto unofficial IT guy in my office (15 users). I have been asked by management to check linux to use in office as windows seems to give them security headaches and worries.

So, without having ANY experience with Linux AT ALL, I dived in and wiped my windows laptop and installed ubuntu.

Played with it and LOVED it. found a few glitches but that is normal. Screwed something up, and i came to this forum for help. Within 20 minutes help arrived and solved the problem. So I used my wife's home desktop and my kids computer as lab rats to test.

Everything works smoothly!!!!! networking and other stuff go without a problem!!!!!!!!

Next....i will takeon my office computer. Hope it goes well............good choice by switching to Linux Ubuntu & enjoy your pc again:KS

---

### Post by ugm6hr on 2009-01-21
> **subzero.amir said:**
> We sometimes use it to call overseas and long distance. The rates in my country is very expensive.

Pidgin does not have a SIP function (i.e. long-distance calling).

Consider using Skype or Ekiga for this:
[Skype]("http://skype.com") has a good reputation for sound quality (and value).
Ekiga comes as default with Ubuntu, so is easy to use.  You will need to get a SIP account from somewhere that allows VOIP-to-landline calls - I have previously used [sipgate]("http://www.sipgate.co.uk/") with the Ekiga software.

---

### Post by bgerlich on 2009-01-21
Plus Ekiga works with freecall.com, the cheapest calling service there is, freecall.com quality is sometimes lacking through

---

### Post by subzero.amir on 2009-01-21
just installed skype. works well and sound quality is better than YM.
Apparently our counterpart overseas also uses skype.
Thanks....

---

### Post by ugm6hr on 2009-01-21
> **subzero.amir said:**
> Apparently our counterpart overseas also uses skype.
Thanks....

Ask and you will receive :)

Glad it's been such a success!

---

