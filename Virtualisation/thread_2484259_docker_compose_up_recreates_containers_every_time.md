---
title: "docker compose up recreates containers every time"
date: 2023-02-21
forum: Virtualisation
---

### Post by roddie2 on 2023-02-21
[COLOR=#445D6E][FONT=&amp](Cross-posted from the official Docker forums)

I’m running Docker CE version 23.0.1 on two different Ubuntu 22.04.1 machines and my daily routine is to run [FONT=courier new]docker compose pull[/FONT] followed by [FONT=courier new]docker compose up -d[/FONT] every morning manually because I like to see what’s going on. I’ve noticed that for the last week or so that [FONT=courier new]docker compose up -d[/FONT] is recreating every container that has been updated recently, even if it recreated it previously.
[/FONT][/COLOR]
[COLOR=#445D6E][FONT=&amp]My containers are running fine and everything is stable, but I wouldn’t expect this kind of behavior and I can’t find where anything has changed.
[/FONT][/COLOR]
[COLOR=#445D6E][FONT=&amp]I was able to “clear” this issue yesterday by stopping all containers, running [FONT=courier new]docker system prune -a[/FONT], and then running [FONT=courier new]docker compose up -d[/FONT] again, but today after a few containers were upgraded, I see the issue again:
[/FONT][/COLOR]
[COLOR=#445D6E][FONT=&amp]Sample from one machine:
[/FONT][/COLOR]```

roddie@plex ~/docker% docker compose up -d
[+] Running 1/1
 &#10303; Container plex  Started                                                 6.7s
roddie@plex ~/docker% docker compose up -d
[+] Running 1/1
 &#10303; Container plex  Started                                                 7.0s

```
[COLOR=#445D6E][FONT=&amp]Thank you for any tips![/FONT][/COLOR]

---

### Post by roddie2 on 2023-02-21
Update - This might be related to [this issue]("https://github.com/docker/compose/issues/9600").  I will mark as solved once I confirm.

---

### Post by roddie2 on 2023-02-21
Update #2 - Downgraded to docker-compose-plugin 2.15.1 (from 2.16.0) and all is good.

---

