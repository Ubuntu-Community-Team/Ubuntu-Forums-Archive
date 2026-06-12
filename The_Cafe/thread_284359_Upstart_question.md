---
title: "Upstart question"
date: 2006-10-25
forum: The Cafe
---

### Post by PatrickMay16 on 2006-10-25
Hey guys. I hear that in the Edgy release, the system V startup thing will be replaced with "upstart".

I just want to ask, with this change in place, will I still be able to do "/etc/init.d/*service* stop/start/whatever" to stop and start services as I need to? Or will it be different? Also, will Ubuntu include a tool for configuring Upstart, so that one can decide what services are started at boot, and so on?

I'd just like to know, because this is important for me. I'm making a tough desicion; should I install Edgy on my laptop when I get it (probably within one month's time), or just stick with Dapper?

I'd really appreciate your answers and discussion on this.

---

### Post by chaosgeisterchen on 2006-10-25
I cannot answer that but I cannot see why /etc/init.d should vanish by using upstart...

---

### Post by .t. on 2006-10-25
/etc/init.d still works perfectly.
update-rc.d is used to control what services are started. I don't know if that's changed, as I didn't know about it until about a week ago.

Use Edgy. It is far improved.

---

### Post by PatrickMay16 on 2006-10-25
> **chaosgeisterchen said:**
> I cannot answer that but I cannot see why /etc/init.d should vanish by using upstart...

I thought /etc/init.d as part of the system V init thing.

> 
/etc/init.d still works perfectly.
update-rc.d is used to control what services are started. I don't know if that's changed, as I didn't know about it until about a week ago.

Use Edgy. It is far improved.

Okay. Thanks, man. I'll use Edgy.

---

### Post by chaosgeisterchen on 2006-10-25
See .t. - it should work perfectly. I rather guess that /etc/init.d is part of the concrete act of booting whereas system v is only a script to handle all this.

---

### Post by John.Michael.Kane on 2006-10-25
PatrickMay16 The /etc/init.d folder is still used in edgy,and the commands you passed stop/start/services under dapper should carry over with out issue.

---

### Post by .t. on 2006-10-25
Upstart has a SysV compatibility thingy.

---

### Post by keybuk on 2006-10-26
> **PatrickMay16 said:**
> Hey guys. I hear that in the Edgy release, the system V startup thing will be replaced with "upstart".

I just want to ask, with this change in place, will I still be able to do "/etc/init.d/*service* stop/start/whatever" to stop and start services as I need to? Or will it be different? Also, will Ubuntu include a tool for configuring Upstart, so that one can decide what services are started at boot, and so on?

I'd just like to know, because this is important for me. I'm making a tough desicion; should I install Edgy on my laptop when I get it (probably within one month's time), or just stick with Dapper?

I'd really appreciate your answers and discussion on this.

Upstart replaces /sbin/init, which is the daemon itself.  The startup scripts themselves won't be replaced until feisty, so you can still use all your existing tools and knowledge.

---

