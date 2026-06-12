---
title: "Hi-jacked?"
date: 2010-12-08
forum: Security
---

### Post by idle1 on 2010-12-08
Hello - I'm a new ubuntu 10.10 user, and I'm having just one problem.

Whenever I visit google.co.uk, although I am clearly in the uk, all the additional text on the page appears to be in Russian. I get the same when doing a whois - parts of the results page appear in cyrillic text.

I have changed my DNS using namebench recommendations, but am still getting the same problem.

To my knowledge, google etc are applying russian text to the page, because they think I am in russia...?

I am obviously avoiding doing anything online that requires a password or personal details at the moment, and until I can sort this out.

Any suggestions anyone? I'm a newbie, and unsure about additional security setup to ubuntu, having been a micro$$oft sucker for twenty years...

---

### Post by TheFr00n on 2010-12-08
It does not sound like a security issue - the average Linux box is (comparatively) quite hard to crack. 

Off the top of my head (and with almost zero expertise) it sounds like a font issue. Have you been fiddling at all?

---

### Post by Joe of loath on 2010-12-08
[http://www.whatsmyip.org/more/](http://www.whatsmyip.org/more/)

See where it thinks you are, and look down the list of information to look for clues if it happens to think you're in russia :lol:

---

### Post by idle1 on 2010-12-08
Hi Froon, No - no fiddling. In fact, I did a clean install after i started getting this problem, and haven't changed anything.

Joe - I use the firefox extension world-ip which does whois, traceroutes, reverse DNS's etc, and no it offers no clues.

I agree this probably isn't a security issue, but being a paranoid type - am wary of all things Russian/Chinese...

---

### Post by photoben on 2010-12-08
Does [this tool]("http://www.maxmind.com/app/locate_demo_ip") report you to be in the correct location?

---

### Post by endotherm on 2010-12-08
just out of curisoity, are you typing the URL in by hand?

---

### Post by idle1 on 2010-12-09
Photoben - Yes - that reports that I'm in London. I used a similar tool yesterday that came up with the same result.

Endotherm - It makes no difference if I type the url in, take it from a bookmark or from clicking a link.

BTW it's just all the link text on the page(in blue) that's in cyrillic. Fortunately I can remember what most of them are, but I'd love to have them back in English...!

---

### Post by idle1 on 2010-12-09
Here's a screenshot...

---

### Post by buellman on 2010-12-09
Same happens to me from time to time. I use 10.10 64bit at the moment.

Greets. Buellman

---

### Post by clubsoda on 2010-12-09
In Firefox, have a look at 
Edit->Preferences->Content->Languages->Choose
What have you got in there?

---

### Post by buellman on 2010-12-09
Deutsch/Deutschland [de-de]
Deutsch [de]
Englisch/Vereinigte Staaten von Amerika [en-us]
Englisch [en]

---

### Post by clubsoda on 2010-12-09
Hmm.

Have you guys run "Language Support" from the System menu since installing? One thing I've noticed on fresh installations is that the language support is usually incompletely installed or in a partially broken state. I'm not sure this will solve the issue but perhaps it's a factor.

You might also check your active net connections when the bogus page is being displayed.```
netstat -n --ip
```From that you can figure out where the page is hosted. More likely that the browser is requesting the incorrect language for some reason.

---

### Post by clubsoda on 2010-12-09
You can also visit [http://c2.com/cgi/test/](http://c2.com/cgi/test/) and check the line HTTP_ACCEPT_LANGUAGE.

---

### Post by msandoy on 2010-12-09
The simple sollution, click on "Google.com in english" below the searchbar. This changes the settings in your browser.

---

### Post by msandoy on 2010-12-09
I do not know how to read the writing in your screenshot, but even if the settings on your computer is correct, if you are automatically logged in to google, it will follow the settings from your account. You might have a hcaked google account.
Try changing your google/gmail password.

---

### Post by idle1 on 2010-12-09
Msandoy - no I don't log in automatically, but have changed passwords anyway. You're right - the google in english link works - I can't beleive I didn't see it. Must have been 'snowblinded' or something. That's what you get for staring at computer screens for thirty years...

Thanks to all for good advice.

Definitely sticking with Linux ;-)

---

### Post by zubair. on 2010-12-10
What happens when your browser is *hijacked* by a site? How do you regain control?

---

### Post by cariboo on 2010-12-10
> **zubair. said:**
> What happens when your browser is *hijacked* by a site? How do you regain control?

 Usually cleaning out your profile, or creating a new one will solve the problem.

---

