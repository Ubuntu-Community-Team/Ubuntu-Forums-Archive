---
title: "How FOSS Development Groups Could Bring in Lots More Money in Donations"
date: 2010-04-26
forum: The Cafe
---

### Post by brucewagner on 2010-04-26
Please spread this idea to all the FOSS (free open source software) developers you know.

There should be a free app for Ubuntu which uses the machine's actual usage statistics to calculate how much you use each application, and each component of the underlying operating system... Then, matcheshat usage time up with the Development Groups who maintain that code... And offers a list of those groups... with a suggested fair percentage for each...

In other words, if a user ( me for example ), wants to "tithe" -- financially contribute -- to the developers and development teams who have created this wonderful masterpiece we call Ubuntu Linux and all its various FOSS applications... I would love a list... showing all the software applications and components I use most, and their associated development teams, with a percentage next to each one ( based on my actual usage ).

I would then simply decide..... If I want to budget, say, $20 per month as a contribution, I could break up that donation to the list of various development teams / organizations... based on my real world usage pastern.

Obviously, Canonical/Ubuntu does not create all the applications that I use. They are not Linux. They are not GNOME. They are not Mozilla. etc., etc. etc. Many improvements actually come from various other different distributions altogether -- like Fedora or Red Hat, for example.

Perhaps the same data that's collected by that "System --> Administration --> Software Sources --> Statistics" tab thingie... could be used...?

I envision the resulting page with a pie chart and a list, side by side.... looking sorta like the output of "Disk Usage Analyzer" (except, of course, listing components and applications by amount of usage, and listing the Development Groups responsible for maintaining each one).

The resulting list could give me a list of the components and applications I use most, broken down by percentages each, list the associated development team responsible for the maintenance of that code, and even a link to each team's donation web page.

I'd rather give money to these groups than to buying anti-virus updates...  Wouldn't you!?


Thoughts on this idea...?

---

### Post by Zill on 2010-04-26
[http://popcon.ubuntu.com/]("http://popcon.ubuntu.com/")

> The popularity contest project is an attempt to map the usage of Ubuntu packages.

---

### Post by bodhi.zazen on 2010-04-26
As this is not a support question, I moved it to the Cafe ...

---

### Post by brucewagner on 2010-04-26
> **Zill said:**
> [http://popcon.ubuntu.com/]("http://popcon.ubuntu.com/")

But I'd want to see this data specific to ME... and MY own personal usage...  not aggregated for all users in the world.

I'd also like to see percentages, and contact information for each development group... to make financial donations.

---

### Post by Zill on 2010-04-26
> **brucewagner said:**
> But I'd want to see this data specific to ME... and MY own personal usage...
If you install popularity-contest on your PC it will log *your* usage in /var/log/popularity-contest.

It should then be possible to paste the data into a spreadsheet and produce the analysis and charts you require.

---

### Post by brucewagner on 2010-04-26
> **Zill said:**
> If you install popularity-contest on your PC it will log *your* usage in /var/log/popularity-contest.

It should then be possible to paste the data into a spreadsheet and produce the analysis and charts you require.

I turned on the popularity-contest (within the Software Sources)....  but I don't see that file.  Maybe it takes some time to appear?

But... I want a GUI app that will use this data to look up the associated development teams, and their associated donation web pages...  and display the list alongside a nice pie chart. 

Won't you please write such a app...   :)

---

### Post by cariboo on 2010-04-26
You do realize that 75% of the developers are paid to do what they do, the other 25% do it as a hobby, and actually have real jobs, or are students. I haven't run into any starving developers yet. :)

---

### Post by Zill on 2010-04-26
> **brucewagner said:**
> I turned on the popularity-contest (within the Software Sources)....  but I don't see that file.  Maybe it takes some time to appear?...
From the [FAQs]("http://popcon.ubuntu.com/FAQ") in the link I supplied earlier:
> Q) When does popularity-contest run ?

A) popularity-contest is run by the weekly cron job 
   "/etc/cron.weekly/popularity-contest".

Under the default configuration of cron, this happens every Sunday
at 6:47 in the morning. This can be changed by editing /etc/crontab
but if your computer is not always turned on, we really recommend you
install the anacron package.
Feel free to write a GUI to improve functionality of the app - this is one of the great freedoms you have with FOSS. :-)

---

