---
title: "development of c language"
date: 2008-09-03
forum: Server Platforms
---

### Post by dimi911 on 2008-09-03
Hi there . I am new at the linux community. So, here is a silly question.
They asked me to built a server but the programmer told me to pay attention that the development of c language is below 4 (my english are pure, but i hope you understand what i am talking about)  
So here is my question
Which version of ubuntu, shall i install ?
or ?
How i can find out which version is the development i am using , eg in my desktop 
Thanks in advance

---

### Post by ad_267 on 2008-09-03
Sorry I'm not quite sure what you mean. Do you mean what version of the GNU C Library are you using?

If you are using Ubuntu 8.04 then this is libc6 version 2.7-10ubuntu3 (Version 6)

To find that out I searched for the libc package and then looked at the version of libc6.

---

### Post by dimi911 on 2008-09-03
> **ad_267 said:**
> Sorry I'm not quite sure what you mean. Do you mean what version of the GNU C Library are you using?

If you are using Ubuntu 8.04 then this is libc6 version 2.7-10ubuntu3 (Version 6)

To find that out I searched for the libc package and then looked at the version of libc6.


Thank you for your answer. I asked him again and told me again "the development of c language "
I guess it is about GNU C Library
So, if i want to use an elder version of it ,shall i install a previous version of ubuntu, ? (dapper for instance )

---

### Post by beniwtv on 2008-09-03
I think you mean the C compiler, right?

Ubuntu AFAIK comes with version 4, but you can install version 3.3 afterwards (search for gcc-3.3 in Synaptic).

Cheers,

---

### Post by dimi911 on 2008-09-03
I wish i new for sure, but it dont think it can be something else
Do i have to remove the version 4. before installing  version 3 ?
And not in synaptic , of course, because it is a sever install 
apt get-remove ..... and so on .. 
Thank you

---

### Post by beniwtv on 2008-09-03
> **dimi911 said:**
> I wish i new for sure, but it dont think it can be something else
Do i have to remove the version 4. before installing  version 3 ?
And not in synaptic , of course, because it is a sever install 
apt get-remove ..... and so on .. 
Thank you

No, you can have both. And yes, it would be apt-get install <package name>, of course :D

Cheers,

---

