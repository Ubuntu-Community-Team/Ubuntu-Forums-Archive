---
title: "Where can I find an email server that includes calendar support?"
date: 2012-07-26
forum: Server Platforms
---

### Post by heavylifting on 2012-07-26
Ok so I am looking for an Ubuntu email server that has support for calendaring. Right now I am looking for the ability to sync mobile devices such as all Apple mobile devices plus Android. I have setup my Postfix server but I haven't been able to find a calendar system with syncing across devices.

---

### Post by Vishal Agarwal on 2012-07-26
These all features are available with zimbra email server.

---

### Post by volkswagner on 2012-07-26
If you are happy with your email/postfix you can use a separate calendar sync like [Owncloud]("http://owncloud.org/").  Owncloud includes file sync and contact sync as well.

For an all in one solution email/calendar/contacts [Citadel]("http://www.citadel.org/") is a nice solution, which is a little lighter weight compared to Zimbra.

I'm not sure why, but it appears Citadel's site is not responding this morning.

---

### Post by spjackson on 2012-07-26
+1 for Zimbra.

---

### Post by LHammonds on 2012-07-26
+1 Zimbra (see my sig for my step-by-step install notes...with detailed info for the iPhone solution)

We currently use Exchange but are poised to migrate to Zimbra very soon.

---

### Post by heavylifting on 2012-07-26
Ok awesome thanks everyone! I am checking out Citadel now and really like what I see so far. If I have already installed Postfix do I need to uninstall it first?

---

### Post by sentinelace on 2012-07-29
Interesting does Zimbra do spam filtering?  How is it compared to qmail?

---

### Post by spjackson on 2012-07-29
> **sentinelace said:**
> Interesting does Zimbra do spam filtering?  How is it compared to qmail?
Zimbra includes Spam Assassin and Clam Anti-virus. I can't comment on how it compares to qmail.

---

