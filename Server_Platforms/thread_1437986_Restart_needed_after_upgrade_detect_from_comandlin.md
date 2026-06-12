---
title: "Restart needed after upgrade detect from comandline"
date: 2010-03-24
forum: Server Platforms
---

### Post by othermale on 2010-03-24
Hello,

  I'm setting up an ubunutu server (tomcat, mysql etc)  which has been going very smoothly I must say.  But I do have a question:
  I plan to do manual updates over  ssh using "sudo apt-get update" and "sudo apt-get upgrade" but I believe sometimes these update will need a complete machine restart.

So the question is: how can I tell if I need to reboot the server after an update _using the command line_?

thanks a bazillion.

---

### Post by KB1JWQ on 2010-03-24
Simple solution?  Use aptitude the same way you're using apt-get; it has more logic.

More in depth:  The kernel and libc stuff require reboots.  I don't *think* anything else does.

---

### Post by cdenley on 2010-03-24
A security update for the linux kernel was released for all ubuntu versions a week ago, so a reboot will be required in order to use the new kernel.

---

### Post by othermale on 2010-03-24
Thanks for the responses. 
  Aptitude looks like a great tool but I can’t seem to find where it would indicate a need to reboot after update. 
  It looks like my only real option is to look over the update contents for kernel and libc stuff and just hope ;)
  Thanks again.

---

