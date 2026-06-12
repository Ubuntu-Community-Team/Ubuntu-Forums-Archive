---
title: "Privacy Violation = YouTube video searches (need opt-out)"
date: 2012-03-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Yfrwlf on 2012-03-31
Your OS always trying to connect to YouTube to download **random** video information is bad enough, but your OS doing **searches** on YouTube for phrases you enter in when trying to search your own videos is beyond sickening.

In the privacy section, at the very least, there has to be an opt-out section for stopping this Google information mining operation.

---

### Post by cariboo on 2012-03-31
I don't know who you are trying to address, but have you filed a bug about your concern, and marked it as a security issue?

---

### Post by lovinglinux on 2012-03-31
Remove *unity-scope-video-remote* package.

```
sudo apt-get remove unity-scope-video-remote
```

---

### Post by Yfrwlf on 2012-04-08
It's not a bug, it was designed that way. :rolleyes:

Thanks for the removal command, nice that you can do that much!  However, for normal users, I believe this should be a privacy setting option still.

---

### Post by zika on 2012-04-08
> **lovinglinux said:**
> Remove *unity-scope-video-remote* package.

```
sudo apt-get remove unity-scope-video-remote
```> **Yfrwlf said:**
> It's not a bug, it was designed that way. :rolleyes:

Thanks for the removal command, nice that you can do that much!   However, for normal users, I believe this should be a privacy setting  option still.This package is not installed by default... At least at my place... I did not intervene in any way about it...

---

### Post by teh603 on 2012-04-08
You could also try a non-Unity version like Kubuntu or Lubuntu.

---

### Post by Yfrwlf on 2012-04-14
> **zika said:**
> This package is not installed by default... At least at my place... I did not intervene in any way about it...

You mean, in your install?  I find it hard to believe they'd leave these automatic online music and video search packages out of the final version, but you never know.  If enough users got upset, they probably would.  It's a nice feature if you're wanting to do searches online of course, but more like spying if you're only trying to search your local computer.  Either way, of course there is a huge marketing benefit from mining this information, and I'm honestly not sure how the majority of Ubuntu users would feel about that.  I don't like it though, and prefer to use search engines or search directly on sites I prefer for the content I prefer.

> **teh603 said:**
> You could also try a non-Unity version like Kubuntu or Lubuntu.

Oh I know I have many options in the open source sofware universe, I'm just recommending ideas for Unity as well as raising awareness and getting feedback.  Linux means freedom (or at least, it is supposed to!), so I know I have choices.

---

### Post by cariboo on 2012-04-14
> **Yfrwlf said:**
> You mean, in your install?  I find it hard to believe they'd leave these automatic online music and video search packages out of the final version, but you never know.  If enough users got upset, they probably would.  It's a nice feature if you're wanting to do searches online of course, but more like spying if you're only trying to search your local computer.  Either way, of course there is a huge marketing benefit from mining this information, and I'm honestly not sure how the majority of Ubuntu users would feel about that.  I don't like it though, and prefer to use search engines or search directly on sites I prefer for the content I prefer.



Oh I know I have many options in the open source sofware universe, I'm just recommending ideas for Unity as well as raising awareness and getting feedback.  Linux means freedom (or at least, it is supposed to!), so I know I have choices.

This still isn't the proper place for this, if you don't want to create a bug report, then at least join the [unity-design mailing list]("https://launchpad.net/~unity-design") and start a discussion about the issue.

---

### Post by zika on 2012-04-14
> **Yfrwlf said:**
> You mean, in your install?Yes, did I not write that? Actually, „at my place“ means on several installs that reside in (as I wrote) „my place"... Vanilla Ubuntu installs that started without the stuff You mention...

---

