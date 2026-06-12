---
title: "Zen and the art of guessing passwords"
date: 2009-11-29
forum: The Cafe
---

### Post by LinuxFanBoi on 2009-11-29
recently this article came out on various tech news media outlets.

[http://it.slashdot.org/story/09/11/18/2149202/US-Government-Using-PS3s-To-Break-Encryption]("http://it.slashdot.org/story/09/11/18/2149202/US-Government-Using-PS3s-To-Break-Encryption")

Now I don't really want to get into a debate over the accuracy of the story or over the government attempting to break encryption,  we all know they do it.  But I would like to get some input on my logic that follows

They claim each PS3 in their cluster can guess 4,000,000 passwords per second. I did some rudimentary attempt to calculate how long it would take to guess a password 12 characters in length with a possible 82 characters commonly available on a typical English keyboard.

the result I came to was 4.12464203 × 10^85 years for a cluster of 60 PS3's to break this password.  This is of course assuming it doesn't break it until it reaches the last available combination.

Now I'm no mathematics genius,  so my math may be incorrect,  but I still suspect that the amount of time it would take to break a password of this length drawing on a pool of 82 characters is so astronomical that this is a very poor way to go about breaking into encrypted data.

If you come to a different conclusion than I please share your input,  as I suspect i may be doing the math wrong.

---

### Post by Exodist on 2009-11-29
To late at night for me to do math.. But sounds interesting..

---

### Post by Sin@Sin-Sacrifice on 2009-11-29
Wow... why not get a cell system like [this]("http://www.mc.com/products/systems/25u42u_dual_cell_blade.aspx")? I would think cracking people like that would be more intensive than that and if it were me deciding on a system then I would use that processor but on better hardware. Just my opinion though. Do the math on 60 of those blades @ over 800 GFlops per blade. Ha...

---

### Post by michaeldt on 2009-11-29
Those PS3's would only take 1.3s to crack a 6 digit password if only lower-case letters were used. 83 seconds if upper and lower case are used. Less than 10 minutes if numbers and the characters above the numbers are used as well.

Now add 2 characters to the password (length 8 ):
lower-case only: 14.5 minutes
upper and lower: 62 hours
upper,lower and numbers + chars above numbers: 35 days

For a 10 character password:
lower-case only: 7 days
upper and lower: 19 years
upper,lower and numbers + chars above numbers: 494 years

For a 12 character password:
lower-case only: 13 days
upper and lower: 51 644 years
upper,lower and numbers + chars above numbers: 2.56 million years

So if all you were up against was those PS3's then simply upper and lower case at 12 digits should be enough. But these are just the maximum possible time. They could guess it in 5 mins depending on where they start their scan and what password you chose.

Of course more powerful options exist and technology improves over time too. But combining upper-case, lower-case, numbers and symbols above numbers should be enough at 12 characters in length.

---

### Post by MJWitter on 2009-11-29
In your calculation I think it should be 82 ^ 12, not the other way around(and I have 94 possible keys on pretty average keyboard).  Also the article says the networked PS3s can check 4m passwords per second, so it is unclear if that is for the 20 they already have, or for each PS3.

---

### Post by RabbitWho on 2009-11-29
Bill Bailey's twitter was hacked twice in a row. Apparently his password was "BillBailey12345

---

### Post by LinuxFanBoi on 2009-11-29
> **MJWitter said:**
> In your calculation I think it should be 82 ^ 12, not the other way around(and I have 94 possible keys on pretty average keyboard).  Also the article says the networked PS3s can check 4m passwords per second, so it is unclear if that is for the 20 they already have, or for each PS3.

That's what I based my calculation on (82^12)/4000000 = 2.310501407e+16, the maximum number of seconds for 1 PS3 to crack this password.

(2.310501407e+16)/60 = 3.850835678e+14, the maximum number of seconds for a cluster of 60 PS3's to break this password.

Given 31,556,926 seconds in a year, it would take 1.220282254e+7 (~12202822.5) years to accomplish this task.

The US government is not going to break anyones passwords efficiently w/ any PS3's.

---

### Post by scragar on 2009-11-29
> **LinuxFanBoi said:**
> That's what I based my calculation on (82^12)/4000000 = 2.310501407e+16, the maximum number of seconds for 1 PS3 to crack this password.

(2.310501407e+16)/60 = 3.850835678e+14, the maximum number of seconds for a cluster of 60 PS3's to break this password.

Given 31,556,926 seconds in a year, it would take 1.220282254e+7 (~12202822.5) years to accomplish this task.

The US government is not going to break anyones passwords efficiently w/ any PS3's.

Unless they pick really bad passwords, You saw the maths above, it takes hours or days for short passwords regardless of what random characters you put in it.

---

### Post by Praxicoide on 2009-11-29
[img]http://imgs.xkcd.com/comics/security.png[/img]

---

### Post by LinuxFanBoi on 2009-11-29
> **praxicoide said:**
> [img]http://imgs.xkcd.com/comics/security.png[/img]
win! :)

