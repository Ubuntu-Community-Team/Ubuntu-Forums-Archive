---
title: "sudo add-apt-repository ppa:mozillateam/ppa error in terminal"
date: 2022-08-08
forum: Ubuntu/Debian BASED
---

### Post by f23948 on 2022-08-08
After I entered in terminal: sudo add-apt-repository ppa:mozillateam/ppa it gives me error
```
Traceback (most recent call last):  File "/usr/bin/add-apt-repository", line 364, in <module>
    sys.exit(0 if addaptrepo.main() else 1)
  File "/usr/bin/add-apt-repository", line 347, in main
    shortcut = handler(source, **shortcut_params)
  File "/usr/lib/python3/dist-packages/softwareproperties/shortcuts.py", line 40, in shortcut_handler
    return handler(shortcut, **kwargs)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 82, in __init__
    if self.lpppa.publish_debug_symbols:
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 120, in lpppa
    self._lpppa = self.lpteam.getPPAByName(name=self.ppaname)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in lpteam
    self._lpteam = self.lp.people(self.teamname)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 98, in lp
    self._lp = login_func("%s.%s" % (self.__module__, self.__class__.__name__),
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 494, in login_anonymously
    return cls(
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 230, in __init__
    super(Launchpad, self).__init__(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/resource.py", line 472, in __init__
    self._wadl = self._browser.get_wadl_application(self._root_uri)
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 447, in get_wadl_application
    response, content = self._request(url, media_type=wadl_type)
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 389, in _request
    response, content = self._request_and_retry(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 359, in _request_and_retry
    response, content = self._connection.request(
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1725, in request
    (response, content) = self._request(
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 144, in _request
    response, content = super(LaunchpadOAuthAwareHttp, self)._request(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 184, in _request
    return super(RestfulHttp, self)._request(
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1441, in _request
    (response, content) = self._conn_request(conn, request_uri, method, body, headers)
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1363, in _conn_request
    conn.connect()
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1153, in connect
    sock.connect((self.host, self.port))
TimeoutError: [Errno 110] Connection timed out
```

---

### Post by f23948 on 2022-08-09
Bump still waiting

---

### Post by ajgreeny on 2022-08-09
Please run that ```
sudo add-apt-repository ppa:mozillateam/ppa
``` again but this time instead of just showing us the apparent error show us everything, including the command in the top line.

I am not sure what this might show you but it should show 
```
user@Xubuntu-2204:~$ sudo add-apt-repository ppa:mozillateam/ppa
[sudo] password for user: 
PPA publishes dbgsym, you may need to include 'main/debug' component
Repository: 'deb https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu/ jammy main'
Description:
Mozilla Team's Firefox 102 ESR and Thunderbird 91 stable builds
More info: https://launchpad.net/~mozillateam/+archive/ubuntu/ppa
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
```
It may also help if you look at the thread at [https://ubuntuforums.org/showthread.php?t=2474534](https://ubuntuforums.org/showthread.php?t=2474534) where a few options, perhaps related to python3,  might give you an answer.

---

### Post by guiverc on 2022-08-09
Have you made any changes to your default python3 ?  as errors with Ubuntu tools can be expected if you've changed the version of any default python3 to something different (*newer, older*) than it was designed for.

---

### Post by f23948 on 2022-08-09
> **ajgreeny said:**
> Please run that ```
sudo add-apt-repository ppa:mozillateam/ppa
``` again but this time instead of just showing us the apparent error show us everything, including the command in the top line.

I am not sure what this might show you but it should show 
```
user@Xubuntu-2204:~$ sudo add-apt-repository ppa:mozillateam/ppa
[sudo] password for user: 
PPA publishes dbgsym, you may need to include 'main/debug' component
Repository: 'deb https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu/ jammy main'
Description:
Mozilla Team's Firefox 102 ESR and Thunderbird 91 stable builds
More info: https://launchpad.net/~mozillateam/+archive/ubuntu/ppa
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
```
It may also help if you look at the thread at [https://ubuntuforums.org/showthread.php?t=2474534](https://ubuntuforums.org/showthread.php?t=2474534) where a few options, perhaps related to python3,  might give you an answer.

Thank you! I got it working today! I don't know why it gives me error yesterday

---

### Post by ajgreeny on 2022-08-10
Great news.
Perhaps the PPA was temporarily offline, but as you have now got things working please mark the reread as SOLVED from the Thread Tools menu up top.

---