### Post by mc4man on 2012-04-14
Pretty easy to ck. - look at any current manifest 
(remote lens is currently default included

---

### Post by na5h on 2012-04-14
> **cariboo907 said:**
> This still isn't the proper place for this, if you don't want to create a bug report, then at least join the [unity-design mailing list]("https://launchpad.net/~unity-design") and start a discussion about the issue.

I agree. We (the people at this forum) are not Canonical nor the Unity team, we are just volunteers trying to help other Ubuntu users with their technical questions and such.

---

### Post by MarkieB on 2012-04-15
no longer participating in ubuntuforums.org

---

### Post by Mr. Picklesworth on 2012-04-15
Okay, I just want to make sure I'm not imagining things: it'll only search online videos if you actually open the Videos lens. Searching from the Home lens only talks to specific scopes that have asked to be on the home lens.
Is that correct?

I think it would be interesting to see a definitive policy on this in the future, if there isn't already one that I have missed. Something like &#8220;The Home lens is about _you_, not anyone else, so it has your files, your applications, your online Google Documents.&#8221; &#8230; but actually written in a coherent way :)

---

### Post by MarkieB on 2012-04-15
no longer participating in ubuntuforums.org

---

### Post by ojdon on 2012-04-15
Ah... The Ubuntu Community. Home to some of the most paranoid computer users in the world.

Posted from **Google** Chrome. ;)

---

### Post by MarkieB on 2012-04-15
no longer participating in ubuntuforums.org

---

### Post by Mr. Picklesworth on 2012-04-15
> **ojdon said:**
> Ah... The Ubuntu Community. Home to some of the most paranoid computer users in the world.

Posted from **Google** Chrome. ;)

Skim over this article (maybe look at page 20), then say people are crazy for taking this stuff seriously:
[http://papers.ssrn.com/sol3/papers.cfm?abstract_id=1450006](http://papers.ssrn.com/sol3/papers.cfm?abstract_id=1450006)

Or, if you don't feel like even looking at a gigantic article &#8212; for which I don't blame you &#8212; here's a nice little summary: [http://arstechnica.com/tech-policy/news/2009/09/your-secrets-live-online-in-databases-of-ruin.ars](http://arstechnica.com/tech-policy/news/2009/09/your-secrets-live-online-in-databases-of-ruin.ars)

If you give anyone _a single_ piece of even moderately unique information, and any other piece of information (including the fact that you're giving them information), you're expanding a worryingly detailed picture of yourself on the web. It doesn't matter if they're good guys or not.

Now, I don't have a huge fear of this (especially with basic unauthenticated GET searches, where the only data you're giving them is an IP address and a search query), but I agree it is a subject that needs to be taken really seriously. People deserve complete control over where their information is going, even when it seems completely trivial and impersonal. Because, once in a while, it isn't.

In this particular case, I think people do have control (don't search for videos if you aren't looking for videos?) so I'm not upset about it, but let's not be so quick to dismiss these concerns ;)

---

### Post by mc4man on 2012-04-15
Don't see as that big an issue, did file a bug on the default source searches (All
[https://bugs.launchpad.net/ubuntu/+source/unity-lens-video/+bug/982467](https://bugs.launchpad.net/ubuntu/+source/unity-lens-video/+bug/982467)

---

### Post by emarkay on 2012-04-15
I see some borderline CoC violations in some of the replies here. 

If you tweet and twit your every move, and never clear your cookies, and 4square and 4chan yourself into everywhere, good for you, buddy.

I don't, and I resent anyone demeaning or mocking those that still believe it is OK to have an expectation of authority on one's privacy.

Thank you.
MRK

---

### Post by sffvba[e0rt on 2012-04-15
> **emarkay said:**
> I see some borderline CoC violations in some of the replies here. 

If you tweet and twit your every move, and never clear your cookies, and 4square and 4chan yourself into everywhere, good for you, buddy.

I don't, and I resent anyone demeaning or mocking those that still believe it is OK to have an expectation of authority on one's privacy.

Thank you.
MRK

The posts and replies have been jailed.


404

---

