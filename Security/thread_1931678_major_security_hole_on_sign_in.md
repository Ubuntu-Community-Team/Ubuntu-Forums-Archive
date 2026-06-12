---
title: "major security hole on sign in"
date: 2012-02-25
forum: Security
---

### Post by flyfishingphil on 2012-02-25
Looked around but didn't find this and was wondering if anybody else is seeing the same thing. Using 11.10 that is up to date and doing a password sign in whenever I fire it up. 

Have had several times lately where I have been able to fire it up, open up my email side and even get into 1 or 2 of them before the password security box pops up calling for the password.

Did a presentation before a group today and was into the presentation when it suddenly did that again. I had entered it to get started then, maybe 5 minutes later, it pops up demanding it again. Not the best screen to flash up in front of a room of people looking at info on fly fishing.

Anybody else seeing this or have suggestions on how to correct it?

---

### Post by Krytarik on 2012-02-26
Two things:

[LIST]
[*]Disable auto-login.
[/LIST]

[LIST]
[*]Don't confuse the keyring password to access your WiFi key with your login password.
[/LIST]
Regards.

---

### Post by flyfishingphil on 2012-02-26
Auto login is already disabled. Not the WiFi key ring that pops up.

Start the laptop, it jumps right into the start up page. Click on email, or net browser, of a file I'm working on. Object opens and begin working. All of a sudden the entry password box jumps up and, if you X it out you're back to the start point when you first turned it on. Fill in the password and you continue doing whatever you were allowwed to do before it popped up.

---

### Post by mcduck on 2012-02-26
> **flyfishingphil said:**
> Auto login is already disabled. Not the WiFi key ring that pops up.

Start the laptop, it jumps right into the start up page. Click on email, or net browser, of a file I'm working on. Object opens and begin working. All of a sudden the entry password box jumps up and, if you X it out you're back to the start point when you first turned it on. Fill in the password and you continue doing whatever you were allowwed to do before it popped up.

Are you perhaps now talking about the *browser's* security password, since there is no popup for login password, you enter that at the login screen.

And are you actually shutting down the computer, or hibernating/suspending it? (There is no way how you could end right into your web browser's startup page if you have actually shut down the computer, and automatic login is disabled)

Could you give us a screenshot if you aren't exactly sure about which password dialog it is?

---

### Post by Gremlinzzz on 2012-02-26
You know for sure its your Ubuntu password,you don't use same password for everything right.its  like your trying to install some thing and its asking for your password. try 
sudo apt-get update 
sudo apt-get upgrade
:popcorn:

---

### Post by Gremlinzzz on 2012-02-26
Do you clean your computer?
try Bleachbit its in the repositories
Could someone be trying to get your fly fishing secrets and installed a root kit? 
install chkrootkit same in repositories:popcorn:

Never use same password for everything.

---

### Post by uRock on 2012-02-26
> **flyfishingphil said:**
> Start the laptop, it jumps right into the start up page. 
This negates that.
> Auto login is already disabled.

Moved to *Security Discussions*.

---

### Post by OpSecShellshock on 2012-02-26
I believe email clients also store saved passwords in the keyring. If you haven't saved the password of your email client (assuming you use something like Evolution or Thunderbird rather than accessing email through the web browser) then the login prompt should be expected every time your mail client attempts to access the email server. Seems to me that a mail server that didn't require authentication would be more of a problem.

---

### Post by Dangertux on 2012-02-26
This actually happens... I've seen this before in current versions of Ubuntu 11.10 64 bit on faster machines.

I've only seen it happening when coming back from suspend or hibernation. What happens is you will get your desktop for a brief moment before being dumped at the unity login screen. On the system I've seen it on it was too fast to get into anything new but whatever was left up after the suspend is clearly visible, maybe on some hardware the window of opportunity might last longer. Perhaps there is a race condition in lightdm? 

Hope this helps.

---

### Post by flyfishingphil on 2012-02-26
mcduck - it's the login in password box after both full shutdown and coming out of suspended. Bad part is it's not all the time, just every now and then. Maybe leave this one open and if/when it happens again I'll post the screen.

gremlinzz - Any effort to get in just about had to come with the latest upgrade to 11.10. Did that maybe 3 weeks ago after doing a total format and installation. Unless somebody has figured out how to get into it on a secured WiFi in-home system.

I'll check out Bleachbits and chrootkit, and I have four full pages of passwords for all of the places and things I need them for. Mostly randoms that I write down as I enter them.

OpSec Shellshock - No, different password for email access thru Thunderbird to my web site email slot. I've made it to the email, and even opened a couple before the system startup login password was demanded.

A little confusing when that happens. First couple of times I thought maybe I had done it without realizing I had entered the startup login password but started paying attention and noted the operation happening before logging in.

Will see if it does it again and try to save the page so we can look at where I was when it finally asked for login.

---

### Post by mcduck on 2012-02-27
> **flyfishingphil said:**
> mcduck - it's the login in password box after both full shutdown and coming out of suspended. Bad part is it's not all the time, just every now and then. Maybe leave this one open and if/when it happens again I'll post the screen.
The thing is those two are completely different password dialogs, and don't even look anything like each other...

...but yeah, a screenshot should definitely clear things up. :)

