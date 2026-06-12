---
title: "Broke my Linux - keeps asking to authenticate when I have NO PASSWORD"
date: 2012-03-25
forum: Security
---

### Post by mustangzrule on 2012-03-25
Why?  How?  I can't even install a bootloader to create a new USB drive to reinstall.  

I tried to use recovery console and get errors also.  I never thought I would se the day when Windows was more stable.

Any assistance past this endless loop appreciated.

---

### Post by mustangzrule on 2012-03-25
Uh oh.  117 views and no responses.  Should I be worried?  No fix?  Wrong forum?

---

### Post by mustangzrule on 2012-03-25
Maybe more details needed:

I can't install any software because it wants me to authenticate.  No matter what I do at this screen it fails.  I set this machine up to not require a password on the only account.

Is there any way to undo this mess?  I would hate to go rifle through my closet for the old Windows XP CD.  Doubt I could even find a license key for it anyway.

Any links, suggestions, etc?  This is truly a dumb terminal right now.

---

### Post by Ms. Daisy on 2012-03-25
Please list the errors you get when you used the recovery console.  In general, the more information you give the better people can help.  When you say "I got errors" then all we can tell you is that you weren't successful.  

Look at this tutorial to see how to reset your password.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

You also need to understand how Ubuntu works.  I don't think you fully understand the concept of sudo, if not please read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Here's the crux: Your user account does not have root (or administrator) rights unless you use sudo. Whenever you make system changes in Ubuntu (like installing software), you have to enter your sudo password which gives the application permission to run.  If you didn't have sudo (and you were the root/administrator account) then anything could run at any time without your permission or knowledge.   That's bad practice and not supported on this forum.

You can set up your Ubuntu computer to not require a password upon boot-up & recovering from hibernate.  But you will always have a sudo password.

---

### Post by mustangzrule on 2012-03-25
FIXED!!!  Upon your suggestion to post the error in recovery console, I thought I would not be one of those who don't try to fix before crying for help.  I searched for the error message
[INDENT]Authentication Token Manipulation Error
Password Unchanged

[/INDENT]This little gem did it:

mount -o remount,rw /


Hope this thread helps the next one with this error.

---

