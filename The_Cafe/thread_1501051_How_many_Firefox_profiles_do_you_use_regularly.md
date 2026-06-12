---
title: "How many Firefox profiles do you use regularly?"
date: 2010-06-03
forum: The Cafe
---

### Post by lovinglinux on 2010-06-03
Firefox profiles are great. They can be used much like the Activities concept in KDE 4.4 and Gnome 3 Shell. What I mean is you can have specific profiles for a specific tasks, each one with it's own set of add-ons, preferences, bookmarks and so on. But they lack some sort of integration between them. You can't switch back and forth between profiles without leaving the interface. For example, Firefox allows you to open a page in a new window or a new tab, but doesn't allow you to open it with a new profile. Also, there isn't an option for example to save a bookmark on another profile, although you can sync bookmarks with Fire Sync (soon to become a default feature). Additionally, to start a new profile you need to add the **-no-remote** and the **-P** switches to your launcher.

So I was thinking about creating a new extension that would allow those things. But before I start, I would like to know if this would be useful to other users as well.

So please vote. Poll is up.

---

### Post by kostkon on 2010-06-03
Just one.

---

### Post by Simian Man on 2010-06-03
I've never heard of this before...so one.  It doesn't sound that useful to me, except for maybe having a secret pr0n profile.

---

### Post by lovinglinux on 2010-06-03
> **Simian Man said:**
> I've never heard of this before...so one.  It doesn't sound that useful to me, except for maybe having a secret pr0n profile.

:)

See [Profiles](http://firefox-tutorials.blogspot.com/2010/05/profiles.html) section of my tutorial.

---

### Post by Legendary_Bibo on 2010-06-03
meh. Setting up profiles is too much of a hassle. I leave my bookmarks menu open, it's there, I like it, I have the right theme for my Okami themed Ubuntu, and I don't care too much for add-ons. None of them look useful to me.

---

### Post by Sam on 2010-06-03
I use one profile for personal usage and one other for web development. I like to keep work/personal separate.

---

### Post by sdowney717 on 2010-06-03
I suppose you could simply switch toggle users and get a different profile.

---

### Post by lovinglinux on 2010-06-03
> **Sam said:**
> I use one profile for personal usage and one other for web development. I like to keep work/personal separate.

I guess most users don't use more than one, just developers do. I also have two profile, one for personal use and another for extension development.

I tried to use a third profile for multimedia stuff, but without such integration is a pita. The development profile works because it has everything I need for development, but a multimedia profile would be constantly used while using my default profile.

---

### Post by lovinglinux on 2010-06-03
> **sdowney717 said:**
> I suppose you could simply switch toggle users and get a different profile.

That works if you will spend a couple of hours using the same profile, but if you need to go back and forth multiple times that is a hassle.

---

### Post by undecim on 2010-06-04
I would definitely use profiles more if they were more convenient. Even if there was just an extension to launch new profile windows from a GUI menu, that would be great (there may or may not be one like this already; I haven't looked)

Those features you described look great. I would love to see an extension that does all that.

EDIT: Random observation: This thread's number is a palindrome.

---

### Post by lovinglinux on 2010-06-04
> **undecim said:**
> I would definitely use profiles more if they were more convenient. Even if there was just an extension to launch new profile windows from a GUI menu, that would be great (there may or may not be one like this already; I haven't looked).

I looked, but not much. I couldn't find any, but I will look further to avoid reinventing the wheel.

> **undecim said:**
> EDIT: Random observation: This thread's number is a palindrome.

Wow. This must be a glitch in the Matrix. I guess I need to follow the white rabbit now, no matter how deep the rabbit-hole goes :)

---

### Post by lovinglinux on 2010-06-04
Firefox extension gallery is really amazing. There is an extension for that too. :oops: 

I haven't tested yet, but I will do now. Nevertheless, it seems the extension haven't been updated for a while.

See [Profile Manager and Synchronizer](https://addons.mozilla.org/en-US/firefox/addon/9452/).

EDIT: it works like a charm, even on Firefox 3.6.5pre and is exactly what I was thinking.

---

### Post by sdowney717 on 2010-06-04
it claims its not compatible for me.

---

### Post by nerdtron on 2010-06-04
I usually use one profile but please if you can make an addon that can make switching profiles easier, that would be great!
I NEED IT! Thank you very much. :)

---

### Post by lovinglinux on 2010-06-04
> **sdowney717 said:**
> it claims its not compatible for me.

Install [Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/")

> **nerdtron said:**
> I usually use one profile but please if you can make an addon that can make switching profiles easier, that would be great!
I NEED IT! Thank you very much. :)

See post [#12]("http://ubuntuforums.org/showpost.php?p=9408235&postcount=12")

---

### Post by sdowney717 on 2010-06-04
strangely, I installed that add on and then installed the profile one and now it works, even though it says it is not compatible.

Screenshot shows a new profile with the message

---

### Post by lovinglinux on 2010-06-04
> **sdowney717 said:**
> strangely, I installed that add on and then installed the profile one and now it works, even though it says it is not compatible.

Screenshot shows a new profile with the message

Because Add-ons Compatibility Reporter allows you to do that. It disables the extensions compatibility check and allows you to report if the extension still works with your FF version or not. Open the add-ons manager and you will see more options for extensions actions now.

---

### Post by wojox on 2010-06-04
I voted uno. I never really understood or could grasp the meaning of profiles.

---

### Post by lovinglinux on 2010-06-04
> **wojox said:**
> I voted uno. I never really understood or could grasp the meaning of profiles.

Profiles can be used in several ways. For example:

[LIST]
[*]if you have only one OS user account (you know how Windows users are), but share the computer with other users, then you can create a profile for each user. 
[*]you can also use profiles to test extensions you like before actually installing them on your default profile. This way you can void errors and profile pollution by an extension you don't know you will keep.
[*]you can use to keep business and personal stuff separated.
[/LIST]

There are other scenarios tho. If you are an extension junky like me, you can improve Firefox performance, by putting extensions you don't use very frequently on a separate profile. 

I have not only extensions that are specific designed for development (debuggers, editors and such) but also Firefox preferences that are not good for performance, but are good for development. For example in my development profile xul files are not saved in the cache. So every time I start Firefox it loads all extensions files, otherwise I wouldn't be capable of viewing some extension changes, due to the cached version. On the other hand, my default profile do not have the same setting, because this slows down Firefox start.

---

