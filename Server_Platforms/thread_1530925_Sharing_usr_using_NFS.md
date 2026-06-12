---
title: "Sharing /usr using NFS"
date: 2010-07-14
forum: Server Platforms
---

### Post by imgx64 on 2010-07-14
I was following a guide about installing and using NFS. The guide mentions an example use case of sharing the /usr directory to install programs only once and use them on multiple computers. I wanted to try the idea, but unfortunately, the guide didn't explain any further. I tried searching the Internet for more information about it, but my Google-fu failed me. I have some questions and doubts about how this works in a real situation.

Admittably, I don't know much about the file system organization in Ubuntu, so please bear with me and explain if some of my assumptions are wrong or if I seem to not understand something.

Does this work for a distribution like Ubuntu or is it only applicable for distributions that are manually installed and configured? How does this interact with APT? Wouldn't APT be confused if files started appearing randomly in /usr without it adding them? What about programs that use config files in /etc or some other files in /var? How will they behave? And the icons in the Gnome menu, surely they won't appear if I just installed programs on the shared /usr without adding them manually. And there are many other situations where I just don't understand how this would work.

If it was feasible, would it be better to have the shared directory be the /usr of the server, or a separate directory on the server (/share/usr for example.) And would I need to re-install the operating system on the computers from scratch?

I'd also be happy if you could point me to a guide, book, website, etc that answers my questions. And if you've ever done it, please share your experience.

I apologize if this belongs to a different forum. I thought I should put it here because it's mainly a discussion, and not a concrete support question/answer.

---

### Post by koenn on 2010-07-14
it's pretty simple:
you 'export' (~ share) a directory on a server, and you mount it on other computers. 
This is 'transparent', i.e. users/programs on the client computers will not know that the /usr they look at is a really a network share. 

apt will not be confused, because it doesn't look in /usr to see what's installed, it keeps track if what it installed in its own database.

It would be best not to export /usr on the server, but use a different directory (/srv/usr or so) : there is no reason to assume the clients will need the same /usr as a server, or that updates to a client should magically end up on your server's /usr - unless you want to create identical servers or so

some other directories, such as /etc, can not be shared/mounted of the network. What will happen is that the executables in /usr will look for their config in /etc of the computer where they're executed, and behave accordingly. 

I've never done this, so I'm not quite sure how to set it up. if you want to use something like apt, I guess you'd run it from the clients, and apt will put files in /usr. If /usr is a mountpoint and another filesystem/exported dir is mounted there, that's where the files will end up. 
You still may have to run apt on other clients, to get the config end pre- and post install scripts right. So sharingh /usr is mainly a mechanism to safe disk space (and, to some extend, force identical versions of binaries). You may need to tweak file modes (permissions, owner ship) to get this working. 


Maybe this belongs in the server subforum.

---

### Post by samosamo on 2010-07-14
It seems very possible but I would be very careful researching on whether the /usr directory is necessary for boot.  Imagine the NFS server is down, etc... your machines would never boot.

---

### Post by koenn on 2010-07-14
> **samosamo said:**
> It seems very possible but I would be very careful researching on whether the /usr directory is necessary for boot.  Imagine the NFS server is down, etc... your machines would never boot.


That is not going to be a problem.
Files that are needed for boot are kept in directories (/etc, /bin, /sbin, ...) that are always on the "/"-partition and can not be mounted from elsewhere

---

### Post by imgx64 on 2010-07-14
> **koenn said:**
> if you want to use something like apt, I guess you'd run it from the clients, and apt will put files in /usr. If /usr is a mountpoint and another filesystem/exported dir is mounted there, that's where the files will end up. 
You still may have to run apt on other clients, to get the config end pre- and post install scripts right. So sharingh /usr is mainly a mechanism to safe disk space (and, to some extend, force identical versions of binaries). You may need to tweak file modes (permissions, owner ship) to get this working.

Well, that sounds plausible, and answers my questions. But will running APT on each computer re-write the files in /usr every time?

---

### Post by koenn on 2010-07-15
I would expect so, yes.

---

