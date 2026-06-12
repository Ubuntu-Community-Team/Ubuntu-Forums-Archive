---
title: "password manager security"
date: 2023-08-09
forum: The Cafe
---

### Post by Skaperen on 2023-08-09
i have a free level email at protonmail.  today i got an announcement from them about their password manager service.  what seems wrong to me about this is storing the encrypted password database on their server instead of my local laptop.  other thoughts about this?

---

### Post by TheFu on 2023-08-10
> **Skaperen said:**
> i have a free level email at protonmail.  today i got an announcement from them about their password manager service.  what seems wrong to me about this is storing the encrypted password database on their server instead of my local laptop.  other thoughts about this?

For me, any time passwords are stored on someone else's computer, that fails my "smell" test for sanity.  It smells bad, though for many people, it is better than not using a password manager at all.  

Even local password managers have some liabilities, since root can dump all the data in RAM and snag passwords, if timed correctly.  Some password managers only decrypt the single line in their encrypted DB when the credentials are specifically requested. These tools also have a limited period for that data to be in RAM unencrypted, to limit exposure, but users need to allow the default settings and have those settings as short as possible to limit the time of attack viability.
Dumping RAM used by a password manager: [https://www.scmagazine.com/news/keepass-bug-lets-attackers-extract-the-master-password-from-memory](https://www.scmagazine.com/news/keepass-bug-lets-attackers-extract-the-master-password-from-memory)

All software can be hacked ... if not directly, though code insertion that sneaks into the code: [https://arstechnica.com/gadgets/2021/04/hackers-backdoor-corporate-password-manager-and-steal-customer-data/](https://arstechnica.com/gadgets/2021/04/hackers-backdoor-corporate-password-manager-and-steal-customer-data/)

I know little about protonmail, except they have a good reputation, are located in a county with strong privacy protections, and that I had an email account with them years ago, mostly as a curiosity.  I stopped using their email mainly because it required using a web browser to access and I find that foolish. We are each different, with different needs.

I would ask this.  Which is easier to hack?  A password saver with millions of users at the end of centralized computers, run by professionals, or a password saver running on millions of different computers, all behind different routers, spread all over the world?  I don't know the answer, but attacking 1 professionally run network seems harder than attacking lots of individual networks from by end-users.  OTOH, the pay-off for attacking the service is that millions of credentials become available to the attackers, not just the 20-50 credentials for cat-video websites and 1 bank that a typical end-user would have stored inside their password store.  I know where I'd spend my effort, as an attacker.

Security isn't a checkbox, "Yes, please".  It is a process.

---

### Post by Skaperen on 2023-08-10
the thing i was pondering was having the DB on a single device vs. an encrypted one "on the net" that i can access from anywhere.  i no long get around, except on the net and basically use one device.  so my needs fit that.  but maybe most people have a need for a network-available password DB so that was their product direction.

certainly the many security aspects are important.  i have considered putting together my own password manager.  but even if i code it in C that is not going to make it secure (i would be FOSS).  for the best security, something developed by experts and (peer) reviewed by experts is (IMHO) the way to go even if it has a lousy UI.  a good PM lets every app that needs to access password based services from anywhere (containers, for example), access it.  but what if someone else has a process running within the scope of allowed access.  good PM security involves good user security.   it is not a bit-flip even if everything can read (-only) that bit.  there is no ultimate security and probably never can be.  better security is a transition an just as you say, a process.  perhaps, for me, something less could be good enough my current needs.  i am not running one, yet, though i do have long random passwords all around, different at each place, even different for each account i have at X (the social media previously known by a name associated with birds).

---

### Post by TheFu on 2023-08-10
> **Skaperen said:**
> the thing i was pondering was having the DB on a single device vs. an encrypted one "on the net" that i can access from anywhere.  i no long get around, except on the net and basically use one device.  so my needs fit that.  but maybe most people have a need for a network-available password DB so that was their product direction.
Proper password managers use encrypted DBs that use well-known, well-tested, encryption methods like AES or GPG.  While I don't go sharing my password files, I go keep them on all the devices where they are needed. My "system of record" versions are on my main workstation.  I have personal, work, and shared password DBs, because I need to be able to turn over each to different people.  For example, when I left my last job, I gave my boss the work password DB and a sealed envelope for how to access it.  When I got home, I deleted my copies from everywhere and stopped the rsync script that runs nightly to copy that file to my 6 locations (securely). While I pushed the file(s) to my different computers, I also pushed it to a nextcloud instance that I run. This clones it to a tablet and phone automatically, if there are changes.  Simple. And because my NC isn't available without using a VPN into the home network, it is fairly secure.

I have little belief that some company trying to make money with a centralized password DB will care about security nearly as much as I do.  They talk a good game, but on a Friday afternoon, when the devops team is in a rush to drink beer, mistakes will be made.  The marketing people and CxO people probably do care, but the overworked devops guy isn't any different than the guy flipping burgers. It is just a job to them, a few days a month. Even if they are extremely cautious 28 days of a month, those other few days are easy to coast while at work and make mistakes.  We all do it and I expect they will as well.
 
I've been using password managers for over a decade, perhaps longer.  I don't just store passwords inside them.  Anything I don't want too lose or might need if I need to leave the country for an emergency are stored there.  passport info, immunization records, lots and lots of phone numbers, software license keys, communications with companies I may need to sue if they don't actually do what they claim they will do, ... and normal credentials for access via phone, computers, apps, ... all the normal stuff people use password managers to store.  I even have some black and white photos of important documents stored inside the encrypted DB.

Password managers aren't just for passwords.  That's the mistake nearly everyone makes.  If you are going to use this encrypted DB and take steps to ensure it is never, ever, lost, or unavailable, why not keep important things inside it?

20+ yrs ago, I had a text file with credentials that used a ZIP password for protection.  Before that, I was storing passwords in a spreadsheet.  As I added more and more accounts, I learned of the risks I was taking since ZIP encryption really isn't very secure.  I looked for a password manager that was cross platform and had a way to import/export data.  I can dump everything inside the password DB to an XML file ... though I don't know if images will come or not.  With XML, the data can be massaged to any format needed using a XSL translation.  Or a little script.
Fortunately, I picked a good tool, with an open DB file format shared by about 10 other tools.  This is good and bad.  For example, I'd like to have at least 5 different ways to unlock the password DB, but it seems only 1 is allowed.  Because not all my devices support a FIDO2 key, I'm stuck with long, random, text to unlock it.  I'd much rather have a few different unlock methods, like how LUKS does it, so it can be boot convenient AND secure, while still having a backup access method.

I do use the autotype feature, but I don't use the automatic login feature or any browser extensions. I have to specifically request the login/password to be typed. It isn't automatic.

I consider browsers to be enemy territory, so I try to keep my dependence on them for anything important to the minimum.  I run different browser instances within highly restrictive firejail sandboxes for nearly everything important. That means no addons/extensions are available, so it really wouldn't matter if I used browser extensions or not. They aren't available where I need the most secure access.  

Everyone has their own level of hassle they are willing to have for any feature. Two of my family members started using a password manager after they saw me using it.  We actually use the same DB format and have our final documents stored along with nice-to-have final instructions for when we die inside a password file that is pre-shared.  The way things are setup, I have the file, but have to travel to their home and do a little seeking to get the unlock information.  One of my sisters has 3 of us as executors for their estate, but we each have 1/3rd of the required unlock code needed to get into the DB.  Additionally, she hid the DB inside a weather safe container and has provided hints for where to locate it to one of her geocaching kids.  I've thought about doing something like that.  I'd use a microSD card and store the password DB on it, then tape that microSD somewhere that it won't be found accidentally, perhaps along the top of a door or under a living room table.  I suppose if I didn't want anyone to ever find it, I'd put it into my home office. ;)

Lots of uses for password DBs and managers. Lots.

---

### Post by Skaperen on 2023-08-12
i'm one of those that didn't know all that stuff a PM could do.  can it save "any" file type (like random binary garbage to make "them" waste time)?  my passwords have been mostly insecure all this time.  this needs to change.  so i need to be on a PM hunt (something FOSS that i can compile on target systems that have the compilers and linkers).  i will compile it to be sure source mostly matches what i'm running.

hmm, now what do i have that can be put into that PM DB.

---

### Post by Skaperen on 2023-08-12
> One of my sisters has 3 of us as...

4 of you.  nice.

---

### Post by DuckHook on 2023-08-13
In addition to TheFu's very complete and excellent advice, here are my two bits:

If I have any say in the matter, I want to control my own data.

When it comes to my bank or my doctor or my insurance, I don't have much (if any) say, so my data resides in their cloud and I just have to live with that.

Fine.

But where I do have complete say is in managing my passwords. I can have my password database cloned among a number of devices for redundancy. I can have it centralized in encrypted form in a very secure server over which I have complete control, like, say, my personal Nextcloud. I can have it associated only with very specific browsers which I use only for very limited sites. These are all uses where I can remain in control of my autonomy, so why give that up?

Protonmail is a good organization. They actually do strive to protect your privacy to the extent allowed by the laws of their jurisdiction. But they are nonetheless removed from my direct control, require me to trust yet another long string of strangers, and must acquiesce to any court orders including secret ones. These are potential dangers that don't exist if I keep everything within my own control.

Therefore, no cloudy password manager for me. My approach requires more work and maintenance, but it's worth it for my peace of mind and independence.

---

### Post by TheFu on 2023-08-13
> **Skaperen said:**
> > One of my sisters has 3 of us as...

4 of you.  nice.

Actually, the family is larger. Not everyone embraces password managers and not all of us like to talk technology, at least not with each other.  The family runs the full range of end-users.  Some memorize exactly which button to press with little understanding.  Others were programmers, but don't do it anymore.  2 of use were system architects for long times.  Some of the kids work with computers daily for their "$day_job" to create money.  Some only have a smartphone, but no computer.  The full range.

One is a Math professor, teaches beginning python at a small liberal arts university, but doesn't really know much about computers.  She started using a password manager, but still uses MS-Windows. I failed to get her to understand that programming python is easier on any OS except MS-Windows.  The school where she works, mandates MS-Windows computers for all students, so she doesn't have any choice. They don't have technical-minded students there. At least, that's her claim.  I can't talk math with her either, even with over 30 hours of math post-Calculus. Funny how specialization works.

Yes, you can store binary data inside a password manager, but I doubt it will make it work harder.  Since we don't want to create our own crypto, the files stored are just data, not seeds.  However, an external seed file can be used as a 2nd factor to unlock the password DB. I've never done that because keeping a seed file on all the systems, in addition to the passwd DB is just a little more hassle that I'd like.  People tend to use photos for their seed files, if you want to go that direction.  The photo isn't stored "inside" the DB, however. Doing that wouldn't be of any help.  Like with passwords, a portion of that seed file gets encrypted and the resulting crypt-text is saved.  Next time the password DB is unlocked, two crypt-text items are required to open it.  The encrypted converted password and the encrypted, converted, data from the external lock file.

---

### Post by PJs Ronin on 2023-08-15
I keep my userid/passwords on recipe cards, in my pantry.   Has worked well so far.

---

### Post by TheFu on 2023-08-16
> **PJs Ronin said:**
> I keep my userid/passwords on recipe cards, in my pantry.   Has worked well so far.

My mother would write down half her passwords in a little book she kept locked in a desk drawer near the computer. The other half was memorized and didn't change for all the different logins.  To have a complete password, she'd look up the username + partial password in her book, then append the memorized part that wasn't written anywhere.  All her complete passwords were over 12 characters, if the site allowed that.

The key parts in Mom's method what that no passwords where the same, the written down part were random, and her memorized part was long enough to be non-trivial as well.
Some people append the written down parts and begin with the memorized part.

Mom didn't travel the last few years.  For people who do travel, using a password manager is a necessity, but for a few passwords to access your home computers, using a method like hers for the physical login isn't a terrible idea, provided we treat those written passwords at least as securely as we would treat US$500 in cash.  Don't leave it out for anyone to find, but also keep it convenient for access where needed.  

Plus, we all need a secure method to have a complex way to access the password manager, right?

---

### Post by ian-weisser on 2023-08-16
A couple years ago, I wrote down a relative's login password while helping them.

A year later, they died.

Turns out that having the login password in the care of somebody trustworthy was immensely helpful to settle their estate. All their bank statements and investment statements were e-mailed. Everything on paper was years out of date. Without access to their system and their e-mail client, it would have been extraordinarily difficult to locate and secure those assets for the inheritors. Bills too, like house and car insurance and lienholders: The information from the bank statements didn't include policy numbers.

---