---

### Post by Rainstride on 2009-11-29
> **scragar said:**
> Unless they pick really bad passwords, You saw the maths above, it takes hours or days for short passwords regardless of what random characters you put in it.

that why you should use random generated passwords for everything. or use something like this [http://supergenpass.com/](http://supergenpass.com/) ;)

---

### Post by LinuxFanBoi on 2009-11-29
> **Rainstride said:**
> that why you should use random generated passwords for everything. or use something like this [http://supergenpass.com/](http://supergenpass.com/) ;)

I prefer to have a client side application for this.  I don't like the idea that someone else can generate my password,  cache it and potentially sell it to the highest bidder.  yes I know it's paranoid,  but you never know what ind of shenanigans people are up to.  Well,  actually if you read a lot of TOS language,  you can use your imagination and still hit pretty close to the meddle of the dart board.

But yeah, I hear what you're saying.

Not to be nit picky but in the article they claim that the 4th amendment allows a suspect the right to withhold passwords from investigators,  wouldn't it actually be the 5th amendment?

---

### Post by scragar on 2009-11-29
> **LinuxFanBoi said:**
> I prefer to have a client side application for this.  I don't like the idea that someone else can generate my password,  cache it and potentially sell it to the highest bidder.  yes I know it's paranoid,  but you never know what ind of shenanigans people are up to.  Well,  actually if you read a lot of TOS language,  you can use your imagination and still hit pretty close to the meddle of the dart board.

But yeah, I hear what you're saying.

Not to be nit picky but in the article they claim that the 4th amendment allows a suspect the right to withhold passwords from investigators,  wouldn't it actually be the 5th amendment?
Nope, it's the fourth.
> The right of the people to be secure in their persons, houses, papers, and effects, against unreasonable searches and seizures, shall not be violated, and no Warrants shall issue, but upon probable cause, supported by Oath or affirmation, and particularly describing the place to be searched, and the persons or things to be seized.

---

### Post by blueshiftoverwatch on 2009-11-29
> **LinuxFanBoi said:**
> Not to be nit picky but in the article they claim that the 4th amendment allows a suspect the right to withhold passwords from investigators,  wouldn't it actually be the 5th amendment?
> **scragar said:**
> Nope, it's the fourth.
Of course that only applies for criminal cases, not civil.

---

### Post by LinuxFanBoi on 2009-11-29
> **scragar said:**
> Nope, it's the fourth.

Yes, that covers the search and seizure of the suspect's property.  But I still think it's the fifth that prevents any court of law or law enforcement agency from forcing a suspect to reveal a password.

> No person shall be held to answer for a capital, or otherwise infamous crime, unless on presentment or indictment of a Grand Jury, except in cases arising in the land or naval forces, or in the Militia, when in actual service in time of War or public danger; nor shall any person be subject for the same offense to be twice put in jeopardy of life or limb; *_nor shall be compelled in any criminal case to be a witness against himself_*, nor be deprived of life, liberty, or property, without due process of law; nor shall private property be taken for public use, without just compensation.

---

