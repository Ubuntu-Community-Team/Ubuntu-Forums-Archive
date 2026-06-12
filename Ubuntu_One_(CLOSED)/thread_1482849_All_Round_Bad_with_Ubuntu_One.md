---
title: "All Round Bad with Ubuntu One"
date: 2010-05-14
forum: Ubuntu One (CLOSED)
---

### Post by esoikie on 2010-05-14
Where to start.  I installed Ubuntu 10 and I click on my name and see this thing Ubuntu One.  Sure, let's check out this new feature.

So I sign up and instead of a confirmation email, I get an email saying that I was trying to sign in and maybe forgot my password.  So I go to the ubuntu one login screen and sign in.  The first thing it does is put me on a page where I can change my password.  So I did.  And it brought me back to the same page.  No option to get to dashboard, etc...

Somehow (not sure) I eventually stumbled on the dashboard (I think by clicking my name and clicking the manage account button).  So I get a glimpse of what it might be able to hold.  But I can't synchronize....

So I go to the website and look things up, it says to click on the elusive 'add a computer' button.  For the life of me I can't find this button anywhere either on the Ubuntu One Dashboard/website or on my computer.

Guess I can't do much with it yet.  Good thing it says Beta on it, or I would be sorely disappointed, but I think it needed a little more love before going live.

---

### Post by hashbrowns on 2010-05-14
I don't have my ubuntu machine with me right now (work computer) but perhaps you could try looking in your /home/username folder's hidden files to see if there is a preference stored for Ubuntu One? It's possible that if you can find any sort of folders or preference files there, deleting them will cause the program to revert back to its "default" behavior - in this case, hopefully sending to you to a "create new account" window instead of this malformed dashboard.

Sorry I can't be of more help, but speaking from previous experience, a lot of these strange glitches where you are automatically directed to a place you shouldn't be in yet is too to these preference files that get automatically put in your home folder's hidden files, like .purple is the one for messaging, I think.

---

### Post by joshuahoover on 2010-05-14
> **esoikie said:**
> Where to start.  I installed Ubuntu 10 and I click on my name and see this thing Ubuntu One.  Sure, let's check out this new feature.

Thank you for sharing your first use experience with Ubuntu One. I'm  sorry to hear it didn't work at all like it should. Below are some questions/comments conerning your experience.

> So I sign up and instead of a confirmation email, I get an email saying that I was trying to sign in and maybe forgot my password.  So I go to the ubuntu one login screen and sign in.  The first thing it does is put me on a page where I can change my password.  So I did.  And it brought me back to the same page.  No option to get to dashboard, etc...It sounds like you may have already had an Ubuntu Single Sign On (SSO) account already. Possibly a Launchpad account, as that uses the Ubuntu SSO service. I captured a video a little while back about how the process is supposed to work in Lucid. It's a silent movie of sorts, so it's super boring but does show how things are supposed to work today: [http://ubuntuone.com/p/qy/](http://ubuntuone.com/p/qy/) Obviously, your experience was different and I have a feeling it all got turned upside down by an existing Ubuntu SSO account. I'm going to try to reproduce the behavior you saw by attempting to sign up for a new account with an email address that is already associated with an Ubuntu SSO account. If you have any further insight into the steps you took from signing up to the time you got the email, it will help me see how we can improve this process. It's less than ideal and we have plans to improve it in the next release, Maverick.

> Somehow (not sure) I eventually stumbled on the dashboard (I think by clicking my name and clicking the manage account button).  So I get a glimpse of what it might be able to hold.  But I can't synchronize....

So I go to the website and look things up, it says to click on the elusive 'add a computer' button.  For the life of me I can't find this button anywhere either on the Ubuntu One Dashboard/website or on my computer.Since things seemed to have gotten tripped up with the "forgot password" email, it sounds like you were never automatically prompted to add your computer to your Ubuntu One account. To work around this for the time being, you can try to run the following from a terminal session (Applications->Accessories->Terminal):

```
u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```That should get the "add your computer" step to show up.

Again, thank you for the feedback and I'll see if I can reproduce the behavior you were seeing so that we can make sure we fix the issue or (at the very least) provide guidance on how to workaround that scenario.

Thank you,

Joshua

---

### Post by Pifilatakanemu on 2010-05-14
I don't want U1 to look bad, but it's obvious it's in beta stage.

If you need a reliable cloud storage service at this very moment, have a look a [Dropbox]("https://www.dropbox.com/referrals/NTIxNTQxNzg5"). 

I'm using it right now, giving U1 a try every once in a while, but right now Dropbox just pwnz ;)

It works alright and syncy your data on other platforms, too, if needed.

Sharing with common people (Win users) is although a feature I don't want to miss anymore. :D

---

### Post by duanedesign on 2010-05-15
There is a bug for some on Lucid that makes the Add A Computer button hard to find. The workaround is here:




[How do I add my computer? Where is the "Add Your Computer" button?]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?")
-
-

---

