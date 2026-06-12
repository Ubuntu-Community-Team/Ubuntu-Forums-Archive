---
title: "Suspicious behaviour of firefox 8.0"
date: 2011-12-18
forum: Security
---

### Post by arroy_0209 on 2011-12-18
I recently upgraded from previous version of firefox to the 8.0 version. The add-ons were transferred as usual but I noticed one suspicious thing: when accessing some website, at the bottom panel I noted something like "connecting to paypal.com", "transferring data from paypal.com" etc and this website had nothing to do with the website I accessed. Why did this happen? I later guessed that may be no-script did something here and I found that paypal.com is whitelisted by default. Is it possible that the website had some advertisement related to paypal.com and no-script interfered? If not then what might be the explanation? (Actually the website mentioned might have been paypalobjects.com as well, I do not remember)

In fact when I load gmail.com, then also at some stage I notice comments like "connecting to accounts.youtube.com" etc which apparently is irrelevant to gmail.com. Also right now while using this ubuntu forum, I notice noscript had allowed yahooapis.com. Can anybody please explain why firefox connects to unrelated website when I try to load some other website? Should I delete those websites from default whitelist of no-script?
By the way, I have two add-ons, no-script and adblockplus.

---

### Post by 2F4U on 2011-12-18
This is certainly not the fault of Firefox, but rather the website you are accessing links to other website. How do you think the famous Facebook button works? The button has a link to Facebook embedded and once you click on it, the original website accesses Facebook.

---

### Post by hansdown on 2011-12-18
Hi, arroy_0209.

Need to know, have you used paypal in the past?

2F4U, This is most certainly true.

---

### Post by arroy_0209 on 2011-12-18
I think I have not used paypal in past. In fact I have reinstalled ubuntu 10.04 LTS-2 two days back and never visited any such website.

In any case, should I reinstall ubuntu 10.04, along with firefox 8.0 and remove the unnecessary whitelisted websites from no-script? (Or may be this was done by adblockplus and in that case should I just leave things as they are now. May be I am getting paranoid.)

Is there any way to check whether some website attacked my operating system/browser whenever I am suspicious?

---

### Post by OpSecShellshock on 2011-12-18
You can certainly remove any site from the NoScript whitelist at any time in the Options. There's an explanation for everything you've noted above, though. If a site has a paypal button on the page anywhere, then you will see communication with paypal called up by the page you're actually on whenever it loads. Gmail is probably the same way, since it and YouTube are both owned by Google, and Google tends to integrate a lot of their stuff on all of their sites. Yahooapis is showing up on this forum because the forum uses it for the post editor. You can see this at work by forbidding yahooapis and trying to type and submit a comment.

---

### Post by lovinglinux on 2011-12-18
> **OpSecShellshock said:**
> You can certainly remove any site from the NoScript whitelist at any time in the Options. There's an explanation for everything you've noted above, though. If a site has a paypal button on the page anywhere, then you will see communication with paypal called up by the page you're actually on whenever it loads. Gmail is probably the same way, since it and YouTube are both owned by Google, and Google tends to integrate a lot of their stuff on all of their sites. Yahooapis is showing up on this forum because the forum uses it for the post editor. You can see this at work by forbidding yahooapis and trying to type and submit a comment.

+1

Most likely the site use paypal buttons. 

I would recommend using [Ghostery](https://addons.mozilla.org/en-US/firefox/addon/9609/) to block third-party tracking sites. Since you have already NoScript and AdBlock, most unwanted stuff would be blocked by these add-ons.

---

