---
title: "Couldn't a time-based login prevent brute force attacks?"
date: 2008-12-12
forum: The Cafe
---

### Post by aysiu on 2008-12-12
I've often read that strong passwords are good. I understand that weak ones (dictionary phrases) are easy to crack.

Please keep in mind that I don't know that much about technical details of things. I am not a programmer. So in your explanations and corrections, talk to me as if I'm a moron.

How difficult would it be to make logins time-based?

In other words, for a remote login, making it so that after the first and second failed attempts to log in to a particular account, you'd have to wait 5 seconds to log in for that particular account, and then after the third failed attempt, you'd have to wait an extra 10 seconds and so on. If there were ten failed attempts coming from the same source, that source would no longer be able to log in for the next 24 hours, and even if that source tried to log in with a correct username and password, it would be denied.

Is this not implemented because it would be difficult to identify a source? Even so, forcing at least a 5-second delay would significantly increase the time it would take for an automated program to go through every single possible dictionary word.

I think I've seen time-based logins before (I forget in what context). Why aren't they more common? And why wouldn't they then make dictionary-word passwords more secure than they currently are?

---

### Post by DOS4dinner on 2008-12-12
At my highschool, if you put in the wrong password 5 times it blocks your account. I would assume most systems would have something like that.

---

### Post by thegreatbitbucket on 2008-12-12
I don't know how hard that would be to implement (I'm not a programmer myself). But, it surprises me that something like that isn't already implemented. It's an extremely good idea.

My friend's iPhone had a feature like that. If you locked the screen with a 4-digit PIN and then got the PIN incorrect around 3 times or so, it wouldn't let you unlock for about 5 minutes. Then if you got it incorrect again, it would be locked for 15 minutes. Incorrect after that, then it would be around 30 minutes, then an hour. Turning it off and on again didn't remove the penalty. It was pretty frustrating to my friend to not be able to use the phone for 15 minutes but it's a good security measure.

The thought that if you couldn't login for 24 hours, even with the correct username and password is also something I like because if someone guessed the correct password, they may not know that it would work.

I hope someone gets a chance to implement this, if it isn't already available yet.

---

### Post by bobbob1016 on 2008-12-12
Well, yes, it would work, but not if they boot a livecd.

Edit:  Kind of like how the club thing works for cars, so long as the guy trying to steal the car doesn't have a spare wheel to put on.

---

### Post by will1911a1 on 2008-12-12
> **bobbob1016 said:**
> Well, yes, it would work, but not if they boot a livecd.

Edit:  Kind of like how the club thing works for cars, so long as the guy trying to steal the car doesn't have a spare wheel to put on.


If they have physical access to the box the game is basically over anyway.

---

### Post by aysiu on 2008-12-12
If someone has the ability to boot a live CD, the password means nothing anyway, so I don't see how that's a relevant scenario to this discussion.

---

### Post by binbash on 2008-12-12
there are some scripts to do this but i prefer port knocking or private key file.Far more secure

---

### Post by Jammanuser on 2008-12-12
> **aysiu said:**
> If someone has the ability to boot a live CD, the password means nothing anyway, so I don't see how that's a relevant scenario to this discussion.

Hahaha! Good point! :D that cracked me up when i read that comment, and then ur reply... :guitar:

Cheers! :lolflag:

Jam Man

):P

---

### Post by happysmileman on 2008-12-12
Well all Linux systems seem to have a 1-2 second delay after incorrect password entry (including when using sudo) for this reason (AFAIK that's the reason anyway).

Anything more than a couple of seconds would become fairly annoying for people with long passwords or bad typing?

---

### Post by HermanAB on 2008-12-12
You can use iptables rate limiting on new connections to make brute force attacks infeasible:
[http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)

Cheers,

H.

---

### Post by Dr Small on 2008-12-12
Whether a properly implemented time based login prevention would work or not should not leave us with the excuse to use dictionary words as passwords.

---

### Post by aysiu on 2008-12-12
> **Dr Small said:**
> Whether a properly implemented time based login prevention would work or not should not leave us with the excuse to use dictionary words as passwords.
No, it shouldn't. But it also means that if you use a dictionary word, it'd be far less likely to be cracked than in a non-time-based scenario, which could probably have it cracked within a few minutes.

---

### Post by CholericKoala on 2008-12-12
> **aysiu said:**
> No, it shouldn't. But it also means that if you use a dictionary word, it'd be far less likely to be cracked than in a non-time-based scenario, which could probably have it cracked within a few minutes.

I like my dictionary word, even though its not really a word

---

### Post by Dr Small on 2008-12-12
> **aysiu said:**
> No, it shouldn't. But it also means that if you use a dictionary word, it'd be far less likely to be cracked than in a non-time-based scenario, which could probably have it cracked within a few minutes.
Just the same, I would still encourage better security practices, because this mechanism would not be implemented everywhere.

---

### Post by Frak on 2008-12-13
This would be taking it from Microsoft themselves:

Look at any Windows Server domain and check the login policies. You'll notice an option that allows login pauses/lockouts with a box for a time amount.

Before anybody flames me on this, remember Microsoft does retain much of the market and they didn't get that way placing blank cd's in cardboard/plastic boxes.

---

### Post by [h2o] on 2008-12-13
Consider what happens when someone, for "fun", attempts to log in to your computer from a place where you also try to login to your computer. His failed "attempts" could block your legal attempts out for a long long time if you take the approach you suggested.

---

### Post by pp. on 2008-12-13
There are numerous systems which enforce time based rules such as delays between attempted logins, permanently or temporarily locking an account or terminal after a given number of failed accounts and so on.

They provide some additional security for those accounts which have strong passwords. They help a tiny little bit when an account uses guessable passwords.

---

