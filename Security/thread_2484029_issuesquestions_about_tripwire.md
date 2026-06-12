---
title: "issues/questions about tripwire"
date: 2023-02-15
forum: Security
---

### Post by gamingranpa on 2023-02-15
Hi.  I recently learned about Tripwire and decided to set it up.  I had a few problems with doing so even following instructions on a couple of different posts on line, but seem to have most of it running now.  I still have a few questions/issues that I would like help with:
   1) it seems when I installed or upgraded to Ubuntu 22.04 (and apparently even before that) Tripwire was included as a package and asked for the site key.  The question didn't set up a site key, it asked for the existing site key.  During installation.  Of course, I didn't know what it was or what the site key password was, so it eventually cancelled and went on with installation.  Shouldn't it be setting up the site key?  Maybe it should even introduce the package first and ask if the user wants to set it up?
    2) after reading the how-to's on line and getting started, I found the package was already installed but not set up.  Following the instructions from at least 2 different sites, I was able to configure it correctly and get it running.  Imagine my surprise when I found it had already been sending messages to root's mail!  Can I change that and have it set up to send messages to my user account instead?  Preferably my email account, since I rarely use the built-in mail account on a home computer.
    3)  I'm still getting a few error messages, especially when I get updates and try to update Tripwire's data.  I have struggled to get it done as best I can, so now I have several *.twr files.  Even though I specify one to use, I get an error message stating the file is formatted incorrectly:

### Error: Invalid input stream format.

    How do I fix that? I mean, I *did* find a user manual on line that I downloaded for free, but it's extensive. I'm sure it's faster if I can get the question answered here.

    Those are my questions, basically.  I wonder if it wouldn't help for users to know it is "installed" on their systems already, by default, and if it wouldn't be good to have the man page set up to offer information like this for the Ubuntu version.  What I get is the typical man page for the generic product.  How about setting one up to tell Ubuntu users it is installed and where to go from there to get it running properly?

     Thanks in advance!

---

### Post by TheFu on 2023-02-15
To initialize the tripwire setup, use the 'sudo tripwire --init' command.

Tripewire was designed for administrators, not end-users.  

Inside enterprises, professional administrators will usually setup an MTA to ensure admin messages are forwarded to the correct administrator for the system.  They don't allow the MTA to accept any remote email, just send. If you don't setup an MTA, forget about sending emails.  Once an MTA is configured, then use the normal method of forwarding email to the account you wish to have sensitive emails sent.  Typically, that's with 
```
sudoedit /etc/aliases
sudo newaliases 
```
**This should never be outside your LAN!**  Definitely not some gmail account.  

Once the MTA is setup and forwarding emails, you'll be better off using crond too, since cron tasks send their output to email for the userid the task is running under.  Same applies for 'batch' and 'at' and 'logwatch' tools as well.

I haven't used 'tripwire' since the 1990s, preferring to use logwatch and versioned backups as my first line security methods for home systems instead.  I remember installing it about 10 yrs ago and finding maintaining the new signatures was more hassle than I'd remembered before.  Perhaps that's changed.  With versioned backups, seeing all the files that changed is pretty easy.  Cross-reference the changed files with those 'logwatch' says were update isn't hard.  Perhaps tripwire is better at this now?

---

### Post by gamingranpa on 2023-02-16
Thanks for the quick response.  I wasn't aware of the aliases, but seems as though it would be the same.  Guess I'll just get reports from the root mail.  I seem to have this running automatically, along with Tiger and several other security routines, since they are sending updates to root on a pretty much daily basis.  Strangely, I can't find them in a cron listing, but they are running and keeping up.
   Also appreciate the advice.  Aside from getting the update to work without errors it seems to work pretty well.

    I used to see a way of marking a response as being a good answer, would mark yours as such but don't see that now.

---

### Post by TheFu on 2023-02-16
The aliases file without an MTA is useless.  MTAs are postfix, sendmail, exim. Their may be some others, but they aren't used worldwide.  sendmail is a beast, so best avoided.  postfix has a "satellite" system setup that is pretty trivial to setup so local mail gets send somewhere else ... assuming you have a real mail server on your network that will accept LAN emails.  Basically, any of my systems can send emails to almost anyone in the world, though they cannot always reply, since the source system isn't resolvable by other internet email servers.  

I find it nice to have a workstation grab some information daily, then send it to an email address that I monitor.  For example, I always have a current NOAA weather report waiting for me every morning.  I don't have to go looking for it nor do I have to add a special weather app that runs all the time/spying on the system or LAN.  One little curl script with a little formatting and the output is forwarded to an email address. Lots of things can be automated with their results sent.

---

### Post by gamingranpa on 2023-02-18
I hadn't thought about having my computer look up other thinks (like NOAA reports) and mailing them to me.  That's an interesting idea.  I have my own routine I use as an extensive greeting program and used to have it looking up weather on line, but removed that portion when Underground Weather changed it's format.  At this point, I have "My Weather Indicator" running that does the job for me anyway.  It's pretty good, though some of the functionality seems to have been lost over time.

---

### Post by TheFu on 2023-02-18
> **gamingranpa said:**
> I hadn't thought about having my computer look up other thinks (like NOAA reports) and mailing them to me.  That's an interesting idea.  I have my own routine I use as an extensive greeting program and used to have it looking up weather on line, but removed that portion when Underground Weather changed it's format.  At this point, I have "My Weather Indicator" running that does the job for me anyway.  It's pretty good, though some of the functionality seems to have been lost over time.

The youngsters these days think they invented things like twitter messages and having data in 1 central place.  Not true.  For over 40, perhaps 50 yrs, we've been emailing ourselves information.  In the real old days, I'd have things emailed to me like source code for programs because I had an email-only internet account. This was long before http.  

Even in the early 2000s, I had an "iPager", which was an email-only device. To get information, there were a few great email-interface tools where we could ask for all sorts of information - like tracking fedex/ups/dhl/usps packages, locations of local stores (starbucks/walmart/mcds....), and even personalized assistants that could remember facts or remind us about meetings exactly when we needed to know.   I used [email]pi@hz.com[/email] and IWantSandy [https://boingboing.net/2007/11/14/i-want-sandy-perfect.html](https://boingboing.net/2007/11/14/i-want-sandy-perfect.html) extensively from my ipager.  Neither successfully move to a sustainable business model, but both were extremely useful before portable devices had IP networking capabilities.  the iPager blackberry 950 was a mobitext connection on a packet network.  Perfect for text and email knowledge access.  The FROM email address was how individual information for a single person was controlled.  OTOH, I doubt many people cared when I was looking for a UPS store + hours open to mail a box.  1 email (the subject held the command) and 2 minutes later, I'd know the answer.

Providing information which all companies do, but having a 3rd party scrap it from their websites made some of these companies unhappy. They added terms of service to prevent scraping and started adding ugly javascript with ajax to make getting the information harder (at the time). Of course, some of that data may have been sensitive for 1 or another reason.  If someone knew how to determine package tracking numbers, they could submit 100K queries looking for some packages they could steal.  Why most companies would want to make it harder for people to find their retail locations and operating hours, I don't know.

These days, people use anonymous twitter bots for similar purposes.  A more complex solution, to a simple problem handled via a script connected to procmail [https://www.intersessions.com/autoresponder.html](https://www.intersessions.com/autoresponder.html) with an MTA.

---

