---
title: "Site wide bayes questions"
date: 2007-05-21
forum: Server Platforms
---

### Post by mbradlcu on 2007-05-21
Hi all,
I have spamassassan setup and ?working? site wide, here's my local.cf:
> use_bayes        1
bayes_auto_learn 1
rewrite_header Subject *****SPAM*****
bayes_path /common/sys/spamdb/bayes
bayes_file_mode 0777

Ok now for the questions:
1) I've noticed that files /common/sys/spamdb/bayes { bayes_journal bayes_seen bayes_toks} now change ownership to the various email users,, why?
2) I thought the setting "bayes_file_mode 0777" should make those files wrx by all but they're ag=rw, why?
3) in interest of security should I have the bayes path some were the email users can't get to, I'm confused how to do this because in order for the email server to allow connections it's setup on our openldap system.
4) I've noticed some of the spam doesn't have a bayes rating, shouldn't the bayes rating be "0" if anything?

I've gone through the spamassassn docs the best I can but I'm obviously still a bit lost,
thanks in advance!

---

