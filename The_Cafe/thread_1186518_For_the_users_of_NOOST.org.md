---
title: "For the users of NOOST.org"
date: 2009-06-13
forum: The Cafe
---

### Post by unknownPoster on 2009-06-13
Hey this is Jeremiah/namegame, I hope some of you will see this.

FYI, I went out of town for two days and when I got back I got this email:
> 
To our valued customer:

Today, at approximately 11:30AM Eastern, dallas158 suffered a permanent data failure. We regret to inform you that all data on dallas158 has been lost.

As you should already be aware, Linode does not provide backups of customer data. We do employ RAID to protect against single hard drive failure, but in this case the host suffered a controller, backplane, or other hardware failure that resulted in unit corruption and data loss, despite our efforts to resurrect the RAID unit on good hardware.

We have recreated all accounts that were located on dallas158 on a new server which utilizes RAID 10 instead of RAID 1 -- and although this doesn't mitigate the loss of user data, the future performance of your Linode's disk IO will be vastly superior.

We understand that this is an inconvenience and therefore will waive the fee for the next two months of service on this account. 

Please feel free to contact us with any questions you may have.

- Linode.com 		

This means that EVERYTHING we had is gone. The database, including the backups, all the threads...everything...

The last version I have is pre-migration from grubbn to noost.

We have a few options. 

1. Attempt to salvage the old database.
2. Start over from scratch.
3. Forget it and move on...

---

