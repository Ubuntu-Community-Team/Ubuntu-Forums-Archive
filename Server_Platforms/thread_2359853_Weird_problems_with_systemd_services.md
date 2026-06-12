---
title: "Weird problems with systemd services"
date: 2017-04-28
forum: Server Platforms
---

### Post by nle on 2017-04-28
Hi, I have a weird issue with a couple of similar systemd services, they sometimes work and sometimes not (atm mostly not).


OS is Ubuntu 16.10 Server.


The two services are [EMAIL="rtorrent@rt.servic"]rtorrent@rt.servic[/EMAIL]e and [EMAIL="irssi@rt.servic"]irssi@rt.servic[/EMAIL]e. They are pretty much identical, so I'll just post the one here.


[EMAIL="rtorrent@rt.servic"]rtorrent@rt.servic[/EMAIL]e tries to start at boot, but fails instantly. It fails if I delete it, re-add it, and start it again.


The kicker is that the command works fine on its own, so it should work, and it has worked on some occasions. 


This is the service:
```

[Unit]
Description=rTorrent with tmux daemon
Requires=network.target local-fs.target openvpn@cyberghost.service
After=openvpn@cyberghost.service sys-devices-virtual-net-tun0.device
Wants=openvpn@cyberghost.service sys-devices-virtual-net-tun0.device


[Service]
Type=forking
KillMode=none
User=%I
ExecStartPre=/bin/rm -f /home/%I/rtorrent/rsession/rtorrent.lock
ExecStart=/usr/bin/tmux new-session -s rt -n rtorrent -d rtorrent
ExecStop=/bin/bash -c "/usr/bin/tmux send-keys -t rt:rtorrent.0 C-q && while pidof rtorrent > /dev/null; do sleep 0.5; echo rtorrent still running...; done"
WorkingDirectory=/home/%I/
Restart=on-failure


[Install]
WantedBy=default.target

```


This is the error, can't get any more information from the log either.
```

  systemctl status rtorrent@rt
  &#9679; rtorrent@rt.service - rtorrent
     Loaded: loaded (/etc/systemd/system/rtorrent@.service; disabled; vendor preset: enabled)
     Active: inactive (dead)


  Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Failed with result 'exit-code'.
  Apr 28 01:06:27 <hostname> systemd[1]: rtorrent@rt.service: Service hold-off time over, scheduling restart.
  Apr 28 01:06:27 <hostname> systemd[1]: Stopped rTorrent with tmux daemon.
  Apr 28 01:06:27 <hostname> systemd[1]: rtorrent@rt.service: Start request repeated too quickly.
  Apr 28 01:06:27 <hostname> systemd[1]: Failed to start rTorrent with tmux daemon.
  Apr 28 01:06:27 <hostname> systemd[1]: rtorrent@rt.service: Unit entered failed state.
  Apr 28 01:06:27 <hostname> systemd[1]: rtorrent@rt.service: Failed with result 'start-limit-hit'.
  Apr 28 01:17:23 <hostname> systemd[1]: Starting rtorrent...
  Apr 28 01:17:23 <hostname> systemd[1]: Started rtorrent.
  Apr 28 01:17:23 <hostname> bash[4575]: no server running on /tmp/tmux-1001/rt

```


This is driving me a bit crazy, any one have any input on this? Thanks!

---

### Post by cariboo on 2017-04-28
Does

```
sudo journalctl
```

give you any additional information?

---

### Post by nle on 2017-04-28
No, unfortunately not, it's just more of the same afaik, then it eventually gives up and halts.

I pasted a log here, just in case anyone spots something.

```

Apr 28 01:06:25 <hostname> systemd[1]: Starting rTorrent with tmux daemon...
Apr 28 01:06:25 <hostname> systemd[1]: Started rTorrent with tmux daemon.
Apr 28 01:06:25 <hostname> systemd[1]: rtorrent@rt.service: Control process exited, code=exited status=1
Apr 28 01:06:25 <hostname> systemd[1]: rtorrent@rt.service: Unit entered failed state.
Apr 28 01:06:25 <hostname> systemd[1]: rtorrent@rt.service: Failed with result 'exit-code'.
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Service hold-off time over, scheduling restart.
Apr 28 01:06:26 <hostname> systemd[1]: Stopped rTorrent with tmux daemon.
Apr 28 01:06:26 <hostname> systemd[1]: Starting rTorrent with tmux daemon...
Apr 28 01:06:26 <hostname> systemd[1]: Started rTorrent with tmux daemon.
Apr 28 01:06:26 <hostname> bash[3994]: no server running on /tmp/tmux-1001/default
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Control process exited, code=exited status=1
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Unit entered failed state.
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Failed with result 'exit-code'.
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Service hold-off time over, scheduling restart.
Apr 28 01:06:26 <hostname> systemd[1]: Stopped rTorrent with tmux daemon.
Apr 28 01:06:26 <hostname> systemd[1]: Starting rTorrent with tmux daemon...
Apr 28 01:06:26 <hostname> systemd[1]: Started rTorrent with tmux daemon.
Apr 28 01:06:26 <hostname> bash[4011]: no server running on /tmp/tmux-1001/default
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Control process exited, code=exited status=1
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Unit entered failed state.
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Failed with result 'exit-code'.
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Service hold-off time over, scheduling restart.
Apr 28 01:06:26 <hostname> systemd[1]: Stopped rTorrent with tmux daemon.
Apr 28 01:06:26 <hostname> systemd[1]: Starting rTorrent with tmux daemon...
Apr 28 01:06:26 <hostname> systemd[1]: Started rTorrent with tmux daemon.
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Control process exited, code=exited status=1
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Unit entered failed state.
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Failed with result 'exit-code'.
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Service hold-off time over, scheduling restart.
Apr 28 01:06:26 <hostname> systemd[1]: Stopped rTorrent with tmux daemon.
Apr 28 01:06:26 <hostname> systemd[1]: Starting rTorrent with tmux daemon...
Apr 28 01:06:26 <hostname> systemd[1]: Started rTorrent with tmux daemon.
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Control process exited, code=exited status=1
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Unit entered failed state.
Apr 28 01:06:26 <hostname> systemd[1]: rtorrent@rt.service: Failed with result 'exit-code'.
Apr 28 01:06:27 <hostname> systemd[1]: rtorrent@rt.service: Service hold-off time over, scheduling restart.
Apr 28 01:06:27 <hostname> systemd[1]: Stopped rTorrent with tmux daemon.
Apr 28 01:06:27 <hostname> systemd[1]: rtorrent@rt.service: Start request repeated too quickly.
Apr 28 01:06:27 <hostname> systemd[1]: Failed to start rTorrent with tmux daemon.
Apr 28 01:06:27 <hostname> systemd[1]: rtorrent@rt.service: Unit entered failed state.
Apr 28 01:06:27 <hostname> systemd[1]: rtorrent@rt.service: Failed with result 'start-limit-hit'.
Apr 28 01:17:23 <hostname> systemd[1]: Starting rtorrent...
Apr 28 01:17:23 <hostname> systemd[1]: Started rtorrent.
Apr 28 01:17:23 <hostname> bash[4575]: no server running on /tmp/tmux-1001/rt

```

---

