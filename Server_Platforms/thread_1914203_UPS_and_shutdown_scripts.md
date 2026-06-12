---
title: "UPS and shutdown scripts"
date: 2012-01-23
forum: Server Platforms
---

### Post by JigglyWiggly_ on 2012-01-23
So I am a pooper.

So I have apcupsd configured I think right, as if I request the status it reports the expected information.

By default apcupsd calls the shutdown scripts once the batterylevel I wrote in the config right?


So in /etc/rc6.d (This is the shutdown place right?) I had a script called a1vmstop and in it it saves the virtual machines, and I tested it seperately and it works.

So when a power outage happened it did not work.

So I realized a problem it does not have Kxx in the name so I added that now.


But what else do I have to do?
Should I put that K01a1vmstop file in /etc/init.d? Should it be called K01a1vmstop or a1vmstop? a1vmstop correct?
Thx

---

### Post by SeijiSensei on 2012-01-24
Take a look at the file /etc/rc2.d/README.  You'll see that all the scripts reside in /etc/init.d and are devoid of a Kxx or Sxx name.  The rcN.d directories correspond to "[run levels]("http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html")" and contain only symbolic links to the actual scripts in /etc/init.d. 

So, to take one example, my system has a symlink called K74bluetooth in /etc/rc6.d/ that points to the /etc/init.d/bluetooth script.  In that script you'll see a bash "case" statement that handles "start", "stop", "restart", etc.  You can follow this approach for your program, or, if it only runs as shutdown, put the script in /etc/init.d and symlink to it as /etc/rc6.d/Kxxa1vmstop.  The number you assign to it determines when it will be executed during the shutdown process.  I use VirtualBox as a VM manager; the script to shutdown that process is assigned to K20 on my machine.  That's probably a good number to assign your script as well.

---

