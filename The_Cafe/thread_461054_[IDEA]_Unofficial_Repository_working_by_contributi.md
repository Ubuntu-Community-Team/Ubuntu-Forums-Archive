---
title: "[IDEA] Unofficial Repository working by contribution from projects"
date: 2007-06-01
forum: The Cafe
---

### Post by Haegin on 2007-06-01
This _[thread](http://ubuntuforums.org/showthread.php?t=237770&highlight=deluge&page=1)_ did make me think a little about setting up a repository for Ubuntu which projects can apply to to get privileges to upload their specific debs whenever they want provided the follow certain rules:
1. It must work with the versions of programs and libraries in the official Ubuntu repositories
2. It must work with the other programs from the repository.
3. Debs uploaded must be uploaded by the related project or somebody endorsed by the related project

The repository would only accept projects that were not in the official Ubuntu repositories and because of the rules they would have to play nicely with any other software in the repository. The third rule is so two projects depending on the same library do not try and upload competing versions of the same thing. Instead the creators of the library could apply to the repository if they wished.

This would have to be less thoroughly tested than the universe and multiverse repositories so the software can get added faster and most testing would be done by the people submitting the debs. If there was a problem with an uploaded deb conflicting with other software a small group of repository maintainers would be responsible for removing the offending deb and notifying the relevant project so they can re-upload a corrected deb.

I am interested in starting something up like this if other people are interested in the idea and think it would work. Please contact me via email if you are interested (hjmills [a_t] gmail [ dot- ] com) or post in this thread if you have questions, thoughts or spot the major flaw in my idea.

---

### Post by Bachstelze on 2007-06-01
> **Human Prototype said:**
> 
The repository would only accept projects that were not in the official Ubuntu repositories

Why not submit it to the official repos, then ?

---

### Post by Haegin on 2007-06-01
Because many projects are fast growing and release new builds frequently while they go through a beta stage. These would never make it into the official repository before the next release which is up to six months away as they would need thorough testing to ensure they worked and would need updating by the time they were tested.
I am proposing a repository which people use with the understanding that it isn't as well tested as the official repository but it will (hopefully) have more of the projects that start up and develop quickly.
When the projects get stable enough they will most likely be added to the Ubuntu repository at which point they will no longer need to be included in the repository I am planning. I am suggesting a stop gap for rapidly developing projects between releases.
Also if projects can maintain control of their debs and how they are packaged but don't need to start up their own repository they may be encouraged to release Ubuntu debs making life easier for Ubuntu users.
Please correct me if my understanding that the submission process for the official repositories takes a long time.

---

### Post by Foxmike on 2007-06-01
I don't know about submission process delays, but for sure it would be nice to have a centralized repo in which there is bleeding edge versions of some projects, rather than having to add several third parties repos.
 
Great idea!

---

### Post by Bachstelze on 2007-06-01
Well, isn't this what Backports are for ?

---

### Post by Haegin on 2007-06-01
Backports seems to me to focus more on newer stable versions of programs that are already in the Ubuntu repos for the future Ubuntu release but significant changes have been made to make it worth updating the version in the official repo for the current release due to popular demand. This means only popular programs that have undergone significant changes get backported and they are already in the Ubuntu repositories.
I am trying to help solve the problem of software not being in the repos rather than software in the repos being out of date.

When reading the introduction in the backports forum it sounds like the extras repo is trying to accomplish a similar goal but I don't know anything about this repo or where it can be found and the guide doesn't cover adding the extras repo (just the backports repo) so if anybody can provide any more information it will be greatly appreciated.

Thanks for all the input and questions, please keep them coming!

---

### Post by Iandefor on 2007-06-03
How about software that's in a legal gray area?

---

### Post by Haegin on 2007-06-03
If it is allowed in the UK (which is where my server is) and its not in the official repositories I am happy to include it. Please keep the feedback coming and if you are a project which is potentially interested in a place to host your debs where you will have access to edit and update them please let me know so I can get an idea of how popular this will be.

---

### Post by EdThaSlayer on 2007-06-03
This would be very nice, since it would save time going around the net looking for a working deb of   new linux software.

---

### Post by Haegin on 2007-06-05
It looks like getdeb.net is trying to overcome the same problem from a different angle (they build the debs themselves rather than the projects submitting them) so I have decided to get involved there rather than re-invent the wheel meaning people have more places to look.

Because of this there is not much point continuing this thread unless people think there is a MAJOR benefit in allowing projects to submit their own debs to a central repository.

---

