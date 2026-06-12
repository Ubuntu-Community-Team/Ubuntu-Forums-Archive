---
title: "Short passcode ONLY for lock screen"
date: 2018-12-20
forum: Security
---

### Post by namangupta on 2018-12-20
I’ve been using windows for a long time and it’s really hectic for me to type in my whole password again and again at the lock screen, please instruct me how to change it ONLY for the lock screen to a 4-6 digit passcode. Since I’m new to this, please tell me the exact command line statements and please do not forward already posted answers, I’ve seen everythimg and none of it has been straight forward.

---

### Post by TheFu on 2018-12-20
The lock screen is tied to the Unix password.
You can disable the lock screen or have a longer delay before it locks, but I've never seen any method to skip entering a password tied to the userid.

But I could be wrong.  I am just an egg too.

---

### Post by namangupta on 2019-01-01
I found a solution that worked for me at [https://askubuntu.com/questions/180402/how-to-set-a-short-password-on-ubuntu#comment522410_180428](https://askubuntu.com/questions/180402/how-to-set-a-short-password-on-ubuntu#comment522410_180428) 

I hope it works for you as well!

---

### Post by deadflowr on 2019-01-01
> **namangupta said:**
> I found a solution that worked for me at [https://askubuntu.com/questions/180402/how-to-set-a-short-password-on-ubuntu#comment522410_180428](https://askubuntu.com/questions/180402/how-to-set-a-short-password-on-ubuntu#comment522410_180428) 

I hope it works for you as well!

It's your thread, you can mark it as solved then:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by TheFu on 2019-01-01
> **namangupta said:**
> I found a solution that worked for me at [https://askubuntu.com/questions/180402/how-to-set-a-short-password-on-ubuntu#comment522410_180428](https://askubuntu.com/questions/180402/how-to-set-a-short-password-on-ubuntu#comment522410_180428) 

I hope it works for you as well!

Those solutions don't actually do what the OP requests.  The full Linux password is what that link handles, not just the screen lock.

But if it works, fine.

Having a short password can be a very dangerous thing for a networked computer.  Remote access is possible and a weak/short password is a huge liability for attacks on the network.  But is it possible to use firewall rules to restrict access to the system to mitigate most of those attacks.

---

### Post by pending... on 2019-01-06
Changing the screenlocker password from the UNIX one to another one is probably is good security feature, as long as it is not too easy to find out. At least, something as long as your UNIX password is better, even if it is easier or handier to type. The lesser you have to type your UNIX password, the more secure you'll be.

---

