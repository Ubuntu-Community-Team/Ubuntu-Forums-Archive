---
title: "Joomla 1.5.1 Permissions Problem"
date: 2008-02-28
forum: Server Platforms
---

### Post by DirtyMonkey on 2008-02-28
Hi,

I am new to using Linux and hope someone can help me solve the following problem.

I have Jooma! 1.5.1 installed on a VPS running Ubuntu 6.06 LTS (Drake), Plesk 8.3 and have successfully updated to Apache2 and PHP 5.1.2.

I wish to avoid chmod 0777 to enable Joomla! installs as outlined at:

[http://help.joomla.org/component/option,com_easyfaq/task,view/id,99/Itemid,268/]("http://help.joomla.org/component/option,com_easyfaq/task,view/id,99/Itemid,268/")

However either I don't seem to have an 'Apache user.conf' file or I'm looking in the wrong place. I am assuming that this method is compatible with Apache2 and PHP 5.1.2...?

Can anyone tell me how to achieve this or suggest a better alternative.

Thanks in advance, DM.

---

### Post by DirtyMonkey on 2008-02-28
Upon further invistigation it seems the solution I mentioned above is not very secure and so not recommended.

I have found an alternative solution but unsure if it is compatable with my system or how to configure sussessfully:

[http://forum.joomla.org/viewtopic.php?f=267&t=210179&p=983626&hilit=proper+permissions+how+do+i+set+proper+permissions&sid=cc579673d0d489332a2e8d9c7556bea2#p983626]("http://forum.joomla.org/viewtopic.php?f=267&t=210179&p=983626&hilit=proper+permissions+how+do+i+set+proper+permissions&sid=cc579673d0d489332a2e8d9c7556bea2#p983626")

Any suggestions?

DM.

---

