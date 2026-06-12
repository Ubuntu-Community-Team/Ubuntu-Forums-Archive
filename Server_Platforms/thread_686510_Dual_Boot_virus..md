---
title: "Dual Boot virus."
date: 2008-02-03
forum: Server Platforms
---

### Post by rockrocket on 2008-02-03
Hi guys, 

I was just curious,
I'm running a grub and have windows xp and ubuntu gutsy.
I just wanted to know, if you receive a windows virus in ubuntu can it travel into your windows partition or in the grub itself


Thanks

---

### Post by grimthegreat on 2008-02-03
i am running Ubuntu 7.10 feisty fawn, and windows vista (home premium) on a dual boot with partition and the such.  i'm running on a HP: DV9000 with nvidia 7600 and intel centrino duo.   But. although i have not encountered that problem i would like to know what others say about it.  it has been my understanding (even though i am VERY new to ubuntu) that there aren't ...hardly any (significant) viruses for linux/ubuntu.  my question would be if i get a virus on my windows, could it infect my ibuntu partition?   I'm here to learn and appreciate any and all feedback.  Thanks everyone.  


   - Grim

---

### Post by HermanAB on 2008-02-03
Binary Windows viruses won't execute on Linux, so they cannot travel anywhere. Macro viruses could run on Linux applications, if you happen to be running the same application on Linux as you would be running on Windows, which is unlikely.

So in general, no - don't worry about viruses - relax and enjoy it.  Linux has different problems to think about, forget about the Windows ones.

Most Linux problems can be avoided by using looooooong passwords.  Always use passwords in excess of 8 characters, since the common crack libraries typically go up to 8 characters.

Cheers,

Herman

---

### Post by lespaul_rentals on 2008-02-03
Good post HermanAB.  I would also like to add that the probability of a  virus spreading to the Windows partition is even more unlikely than getting infected by a Linux virus.  If for some reason someone made a virus that could infect both Linux and Windows without evolving, it would have to somehow mount your Windows partition and inject itself in there.  This would be extremely difficult.

---

### Post by grimthegreat on 2008-02-04
wow. thanks for all the help everyone. That makes me feel alot more at ease. i guess i need to get out of the windows mindset and into the linux frame of mind.. hehe. but what "other problems" would those be? and i'm really new, so could you perhaps show me how to structure a strong password??  like i've been taught in my classes (i'm currently working on my associates in computer forensics) that a strong 'structure' is like... if you take an object (or perhaps an animal or something, but nothing that's 'personal' to you) say, a dog named lucky    so you would go,  luckydog < then your favorite number or place>.  So with the dog,  you could do <luckydog8> or <luckycanine8> or any variation of the such.  What do you all think about that?

---

### Post by lespaul_rentals on 2008-02-04
> **grimthegreat said:**
> wow. thanks for all the help everyone. That makes me feel alot more at ease. i guess i need to get out of the windows mindset and into the linux frame of mind.. hehe. but what "other problems" would those be? and i'm really new, so could you perhaps show me how to structure a strong password??  like i've been taught in my classes (i'm currently working on my associates in computer forensics) that a strong 'structure' is like... if you take an object (or perhaps an animal or something, but nothing that's 'personal' to you) say, a dog named lucky    so you would go,  luckydog < then your favorite number or place>.  So with the dog,  you could do <luckydog8> or <luckycanine8> or any variation of the such.  What do you all think about that?

I don't really think that's a good idea TBH.  In my opinion, a good password should follow these rules:

Must be somewhat easy to remember, so that you don't forget it.

Should have about 2 or so special characters, pick a couple from the list of common ones: ! @ # $ % ^ & * ( ) - _ + = 

Include 2 or 3 numbers in there.

Make your password longer than 8 letters if possible.

Include 1 or 2 capital letters.

If the field will allow you to do so, include a space somewhere in the password.  Most people do not use the space character when bruteforcing a login, and dictionaries most of the time do not have spaces.

Bad password: "hellothere"
Decent password: "doofus13"
Good password: "Bart67+Tux"

---

