---
title: "Allow Non-admin Users to Update System?"
date: 2008-08-13
forum: Security
---

### Post by Zenguy on 2008-08-13
Is suspect that this has a pretty simple answer, but it it possible to setup a system so a non-admin can allow system updates to be processed?

For example, if I setup a system for my kid, I don't want to have to log in on a regular basis and perform system updates. It would be best for them to happen automatically when my child logs in. I also do not want my kid to create new users, change internet settings, access other users files, etc. I want to restrict her access while allowing the system to keep itself updated.

"Software Sources" will allow installing security updates without confirmation, but it's not clear if it still requires sudo access to make this happen.

I've also thought about modifying the sudoers file and granting access to update manager only, but have not done any experimenting with this.

This must be a common problem for folks in an enterprise environment who have many users with non-admin rights to their machines, but need to keep their workstations updated. How is this typically managed?

Thanks.

---

### Post by brian_p on 2008-08-13
> **Zenguy said:**
> 

I've also thought about modifying the sudoers file and granting access to update manager only, but have not done any experimenting with this.

That's the route to take. Experiment away:

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by HermanAB on 2008-08-13
Hrrmmm...  Why? Most Linux problems are caused by updates.

There is a new release of Ubuntu every six months.  Consequently, messing with updates is simply a waste of time, especially since it can render your system unusable when something goes wrong.

Don't fix it if it ain't broke.  

Cheers,

Herman

---

### Post by brian_p on 2008-08-13
> **HermanAB said:**
> Hrrmmm...  Why? Most Linux problems are caused by updates.

There is a new release of Ubuntu every six months.  Consequently, messing with updates is simply a waste of time, especially since it can render your system unusable when something goes wrong.

Don't fix it if it ain't broke.  

Typing, as I am, on a machine running Debian Etch doesn't allow me to argue against this view! I think you would agree though that Zenguy could and should enable security updating.

---

### Post by atoponce on 2008-08-13
> **HermanAB said:**
> Hrrmmm...  Why? Most Linux problems are caused by updates.

There is a new release of Ubuntu every six months.  Consequently, messing with updates is simply a waste of time, especially since it can render your system unusable when something goes wrong.

Don't fix it if it ain't broke.  

Cheers,

Herman

So, an update that fixes a security vulnerability isn't worth the time?  Just wait 6 months, and maybe it will be fixed then?  Is that what I'm seeing?

---

### Post by cariboo on 2008-08-14
I guess it depends on your outlook, I see updates as fixing things that are broken, Look what the point release for hardy repaired. In a lot of cases hardy was almost unusable, if you didn't do all the updates and just waited for the release, at the end of six months you'd have a pretty broken system. Now it looks like security updates are being rolled into regular updates, so just waiting for security updates may may leave your system vulnerable.

Jim

---

