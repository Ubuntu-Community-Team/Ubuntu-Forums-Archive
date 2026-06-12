---
title: "Ubuntuone browser start problem"
date: 2010-01-31
forum: Ubuntu One (CLOSED)
---

### Post by thedeli on 2010-01-31
"Add Your Computer The final step is adding your computer to your Ubuntu One account. A web page will launch after clicking Ubuntu One in the previous step (see the image below). Simply click on 'Add this Computer'. Because this is your computer, it's necessary for you to explicitly allow the software to access your Ubuntu One account."

says like that in the installation process. I am using karmic koala, so the ubuntuone client came installed. when I start it I only see the cloud icon. I cannot login. Browser does not start to login. I reinstalled, uninstalled and installed again. but nothing changes. I want to use "One" :)

---

### Post by duanedesign on 2010-02-01
1. Quit the Ubuntu One client. R-click on the applet(icon) in the panel
      and select 'Quit'
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. See if you have an entry for 'Ubuntu One token'. If you do Right
      click on it and select Delete.
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. If your computer is listed click on the checkbox next to your
      computer.
   7. Click the "Remove selected computers" button
   8. Open Applications->Internet->Ubuntu One
   9. A web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer 

You should be connected after you follow these steps. If you are not connected, can you please attach the following files to this thread?

~/.cache/ubuntuone/log/oauth-login.log
~/.cache/ubuntuone/log/syncdaemon-exceptions.log

---

### Post by can0ne on 2010-02-01
> **thedeli said:**
> "Add Your Computer The final step is adding your computer to your Ubuntu One account. A web page will launch after clicking Ubuntu One in the previous step (see the image below). Simply click on 'Add this Computer'. Because this is your computer, it's necessary for you to explicitly allow the software to access your Ubuntu One account."

says like that in the installation process. I am using karmic koala, so the ubuntuone client came installed. when I start it I only see the cloud icon. I cannot login. Browser does not start to login. I reinstalled, uninstalled and installed again. but nothing changes. I want to use "One" :)

which package did you reinstall?
i've had the same problem some minutes ago and solved it by "aptitude install ubuntuone-client-gnome". then the page came up, after clicking "One" :)

---

### Post by can0ne on 2010-02-01
> **thedeli said:**
> "Add Your Computer The final step is adding your computer to your Ubuntu One account. A web page will launch after clicking Ubuntu One in the previous step (see the image below). Simply click on 'Add this Computer'. Because this is your computer, it's necessary for you to explicitly allow the software to access your Ubuntu One account."

says like that in the installation process. I am using karmic koala, so the ubuntuone client came installed. when I start it I only see the cloud icon. I cannot login. Browser does not start to login. I reinstalled, uninstalled and installed again. but nothing changes. I want to use "One" :)

which package did you reinstall?
i've had the same problem some minutes ago and solved it by "aptitude install ubuntuone-client-gnome". you also can try "u1sync --authorize"

---

### Post by thedeli on 2010-02-01
> **duanedesign said:**
> 1. Quit the Ubuntu One client. R-click on the applet(icon) in the panel
      and select 'Quit'
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. See if you have an entry for 'Ubuntu One token'. If you do Right
      click on it and select Delete.
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. If your computer is listed click on the checkbox next to your
      computer.
   7. Click the "Remove selected computers" button
   8. Open Applications->Internet->Ubuntu One
   9. A web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer 

You should be connected after you follow these steps. If you are not connected, can you please attach the following files to this thread?

~/.cache/ubuntuone/log/oauth-login.log
~/.cache/ubuntuone/log/syncdaemon-exceptions.log

