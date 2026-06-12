---
title: "Desire To Jail Skype"
date: 2010-03-13
forum: Security
---

### Post by SuperMike on 2010-03-13
I want to jail Skype into its own process and not the one I login with. That way, if a hacker breaks in, it's limited to this process and only the limited functionality that that user account has.

The thing is this -- thousands of Linux guys run Skype, but Skype is hardly ever updated or have security patches, and we run it all the time. It seems like an easy avenue for an exploit. As well, my iptables firewall blocks input connections that I have not established, but Skype is an established connection.

How do I create a Bash script that launches Skype under a separate user account?

---

### Post by tgalati4 on 2010-03-13
You have several issues to deal with:

Skype is a binary blob (binary large object)--so there is no source code.  That is the primary point of contention with regards to security.  It runs with user privilege.  It needs access to your sound and video hardware.  It needs network access.

Unless you are running a kernel/distro that supports jailing, I don't see how to do it in normal userland.

You could create a special skype user and skype group and try to run it with those permissions--sort of like chroot.

You could also simply create a virtual machine and install another instance of linux (perhaps slimmed down to the bare essentials) just to run skype.  I don't know if that would really make it more secure because exploits could try to run arbitrary code (say to write files) and that could just as easily occur with a virtual machine.

Perhaps another approach would be to write a secure wrapper script that would run skype with extra monitoring attached.

There aren't many options to utilize:

tgalati4@tpad-Gloria7 /tmp $ skype --help
Skype 2.1.0.47

Usage: skype [options]
Options:
  --dbpath=<path>       Specify an alternative path to store Skype data files.
                        Default: ~/.Skype
  --resources=<path>    Specify a path where Skype can find its resource files.
                        Default: /usr/share/skype
  --disable-api         Disable Skype Public API.
  --disable-cleanlooks  Disable forced use of the Cleanlooks Qt style.
                        Use this option together with Qt's -style <style>
                        command to set a custom Qt style for Skype.
  --pipelogin           Command line login. "echo username password | skype --pipelogin"
  --version             Display version information and exit.

------------------

I keep hearing rumors of open-sourcing the linux skype client.  We can only hope.

---

### Post by rookcifer on 2010-03-13
Write an AppArmor profile for it.

---

### Post by Agent ME on 2010-03-14
This seems to be relevant - [http://myy.helia.fi/~karte/skype_in_a_sandbox.html](http://myy.helia.fi/~karte/skype_in_a_sandbox.html)

---

