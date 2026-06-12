---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2011-03-29
forum: Server Platforms
---

### Post by Mururmir on 2011-03-29
Hi everybody,

i have problems running Bittorrent Daemon transmission on a kinda stable Ubuntu environment. I've been running it for about a year and had no problems so far until a couple of days ago. I'm not able to access the web interface which comes along with it and the daemon itself appears to be not running at all. As far as i can tell it seems to have an issue with the start script, however i have no idea how to fix that.

Here's what i get when it's trying to start the daemon after reinstalling it (sorry for german language :/ but at least there are crappy translations made by me).

Richte transmission-daemon ein (2.05-0ubuntu0.2) ... [FONT=Courier New]//configuring transmission-daemon[/FONT]
 * Starting bittorrent daemon transmission- daemon                                                                                                                                             invoke-rc.d: initscript transmission-daemon, action "start" failed.
dpkg: Fehler beim Bearbeiten von transmission-daemon (--configure): [FONT=Courier New]/*Error while processing transmission-daemon */[/FONT]
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 255 zurück  [FONT=Courier New]/*This line doesn't even make to much sense in the german language but it says something about a subprocess installed post-installation Skript which return the error value 255 */[/FONT]
Fehler traten auf beim Bearbeiten von: /[FONT=Courier New]* Errors occurred while processing transmission-daemon*/[/FONT]
 transmission-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas on that? Somebody having similar problems?

Note: Already tried apt-get -f install didn't work for me

Thanks in advance for your time and passion

greets

---

