---
title: "Does ubuntu collect user data?"
date: 2009-07-08
forum: Security
---

### Post by a11z on 2009-07-08
Does Ubuntu collect any user data by running a service in background or as a root?

Or,

Does Ubuntu use a service similar to "Problem Reporting Service" in XP to improve useage by collecting user data without or bypassing my will?

Thanks.

---

### Post by baizon on 2009-07-08
No, Ubuntu does not collect any information. The only information "it" collect is statistical information (i'm not sure bot i think its deactivated by default). But you can deactivate it with: System->Administration->Software Sources->Statistics. There remove "Submit statistical information". I thinks that's all.

---

### Post by cariboo on 2009-07-08
Ubuntu does have a crash reporting utility called apport. To learn more about apport have a look at [this]("https://wiki.ubuntu.com/Apport") wiki page.

---

### Post by juancarlospaco on 2009-07-10
Ubuntu collect Package data and Hardware Data on demand.
But not User data.

---

### Post by a11z on 2009-07-10
> **juancarlospaco said:**
> Ubuntu collect Package data and Hardware Data on demand.
But not User data.

Which utility/pkg is being used to collect "pkg data and hw data on demand"? Can it be removed from the Synaptic or Terminal?

---

### Post by cariboo on 2009-07-10
There is a program called popularity-contest, that has to be enabled either during installation or in Synaptic Package Manager-->Settings-->Statistics. The other utility is System-->Administration-->System Testing, it only sends information to Canonical if you run it.

---

### Post by juancarlospaco on 2009-07-10
> **cariboo907 said:**
>  synaptic package manager-->settings-->statistics. The other utility is system-->administration-->system testing, it only sends information to canonical if you run it.

**[size="3"]+1[/size]**

---

