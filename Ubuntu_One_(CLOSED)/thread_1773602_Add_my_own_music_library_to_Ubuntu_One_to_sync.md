---
title: "Add my own music library to Ubuntu One to sync ?"
date: 2011-06-02
forum: Ubuntu One (CLOSED)
---

### Post by shelbydz on 2011-06-02
Hi All, 

I just signed up for a 30 day trial of Ubuntu One mobile. I have music all over the place and thought that this would help me sync it on my phone. I shared my Music folder on my laptop, but all it was upload the file structure (not the music) to the server. 

How do I get Ubuntu Music to sync my existing collection?

---

### Post by duanedesign on 2011-06-06
I keep all my music in my ~/Music folder. If you set that folder to sync it will be available to use via the streaming music service. If all you are are seeing is the folders that might mean it is only partially done syncing. Ubuntu One syncs metadata(folders) first then the files. If after awhile you still notice the music not show up let me know. You can see how many files are in the queue to sync by running the following command in a Terminal.

```
u1sdtool --waiting | wc -l

```
This will give you the number of files left to sync.

thank you,
duanedesign

---

