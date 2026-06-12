---
title: "Ubuntuzilla checks for updates frequently"
date: 2007-09-30
forum: Ubuntuzilla
---

### Post by heypete on 2007-09-30
Perhaps I'm mis-reading the crontab file, but it appears that Ubuntuzilla checks for updates every four hours, every day.

Here's the crontab file that Ubuntuzilla installed:
pete@serenity:~$ crontab -l
0 0,4,8,12,16,20 * * * /usr/local/bin/ubuntuzilla.py -p firefox -a checkforupdategui 2>&1 | logger -p user.notice -t "UBUNTUZILLA" -- 
0 0,4,8,12,16,20 * * * /usr/local/bin/ubuntuzilla.py -p thunderbird -a checkforupdategui 2>&1 | logger -p user.notice -t "UBUNTUZILLA" -- 

As far as I know, Mozilla updates their software every few weeks at most, unless there's a critical security update.

I'd really hate if I were being a burden on the Mozilla folks by querying their server every four hours for updates...particularly so if every other Ubuntuzilla user was hitting their servers all at those particular times. I'd imagine it'd make for some very busty traffic.

Surely it isn't necessary to query for updates more often than once every other day, right? Once a week is probably adequate. Also, it'd probably be better if the Ubuntuzilla-installed crontab randomized the minutes field, so as to spread the load out a bit more evenly. Having 10,000 (or more?) users hit a website for an update all at the exact same instant is Not Fun(tm).

Of course, if the update checking program is getting the version information from some other source (say, DNS) that's a bit more lightweight and more easily distributed, it might be ok to check every day...but randomizing the minutes is probably still a good idea.

Now, I could be completely wrong and have totally misinterpreted the settings in crontab, and will gladly stand corrected if someone points out my errors.

Cheers!
-Pete

---

### Post by nanotube on 2007-09-30
that is an interesting point, thanks for bringing that up!

according to web stats, there are more than 300k hits to the mozilla.org site per day (according to alexa), so i think an extra 2-3-10 k hits to the site would make that much of a difference - their servers are built to handle a lot more than that. but clearly as the number of ubuntuzilla users grows, this may become more of a problem.

also, i doubt that everyone hits the servers at the same time - everyone's clock is a few seconds to a few minutes off, so there's not a single spike at those hours, but rather a bit of a cloud (probably normally distributed! :) ).

as to update checking frequency per se - the reason it's there is so that people do not have to go unpatched for more than a few hours. if the update checking frequency is reduced to say, a week, it is conceivable that the users would not be notified for a whole week after the update is released. at that rate, you might as well be waiting for ubuntu repositories to release the updated .debs. :) 

as to why it doesn't just check once per day- people are at their computers at different times, and if it only checks once, it is quite likely that you just won't see the update notification because you weren't there. so i thought every 4 hours would be a good balance - noticeable, but not so frequent as to be an annoyance.

i think you have a great idea regarding the randomization of the minutes, so that the update checks are spaced out over a whole hour, rather than clustered immediately upon the hour. 

also, i think it's possible to only /query/ for updates once per day, cache the result somewhere, and then /notify/ every X hours. that way the frequency of notifications remains, but load on mozilla.org is reduced 6 times. i'll think about implementing that.

in the meantime, please let me know if you have any other comments, suggestions, solutions, or disagreements with what i have said above. :)

thanks again for your feedback!

---

### Post by heypete on 2007-09-30
I inquired because I run a small NTP server, and due to misbehaving clients I receive a huge amount of traffic every hour on the hour, even though the average level of traffic is quite low. Even though the Mozilla folks have more resources, it's polite to be nice to their servers, particularly with relatively resource-intensive HTTP requests. :)

ClamAV was having a similar problem with people checking for updates very frequently and this causing a big load on their servers, so they implemented a clever DNS-based version checking scheme which is very lightweight. It might be possible for you (that is, Ubuntuzilla) to setup a local DNS-based version checking thing (perhaps the end-user's computer does a DNS query for a TXT record corresponding to "firefox", and your system returns the current version number) that will check the Mozilla site, say, once an hour. This way we're not burdening the Mozilla folks with a huge number of queries, and DNS is very lightweight and easy to expand capacity to.

I'm also somewhat curious why Firefox/Thunderbird can't take care of updating themselves...I'm a relative newb to Ubuntu (been using it for about 3-4 months now), but why is it that Firefox/Thunderbird cannot update themselvees through the normal "Check for updates" method? That's always worked fine for me on the Mac and Windows computers. I realize that permissions and whatnot are different in linux, but surely there's a way to run Mozilla products in such a manner that they can automatically check and update themselves through the normal methods without having to run them as root, right?

Maybe there's a method to have Ubuntuzilla check for updates once per day at some regular interval (say,once  every 24 hours based on when they log in, rather than a specific time of day), and then display some sort of persistent dialog (like how Firefox does) that won't go away until you manually acknowledge or cancel it. This way, if the user isn't at their desk at the moment, they'll know there's an update when they return.

Ideally, the Mozilla folks could make a .deb that works, or the Ubuntu folks could backport Firefox to feisty. I dislike having to sit here and say "I can't wait until Gutsy comes out, just because I can update all the buggy stuff that I've installed in Feisty like Seahorse [encryption key manager], old versions of Thunderbird, etc.", because I know that if I stick with the repo versions, I'll have similar problems in 3 months or whatever. :)

Anyway, thanks for your hard work and excellent installer.

---

### Post by nanotube on 2007-09-30
well, i don't run my own dns server, so i don't think we can do a dns solution, as elegant as it seems. :)

the auto-update check in ff/tb requires having root privileges (or write privileges to the install dir, which usually means root privileges, unless ff/tb are installed into the user's home dir). thus, when running ff/tb as regular user, no update checking will be done. that's just the way ff/tb are built, and there's no way around it other than to change the actual code of firefox/thunderbird. 

i myself don't see why they can't at least /check/ for updates and notify the user - and then prompt the user to run ff/tb as root to actually carry out the update. gotta ask mozilla folks about that one.

i'll get around to improving the update check after my comp exams in a couple of weeks. maybe i'll come up with some nice framework - any ideas are welcome. persistent message on login (or on firefox/thunderbird start) seems like a nice possibility...

thanks for your thoughts :)

---

