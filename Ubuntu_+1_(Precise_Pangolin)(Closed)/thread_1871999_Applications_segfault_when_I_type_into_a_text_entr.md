---
title: "Applications segfault when I type into a text entry box"
date: 2011-10-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jfernyhough on 2011-10-29
I'm beginning to pull my hair out. When I type into certain text boxes, for example each of gksudo, synaptic quick search, File Save As... the application quits. Terminator won't run (segfault).

When run from the terminal all give a simple "Segmentation fault".

Firefox works fine (otherwise I'd be really screwed), as does gnome-terminal.

I'm not running PPAs other than for non-system software (e.g. chromium, firefox-trunk, virtualbox). I did have gnome3-team/gnome3 and ricotz/testing enabled but have ppa-purged back - same thing happening.

Where do I look?

---

### Post by jfernyhough on 2011-10-30
Hmm. This is looking interesting.

I ran chromium-browser -g which starts it within gdb (handy) and the final error is as follows:
```
#0  0x00007fffee7414c5 in _IO_file_doallocate ()
   from /lib/x86_64-linux-gnu/libc.so.6
```running bt at this point goes back to /usr/lib/x86_64-linux-gnu/libXcursor.so.1

```
#6  0x00007fffeccbec80 in ?? () from /usr/lib/x86_64-linux-gnu/libXcursor.so.1
```Now this is interesting as I just recently tried to change the default cursor theme as I got tired of having one theme for title bars (DMZ-White) and within e.g. Firefox windows (neutral). Known issue which has a workaround (sudo update-alternatives --config x-cursor-theme).

Resetting x-cursor-theme doesn't seem to have made any difference, though.

However, I also found this bug report: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/652026](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/652026) though the only resolution is a "fix released" with no details, which is less than useful.

Going to try GDM instead of LightDM and see if it makes a difference.

--edit
Nope. No difference.

Also tried resetting x-cursor-theme back to auto (DMZ-White).

--edit 2
Full stack trace if anyone is interested
```
Program received signal SIGSEGV, Segmentation fault.
0x00007fffee7414c5 in _IO_file_doallocate () from /lib/x86_64-linux-gnu/libc.so.6
(gdb) bt
#0  0x00007fffee7414c5 in _IO_file_doallocate () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007fffee74ed3c in _IO_doallocbuf () from /lib/x86_64-linux-gnu/libc.so.6
#2  0x00007fffee74ddb4 in _IO_file_underflow () from /lib/x86_64-linux-gnu/libc.so.6
#3  0x00007fffee74ed7e in _IO_default_uflow () from /lib/x86_64-linux-gnu/libc.so.6
#4  0x00007fffee74308a in _IO_getline_info () from /lib/x86_64-linux-gnu/libc.so.6
#5  0x00007fffee741f6b in fgets () from /lib/x86_64-linux-gnu/libc.so.6
#6  0x00007fffeccbec80 in ?? () from /usr/lib/x86_64-linux-gnu/libXcursor.so.1
#7  0x00007fffeccbf095 in ?? () from /usr/lib/x86_64-linux-gnu/libXcursor.so.1
#8  0x00007fffeccbf140 in ?? () from /usr/lib/x86_64-linux-gnu/libXcursor.so.1
#9  0x00007fffeccbf140 in ?? () from /usr/lib/x86_64-linux-gnu/libXcursor.so.1
```

---

### Post by jfernyhough on 2011-10-30
Not the kernel. Tried using Liquorix 3.0.8, same thing.

Wonder if this is a pygtk thing. I found a couple of references when searching.

--edit

This is looking more like a python thing. Tried running SickBeard and now the web UI won't load.

