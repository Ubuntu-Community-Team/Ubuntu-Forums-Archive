---
title: "Traveling to China next month, thoughts on computer usage"
date: 2011-08-01
forum: The Cafe
---

### Post by Wood Prof on 2011-08-01
I'm traveling to Shanghai and Nanjing in early September.  I will be visiting the Nanjing Forestry University and then a furniture expo in Shanghai.  There are two things I am concerned about.  Besides having the hard drive on my laptop encrypted (my preference and required by the university I work for), what else should I make sure I do or don't do with my computer in China?

Cheers.

---

### Post by GSF1200S on 2011-08-01
I would be careful using open WiFi- pretty easy to get passwords taken if the person wants to. Really though, thats anywhere. I would also get Tor setup on the computer and Torbutton for Firefox- the Chinese government blocks alot of websites, and they may be ones you choose to access. I would go a step further than merely encrypting home- I would put all passwords and personal information in a very heavily encrypted file container (like Truecrypt, or others). I would have all links to family members, photos of family members, etc in that container as well.

Of course, you could go crazy with this- setup a distro using only Openbox and a panel on EXT2 (non-journaling), have SELinux and IPtables configured to the hilt, use secure-delete for removing any files, use no-script if accessing a website with a Chinese domain, etc.

Personally, I think much of the crap about the Chinese is BS- they are a good group of people and you probably wont have any issues. I do think they are a little more strapped for cash, and despite the country being run by a "communist" government, the economy is brutally capitalistic- watch the computer, watch any data that could be used to make money.

---

### Post by Wood Prof on 2011-08-01
Already have TOR ready to go.  Because of my paranoia I had already placed things I didn't want eyes on inside of a Truecrypt container.  I just don't want to get over there and have something happen that could have been prevented with a little preparation.

---

### Post by doas777 on 2011-08-01
personally i would pick up a new laptop just for the trip and put only stuff you will need on your trip on it. that way, if it gets stolen/comprimised/confiscated/etc you have no worries except how to get through the rest of the trip sans laptop.

Encryption makes governments nervous and some are more vocal about it than others. encryption carries a presumption of guilt to it (for no good reason, but it does...)  so it may be more of a problem then not. even if you put in the password for them, it will won't be until after weeks of analysis that they would declare you innocent.

I agree with GFS, the Chinese are just normal people like the rest of us, but totalitarian/authoritarian governments are not people, and trust in them is misplaced.

---

### Post by 3Miro on 2011-08-01
I would guess there are two ways to go about this problem.

1. Full encryption/security everything set to the highest "paranoia" levels. Don't access Internet directly, but set VPN (or some sort of encrypted proxy) to a trusted home machine and only have heavily encrypted traffic between you and that one. You will be able to access all web-pages and do whatever you will be protected.

2. They cannot take what isn't there. Clean the HDD (overwrite it with random numbers) and then make a clean install. Set a minimal installation, make sure you disable cookies and browser history. Either only access public "safe" sites of combine this with VPN or desktop export from a machine that is trusted at home. Your laptop should be nothing more than a terminal of the real machine at home.

---

### Post by GSF1200S on 2011-08-01
Good ideas listed here; there is an app called nwipe that can use a number of methods to securely wipe an entire hard drive.

I suggested EXT2 above due to the fact it is non-journaling; when you normally delete a file, you dont actually delete the file- the filesystem just denotes that the space where the file exists can be overwritten. Further, even if you use something like secure-delete to remove a file from a journaled file-system, it could still be recovered from the journal. EXT2+secure-delete = data gone.

Im pretty sure you could even setup a Custom Action in Thunar (a nice light file manager not requiring much of XFCE to use) which would allow you to right-click secure-delete a file. 

I like 3miro's suggestion though- setup a nice encrypted connection between the laptop and your desktop at home (running as a server), and use the laptop like a terminal. Add SELinux and IPTables to the mix if you plan on running on open wifi (though this a really bad idea security-wise)..

