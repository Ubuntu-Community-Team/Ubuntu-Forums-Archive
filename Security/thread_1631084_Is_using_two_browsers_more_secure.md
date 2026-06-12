---
title: "Is using two browsers more secure?"
date: 2010-11-26
forum: Security
---

### Post by Blutkoete on 2010-11-26
Hello!

At the moment, I'm using Ubuntu 10.10 and two browsers: Firefox with NoScript for general browsing, and Chromium for my mail accounts. The idea behind this was/is never to be logged into my mail account with the browser that opens other web pages and maybe executes malicious code.

Is this really adding security or is it just adding felt security?

Is there a way to achieve this under Ubuntu without using two browsers (maybe using two distinct Firefox instances or another program)?

It's kind of uncomfortable when people send me links to other web pages which I would like to open in Firefox. Is there something like a plugin that gives me a "Open link in different browser ..." context menu (maybe there's something like that in a different browser)?

When I should ask these questions in a Firefox/Chromium forum, just tell me.

Thank you!

---

### Post by wet-willy on 2010-11-26
You may have your reasons for being "overly paranoid" if you're a "**home computer user**". 

In Ubuntu menus, under System/Preferences/Preferred Applications, the default setting under the 'internet' tab is 'open link with web browser default'. What's your default browser?

---

### Post by Blutkoete on 2010-11-26
My default browser is Firefox, but of course Chromium doesn't offer me an "Open this link in default browser" option.

Actually, if I flip things around (Firefox for mail, Chromium for normal browsing), there is an addon that seems to to the job ([here]("http://www.blogsdna.com/10268/how-to-open-links-in-a-different-browser-while-browsing-in-firefox.htm")). I'll just do some more Google research.

Generally I take the noone-cares-for-my-data approach to paranoia, but I just read two articles about sites beeing able to identify you or break into your accounts when you're browsing with a browser that is logged into specific accounts like Xing or GoogleMail, so I thought that using two browsers was a good idea (e.g. [here]("http://www.infosecurity-us.com/view/7605/researchers-identify-anonymous-users-through-web-browser-history-and-social-networks/"))

I'm still not sure whether it actually helps.

---

### Post by CharlesA on 2010-11-26
That link looks like a proof of concept exploit. Is actively being used?

---

### Post by emiller12345 on 2010-11-26
Just to make you a little more paranoid, they don't need to access the leftovers from Xing, Facebook, or LinkedIn to identify your browser, take a look at this... 

**[http://panopticlick.eff.org]("https://panopticlick.eff.org")**

I know its old, but it shows that your browser leaves behind a fingerprint where ever you go. It's something to think about.

---

### Post by bodhi.zazen on 2010-11-26
What makes you think two browsers are more or less safe then one ?

First such exploits are extreemly rare.

Second, and more important, do not open untrusted emails or browse to shady sites.

Third use NoScript

If you need something beyond that I would suggest you learn to use Apparmor or Selinux. Both would confine your browser.

Another alternate would be to use Virtualbox, there are several light weight, kiosk distros you could use, or even slitaz.

[http://www.slitaz.org/en/](http://www.slitaz.org/en/)

---

### Post by Penguin=) on 2010-11-26
I guess it safer to use two browsers.

Because on one browser you can share all your information, and on the other you can just browse the internet.

Its all up to you my friend, if it feels safer, do it!:p:o:):P:guitar:

---

### Post by CharlesA on 2010-11-26
> **Penguin=) said:**
> I guess it safer to use two browsers.

Because on one browser you can share all your information, and on the other you can just browse the internet.

Its all up to you my friend, if it feels safer, do it!:p:o:):P:guitar:

It's still security thru obscurity.

Bodhi covered the way to secure yer browser.

---

