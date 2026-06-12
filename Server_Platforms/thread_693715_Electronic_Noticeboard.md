---
title: "Electronic Noticeboard"
date: 2008-02-11
forum: Server Platforms
---

### Post by RudolfMDLT on 2008-02-11
Hi there,

I think this is the right place to post this...

At the moment I have an apache server up and running and my website is running smoothly. I am the Rep for the electrical and biomedical students in my class, and constantly need to run around giving people updates on news, class locations ect... Usually I resort to a grouped sms list, but this costs money.


Now, I'm using a page on my URL that they can go to on their mobile phones. It's really small, loads fast and as far as I'm concerned less of a hassle.

I would like to expand it's uses. beyond this point I'm a complete noob and would appreciate some help to get on the right path. I'm not even sure what a system like this is called in reality, but I'm sure something of the sort must already be in place!

Is it possible for the server to download an email, save it as text and then for myself to upload that mail in raw text on the website. That is, email a gmail account, dedicated for this purpose, pop the mail from there, save it as text, and using some application or personal script, add it to a flat html file? All automated.

If yes, could you tell how me how? ;) Just kidding, though that would be appreciated! I would appreciate some pointers on what mail apps may work or whether there is already something similar to this and what it's called?

Thanks for any advice,

Rudolf

---

### Post by faulkes on 2008-02-11
Although I haven't done something like this in quite awhile, I would suggest looking at something like fetchmail and pipe through perl or sed to remove unwanted headers (so you get just the body text), write that to a file (with any html you want included).

If you wanted to automate it, you could run it as a cron job and have it scp'd automatically.

Faulkes

---

