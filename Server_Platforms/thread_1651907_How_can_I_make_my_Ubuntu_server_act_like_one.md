---
title: "How can I make my Ubuntu server act like one?"
date: 2010-12-23
forum: Server Platforms
---

### Post by mike_yung on 2010-12-23
I have an Ubuntu server which would not boot due to a reference in /etc/fstab to a drive which was not working.  This was difficult to troubleshoot because instead of the normal login prompt, all I was given to work from was a message from ureadahead and a system that would not respond to keyboard input, except for ctrl-alt-del.

I want to configure things properly so that if & have another drive  problem I will still be able to login directly and deal with the issue.     Rather then lock up, I'd prefer that the boot process warn me about a  broken fstab and prompt for ctrl-D or type root pass so I can get a  shell.

Any help would be appreciated.  Thanks in advance.

---

### Post by CharlesA on 2010-12-23
Hit "s" to skip the failed mount.

Then add "noauto" to the options in fstab

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571444](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571444)

---

### Post by mike_yung on 2010-12-23
thanks I'll give that a try

---

### Post by mike_yung on 2010-12-30
Thanks for pointing out that I'm affected by a bug and not a misconfiguration.  I've made some progress with your help.
     
    [LEFT]I've edited /etc/fstab and  added the nobootwait option for the data storage drives.  Now  if one should fail, my fileserver will still boot unattended (provided the drive containing the core of my fs is OK).  I  already am using the noauto option for all my temporary storage.[/LEFT]
     
    [LEFT]I've not had much luck in  getting the diagnostic info from the boot process onto the screen.  If I  modify /etc/default/grub and set the &#8220;quiet splash" option for GRUB_CMDLINE_LINUX_DEFAULT I do get a prompt to 'press S to skip'.  However when I use the "text" option which I prefer all I see is the message from ureadahead.


According to [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571444/comments/47](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571444/comments/47) this has been "fixed in maverick".  This is encouraging.  
[/LEFT]

---

### Post by mike_yung on 2010-12-30
I don't want to move to 10.10 but would like to upgrade mountall to mountall_2.19_i386.deb .  How can this be done properly?

I added "deb [http://ubuntu.articnetwork.ca/ubuntu/](http://ubuntu.articnetwork.ca/ubuntu/) maverick main" to my software sources list but that added over 500 packages to the update manager's list.

My software sources are configured for only long term support releases.

I just want to update mountall and it's dependencies, while leaving the update manager in an easy to maintain state.

---

### Post by CharlesA on 2010-12-30
You need to have the splash screen enabled and go to tty7 (ctrl + alt + f7) to see the error. It's annoying, and I filed a bug report on it, but it didn't get anywhere.

As for upgrading a specific package, I don't know, but I don't think it would be a good idea to add packages from a different distro version.

Maybe backports, but I don't know.

---

### Post by mike_yung on 2010-12-30
OK, I'll just live with this until they decide to fix the mountall which comes with 10.04.  Thanks again.

---