In terms of buying another computer for this task, you might consider a cheap netbook..

---

### Post by GSF1200S on 2011-08-01
> **doas777 said:**
> personally i would pick up a new laptop just for the trip and put only stuff you will need on your trip on it. that way, if it gets stolen/comprimised/confiscated/etc you have no worries except how to get through the rest of the trip sans laptop.

Encryption makes governments nervous and some are more vocal about it than others. encryption carries a presumption of guilt to it (for no good reason, but it does...)  so it may be more of a problem then not. even if you put in the password for them, it will won't be until after weeks of analysis that they would declare you innocent.

I agree with GFS, the Chinese are just normal people like the rest of us, but totalitarian/authoritarian governments are not people, and trust in them is misplaced.
I agree- I dont think youll have any issues with the people in terms of your computer security; I would worry far more about the government. That said, just like anywhere, im sure there are Chinese people with nefarious purposes ready to steal information from you..

---

### Post by kaldor on 2011-08-01
Treat China the same as anywhere. Just don't outright bash things which you know will cause problems. Without getting political, I think you will know what I mean.

China is a fairly safe place from what I hear.

---

### Post by doas777 on 2011-08-01
> **kaldor said:**
> Treat China the same as anywhere. Just don't outright bash things which you know will cause problems. Without getting political, I think you will know what I mean.

