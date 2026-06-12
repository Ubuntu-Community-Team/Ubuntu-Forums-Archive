---
title: "Never been able to get into my old account..."
date: 2014-01-25
forum: Resolution Centre
---

### Post by 3vi12 on 2014-01-25
Okay, where to start...

After the switch to single sign-on, I was never able to log in with my old account.  This probably has something to do with the fact that I already had an Ubuntu SSO ID, but I used a different e-mail address for it than I use for the Ubuntu forums (I use different e-mails for every site to simplify blocking and so that I can give people a heads-up when their user database has been sold to spammers).

Here's my old account:  [http://ubuntuforums.org/member.php?u=95459](http://ubuntuforums.org/member.php?u=95459)

I've tried, several times, to get it working by doing things like adding/changing the primary mail of my Ubuntu SSO account to the address I registered with here in the forums.  However, it never worked and I would just get frustrated after beating on it for a while and give up.

*[Note:  I've change the @'s in the paragraph below to \, because I really hate spam]*

When logging in with my 'real' Ubuntu SSO ID, the personal details page always shows that it's going to pass in fullname ubuntu\eternaldusk.com, username "kh1hv1-ubuntuone" (where the first part of that comes from, I do not know), email ubuntuforums\eternaldusk.com, on the personal details page.  I then receive the following error:

[INDENT][FONT=courier new]The following errors occurred during your registration:
[/FONT]
[FONT=courier new]That username is already in use or does not meet the administrator's standards. If you are kh1hv1-ubuntuone and you have forgotten your password, click [here]("http://ubuntuforums.org/login.php?do=lostpw").[/FONT][/INDENT]

I get the same results, but with different email addresses when I change the preferred e-mail address for the SSO.

Clicking 'here' ([http://ubuntuforums.org/login.php?do=lostpw](http://ubuntuforums.org/login.php?do=lostpw)) takes me back to the forum index!

To ad to my confusion, under the error message mentioned above is a 'Register' box, with my e-mail address filled in, and a 'Complete Registration' button that does nothing when I click it.

So... today I bit the bullet and created another Ubuntu SSO account (which I do not want) just so I could get in here to post this message.

If anyone could help me sort out this mess such that I can login with my old ID again and trash this new Ubuntu SSO account, I'd be most appreciative.

Thanks in advance,

---

### Post by howefield on 2014-01-25
Let's see if we can sort it out.

SSO tries to match the e-mail address it has with one on the forum. As the address you've used at SSO is NOT the same as the one we have on the forum - it didn't match therefore no access to your forum account.

What you need to do is set the preferred address at login.ubuntu.com to the same as the one in your original forum account, after you have done that I can disassociate this new account. You can change it to whatever you like after you have successfully logged into the forum with the proper account.

So once you have set up SSO to match the old e-mail address, let me know.

---

### Post by Iowan on 2014-01-25
The 3vi1 account is associated with a Launchpad ID. I will disassociate it, then you can try logging in again. (3vi registered with a lyondell account)

---

### Post by 3vi12 on 2014-01-25
That was the missing piece!  I apparently had not followed my system when I first registered here, so the e-mail was not what I thought.
 
I had even tried to send myself a test private message from this new account to see if I got a notification at an unexpected email (but received none, probably because of setting I had configured on my account here) 

Now that I've added that email to my ubuntu sso, I am able to log in with it.  I suppose this means I can change my preferred email back to the norm for my ubuntu sso ID and still get in here now that it's linked?

---

### Post by Iowan on 2014-01-25
After everything is working, we will need to disable this account. You won't be able to post in this thread from your original account.

---

