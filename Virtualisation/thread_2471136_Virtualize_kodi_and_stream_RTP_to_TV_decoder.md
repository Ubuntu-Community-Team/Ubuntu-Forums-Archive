---
title: "Virtualize kodi and stream RTP to TV decoder"
date: 2022-01-21
forum: Virtualisation
---

### Post by borhackerfree on 2022-01-21
Hi everyone there,

I have a technical challenge in mind, first, to learn, and also it may be very useful.
I have a PC (home environment) running Ubuntu server 18.04.6 with SAMBA server and Transmission. Now I want to install a hipervisor in order to virtualize an operative system like, for example, LibreELEC, and then, stream the video and audio over my LAN as an RTP stream, so I can see it in my TV, accessing it from my TV decoder, and then I don't need any additional hardware.
I think this is going to be difficult, but:
- can anybody, please, tell me, will it be possible?
- can you tell me what hipervisor I could choose? I think I prefer KVM because it, is, as I read, the official Linux hipervisor.
- can you tell me whether the hipervisor will output RTP stream or I have to use VLC?

Thanks in advance

---

### Post by Tadaen_Sylvermane on 2022-01-21
You have a few misconceptions.

Kodi does not provide a stream. At best it can do a UPNP server but that can be accomplished many far easier ways. It is a 10 foot interface for a tv, not a streaming server.
Hypervisor just runs vms. it doesn't output anything specifically. The VM provides whatever stream you create.

Use Minidlna if you are after basic streaming. This can be run on the host with zero difficulty. Just point it at your media directories and let it run. should be visible to any device with upnp capability.

*EDIT* Just in case you are worried about an over complicated configuration file here is my example file. It runs in a docker with my main media share bind mounted read only into the docker. Obviously customize to your own situation.

```
media_dir=A,/var/minidlna/pool/music
media_dir=V,/var/minidlna/pool/video
friendly_name=Megalith
db_dir=/var/minidlna/db
log_dir=/var/minidlna/log
inotify=yes
```

---

