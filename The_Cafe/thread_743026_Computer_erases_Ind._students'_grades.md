---
title: "Computer erases Ind. students' grades"
date: 2008-04-02
forum: The Cafe
---

### Post by Sporkman on 2008-04-02
[http://news.yahoo.com/s/ap/20080401/ap_on_re_us/grades_gone_4](http://news.yahoo.com/s/ap/20080401/ap_on_re_us/grades_gone_4)

> **Computer erases Ind. students' grades**

Tue Apr 1, 6:47 PM ET

EVANSVILLE, Ind. - A computer malfunction wiped out a month's worth of grades at three high schools and one middle school, giving struggling students a second chance but dismaying others.

The Evansville-Vanderburgh School Corp. announced on its Web site that the malfunction occurred during spring break.

Students at Harrison High had mixed reactions, depending on how the second semester was going for them, senior Ibrahim Dughaish said Monday.

"Some are really upset because they worked hard for five weeks," but others saw it as a reprieve, he said.

"My son is an honor roll student and I prefer him keep his grades. He works hard for them," said parent Teresa Hayes.

Upcoming report cards at the four schools will not be issued as scheduled. Instead, the final two weeks of the current six-week period will be combined with the final six weeks of the year into an eight- week reporting period.

Harwood Middle School Principal Mike Raisor said some of his teachers had printed out grades before spring break, but most had not.

"I think the reality set in with everyone that you couldn't do anything about it. They took it pretty well in stride," Raisor said.

The school district's announcement said IBM engineers determined the loss of data was caused by "an unfortunate and very rare combination of hardware problems and backup configuration settings."

---

### Post by aaaantoine on 2008-04-02
What, no paper trails?

---

### Post by mips on 2008-04-02
I wonder if they tried a data recovery company at all?

In most cases information can be recovered, just a matter of how far you want to take it and how much $$$ you have.

---

### Post by munkyeetr on 2008-04-02
Has their sysadmin never heard of BACKUPS!!!???

---

### Post by Dr Small on 2008-04-02
Yeah... What happened to the backups, or where was the IT department all this time?

Or really, to narrow it down, what are the IT department doing with all their time when they are supposed to be making backups??

Well, maybe it was an April Fools joke by IT to the school :p

---

### Post by billgoldberg on 2008-04-02
> **munkyeetr said:**
> Has their sysadmin never heard of BACKUPS!!!???

Just what I was thinking.

If that doesn't cost him his job, I don't know what will.

---

### Post by NullHead on 2008-04-02
Wow those poor students! 

Where did the idea of BACKUPS go??? this is nothing new people ...

If the IT department was functioning correctly no one would ever have known there was a problem and the system would only be down for a hour or two.

---

### Post by aaaantoine on 2008-04-02
Re: Backups!?

> The school district's announcement said IBM engineers determined the loss of data was caused by "an unfortunate and very rare combination of hardware problems and backup configuration settings."

So basically, they *thought* they had a working backup system in place, but apparently didn't.

---

### Post by freebeer on 2008-04-02
backing up to /dev/null is fast, but not recommended.  :D

---

### Post by herbster on 2008-04-02
I bet the cronjob had rsync with sudo and the sucker was waiting for a password, then boom some racoons gnarl the power wires.

---

### Post by munkyeetr on 2008-04-02
> **aaaantoine said:**
> Re: Backups!?



So basically, they *thought* they had a working backup system in place, but apparently didn't.

Still, just on my home computer I go in and check that my backups are running and functional every couple days (ie: I extract some of the archives randomly and look to see the files are there and they hold data). If it was my job, I'd probably check everyday as part of my routine, but that's just me.

---

### Post by popch on 2008-04-02
The problem starts with the article's title. It should not read 'Computer erases' but 'School loses through negligence'

---

### Post by Sporkman on 2008-04-02
> **popch said:**
> The problem starts with the article's title. It should not read 'Computer erases' but 'School loses through negligence'

I thought the title was cute. :)

---

### Post by forrestcupp on 2008-04-02
The school was relying on Window's System Restore as their backup method. :)

---

### Post by D-EJ915 on 2008-04-02
> **freebeer said:**
> backing up to /dev/null is fast, but not recommended.  :D:lolflag:

The ending sounded like "there was a hardware failure, but there was also a failure to back up"

---

### Post by LaRoza on 2008-04-02
That is simple, just restore from the backups.

I like it how it is blamed on the computer, not the humans.

---

### Post by Xzallion on 2008-04-02
If its anything like the schools in my area, they don't have a paid tech position.  They have one volunteer run the entire thing for the school district (which where I live thats about 12 different schools).  The schools get "technology" grants that can only be spent on computers/tv's/projectors etc so they have state of the art systems for nothing but word processing, and can use none of it to pay for good support onsite unless something goes wrong.  In which case they call "microsoft", and yes thats what they say... and wait for it to be fixed by the techs they call in.

No ones getting fired, or even reprimanded.  No ones there to check the backups, and I don't think most schools can afford to do backups or to pay for a data recovery service.   But then again I only know about the Southwest Missouri area here in the US.

