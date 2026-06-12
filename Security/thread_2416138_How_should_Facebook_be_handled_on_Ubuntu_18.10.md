---
title: "How should Facebook be handled on Ubuntu 18.10?"
date: 2019-04-05
forum: Security
---

### Post by smith73 on 2019-04-05
I tried to register several FB accounts from Tor and an email on Tor and needed to disable 3 Facebook Container addons for Tor as otherwise Facebook would not function.
And Facebook still disabled my accounts although I implemented other FB security requirements (as I suppose it noticed some "suspicious behaviour").

I was advised to use Mozilla and Chrome for Facebook, but it seems dangerous in regard to FB tracking.

Can someone advice on how to handle Facebook on Ubuntu 18.10?

---

### Post by TheFu on 2019-04-05
Use ipset to block these subnets in your Linux filewall: [https://ipinfo.io/AS32934](https://ipinfo.io/AS32934)
Use something like pi-hole to block the DNS domains. Use the regex patterns for the best coverage.

Finding all the external content acceleration networks will be harder. A few are below:

If you want to stop facebook tracking, then add these lines to your /etc/hosts file on every system you want to prevent it after you've done the items above. All 3 steps are necessary.
```

127.0.0.1       ads.ak.facebook.com.edgesuite.net
127.0.0.1       creative.ak.fbcdn.net
127.0.0.1       external-lhr0-1.xx.fbcdn.net
127.0.0.1       external-lhr1-1.xx.fbcdn.net
127.0.0.1       external-lhr10-1.xx.fbcdn.net
127.0.0.1       external-lhr2-1.xx.fbcdn.net
127.0.0.1       external-lhr4-1.xx.fbcdn.net
127.0.0.1       external-lhr5-1.xx.fbcdn.net
127.0.0.1       external-lhr6-1.xx.fbcdn.net
127.0.0.1       external-lhr7-1.xx.fbcdn.net
127.0.0.1       external-lhr8-1.xx.fbcdn.net
127.0.0.1       external-lhr9-1.xx.fbcdn.net
127.0.0.1       fbcdn-creative-a.akamaihd.net
127.0.0.1       fbkmnr.112.2o7.net
127.0.0.1       fbtrack.webtrekk.net
127.0.0.1       fbtrk.com
127.0.0.1       ffbqk.voluumtrk.com
127.0.0.1        facebookinc.122.2o7.net
127.0.0.1       ads.facebook.com
127.0.0.1       www.facebook.com facebook.com
```

There are probably a few more.

If you actually want to keep using facebook AND not be traced, I don't think that is possible.  I have some ideas, but they wouldn't be 100%.

---

### Post by Tadaen_Sylvermane on 2019-04-07
not wanting to be tracked + using facebook is an oxymoron I think. it doesn't make sense.

at the end of the day their entire business model is based on tracking you. if you stop it, they won't let you use it. if it was built on anything else then there would be a fee to use the service. facebook isn't free. your life and data is the payment.

---

### Post by smith73 on 2019-04-07
Don't know about how someone's "life and data" can bring much consistent revenue to Facebook, especially if Facebook knows nothing about certain ranges of meaning for these terms (otherwise they'd all be Nobel laureates at Facebook). Although in such a thing as "Facebook University" there was a presentation of a very prospective researcher for these terms, but they have no idea on how to apply his research to humans.

It may be somewhat ok to use Facebook on Tor, but I suppose Facebook tracks frequent IP changes or anything from Tor network? 
I was successfully using my one Facebook account, which I deleted later, on Mozilla, now I tried to open several Facebook accounts on Tor and failed, despite that I formally complied with FB registration requirements.
When I had 1 "Facebook Container"-type addon enabled on Tor, Tor didn't even open the main Facebook page.

I have no idea of what Facebook actually tracks for. What does Facebook track for? If it is only the pages opened in a browser, it may be somewhat ok to clear up caches etc with bleachbit before using Facebook on Mozilla with relevant addons. Can FB track the content of Google email used for registration? 

I need FaceBook to join several groups and am not going to spend much time there.

---

### Post by DuckHook on 2019-04-08
I agree with Tadaen_Sylvermane:

With few exceptions, when it comes to practically all social media (not just Facebook), *you* are the product. Therefore, the moment you sign up, you are tacitly agreeing to have them deconstruct your private life and sell the analysis of your private info to all and sundry.

They don't need to physically track you in order to leverage your private data. Therefore, TOR is largely pointless.

Even if you manage to get TOR working, you might marginally lower your value-as-product to them, but the idea that you can isolate yourself from their business model while continuing to benefit off of them is disingenuous.

One of the biggest societal issues with all social media is how opaque they are to examining how they abuse our data. You want to know what Facebook tracks for? Good question. But how are ***we*** supposed to know? You are asking the wrong people. The very issue at stake is that we all *ought* to know—or at least have access to that knowledge—but do not (and not for lack of trying). Facebook has demonstrated time and again either their contempt for or negligence of our privacy. Cambridge Analytics, anyone?

So, if you want to use Facebook, you will be in good company. After all, over a billion other people do. Just don't fool yourself about it, and be aware that they have invented ways of exploiting your data that have now pushed them into the exosphere of corporate valuations. You can comfort yourself with quips about Nobel laureates, but Facebook is laughing all the way to the bank leveraging the very data that you don't think "can bring them much consistent revenue".

---

### Post by huff2 on 2019-04-08
Why spend the time collecting data to analyze a network when you can just have people give it to you? The network then builds itself. Stay away from all social media if you don't like being tracked. The uses are beyond the scope of this conversation. My (experienced) advice to you: Don't put in the effort except for the possibility of learning something new. You will not succeed in having access to Facebook while not giving them any data. You should put more effort into controlling what you put on Facebook. ie posts, photos, strong opinions, etc. 

That said, I use Facebook ... whatever lol.

---

### Post by smith73 on 2019-04-08
When the abstractions like the two above-mentioned are being produced, it is more likely that their direct cause has been a transient epileptic discharge in certain areas of the brain (which is normal and which I won't discuss here) rather than some type of "objective truth". 

I obtained the link to this forum from Ubuntu installation tips, so may suppose that my knowledge of C++ doesn't exceed 5% of the majority's of the forum and my knowledge of IT - ~30%. 

I used Facebook for several months probably on Mozilla Windows 90% for reading during which I mainly:
1) didn't click on a single ad;
2) didn't accept any Facebbok recommendations sent via email;
3) joined several groups links to which I obtained not via Facebook and friended some folks from them;
4) wrote ~2 comments in one group and posted a question in another;
5) posted one comment regarding Maxwell's equations on one MD's post in which they were mentioned;
6) posted in my profile a photo of "myself" made on the basis of currently non-existent optical technology;
7) posted a (private) post in my profile with a message ~"Facebook is a bucket of bs".
8) deleted this Facebook account (to which main interface I still can login and get the FB message in the upper menu bar that there are some errors with this account).
So can you tell how much revenue was produced for Facebook as a direct result of these actions?

