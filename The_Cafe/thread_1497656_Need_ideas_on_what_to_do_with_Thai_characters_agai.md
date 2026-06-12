---
title: "Need ideas on what to do with Thai characters against mysql"
date: 2010-05-30
forum: The Cafe
---

### Post by kenweill on 2010-05-30
Here's the problem (of someone I knew online): I just want to help him with his problem.

> 
I (accidentally) changed my password to a string that uses Thai characters.

the first few characters of the password are fine (and recognized by the system) but the last character poses a problem.

The last character is in the Thai language and is: &#3637;
The password reminder feature tells me my password but changes the last character to: &#65533;&#65533; , which does not work

I've tried several different combinations and am 100% certain the problem is with the last character (as I've created a few other test accounts, and that character is the only one that is not recognized)

The site is PHP and appears to be a MySQL db.

Technical support on the website is slow to respond to my specific problem. I need to access my account ASAP.


The problem needs to be solved without brute force hack or other methods that would frustrate the site's admin.

I just need a few ideas of what I have to do to help him with his problem.

---

### Post by McRat on 2010-05-30
> **kenweill said:**
> Here's the problem (of someone I knew online): I just want to help him with his problem.



The problem needs to be solved without brute force hack or other methods that would frustrate the site's admin.

I just need a few ideas of what I have to do to help him with his problem.

Might try this.  Go into any word processor that supports extended character sets.  Type the password in using the correct chars, and copy then paste the string into the password box.

On Windows computers, you can hold down the ALT key and type the 3 digit code for chars that aren't typable as well.

---

### Post by kenweill on 2010-05-30
Thank you. I will your idea.

@update
can't find the 3 digit codes for these characters :(

@update
found it in openoffice writer. :)

---

