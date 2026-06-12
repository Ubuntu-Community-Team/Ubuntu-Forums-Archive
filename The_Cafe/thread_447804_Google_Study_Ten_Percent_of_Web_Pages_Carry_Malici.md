---
title: "Google Study: Ten Percent of Web Pages Carry Malicious Code"
date: 2007-05-18
forum: The Cafe
---

### Post by adamklempner on 2007-05-18
[http://www.foxnews.com/story/0,2933,273614,00.html](http://www.foxnews.com/story/0,2933,273614,00.html)

> About one in 10 Web pages is infected with malicious software that could result in a user's personal information being stolen, according to Google researchers.

Sensitive data such as banking passwords and e-mail addresses could unwittingly be handed over to criminals as a result of visiting infected pages, which work by exploiting a vulnerability in the user's Internet browser, a study by Google researchers suggests.

The researchers said in their report that they had analyzed approximately 4.5 million Web pages over a 12-month period and found that 450,000 had caused a test computer to make a "drive-by download," a common example of which was a "keylogger," which captures every keystroke a user makes.

The report, entitled "The Ghost in the Browser," concluded: "Unfortunately, average computer users have no means to protect themselves from this threat."

"Their browser (sic) can be compromised just by visiting a web page and become the vehicle for installing multitudes of malware on their systems."

Pages with advertising were among those most commonly exploited, the study, said, because the ads were often displayed via a third-party network and not under the control of the Web site owner.

Other pages that were vulnerable included those with user-generated content, such as forums or blogs, and those that make use of "widgets" — for instance, traffic counters — which could be configured to exploit a visitor's computer.

In many instances the Web site owner was unaware his site had been infiltrated, experts said.

"We expect that the majority of malware is now spreading via web-based infection, because the computer of an average user provides a rich environment for adversaries to mine," Niels Provos, who led the study, wrote.

"Banking transactions and credit-card numbers, for instance, are much more likely to be found on a user's machine than on a compromised server."

The work of anti-virus software providers was made difficult by the fact that malware evolved rapidly, one malicious bit of code changing 1,100 times over the 12-month period of the study, the authors said.

But Graham Cluley, an expert at the British computer-security firm Sophos, said that there was "a fair amount" users could do to protect themselves, such as ensuring their virus-protection software was up to date and setting their PCs to automatically download patches from Microsoft's Internet servers.

"Anti-virus vendors now also sell plug-ins, which screen pages as you try to access them, detecting relevant threats," Cluley said.

He added that according to research by his company, 70 percent of Web-based infections were found on "legitimate" Web sites.

Google said it was now labeling sites that had been identified as malicious as "potentially harmful" when they were returned as search results.


We are not susceptible to this, are we?  There is a link to the actual google paper about this in the news article.  It seems like most of the problems stem from ActiveX, but I wonder if there is some cross platform Firefox vulnerability that I should worry about.  Also, since I use Adblock Plus and don't display any ads, does that remove a lot of the threats?

---

### Post by compmodder26 on 2007-05-18
> **adamklempner said:**
> [http://www.foxnews.com/story/0,2933,273614,00.html](http://www.foxnews.com/story/0,2933,273614,00.html)



We are not susceptible to this, are we?  There is a link to the actual google paper about this in the news article.  It seems like most of the problems stem from ActiveX, but I wonder if there is some cross platform Firefox vulnerability that I should worry about.  Also, since I use Adblock Plus and don't display any ads, does that remove a lot of the threats?

I'd say the most probable attack vector for Firefox would be through a javascript vulnerability.  There were 1 or 2 a while back.  I don't know about any now.

---

### Post by Enverex on 2007-05-18
Most exploits are either ActiveX exploits (which is only part of IE) or IE specific explots. The rest are normally Javascript which are the annoying redirects, message boxes, etc, which you can turn off but you lose some page functionality.

---

### Post by compmodder26 on 2007-05-18
IIRC, I believe Firefox had a js vulnerability a while back that could cause a buffer overflow.

---

