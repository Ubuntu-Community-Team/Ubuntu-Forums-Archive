---
title: "Fun with netcat"
date: 2009-04-15
forum: The Cafe
---

### Post by olejorgen on 2009-04-15
**Tools needed:**
netcat
speex (optional)
dyndns.com (optional)
alsa-utils

**VoIP**
```

# Computer 1
HOST=your.friend.dnsalias.net # or ip
PORT=45321
netcat -l -p $PORT | aplay
# or
netcat -l -p $PORT | speexdec -
# Computer 2
HOST=your.friend.dnsalias.net # or ip
PORT=45321
arecord | netcat $HOST $PORT
# or
arecord -t raw | speecenc --8bit --denoise - - | netcat $HOST $PORT

```
Using speex adds significant latency though.. since the pipe buffer is 4KB :P

**Filesharing**
```

# Computer 1
cat file | netcat $HOST $PORT
# with compression
cat file | gzip | netcat $HOST $PORT
# Computer 2
netcat -l -p $PORT > file
# with compression
netcat -l -p $PORT | gzip -d > file

```

---

