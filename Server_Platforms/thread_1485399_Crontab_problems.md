---
title: "Crontab problems"
date: 2010-05-16
forum: Server Platforms
---

### Post by zOdeac on 2010-05-16
ok i have no idea what i am doing wrong so i figured i would ask for help.

I have this entered into my crontab/root file,
1 * * * * /var/www/alertatech/server/bin/  ./tester.sh     #test

from what i understand is 1 is for min and the /var/ part is the 
path to the file i want to launch and the ./tester.sh is the file i want to run.

If i run this file in command line i can hit ./tester.sh and everything works great but as i try to set a task up for this i get this though webmin

Output from command /var/www/alertatech/server/bin/ ./tester.sh  ..
/bin/sh: /var/www/alertatech/server/bin/: Permission denied

any ideas on how i can do this..  I set 

Execute cron job as:root
Command:/var/www/alertatech/server/bin/  ./tester.sh   

Thanks in advance for help,
zOdeac

---

### Post by Ryan Dwyer on 2010-05-16
It should be:
/var/www/alertatech/server/bin/tester.sh

Or if the tester.sh script tries to access files relative to its directory:
cd /var/www/alertatech/server/bin && ./tester.sh

---

