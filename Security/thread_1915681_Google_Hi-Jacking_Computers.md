---
title: "Google Hi-Jacking Computers?"
date: 2012-01-26
forum: Security
---

### Post by Jackson45acp on 2012-01-26
Hello everyone.

I have a concern that I would like to run past the forum.

I am a fairly new user to Ubuntu and I am currently running 10.04 LTS (Lucid Lynx) and I have Firestarter installed.

I notice that sometimes when I open the Firestarter GUI and select STATUS>ACTIVE CONNECTIONS I see where there is a connection to my computer, sometimes even when Firefox hasn't even been launched. It shows a numerical i.p address. When I then right click LOOKUP HOSTNAMES, instead of getting a domain name, it gives me something like Yx-in-f95.1e100.net as connecting on port 80 and more from Google on HTTPS port 443. 

I then try to block connections for the numerical 1.p. address under the Outbound Traffic Policy, but each time I block one, another one pops up a few seconds later in it's place. I searched about a dozen of the numerical i.p. addresses under ARIN Whois and they all point directly to Google.

What is bizarre is that this occasionally occurs when the browser isn't even open, but when I launch Firefox and it opens to my home page, (which is an European-based, rugby team website that has NOTHING to do with Google as far as I know of anyway) the Firestarter "Active connections list grows to sometimes about 4 or 5 connections, one being the home page website and the rest to Google. Each numerical i.p. address from Google's domain always switches to something like the Yx-in-f95.1e100.net. NEVER does it say Google.com.

In light of the recent issues with Google's privacy abuse investigation, I am wondering if this is something anyone else is experiencing, and if this is something I should be concerned about. I assume that Google is tracking my online activity with this, but how is it occurring and how do I stop it. I do not want to provide Google jack on my personal surfing habits. Even when I go to Ubuntuforums.org, after a page loads, all I have are about 5 or 6 active connections to i.p. addresses registered to Google. WTF? Even when I leave the sign in page to Ubuntu forums up and the Canonical connection drops from inactivity, Google's connections stay on A LOT longer. 

Any help would be greatly appreciated. I apologize if this is posted in the wrong area of the forum, but would really like some help, and I didn't know exactly where to put this post. Also, if anyone knows of a reputable program I can get from the repository or elsewhere that will do a scan on my Ubuntu computer for viruses and malware I would appreciate a pount in the right direction.

And before anyone goes there, I KNOW Linux-based systems are hard to infect and take control of, but it is NOT impossible and the threats are growing against our beloved Ubuntu every day. 

Thanks all,

Jax

---

### Post by kerry_s on 2012-01-26
google services on the Web site? like adsense or that counter thing.
could it be dns caching? 
pipelining? 
your ISP could be using google vm's to improve service? 

any which way i'm sure google is not out to get you, unless your doing something your not suppose to. ;-)

---

### Post by Jackson45acp on 2012-01-26
Thanks for the reply.

No, I am not doing ANYTHING illegal, on line or otherwise. Far too old for the accompanying consequences. :)

I have no idea why or how it's happening. I can tell you this much further, that it doesn't matter which site I visit on the web, even something like CNN, I get an active connection to an i.p. belonging to Google.

Well, I should say, every site I have tried, EXCEPT for the U.S. Department of Justice.

Just find it interesting in light of the recent news about Google ramping up their data mining operations and not giving people an option to "opt out".

Doesn't this ring a bell for anyone else? I guess I will have to file a complaint with www.ic3.gov and let them investigate this. After all, it is what I pay my taxes for.

Thanks again,

Jax

---

### Post by CharlesA on 2012-01-26
1) Don't use firestarter
2) See what process the connection belongs to with:

```
sudo netstat -nlp
```

---

### Post by Dangertux on 2012-01-26
Do the websites you're visiting happen to have a google +1 button on them?

Because that will load from google's API hence the connection ;-)

So will google analytics, which is used on pretty much everything.

---

### Post by Jackson45acp on 2012-01-26
> **CharlesA said:**
> 1) Don't use firestarter
2) See what process the connection belongs to with:

