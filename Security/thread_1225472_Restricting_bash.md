---
title: "Restricting bash"
date: 2009-07-28
forum: Security
---

### Post by Vintovka on 2009-07-28
I have a user, and I want him to be able to run exactly one command when he logs in. The command is under /usr/bin. It is called by a script on a remote system, so I cannot link it or change the command name. bash -r would be perfect, but I can't execute commands with slashes in them. I cannot change the way the command is called. So, my user needs to execute /usr/bin/<command> and absolutely nothing else. Any ideas how I can make this happen using bash?

---

### Post by The Cog on 2009-07-28
You could very probably do it with a chroot jail and only put that one command in the jail's /usr/bin. I would be interested to hear of any other ideas.

---

### Post by cdenley on 2009-07-28
Why not set the users shell to /usr/bin/<command>, or a small script which executes it?

---

### Post by hggdh on 2009-07-28
Indeed, you must set the user's shell to the script/command you want them to run. If they can only execute /usr/bin/<command>, then you set it up to run it as the login shell. But -- if this command ends execution, then the login session also ends.

You can also set it up as a shell script. Now, with a shell script, *this* shell will be limited to executing commands under the working directory (no full paths). So... what you do:

1. write a shell script that call *another* shell script/programme; this second shell script/programme *must* be under the same login directory (but, perhaps, under a subdirectory of it), since you cannot execute any commands that go *out* of the login directory.
2. the *second* shell script/programme is *NOT* a restricted shell! There, you can do whatever you like... just remember that the restricted shell has a very limited environment, so you will have to set it up manually in the second shell (or programme).
3. make sure there are no escapes from the second shell/programme, otherwise the users will eventually find it, and... lo and behold, they will be ou fo the jail.

---

### Post by Warren Watts on 2009-07-28
You can also replace bash with a different, more restrictive shell like [Iron Bar Shell]("http://ibsh.sourceforge.net/").
>     * the user can not step out of his/her home directory (jail)
    * the user can not access any files outside his/her jail
    * the user may execute only those commands, which the sysadmin lists in the appropriate configuration file
    * to prevent the user to store mp3's, bots, source or anything in his/her jail, ibsh regularly, automatically and without any notice blocks access to those files, which have NOT an extension listed by the sysadmin in the appropriate configuration file, or contain source code or elf binary data.
    * redirections, pipes, multiple command executions are not allowed
    * ibsh not only inspects the command, but the arguments as well
    * ibsh automatically logs the activities of the user to syslog
    * user commands files, user extension files for more control and customization 

I use ISBH for a proxy I have set up that allows friends at work to use my computer as a tunneled SSH web proxy at work (Our internet access is restricted).
Specific users get ISBH rather than bash when they log in to the server.

[IMG]http://sourceforge.net/dbimage.php?id=23046[/IMG]

---

### Post by hggdh on 2009-07-29
Yes, it looks nice. Unfortunately, it seems to be dead/orphaned, since there are no new updates since 2005.

Pity.

---

### Post by bodhi.zazen on 2009-07-29
You have several options.

First you can use rbash. Be warned, it is rather trivial to break out of a rbash shell, but for causal use it works.

[http://blog.bodhizazen.net/linux/how-to-restrict-access-with-rbash/](http://blog.bodhizazen.net/linux/how-to-restrict-access-with-rbash/)

Better would be to use a ssh key with a forced command.

Forced commands with ssh keys are mentioned as foot notes , you can look at this if you wish :

[http://blog.bodhizazen.net/linux/svnssh/](http://blog.bodhizazen.net/linux/svnssh/)

That blog will show you how to set up a key with a forced command (svn in this case) and restrict abuse (shell, port forwarding, etc).

Best use Apparmor.

---

