---
title: "Howto: Chromium+tor+polipo"
date: 2012-06-18
forum: Tutorials
---

### Post by art2003 on 2012-06-18
Tested with Ubuntu 12.04

```

sudo apt-get update
sudo apt-get install chromium-browser tor polipo

```

Now edit /etc/polipo/config
and add:

```

socksParentProxy = "localhost:9050"
diskCacheRoot = ""
disableLocalInterface=true

```

Now when you want to be on tor launch it with:

```

chromium-browser --proxy-server="127.0.0.1:8123;https=127.0.0.1:8123;
socks=127.0.0.1:8123;sock4=127.0.0.1:8123;
sock5=127.0.0.1:8123,ftp=127.0.0.1:8123" --incognito check.torproject.org

```

You can put that line inside a bash script or in a launcher

---

### Post by TomasKrchnak on 2013-02-22
Doesn't work for me, after following your steps Chromium says it is not using Tor network. Could you help me find where the problem might be? Thanks in advance :)

// update: Everything is OK after restart, my fault. Thanks for your work :)

---

