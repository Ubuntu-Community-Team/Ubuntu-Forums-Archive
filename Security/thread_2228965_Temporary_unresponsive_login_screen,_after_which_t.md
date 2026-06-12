---
title: "Temporary unresponsive login screen, after which two new accounts are discovered"
date: 2014-06-10
forum: Security
---

### Post by HairlessMonkey on 2014-06-10
Hello,

I am running Ubuntu 14.04 LTS and today saw a bit of a weird thing happen.
I left my computer to get a coffee, and when I got back the desktop had locked and was showing the login-screen. 
All good right? (Edit, the coffee machine is basically in plain sight of my computer, no-one was even close to it.)

Now, when I started typing, nothing is being entered in the password box like it normally does.
The mouse worked perfectly. There was a prompt in the password box the blinked like it normally does.
I went and asked a colleague with more Ubuntu experience but he didn't have a clue. 
After trying a few times more with him watching, and in frustration hammering randomly on the keyboard I turned my head away from the screen for a few seconds.
When I turned back, I am logged in and the text editor that is showing is showing lots (perhaps all, I couldn't tell) of the keystrokes I made while doing retries and the above random hammering.

I then though, oh well, that was a first "lag" of the ubuntu gui I had experienced and continued to work until I shut down the computer and went home.
Now when restart the computer I see two new accounts that I don't recognize on login screen. Previously there were only my account and a "Guest" account.
Now there are two more, "test", and "temporary".

This is beginning to feel suspicious and since I am using this computer to access sensitive information I am wondering if anyone has any tips about what can have caused this.

A sidenote, I practically always do the upgrades immediately when Ubuntu prompts for them. I did one of those in the morning today a couple of hours before the strange login-event happened.

I would be glad for any information.
/Thomas

---

### Post by bapoumba on 2014-06-10
*Thread moved to **Security Discussions**.*
Some people here will be able to answer the possible security breach.

In the mean time, you can have a look at the recent upgrades in /var/log/apt/history.log or term.log. Please see what got upgraded/installed since you booted the machine that day or the few days before. Using any third party repositories or ppa ? If so, which ones ?

---

### Post by Chayak on 2014-06-10
How are you connected to the internet?
Do you have remote desktop enabled?
Do you have an SSH server installed?
Are you using a weak password?

---

### Post by HairlessMonkey on 2014-06-11
Please ignore/delete this question.
It can be filed under stupidity (those accounts were not new accounts, yes I had created them and forgot about them but looking at .bash_history on them I remembered.)
The only strange thing left was the laggy login but that is in itself not anything I will pursue further.

/Thomas

---

