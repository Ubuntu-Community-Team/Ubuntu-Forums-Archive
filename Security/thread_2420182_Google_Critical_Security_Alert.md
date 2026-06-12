---
title: "Google Critical Security Alert"
date: 2019-05-31
forum: Security
---

### Post by Owen_Murphy on 2019-05-31
I have an old machine running Ubuntu and whenever I boot it up, I get a google Critical Security Alert e-mail saying that google prevent someone/something from accessing my google account.  The IP listed is from my computer and it only happens when I boot up this particular computer, so there's definitely something on the computer that's trying to log into my google account when I boot up.  I'm hoping it's nothing nefarious, like some program I added my google credential to a while back, but I'd like to be able to check.

How would I check to see what specifically on my computer is trying to log into my google account?

---

### Post by #&amp;thj^% on 2019-05-31
Google offers a [Recently Used Devices ]("https://myaccount.google.com/intro/security")page that shows you where specific devices have accessed your account. This page is available from the Sign-in & Security account section in your Google account settings page.

---

### Post by Owen_Murphy on 2019-05-31
I meant is there a way to check on my computer to see what is trying to sign into google.  The google sign-in and security doesn't really show too much information other than the location and operating system.  Basically I want to see specifically what program/process is trying to log into my google account on my computer

---

### Post by #&amp;thj^% on 2019-05-31
Yep I knew what you meant, but this is the only reliable way.
You can see your sign-in history, including the dates and times that your Gmail account was used. You can also see the IP addresses which were used to access your account.
So if all the IP's aren't from you or your system, I'd wipe and re-install, just no 2 ways about that. :)
BTW: How do I revoke and re-authorize access to my Google account?<<<If needed: [https://www.cirrusinsight.com/support/gmail/how-do-i-revoke-and-re-authorize-google-authorization](https://www.cirrusinsight.com/support/gmail/how-do-i-revoke-and-re-authorize-google-authorization)
And: [https://blog.savagesec.com/worried-someone-is-accessing-your-gmail-account-1c14e2039e6b](https://blog.savagesec.com/worried-someone-is-accessing-your-gmail-account-1c14e2039e6b)

---

### Post by kpatz on 2019-05-31
What version of Ubuntu is it?  18.04 and higher (and some older ones?) let you add your online credentials to places like Facebook, Google, etc.  Maybe you did this with your Google account?  Maybe you have an email client on there like Thunderbird that's set up to access your Google account?  What does the sign-in history on Google say?  Are there any details as to what OS, application, etc. tried to log in?

When did you last change your Google password?

---

### Post by DuckHook on 2019-05-31
You know that it's coming from your old machine, so there's limited exposure to your Google account. Since it is also localized in this way, you may wish to consider running some sort of packet sniffing app on your machine. Something like tcpdump would give you an avalanche of info—the usual difficulty of which is sifting through the resulting haystack looking for the needle.

You mentioned that this is plain vanilla Ubuntu—did you perchance sign up Google to be one of your Online Accounts in System Settings? This is usually done to enable Gnome Calendar/Task List/e-mail alerts. FWIW, I find this setting quite useful and have set my Google security to allow it.

Also FWIW, I find Google to be irritatingly alarmist. Mrs DuckHook has locked herself out of Google's services many a time because she reflexively invokes Google's higher security restrictions when it characterizes Thunderbird as an untrustworthy app.

---

### Post by lisati on 2019-06-01
> **DuckHook said:**
> Also FWIW, I find Google to be irritatingly alarmist. Mrs DuckHook has locked herself out of Google's services many a time because she reflexively invokes Google's higher security restrictions when it characterizes Thunderbird as an untrustworthy app.

Agreed. On more than one occasion, I've managed to trigger a handful of Google alerts when, for one reason or another, I've reset an android device back to factory settings and used the exact same email address for its accounts and settings.

---

### Post by Owen_Murphy on 2019-06-03
Ah, it's probably Thunderbird.  I had it linked to my google account, but I haven't really done anything with it in a while.  It's probably trying to log into google and getting flagged for whatever reason.  When I get a chance, I'll have to sign out from Thunderbird and see if that fixes it.

---

### Post by TheFu on 2019-06-03
Google doesn't like it when we use anything other than Google-Chrome browser to access their content.  If you really want to see google complain, try using a VPN and changing the exit nodes around the world multiple times a day.  Google freaks out completely and sends multiple warning messages.

Basically, google's security team has decided that warning about any other program, using standard protocols and authentication, is a security risk.  Really, it is a data risk to google capturing as much personal information and tracking our use of their services and millions of other services thanks to webmasters deciding to allow google-analytics on their web properties.  UF does this by hooking into google's tagging infrastructure. They also hook into facebook's tracking here too, BTW.

Besides using a packet sniffer, you might be able to see something using the port number and **lsof**, but getting the timing just right will be nearly impossible.

Please mark the thread solved - thread tools - near the top.

---

### Post by #&amp;thj^% on 2019-06-03
> **TheFu said:**
> Google doesn't like it when we use anything other than Google-Chrome browser to access their content.  If you really want to see google complain, try using a VPN and changing the exit nodes around the world multiple times a day.  Google freaks out completely and sends multiple warning messages.

[U]Basically, google's security team has decided that warning about any other program, using standard protocols and authentication, is a security risk.  Really, it is a data risk to google capturing as much personal information and tracking our use of their services and millions of other services thanks to webmasters deciding to allow google-analytics on their web properties.  
[/U]
Please mark the thread solved - thread tools - near the top.
Yep I agree, it's just a placebo effect for the user feeling safer.
Kind of reminds me of a out of whack car alarm.:D

---

