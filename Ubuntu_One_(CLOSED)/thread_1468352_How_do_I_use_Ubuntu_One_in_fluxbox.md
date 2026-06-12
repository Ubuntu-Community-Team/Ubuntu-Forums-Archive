---
title: "How do I use Ubuntu One in fluxbox?"
date: 2010-05-01
forum: Ubuntu One (CLOSED)
---

### Post by dan000 on 2010-05-01
I have two computers. One running regular Ubuntu, and I use Gnome on it. The other runs Xubuntu, but I use Fluxbox, rather than XFCE.

I've already upgraded both to Lucid Lynx. I set up Ubuntu One on the Ubuntu box, but can't figure out how to get it working in Fluxbox on the Xubuntu box.

Here's what I've done so far:
I installed ubuntuone-client, ubuntuone-client-gnome, and ubuntuoneclient-tools, and, of course, any dependencies.
I ran ubuntuone-launch (which starts the syncdaemon).

I tried using ubuntuone-preferences to actually set it up on this computer. At first, I was having errors that related to gnome-keyring-daemon, but I fixed that by adding "gnome-keyring-daemon --start" to my ~/.fluxbox/startup file. I didn't use to need that for gnome-keyring-daemon to work properly, so I'm not sure why I need it now.

Anyway, once I got that sorted, opening ubuntuone-preferences didn't give me any options to set up the account on this computer. It's supposed to open up a new browser window to setup OAuth, but it didn't.

So, I tried to set it up using "u1sync --authorize".
This opened up a browser window like I expected, I put in my username and password, authorized this computer. It redirected me to a localhost page, which redirected me back to my Ubuntu One account page, but in the terminal, I had this error:
```
Created new window in existing browser session.
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/protocols/basic.py", line 251, in dataReceived
    why = self.lineReceived(line)
  File "/usr/lib/python2.6/dist-packages/twisted/web/http.py", line 1573, in lineReceived
    self.allContentReceived()
  File "/usr/lib/python2.6/dist-packages/twisted/web/http.py", line 1641, in allContentReceived
    req.requestReceived(command, path, version)
  File "/usr/lib/python2.6/dist-packages/twisted/web/http.py", line 807, in requestReceived
    self.process()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/web/server.py", line 125, in process
    self.render(resrc)
  File "/usr/lib/python2.6/dist-packages/twisted/web/server.py", line 132, in render
    body = resrc.render(self)
  File "/usr/lib/python2.6/dist-packages/twisted/web/resource.py", line 210, in render
    return m(request)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 466, in render_GET
    self.retrieve_function(store=self.store_yes_no, verifier=verifier)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 396, in retrieve_access_token
    access_token = self.make_token_request(oauth_request)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 261, in make_token_request
    self._forward_error_callback(error)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 160, in _forward_error_callback
    raise error
exceptions.Exception: Invalid request token: fjX45fVBnlX40PxmSSGS

```
I tried this several times, and the only thing that changed was the request token.
On [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/), both machines are listed, and the xubuntu machine is listed multiple times, with each request token. However, I know it's not working, because in Ubuntu One Preferences, it shows it's disconnected, and the output of "u1sdtool -s" is:
```
State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE
```
I don't see how the request token could be invalid, so maybe it's a problem with python-twisted-web, but I'm sure I don't know what.
I'm out of ideas. Anyone else have any?

---

### Post by joshuahoover on 2010-05-03
> **dan000 said:**
> I have two computers. One running regular Ubuntu, and I use Gnome on it. The other runs Xubuntu, but I use Fluxbox, rather than XFCE.

I've already upgraded both to Lucid Lynx. I set up Ubuntu One on the Ubuntu box, but can't figure out how to get it working in Fluxbox on the Xubuntu box.

Here's what I've done so far:
I installed ubuntuone-client, ubuntuone-client-gnome, and ubuntuoneclient-tools, and, of course, any dependencies.
I ran ubuntuone-launch (which starts the syncdaemon).

I tried using ubuntuone-preferences to actually set it up on this computer. At first, I was having errors that related to gnome-keyring-daemon, but I fixed that by adding "gnome-keyring-daemon --start" to my ~/.fluxbox/startup file. I didn't use to need that for gnome-keyring-daemon to work properly, so I'm not sure why I need it now.

Anyway, once I got that sorted, opening ubuntuone-preferences didn't give me any options to set up the account on this computer. It's supposed to open up a new browser window to setup OAuth, but it didn't.

So, I tried to set it up using "u1sync --authorize".
This opened up a browser window like I expected, I put in my username and password, authorized this computer. It redirected me to a localhost page, which redirected me back to my Ubuntu One account page, but in the terminal, I had this error:
```
Created new window in existing browser session.
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/protocols/basic.py", line 251, in dataReceived
    why = self.lineReceived(line)
  File "/usr/lib/python2.6/dist-packages/twisted/web/http.py", line 1573, in lineReceived
    self.allContentReceived()
  File "/usr/lib/python2.6/dist-packages/twisted/web/http.py", line 1641, in allContentReceived
    req.requestReceived(command, path, version)
  File "/usr/lib/python2.6/dist-packages/twisted/web/http.py", line 807, in requestReceived
    self.process()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/web/server.py", line 125, in process
    self.render(resrc)
  File "/usr/lib/python2.6/dist-packages/twisted/web/server.py", line 132, in render
    body = resrc.render(self)
  File "/usr/lib/python2.6/dist-packages/twisted/web/resource.py", line 210, in render
    return m(request)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 466, in render_GET
    self.retrieve_function(store=self.store_yes_no, verifier=verifier)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 396, in retrieve_access_token
    access_token = self.make_token_request(oauth_request)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 261, in make_token_request
    self._forward_error_callback(error)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 160, in _forward_error_callback
    raise error
exceptions.Exception: Invalid request token: fjX45fVBnlX40PxmSSGS

```I tried this several times, and the only thing that changed was the request token.
On [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/), both machines are listed, and the xubuntu machine is listed multiple times, with each request token. However, I know it's not working, because in Ubuntu One Preferences, it shows it's disconnected, and the output of "u1sdtool -s" is:
```
State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE
```I don't see how the request token could be invalid, so maybe it's a problem with python-twisted-web, but I'm sure I don't know what.
I'm out of ideas. Anyone else have any?

What happens if you run the following command?

u1sdtool -c

My guess is that you're running into problems related to the server side. We're working on fixing these problems right now. We'll keep you updated in two ways on our progress:

1) [http://identi.ca/ubuntuone](http://identi.ca/ubuntuone) 
2) [https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status) 

My apologies for the inconvenience and thank you for your patience.

Thank you,

Joshua

---

