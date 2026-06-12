---
title: "Apache2 - Can access website from PC but not mobile phone..."
date: 2008-02-18
forum: Server Platforms
---

### Post by RudolfMDLT on 2008-02-18
Hi there,

I'm using a small little page to keep my class posted on what's happening in and around the school. I can access the website from a PC but not from any of  the mobile phones using the phone's GPRS/3G/EDGE connection? I used to be able to do this, but after the weekend I've lost this ability. All that I've done is install lynx in the server.

The website is [http://rudolfmdlt.is-a-geek.org](http://rudolfmdlt.is-a-geek.org). and the page specifically for the phones is  [http://rudolfmdlt.is-a-geek.org/bme/bmem](http://rudolfmdlt.is-a-geek.org/bme/bmem) .

I keep getting a "connection timed out" error? but when using an SSH client off my cell phone I can connect to the server.

Please help me!!! This is a little embarrassing! LOL ;)

Thanks of any advice,

Rudolf

PS: The URL is a DynDNS URL.

---

### Post by p_quarles on 2008-02-19
My phone was able to load the page, but it only displayed one word of text ("calculus"). This is an older phone, using a very basic browser. 

So, I decided to look at the code, and I think that may be the problem:
[W3C Validation results](http://validator.w3.org/check?verbose=1&uri=http%3A%2F%2Frudolfmdlt.is-a-geek.org%2Fbme%2Fbmem)
It's missing all sorts of data and tag closes.

---

### Post by MJN on 2008-02-19
It works fine on my phone (SVP M600 running WM5 with Pocket IE), not that that helps much!
 
Can you view the 'non-phone' page on the phones? Given you're using frames you might want to try a specific frame (e.g. [http://rudolfmdlt.is-a-geek.org/main.html](http://rudolfmdlt.is-a-geek.org/main.html))
 
As p_quarles says certainly sort of the code out, even if you do get it working! ;)
 
Mathew

---

### Post by RudolfMDLT on 2008-02-19
:oops: Sorry about the crummy code - As I have to edit this page from a SSH client on my phone I really needed to keep the code to the bare basics! But yeah, if it is necessary I'll definitely make it "standardized".  

I did some of my own testing and it seems to work and then not... :confused:

Is there anyway to setup a watch on whether the URL stays up? Maybe my ADSL router may be acting up, it runs it's own internal dynDNS client. Something like a "tracepath" that runs every X minutes? Or if that's too crude - any advice, I'm not too sure what to look for? 

Thank you very much for that validator link! Thats very useful. For someone like me that just hacks away at some html code, that should help sort out some of the noob associated troubles. 

Thank you guys very much for your time! 

Thanks,

Rudolf

PS: I just looked at my code and the validator.... it seems to have picked up a lot of "false" faults? Anyway - it does have a point about the stuff that I left out in the header.

@MJN - I had a look at your website and found the SiteUptime link! Thanks! :)

---

### Post by RudolfMDLT on 2008-02-20
No luck.

ALL computers from ANYWHERE can see my URL and download the page. But cell phones still won't....

I can access the Webmin login screen on port 10000 from my cell phone but not my own damn webpage!? I get a connection timed out error? Can some one please help me sort this out?

Thanks,

Rudolf

---

### Post by MJN on 2008-02-20
Have you attempted connecting/downloading one of your 'normal' pages from your phone? (e.g. the frame URL quoted above)
 
Mathew

---

### Post by p_quarles on 2008-02-20
I don't know if the code got somehow corrupted on the upload, but here's the mobile page:
[HTML]<html>
<head><title>BME Mobile Notice Board</title></head><body bgcolor="#000000" text="#EADE00" link="#18169E" vlink="#5b5a9e" alink="#ff0000"><b> <font size = "+1">BME <font color="#1E90FF"><u>Mobile</u> </font><br><b> <font size = "-1">
Last Update: 2008.02.19.18.30 </font> </b><p>

<li>Main page updated - Please have look<p>

<li><font color="red"> Calculus: </font> Do you have a problem with how the bloke lectures? I have had some complaints from the electrical side...
<br>Dr. Love is taking us for the next couple of days - she's really good! Any opinions on Alex taking as for Calculus AND Algebra?
<p>
<li>Physics labs start on the 20th Feb! Check your groups!
<p>
<li> CodeBlocks on Vista Solution on main page... 

<p>
<li>Vanschaik Drirect Sales in capetown: Tel: 021 918-8410 <br>
Title: How To Program C++ 6th or 5th Edition; 
Author: Deitel; 
Publisher: Pearson <br> 
5th Edition ISBN:1-13-185757-6 <br>
5th Edition New ISBN: 978013185757 <br>
Sorry about the 2 ISBN's but the one on the book and the one
on the web differ. See what you can do. An ISBN???? International Standard Book Number, the new standard is 13 digits
</body>
</html>[/HTML]
There's no doctype, none of the paragraphs are closed (among other style tags), and there's a close-font tag that was never opened. Cell phone browsers are much more touchy than Opera, Firefox or IE. Given the number of serious problems with the code on this page, it doesn't surprise me at all that the phone browsers are timing out. They probably can't figure out what they're looking at. 

