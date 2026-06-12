---
title: "Smashed Partiton"
date: 2008-04-16
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2008-04-16
Only a few minutes ago, I was using gparted to make my data "safer" in it's own partition via: Psychocats How-to on his web page.

Things weren't going well, but I got some help online via LiveCd. 

With help, eventually gparted showed a screen with an orange colored bar, moving back and forth and some words to the effect that /dev/sda1 was being moved to the left and shrunk.

Ten minutes or more went by and as there is NO PROGRESS BAR, or something to indicate the percentage of completion or in some way to give the end user an idea of what is happening.So, I canceled the operation, thinking something was stuck. I posted a question in the thread about how long it would take and was told between 2 hours and 6 to 7 hours. 

I think it would have been more prudent for GParted to make an assessment of how much time that operation was going to take and report it to the end user.

In all events, the CANCEL button should be de-activated once a process like partitioning starts, so that no damage is done. I've lost my OS, maybe my data, too.

---

### Post by prshah on 2008-04-16
> **Mark_in_Hollywood said:**
> 
Ten minutes or more went by and as there is NO PROGRESS BAR, or something to indicate the percentage of completion or in some way to give the end user an idea of what is happening.So, I canceled the operation, thinking something was stuck. I 

In all events, the CANCEL button should be de-activated once a process like partitioning starts, so that no damage is done. I've lost my OS, maybe my data, too.

Were the HDD activity lights on the tower not active? If so, then it _was_ really stuck. If they were active, then it was a bad move to cancel the operation.

The moving and shrinking operation cannot be canceled once started; gparted clearly gives a frightening warning about this, when you start the whole process, and when you attempt to cancel it as well.

---

### Post by Mark_in_Hollywood on 2008-04-16
I saw nothing that said DON'T CANCEL!!!

Why on earth is there a cancel button if it's not safe to do such? Or why isn't the cancel button greyed-out until it in a safe place to stop. Why isn't there a progress bar to help a newbie know where things are?

---

### Post by mips on 2008-04-16
I suppose for average joe this is a good complaint. For the eletist it would be common sense not to hit 'cancel'. Yes, 'cancel' should not be an option, maybe ctrl-c for the geeks.

---

### Post by popch on 2008-04-16
Did, in fact, anything happen at all to your partition? I can quite imagine that gparted was reckoning the number of moves necessary or something like that by way of preparing to move and resize your partition.

All you've told us so far is that you clicked on 'cancel' and that gparted stopped doing whatever it is that it was doing.

---

### Post by bryncoles on 2008-04-17
i saw a program called 'testdisk' recommended in another thread (i forget which one, sorry). its in the repo's though, has a nice online guide and claims to be able to recover lost partitions and the like. perhaps someone more knowledgable than me could comment on the possibility of using this program during a live-cd session to recover your partition, and any data that you may have lost?

---

### Post by Mark_in_Hollywood on 2008-04-25
I have my entire /dev/sda1 "recovered". By allowing GParted to perform it's "test" function, it has found the multiply-claimed blocks in inode: xxxxx and the 320 gig drive is all good.

I had four or five different posts regarding the problem over the course of several weeks. 

Thread Closed -- Ubuntu Success!!!

---

