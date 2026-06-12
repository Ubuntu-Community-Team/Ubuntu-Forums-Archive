---
title: "Rolling Releases"
date: 2013-04-28
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2013-04-28
OK - I've done the due diligence and looked for how / why / if subject will be employed by Ubuntu. 

I've not found a definite answer - is there one?

---

### Post by Mathor on 2013-04-28
[http://www.markshuttleworth.com/archives/1252](http://www.markshuttleworth.com/archives/1252)

Mark Shuttleworth announced it on his blog on 13.04's release day.

> In the work to underpin a rolling release, we made huge strides in  automated quality assessment and performance testing. From here on our,  I’m going to treat the cutting edge of Ubuntu as a rolling release,  because the team have done such an amazing job of making daily quality a  reality. That’s a value that we have all adopted, and the project is  much better off for it

Also in [https://launchpad.net/ubuntu/saucy](https://launchpad.net/ubuntu/saucy) milestones have been created to implement the monthly snapshot concept that was argued for in the last UDS, to potentially do away with the alpha and beta milestones.

Ubuntu 13.05 - Released May 31
Ubuntu 13.06 - Released June 31
Ubuntu 13.07 - Released July 31
Ubuntu 13.08 - Released August 31
Ubuntu 13.09 - Released September 31
Ubuntu 13.10 - Released October 31

and if this theme were to continue into the "T" series it would be as follows

Ubuntu 13.11 - Released November 31
Ubuntu 13.12 - Released December 31
Ubuntu 14.01 - Released January 31
Ubuntu 14.02 - Released February 31
Ubuntu 14.03 - Released March 31
Ubuntu 14.04 LTS - Released April 31

and it would roll on and on...

---

### Post by pfeiffep on 2013-04-28
Thanks Mathor, I guess my google search wasn't 'RARING' ):P enough!

So, in your opinion, does this treatment indicate that the end user will periodically perform apt-get {upgrade update dist-upgrade} and not have to actually install the next release?  Or is this just a spin on terminology?;)

---

### Post by Mathor on 2013-04-28
As far as I'm aware, if you are running the development release, the proposed plan is to sync the toolchain to point to "T" series when 13.10 is released, so that a dist-upgrade should be all that is needed to continue on to the "T" series.

---

### Post by roly33 on 2013-04-28
> **Mathor said:**
> [http://www.markshuttleworth.com/archives/1252](http://www.markshuttleworth.com/archives/1252)

Mark Shuttleworth announced it on his blog on 13.04's release day.



Also in [https://launchpad.net/ubuntu/saucy](https://launchpad.net/ubuntu/saucy) milestones have been created to implement the monthly snapshot concept that was argued for in the last UDS, to potentially do away with the alpha and beta milestones.

Ubuntu 13.05 - Released May 31
Ubuntu 13.06 - Released June 31
Ubuntu 13.07 - Released July 31
Ubuntu 13.08 - Released August 31
Ubuntu 13.09 - Released September 31
Ubuntu 13.10 - Released October 31

and if this theme were to continue into the "T" series it would be as follows

Ubuntu 13.11 - Released November 31
Ubuntu 13.12 - Released December 31
Ubuntu 14.01 - Released January 31
Ubuntu 14.02 - Released February 31
Ubuntu 14.03 - Released March 31
Ubuntu 14.04 LTS - Released April 31

and it would roll on and on...

I think the new Ubuntu Monthly builds makes better sense than having Daily Builds, as it should mean less bug slipping through due to having to build the .iso daily.

During the 13.04 Dev Cycle I had to do at least 3 clean re-installs due to buggy Kernel updates.

Roland

---

### Post by Mathor on 2013-04-28
I'm almost certain that daily builds will also be made. You will have the daily builds, weekly cadence builds, monthly snapshot builds, and 6 month stable release builds. The idea is to make as AS MANY builds as possible. Daily builds are necessary to maintain quality throughout the cycle. The more builds, the more testing, the better the quality. Where the rolling release is a benefit is ceasing to put so much pressure on "supporting" 6 month milestones. If you need complete stability and lots of support, that is what the LTS is for.

---

### Post by Mathor on 2013-04-28
Also the monthly milestone concept allows for development efforts to be more constructive, by thinking on a month-to-month basis, instead of setting huge goals over a 6 month period and not achieving a lot of those goals. The month-to-month concept allows for development efforts to be more organic and ever-changing. 

[http://status.ubuntu.com/ubuntu-raring/](http://status.ubuntu.com/ubuntu-raring/)

This shows the goals for this current month. This allows to break down 6 months of work into a bunch of 1 month goals. As you can see, developers only completed about 67 percent of what they set out to accomplish for the cycle. I think in the saucy cycle it'll be easier to accomplish more if work is broken up like that. All the freezes that come with having to produce alphas and betas and stable releases slow down the development process.

---

### Post by Starks on 2013-04-28
I can only assume that saucy-proposed is the rolling release.

---

### Post by Gavin77 on 2013-04-28
> **Mathor said:**
> 

Ubuntu 13.05 - Released May 31
Ubuntu 13.06 - Released June 31
Ubuntu 13.07 - Released July 31
Ubuntu 13.08 - Released August 31
Ubuntu 13.09 - Released September 31
Ubuntu 13.10 - Released October 31

and if this theme were to continue into the "T" series it would be as follows

Ubuntu 13.11 - Released November 31
Ubuntu 13.12 - Released December 31
Ubuntu 14.01 - Released January 31
Ubuntu 14.02 - Released February 31
Ubuntu 14.03 - Released March 31
Ubuntu 14.04 LTS - Released April 31

and it would roll on and on...

Not to be picky but June, September, November have only 30 days.
And Feb 31, I've never seen one of those before :)

---

### Post by roly33 on 2013-04-29
> **Gavin77 said:**
> Not to be picky but June, September, November have only 30 days.
And Feb 31, I've never seen one of those before :)

don't forget April only has 30 days as well

January,March,May,July,August,October & December=31 Days
April,June,September & November=30 Days
Febuary=28/29 Days

Roland

---

### Post by pfeiffep on 2013-04-29
So putting aside the calendar quirks :) how will this impact a user who wants to stay current? It just so happened that I switched to Ubuntu 12.10 in Feb. and thought joining the QA team and doing some testing would be a great way to introduce a new OS to me. So I ran both 12.10 and the daily 13.04 concurrently on 2 machines and I'm confident that this immersion paid off in spades. I've since adopted the 13.04 final and started evaluation Linux Mint 14.

I'm not quite certain how to employ this rolling release and use it to MY benefit. I really don't want to ignore a new methodology, but I'm ready to start using this a bit more in depth and start focusing on the functionality.
 
I was hoping that a rolling release would help me by being able to just upgrade raring periodically and not have to perform a 'fresh install' of saucy ever. I'm kinda making an anaolgy to M$ here with their service packs .. I was ably to totally skip Win ME & Vista staying with XP until I adopted Ubuntu. 

Hopefully I'm not offending anyone by mentioning M$ and I'd like to think that the price of freedom in computing is time spent learning!

---

### Post by roly33 on 2013-04-29
> **pfeiffep said:**
> So putting aside the calendar quirks :) how will this impact a user who wants to stay current? It just so happened that I switched to Ubuntu 12.10 in Feb. and thought joining the QA team and doing some testing would be a great way to introduce a new OS to me. So I ran both 12.10 and the daily 13.04 concurrently on 2 machines and I'm confident that this immersion paid off in spades. I've since adopted the 13.04 final and started evaluation Linux Mint 14.

I'm not quite certain how to employ this rolling release and use it to MY benefit. I really don't want to ignore a new methodology, but I'm ready to start using this a bit more in depth and start focusing on the functionality.
 
I was hoping that a rolling release would help me by being able to just upgrade raring periodically and not have to perform a 'fresh install' of saucy ever. I'm kinda making an anaolgy to M$ here with their service packs .. I was ably to totally skip Win ME & Vista staying with XP until I adopted Ubuntu. 

Hopefully I'm not offending anyone by mentioning M$ and I'd like to think that the price of freedom in computing is time spent learning!

All you have to do is change your Repo's over to the Saucy ones and away you go.

[This]("http://ubuntuforums.org/showthread.php?t=2138987") thread might be of some use to you.

Roland

---

### Post by pfeiffep on 2013-04-29
Thanks roly33 for the link. In addition to some humor interspersed I found that there was some real content. I'll certainly be waiting for a couple of months to jump on the bandwagon!

---

### Post by craig10x on 2013-04-29
Trouble is, i used the terminal commands to move over to saucy from raring and things really got borked up...i even tried making the changes by edited the list since they were still reading raring, but even after all that bother, my updater wouldn't work properly anymore...:(

I ended up having to re-install 13.04 from the final iso and that is running smooth as silk...:)

So ends my attempt to "roll" with development...they really need a more fool proof way of moving into each new version...upgrading can be hit or miss...i know that is what the developers mentioned they are aiming to do, but question is WHEN will it be available...obviously not for 13.04....but perhaps before 13.10 is released?  They haven't said as of yet...

So looks like i won't be participating in development anymore...it was kind of fun..i will miss it...and it worked surprisingly well...but this "change over" business...not always so successful, as it is right now...
What i liked about the idea of "rolling" is getting new stuff, getting each new version, and not having to keep re-installing to get it (and i am not fond of upgrading final versions to final versions...they can also be hit or miss too)...

Now, it looks like i am stuck back in having to re-install every 6 months again...

---

### Post by sgage on 2013-04-29
> **craig10x said:**
> Trouble is, i used the terminal commands to move over to saucy from raring and things really got borked up...i even tried making the changes by edited the list since they were still reading raring, but even after all that bother, my updater wouldn't work properly anymore...:(

I ended up having to re-install 13.04 from the final iso and that is running smooth as silk...:)

