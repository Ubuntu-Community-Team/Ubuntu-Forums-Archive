---
title: "New upgrade script"
date: 2007-05-18
forum: Ubuntu Christian Edition
---

### Post by kiwidipstick on 2007-05-18
Hi mhancoc7,
Just wanted to say thank you for the new upgrade script to fix a few faults.
It worked fine for me and now automatix works fine too.
Blessings to thee, James.

---

### Post by mhancoc7 on 2007-05-18
> **kiwidipstick said:**
> Hi mhancoc7,
Just wanted to say thank you for the new upgrade script to fix a few faults.
It worked fine for me and now automatix works fine too.
Blessings to thee, James.

Thanks for letting me know. I am really glad things are working for you.

Are you having any trouble with the web content filtering?

Thanks, Jereme

---

### Post by kiwidipstick on 2007-05-19
Yes, I still cannot download mp3 sermons with Dansguardian enabled.
I have tried to put a 'disregard' symbol (#) in front of mp3, but it still will not do it when Dansguardian is enabled.
So, I have to admit, that I tend to leave it disabled all the time.
Blessings, James.

---

### Post by mhancoc7 on 2007-05-19
> **kiwidipstick said:**
> Yes, I still cannot download mp3 sermons with Dansguardian enabled.
I have tried to put a 'disregard' symbol (#) in front of mp3, but it still will not do it when Dansguardian is enabled.
So, I have to admit, that I tend to leave it disabled all the time.
Blessings, James.

Where are you downloading them from?  I would like to test it.

Jereme

---

### Post by kiwidipstick on 2007-05-19
Jereme, here is the site: [http://www.jamesknox.com/](http://www.jamesknox.com/)
Thanks for your interest, James.

---

### Post by mhancoc7 on 2007-05-20
> **kiwidipstick said:**
> Yes, I still cannot download mp3 sermons with Dansguardian enabled.
I have tried to put a 'disregard' symbol (#) in front of mp3, but it still will not do it when Dansguardian is enabled.
So, I have to admit, that I tend to leave it disabled all the time.
Blessings, James.

> **kiwidipstick said:**
> Jereme, here is the site: [http://www.jamesknox.com/](http://www.jamesknox.com/)
Thanks for your interest, James.

Ok, heres how to get it to work! :)

1. Enable Dansguardian
2. "Comment Out" (#) .mpg in the Blocked File Extension configuration file.
3. "Comment Out" (#) audio/mpeg in the Blocked MIME Types configuration file.
4. Save & Exit
5. Restart browser

Now you can download mp3s!!

Let me know if you have any trouble. It worked like a charm for me.

God Bless, Jereme

---

### Post by kiwidipstick on 2007-05-20
> **mhancoc7 said:**
> Ok, heres how to get it to work! :)

1. Enable Dansguardian
2. "Comment Out" (#) .mpg in the Blocked File Extension configuration file.
3. "Comment Out" (#) audio/mpeg in the Blocked MIME Types configuration file.
4. Save & Exit
5. Restart browser

Now you can download mp3s!!

Let me know if you have any trouble. It worked like a charm for me.

God Bless, Jereme

Okay, did that. Now I get this response: 'The folder contents could not be displayed. error accessing 'file:///home/ubuntu/Desktop':file not found. 
Hmmm, what now Jereme?
Blessings, James.

---

### Post by mhancoc7 on 2007-05-20
> **kiwidipstick said:**
> Okay, did that. Now I get this response: 'The folder contents could not be displayed. error accessing 'file:///home/ubuntu/Desktop':file not found. 
Hmmm, what now Jereme?
Blessings, James.


When are you getting that error message?

Jereme

---

### Post by kiwidipstick on 2007-05-21
> **mhancoc7 said:**
> When are you getting that error message?

Jereme

When I right click on 'save as'.
Blessings, James.

---

### Post by mhancoc7 on 2007-05-21
> **kiwidipstick said:**
> When I right click on 'save as'.
Blessings, James.

Sounds like it is trying to save it to a location that does not exist. Try changing the location where it will be saved.

Jereme

---

### Post by mysticrider92 on 2007-05-21
That error means it is trying to save to /home/ubuntu/Desktop, as Jereme said. Unless your username is ubuntu, that needs to be changed.

---

### Post by kiwidipstick on 2007-05-21
> **mhancoc7 said:**
> Sounds like it is trying to save it to a location that does not exist. Try changing the location where it will be saved.

Jereme

Yes it does, doesn't it. However, I decided to try and download anyway, despite the error message...and it worked! So goodness knows why the error response appears, I will just ignore it.
Thanks and blessings, Jereme, James.

---

### Post by ds-polleke on 2007-05-22
i was allready on feisty (7.04) -with wireless working- ... when i decided to "convert" to CE. .that chrashed my system..

after a clean "???" CE install i could not download and isntall updates because the packages could not be verified.. This script was to fix that error but  it uninstalled all i installed before (!!!)

and it chrashes (again)  downloading: Translation-nl

and wireless does not work correctly. i have to punch in my wep key every time! (thats no prob. for me but for my wife it is)



Blasted! i can start all over again (3rd time)

---

### Post by mhancoc7 on 2007-05-22
> **ds-polleke said:**
> i was allready on feisty (7.04) -with wireless working- ... when i decided to "convert" to CE. .that chrashed my system..

after a clean "???" CE install i could not download and isntall updates because the packages could not be verified.. This script was to fix that error but  it uninstalled all i installed before (!!!)

and it chrashes (again)  downloading: Translation-nl

and wireless does not work correctly. i have to punch in my wep key every time! (thats no prob. for me but for my wife it is)



Blasted! i can start all over again (3rd time)

I am sorry for your trouble. I am not sure why you are having so much trouble with it. The latest script should not be causing those issues. Also, if you did a clean Ubuntu CE install you definitely should not have those issues.

Keep me updated on your progress.

Thanks, Jereme

---

