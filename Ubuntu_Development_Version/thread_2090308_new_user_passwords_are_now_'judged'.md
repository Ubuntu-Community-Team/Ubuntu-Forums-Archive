---
title: "new user passwords are now 'judged'"
date: 2012-12-01
forum: Ubuntu Development Version
---

### Post by mc4man on 2012-12-01
Ubuntu itself doesn't yet care what the 1st/install user password is, 1 char is allowed.
In the past add users would need to use a min. of 6 chars, now it's at least 7 but not just any 7, has to meet some test (consecutive #'s or horizontal letters on keyboard seem to fail.

Don't really consider a bug, (other than criteria seem weird) but if anyone knows what source controls this would like to know.

(being a poor 2 finger typer typically setup up add users with a simple - 
123456 or 234567

---

### Post by buzzmandt on 2012-12-01
not happy about that myself
no one else uses my computers, why do i need to 'fort knox' them?

---

### Post by cariboo on 2012-12-01
Having a user name and password that is hard to guess, makes it harder for the bad guys to crack your system.

---

### Post by bird1500 on 2012-12-01
> **buzzmandt said:**
> not happy about that myself
no one else uses my computers, why do i need to 'fort knox' them?
Same here.
I dislike systems that think they know better what password I need.
If it was about serious security then Ubuntu should force me to use **encrypted filesystems**, otherwise the "bad guy" can access anything anyway if he has access to my pc.

I'll login as root and change my password to a simple one anyway. Ubuntu can't dictate me what I need.

---

### Post by mc4man on 2012-12-01
> **cariboo907 said:**
> Having a user name and password that is hard to guess, makes it harder for the bad guys to crack your system.
Even though I've had no issue using just 1 the above is certainly with merit.
Whether some patterns should be enforced rather than suggested, I don't know, was somebody's good idea somewhere

Though I would think screen 1's pass (unacceptable) would be as hard as screen 2's (strong

---

### Post by VinDSL on 2012-12-01
Best Password Checker I've seen is (gulp)...

[INDENT][https://www.microsoft.com/en-gb/security/pc-security/password-checker.aspx](https://www.microsoft.com/en-gb/security/pc-security/password-checker.aspx)[/INDENT]

Been using it for years.

Running your "not good enough" password against the MS checker gives a "Best Strength" rating.

Personally, I'd say it IS a bug...  ;)

---

### Post by mc4man on 2012-12-02
As it turns out "not good enough" doesn't mean 'can't use'
Just need 9 chars now (123456789 for my occasional test users

---

### Post by MacUntu on 2012-12-02
Why set a password at all if you use a weak one?

> **bird1500 said:**
> I'll login as root and change my password to a simple one anyway. Ubuntu can't dictate me what I need.
You can log in as root, so they don't.

---

### Post by ventrical on 2012-12-02
I have always used 9 letter passwords so this is news to me. (I'll have to try it out) :)

  I wonder if it has to do with secret current development :)

 btw ...  I had done an 'encrypted' install a while back during the beginning of raring and I was allowed to get away with using only 6 characters but  the requirment was that you had to use numbers mixed with letters.

---

### Post by bouncingwilf on 2012-12-02
Well my philosophy is to use a really strong password (15 Chars+) and then to set autologin. If anyone does then get to my machine via the "backdoor" - i.e. non-physical access, then they are hopefully going to have a job of elevating privileges to root! That way I only need my password for sudo. Having said this, I think I would still object to being forced to work this way - It's my machine and I'll do what I like!

Bouncingwilf

---

### Post by grahammechanical on 2012-12-02
> It's my machine and I'll do what I like!

True. But is it your operating system? You did accept the End User Licence when you installed, did you not? Oh, it has not yet come to that. :)


With all the fuss about privacy and the shopping lens, I would not be surprised to one day see some kind of notice to the effect that by using Ubuntu I have accepted certain conditions of use.

> By searching in the dash you consent to:

the collection and use of your search terms and IP address in this way; and the storage of your search terms and IP address by Canonical and such selected third parties (if applicable).

A small part of such a licence is already in place.

Regards.

---

### Post by The Cog on 2012-12-02
> **buzzmandt said:**
> no one else uses my computers, why do i need to 'fort knox' them?

To keep it that way.

---

### Post by bouncingwilf on 2012-12-02
> **grahammechanical said:**
> True. But is it your operating system? You did accept the End User Licence when you installed, did you not? Oh, it has not yet come to that. :)


With all the fuss about privacy and the shopping lens, I would not be surprised to one day see some kind of notice to the effect that by using Ubuntu I have accepted certain conditions of use.



A small part of such a licence is already in place.

Regards.

Erm......I'm using Linux Mint and not searching with the dash

Bouncingwilf

---

### Post by exploder on 2012-12-02
I think that with the various lenses being able to connect to the outside world a strong password is a good idea. Ubuntu is gaining in popularity and that will put a big target on it for hackers and malware. I am from an IT background and always use a strong password so none of this really bothers me. Better safe than sorry.

---

### Post by Yeeha on 2012-12-02
Theoretically... If program creates lot of rules for passwords for example that you cant use keys next to each other doesnt that make password cracking easyer as lot of the possibilites simply arent possible. Ofcourse it doesnt matter if password is long enough but...

---

### Post by zika on 2012-12-02
> **Yeeha said:**
> Theoretically... If program creates lot of rules for passwords for example that you cant use keys next to each other doesnt that make password cracking easyer as lot of the possibilites simply arent possible. Ofcourse it doesnt matter if password is long enough but...Symbolic dynamics in a nutshell...
On the spot!

---

### Post by mc4man on 2012-12-02
Actually my mistake for not noticing that in prev. it did also use the 'not good enough'. 
The current method was changed [quite some time ago]("http://bazaar.launchpad.net/~vcs-imports/gnome-control-center/trunk/revision/11761") (May) for good reasons, ubuntu hasn't upped g-c-c till recently.

So really the only change was to move from 6 to 9 as min, for my use of _add. users_ have set back to 6 in pwquality.conf

---

### Post by Yougo on 2012-12-02
> **Yeeha said:**
> Theoretically... If program creates lot of rules for passwords for example that you cant use keys next to each other doesnt that make password cracking easyer as lot of the possibilites simply arent possible. Ofcourse it doesnt matter if password is long enough but...

there's an XKCD for everything :)
[img]http://imgs.xkcd.com/comics/password_strength.png [/img]

---

### Post by jbicha on 2012-12-02
There's a [GNOME bug]("https://bugzilla.gnome.org/688315") asking for an override option.

---

### Post by mc4man on 2012-12-02
> **jbicha said:**
> There's a [GNOME bug]("https://bugzilla.gnome.org/688315") asking for an override option.

At least here none of the warnings are 'enforced', not sure then what MC means by 'get past this dialog...'?

(the whole warning's thing seems a bit suspect as one can go from 'weak', 'fair', 'good' or even 'strong' to 'not good enough' by **adding** additional characters of certain types/pattern to a weak/fair/good/strong password

Ex.

1@3467sdgbz123 = strong
1@3467sdgbz1234 = not good enough
(g-c-c seems to use some edits to mentioned conf but not others.

---

### Post by VinDSL on 2012-12-02
> **ventrical said:**
> I have always used 9 letter passwords [...]

> **bouncingwilf said:**
> Well my philosophy is to use a really strong password (15 Chars+) and then to set autologin.[...]

It's my machine and I'll do what I like!
Interesting!

I used a 26 letter password, at one time, but... sometimes I have to use someone else's machine, like a "gas pump" at a service station (odometer reading for corporate credit card), or an ATM machine (PIN number), and they won't allow that many characters.

I digress: I ran a program for over 2 years, on a dedicated machine, trying to randomly guess the correct order of the english alphabet (yes, I know there is no true randomness on computers).  After 2 years, it had correctly guessed the first 13 letters.  At 100K tries a second, I judged that it would take  1,840,645,487,000,000,000,000,000 years to guess them all -- soooo, I figured a 26 letter password was pretty safe.  LoL! :D

On PCs, I finally settled on 10 letters -- a mixture of caps/lower-case letters, numbers, international english keyboard characters, and punctuation symbols -- arranged in a geometric pattern.

On other systems, you have to go with the flow.  For instance, my cell phone provider only allows four numbers.  Really!  What a bunch of morons... :P

Anyway, the 10 letter sequence I normally use, allows me to use my left "pinky" (hidden under the palm of my left hand) to press the [shift] key, so if someone is watching me type my password (over my shoulder, with a security camera, etc.) they still don't know what I typed.

I have my web server(s) setup to use keyboard login or a virtual keyboard, so nobody can capture my login sequence with a "keylogger".  

You can do the same thing on an Ubu box by implementing Onboard or Matchbox.

Example: I`m typing this line with Matchbox ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-2-dec-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-dec-2012-1.png")[/INDENT]


Anyway, it's GOOD to be a little paranoid, especially if you're connected to the web, controlling web servers remotely (including forum mods & admins), doing online banking, blah, blah, blah. :)

---