So ends my attempt to "roll" with development...they really need a more fool proof way of moving into each new version...upgrading can be hit or miss...i know that is what the developers mentioned they are aiming to do, but question is WHEN will it be available...obviously not for 13.04....but perhaps before 13.10 is released?  They haven't said as of yet...

So looks like i won't be participating in development anymore...it was kind of fun..i will miss it...and it worked surprisingly well...but this "change over" business...not always so successful, as it is right now...
What i liked about the idea of "rolling" is getting new stuff, getting each new version, and not having to keep re-installing to get it (and i am not fond of upgrading final versions to final versions...they can also be hit or miss too)...

Now, it looks like i am stuck back in having to re-install every 6 months again...

Did you edit Ubuntu.info as outlined in the saucy sources thread?

---

### Post by craig10x on 2013-04-29
Yep...i was pretty careful too (i found it rather tedious...there was so many lines that i had to substitute saucy for raring in)...and it still didn't help...i got frustrated and ended up re-installing 13.04 final (i had that as a back up disc)...which is where i am now...

Actually, a real rolling release doesn't require doing such things...i think they said they wanted to make it so you would not have to do this upgrading thing anymore...that there would be a kind of "symlink" that would automatically "point" to the next development release without you having to do a thing...question is: when and also how would you add that "symlink" or whatever it will be...

