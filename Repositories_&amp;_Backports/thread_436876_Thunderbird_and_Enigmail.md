---
title: "Thunderbird and Enigmail"
date: 2007-05-08
forum: Repositories &amp; Backports
---

### Post by MikeMcKay on 2007-05-08
Hi,  I'm having a problem with installing the Thunderbird Enigmail extension.  I run Ubuntu 6.06 LTS and Thunderbird 1.5.0.10 which is the up to date version from the Dapper repository.  The version of the Enigmail extension in the Dapper repository, however,  is compatible with Thunderbird version 1.5.0.2.0 only and, consequently, it won't install.  Does anyone know of a way around this ?  Mike

---

### Post by wieman01 on 2007-05-08
Can't you just install Thunderbird from source? I remember that's what I did to get Enigmail going.

---

### Post by MikeMcKay on 2007-05-08
Thanks for the prompt response wieman.  Installing from source is my fallback plan.  I've been trying to avoid this, however, because firstly I've not done it before and, secondly,  I think that I would lose the automatic updating that you get from the repositories (although I suspect that you could get round that by setting-up some sort of local repository but, for me, that would really be too hard right now).  Mike

---

### Post by wieman01 on 2007-05-08
> **MikeMcKay said:**
> Thanks for the prompt response wieman.  Installing from source is my fallback plan.  I've been trying to avoid this, however, because firstly I've not done it before and, secondly,  I think that I would lose the automatic updating that you get from the repositories (although I suspect that you could get round that by setting-up some sort of local repository but, for me, that would really be too hard right now).  Mike
That's true, but on the other hand you won't be able to install Enigmail using the standard repositories. So that's the catch. In my experience, Dapper's repositories always lag a little behind so it may take a while before they decide to update Enigmail. Therefore, installing from source is the lesser of two evils. Your choice.

BTW: Installing/compiling from source is not that difficult. If you decide to give it a go, post your problems here. People will help. :-)

---

### Post by paparucino on 2007-05-08
> **MikeMcKay said:**
> Thanks for the prompt response wieman.  Installing from source is my fallback plan.  I've been trying to avoid this, however, because firstly I've not done it before and, secondly,  I think that I would lose the automatic updating that you get from the repositories (although I suspect that you could get round that by setting-up some sort of local repository but, for me, that would really be too hard right now).  Mike

If you already have it downloaded:

You must look for the extension in  ./thunderbird/xxxxxxxx.default/exensions
Y'll see a lot of strange directories.  Search inside everyone, you must be patient, for a file called install.rdf. open it with an editor than look for **em:minVersion** and **em:maxVersion**
Modify the values according your TBird release. Usually I put 99.99 so I don't have to change every time.

If you have the .tar.bz file you must open the file, edit the same file as above and pack it again

---

### Post by MikeMcKay on 2007-05-16
GOOD NEWS ! !  It seems someone's fixed the Enigmail package in the repository so that it's now compatible with Thunderbird 1.5.0.10 (actually, 1.5.0.4 to 1.5.0.98 inclusive).  Whoever you are, many thanks.  Mike

---

