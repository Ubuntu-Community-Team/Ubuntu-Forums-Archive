---
title: "Spambot / virus in MSN messenger / pidgin / evolution"
date: 2011-12-21
forum: Security
---

### Post by tyrkov on 2011-12-21
Hi all,

I'm using pidgin, on Ubuntu 11.04 (natty) to logon to my MSN messenger account.
I recently noticed that messages were sent automatically to people
on my contact list. In particular when someone went online, there was apparently
a message of the type "hi there" or "whats up :)" sent to them. Then the "bot" or whatever
is the cause of this, would go on starting a "conversation" with the unsuspecting contact..
Also, many people told me that my profile picture had changed to an image of  *ahem* pornographic content..

I tried one or two things to fix this..
First off, I changed my MSN password, which was admittedly weak.
That seemed to fix the hacked profile picture issue..
However that didn't resolve the automatic messages issue.
I tried to uninstall pidgin, reinstall -- that didn't work either.
I logged in to MSN using evolution, which also didn't fix anything. That however allowed me
to see the content of the sent messages, which were invisible in pidgin.

HELP !!

---

### Post by OpSecShellshock on 2011-12-21
I think what's happened is not on your local machine at all, but is actually the result of the account itself being compromised. That would explain why the chat logs don't show up in Pidgin but do show up in Evolution: Evolution is pulling the data from the servers to your computer, but the chat conversations themselves are not originating from your computer. If the password you changed to when you discovered this and reset it was also not strong, it may have just been cracked again. Next time you log into the MSN account, check the settings to see if messages are being forwarded to any other accounts. You may also want to disable the function that allows you to receive emails in your desktop client before changing the password in case they are being similarly intercepted by another client somewhere else.

---

### Post by tyrkov on 2011-12-23
Hi,

I checked the settings with regard to forwarding from/to other accounts. It looks like
forwarding from my yahoo mail account to the MSN account was active by default, as
originally I had used that same yahoo account to create the MSN account.
As I didn't find a way to disable forwarding from yahoo to MSN, I decided to change the
yahoo mail password, which was also weak. I did and ... up till now, I didn't notice any new spam.....
so I guess the problem was the hacked yahoo account.

Thanks !

---

