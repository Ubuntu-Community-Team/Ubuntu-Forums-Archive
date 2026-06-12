---
title: "Running a script on CD insert?"
date: 2008-06-13
forum: Server Platforms
---

### Post by logical_thought on 2008-06-13
I'm trying to get a script to run whenever a cd is inserted, but I don't know how. I figured out how to get it to work with gnome, but  I need to find a way to get this to work on a headless server when no one is logged in.

So far I've tried setting up my script in cron. I install autofs and told my script to try and access the cdrom every few minutes, which works on the first cd...but then it keeps accessing the same disk. 

I would like to find a way to have the script run one time (instead of with cron) when the cd is inserted and then it ejects.

PS. Sorry if I posted this in the wrong place, I wasn't sure where this fit.

---

### Post by windependence on 2008-06-14
Why are you wanting to do this?

-Tim

---

### Post by logical_thought on 2008-06-14
> **windependence said:**
> Why are you wanting to do this?

-Tim
I make a lot of dvds and would like to back them up directly to my backup server instead of making the backup on my desktop and uploading them.

They are all dvds that I have made (home movies, trips, etc...)

---

### Post by logical_thought on 2008-06-14
Thinking on it now....all I really need is the cd to automount when it is inserted.

---

### Post by logical_thought on 2008-06-22
I solved this custom daemon, but I would still like to know if there is a built in (or easier) method.

---

