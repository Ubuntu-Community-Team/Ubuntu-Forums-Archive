---
title: "'make menuconfig' in an ssh shell - no keyboard input"
date: 2012-11-13
forum: Server Platforms
---

### Post by dzchimp on 2012-11-13
I have access to a build server into which I ssh into, with non-root privileges. The purpose is to compile Android kernels.

For this, I need to first compile a cross compiler, and crosstool-ng has always been my choice. However I found that on the new server, on doing a 'make menuconfig' or a 'ct-ng menuconfig', the menuconfig screen opens up, but allows no keyboard input.

Keys like Up, Down, Tab do not evoke the usual response. The only thing that does work is Ctrl-C, which promptly exits menuconfig.

Can anyone help me get to the root of this problem?

---

### Post by Doug S on 2012-11-13
It is not clear to me how to try to help, and this reply is perhaps of no value.
 
I never use "make menuconfig", but I tried it via SSH just to see if it would work as expected. It did. My build computer is Ubuntu server 12.04 and my ssh session was via PuTTY from an MS windows computer. My sshd_config file is unchanged from default, and I don't have any special settings on PuTTY.
 
I also tried an SSH session from my main server (also 12.04) to the build computer, opened within an already open PuTTY session to that main server. "make menuconfig" worked fine there also.
 
As a third test, I physically sat at the mainserver and did an ssh session to the build computer from a terminal window. "make menuconfig" worked fine.

---

### Post by dzchimp on 2012-11-13
Thank you. 

It works for me on another server. So, it does seem that something with that particular server configuration is at the root of this. I'm wondering what it could be, and how I can find out.

---

### Post by Doug S on 2012-11-13
Perhaps compare the /etc/ssh/sshd_config files from the two servers looking for differences. (assuming you have read access, which by default you would, but maybe that has been changed).

---

### Post by dzchimp on 2012-11-13
> **Doug S said:**
> Perhaps compare the /etc/ssh/sshd_config files from the two servers looking for differences. (assuming you have read access, which by default you would, but maybe that has been changed).

I'm being denied read permissions on the problematic server. I'd probably have to submit a request to the admin to take a look.

---

