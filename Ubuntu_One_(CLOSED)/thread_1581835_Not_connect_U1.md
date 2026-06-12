---
title: "Not connect U1"
date: 2010-09-25
forum: Ubuntu One (CLOSED)
---

### Post by madzombie on 2010-09-25
Hi,
I can't Ubuntu One. I have a account on Ubuntu One.
But, I run u1 tool and click Devices tab. 
Only write < Local Machine > not show my computer name. 
I try connection as press connect button. 
But, status show Not connect.
I select Account tab and press "Manage Account" button after than running firefox. I login on the page. 
But it doesn't nothing happened.

How can i do ? 

Thanks.

---

### Post by Matt3223 on 2010-09-26
I had a similar problem with Lucid the last couple weeks.

Steps two and three from [this post](http://ubuntuforums.org/showpost.php?p=9853143&postcount=2) helped me out.

> 
2. Open Seahorse (System -> Preferences -> Password and Encryption keys) and delete the Ubuntu One Token.

3. Then open Ubuntu One Preferences (System -> Preferences -> Ubuntu One). You should be prompted to add your computer. this new token should work.

thank you,
duanedesign


Except, "Password and Encryption Keys" wasn't located under System >> Preferences for me. I had to alt+F2 "seahorse" to delete the Ubuntu One Token.

---

### Post by duanedesign on 2010-09-26
> **Matt3223 said:**
> 
Except, "Password and Encryption Keys" wasn't located under System >> Preferences for me. I had to alt+F2 "seahorse" to delete the Ubuntu One Token.

I think I will revise my canned response to include the Alt+ f2 "seahorse" directions. Seahorse has been moved around in the last couple of releases. For Maverick it is in System > Preferences, for Lucid it is Applications > Accessories. The using of Alt+f2 is a nice way to provide instructions that will work for all.

thank you,
duanedesign

---

### Post by lfeuerbach on 2010-10-01
I followed these instructions, and not only was there no ubuntu one password in seahorse, I'm still having the same problem.

Cannot connect my desktop, and I am not getting the prompt to add my computer.

No wonder Linux gets nowhere.

---

