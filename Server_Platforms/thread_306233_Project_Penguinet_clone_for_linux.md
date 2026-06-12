---
title: "Project: Penguinet clone for linux?"
date: 2006-11-24
forum: Server Platforms
---

### Post by luckylucky on 2006-11-24
Howdy Programmers!

I'm not a programmer myself, but have a good idea for what (hopefully) should be an easy, fun & extremely useful contribution for the linux community.  If a programmer would be so inclined to make such a program then I'm sure that it would be a smash hit app that would be widely used by linux people.  Here is the idea...

We all ssh into servers remotely to administer the servers.  Of course the simplest way is to just use a terminal to ssh into the remote server, and is probably what most people do.  There is also puTTy, which is available both for windoze & linux, which is allright.  However the BEST program is penguinet ([http://www.siliconcircus.com/penguinet](http://www.siliconcircus.com/penguinet)) but unfortunately it is only for windoze and is not free (either as speech or beer).  The really nice thing about penguinet is that it can save profiles of ssh login information (including the passwords) so that you could easily log into whatever ssh server you want with whatever account you want with just a click of a button.  This way you don't have to keep typing in the login info each time... just click a profile button and you're in.  Feel free to try their 30 day full demo to see how wonderful it is.

Ok, so here is the idea for some smart cookie programmer - - could you clone penguinet & it's functionality into an open source project?  If you choose to accept this mission I'm sure that you'd have a famous piece of software that would grant you linux fame & glory, and you'd be admired by many linux administrators for creating this ultra useful tool.

So... are YOU up for the challenge?

---

### Post by elst on 2006-11-24
You don't actually need to type passwords more than once per session for SSH - if you use key-based authentication the SSH agent software supplied with OpenSSH and PuTTY lets you specify the passphrase for a key once, and then access all resources that use that key without any extra prompts. The result is *very* smooth on Linux, as KDE and GNOME will both transparently access SSH services once you add the relevant key to the agent.

---

### Post by luckylucky on 2006-11-25
That's interesting... how would you actually do that?  Could you please elaborate upon that and/or provide a link to a good howto?

Thank you.

---

### Post by elst on 2006-11-25
This is an SSH HOWTO that I've been working on:

[http://www.elsn.org/SSH-HOWTO/ssh-howto.html](http://www.elsn.org/SSH-HOWTO/ssh-howto.html)

There's some sections explaining agents and how to set them up on Linux.

Any feedback is very welcome, so if you have any issues or queries feel free to mail me.

---

