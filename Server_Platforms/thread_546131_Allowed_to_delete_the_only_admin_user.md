---
title: "Allowed to delete the only admin user"
date: 2007-09-08
forum: Server Platforms
---

### Post by xdaiana on 2007-09-08
Hello all!
If this issue was discussed before I apologize.....
Today I encountered following problem: due to a (already known) skype issue, I deleted the user I normally use form the admin group. but the problem is that it is the only user with admin rights on this system. I already fixed the issue with recovery mode, but what i want to point out here is:

I would have definitely preferred to get a warning about deleting the only user with sudo rights!

As an additional info, I use Dapper.

And as an ex SuSE and RedHat user i wasn't familiar at all with the ubuntu way of handling root.

---

### Post by 5-HT on 2007-09-09
Definitely understandable. You can file that as a feature request if you'd like via launchpad. Though I personally don't like being asked 'are you sure' 'are you really sure' 'really?????': if one is deleting users one needs understand the repercussions before hand.
cheers,

---

### Post by xdaiana on 2007-09-09
well, I don't like this kind of asking either and I suppose most of us don't.

But if I'm about to do an action which blocks my complete access to root privileges via GUI I definitely should be warned about that.

Not having GUI login for root is (as far as i know) ubuntu-typical, the distros I used before allowed it, so I supposed the root user is still there and usable.

I didn't delete the user, I only removed it from a group. I didn't know I wouldn't be allowed to use the root passwd any more from this user because I haven't faced this situation before and it's not described in the help for users&groups either.

And what addionally is sort of unusual: when starting in recovery mode, I wasn't asked for ANY password...

As a statement: I don't want to complain here or search for excuses, I want just to prevent other ubuntu users to make the same mistake :-?

---

### Post by kerry_s on 2007-09-09
lets say you were to be asked for a password in recovery, what would you use? your user is no longer valid, root is disabled except for recovery and root has no password.

i just think you need to ask if your unsure of something, before you do it, especially if it requires root.

just what did you think "admin" means, if you have no admin, what did you expect to happen?

---

### Post by xdaiana on 2007-09-09
I'm sort of new to ubuntu, I'm used to the old RedHat and to SuSE. So I also expected to have a root user with a root password. The root passwd being the same as the first user - that's a thing that was very unusual to me.

But my actual user is NOT root, or is it?

---

### Post by koenn on 2007-09-09
Ubuntu's approach to root and sudo is different from other distro's. There's quite a good rationale for it, and it's documented : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Leaving recovery mode unprotected is usually considered less of a security issue, because it is only accessible for someone who has physical access to the computer (in which case there are plenty of other ways to get access - booting a live cd or stealing the hard disks to name just 2). Password-protecting recovery mode therefore only makes sense if it is a part of a policy, and is complemented by other measures re. who has physical access to this computer ? Are users allowed to reboot ? If users are not allowed to reboot, do i take measures to prevend "hard" reboots (power switch, unplug the power cord, ..) , how do I protect the grub boot menu, etc. 

You can password protect recovery mode by creating a password for root (simply "sudo passwd root" will do) but you should trade that off against its downsides or complement it with additional mesures : do you allow root to ssh ? to do gui logins ? ... With ubuntu's default "no root", this is not an issue, but with an enabled root, you have to configure it for every service. 

It's not uncommon to deny GUI logins,ssh login, etc to root, forcing users to login as a user and then su or sudo to become root. Ubuntu has just taken this 1s step further.

---

### Post by xdaiana on 2007-09-09
I admit that regarding the security question you're definitely right. Sincerely, I never thought this way....

But regarding the quasi non-existing (or let's say &#8221;only theoretically existing&#8221;) root user:

As far as I remember, I wasn't informed at all at the installation that the user I created will be so strongly bound to the root. And I was even more confused about not being asked for root passwd at all during the installation process. It's a whole different approach and we should, in my opinion, be at least made aware of when installing. It sure makes life easier for people swithing from other distros.

And last, but not least: thanx for the docu link, it was very helpful.

---

### Post by koenn on 2007-09-09
> **xdaiana said:**
> As far as I remember, I wasn't informed at all at the installation that the user I created will be so strongly bound to the root. And I was even more confused about not being asked for root passwd at all during the installation process. It's a whole different approach and we should, in my opinion, be at least made aware of when installing. It sure makes life easier for people swithing from other distros.
You have a point there. 
Apparently, the setup is simplified to its limits to cater for users without any linux experience (they don't know or care about root and all that ) but the result can be somewhat  confusing to people with some experience. It's probably assumed that users with linux experience are used to finding and reading documentation :)

---

### Post by xdaiana on 2007-09-09
Yes, I did read the corresponding documentation. But only after having this problem. I found a solution posted on the internet, applied it and I restored the functioning system.

But I don't read documentation for all &#8221;Next&#8221; buttons I press, I do this supposing that, if I make such a risky decisions, I should get a warning. 

Well, like in the &#8221;old&#8221; saying: &#8221;Every kick in the behind is a step forward&#8221; - I learned something about the ubuntu system and it was an interesting, even if not very pleasant, challenge.

---