China is a fairly safe place from what I hear.
No doubt, but nowadays every country is getting a bit oppressive about incoming electronics. for instance US Customs and Border Enforcement has gotten particularly out of hand: [http://www.consumertraveler.com/today/warning-us-customs-and-border-protection-may-confiscate-your-laptop-and-pda/](http://www.consumertraveler.com/today/warning-us-customs-and-border-protection-may-confiscate-your-laptop-and-pda/)

I'd give the same minimalism advice to anyone traveling to any other developed country as well.

---

### Post by Bandit on 2011-08-01
> Traveling to China next month, thoughts on computer usage

Yea dont surf for porn.. Seriously..

---

### Post by PhillyPhil on 2011-08-01
I lived in China for several years.  No need to do anything different from any other country except consider the following:

- Have an encrypted VPN available if you'd like uncensored web access.
- Unlike in most other countries, the government helping domestic companies steal data/research is quite common (many companies are state controlled)

---

### Post by Inodoro Pereyra on 2011-08-01
Well, I don't know anything about encryption and stuff like that, but, if you're going to China, see if you can find something made in USA there...:p

---

### Post by drawkcab on 2011-08-01
I would not travel with any media that could be suspected as pirated in any sort of way.

I agree that this is what a netbook or tablet armed with only the essentials is for.

---

### Post by sammiev on 2011-08-01
If your software is all legal then no worries. You may want to use a VPN like the ones I'm posting below. GL :)

[Is there a Free VPN for Linux]("http://www.paulstechtalk.com/how-to-get-a-free-vpn-for-ubuntukubuntu/")

and

[URL="http://www.freeusvpn.com/free-pptp-vpn/"]
FREE US PPTP VPN[/URL]

---

### Post by SoFl W on 2011-08-01
Deleted by author

---

### Post by christopher.wortman on 2011-08-02
> **Wood Prof said:**
> I'm traveling to Shanghai and Nanjing in early September.  I will be visiting the Nanjing Forestry University and then a furniture expo in Shanghai.  There are two things I am concerned about.  Besides having the hard drive on my laptop encrypted (my preference and required by the university I work for), what else should I make sure I do or don't do with my computer in China?

Cheers.

If it is anything like Japan, the websites are heavily cencored. Buy a cheap used netbook from Ebay or local shop if you can afford it.This way if you get mugged you are only out a sub $100 computer lol.  Install Linux on it and make sure you don't have the ugly codecs installed, this way when they confiscate it and look for things like that they dont try to make an example out of you. In fact if you can do without one, just use the computers they have there. Stay off of tor, dont use torrents (even if they are legal), stay off of Google, use Bing if you can bear it. 

[http://www.ehow.com/how_2037819_use-laptop-china.html](http://www.ehow.com/how_2037819_use-laptop-china.html)

---

### Post by jtarin on 2011-08-02
Here's my two-cents on this.
[Read here]("http://www.informationweek.com/news/government/security/231002431").....[then go here for download]("http://www.spi.dod.mil/lipose.htm"). 135mb .iso (you can put it on a USB)

---

### Post by Kromgol on 2011-08-02
Wow, China eh? I have always wanted to visit the place myself as the culture, the people, everything seems so interesting there! I couldn't care less that it's a dictatorship or that they censor things.

Anyway, i don't think you will need to be too worried about getting hijacked or anything. Despite common belief, China is an extremely safe country for someone to visit, probably even safer than the U.S. where like half of the people are drug addicts and rob every person they see (GENERALIZATON).

The government won't be giving you that much hassle as long as you don't act like some crazy pro-democratic maniac that runs around in the street screaming that you want democracy.

Just use VPN or something if you want to access something outside of the chinese firewall, and encrypt data if you wish.
Though i find it really hard to believe that some chinese guy sits in a corner and awaits some random tourist that uses Wi-Fi or something to hijack the data.

People think too harshly of China, tbh it seems like a really great country.

---

### Post by rjbl on 2011-08-02
Quick advice is don't waste any of your baggage allowance hauling a 'puter into and around the PRC. There are loads, and loads, of public Internet access points *everywhere* even out in the back of beyond; access is unbelievably cheap, pennies per hour even in really swish hotels.

Set up a new webmail box with one of the global providers, recognise that there is a greater risk of Google checking through your email than some faceless goon in the State Security Department and enjoy. 

You will probably find that access to the whole WWW from your hotel's Internet Cafe is pretty much as free as it is at home. The PRC seems to have two DNS networks - one for local folks and one for visitors; so that the typical view that visitors take home is 'Site blocking? What site blocking?' I don't know about using Cybercaffs out on the street - you may find nervousness by their private-enterprise owners over allowing foreign devils loose on their networks - expect big smiles and 'Busy right now, come back in a coupla hours'

Whenever you get to feel really paranoid about Nasty Government Watching Your Every Cybermove try to remember that monitoring Cybercitizens, in China, or here in the Freedom Lovin' West or in, say, the autocratic Middle East is a vastly labour intensive job. The PRC has a ginormous population of highly connected citizens; sure it probably employs many more cyber-cops than the US or the UK but they sure as hell can't be everwhere 24/7. Just don't try to start a Revolution and, for heaven's sake, enjoy being there. The people are incredibly high energy and really nice folks, I promise you.

Hope this helps

rjbl

---

### Post by PhillyPhil on 2011-08-02
> **drawkcab said:**
> I would not travel with any media that could be suspected as pirated in any sort of way.

:D good advice when traveling to the USA (?) but not China!  If you can find someone who paid MS for their copy of Windows in China I'll but you a steak dinner!  You can buy pirated Windows for about $2 anywhere, even in shops on university campuses.> **christopher.wortman said:**
> If it is anything like Japan, the websites are heavily cencored. Buy a cheap used netbook from Ebay or local shop if you can afford it.This way if you get mugged you are only out a sub $100 computer lol.  Install Linux on it and make sure you don't have the ugly codecs installed, this way when they confiscate it and look for things like that they dont try to make an example out of you. In fact if you can do without one, just use the computers they have there. Stay off of tor, dont use torrents (even if they are legal), stay off of Google, use Bing if you can bear it. 

[http://www.ehow.com/how_2037819_use-laptop-china.html](http://www.ehow.com/how_2037819_use-laptop-china.html)

Shanghai is possibly the safest-feeling city I have ever been in my life (Nanjing's fine too).  Probably because the police are very, er, ''effective'', shall we say...
This advice is all well meaning I'm sure, but it's a bit weird: ''stay off Google''?! ''don't use torrents/tor''?! 
Why? What do you think might happen?
As for your stuff being seized, I think that is more likely to happen to you in the US than China, and it's certainly MUCH more likely to happen to a Chinese citizen than a foreigner.

> **rjbl said:**
> Quick advice is don't waste any of your baggage allowance hauling a 'puter into and around the PRC. There are loads, and loads, of public Internet access points *everywhere* even out in the back of beyond; access is unbelievably cheap, pennies per hour even in really swish hotels.



You can use any cafe anywhere, no problems at all, even in the darkest dingiest corners of the city you can find.  You need your passport, but you won't be turned away.  I wouldn't be viewing any secret/sensitive data there though.

---

### Post by jtarin on 2011-08-02
> **Kromgol said:**
> Wow, China eh? I have always wanted to visit the place myself as the culture, the people, everything seems so interesting there! I couldn't care less that it's a dictatorship or that they censor things.

Anyway, i don't think you will need to be too worried about getting hijacked or anything. Despite common belief, China is an extremely safe country for someone to visit, probably even safer than the U.S. where like half of the people are drug addicts and rob every person they see (GENERALIZATON).

The government won't be giving you that much hassle as long as you don't act like some crazy pro-democratic maniac that runs around in the street screaming that you want democracy.

Just use VPN or something if you want to access something outside of the chinese firewall, and encrypt data if you wish.
Though i find it really hard to believe that some chinese guy sits in a corner and awaits some random tourist that uses Wi-Fi or something to hijack the data.

People think too harshly of China, tbh it seems like a really great country.
Ha!! What planet do you live on.......visit or live there and you'll be talking out the other side.:p

---

### Post by Paddy Landau on 2011-08-02
> **jtarin said:**
> [Read here]("http://www.informationweek.com/news/government/security/231002431").....[then go here for download]("http://www.spi.dod.mil/lipose.htm"). 135mb .iso (you can put it on a USB)
Or you could, I suppose, do something similar by installing Ubuntu onto a flash drive.

---

### Post by mips on 2011-08-02
Talk about paranoia...

---

### Post by kaldor on 2011-08-02
> **Kromgol said:**
> People think too harshly of China, tbh it seems like a really great country.

I agree. It seems to be a fairly good place compared to many other countries out there. But with that in mind, there are still too many atrocities committed (and still occurring) by their government toward their own people to be acceptable imo. I can't get into too much detail on it here (CoC) but look around for yourself on Google to see what I mean.

---

### Post by Wood Prof on 2011-08-02
I'm not too worried about the people of China, I just didn't want to do anything dumb that would land me or my Chinese colleague in hot water. I already have a VPN setup though the university, so I shouldn't have any problem with access to websites.  The laptop I'm taking has very minimal data on it, and what is there is behind two layers of encryption.

---

### Post by kaldor on 2011-08-02
> **Wood Prof said:**
> I'm not too worried about the people of China, I just didn't want to do anything dumb that would land me or my Chinese colleague in hot water. I already have a VPN setup though the university, so I shouldn't have any problem with access to websites.  The laptop I'm taking has very minimal data on it, and what is there is behind two layers of encryption.

Then you have nothing to worry about. Just be careful in what you say in public or around officials, and remember the socialistic values of the country.

---

### Post by Kromgol on 2011-08-02
> **kaldor said:**
> I agree. It seems to be a fairly good place compared to many other countries out there. But with that in mind, there are still too many atrocities committed (and still occurring) by their government toward their own people to be acceptable imo. I can't get into too much detail on it here (CoC) but look around for yourself on Google to see what I mean.

I know, but China today is a lot better than it was under Mao's regime, just look at what happened when he tried to do the famous Great Leap forward. But i gotta say, most chinese people seems a lot happier and open than your average american, don't you agree?

If i had to decide which place i would live in or spend some time in, i would take China over for example our "shining beacon of democracy" USA.

> **jtarin said:**
> Ha!! What planet do you live on.......visit or live there and you'll be talking out the other side.:p

Sure, as China is vast country there will always be areas where the living standard will be worse. Especially in the rural areas of China, where approximately 55% of the population live. But thankfully the Chinese government has realized some of the problems of having an undeveloped countryside, and therefore has been focusing more on that, especially since Xiaoping came a long. They have been improved, but it's far from done as in some areas it's really hard to find running water, working roads and jobs.

And because of this, a lot of people have chosen to migrate to the urban areas of China to find work in some industry and hopefully have a better life than they had before, but working in an industry in China is still tough, as there's plenty of industries that are not regulated enough when it comes to enviroment/health safety etc.

Life in China isn't easy, but you can't deny that it has become better and better since Mao's time, and i still think China is one of the most beautiful country of all countries in the world. They got such an amazing history behind them as well, with the first dynasty being established 2600 B.C! Their history is far more interesting than America's history, European history or a like can become. The only history that i slightly compare to being as good as the chinese one is the roman empire.

You know, i used to think like you. I was like "Sucks that the communist party ruined such a beautiful country!11!1!", but once i read up on more and more on China, i realized that it was far better than i originally though. Damn, i even wrote a whole essay about the state of China and their improvements some months back.

I'm afraid most people still think that a state that has a dictatorship is bad. Sure, a dictatorship isn't perfect, but is a democracy perfect? Far from.

If China was to move from a dictatorship to a democracy in a small amount of time in for example a revolution it would heavily unstabilize the country and the following regime could even become "worse" than the other one. China will most probably move over to a democracy, but i'm able to say now that this won't be happening for quite some time.

Yes, i have not visited China, that one is true. But i do have some insight from my reading and watching, and i can't have everything wrong.

The generation that is now growing up in China are the ones that are going to rule the country tomorrow, and they are the ones that will make the country even better, wether it be through a democracy or a dictatorship. Nowadays the ones that have an important position in the communist party are remnants from Mao's time and some new fresh blood are needed at the top.
 
Without Deng Xiaoping, the China we have today wouldn't exist. I thank him for bringing a more capitalist model into China as a pure socialist/communist society would never work (Which i will try not to talk about more in here).

I hope you understood my summarized POV and why i think what i think.
Sorry for going off-topic, i felt it was necessary.

---

### Post by kaldor on 2011-08-02
> **Kromgol said:**
> I know, but China today is a lot better than it was under Mao's regime, just look at what happened when he tried to do the famous Great Leap forward. But i gotta say, most chinese people seems a lot happier and open than your average american, don't you agree?

If i had to decide which place i would live in or spend some time in, i would take China over for example our "shining beacon of democracy" USA.


Agreed about the improvements entirely. However, I'm not American so I can't really say anything on that :)

It also depends on the area of China you live in, though. I hear that the smaller communities have a lot of corruption and problems with officials as compared to the larger areas. Though I doubt living in a large city in China would be much different than living in New York, Ottawa, or what-have-you; it's still modern and developed.

---

### Post by Kromgol on 2011-08-02
> **kaldor said:**
> Agreed about the improvements entirely. However, I'm not American so I can't really say anything on that :)

It also depends on the area of China you live in, though. I hear that the smaller communities have a lot of corruption and problems with officials as compared to the larger areas. Though I doubt living in a large city in China would be much different than living in New York, Ottawa, or what-have-you; it's still modern and developed.

Yeah, i guess it's a lot harder to have control over all communities and such in such a big country as China. I'm guessing a lot of areas are kinda autonomous, and have a small government of their own.

---

### Post by kaldor on 2011-08-02
> **Kromgol said:**
> Yeah, i guess it's a lot harder to have control over all communities and such in such a big country as China. I'm guessing a lot of areas are kinda autonomous, and have a small government of their own.

I believe they have their local-level government (forget the terms on it) and that's where the corruption stems from; power-high or greedy officials who can abuse their power.

---

### Post by Kromgol on 2011-08-02
> **kaldor said:**
> I believe they have their local-level government (forget the terms on it) and that's where the corruption stems from; power-high or greedy officials who can abuse their power.

Well, guessing it's the way of life in most undeveloped parts of every country.

---

### Post by tgalati4 on 2011-08-02
I would be more concerned about the food than your computer.

---

### Post by Kromgol on 2011-08-02
> **tgalati4 said:**
> I would be more concerned about the food than your computer.

Really? I would love to taste the Peking duck :D

---

### Post by doas777 on 2011-08-02
I knew a guy who spent a month studying the culture in China during college. on his second week he ate at a McDonalds, got food poisoning, and spent the next 2 weeks in the state-run hospital.

---

### Post by smellyman on 2011-08-02
I am in China all the time.

everything will be ok.

although it is nice to know when you're in the US, the us government and google aren't spying on you.

---

### Post by sandyd on 2011-08-02
> **Wood Prof said:**
> I'm traveling to Shanghai and Nanjing in early September.  I will be visiting the Nanjing Forestry University and then a furniture expo in Shanghai.  There are two things I am concerned about.  Besides having the hard drive on my laptop encrypted (my preference and required by the university I work for), what else should I make sure I do or don't do with my computer in China?

Cheers.
a) get some blocklists to block idiots & bad guys. Don't get too many, or it won't work properly. : [http://www.iblocklist.com/lists.php](http://www.iblocklist.com/lists.php)

You can use MoBlock if you want for blocklists, its a nice app and already comes preloaded with a list of blocklists.

Choose level1, dshield, and anything else you want.

b) Big daddy is watching. Invest, or setup an encrypted VPN. Their like 5-10/m

c) After you setup a VPN, you can surf on open wifi networks, or any network, and you don't need to worry about a single thing.....

