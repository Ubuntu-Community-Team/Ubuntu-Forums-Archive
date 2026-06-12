---
title: "Auto website refresh Cron."
date: 2010-02-15
forum: The Cafe
---

### Post by themarker0 on 2010-02-15
(*originally made for MyBBoard.net's forum, of where i saw this*)

Hey since i have my server alive, i want to start using crons. I have one for backing on, but the lack of files is a waste of a cron. So just wondering how do you have this auto refreshing? I assume it has something to do with the Lynx browser, but i have no idea in heaven, how you have that working.

Would anyone be kind enough to share this? I have done a little research, as so far nothing has come up. Also if it doesn't use lynx thats fine, i don't mind changing server side browsers, i have about 14gigs left .

---

### Post by Simon17 on 2010-02-15
Why do you want to automatically refresh the page?

I'm asking because depending on what you want to do with the page, it might be easier to use curl.

---

### Post by themarker0 on 2010-02-15
I don't mind how hard or how easy. I don't know if my server has CURL at the moment so :P If you go to [http://community.mybboard.net/forum-13.html](http://community.mybboard.net/forum-13.html) You will see Ryan Loos and Dennis Tsanng are always viewing. That is because they have their page set to auto logon.

I don't mind how you do it, i just want to make the same impression on a hosting site i am at (So spammers beware!)

---

### Post by lovinglinux on 2010-02-15
So you want to appear to be always logged on your own site, by logging in and refreshing the page in regular intervals. Is that right? 

So use [Reload Every](https://addons.mozilla.org/en-US/firefox/addon/115) extension for Firefox.

---

### Post by Simon17 on 2010-02-15
Yeah, if all you want to do is stay logged in, curl is the best way to go, in my opinion.

There are some pretty good curl tutorials around which should make things a lot easier for you.

---

### Post by themarker0 on 2010-02-15
> **lovinglinux said:**
> So you want to appear to be always logged on your own site, by logging in and refreshing the page in regular intervals. Is that right? 

So use [Reload Every]("https://addons.mozilla.org/en-US/firefox/addon/115") extension for Firefox.

I would like to do it server side. Is it possible to install firefox on a serer?

> **Simon17 said:**
> Yeah, if all you want to do is stay logged in, curl is the best way to go, in my opinion.

There are some pretty good curl tutorials around which should make things a lot easier for you.

I will start looking, thank you. :)

---

### Post by Simon17 on 2010-02-15
I just want to point out that you *can* install firefox on a server, but you wouldn't want to. I wouldn't even want to install it on a desktop. Even if you did, you'd have to install X and a bunch of libraries first.

Once you get something working, please give us an update on here and let us know how it went.

---

### Post by themarker0 on 2010-02-15
I first need to get DHCP working over, i have to find the file that handles it, then i will take an attempt at working with cURL. Should be fun :P

---

