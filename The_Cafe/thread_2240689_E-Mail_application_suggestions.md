---
title: "E-Mail application suggestions"
date: 2014-08-21
forum: The Cafe
---

### Post by msknight on 2014-08-21
I used to run Kmail because it was important to me that e-mail was kept in a folder structure. Easy to back up and easy to move between machines.

However, they changed with version 2 and incorporated a database which meant I had to change.  I switched to Thunderbird but somehow it lost months worth of e-mails so I switched.

I settled on Claws mail for some years, but I use a lot of e-mail, and the developers won't entertain adding features which I need, unless they need it themselves; like filter processing outgoing mail, search for mail in folders below the current folder, and also lately there is a bug where if I send a mail, the sent mail vanishes in to thin air. It is supposed to go in the sent folder, but something is wrong somewhere ... so I've had enough of it.

So ... I need a reliable alternative which filters outgoing mail as well as incoming, stores mail in a folder structure so it is self contained and easy to backup/move, and searches more than the current folder. 

Any suggestions please? I'm willing to go back to Thunderbird or Kmail if things have changed since I used to run them, and I also have a small history of donating to projects that make a positive difference to my life.

---

### Post by buzzingrobot on 2014-08-22
There's Evolution, which will bring in as many Gnome dependencies as Kmail brings in KDE dependencies. Trojita ([http://trojita.flaska.net/)]("http://trojita.flaska.net/") is a QT app I have not used.  Geary is a newer app, but isn't trying to do the things you want. Balsa is an old Gnome2 vintage app in a questionable state of support.

Other than those and the three you've tried, I can't think of any other GUI mail apps for Linux. There's definitely a shortage. (FWIW, I used to find Kmail unusable. But, in current KDE releases, it's been fine.  However, I don't think I'd try it as a standalone outside KDE.  As you've seen, it's strongly coupled with KDE's "semantic desktop" aka the databases.)

Text-based email clients are out there, including Alpine and Mutt.  Mutt, in particular, is adamantly keyboard fixated, requires much hands-on setup work editing config files and such, pushes HTML, etc., rendering out to external tools, and, I suspect, could be massaged to do what you need.

If by "folder structure" you mean a client that uses maildir, that limits your options even more.

---

### Post by msknight on 2014-08-23
Yup, maildir, for portability and ease of backup/restore. It seems that a load of devs are making their product for them, and not thinking about other people. They expect everyone else to be coders, like them, and able to alter their product easily. They seem to expect everyone to have concluded the same choices about working environment as them and as a consequence end up with a niche product that suits them but will never make it in the wild.

And I'm saying that about things across the board. It seems to be an attitude that is not only in the open source community but also in commercial product these days ... and it is driving me nuts because the very thing I came to IT for, to make life easier for people, is slapping me in the face from the people who create the tools I need to support not only my self, but other people. I feel like a generic mechanic but the company that makes my tools is creating spanners that don't grip a nut properly, because the developer behind it is using screws.

But somehow, the devs that think like this seem to think that they can carry on with this attitude and still make a fortune? Nope. Whenever I make a donation, I get such a thank-you that it looks to me like the devs aren't getting much, and are wondering why?!

And the situation is summed up in the list of e-mail alternatives ... which, by the way, many thanks for putting that list together. I appreciate it.  So ... it looks like it is back to Thunderbird.

---

### Post by msknight on 2014-08-23
You know ... I think I'm going to take a chance and give Trojita a try.  Thanks for the heads up. - Oh, cancel that, it's IMAP and I don't have the remote storage for the number of e-mails that I go through. I have history and archives going back to 2003. It would have been earlier than that, if some un-named e-mail clients hadn't toasted my storage.

---

### Post by buzzingrobot on 2014-08-23
> **msknight said:**
>  It seems that a load of devs are making their product for them, and not thinking about other people. They expect everyone else to be coders, like them, and able to alter their product easily. They seem to expect everyone to have concluded the same choices about working environment as them and as a consequence end up with a niche product that suits them but will never make it in the wild.


There are reasons for that. At its roots, FOSS exists for developers. It allows developers to modify/fork/leverage existing code to scratch their own itches.   If the interests of users are considered, those users are often other developers. (E.g., things like emacs, vi, mutt, tiling window managers, etc., were obviously not created for mainstream users.)

Surprisingly, there remains a lingering notion that any focus on usability, design, consistency, etc., amount to pointless eye candy.

Mostly, I suspect, people just get it wrong, even if they do try to build something for ordinary users. Like any other creative activity, most of the results will not generate any kind of appeal.

i think it is commonly assumed that "everyone" is using web mail -- Gmail, Outlook, Yahoo, etc. -- so why bother writing a new client?  That's wrong, of course, but there's little incentive for FOSS developers to consider otherwise.

---

### Post by msknight on 2014-09-01
Thanks for this.  Good reasons. 

When i was developing the Dropcalc for the Lineage 2 Java system, (PHP and MySQL, I never made the jump from Pascal to C) I was mostly motivated by people wanting to use the system and making suggestions to improve it. It went way beyond what I needed it to do .. but that was my incentive; to see the system out there and people wanting to use it.

Certainly, I didn't expect my suggestions to be kicked back with things like, "You want it, you code it, " or, "We don't code for money."  ... I mean ... it was a bit of a shock to be honest.  Why develop something if you don't want to see it grow and succeed in the world?

Of course, when a russian crew took my code and removed all the attribution and started pushing it themselves; together with the hacker who found an SQL injection path and warned me about it allowing me time to patch it ... but then spewing it all over the internet to boost their creds ... you know that even after all these years I still get e-mail about that vuln. I gave up in the end.

I guess I'm just a dinosaur from a bygone coding era.

---

### Post by robin7 on 2014-09-07
I too had some minor issues with Thunderbird, and liked the older version better.  Seamonkey (also a Mozilla product, built from the old Netscape suite which was awesome) has an e-mail client very much like "the old Thunderbird," and has been as reliable and solid as T-Bird.  

Seamonkey is an all-in-one internet suite, and most Firefox / Thunderbird add-ons work on Seamonkey as well. I find the browser a little bit faster than Firefox, and the e-mail client is bug-free and rock solid.

---

### Post by msknight on 2014-09-16
Thanks for taking the time to suggest that. I'll go take a look at it.

---

### Post by Bucky Ball on 2014-09-16
Been using Thunderbird for years and never had a problem. I find Evolution to be buggy (my wife uses it and I did for a few months when I first started using Ubuntu and also found it buggy then, which is why I swapped back to Thunderbird).

Have just discovered the Lightning integrated calendar for Thunderbird so liking it more now. It has pepped things up a bit. Good luck with your explorations. ;)

---

