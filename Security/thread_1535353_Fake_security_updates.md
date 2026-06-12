---
title: "Fake security updates?"
date: 2010-07-20
forum: Security
---

### Post by Mduke on 2010-07-20
This is probably a very stupid question, but coming from windows and probably being the most ridiculously security paranoid person in the world, I've been curious ever since updating and researching rootkits for ubuntu. I've noticed a couple people saying you could get rootkits through being disguised as an important security update. Now, I was doubtful it was possible for this to happen, but it's been digging into me more and more whether or not this can actually happen through the official ubuntu update manager.


I know rootkits are rare in the first place, and I'm smart when it comes to installing things from the ubuntu repos, and after first hearing something like "a rootkit will disguise itself as an update you wouldn't think twice about and install" starts to get to me slowly over time.

So, people saying things like this, are they just trying to scare others or is there some actual truth in it?

---

### Post by wacky_sung on 2010-07-20
I think it is possible to get a rootkit out of the unofficial Ubuntu repository as you may not know what has been compiled within it.Each update of repository has a authentication key,unless the cracker break the key file otherwise it is almost impossible.

FYI this is not Window OS which update does not use any authentication key.

---

### Post by Mduke on 2010-07-20
Thanks for your reply

So it's pretty much impossible for anything fake to make its way into the update manager disguised as a legitimate update without a hacker somehow getting it authenticated (getting the ubuntu symbol next to the repo?) in which case it would be widespread to everyone who installed their updates without thoroughly checking each one over?

---

### Post by wacky_sung on 2010-07-20
That's why Linux is secure as compare to window.From what you mention,i know you are mainly from window user.Linux is totally difference compare with window in term of security.

---

### Post by rookcifer on 2010-07-20
The likelihood of getting a rootkit from the Ubuntu repos is extremely slim due to various security measures (such as package signing).  And if the repos ever did have a security breach (like Fedora did a couple years ago), the scope of damage done before it was fixed would be low.  Indeed, Ubuntu updates automatically check each package against the repo's signing key.  There is no way for an attacker to forge this signature unless he actually got a hold of the private key and pass phrase, which is extremely unlikely.

---

### Post by uRock on 2010-07-21
> **rookcifer said:**
> The likelihood of getting a rootkit from the Ubuntu repos is extremely slim due to various security measures (such as package signing).  And if the repos ever did have a security breach (like Fedora did a couple years ago), the scope of damage done before it was fixed would be low.  Indeed, Ubuntu updates automatically check each package against the repo's signing key.  There is no way for an attacker to forge this signature unless he actually got a hold of the private key and pass phrase, which is extremely unlikely.
This is why I love Ubuntu. Hakuna Matata!

---

### Post by welshywoo on 2011-01-13
I have considered this many times, of course it is possible. And if an attacker has a chance then quite likely. If your machine becomes exploited (perhaps through a clientside web attack, perhaps you run too many plugins in firefox??, or a vulnerable service, a trojan in a file) then any files could be replaced. What if your update manager was replaced with a fake? At which point it tricked you to downloading security updates for files that were infact more fake files. Im going to attempt a proof of concept of this soon.
It is wrong to assume that linux is more secure than any other os, infact it is wrong to assume your system is secure anyway. Whos to say which is more secure really?  At the end of the day it is down to the user of the pc and its environment.  Security experts are usually a step behind in regards to discovering new threats. Its like defending yourself from the common cold, these threats are designed to penetrate your defences and always find new ways to adapt.

---

### Post by rookcifer on 2011-01-13
> **welshywoo said:**
> I have considered this many times, of course it is possible. And if an attacker has a chance then quite likely. If your machine becomes exploited (perhaps through a clientside web attack, perhaps you run too many plugins in firefox??, or a vulnerable service, a trojan in a file) then any files could be replaced.

Care to explain how a rootkit is going to install itself through firefox?  And a trojan in a file is highly unlikely unless one goes around looking for odd .deb packages on the web.  The reason trojans are prevalent on Windows is precisely because there is no central package manager (and because Windows typically runs with full admin privileges which means any bug in the application code gives a malicious file root access).


 > What if your update manager was replaced with a fake?

How?

 > At which point it tricked you to downloading security updates for files that were infact more fake files. Im going to attempt a proof of concept of this soon.

I would be curious to see this.  I would also be curious to see if it takes user intervention (a la social engineering).

> It is wrong to assume that linux is more secure than any other os, infact it is wrong to assume your system is secure anyway.

I agree it's wrong to assume 100% security (which is impossible), but I also think it's wrong to focus on Windows flaws as affecting Linux.

---

### Post by bodhi.zazen on 2011-01-13
> **rookcifer said:**
> Care to explain how a rootkit is going to install itself through firefox?

I agree with what you are saying, but ...

Your example is not the greatest. Firefox has a relativly large number of potential vulnerabilities.

See :

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

And search for firefox or xulrunner. 30 or so hits for xulrunner (some for "older" versions mind you).

Now enters the problem with your example, these vulnerabilities in combination with a rootkit = bad news

From [http://www.ubuntu.com/usn/usn-1019-1](http://www.ubuntu.com/usn/usn-1019-1)

> An attacker could exploit these to crash the browser or possibly run arbitrary code as the user invoking the program.

So while these vulnerabilities have not to my knowledge been exploited, running arbitrary code means potentially downloading and running a rootkit, which by definition provide privilege escalation (from user -> root as the name implies).

So that is one way how, in theory, firefox can be be exploited to then gain root access.

Again, that I know, these vulnerabilities have not yet been exploited, and yes there is a big difference between a potential vulnerability and an exploit.

Keep in mind, one does not necessarily need root access to cause mayhem. Many users can run servers on non-privileged ports.

Another potential vulnerability is apt-url in concert with a ppa. I do not like apt-url because now we are one step closer to drive by installations of who knows what =) . Sure it may be "easy" for new users, but IMO at the potential sacrifice of security (I do not think you should be able to install a .deb from firefox).

