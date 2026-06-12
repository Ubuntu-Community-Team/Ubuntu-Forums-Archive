---
title: "Backup software? Multi Terabyte"
date: 2006-07-19
forum: Server Platforms
---

### Post by Bydgoszcz on 2006-07-19
I have read the the [How to create a terabyte array]("http://www.ubuntuforums.org/showthread.php?t=96896&page=4&highlight=parity+backup") but I am continuosly running into a problem of backup. Now I know you can use RAID-5 and have parity backup but you cant expand on RAID-5 (You can but only with HD's that are all the same size, so this is usless as HD's are getting cheaper and cheaper)

Now with LVM you can do grouping which allows you to add different size HD's and continuosly grow without having to rebuild an array. The problem now with LVM is the fact that if one frive fails the whole thing fails ( I thought only the one drive failed and the info on that one drive was gone, guess not)

So this is my question, I know there is backup stuff that mirrors and such but im not about to buy another Terabyte worth of HD's, but is there a backup solution that creates parity information on a seprate HD like RAID-5 does but is a software program that runs every other day and scans for files that have changed and just updates the parity info?

Thanks.

---