---

### Post by billgoldberg on 2008-04-02
> **Xzallion said:**
> If its anything like the schools in my area, they don't have a paid tech position.  They have one volunteer run the entire thing for the school district (which where I live thats about 12 different schools).  The schools get "technology" grants that can only be spent on computers/tv's/projectors etc so they have state of the art systems for nothing but word processing, and can use none of it to pay for good support onsite unless something goes wrong.  In which case they call "microsoft", and yes thats what they say... and wait for it to be fixed by the techs they call in.

No ones getting fired, or even reprimanded.  No ones there to check the backups, and I don't think most schools can afford to do backups or to pay for a data recovery service.   But then again I only know about the Southwest Missouri area here in the US.

Doesn't every school has it's own IT department?

The high school where I went had about 200 computers and they had like 3 or 4 full time system admins.

What the point of having the latest computers if they can't be maintained properly?

---

### Post by lespaul_rentals on 2008-04-02
Anyone else think this is an April Fool's joke?  It sounds very unlikely that all the data would be lost.  It sounds even more unlikely that something like this would make the news.  And the parts about "struggling students seeing hope" and "successful students disappointed," come on.  If you had straight A's the school isn't going to reset your GPA back to 0, and if you're a lazy bum who doesn't care about last week's assignment, they aren't going to just let you get away with that.  There would definitely be some form of archives, whether on hard drive or paper.

All I can say is, if this is real, the IT department for that school district fails.  I'm not an IT administrator; I just have a server at home, but if I were maintaining a server with critical data on it, I would use a RAID-5 setup.  That way, if one drive failed, the system would still be functional and no data loss would be experienced.  I would have a daily differential backup, so any files modified that day would be backed up and replace the older versions.  I would also have a full, weekly backup performed every Friday night on two seperate drives.  If there were files that contained very critical data in them (such as students' grades) I would make a script to calculate the SHA-512 hashes of the original files and the files that had been written to the backup drives, to verify that they had not been corrupted during the transfer.  I would take one of the drives to a remote location, so that a fire or flood would not destroy it.  I would also have a bi-weekly backup onto a drive, just in case an outdated version of a file needed to be recovered.

---

### Post by lespaul_rentals on 2008-04-02
> **billgoldberg said:**
> Doesn't every school has it's own IT department?

The high school where I went had about 200 computers and they had like 3 or 4 full time system admins.

What the point of having the latest computers if they can't be maintained properly?

I work in the IT department for the Boise School District, the largest school district in Idaho.  We maintain about 50 sites.  There are about 10 different senior technicians that handle hardware and software issues for the schools, and about 5 or so network admins that handle the server.  I am an intern so I don't really handle too much of the hands-on stuff, and most of the assistance I give is over the phone, filling out work orders so the senior techs can handle it.  But I still know a lot about the inner workings of the IT department for our schools, and I can confirm what you are saying, billgoldberg.

---

### Post by jesusfreak107 on 2008-04-02
yes, it has to be an april fools joke, because a school that does not even have an IT department would have everything on paper.  plus, the only way that could happen is if they stored the backups on the same HDD that the originals were stored on.  Which would be... STUPID!  and, yes, this is also obviously the people's problem, if it is real.

---

### Post by jesusfreak107 on 2008-04-02
yes, that is true.  I do not attend college yet, and I am homeschooled, but I am tech support for almost 10 family computers, and I know that a school would have to have an IT department.  if they are running Windows, they would have miinor glitches almost every day, and frequent viruses, and if they were running Linux, they would need a Techie to help out the people that do not know how to use it.

---

### Post by jesusfreak107 on 2008-04-02
okay, everyone needs to go onto the story, and give it a one star rating. no account needed.

edit: okay, maybe you do need an account.  I'm not sure.

---

### Post by popch on 2008-04-02
I find the story all too credible. 

"an unfortunate and very rare combination of hardware problems and backup configuration settings" sounds like real life to me, in a setting where people keep forgetting that the computer alone is not a solution.

---

### Post by madjr on 2008-04-02
i guess they were using windows..

---

### Post by jesusfreak107 on 2008-04-02
amen

---

### Post by lespaul_rentals on 2008-04-02
> **madjr said:**
> i guess they were using windows..

That joke really isn't funny anymore.  I have never had unexplained data loss while using XP, ever.  To be honest, I have had more critical errors in the 6 months I have used Linux than in the 4 years I used XP every day of my life.  I love Linux, but stop it with the sour grapes attitude and appreciate XP for the decent operating system it is.

As far as file systems go, despite all of its problems, NTFS isn't a risky file system by any means.  Stop with the Windows jokes.  There are a score in every thread now.  If you're going to mock an operating system, at least come up with a unique way to do so.

---

### Post by popch on 2008-04-03
> **lespaul_rentals said:**
>   I have never had unexplained data loss while using XP, ever..

The OP states quite clearly that the data loss was explained, and that it was due to hardware problems.

The data loss became a problem because of improperly configured backup, whatever that might be. That means expressis verbis that they had no usable backup of the lost data.

---

