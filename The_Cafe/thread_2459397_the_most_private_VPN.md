---
title: "the most private VPN"
date: 2021-03-17
forum: The Cafe
---

### Post by Skaperen on 2021-03-17
IMHO, the most private VPN is one you run for yourself.  that may even be secure if you set up everything right.  i use openVPN for mine.

privacy and security are not the same thing.  i see an increased demand for VPNs when ads for commercial VPN services has hit rhe media.  can you really establish a trust relationship with any of the VPN providers?

---

### Post by DuckHook on 2021-03-17
Not to be argumentative, but how did you establish a trust relationship with Canonical? Could they not have built Ubuntu to report your every important piece of data back to them?

Most of us don't compile Ubuntu from source. We download an ISO put out by Canonical and just "trust" that they haven't hidden anything nefarious inside.

My point is that trust has to start somewhere. A pol once remarked: "Trust, but verify". This is good advice. Without taking that first step of trust, nothing could get started. But without verification, the unscrupulous will always be tempted to betray that trust. Nor am I saying that trust should be handed out indiscriminately. There are several tests that must be passed before we should consider trusting people. But those tests are vague and hard to quantify. As in life, extending trust in the IT-sphere is something of an art.

You are right in that the most private VPN is the one you run purely between your own client and your own server. But your private VPN is unlikely to be the one your doctor uses to store your patient charts. It is unlikely to be the one your accountant uses to store your financial statements. Nor will the bank, the newspaper, the government nor Ubuntu Forums consent to use your server for their business. In order to transact with practically any entity other than yourself, you must leave the confines of your own walled garden and brave the big bad world, hence the need for commercial VPN providers.

I do get your larger point. I have personally switched VPN providers because, over time, they failed the verification test. But my approach was not to distrust them; rather, it was to make a habit of periodically verifying all things that I tend to take for granted.

---

### Post by Skaperen on 2021-03-18
i established trust from history.  over time, either they were very good at hiding it from the world, or would have been caught by now.

---

### Post by aljames2 on 2021-04-03
So, what might one look for/at to verify a commercial VPN company isn’t straying from its original, marketed commitment.  When would you pull the plug on a VPN?

---

### Post by Skaperen on 2021-04-03
i really have no idea how to verify a commercial VPN company short of breaking in.  but, if i can break in, *game over*, i can't trust them.  but, really, i won't be trying.

---

### Post by Skaperen on 2021-04-03
as to Canonical and Ubuntu, it's the openness and the community that eventually establishes the trust.  there are many eyes and enough now that if they did try to hide some spy code, someone would notice and let it out.  so i don't really need to read the source code.  and i believe that, by now, hiding it in just distributed binary code, only, would still be eventually caught.  that, and they know there is a chance of being caught, so they are not going to try.

---

### Post by DuckHook on 2021-04-03
> **aljames2 said:**
> So, what might one look for/at to verify a commercial VPN company isn’t straying from its original, marketed commitment.  When would you pull the plug on a VPN?
Excellent question. See below.
> **Skaperen said:**
> i really have no idea how to verify a commercial VPN company short of breaking in.  but, if i can break in, *game over*, i can't trust them.  but, really, i won't be trying.
You both raise a truly vexing issue. One of the biggest problems with the proprietary world is that their ownership structure is impenetrably secretive. And where there is darkness, there is corruption. Evil festers when hidden out of sight. A "good" VPN could turn rogue overnight and we would be none the wiser. Two years ago, the VPN provider that I had relied on sold out to a scoundrel. The new owner had made his fortune producing malware and spyware. He was now in control of a large VPN provider. This smelled like three day old fish left out in the sun. I pulled the plug immediately.

The issue is exacerbated by other factors. If the VPN is headquartered in the US, it could be compelled by a court of law to turn over its logs to the authorities under a gag order, so they couldn't tell you about it no matter how much they might want to.

There are a few things that improve your chances:

[LIST]
[*]
[*]Use a larger VPN provider who has a lot of servers spread out all over the world.
[*]Make sure they are not headquartered in any of the five eyes or seven eyes countries.
[*]Make sure their ownership structure is unsullied,
[*]A really good sign is if they have been taken to court by a three&#8209;letter agency and have proven that they have no logs to hand over.
[*]In lieu of an actual court case, go with the one that regularly submits to third-party security audits and whose no log policies have been confirmed by reputable auditors.
[*]Subscribe to a few security mailing lists/channels to keep apprised of the latest in cyber&#8209;dangers.
[/LIST]
I have confidence in my current VPN provider, but it's not unlimited. It is a bad idea to trust any corporate entity unreservedly. Always be prudent in handing out your trust. If my current provider decides to forego their next security audit, or if third&#8209;party security sources start feeling queasy about them, then it will be time to go shopping again.

