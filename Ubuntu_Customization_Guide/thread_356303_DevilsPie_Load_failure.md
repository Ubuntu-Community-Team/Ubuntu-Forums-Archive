---
title: "DevilsPie Load failure"
date: 2007-02-08
forum: Ubuntu Customization Guide
---

### Post by bphunter616 on 2007-02-08
I'm not really sure where to post this question, apologies if done incorrectly.

I've installed Devilspie via "synapse" pkg mgr.  created .sd files in appropriate location and found myself dealing at first with an error:  No S-expressions to load, quiting.  Then when running "devilspie -d" I noticed the following which then simply seemed to stop...

bhunter@ibmt43:~$ devilspie -d
Devil's Pie 0.17.1 starting...
Loading /etc/devilspie
Loading /home/bhunter/.devilspie
Loading /home/bhunter/.devilspie/workspace4.ds
Loading /home/bhunter/.devilspie/workspace3.ds
Loading /home/bhunter/.devilspie/workspace2.ds
Loading /home/bhunter/.devilspie/workspace1.ds

that's it...  nothing after this point.  Searching thus far hasn't revealed what I may be dealing with.  

:confused:

---

### Post by dj9866 on 2007-03-20
I see that you haven't received any replies to your original post.  I also have exactly the same situation.  Am running Ubuntu 6.10 and have the latest version of Devilspie installed.  

If you have resolved this problem, can you provide guidance?

Thank you.

---

### Post by dj9866 on 2007-03-21
I finally determined what was going on and assume that you have also, since it has been almost a year since your original post.  

When it doesn't give control back to the terminal screen, it is because the job is still running.  As an example, if you were to run 'devilspie .devilspie/gaim.ds &' the job is run in the background.  The job executes and returns control to the terminal screen.

In the startup tab under the sessions screen, I have 'devilspie &' and it works as it should.

It is unfortunate that the needed info is so scattered.

---

