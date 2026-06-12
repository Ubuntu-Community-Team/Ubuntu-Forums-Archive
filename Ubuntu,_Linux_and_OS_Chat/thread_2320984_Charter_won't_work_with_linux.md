---
title: "Charter won't work with linux"
date: 2016-04-19
forum: Ubuntu, Linux and OS Chat
---

### Post by cmcanulty on 2016-04-19
I jus spent an hour with a charter (idiot) tech who tells me they don't support linux and that's why my connection is slow because charter won't work properly with linux. Where do they get these people and does anyone have a suggestion to get around this? My speed is well below what they say it should be. The installation guy told me it was because the drop line from the road to my house (about 300 feet) is probably the issue. But tech won't let me get to a person to check that as they go back to they don't support linux and that is my problem.

---

### Post by TheFu on 2016-04-19
I used to run into this.  YOU have to know how to give them the data they want. Be assertive, but not rude.  Networking is networking and their lack of knowledge around Linux just means that person cannot tell you, like grandma, what to point-n-click on to get the data.

The CSR isn't an idiot.  They just aren't trained to deal with Linux.  I'm not trained to deal with diesel trucks, but that doesn't mean I can't drive on the highway next to one.  Like road signs, networking is all the same, regardless of which vehicle I'm driving.  Kindness and giving the other person a chance to help will go far.  Ask for their help. If they cannot, call back or say "escalate" to get someone else. In telecom, "I'd like to escalate" is the phrase to get someone else, often a supervisor.  Be clear you don't need help with Linux, just have them tell you the info they need and YOU need to know how to get it for them.  If that is an issue, get those skills BEFORE complaining.

There are at least 10,000 charter customers running Linux just fine, BTW.

---

### Post by unflavored on 2016-04-19
You could ask an acquaintance to let you borrow a spare windows laptop.

---

### Post by cmcanulty on 2016-04-19
I gave them the speed test results and they wouldn't accept that, what else should I give them? Thank you!

---

### Post by TheFu on 2016-04-19
Maybe the cable modem has a s/n page which shows the issue?  Different modems put that at a different place - you'll have to do the research.  
Also, be specific with your expectations.  "Too slow" isn't good enough.

I'm paying for 15/3 and only see 8x1 ... what can be done to solve this?  If the results are within 15% of the paid-for bandwidth, that is protocol overhead.  Writing a letter to the public utility commission would be the next step if they refuse to help.  Putting things onto paper always gets their attention. Be 100% truthful and have documentation to proved there is an issue and have dates, names, times, when you contacted Charter for help, but were refused.

Another trick I found to get a better cable put in, for free, was to sign up for their VoIP service. VoIP requires a better connection than TV or internet, so Comcast always ran a fresh cable.  I'm not 300ft - maybe 40ft, but they always took the long way around the house, and always used a thicker cable.  After the first 30 day free trial, I found their voice solution to be poor and dropped it, but they didn't pull the new cable out.  I was left with a much, much, much better internet connection.  Poor me.

Besides dealing with their phone support, check out their forum on DSL-Reports.  More knowledgeable techs watch that for every ISP and try to help. [https://www.dslreports.com/forum/charter](https://www.dslreports.com/forum/charter)  Good FAQ for the "help us help you" stuff.  Do that stuff. Capture/write down the results.  Data and facts are critical.

---

### Post by cmcanulty on 2016-04-19
thanks I will definitely try that

---

### Post by pqwoerituytrueiwoq on 2016-04-19
check what model you are using, they tend to not update peoples old obsolete modems, unless they have a reason to, eg service upgrade, id guess you have some old docsis 1 or 2 modem, some of these can't preform at current advertised speeds
you can also runs a speedtest on there own website
[IMG]http://i.imgur.com/Dgi46Co.png[/IMG]

be sure to run a test bypassing your router just to be sure (modems lock on to MAC address, so the modem will need a reboot unless you clone your routers external MAC address)

be sure to run the test with a wired connection, wifi speeds drop over distance and commonly can't handle full speed a few rooms away from the source

in my area charter offers speeds starting at 60/4, however i have seen nothing of speeds over that, i know they used offer 100 down, maybe they don't offer anything but 60 now, i have done everything but ask about that
id ballpark the cable that runs to my house to be close to 250ft

---

### Post by TheFu on 2016-04-19
DOCSIS v2 is limited to 38Mbps down.  For higher speeds, a DOCSIS v3 modem is required. I think those are limited by the number of channels the provider will bond (304 Mbps for Comcast). [https://en.wikipedia.org/wiki/DOCSIS#Throughput_2](https://en.wikipedia.org/wiki/DOCSIS#Throughput_2)

If there are performance issues, always use wired ethernet, turn on the linux firewall, and directly connect the Linux machine to the modem (as suggested by pqwoerituytrueiwoq).
Wifi is NOT a good idea for these sorts of tests.

Only 4Mbps up? Ouch.

---

### Post by cmcanulty on 2016-04-20
[ATTACH=CONFIG]268467[/ATTACH]

I have a brand new modem as now charter brings one out when you get new service now and won't let people use their own anymore. Here is my wired speedtest in screenshot. Not bad but if I'm paying for 60mgs it isn't close to 60

---

### Post by TheFu on 2016-04-20
> **cmcanulty said:**
> [ATTACH=CONFIG]268467[/ATTACH]

I have a brand new modem as now charter brings one out when you get new service now and won't let people use their own anymore. Here is my wired speedtest in screenshot. Not bad but if I'm paying for 60mgs it isn't close to 60

Then what is this?
[http://www.charter.net/support/internet/compliant-modems-charter-network/](http://www.charter.net/support/internet/compliant-modems-charter-network/)  
> You may also choose to buy a modem that is certified by Charter to work with your internet service.
 
But if you have additional services, like VoIP, or addon security services, the selection is limited and may not be available to consumers (I hate that word).  If you have business service, with a subnet/multiple static IPs, then Charter might not allow your own device.

---

### Post by cmcanulty on 2016-04-20
I know it depends on your local area, they told me only their "free" modem then they raise the price

---

### Post by howefield on 2016-04-20
Moved to the "*Ubuntu, Linux and OS Chat*" forum.

---

### Post by pqwoerituytrueiwoq on 2016-04-20
> **cmcanulty said:**
> [ATTACH=CONFIG]268467[/ATTACH]

I have a brand new modem as now charter brings one out when you get new service now and won't let people use their own anymore. Here is my wired speedtest in screenshot. Not bad but if I'm paying for 60mgs it isn't close to 60
you can use your own but you are required to have one of theres, but if you have a docsis 2 modem they should upgrade it upon request, my mom has theres in the box it came in and her's in use

---

