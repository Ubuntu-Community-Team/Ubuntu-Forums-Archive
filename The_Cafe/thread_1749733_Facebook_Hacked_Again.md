---
title: "Facebook Hacked Again"
date: 2011-05-04
forum: The Cafe
---

### Post by rf.bennett1 on 2011-05-04
Facebook been hacked again with fake pics & Vids of Bin Laden don't click on the picture because if you do it will forward your browser to a blank website (in my case Google Chrome 11) and you get a DOS Attack (Denial Of Service) and your your modem will start having a fit!!! I have just Alerted Facebook :) Block port number 3422 on your firewall (Ports my be different according your OS in my case GNU/Linux Ubuntu 11.04.

---

### Post by _outlawed_ on 2011-05-04
Citation needed of claims.

---

### Post by rf.bennett1 on 2011-05-04
Claims? :confused:

---

### Post by 3Miro on 2011-05-04
DOS attack by clicking on a picture? This would be the most useless thing, not to mention probably impossible to implement (what kind of a bandwidth would the hackers need?) Also, DOS attacks cannot be prevented by closing a port. This makes no sense.

---

### Post by rf.bennett1 on 2011-05-04
I clicked on the picture my browser got forwarded to a blank website and my router had a fit so i pressumed it was a DOS Attack.

---

### Post by _outlawed_ on 2011-05-04
> **rf.bennett1 said:**
> I clicked on the picture my browser got forwarded to a blank website and my router had a fit so i pressumed it was a DOS Attack.

What exactly do you mean by a "fit"?

---

### Post by rf.bennett1 on 2011-05-04
by a fit i mean "extreme excessive send/receiving".

My firewall logged this: 05/05/11 23:14:18] ufw blocked in proto tcp from any to any port 3422

If it's not a DOS Attack i'm sorry for any confusion.

---

### Post by gsmanners on 2011-05-04
Yeah. A UFW log should look more like this:

```
May  3 14:35:43 ubuntu kernel: [15669.528047] [UFW BLOCK] IN=eth0 OUT= MAC=00:de:ad:be:ef:65:00:16:de:ad:be:ef:08:00 SRC=205.171.3.65 DST=192.168.1.102 LEN=59 TOS=0x00 PREC=0x00 TTL=58 ID=43397 PROTO=UDP SPT=53 DPT=43855 LEN=39
```

---

### Post by _outlawed_ on 2011-05-04
> **rf.bennett1 said:**
> 05/05/11 23:14:18] ufw blocked in proto tcp

Running torrents?

---

### Post by rf.bennett1 on 2011-05-04
18 Torrents......Sorry my bad i understand now...i will ask ubuntuforums to delete this post.

Thanx Outlawed :)

---

### Post by _outlawed_ on 2011-05-04
> **rf.bennett1 said:**
> 18 Torrents......Sorry my bad i understand now...i will ask ubuntuforums to delete this post.

Thanx Outlawed :)

I get a ton of ufw stuff in my router logs too, only when I am running torrents. I've currently got about a few hundred just from the past few days seeding all torrents of Natty 11.04.

---

### Post by 3Miro on 2011-05-04
> **rf.bennett1 said:**
> by a fit i mean "extreme excessive send/receiving".

My firewall logged this: 05/05/11 23:14:18] ufw blocked in proto tcp from any to any port 3422

If it's not a DOS Attack i'm sorry for any confusion.

DOS attack means that someone is sending an enormous amount of traffic to a computer, clogging the connection and preventing the machine from accessing the network. This makes sense if you want to take down a server, Yahoo got hit a few years ago. Why would a hacker want to block random people from getting to the Internet, there is no gain for them. Furthermore, clogging your connection would require a more powerful connection than all the people that have clicked on the picture combined.

In the case of Yahoo, I think they used a virus that would infect many machines all over the world and cause them to hit the server at one specific point. This is very hard to do for some random people (everybody knows Yahoo ahead of time, there is no way for them to know who would click on the picture ... this is way more complicated).

Something of the sort requires preparation you cannot make a virus and infect a sufficient number of people fast enough. The news of OBL's dead came only a couple of days ago ... unless ... we found a conspiracy!!!!! :D

I don't know what happened to your router. However, it wasn't a DOS attack (it could be some other attack, check what listens to port 3422 by default).

---

### Post by rf.bennett1 on 2011-05-04
Would this excessive torrent use flag up on my ISP?

---

### Post by rf.bennett1 on 2011-05-04
I didn't know Yahoo got hit i only learned that Sony Playstation was hit twice a few days ago. I thought companies like yahoo and sony would have encrypted servers 1028bit SSL perhaps.

