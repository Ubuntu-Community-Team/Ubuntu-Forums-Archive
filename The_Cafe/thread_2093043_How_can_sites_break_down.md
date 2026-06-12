---
title: "How can sites break down?"
date: 2012-12-09
forum: The Cafe
---

### Post by nec207 on 2012-12-09
How can massive sites like yahoo groups ,yahoo answers , photobucket and youtube break down.
 
It seems when I go to youtube now every thing is out place and pushed down.Some times yahoo groups ,yahoo answers have major problems.
 
The popular sharing sites like photobucket some times show up broken URL's and webshots move to update software ( called smile ) broke all URL's and site is in crisis mode.
 
Over past some months yahoo is been having major problems.
 
**Can some one explain the software engineering and why things like this happan.**

---

### Post by KiwiNZ on 2012-12-09
Nothing made by man is perfect.

---

### Post by TheFu on 2012-12-09
> **nec207 said:**
> How can massive sites like yahoo groups ,yahoo answers , photobucket and youtube break down.
 
It seems when I go to youtube now every thing is out place and pushed down.Some times yahoo groups ,yahoo answers have major problems.
 
The popular sharing sites like photobucket some times show up broken URL's and webshots move to update software ( called smile ) broke all URL's and site is in crisis mode.
 
Over past some months yahoo is been having major problems.
 
**Can some one explain the software engineering and why things like this happan.**

Running a large site across the world is complex. Complex things often break. Sometimes they break for hardware reasons, other times for human error and lastly for software errors in code or configuration.

There is also internet issues - DNS failures, routing, local issues from your ISP, governments blocking things - China has a history of accidentally black holing large parts of the internet for the entire world - when they were just trying to maintain their "great firewall."  Accidents happen.

When bad things happen, people become involved and route around the issue if that is possible.  If your country internet access is government controlled, there may not be any way to get around the issue.  There was an article this week about the total number of different connections to the internet that each country has and who actually owns them.  There was a much too large list of countries with either 100% government controlled internet or with very few private companies controlling it. It was scary to me.

Without inside knowledge for each and every situation you are complaining about, it is impossible to know what the specific issue was for the apparent outages you saw.  Further, it is unlikely that the largest sites have world-wide outages. Perhaps there infrastructure where your traffic gets routed is not working as desired.

Sometimes the data center provider has an outage - Amazon cloud and other "cloud service" provides have failures more often than we'd like too.

It gets complicated.  Designing redundant systems is not something you do without many years of experience.

I hope that helped a little.

---

### Post by lisati on 2012-12-09
Gettng all the parts working together as a coherent whole is no mean feat, particularly when you're talking about organizations such as Google and Yahoo. Sometimes I struggle just with what I've got hooked together on my home network.

---

### Post by nec207 on 2012-12-09
Is it just me or is other people here having problems with those web sites.

---

### Post by tgalati4 on 2012-12-09
First "ping" the site to see if you have an internet connection to it.

Open a terminal:

```
ping www.google.com
```

Hit Control-C to stop pinging.

If ping doesn't work, then you have no way to communicate with the site.  If ping works, but the site still does not respond, clear the cache in your browser or try another browser (firefox vs chrome) and see if the site is dead in both browsers.  If still dead, but the ping is still works, then you can be reasonably sure that the actual web server is down, but your internet connection to the remote service is OK.

Many sites have status indicators.  When gmail (google mail) was having problems you could see the status at this page:

[http://downrightnow.com/gmail](http://downrightnow.com/gmail)

Perhaps the services that you use have similar status pages?

---

### Post by TheFu on 2012-12-09
> **nec207 said:**
> Is it just me or is other people here having problems with those web sites.

I don't use most of those sites, so I haven't noticed anything wrong with them.  A user in Europe probably will visit completely different infrastructure than a user in N. America, or S. America or Asia, so it is hard to say.

For fun, what does **dig yahoo.com** produce for you?  Here's my results:
```
yahoo.com.              749     IN      A       72.30.38.140
yahoo.com.              749     IN      A       98.139.183.24
yahoo.com.              749     IN      A       98.138.253.109
```

The first result goes to San Jose, but the 2nd one goes to Washington and the 3rd also goes to Washington.  I didn't look too hard to see if that was DC or state. It is probably DC based on my Georgia location.

Running the same dig command a few minutes later, swaps each of those results around. This is just DNS round-robin load balancing. That is pretty easy.

---

### Post by nec207 on 2012-12-09
For the past 3 or 4 days youtube UI is messed up .There some thing wrong with the youtube UI .
 
It seems like 2 or 3 times month there are problems with yahoo groups and yahoo answers .

---

### Post by lisati on 2012-12-09
> **nec207 said:**
> For the past 3 or 4 days youtube UI is messed up .There some thing wrong with the youtube UI .
 
It seems like 2 or 3 times month there are problems with yahoo groups and yahoo answers .

No problems with Youtube noticed here.

---

### Post by SeijiSensei on 2012-12-09
YouTube changed its site design, but it's not "broken" in any way I can tell.

---

### Post by nec207 on 2012-12-09
> **SeijiSensei said:**
> YouTube changed its site design, but it's not "broken" in any way I can tell.
 
Are you saying youtube site got a new look? If so that that why it looks different.
 
Why is the title of the video not on the top?

---

### Post by CharlesA on 2012-12-09
> **nec207 said:**
> Are you saying youtube site got a new look? If so that that why it looks different.
 
Why is the title of the video not on the top?

It's below the video at least from what I have seen lately. I don't really go to youtube that often though and run with most of the scripts blocked.

---

### Post by haqking on 2012-12-09
You probably have NOScript running ;-)

---

### Post by nec207 on 2012-12-10
> **CharlesA said:**
> It's below the video at least from what I have seen lately. I don't really go to youtube that often though and run with most of the scripts blocked.
 
So it problem youtube is having?
 
Has for groups yahoo groups they seem to have a lot problems that yahoo for you .
 
[COLOR=black]You say you don't realy ue yahoo . What do you use for groups than? Reddit groups or google groups?[/COLOR]
 

[COLOR=black]The nice thing about yahoo groups ,google groups and reddit groups if you cannot find the topic of your interest you can make your own group.[/COLOR]

---

### Post by haqking on 2012-12-10
> **nec207 said:**
> So it problem youtube is having?
 
Has for groups yahoo groups they seem to have a lot problems that yahoo for you .
 
[COLOR=black]You say you don't realy ue yahoo . What do you use for groups than? Reddit groups or google groups?[/COLOR]
 

[COLOR=black]The nice thing about yahoo groups ,google groups and reddit groups if you cannot find the topic of your interest you can make your own group.[/COLOR]

usenet and thunderbird these days.

And as far as i know youtube are fine, i have seen no issues and i use it daily

---

### Post by AstroLlama on 2012-12-10
That's interesting, I've seen similar behavior from the sites you mentioned and others, too, but with much less frequency. I would say I very very rarely see graphical issues with those large sites.

---

