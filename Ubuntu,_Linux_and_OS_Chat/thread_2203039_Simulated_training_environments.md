---
title: "Simulated training environments"
date: 2014-02-01
forum: Ubuntu, Linux and OS Chat
---

### Post by ugjim2k on 2014-02-01
Good day members,
I am currently reading for linux certification (starting with LPIC-1 and progressing eventually to LPIC-3) and wanted to know if there are any environments that people have managed to create to simulate typical linux failures that require an administrator to resolve, typical things like a failed DHCP server, corrupted file system, poorly configured user accounts or LDAP server, etc. Having such environments would work as excellent learning tools for one to use rather than focusing entirely on only the text material and few practical examples that are commonly provided in training books.

Thanks.

---

### Post by tgalati4 on 2014-02-01
tgalati4@tpad-Gloria7 ~ $ ping zalman
PING zalman (192.168.1.131) 56(84) bytes of data.
^C
--- zalman ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3023ms

Set up a linux server and remotely log into it.  Then start breaking things and you will quickly see what needs to be done to fix it.  The big problem with a remote server is when it is down, you can't log into it to fix it.  

If you don't have a spare machine to load a server onto, then sign up for a small, free virtual private server and load up some server distro and play on that.

I don't know of any online training environments.  There are bash environments and other console simulators, but I am not aware of any server "flight" simulator that you can inject problems into--like a flooded data room.

---

### Post by Don_Stahl on 2014-02-02
Sounds like a good project for someone. Could be as simple as guidelines for "how to break the server" in ways that can still be addressed by a student.

---

### Post by ugjim2k on 2014-02-04
Sounds fair enough. Have any recommendations on where I could set up a free virtual private server?

---

### Post by ugjim2k on 2014-02-04
> **Don_Stahl said:**
> Sounds like a good project for someone. Could be as simple as guidelines for "how to break the server" in ways that can still be addressed by a student.

Was thinking of the same whereby someone could create bash scripts that would "configure" a system as a broken system and then leave it to the learner to try and find out what was broken. Would be an interesting project.

---

### Post by tgalati4 on 2014-02-04
[http://www.dreamhost.com/servers/vps/](http://www.dreamhost.com/servers/vps/)

[https://www.linode.com/](https://www.linode.com/)

Spend some time on the server forums and do an 80/20 survey.  80% of the problems are caused by 20% of the problems.  Make a list of these problems and the solutions.  There may even be lists already created.

[http://www.tuxradar.com/content/how-fix-most-common-linux-problems](http://www.tuxradar.com/content/how-fix-most-common-linux-problems)
[http://www.tldp.org/FAQ/Linux-FAQ/common-problems.html](http://www.tldp.org/FAQ/Linux-FAQ/common-problems.html)
[http://www.maximumpc.com/article/features/linux_troubleshooting_guide_fix_most_common_problems](http://www.maximumpc.com/article/features/linux_troubleshooting_guide_fix_most_common_problems)

Some problems are obscure and trick questions:  When confronted with a blank console screen, what is the first thing that should be checked?  Has the text color been changed to the background color?  Is the console machine turned on?  Silly questions.

---

