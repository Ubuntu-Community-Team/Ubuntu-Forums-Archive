---
title: "what to do with package non-maintainers?"
date: 2008-03-04
forum: Repositories &amp; Backports
---

### Post by Circus-Killer on 2008-03-04
i'm not sure if i'm even posing the right question, but what is done about package maintainers who do not maintain their respective packages?

i find every now and again, there will be a problem with a package or program, and instead of the package being upgraded to a newer version which works, it is left broken.

a perfect example is the checkgmail package in the repos. since the beginning of gutsy's stable life, checkgmail has not worked due to gmail changing there method of authorization.

checkgmail has itself been updated, and if you install the updated version, it works perfectly. so why, after so many months, has the package in the repos not been upgraded to a working one. i understand that major version jumps are saved for the next release of ubuntu, however in situations like these i think its bad to have to wait 6 months just to have a working package replace the broken one.

so is there a way that ubuntu tracks maintainers performance, and how they handle their responsibiities. i'm sure there are plenty of people willing to take on a job that the current maintainer is unwilling to do. plus, once a maintainer has been deemed inefficient, for lack of a better word, what can be done about it? should there be guidelines that specify how and when a maintainer needs to be replaced? or do we keep the same maintainers even though they haven't maintained the package in 2 years?

just something to ponder about. maybe i got this all wrong, and admittedly have no idea on ubuntu's rules on how they assign maintainers and what what. this is just a problem that i can see getting out of control if not considered.

---

### Post by bapoumba on 2008-03-04
[https://bugs.launchpad.net/gutsy-backports/+bug/189795]("https://bugs.launchpad.net/gutsy-backports/+bug/189795")
The proper way to deal with this situation, as far as I know, is a bug report and backporting the working hardy version to gutsy (please see the above link regarding the example of checkgmail).
Then it depends where the package is located in the ubuntu archives. [MOTU]("https://wiki.ubuntu.com/MOTU")s deal with everything in universe/multiverse, this is where most people interested in packaging can join. you can also check the [Packaging and Compiling Programs]("http://ubuntuforums.org/forumdisplay.php?f=44") sub-forum here.

---

