---
title: "Proxy issues with flasplugin-installer"
date: 2012-04-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Ender985 on 2012-04-20
Hello all,

So I'm testing 12.04 from behind a proxy. So far I have set the proxy in Network Settings (and applyed systemwide), I have set the exports for $http_proxy, $https_proxy and $ftp_proxy in ~/.bashrc,  and I have written it to /etc/wgetrc and /etc/apt/apt.conf . So that browsers work, the graphical package manager works and apt-get via command line also works.

Except for the flashplugin-intstaller. Each time it tries to fecth  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.233.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.233.orig.tar.gz) , it gets stuck there for a few minutes, and eventually times out with

```
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 234, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 93, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 239, in retrieve
    fp = self.open(url, data)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 344, in open_http
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 954, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 814, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 776, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 757, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 571, in create_connection
    raise err
IOError: [Errno socket error] [Errno 110] Connection timed out
```

I can download the .tar.gz just fine via both browser and wget, so getting to the file is not the problem. It has to be that the script performing the update does not recognize the proxy, but I have set it up in every location I know and yet it keeps failing.

Does anybody know how to fix this?

---

### Post by zika on 2012-04-20
> **Ender985 said:**
> Hello all,

So I'm testing 12.04 from behind a proxy. So far I have set the proxy in Network Settings (and applyed systemwide), I have set the exports for $http_proxy, $https_proxy and $ftp_proxy in ~/.bashrc,  and I have written it to /etc/wgetrc and /etc/apt/apt.conf . So that browsers work, the graphical package manager works and apt-get via command line also works.

Except for the flashplugin-intstaller. Each time it tries to fecth  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.233.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.233.orig.tar.gz) , it gets stuck there for a few minutes, and eventually times out with

```
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 234, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 93, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 239, in retrieve
    fp = self.open(url, data)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 344, in open_http
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 954, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 814, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 776, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 757, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 571, in create_connection
    raise err
IOError: [Errno socket error] [Errno 110] Connection timed out
```I can download the .tar.gz just fine via both browser and wget, so getting to the file is not the problem. It has to be that the script performing the update does not recognize the proxy, but I have set it up in every location I know and yet it keeps failing.

Does anybody know how to fix this?If You just want flash to work: once You've done with wget, extract libflashplayer.so in ~/.mozilla/plugins and forget about proxy... ;)
It is the other story if you're concerned with the script and why it does not work... That is flash-non-related... ;)

---

### Post by Ender985 on 2012-04-20
Thanks for the workaround. I thought I would report the problem here so we can fix it before 12.04 goes live, so I was planning to leave flash broken until we can figure out how to solve it. However I'm thinking I will still be able to reproduce the problem even if I install it manually, so I'll probably just do that.

I tried to understand the script to see what is the command it is using to download the package, but to no avail..

---

