---
title: "start mysql before jabber"
date: 2010-05-03
forum: Server Platforms
---

### Post by outdooricon on 2010-05-03
Currently when the system boots, It boots jabberd2 before mysql. So jabber fails. Then, later mysql is loaded. I either want to force jabber to load mysql first, or make the system boot mysql first. I've tried changing /etc/init.d/jabberd2 to say "# Required-Start:    mysql $network $named $remote_fs"... however, insserv says that mysql service has to be enabled... so I assume that's an issue because mysql is an upstart script. Any ideas?

---

### Post by dudumomo on 2010-05-03
Manually, does it work ? If you start first mysql then jabber ?

If yes, you can simply add a delay to the jabber script.
You can add: sleep xx &
xx for xx seconds

---

### Post by Xipher on 2010-05-03
Actually it would be better to adjust the init scripts sequence value. If you check update-rc.d documentation you will find that you can provide an "NN" value. This value specifies the order in which the service is started when init loads the run level. Adjust those so mysql is lower then jabber for starting and higher for stopping so that mysql isn't stopped out from under jabber and it can shutdown clean.

---

### Post by Wim Sturkenboom on 2010-05-04
> **dudumomo said:**
> Manually, does it work ? If you start first mysql then jabber ?

If yes, you can simply add a delay to the jabber script.
You can add: sleep xx &
xx for xx seconds
That's bad practice (in general); today it might need one sec delay, tomorrow 20 sec delay.
It would be better to let the script check if mysql is running.

I'm not familiar with Ubuntu server setups (I use Slackware servers), but I think that Xipher has the correct solution in the post above.

---

### Post by dudumomo on 2010-05-04
Indeed, seems far better !

---

### Post by outdooricon on 2010-05-04
> **Xipher said:**
> Actually it would be better to adjust the init scripts sequence value. If you check update-rc.d documentation you will find that you can provide an "NN" value. This value specifies the order in which the service is started when init loads the run level. Adjust those so mysql is lower then jabber for starting and higher for stopping so that mysql isn't stopped out from under jabber and it can shutdown clean.

So, I believe that this worked on jaunty, when mysql wasn't converted to upstart. However, now there is no mysql process listed in any of the /etc/rcRUNLEVEL.d/ directories. I have tried creating my own symlink for /etc/rc2.d/S10mysql to the mysql init script, since that would make it start before /etc/rc2.d/S20jabberd2, however this still didn't work. My assumption is that since upstart is supposed to init processes asynchronously, that making the symlink to it, in fact just starts running upstart.  Especially since when I read the /etc/init.d/mysql init file, it seems to just makes upstart calls.

---

