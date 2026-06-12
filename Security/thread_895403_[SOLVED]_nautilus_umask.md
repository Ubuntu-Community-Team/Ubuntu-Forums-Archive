---
title: "[SOLVED] nautilus umask???"
date: 2008-08-20
forum: Security
---

### Post by eotakos on 2008-08-20
Hello!

does anyone know which is the configuration file that controls the umask for nautilus? 


thanks in advance

---

### Post by Vivaldi Gloria on 2008-08-20
/etc/profile sets umask in default hardy. I don't know if there is a seperate umask for nautilus. Check gconf-editor.

---

### Post by eotakos on 2008-08-20
actually i'm looking for the equivalent of /etc/profile that applies only for personal preferences.

according to the ubuntu book i'm studying the file i'm looking for is supposed to be the   ~/.bash_profile   but this doesn't exist!

any further suggestions?

thanks for your answer again!

---

### Post by Vivaldi Gloria on 2008-08-20
See "Session-wide environment variables" here:

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

You can create ~/.bash_profile if it doesn't exist.

---

### Post by eotakos on 2008-08-20
I guess a disadvantage about being rookie is that if you want to learn about something you're not always lucky enough to be searching info for the right thing. Sure i searched the community docs, but i used umask as a keyword which returned useless results.

anyhow... you knew better than me what i wanted to learn about! :-) 
i guess that's why you are thanked in this forum more times than you have posted...

once again thank you - i appreciate your taking the time to answer

---

### Post by Vivaldi Gloria on 2008-08-20
> **eotakos said:**
> once again thank you - i appreciate your taking the time to answer

You're welcome mate.

---

