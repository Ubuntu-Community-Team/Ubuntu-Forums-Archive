---
title: "Why is some software in repository not the latest?"
date: 2017-02-01
forum: Ubuntu, Linux and OS Chat
---

### Post by sitongia on 2017-02-01
The latest example I've encountered is gnome-tweak-tool. The release installed here on my 16.04 LTS desktop is from 2013. I can see from the software's release site that it has been updated as recently as Sept. 2016. Why isn't a much newer release in the repository for update? This is a general question, because I've encountered the same situation with other software. Is this a result of a fundamental policy or procedure for updating software? Should I be sending in a request to update the repository? Is that how the system works? Thank you.

---

### Post by slickymaster on 2017-02-01
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by ian-weisser on 2017-02-01
It's neither a policy nor a procedure.

It's simply that software is packaged by volunteers. Debian and Ubuntu are, of course, community-driven projects.

Volunteers who care deeply about their particular software gather like-minded fellows, form a team (committee), and share the burden of packaging, testing, maintaining, upstreaming bugs, etc. among more than one person. Such teams are more likely to outlast any individual volunteer, who may grow bored, feel unappreciated, change jobs, get married or divorced, etc.

If you care deeply about certain software, you can learn the process and volunteer to maintain your favorite package(s) for a few releases. Start at mentors.debian.net - most packages start at Debian and are imported from Debian to Ubuntu.
If you feel that the technical or time burden of packaging is too much, you can help recruit, lead, coordinate, cheerlead, and otherwise use your social skills encourage packagers. You can also partner with other occasional-packagers to handle minor tasks like fixing documentation or answering easy user questions...that's how teams start.

---

### Post by sitongia on 2017-02-01
Thank you for this explanation, ian-weisser. I will look into this.

Just for future reference, I was wrong about the release I'm running. It is 16.1.

Unfortunately, the pull-down Tools doesn't include marking this as solved.

---

### Post by lisati on 2017-02-01
> **sitongia said:**
> Just for future reference, I was wrong about the release I'm running. It is 16.1.

Do you mean 16.10? (The Ubuntu release cycle and numbering is based around the months of April and October, 04 and 10 respectively)

---

### Post by vasa1 on 2017-02-02
> **sitongia said:**
> ...
Unfortunately, the pull-down Tools doesn't include marking this as solved.
That option isn't available for posts in this particular subforum and most subforums that aren't for technical support.

All the same, you may be able to go to the first post, click on **Edit**, and then click on **Go Advanced** and modify the title of the first post.

---

### Post by Geoffrey_Arndt on 2017-02-02
Sitongia . . . your question is a good one.   A little additional info is that Ubuntu uses the most common method for constructing and maintaining a Linux distribution . . . sometimes referred to as the "snapshot" method.   So, at a point in time (shortly before release), the distro is "frozen" regarding package/software content.   From that point on (except for browsers and a FEW other exceptions), the only updates to the distro packages are bug and security fixes.   But no newer versions (point releases) of any included package.    This is done mainly for "stability".

Other distros such as Arch, Solus and a few others are "rolling" distro models.   Packages are not frozen, but updated shortly after they are tested, and then made available to the "Updater Process".   So, the advantage is newer packages AND no reinstall of the base distro is ever needed (amost ever . . ).    The disadvantage is mainly "less stability" and a different workload for the maintainers.

---