---

### Post by TheFu on 2021-04-04
Maybe don't trust SuperVPN & GeckoVPN.
[https://haveibeenpwned.com/PwnedWebsites#SuperVPNGeckoVPN](https://haveibeenpwned.com/PwnedWebsites#SuperVPNGeckoVPN)

I don't trust any free VPN services. When I'm looking, I want to know who the owner is - a real name of a real person. Where they are located. Where the VPN company is located - is that a trustworthy country/island?  Where is their staff located?  I've seen VPNs with CEOs in Europe, the company incorporated in Panama, and the support teams in Singapore and Hong Kong.  To me, that's multiple red-flags.  Certain countries/islands are known to harbor criminals - maybe avoid VPNs in those too, because if a govt won't hold people accountable for actions, there is no rule of law. For me, that's an important consideration.

I want a VPN with strong encryption, not weak.  I'd like multiple exit nodes around the world, since that's one of the main reasons I use a VPN for my research needs.  I want normal F/LOSS to be used, not some highly customized version.  Let me install openvpn or wireguard from anywhere I choose and have that work, just with slightly different configuration for each server.

I want a VPN that has been sued by the local govt trying to get access to data and for them to truthfully claim, "we don't have that data."   I want to pay for the VPN using untraceable methods.  For me, that's a "gift card" not tied to my name or location.

---

### Post by scorp123 on 2021-04-05
> **Skaperen said:**
> can you really establish a trust relationship with any of the VPN providers?

Depends on the jurisdiction under which the VPN provider operates, I guess? 

Me personally I'd never trust any VPN provider operating out of the USA or China or any territory that is politically attached to one of them (e.g. Puerto Rico, Hong Kong, etc.). Both have demonstrated again and again that they do not care about or respect the privacy of their own citizens, let alone foreigners. Both the US and China have established laws that allow a (secret) court to demand any information they want from anyone who is storing any data about you, e.g. your VPN provider, and that VPN provider isn't even allowed to inform you. 

So when choosing a VPN I'd go with one that legally operates under a jurisdiction where they have very strong data protection and privacy laws and a clear and transparent policy regarding what details exactly they are storing about you, which of your activities they are logging or not, and under what circumstances they would hand out those logs to foreign law enforcement agencies, if for whatever reasons it ever came to that. 

And always read the fine print: the VPN providers who claim they have a "no logs policy" ... if for example they are EU- or US-based they are probably lying to your face because those territories do have "data retention laws". They are legally obliged to keep logs, it would be illegal for them not to do it. If they claim they aren't doing it despite the legal requirements in their jurisdiction ... then they are very very likely lying. 

Just my 0.02€.

---

### Post by CelticWarrior on 2021-04-05
> [COLOR=#000000]Both the US and China have established laws that allow a (secret) court to demand any information they want from anyone who is storing any data about you, e.g. your VPN provider, and that VPN provider isn't even allowed to inform you.[/COLOR]

Correct about USA, incorrect about China.

Let me explain:
 In China any company must provide users' data whenever requested by the courts for any matter of national security, no secret laws or courts required, it's all done in plain view. And companies aren't required to deny it (and they couldn't anyway because it's a public matter). Failure to comply is cause to be forbidden to operate in the country. That's what happened to Google, Facebook and Twitter when they refused to give the data for the investigation of terrorist attacks while at some time they're doing it in a much larger scale at home (US) for no reason/merit.

---

### Post by TheFu on 2021-04-05
Seems there is some confusion about about US laws.

There **is** a FISA court. It has the ability to request data if there is probable cause for the request. It can prevent the recipient if the request from notifying anyone or taking proactive action to convey the same. 

It cannot force added actions. Look up "canary notice" or Canary Warrant, most reputable companies have canary pages. Those are updated periodically/quarterly to say they have NOT received any secret demands for logs or other data by the US govt.  [https://en.wikipedia.org/wiki/Warrant_canary](https://en.wikipedia.org/wiki/Warrant_canary)

VPNs in the US can also appeal these demands. They win sometimes, usually when the govt is fishing, not a specific enough reqest. In China, that isn't allowed. In Britain, Australia, France, Russia, we don't have the right to keep our passwords private. In the US, we do.  [https://en.wikipedia.org/wiki/Key_disclosure_law](https://en.wikipedia.org/wiki/Key_disclosure_law)  I tried to come up with a general rule for which countries respect keys and password privacy. It is imperfect, but basically, places that have lots of terrorist attacks aren't as privacy centered - that's not 100% - just a guideline for "western countries".  Not sure I can blame them. Northern European countries  seem to have strong privacy protections.

A few US-based VPN companies have successfully refused to provide logs in court. They won because they didn't have any logs. [https://www.reddit.com/r/privacytoolsIO/comments/8p4ox7/private_internet_access_nologging_claims_proven/](https://www.reddit.com/r/privacytoolsIO/comments/8p4ox7/private_internet_access_nologging_claims_proven/)
[https://www.techspot.com/news/82259-keeping-private-5-vpns-have-verified-keep-no.html](https://www.techspot.com/news/82259-keeping-private-5-vpns-have-verified-keep-no.html)  The US isn't alone.

It is true that a number of VPN services that claimed to be no-log were lying.

There are caveats. Logs exist for an active VPN session and for a few minutes after, then get deleted.  Reconnect every day and there is only the log for the last day available.  Reconnect hourly, if you want more privacy.  Most reputable VPN companies will have these spelled out. Some people are ignorant and don't read or understand the caveats.

Google fights against unreasonable data requests. [https://arstechnica.com/tech-policy/2017/09/justice-department-goes-nuclear-on-google-in-search-warrant-fight/](https://arstechnica.com/tech-policy/2017/09/justice-department-goes-nuclear-on-google-in-search-warrant-fight/)
I find it easier to block the 800+ google domains than worry. Same for facebook, twitter, and thousands of web tracking internet companies. I'd rather they didn't get any data. There are lots of ways to do this. in 2011:  [https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279](https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279)

---

### Post by QIII on 2021-04-05
> ... US ... have established laws that allow a (secret) court to demand any information they want from anyone who is storing any data about you, e.g. your VPN provider, and that VPN provider isn't even allowed to inform you.

This is factually *incorrect*, but it makes for great urban legend.  I can't speak for the laws in China, so I won't comment.

OK.  This has all been a *mostly* factual discussion of law surrounding an issue of importance to us geeky types, which is fine.  But let's not stray into the "shoulds and should-nots", attach moral or ethical discussions, nor speculate on the intentions of any government involved.  That will cross the line and cause this thread to be closed.

---

### Post by DuckHook on 2021-04-05
To further reinforce QIII's point, when considering jurisdictional issues, it is unnecessary to devolve into political judgmentalism anyway. Everyone has different needs, risks and objectives.

For example, I don't do anything illegal (like copyright&#8209;violating torrenting). So my use of VPN is not to evade the law. My primary concern is personality profiling. This is the process whereby nameless data agglomerators pervert browsers and insert tracking technology into apps in order to build a detailed profile of who you are and what parts of your personality can be exploited for their commercial gain. This information is then sold to all and sundry. A critical component of such tracking is your IP address and search history.

My secondary concern is identity theft/phishing, whereby scumbags build a detailed profile of who I am and then use it for nefarious purposes.

Therefore, in my case, a VPN that keeps logs and operates in a jurisdiction that subjects them to gag orders, though not ideal, would not be automatically disqualified. *Provided they don't **sell** that info to anyone*, the prospect of court&#8209;ordered government spying does not exactly fill me with dread and indignation. The use of even such a quasi&#8209;compromised VPN still effectively prevents such personality profiling by non&#8209;government actors, which is far and away my main objective.

Of course, if you are a dissident operating under a repressive regime, then your needs will be quite different. The point is that the tools must be chosen to serve the need. The drawback in many people's approach to VPN is their failure to firstly and properly assess their need.

---

### Post by scorp123 on 2021-04-06
To add to my previous post and all the friendly people who replied to it:  Yes, I may have oversimplified things... But the fact remains: You are more likely to get spied on in certain jurisdictions than in others. And that's what matters.

And by being a foreigner + non-citizen and by probably not being "in sync" with whatever is going on there except by reading about it in the news, chances are also you won't be able to prevent anyone from handing over any private information they might have about you to any other entity that has standing to make such demands...  By the time you learn about these things going on, it might already be too late. 

So the fact that I could e.g. maybe fight for my right to privacy in a court of law or maybe count on my VPN provider to do that for me.... I don't think that this is of any importance. It's just nice in theory but not really something I as end-user would want to deal with and waste time and money on. I just want my privacy and not anyone messing with it.

Being a customer of an US-based VPN provider might thus be attractive for US citizens: You live there, you are "in sync" with what's going on, you know where and how to quickly get a lawyer there, and so on. For me as an European living on the other side of the Atlantic this would be way too much of a hassle and highly inconvenient and therefore not attractive at all.

So when picking a VPN provider I absolutely think you should consider these things, no matter what the exact legal details are.

---

### Post by DuckHook on 2021-04-06
@scorp123

I agree with you up to a point. If we are shopping for a VPN provider, then we may as well choose one headquartered in a privacy&#8209;respecting jurisdiction.

However, when it comes to being spied upon, like most things in life, the details matter. In this case, they matter a lot.

[list=1]
[*]On these forums, we repeatedly get the refrain that the objective is to hide from three letter agencies. This is so unrealistic that it crosses over into silliness. If you are the specific target of a three letter agency, then hiding your IP address and surfing habits are the least of your problems. Outside of Hollywood fantasies, it is impossible for an average person to fight against or hide from such agencies. The only realistic avenue available to one under such surveillance is to cooperate with the agency and show them that one is harmless.
[*]On the other hand, if the objective is to avoid the attention of such agencies in the first place, then using a VPN can be counterproductive. In fact, if done injudiciously (as most people tend to do) it waves a red flag. Since the natural predisposition of such agencies is to suspect everyone, then using a VPN implies that you have something to hide. You are more apt to draw added attention to yourself than to attain your privacy objective.
[*]The only realistic way to curb the power of three&#8209;letter agencies is the political route—to have even more potent authorities limit their reach, whether these be courts, legislators or the weight of public opinion. 
[*]It is also theoretically possible to make hard encryption and privacy so widespread that it becomes pragmatically impossible to separate the wheat from all the chaff. The larger the ocean of anonymity, the easier it is to lose oneself within it. But this dynamic does not exist today.
[/list]
What makes #4 unrealistic is that the vast majority of people do not value their privacy. They may make noises that sound like they do, but these are self&#8209;delusions contradicted by both their conduct and their values. In fact, the vast majority are quite happy to sell their privacy for the technological equivalent of a mess o' pottage.

[list]
[*]If you have an account with Facebook, Whatsapp, Twitter, Instagram, Snapchat, Linkedin, WeChat, Baidu, Weibo or any of several dozen similar proprietary social media platforms, *you have sold your privacy*.
[*]If you use Gmail, Yahoo mail, Outlook mail, Apple mail or any other free e-mail platform, *you have sold your privacy*.
[*]If you use subscription services like Youtube, Chrome, Spotify, Kindle, Amazon Prime, OneDrive, Google Drive, iCloud storage, etc, *you have sold your privacy*.
[*]If you use Zoom, Skype, Hangouts, Duo, Facetime or any of the proprietary video chatting platforms, *you have sold your privacy*.
[*]If you buy stuff from Amazon, eBay, Alibaba, etc, then you pay them with not only your hard earned cash, *but with your privacy*.
[*]If you install dozens of apps from either the Google or Apple app stores onto your phone, or opaque proprietary apps onto opaque proprietary operating systems that are built to track you everywhere, everywhen and every&#8209;which&#8209;way, then *you sold your privacy a long time ago*.
[/list]
In the face of such widespread privacy&#8209;killing wilful self&#8209;destruction, it is difficult to see most people's VPN usage as anything more than a sad joke.

Recently, numerous security experts have found that government three&#8209;letter agencies do not even bother to set up complicated data collection schemes anymore. They just buy whatever data they want on the open market from commercial entities that have already done their work for them. It turns out that even three&#8209;letter agencies, with all the resources of nation states behind them, cannot do better than the sheer efficiency, ingenuity and completeness that results from the profit motive.

These largely unknown data agglomerators and personality profilers do not do their dirty work using anything overtly underhanded—they build their profiles using data that the vast majority of people freely hand over to them. VPNs, no matter where their HQ, won't stop this any more than a curtain will hold back a tsunami.

***Summary:***

It is simply not the case that jurisdictional considerations are as important as people think. While a good jurisdiction does have some value, this is dwarfed by the other factors that compromise our privacy.

The whole field of privacy, anonymity and anti&#8209;profiling *is all about the details*. It is not about some tool. It is just as foolish to think that a good VPN will give us privacy as it is to think that installing AV will magically immunize us against malware. Since 99% of privacy is the result of personal behaviour, 99% of the solution must involve significant changes to personal behaviour. Most people will not only be uncaring, but will actively resist those changes because they have become addicted to the drugs that have been handed out to them in exchange for their privacy.

In contrast, those who are serious about protecting their privacy have no choice but to address themselves to the complex and frustrating details.

---

### Post by QIII on 2021-04-06
As I said, discussion of whether a jurisdiction should or should not "spy" on its citizens is something we will not allow here. But there is a further consideration beyond the very detailed comments above, and I say this over and over:

It takes from 3 to 5 government analysts to track/surveil any given person of interest.  Add to that supervisors and those who surveil all of them ... You can quickly see how unlikely government surveillance is to be bothersome to any normal individual.  If the word "bomb" pops up in your communications and they rewind the tape to find that you were discussing with your spouse the cute littly "dooty bomb" your baby just dropped -- well, you just got your name off of every government's list of interesting people forever.


As described above, add a profit motive and the game changes:  In the Western world, the danger to our privacy at the hands of commercial interests is greater by orders of magnitude than the danger posed by governments.  Say "dooty bomb" and every disposable diaper manufacturer will want your every detail.

I use VPNs to protect the *data* communicated back and forth with my clients to avoid corporate espionage or PII disclosure.  The selection of the VPN provider is usually theirs to make.  I like to use the username "Dooty Bomb" when I do that, by the way.  Three letter agencies hate that.  "Hah!  Made you look!"

---

### Post by CelticWarrior on 2021-04-06
> [COLOR=#000000]On the other hand, if the objective is to avoid the attention of such agencies in the first place, then using a VPN can be counterproductive. In fact, if done injudiciously (as most people tend to do) it waves a red flag. Since the natural predisposition of such agencies is to suspect everyone, then using a VPN implies that you have something to hide. You are more apt to draw added attention to yourself than to attain your privacy objective.[/COLOR]

Again, not applicable to China. Waving red flags is pretty much the national sport there and everyone under 45 and their dogs and cats uses a VPN.

---

### Post by Irihapeti on 2021-04-06
If you really think that someone is after you, whether it's your cousin, neighbour or TLA, then DON'T come here and spell out all the details of what's going on and - in particular - discuss what you can do about it. This is a public forum, after all.

It intrigues the number of people who do just this, and don't seem to realise that the cousin/neighbour/TLA can read about their plans and then circumvent them. This also crosses into silliness.

---

### Post by QIII on 2021-04-06
*Your* cousin *is* after you, Irihapeti!  :)

---

### Post by DuckHook on 2021-04-06
> **QIII said:**
> *Your* cousin *is* after you, Irihapeti!  :)
Ahh… but just add a VPN and it will solve ***everything***. :^o

---

### Post by Irihapeti on 2021-04-06
> **QIII said:**
> *Your* cousin *is* after you, Irihapeti!  :)

> **DuckHook said:**
> Ahh… but just add a VPN and it will solve ***everything***. :^o

:lolflag:

---

### Post by scorp123 on 2021-04-07
> **DuckHook said:**
> 
 On these forums, we repeatedly get the refrain that the objective is to hide from three letter agencies. This is so unrealistic that it crosses over into silliness.
Depends on how you go about it I guess? But yes, I understand what you mean.

> **DuckHook said:**
> 
 The only realistic avenue available to one under such surveillance is to cooperate with the agency and show them that one is harmless.
I disagree with that one. I shouldn't have to prove my "innocence" just because they feel like suspecting me of something. It's their job to prove me of being "guilty" of whatever it is they want to accuse me of. "Innocent until proven guilty" is how it works in civilised countries.

> **DuckHook said:**
> 
 On the other hand, if the objective is to avoid the attention of such agencies in the first place, then using a VPN can be counterproductive. In fact, if done injudiciously (as most people tend to do) it waves a red flag. Since the natural predisposition of such agencies is to suspect everyone, then using a VPN implies that you have something to hide. You are more apt to draw added attention to yourself than to attain your privacy objective.
Ah, the classical "Nothing to hide" argument?
[https://en.wikipedia.org/wiki/Nothing_to_hide_argument]("https://en.wikipedia.org/wiki/Nothing_to_hide_argument")

*"Arguing that you don't care about the right to privacy because you have nothing to hide is no different than saying you don't care about free speech because you have nothing to say."*
Edward Snowden.

> **DuckHook said:**
> 
The only realistic way to curb the power of three&#8209;letter agencies is the political route&#8212;to have even more potent authorities limit their reach, whether these be courts, legislators or the weight of public opinion. 
I'm on the other side of the Atlantic, I neither have the time, the patience, the power nor the money to go any of those routes. So that approach isn't viable for me.

> **DuckHook said:**
> 
In the face of such widespread privacy&#8209;killing wilful self&#8209;destruction, it is difficult to see most people's VPN usage as anything more than a sad joke.
True.

> **DuckHook said:**
>   It is just as foolish to think that a good VPN will give us privacy as it is to think that installing AV will magically immunize us against malware. Since 99% of privacy is the result of personal behaviour, 99% of the solution must involve significant changes to personal behaviour. 
Yes, I agree to that.

---

### Post by DuckHook on 2021-04-07
> **scorp123 said:**
> I disagree with that one. I shouldn't have to prove my "innocence" just because they feel like suspecting me of something. It's their job to prove me of being "guilty" of whatever it is they want to accuse me of. "Innocent until proven guilty" is how it works in civilised countries.
I don't think that we are fundamentally in disagreement here. I make no assertion that general surveillance is okay. The important condition in my statement was: "under such surveillance". This means someone already and specifically targeted. You are addressing a philosophical concern. I am addressing a pragmatic one. It's like the difference between one's legal right to be presumed innocent until proven guilty and one's pragmatic behaviour when pulled over by highway patrol. As aggrieved as one might feel, it would be unwise to be anything other than cooperative.
> Ah, the classical "Nothing to hide" argument?
Actually, this wasn't at all my point, but I can see how it can be misinterpreted as such. Were I to ascribe to the view you attribute to me, I would not be using a VPN. Since I do, then I clearly don't agree with the "nothing to hide" argument.

My point is that VPN usage *if used injudiciously* waves a red flag to agencies sniffing for suspicious behaviour. Various security professionals agree on this same point. In the situation that exists today, where the vast majority of people do not care about their privacy and the default behaviour is the exchange of reams of data in the clear, an encrypted exchange stands out like a sore thumb. This is not an "ought" statement; it is an "is" statement. It is an assessment of the reality that we live in.

I do not pretend to have a solution to the above other than what I stated in my point #3.
> I'm on the other side of the Atlantic, I neither have the time, the patience, the power nor the money to go any of those routes. So that approach isn't viable for me.
Actually, you have way more going for you than we do on our side of the pond. You have the GDPR. We have a hodge-podge of cobbled together legislation that varies from place to place and is generally toothless.

Perhaps my real point was lost in my sea of long&#8209;windedness and can be better expressed as follows (QIII has already alluded to it):

People are overly concerned about *government* surveillance when the far greater danger is elsewhere. The real danger is profit&#8209;driven personality profiling. When little&#8209;known data agglomerators assemble a frighteningly accurate picture of who we are, anyone—including governments—can access it to their advantage and to our disadvantage. The program that Snowden blew the whistle on, called PRISM, was 13 years ago and arguably unnecessary today. The same info on almost all of us is now available through companies like [Experian and Quantcast]("https://privacyinternational.org/long-read/4398/companies-control-our-secret-identities"), and has been analyzed, parsed and packaged so that anyone from marketers to insurance companies to political parties to banks to crooks to, yes, governments can buy it on the cheap. Do visit the above link. It is a sobering read. So, it's a matter of paying attention to the real problem rather than getting distracted chasing shadows:

[list]
[*]Being denied health insurance because all insurance companies have access to our DNA profile is way scarier (and a more realistic and urgent danger) than macho fantasies of Jason Bourne.
[*]Being denied a mortgage or a job because of projected character defects in our personality profile (as versus basing decisions on our real past conduct) is way scarier than any three letter agency.
[*]Being spearphished by scumbags because they know all about our personal interests and can craft a believable story of camaraderie over a "shared hobby" is way scarier than government surveillance.
[*]Having our bank accounts emptied out, two mortgages registered in our name and three cars bought on our credit due to identity theft is way scarier than illusory conspiracies.
[*]Being manipulated by political parties or unsavoury cults because they know our susceptibilities and exactly which of our buttons to push is way scarier than imaginary spies.
[/list]
I'll put it even more bluntly:

What is the point in dickering with a VPN and agonizing over government spying if one has five social media accounts; two free email accounts; subscribes to Youtube, Amazon Prime, Disney and Roku; uses Zoom, Skype and Hangouts; buys from Amazon, eBay and a dozen other online stores; and has a hundred apps installed from the Android or Apple store? I mean, really…. what would be the point? It would be a joke—a colossal waste of time. It would just be a way of beguiling oneself into feeling a false sense of privacy when one has already given the farm away through all of one's other conduct.

---

### Post by aljames2 on 2021-04-08
>  I mean, really…. what would be the point? It would be a joke—a colossal waste of time. It would just be a way of beguiling oneself into feeling a false sense of privacy when one has already given the farm away

I agree here.  I check a few of these boxes myself.  I haven’t wrestled with using an outbound VPN yet because it seems I’m raveled up in some of this.  My wife and I do not do social media thank goodness but we do stream content and shop online.  These companies have a way of sinking their claws into you with conveniences that are paid for with not only your money, but your privacy as well.

Unplugging oneself from these dependencies, or at least a major cutback, seems to be a good first step.

Of course, a remote access VPN to access a home network I think is always in order, but I know that’s not what we’re talking about here.

---

### Post by DuckHook on 2021-04-08
> **aljames2 said:**
> &#8230;we do stream content and shop online.
&#8230;
Unplugging oneself from these dependencies, or at least a major cutback, seems to be a good first step.

There are ways of streaming content that provide decent privacy. For example, one does not have to be signed in to Google to stream Youtube content. Google wants you to (guess why?) and will offer you lots of blandishments to sucker you into doing so, but so long as you resist the temptations, you can be relatively anonymous. The method that I often use is a separate browser&#8212;either Brave or Firefox, ***NOT Chrome***&#8212;running within a LXD container (you can run yours in a VM if that's more comfortable for you) that is automatically connected to a VPN. Do ***NOT*** sign this browser in to anything, least of all a Google account. Make sure the browser is set to delete all cookies at exit. For added privacy, install Ghostery or Privacy Badger. NoScript is even better, but some find it hard to configure. A browser hardened in this way can do double duty and stream more than Youtube. I also use mine for TubiTV.

If streaming a subscription service like Netflix, launch another browser instance in a separate container. Follow TheFu's strategy and lie. Do not sign up with your real name or your real e-mail address or your real cell number. When asked for your Mother's maiden name or your high school sweetheart, lie. When filling out your street address, lie. Payment is a problem. You can use an intermediary service like Paypal, but while this protects your actual credit card data, your identity is still shared with Netflix. More anonymous is a pay&#8209;as&#8209;you&#8209;go rechargeable credit card, but not all online services will accept those. More services are accepting bitcoins these days. It's an option, although I've never used it. The main takeaway is: lie, lie, lie.

How to keep track of all those lies? Use a password manager. All password managers that I'm aware of have extra fields within their databases that can hold exactly the sort of data that make up all those lies.

What about cell phone number and email addresses? You can't exactly use a fake one because many subscriptions will only activate after contacting or confirming you on those addresses.

For email, I use anonaddy. This service allows you to create proxy email addresses that are associated with your real email only on anonaddy's server. You can create a unique email for each subscription. If you ever want to stop a subscription, you can forever cut them off from bothering you again by deleting the proxy email address. This has the added benefit of showing you which vendors sell your email addresses to third parties. There are other similar services to anonaddy. I use them because they have a good app on FDroid and FDroid is our friend.

For cell phones, I use a cell proxy. These providers operate the same way anonaddy does for email. There are many, all findable through a simple websearch.

It is an impossible ask to not use online shopping these days. What with the rotating lockdowns and the sheer convenience, asking people to forego online shopping would be pushing on a rope. But even here there are ways to preserve your privacy. In tandem with the above strategies (lie, lie, lie, pay anonymously, lie some more), if you live within or near an urban centre, then you can have purchases delivered to a mailbox service. These are providers who will receive, warehouse and notify their customers of all deliveries. All you have to do is direct your deliveries to the address of the service and then pick it up upon notification of delivery. Yes, it costs money and it's not as convenient as having things dropped off at your front door, but the reality is that our privacy comes at a cost. One further benefit is that you will eliminate the criminal parcel heists that are exploding all around us.

---

