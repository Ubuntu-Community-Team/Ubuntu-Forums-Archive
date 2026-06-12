---
title: "Small Player scores big open-source win."
date: 2007-02-26
forum: The Cafe
---

### Post by Adamant1988 on 2007-02-26
[http://www.businessweek.com/technology/content/feb2007/tc20070226_455515.htm?campaign_id=rss_daily](http://www.businessweek.com/technology/content/feb2007/tc20070226_455515.htm?campaign_id=rss_daily)

Just curious what you all feel about this.  I know that a lot of people feel one of the keys to beating Microsoft is to compete with exchange, so I thought this was an interesting article to share. 


Discuss.

---

### Post by prizrak on 2007-02-26
I personally always thought that Linux has a very good server presence and that if we want it to become a viable desktop OS it needs to take over the corporate desktop as opposed to server. What Open Xchange is doing is pretty important though. I think it's one less thing for companies/people to depend on Windows for and could lead to greater Linux desktop adoption in the workplace. One problem with it is Evolution, it is a very crappy piece of software nowhere near the ease of use and integration of Outlook (I'm speaking as someone who tried both without having any experience with either) and generally needs a complete rewrite if it is to become a client of choice. 

Basically the problem with corporate Linux is that there are some very key applications either missing or are just not up to snuff (DIA comes to mind) .

---

### Post by OffHand on 2007-02-26
> **prizrak said:**
> One problem with it is Evolution, it is a very crappy piece of software nowhere near the ease of use and integration of Outlook (I'm speaking as someone who tried both without having any experience with either) and generally needs a complete rewrite if it is to become a client of choice. 

+1

---

### Post by macogw on 2007-02-26
I just wish Evolution would let you use the calendar without going through the email setup thingy.  Alternatively, Ubuntu should come with a calendar app so we can pretend Evolution's not there.  I don't want my email taking up my hard drive space.  Let it use someone else's server space.  And I don't want to have to be on this computer to get my email.

---

### Post by Gargamella on 2007-02-26
I like it, very good news

---

### Post by H.E. Pennypacker on 2007-02-26
> **macogw said:**
> I don't want my email taking up my hard drive space.  Let it use someone else's server space.  And I don't want to have to be on this computer to get my email.

Same here!  But if that's the case, why don't I just go on Firefox, and check my GMAIL account through the browser?  Eliminates the need for an email client.

---

### Post by CarpKing on 2007-02-26
> **H.E. Pennypacker said:**
> Same here!  But if that's the case, why don't I just go on Firefox, and check my GMAIL account through the browser?  Eliminates the need for an email client.

Yeah, but if you want to use the calender or address book, you have still have to set up evolution with some sort of email address, even if it's a fake and you set it to never check it.

---

### Post by YourSurrogateGod on 2007-02-26
If you ask me, this talks more about the skill of the people working on the open source model. I know plenty of people that do some incredible things in Windows.

It's the people, not the OS.

---

### Post by DoctorMO on 2007-02-26
To be honest the way in which some apps simply copy features instead of thinking about how to build software is not good at all!

Take for instance email applications, no way should your email application deal with addresses, address books, calendars or anything else for that matter; they should be handled via dbus to allow all apps to add to address book or take from address book including firefox when required.

The same can be said of pda/mobile apps, the linux developers simply tried to copy palm desktop and failed because palm desktop is horrible. we should be looking to integrating not simply making lots of apps do EVERYTHING. linux shouldn't be an emacs competition.

The first distro to integrate dbus with personal data wins my vote, if I wasn't busy with my current project I'd do it myself.

---

### Post by YourSurrogateGod on 2007-02-26
Doc, what's dbus?

---

### Post by YourSurrogateGod on 2007-02-26
Also, in some respects, it's not the fairest comparison between Windows and a smaller company. Smaller companies tend to be more flexible and outperform the bigger ones much better. A better comparison would be Red Hat/Suse vs. Microsoft.

---

### Post by DoctorMO on 2007-02-26
dbus is a messaging protocall where one application say your address book can 'listen' via dbus for requests and submissions of address book entries from other applications. as long as all address book applications follow the same dbus language it doesn't matter what address book is listening.

What you end up with is an ability to transparently send formal data to and from the applications that you have designated. so you may even have a bookmarks application that instead of firefox and konqueror all having their own bookmarks they simply communicate over dbus addition and management of bookmarks.

this allows the programmer to concentrate on making his application do one thing and one thing well; something which has been a main stay of linux/unix applications. unfortunately a lot of gui developers try and branch out and make their creations do everything under the sun in order to add value when it isn't that kind of value they need.

---

### Post by Polygon on 2007-02-26
im taking thats what mac os X uses (dbus) when it has stuff like "the address book" and "dictionary" being used across multiple things across the system

---

### Post by Adamant1988 on 2007-02-27
> **DoctorMO said:**
> dbus is a messaging protocall where one application say your address book can 'listen' via dbus for requests and submissions of address book entries from other applications. as long as all address book applications follow the same dbus language it doesn't matter what address book is listening.

What you end up with is an ability to transparently send formal data to and from the applications that you have designated. so you may even have a bookmarks application that instead of firefox and konqueror all having their own bookmarks they simply communicate over dbus addition and management of bookmarks.

this allows the programmer to concentrate on making his application do one thing and one thing well; something which has been a main stay of linux/unix applications. unfortunately a lot of gui developers try and branch out and make their creations do everything under the sun in order to add value when it isn't that kind of value they need.

Novell is working on something that sounds like what you're saying.  I've seen the mockups for the design, GAIM, evolution, and other programs were all talking to the exact same "address book" It was pretty neat.

---

### Post by steven8 on 2007-02-27
> **Adamant1988 said:**
> [http://www.businessweek.com/technology/content/feb2007/tc20070226_455515.htm?campaign_id=rss_daily](http://www.businessweek.com/technology/content/feb2007/tc20070226_455515.htm?campaign_id=rss_daily)

Just curious what you all feel about this.  I know that a lot of people feel one of the keys to beating Microsoft is to compete with exchange, so I thought this was an interesting article to share. 


Discuss.

Every big deal a linux creator can make like this is terrific.

---

### Post by DoctorMO on 2007-02-27
Can you remember what it was called? It's good they're looking into this kind of thing. it shouldn't be too hard you just have to have enough authority to create a standard and stick to it.

---

