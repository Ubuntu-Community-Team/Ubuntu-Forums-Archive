---
title: "Exim can't delete queue"
date: 2008-10-04
forum: Server Platforms
---

### Post by Shwick2 on 2008-10-04
Ubuntu 8.04
Exim 4

I have 10 frozen messages in the queue and I can't delete them. Both of these commands:

sudo exim -bpr | grep frozen | awk '{print $3}' | xargs exim -Mrm
		
sudo exim4 -bp | awk '/^ *[0-9]+[mhd]/{print "exim -Mrm " $3}' | sh

return Permission Denied.  Also I know that only the sender of the mail can delete it so I tried it without sudo, still denied.

I got these commands from two different places, does it matter if I use exim or exim4?

---

### Post by Shwick2 on 2008-10-05
Problem solved, should have put sudo in the second call to exim.

sudo exim4 -bp | awk '/^ *[0-9]+[mhd]/{print "sudo exim -Mrm " $3}' | sh

sudo exim4 -bpr | fgrep '*** frozen ***' | awk '{print $3}' | sudo xargs exim -Mrm

---

