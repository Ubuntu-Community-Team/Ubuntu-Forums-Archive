---
title: "forum accounts easy to steal ?"
date: 2013-08-05
forum: The Cafe
---

### Post by aze555666 on 2013-08-05
Hi,

I just created an Ubuntu One account in order to link it to my forum account and set a new password since the old one is now in the wild.
I created my One account using my email address and didn't need any confirmation (not even confirmation email). Then I just had to click "connect to forum" and keep all checkboxes (what information do I want to share with forum -> full name / nickname / email address). Since the One account shared the email address with the forum, the latter recognized me and my accounts were linked.
I am now logged on forums, without using my old password, without proving that I'm the owner of the email adress linked to my forum account.

Unless I have missed something, it sounds like a big security issue : I could create a One account using the email address of any member who did not come back yet, and I will own his forum account !

Regards,

aze555666

---

### Post by CharlesA on 2013-08-05
How would you know the email another member uses on the forum without having access to the database itself?

---

### Post by coffeecat on 2013-08-06
> **aze555666 said:**
> I created my One account using my email address and didn't need any confirmation (not even confirmation email).

Are you saying you didn't receive something like this?

> Hello

As a final step of the Ubuntu Single Sign On (SSO) account creation process, please validate the email address **<snip>**. Ubuntu SSO enables convenient access to a variety of Ubuntu-related services like Ubuntu One with the same username and password.

Here is your confirmation code:

    **<snip>**

Enter this code into the registration form, or click the following link to automatically confirm your account:

    **<snip>**


If you don't know what this is about, then someone has probably entered your email address by mistake. Sorry about that. You don't need to do anything further. Just delete this message.

Thank you,

The Ubuntu Single Sign On team

---

