---
title: "Could someone give me examples of sites that require Flash 12 or higher?"
date: 2016-04-04
forum: Ubuntu, Linux and OS Chat
---

### Post by Jeremy_Andrews on 2016-04-04
So, I was having an argument with someone online... there's this thread started by a guy who wants to try Linux coming from Windows, and I told him that I thought he should go with Kubuntu (for the Windows-like interface) and install Chrome because Flash player is no longer updated for Firefox on Linux. 

Well, I got into this huge argument with someone insisting that you don't need Flash anymore, and that all the sites that need Flash work fine with the old 11.2 version of Flash. They acted really obtuse and as if they "weren't too sure" what the limitation was even though I spelled it out five times, and even demanded that I post a screenshot of a site that worked in Firefox on Windows side-by-side with a screenshot of that same site not working with Firefox on Linux with 11.2 installed. He thought it was ridiculous that I was suggesting Chrome was a better browser on Linux because it can run Netflix and use a newer Flash player. Needing Chrome for Netflix was the only point he conceded, although he did so grudgingly. He also conceded that Silverlight required workarounds like Pipelight or Wine, but he's holding his ground on Firefox's Flash and HTML5 being good enough for anybody.

The problem is that now that YouTube is fully or almost fully HTML5, the only example that immediately comes to mind would be AnyMeeting, and I don't have a subscription to that so I can't take a screenshot. In fact, most of the examples I know are paid services or pieces of corporate infrastructure that I don't use myself. I also know some French websites that require it, but I can't view them in the US even with an updated Flash player. That means I can't provide the screenshot he's asking for, so he's acting like he won the argument. 

The thing is, the only reason I can't think of any examples is because I haven't used Firefox on Linux recently... seems like when I do, the examples just come to me out of the woodwork, whereas I don't even notice them on Chrome.

HTML5 was only published as a formal standard 2 years ago, and Flash is now at version 20, so I find it hard to believe that absolutely nothing uses Flash or requires an updated Flash player anymore. Up until very recently, all I would have had to do was use monetized YouTube videos or Google Play to make my case and it would have been over. I mean, I don't even like Flash that much, but it's frustrating that someone won't even acknowledge that a limitation exists for Linux users that has to be worked around in some manner and is going around trying to convince naïve Windows users inquiring about Linux that websites requiring updated Flash players don't even exist anymore, just because they personally happen to like using Firefox. 

Surely he isn't right... I just don't happen to use a lot of media-heavy sites, so I'm in a bad position to counter his arguments. I mean, if the majority of you guys tell me he's right and that those sites aren't out there anymore, I'll just have to believe it because my searches aren't turning up anything for "requires Flash 12 or higher".

*[SIZE=3]EDIT: Just heard back from the guy I was having the argument with... turns out it was a misunderstanding and we're having a laugh about it now. We'd been arguing with different assumptions in mind that neither of us ever actually spelled out. Apparently he IS using the latest Flash Player in Firefox. Says someone found a way to retrofit the Pepper plugin to work with NPAPI after all, and that it's extremely easy to do now.[/SIZE]*

---

### Post by howefield on 2016-04-04
> **Jeremy_Andrews said:**
> ... because Flash player is no longer updated for Firefox on Linux.

Without getting into the schoolboy arguments, what makes you think that Firefox can't use the same version of flash (as far as I am aware that would be version 21.0.0.197) as Chrome does on Linux or Windows?

---

### Post by Geoffrey_Arndt on 2016-04-04
It's not so much that some (3 or 4 of 10???) websites still require flash for video, but there are some sites (Weightwatchers Tracker App) that require flash - - but it's getting less common year by year.  Perhaps another 4-5 years and it's use will be rare (hopefully - - as it's a steady security risk).    If I find a website that requires flash, if possible (and mostly it is) - - I just avoid that site in the future.

The new plugin that Howefield refers to will run pepperflash via a software wrapper . . . but I don't know how stable it is.  (so that it would be using the latest flash , , , from our friends at Adobe . . . )

