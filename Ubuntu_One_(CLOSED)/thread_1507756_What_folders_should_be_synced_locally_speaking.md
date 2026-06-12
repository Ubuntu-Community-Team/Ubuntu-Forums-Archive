---
title: "What folders should be synced locally speaking?"
date: 2010-06-12
forum: Ubuntu One (CLOSED)
---

### Post by Vanillalite on 2010-06-12
So I just signed up and got my account. Everything appears to be good in the ubuntu one preferences. It shows my account info and shows my local pc under devices. It says connect which I did, and it says everything is synced.

What I don't understand is what folders does it sync with? Is there a way to tell it which folders to sync with? I'd like to sync my music and picture folders, but I don't see a way both in my local ubuntu one preferences or in the web interface. I only see a way to select which computer to sync with.

Should it just automatically sync with your user folders like downloads, videos, music, pictures etc...? If so none of that has actually well synced.

I saw in some of the other threads people said to check on things to see if they are working by going to the terminal and typing 

```
u1sdtool -s
```

When I do that the output I get is...

```
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE
```

Little help please? Thanks in advance!

---

### Post by laoshi on 2010-06-12
Files that you put in the folder Ubuntu One in your Home folder are synchronized. But you can also select individual folders to sync by right clicking on them and press 'Synchronize on Ubuntu One' - then the files are put into the queue and sync'ing starts.
If you want to see what files are queued up, use ```
u1sdtool --waiting-content
```
If you want to see how many files are in the queue use ```
u1sdtool --waiting-content | wc -l
```
If you want to see which files are being uploaded/downloaded use ```
u1sdtool --current-transfers
```

---

