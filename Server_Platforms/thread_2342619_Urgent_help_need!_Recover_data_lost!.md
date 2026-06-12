---
title: "Urgent help need! Recover data lost!"
date: 2016-11-08
forum: Server Platforms
---

### Post by rhandy2 on 2016-11-08
Hi

I´m runnning ubuntu server with 2 drives for data . My mirror is gone. Only one year after I see that failure and I rebuild Raid. 

Problem Rewrite my paradox db files with old ones (2015). How I can recover?

---

### Post by mastablasta on 2016-11-08
raid is not a backup solution. it only guards against disk failure. not bad data or data being overwritten or anyhting like that.


if you overwrote your partition maybe photorec would be able to solve. someone that actually used it should advice on it.

---

### Post by rhandy2 on 2016-11-08
Thank you!

I will try photorec.

---

### Post by oldfred on 2016-11-08
I have had to use photorec. 
Better if testdisk's deeper search can find files as then they have full file names.

Photorec finds anything on drive that looks like a file by type, but then only file extension.
I had many .txt files and it found all of them, including every deleted version and parts of those same files. I had as many as 10 of same file, but no idea which was newest. Lots of grepping to find which .txt were the same and lots of file compares.

---

### Post by rhandy2 on 2016-11-08
problem is all files without name

---

