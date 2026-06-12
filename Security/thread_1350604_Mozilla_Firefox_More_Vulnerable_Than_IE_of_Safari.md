---
title: "Mozilla Firefox More Vulnerable Than IE of Safari?"
date: 2009-12-09
forum: Security
---

### Post by chiques on 2009-12-09
I just received this PDF about Mozilla Firefox being the most vulnerable browser on the market. Currently it's being distributed to all of the teachers in my sister in law's school district. I thought open source made it more secure when there were security holes. What gives?

---

### Post by scaine on 2009-12-09
You can read up on the original report here :
[http://prosecure.netgear.com/community/security-blog/2009/11/web-browser-vulnerability-report---firefox-leads-the-pack-at-44.php](http://prosecure.netgear.com/community/security-blog/2009/11/web-browser-vulnerability-report---firefox-leads-the-pack-at-44.php)

(click on "report" in the first line).

The web browser vulnerabilities appear to be given without context (for example, they may be related to plug-ins), and since the "research" was conducted in Q1 2009 and six months have passed without comment, I wouldn't give this report much credence.

Honestly, any report that rates *Safari* as more insecure then IE, well, draw your own conclusions.

I'm still using Firefox and will continue to do so until such time that Chromium tempts me away.  But that's a long way off.

---

### Post by cdenley on 2009-12-09
> **scaine said:**
> 
I'm still using Firefox and will continue to do so until such time that Chromium tempts me away.  But that's a long way off.

FYI, they just release a beta version of Google Chrome for Linux. I installed but, but haven't used it much yet.
[http://www.google.com/chrome/intl/en/w00t.html](http://www.google.com/chrome/intl/en/w00t.html)

---

### Post by witeshark17 on 2009-12-09
Here's an [ article about Chrome](http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http://derhil.de/2009/12/09/google-is-evil&sl=de&tl=en) that could be worth a look.

---

### Post by cdenley on 2009-12-09
> **witeshark17 said:**
> Here's an [ article about Chrome](http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http://derhil.de/2009/12/09/google-is-evil&sl=de&tl=en) that could be worth a look.

Kind of a rough translation. I think the point is that the chrome installer adds google's repo to your software sources so it will be updated with all your other packages.

---

### Post by chiques on 2009-12-09
Well, they need to make up their mind. I just ran across this [http://blog.internetnews.com/skerner/2009/03/cenzic-ie-tops-browser-vuln-li.html](http://blog.internetnews.com/skerner/2009/03/cenzic-ie-tops-browser-vuln-li.html)
I'll still put my faith in the Linux/Mozilla community. I don't trust IE.

---

### Post by Jive Turkey on 2009-12-09
It sounds like a sponsored research project, and by sponsored I mean paid for by microsoft.  There is really no data or explanation offered to substantiate the chart.  I call FUD.

Not that think it couldn't be true, in some sense of the word it probably is but they don't define "vulnerabilities" for example.  What concerns me when it comes to vulnerability is 1) remote code execution  2) privilege escalation  3)denial of service.

There are many other things that could be considered vulnerabilities that I find to be useful features and pose very little threat at all.

---

### Post by chiques on 2009-12-09
So bottom line?:



1. In any software, if you want it as secure as possible ALWAYS KEEP IT UPDATED (Windows Update, Ubuntu Updates, Mac Software Update, etc..)

2. These vulnerabilities are mostly because of small programs that can be installed on Mozilla known as 'plug-ins'. If you don't go around trying every plug in, you're that much safer.  So the report can easily be taken out of context.

3. Any report that claims Safari is less secure than Internet Explorer should flag suspicion immediately. Macintosh doesn't mess around when it comes to their customers privacy and security. IE on other hand...well lets just say don't go to certain sites with it because your computer will never run the same again.

---

### Post by sliketymo on 2009-12-09
You have to remember that Mozilla is completely open about any security vulnerabilities that come up,and they are very swift to patch them,the others,not so much.Draw your own conclusions.

---

### Post by Agent ME on 2009-12-09
I remember reading about this before. The study is very vague about defining 'vulnerabilities'; Firefox has a very open development process, so all problems with it are reported publicly, and many complete non-issues are included in its numbers here. IE and others have a very closed development process, and we only ever hear about the big bugs that are often used by malware.

Also, Firefox is updated a lot more frequently than IE and others, often within a few days the public discovery of a vulnerability. A much better study would compare the amounts of time each browser has been publicly known to be vulnerable to different hacks (and I'm pretty sure Firefox would come out above IE in this).


Lastly... that's being distributed to people in her school district? I wonder who would be behind that. (Probably some strict admin who was annoyed by the kids installing this new-fangled "Foxfire" thing on school computers and wanted to find something bad about it to say to give a reason to stop it from happening. I wouldn't be surprised if the school computers were still running IE6, which would make this handout being distributed even more ridiculous.)

---

### Post by rookcifer on 2009-12-09
> **chiques said:**
> I just received this PDF about Mozilla Firefox being the most vulnerable browser on the market. Currently it's being distributed to all of the teachers in my sister in law's school district. I thought open source made it more secure when there were security holes. What gives?

1) Internet Explorer is closed source, which means by nature fewer vulns will be found (though a large number are still found).

2) Some of the vulns are found internally by M$, and they never release them.  We will never know how many holes IE truly has had because M$ will never release internally found code errors.

3) Every single vuln found in Firefox is made public.  Mozilla has no such luxury of hiding vulns.

4) Even though Firefox has a higher number of vulns, they are almost always patched *much* faster than IE.  M$ only patches *once a month.*

5) A vulnerability in Firefox while running on Linux is not nearly as significant as the same vuln on Windows.  This is true for 2 reasons: A) most exploits are not written for Linux and B) Most Windows users run as admin, so they are wide-open to any attack.  Almost all Linux users run with limited privileges thus greatly mitigating the efficacy of most attacks.

6) Browser vulnerability numbers are always fluctuating -- some years IE will have more vulns and some years it might be Firefox.  Really, the whole number of vulns statistic means *nothing*.  What really matters is how proactive the devs are at patching them and Firefox wins this race hands down.

7) How are the vulnerability numbers generated?  One must remember, not all vulnerabilities are created equal.  Some are very benign, only slight nuisances, while others allow remote root exploits.  Microsoft has pulled this trick before in other areas.  I remember reading a report they released about how Red Hat had a higher number of vulns than Windows.  What they said was true, Red Hat did have more vulns.  However, what M$ does *not* tell you is that Red Hat comes bundled with a *ton* of third party software and all of the vulns in the *third party* software were counted *against* Red Hat.  Microsoft **did not** count third party vulns against Windows.  They pull tricks like this all the time.  You know what they say -- lies, damned lies...

---

### Post by lykwydchykyn on 2009-12-09
Never trust any so-called "security" comparison that relies on a single metric.  Especially one that is so meaningless -- who cares how many vulnerabilities were found, it's about how many went unpatched and how many were actually exploited while they were unpatched, and what the attackers were able to do.

You can't summarize security with a single number like that.  It's just not that simple.

---

