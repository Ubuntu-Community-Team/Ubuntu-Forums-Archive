---
title: "How do I make this go away?"
date: 2024-02-01
forum: Ubuntu, Linux and OS Chat
---

### Post by NoDeity on 2024-02-01
How do I make it go away without spending money, that is. It's annoying. It's an ad. Can I make it go away or is it time to start auditioning other distros?

---

### Post by coffeecat on 2024-02-01
Point of information for anyone trying to help this member. They are complaining about the Ubuntu Pro prompts in the Software Updater. I have already told them (via pm) that Ubuntu Pro is free for personal use when I removed an earlier post from public view because of its tone, but it seems they are intent on ignoring that fact.

I'll move this to Ubuntu Linux & OS Chat, and wish luck to anyone replying.

---

### Post by Rubi1200 on 2024-02-01
@NoDeity

I believe Ubuntu Pro is not only free but also optional. You do not need to sign up for it.

Maybe there is someone else who can tell you how to turn off the prompts. I do not use vanilla Ubuntu so am unable to assist.

---

### Post by NoDeity on 2024-02-01
There definitely ought to be a way to simply turn off the prompts.

---

### Post by ajgreeny on 2024-02-01
Use something other than software-centre, eg terminal commands, Synaptic, etc.

You will still see U-Pro mentioned but it won't be a separate dialogue, just a few additional words that you can ignore.
I have never used the software-centre so have no real idea what you are seeing or whether that dialogue box requires action from the user. Synaptic or terminal certainly does not require you to do anything.

---

### Post by grahammechanical on 2024-02-01
In my opinion if Canonical did not publicize the availability of Ubuntu Pro then people would complain that Canonical was being secretive and only interested in earning money from commercial organisations.

Ubuntu Pro is definitely a benefit to commercial organisations. I have no problem with Canonical earning some revenue by providing this service. I am certainly glad that Canonical has made this benefit available to ordinary users like myself.

Regards

---

### Post by VMC on 2024-02-01
I have Ubuntu Pro enabled, and I don't see that message. What release are you using and how are you updating? Have you tried another method of updating; perhaps using the terminal.

---

### Post by martinr on 2024-02-07
You hit [bug]("https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/2015420") and [bug]("https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/2052546"), that were recently identified.

Disabling the messages is very hard and requires Python code changes in the file "/usr/lib/update-notifier/apt_check.py" ([see here]("https://github.com/canonical/ubuntu-pro-client/issues/2458")), but those will be undone at each update that package receives.

In the mean time the only pragmatic way to make the messages disappear, is to give into a [(free) ESM / Pro subscription]("https://ubuntu.com/pro/dashboard") and wait until the bugs get fixed. Then it should be more ease to un-cofigure the messages you see.

---

