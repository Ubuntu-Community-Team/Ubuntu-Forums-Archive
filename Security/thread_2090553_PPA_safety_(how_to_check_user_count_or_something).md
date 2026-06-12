---
title: "PPA safety (how to check user count or something)?"
date: 2012-12-02
forum: Security
---

### Post by ksatta1 on 2012-12-02
I've been using PPAs for ages. I've googled  about it etc and I always keep finding suggestions to check how many  users are using it. I've always tried to find that info, but I can't see  it anywhere. For example: [https://launchpad.net/~apt-fast/+archive/stable]("https://launchpad.net/%7Eapt-fast/+archive/stable") . I can't find any link to check user counts, comments etc.


  Eventually I just give up and install. Now I decided to figure out this problem which is affecting my Ubuntu security (in theory anyway) :)


What do you check before adding a PPA?

---

### Post by ibjsb4 on 2012-12-03
Its been around since Lucid 10o4 and last update was 9 days ago.  Don't know what security problem your dealing with, but the package looks good.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=apt-fast&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=apt-fast&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by ksatta1 on 2012-12-03
I'm sure apt-fast is fine, it was just an example. I'm just curious how I can get some idea that the packages don't try to steal my passwords or something (this is just theory, it's possible). In other words I just want to steer clear of malicious packages.

If the packages make my Ubuntu crash every 5mins or something, that's fine, it's just a fun challenge to get it all fixed :) I'm sure this is what most users are trying to avoid, but for me it's just that I don't want to get any malicious packages.

> Its been around since Lucid 10o4 and last update was 9 days ago.  Don't  know what security problem your dealing with, but the package looks  good.Hmm.. If the PPA provides lucid packages that doesn't neccessarily mean anything, it could've been uploaded yesterday?

But for now I have only found this to do some checking: [https://launchpad.net/~apt-fast/+archive/stable/+builds?build_state=built&batch=75&direction=backwards&start=225](https://launchpad.net/~apt-fast/+archive/stable/+builds?build_state=built&batch=75&direction=backwards&start=225) . From there I can see that the first build was published in June 2012, so atleast it's been around that long. But I still have no idea if anyone has ever downloaded it?

From [http://askubuntu.com/questions/35629/are-ppas-safe-to-add-to-my-system-and-what-are-some-red-flags-to-watch-out/224640#224640](http://askubuntu.com/questions/35629/are-ppas-safe-to-add-to-my-system-and-what-are-some-red-flags-to-watch-out/224640#224640) :
> 
**How many users have used the PPA** - For example, I have a PPA from [http://winehq.org](http://winehq.org)  in my personal PPA. Would you trust ME with 10 users that confirm using  my PPA having 6 of them saying it sucks than to the one Scott Ritchie  offers as **ppa:ubuntu-wine/ppa** in the official winehq  website. It has thousands of users (including me) that use his PPA and  trust his work. This is work that has several years behind it.
I keep finding suggestions like that when googling, but I've never figured out how to check the amount of users?

---

### Post by ibjsb4 on 2012-12-03
> **ksatta1 said:**
> Hmm.. If the PPA provides lucid packages that doesn't neccessarily mean anything, it could've been uploaded yesterday?

Look at the link I gave you; its been around for years.

---

### Post by ksatta1 on 2012-12-03
> **ibjsb4 said:**
> Look at the link I gave you; its been around for years.

Well, that just means that something called "apt-fast" has been around for years (and it was actually a different PPA at first).

Apt-fast is fine, I've been using it for a long time. My question in any case is that if I find some PPA that I want to try, how can I see some info like download counts. I keep finding these suggestions to check "how many users are using the PPA", but I don't know how to find that info.

Like the other day I found a PPA to install AMD proprietary drivers on my older laptop (legacy display adapter). Once again I had no idea if anyone else had downloaded it.

If I saw something like:
- It's been around for some time
and It's been downloaded 1000 times

If the PPA is still in launchpad, it's most likely ok.

---

### Post by ibjsb4 on 2012-12-03
To me, it sounds like your asking a lot from a PPA.  One last thought that may make you a bit more confidant with PPA's is:

[http://manpages.ubuntu.com/manpages/natty/man1/ppa-purge.1.html](http://manpages.ubuntu.com/manpages/natty/man1/ppa-purge.1.html)

Its in the software center.

Good luck  :)

---

### Post by ksatta1 on 2012-12-03
Yup. I've actually used it :) Thank you for all the replies.

But anyway it looks like I haven't missed anything. I think what people mean by "check how many users use it" is reading some thread on a forum where people are commenting it or something.

And in the end I suppose malicious software is really rare on Linux, and if some is detected it's removed from launchpad. Sooner or later someone is bound to check the sources anyway. However adding download counts or something to launchpad might be a good idea, I think I actually found some old feature req. to make it visible to the publishers atleast. I figured since people are talking about checking user amounts it meant it's visible on launchpad.

Anyway the security aspect of PPAs is quite close to Google Play on Android, except that you can't know if anyone else has actually downloaded it or not.

---

