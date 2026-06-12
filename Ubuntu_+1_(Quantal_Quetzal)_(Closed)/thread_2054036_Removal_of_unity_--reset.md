---
title: "Removal of unity --reset"
date: 2012-09-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-09-06
As presented here:

[https://code.launchpad.net/~didrocks/unity/unity-reset-removal/+merge/123112](https://code.launchpad.net/~didrocks/unity/unity-reset-removal/+merge/123112)

Regards,
Effenberg

---

### Post by kansasnoob on 2012-09-06
I have mixed feelings about this :-k

There were times when it was quite useful, but OTOH there were times that it was overused (maybe more accurately "over-recommended") and a user could be very disappointed finding that they'd wiped out hours of work getting their preferred configuration set.

If I still had a brain I'd think it would have been better to "fix" it by having that command auto-create a backup config so it could be easily reversed :confused:

---

### Post by effenberg0x0 on 2012-09-06
> **kansasnoob said:**
> I have mixed feelings about this :-k

There were times when it was quite useful, but OTOH there were times that it was overused (maybe more accurately "over-recommended") and a user could be very disappointed finding that they'd wiped out hours of work getting their preferred configuration set.

If I still had a brain I'd think it would have been better to "fix" it by having that command auto-create a backup config so it could be easily reversed :confused:

I tend to agree, I feel we're at a safer place when things are updated, improved, fixed instead of deprecated and dropped. But, to be honest, I know *nothing* about the deprecation of ccsm, the move from gconf to dconf and how compiz uses that and how that impacts the usage of unity --reset. I don't know which compiz settings are being worked to be available to the ordinary users in 12.10. And I also don't know where to find the official/reliable information and plans (roadmap) for this. So I can't possibly have a usable opinion about it. I don't even know if it makes sense to test and report regarding it. And, in my opinion, QA also doesn't know. And if anyone tells me anything regarding this, I'll ask what's the source and it's reliability, where was it officially posted at. So it's a dead end :)

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-09-06
Well, it doesn't matter anymore. It was proposed, approved and merged in 3 hours:

[https://code.launchpad.net/~didrocks/unity/unity-reset-removal/+merge/123112](https://code.launchpad.net/~didrocks/unity/unity-reset-removal/+merge/123112)

Regards,
Effenberg

---

### Post by diesch on 2012-09-06
The current implementation do *unity --reset* doesn't work aynmore in 12.10 as Unity uses GSettings instead of GConf now and Metacity isn't installed anymore by default. Removing it is a sane decision.

A version that works for 12.10 needs to be rewritten from scratch. It should be possible to do that with a shell script, and that could even include a backup function.

---

### Post by mc4man on 2012-09-06
Atm dconf/gsettings is very limited, there is only 1 schema - org.compiz.integrated
Nothing in  profile > unity > plugins that is added gets a schema, nor do I see any in there by default.

Whether this is because of the move to gsettings is incomplete or something else don't know, it would be nice to see all enabled plugins get schemas
(whether supported ones or otherwise

As it stands if one causes additions to profile > unity > plugins what is in there can be directly edited in dconf-editor though with no schema cannot be set or reset thru gsettings

So atm if one was to explore a certain 'tool' you can see some ways to bork things up pretty good. In those cases it's probable that only removing 1 or 2 config files will fix

---

### Post by effenberg0x0 on 2012-09-06
> **effenberg0x0 said:**
> And if anyone tells me anything regarding this, I'll ask what's the source and it's reliability, where was it officially posted at. So it's a dead end :)


> **diesch said:**
> Removing it is a sane decision.

Hi :)

Can you please name your sources, evaluate its reliability and point us to where this info was officially posted?
BTW, I am *not* joking.

Regards,
Effenberg

---

### Post by castrojo on 2012-09-06
It's been broken since at least the move to gsettings, 3 weeks ago I think?

Here it is: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1035261](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1035261)

---

### Post by jbicha on 2012-09-06
I believe dconf reset -f /org/compiz/ basically duplicates what unity --reset would have done (except for the killing Compiz & restarting part).

You can run dconf dump /org/compiz/ first to see what custom Compiz settings you have.

dconf dump & dconf reset are really cool tools and worth learning more about.

---

### Post by effenberg0x0 on 2012-09-06
Yea, I'm familiar with dconf dump, I believe I posted stuff to dump then grep or sed or awk some times in this cycle or the previous one, I can't remember. But dconf reset is new to me, it's definitely useful :) 

But anyway Ubuntu is not designed for me. It is focused in UX for ordinary users. Normal people won't do console and many believe a shebang is some sort of pr0n. In that sense, considering that ordinary users won't ever be able to regexp match over the stdout of a query to find key/value pairs they should investigate/get/set to fix their install, I believe everyone in development is pretty confident there won't ever be a need to reset unity. And that is actually good news (if we look back at the recent past - OO and PP, unity --reset was almost motd at support boards, even here). 

Thanks,
Effenberg

---