---

### Post by sgage on 2013-04-29
> **craig10x said:**
> Yep...i was pretty careful too (i found it rather tedious...there was so many lines that i had to substitute saucy for raring in)...and it still didn't help...i got frustrated and ended up re-installing 13.04 final (i had that as a back up disc)...which is where i am now...

Actually, a real rolling release doesn't require doing such things...i think they said they wanted to make it so you would not have to do this upgrading thing anymore...that there would be a kind of "symlink" that would automatically "point" to the next development release without you having to do a thing...question is: when and also how would you add that "symlink" or whatever it will be...

Ubuntu is not a "real" rolling release yet. I'm not sure what the plan was/is. A 'symlink' thing sounds sort of like a hybrid setup to me. 

The way I moved to saucy was to simply bring my sources.list into gedit, replace all raring with saucy, and did a dist-upgrade. Well, that went haywire in a way that sounds similar to what you experienced. I made those changes to Ubuntu.info, and did the raring-saucy change on my backup sources file. And it worked perfectly.

Anyway, I don't understand what is going on with "rolling releases" and all. I'm just going along as if it was the same old dev cycle. I'm not sure anything is really written in stone, other than Mr. Shuttleworth making a comment to the effect that the dev version WAS the rolling release. That's how I'm playing it.

---

### Post by craig10x on 2013-04-29
I hear you...well, in the developers discussion they said the plan was to add that new way to make it point to each new version...one had mentioned about a symlink, but they did say they had to work out how best to add in whatever they decide to use to do it...it sounded to me that they definitely wanted to do it...just had to figure the best way to do it...

I would imagine they should have it ready long before 14.04 arrives...so i would think sometime during this 13.10 development cycle...and i hope we will learn how it is coming along during the upcoming developer discussions...

Until then, i think i will just staying with 13.04 final...though i will certainly take a look at 13.10 development when daily builds start becoming available...though i would not consider installing until the "symlink" or whatever is actually available to add in...

Honestly, i would just upgrade from final to final...but i know that can be hit or miss also...i seem to do very well on development, though...

---

### Post by JonPaul on 2013-04-29
Hi Craig

It was a cut and paste at the _beginning_ of ubuntu.info, not changing raring for saucy....

Post #7 on how to change repos to saucy

So far (touch wood) have had no hassles.

JonPaul

---

### Post by craig10x on 2013-04-29
;)> **JonPaul said:**
> Hi Craig

It was a cut and paste at the _beginning_ of ubuntu.info, not changing raring for saucy....

Post #7 on how to change repos to saucy

So far (touch wood) have had no hassles.

JonPaul

Thanks...i think i see where i messed up!  Oh well, i guess i will just have to watch to see when they add the new method to 13.10...meanwhile, i will just stay on the 13.04 final....
When the new method is available, then i might consider installing 13.10 development at that point...but i definitely want that easier method before i go back into development again...;)

---

### Post by pfeiffep on 2013-04-29
I think Mark Shuttleworth[ answered]("http://news.softpedia.com/news/Mark-Shuttleworth-Says-That-the-Cutting-Edge-of-Ubuntu-Is-a-Rolling-Release-349083.shtml") 

> [FONT=Verdana]“In the work to underpin a rolling release, we made huge strides in automated quality assessment and performance testing. [/FONT]

[FONT=Verdana]“From here on our, I’m going to treat the cutting edge of Ubuntu as a rolling release, because the team have done such an amazing job of making daily quality a reality. That’s a value that we have all adopted, and the project is much better off for it,” said Mark Shuttleworth on his [/FONT][blog]("http://www.markshuttleworth.com/archives/1252")[FONT=Verdana].[/FONT]

[FONT=Verdana]This means that users will be able to treat the daily builds of Ubuntu 13.10, for example, as a rolling release model. It may not be the best idea, by Mark Shuttleworth thinks that the quality provided is good enough.[/FONT]

---

