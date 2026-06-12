---
title: "How does the new malformed URL prefix phishing tactic work?"
date: 2021-02-20
forum: The Cafe
---

### Post by Paddy Landau on 2021-02-20
According to several reports, there's a new phishing tactic that makes use of malformed URL prefixes.

Instead of using [FONT=courier new]http://[/FONT] or [FONT=courier new]https://[/FONT], the URLs begin with [FONT=courier new]http:/\[/FONT] or [FONT=courier new]https:/\[/FONT].

I am struggling to understand how this differs from just using a bad website, because as far as I can tell, the malformed prefix is just translated into a normal prefix by the browser (intended to be a helpful feature), but no other change is made.

So, if I go to
```
https:/\www.example.com/somepath
```
this is identical to
```
https://www.example.com/somepath
```

GreatHorn [provides an explanation]("https://www.greathorn.com/blog-new-phishing-attack-identified-malformed-url-prefixes/") that includes an actual malformed URL (which I won't reproduce here for security reasons; to see it, visit the article and scroll down to "Example phishing email").

That sample URL contains an additional "[FONT=courier new]//[/FONT]" but it's somewhere in the middle instead of at the front. I don't believe that it makes a difference, because in URLs, a double-slash is identical to a single slash (even in the prefix according to my experiments).

I have been experimenting using my own domain name, and I can't tell how it's any different from a normal URL in practical terms. (Chrome catches the problem; I think that it's a recent security fix; but [FONT=courier new]curl[/FONT] doesn't catch it.)

Can you explain to me, please, how this tactic is any more successful than using a normal prefix?

---

### Post by grahammechanical on 2021-02-21
Might I suggest as a line of enquiry and not wishing to slander any organisation, that you are testing this out on the wrong (or should that be, right) operating system? You are using the wrong (or should that be, right) web browser?

I have read the article that you linked to and I agree that the attack can only stand any chance of working if it redirects to a fake web site. If the OS/browser corrects the misspelt URL then the user would be directed to the proper web site. Some other factors must be in play for this scam to be worth the effort the crooks are putting into it.

Regards

---

### Post by Paddy Landau on 2021-02-21
> **grahammechanical said:**
> … as a line of enquiry … you are testing this out on the wrong (or should that be, right) operating system? … web browser?
I went into Windows, and realised that there was precious little to test! Very few people on Windows are going to open the link in a PowerShell.
Also, these days, there aren't many popular browsers that don't use Chromium or Mozilla!
I tried Firefox, and it also corrected the backslash to a forward slash.
Likewise Microsoft Edge on Windows.
> **grahammechanical said:**
> … I agree that the attack can only stand any chance of working if it redirects to a fake web site. … Some other factors must be in play for this scam to be worth the effort the crooks are putting into it.
Yes, that's what I was thinking. I tried to replicate the hack by creating my own email with a button, but Chrome (and, therefore, probably all Chromium browsers) warned me about it.

So, I'm flummoxed as to how that can be a phishing attack different from normal ones.

---

### Post by grahammechanical on 2021-02-21
You are running your tests on URLs that lead to genuine web sites. What if, these researchers are running their tests with URLs that lead to actual scam web sites? Then what they are witnessing is the browser auto correcting the malformed URL. Just as you have noticed browsers do. It might be a scam web site but it is an actual web site with a genuine URL even if the owners of the web site are not genuine honest people.

Regards

---

