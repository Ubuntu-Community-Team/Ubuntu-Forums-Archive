---
title: "Facebook Virus?"
date: 2012-11-02
forum: Security
---

### Post by otetiani on 2012-11-02
Maybe I'm paranoid, but this is the second time I had a "system" pop-up saying I had a system error, no details, right after logging into Facebook.

The first time I ignored it as a "glitch" you know maybe I clicked to fast or something or hit a button.

The second time I clicked Send Report (the only other option other than cancel) and it requested my password, which I have never seen before.

Tried looking at logs in /var/log/ but couldn't find any errors.

any way I can find if there was an actual error?

---

### Post by gerowen on 2012-11-02
I've had this happen a couple of times and as far as I can tell the reason it prompts for the password is because the error occurred in a file that a normal user account does not have read access to.  Next time the error pops up and asks to send a report you can click the "Details" button and it will tell you what process specifically had the issue.

---

### Post by otetiani on 2012-11-02
That's why I desided to send a report, I was hoping to see details, but it requires a password first which I did not wish to do as I suspect it is a virus.

I have now combed through all the logs in /var/logs/ and with the exception of the system log I am confident there is no error logged there.

---

### Post by otetiani on 2012-11-02
Found it, it was a ```
colord
``` crash.

my bad, just never saw a bug report in that format where it asks for a password prior to showing details.

---

### Post by cryptotheslow on 2012-11-02
I've been running 12.04 since it was in beta and colord is and has been forever crashing along with the bluetooth daemon. Most times the laptop will be sat idle and colord just randomly pegs out and reports a crash.

The crash report process asks for a password because colord runs under the user "colord" - rather than your user account, so you need to enter your sudo password for the crash report to access the colord's space to construct a full report.

In that respect it is nothing to worry about - just user separation doing what it should.

My question would be why does colord crash so often?

---

### Post by cariboo on 2012-11-02
Check the crash logs in /var/crash, it may tell you in amongst all the rest of the information why colord is crashing.

---

