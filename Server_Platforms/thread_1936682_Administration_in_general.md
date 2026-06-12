---
title: "Administration in general"
date: 2012-03-06
forum: Server Platforms
---

### Post by kgatan on 2012-03-06
I have a question which is a bit diffrent and maybe not directly related to ubuntu linux. But as there seem to be a lot of administrator here from big companys to home enviroments i am hoping on some insight in this issue.

I have been experimenting alot with nix systems now for a while, trouble shooting and testing different services etc. Im also the administrator of a small company and its IT.

My question is if you have some suggestions on how to efficiently manage documentation of configurations, troubleshooting, infrastructure and so on.

I find myself often to be a bit lazy in this area which results in having to the same search multiple times instead of reading back.

Are there any easier ways to do this that are more efficient then just documents?
Suggestions for books and guides related to this area of administration?

I tried googling but have trouble finding articles or guides.

---

### Post by spynappels on 2012-03-06
Separate changelogs for each server, whether it is physical or virtual, and document each change immediately along with why the change was made. Needs discipline but can be a lifesaver.

---

### Post by Jonathan L on 2012-03-06
> My question is if you have some suggestions on how to efficiently manage documentation of configurations, troubleshooting, infrastructure and so on...Just a couple of thoughts:

In some environments you can get a long, long, way with some disciplined use of a wiki, especially if you have any automated logging of the configurations.

An upscale solution, from quite a different angle, is the work of Mark Burgess, specifically cfengine, which you might care to read about.  [http://en.wikipedia.org/wiki/Cfengine](http://en.wikipedia.org/wiki/Cfengine)

Kind regards,
Jonathan.

---

### Post by d4m1r on 2012-03-06
I think you need to be more specific....Network administration or administrating linux PC's around the office?

---

### Post by kgatan on 2012-03-07
Thanks for the feedback!

If you have any suggestions for logging services please let me know. The package ive found so far seems to be "etckeeper" which i will look into.

A wiki sounds like a good idee as well. I considered a blog as a journal earlier for all experimenting at home but wiki sounds like a better option.
Any suggestions on a open source wiki for this kind of managemnet?

Its difficult to be more specific since the question is only regarding documentation of configurations. It concerns everything from infrastructure to software.

For a small company as the one i work with i guess that just simple documents are good enough since amount of users and servers are limited.
But if you have a company with staff that administrate other companys IT then the need for efficient documentations is much more important.

---

### Post by winh8r on 2012-03-07
> **spynappels said:**
> Separate changelogs for each server, whether it is physical or virtual, and document each change immediately along with why the change was made. Needs discipline but can be a lifesaver.

You wouldn't be the first sysadmin with eight pocket sized diaries in his briefcase, I can assure you of that!!

Diarys don't crash and pencils rarely fail to boot either.

---

### Post by Cheesemill on 2012-03-07
I've used several methods at various places that I've worked, from a big red book tied to the server rack to wikis.

Using a wiki tends to be my favourite option as several people can view/edit it at once as well as being able to automate tasks such as machine name / IP address lists , installed packages, etc...

---

### Post by HermanAB on 2012-03-08
Subversion or good old RCS.

I use RCS to keep track of changes to files in /etc:
[http://www.aeronetworks.ca/howtos/rcs-howto.html](http://www.aeronetworks.ca/howtos/rcs-howto.html)

and a combination of log books and Wikis.

---

### Post by Jonathan L on 2012-03-11
> A wiki sounds like a good idee as well. I considered a blog as a journal earlier for all experimenting at home but wiki sounds like a better option.
Any suggestions on a open source wiki for this kind of managemnet?
[...]
But if you have a company with staff that administrate other companys IT then the need for efficient documentations is much more important.Hi again

I've had good results with Media Wiki software.  Attached is an image of the kind of thing which goes into one of them.  Even though the individual pages have very low numbers of authors, the amount of editing to correct minor errors (esp cut-and-paste recipe snippets) is small but very significant.  All those "edit" buttons just encourage fixing.  We have about ten usernames, anonymous browsing disabled, and as yet no read-only users.  I know that many of the freelancers reuse the information for other projects (how to install Raid, what good options are for DHCP, etc.) and I'm happy about that as it means they invest effort to keep this work accurate.

Pro: many people have experience of editing Wikipedia or see value in doing so; cheap; easy to add 
small things yourself.    One very valuable addition is PdfBook, which makes a big PDF of all the wiki pages in a particular category.  The API is pure web, so it's pretty easy to automate article addition etc.

Con: It is very fiddly to make tables without scripted help, image uploads are tedious, articles can be difficult to organise, works much better if you make yourself some good templates and categories.  Layout can be tricky if you care.

The searching, recent changes, edit history facilities are really great on pretty much all wikis, including this one.  I don't know what we'd do without it on the projects we use it for.

Hosting is done off-site (at Amazon Web Services) so we have access from everywhere.  We've added a number of small custom additions to pull live data.  We're half-way through "add incoming email message as article", which will really help.  Additionally we will forward syslog to the same place, so we can cross-link from the wiki to the logs.

Hope that's of some use.

Kind regards,
Jonathan.

---