```
sudo netstat -nlp
```
Charles: Thanks for the reply. I ran the sudo command on the home page, and found nothing associated with the connection as far as I can tell. I am still somewhat of a noob, but I do sudo properly and I hope this doesn't sound stupid, but I see nothing in the results that directs me to Google or the specific i.p. address. Is there something else I should be looking for? 

Sorry.... I see where you didn't ask for this. LOL!

Jax

---

### Post by Jackson45acp on 2012-01-26
> **CharlesA said:**
> 1) Don't use firestarter
2) See what process the connection belongs to with:

```
sudo netstat -nlp
```
By the way, can you tell me why I shouldn't use Firestarter? can you recommend something else? I like it because I can kill alot of connections by adding them to my outgoing traffic policy and it speeds up my page loading BIG TIME. It just seems that Google owns MILLIONS of i.p. addresses and each time I block one, another one pops up from them and I simply do not see how to block a range of i.p. addresses.

Thanks again for your help.

Jax

---

### Post by Jackson45acp on 2012-01-26
> **Dangertux said:**
> Do the websites you're visiting happen to have a google +1 button on them?

Because that will load from google's API hence the connection ;-)

So will google analytics, which is used on pretty much everything.
No google+1 or google analytics tab. (I am familiar with what you are talking about on both accounts, also, btw.

Thanks for the reply,

Jax

---

### Post by Dangertux on 2012-01-26
I can almost guarantee there are scripts calling the google API on CNN and probably most of the other sites you visit.

---

### Post by CharlesA on 2012-01-26
> **Jackson45acp said:**
> Charles: Thanks for the reply. I ran the sudo command on the home page, and found nothing associated with the connection as far as I can tell. I am still somewhat of a noob, but I do sudo properly and I hope this doesn't sound stupid, but I see nothing in the results that directs me to Google or the specific i.p. address. Is there something else I should be looking for? 

Sorry.... I see where you didn't ask for this. LOL!

Jax

Yeah, you just needed sudo to show which process a connection belongs to. If it's not there you should be ok.

> **Jackson45acp said:**
> By the way, can you tell me why I shouldn't use Firestarter? can you recommend something else? I like it because I can kill alot of connections by adding them to my outgoing traffic policy and it speeds up my page loading BIG TIME. It just seems that Google owns MILLIONS of i.p. addresses and each time I block one, another one pops up from them and I simply do not see how to block a range of i.p. addresses.

Thanks again for your help.

Jax

Firestarter is no longer underdevelopment and isn't really meant to be used as a traffic monitor, so to speak, it is meant to be run, have rules enabled and closed.

One alternative is ufw (which is installed by default), or gufw (GUI version of ufw)

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

> **Dangertux said:**
> I can almost guarantee there are scripts calling the google API on CNN and probably most of the other sites you visit.

Webmasters use it for tracking traffic, if I remember right.

---

### Post by Jackson45acp on 2012-01-26
Thanks Charles and Dangertux.. 

My understanding was that Firestarter was  simply as you Charles said,  an adjustment tool FOR THE UFW to set how  it functions and that you  didn't have to mess with it. Unfortunately, my   Internet connection  speeds are only 1.5mb/sec max and when I visit  pages that have things  trying to load like loadus.excelator.com and  connect.facebook.net ,  (and many other things I do not use, want or  need), it seriously delays  my actual desired web page from loading. At  least Firestarter gives me  a way to kill them by modifying the outbound  traffic policy. I realize  Firestarter is no longer supported but it does  still work.  Platform.twitter.com was killed and THAT was a wonderful  thing. That  delayed my pages loading by at least 30 seconds. Might as  well have  been on dial up. So, the GUFW I understand is basically the  same thing.   A different GUI for controlling the UFW. Is this right?  Does it allow  me to block scripts, connections, etc or is it also a "set  and forget"  program?

Also, any advice as to how to stop Google's scripts from running as a   whole? Like maybe through AdBlock Plus? I have it installed and write   rules to block unwanted "images" (and scripts) on each and every page I   go on, but it seems like a never-ending battle. I realize that Google   and others say they are  "trying to customize my web-experience to my   tastes" (which is mostly BS in my opinion), but I don't want any "big   brother" like Google or Facebook, et al. spying on me mainly because it   slows down my page loading speed and therefore wastes my time. I do not   use either service so why should they slow me down? 

The Internet used to not be so complicated, corrupt and riddled with crap. What happened? :confused:

Anyway, can you address my question re: a spyware detection program for   Ubuntu? Is it even theoretically possible to get spyware if the  jacknuts  do not have access to root?

I love Ubuntu, and heaven knows it's SOOOOOOOOOO much better (in a whole   other universe) than Microshat, but it's becoming  a pain with all of   these page hitch-hikers loading. Sure wish you could right click on the   process scroll at the bottom of the page when something is loading and   kill it dead, once and for all pages to come. A "Daisy Cutter" of  sorts  for scripts. Are you listening programmers? LOL

I am still NOT convinced that I have a clean machine as the Internet   connections to these Google i.p.'s occur occasionally even when the   browser hasn't even been launched yet. Explain that one if you can!

Thanks to all. Stay tuned for my response from the Cybercrime Division of the DOJ! 

Rock on, :guitar: (Being a bass player myself, I dig this one). Looks like my Chris Beattie Sig. Dinky!

Thanks again you guys.

Jax

---

### Post by Jackson45acp on 2012-01-26
Please delete this or tell me how!

---

### Post by Jackson45acp on 2012-01-26
Dangertux:

Any way to kill the Google APIs from ever running in the first place?

Jax

---

### Post by |{urse on 2012-01-26
Don't install chrome or any other google products, don't use sites that are in any way affiliated with google (in other words, disreputable or unlisted sites) and use an isp that blocks google (i'm not personally aware of any that do it).

You may want to read more about googles revised privacy policy also.

[http://www.npr.org/2012/01/25/145859965/google-revises-its-privacy-policy](http://www.npr.org/2012/01/25/145859965/google-revises-its-privacy-policy) 

I like npr, there's plenty more info than this on the net though.

---

### Post by CharlesA on 2012-01-26
Running Firefox with NoScript/Adblock Plus will block 90% of those.

You have rkhunter and a couple other "malware" scanners, but most of the time they report false positives.

Even without NoScript, the chance of getting some form of malware on a *nix box is very slim. With NoScript, the chance is almost nothing.

---

### Post by Dangertux on 2012-01-26
> **CharlesA said:**
> Running Firefox with NoScript/Adblock Plus will block 90% of those.

You have rkhunter and a couple other "malware" scanners, but most of the time they report false positives.

Even without NoScript, the chance of getting some form of malware on a *nix box is very slim. With NoScript, the chance is almost nothing.

That pretty much covers it.

---

### Post by bluexrider on 2012-01-26
> **|{urse said:**
> Don't install chrome or any other google products, don't use sites that are in any way affiliated with google (in other words, disreputable or unlisted sites) and use an isp that blocks google (i'm not personally aware of any that do it).

You may want to read more about googles revised privacy policy also.

[http://www.npr.org/2012/01/25/145859965/google-revises-its-privacy-policy](http://www.npr.org/2012/01/25/145859965/google-revises-its-privacy-policy) 

I like npr, there's plenty more info than this on the net though.

This is just the case for me to find another search engine. Wherever I go, there I am.

I really don't want to let them know where I was let alone where I am going.

---

### Post by uRock on 2012-01-26
EtherApe is a great graphic tool for seeing what IPs you are connected to and seeing which protocol said connections are using. EtherApe is in the repos and installed via Ubuntu Software Center or CLI.
[[img]http://etherape.sourceforge.net/images/v0.9.3-thumb.png[/img]]("http://etherape.sourceforge.net/images/v0.9.3.png")

---

### Post by |{urse on 2012-01-26
> **bluexrider said:**
> This is just the case for me to find another search engine. Wherever I go, there I am.

I really don't want to let them know where I was let alone where I am going.

I'd suggest duck duck go :) Private and no tracking (they claim)

[http://duckduckgo.com/](http://duckduckgo.com/)

---

### Post by Jackson45acp on 2012-01-27
> **bluexrider said:**
> This is just the case for me to find another search engine. Wherever I go, there I am.

I really don't want to let them know where I was let alone where I am going.
Hey everyone...

Thanks for the great tips from all. I plan on installing NoScript right after I finish this post, and am going to also try out Etherape and maybe even Rkhunter just to see what shows up. I can usually tell what is a false pos with a little research. Great information from all.

Now then, BlueXrider.... bitchin scooter btw.... for a new private browser, I have read a bit about ixquick, which is bassed out of Europe and has won the very first   [European Privacy Seal]("http://ixquick.com/eng/press/europrise.html") and it sounds like a nice search engine. The European countries demand privacy on the Internet, so maybe this is a good one. Seems pretty tight from what I have read about it. I have not yet tried it however. Has anyone checked it out yet?

Anyway, thanks again to all for the help on my issues. I will post a follow up experience report with all of the above mentioned programs. Hopefully, after NoScript is on board,  life will be good again. :)

Many thanks, lads.

Jax

---

### Post by Jackson45acp on 2012-01-27
> **Dangertux said:**
> That pretty much covers it.

 You guys nailed it! NoScript kicks tush! My page load speed is off the charts, everywhere I go! THANK YOU, THANK YOU, THANK YOU!!!!!  The rootkit hunter wouldn't load for some reason, it said I needed Wine. is this a Windows program? If so, I will just pass, I think. I have enough bad dreams about my past experiences with Windows. Weird thing is, it came in a tarball.

---

### Post by CharlesA on 2012-01-27
The name of the program is rkhunter and it is in the repos.

Glad NoScript helps speed up your browsing. :)

---

### Post by Jackson45acp on 2012-01-27
Kurse,  I don't use anything from Google. No Chrome, no Gmail, nada.  In light of their recent changes in privacy policy and not allowing people to opt out is a real big sign of the company integrity.  Personally, I hope they go down in flames and take Facebook, Twitter and MySpace with them. Complete wastes of bandwidth IMO. The only thing I care for from Google is Youtube. Sure wish the rest of the video hosting web sites had the amount of content that Youtube does, but them again, with the snot-nosed 12 year old kids posting fake videos which are simple, (non-entertaining) CGI from video game grabs. That's BS. More wasting of my time.    Just sayin,    Jax

---

### Post by Jackson45acp on 2012-01-27
> **CharlesA said:**
> The name of the program is rkhunter and it is in the repos.

Glad NoScript helps speed up your browsing. :)

 It made browsing fun again. Thanks a LOT, Charles.  I didn't find rkhunter in the repos. The one I pulled was from the Sourceforge web site.  Will take another look.   Thanks again. You may have never asked for this, but I am thankful you are here and share good info openly and kindly.  Good Karma to you, bro.  Jax

---

### Post by CharlesA on 2012-01-27
Huh, rkhunter should be in the universe repo.

In any case, I don't think you need to run it. ;)

---

### Post by Jackson45acp on 2012-01-27
> **CharlesA said:**
> Huh, rkhunter should be in the universe repo.

In any case, I don't think you need to run it. ;)

 Hey Charles,  I found and downloaded rkhunter. It does not show up in my menu automatically, and I forget the process of how to add it to your menu. I ran rkhunter in terminal and it now shows it in the menu, however when I click on it to launch, it does not open.  It's been awhile since I have installed a program, and I forget what command I have to put in to get it to launch.  Can you refresh me?  Thanks,  Jax  P.S. I probably don't need to run rkhunter, but now that it is installed, I would like to, if nothing else for the practice of the process of adding and launching. I clearly don't do it often enough.    One other question, Am I not allowed to edit my profile and icon until I post 50 times? It doesn't allow me to edit my avatar or add signature or anything. Thanks!

---

### Post by CharlesA on 2012-01-27
It's a CLI utility, so I don't know if it will run from the GUI or not.

As for the profile thing, you need 50 beans, which are posts in the support area in order to edit your avatar/signature. This was done to help reduce spam.

---

### Post by emiller12345 on 2012-01-31
I know this is a few days late, but I just found something interesting.  In firefox I have an entry in the 'about:config' section that refers to a google website
urlclassifier.keyupdatetime.[https://sb-ssl.google.com/safebrowsing/newkey](https://sb-ssl.google.com/safebrowsing/newkey)
apparently its used to help make sure our browsing is 'safe'

---

