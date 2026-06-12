---
title: "Keypass &amp; UbuntuOne - NoScript/AppArmor"
date: 2012-05-30
forum: Security
---

### Post by krustenBrot on 2012-05-30
Hey everyone,
 
 I actually got 2 Questions, but i guess here are people more than  capapable of answering both in on Thread instead of opening 2 new  threads.
 
 1. I am using keypass to store my Passwords, and i put the key database  into my UbuntuOne folder, now everytime i unlock my database its syncing  of course - any chacne this might be a serious security risk or can i  ignore the syncing?
 
 2. just wondering if its necessary to use NoScript + AppArmor if i got  it right AppArmor restricts Firefox just to its specific Tasks - so even  if it is being captured by a malicious script - it wont be able to do  much. Right? 
 
 Thanks!

---

### Post by Soul-Sing on 2012-05-30
1) unlocking the database of keepassx, without making any changes in the database, why would it be syncing the database? If you made any changes, the locked database will be "updated", and placed in ubuntu-one.

2) the only thing i can add to your question, is to apparmor firefox with the standard apparmor profile given you via Ubuntu by Jamie Strandboge. It hardens firefox.
Using no-script is wise, RequestPolicy is also a great add-on, and quickjava i would recomment using. With the default option to disable java.
Are you now safe on the internet? No. [COLOR="Red"]Its all about your internet behaviour.[/COLOR]

---

### Post by Hungry Man on 2012-05-30
I highly suggest that you use LastPass if you're interested in syncing passwords. It's very secure and you don't really have to worry. I would not trust keepass + UbuntuOne without knowing explicit details about both.

AppArmor protects your system from exploitation. A compromised Firefox will have no access to anything it doesn't need access to.

NoScript protects your browser from in-browser attacks. XSS, ClickJacking, CSRF that can lead to both system compromise and in-browser compromise.

I prefer AppArmor but the two are not redundant, using both will improve security.

---

### Post by krustenBrot on 2012-05-31
Thank you for the provided answers.

1. KeePass is apparently syncing just 1 File and that's a **.lock* file. The changelog from version 1.08 - 1.09 says the following about  .lock files:
> * KeePass now stores the user and machine name in .lock files, so it can  show who's currently editing the file when trying to open a locked  file."So this should be safe.

> 1) unlocking the database of keepassx, without making any changes in the  database, why would it be syncing the database? If you made any  changes, the locked database will be "updated", and placed in  ubuntu-one.Jep tried it and you're totally right, it only snycs if i made changes, saved & closed the DB.  I guess that's solved :KS

2. Thanks, leoquant - added these addons :) Hungry Man: > NoScript protects your browser from in-browser attacks. XSS,  ClickJacking, CSRF that can lead **to both system compromise** and  in-browser compromise. yeah that's what i'm trying to understand, as long as my Firefox is "restricted" by AppArmor && i'm not storing any passwords or personal Data in Firefox, how is it possible to compromise my system?

---

### Post by Hungry Man on 2012-05-31
Well, it's going to be very difficult and I don't think NoScript is really necessary with AppArmor for preventing system compromise. If you want to prevent session hijacking and other in-browser attacks NoScript is useful though.

---

### Post by krustenBrot on 2012-06-01
edit: never mind... - i just have to learn more about AppArmor isntead of wasting your time! ;)

Helpful thread, thank you. I'm marking it as solved. :)

---

