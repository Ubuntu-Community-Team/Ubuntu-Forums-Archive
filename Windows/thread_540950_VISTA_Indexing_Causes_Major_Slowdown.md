---
title: "VISTA Indexing Causes Major Slowdown"
date: 2007-09-02
forum: Windows
---

### Post by R_U_Q_R_U on 2007-09-02
This from Office Watch 12.23

 1. VISTA, OUTLOOK AND INDEXING
  An expanded version of this article is online at [http://news.office-watch.com?549]("http://news.office-watch.com/?549")
   
  Do you have trouble with Outlook 2007 and other programs running slowly under Windows Vista?   Opening Explorer windows, saving documents and even simple typing can make you wait and wait.  Looking around the internet, there are plenty of people with similar problems.
   
  We have some theories about the problem and some possible workarounds that might help you.
   
   
  2. WHAT'S THE PROBLEM?
  Our informal tests suggest the Vista indexing services grabs more and more resources (especially RAM) as the number of indexed items grows.   For most people the majority of indexed items are in Outlook.
  Vista runs fine when there's little to be indexed but once you put any kind of reasonable load on it, the indexing system starts bogging down the entire works.  Once you get a few hundred thousand indexable items, the Vista indexing service drags the entire system down.
   
  Adding RAM will speed things up a bit but, over time, the problem may return as the number of indexed items rises.
   
  Regardless of the indexing status, the operating system should not slow down to this degree.  Apologists for Microsoft have said that the problem is having 'too many' emails in Outlook - which is a typical 'blame the customer' response from Microsoft.  Outlook, by design, can cope with extremely large data files (ie PST / OST files of many gigabytes).  Microsoft went to the trouble of revamping the data file format to provide for much larger data files than are currently in use.
  Now the Vista indexing service is undoing that work.  Vista indexing was supposed to make finding things easier, instead it forces you to reduce your Outlook data to suit the limitations of the operating system.
   
  Other desktop search products like Google Desktop Search and Copernic Desktop Search can index large quantities of data without slow-down on a Vista computer.   You would expect Vista indexing, as part of the operating system, to be able to perform better than third-party products - not worse...

---

### Post by angryfirelord on 2007-09-02
This is a good article for Vista users:
[http://www.extremetech.com/article2/0,1697,2110595,00.asp]("http://www.extremetech.com/article2/0,1697,2110595,00.asp")

Would using Thunderbird allow someone to get around this problem?

---

### Post by salsafyren on 2007-09-02
Please stop posting this crap in a Linux forum.

Even though this part of the forum is for off-topic subjects, Vista drivel  simply is too much. Go post it elsewhere.

---

### Post by BuffaloX on 2007-09-02
I hate it when people whine when beta software is not working. ](*,)

---

### Post by insane_alien on 2007-09-03
> **salsafyren said:**
> Please stop posting this crap in a Linux forum.

Even though this part of the forum is for off-topic subjects, Vista drivel  simply is too much. Go post it elsewhere.

well, this is th 'windows discussions' section. an with all due respect, this is not your forum. its up to the admin to decide what is allowed.

---

### Post by Sandsound on 2007-09-03
> **BuffaloX said:**
> I hate it when people whine when beta software is not working. ](*,)

It's not even in the repro's

$apt-get vista
give me this error:
E: Invalid operation vista

Maybe I'm doing it wrong ?

;-)

---

### Post by Epilonsama on 2007-09-03
Is there a way to at least turn off Vista Indexing?

---

### Post by Depressed Man on 2007-09-03
Yes, [http://4sysops.com/?p=457](http://4sysops.com/?p=457)

I kinda wish there was a battery option though. Not sure if there is (I was googling for one earlier). I don't mind the indexing when my laptop is on AC power. But on battery it's deadly to the battery life. Which is why I have Copernic Desktop Search stop when on battery power.

---

### Post by BuffaloX on 2007-09-03
> **insane_alien said:**
> well, this is th 'windows discussions' section. an with all due respect, this is not your forum. its up to the admin to decide what is allowed.

When I replied to this, it was in the Cafe....

> **Sandsound said:**
> It's not even in the repro's

$apt-get vista
give me this error:
E: Invalid operation vista

Maybe I'm doing it wrong ?

;-)

Try "sudo apt -get install vista" but I think you need the "restricted" repository. :lolflag:

---

### Post by Frak on 2007-09-03
> **Depressed Man said:**
> Yes, [http://4sysops.com/?p=457](http://4sysops.com/?p=457)

I kinda wish there was a battery option though. Not sure if there is (I was googling for one earlier). I don't mind the indexing when my laptop is on AC power. But on battery it's deadly to the battery life. Which is why I have Copernic Desktop Search stop when on battery power.
Thanks for the link, very helpful.

I've been wanting to turn it off for awhile.

---

