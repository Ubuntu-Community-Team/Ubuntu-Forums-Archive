---
title: "virus??? setup_build8_294.exe"
date: 2010-01-04
forum: Security
---

### Post by Typhoeus on 2010-01-04
Hi all.
 
      Its really cold in England at the mo so I asked google using firefox "minimum working temperature" second on the list was a page by [www.ajphilips.co.uk](www.ajphilips.co.uk). on clicking this link I was redirected to a page by [www.liveguardfor-pc.net](www.liveguardfor-pc.net) which straight away told me that I had X amount of viruses in my, my documents folder, shared documents folder and hard drive c. It also changed firefox so that I could not access my panels or firefoxes minimise,restore or close buttons in the top right corner of the screen. The site then tried to download a file called "setup_build8_294.exe". I know this is going to be more of a windows issue but I would still like to understand what is going on as it was -10 c at my girlfriends workplace and her colleges (our friends) who are windows users would no doubt of made the same google search.

   I've downloaded the above file and scaned it with clamav using the gtk front end and the file came back as clean I also did some checks regarding the site and they came back dubiouse (I will try and find the results I got and add them to this post. 

  I'm am on xubuntu 8.04 hardy heron and I have reinstalled firefox so that    it no longer hides the panels. 

   If anyone has any knowledge on this issue that they could share I would be greatfull 

  Thanks all and anyone


Found the dubiouse info at [http://www.malwareurl.com/listing.php?domain=www1.liveguardforpc.net](http://www.malwareurl.com/listing.php?domain=www1.liveguardforpc.net)

---

### Post by jonest1 on 2010-01-04
These types of sites and applications are dubious to say the least.  Most of them are either a virus or nagware.  Obviously, if it says it scanned your C: drive, then it's a load of crud.

As far as changing the look and feel of the browser windows.  This can be done through web coding itself to produce a window where there are no buttons or URL bar, etc.  The best thing to do is to just back out of it.

There are some firefox security related software which can assist.  I forget the names, but one makes it to where a lot of the scripting for this type of site will not work.  It's one of the most popular extensions, so, it should not be hard to find.  I also like using ad-block plus and am sure to try to keep the pop-up bocker on.

---

### Post by ajgreeny on 2010-01-04
I saw this same behaviour a while ago, which took me to probably the same liveguardforpc site as you mentioned, with the same so called virus scan performed.

A quick google told me to steer clear of that domain as it was a malware site and wpild cause any number of problems, to a windows PC at least.  I could not shut down the site as it kept just reopening again and again, so I simply logged out of the session and logged in again.  Firefox "crashed" of course, but no problem, I was not doing anything too important, and I do not open at the last session in FF, but with an empty new one.  So for me problem over, but it was a bit of a surprise that this could happen in Ubuntu.

A lesson, I suppose, that should be learned by all.  Don't get complacent and assume linux and ubuntu is completely unassailable by odd problems of this type.  At least it didn't do any damage to the OS.

---

### Post by Typhoeus on 2010-01-04
Thanks for taking the time to reply guys I appreciate it.

   As a learning linux user I wasn't to worried about my system with this prob and it has made my girlfriend a bit more understanding that linux doesn't always do what you want out of the box (it will do what you want it just takes a bit of learning) but it has the bonus of not being plauged by this kind of s**t.

  I would like to know a bit more about the security extentions  that jonest1 mentioned. I just have a basic install of firefox. Please point me in the right direction.Also how is this going to effect our friends the windows users who have no doubt hit the same site (Its me who's going to have to sort this out for them). If I put them on firefox with the security extentions I hope to learn about will they be safe or at leat safer than Iexplorer

I wish I could communicate better, I hope you get my meaning.

Thanks

---

### Post by FuturePilot on 2010-01-04
NoScript [https://addons.mozilla.org/en-US/firefox/addon/722]("https://addons.mozilla.org/en-US/firefox/addon/722")

---

### Post by Typhoeus on 2010-01-04
Good call FuturePilot that add on stops that site loading its page and nasties as well. I will keep using it and see how it goes in day to day use. I guess that any site with scripts will be blocked and there will prob be an option to always allow certain sites if I want to. For others seeking help either follow futurepilots  link or open firefox, select tools, add-ons, then select the "get add-ons" tab and search for "no script"

life is better with friends

This works for windows as well ????

---

### Post by FuturePilot on 2010-01-04
> **Typhoeus said:**
> Good call FuturePilot that add on stops that site loading its page and nasties as well. I will keep using it and see how it goes in day to day use. I guess that any site with scripts will be blocked and there will prob be an option to always allow certain sites if I want to. For others seeking help either follow futurepilots  link or open firefox, select tools, add-ons, then select the "get add-ons" tab and search for "no script"

life is better with friends

This works for windows as well ????

Yes, you can whitelist sites that you trust. And yes it will work on Windows or any other OS that Firefox runs on for that matter.

---

### Post by Typhoeus on 2010-01-04
you know what FuturePilot crackers have pissed me of to on end over the years (and I mean years ). wish i was smart enough to read the book that came with my spectrum 48k when I was 8 (I'm now 35 , gutted school wouldn't let me do computer studies) I've now got a morgage to pay and not enough time to geek as much as I'd like (in my book book geek is cool) thanks for for help it has noted, any more would be fantastic (although basic to others)

Its took me ages  to write this cause I try to get my grammer right n I know it's a big issue in the geek community. ??????????

  To anyone else... share the knowledge. share the the knowledge    

thanks

---

### Post by cariboo on 2010-01-05
I wouldn't worry to much about bad grammar, we don't have any grammar [s]Nazis[/s] in the support forums. Some of us think faster than the fingers can type, so things can look a bit strange sometimes.

---

### Post by Typhoeus on 2010-01-19
Just a bit of feed back, hope it helps some one.

Been using no script for a couple of weeks now, at first it was a slight hassle (mostly for technophobe girlfriend) but if you keep your eyes open at the bottom right hand corner of firefox you will notice either an options button or a no script icon. Click there and you will be given easy to use options for what to do. 

The more you use it the easier it gets. Just like one of you guys said you build up a white list of sites that you allow, so once you trust a site you dont get anymore probs. Once you allow a site you may have to reload the page your trying to view (either click reload current page button or hit the back button and then navigate back to the page you want). 

Thanks guys. It opens up your eyes a bit to what is going on in a web page.

---

### Post by running_rabbit07 on 2010-01-19
AppArmor should protect you from web applications like that. It should stop them from making the changes to you settings. See the AppArmor link in my signature for more info. To start the factory AppArmor profile for Firefox, enter this in a terminal, ```
sudo enforce firefox
```

---

