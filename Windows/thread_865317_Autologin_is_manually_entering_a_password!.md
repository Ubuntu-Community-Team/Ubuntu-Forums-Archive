---
title: "Autologin is manually entering a password?!"
date: 2008-07-20
forum: Windows
---

### Post by Mr. Picklesworth on 2008-07-20
I don't use my Win Vista partition much, so I turned on auto login. (Involved a funny little command to get to the GUI for it: netplwiz).

A while ago, I also changed my account password to something less long-winded. When I restarted into Vista just recently, something happened that I found terrifying in a few different ways:
It tried to log me in, but instead popped up an error message that the entered password was incorrect.

Okay, obviously I need to enter my new password; the autologin is not caught up yet. Logged in manually, went back to netplwiz and told it a second time to log me in automatically, entering and confirming my password in a dialog. Wait, WHAT?!
This suggests to me that Windows is now storing my password in a reversible way, then punching in that stored password to log me in 'automatically'. I find that very concerning. I prefer having my passwords nicely encrypted, and have always assumed autologin to be a sort of exception in the authentication system which does not actually expose such data. (Like the passwordless login module for PAM).

Windows' security rant aside, should I be concerned about this? Is there, err, an excuse for this design that I can laugh at?
Actually, more importantly, are user account passwords *ever* properly encrypted in Windows Vista? I know in XP there were all sorts of tools that could quickly reverse the encrypted user account passwords, but I've gone on the assumption to this point that Vista has seen some good improvement for that end of things...

---

### Post by Battie on 2008-07-22
IF netplwiz is using reversible encryption (and I don't know for sure yet, but it seems likely), then yes, you might as well be storing them in plain text:

[http://technet2.microsoft.com/windowsserver/en/library/eeff044c-d4a8-4699-a4b8-c5e563118c931033.mspx?mfr=true](http://technet2.microsoft.com/windowsserver/en/library/eeff044c-d4a8-4699-a4b8-c5e563118c931033.mspx?mfr=true)

Don't know about Vista's encryption methods though, but now I'm insterested...

---

