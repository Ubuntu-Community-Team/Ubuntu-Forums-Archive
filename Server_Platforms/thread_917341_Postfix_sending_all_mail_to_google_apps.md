---
title: "Postfix sending all mail to google apps"
date: 2008-09-11
forum: Server Platforms
---

### Post by glave on 2008-09-11
I recently had to reinstall my server and I've hit a snag on setting things back up, and I don't have the foggiest where to begin.


Well over a year ago, I dumped off my mail over to Google Apps for simplicity. Right off the bat, I was still getting any server related messages (From cron or mdadm being sent to root, from root) delivered. Messages arrived correctly showing they were FROM root. I did not have to setup a relay to google or anything.

I currently have gotten postfix reinstalled, and I used instructions primarily from [here]("http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps"). The problem is that since I'm connecting to gmail's smtp using my personal credentials, all emails appear as if **I** am the sender, and end up in my sent email folder (label).

How can I set myself back up in such a way that my system sends out all of its emails as root, or whatever, and they arrive at my google apps hosted domain just fine? This server just sends its mail out, and has no need for anyone to ever check mail on it at all.

---

### Post by inphektion on 2008-09-11
I've never used postfix like you are describing so I'm just taking a guess but do you have a masquerade_domain?  Try setting that.

---

### Post by MountainX on 2008-12-21
I'm working on the same issue. I just found this site:
[http://blog.twinklesprings.com/2008/03/27/remote-mail-delivery-for-google-apps-and-postfix-mail-server/](http://blog.twinklesprings.com/2008/03/27/remote-mail-delivery-for-google-apps-and-postfix-mail-server/)

It looks like it addresses the question, but I'm still not 100% clear on how to implement the proposed solution... maybe you will figure it out before I do.

---

### Post by MountainX on 2009-01-29
I have this working really well. Not sure if anyone cares, but if you do, leave a message and I'll provide some details about my solution.

---

### Post by hyper_ch on 2009-01-30
have a look at "always_bcc"

---

### Post by codedmin on 2009-10-13
> **MountainX said:**
> I have this working really well. Not sure if anyone cares, but if you do, leave a message and I'll provide some details about my solution.

Hy would like some tips.

Thanks

---

### Post by MountainX on 2009-10-13
> **codedmin said:**
> Hy would like some tips.

Thanks

**My References**:
[COLOR=#000080]_[[SIZE=2]http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps[/SIZE]]("http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps")_[/COLOR]
  [COLOR=#000080]_[[SIZE=2]http://blog.twinklesprings.com/2008/03/27/remote-mail-delivery-for-google-apps-and-postfix-mail-server/[/SIZE]]("http://blog.twinklesprings.com/2008/03/27/remote-mail-delivery-for-google-apps-and-postfix-mail-server/")_[/COLOR]
  [COLOR=#000080][U][[SIZE=2]http://flurdy.com/docs/postfix/#config-simple-mta[/SIZE]]("http://flurdy.com/docs/postfix/#config-simple-mta")

[http://www.howtoforge.com/block_spam_at_mta_level_postfix](http://www.howtoforge.com/block_spam_at_mta_level_postfix)
[http://www.howtoforge.com/postfix_relaying_through_another_mailserver](http://www.howtoforge.com/postfix_relaying_through_another_mailserver)
[http://www.howtoforge.com/virtual_postfix_antispam](http://www.howtoforge.com/virtual_postfix_antispam)
[http://www.howtoforge.com/howtos/email/antispam-antivirus](http://www.howtoforge.com/howtos/email/antispam-antivirus)
[http://www.howtoforge.com/drupal-plus-postfix-integration-under-ubuntu-8.04](http://www.howtoforge.com/drupal-plus-postfix-integration-under-ubuntu-8.04)
[http://www.postfix.org/docs.html](http://www.postfix.org/docs.html)
[http://www.postfix.org/DEBUG_README.html](http://www.postfix.org/DEBUG_README.html) 
[http://knol.google.com/k/johnny-chadda/how-to-set-up-an-email-server-using/3fn8hfdoyus04/2#](http://knol.google.com/k/johnny-chadda/how-to-set-up-an-email-server-using/3fn8hfdoyus04/2#) 
[/U][/COLOR]

---

