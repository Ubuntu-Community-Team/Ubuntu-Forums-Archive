---
title: "Do firefox add-ons and apparmor give full protection against attack due to browing?"
date: 2012-04-02
forum: Security
---

### Post by arroy_0209 on 2012-04-02
I am looking for the ultimate solution to the problem of threat due to internet browsing. Is there any? I have these add-ons: no-script, adblockplus, click&clean, better-privacy and also ubuntu-supplied apparmor profile for firefox enforced. Do I still need to be cautious while browsing? People advise, e.g., not to click any link in emails from unknown senders. If someone does that, will he/she be affected even though the add-ons and apparmor are enabled?

Second, to what extent is it possible to to stay from clicking links in emails? If I register with some discussion forum, often they will send a link via email, to click and complete the procedure. How do I know beforehand that this particular "clicking" will not affect me? It seems, at some point we will have to give up desire to stay totally secure and take risk or give up browsing altogether. Do you agree?

---

### Post by Dangertux on 2012-04-02
> **arroy_0209 said:**
> I am looking for the ultimate solution to the problem of threat due to internet browsing. Is there any? I have these add-ons: no-script, adblockplus, click&clean, better-privacy and also ubuntu-supplied apparmor profile for firefox enforced. Do I still need to be cautious while browsing? People advise, e.g., not to click any link in emails from unknown senders. If someone does that, will he/she be affected even though the add-ons and apparmor are enabled?

Second, to what extent is it possible to to stay from clicking links in emails? If I register with some discussion forum, often they will send a link via email, to click and complete the procedure. How do I know beforehand that this particular "clicking" will not affect me? It seems, at some point we will have to give up desire to stay totally secure and take risk or give up browsing altogether. Do you agree?

Common sense predicates most of the answer to your last question. That being said, there is a bit of a misunderstanding about Apparmor in this last bit.

Apparmor confines applications on a process by process basis. For instance, if you click something, download it , run it and it starts it's own PID, apparmor will do nothing, it has no profile for that PID.

Now if something you click injects code into firefox, then it is tried to run from firefox's PID, and firefox tries to access something it shouldn't... I don't know.../bin/bash maybe... Apparmor will stop this.

Hope that helps.

---

### Post by Cavsfan on 2012-04-02
For Firefox, Noscript is a very good addon but, sort of a pain to initially setup.
I also use WOT (web of trust). WOT is not perfect but, better than nothing. It has red circles next to known bad websites, yellow circles next to iffy websites 
and green circles next to known good websites.

---

### Post by arroy_0209 on 2012-04-02
Thanks for your advices. Regarding what Dangertux wrote, I am actually considering the second possibility you mentioned. Downloading a program is not I have in mind. At most I download pdf/ps files from journals etc or pictures from wikipedia etc. These are opened by evince or eog so I hope there is nothing to worry from that side.

---

### Post by Dangertux on 2012-04-02
> **arroy_0209 said:**
> Thanks for your advices. Regarding what Dangertux wrote, I am actually considering the second possibility you mentioned. Downloading a program is not I have in mind. At most I download pdf/ps files from journals etc or pictures from wikipedia etc. These are opened by evince or eog so I hope there is nothing to worry from that side.


Keep in mind once the file is opened by another application, it is THAT application's apparmor profile (if there is one) that will affect it

Hope this helps.

---

### Post by Cavsfan on 2012-04-02
> **arroy_0209 said:**
> Thanks for your advices. Regarding what Dangertux wrote, I am actually considering the second possibility you mentioned. Downloading a program is not I have in mind. At most I download pdf/ps files from journals etc or pictures from wikipedia etc. These are opened by evince or eog so I hope there is nothing to worry from that side.

I've never had a problem with PDFs although Noscript will confirm that you want to open it and there should be no problem whatsoever downloading pictures.

---

### Post by arroy_0209 on 2012-04-02
I get your point and I think the evince is also protected by apparmor by default. This is known from result of "sudo aa-status" which shows that 13 profiles (including one for evince) are in enforce mode. But I have no profile for eog. I tried to learn apparmor but gave up. It is so time-consuming for people like me to learn new languages. May be ubuntu can provide apparmor profiles for such common applications. Otherwise there will be no other way and I will be forced to learn myself. When I gave up windows for linux I did not imagine that security will remain a headache.

Thanks for your suggestions.

---

### Post by Cavsfan on 2012-04-02
> **arroy_0209 said:**
> I get your point and I think the evince is also protected by apparmor by default. This is known from result of "sudo aa-status" which shows that 13 profiles (including one for evince) are in enforce mode. But I have no profile for eog. I tried to learn apparmor but gave up. It is so time-consuming for people like me to learn new languages. May be ubuntu can provide apparmor profiles for such common applications. Otherwise there will be no other way and I will be forced to learn myself. When I gave up windows for linux I did not imagine that security will remain a headache.

Thanks for your suggestions.

IMHO, there is not much of a security issue with Linux. I dual boot windows 7 and Lucid Lynx and even in Windows 7 with FF and the above mentioned addons, 
I have never had any problems there either.
In windows, you just have to right click on a downloaded file and then click Scan with Antivirus software.
If people did that for every file, they would never get a virus. But, I know you are not asking about windows. Just thought I'd throw that out there.

In Ubuntu, I personally have never seen or heard of any breech of security.

---

### Post by Ms. Daisy on 2012-04-03
> **Cavsfan said:**
> In Ubuntu, I personally have never seen or heard of any breech of security.
[http://ubuntuforums.org/showthread.php?t=1947144](http://ubuntuforums.org/showthread.php?t=1947144)
 
Now you have.

---

### Post by Cavsfan on 2012-04-03
> **Cavsfan said:**
> In Ubuntu, I personally have never seen or heard of any breech of security.

> **Ms. Daisy said:**
> [http://ubuntuforums.org/showthread.php?t=1947144](http://ubuntuforums.org/showthread.php?t=1947144)
 
Now you have.

It looks pretty much self inflicted and on a developmental release.

From post #4 in that thread:
"Now I know: I have messed up with Firefox add-ons long time ago.
 I was finding information about XSS (Cross Site Scripting) and accepted XXS 0.4.5  add-on :oops:.
 **But the key issue is that Firefox created *tor* system connection (my own fault ), but when I disabled add-on, Firefox did not take away *tor* start from init procedure!"**

My FF Addons: BetterPrivacy (deletes persistent flash cookies), Biscuit (I select cookies to keep when FF is closed), Collusion, Noscript, Tab Control, Ubuntu Firefox Modifications and WOT.
Pretty sure that with these addons and Lucid LTS, I will have no trouble.

My windows 7 setup has never even had any serious problems with the same addons and Avira free antispyware. I'm pretty careful.

---

### Post by dontquoteme on 2012-04-06
It's worth suggesting that you try the startpage.com Proxy which has SSL options for viewing pages.

[www.startpage.com]("http://www.startpage.com") 
Startpage does not record your IP!!  And they don't resell on your data like other search engines.  They use SSL encryption so that not even your ISP can see  which pages you're browsing - so excellence in privacy is guaranteed.  Their video explains how they work.

Startpage - Youtube
[http://www.youtube.com/watch?v=qv3SCbI5KFM](http://www.youtube.com/watch?v=qv3SCbI5KFM)

As you can use SSL to view the sites you're safe from attack - as the site never "sees" you... only Startpage.   They're like a firewall between you and the site - and it's free. :)

---

