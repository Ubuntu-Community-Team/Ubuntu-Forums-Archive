---
title: "How the Heartbleed bug affects users"
date: 2014-04-10
forum: The Cafe
---

### Post by CharlesA on 2014-04-10
There is a bunch of info regarding this bug over here: [http://heartbleed.com/](http://heartbleed.com/) but it is mostly geared to server administrators.
This explanation is more suited to users: [http://www.vox.com/2014/4/8/5593654/heartbleed-explainer-big-new-web-security-flaw-compromise-privacy](http://www.vox.com/2014/4/8/5593654/heartbleed-explainer-big-new-web-security-flaw-compromise-privacy)

As far as users are concerned, there isn't much they can do except check with any sites they use and see if they have been patched.

If they have been patched, change your passwords. I would even go so far as to change passwords for sites that say they are unaffected, just in case.

There are some resources to help with that including a scanner from LastPass: [https://lastpass.com/heartbleed/](https://lastpass.com/heartbleed/)

I also found a small list of commonly used sites that said if they were affected or not. It can be found here:
[http://mashable.com/2014/04/09/heartbleed-bug-websites-affected/](http://mashable.com/2014/04/09/heartbleed-bug-websites-affected/)

Hope this helps.

---

### Post by pfeiffep on 2014-04-10
+1
> **CharlesA said:**
> There is a bunch of info regarding this bug over here: [http://heartbleed.com/](http://heartbleed.com/) but it is mostly geared to server administrators.
This explanation is more suited to users: [http://www.vox.com/2014/4/8/5593654/heartbleed-explainer-big-new-web-security-flaw-compromise-privacy](http://www.vox.com/2014/4/8/5593654/heartbleed-explainer-big-new-web-security-flaw-compromise-privacy)

As far as users are concerned, there isn't much they can do except check with any sites they use and see if they have been patched.

If they have been patched, change your passwords. I would even go so far as to change passwords for sites that say they are unaffected, just in case.

There are some resources to help with that including a scanner from LastPass: [https://lastpass.com/heartbleed/](https://lastpass.com/heartbleed/)

I also found a small list of commonly used sites that said if they were affected or not. It can be found here:
[http://mashable.com/2014/04/09/heartbleed-bug-websites-affected/](http://mashable.com/2014/04/09/heartbleed-bug-websites-affected/)

Hope this helps.

Thanks for this informed information. Here's another site for end users to [check]("http://filippo.io/Heartbleed/")  (scan) sites they normally visit, or[ here]("https://www.ssllabs.com/ssltest/index.html")

---

### Post by pfeiffep on 2014-04-11
Here's a nice slide show summarizing [Heartbleed]("http://www.eweek.com/security/slideshows/heartbleed-ssl-encryption-flaw-10-ways-to-minimize-the-threat.html?kc=EWKNLEDP04112014A&dni=117348479&rni=25875118")

---

### Post by CharlesA on 2014-04-11
> **pfeiffep said:**
> Here's a nice slide show summarizing [Heartbleed]("http://www.eweek.com/security/slideshows/heartbleed-ssl-encryption-flaw-10-ways-to-minimize-the-threat.html?kc=EWKNLEDP04112014A&dni=117348479&rni=25875118")

Good slideshow. :)

---

### Post by pqwoerituytrueiwoq on 2014-04-11
how can i check for myself to see if a site is affected? (IE attempt to use this exploit to see if they are affected)

---

### Post by CharlesA on 2014-04-11
> **pqwoerituytrueiwoq said:**
> how can i check for myself to see if a site is affected? (IE attempt to use this exploit to see if they are affected)

Use the scanner lastpass has up, but keep in mind nothing is 100%.

---

### Post by dave_moran on 2014-04-12
thx for the help.

---

### Post by rburkartjo on 2014-04-12
here is the link

[https://www.ssllabs.com/ssltest/](https://www.ssllabs.com/ssltest/)

please know it might take a few minutes

[http://ubuntuforms.org](http://ubuntuforms.org)   sever got an A-

---

### Post by sandyd on 2014-04-12
Merged.

---

### Post by QDR06VV9 on 2014-04-14
This was todays(4-14-2014) check.
```
[TABLE]
[TR]
[TD]Site:[/TD]
[TD]ubuntuforums.org[/TD]
[/TR]
[TR]
[TD]Server software:[/TD]
[TD]Apache/2.2.22 (Ubuntu) [/TD]
[/TR]
 [TR]
[TD]Was vulnerable:[/TD]
 [TD]Possibly (known use OpenSSL, but might be using a safe version)[/TD]
[/TR]
 [TR]
[TD]SSL Certificate:[/TD]
[TD]Now Safe (created 6 days ago at Apr  8 14:28:06 2014 GMT)[/TD]
[/TR]
[TR]
[TD]Assessment:[/TD]
[TD]Change your password on this site if your last password change was more than 6 days ago [/TD]
[TD][/TD]
[/TR]
  [/TABLE]

```
So has everybody changed there passwords?

---

### Post by CharlesA on 2014-04-14
Passwords aren't stored on the forums anymore and logging in is dealt with via Ubuntu One/Launchpad.

---

### Post by QDR06VV9 on 2014-04-14
> **CharlesA said:**
> Passwords aren't stored on the forums anymore and logging in is dealt with via Ubuntu One/Launchpad.

Hoped that was the case but wanted to hear it from you!

---

### Post by Camilia on 2014-04-16
> **CharlesA said:**
> 
If they have been patched, change your passwords. I would even go so far as to change passwords for sites that say they are unaffected, just in case.

There are some resources to help with that including a scanner from LastPass: [https://lastpass.com/heartbleed/](https://lastpass.com/heartbleed/)

One of the companies affected by the vulnerability was password manager LastPass, but the company upgraded its servers as of 5:47 a.m. PT Tuesday, spokesman Joe Siegrist said. [CNET]("http://www.cnet.com/news/heartbleed-bug-undoes-web-encryption-reveals-user-passwords/")

If was hacked once how does anyone know it won't be hacked again?

---

### Post by CharlesA on 2014-04-16
> **Camilia said:**
> One of the companies affected by the vulnerability was password manager LastPass, but the company upgraded its servers as of 5:47 a.m. PT Tuesday, spokesman Joe Siegrist said. [CNET]("http://www.cnet.com/news/heartbleed-bug-undoes-web-encryption-reveals-user-passwords/")

If was hacked once how does anyone know it won't be hacked again?

Considering the password database they use is encrypted and this bug has nothing to do with a system being "hacked" actively - the vulnerability dealt with a bug in OpenSSL that was patched soon after it was made public. They also reissued their SSL certificate on 4/7 after the patch was applied.

If you don't want to trust them, that is up to you.

---

### Post by Camilia on 2014-04-16
> **CharlesA said:**
> Considering the password database they use is encrypted and this bug has nothing to do with a system being "hacked" actively - the vulnerability dealt with a bug in OpenSSL that was patched soon after it was made public. They also reissued their SSL certificate on 4/7 after the patch was applied.

My point that is that it was targeted by heartbleed for some unknown reason. Why shouldn't the heartbleed item weaken its security again?

---

### Post by CharlesA on 2014-04-16
> **Camilia said:**
> My point that is that it was targeted by heartbleed for some unknown reason. Why shouldn't the heartbleed item weaken its security again?

Because it was a flaw in OpenSSL and wasn't exactly a targeted attack. The flaw has been patched and LastPass reissued their SSL cert in case the private key was compromised.

---

### Post by Camilia on 2014-04-16
> **CharlesA said:**
> Because it was a flaw in OpenSSL and wasn't exactly a targeted attack. The flaw has been patched and LastPass reissued their SSL cert in case the private key was compromised.
Thanks for the info. Since it is described as a bug I was thinking of something like a Trojan virus. 

Info from the Washington post made the problem more clearer. Just don't understand what  made the Heartbleed bug develop or why.

---

