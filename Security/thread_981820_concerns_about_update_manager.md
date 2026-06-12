---
title: "concerns about update manager"
date: 2008-11-14
forum: Security
---

### Post by frazerr on 2008-11-14
Update Manager has just offered to update
login 
passwd

it seemed suspicios to me,

So I quit update manager, and checked in synaptic, and yes... it told me the updates came from ubuntu.

I was worried that some other repo was trying to overwrite them.  Does update manager only update things from the repo they were originally from?

It took me ages to think to check in synaptic,
and I think update manager should tell you more details.


where is it published what is being released when?  I tried searching for them...

---

### Post by hyper_ch on 2008-11-14
It updates from all sources you have given in the sources.list. So if you add 3rd party repos and if they have newer versions, it will upgrade.

---

### Post by Kevbert on 2008-11-14
The update information is detailed [[COLOR="Red"]here[/COLOR]]("http://www.ubuntu.com/usn/usn-670-1"). You can subscribe to these security bulletins [[COLOR="Red"]here[/COLOR]]("http://www.ubuntu.com/usn").

---

### Post by mssever on 2008-11-15
> **hyper_ch said:**
> It updates from all sources you have given in the sources.list. So if you add 3rd party repos and if they have newer versions, it will upgrade.

That's why it's so important to only add repos you trust.

A couple years ago, some guy was running a repo for his friends. He had some newer versions of certain programs than was available in the official repos, so after someone discovered that, people started posting his repo details around these forums and elsewhere and random people added his repo. He got sick of the added bandwidth his reps was suddenly using, so he made his own version of some standard package and included a snippet to change people's wallpaper to a warning against using third-party repos. People got mad, but he made his point. Unless you scrutinize every update (which is difficult in practice), anyone who runs any repo in your sources.list can take full control of your computer if they want to.

---

