---
title: "Firefox and Chrome help Google track your online activities"
date: 2009-09-11
forum: The Cafe
---

### Post by t0p on 2009-09-11
Holy cow!  Have you heard about [this]("http://ha.ckers.org/blog/20090824/google-safe-browsing-and-chrome-privacy-leak/")?

Okay, maybe you don't care.  You don't do anything illegal or immoral, right?  Maybe so.  But remember: if you do something that any government, anywhere in the world, doesn't like, they can take Google to court in their jurisdiction to reveal what data they hold about you.  And if a court order Google to release data, Google *will* comply.  They help the Chinese government to track down and execute dissidents, so they'll certainly sell *you* out.

Incidentally, in Firefox you can deactivate this tracking system by going to **Edit > Preferences > Security** and untick **Block reported attack sites** and **Block reported web forgeries**.  Will this put you in danger?  Perhaps.  But I can't remember the last time Firefox warned *me* about an "attack site"...

---

### Post by -grubby on 2009-09-11
Look at it from Google's point of view: They either comply, or they can't offer their product in that country anymore. The latter isn't so great for business.

---

### Post by t0p on 2009-09-11
> **-grubby said:**
> Look at it from Google's point of view: They either comply, or they can't offer their product in that country anymore. The latter isn't so great for business.

I take it you didn't read the article I linked to.  The point is, Google are using individually identifiable cookies to facilitate the update process.  And they don't need to!  From [the blog]("http://ha.ckers.org/blog/20090824/google-safe-browsing-and-chrome-privacy-leak/"):

> Now here’s the real question: **why would Google need to know my machineid and userid to give me an update - wouldn’t the version number of my browser be enough to make that decision?** I just can’t believe this isn’t used for tracking. There’s no more plausible deniability. What a perfect way to spy on people too… use their own browser against them in the name of security.

Do you get it now?  The issue is not Google's compliance with court orders.  The issue is the fact Google are tracking us individually when *they don't need to*.

---

### Post by Warpnow on 2009-09-11
There was a thread recently about Iron, the modified google chrome that doesn't track you.

Google also claims that the ID that tracks you is only used for limited things, so they wouldn't have it. Not sure where I read that, but am positive I did. I believe it was only for updates.

---

### Post by arinlares on 2009-09-11
I had Firefox warn me about attack sites on three occasions.  It's a nice feature. So what if the information is sent from your computer to a server to check if the site you're on is an attack site?  I'm sure when you install a package, it's tracked similarly.  So long as you aren't looking up kiddie porn or how to make mustard gas, it's no issue.  Even then, you agreed to be tracked, as I'm sure it's in the EULA.

---

### Post by t0p on 2009-09-11
> **Warpnow said:**
> Google also claims that the ID that tracks you is only used for limited things, so they wouldn't have it. Not sure where I read that, but am positive I did. I believe it was only for updates.

It doesn't really matter if Google say the tracking ID is "only used for limited things".  If Judge X in the Republic of Mordor tells Google to disclose all data pertaining to the user at ip address AAA.BBB.CCC.DDD, Google will hand over *everything*. They're not going to say "Sorry, Judge X, we didn't collect that data for your evil purposes."  And they don't need to collect all that data in the first place!  There is no need for the update system of their Safe Browsing feature to issue this individually identifiable tracking ID.

---

### Post by t0p on 2009-09-11
> **arinlares said:**
> I had Firefox warn me about attack sites on three occasions.  It's a nice feature. So what if the information is sent from your computer to a server to check if the site you're on is an attack site?  I'm sure when you install a package, it's tracked similarly.

Please tell me which applications you're referring to.

 > **arinlares said:**
> 
So long as you aren't looking up kiddie porn or how to make mustard gas, it's no issue. 

Or if you live in a dictatorship where the oppressive regime kill members of your religion.  Or you campaign for democracy.  Or...

---

### Post by misfitpierce on 2009-09-11
I say you gotta get over it, the chances are there that every app you use that connects to the internet sends part of your info somewhere that you may not want going out. You connect to the internet, you get over it and learn to deal with it... Dont like? Stay offline I say ha! :)

---

### Post by arinlares on 2009-09-11
I stand by what I said.  If you don't want to be caught, don't do anything wrong.  Political dissenters know they run a risk of being killed in their respective countries.

As far as the packages being installed being tracked, I'm quite sure that there is a log recorded somewhere on the server that has statistics of every download request recorded.  So, what's stopping a government from requesting information about the software its citizens are using?  Any information put on the internet is recorded.  It's just the way it works, unfortunately.

---

### Post by lovinglinux on 2009-09-11
About Chrome, I believe there is an option to turn off the features that send data back to Google. Besides, you can use Chromium instead, which doesn't have those "features",as far as I know.

About Firefox, that **Block reported attack sites** and **Block reported web forgeries** are the first features I turn off when creating a new Firefox profile. There is the privacy issue, of course, but these features have been reported to cause Firefox lock ups and slow down web browsing.

