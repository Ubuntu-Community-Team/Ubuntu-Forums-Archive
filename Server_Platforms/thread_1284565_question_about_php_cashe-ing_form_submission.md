---
title: "question about php cashe-ing form submission"
date: 2009-10-06
forum: Server Platforms
---

### Post by rhythmiccycle on 2009-10-06
i'm hosting an online math homework site using ubuntu 9 desktop

answers are endeared using a form using text boxes (and sometimes radio buttons) the form is send to anther php page that check the answers, stores the scores on a database, and let the user know how they did.

the question have random numbers in them, I want the students to do the problem again with different numbers, until they get it right.

after they get their score they can go back, and new problems are given (because of the random numbers coming from the php)

the problem is,
sometimes when the browser goes back to question page, from the check answer page, the number don't change. The page is cashed by the user's browser i think. 

i want the page to make new random numbers every time the browser goes back to the page.

I can't figure out the cause, I've seen it refresh and not refresh on the same browser when I was working on it.

What caused a page to refresh vs cashe?
is there a way to make it alway refresh?
or at least a way to not let un-refreshed pages to give scores to the data base?

---

### Post by scragar on 2009-10-06
I think the easiest way would be to give the page an expires date, or a random query string every time you link to it:
```
<a href="test.php?<?php echo time(); ?>">Take the test</a>
```

[php]header("Cache-Control: no-cache, must-revalidate");
// tell browsers to always request the page

header("Expires: Thu, 1 Jan 1970 00:00:01 GMT");
// anticipate some browsers ignoring that and give a really old expires date as well, unix epoch is a common choice.
[/php]

---

### Post by rhythmiccycle on 2009-10-06
thanks for the idea.

let me get this straight:

that would be like putting a time limit on each page? 
What if a student needs a long time to solve it?

---

### Post by rhythmiccycle on 2009-10-06
> **scragar said:**
> 
[php]header("Cache-Control: no-cache, must-revalidate");
// tell browsers to always request the page
[/php]


if i put the code at the top of the page, it will make it if a user hits the back button on their browser the page must refresh?

---

### Post by scragar on 2009-10-07
That code removes the cache from the pages, if the user refreshes the page or clicks back it must reload the page.

---

### Post by rhythmiccycle on 2009-10-08
i put the code at the top, everything seems to be working, I just need to test it out from different computers, I'll let you know how it goes.

---

### Post by rhythmiccycle on 2009-10-15
header("Cache-Control: no-cache, must-revalidate"); 

did not work.

I used Internet Explorer and when I go back the page does not refresh.

I sort of fixed the problem by clearing the session data that stores the answers on the check answer page. so when a student tried to go back with out refreshing, all answers are considered wrong. 


I would still like to get the "must-revalidate" to work. My life would be alot easer if I could find a code like that that actually works

---