```

Traceback (most recent call last):   File "/home/jonathon/src/Sick-Beard/cherrypy/_cprequest.py", line 660, in respond     response.body = self.handler()   File "/home/jonathon/src/Sick-Beard/cherrypy/lib/encoding.py", line 193, in __call__     self.body = self.oldhandler(*args, **kwargs)   File "/home/jonathon/src/Sick-Beard/cherrypy/_cpdispatch.py", line 25, in __call__     return self.callable(*self.args, **self.kwargs)   File "/home/jonathon/src/Sick-Beard/sickbeard/webserve.py", line 1806, in index     return _munge(t)   File "/home/jonathon/src/Sick-Beard/sickbeard/webserve.py", line 98, in _munge     return unicode(string).encode('utf-8', 'xmlcharrefreplace')   File "/usr/lib/pymodules/python2.7/Cheetah/Template.py", line 1010, in __unicode__     return getattr(self, mainMethName)()   File "_home_jonathon_src_Sick_Beard_data_interfaces_default_home_tmpl.py", line 288, in respond   File "/home/jonathon/src/Sick-Beard/sickbeard/tv.py", line 655, in nextEpisode     curEp = self.getEpisode(int(sqlEp["season"]), int(sqlEp["episode"]))   File "/home/jonathon/src/Sick-Beard/sickbeard/tv.py", line 133, in getEpisode     ep = TVEpisode(self, season, episode)   File "/home/jonathon/src/Sick-Beard/sickbeard/tv.py", line 956, in __init__     self.specifyEpisode(self.season, self.episode)   File "/home/jonathon/src/Sick-Beard/sickbeard/tv.py", line 1017, in specifyEpisode     result = self.loadFromTVDB(season, episode)   File "/home/jonathon/src/Sick-Beard/sickbeard/tv.py", line 1092, in loadFromTVDB     myEp = t[self.show.tvdbid][season][episode]   File "/home/jonathon/src/Sick-Beard/lib/tvdb_api/tvdb_api.py", line 824, in __getitem__     self._getShowData(key, self.config['language'])   File "/home/jonathon/src/Sick-Beard/lib/tvdb_api/tvdb_api.py", line 755, in _getShowData     self.config['url_seriesInfo'] % (sid, getShowInLanguage)   File "/home/jonathon/src/Sick-Beard/lib/tvdb_api/tvdb_api.py", line 538, in _getetsrc     src = self._loadUrl(url)   File "/home/jonathon/src/Sick-Beard/lib/tvdb_api/tvdb_api.py", line 522, in _loadUrl     header, resp = h.request(url, headers=h_header)   File "/home/jonathon/src/Sick-Beard/lib/httplib2/__init__.py", line 1142, in request     (response, content) = self._request(conn, authority, uri, request_uri, method, body, headers, redirections, cachekey)   File "/home/jonathon/src/Sick-Beard/lib/httplib2/__init__.py", line 914, in _request     (response, content) = self._conn_request(conn, request_uri, method, body, headers)   File "/home/jonathon/src/Sick-Beard/lib/httplib2/__init__.py", line 867, in _conn_request     conn.request(method, request_uri, body, headers)   File "/usr/lib/python2.7/httplib.py", line 955, in request     self._send_request(method, url, body, headers)   File "/usr/lib/python2.7/httplib.py", line 989, in _send_request     self.endheaders(body)   File "/usr/lib/python2.7/httplib.py", line 951, in endheaders     self._send_output(message_body)   File "/usr/lib/python2.7/httplib.py", line 811, in _send_output     self.send(msg)   File "/usr/lib/python2.7/httplib.py", line 773, in send     self.connect()   File "/home/jonathon/src/Sick-Beard/lib/httplib2/__init__.py", line 745, in connect     self.sock.connect(sa)   File "/home/jonathon/src/Sick-Beard/lib/socks/__init__.py", line 389, in connect     self.__negotiatehttp(destpair[0], destpair[1])   File "/home/jonathon/src/Sick-Beard/lib/socks/__init__.py", line 355, in __negotiatehttp     raise HTTPError((statuscode, statusline[2])) HTTPError: (403, 'Forbidden')
```--edit 2
New error
```
Program received signal SIGSEGV, Segmentation fault.
0x00007fffee746c90 in _IO_setb () from /lib/x86_64-linux-gnu/libc.so.6
(gdb) bt
#0  0x00007fffee746c90 in _IO_setb () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007fffee739540 in _IO_file_doallocate () from /lib/x86_64-linux-gnu/libc.so.6
#2  0x00007fffee746d3c in _IO_doallocbuf () from /lib/x86_64-linux-gnu/libc.so.6
#3  0x00007fffee745db4 in _IO_file_underflow () from /lib/x86_64-linux-gnu/libc.so.6
#4  0x00007fffee746d7e in _IO_default_uflow () from /lib/x86_64-linux-gnu/libc.so.6
#5  0x00007fffee73b08a in _IO_getline_info () from /lib/x86_64-linux-gnu/libc.so.6
#6  0x00007fffee739f6b in fgets () from /lib/x86_64-linux-gnu/libc.so.6
#7  0x00007fffeccb6c80 in ?? () from /usr/lib/x86_64-linux-gnu/libXcursor.so.1
#8  0x00007fffeccb7095 in ?? () from /usr/lib/x86_64-linux-gnu/libXcursor.so.1

```

--edit
Doesn't seem to be any problem with locales. All seem to be set correctly and up-to-date.

```
sudo dpkg-reconfigure locales
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... cannot open locale definition file `da_DK': No such file or directory
failed
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... cannot open locale definition file `hi_IN': No such file or directory
failed
  en_NG.UTF-8... cannot open locale definition file `da_DK': No such file or directory
failed
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... cannot open locale definition file `tl_PH': No such file or directory
failed
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZM.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.

```
I'd like to be able to cut down on the ones I'm not using though.

---

### Post by jfernyhough on 2011-10-30
I think a reinstall might be in order. I can't find any reason for this. Grr.

---

### Post by dino99 on 2011-10-31
where is your bug report ? I'm seeing the same issues too.

---

### Post by jfernyhough on 2011-10-31
Glad I'm not going crazy here. I haven't filed a report as I can't narrow it down to any particular thing. It could be libc or gtk or python or...

What should I report this against? I guess libc as it's common in each backtrace?

--edit
Argh, it's not precise. It's something in my /home. Rebooted to try my 11.10 Kubuntu install which just started not loading plasma, so I moved ~/.kde and logged in again. This time I get a desktop, but the same applications segfault with the exact same errors. This is painful.

Going to try creating a new user then migrating settings across.

---

### Post by jfernyhough on 2011-10-31
No problems initially with a new user so it's something in my configs. I tried using gnome-tweak-tool to select a custom mouse cursor theme (neutral) and the issues started. I went back to DMZ-White and no issues.

Annoying.

It's not just precise, though, so something somewhere has become corrupt.

OMG. No way. I just tried extracting the cursor theme again, overwriting both ~/icons/neutral and /usr/share/icons/neutral (from before for global cursor support) and guess what?

Fixed.

So it was down to a corrupt cursor theme. Crikey.

--edit
Uh, why does this affect Sickbeard? That's also working again...

---

