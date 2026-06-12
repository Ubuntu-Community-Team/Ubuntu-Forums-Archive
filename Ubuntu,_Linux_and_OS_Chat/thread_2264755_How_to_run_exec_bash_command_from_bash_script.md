---
title: "How to run exec bash command from bash script"
date: 2015-02-09
forum: Ubuntu, Linux and OS Chat
---

### Post by yusuf4 on 2015-02-09
I have a bash script and I want to run commands like these.
First-Command
&& exec bash
&& Last-Command

The exec bash will throw a error in this way.
If I write like this:
First-Command;
exec bash;
Last-Command

The Last-Command doesnt work because of exec bash starting a new thread.

Is there a work around of this scenario?

Can we connect some editor application to a terminal and submit commands to the terminal through that editor application.

Thank You.

Best Regards,
Yusuf

---

### Post by TheFu on 2015-02-10
I've never seen exec used in bash scripting before. [http://www.tldp.org/LDP/abs/html/x17974.html](http://www.tldp.org/LDP/abs/html/x17974.html) has some examples.  I learned something new.

Also - this won't start threads, it starts processes - which are fairly light in Unix systems.

If you only want to run cmd2 and cmd3 if the prior command completes successfully, then use[B]
cmd1 && cmd2 && cmd3[/B].  Or you could store the RC from each and use an 'if' for the decision.

If you need remote control of scripts, that is possible. Most people use **ssh** for that, but in the old days **expect** was used too.

The ABSG is really useful for odd bash scripting and as a general how-to guide: [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) 
Hope it helps.

---

### Post by sudodus on 2015-02-10
Hi Yusuf,

Welcome to the Ubuntu Forums! If you want help, it might be better to post in one of the support forums, for example in [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331") or if more advanced bash, in [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310")

Why do you want to run **exec bash**?

What are the first-command and last-command?

It will be much easier to help, if you tell us as much as possible. Otherwise we can only guess, and maybe we misunderstand what you want to do and give irrelevant advice.

-o-

It is possible start any program directly from a terminal (or terminal window) or from a shell-script file. So yes we can connect some editor application to a terminal and submit commands. Again, please tell us what you have and what you want (what you are trying to do).

---

