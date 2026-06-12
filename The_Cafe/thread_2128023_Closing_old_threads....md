---
title: "Closing old threads..."
date: 2013-03-21
forum: The Cafe
---

### Post by zer010 on 2013-03-21
I found QIII's explanation for closing old threads insightful. I've never really thought about it that way...

  > If a post is older than a year or so and hasn't had a new reply in  that time, instead of replying to it, create a new thread. In the  software world, a lot can change in a very short time, and doing things  this way makes it more likely that you will find the best information.  You may link to the original discussion in the new thread if you think  it may be helpful.
[I]
Thread **closed.**[/I]

---

### Post by Roasted on 2013-03-21
Perhaps their response alone should be a sticky for a while. It's been happening more frequently lately.

---

### Post by QIII on 2013-03-21
I have to admit that I plagiarized it.

It's number 2 under "Posting Tips"  [here](http://ubuntuforums.org/misc.php?do=showrules).

 ;)

---

### Post by CharlesA on 2013-03-21
> **QIII said:**
> I have to admit that I plagiarized it.

It's number 2 under "Posting Tips"  [here](http://ubuntuforums.org/misc.php?do=showrules).

 ;)

How could you! :P

---

### Post by Perfect Storm on 2013-03-22
> **CharlesA said:**
> How could you! :P

I see a lawsuit in the horizon...

---

### Post by cariboo on 2013-03-23
Just FYI, we are looking at several auto-thread closing mods, once we decide which one to use, we'll submit it to Canonical IS for security testing, and eventual install.

---

### Post by deadflowr on 2013-03-23
> **cariboo907 said:**
> Just FYI, we are looking at several auto-thread closing mods, once we decide which one to use, we'll submit it to Canonical IS for security testing, and eventual install.

At first I thought it meant you were going to make one of the newer moderators comb the forums for old threads. That's what I get for reading multiple use terms like mod.

Also, it is truly amazing how many people read the quote in post #1 and go wow that's insightful. I can't help but think, ya know you were suppose to read it when you signed up.

---

### Post by cariboo on 2013-03-23
To quote QIII from another unrelated thread:

> What do you mean? Forum rules? I didn't know there were any stinking rules.

we get this response so often, we almost need a pre-made script to respond. :)

---

### Post by SeijiSensei on 2013-03-23
Why not just run a script each night that runs the mysql or psql command-line client to mark all threads with a creation date older than today-86400*365 as closed?  I wouldn't bother with a vB mod for a task that you can handle with a bash script.

---

### Post by CharlesA on 2013-03-23
> **SeijiSensei said:**
> Why not just run a script each night that runs the mysql or psql command-line client to mark all threads with a creation date older than today-86400*365 as closed?  I wouldn't bother with a vB mod for a task that you can handle with a bash script.

Good idea, but I don't know how well the berries would handle it - considering they have a tenancy to stop talking to each other after a change such as adding a new forum or new usergroup.

Also, since we don't have access to the servers and have to go thru Canonical IS, I don't know how feasible that would be or how much load it would put on the DB server.

---

### Post by vasa1 on 2013-03-23
I have mixed feelings purely because some of these necro threads did bring up something interesting which I probably wouldn't have come across otherwise.

---

### Post by SeijiSensei on 2013-03-23
> **CharlesA said:**
> Also, since we don't have access to the servers and have to go thru Canonical IS, I don't know how feasible that would be or how much load it would put on the DB server.

I thought Canonical just provided the hosting facilities.  I didn't realize you all were so dependent on them for actually managing the site itself.

I doubt it would be a big load.  While I realize the site is worldwide, I'd bet there are fairly slow periods.  Or you could just do it once each weekend.  Or spread the load over the forums and do a few each night.  I've managed some PG databases with record counts in the 8-10 million range.  They were slow until I figured out the proper indexes.  I presume vB's database already has good indexes.

Do you all not have a parallel development server that you can test things on outside of production?

---

### Post by NTL2009 on 2013-03-23
I have a different view of this. 

I've had some nagging (not show-stopper) problems, and I've searched this forum for answers. Sometimes I find some useful and substantial, but incomplete/inconclusive info on my problem in an old thread. But when I try to find out if there is any new info on this, or get a clarification, or just to re-start the discussion to find out if there is a solution I missed, or if others still have the problem, a mod comes along and shuts it down. I'm told to start a new thread.