If you want to be cheap, setup a SSH Proxy, so that you can connect to the internet through SSH.

---

### Post by rajeev1204 on 2011-08-02
Talk about paranoia.

---

### Post by jtarin on 2011-08-02
> **rajeev1204 said:**
> Talk about paranoia.Is this comment gleaned from your personal experience in China or its just your surmising about the amount of protection?

---

### Post by PhillyPhil on 2011-08-02
> **kaldor said:**
> Agreed about the improvements entirely. However, I'm not American so I can't really say anything on that :)

It also depends on the area of China you live in, though. I hear that the smaller communities have a lot of corruption and problems with officials as compared to the larger areas. Though I doubt living in a large city in China would be much different than living in New York, Ottawa, or what-have-you; it's still modern and developed.

They're *partly* modern and developed.  It's a very different experience from a western city.  Corruption is rife everywhere, btw.  You quite literally cannot conduct business without encountering it.

I suggest the OP ignore almost everything in this thread. The vast majority of posts are paranoid babble, making no sense whatsoever, based firmly on people's complete ignorance (lack of knowledge) on the subject.
(And to avoid being asked, yes, that is based on years of living, studying and working in China)

---

### Post by rajeev1204 on 2011-08-02
> **jtarin said:**
> Is this comment gleaned from your personal experience in China or its just your surmising about the amount of protection?

