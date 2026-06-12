---
title: "Landscape client on Server 18.04 unable to register (but client on 16.04 works fine)"
date: 2018-11-02
forum: Server Platforms
---

### Post by nextfalcon on 2018-11-02
We have a small collection of VMs mostly running 16.04-LTS, with a couple running 18.04-LTS.  I recently set up a new 18.04 system to run Landscape-on-Premises 18.03.  

The setup went fine and is running, all the 16.04 VMs are registered.  As expected I needed to give each client the server's certificate and specify it in /etc/landscape/client.conf by adding "ssl_public_key = /etc/ssl/certs/certnamehere.pem".

With the 18.04 systems though this does not work.  /var/log/landscape/broker.log shows "pycurl.error: (77, '')" just as if no ssl_public_key was specified.

Running landscape-configure with -k does not help.  Adding the cert and ca to /usr/local/share/ca-certificates and running update-ca-certificates does not help.

I have run out of rabbit holes to fall down trying to google the problem. 

Here is an example of /etc/landscape/client.conf
```

[client]
log_level = info
url = https://valid-FQDN-here/message-system
ping_url = http://valid-FQDN-here/ping
data_path = /var/lib/landscape/client
computer_title = AVMName
account_name = standalone
ssl_public_key = /etc/landscape/certnamehere.pem

```

Here is the output in /var/log/landscape/broker.log
```

2018-11-02 11:08:58,228 INFO     [MainThread] Starting urgent message exchange with https://valid-FQDN-here/message-system.
2018-11-02 11:08:58,233 ERROR    [PoolThread-twisted.internet.reactor-0] Error contacting the server at https://valid-FQDN-here/message-system.
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/landscape/lib/fetch.py", line 116, in fetch
    curl.perform()
pycurl.error: (77, '')


During handling of the above exception, another exception occurred:


Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/landscape/client/broker/transport.py", line 82, in exchange
    message_api)
  File "/usr/lib/python3/dist-packages/landscape/client/broker/transport.py", line 56, in _curl
    headers=headers, cainfo=self._pubkey, curl=curl))
  File "/usr/lib/python3/dist-packages/landscape/lib/fetch.py", line 118, in fetch
    raise PyCurlError(e.args[0], e.args[1])
landscape.lib.fetch.PyCurlError: Error 77:
2018-11-02 11:08:58,234 INFO     [MainThread] Message exchange failed.
2018-11-02 11:08:58,234 INFO     [MainThread] Message exchange completed in 0.01s.
2018-11-02 11:09:46,612 INFO     [MainThread] Broker stopped with config /etc/landscape/client.conf

```

I get the exact same behavior with all three Server-18.04-LTS VMs (two fresh installs, one do-release-upgrade'ed from 16.04).

Any suggestions as to what to try next?

---

### Post by tfrazier on 2019-10-04
Bump.  I'm running into this as well.

---

