---
title: "Account deactivation request: JackOdanaka"
date: 2013-01-24
forum: Resolution Centre
---

### Post by Jack Odanaka on 2013-01-24
Please delete/disable/deactivate JackOdanaka [1] (**not** this account, Jack Odanaka [2]).

Yesterday, I tried to log in to this account (Jack Odanaka, with a space) after not using it for ~6 months, but I seemed to have the wrong password, and I couldn’t reset it by email because the email address I had associated to this account no longer exists (it was part of a domain hosting package that I allowed to expire because I thought I wasn’t using it — I didn’t use email much at the time, and remembered it too late).

So I registered as JackOdanaka (no space), intending to request that this account’s associated email address be changed to my current one. Then I logged out (I forget why), and found that I could not log back in — my password for JackOdanaka was also being rejected. I decided that my passwords were being corrupted somehow as they were stored in the database, perhaps relatedly to the login issue [3], and there was nothing I could do about it.

Today I decided to try again, and reset my password for JackOdanaka. In so doing, I found that my corruption hypothesis is, in a way, correct — my passwords were being silently truncated to fifty characters. (I suspected from prior experience with other websites that the length of my passwords could be problematic, so I tried first setting my password to a puny 32-character one, then, after that worked, to a 64-character one, at which point I realized that the new password box didn’t look like it had twice as many bullets as the current password box, and counted the former’s bullets, finding fifty.)

Armed with this knowledge, I successfully logged in to this account by truncating what I thought was its password to fifty characters.

Why are passwords silently truncated? If there is some software limitation constraining password length, would it not be best to note this near the fields for setting and changing passwords, and reject overlong passwords?

[1] <[http://UbuntuForums.org/member.php?u=1780108](http://UbuntuForums.org/member.php?u=1780108)>
[2] <[http://UbuntuForums.org/member.php?u=1711735](http://UbuntuForums.org/member.php?u=1711735)>
[3] <[http://UbuntuForums.org/showthread.php?t=2091969](http://UbuntuForums.org/showthread.php?t=2091969)>

---

### Post by Elfy on 2013-01-25
Disabled the JackOdanka account. 

Password limit is set by vBulletin.

---

