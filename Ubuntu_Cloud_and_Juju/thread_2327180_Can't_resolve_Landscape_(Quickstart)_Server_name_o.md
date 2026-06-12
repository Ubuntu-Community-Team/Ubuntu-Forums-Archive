---
title: "Can't resolve Landscape (Quickstart) Server name on local network"
date: 2016-06-08
forum: Ubuntu Cloud and Juju
---

### Post by cduston on 2016-06-08
I am trying to set up a small network inside of our University network, using Landscape to manage the machines. I've got the landscape server up and running, but I am having trouble connecting the clients. When I try to register the client, I get the following message:

```

sudo landscape-config --computer-title "PHY13" --account-name standalone --url https://PHY15/message-system --ping-url http://PHY15/ping
...
...(answering some questions...)
...
Request a new registration for this computer now? (Y/n): 
Please wait... We were unable to contact the server. Your internet connection may be down. The landscape client will continue to try and contact the server periodically.
```

Messages about connection in Landscape are stored in /var/log/landscape/broker.log:

```
2016-06-08 09:13:57,435 INFO     [MainThread] Starting urgent message exchange with https://PHY15/message-system.
2016-06-08 09:13:57,945 ERROR    [PoolThread-twisted.internet.reactor-1] Error contacting the server at https://PHY15/message-system.
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/landscape/broker/transport.py", line 71, in exchange
    message_api)
  File "/usr/lib/python2.7/dist-packages/landscape/broker/transport.py", line 45, in _curl
    headers=headers, cainfo=self._pubkey, curl=curl))
  File "/usr/lib/python2.7/dist-packages/landscape/lib/fetch.py", line 109, in fetch
    raise PyCurlError(e.args[0], e.args[1])
PyCurlError: Error 6: Could not resolve host: PHY15
2016-06-08 09:13:57,946 INFO     [MainThread] Message exchange failed.
2016-06-08 09:13:57,946 INFO     [MainThread] Message exchange completed in 0.51s.
```

Ok, so the host can't resolve. However, I *can* ping it by using 

```
ip addr show
```

on the server, and then

```
ping XX.XX.XX.XX
```

(XX.XX.XX.XX is the ip, I just don't know what is safe to share or not...). Anyway, I get answers to the ping. But, as you can see from the above, the name of the machine is:

```

hostname -f
PHY15

```

and I can ping this machine with PHY15.local, but I can't get the landscape-config to find it. I guess this looks like some kind of name search error on the client, or maybe something about the network. Anyone have any ideas on how to debug this?

EDIT: I am aware of some silliness with the self-signed certificates, although I am following the quickstart guide exactly I would like to point out that I have tried that fix. On the landscape server, I created my own CA, generated an SSL, and signed it with the new CA. Then I copied that certificate into the /usr/local/share/ca-certificates. directory on the client and ran sudo update-ca-certificates. Same response. Just for good measure, I also copied that .crt into /etc/landscape/ (which is pointed to by ssl_public_key in /etc/landscale/client.conf), with no success.

---

### Post by Christopher_Duston on 2016-06-16
So much for the "Ubuntu Community". Not like I had a bunch of replies over at LinuxQuestions, but at least I found someone there to stick with me and this is now solved.

In case anyone cares, the hostnames were inconsistent and whatever service is supposed to deal with that was not able to. I changed every single reference of "PHY15" to "PHY15.local" on both the client side and the server side. This means /etc/hostname, /etc/hosts, Landscape, Apache, and all the SSL and CA documents. Landscape is still giving me some problems, but I might be able to hack them.

Thanks for nothing!

---

### Post by QDR06VV9 on 2016-06-16
Well yes we care!:)
And thanks for sharing _**your** _solution with us here at UF.
Kind Regards

---

### Post by QIII on 2016-06-16
You might have done yourself a favor to bump your thread after 12 hours rather than giving it a couple of weeks to sink to the deep end of the pool and expecting everyone to go looking for it.

But I am glad you got it sorted out.

---

