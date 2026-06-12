---
title: "Updating to 12.04 from 11.10"
date: 2012-03-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Spewed on 2012-03-23
Is there a way that I can upgrade to Ubuntu 12.04 LTS without losing any of my programs, install themes or files that I have on Ubuntu 11.10? I basically want them to just transfer over. I know that it is in beta status and that I am not guaranteed anything as far as losing data, or carrying over files, etc as it's in beta stage, but is there a routine, or process that one would ordinarily follow when attempting to do this? 

Has anyone succeeded in upgrading without losing any data?

I know about the sudo update-manager -d command, but will that result in a loss of data?

---

### Post by wildmanne39 on 2012-03-23
Hi, 12.04 is still in testing it would not be wise to install it without having another production machine to use.
Thanks

---

### Post by Spewed on 2012-03-23
> **wildmanne39 said:**
> Hi, 12.04 is still in testing it would not be wise to install it without having another production machine to use.
Thanks

I'm well aware of that, and I'm afraid that's not the question I asked. Thanks for your consideration though. :)

---

### Post by uRock on 2012-03-23
Moved to Ubuntu+1 where all discussions about testing are discussed.> **Spewed said:**
> I know about the sudo update-manager -d command, but will that result in a loss of data?
Upgrading always runs the risk of losing data, but the command you listed is the only way I know of. Beta testing itself runs a risk of data loss.

---

### Post by wildmanne39 on 2012-03-23
Hi, it would be good to back up your data to an external source before proceeding just in case.
Thanks

---

### Post by kansasnoob on 2012-03-24
> **Spewed said:**
> Is there a way that I can upgrade to Ubuntu 12.04 LTS without losing any of my programs, install themes or files that I have on Ubuntu 11.10? I basically want them to just transfer over. I know that it is in beta status and that I am not guaranteed anything as far as losing data, or carrying over files, etc as it's in beta stage, but is there a routine, or process that one would ordinarily follow when attempting to do this? 

Has anyone succeeded in upgrading without losing any data?

I know about the sudo update-manager -d command, but will that result in a loss of data?

I'd strongly recommend waiting until Beta 2 is released on March 29th, then be sure to read the release notes - particularly ***known issues***!

That said also use exactly the correct upgrade procedure! You said "sudo update-manager -d" but that's not quite correct. Please do NOT use sudo, rather just:

```
update-manager -d
```

Then if you follow the gui instructions that will get you to the last milestone. So if you run that right now you'll get 12.04 Beta 1 and you'd have to tackle a ton of updates.

If you wanted to get the very latest "daily build" you'd want to run:

```
update-manager -d -c
```

Regardless some risk is always involved when running release upgrades. The data you don't back up will inevitably be the data you lose ;)

---

