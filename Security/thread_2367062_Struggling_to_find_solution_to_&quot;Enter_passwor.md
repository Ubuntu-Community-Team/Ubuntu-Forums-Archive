---
title: "Struggling to find solution to &quot;Enter password for keyring&quot; for Nautilus"
date: 2017-07-25
forum: Security
---

### Post by Paddy Landau on 2017-07-25
Here is what used to happen when I wanted to FTP via Nautilus.

[LIST]
[*]Open Nautilus.
[*]Select a bookmark to connect to another computer via FTP.
[*]The very first time, and only the first time, it asked for the FTP password. I typed the password and selected "Remember forever" (see screenshot).
[ATTACH=CONFIG]276132[/ATTACH]
[*]Nautilus connects.
[/LIST]
However, this has changed. If I remember correctly, the change happened after I updated my account password (which I did via Users and Groups, i.e. [FONT=lucida console]users-admin[/FONT]).

This is what happens now:

[LIST]
[*]Open Nautilus.
[*]Select a bookmark to connect to another computer via FTP.
[*]The computer pops a message saying, "Enter password for keyring 'Default keyring' to unlock" (see screenshot).
[ATTACH=CONFIG]276133[/ATTACH]
[*]Enter my account password. This is remembered until I next log out.
[*]Nautilus asks me for my FTP password (yet again).
[*]Enter the password and ask it to remember forever, which sadly it doesn't.
[/LIST]
Despite extensive searching, I cannot find an answer to my problem. The solutions either are out of date or don't apply.

Can you tell me how to let Nautilus access the default keyring again without having to ask every time, so that it can read the FTP password, please?

---

### Post by #&amp;thj^% on 2017-07-25
Paddy Landau have you tried installing seahorse?
[https://www.lifewire.com/guide-to-seahorse-tool-2196541](https://www.lifewire.com/guide-to-seahorse-tool-2196541)
It has made my life so much simpler with regards to passwords.

---

### Post by Paddy Landau on 2017-07-25
> **1fallen said:**
> have you tried installing seahorse?
I did indeed install seahorse after reading one of the solutions, but I couldn't figure out how to make it work for this purpose.

I notice that the FTP key is under the Default Keyring, but for whatever reason, Nautilus doesn't seem to have access to this keyring until I enter my account password.

I wonder — could it be anything to do with the fact that the default file manager for Lubuntu is PCManFM and not Nautilus?

---

### Post by #&amp;thj^% on 2017-07-25
Hmmm? It shouldn't, but wouldn't hurt to try first with  PCManFM and FTP. (Sorry my knowledge with  PCManFM is very low)
Sometimes I have found that deleting all items in the menu in seahorse has helped also.

---

### Post by Paddy Landau on 2017-07-25
> **1fallen said:**
> … try first with  PCManFM and FTP. … Sometimes I have found that deleting all items in the menu in seahorse has helped also.
I've tried both, but, alas, it still happens. The password was re-added to the Default Ring when I reconnected with "Remember forever".

I've realised that if the Default Keyring is unlocked prior to calling Nautilus, it doesn't ask for the FTP password, so at least I now know how to avoid typing that as well each time.

It's as though there is an automatic unlocking of the keyring for Nautilus, until the account password is changed (as I say, if I remember correctly). I might be misremembering when the problem started, though, but it definitely used to work.

---

### Post by #&amp;thj^% on 2017-07-25
Sadly I can now confirm your same problem.
I created a 16.04 Lubuntu install with nautilus as default FM and report the same as you have seen.
I'm not  seeing this on other Platforms (Non-Debian) though.:(
If I find a solution I will report here.
Kind Regards

---

### Post by Paddy Landau on 2017-07-26
Thanks for that. Now I know why it used to work and now it doesn't &#8212; it was that I had to reinstall Lubuntu, whereas I used to have lubuntu-desktop installed over Ubuntu.

I created a brand new "vanilla" installation of Lubuntu, and using the built-in file manager (PCManFM), the problem recurred.
I created a brand new "vanilla" installation of Ubuntu, and using the built-in file manager (Nautilus), the problem did not occur.

Thus, there is a bug whereby Lubuntu doesn't unlock the keyring for the user.

I'll raise a bug report and post back here once done.

---

### Post by #&amp;thj^% on 2017-07-26
Nice thanks for confirming.
I thought it might be PCManFM not unlocking the keyring for the user though.
I'll be curious as to what is causing this though.:confused:
Thanks Paddy Landau

---

### Post by Habitual on 2017-07-26
Auto-Login used to make Chrome + keys play dead.

Just sayin'

---

### Post by Paddy Landau on 2017-07-26
> **1fallen said:**
> I thought it might be PCManFM not unlocking the keyring for the user though.
No, it seems to be at a much lower level, specifically for Lubuntu.

I have raised a [bug report for this]("https://bugs.launchpad.net/ubuntu/+source/gnupg/+bug/1706701"). Please add your vote (click the green writing at the top left). Thanks for your involvement.

---

### Post by #&amp;thj^% on 2017-07-26
I'm still having problems with my account Paddy Logging in to LP.
Working on a solution seems to be null here.:(
And I'm not going to jump through hoops here to help them. (Sorry very frustrated with this, it has been months now with no resolve)

---

### Post by Paddy Landau on 2017-07-26
> **1fallen said:**
> I'm still having problems with my account Paddy Logging in to LP.
That's bizarre — it uses the *same* login as does this forum! You should be able to enter the same login details when logging into [Launchpad]("https://bugs.launchpad.net/") as you do for Ubuntu Forums. What happens when you try?

---

### Post by #&amp;thj^% on 2017-07-26
You would think that for sure.
> Oops!

Sorry, something just went wrong in Launchpad.

We&#8217;ve recorded what happened, and we&#8217;ll fix it as soon as possible. Apologies for the inconvenience.

(Error ID: OOPS-e3ccb93eaf8b8a4c2eb1414d7376f271) 
There ya go.

---