### Post by aze555666 on 2013-08-06
> **CharlesA said:**
> How would you know the email another member uses on the forum without having access to the database itself?
You could either use a random address hoping to hack a random forum account, or be able to link a forum username and an email address using other information sources (either search for the same username elsewhere on the internet and find sites/forums that my display email in profile, or just be the guy who got the DB from ubuntuforums a few days ago and have all emails but didn't decrypt passwords yet)

> **coffeecat said:**
> Are you saying you didn't receive something like this?
No, didn't get it. Double checked my webmail in case I would have mechanicallyclicked the link and trashed the email, but didn't find anything.

---

### Post by pqwoerituytrueiwoq on 2013-08-06
i did not get one of those either
@[URL="http://ubuntuforums.org/member.php?u=923868"][B][COLOR=#C61919][B]CharlesA
[/B][/COLOR][/B][/URL]I am pretty sure the guy/gal who hacked the forums in the 1st place would have this info, what about the admin accounts, could he/she steal any of those?

i had a ubuntu one account prior to the site getting hacked

---

### Post by CharlesA on 2013-08-06
> **aze555666 said:**
> You could either use a random address hoping to hack a random forum account, or be able to link a forum username and an email address using other information sources (either search for the same username elsewhere on the internet and find sites/forums that my display email in profile, or just be the guy who got the DB from ubuntuforums a few days ago and have all emails but didn't decrypt passwords yet)

What is the profit in doing that? If someone is in the process of registering random email address and links them to the forum, we would see a noticeable increase user registration and that would probably be a red flag that something is going on.

> **pqwoerituytrueiwoq said:**
> i did not get one of those either
@[URL="http://ubuntuforums.org/member.php?u=923868"][B][COLOR=#C61919][B]CharlesA
[/B][/COLOR][/B][/URL]I am pretty sure the guy/gal who hacked the forums in the 1st place would have this info, what about the admin accounts, could he/she steal any of those?

i had a ubuntu one account prior to the site getting hacked

Perhaps, but again, where is the profit? Besides I'm pretty sure all of the mods/admins have already linked their launchpad/UO account to their forum account, so a hijack like that isn't possible.

---

### Post by pqwoerituytrueiwoq on 2013-08-06
> **CharlesA said:**
> Perhaps, but again, where is the profit?better safe than sorry, don't want the forums to go down again

---

### Post by cariboo on 2013-08-07
> **aze555666 said:**
> 
Unless I have missed something, it sounds like a big security issue : I could create a One account using the email address of any member who did not come back yet, and I will own his forum account !

Regards,

aze555666

So you've got access to a member account that has no privileges how is that supposed be insecure? We have other security measures in place when it comes to the moderation team.

---

### Post by Irihapeti on 2013-08-07
> So you've got access to a member account that has no privileges how is that supposed be insecure? 

I think it's slightly missing the point. Supposing that I weren't a moderator and someone got hold of my account. They could post a load of nonsense, maybe not bad enough to get jailed, in my name. Given that the internet never forgets, I could be having to explain that to prospective employers for a long time. Or maybe never even getting the chance of explaining it. :(

However, I'm pretty sure I got a message like coffeecat describes when I changed my email address several months ago. If some of you *aren't* getting one, maybe it's a bug that needs to be reported.

---

### Post by Elfy on 2013-08-07
> **aze555666 said:**
> Hi,

I just created an Ubuntu One account in order to link it to my forum account and set a new password since the old one is now in the wild.
I created my One account using my email address and didn't need any confirmation (not even confirmation email). Then I just had to click "connect to forum" and keep all checkboxes (what information do I want to share with forum -> full name / nickname / email address). Since the One account shared the email address with the forum, the latter recognized me and my accounts were linked.
I am now logged on forums, without using my old password, without proving that I'm the owner of the email adress linked to my forum account.

Unless I have missed something, it sounds like a big security issue : I could create a One account using the email address of any member who did not come back yet, and I will own his forum account !

Regards,

aze555666

If you did not receive any sort of confirmation of the e-mail from login.ubuntu.com you should talk to them about it. 

I've received more than one of these mails from them regarding e-mail changes/additions to my u1 account.

> **Irihapeti said:**
> I think it's slightly missing the point. Supposing that I weren't a moderator and someone got hold of my account. They could post a load of nonsense, maybe not bad enough to get jailed, in my name. Given that the internet never forgets, I could be having to explain that to prospective employers for a long time. Or maybe never even getting the chance of explaining it. :(

However, I'm pretty sure I got a message like coffeecat describes when I changed my email address several months ago. If some of you *aren't* getting one, maybe it's a bug that needs to be reported.


Would you not contact admins at the forum saying that you think that the account's been hacked? 

We've got access to account information as well - including changes to various user editable fields.

At the end of the day if people think that there is an issue at login.ubuntu.com then it is _there_ that the question should be asked, not here - we have no control over SSO, nor do we have any control over having to use SSO.

---

### Post by Irihapeti on 2013-08-07
If I knew/suspected that the account had been hacked, then of course I'd contact the admins. I was only laying out a hypothetical scenario in which harm could be done without actually jeopardising everyone else's details. Someone out of range of internet coverage might not even know for several days that anything had happened.

Entirely agree that SSO questions don't belong here, and that was what I was trying to say in my final paragraph. Maybe not very successfully :(

---

### Post by coffeecat on 2013-08-07
The bottom line is that you would have to be able to create an Ubuntu One account without **email** validation in order to hijack a forum account. The validation email I posted earlier was from my personal Ubuntu One account made 2-3 years ago (edited to remove identifiable information). Yesterday, I created two new Ubuntu One accounts for administrative forum testing purposes using email addresses that I had not used in Ubuntu One before. In each case I received "finish your registration" emails as follows:

> Hello

Welcome to your new Ubuntu One account.

You can log in right away and start using your new account.

Please take a moment to confirm your email address with us by clicking on the
link below.

<link snipped>

Thank you,

The Ubuntu One team
[https://login.ubuntu.com/](https://login.ubuntu.com/)

If you don't know what this is about, then someone has probably entered your email address by mistake. Sorry about that.
If you wish to report this email being incorrectly used, please click the following link:

<link snipped>

You can also seek further assistance on:

[https://forms.canonical.com/sso-support/](https://forms.canonical.com/sso-support/)


Again, identifiable information snipped. Until I verified the two accounts, I could not use them - it's as simple as that.

The claims in this thread that people were able to create new Ubuntu One accounts without having to verify the email addresses are, frankly, stretching my credulity to breaking point.

However, if there is an intermittent bug allowing creation of Ubuntu One accounts without email validation, then this needs to be reported to the Ubuntu One admins as a matter of priority. But such reports need to be better documented than the anecdotal claims in this thread.

---

### Post by aze555666 on 2013-08-07
Hi,

I didn't get any confirmation email.
I know that a bug report would need a better documentation (tracking bugs is part of my job), but I have no clue on what happened, so unfortunately I can't give more details :(.
Also, I don't know where to report the Ubuntu One issue. Not being an Ubuntu user anymore (which is why I didn't have an Ubuntu One account), I just wanted to make you aware of the issue I found (which is always better than being silent as far as security is concerned) : I will not try to determine whether an Ubuntu place (U forums) is the right place to report an Ubuntu place (U One) issue or not.

Also, even if there was no issue with the confirmation email from U One, I'm not sure that the issue has nothing to do with forums : the forum let me in just because U One redirected me there using my email address, and linked my account. Could at least have checked my old password before linking accounts.

Regards,

aze555666

---

### Post by CharlesA on 2013-08-07
> **aze555666 said:**
> 
Also, even if there was no issue with the confirmation email from U One, I'm not sure that the issue has nothing to do with forums : the forum let me in just because U One redirected me there using my email address, and linked my account. Could at least have checked my old password before linking accounts.

Old passwords were randomized and it linked your accounts via email address. That is why we are using SSO - the forum no longer stores user passwords in the database and relys on UO to authentication.

---

### Post by matza55 on 2013-08-07
Sadly, i'm afraid of someone going to abuse my account on Ubuntu. But I only yet wondering, why WHY?

But also: there is good people who can fix it! I love them!

---

### Post by ventrical on 2013-08-07
As I had postulated on disourse forums that the attacker could have been someone  on the*inside* then it could be possible that the hacker may have created a sort of backdoor of sorts. With exploits such as these anything is possible.

 The other theory is that the attacker is always logged on waiting for a log-off of other members or a maintanance event where a port may be temporarily opened offering up an opportunity for remote access.

---

### Post by QIII on 2013-08-07
It seems a waste of time to continue to postulate fantastic scenarios when the actual events that have been explained to you are much more mundane.

---

### Post by ventrical on 2013-08-07
> **QIII said:**
> It seems a waste of time to continue to postulate fantastic scenarios when the actual events that have been explained to you are much more mundane.


mundane ?? Oh really ??

"At 16:58 UTC on 14 July 2013, the attacker was able to log in to a
moderator account owned by a member of the Ubuntu Community.

This moderator account had permissions to post announcements to the
Forums. Announcements in vBulletin, the Forums software, may be
allowed to contain unfiltered HTML and do so by default.

The attacker posted an announcement and then sent private messages to
three Forum administrators (also members of the Ubuntu community)
claiming that there was a server error on the announcement page and
asking the Forum administrators to take a look.

One of the Forum administrators quickly looked at the announcement
page, saw nothing wrong and replied to the private message from the
attacker saying so.  31 seconds after the Forum administrator looked
at the announcement page (and before the administrator even had time
to reply to the private message), the attacker logged in as that Forum
administrator.

Based on the above and conversations with the vBulletin support staff,
we believe the attacker added an XSS attack in the announcement they
posted which sent the cookies of any visitor to the page to the
attacker."



regards..

---

### Post by CharlesA on 2013-08-07
> **ventrical said:**
> As I had postulated on disourse forums that the attacker could have been someone  on the*inside* then it could be possible that the hacker may have created a sort of backdoor of sorts. With exploits such as these anything is possible.

 The other theory is that the attacker is always logged on waiting for a log-off of other members or a maintanance event where a port may be temporarily opened offering up an opportunity for remote access.

You do remember where the IS team said they have reinstalled both the servers and the forums software from scratch and vetted the database tables, right?

We don't need conspiracy theories here.

Closed for review.

---

### Post by CharlesA on 2013-08-07
Moved to cafe and reopened.

---

### Post by ventrical on 2013-08-07
> **CharlesA said:**
> You do remember where the IS team said they have reinstalled both the servers and the forums software from scratch and vetted the database tables, right?

We don't need conspiracy theories here.


And we can't rest on our laurels either. Can we ?

;)

---

### Post by cariboo on 2013-08-08
To expand on what CharlesA and QII have said, vBulletin was installed from scratch and all code and database tables were vetted by Canonical IS. While they were going through the process, they found a large number of undocumented hacks as well as several accounts that had more privileges than they should have that were again undocumented. Also while in the process they found a problem with the vBulletin software that was reported and fixed before the forum went live.

You can speculate all you want, but the blog post ventrical quoted has all the pertinent information. If you read it, you see what you are saying just isn't possible any more.

---

### Post by ventrical on 2013-08-08
Is Apache server software being used on the admin side?

Just curious.

thnxs

---

### Post by cariboo on 2013-08-08
The site does use apache, you can find the info for yourself at:

[http://news.netcraft.com/](http://news.netcraft.com/)

Then enter the url of the site you want to check in the search box in the upper left.

---

### Post by ventrical on 2013-08-08
> **cariboo907 said:**
> The site does use apache,...

Thank you ..

Why not 2.4 rather than 2.22.?

---

### Post by sandyd on 2013-08-08
> **ventrical said:**
> Thank you ..

Why not 2.4 rather than 2.22.?

The forum servers run Ubuntu. Newest is 2.2.22 in raring.
[http://packages.ubuntu.com/search?keywords=apache2&searchon=names&suite=raring&section=all](http://packages.ubuntu.com/search?keywords=apache2&searchon=names&suite=raring&section=all)

---

### Post by Elfy on 2013-08-08
IF there is a backdoor and IF there is someone hatching plans, then THEY are in IS and there is absolutely nothing we can do about it.

If you don't trust the way the forum is set up - please post in RC and we will disable your account.

This thread is now chasing it's tail.

Closed.

---

