---
title: "Let us build &quot;UPDATE BEST PRACTICES&quot;"
date: 2008-08-03
forum: The Cafe
---

### Post by rahmath on 2008-08-03
Hi All,

I would like to have a good idea regarding updating our Ubuntu installation. I googled for a hint, but no use. I think, this is a very much needed thing to build a best practices in updating ubuntu systems. I had found that many users had fallen in to trouble after unnecessary updates. So let us, each and every one share their ideas and experience in updating ubuntu system, thus finally we will have a better best practices which will be helpful for all the ubuntu users.

Let me share some of my Q's;

1. When the updates are ready to download and install, how can we decide which one to install and which should be left out (i didnt mean how to select it, i mean logically how can choose what are the required updates for our system.

2. What is the criteria in choosing update.

3. Is there any resources in the net to know about the reliability and stability of these updates? (means for eg; firefox 4 is launched and it is available in the update repo, but b4 appylying it to our system, we need to know whether its buggy or a reliable one)


like this... 

Now everyone please come up with your thoughts...


Hope this we can make this as a useful work.

Thanks in advance for each and every contributors...

---

### Post by Sef on 2008-08-03
Moved to Community Cafe.

---

### Post by stinger30au on 2008-08-03
i just let the update manager do its job and let it install everything it wants to. never had a drama with it yet

---

### Post by ThrobbingBrain66 on 2008-08-03
1. You should certainly download and install any security updates.  Really, the rest is up to the user, I suppose.  By expanding the 'Details' section of the update manager, you can see what each package update fixes and decide for yourself whether you want to update it or not. 


2. Security updates are a must, big fixes are really only necessary if you suffer from the bug being fixed, I guess. However, bug fixes will generally increase overall system stability for everyone.


3. In your example, if Fx 4.0 is released by Mozilla it must be stable.  If it's stable it will then makes it's way through the repos.  Ubuntu, and maybe other distros employ a proposed-updates repo where the updates can be downloaded and tested by anyone who's enabled this repo.  After they have been thoroughly tested, and no issues are reported, they are sent out to everyone in the regular update repo.

BTW, I don't think I've heard of anyone being bitten by a bad update since Breezy or Dapper.  The proposed-update repo has been invaluable in avoiding these types of problems.

---

### Post by armageddon08 on 2008-08-03
> **ThrobbingBrain66 said:**
> BTW, I don't think I've heard of anyone being bitten by a bad update since Breezy or Dapper.  The proposed-update repo has been invaluable in avoiding these types of problems.

I just found a thread in Desktop effects and Customization Section.....the guy's CF install broke after the recent updates: [Compiz just broke]("http://ubuntuforums.org/showthread.php?t=877546&highlight=update").
Another guy's themes broke after those updates: [Themes broken after update]("http://ubuntuforums.org/showthread.php?t=876569&highlight=update")

---

### Post by ThrobbingBrain66 on 2008-08-03
> **armageddon08 said:**
> I just found a thread in Desktop effects and Customization Section.....the guy's CF install broke after the recent updates: [Compiz just broke]("http://ubuntuforums.org/showthread.php?t=877546&highlight=update").
Another guy's themes broke after those updates: [Themes broken after update]("http://ubuntuforums.org/showthread.php?t=876569&highlight=update")

I should have been more clear with my statement.  Back in the Breezy and Dapper days, there were a few updates that borked A LOT of users' installs. Now, I don't want to make it seem like updating back then was a game of Russian Roulette or anything like that, but it did happen.  And that's not even to mention the troubles users had with updated kernels and their graphics drivers breaking.

Updates aren't going to be perfect for everyone.  As a developer, all you can try to achieve is 'almost everyone'.  To be fair, we don't know what kind of modifications were made to the installs that broke, which you linked to.  There hasn't been a major uproar in the community, so that leads me to believe that any problems were the result of one of the following:

[INDENT]1. A small, unlucky number of users encountered a problem that wasn't caught during testing.[/INDENT]

[INDENT]2. They made some modifications to their installs that caused the updates to fail.[/INDENT]

[INDENT]3. The updates didn't completely install or install correctly which led to their problems.[/INDENT]

In closing, I'd like to reiterate that my point is that updates are very reliable and a user should not be so worried about wrecking their install that they don't keep up-to-date.

---

### Post by armageddon08 on 2008-08-03
> **ThrobbingBrain66 said:**
> I should have been more clear with my statement.  Back in the Breezy and Dapper days, there were a few updates that borked A LOT of users' installs. Now, I don't want to make it seem like updating back then was a game of Russian Roulette or anything like that, but it did happen.  And that's not even to mention the troubles users had with updated kernels and their graphics drivers breaking.

Updates aren't going to be perfect for everyone.  As a developer, all you can try to achieve is 'almost everyone'.  To be fair, we don't know what kind of modifications were made to the installs that broke, which you linked to.  There hasn't been a major uproar in the community, so that leads me to believe that any problems were the result of one of the following:

[INDENT]1. A small, unlucky number of users encountered a problem that wasn't caught during testing.[/INDENT]

[INDENT]2. They made some modifications to their installs that caused the updates to fail.[/INDENT]

[INDENT]3. The updates didn't completely install or install correctly which led to their problems.[/INDENT]

In closing, I'd like to reiterate that my point is that updates are very reliable and a user should not be so worried about wrecking their install that they don't keep up-to-date.

So, what do you say should I install the recent updates......After seeing those threads I didn't apply the updates.

---

### Post by ThrobbingBrain66 on 2008-08-03
> **armageddon08 said:**
> So, what do you say should I install the recent updates......After seeing those threads I didn't apply the updates.

I'm saying that I applied the updates and had no problems. Now, I can't guarantee you'll get the same positive results as me. But you have to remember that A LOT of users installed those updates and you've only shown me only two that had issues.

---

