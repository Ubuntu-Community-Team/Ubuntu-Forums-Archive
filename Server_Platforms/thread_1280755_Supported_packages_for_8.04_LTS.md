---
title: "Supported packages for 8.04 LTS?"
date: 2009-10-02
forum: Server Platforms
---

### Post by jptech on 2009-10-02
I really like the idea of the LTS releases of Ubuntu, but I'm finding it terribly difficult to find a decent explanation of which packages are supported long term and which aren't.  I'd like to offer some constructive criticism on the subject.

To begin with, I'm talking about version 8.04 LTS.

I assume the Ubuntu Server Guide ([https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)) is a reasonable starting point for information.  I've also look at the server FAQ ([https://help.ubuntu.com/community/ServerFaq#What%20(packages/repositories)%20are%20maintained%20(supported)?]("https://help.ubuntu.com/community/ServerFaq#What%20%28packages/repositories%29%20are%20maintained%20%28supported%29?")).  Both say that packages in 'main' are supported while packages in 'universe' and 'multiverse' aren't.  What about 'restricted'?

Also, the server guide refers to 'universe' and 'multiverse' as repositories while the documentation on repositories ([https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)) properly identifies them as components of a repository.

I haven't been able to find any decent information regarding which repositories are actually supported long term; hardy? hardy-updates? hardy-security? hardy-backports.  I think I have it figured out:

  Supported
hardy main restricted
hardy-updates main restricted
hardy-security main restricted

  Not Supported
hardy universe multiverse
hardy-updates universe multiverse
hardy-security universe multiverse
hardy-backports main restricted universe multiverse

However, cobbling that information together took the better part of my morning and it shouldn't have.  It's 9 lines of information that could easily be included in sources.list.

Speaking of sources.list, I was extremely displeased to see unsupported repository components enabled by default.  The server guide warns about it ([https://help.ubuntu.com/8.04/serverguide/C/extra-repositories.html](https://help.ubuntu.com/8.04/serverguide/C/extra-repositories.html)), but they shouldn't be enabled by default if they're not supported (IMO).

May I suggest that 10.04 only have sources.list entries for supported repositories and components enabled with clear, inline comments documenting what is supported and what isn't?

---

### Post by BQAggie2006 on 2009-10-02
Don't know if you saw this in your research, but it might give you a better understanding of what each repository component contains:

[http://en.wikipedia.org/wiki/Ubuntu_linux#Package_classification_and_support](http://en.wikipedia.org/wiki/Ubuntu_linux#Package_classification_and_support)

As you can see on that page, all un-supported means is that updates come from community developers and not the developers at Canonical.

---

### Post by jptech on 2009-10-02
> **BQAggie2006 said:**
> Don't know if you saw this in your research, but it might give you a better understanding of what each repository component contains:

[http://en.wikipedia.org/wiki/Ubuntu_linux#Package_classification_and_support](http://en.wikipedia.org/wiki/Ubuntu_linux#Package_classification_and_support)

As you can see on that page, all un-supported means is that updates come from community developers and not the developers at Canonical.

I always forget how awesome Wikipedia is.  Thanks you very much for the link.  That is exactly the info I was looking for.

---