I want to use (95% read) several Facebook groups and several pages for educational purposes and your use of the term "data" is highly vague. I didn't use Facebook a lot and may have missed something, just curious.

---

### Post by huff2 on 2019-04-08
Smith73 - I'm completely confused by your last comment. If you want to use FB then use it. I use it. Millions use it. I use it to stay in touch with former associates in groups. 

"When the abstractions like the two above-mentioned are being produced,  it is more likely that their direct cause has been a transient epileptic  discharge in certain areas of the brain (which is normal and which I  won't discuss here) rather than some type of "objective truth". " - What does this mean exactly? What are you referring to? 

Everything is data, by the way. Were you looking for specific examples? Its rather obvious. Your name is data. Your pictures. Your links. All of it. That's literally what data is in the data science community. It's either qualitative or quantitative. 

Also, nothing to be hyper-concerned about. Everyone here is simply saying that companies want data, lots of it. No, they don't necessarily know what they are going to do with it. That is the job of a data analyst. Sometimes correlations exist, sometimes they don't. Sometimes it's useful. Sometimes it's not. Sometimes it correlates but the correlation means nothing as to a cause. Yes, that should sound vague. These are general terms not specific examples. 

It also depends on WHO is doing the collecting. Some companies may see a need to collect only certain types or specific data points, others may just collect everything they can get their hands on and store it in a massive database. Governments from local to national to global do this all the time. As far as FB, I have no idea what they do with it or who they sell it to. I'm sure there are reports and theories about that. 

I have worked with data professionally in a few different areas. I have seen different uses, interpretations and opinions about what to even collect. When I worked in company-level intelligence in the military I saw many different uses, most of which was for analyzing a social network or simply stock piling weather patterns from everywhere. Then, after that, I worked in journalism for 8 years and saw too many uses to mention. Then, I was a general manager and used data to help me make better decisions. 

