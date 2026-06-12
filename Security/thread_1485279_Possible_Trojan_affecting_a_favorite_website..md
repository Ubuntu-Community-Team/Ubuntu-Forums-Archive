---
title: "Possible Trojan affecting a favorite website."
date: 2010-05-16
forum: Security
---

### Post by Jonas thomas on 2010-05-16
Hi I'm not sure if this is the proper venue for this but I thought I'd give it a go.

I really like this site in the past: [http://www.videotutorialsrock.com/](http://www.videotutorialsrock.com/) and I was telling some friends about it.  When I went to the site recently firefox when nuts and I got one of those pop ups showing that my system was being scanning my windows system for viruses.  (I have to admit it was rather amusing since I was running linux)  I basically didn't click on anything other than shutting down the forms.  The disturbing thing is that this happened by simply visiting the sight.

I got to believe the guy who set up the sight is ok and for whatever reason is longer paying attention his sights.  Going to one of his linked sights it looks like he's been hacked. [http://www.khronologic.com/forums/](http://www.khronologic.com/forums/).  I don't know if he's croaked, on vacation or whatever.

Questions:  If things went weird on my Linux computer one time and now appear normal, do I have something to worry about here?

I suppose as far as downloading any content from this sight now, it's probably a recipe for something bad to happen.

I really like B. Jacobs content, and I wanted to get ahold to him through something other than his/her web site to find up what's up.
Any suggestions?

---

### Post by mgmiller on 2010-05-16
That's really quite funny.  Yes, that site has been hacked.  All that happened is that firefox was made to display a video of a phony windows scan.  It then tries to convince you that you are infected and wants you to download and install something to "fix" it.  Of course, the downloaded file actually contains the malware.  In our case, nothing you saw there can have any effect on you.  Nothing you saw in the "scan" had any relation to your actual Linux file system, which does not contain any of the files scanned or revealed by the scan.  Even if you downloaded and tried to execute the "fix", nothing would happen (assuming you don't have wine installed).

Just sit back, relax and watch the blinking lights.  It can't hurt you.

---

### Post by mgmiller on 2010-05-16
Now that's odd, I just tried to look him up in the network tools and when I went back to his site, it behaved normally without the popup.  It gives his contact e-mail as:
  [IMG]http://www.videotutorialsrock.com/y8kl5g5wldgt.png[/IMG]  
I guess you could drop him a line and ask what's going on.

---

### Post by OpSecShellshock on 2010-05-16
I recognize the domain that's loading the malware. Same folks who've been involved in the big Wordpress/PHP/GoDaddy/Network Solutions hacks of the last couple weeks. Far as I know, it's still ongoing. When people clean their sites they just get compromised again (last I heard). If you browse there with NoScript enabled and click on the options, the domain will be displayed but the script won't run. The hosting provider can probably suggest a fix for it.

---

### Post by Jonas thomas on 2010-05-16
I tried emailing the site author.  His email is no longer valid.
He had a bunch of interesting source code..  I wonder if that's been compromised.
Bummer... Lots of good stuff on that sight.
Do you have any links you can provide as to what is going one with this godaddy thing.

---

### Post by wilee-nilee on 2010-05-16
If you have noscript, and adblock plus running in addons for FF you should never see a popup. Adblock I use easy-list, and easy-privacy, I also use better privacy a sol cookie flash cookie remover.

---

### Post by Jonas thomas on 2010-05-16
> **wilee-nilee said:**
> If you have noscript, and adblock plus running in addons for FF you should never see a popup. Adblock I use easy-list, and easy-privacy, I also use better privacy a sol cookie flash cookie remover.

I suppose I should lock down my firefox a bit.
I have to say as near a I can recall, the behavior wasn't a typical pop up.  As I recall I think the main screen shrunk down wiggling all over the place from my compiz fusion and then exploded with the virus checker. Darn exciting for a couple of seconds.

---