### Post by CharmyBee on 2009-06-13
Ouch, what a shame. I was starting to post there as well :(

---

### Post by arcdrag on 2009-06-13
I especially like how they attempt to water it down by calling it an "inconvenience".  Anyway, that's pretty rough...its always heartbreaking when something you helped to build gets destroyed by something completely out of your control.

---

### Post by unknownPoster on 2009-06-13
As an update for the "noosters"

I've posted a very simple webpage at noost.org

---

### Post by notwen on 2009-06-13
thanks for the heads up.  was wondering what was going on.  here's to hoping we can salvage some of the posts.

---

### Post by cmay on 2009-06-13
i been wondering why i could not connect there the last couple of hours i been trying. thats too bad. 

i maybe have a proposal for you but i cant promise anything yet. i am going to put up a webpage using a free server space to being with and then i will pay a small amount for having a 3 gigabyte sever space .

 we have already one used php fusion to make a forum once but no one ever joined so we closed it down. 

now as it is i need to put up a small webpage for very personal reasons and i will use the same place and the same php fusion and have my brother set it up and make sure its ok and then i will use the rest of the space for what ever comes to mind. 

that space could be used for creating the new os talk again and have me pay for it for at least a year if you can make it run and adminstate it as before. 

tonight my brother is going to put it up so it will be up and running by late night and i will start do what i need to wiht the page and then if there is a valid reason to keep it up for longer time i will pay for it within that long. a week or so before i know that for sure.  please pm me if it has any interest but as i said i can not promise anyhting. if it turns out to also  be  about also getting the new os talk back i know i can pay the money for it for a year and it would make me happy to do so. 

please keep posted what will happen and thanks for the psot here .

---

### Post by tjwoosta on 2009-06-13
> 1. Attempt to salvage the old database.

Why not?

> 2. Start over from scratch.

Id prefer this to quiting.

---

### Post by unknownPoster on 2009-06-13
> **tjwoosta said:**
> Why not?



It's not as easy as it sounds.

Ever since we merged I've been straightening out the database, and I feel "salvaging" it requires more work than it's worth...

Let me add, that's it's not a "pure" version of the database I have. The backup I got isn't in perfect condition.

EDIT: To make it more clear... the database I have some tables in the wrong places, some are missing, etc. It's in worse shape than I imagined.

---

### Post by nitehawk777 on 2009-06-13
I'm just really sorry to hear about the mess!!!  I didn't post a lot over there,...but I certainly did enjoy dropping by a lot, and reading all the other postings.  Hope it gets continued!:KS

---

### Post by FuturePilot on 2009-06-13
Ouch :( I was wondering what happened. That really sucks though...everything gone :cry:

From the sounds of it, I would say forget about trying to salvage the old database if it's in that bad of shape. I'd prefer starting over than giving up.

---

### Post by zmjjmz on 2009-06-13
Worst comes to worst, just start over.

---

### Post by kk0sse54 on 2009-06-13
I say we start from scratch, it was a great community and it would be a shame to just walk away and it sounds more trouble than it's worth to attempt to use the old back up image. Some of the stickies and tutorials can probably be saved from google cache and reposted. On the bright side at least we finally get reorganize and restructure the forums :neutral:

---

### Post by schauerlich on 2009-06-13
You didn't have any local backups?

---

### Post by LookTJ on 2009-06-13
I'd also concur that we should start from scratch.

---

### Post by unknownPoster on 2009-06-13
> **EDavidBurg said:**
> You didn't have any local backups?


Yes, I do, but for some reason, they are "broken." Tables are missing/shuffled. I really don't know what happened. I assume the back up system was "solid," but it wasn't. I tried restoring from them and things are really mixed up.

I think the database is just "worn-out" There were too many merges in too short of a time for things to be straightened out.

---

### Post by sertse on 2009-06-13
Continue of course! 

The grubbn to noost 

> The last version I have is pre-migration from grubbn to noost.


That is still a lot of data no? We haven't demerged again frm that long...

---

### Post by unknownPoster on 2009-06-13
> **sertse said:**
> Continue of course! 

The grubbn to noost 



That is still a lot of data no? We haven't demerged again frm that long...

All I know is that I have a SQL file from 5/30/09 and when I try to "restore" from it, things don't work.

---

### Post by Regenweald on 2009-06-13
> **unknownPoster said:**
> All I know is that I have a SQL file from 5/30/09 and when I try to "restore" from it, things don't work.

A company i used to work for did tape backups religiously, virus hit, corrupted a mailserver and then we realized that the tapes were never working to begin with ;) heads rolled. Sometimes even backups can suck.

---

### Post by unknownPoster on 2009-06-13
Updated information at: [http://www.noost.org](http://www.noost.org)

---

### Post by Skripka on 2009-06-13
> **sertse said:**
> Continue of course! 


I agree.

---

### Post by unknownPoster on 2009-06-14
The forum is now back up at noost.org

Please bare with us as we get up and running again.

Thanks,
Jeremiah

---

### Post by sertse on 2009-06-14
Wow, I'm start to get what you mean by over again.

anyway the member list could be salvaged at least?

---

### Post by unknownPoster on 2009-06-14
> **sertse said:**
> Wow, I'm start to get what you mean by over again.

anyway the member list could be salvaged at least?

I'm not sure. The mybb_users table is one of the ones with the most problems. I can't make any promises...

I wish this was easier, but when the server has a hardware failure, there's not much I can do.

---

### Post by handy on 2009-06-14
I'm stuffed today, Jeremiah, but in the following days I'll find & put back how-to's & whatever I can find.

Thanks again for your effort.

---

### Post by cmay on 2009-06-14
good to see the forum up again. :)

---

### Post by unknownPoster on 2009-06-14
Thanks for the cooperation by everyone so far, transitions and changes are hard to accept and adjust to. 

Even though we basically lost everything, I'm thankful that this bump in the road didn't seriously derail us.

---

### Post by chucky chuckaluck on 2009-06-14
they're only giving you the next two months free? seems they should reimburse you for all the time you were paying them to keep your data.

---

### Post by collinp on 2009-06-14
Data loss sucks.

Remember to make backups.

---

### Post by mr.propre on 2009-06-14
> **Hellow said:**
> Data loss sucks.

Remember to make backups.

+1
My hoster takes backups but i prefer to have a backup for my own.

---

### Post by mr.propre on 2009-06-17
Just somthing that hit me today. Why on earth do they use RAID 10 instead of RAID 5?

---

### Post by handy on 2009-06-17
Serious problems arise when your backups are kept on the same server.

Apart from that, we all know that RAID anything, is NOT a backup, don't we?

---

### Post by mr.propre on 2009-06-18
> **handy said:**
> 
Apart from that, we all know that RAID anything, is NOT a backup, don't we?

True, de change on dataloss because of failing hardware is smaller.

---

