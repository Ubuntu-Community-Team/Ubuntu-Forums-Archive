---
title: "Can't connect"
date: 2010-01-24
forum: Ubuntu One (CLOSED)
---

### Post by Anushka on 2010-01-24
When trying to log in I get the notice:

"OpenID authentication failed: Nonce already used or out of range"


I managed to use Ubuntu One once today. After that this started. Any ideas?
Thanks; Anu

---

### Post by joshuahoover on 2010-01-25
> **Anushka said:**
> When trying to log in I get the notice:

"OpenID authentication failed: Nonce already used or out of range"


I managed to use Ubuntu One once today. After that this started. Any ideas?
Thanks; Anu

Hi Anu! Sorry to hear you're running into this problem. We're working on a fix right now but the workaround appears to be:[INDENT]*Upon receiving OpenID failed error with 'nonce' info, go to [https://one.ubuntu.com/](https://one.ubuntu.com/) The login attempt _was_ successful, the problem is that the page is not redirected properly.*
[/INDENT]The bug where this is being tracked is: [https://bugs.edge.launchpad.net/ubuntuone-client/+bug/510866](https://bugs.edge.launchpad.net/ubuntuone-client/+bug/510866)

Thank you,

Joshua

---

### Post by Anushka on 2010-01-26
Thanks Joshua! I tried that and it worked... for me. But now I'm trying to share some files with a friend and he says he hasn't gotten an email and can't see them in his ubuntu. I can see the files and I've shared them. If I click the "share" button it says that he hasn't accepted my share. But he never got the notice about it...

Help! ;)

Anu

---

### Post by duanedesign on 2010-01-27
There are some files in
$HOME/.cache/ubuntuone/log/*
Take a look at the entries from around the time you shared the file. There might be a clue in there as to whether or not the operation was succesful. If you need any help with this let me now. Also you can stop by #ubuntuone on IRC freenode network and get real time support.

The Ubuntu One team is working very hard each day to take care of these issues. They are making great progress on this exciting project.

You might take a look at [this wiki page]("https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/Diagnostics"). There is a python script you can run and some tips on what to look for in your $HOME/.cache/ubuntuone/log/syncdaemon-exceptions.log. If you need any help with this i will be more than happy to help.

---

