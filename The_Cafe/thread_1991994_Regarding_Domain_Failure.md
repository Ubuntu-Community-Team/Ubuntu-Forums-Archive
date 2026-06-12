---
title: "Regarding Domain Failure"
date: 2012-05-31
forum: The Cafe
---

### Post by TusharK on 2012-05-31
I am new to this and even don't know if this is the right place to post such type of problem or not. Need suggestions.

Lets start from the beginning of the problem.

I own a domain [www.tushark.com.np]("http://www.tushark.com.np"). Suddenly my account was suspended. The following error showed  when i browse my website : 

> Your account has been suspended.

(Reason: Due to heavy cpu usage.)

After that I deleted my account from that hosting provider (but without unsuspending my account). Later I modified my domain and linked it to the new nameservers. The domain registrant took 4 days to modify my domain. Now it shows that the domain is modified but when I look the information of my domain in [http://whois.domaintools/tushark.com.np](http://whois.domaintools/tushark.com.np) it still shows the previous nameservers. And when i go to my website the following error shows up in chrome: 

> This webpage is not available
The webpage at [http://tushark.com.np/](http://tushark.com.np/) might be temporarily down or it may have moved permanently to a new web address.
Error 137 (net::ERR_NAME_RESOLUTION_FAILED): Unknown error.

What might be the causes to it?

---

### Post by oldos2er on 2012-05-31
Moved to Community Cafe since your problem doesn't involve Ubuntu support.

---

### Post by cryptotheslow on 2012-05-31
I see the DNS record pointing to freehosting.com servers and the site comes up fine "Tushark - Your Technology Pal"

I expect you are suffering from either cached DNS records or cached content either locally or on your ISP.

---

### Post by TusharK on 2012-06-03
> **cryptotheslow said:**
> I see the DNS record pointing to freehosting.com servers and the site comes up fine "Tushark - Your Technology Pal"

I expect you are suffering from either cached DNS records or cached content either locally or on your ISP.

Thank you as you tried to figure out the problem and solve it. My site is now live and running. It took around 12 days to update the nameserver. I was very much confused then.
Anyway Thanks Again.

---

