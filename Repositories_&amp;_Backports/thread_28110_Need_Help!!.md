---
title: "Need Help!!"
date: 2005-04-18
forum: Repositories &amp; Backports
---

### Post by Alighera on 2005-04-18
ok sorry if this question has been asked a lot but im new to the linux thing.....um i installed ubuntu and i accidentally overwrote my Win98 and everything else...so now that i know how to make partitions and such i need to format my hard drive so i can start fresh. how the hell do i format my hard drive through the terminal???

---

### Post by bored2k on 2005-04-18
You're trying to format a drive you're mounted on *O_O* ? 
I suggest GParted:
[http://ubuntuguide.org/#gparted](http://ubuntuguide.org/#gparted)

---

### Post by Alighera on 2005-04-18
ok im sorry let me rephrase the question.....how do i format my hard drive at all??? the only OS i have is ubuntu and i want to delete everything.....how?

---

### Post by mendicant on 2005-04-18
Do you have the live CD or just the install CD?  You can do it with either, but you may be happier using the live CD.

---

### Post by Alighera on 2005-04-18
well i have the install cd installed and i want to know how to format my whole hard drive and delete everything and start clean.....

---

### Post by mendicant on 2005-04-18
Well, it depends on exactly what you mean by start clean.  You can reinstall Ubuntu, you can install Windows again, you can install both.  What, exactly, do you want to do?

---

### Post by Alighera on 2005-04-18
i want to just completely clean the hard drive to where there is absolutly nothing and i want to use my windows boot floppy and my WIN98 cd and reinstall WIN98

---

### Post by mendicant on 2005-04-18
Well, then, you typically don't need to do anything--doesn't Windows just install, and take everything over?  At worst, you'd lose a GB or less on the swap space.  If you do insist on reformatting, you can use your Windows boot floppy (assuming it has fdisk).  Otherwise, you can load up the install CD, and go to the point where it partitions your hard drive.  Go to the console by hitting Alt-F2, then use fdisk, or cfdisk to repartition.  This version of fdisk is different from the Windows version.  You do:

% fdisk /dev/hda ## or whatever hard drive it is
Then use 'd' to delete all the partitions, then 'n' to add a new one.

At this point, you would have one partition, and Windows will be happy to take it over.

---

### Post by mendicant on 2005-04-18
Oh, and 'w' to write the partition table and exit.

---

### Post by Alighera on 2005-04-19
thanks thats all i was wondering.

---

