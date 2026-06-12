---
title: "RequestPolicy: new Firefox extension for privacy and security"
date: 2009-01-08
forum: The Cafe
---

### Post by justin samuel on 2009-01-08
Hi all,

I just wanted to announce my new Firefox extension to fellow Ubuntu users.

RequestPolicy is an extension that gives you greater privacy and security in your browsing. It does for cross-site requests what NoScript does for scripts and objects. Cross-site requests are dangerous for privacy because they provide websites other than the one you are visiting with information about what pages you visit (resulting in Google and other companies knowing a huge amount about all of your browsing habits). Cross-site requests are also dangerous for security because they make you vulnerable to things such as Cross-Site Request Forgery (CSRF) and clickjacking.

RequestPolicy is by no means a replacement for NoScript. The two work great together. For example, if you whitelist a domain with NoScript, RequestPolicy makes sure that scripts from that domain don't get executed when you are visiting some other site because the cross-site request is blocked by default.

If you try out RequestPolicy, let me know what you think. You can post here, PM/email me, or post a review at [_AMO_]("https://addons.mozilla.org/en-US/firefox/addon/9727/").

[_www.requestpolicy.com_]("http://www.requestpolicy.com/")

[_download from addons.mozilla.org_]("https://addons.mozilla.org/en-US/firefox/addon/9727/")

Thanks for your feedback!

---

### Post by cardinals_fan on 2009-01-08
> The add-on site requires that users log in to install experimental add-ons as a reminder that you are about to undertake a risk step.
Good job on sounding condescending, Mozilla.

---

### Post by justin samuel on 2009-01-08
> **cardinals_fan said:**
> Good job on sounding condescending, Mozilla.

From the perspective of a developer of a new extension, that warning is pretty bad sounding and the requirement to login is a huge deterrent (note: you can install from the [requestpolicy.com]("http://www.requestpolicy.com/") website, instead).

However, there's a good reason for the warning and requirement to log in: the "experimental" addons are experimental because they have not been reviewed by an AMO editor. So, anyone can create an AMO account and upload an extension with malicious code to be served by AMO as an experimental extension.

It will probably be another month+ before my extension is reviewed because there is a huge backlog of addons to be reviewed and a shortage of AMO editors. (If you have extension development experience, they are always looking for volunteers. I heeded the call myself, in fact.)

---

### Post by cardinals_fan on 2009-01-08
> **justin samuel said:**
> 
However, there's a good reason for the warning and requirement to log in: the "experimental" addons are experimental because they have not been reviewed by an AMO editor. So, anyone can create an AMO account and upload an extension with malicious code to be served by AMO as an experimental extension.

I wonder why they don't just show a warning...

---

### Post by EdThaSlayer on 2009-01-09
Sounds pretty cool, this add-on. I wonder if it does all the wonders you claim it to do. Will check it out once I go home on a test pc. :D
Or until someone else tries it and confirms its true.

Good job though, we need more privacy in this day and age where it has become a scarce commodity(or should I say, right?).

---

### Post by justin samuel on 2009-01-09
> **EdThaSlayer said:**
> Sounds pretty cool, this add-on. I wonder if it does all the wonders you claim it to do.

I sure hope it does, or my wife is going to want to know what I've been doing in here with the door shut the past few months.

(Side note: my wife has been using Ubuntu for almost exactly 1 year now. She says she likes it better than Windows because it's faster. She isn't so interested in this extension, though, nor is she a NoScript user. Ah, well, at least she isn't using IE.)

---

