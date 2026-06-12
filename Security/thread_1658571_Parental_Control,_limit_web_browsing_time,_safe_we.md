---
title: "Parental Control, limit web browsing time, safe web browsing"
date: 2011-01-02
forum: Security
---

### Post by toolmania1 on 2011-01-02
I looked at the Dan's Gaurdian page.  Also, there is another long post in the tutorials part of this forum.  Dan's Gaurdian appears to be best with Suse Linux.  I have Ubuntu.  

1. Can I use Dan's Gaurdian with Ubuntu?

I checked the site and it said that Dan's Gaurdian will filter web content.  What type of content does it filter?  We want to filter our bad words and bad images.  

Net nanny for windows does all of this.  It also will put block images in front of bad words.  Also, in a chat, it will send an email if a bad word is posted in a chat.  

Pretty much, our 9 year old is a good kid.  But, we do not want things to come her way that she should not have to deal with.

2. Also, how can we limit her to 1 hour per day.  I can lay down a rule, sure.  But, is there something that can log that she has been on an hour?  Or, can I set up another user in Ubuntu to do some of this stuff. 

I also am pretty sure if I made a different user, that I could block all sites except a few with iptables or using the proxy trick where the ip address routes back to 0.0.0.0 except for these sites.

3. How can we view a log of chatting she would do from sites like fantage.com and webkinz.com.

Any other ideas in this area of security?

Thanks in advance!

---

### Post by toolmania1 on 2011-01-02
Can ipsniff log any chat from any web site or is it only for chat within Ubuntu?

---

### Post by toolmania1 on 2011-01-02
Also, I read about Ubuntu Christian Edition ( Ubuntu CE ).  Can I upgrade from my current Ubuntu to that version?  I do not want to reinstall everything, but I may do it since I read Dan's Gaurdian is already set up in Ubuntu CE.  Is that true?

---

### Post by cariboo on 2011-01-02
You can install dansguardian from the repositories, without having to do any extra work.

---

### Post by toolmania1 on 2011-01-02
I am told that I have not met the dependencies

"The following packages have unmet dependencies:

dansguardian : Depends : libclamav6 ( >= 0.96.5+dfsg ) but 0.96.3+dfsg-2ubuntu1.2 is to be installed.

I did install Clamav before, if that is what dansguardian is depending on.  I had problems upgrading to .96.5 though.  I am still at .96.3.  Is that that the issue?

If so, how do I upgrade clamav.  I tried a few ways, including removing clamav and installing again, but I always get .96.3.

---

### Post by cariboo on 2011-01-03
If you check the clamav thread  on this page, apparently if you enable the backports repository you should get a newer version of clamav.

---

### Post by bodhi.zazen on 2011-01-03
> **toolmania1 said:**
> I looked at the Dan's Gaurdian page.  Also, there is another long post in the tutorials part of this forum.  Dan's Gaurdian appears to be best with Suse Linux.  I have Ubuntu.  

1. Can I use Dan's Gaurdian with Ubuntu?

I checked the site and it said that Dan's Gaurdian will filter web content.  What type of content does it filter?  We want to filter our bad words and bad images.  

Net nanny for windows does all of this.  It also will put block images in front of bad words.  Also, in a chat, it will send an email if a bad word is posted in a chat.  

Pretty much, our 9 year old is a good kid.  But, we do not want things to come her way that she should not have to deal with.

2. Also, how can we limit her to 1 hour per day.  I can lay down a rule, sure.  But, is there something that can log that she has been on an hour?  Or, can I set up another user in Ubuntu to do some of this stuff. 

I also am pretty sure if I made a different user, that I could block all sites except a few with iptables or using the proxy trick where the ip address routes back to 0.0.0.0 except for these sites.

3. How can we view a log of chatting she would do from sites like fantage.com and webkinz.com.

Any other ideas in this area of security?

Thanks in advance!

Dansguradian is highly customizable, you will need to read the documentation.

If you want something more light weight, use privoxy. Again you will need to read the documentation.

I gave you a link to my blog in your other thread.

---

### Post by toolmania1 on 2011-01-03
Yes, I see the link, thanks.  I will look into this later tonight.  Thank you for your time and information.:guitar:

---

### Post by toolmania1 on 2011-01-06
I think a lot of this thread was answered under my other thread you helped with for gnome nanny.

Marking this one closed.

---