Anyway, fix up the code, and if that doesn't make a difference, then and not until then would it make sense to look for something else.

---

### Post by RudolfMDLT on 2008-02-20
> Tentatively passed validation, 1 warning(s)
[http://validator.w3.org/check?uri=http%3A%2F%2Frudolfmdlt.is-a-geek.org%2Fbme%2Fbmem](http://validator.w3.org/check?uri=http%3A%2F%2Frudolfmdlt.is-a-geek.org%2Fbme%2Fbmem)

I didn't put in the UTF encoding as BlueFish HTML editor removes it every time i type it in.

Anyway, I still get the Time Out error. And just now it works again....

Sorry about the font and formatting code errors - I learned html from a 20 page book about 6 or 7 years ago. Seemed that stuff worked then and as stuff worked well enough in FireFox and mostly on the phones I never really bothered. 

Anyway, thanks for your time - Any ideas on what to do with this connection time out error?

---

### Post by MJN on 2008-02-20
Well, I've asked you twice to try something but have yet to receive a reply either way so I can't really help you further beyond that.
 
Given there is an issue with your HTML coding, which may or may not be the cause of the problem, then you really need to eliminate this is a potential cause by testing mobile access to other pages - particularly 'simple' pages with very little markup.
 
Mathew

---

### Post by RudolfMDLT on 2008-02-21
I have and they work. Google loads fine, and when my website wants to, it loads fine as well. WebMIN on the same URL, also loads fine every time, SSH on the same url also works fine. 

This website loads EVERYTIME from a PC, but the cell phones some times won't load it. :confused: Does this actually make sense?

I can blame the cellphone service providers as they have been known to be temperamental. Sometimes Google/other URL's won't load, but those are really rare cases.

If this sounds like "bullsh.." to you, please say so and we'll call it an end. I feel rally bad about this goose chase, but I was/am desperate for a solution. If you think Ubuntu/Apache/DynDNS aren't to blame I'll go hunt somewhere else for a solution.

Thanks again for your time,

Rudolf

---

### Post by MJN on 2008-02-21
Not bull... just confusing!

You didn't confirm you'd had success accessing your 'non-phone' pages on the phone and so I had to assume you hadn't tried.

Now that I know you have then the only variables left are i) your terrible HTML code (it has to be stated this strongly given it's looking like it might be to blame), ii) a problem with your phone/provider (as I can view the page fine on mine, every time),  or iii) some other factor that's yet to be touched on.

Given that the only common factor that causes failures regularly is your 'mobile' page (with the poor code) then you really owe it to yourself, not the mention the rest of us trying to debug this with you!, to sort it out.

How we can continue to help I'm not sure... although I'd like to!

Mathew

---

### Post by RudolfMDLT on 2008-02-22
But the code isn't THAT terrible, it passes the test of the W3 validator.

Anyway - I'll go hunting and see what I can find. 

Thanks for your help!

---

### Post by MJN on 2008-02-22
It was missing header info when I last looked - this can be very important to some browsers, particularly those on non-mainstream platforms.
 
Mathew

---

### Post by RudolfMDLT on 2008-02-24
The only missing header info is the the encoding info. But when I put this in, my HTML editor(BlueFish) removes the encoding tag? 

Anyway - When the phones can find the website they load it fine. The errors we are getting are "time out" errors. Which make want to blame the phone's GPRS connection. 

But my SSH client works 99% of the time and also the webmin page loads 99%, but the BME page only about 40% of the time. 

Interesting is the fact that when using a WAP connection the BME pages loads 99% of the time. Only when relying on GPRS/More advanced connections do we have problems with the BME page?

---

### Post by MJN on 2008-02-24
I wonder if your service provider implements an intercepting proxy server for HTTP connections? If this is somehow struggling with your 'mobile' pages (and not your usual stuff) then perhaps it is this that's finding some issue with them. This would also fit with your other protocols not being affected.

Run a packet sniffer (e.g. Ethereal) on your serverand check the incoming client address and HTTP headers to see if your phone is connecting direct.

It's clutching at straws but there really isn't all that much more to go on.

Mathew

---

### Post by RudolfMDLT on 2008-02-24
> **MJN said:**
> 
It's clutching at straws but there really isn't all that much more to go on.


You've got that right! :)

I'll try that as soon as I can spare the time and report back! Is there anyway to check on what IP or MAC an incoming SSH connections is made on, on the server side without relying on a protocol analyzer or packet sniffer? In that way I can see whether the SSH Address matches the HTTP Address? or do I have things wrong?

Thank you,

Rudolf

---

### Post by MJN on 2008-02-24
Sure - your /var/log/auth.log will show it.

SSH isn't proxyable (other than a man-in-the-middle attack!) and so this would be a good test.

There are various 'Show my IP'-style websites out there to tell you what IP you are connecting from and I'm sure I've seen some that analyse the headers to guess if you are being proxied so have a Google around for some.

Mathew

---