I repeat, talk about paranoia.

---

### Post by jtarin on 2011-08-02
> **rajeev1204 said:**
> I repeat, talk about paranoia.I would have a tendency to agree with you to a point....but the country in question is not at all what they want you to think they are and precaution is a good by-word.

---

### Post by rajeev1204 on 2011-08-02
My advice to the OP.

1.Whenever travelling abroad ,take tips from someone who has travelled there.
2.Respect local traditions and laws

Unless the OP is a pro democracy blogger or activist,i dont think he has anything to worry about.
Though in this case they wont give you a visa either :D

He is on a visit to a university for god's sake.

---

### Post by Metallion on 2011-08-03
> **christopher.wortman said:**
> If it is anything like Japan, the websites are heavily cencored.

Who told you this rubbish? I've been living in Japan for over a year and I don't know about a single censored website.

---

### Post by jtarin on 2011-08-03
> **Metallion said:**
> Who told you this rubbish? I've been living in Japan for over a year and I don't know about a single censored website.And if they do it right you won't.:P

---

### Post by linuxforartists on 2011-08-05
Speaking of paranoia:

[China requires cafes, restaurants that offer public Wi-Fi to install spyware]("http://www.nytimes.com/2011/07/26/world/asia/26china.html")

That being said, the PRC has a track record of announcing privacy invasions like this, then sometimes backing off.  For reference, look up the outcry over "Green Dam Youth Escort."

