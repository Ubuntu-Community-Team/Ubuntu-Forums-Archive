---
title: "&quot;I've written my IPtables rules.  What next?&quot;"
date: 2007-05-05
forum: Server Platforms
---

### Post by nick1 on 2007-05-05
Greetings,

I have a LAMP server installation of Ubuntu 7.04 Feisty Fawn which I would like to secure using IPtables.  Assume this server is a production server providing HTTP and SSH services.

I've been studying IPtables and I think I am ready to implement my firewall rules.  Getting a grip of basic IPtables wasn't all that bad, I'm actually more confused on how I go about implementing my firewall rules.

I would like this post to serve as documentation on how to implement IPtables after you have them written out.  In other words "I've written my IPtables rules.  What next?"

Since I'm still confused on the steps required to activate my IPtables rules, here are the steps *I think* I need to carry out *after* I have written my rules:

1.)  At the very top of my rules, place the line:

	```
#!/bin/bash
```

2.)  Save my IPtables rules to a file named:

	```
rules.sh
```

3.)  Place rules.sh into the following directory:

	```
/etc/init.d
```

4.)  Issue the following commands:

	```
cd /etc/init.d
```
	```
update-rc.d rules.sh defaults
```

	Additional information about update-rc.d can be found at:
	[http://wiki.linuxquestions.org/wiki/Update-rc.d](http://wiki.linuxquestions.org/wiki/Update-rc.d)

5.)  You're done.

Again, from what I've learned so far about IPtables, this is what *I think* needs to be done after I have my IPtables rules written out.  I need someone to review these steps and constructively criticize them.

My ultimate goal is to provide documentation for newbies so they can see exactly what they need to do after they have their IPtables rules written out.

I've read a little about the modprobe utility.  Some questions I have:

1.)  Is it necessary to include modprobe in the IPtables rules?

2.)  If so, which modules should be included?

3.)  And where in the rules should they be placed?

As for permissions, what permissions should rules.sh have?

Thank you for your time,

*Nick*

---

### Post by neouser99 on 2007-05-05
not that there is nothing wrong with iptables, and it is definitely something that if you have the time and patience, you should go learn it. but if that is not your ultimate goal, let me offer a suggestion ```
sudo apt-get install shorewall
``` shorewall is a firewall configuration program that using iptables/netfilter (kernel level packet instructions) to setup a highly versatile, configurable, and easy to maintain firewall. if i missed the mark, we can figure out your iptables later, i just wanted to offer this suggestion first.

-neo

---

### Post by gombadi on 2007-05-05
Looks good.
That will load the firewall rules early in the boot process so be in place when the interface is brought up.

Also now ubuntu uses upstart to start services. You may want to investigate how to set up the rules.sh script with upstart. That said it should still work fine as you have described.


As for permissions it just needs to be executable like any other shell script so as root this will work.
```
chmod 0754 /etc/init.d/rules.sh
```

I have found that iptables will load any kernel modules it needs by itself so in my firewall I just load the iptables commands and it takes care of the module loading.

---

### Post by Ambis on 2007-10-15
Thank you for this great "tutorial" =)

Finally I got my rules to load up at boot.

I was first a bit confused about the contents of the .sh file, but it goes like this:

-----------------
#!/bin/bash
iptables -A INPUT -yourrules..
iptables -A INPUT -morerules..
-----------------

Cheers.

---

### Post by codmate on 2007-10-15
I thought that by default on Ubuntu, the iptables config was kept in
/etc/iptables.up.rules
You can generate a text stream to send to here by entering the rules manually on the command line (or indeed, with a script), and then running
iptables-save > /etc/iptables.up.rules

---

### Post by fatbastard spice on 2007-10-15
Only other thing i did was take the rules and put them more in the format of the other scripts in /etc/init.d  So giving them start & stop commands. Also added open & closed commands so that i could test new software with the firewall completely open or closed. Though based on gombadi's post looks like i'll have to examine upstart to see if i need to update the script.

---

