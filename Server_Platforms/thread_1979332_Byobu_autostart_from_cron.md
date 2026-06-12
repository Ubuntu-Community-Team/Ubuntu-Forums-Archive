---
title: "Byobu autostart from cron"
date: 2012-05-13
forum: Server Platforms
---

### Post by whisperity on 2012-05-13
Dear fellow Ubuntu users,

I have an automatation question I'd like to ask from you.
My server runs some servers which are, unfortunately, not daemons (like Minecraft or Source Dedicated Server). I am planning on making them automatically start at boot with the *@reboot* directive in crontab, but I wish their sessions to be usable from *byobu*.

Problem being, that byobu does not auto-start. I have written a shell script:
```
#!/bin/bash
screen -dr byobu -X screen -t srcds
screen -r byobu -p srcds -X stuff "./start_gmod.sh $(printf '\r')"

```And I execute it as my **nonprivileged** user in *crontab*:
```
@reboot           sourcesrv                    cd /srv/srcds/orangebox && ./hook-byobu.sh
```However, running this script requires *byobu* to be started when it runs. If I test the script with starting byobu by hand and then executing it from SSH, it does order byobu to make a new window and then starts the server.

My question being: [FONT=Lucida Console][SIZE=2]can I, somehow, automatize the start of byobu into the *hook-byobu.sh* file[/SIZE][/FONT]? I tried adding *byobu* (the command itself) after the shebang-line, but then it hangs until I, by hand, F6 (detach) from byobu.

Turning byobu's *Start automatically after log in* on does not work, because there is no login to happen, as the script is started from cron.

---

