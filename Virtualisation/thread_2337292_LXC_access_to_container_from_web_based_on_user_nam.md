---
title: "LXC: access to container from web based on user name"
date: 2016-09-16
forum: Virtualisation
---

### Post by Randolph_Hill on 2016-09-16
Want to  setup some containers on my home system that will be assigned to specific individuals.
The user would access the container via a web browser where they would provide their user-name and password.
This would directly connect to the log on prompt of their assigned container.

Is there anything simple?


Randy

---

### Post by ian-weisser on 2016-09-16
Look into VPNs and OpenStack and similar already-available solutions of this type.

One expects you really don't want the headache of configuring and securing and regularly auditing your login webserver.
It's possible to use ssh keys instead of a webpage for user authentication, if you want to play with it.

---

### Post by Randolph_Hill on 2016-09-17
Thank you Just about to check OpenStack.

---

### Post by TheFu on 2016-09-17
OpenStack? Really? Got 10 physical machines? If not, openstack doesn't really make much sense. The overhead of installing and using it is huge. Heck, Proxmox makes more sense than openstack for a small userbase.

BTW, container "best practices" uses them for 1 task, not as a replacement for a full VM. All the training I've seen says to never allow remote shell connections into any container - that includes ssh.  What they say is, "if you need ssh inside a container, then you are doing it wrong."  That is for enterprise deployments and that is where containers really shine with 10x densities over normal VM deployments.

OTOH, the flexibility of containers really does make this an interesting solution, though I'm not ready to put container-based systems on the internet at this point.  Also, wouldn't use a web front-end. Would be inclined to run sshd from what little has been said, but totally lock down the number of open files, total number of processes allowed per userid and total storage available per userid.

The purpose of the logins would guide my suggestions greatly. Students? Paying clients? A group of hackers? I'd have very different setups for each.

---

### Post by MAFoElffen on 2016-09-19
The first post is a bit vague for me to answer in any detail.

On the one hand, this could be taken as wanting to provide remote access to an unprivileged container by unprivileged users. Yes, these unprivileged users are being verified via user credentials, but are not members of the Wheel group = not Administrators.

On the other hand, I could interpret this as web access to a server, immaterial to where that server resides and what that server actually is.

Funny I should say this about a new technology, but "Traditionally" when you think of a container, you think an OS or application template, where you create a copy of... Then you run that copy of for a short time (limited lifespan)... where it does something and creates a result... then it gets disposed of and goes away. When you think unprivileged containers, you think of containers that are ran by normal users. 

I may be wrong, and many here may correct me on this, which would more than welcomed for discussion... but I do not think of container "instances" as being persistent, nor something running 24/7. (This practice may evolve and change in time.) For an providing a virtual server where you can count on up-time, where a user would have access to that server 24/7, I think more along the lines of a VM Guest Server. When I think of making that possible in a container framework, in what you describe, then the thought of a user logging in remotely and starting a container instance. If I think of the "server" being there 24/7, then I do not think of a container instance, but rather of physical or virtual servers, That may be just me, but...

I am guilty of pushing containers to their limits and of trying to use them as virtual guests. It is a personal challenge of mine to test and see possibilities. ..and using a container as a virtual guest *IS* possible. I'm just not sure yet if it is "smart" for something that needs a 24/7 up-time guaranty.

I can see by the responses that this confusion is also seen by others, so I am asking the OP (Original Poster) for more clearer information detail about the services these users need, when they them, and what they would need to do. I believe that detail will clear up the direction of the mechanics needed to make that possible.

---

