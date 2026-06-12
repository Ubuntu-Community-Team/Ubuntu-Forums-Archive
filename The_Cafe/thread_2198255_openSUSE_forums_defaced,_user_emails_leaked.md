---
title: "openSUSE forums defaced, user emails leaked"
date: 2014-01-07
forum: The Cafe
---

### Post by RichardET on 2014-01-07
As reported by openSUSE on its site:

As [hackernews.com]("http://thehackernews.com/2014/01/openSUSE-Forum-Hacked-by-Pakistani-hacker.html#") noted, the [public openSUSE forums]("http://forums.opensuse.org")  have been compromised and defaced. A cracker managed to exploit a  vulnerability in the forum software which made it possible to upload  files and gave access to the forum database. [h=2]Passwords: Safe! Emails: Not so much :-/[/h] Credentials for your openSUSE login are not saved in our application databases as we use a single-sign-on system ([Access Manager from NetIQ]("https://www.netiq.com/products/access-manager/"))  for all our services. This is a completely separate system and it has  not been compromised by this crack. What the cracker reported as  compromised passwords where indeed random, automatically set strings  that are in no way connected to your real password.
 However, some user data is stored in the local database for  convenience, in the case of the forum the user email addresses. Those  the hackers had access too and we’re very sorry for this data leak!
 [h=2]And now?[/h] As the exploit is in the forum software we use and there are no known  fixes or workarounds we have decided to take the forums offline for  now, until we have found a solution. Stay tuned for updates [here]("http://news.opensuse.org"), on [twitter]("http://twitter.com/openSUSE"), [facebook]("http://www.facebook.com/group.php?gid=2256834487") or [g+]("https://plus.google.com/110312141834246266844?prsrc=3").

---

### Post by sammiev on 2014-01-07
Now I know why I'm getting 21 spam emails in 9 hrs. I kind of put 2 and 2 together after noticing the forums were off line.

---

### Post by Don_Stahl on 2014-01-07
:( 

OpenSUSE was my first positive experience with Linux. Too bad the forum got hacked. No software with a connection to a network is invulnerable, I guess.

---

### Post by RichardLinx on 2014-01-08
My e-mail address that I have tied to an openSUSE forums account wont let me login... Haven't used it in well over a year so it could have been caused by any number of things (potentially even the UF hack that happened a while back?). I'm getting the following message when I try to login:

> We've detected unusual activity. For your protection, we've disabled your account.

I pretty much just logged onto UF to see if accounts tied to that e-mail still work, and it seems they do... But I mean, I can't access the e-mail account so that's not really too helpful. At least I'm pretty sure it held nothing of any real importance, just a bunch of old blog and forum accounts, my UF account, launch pad account, bunch of linux forums... No big deal, but kind of annoying now that I know about it.

---

### Post by mastablasta on 2014-01-08
well that's not good. time to get ready for some spam then.

---

### Post by coffeecat on 2014-01-08
> **RichardLinx said:**
> I pretty much just logged onto UF to see if accounts tied to that e-mail still work, and it seems they do... But I mean, I can't access the e-mail account so that's not really too helpful. At least I'm pretty sure it held nothing of any real importance, just a bunch of old blog and forum accounts, my UF account, launch pad account, bunch of linux forums... No big deal, but kind of annoying now that I know about it.

The following is OT to this thread, but I'll post it anyway because it might be helpful to both yourself and others in your position with a possibly compromised email account registered to their forum account.

Bottom line - it won't affect your Ubuntuforums activity except for forum email notifications. And, as you have found, it doesn't affect your ability to log into UF from Ubuntu One SSO, but you might find it useful to change your Ubuntu One preferred email and your forum email. Just to remind everyone - once your Ubuntu One and ubuntuforums accounts are linked, you can change the email in either or both and they don't have to match. Email match between Ubuntu One and the forum is only necessary for the initial login association of the two accounts.

---

### Post by RichardLinx on 2014-01-08
> **coffeecat said:**
> The following is OT to this thread, but I'll post it anyway because it might be helpful to both yourself and others in your position with a possibly compromised email account registered to their forum account.

Bottom line - it won't affect your Ubuntuforums activity except for forum email notifications. And, as you have found, it doesn't affect your ability to log into UF from Ubuntu One SSO, but you might find it useful to change your Ubuntu One preferred email and your forum email. Just to remind everyone - once your Ubuntu One and ubuntuforums accounts are linked, you can change the email in either or both and they don't have to match. Email match between Ubuntu One and the forum is only necessary for the initial login association of the two accounts.

Thanks for the heads up. :)

---

### Post by Dragonbite on 2014-01-08
Well, this sucks.

I just cleared out my spam folder in preparation to see if there is an increase or not to what shows up there.

---

### Post by RichardET on 2014-01-08
Hello @dragonbite - I am also an openSUSE refugee - first as RichardET, now as BSDuser.  I can't decide which distribution I prefer - Ubuntu or openSUSE, so I use both as my mood strikes me, but I prefer the ease of adding software in Ubuntu over openSUSE, but I also like Yast, so that is a plus on the openSUSE side, thus can't decide.

---

### Post by sammiev on 2014-01-08
In the last 5 1/2 hrs I have only received 3 spam emails. A lot better than late yesterday.

---

### Post by oldos2er on 2014-01-08
I haven't logged in to the openSUSE forums for awhile, but they already had SSO in place. Also not sure which version of vbulletin they're using.

---

### Post by Dragonbite on 2014-01-08
> **sammiev said:**
> In the last 5 1/2 hrs I have only received 3 spam emails. A lot better than late yesterday.

I've gotten none yet (*knock on wood*)

---

### Post by sammiev on 2014-01-08
> **Dragonbite said:**
> I've gotten none yet (*knock on wood*)

In the last 3 1/2 hrs I got 7 new spam emails. :(

---

### Post by os2 on 2014-01-10
This forum was hacked only recently too.

---