---

### Post by 3Miro on 2011-05-04
> **rf.bennett1 said:**
> Would this excessive torrent use flag up on my ISP?

It might, if the ISP cares about this. Torrents are not illegal by default, most of us download .iso files for most distributions with torrents. Some ISP put some limitations on the default torrent ports as they don't want to deal with too much traffic, but I don't see an issue with using torrents at all.

---

### Post by 3Miro on 2011-05-04
> **rf.bennett1 said:**
> I didn't know Yahoo got hit i only learned that Sony Playstation was hit twice a few days ago. I thought companies like yahoo and sony would have encrypted servers 1028bit SSL perhaps.

Yahoo was years ago and DOS attack doesn't steal any data. DOS is denial of service, meaning that people cannot access Yahoo because the server is constantly busy processing bogus requests. All the data is safe, you just cannot get to it.

PlayStation is another story altogether.

---

### Post by Timmer1240 on 2011-05-04
I clicked on a link in a message on facebook last night and it spammed everyone on my friends list with the same message and link something about seeing yourself aged 20 years.Anyways I went to everyones page and removed the bogus posts changed my password and swithced my facebook security settings to Https connection.I dont think it installed anything on my computer im running debian testing and all seems well now.I hope it cant infect Linux any input?

---

### Post by 3Miro on 2011-05-04
I can't say about Facebook, but it cannot really infect your computer. An attack like that would require specific knowledge on what OS you are running. If one knows that you run Debian testing (as opposed to stable), then they can try something, but who would specifically target Debian testing? At any rate, if one has enough such knowledge of Linux, they are far more likely to join the community in fixing the problems, then creating "viruses" on Facebook.

---

### Post by Timmer1240 on 2011-05-04
Yes if I was running windows I would be more worryied about it as a bunch of other people were talking about getting hit with it and they all run windows.It did spam everyone on my friends list with bogus messages and links but I think thats just some activity from their servers after I clicked the link I dont think it came from my computer itself.

---

### Post by user1397 on 2011-05-04
i clicked on a link like that and it just went to a blank page but immediately reverted back to facebook...looked fishy for sure, but i have noscript on so i'm not worried :)

---

### Post by CharlesA on 2011-05-04
It's not "hacking" it's having people click on random links that spam everyone they are "friends" with.

Clicking random links on the internet isn't a good thing to be doing.

---

### Post by Yownanymous on 2011-05-05
It's plain old social engineering. It doesn't infect your computer, but you have authorised an application to spam your facebook. In all honesty you can't really be that smart if you're falling for "exciting-sounding" messages like "See yourself in 20 years".

And I guess cloud applications such as on Facebook blow the "Linux is safe" line apart.

---

### Post by Smaug95swe on 2011-05-05
Well yea this just was on the newspaper for me so he is not lying

I dont know what it does tho... Didnt care to read the article

---

### Post by Thewhistlingwind on 2011-05-05
> **CharlesA said:**
> 
Clicking random links on the internet isn't a good thing to be doing.

At least if they have sensationalism attached. I've learned a great deal from random links on the Internet.

---

### Post by Smaug95swe on 2011-05-05
I would guess that Its not a DOS that you get but maybe a Trojan that download Pretty much stuff thats why the connection is so bad? or i dunno

---

### Post by jhonan on 2011-05-05
Actually, it's a very common to see this on Facebook. I suppose it could be classified as a trojan. The way it works is;

- You see one of your friends 'liked' a web-page, usually something sensational, like pictures of dead Osama, or a rollercoaster crash or 'I caught my daughter on webcam' - So you click it

- The page you go to has some javascript which automatically registers you as having 'liked' the page, even though you didn't click the 'like' button

- The 'like' is then posted to your Facebook wall, appears on your friend's walls, they see the link, click on it, and the cycle continues.

---

### Post by t0p on 2011-05-05
> **Smaug95swe said:**
> Well yea this just was on the newspaper for me so he is not lying

I dont know what it does tho... Didnt care to read the article

I don't suppose you'd care to provide a link to the news story, for those off us too lazy or clueless to find it for ourselves?  I know Google is my friend, but sometimes he expects me to do stuff when I'd rather be playing backgammon (**gnubg** FTW!!)

---

### Post by Timmer1240 on 2011-05-05
> **jhonan said:**
> Actually, it's a very common to see this on Facebook. I suppose it could be classified as a trojan. The way it works is;

- You see one of your friends 'liked' a web-page, usually something sensational, like pictures of dead Osama, or a rollercoaster crash or 'I caught my daughter on webcam' - So you click it

- The page you go to has some javascript which automatically registers you as having 'liked' the page, even though you didn't click the 'like' button