Speaking as someone who's lived in China--I once worked in Shanghai--the country is much safer than the United States, but not as safe as Japan or Singapore.  Scams are common, such as "art students" who pretend they just want to practice their English, but then drag you to an overpriced art store or tea shop: [How Kevin Rose (CEO of Digg.com) and Glenn McElhose got scammed in China]("http://www.fourhourworkweek.com/blog/2009/10/08/random-episode-6-how-kevin-rose-and-glenn-mcelhose-got-scammed-in-china-ha/") (video).

From a traveler's point of view, go to China for the famous landmarks: The Great Wall, the Terracotta Warriors of Xi'an, etc.  The food is awesome as well: Beijing roast duck, Sichuan kung pao chicken, Shanghai xiaolongbao, Hong King dim sum, ah the mouth waters!

But to learn about Chinese culture, go to Taiwan.  When the Communists took over, the retreating Nationalists basically wrapped up traditional Chinese culture in a package and shipped it over to Taiwan.  You can find masters of martial arts, crafts, and other practices that went extinct on the mainland.  The people are lovely, easily my favorite aspect of that place.  Here's a great video I like to share: [Taipei]("http://youtu.be/Y-V5q6L8igM") (video). Here's another awesome one: [Time for Taiwan - My Beautiful Island]("http://www.youtube.com/watch?v=ncU6_jG4P7Q&feature=share") (long video, but I love it)

