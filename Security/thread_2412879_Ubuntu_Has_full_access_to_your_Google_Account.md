---
title: "Ubuntu Has full access to your Google Account"
date: 2019-02-18
forum: Security
---

### Post by raccoonstrait on 2019-02-18
G'day all,

Running 18.04 which is fully up to date. I use Chromium for my browser, and to log into Gmail. Google recently sent an email suggesting a security checkup. One of the issues listed was that Ubuntu has full access to my Google account. I removed that permission which then logged me out of Gmail. I re-logged into Gmail which then put Ubuntu back on the list of having full access to my Google account.

Now, I understand why Ubuntu might want access to my Google account, and I disagree with all the possible arguments. So my question then is, is there some way to block Ubuntu from having full access to my Google account while still using Gmail via the Chromium browser?

Thanks

Raccoon Strait

---

### Post by mikewhatever on 2019-02-18
I don't think it is accurate to say "Ubuntu has full access to my Google account". In fact, it's a rather vague statement, which doesn't mean much, or makes sense. 
As a Debian distro, Ubuntu is a collection of integrated programs and utilities that work together. Now, ask yourself which programs have or want access to your Google account without explicit permission. The answer is, obviously, none.

---

### Post by raccoonstrait on 2019-02-18
I don't know the accuracy of the statement. It is Google that is reporting it as part of a security checkup.

[https://myaccount.google.com/intro/security-checkup?hl=en-US](https://myaccount.google.com/intro/security-checkup?hl=en-US)

I think that will only actually work if your logged into your Google account.

I guess I should add that originally Google listed two items. One was Debian, and the other Ubuntu. I had used one of my Raspberry Pi's, running Debian Stretch, for email after a theft of my computers. Then I bought a new notebook to use as my desktop and stopped using the Debian. When I followed the Google instructions and removed both of those, I was only logged into the Ubuntu, and when I logged into Gmail again, only the Ubuntu showed back up in the security checkup. If I go to the Raspberry Pi and log into Gmail, I bet that would show up again in the security checkup. Of interest, my machine is dual bootable, and though I don't often use Gmail in Windows, I do sometimes, and they were not listed in the security checkup.

Raccoon Strait

---

### Post by mikewhatever on 2019-02-20
Well, I don't think there is anything to be done here. It looks like Google named 'Chromium on Ubuntu' just Ubuntu. This is the way it is, we can't fix it.
The issue has been raised before, and some couldn't help it to assume there is an evil conspiracy.
[https://askubuntu.com/questions/989359/why-has-the-ubuntu-app-full-access-to-my-google-account](https://askubuntu.com/questions/989359/why-has-the-ubuntu-app-full-access-to-my-google-account) 

There is zero evidence that Ubuntu wants or has "full access" to Google accounts. Ignoring it is probably the best way to go, but if it really bothers you, do ask Google for clarifications.

---

### Post by raccoonstrait on 2019-02-21
Thanks mikewhatever,

I appreciate your feedback. I guess this needs to be written off as some inefficient coding in Chromium. By inefficient I am thinking that there is probably more than one way to code the logging in to Google, and the easier option was chosen. However, like you say, ignoring it is likely the best. 

BTW, I have asked Google, and got nothing of any value back, which is why I came here.

Thanks again for your time and effort.

Raccoon Strait

---

