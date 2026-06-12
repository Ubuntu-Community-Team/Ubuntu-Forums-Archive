---
title: "Adding a Windows PC to Ubuntu Domain"
date: 2013-01-28
forum: Server Platforms
---

### Post by chrisguk on 2013-01-28
I have a server that I configured with DNS, everything from the buntu aspect works fine with BIND9 etc.  All my other clients are able to join the domain no problem.

I have searched the internet and find countless examples of adding a buntu machine to a Windows AD domain but not the other way around.

So!

How can I add a windows based OS to my buntu server domain?

---

### Post by lingpanda on 2013-01-28
> **chrisguk said:**
> I have a server that I configured with DNS, everything from the buntu aspect works fine with BIND9 etc.  All my other clients are able to join the domain no problem.



I have searched the internet and find countless examples of adding a buntu machine to a Windows AD domain but not the other way around.



So!



How can I add a windows based OS to my buntu server domain?



The same way you would a windows domain. [http://windows.microsoft.com/en-US/windows7/Connect-your-computer-to-a-domain](http://windows.microsoft.com/en-US/windows7/Connect-your-computer-to-a-domain)

---

### Post by chrisguk on 2013-01-28
I am familiar with that method but each time I do it I get an active directory error message.  Is there anything special I need to do?

---

### Post by lingpanda on 2013-01-28
> **chrisguk said:**
> I am familiar with that method but each time I do it I get an active directory error message.  Is there anything special I need to do?







No nothing special. What is the error message? Make sure you are using a user with rights to join a computer to the domain.

---

### Post by chrisguk on 2013-01-28
I'm away from the pc at the moment, I will post the error in the morning if that's ok? ;)

---

### Post by offgridguy on 2013-01-28
It can be a problem as windows doesn't like to recognize linux, vice versa  no
problem.  Some info regarding compatibility here.

[http://ask-leo.com/does_linux_have_a_role_in_the_home.html](http://ask-leo.com/does_linux_have_a_role_in_the_home.html)

---