"You haven't added any computers or devices to your Ubuntu One account. To get started please visit the installation details." I am getting this on step 5. 
oauth-login : 
```
Ubuntu One istemcisi 1.0.2 sürümü ba&#351;lat&#305;l&#305;yor
Dahili hata: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/main.py", line 244, in maybe_login
    self.processor.login(realm, consumer_key, do_login)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/main.py", line 81, in login
    from ubuntuone.oauthdesktop.auth import AuthorisationClient
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 38, in <module>
    from twisted.web import server, resource
  File "/usr/lib/python2.6/dist-packages/twisted/web/server.py", line 29, in <module>
    from twisted.spread import pb
  File "/usr/lib/python2.6/dist-packages/twisted/spread/pb.py", line 49, in <module>
    from twisted.spread.jelly import jelly, unjelly, globalSecurity
  File "/usr/lib/python2.6/dist-packages/twisted/spread/jelly.py", line 89, in <module>
    import decimal
  File "/usr/lib/python2.6/decimal.py", line 3584, in <module>
    val = globals()[globalname]
KeyError: 'ROUND_CEiLiNG'

Ubuntu One istemcisi 1.0.2 sürümü ba&#351;lat&#305;l&#305;yor
Dahili hata: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/main.py", line 244, in maybe_login
    self.processor.login(realm, consumer_key, do_login)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/main.py", line 81, in login
    from ubuntuone.oauthdesktop.auth import AuthorisationClient
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 38, in <module>
    from twisted.web import server, resource
  File "/usr/lib/python2.6/dist-packages/twisted/web/server.py", line 29, in <module>
    from twisted.spread import pb
  File "/usr/lib/python2.6/dist-packages/twisted/spread/pb.py", line 49, in <module>
    from twisted.spread.jelly import jelly, unjelly, globalSecurity
  File "/usr/lib/python2.6/dist-packages/twisted/spread/jelly.py", line 89, in <module>
    import decimal
  File "/usr/lib/python2.6/decimal.py", line 3584, in <module>
    val = globals()[globalname]
KeyError: 'ROUND_CEiLiNG'

Ubuntu One istemcisi 1.0.2 sürümü ba&#351;lat&#305;l&#305;yor
Dahili hata: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/main.py", line 244, in maybe_login
    self.processor.login(realm, consumer_key, do_login)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/main.py", line 81, in login
    from ubuntuone.oauthdesktop.auth import AuthorisationClient
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 38, in <module>
    from twisted.web import server, resource
  File "/usr/lib/python2.6/dist-packages/twisted/web/server.py", line 29, in <module>
    from twisted.spread import pb
  File "/usr/lib/python2.6/dist-packages/twisted/spread/pb.py", line 49, in <module>
    from twisted.spread.jelly import jelly, unjelly, globalSecurity
  File "/usr/lib/python2.6/dist-packages/twisted/spread/jelly.py", line 89, in <module>
    import decimal
  File "/usr/lib/python2.6/decimal.py", line 3584, in <module>
    val = globals()[globalname]
KeyError: 'ROUND_CEiLiNG'

Ubuntu One istemcisi 1.0.2 sürümü ba&#351;lat&#305;l&#305;yor
Dahili hata: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/main.py", line 244, in maybe_login
    self.processor.login(realm, consumer_key, do_login)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/main.py", line 81, in login
    from ubuntuone.oauthdesktop.auth import AuthorisationClient
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 38, in <module>
    from twisted.web import server, resource
  File "/usr/lib/python2.6/dist-packages/twisted/web/server.py", line 29, in <module>
    from twisted.spread import pb
  File "/usr/lib/python2.6/dist-packages/twisted/spread/pb.py", line 49, in <module>
    from twisted.spread.jelly import jelly, unjelly, globalSecurity
  File "/usr/lib/python2.6/dist-packages/twisted/spread/jelly.py", line 89, in <module>
    import decimal
  File "/usr/lib/python2.6/decimal.py", line 3584, in <module>
    val = globals()[globalname]
KeyError: 'ROUND_CEiLiNG'

```

syncdaemon-exceptions : 
```
2010-02-01 01:24:33,978 - ubuntuone.SyncDaemon.DBus - ERROR - Can't get the auth token
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1073, in connect
    access_token = self.main.get_access_token()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/main.py", line 299, in get_access_token
    return self.oauth_client.get_access_token()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/main.py", line 339, in get_access_token
    raise NoAccessToken("No access token found.")
NoAccessToken: No access token found.
2010-02-01 01:24:43,998 - ubuntuone.SyncDaemon.DBus - ERROR - Can't get the auth token
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1073, in connect
    access_token = self.main.get_access_token()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/main.py", line 299, in get_access_token
    return self.oauth_client.get_access_token()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/main.py", line 339, in get_access_token
    raise NoAccessToken("No access token found.")
NoAccessToken: No access token found.
```

---

### Post by thedeli on 2010-02-01
> **can0ne said:**
> which package did you reinstall?
i've had the same problem some minutes ago and solved it by "aptitude install ubuntuone-client-gnome". you also can try "u1sync --authorize"

"u1sync --authorize" worked for me and I added my computer. and yes :) it worked. I can sync my files :) thank you all :)

---

### Post by joshuahoover on 2010-02-01
> **thedeli said:**
> "You haven't added any computers or devices to your Ubuntu One account. To get started please visit the installation details." I am getting this on step 5. 
oauth-login : 
```
Ubuntu One istemcisi 1.0.2 sürümü ba&#351;lat&#305;l&#305;yor
Dahili hata: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/main.py", line 244, in maybe_login
    self.processor.login(realm, consumer_key, do_login)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/main.py", line 81, in login
    from ubuntuone.oauthdesktop.auth import AuthorisationClient
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 38, in <module>
    from twisted.web import server, resource
  File "/usr/lib/python2.6/dist-packages/twisted/web/server.py", line 29, in <module>
    from twisted.spread import pb
  File "/usr/lib/python2.6/dist-packages/twisted/spread/pb.py", line 49, in <module>
    from twisted.spread.jelly import jelly, unjelly, globalSecurity
  File "/usr/lib/python2.6/dist-packages/twisted/spread/jelly.py", line 89, in <module>
    import decimal
  File "/usr/lib/python2.6/decimal.py", line 3584, in <module>
    val = globals()[globalname]
KeyError: 'ROUND_CEiLiNG'
```

I think you're affected by the following bug, which has a workaround described there: [https://bugs.edge.launchpad.net/ubuntuone-client/+bug/467397](https://bugs.edge.launchpad.net/ubuntuone-client/+bug/467397)

Thanks,

Joshua

---