I also recommend using [CustomizeGoogle](https://addons.mozilla.org/en-US/firefox/addon/743) extension for FF, which, among other features, allows to anonymize the Google cookie ID and prevent sending cookies to Google Analytics. Additionally, I also add Google Analytics to AdBlock Plus blocklist.

For additional privacy, I also recommend setting **network.http.sendRefererHeader** in Firefox preferences (about:config) to zero. This way, whenever you visit a link from one site, the destination site doesn't know the original site you were referred from.

More info: [http://kb.mozillazine.org/Network.http.sendRefererHeader](http://kb.mozillazine.org/Network.http.sendRefererHeader)

Also set **network.prefetch-next** to false. This is what it does:

> Link prefetching is when a webpage hints to the browser that certain pages are likely to be visited, so the browser downloads them immediately so they can be displayed immediately when the user requests it. This preference controls whether link prefetching is enabled. 

I don't like the idea of a web site deciding which links "are likely to be visited" and telling Firefox to download them. For instance, what if you do a web search and visit a site that links to illegal content? How would you be able to determine that just reading the search results summaries? So, I turn that thing off. I don't want to have Firefox downloading stuff I'm not aware about.

More info: [http://kb.mozillazine.org/Network.prefetch-next](http://kb.mozillazine.org/Network.prefetch-next)

Also beware that there are lot's of nice and fancy Firefox extensions that are capable of tracking your web browsing habits. Most of the time, this data is necessary to allow the extension to provide extra features and they usually have a privacy policy. Nevertheless, it is better to stay away from them if you are really concerned about privacy.

For those who are thinking about posting "use Opera, it's way better than Firefox", don't forget that the "Turbo" mode is also a browsing history tracking feature, since all pages goes to Opera servers to be compressed before being displayed on your browser. Who knows what info the keep about you.

---

### Post by t0p on 2009-09-11
> **arinlares said:**
> I stand by what I said.  If you don't want to be caught, don't do anything wrong.  Political dissenters know they run a risk of being killed in their respective countries.

So screw 'em, right?  Wow.  You're a cold one.  And what about those whose religion is persecuted?  They should stop worshipping their god?

> **arinlares said:**
> 
As far as the packages being installed being tracked, I'm quite sure that there is a log recorded somewhere on the server that has statistics of every download request recorded.  So, what's stopping a government from requesting information about the software its citizens are using?  Any information put on the internet is recorded.  It's just the way it works, unfortunately.

You're wrong, the internet doesn't "just work that way".  Surveillance systems are added to the internet.

And there are ways around them.  For instance, the Firefox user can disable Safe Browsing.  But he won't do that unless he knows about the issue.  That's one reason I post stuff like this.  So the info gets disseminated.  If just one potential target disables Safe Browsing because of this thread, I have succeeded.

Remember, a lot of people use Firefox because it is "more secure".  How ironic that the user's security is potentially endangered by this.  How unfortunate too, because Firefox *is* more secure if properly configured.  Of course, people won't know *how* to properly configure the browser unless they find out how.  Hopefully this thread will help.  Thanks, **lovinglinux**, for the extra pointers!

Why is so much trust invested in Google?  You do all realise that their first priority is their shareholders?  That "Don't Be Evil" stuff is just publicity.

---

### Post by lovinglinux on 2009-09-11
> **arinlares said:**
> I stand by what I said.  If you don't want to be caught, don't do anything wrong.  Political dissenters know they run a risk of being killed in their respective countries.

I don't want to be rude or turn this topic into a political discussion, but that comment above is really absurd.

---

### Post by arinlares on 2009-09-11
> **t0p said:**
> So screw 'em, right?  Wow.  You're a cold one.  And what about those whose religion is persecuted?  They should stop worshipping their god?

To put it shortly, yes.  Screw'em.  It's their choice.  Same goes for religion.  The only thing they can't control is the color of their skin, and physical deformities that can result in them being persecuted.

I'm going to bow out of this discussion simply so it doesn't go too far away from the topic.  I also seem to be in violation of the rules of this section, so I should shut up, I'm sure.

---

### Post by bapoumba on 2009-09-11
Please keep the political/religion debate some place else, thanks.

---

### Post by AggravatedGestalt on 2010-11-04
> **misfitpierce said:**
> I say you gotta get over it, the chances are there that every app you use that connects to the internet sends part of your info somewhere that you may not want going out. You connect to the internet, you get over it and learn to deal with it... Dont like? Stay offline I say ha! :)

How many people make such asinine statements? If you don't like it, then run away? Nonsense! The highest level of nonsense that can be expressed. This is mental laziness, and self stagnating dribble. 

If you dislike something, then change it! Unless you must harm others to accomplish something, no one should be discouraging you, me, or anyone else. To say otherwise is to say that unless "the designers" have specifically provided an option for "you", then you have no right to modify or change it. Hmm. 

To see people with such mentalities using Linux is an astonishing discrepancy. Oh wait,. this is Ubuntu.

---

### Post by CharlesA on 2010-11-04
Stop resing dead threads please.

Closed.

---

