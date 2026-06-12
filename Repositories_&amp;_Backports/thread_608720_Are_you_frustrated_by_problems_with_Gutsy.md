---
title: "Are you frustrated by problems with Gutsy?"
date: 2007-11-10
forum: Repositories &amp; Backports
---

### Post by exploder on 2007-11-10
I have seen posts from people that are very frustrated by problems they are having with Gutsy. I have also seen posts where people are going back to Feisty because of difficulty with Gutsy. I was at this point but now have a Gutsy based system that performs very well.

If you are frustrated to this point maybe I can be of some help to you. This is by no means a recommended method of fixing things but at least in my case the results speak for themselves. 

Before I begin let me say that this can potentially break Gutsy. In my case I was prepared to reinstall because the problems were so bad anyways.

1) Enable the Gutsy Proposed repository. We are going to install all or most of these updates. Example (My system uses no restricted drivers so I had no issue with updating this package, your results may vary.)  

2) Install the updates.

These updates should have fixed the following problems: log on / off and shutdown problems, screen lock and shutdown problem, OpenOffice freezing and crashing problems, DNS Name lookup problems, and slow logon problems.

One new problem was introduced with these updates, GDM Errors at startup.

3) Now we are going to fix the GDM Error by editing the /etc/hosts file. Simply add your computer name to the end of the top line in the file. ( I found this tip in a bug report.)

4) Disable the Gutsy Proposed repository and test out your results.

Please post your results. I really hope this helps some of you out. I can not guarantee you will have the same results as me so keep that in mind. This is not the usual way that problems are resolved but my results were extremely positive.

---

