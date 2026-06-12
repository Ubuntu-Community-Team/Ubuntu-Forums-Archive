---
title: "2 wierd ideas for linux (nudo and internal repos)!"
date: 2008-01-20
forum: The Cafe
---

### Post by Xbehave on 2008-01-20
nudo(normal user do)
IS it possible to give users an authority between root and normal user? what i was thinking about is giving a normal user the authority to do something with the equivilant of sudo.
why? well to limit local users abilities to not even being able to break thier own settings without running something in nudo.

Internal repositories
My second weird idea is to offer the strength of customization of Linux to somewhere it has previously been limited. while running a network you probably dont want to give anybody the ability to install programs on thier machine. However you may have a whole set of different workers trying to complete different tasks or people who work more effectively using some software, but neither want to go round ask everybody what their specific needs are, nor install every peice of software on every computer.
Would setting up a repository that included all optional software being used in the company? be possible. then using some soft of /usr/usr/bin and complicated security stuff to allow users to install/remove/reinstall optional software (say if they prefer gnumeric instead of OO calc).

Are either of these ideas good? feasible?
I do realize the 2nd 1 sort of lost the goodness between my head and the keyboard, but try considering it for a 2nd there must be a useful situation for it!

---

### Post by DMcA on 2008-01-20
I'm pretty sure you can do most of this. The first point could probably be solved by fiddling with permissions, although I don't really know much about the issue. On the second point, setting up a local repository is straightforward and you could allow users to use apt-get but not to edit their sources.list I'd have thought. 

I do like the idea of a nudo command though, even if it's not that useful

---

### Post by DeadSuperHero on 2008-01-21
APT-on-CD is pretty capable, you might want to look at that.
The main problem is putting all the repo files ONTO a large enough CD or DVD, and then have it all placed inside the system, I think. How could this be implemented without causing too much bloat?

---

### Post by insane_alien on 2008-01-21
internal repos is a huge eater of disk space(i have one for my network because currently i have the diskspace and a slow enough conection to warrant only downloading a package once. most user will not have the resources. heck, my brothers laptop wouldn't even be able to hold the entire repos.

as for 'nudo'(honestly thought it was something else when i clicke the thread titile ;P

it is possible with the sudo command and smart use of groups and priveledges. it is again one of those things that would need to be set up post installation as everybody has a different set up. it could do with an easier way to do it and i'm sure somebody would appreciate a GUI for it.

---

### Post by GGLucas on 2008-01-21
The repo thing is easy, you can set up a pc in the network to act as repo webserver, and then just set up your router/individual PCs to redirect requests for the official repos to that machine (or you could just edit their sources.list to point to your repo server), of course, if you want different installed programs for different users, you'll run into trouble.

The nudo thing should be doable, the problem is that to log in as a user, you need to have certain rights over specific files in your home folder, so while it's possible, it won't be practically useful by far. Anyway, you would create a second user for every user you have, then chown the files to that second user, chmod them to something like 644 so the "actual" user can access them read only, and the "priviledged" normal user can access them read/write, then create a bash script in /usr/local/bin/nudo with something like
```
#!/bin/bash
sudo -u PRIVILEDGED_USER $@ 
```

of course, if you have multiple users on one machine, you'll have to check which user is running the nudo script so you can pick the right priviledged user for them.

Again, messing with the ownership/permissions of configuration files in your home directory might screw it up and prevent you from logging in, so be careful.

---

### Post by Xbehave on 2008-01-21
> **GGLucas said:**
> The repo thing is easy, you can set up a pc in the network to act as repo webserver, and then just set up your router/individual PCs to redirect requests for the official repos to that machine (or you could just edit their sources.list to point to your repo server), of course, if you want different installed programs for different users, you'll run into trouble.


but could you give users permision to install from that repo, while stoping them running dpkg?

---

### Post by Lord Illidan on 2008-01-21
> nudo(normal user do)
IS it possible to give users an authority between root and normal user? what i was thinking about is giving a normal user the authority to do something with the equivilant of sudo.
why? well to limit local users abilities to not even being able to break thier own settings without running something in nudo.

I don't understand this at all. Explain further.

2nd idea : Can be done, but you need a lot of disk space.

---

### Post by GGLucas on 2008-01-21
> **Xbehave said:**
> but could you give users permision to install from that repo, while stoping them running dpkg?

Well no, but why would you want to do that ? You could deny them permission to edit their sources.list and have only your own repo in it, what would they be able to do with dpkg that you want to prevent them from doing? On the other hand, they need root permissions to run apt, so they'd also have root permissions to edit sources.list.. that might be a problem.

---

### Post by Xbehave on 2008-01-21
with dpkg they can download and install any package making the restriction to the local repo pointless,
I see the root access as a problem although you can install software without root if you jsut setup a directory they can install the programs to that isnt root protected, but then restricting access to this folder so only a program and not even the user manually can access it is abit more tricky
if that was done and no-exec was set on the rest of their writable system then it would be doable!

---

### Post by DMcA on 2008-01-21
> **Xbehave said:**
> with dpkg they can download and install any package making the restriction to the local repo pointless,
I see the root access as a problem although you can install software without root if you jsut setup a directory they can install the programs to that isnt root protected, but then restricting access to this folder so only a program and not even the user manually can access it is abit more tricky
if that was done and no-exec was set on the rest of their writable system then it would be doable!

Would this not work?:

Create a group that includes apt-get and add it to /etc/sudoers

---