"So can you tell how much revenue was produced for Facebook as a direct result of these actions?" - No, I can't. Of course I can't. I don't do quantitative analysis for FB. But, I can guarantee that someone can give an estimate. There are so many ways to give you that estimate. Welcome to finance. Margins, KPI's, etc are created all the time to serve a specific purpose. Sure there are commonly used concepts. Assume that Facebook knows that it has in collection 100 data points, this could be of anything. The company also knows how much in revenue it generated during the time these points were collected, say 100 dollars. Then, anyone can say that they make $1 per data point (this would be a margin, a crappy one but this is the idea.) You listed 8 points. That's 8 dollars made off of you. This IS how data is analyzed. It is obviously more complex than my example. But that is essentially it. They could also say that they have 100 profiles. That's $1 per profile. This revenue/profile margin can be then marked as a KPI. Then they can set a goal to push this KPI up 10%. How can we do that? Well, based on your KPI, you would want to increase the number of profiles. BUT, lets say you increase to 200 profiles but the revenue doesn't increase. Then your KPI would be 50 cents. Then, you want to analyze why. Maybe your initial assumption that there was a correlation between profiles and revenue is wrong. Correlation is not Causation. This would mean that your KPI is incorrect. Welp, back to the drawing board. 

This is literally endless. There are no set rules. Maybe general good practice guidelines. But, ultimately no rules. You can interpret it however you want. Which is why we need to be very careful when the media reports on a new study. They could very easily be misrepresenting the analysis of the data that was collected. 

So, no one can give you a specific answer to your question. The point is, FB wants to track you. If you don't let them, then they will try to indirectly pressure you into "giving in" to using channels to access their content that allows them to track what they want. It's really that simple.

---

### Post by wildmanne39 on 2019-04-09
I know of no way, a few weeks ago I signed in with TOR and my account was immediately locked and I had to go through a verification process without TOR to regain access, if you want to use their site then you will be data mined, I personally would recommend just doing away with facebook if you do not want to let them know everything you are doing which includes private messages.

---

### Post by TheFu on 2019-04-09
The real issue with all social networks and advertising tracking is that there isn't an opt-in process.  Everyone is opted-in, without proactive consent.  Look at any "Like" button you see anywhere.  That is facebook tracking you, even if you aren't logged in.  The "like" button image is custom and allows them to figure out who you were last time they saw you **anywhere** else on the internet.  

The only possible way that you could use facebook and not be known is to 
* never use it outside a tor browser.
* never use any other account in that same tor browser session - don't visit google, don't visit any sites that have **any** tracking at all.
* don't allow any data to be saved locally, which means no cookies, no "local objects" which are part of flash and html5 standards.
* never trust "incognito modes" in browsers. Time and again those have had bugs that leaked. It takes just 1 leak and your veal is broken.
* never use the same email address(es) that facebook knows about **anywhere** else.  Do not check those emails outside of TOR.

So, basically, an average person would need to use read-only media and boot from that, with tor browser installed onto it, and only use that to log into any social network.  They'd also need to create a fresh DVD with a new copy of a TOR OS every 2-6 weeks, just to get any patches which close newly discovered TOR issues.

These same techniques are mandatory for any facebook-owned tools like "messenger" - they might claim not to share data.  I don't believe them.

Same for google.  Actually, I believe google is much worse, but just hasn't been caught because they are better at security.  Better, not perfect.  No way, no how, will you find the Chrome browser on any of my systems.  MSFT is switching to a chromium-based browser and had to remove over 50 connections to back-end google services.  [https://www.theverge.com/2019/4/8/18300772/microsoft-google-services-removed-changed-chromium-edge-browser](https://www.theverge.com/2019/4/8/18300772/microsoft-google-services-removed-changed-chromium-edge-browser)  I'm reconsidering using chromium, even for emergencies like airline, hotel, and banks inside a linux container, using a VPN.  Wish there was a good answer. Perhaps there is but I just haven't figured it out yet.  Too bad lynx and dillo don't work.

And if you use a smartphone, even having any of these social apps installed is failure enough. We don't need to ever use them.  Facebook has been caught gathering data on smartphones from non-facebook users.

---

### Post by huff2 on 2019-04-09
TheFu - Wow! That article is shocking. Thanks for sharing. What's really scary, to me, is that even if you decide to wipe yourself all that stuff and crawl into a virtual hole, coming out only to explore the streets in the shadows at night, you can never erase what they already have and will always have. In the S-2 shop I heard guys talk about how their is so much data that even the algorithms to sort it are ridiculously technical and WHAT the goal is or WHAT needs to be sorted out is just insane. I heard people say that the fear of missing something is in a world of constant data flow and extremely gifted individuals are asked to work on algorithms just to try and determine what is even important. It's seriously crazy. A hoarders mindset - "We're just going to keep that, may need it, don't know. Maybe will throw something else away." In the end, all is kept.

---

