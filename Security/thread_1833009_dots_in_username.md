---
title: "dots in username"
date: 2011-08-25
forum: Security
---

### Post by floobit on 2011-08-25
I am trying to set up a small desktop machine that plays nicely with some Red Hat servers, and would like my username on the local machine to match my username on the servers.  My username on these servers is in the format first.last, and neither ubuntu nor debian allow you to create a username with a dot in the graphical interface.  I could useradd first.last just fine, but then on reboot the login screen on gdm prevented me from logging in as any of the users.  

What is going on here?  Can I really not have a dot in my username?  Is there a workaround?  This seems quite odd.  from what I've read, this used to be a problem 10 years ago because useradd did not yet have support, but I haven't seen any posts more recent than 2004 that discuss this issue.  

Thanks

---

### Post by Lars Noodén on 2011-08-26
First, try submitting a bug report in Launchpad so that the problem can get fixed in future versions.

Second, the work around is to use [adduser](http://manpages.ubuntu.com/manpages/natty/en/man8/adduser.8.html) in the shell to create your user.

---

### Post by floobit on 2011-09-02
Thank you for the reply.  Upon your advice, I did submit a bug report (actually updated an existing one).  I am guessing it is a policy decision to prevent compatibility issues.  

I did use useradd first.last to create a new user.  Such a solution prevents the gdm login screen from working on restart, and even deleting the user does not easily unbreak it.  So, as long as a graphical interface is desired (specifically gnome2), this workaround does not help.  

The problem seems to arise from features in gnome2.  Does the same issue arise in other windows managers?  If I switched to Xcfe, could I get around this issue?

Thanks

---

### Post by bodhi.zazen on 2011-09-02
> **floobit said:**
> Thank you for the reply.  Upon your advice, I did submit a bug report (actually updated an existing one).  I am guessing it is a policy decision to prevent compatibility issues.  

I did use useradd first.last to create a new user.  Such a solution prevents the gdm login screen from working on restart, and even deleting the user does not easily unbreak it.  So, as long as a graphical interface is desired (specifically gnome2), this workaround does not help.  

The problem seems to arise from features in gnome2.  Does the same issue arise in other windows managers?  If I switched to Xcfe, could I get around this issue?

Thanks

If the problem is with the login (gdm) you would need to change to kdm, xdm, lightgdm, or Slim. I am not sure which of those may or may not work with a long in name with a .

If the problem is with gnome, and not gdm, then changing to xfce, or another window manager may help.

gnome 2 is depreciated, you could also try gnome 3 .

---

### Post by floobit on 2011-09-02
Yes.  I was just hoping that this might have been documented somewhere.  It has clearly been tested and developers have put specific code in to check for periods in usernames.  VMware, for instance, does not let you do this when setting up a new machine on most distros I've attempted.  If this code and testing is not publicly documented, I suppose I can do the testing myself and let everyone know.

Gnome3 is not an option for me in this instance because it does not play nicely with the 3D acceleration drivers provided by vmware or virtualbox.  If I need to do these tests, though, I would include it, testing on a dedicated box.

---

