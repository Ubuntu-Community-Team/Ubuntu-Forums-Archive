---
title: "Help determining correct order of operations for account changes"
date: 2019-03-04
forum: Resolution Centre
---

### Post by fr33z0n3r on 2019-03-04
**This post is not a request to change my account right now.**

So I have SSO and I'm working fine here for years. 

I would like to change my forum username, AND ALSO want to change my SSO username.  I know you don't manage the SSO account, but they say that changing that username will break access into sites.

1.  Can you confirm that if I change my SSO username, that change will break my forum access here?

2. Is there anyway to retain access to my current forum account AFTER I change my SSO username? (If access breaks I will not be able to post here)  Please describe how I can communicate with someone to regain access to my forum account.


Thanks!

---

### Post by coffeecat on 2019-03-04
> **fr33z0n3r said:**
> they say that changing that username will break access into sites.

Who says?

> **fr33z0n3r said:**
> 1.  Can you confirm that if I change my SSO username, that change will break my forum access here?

No I can't confirm that. It won't break forum access.

> **fr33z0n3r said:**
> 2. Is there anyway to retain access to my current forum account AFTER I change my SSO username? (If access breaks I will not be able to post here)  Please describe how I can communicate with someone to regain access to my forum account.

Change your username on Ubuntu One. Change your email on Ubuntu One or on the forum. None of those will interfere with your forum access. Only a forum admin (or in theory Canonical IS) can unlink your forum account from your Ubuntu One account.

---

### Post by fr33z0n3r on 2019-03-04
My bad.  I also have a Launchpad account and was told I have to change the username there.  This is what would break access elsewhere.

---

### Post by coffeecat on 2019-03-04
No problem. However, the Ubuntu One people do occasionally make changes without thinking to tell us. :) In the unlikely event of them (not us!) breaking your access to your forum account, or if you have any other problem with your account and can't log in, send an email to the Forum Council mailing list and we'll look into it - the address is on this page: [https://wiki.ubuntu.com/ForumCouncil](https://wiki.ubuntu.com/ForumCouncil)

---

### Post by fr33z0n3r on 2019-03-04
Thanks.  This is the warning when you go to rename your account on Launchpad.  This is what made me think this will break all access.

[IMG]https://i.imgur.com/CGGpzGJ.png[/IMG]

---

### Post by coffeecat on 2019-03-04
Well, that's interesting. The link from the forum is to Ubuntu One, not to launchpad. 

I just tried with a dummy Ubuntu One account I use for forum testing purposes. Attempting to Change the Full name and Username gave me this message:

> Because you have a Launchpad account, you need to change your username from Launchpad.

I was not aware that changes to the launchpad name would change your Ubuntu One openID. I don't think we were ever told that and the openID is critical for the link to the forum account. So, please discount what I said before. I'll ask one or more of the other admins to have a look and comment.

---

### Post by fr33z0n3r on 2019-03-04
thanks for looking into it.

---

### Post by fr33z0n3r on 2019-03-08
Any news on this?

---

### Post by coffeecat on 2019-03-08
Hi. Sorry to keep you waiting.

I think the other forum admins are as baffled by this as much as I am. The only thing I have discovered is that if you go to [https://login.ubuntu.com/](https://login.ubuntu.com/) while logged into Ubuntu One, scroll to the bottom of the page and click on the "Support" link you are taken to this [FAQ](https://help.ubuntu.com/community/SSO/FAQs) page. Which, worryingly, was last edited nearly 7 years ago. That's before SSO login was imposed on us. "Can I Change my Username?" takes you [here](https://help.ubuntu.com/community/SSO/FAQs/Change_LP_Username).

None of which is of much help really.

I'll take this up with the other admins again. Short of raising a support ticket with Canonical (which is a convoluted bureaucratic process) I don't know how to contact an Ubuntu One admin directly for them to confirm that the openID does indeed change if the Launchpad username changes. It is important that we know this definitely one way or the other.

In the meantime, assuming that the openID does change (which would break the link to the forum **and** make your account inaccessible until a forum admin intervenes), we do have an option which needs a little forward planning, and which would go something like this:

[list=1][*]You change your Launchpad username, the openID changes and you temporarily lose access to the fr33z0n3r forum account.
[*]You then email the Forum Council at the email address shown under contact in [this page](https://wiki.ubuntu.com/ForumCouncil), telling us that you have lost access to your forum account. You would need to email us from the address registered to the fr33z0n3r account, or quote it, so that we know it is you.
[*]I or one of the other admins would then remove the openID reference from your fr33z0n3r profile.
[*]This would allow you to relink your Ubuntu One account with the forum fr33z0n3r account simply by logging in from Ubuntu One, **so long as the emails in the two accounts match**.[/list]

Let us know if you wish to proceed with that, or if you wish to defer renaming your launchpad account until we have confirmed what they already appear to be telling us. 

Again, it doesn't add much useful information, but I have rendered the URL in the Launchpad warning you posted into a hyperlink: [https://help.launchpad.net/YourAccount/OpenID#rename-account](https://help.launchpad.net/YourAccount/OpenID#rename-account)

Sorry to have misled you earlier in the thread. In our defence, I have to say that, as far as I am aware, the forum admins were never forewarned about this matter, and I don't remember it coming up before. As you can see, it is important for us to have known this so that we can able to help members effectively with their forum accounts.

---

### Post by QIII on 2019-03-08
Some Admins are more baffled than others.  Then again, I find myself easily baffled quite often.

I think the idea of making the change and then contacting us via the mailing list would be a quick work around.  That doesn't, however, address the issues we will have to work out with Ubuntu One -- which you shouldn't need to worry about.

---

