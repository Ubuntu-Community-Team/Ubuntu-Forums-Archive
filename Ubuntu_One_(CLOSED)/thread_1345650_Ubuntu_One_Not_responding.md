---
title: "Ubuntu One Not responding"
date: 2009-12-04
forum: Ubuntu One (CLOSED)
---

### Post by Irritated on 2009-12-04
Having upgraded to Ubuntu 9.10 I've been trying to set up Ubuntu One for some time now with no success. When I click Application > Internet > Ubuntu One nothing happens for good while and then I get "Ubuntu One:Error. Authorization Error [Errno socket error][Errno 104] Connection reset by peer".
 I've also tried installing Dropbox as an alternative but this just gives me "Trouble connecting to Dropbox servers. Maybe your internet connection is down, or you need to set your http_proxy environment variable." Eventhough I have set the http_proxy.
I feel there is a connection (excuse the pun) between the two problems. Help. I'm very irritated.

---

### Post by andrea000 on 2009-12-05
Have you authorized your pc on u1's website or have
you made it that far yet?Just in case you have not
update your computer then open a terminal 
applications->accessories->terminal
copy and paste this
> u1sync --authorize
the u1 website should come up asking you to add your
pc.That's about all i can tell you as for a reason
that might be causing your problem.

---

### Post by Irritated on 2009-12-07
No I hadn't got that far yet. All I've ever done with Ubuntu One on my desktop on is click Applications > Internet > Ubuntu One.  So I tried  u1sync --authorize but I think this is just the command line version of clicking the former. In any case it just gave me the same error but with a little bit more info:
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 576, in msg_reply_handler
    reply_handler(*message.get_args_list(**get_args_opts))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 276, in got_state
    self.acquire_access_token(description, store)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 336, in acquire_access_token
    self.request_token = self.make_token_request(oauth_request)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 232, in make_token_request
    self._forward_error_callback(e)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 145, in _forward_error_callback
    raise error
IOError: [Errno socket error] [Errno 104] Connection reset by peer

---

### Post by tns09 on 2009-12-07
I get this error when trying to connect
IOError: Error showing url: Failed to execute child process "/opt/firefox/firefox" (No such file or directory)
Ubuntu 9.10

---

### Post by Irritated on 2009-12-08
I uninstalled Ubuntu One and installed it again and now my error message reads:
Ubuntu One:Error
Authorization Error
[Errno socket error][Errno 110] Connection timed out

So obviously the problem is something to do with the way Ubuntu One connects to the internet. Every other part of Ubuntu connects to the internet fine through my proxy.

---

### Post by babumuchhala on 2009-12-08
At my college I also have a proxy, and I keep getting the same error
```
[Errno socket error][Errno 110] Connection timed out
```

---

### Post by Irritated on 2009-12-08
> **babumuchhala said:**
> At my college I also have a proxy, and I keep getting the same error
```
[Errno socket error][Errno 110] Connection timed out
```
Are you on a Windows network? I am. I think that might be part of the problem. Just a hunch though.

---

### Post by joshuahoover on 2009-12-15
> **babumuchhala said:**
> At my college I also have a proxy, and I keep getting the same error
```
[Errno socket error][Errno 110] Connection timed out
```

Ubuntu One currently won't work behind a proxy server.

---

### Post by molnarandris on 2010-01-04
> Ubuntu One currently won't work behind a proxy server.

Will this behavior ever change? I wanted to try it out in september, when I ran into this error. I just gave it one more try, but it does not seem to change. Isn't it frequent to use proxy servers? 

It's because of the proxy, isn't it? :

```
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 576, in msg_reply_handler
    reply_handler(*message.get_args_list(**get_args_opts))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 292, in got_state
    self.acquire_access_token(description, store)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 359, in acquire_access_token
    self.request_token = self.make_token_request(oauth_request)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 260, in make_token_request
    self._forward_error_callback(oauth.OAuthError(data))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 160, in _forward_error_callback
    raise error
oauth.oauth.OAuthError

```

Thanks,
Andras

---

### Post by rchar66 on 2010-01-04
I'm also getting the "*[Errno socket error][Errno 110] Connection timed out*" error message.

If it's because of the proxy server here, then it's really pointless to even try using ubuntuone. I'm usually on a network with a proxy server.

---

### Post by InteXX on 2010-01-08
> **joshuahoover said:**
> Ubuntu One currently won't work behind a proxy server.

Does this include NAT?

Thanks,
Jeff

---

