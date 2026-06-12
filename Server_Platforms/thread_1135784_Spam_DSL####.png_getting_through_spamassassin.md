---
title: "Spam DSL####.png getting through spamassassin"
date: 2009-04-24
forum: Server Platforms
---

### Post by robinbillings on 2009-04-24
Hello everyone,

I am using the 8.04 LTS server edition with the configuration specified in the default documentation for setting up mail servers, using Postfix, spamassassin, amavis-new, clamav, dkim-filter, and python-policyd-spf (as documented here: 

[https://help.ubuntu.com/8.04/serverguide/C/mail-filtering.html](https://help.ubuntu.com/8.04/serverguide/C/mail-filtering.html)

It is working great with one exception, I keep getting spam with graphic png files and random text, with the png files advertising Viagra + Cialis.  All the png files are of this format: DSL####.png, with the #### being a 4-digit number.  Is there a simple configuration switch in amavis-new or spamassassin that can flag these files for labelling as ****SPAM****?  Any assistance would be most appreciated!

Robin Billings

---

### Post by tigerstripedcat on 2009-04-26
I know I'm getting tons of them.  I read somewhere to add:

mimeheader LOCAL_DSL_ATTACHMENT Content-Type =~ /name="dsl[0-9]{4}\.png"/i


to the 

~/.spamassassin/user_prefs

file

I hope it works.  If you find a better way, post it here, and I'll do the same.

TSC

---

