---
title: "Dansguardian so hard to configure"
date: 2006-12-30
forum: Ubuntu Christian Edition
---

### Post by jlc on 2006-12-30
This sucka makes it hard ;)  

Just trying to update my podcast feeds. 

```

justin@echelon:/var/log/dansguardian$ pwd
/var/log/dansguardian
justin@echelon:/var/log/dansguardian$ tail -n 20 access.log
2006.12.30 13:31:30 - 192.168.1.104 http://media.gospelcom.net/rzim/LMPT/MP3/126-1.mp3 *DENIED* Banned MIME Type: audio/mpeg HEAD 0
2006.12.30 13:31:30 - 192.168.1.104 http://media.gospelcom.net/rzim/LMPT/MP3/126-1.mp3 *DENIED* Banned MIME Type: audio/mpeg HEAD 0
2006.12.30 13:31:30 - 192.168.1.104 http://media.gospelcom.net/rzim/LMPT/MP3/126-1.mp3 *DENIED* Banned MIME Type: audio/mpeg HEAD 0
2006.12.30 13:31:30 - 192.168.1.104 http://media.gospelcom.net/rzim/LMPT/MP3/126-1.mp3 *DENIED* Banned MIME Type: audio/mpeg GET 0
2006.12.30 13:31:31 - 192.168.1.104 http://www.downloads-walkintheword.com/podcast/ww20061229.mp3 *DENIED* Banned extension: .mp3 HEAD 0
2006.12.30 13:31:31 - 192.168.1.104 http://www.downloads-walkintheword.com/podcast/ww20061229.mp3 *DENIED* Banned extension: .mp3 HEAD 0
2006.12.30 13:31:31 - 192.168.1.104 http://www.downloads-walkintheword.com/podcast/ww20061229.mp3 *DENIED* Banned extension: .mp3 HEAD 0
2006.12.30 13:31:31 - 192.168.1.104 http://www.downloads-walkintheword.com/podcast/ww20061229.mp3 *DENIED* Banned extension: .mp3 GET 0
2006.12.30 13:31:31 - 192.168.1.104 http://media.gospelcom.net/rzim/JT/MP3/JT152-4.mp3 *DENIED* Banned MIME Type: audio/mpeg HEAD 0
2006.12.30 13:31:32 - 192.168.1.104 http://media.gospelcom.net/rzim/JT/MP3/JT152-4.mp3 *DENIED* Banned MIME Type: audio/mpeg HEAD 0
2006.12.30 13:31:32 - 192.168.1.104 http://media.gospelcom.net/rzim/JT/MP3/JT152-4.mp3 *DENIED* Banned MIME Type: audio/mpeg HEAD 0
2006.12.30 13:31:32 - 192.168.1.104 http://media.gospelcom.net/rzim/JT/MP3/JT152-4.mp3 *DENIED* Banned MIME Type: audio/mpeg GET 0
2006.12.30 13:31:43 - 192.168.1.104 http://media.gospelcom.net/rzim/LMPT/MP3/126-1.mp3 *DENIED* Banned MIME Type: audio/mpeg HEAD 0
2006.12.30 13:31:44 - 192.168.1.104 http://media.gospelcom.net/rzim/LMPT/MP3/126-1.mp3 *DENIED* Banned MIME Type: audio/mpeg HEAD 0
2006.12.30 13:31:44 - 192.168.1.104 http://media.gospelcom.net/rzim/LMPT/MP3/126-1.mp3 *DENIED* Banned MIME Type: audio/mpeg HEAD 0
2006.12.30 13:31:44 - 192.168.1.104 http://media.gospelcom.net/rzim/LMPT/MP3/126-1.mp3 *DENIED* Banned MIME Type: audio/mpeg GET 0

```


justin@echelon:/etc/dansguardian$ cat exceptionsitelist

```

dansguardian.org
windowsupdate.microsoft.com
windowsupdate.com
download3.vmware.com
rzim.org
walkintheword.com
media.gospelcom.net
www.downloads-walkintheword.com

```


justin@echelon:/etc/dansguardian$ cat exceptionurllist
```

http://media.gospelcom.net/rzim
http://www.downloads-walkintheword.com/podcast/

```

How exactly is the path supposed to be in, or am I doing something else wrong?

Thanks,

---

### Post by jlc on 2006-12-30
Ah ha!

I was half way there,

The walk in the world worked in rhythmbox, just not rzim so I looked again and it was the trailing slash in exceptionurllist

from
```

http://media.gospelcom.net/rzim
http://www.downloads-walkintheword.com/podcast/

```

to
```

http://media.gospelcom.net/rzim/
http://www.downloads-walkintheword.com/podcast/

```

---

### Post by urukrama on 2006-12-31
Just in general,  there is no need to add "www." to urls or domains in the exceptionsitelist or the bannedsitelist. Thus, just 

```
downloads-walkintheword.com
```

would have done the job.

---