OK, but then what? I assume that many others do the same as I do, they auto-subscribe to the thread they posted to. Are they going to take the time to PM me, or track me to see if I start a new thread? Probably not. It just seems better to allow the thread to continue, with all the info in one place. 

It seems at odds to me that people are told to search before starting a new thread, but then when they search and find one, they are told to start a new one. Which is it?

Yes, I understand that things change quickly, but some of these nagging bugs certainly are still around a year later. And if they have been fixed, why not get that info in the old thread, to provide some actual closure to the thread? If it is appropriate to start a new thread because things have changed, it seems it would be most helpful to include a link to the new thread, and _then_ close the old thread.

Is my thinking off-kilter? Am I missing something? I'm just trying to give some hopefully constructive feedback on this.

edit/add: I do think that a _warning_ that one is posting to an old thread is a good thing. But once the poster is aware that it is old, and decides that it is still relevant, I think the post should go through. JMO.

Thanks, NTL2009

---

### Post by Elfy on 2013-03-23
> **SeijiSensei said:**
> I thought Canonical just provided the hosting facilities.  I didn't realize you all were so dependent on them for actually managing the site itself.

I doubt it would be a big load.  While I realize the site is worldwide, I'd bet there are fairly slow periods.  Or you could just do it once each weekend.  Or spread the load over the forums and do a few each night.  I've managed some PG databases with record counts in the 8-10 million range.  They were slow until I figured out the proper indexes.  I presume vB's database already has good indexes.

Do you all not have a parallel development server that you can test things on outside of production?

Yes we are.

Yes we do have a dev server at the moment - however it will be disabled in due course.

we're actually looking at plugins to do this job negating the need for one of us to get involved. We would prefer it to be done with a mod, we have control of those. 

'Physically' there are the 7 of us and whoever happens to be on call at Canonical.

We are pretty much dependent on others, generally they are rapid to respond to our calls for help. Certainly in recent times we have had no reason to mutter.

---

### Post by llanitedave on 2013-03-25
> **NTL2009 said:**
> I have a different view of this. 

I've had some nagging (not show-stopper) problems, and I've searched this forum for answers. Sometimes I find some useful and substantial, but incomplete/inconclusive info on my problem in an old thread. But when I try to find out if there is any new info on this, or get a clarification, or just to re-start the discussion to find out if there is a solution I missed, or if others still have the problem, a mod comes along and shuts it down. I'm told to start a new thread.

OK, but then what? I assume that many others do the same as I do, they auto-subscribe to the thread they posted to. Are they going to take the time to PM me, or track me to see if I start a new thread? Probably not. It just seems better to allow the thread to continue, with all the info in one place. 

It seems at odds to me that people are told to search before starting a new thread, but then when they search and find one, they are told to start a new one. Which is it?

Yes, I understand that things change quickly, but some of these nagging bugs certainly are still around a year later. And if they have been fixed, why not get that info in the old thread, to provide some actual closure to the thread? If it is appropriate to start a new thread because things have changed, it seems it would be most helpful to include a link to the new thread, and _then_ close the old thread.

Is my thinking off-kilter? Am I missing something? I'm just trying to give some hopefully constructive feedback on this.

edit/add: I do think that a _warning_ that one is posting to an old thread is a good thing. But once the poster is aware that it is old, and decides that it is still relevant, I think the post should go through. JMO.

Thanks, NTL2009

I think that's a good point.  Sometimes necros can be informative and useful.  Sometimes not.  I would make it a case-by-case judgement rather than a simple automatic shutdown.

---

### Post by RobertoRecordo on 2014-01-10
I came to the forum today because I wanted to know the details of format strings in GEDIT, which are not documented in the gui help.
I did a search and the first thread that came up[HTML]http://ubuntuforums.org/showthread.php?t=1278676
[/HTML] 

I later found the simple anwer at [HTML]http://flsdemo.nrcfoss.au-kbc.org.in/content/docs/Gnome/gnome/users/gedit/2.26/gedit-insert-date-time-plugin.html.html#gedit-date-time-configure[/HTML],
and wanted to post it, as the answers given in the forum were less than useful:
```
rr@PT1500:~$ man strftime
```

however the thread is closed.

Does it make sense to close it when there is the only search result for "gedit date time" (search titles only)?

I don't want to open a new thread, that makes no sense at all.

---

### Post by CharlesA on 2014-01-10
That is a thread from 2009, and all thread are set to automatically close after 1 year of inactivity.

Reason being, old threads worked for old versions of Ubuntu, and it might not work for the newer versions.

---