---

### Post by flyfishingphil on 2012-02-27
OK, to make sure it is all clear. I have my laptop set up with password only access when starting it up. Usually it will pop up a box asking for the password before you can get in to anything on the computer. This is the same one on start up from shut down and start up from suspended.

Did a full shutdown for a few hours and started it back up a few minutes ago.

Showed usual desktop screen and allowed me to open Firefox, clikc on the link to FB and actually get in to FB before the password pop up box jumped up and wouldn't let me go any further. 

Tried to save the screen, so I could post it here, but all that was saved was the FB page, not the pop up security password box.

I'll try it again later and write down everything that it says in the pop up box, or maybe even try to take a photo of the screen to post, and pass on that info.

---

### Post by cariboo on 2012-02-27
If you can do this on a regular basis, I'd suggest you create a security bug report. I'd suggest you do a better job of explaining the problem, as full shutdown and suspend. are not the same thing, when it comes to talking to developers.

---

### Post by flyfishingphil on 2012-02-28
OK, let's try this description and see if it's something in the settings or a security but that needs to be reported.

1. When starting up from full shutdown the computer goes to a lit screen for a few, the screen goes blank for a few then it opens to my usual desktop. At this time I can get into just about anything I want without entering any form of passwrod. After a couple of minutes a window pops up that says:

  [I]Unlock Login Keyring
      Enter password to unlock your login keyring
       The login keyring did not get unlocked when you logged in to your computer[/I]
         PASSWORD:

If I choose the enter the password the box disappears. If I don't enter the password there doesn't appear to be any problem and I can access everything in the computer.

2. When restarting the computer from the suspended state there is a box that appears on the screen that only asks for PASSWORD. No other access is allowed until the password is properly entered in the box provided.

Question:

Is there a setting that I need to do so the computer cannot be accessed by anyone that starts it from the full shutdown state, or is this a bug that needs to be reported?

It would be nice to have it set up so that if someone else starts the computer they cannot get into all of the files, etc, without the password.

Thanks for the patience with the low level knowledge user.

---

### Post by cariboo on 2012-02-28
> **flyfishingphil said:**
> OK, let's try this description and see if it's something in the settings or a security but that needs to be reported.

1. When starting up from full shutdown the computer goes to a lit screen for a few, the screen goes blank for a few then it opens to my usual desktop. At this time I can get into just about anything I want without entering any form of passwrod. After a couple of minutes a window pops up that says:

  [I]Unlock Login Keyring
      Enter password to unlock your login keyring
       The login keyring did not get unlocked when you logged in to your computer[/I]
         PASSWORD:

If I choose the enter the password the box disappears. If I don't enter the password there doesn't appear to be any problem and I can access everything in the computer.

2. When restarting the computer from the suspended state there is a box that appears on the screen that only asks for PASSWORD. No other access is allowed until the password is properly entered in the box provided.

Question:

Is there a setting that I need to do so the computer cannot be accessed by anyone that starts it from the full shutdown state, or is this a bug that needs to be reported?

It would be nice to have it set up so that if someone else starts the computer they cannot get into all of the files, etc, without the password.

Thanks for the patience with the low level knowledge user.

To answer your question, disable auto-login, what you are seeing is normal when you have auto-login enabled. Go to System Settings->User Accounts, and disable auto-login. When you restart the system, you will now be asked to enter a password before proceeding to the desktop. If you use the same password as your keyring password, you won't be asked for it to connect to the internet.

---

### Post by flyfishingphil on 2012-02-28
Merci Beaucoop cariboo907!!!

Surprising how you can overlook something that simple when you're trying to figure something out. 

It would seem, since it started right after one of the updates, that it may have been a change that happened with the update. IO never set it that way and it started happening a week or so ago.

Your solution worked and I'll park that in the corner of my dusty, empty, brain area for future reference.

Solved!

---

