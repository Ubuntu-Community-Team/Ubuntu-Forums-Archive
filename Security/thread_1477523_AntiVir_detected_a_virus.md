---
title: "AntiVir detected a virus?"
date: 2010-05-08
forum: Security
---

### Post by The Fridge on 2010-05-08
Was running AntiVir manually (I like to do so periodically) and was shocked to see it had detected a virus! In my panic I chose to delete the files, although they could have been false positives. I am running 9.04.

Here is a copy and paste from the terminal window:


  file: /home/fraser/.icedteaplugin/cache/http/lowes-com.wiktionary.org.weebly-com.teensitedesign.ru/pics/JavaJ.jar
    last modified on  date: 2010-03-17  time: 18:14:44,  size: 6535 bytes
    ALERT: billi/Hieeyfc.class <<< JAVA/Dldr.Ag.DIVV ; virus ; Contains detection pattern of the Java virus JAVA/Dldr.Ag.DIVV
    ALERT: billi/Hirwfee.class <<< JAVA/Agent.3049 ; virus ; Contains detection pattern of the Java virus JAVA/Agent.3049
    ALERT: billi/Hiydcxed.class <<< JAVA/Agent.2972 ; virus ; Contains detection pattern of the Java virus JAVA/Agent.2972
    ALERT-URL: [http://www.avira.com/en/threats?q=JAVA%2FDldr%2EAg%2EDIVV](http://www.avira.com/en/threats?q=JAVA%2FDldr%2EAg%2EDIVV)
    ALERT-URL: [http://www.avira.com/en/threats?q=JAVA%2FAgent%2E3049](http://www.avira.com/en/threats?q=JAVA%2FAgent%2E3049)
    ALERT-URL: [http://www.avira.com/en/threats?q=JAVA%2FAgent%2E2972](http://www.avira.com/en/threats?q=JAVA%2FAgent%2E2972)
  which action to take (quit, none, rename, move, delete)? [none] delete
  will use the specified action [delete]
  action taken: file deleted
--------------------------------------------------------------------------------------------------------------------


Just checked out the URLs and the Avira site is drawing a blank for them. I hope I haven't screwed everything up!

Any help would be greatly appreciated,

Thanks

---

### Post by wilee-nilee on 2010-05-08
If I was going to use AV software on my Linux OS I would use clamav/clamtk whatever name is on your distribution; in synaptic and avast, avira is well not as robust as avast. You don't need AV software but a locked down system, and the correct add-ons using FF will save you a lot of hassle. There is a security thread by a mod I would find it and take a read.

---

### Post by mikewhatever on 2010-05-08
What kind of help do you want? I mean, you've deleted the supposedly infected file. What else? Does java still work?

---

### Post by The Fridge on 2010-05-09
> **mikewhatever said:**
> What kind of help do you want? I mean, you've deleted the supposedly infected file. What else? Does java still work?I was just wondering if anyone had encountered that before. I'm still quite new to Linux, so I'm from the background where a virus is encountered and I immediately assume there's going to be more.

Also, is there a possibility that there could have been a file that was indeed a Windows virus, but not actually active on Linux, but still detected by AntiVir?

@wilee-nilee I've got Clam, but when I run 'freshclam' it says it's out f date and to check the website, but I didn't think you could update it yourself and had to wait for Ubuntu updates.

---

### Post by CharlesA on 2010-05-09
It looks like whatever "virus" was on the machine was in the browser cache. Delete it (which you did) and you will be fine.

Not to mention that Viruses written for windows don't run on Linux.

ClamAV does that when the engine is out of date (not the virus definitions). I haven't used it in ages, since it would throw up false positives for me all the time.

---

### Post by mikewhatever on 2010-05-10
> **The Fridge said:**
> I was just wondering if anyone had encountered that before. I'm still quite new to Linux, so I'm from the background where a virus is encountered and I immediately assume there's going to be more.

Also, is there a possibility that there could have been a file that was indeed a Windows virus, but not actually active on Linux, but still detected by AntiVir?

@wilee-nilee I've got Clam, but when I run 'freshclam' it says it's out f date and to check the website, but I didn't think you could update it yourself and had to wait for Ubuntu updates.

Apparently, according to the output you didn't have a Windows virus, but a Java one. Keep java updated.

---

### Post by Rubi1200 on 2010-05-10
You might also want to consider using the NoScript addon for Firefox if you are not already using it.

---

### Post by johnharris on 2010-09-09
I believe antivir is a fake antivirus program.  please see this:
[http://free-pc-guides.com/virus-removal-guides/how-to-uninstall-remove-antivir-solution-pro-virus-removal-guide-02825](http://free-pc-guides.com/virus-removal-guides/how-to-uninstall-remove-antivir-solution-pro-virus-removal-guide-02825)

---

### Post by uRock on 2010-09-09
Avira AntiVir is not a fake program.

---

### Post by howefield on 2010-09-09
> **johnharris said:**
> I believe antivir is a fake antivirus program.  please see this:
[http://free-pc-guides.com/virus-removal-guides/how-to-uninstall-remove-antivir-solution-pro-virus-removal-guide-02825](http://free-pc-guides.com/virus-removal-guides/how-to-uninstall-remove-antivir-solution-pro-virus-removal-guide-02825)

Avira Antivir, which the OP is referring to (all those months ago) isn't fake.

You are talking about a different "product"

---

### Post by howefield on 2010-09-09
Sorry, double post. Pressed quote instead of edit...

---

### Post by johnharris on 2010-09-17
whoa geez louise excuse me.

---

