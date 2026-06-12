---
title: "Bogus virus checking"
date: 2011-04-11
forum: Security
---

### Post by Total Noob on 2011-04-11
10.10.

How do I stop the bogus Windows "Security Threat Analysis" scam that redirects my browser and interferes with many of my google image results?

Thanks.

---

### Post by tgalati4 on 2011-04-11
adblock and noscript plug-ins in firefox.  For Windows, I have found bitdefender to clean up the mess.  Of course, boot with an Ubuntu LiveCD, install bitdefender while in the live session then clean the Windows drive.

---

### Post by Dutch70 on 2011-04-11
You must be talking about windows, right? 

Sounds like rogue spyware & should be taken seriously. 
If you don't have any luck with tgalati4's advice.

This site has a lot of tutorials, and personalized help, ...eventually.
[[COLOR="RoyalBlue"]http://www.bleepingcomputer.com/[/COLOR]]("http://www.bleepingcomputer.com/")

---

### Post by Total Noob on 2011-04-12
> **Dutch70 said:**
> You must be talking about windows, right? 

Sounds like rogue spyware & should be taken seriously. 
If you don't have any luck with tgalati4's advice.

This site has a lot of tutorials, and personalized help, ...eventually.
[[COLOR="RoyalBlue"]http://www.bleepingcomputer.com/[/COLOR]]("http://www.bleepingcomputer.com/")

Thanks.

Both Linux and Windows affected by intermittent interruptions for "Windows Security Threat Analysis."

But after adding the addons, I am still plagued by [url]http://www.storefeedbackrewards.com/ which is offering a bogus Walmart coupon, an iPod and other stuff in exchange for personal info, and by scanfreeantivxp.com, which loads up the "Security Threat Analysis."

This phenomenon is particularly bad if I click on a photo from Webshots that comes up in response to a google image search.

---

### Post by ankspo71 on 2011-04-12
Hi,
In firefox you can see if enabling the option called "warn me when websites try to redirect or reload the page" helps. There are also few firefox addons that enhance this feature. Redirect Remover, Redirect Cleaner, Verify Redirect etc.

Also clear your browser's history and cache because something in there might be causing it.

In addition to everyone's advice, and only as a last resort...
It's not that uncommon for _[DNS servers to become hijacked]("http://en.wikipedia.org/wiki/DNS_hijacking")_ too, in which case you can change to another DNS server like _[Google Public DNS]("http://code.google.com/speed/public-dns/")_ who promises better security and no redirects.

Hope this helps.

---

### Post by uRock on 2011-04-12
Moved to Security Discussions

---

### Post by SeijiSensei on 2011-04-12
> **Total Noob said:**
> But after adding the addons, I am still plagued by [url]http://www.storefeedbackrewards.com/ which is offering a bogus Walmart coupon, an iPod and other stuff in exchange for personal info, and by scanfreeantivxp.com, which loads up the "Security Threat Analysis."

How exactly are you plagued by these sites?  I visited the first of them, then left.  It tried to get me to continue along, but I refused to cooperate.  Are you saying that you end up at that site when you enter a different URL in address bar?  Noscript certainly blocks browser hijacking via Javascripts.  Otherwise just don't visit those pages.

Perhaps you could describe the problem in more detail?

---

### Post by Total Noob on 2011-04-12
> **SeijiSensei said:**
> How exactly are you plagued by these sites?  I visited the first of them, then left.  It tried to get me to continue along, but I refused to cooperate.  Are you saying that you end up at that site when you enter a different URL in address bar?  Noscript certainly blocks browser hijacking via Javascripts.  Otherwise just don't visit those pages.

Perhaps you could describe the problem in more detail?

OK. If I search Google images for something and a photo with that tag is indexed, it appears on the screen as a thumbnail in [www.Google.com/images](www.Google.com/images) with other pics with similar tags. 

If you click on a picture you want to see, you are redirected to a page, also with a Google url, in which the picture you clicked appears floating over a dimmed version of the web page that links to it. On the right hand side of the Google url page, you are invited to click to either see the underlying webpage or to click to see the pic in isolation in its full size, which may be bigger than what appears on the web page.

Check it out with this link: [http://www.google.com/imgres?imgurl=http://www.wtv-zone.com/Mary/WebPageGifs/WEBPAGEGIFS2/WebPageGifs3/OBAMA.JPG&imgrefurl=http://www.wtv-zone.com/Mary/OBAMA.HTML&usg=__zJlNmciFJByZ9qrYwng8ge9MQB8=&h=375&w=300&sz=39&hl=en&start=0&zoom=1&tbnid=PSRwF422-1s63M:&tbnh=158&tbnw=134&ei=6m2kTbyhCYSa0QGS69HMCA&prev=/images%3Fq%3Dobama%26hl%3Den%26biw%3D1023%26bih%3D650%26gbv%3D2%26tbm%3Disch&itbs=1&iact=hc&vpx=543&vpy=115&dur=28&hovh=250&hovw=200&tx=111&ty=125&oei=6m2kTbyhCYSa0QGS69HMCA&page=1&ndsp=17&ved=1t:429,r:3,s:0](http://www.google.com/imgres?imgurl=http://www.wtv-zone.com/Mary/WebPageGifs/WEBPAGEGIFS2/WebPageGifs3/OBAMA.JPG&imgrefurl=http://www.wtv-zone.com/Mary/OBAMA.HTML&usg=__zJlNmciFJByZ9qrYwng8ge9MQB8=&h=375&w=300&sz=39&hl=en&start=0&zoom=1&tbnid=PSRwF422-1s63M:&tbnh=158&tbnw=134&ei=6m2kTbyhCYSa0QGS69HMCA&prev=/images%3Fq%3Dobama%26hl%3Den%26biw%3D1023%26bih%3D650%26gbv%3D2%26tbm%3Disch&itbs=1&iact=hc&vpx=543&vpy=115&dur=28&hovh=250&hovw=200&tx=111&ty=125&oei=6m2kTbyhCYSa0QGS69HMCA&page=1&ndsp=17&ved=1t:429,r:3,s:0)

My problem is that right at the point where I'm making up my mind on the google url page while looking at both the pic and through to the linking site -- some of the time with lots of sites, virtually all of the time with Webshots -- I am quickly (<1 second) hijacked and I end up at some bogus sight with a non Google url offering virus protection or some other bogus product. It is not a pop up or pop under; my page is gone to history. Sometimes there is a delay in it starting so I can click through, but that is reasonably rare. 

And to make it more complex, you can't back out of being hijacked. You have to answer yes to a "do you really want to leave the page" and you better go back at least two steps otherwise you are re-hijacked if you only go back one. Whatever is happening is very consistent and won't give up if you try again and again.

Some sites reproduce themselves 8 or 10 times in a row in the process, so you have to go back 10 times to get to where you were, and then you still can't get what you want.

All of this makes looking at pictures very difficult and time consuming and sometimes impossible as you are never allowed to choose the website or the picture before being hijacked. 

I am especially worried about when my data is in the cloud on Google docs or wherever and I can't get it back because of this type of hijacking.

By the way, I tried the noscript and other addons for firefox in my Ubuntu 10.10, and they were useless, if not counterproductive by blocking other things I didn't want blocked. Clearing cache cookies and history was useless in Linux as was deleting that stuff with ccleaner (in my Windows installation). 

I'm a noob, so I don't know what DNS is or how those fixes work, but I found some on line instructions, changed the DNS to the Google public one on an old XP computer, and it was useless. No help at all. 

It seems like a bigger problem than I can solve all on my own, and Google seems like it is a target or perpetrator in this because it is happening primarily with them.

---

### Post by CandidMan on 2011-04-12
DNS is usually how your computer decides what ip address a host name is at after looking at your hosts file. DNS servers have databases matching IP addresses to hostnames like [http://google.com](http://google.com) to [http://209.85.146.104](http://209.85.146.104). If this has been hacked someone could point your PC to any computer they want when you type google.com into the address bar.

You could try making a new firefox profile to eliminate that as a problem, lookup how to change DNS to eliiminate that. Not trying to worry you but failing that maybe your PC has been compromised

Could you run this command in a terminal ```
cat /etc/hosts
```

---

### Post by SeijiSensei on 2011-04-12
Try starting with a new Firefox profile.  Close down Firefox, then type this in a Terminal window:

```

$ cd ~/.mozilla
$ mv firefox firefox.bad

```

Then try starting Firefox again to build a new profile.

What about other browsers like Chrome or Opera or, if you're on Kubuntu, rekonq?  Same problems?

If all this fails, try creating a brand new user in Ubuntu and logging into that account.  Same problems?

---

### Post by 1clue on 2011-04-12
There is a functionally beautiful solution even if it's cosmetically not beautiful.

In /etc/hosts, add lines like this:

127.0.0.1   doubleclick.net
127.0.0.1   [www.doubleclick.net](www.doubleclick.net)
127.0.0.1   [www.storefeedbackrewards.com](www.storefeedbackrewards.com)

When you view the page (say in Google) the side bar advertisements show broken images, but you're not plagued by adware.

This relies on the fact that /etc/hosts is scanned before DNS is used in name resolution.  If it finds a site here, it redirects to whatever you put as the IP address (localhost in the above examples) and since no DNS is there it refuses and returns very quickly with no file.

If you use a DNS, you can also add static entries for those files in the DNS and they will be blocked for everyone on your network.

There is an equivalent static hosts file in Windows but I think it moves from version to version so you need to google your windows and hosts.

---

### Post by Total Noob on 2011-04-12
> **ankspo71 said:**
> Hi,
In firefox you can see if enabling the option called "warn me when websites try to redirect or reload the page" helps. 

Tried with Windows, No help there. Zilch. Immediate no warning redirect.

> **ankspo71 said:**
> There are also few firefox addons that enhance this feature. Redirect Remover, Redirect Cleaner, Verify Redirect etc.

Redirect remover: Zero help with Windows. Went right to scam virus protection.

Redirect cleaner helps, but not by much. I clicked on a picture and got a 403 error: forbidden. So I can't get to my picture that way either. 

Noredirect: useless with Windows version.

> **ankspo71 said:**
> Also clear your browser's history and cache because something in there might be causing it.

Done that and no gain in Windows.

> **ankspo71 said:**
>  In addition to everyone's advice, and only as a last resort...
It's not that uncommon for _[DNS servers to become hijacked]("http://en.wikipedia.org/wiki/DNS_hijacking")_ too, in which case you can change to another DNS server like _[Google Public DNS]("http://code.google.com/speed/public-dns/")_ who promises better security and no redirects.

Hope this helps.

Didn't work either with Windows.

Thanks for your help, but this is starting to look like a really annoying and complicated problem that doesn't bode well for internet use, linux side or windows side.

---

### Post by tgm4883 on 2011-04-12
> **Total Noob said:**
> Tried with Windows, No help there. Zilch. Immediate no warning redirect.



Redirect remover: Zero help with Windows. Went right to scam virus protection.

Redirect cleaner helps, but not by much. I clicked on a picture and got a 403 error: forbidden. So I can't get to my picture that way either. 

Noredirect: useless with Windows version.



Done that and no gain in Windows.



Didn't work either with Windows.

Thanks for your help, but this is starting to look like a really annoying and complicated problem that doesn't bode well for internet use, linux side or windows side.

What DNS server are you using? I've seen issues with hijacked routers that use a malicious DNS server

---

### Post by Total Noob on 2011-04-12
> **SeijiSensei said:**
> Try starting with a new Firefox profile.  Close down Firefox, then type this in a Terminal window:

```

$ cd ~/.mozilla
$ mv firefox firefox.bad

```

Then try starting Firefox again to build a new profile.

What about other browsers like Chrome or Opera or, if you're on Kubuntu, rekonq?  Same problems?

If all this fails, try creating a brand new user in Ubuntu and logging into that account.  Same problems?

Seems bigger than that. I don't have a Firefox profile, at least not in the way I have a facebook profile, if that is what you mean. I have had firefox off and on, and have different versions on different computers, and the same results. Using wifi, different networks, same results.

I have also been having that trouble with various computers with different os's and with different browsers with different versions, sometimes using google search for the first time on them. No difference. Opera, Chrome, IE8, most of the biggies. 

I have not tried creating new users. 

This seems like a big issue, more than I can handle, and possibly a flaw in Google's service since it is so consistent with them. I have been doing virus checking all along, but that's not it because Linux is doing the same thing as Windows. BTW, I virus checked my Linux and that turned up nothing.

I won't keep stuff in the cloud until I can be sure I can get it all back.

---

### Post by 1clue on 2011-04-12
Try what I said above.

The irritating windows are generally from adware sites.  They  load in a panel.  It's not redirecting, it's just loading a panel.  Put the adware site into your /etc/hosts and give it an IP address of 127.0.0.1, and the entire panel will not load.

I do this.  It works.

---

### Post by Total Noob on 2011-04-12
> **tgm4883 said:**
> What DNS server are you using? I've seen issues with hijacked routers that use a malicious DNS server

Seemed pretty correct. There was Ipv4 and 167. and 7 other digits not giving the rest of the numbers in case that is a way into my computer. IDK if it is.

My ISP is Cablevision (Optimum on line)

Is there a problem with my provider's service? Is Cablevision hijacking me?

---

### Post by Total Noob on 2011-04-12
> **1clue said:**
> Try what I said above.

The irritating windows are generally from adware sites.  They  load in a panel.  It's not redirecting, it's just loading a panel.  Put the adware site into your /etc/hosts and give it an IP address of 127.0.0.1, and the entire panel will not load.

I do this.  It works.

You are more sophisticated than me, and I don't know how to follow your advice.

However, it seems to me that the problem is not a panel, as in the down the side ads from Google on results pages. I am taken away to a different url, and can go back by going back. It is not a pop up or pop under or floating ad that one can x out of. If I x out, I am asked if I want to leave the page, and if I do, the browser terminates.

I also get the same problem after a thorough cache cleaning, so I don't think it is a cookie or anything like that causing the redirect.

---

### Post by tgm4883 on 2011-04-12
> **Total Noob said:**
> Seemed pretty correct. There was Ipv4 and 167. and 7 other digits not giving the rest of the numbers in case that is a way into my computer. IDK if it is.

My ISP is Cablevision (Optimum on line)

Is there a problem with my provider's service? Is Cablevision hijacking me?

It sounds ok, but lets just check. Can you give us the first 3 octets? (DNS isn't specific to you, so you could give us the whole thing if you really wanted.)

---

### Post by 1clue on 2011-04-12
> **Total Noob said:**
> You are more sophisticated than me, and I don't know how to follow your advice.

However, it seems to me that the problem is not a panel, as in the down the side ads from Google on results pages. I am taken away to a different url, and can go back by going back. It is not a pop up or pop under or floating ad that one can x out of. If I x out, I am asked if I want to leave the page, and if I do, the browser terminates.

I also get the same problem after a thorough cache cleaning, so I don't think it is a cookie or anything like that causing the redirect.


This is the least sophisticated solution you could possibly get.  You are editing a text file and it fixes your computer.

I used to get those same antivirus warnings.  I don't anymore.

If you want, you can search on "adware hosts file" and find sites which have that hosts file ready to use.

---

### Post by CandidMan on 2011-04-12
>  If you want, you can search on "adware hosts file" and find sites which have that hosts file ready to use.
I've found this site's host file pretty effective [http://someonewhocares.org/hosts/](http://someonewhocares.org/hosts/) but it may diminish ad revenue for some sites. If the OP is worried about that sort of thing :-)

---

### Post by SeijiSensei on 2011-04-12
> **Total Noob said:**
> Seems bigger than that. I don't have a Firefox profile, at least not in the way I have a facebook profile, if that is what you mean.

No, I meant the configuration for Firefox in your home directory.  That has bookmarks, stored passwords, etc. However...

> I have also been having that trouble with various computers with different os's and with different browsers with different versions, sometimes using google search for the first time on them. No difference. Opera, Chrome, IE8, most of the biggies. 

Are these machines all on the same network but behind a single router?  Do you have these problems if you take your computer to a friend's house and connect from there?

If the first of these is true, trying resetting the router to factory defaults.  Usually there's a small button in the back of the router to do this.  Press and hold the button for fifteen seconds or so.  The router's lights should flash at some point.  Then disconnect the router from the power line, wait ten seconds, and connect it again.

Another possibility you can try ruling out is "DNS-poisoning".  On your Ubuntu machine, after you have connected to the Internet, try this:

Edit the file /etc/resolv.conf using the command "sudo nano /etc/resolv.conf".  You'll see some lines that begin with "nameserver".  Delete those lines and replace them with:

```

nameserver 8.8.8.8
nameserver 8.8.4.4

```

Then save the file by holding down Ctrl and typing "x".  Agree to save the file when prompted.

Now try visiting one of those dicey sites.  Make sure you've cleared your Firefox cache before doing so.  Personally, I think you should still [delete your Firefox configuration]("http://ubuntuforums.org/showpost.php?p=10668072&postcount=10") using the steps I gave you in the earlier posting.  Do that, change resolv.conf, and try again.

---

