---
title: "fail2ban config to block attacks on magento payflow endpoint"
date: 2019-04-01
forum: Security
---

### Post by rahul.pragma on 2019-04-01
Hi,


This is regarding the stopping DDoS attack on Magento payment gateway reported here:
[https://support.magento.com/hc/en-us/articles/360025515991-PayPal-Payflow-Pro-active-carding-activity](https://support.magento.com/hc/en-us/articles/360025515991-PayPal-Payflow-Pro-active-carding-activity)

I am trying to create the Fail2Ban rules to rate-limit the access to "/paypal/transparent/requestSecureToken/" url.

Here are a few rules I tried but nothing works:
[ATTACH]282908[/ATTACH] (Sorry, Forum doesn't allow to add the code inline due to its nature so attaching it as .txt a file)


Here are a few lines from my apache access log:
[ATTACH]282909[/ATTACH]


Can anyone please suggest the correct Regex? This will help thousands of Magento websites to prevent the hack.

Someone posted the solution here but it doesn't work for me because of the different apache log format:
[https://gist.github.com/digitalengineering/896934dd526302a68c198e1b0333219b](https://gist.github.com/digitalengineering/896934dd526302a68c198e1b0333219b)

---

