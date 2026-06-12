---
title: "SSL Encryption Hacked"
date: 2011-09-29
forum: Security
---

### Post by Merisi on 2011-09-29
This article has just come to my notice (I'm not sure if anyone else has posted this I couldn't find it in a search)

[http://www.theregister.co.uk/2011/09/19/beast_exploits_paypal_ssl/](http://www.theregister.co.uk/2011/09/19/beast_exploits_paypal_ssl/)

I also found this on the No Script forums.

[http://forums.informaction.com/viewtopic.php?f=7&t=7238&sid=45e1c71ce8e235caa3131233119f342f](http://forums.informaction.com/viewtopic.php?f=7&t=7238&sid=45e1c71ce8e235caa3131233119f342f)

Is the fact that SSL can be exploited a worry for Linux users?

---

### Post by collisionystm on 2011-09-29
> **Merisi said:**
> This article has just come to my notice (I'm not sure if anyone else has posted this I couldn't find it in a search)

[http://www.theregister.co.uk/2011/09/19/beast_exploits_paypal_ssl/](http://www.theregister.co.uk/2011/09/19/beast_exploits_paypal_ssl/)

I also found this on the No Script forums.

[http://forums.informaction.com/viewtopic.php?f=7&t=7238&sid=45e1c71ce8e235caa3131233119f342f](http://forums.informaction.com/viewtopic.php?f=7&t=7238&sid=45e1c71ce8e235caa3131233119f342f)

Is the fact that SSL can be exploited a worry for Linux users?


Its a worry for everyone. Linux is no different that any other OS when it comes to accessing things via the web.

---

### Post by Dangertux on 2011-09-29
This has been coming for a while now, for some reason nobody wants to adopt newer standards. To be quite honest I'm surprised TLS 1.0 held out as long as it did :-/

---

### Post by OpSecShellshock on 2011-09-29
Here's an article that contains links to what various browser developers are saying about the issue: [http://news.cnet.com/8301-27080_3-20113530-245/browsers-tackle-the-beast-web-security-problem/](http://news.cnet.com/8301-27080_3-20113530-245/browsers-tackle-the-beast-web-security-problem/)

The Mozilla and Opera quotes are probably the most useful. Mozilla because they are trying to explain what they think would have to happen in order for it to work, and Opera because they explain what happens to the functionality of the web when users try to address it by upgrading on the client side without a commitment from site owners on the server side (which is, of course, the largest impediment here).

---

### Post by emiller12345 on 2011-09-29
would it be advisable to uncheck the 'use TLS 1.0' check box in firefox? 
Edit >> Preferences >> Advanced >> Encryption >> 'use TLS 1.0'

---

### Post by Merisi on 2011-09-30
The more I read about BEAST, the less concerned I feel about it.  I think you'd have to be really unlucky to fall victim to it an hopefully Firefox and addons like No Script will come up with solutions.

---

### Post by OpSecShellshock on 2011-09-30
> **emiller12345 said:**
> would it be advisable to uncheck the 'use TLS 1.0' check box in firefox? 
Edit >> Preferences >> Advanced >> Encryption >> 'use TLS 1.0'

I would absolutely not advise that. For most sites it remains the best thing available, as support for later versions of TLS is not widespread enough, and you still need to allow whatever encryption you can get.

> The more I read about BEAST, the less concerned I feel about it.  I  think you'd have to be really unlucky to fall victim to it an hopefully  Firefox and addons like No Script will come up with solutions.

NoScript already pretty much had it covered, in the sense that Java objects on pages won't load unless you specifically allow them to, and according to the Mozilla developers Java would be needed to circumvent the browser's built-in same origin enforcement mechanisms. Of course if that's true then users could also disable the Java plugin or remove it entirely. And folks should keep in mind that all the browser developers are pretty convinced that a successful MiTM would have to have taken place before BEAST could even do its thing.

---

