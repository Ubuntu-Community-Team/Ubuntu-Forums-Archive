---
title: "Have I been hacked"
date: 2011-09-14
forum: Security
---

### Post by BUTTS on 2011-09-14
Hi,
  I hope this is the right place to ask this. I am running Wordpress on my Ubuntu 10.04 desktop. So I am running Apache2 and phpmyadmin locally. To get the thing working properly, I have had to spend a lot of time reading various tutorials. I have had to enable things like write permissions on various folders et. But I must admit, I have been following with blind faith and I admit not really knowing what I am doing. Cutting a long story short, I received an email yesterday from facebook telling me this.
 Quote: ‘A new unknown device logged into your Facebook account (Monday, 12 September 2011 at 14:03) from (my town), ENG, GB (IP=xxx.xxx.xx.xxx).(Note: This location is based on information from your ISP or wireless provider.)’.

 I won’t reveal the IP address for obvious reasons. I was forty miles away at the time it was supposed to have been hacked. Now the IP=xxx.xxx.xx.xxx is not the same ip number as local host 127.0.0.1. The odd thing is I entered IP=xxx.xxx.xx.xxx as the url in my browser on my Ubuntu setup and it came up with Apache is working, just like when you enter localhost (127.0.0.1). Have I compromised my security or am I being paranoid.

Please advise,
	Butts.

---

### Post by spynappels on 2011-09-14
Did someone else log in to your FB acct from your computer while you were away?

---

### Post by BUTTS on 2011-09-14
No. There is no way someone could do that, believe me!

---

### Post by spynappels on 2011-09-14
And the IP was definitely your public IP?

---

### Post by psrdotcom on 2011-09-14
If your IP is assigned by DHCP, then it is not at all a problem. if you have static IP address from your ISP, then if you login with any one your mobile devices, then also no probs.
:)

---

### Post by BUTTS on 2011-09-14
Hi. Thanks for the replies so far by the way. 'Is that my public IP'? Ahh..didnt really think of that. By that do you mean is it my **static** IP that my isp gives me? I must admit, I haven't checked. I will most probably check that out this evening. Didnt think though that my own ip would cause Apache to give me the 'it's working message' when inputted in the browser bar. But I am at the limits of my knowledge here. I'm learning though. Possibly by getting my fingers burnt. Ouch....

---

### Post by kagz on 2011-09-14
i dont think you have been hacked...i would strongly advice you change your passwords just to make sure u r safe..

---

### Post by Dangertux on 2011-09-14
If it's you're public IP I wouldn't sweat it.

I agree , just change your passwords.

---