### Post by Mach1723 on 2010-05-16
You might be able to find the files and source code via [http://web.archive.org/web/*/http://www.videotutorialsrock.com/](http://web.archive.org/web/*/http://www.videotutorialsrock.com/) or (for all files) [http://web.archive.org/web/*/http://www.videotutorialsrock.com/*](http://web.archive.org/web/*/http://www.videotutorialsrock.com/*)

NVM: nothing useful there, really should have checked before i bothered linking..

---

### Post by wilee-nilee on 2010-05-16
> **Jonas thomas said:**
> I suppose I should lock down my firefox a bit.
I have to say as near a I can recall, the behavior wasn't a typical pop up.  As I recall I think the main screen shrunk down wiggling all over the place from my compiz fusion and then exploded with the virus checker. Darn exciting for a couple of seconds.

I know very little about this sort of thing, but I would speculate that it was a flash script, which is what noscript is for. There is a thread by a mod about security you will have to find it.

---

### Post by OpSecShellshock on 2010-05-16
The best single source for information on it (with ideas for what to do about it as well) that I've run across is here:

[http://blog.sucuri.net/](http://blog.sucuri.net/)

All of the most recent posts, probably going back about 2 weeks, are about this issue. There are also links to other sites' analysis and some explanations of the code.

---

### Post by FuturePilot on 2010-05-16
There's no Flash involved. It's all javascript. If you look at the source to the original website, it looks like someone injected a script into the page to redirect to that fake virus scanner.

---

### Post by Jive Turkey on 2010-05-17
It looks like you could post him a snail-mail letter or even call him on the phone from the info in his dns record > 
Here's what we know about videotutorialsrock.com:

    * "William Jacobs" owns about 46 other domains View these domains >
    * is a contact on the whois record of 4 domains
    * 1 registrar has maintained records for this domain since 2007-05-14
    * This domain has changed name servers 1 time over 3 years.
    * Hosted on 2 IP addresses over 3 years.
    * View 26 ownership records archived since 2007-06-06 .
    * Wiki article on Videotutorialsrock.com
    * 2,104 other web sites are hosted on this server.

DomainTools for Windows®

Now you can access domain ownership records anytime, anywhere... right from your own desktop! Download Now>
Registrant:
   William Jacobs
   550 Memorial Drive
   Cambridge, Massachusetts 02139
   United States

   Domain Name: VIDEOTUTORIALSROCK.COM
      Created on: 14-May-07
      Expires on: 14-May-11
      Last Updated on: 15-May-10

   Administrative Contact:
      Jacobs, William  
      500 Memorial Drive Room #535
      Cambridge, Massachusetts 02139
      United States
      (561) 225-8885      Fax -- 

   Technical Contact:
      Jacobs, William  
      500 Memorial Drive Room #535
      Cambridge, Massachusetts 02139
      United States
      (561) 225-8885      Fax -- 


I might add that while using firefox and its no-script plugin I was able to access the site adn view one of the videos without triggering the scareware ad.  Hmmm, "Allow scripts from kdjkfjskdfjlskdjf.com"? sure sounds like a great idea!

---

### Post by rookcifer on 2010-05-17
I visited the site and first I got the hilarious Windows scan for viruses screen saying my PC was infected :P

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157253&stc=1&d=1274108898[/IMG]

Then it automatically downloaded this Windows executable that it claims will "clean" my PC up:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157254&stc=1&d=1274108898[/IMG]

Now, here's a major difference in Linux and default Windows behavior:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157255&stc=1&d=1274108898[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157260&stc=1&d=1274109665[/IMG]

As you can see, the executable bit is not set by default which means one has to manually make the file executable before it will actually execute.  This means no automatic execution or execution upon double click.  This helps those who might be running WINE.

---

### Post by Jonas thomas on 2010-05-17
> **OpSecShellshock said:**
> The best single source for information on it (with ideas for what to do about it as well) that I've run across is here:

[http://blog.sucuri.net/](http://blog.sucuri.net/)

All of the most recent posts, probably going back about 2 weeks, are about this issue. There are also links to other sites' analysis and some explanations of the code.

Wow interesting reading.... Thanks

---

### Post by frogotronic on 2010-05-22
> **Jonas thomas said:**
> Hi I'm not sure if this is the proper venue for this but I thought I'd give it a go.

I really like this site in the past: [http://www.videotutorialsrock.com/](http://www.videotutorialsrock.com/) and I was telling some friends about it.  When I went to the site recently firefox when nuts and I got one of those pop ups showing that my system was being scanning my windows system for viruses.  (I have to admit it was rather amusing since I was running linux)  I basically didn't click on anything other than shutting down the forms.  The disturbing thing is that this happened by simply visiting the sight.

I got to believe the guy who set up the sight is ok and for whatever reason is longer paying attention his sights.  Going to one of his linked sights it looks like he's been hacked. [http://www.khronologic.com/forums/](http://www.khronologic.com/forums/).  I don't know if he's croaked, on vacation or whatever.

Questions:  If things went weird on my Linux computer one time and now appear normal, do I have something to worry about here?

I suppose as far as downloading any content from this sight now, it's probably a recipe for something bad to happen.

I really like B. Jacobs content, and I wanted to get ahold to him through something other than his/her web site to find up what's up.
Any suggestions?

This is ransomware ( [http://vimeo.com/6949998](http://vimeo.com/6949998) )and will seriously damage a windows install.  On Ubuntu you're fine.

- CH

---