---

### Post by night_sky2 on 2016-04-04
> **Jeremy_Andrews said:**
> because Flash player is no longer updated for Firefox on Linux. 

*Technically Adobe Flash 11.2 for Linux still receives security updates until 2017.

I am using the 11.2 version with Firefox for Linux and it **still works on most websites**. So I'll wait and see what happens in the (near) future. But some people may have very specific needs on particular websites that absolutely require ''the latest flash version''. In that case, pepperflash (bundled with Google Chrome) is recommended.

---

### Post by sgian on 2016-04-05
I use primarily Firefox for browsing with that old version of flash set to "ask to activate", primarily because flash is a security risk exploited by malware through advertising even on legitimate sites.  But when I forget to change flash from "always activate", I've noticed that sometimes firefox and that old version of flash cause Ubuntu to freeze for about 5 minutes or so.  This never happens when flash is disabled or when I use chrome, so I feel like I can safely assume that the freezes are caused by the old version of flash.

It sounds to me like you were arguing with someone who really dislikes google.  When people make emotional decisions like hating a company, in my experience, it is really hard to make them change their minds so I try to leave them alone.  It isn't like google is easily defensible in their data-mining, and I'd personally prefer to not get mired in their hate so it isn't worth it to me.  I would recommend that you also rethink getting into an internet war with this guy for the reasons above and because there are more important things in life than getting involved in an internet battle lol.

---

### Post by Bucky Ball on 2016-04-05
I have flash set to 'ask to activate' in Firefox. I'm never asked, so don't spose I've come across many sites that use it lately, or for months, or at least not sites that need the latest. :-k

---

### Post by Jeremy_Andrews on 2016-04-05
> **howefield said:**
> Without getting into the schoolboy arguments, what makes you think that Firefox can't use the same version of flash (as far as I am aware that would be version 21.0.0.197) as Chrome does on Linux or Windows?

Well, I was told about three years ago that Adobe would no longer update the NPAPI version of Flash, and Mozilla refused to implement PPAPI (I bothered them about it several times and they basically just told everyone to do without it and wait for HTML5 to take off). They asked Linux Firefox users to make sacrifices that Google wasn't asking people to make. So I started using Chrome on Linux as a result, that being the primary motivation. Naturally, I didn't want said Windows user to have a bad experience with a common plug-in like Flash not working as I'd experienced myself, so I suggested that they install Chrome from the start so that they wouldn't have to switch browsers every time they wanted to use a site that requires an updated Flash player.

I'm not one of those people that dislikes Firefox. I still use it on Windows... but on Linux, Chrome seems to be the way to go nowadays because it "just works," whereas with Firefox you might have to manually install an outdated plugin or figure out Pipelight and try to get the Windows version of Flash working.

As far as I am aware, the last supported version of Flash for Firefox on Linux was 11.2, released sometime in 2012.

EDIT: Just heard back from the guy I was having the argument with... turns out it was a misunderstanding and we're having a laugh about it now. Apparently he IS using the latest Flash Player in Firefox. Says someone found a way to retrofit the Pepper plugin to work with NPAPI after all, and that it's extremely easy to do now.

---

### Post by Geoffrey_Arndt on 2016-04-05
Sounds like your friend was on top of things from the start . . . :)

---

### Post by kansasnoob on 2016-04-06
I have to use Chrome to watch videos on Crackle. Chrome also works better for streaming videos on NBC - dunno why, it's just smoother playback.

But another option is running the Windows version of Firefox in Wine, or possibly Pipelight might be enough. For me so far it's just easier to use Firefox for most streaming and Chrome for a few others.

Oh, AFAIK the Linux version of Chrome still doesn't work on Hulu.

---

### Post by kurt18947 on 2016-04-06
NFL.com seems to require Flash 15 for NFL live now portions of its site. Flash 11.x still works for most parts. I've used the freshplayer plugin and it works pretty well but not yet 100% in my experience. My problems may arise from having both 'native' flash and freshplayer/pepperflash installed, not sure.

---

