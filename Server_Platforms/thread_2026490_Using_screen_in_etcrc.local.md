---
title: "Using screen in /etc/rc.local"
date: 2012-07-15
forum: Server Platforms
---

### Post by NealR on 2012-07-15
Hi,

I'm trying to start 2 game servers on server startup. So I'm putting the following details into my rc.local file:

screen -t server1
cd /home/steamcmd/csgo-gg 
sudo -u steamcmd ./srcds_linux -game csgo -usercon +game_type 1 +game_mode 0 +mapgroup mg_armsrace +map ar_baggage&
screen -t server2
cd /home/steamcmd/csgo-cc
sudo -u steamcmd ./srcds_linux -game csgo -usercon +game_type 0 +game_mode 0 +mapgroup mg_allclassic +map de_dust +port 27016

The problem I have, is that with the lines above in my rc.local file, neither of the servers run. I've tried messing about with the order of the screen -t serverX command, but I cannot get them running. Or if I do get them on, then screen is not running them.

Any advice?

Thanks,

NealR

---

### Post by NealR on 2012-07-15
Nevermind,

Ended up figuring out how to create a script(learnt something new at least) and then ran the screen -dmS server1 SCRIPTNAME and thats done the trip nicely.

Thread can be closed :-)

---

