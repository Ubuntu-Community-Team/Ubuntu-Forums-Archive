---
title: "Not authenticated Metacity update?"
date: 2008-07-20
forum: Security
---

### Post by OrelEagle on 2008-07-20
Hello,

this morning the update manager wants to update metacity, libmetacity0 and metacity-common. Even if the list of changes isn't available, I decided to update. 

But I got a warning telling me that these updates can't be authenticated! This is a normal warning if you're installing software from non official repositories, but since metacity is in the default install, I have a few doubts…

Is it safe to accept this update?

---

### Post by brian_p on 2008-07-20
> **OrelEagle said:**
> 

But I got a warning telling me that these updates can't be authenticated! This is a normal warning if you're installing software from non official repositories, but since metacity is in the default install, I have a few doubts…

Is it safe to accept this update?

You should have the ubuntu-keyring package for the official repositories on your system. Check with your package manager and/or do

```
sudo apt-get -s install ubuntu-keyring 

```

---

### Post by OrelEagle on 2008-07-20
Thanks for your answer.

> **brian_p said:**
> You should have the ubuntu-keyring package for the official repositories on your system. 

I have this package on my system. How should it tell me if this update is safe?

I checked the package on [Ubuntu website]("http://packages.ubuntu.com/hardy/metacity"), and it seems that the update I'm receiving isn't mentioned there:

The lastest version is supposed to be 1:2.22.0-0ubuntu4
and I'm asked to update to 1:2.22.0-0ubuntu4.1

Any idea where this update come from?

---

### Post by brian_p on 2008-07-20
> **OrelEagle said:**
> 

I have this package on my system. How should it tell me if this update is safe?

It authenticates the update and you would not get the message you did get.

> I checked the package on [Ubuntu website]("http://packages.ubuntu.com/hardy/metacity"), and it seems that the update I'm receiving isn't mentioned there:

The lastest version is supposed to be 1:2.22.0-0ubuntu4
and I'm asked to update to 1:2.22.0-0ubuntu4.1

Any idea where this update come from?

The latest version is as you say. Where 1:2.22.0-0ubuntu4.1 is from I don't know. You could try commenting out all but the official Ubuntu repositories in /etc/apt/sources.list and see what happens when you update.

---

### Post by OrelEagle on 2008-07-20
> **brian_p said:**
> The latest version is as you say. Where 1:2.22.0-0ubuntu4.1 is from I don't know. You could try commenting out all but the official Ubuntu repositories in /etc/apt/sources.list and see what happens when you update.

Thanks a lot for the help. I found the reason: the update came from "gelir": [https://launchpad.net/~gilir/+archive](https://launchpad.net/~gilir/+archive)

I think I added this repo when I wanted to try some screenlets. Since I don't need it anymore I removed the repo and the update notification disappeared.

---

### Post by CatKiller on 2008-07-20
Yeah, I noticed that this morning too. It is from the Screenlets repository. From the [Screenlets FAQ]("http://screenlets.org/index.php/FAQ#Ubuntu_.28Edgy.2F_Feisty.2F_Gutsy.2F_Hardy.29"):

> Do NOT, NOT, NOT use any other packages from this repo, or you're in for surprises!

I don't know why they're pushing a Metacity update in this repo. It's possible that they've put in a bugfix to make Metacity work better with Screenlets, but since they don't say what they've changed it's rather hard to say.

I'd wanted to keep this repository in my sources.list to keep up with any updates to Screenlets (which has happened previously) but this update has made me reconsider.

Perhaps that was the purpose.

At least they don't use an authentication key, so it's obvious that it's an unofficial update.

---

