---
title: "Confining the guest account using AppArmor"
date: 2011-07-26
forum: Security
---

### Post by twipley on 2011-07-26
I think a generic how-to-confine-guests-accounts using AppArmor is well due.

This is a follow-up solution to [http://ubuntuforums.org/showthread.php?p=11082813](http://ubuntuforums.org/showthread.php?p=11082813)

The only (partial) walkthrough I have seen yet comes from no one other than the one and only bodhi.zazen:

> What you would do is make a link to /bin/bash , I call it "jailbash"

```
sudo ln /bin/bash /usr/local/jailbash
```

You then change the users log in shell from bash to jailbash

```
sudo chsh <user>
```

Then, bodhi.zazen tells us an AppArmor profile for jailbash should be set up. He gives us an example of such a profile, which, he notes, "may be more or less restrictive than you want; you will need to adapt it to your needs." [http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.local.bin.jailbash](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.local.bin.jailbash)

The question is, does that profile apply to standard users and still is up to date?

---

### Post by bodhi.zazen on 2011-07-26
> **twipley said:**
> The question is, does that profile apply to standard users and still is up to date?

The basic principles are up to date, you will still need to manually review the jailbash profile.

Apparmor is a nice tool, easier to learn the selinux, but the down side is that you must maintain your own profiles.

Personally I have migrated to Fedora as I find selinux is more mature.

Fedora has what is called the xguest , which is a guest account confined by selinux . 

selinux is harder to learn, but the selinux policies are activly maintained and there are very fine tools, graphical an otherwise, to help you learn and maintain your policies.

See : [http://www.linuxtopia.org/online_books/fedora_selinux_guides/fedora_11_selinux_user_guide/fedora_11_selinux_sect-Security-Enhanced_Linux-Confining_Users-xguest_Kiosk_Mode.html](http://www.linuxtopia.org/online_books/fedora_selinux_guides/fedora_11_selinux_user_guide/fedora_11_selinux_sect-Security-Enhanced_Linux-Confining_Users-xguest_Kiosk_Mode.html)

---

### Post by twipley on 2011-07-26
Yes, finger right on it, it is the maintenance cost that turns me down, for crying it out loud. Indeed, awesome for government profiles, but for the personal user, which is in-that-field quite non-knowledgeable, that approach is a little less viable.

In a few years from now on perhaps AppArmor will by default secure both Firefox and the guess account -- which would be awesome for the average end user.

---

### Post by bodhi.zazen on 2011-07-26
> **twipley said:**
> Yes, finger right on it, it is the maintenance cost that turns me down, for crying it out loud. Indeed, awesome for government profiles, but for the personal user, which is in-that-field quite non-knowledgeable, that approach is a little less viable.

In a few years from now on perhaps AppArmor will by default secure both Firefox and the guess account -- which would be awesome for the average end user.

Apparmor is a nice start, but, IMO, it needs a few things.

There is a profile for firefox already.

What apparmor needs are :

1. A profile for each network aware application, from firefox to the weather applets.

2. A set of graphical tools to manage profiles and logs.

I would caution you, selinux is much more mature, so there is lsess a need to write profiles. BUT it is not perfect either.

Personally I confine all my users, but, that means I have to write a few policies. Now I have been using selinux since the days before apparmor, so I am familiar with managing it.

And there is also a bit of a learning curve with selinux.

I think a better question is, what makes you think a "personal user" needs such things ?  At this time they do not.

---

### Post by twipley on 2011-07-26
> **bodhi.zazen said:**
> What AppArmor needs is a profile for each network aware application, from Firefox to the weather applets.
Indeed. However, why limit the scope of it to "network-aware" applications? You know, if I downloaded a PDF file exploiting a vulnerability in the default PDF-viewer application, the system could be damaged up to the root, is not it? But, would "everything" need to be isolated from the rest of the system, or would that be "overkill?"

> **bodhi.zazen said:**
> I think a better question is, what makes you think a "personal user" needs such things? At this time they do not.
Well. Suppose I do manage by banking over the Internet. I would therefore want to ensure at great length that the system I am on is not compromised. Imagine someone sitting on his chair far away receiving the keys inputted over here, or seeing at distance what is on-screen happening over here. Such things should not happen, but they are happening, from what I have read -- such unethical practices!

---

### Post by bodhi.zazen on 2011-07-26
> **twipley said:**
> Indeed. However, why limit the scope of it to "network-aware" applications? You know, if I downloaded a PDF file exploiting a vulnerability in the default PDF-viewer application, the system could be damaged up to the root, is not it? But, would "everything" need to be isolated from the rest of the system, or would that be "overkill?"

Well, you sort of need to start with the network aware applications.

If just opening a file cause root compromise, they your OS has serious problems.

If you are concerned about such things you really should be running Fedora and using the sandbox, but such things are highly improbably if you are running Linux, this is not windows.


> Well. Suppose I do manage by banking over the Internet. I would therefore want to ensure at great length that the system I am on is not compromised. Imagine someone sitting on his chair far away receiving the keys inputted over here, or seeing at distance what is on-screen happening over here. Such things should not happen, but they are happening, from what I have read -- such unethical practices!

Well, internet banking has (at least) 3 points of venerability - your box, "the internet" connection, and the server you are connecting to.

At this time there are no know spyware applications or key loggers that run on Linux the way they do on Windows and honestly I think you can relax on that issue.

Your biggest potential problem would be your browser, and as I said there is an apparmor profile for firefox. You should use https (ssl) and NoScript.

Not much you can do about "the internet" except use https.

Not much you can do about your financial institution's servers, they seem to keep using Windows and flash >_< 

Some day they will convert to a more secure OS and stop using javascript and flash, IMO there is no role for such things when it comes to financial transactions, certainly not at the expense of security.

---

### Post by twipley on 2011-07-26
> **bodhi.zazen said:**
> If just opening a file cause root compromise, they your OS has serious problems.
Vulnerability exploits in a PDF-viewer application would be something imaginable, would not it be?

> **bodhi.zazen said:**
> Not much you can do about your financial institution's servers, they seem to keep using Windows and flash >_< 
:facepalm:

---

### Post by bodhi.zazen on 2011-07-26
> **twipley said:**
> Vulnerability exploits in a PDF-viewer application would be something imaginable, would not it be?

All things are possible.


[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

But going from an from a vulnerability to an exploit to root access, that would take some work.

As I said earlier, this is part of the reason I use Fedora, my users are confined by selinux and a user_u

If you have this level of paranoia, I suggest you do the same, writing an apparmor profile for each and every application is going to be impractical for you, and then who would review such profiles ?

[http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/chap-Security-Enhanced_Linux-Confining_Users.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/chap-Security-Enhanced_Linux-Confining_Users.html)

You will need to tweak the policies a bit if you confine your users, not too bad.

You may also like the selinux sandbox and xguest.

[http://www.bress.net/blog/archives/195-Firefox-in-a-sandbox-with-Fedora.html](http://www.bress.net/blog/archives/195-Firefox-in-a-sandbox-with-Fedora.html)

No reason you can not sandbox evince as well =)

---

### Post by c.cobb on 2011-07-26
> **bodhi.zazen said:**
> Some day they will convert to a more secure OS and stop using javascript and flash, IMO there is no role for such things when it comes to financial transactions, certainly not at the expense of security.

Unfortunately, there's no financial incentive for them to change. As [KrebsOnSecurity]("http://krebsonsecurity.com/") reports, banks turn to the courts to make it increasingly difficult for customers to sue them for bad security practices. (Unlike personal accounts, commercial accounts are exempt from reimbursement for losses due to online fraud.) Plus, banks rely on third parties to provide the security which further insulates them from having to share their customer's pain. 

I've been building a custom remix of Ubuntu to use for eBanking that runs from a Live USB. Works great, and I plan on doing a writeup. I'd actually feel safe using this to access my bank from any PC -- in an Internet cafe, hotel lobby, or other unsafe location.

---

### Post by bodhi.zazen on 2011-07-27
FYI at our last LUG meeting we discussed apparmor, and out of the discussion I posted a blog on how to generate a profile for an application, using privoxy as an example.

See : [http://blog.bodhizazen.net/linux/apparmor-privoxy-profile/](http://blog.bodhizazen.net/linux/apparmor-privoxy-profile/)

Note: That blog assumes you are already familiar with the basics of apparmor.

Next month we are going to discuss selinux, so expect a blog about that next ;)

---

### Post by twipley on 2011-08-10
For what it is worth, I have submitted a brainstorm idea at [http://brainstorm.ubuntu.com/idea/28372/](http://brainstorm.ubuntu.com/idea/28372/)

One question, though: is the guest session already automatically sandboxed through AppArmor? I believe I have read something somewhere that seemed to imply that.

---

### Post by twipley on 2011-12-27
It seems the feature already is implemented. That is what the head of the security team told me -- that the guest session already is sandboxed through AppArmor.

...for anyone who still could have been wondering.

---

### Post by Dangertux on 2011-12-27
> **twipley said:**
> It seems the feature already is implemented. That is what the head of the security team told me -- that the guest session already is sandboxed through AppArmor.

...for anyone who still could have been wondering.

Yeah, I was discussing this a while ago with someone for anyone who is interested the profile is in /etc/apparmor.d/light-dm-session (or something similar not on a buntu box atm)

It is rather similar the the aforementioned jailbash, with some minor improvements (mostly in terms of flexibility).

---

