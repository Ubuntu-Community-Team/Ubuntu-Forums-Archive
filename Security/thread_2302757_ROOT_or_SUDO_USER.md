---
title: "ROOT or SUDO USER"
date: 2015-11-13
forum: Security
---

### Post by IONx64 on 2015-11-13
Hello dear sirs,

I need your advices and help to be secure on Ubuntu, i am newbie in linux world. I am log   in  as admin, but i was told that it is more secure to be log in as sudo user, is that true? if true please help me how to become a sudo user or what to for my security? thanks in advanced.

---

### Post by Lars Noodén on 2015-11-13
[Logging in graphically as root is unsafe](http://ubuntuforums.org/showthread.php?t=1486138) and should be avoided at all costs.  Using the terminal as root is less problematic, but the recommended practice around here is to use sudo after having logged in as an unprivileged user.  That limits the potential damage a little.  What sudo can and can't do is outlined in [/etc/sudoers](http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html).  Ubuntu's default is a bit loose, it is set to allow any user in the group 'sudo' to do anything.  However, the sudo is designed for better granularity. You can set it to accept only certain programs and/or certain options for those programs.  There area lot of guides on the net, but most are poor and many wrong.  If you have a chance, take a look at Michael W Lucas' book *Sudo Mastery* for detailed coverage of capabilities and examples.  

That said, which tasks do you wish to accomplish?  That will determine how you set up /etc/sudoers

---

### Post by coffeecat on 2015-11-13
> **IONx64 said:**
> i am newbie in linux world. I am log   in  as admin, but i was told that it is more secure to be log in as sudo user, is that true? if true please help me how to become a sudo user or what to for my security?

If you are a newcomer to Ubuntu, then I think you are trying to make things more complicated than need be, or whoever told you to "login as a sudo user" (whatever that means) is either misadvising you, or you perhaps misunderstood.

The Ubuntu security model is easy to understand for a beginner. Simply put, when you install Ubuntu (or one of the official variants) the first created user account has sudo rights for when they are needed. It is the admin account. Most of the time you can use this account for ordinary unprivileged stuff such as emailing, browsing the internet, listening to music, and so on. When you need elevated rights, such as installing software or prefacing terminal commands with sudo, you simply use your login password.

---

### Post by Skaperen on 2015-11-13
the meaning of "a sudo user" should be a non-privileged user that is allowed to run sudo. on my puter "admin" is allowed to run sudo and i am even safer by accessing ubuntu forums under _another user not even allowed to run sudo_.

---

### Post by IONx64 on 2015-11-13
Thanks for your support dear friends. 

Dear Lars Nooden can u give me link of Michael W Lucas' book *Sudo Mastery? thanks*

---

### Post by Lars Noodén on 2015-11-13
Sure.

[https://www.tiltedwindmillpress.com/?product=sudo-mastery-user-access-control-for-everyone](https://www.tiltedwindmillpress.com/?product=sudo-mastery-user-access-control-for-everyone)
[https://www.michaelwlucas.com/nonfiction/sudo-mastery](https://www.michaelwlucas.com/nonfiction/sudo-mastery)

---

### Post by IONx64 on 2015-11-13
> **Lars Noodén said:**
> Sure.

[https://www.tiltedwindmillpress.com/?product=sudo-mastery-user-access-control-for-everyone](https://www.tiltedwindmillpress.com/?product=sudo-mastery-user-access-control-for-everyone)
[https://www.michaelwlucas.com/nonfiction/sudo-mastery](https://www.michaelwlucas.com/nonfiction/sudo-mastery)

Thanks for links sir.

---

