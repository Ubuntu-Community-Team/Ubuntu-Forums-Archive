---
title: "Problems with 13.04"
date: 2013-04-10
forum: Ubuntu Development Version
---

### Post by bigal1932flying on 2013-04-10
Last month when I went to update 12.10 I received a message saying that I could Upgrade to 13.04 so I went ahead and did the Upgrade.
I now find that I have a couple of problems:
1. Firefox is painfully slow. So slow that I prefer to use W7.
2. Thunderbird is also SLOW and keeps asking me for my ISP Password.

Is there a solution to these problems? I have ADSL2+ so the Internet should not be a problem. THANKS!

---

### Post by papibe on 2013-04-10
Thread moved to **Ubuntu +1 (Raring Ringtail)**.

---

### Post by Frogs Hair on 2013-04-11
The update manager normally doesn't offer upgrades to unreleased versions unless software and updates is set to look for them.  I'm not suggesting it isn't possible though. Upgrading should not affect saved passwords in Thunderbird . What is an ISP password and is it different than a mail password ?   

Just In case:   [https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

---

### Post by dino99 on 2013-04-11
Thats kind of issue often met on system doing only dist-upgrade, due to old borked settings left behind. At least doing a fresh install for each LTS is a good idea, as too many changes are done with every release to take care of all possible race/conflict/....

---

### Post by bigal1932flying on 2013-04-11
Just after Posting this I installed the available Updates, then  I tried Chrome Browser and found it to be much faster.Firefox is still painfully slow though. I also checked my Emails this morning and although it was still slow it did not ask for my Password.

---

### Post by jerrylamos on 2013-04-12
> **Frogs Hair said:**
> The update manager normally doesn't offer upgrades to unreleased versions unless software and updates is set to look for them.   [https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)The Update Manager default is to notify for a new release.  Since I usually always have U+1 partition(s) I turn that default off.  I also turn off the default Check for Updates Daily.  I don't like Update Manager crashing in on what I'm doing.  Many times in the past Update Manager was quite willing to install a partial upgrade which screwed me so I had to re-install.  I update frequently when I want to.

---

### Post by 3rdalbum on 2013-04-12
> **bigal1932flying said:**
> Last month when I went to update 12.10 I received a message saying that I could Upgrade to 13.04 so I went ahead and did the Upgrade.
I now find that I have a couple of problems:
1. Firefox is painfully slow. So slow that I prefer to use W7.
2. Thunderbird is also SLOW and keeps asking me for my ISP Password.

Is there a solution to these problems? I have ADSL2+ so the Internet should not be a problem. THANKS!

gksudo "update-manager -d" is not for ordinary updates, it should only be used if you want to upgrade to the development version of Ubuntu.

I don't know about your Firefox being slow, sorry.

As for Thunderbird, it is asking for your password because it's getting no reply or an invalid reply from the mail server (usually at your ISP). Thunderbird's default setting is to guess what method of authentication your ISP uses. Sometimes it gets it wrong and you have to specify it manually in the Thunderbird settings; try a few different authentication types and see what works.

Sometimes, your ISP will do upgrades on the mail server that will cause Thunderbird to be confused about what authentication type is correct. Maybe your ISP has changed authentication type completely, and only checked that Outlook Express gets it right. If you've just done the upgrade to 13.04, it's even possible that your ISP's mail server is down for maintenance; your exact problem used to happen to a friend of mine, whenever their ISP's mail servers crashed. Thunderbird can't tell the difference between "bad authentication" and "No authentication because your ISP is having problems", so it assumes you've got the password wrong and asks for the password again. Evolution does the same, and so does Network Manager when you're using wifi.

---

### Post by mcellius on 2013-04-12
As for Thunderbird, I was recently advising a friend who was installing Ubuntu 12.04.  When he tried to use either Thunderbird or Evolution, his password wouldn't work.  I figured he was doing something wrong.

But then I reinstalled Raring on my computer, and found that I was having the same problem.  I was using gmail (as my friend was, also), and everything I tried failed - and yet, Thunderbird was working just fine with the same account in Ubuntu on other computers.  I made sure all settings were the same, and still no luck.

I logged in to gmail through the webpage (using Firefox) and that worked just fine.  And so then I got the idea that since I was already logged-in through the webpage, maybe if I opened Thunderbird again and tried to set it up while I still had the web-based gmail open, gmail would somehow get the login information from the webpage and allow me to set up Thunderbird.  It worked!  After that, I was able to close Firefox and still use Thunderbird, and it has worked ever since.

---

### Post by cariboo on 2013-04-12
When you tried setting up Thunderbird to receive mail from gmail, did you use IMAP?

---

### Post by mcellius on 2013-04-12
I used IMAP, which was the same as how I had set it up on my other computer.  In earlier installs, there were never any problems at all, just this one - which I suspect is due to some change either with Thunderbird or gmail, not with Ubuntu.  (This seems especially true, since my friend was having trouble accessing his account from Precise, where I never had problems; my problem with accessing my gmail account only happened in Raring, and even then only with a new install; it worked fine in earlier Raring installs.)

---

### Post by bigal1932flying on 2013-04-13
I have found Chrome works well, really quick and easy to use. As I said earlier Thunderbird has stopped asking for my Password, so I can put up with the SLOW start.
THANKS for the help. I consider my problem to be solved.

---

### Post by mcellius on 2013-04-13
I installed Raring today from the latest ISO, and Thunderbird worked just fine.  When I opened it to set up my account, it found it and logged me in just as it should.  So I don't know if the problem was with Thunderbird or with something else, but it's all good now.

---

