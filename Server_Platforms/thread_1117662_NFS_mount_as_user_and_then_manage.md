---
title: "NFS mount as user and then manage"
date: 2009-04-06
forum: Server Platforms
---

### Post by any.linux12 on 2009-04-06
Hi guys!

This time I've a question that is realy wierd to me. It's like, I've a network with 6 user and I need at least 5 groups.

For example:

       Group1       Group2       Group3       Group4        Group5       
       user1        [COLOR="Lime"]user2[/COLOR]        [COLOR="DarkOrange"]user3[/COLOR]        [COLOR="Lime"]user2[/COLOR]         all
       [COLOR="Lime"]user2[/COLOR]                     [COLOR="DarkSlateBlue"]user4[/COLOR]        [COLOR="Blue"]user5[/COLOR]               
       [COLOR="Blue"]user5[/COLOR]                     [COLOR="Lime"]user2[/COLOR]        [COLOR="Yellow"]user6[/COLOR]

*sorry thats not allign and that I can't use names

well, lets go to the problem

I have a folder mounted in each laptop from our data server and first I want to mount on each laptop as a diferent userid (ex. 1015 until 1020)

Then (and this sounds impossible to me) I want to be able to create folders and files according to the user that is connected and the folder where he is. For example, if I'm the user2, I belong to the group, 1 2 3 4 and 5 (all), how can I say that if I create the folder inside a Group2 folder will have mod user2:group2 and if I create inside the group3 will have user2:group3

Please say something even if you don't know. Just to know if it is to hard impossible or easy.

Thanks in advance

---

### Post by any.linux12 on 2009-04-06
I'm trying to figure out other way but I can't find if it's possible to mount nfs partition with user id and group id. Is it???

Please say yes :p

---

