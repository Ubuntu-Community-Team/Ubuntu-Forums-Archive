---
title: "After installing SELinux-policy-default,why can't I use my Ubuntu?"
date: 2006-09-03
forum: Server Platforms
---

### Post by kiddyliu on 2006-09-03
I have installed SELinux-policy-default and the pre-depending packages it needed successfully on my machine.
$sudo sestatus
SELinux status:                 enabled
SELinuxfs mount:                /selinux
Current mode:                   permissive
Mode from config file:          enforcing
Policy version:                 20
Policy from config file:        .
Then I logout.But when I relogin,the terminal reads "Would you like to enter a security context?[y]",I typed "n",then it logouted automatically.I typed "y",but I just didn't known how to enter the correct security context.I want got some documents from the [www.nsa.gov/selinux,but](www.nsa.gov/selinux,but) all of my classmates' machines can't connect to that website. By the way,I'm a Chinese college student(so maybe my English writing skills is a little weak).Now what should I do?I want to user my Ubuntu with selinux.
Thanks a lot.

---