Personally, I think the average computer user has as much to fear from tech firms like Facebook as from the PRC government: [Beware online "filter bubbles"]("http://www.ted.com/talks/eli_pariser_beware_online_filter_bubbles.html") (TED Talk video)

If you're interested in more, you can check out my travel blog at [Marcus Goes Global]("http://www.marcusgoesglobal.com/").  All my stories and photos of Asia are there.  Use the contact form on my blog to e-mail me if you have questions.  Have fun in China!

---

### Post by whatthefunk on 2011-08-08
I lived in China for a while.  Dont worry too much about it.  Be sure theres no porn on your computer when you enter the country.  Dont smuggle drugs in.  Start bargaining at around 50 cents.

---

### Post by kaldor on 2011-08-08
> **Metallion said:**
> Who told you this rubbish? I've been living in Japan for over a year and I don't know about a single censored website.

Maybe he's thinking about South Korea.

---

### Post by whatthefunk on 2011-08-08
> **kaldor said:**
> Maybe he's thinking about South Korea.

Ive spent a few years in South Korea as well...wont find much censorship there.

---

### Post by smellyman on 2011-08-08
> **kaldor said:**
> Maybe he's thinking about South Korea.
 
and you're thinking of North

---

### Post by kaldor on 2011-08-08
> **smellyman said:**
> and you're thinking of North

Nope, [_pretty sure_]("http://en.wikipedia.org/wiki/Censorship_in_South_Korea") I was thinking about the [_South_]("http://joongangdaily.joins.com/article/view.asp?aid=2929934"). 

Japan has quite light censorship laws. I've often found people confuse SK for Japan when it comes to things like this, both being modern nations.

---

