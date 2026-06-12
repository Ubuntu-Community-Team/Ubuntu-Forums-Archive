---
title: "SA-learn (spamassassin)"
date: 2009-08-01
forum: Server Platforms
---

### Post by polo23 on 2009-08-01
Hello, I found out the following information:
my **SPAMD daemon is running under root**. But I have in master.cf(postfix configuration file) the following lines:
 
Postfix master process configuration file. For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# ==================================================  ========================
# service type private unpriv chroot wakeup maxproc command + args
# (yes) (yes) (yes) (never) (100)
# ==================================================  ========================
 [B]smtp inet n - n - - smtpd
-o content_filter=spamfilter:dummy
 [/B]
 
==================================================  ==================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe([IMG]http://www.linuxforums.org/forum/images/smilies/icon_cool.gif[/IMG] delivery
# agent. See the pipe([IMG]http://www.linuxforums.org/forum/images/smilies/icon_cool.gif[/IMG] man page for information about ${recipient}
# and other message envelope options.
# ==================================================  ==================
 
 [B]spamfilter unix - n n - - pipe
flags=Rq user=spamfilter argv=/usr/local/bin/spamfilter -f ${sender} -- ${recipient}[/B]
 
Spamfilter is user for spamassassin(spamd)(but for me is strange that spamd is running under root). I configured master.cf according to
 **h-t-t-p://onetforum.com/fourm/viewtopic.php?p=27]Kalinga's]Kalinga's Community Support Forum &bull; View topic - Integrating Spam Assassin with Postfix**(h-t-t-p replace by http)
 It is recomended by spamassassin original www pages.
 
 
In local.cf I have: **bayes_path /home/spamfilter/.spamassassin/bayes.**
 
And now when I send mail(for example at 21:00 oclock) which spamassassin mark like autolearn= spam and I show to the /home/spamfilter/.spamassassin/bayes so I can see that files bayes_tooks nad bayes_seen was modified in 21:00 but their size didnt change? How is it possible - when spamssassin changes the files so they have to increase their size...When I type command **sa-learn --dump magic** so I can see that in row nspam increase his value +1. This is confirmation that autolearn works.(but the database dont increase his size).
 
My second problem: I get mail with sign autolearn=ham. I take the mail and I use the following command: **sa-learn --spam --file mail** (at 21:55 oclock)l. When type **sa-learn --dump magic** so I can see that nspam was increased +1 its OK. But when I look to the /home/spamfilter/.spamassassin I can see that database file was change but their size didnt change. Its normal???
 
And the last problem: When I get mail with sign autolearn=ham so I tried type **sa-learn --spam --file mail**. When I got the same mail so spamassassin mark the mail again autolearn=ham. How is it possible when I learn bayes by hand (**sa-learn --spam --file mail**) that this mail is spam? I have explicit set in local.cf bayes_min_spam_num 1. This means that for bayes is sufficient one mail for learning(according to me). But it dosesnt work.
 
Thanks for advise(I need it necessary).
 
 
 
 
Sorry for my terrible english.

---