- The 'like' is then posted to your Facebook wall, appears on your friend's walls, they see the link, click on it, and the cycle continues.

Ok this explanation make sense Thankyou.

---

### Post by jerenept on 2011-05-05
> **jhonan said:**
> Actually, it's a very common to see this on Facebook. I suppose it could be classified as a trojan. The way it works is;

- You see one of your friends 'liked' a web-page, usually something sensational, like pictures of dead Osama, or a rollercoaster crash or 'I caught my daughter on webcam' - So you click it

- The page you go to has some javascript which automatically registers you as having 'liked' the page, even though you didn't click the 'like' button

- The 'like' is then posted to your Facebook wall, appears on your friend's walls, they see the link, click on it, and the cycle continues.

Or sometimes the site tells you that you have to share the link with 10 or 20 friends before you can see the OMG OSAMA PIXX or OMG ROLLERCOASTER CRASH.

This annoys me.
Also, I block any application that sends me a request, and hide any app that happens to encroach on my news feed. I'm paranoid.

---

### Post by jhonan on 2011-05-05
> **jerenept said:**
> Also, I block any application that sends me a request, and hide any app that happens to encroach on my news feed. I'm paranoid.
If you were really paranoid you'd delete your Facebook account. :D

---

### Post by jerenept on 2011-05-05
> **jhonan said:**
> If you were really paranoid you'd delete your Facebook account. :D

If I do that, what would I do all day? Work? :P

P.S. only my name, birthday and gender are publicly viewable. I have no apps permitted to access my account. My password is 19 characters long, with capitals and numbers. I always use https. I'm pretty freaking confident anout my data in Facebook.

---

### Post by Wolligog on 2011-05-05
I had a warning from a facebook contact 2 days ago that he unwittingly opened a facebook macro virus and it was sending messages to everyone on his friends list. but if people are gonna use windows then they shouldn't complain when they get viruses.!

---

### Post by aaaantoine on 2011-05-05
Now that XP share is down to about half of all Windows installs, there's even less of an excuse to get viruses.

Pro-tip: If a website is requesting access to your computer, DENY!

---

### Post by jerenept on 2011-05-05
> **Wolligog said:**
> I had a warning from a facebook contact 2 days ago that he unwittingly opened a facebook macro virus and it was sending messages to everyone on his friends list. but if people are gonna use windows then they shouldn't complain when they get viruses.!

The "virus" you speak of uses JavaScript. Linux is 100% susceptible. The website is [here]("http://kronik969.info/").

---

### Post by uRock on 2011-05-07
> **jhonan said:**
> If you were really paranoid you'd delete your Facebook account. :D
That's like selling your house because you are scared of a trespasser stealing the buds off of your roses on Mother's Day.

---

### Post by NightwishFan on 2011-05-07
Not on facebook but on skype I had a message telling me that there was a "system upgrade" for a vulnerability and I should click here.

It said the exploit was on:
Windows Xp
Windows Vista
Windows 7
Mac Os X etc etc

I was like.. hmm i dont see GNU/Linux on that list so I guess I am alright.  ;)

---

### Post by |{urse on 2011-05-07
Yeah a buddy of mine recently spammed me the "Osama shooting caught on video" link, a few people who clicked it got infected (I didnt click it because i dont care one whit about Osama) Anyways when they clicked it the got ddosed and all windows xp users ended up with a rogue antivirus later that day (more smitfraud fun).

---

### Post by Dustin2128 on 2011-05-07
> **NightwishFan said:**
> Not on facebook but on skype I had a message telling me that there was a "system upgrade" for a vulnerability and I should click here.

It said the exploit was on:
Windows Xp
Windows Vista
Windows 7
Mac Os X etc etc

I was like.. hmm i dont see GNU/Linux on that list so I guess I am alright.  ;)
Heh, I think I'm going to start a fail blog of social engineering in linux/firefox/etc. The worst one I ever got was probably browsing on a slack 13.1 computer with opera I think, and some random website redirecting me to a website with the classic windows xp pop-up box poorly copied with flash telling me that my version of internet explorer needed to be updated! :lolflag: :lolflag: :lolflag:
God I wish that I had taken a screenshot... :(

---

### Post by Thewhistlingwind on 2011-05-07
> **jerenept said:**
> The "virus" you speak of uses JavaScript. Linux is 100% susceptible. The website is [here]("http://kronik969.info/").

Noscript :popcorn:

(BTW, totally keeping that around in case I need to give someone an example of why these sorts of things are worth turning off.)

EDIT: No demonstrations.
EDIT: That is, no explanations by demonstration

---

