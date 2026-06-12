---
title: "SSH not running but have &quot;ssh-XXXX&quot; entry in /tmp?"
date: 2009-10-10
forum: Security
---

### Post by JamesKube on 2009-10-10
Noob to Ubuntu and a little paranoid since I'm used to having several layers of pretty intuitive and easy to use security measures in place on Windows systems...

So, trying to get a feel for my system and noticed this directory in my "/tmp" dir:

"ssh-dMBDd11533"

Is this entry normal, even when I don't have an ssh server running AND haven't ssh'd into a system from this particular machine?  

Also, is it normal to have two entries for a single user when running the "who" command (tty and pts)?  I believe that this is normal; however, any input would be greatly appreciated.

---

### Post by unspawn on 2009-10-11
> **JamesKube said:**
> Noob to Ubuntu and a little paranoid since I'm used to having several layers of pretty intuitive and easy to use security measures in place on Windows systems...
No, that is not what Clippy is for :-]


> **JamesKube said:**
> So, trying to get a feel for my system and noticed this directory in my "/tmp" dir: "ssh-dMBDd11533" Is this entry normal, even when I don't have an ssh server running AND haven't ssh'd into a system from this particular machine?  
The directory might have contents. If it has it could be a zero size file of type socket with a filename like "agent-PID" denoting the fact this directory is used for ssh-agent. The PID, if currently in use, should show the PID of the SSH Agent process.


> **JamesKube said:**
> Also, is it normal to have two entries for a single user when running the "who" command (tty and pts)?
It does not have to but yes, it is possible to have one (login), two (+terminal window) or more entries. As always *talking about things* is not equal to *actually posting details*. The latter is more efficient and makes it easier for people to assess and explain.

---

### Post by Lars Noodén on 2009-10-11
> **JamesKube said:**
> ... I'm used to having several layers of pretty intuitive and easy to use security measures in place on Windows systems...


Thanks.  That was a good laugh. 8-)

> **JamesKube said:**
> 
...noticed this directory in my "/tmp" dir:
"ssh-dMBDd11533"


@ unspawn mentioned that this is for the ssh-agent.  Ubuntu does this automatically for you at start up.  The agent is used in conjunction with keys when you log in repeatedly with SSH, SFTP, or SCP to the same machine or to  multiple machines using the same keys.  If you read "[SSH and ssh-agent](http://www.securityfocus.com/infocus/1812)" you'll get an idea about how to use the agent.  However, you can skip the first step.  

If you look at your machine using **ps** or **pgrep**, you'll see a process called ssh-agent and the corresponding process id number.  Then if you look in the directory /tmp/ssh-yaddayadda, you'll see that the PID matches.  The contents of /tmp/ get wiped with each reboot.

---

### Post by JamesKube on 2009-10-11
Thanks for the response Unspawn!  But for the record, I disagree, Clippy is the utlimate in IDS technology :-) !

As far as the SSH directory in /tmp...so, although I've never SSH'd from or to this machine before, and as far as I can tell the SSH daemon isn't running (this may be where I'm making a noob mistake [grep'd for SSH in /etc/init.d/ for "ssh" and didn't get any hits) it's still normal to have an "ssh-XXXX" entry in /tmp?  

Also, here's my output from "who":

james     tty7         2009-10-06 04:36 (:0)
james     pts/0        2009-10-10 21:22 (:0.0)


Thanks again!

---

### Post by JamesKube on 2009-10-11
Thanks Lars!

[I've ditched Windows, but still feel that it's pretty securable, albeit inherently "full 'o holes," for desktop use I'd still suggest it to most "non-computer" people [and I'd go to their house and install ThreatFire, AVG, ZoneAlarm, etc...naturally need third party app's to plug all of the holes Mr$oft left in there].  Love Linux, but it's not quite ready for regular consumption by everyone, although Ubuntu has gotten it pretty much there (my non-geek Wife actually prefers Ubuntu to Windows now!)] :-) 

I think between you and Unspawn, you've cleared up some misconceptions on my part.  Ran ```
ps -A | grep ssh
``` and sure enough, found an 'ssh-agent' entry.  Thanks again!

---