So, IMO, firefox has a number of potential problems, and thus this is not the best potential example.

Firefox has more then it's fair share of potential exploits and potentially very broad access to system resources (between flash and multimedia and openoffice to open documents and a pdf reader and what not, the list goes on, take a look at the default apparmor profile for firefox, lots of access).

Personally I harden firefox, and in Ubuntu that means using apparmor for all network aware applications, in this case firefox.

Personally I think the apparmor profile for firefox should be enabled by default and restrict write access to files home only (and disallow access to sensitive directories such as .ssh and .gpg to name a few).

---

### Post by ianblaire on 2011-01-14
> **wacky_sung said:**
> 
FYI this is not Window OS which update does not use any authentication key.

This is not true. Windows update uses SSL, SHA1 and certificates
source: [http://download.microsoft.com/download/a/9/4/a94af289-a798-4143-a3f8-77004f7c2fd3/windows%20update%20explained.docx](http://download.microsoft.com/download/a/9/4/a94af289-a798-4143-a3f8-77004f7c2fd3/windows%20update%20explained.docx) (docx warning, but what did you expect on microsoft.com?)

---

### Post by rookcifer on 2011-01-15
> **bodhi.zazen said:**
> I agree with what you are saying, but ...

Your example is not the greatest. Firefox has a relativly large number of potential vulnerabilities.

Yeah but rootkits are only good if the attacker has exploited a *root* owned process or service.  Firefox does not run as root.  Of course, there is a possibility of some sort of escalation exploit, but those are rare.  I am not sure how many have been found with Firefox, but I suspect not too many.

> So while these vulnerabilities have not to my knowledge been exploited, running arbitrary code means potentially downloading and running a rootkit, which by definition provide privilege escalation (from user -> root as the name implies).

Well traditionally a rootkit has been a tool used by crackers to *maintain* access to a box they have *already* rooted.  That's why its called a rootkit.  The Windows security vendors have perverted the term to mean essentially the same thing as a trojan horse.  And even if Firefox executes malicious code, it does not follow that a rootkit will be installed since, as I said before, FF doesn't have root access.

> Again, that I know, these vulnerabilities have not yet been exploited, and yes there is a big difference between a potential vulnerability and an exploit.

Yes, I would be curious to see someone attempt this.  The more Linux distros are tested, the more secure they will be (much like crypto ciphers).  I am not declaring it an impossibility, but I don't see how his attack would work.  I will keep an open mind, but I suspect we will never see any such working attack (not without user intervention -- like downloading a .deb and purposely giving it root).

> Keep in mind, one does not necessarily need root access to cause mayhem. Many users can run servers on non-privileged ports.

Yeah but a rootkit will not work without root access.

> Another potential vulnerability is apt-url in concert with a ppa. I do not like apt-url because now we are one step closer to drive by installations of who knows what =) . Sure it may be "easy" for new users, but IMO at the potential sacrifice of security (I do not think you should be able to install a .deb from firefox).

I agree.  It's a bad idea to encourage users to install anything not in the repos.

> Personally I harden firefox, and in Ubuntu that means using apparmor for all network aware applications, in this case firefox.

I use Chromium.  It has its own sandbox plus I harden it with AppArmor, so it's sort of double sandboxed.

> Personally I think the apparmor profile for firefox should be enabled by default and restrict write access to files home only (and disallow access to sensitive directories such as .ssh and .gpg to name a few).

I think it should be enabled but deny write access to anything but ~/Downloads.

---

### Post by welshywoo on 2011-03-02
"Evilgrade is a modular framework that allows the user to take
advantage of poor upgrade implementations by injecting fake updates."

[URL="http://blog.infobytesec.com/2010/10/evilgrade-20-update-explotation.html"]http://blog.infobytesec.com/2010/10/evilgrade-20-update-explotation.html
[/URL]

---

### Post by rookcifer on 2011-03-02
> **welshywoo said:**
> "Evilgrade is a modular framework that allows the user to take
advantage of poor upgrade implementations by injecting fake updates."

[URL="http://blog.infobytesec.com/2010/10/evilgrade-20-update-explotation.html"]http://blog.infobytesec.com/2010/10/evilgrade-20-update-explotation.html
[/URL]

From your own documentation:

> Trust

A lot of application don’t verify the updates contents. They blindly trust without verification of the master update server.

If you're basing your attack on these two assumptions, then it wont work.  Ubuntu [does both]("https://help.ubuntu.com/community/SecureApt") of these things.  All repositories are verified via digital signatures and all packages within the repository itself are digitally signed.

There is always a possibility of rooting a box, deleting /etc/apt/trusted.gpg, replacing it with your own keyring and then changing /etc/apt/sources.list.  But if someone already has root, why go through that trouble?  If you have root, you aren't going to worry about fake updates because you already pwn the box!

Basically, I don't see how your attack will give someone who doesn't have root access a chance of getting it.  You aren't going to manipulate apt-cache without root.  

Care to tell me where I am wrong?

---

### Post by Rasa1111 on 2011-03-02
> **uRock said:**
> This is why I love Ubuntu. Hakuna Matata!

True that! lol

OP,
Just relax mate, enjoy your new OS.
That's just one great thing about Ubuntu..
The work has been done so that you *can* simply *enjoy it* and use it, without being paranoid about everything, and constantly compromised.

I used to be paranoid when i had windows to.
But I can honestly say Ive not felt paranoid once since switching to Ubuntu.
Security conscious, sure...
paranoid/worried.. not at all. 
):P

---

