---
title: "Australian National University Hack"
date: 2019-10-03
forum: Ubuntu, Linux and OS Chat
---

### Post by pushbike06 on 2019-10-03
The Australian National University, aka ANU, system was recently hacked over a period of time by a team of several entities.
The original access was through an email, unopened, apparently previewed, i.e. downloaded from the mail server.
The user ports to the system are apparently via Microsoft systems and software.
The servers are, to me , unknown, but I would expect them to be Linux.
Is it possible for this type of hack to occur through a Linux port system, say Ubuntu, and the Thunderbird app.?

ABC news story:
[https://www.abc.net.au/news/2019-10-03/why-no-one-will-say-yet-who-hacked-anu/11571790?section=technology](https://www.abc.net.au/news/2019-10-03/why-no-one-will-say-yet-who-hacked-anu/11571790?section=technology)

---

### Post by Skaperen on 2019-10-04
who did it is not the most important question.  the most important question is who let it happen.

Linux can be attacked, too.  the kernel itself is usually quite solid.  but there is a history of many userland programs listening and communicating on those ports that have had many vulnerabilities.  probably the most common is the buffer overflow where the amount of data going into a buffer is not properly limited, allowing the sender to overwrite other data, and the stack, which has pointers that process will eventually use.  carefully designed data streams can include new pointers and code to take over the process and go from there.  many things are used these days to fight this in cases where the code cannot be changed.

years ago one of my servers had the imapd software hacked with an upload of a toolkit to take over the whole server.  it failed because the uploaded machine code was for an x86, but my server was a Sun SparcStation.  i diagnosed the whole program from fixing the software source code to tracking down the time and which computer in a student lab at a major university did it.  their administration determined which student it was and dismissed from school for 2 years.  that toolkit, a rootkit, would have immediately deleted all the logs i used to track down the source, had it been an x86.

Linux or Ubuntu are not magically more secure.  but they do have the advantage of more eyes looking at the source code who are not motivated to make more money in hiding vulnerabilities.

---

